---
title: "Migrieren HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP"
description: "Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel HSM-geschützt ist und Sie die Migration zu Azure Information Protection mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: d0bb1cad20acdc16ee47c4a970a0cc095d07dc75
ms.lasthandoff: 02/24/2017


---

# <a name="step-2-hsm-protected-key-to-hsm-protected-key-migration"></a>Schritt 2: Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel HSM-geschützt ist und Sie die Migration zu Azure Information Protection mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) zurückkehren und eine andere Konfiguration auswählen.

> [!NOTE]
> Für diese Anweisungen wird angenommen, dass Ihr AD RMS-Schlüssel modulgeschützt ist. Dies ist der am häufigsten vorkommende Fall. 

Das Verfahren zum Importieren des HSM-Schlüssels und der AD RMS-Konfiguration in Azure Information Protection, um den von Ihnen verwalteten Azure Information Protection-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in zwei Phasen.

Da Ihr Azure Information Protection-Mandantenschlüssel von Azure Key Vault gespeichert und verwaltet wird, muss dieser Teil der Migration nicht nur in Azure Key Vault, sondern auch in Azure Information Protection verwaltet werden. Wenn Azure Key Vault für Ihre Organisation nicht von Ihnen, sondern von einem anderen Administrator verwaltet wird, müssen Sie sich mit diesem Administrator abstimmen und mit ihm zusammenarbeiten, um diese Prozeduren abzuschließen.

Stellen Sie zu Beginn sicher, dass Ihre Organisation über einen Schlüsseltresor verfügt, der in Azure Key Vault erstellt wurde, und dass er HSM-geschützte Schlüssel unterstützt. Auch wenn dies nicht erforderlich ist, empfehlen wir, einen dedizierten Schlüsseltresor für Azure Information Protection zu verwenden. Dieser Schlüsseltresor wird so konfiguriert, dass der Azure Rights Management-Dienst darauf zugreifen kann, sodass dieser Schlüsseltresor nur Azure Information Protection-Schlüssel enthält.


> [!TIP]
> Falls Sie die Konfigurationsschritte für Azure Key Vault ausführen möchten und noch nicht mit diesem Azure-Dienst vertraut sind, hilft Ihnen der Artikel [Erste Schritte mit Azure Key Vault ](https://azure.microsoft.com/documentation/articles/key-vault-get-started/) möglicherweise weiter. 


## <a name="part-1-transfer-your-hsm-key-to-azure-key-vault"></a>Teil 1: Übertragen Ihres HSM-Schlüssels in Azure Key Vault

Diese Verfahren werden vom Administrator für Azure Key Vault durchgeführt.

1.  Befolgen Sie die Anweisungen in der Azure Key Vault-Dokumentation, indem Sie [Implementieren von „Bring Your Own Key“ (BYOK) für Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) mit folgender Ausnahme anwenden:

    - Führen Sie nicht die Schritte zum **Generieren Ihres Mandantenschlüssels** aus, da Sie bereits über das Äquivalent aus Ihrer AD RMS-Bereitstellung verfügen. Stattdessen müssen Sie den vom AD RMS-Server verwendeten Schlüssel aus der Thales-Installation identifizieren und diesen Schlüssel während der Migration verwenden. Verschlüsselte Thales-Schlüsseldateien weisen meist einen Namen nach dem Muster **key<*Schlüsselanwendungsname*><*Schlüsselbezeichner*>** auf dem lokalen Server auf.

    Wenn der Schlüssel in Azure Key Vault hochgeladen wird, werden Ihnen die Schlüsseleigenschaften, einschließlich der Schlüssel-ID, angezeigt. Dies sieht etwa so aus: https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Sie sollten sich diese URL notieren, da der Azure Information Protection-Administrator ihn benötigt, um dem Azure Rights Management-Dienst mitzuteilen, dass dieser Schlüssel als Mandantenschlüssel verwendet werden soll.

2. Verwenden Sie während einer PowerShell-Sitzung an der mit dem Internet verbundenen Arbeitsstation das Cmdlet [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/en-us/library/mt603625(v=azure.300\).aspx) zum Autorisieren des Dienstprinzipals „Azure Rights Management“, damit dieser auf den Schlüsseltresor zugreifen kann, in dem der Azure Information Protection-Mandantenschlüssel gespeichert werden soll. Die erforderlichen Berechtigungen sind „decrypt“, „encrypt“, „unwrapkey“, „wrapkey“, „verify“ und „sign“.
    
    Wenn beispielsweise der Schlüsseltresor, den Sie für Azure Information Protection erstellt haben, „contoso-byok-ky“ heißt und die Ressourcengruppe „contoso-byok-rg“, führen Sie den folgenden Befehl aus:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get


Jetzt haben Sie Ihren HSM-Schlüssel in Azure Key Vault für den Azure Rights Management-Dienst von Azure Information Protection vorbereitet und können die AD RMS-Konfigurationsdaten importieren.

## <a name="part-2-import-the-configuration-data-to-azure-information-protection"></a>Teil 2: Importieren der Konfigurationsdaten in Azure Information Protection

Diese Verfahren werden vom Administrator für Azure Information Protection durchgeführt.

1.  Verwenden Sie während einer PowerShell-Sitzung an einer mit dem Internet verbundenen Arbeitsstation das Cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/dn629415.aspx), um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen.
    
    Laden Sie dann mit dem Cmdlet [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx) die erste exportierte XML-Datei für eine vertrauenswürdige Veröffentlichungsdomäne hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. 
    
    Um dieses Cmdlet ausführen zu können, benötigen Sie die URL für den Schlüssel, der im vorherigen Schritt angegeben wurde.
    
    Beispielsweise würden Sie unter Verwendung unseres URL-Schlüsselwerts aus dem vorherigen Schritt und der TPD-Datei „C:\contoso-tpd1.xml“ Folgendes ausführen:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```
    
    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

2.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 1 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen.  

3.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](https://msdn.microsoft.com/library/azure/dn629416.aspx), um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Verwenden Sie das Azure RMS-Cmdlet [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx), wenn Sie später bestätigen müssen, welchen Schlüssel Ihr Azure Information Protection-Mandantenschlüssel in Azure Key Vault verwendet.

Sie können jetzt mit [Schritt 3: Aktivieren Ihres Azure Information Protection-Mandanten](migrate-from-ad-rms-phase1.md#step-3-activate-your-azure-information-protection-tenant).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

