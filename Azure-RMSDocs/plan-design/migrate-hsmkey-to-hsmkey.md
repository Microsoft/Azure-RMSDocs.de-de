---
title: "Schritt 2&colon; Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln | Azure RMS"
description: "Diese Anweisungen sind Teil des Migrationspfads von AD RMS zu Azure Rights Management und gelten nur, wenn Ihr AD RMS-Schlüssel HSM-geschützt ist und Sie die Migration zu Azure Rights Management mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 690729d16358b7b997d9cd1fd8cabed22ce78df4


---

# Schritt 2: Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, Azure Rights Management*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel HSM-geschützt ist und Sie die Migration zu Azure Rights Management mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) zurückkehren und eine andere Konfiguration auswählen.

> [!NOTE]
> Für diese Anweisungen wird angenommen, dass Ihr AD RMS-Schlüssel modulgeschützt ist. Dies ist der am häufigsten vorkommende Fall. 

Das Verfahren zum Importieren des HSM-Schlüssels und der AD RMS-Konfiguration in Azure RMS, um den von Ihnen verwalteten Azure RMS-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in zwei Phasen.

Da Ihr Azure RMS-Mandantenschlüssel von Azure Key Vault gespeichert und verwaltet wird, muss dieser Teil der Migration nicht nur in Azure Key RMS, sondern auch in Azure Key Vault verwaltet werden. Wenn Azure Key Vault für Ihre Organisation nicht von Ihnen, sondern von einem anderen Administrator verwaltet wird, müssen Sie sich mit diesem Administrator abstimmen und mit ihm zusammenarbeiten, um diese Prozeduren abzuschließen.

Stellen Sie zu Beginn sicher, dass Ihre Organisation über einen Schlüsseltresor verfügt, der in Azure Key Vault erstellt wurde, und dass er HSM-geschützte Schlüssel unterstützt. Auch wenn dies nicht erforderlich ist, empfehlen wir, einen dedizierten Schlüsseltresor für Azure RMS zu verwenden. Dieser Schlüsseltresor wird so konfiguriert, dass Azure RMS darauf zugreifen kann, sodass dieser Schlüsseltresor nur Azure RMS-Schlüssel enthält.


> [!TIP]
> Falls Sie die Konfigurationsschritte für Azure Key Vault ausführen möchten und noch nicht mit diesem Azure-Dienst vertraut sind, hilft Ihnen der Artikel [Erste Schritte mit Azure Key Vault ](https://azure.microsoft.com/documentation/articles/key-vault-get-started/) möglicherweise weiter. 


## Teil 1: Übertragen Ihres HSM-Schlüssels in Azure Key Vault

Diese Verfahren werden vom Administrator für Azure Key Vault durchgeführt.

1.  Befolgen Sie die Anweisungen in der Azure Key Vault-Dokumentation, indem Sie [Implementieren von „Bring Your Own Key“ (BYOK) für Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) mit folgender Ausnahme anwenden:

    - Führen Sie nicht die Schritte zum **Generieren Ihres Mandantenschlüssels** aus, da Sie bereits über das Äquivalent aus Ihrer AD RMS-Bereitstellung verfügen. Stattdessen müssen Sie den vom AD RMS-Server verwendeten Schlüssel aus der Thales-Installation identifizieren und diesen Schlüssel während der Migration verwenden. Verschlüsselte Thales-Schlüsseldateien weisen meist einen Namen nach dem Muster **key<*Schlüsselanwendungsname*><*Schlüsselbezeichner*>** auf dem lokalen Server auf.

    Wenn der Schlüssel in Azure Key Vault hochgeladen wird, werden Ihnen die Schlüsseleigenschaften, einschließlich der Schlüssel-ID, angezeigt. Dies sieht etwa so aus: https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Sie sollten sich diese URL notieren, da der Azure RMS-Administrator ihn benötigt, um Azure RMS mitzuteilen, dass dieser Schlüssel als Mandantenschlüssel verwendet werden soll.

2. Verwenden Sie während einer PowerShell-Sitzung an einer mit dem Internet verbundenen Arbeitsstation das Cmdlet [Set AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx ) zum Autorisieren des Azure RMS-Dienstprinzipals (Microsoft.Azure.RMS), damit dieser auf den Schlüsseltresor zugreifen kann, in dem der Azure RMS-Mandantenschlüssel gespeichert werden soll. Die erforderlichen Berechtigungen sind „decrypt“, „encrypt“, „unwrapkey“, „wrapkey“, „verify“ und „sign“.
    
    Wenn beispielsweise der Schlüsseltresor, den Sie für Azure RMS erstellt haben, „contoso-byok-ky“ heißt und die Ressourcengruppe „contoso-byok-rg“, führen Sie den folgenden Befehl aus:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign


Jetzt haben Sie Ihren HSM-Schlüssel in Azure Key Vault für Azure RMS vorbereitet und können die AD RMS-Konfigurationsdaten importieren.

## Teil 2: Importieren der Konfigurationsdaten in Azure RMS

Diese Verfahren werden vom Administrator für Azure RMS durchgeführt.

1.  Verwenden Sie während einer PowerShell-Sitzung an einer mit dem Internet verbundenen Arbeitsstation das Cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/dn629415.aspx ), um eine Verbindung mit Azure RMS herzustellen.
    
    Laden Sie dann mit dem Cmdlet [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx) die erste exportierte XML-Datei für eine vertrauenswürdige Veröffentlichungsdomäne hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. 
    
    Um dieses Cmdlet ausführen zu können, benötigen Sie die URL für den Schlüssel, der im vorherigen Schritt angegeben wurde.
    
    Beispielsweise würden Sie unter Verwendung unseres URL-Schlüsselwerts aus dem vorherigen Schritt und der TPD-Datei „C:\contoso-tpd1.xml“ Folgendes ausführen:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```
    
    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

2.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 1 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen.  

3.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Verwenden Sie das Azure RMS-Cmdlet [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx), wenn Sie später bestätigen müssen, welchen Schlüssel Ihr Azure RMS-Mandantenschlüssel in Azure Key Vault verwendet.

Sie können jetzt mit [Schritt 3: Aktivieren des RMS-Mandanten](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).




<!--HONumber=Aug16_HO4-->


