---
title: Migrieren HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP
description: Anweisungen, die Teil der Migrationspfads von AD RMS zu Azure Information Protection und gilt nur, wenn Ihr AD RMS-Schlüssel HSM-geschützten ist und Sie sind möchten mit einem HSM-geschützten mandantenschlüssel in Azure Key Vault zu Azure Information Protection migrieren.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 05/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 11391088aa0e2a084198cdb0aa73eeb6be0795d0
ms.sourcegitcommit: 3e948723644f19c935bc7111dec1cc54a1ff0231
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65780855"
---
# <a name="step-2-hsm-protected-key-to-hsm-protected-key-migration"></a>Schritt 2: Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel HSM-geschützt ist und Sie die Migration zu Azure Information Protection mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 4 zurückwechseln: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) zurückkehren und eine andere Konfiguration auswählen.

> [!NOTE]
> Für diese Anweisungen wird angenommen, dass Ihr AD RMS-Schlüssel modulgeschützt ist. Dies ist der am häufigsten vorkommende Fall. 

Das Verfahren zum Importieren des HSM-Schlüssels und der AD RMS-Konfiguration in Azure Information Protection, um den von Ihnen verwalteten Azure Information Protection-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in zwei Phasen.

Da Ihr Azure Information Protection-Mandantenschlüssel von Azure Key Vault gespeichert und verwaltet wird, muss dieser Teil der Migration nicht nur in Azure Key Vault, sondern auch in Azure Information Protection verwaltet werden. Wenn Azure Key Vault für Ihre Organisation nicht von Ihnen, sondern von einem anderen Administrator verwaltet wird, müssen Sie sich mit diesem Administrator abstimmen und mit ihm zusammenarbeiten, um diese Prozeduren abzuschließen.

Stellen Sie zu Beginn sicher, dass Ihre Organisation über einen Schlüsseltresor verfügt, der in Azure Key Vault erstellt wurde, und dass er HSM-geschützte Schlüssel unterstützt. Auch wenn dies nicht erforderlich ist, empfehlen wir, einen dedizierten Schlüsseltresor für Azure Information Protection zu verwenden. Dieser Schlüsseltresor wird so konfiguriert, dass der Azure Rights Management-Dienst darauf zugreifen kann, sodass dieser Schlüsseltresor nur Azure Information Protection-Schlüssel enthält.


> [!TIP]
> Wenn Sie die Konfigurationsschritte für Azure Key Vault ausführen möchten und noch nicht mit diesem Azure-Dienst vertraut sind, finden Sie nützliche Informationen im Artikel [Erste Schritte mit Azure Key Vault](/azure/key-vault/key-vault-get-started). 


## <a name="part-1-transfer-your-hsm-key-to-azure-key-vault"></a>Teil 1: Übertragen Ihres HSM-Schlüssels in Azure Key Vault

Diese Verfahren werden vom Administrator für Azure Key Vault durchgeführt.

1. Führen Sie für jeden exportierten SLC-Schlüssel, den Sie in Azure Key Vault speichern möchten, die Schritte im Abschnitt [Implementieren von „Bring Your Own Key“ (BYOK) für Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys#implementing-bring-your-own-key-byok-for-azure-key-vault) der Azure Key Vault-Dokumentation durch – mit folgender Ausnahme:

   - Führen Sie nicht die Schritte zum **Generieren Ihres Mandantenschlüssels** aus, da Sie bereits über das Äquivalent aus Ihrer AD RMS-Bereitstellung verfügen. Klicken Sie stattdessen identifizieren Sie den Schlüssel von AD RMS-Server über die unterstützende nCipher-Installation verwendet, und verwenden Sie diesen Schlüssel während der Migrations. Schlüsseldateien nCipher verschlüsselt werden in der Regel mit dem Namen **Schlüssel<*Schlüsselanwendungsname*><*KeyIdentifier*>** lokal auf dem Server.

     Wenn der Schlüssel in Azure Key Vault hochgeladen wird, werden Ihnen die Schlüsseleigenschaften, einschließlich der Schlüssel-ID, angezeigt. Das sieht ungefähr folgendermaßen aus: https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Notieren Sie sich diese URL, da der Azure Information Protection-Administrator sie benötigt, um dem Azure Rights Management-Dienst mitzuteilen, dass dieser Schlüssel als Mandantenschlüssel verwendet werden soll.

2. Verwenden Sie auf der Arbeitsstation mit Internetverbindung in einer PowerShell-Sitzung die [Set-AzKeyVaultAccessPolicy](/powershell/module/az.keyvault/set-azkeyvaultaccesspolicy) -Cmdlet zum Autorisieren des dienstprinzipals für Azure Rights Management auf den schlüsseltresor zugreifen, die die Azure-Informationen gespeichert werden Protection-mandantenschlüssel. Die erforderlichen Berechtigungen sind „decrypt“, „encrypt“, „unwrapkey“, „wrapkey“, „verify“ und „sign“.
    
    Wenn beispielsweise der Schlüsseltresor, den Sie für Azure Information Protection erstellt haben, „contoso-byok-ky“ heißt und die Ressourcengruppe „contoso-byok-rg“, führen Sie den folgenden Befehl aus:
    
        Set-AzKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,sign,get


Jetzt haben Sie Ihren HSM-Schlüssel in Azure Key Vault für den Azure Rights Management-Dienst von Azure Information Protection vorbereitet und können die AD RMS-Konfigurationsdaten importieren.

## <a name="part-2-import-the-configuration-data-to-azure-information-protection"></a>Teil 2: Importieren der Konfigurationsdaten in Azure Information Protection

Diese Verfahren werden vom Administrator für Azure Information Protection durchgeführt.

1. Verwenden Sie während einer PowerShell-Sitzung an einer mit dem Internet verbundenen Arbeitsstation das Cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice), um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen.
    
    Laden Sie dann mit dem Cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) jede exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben.
    
    Um dieses Cmdlet auszuführen, benötigen Sie die Kennwörter, die Sie zuvor für die jeweiligen Konfigurationsdatendateien angegeben haben, sowie die URL für den Schlüssel, der im vorherigen Schritt identifiziert wurde.
    
    Führen Sie den folgenden Befehl aus, um das Kennwort zu speichern. Als Beispiel dienen hier die Konfigurationsdatendatei „C:\contoso-tpd1.xml“ und der Wert für die Schlüssel-URL aus dem vorherigen Schritt:
    
    ```
    $TPD_Password = Read-Host -AsSecureString
    ```
    
    Geben Sie das Kennwort ein, das Sie für den Export der Konfigurationsdatendatei angegeben haben. Führen Sie dann den folgenden Befehl aus, und bestätigen Sie, dass Sie diese Aktion ausführen möchten:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword $TPD_Password –KeyVaultKeyUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Verbose
    ```
    
    Im Rahmen dieses Importvorgangs wird der SLC-Schlüssel importiert und automatisch als archiviert festgelegt.

2.  Wenn Sie alle Dateien hochgeladen haben, führen Sie [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) aus, um anzugeben, welcher importierte Schlüssel mit dem derzeit aktiven SLC-Schlüssel in Ihrem AD RMS-Cluster übereinstimmt. Dieser Schlüssel wird zum aktiven Mandantenschlüssel für Ihren Azure Rights Management-Dienst.

3.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice), um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Verwenden Sie das Azure RMS-Cmdlet [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys), wenn Sie später bestätigen müssen, welchen Schlüssel Ihr Azure Information Protection-Mandantenschlüssel in Azure Key Vault verwendet.

Sie können jetzt mit [Schritt 5 beginnen: Aktivieren Sie den Azure Rights Management-Dienst](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).


