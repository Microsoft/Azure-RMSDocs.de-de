---
title: Migrieren softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP
description: Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: eccaf8570704ee5adf13bf3f3d4426fecaa5e08e
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2018
ms.locfileid: "39370556"
---
# <a name="step-2-software-protected-key-to-hsm-protected-key-migration"></a>Schritt 2: Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 4 zurückwechseln: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) zurückkehren und eine andere Konfiguration auswählen.

Das Verfahren zum Importieren der AD RMS-Konfiguration in Azure Information Protection, um den von Ihnen verwalteten Azure Information Protection-Mandantenschlüssel (BYOK) in Azure Key Vault zu erhalten, gliedert sich in vier Phasen.

Sie müssen zuerst den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC) aus den AD RMS-Konfigurationsdaten extrahieren und an ein lokales Thales-HSM übertragen, als Nächstes ein Paket mit Ihrem HSM-Schlüssel erstellen und dieses an Azure Key Vault übertragen, dann den Azure Rights Management-Dienst von Azure Information Protection für den Zugriff auf Ihren Schlüsseltresor autorisieren und schließlich die Konfigurationsdaten importieren.

Da Ihr Azure Information Protection-Mandantenschlüssel von Azure Key Vault gespeichert und verwaltet wird, muss dieser Teil der Migration nicht nur in Azure Key Vault, sondern auch in Azure Information Protection verwaltet werden. Wenn Azure Key Vault für Ihre Organisation nicht von Ihnen, sondern von einem anderen Administrator verwaltet wird, müssen Sie sich mit diesem Administrator abstimmen und mit ihm zusammenarbeiten, um diese Prozeduren abzuschließen.

Stellen Sie zu Beginn sicher, dass Ihre Organisation über einen Schlüsseltresor verfügt, der in Azure Key Vault erstellt wurde, und dass er HSM-geschützte Schlüssel unterstützt. Auch wenn dies nicht erforderlich ist, empfehlen wir, einen dedizierten Schlüsseltresor für Azure Information Protection zu verwenden. Dieser Schlüsseltresor wird so konfiguriert, dass der Azure Rights Management-Dienst von Azure Information Protection darauf zugreifen kann, sodass dieser Schlüsseltresor nur Azure Information Protection-Schlüssel enthält.


> [!TIP]
> Wenn Sie die Konfigurationsschritte für Azure Key Vault ausführen möchten und noch nicht mit diesem Azure-Dienst vertraut sind, finden Sie nützliche Informationen im Artikel [Erste Schritte mit Azure Key Vault](/azure/key-vault/key-vault-get-started). 


## <a name="part-1-extract-your-slc-key-from-the-configuration-data-and-import-the-key-to-your-on-premises-hsm"></a>Teil 1: Extrahieren des SLC-Schlüssels aus den Konfigurationsdaten und Importieren des Schlüssels in das lokale HSM

1.  Azure Key Vault-Administrator: Führen Sie für jeden exportierten SLC-Schlüssel, den Sie in Azure Key Vault speichern möchten, die folgenden Schritte im Abschnitt [Implementieren von „Bring Your Own Key“ (BYOK) für Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys#implementing-bring-your-own-key-byok-for-azurekey-vault) der Azure Key Vault-Dokumentation durch:

    -   **Generieren und Übertragen Ihres Schlüssels an das Azure Key Vault-HSM**: [Schritt 1: Vorbereiten der Arbeitsstation mit Internetverbindung](/azure/key-vault-hsm-protected-keys/#step-1-prepare-your-internet-connected-workstation)

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: [Schritt 2: Vorbereiten der verbindungslosen Arbeitsstation](/azure/key-vault-hsm-protected-keys/#step-2-prepare-your-disconnected-workstation)

    Führen Sie die Schritte zum Generieren Ihres Mandantenschlüssels nicht aus, da Sie bereits über das Äquivalent in der XML-Datei mit den exportierten Konfigurationsdaten verfügen. Führen Sie stattdessen ein Tool zum Extrahieren dieses Schlüssels aus der Datei und zum Importieren des Schlüssels in das lokale HSM aus. Wenn Sie das Tool ausführen, werden zwei Dateien erstellt:

    - Eine neue Konfigurationsdatendatei ohne den Schlüssel, die dann auf Ihren Azure Information Protection-Mandanten importiert werden kann.

    - Eine PEM-Datei (Schlüsselcontainer) mit dem Schlüssel, die dann in Ihr lokales HSM importiert werden kann.

2. Azure Information Protection-Administrator oder Azure Key Vault-Administrator: Führen Sie auf der nicht verbundenen Arbeitsstation das TpdUtil-Tool aus dem [Azure RMS-Migrationstoolkit](https://go.microsoft.com/fwlink/?LinkId=524619) aus. Wenn das Tool beispielsweise auf Ihrem Laufwerk E: installiert ist, auf das Sie Ihre Konfigurationsdatendatei mit dem Namen „ContosoTPD.xml“ kopieren:

    ```
        E:\TpdUtil.exe /tpd:ContosoTPD.xml /otpd:ContosoTPD.xml /opem:ContosoTPD.pem
    ```

    Wenn mehrere RMS-Konfigurationsdatendateien vorliegen, führen Sie dieses Tool für die restlichen Dateien aus.

    Führen Sie „TpdUtil.exe“ ohne Parameter aus, um Hilfe für dieses Tool anzuzeigen, einschließlich einer Beschreibung, Verwendungshinweisen und Beispielen.

    Weitere Informationen zu diesem Befehl:

    - **/tpd**: Gibt den vollständigen Pfad und den Namen der exportierten AD RMS-Konfigurationsdatendatei an. Der vollständige Parametername lautet **TpdFilePath**.

    - **/otpd**: Gibt den Ausgabedateinamen für die Konfigurationsdatendatei ohne den Schlüssel an. Der vollständige Parametername lautet **OutPfxFile**. Wenn Sie diesen Parameter nicht angeben, erhält die Ausgabedatei standardmäßig den ursprünglichen Dateinamen mit dem Suffix **_keyless** und wird im aktuellen Ordner gespeichert.

    - **/opem**: Gibt den Ausgabedateinamen für die PEM-Datei an, die den extrahierten Schlüssel enthält. Der vollständige Parametername lautet **OutPemFile**. Wenn Sie diesen Parameter nicht angeben, erhält die Ausgabedatei standardmäßig den ursprünglichen Dateinamen mit dem Suffix **_key** und wird im aktuellen Ordner gespeichert.

    - Wenn Sie beim Ausführen dieses Befehls (unter Verwendung des vollständigen Parameternamens **TpdPassword** oder des kurzen Parameternamens **pwd**) das Kennwort nicht angeben, werden Sie zur Eingabe aufgefordert.

3. Fügen Sie zur gleichen nicht verbundenen Arbeitsstation Ihr Thales-HSM hinzu, und konfigurieren Sie es entsprechend der Thales-Dokumentation. Sie können nun Ihren Schlüssel mithilfe des folgenden Befehls in Ihr angeschlossenes Thales-HSM importieren. Ersetzen Sie dabei „ContosoTPD.pem“ durch Ihren eigenen Dateinamen:

        generatekey --import simple pemreadfile=e:\ContosoTPD.pem plainname=ContosoBYOK protect=module ident=contosobyok type=RSA

    > [!NOTE]
    >Wenn Sie über mehrere Dateien verfügen, wählen Sie die Datei aus, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS zum Schutz der Inhalte nach der Migration verwenden möchten.

    Dadurch wird eine Ausgabeanzeige generiert, die in etwa folgendermaßen aussieht:

    **key generation parameters:**

    **operation &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Durchzuführender Vorgang&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; import**

    **application &nbsp;&nbsp;&nbsp;&nbsp;Anwendung&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; simple**

    **verify &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sicherheit von Konfigurationsschlüssel prüfen key&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yes**

    **type &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Schlüsseltyp &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RSA**

    **pemreadfile &nbsp;&nbsp; PEM-Datei mit RSA-Schlüssel &nbsp;&nbsp; e:\ContosoTPD.pem**

    **ident &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Schlüsselbezeichner &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contosobyok**

    **plainname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Schlüsselname&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ContosoBYOK**

    **Key successfully imported.**

    **Path to key: C:\ProgramData\nCipher\Key Management Data\local\key_simple_contosobyok**

Diese Ausgabe bestätigt, dass der private Schlüssel zu Ihrem lokalen Thales-HSM-Gerät migriert wurde mit einer verschlüsselten Kopie, die in einem Schlüssel gespeichert ist (in unserem Beispiel „key_simple_contosobyok“). 

Nachdem Ihr SLC-Schlüssel extrahiert und auf Ihr lokales HSM importiert wurde, sind Sie bereit, den HSM-geschützten Schlüssel zu paketieren und an Azure Key Vault zu übertragen.

> [!IMPORTANT]
> Sorgen Sie im Anschluss an diesen Schritt dafür, dass diese PEM-Dateien sicher von der nicht verbundenen Arbeitsstation gelöscht werden, damit unbefugte Benutzer nicht darauf zugreifen können. Führen Sie beispielsweise „cipher /w:E“ aus, um alle Dateien sicher vom Laufwerk E: zu löschen.

## <a name="part-2-package-and-transfer-your-hsm-key-to-azure-key-vault"></a>Teil 2: Paketieren und Übertragen des HSM-Schlüssels an Azure Key Vault

Azure Key Vault-Administrator: Führen Sie für jeden exportierten SLC-Schlüssel, den Sie in Azure Key Vault speichern möchten, die folgenden Schritte des Abschnitts [Implementieren von „Bring Your Own Key“ (BYOK) für Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azurekey-vault) der Azure Key Vault-Dokumentation durch:

- [Schritt 4: Vorbereiten des Schlüssels für die Übertragung](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-4-prepare-your-key-for-transfer)

- [Schritt 5: Übertragen des Schlüssels an Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-5-transfer-your-key-to-azurekey-vault)

Führen Sie die Schritte zum Generieren des Schlüsselpaars nicht aus, da Sie bereits über den Schlüssel verfügen. Stattdessen führen Sie einen Befehl zum Übertragen dieses Schlüssels (in unserem Beispiel verwendet der KeyIdentifier-Parameter „contosobyok“) aus Ihrem lokalen HSM aus.

Bevor Sie Ihren Schlüssel an Azure Key Vault übertragen, stellen Sie sicher, dass das Dienstprogramm „KeyTransferRemote.exe“ **Result: SUCCESS** (Ergebnis: ERFOLG) zurückgibt, wenn Sie eine Kopie Ihres Schlüssels mit eingeschränkten Berechtigungen erstellen (Schritt 4.1) und Ihren Schlüssel verschlüsseln (Schritt 4.3).

Wenn der Schlüssel in Azure Key Vault hochgeladen wird, werden Ihnen die Schlüsseleigenschaften, einschließlich der Schlüssel-ID, angezeigt. Das sieht ungefähr folgendermaßen aus: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Sie sollten sich diese URL notieren, da der Azure Information Protection-Administrator ihn benötigt, um dem Azure Rights Management-Dienst von Azure Information Protection mitzuteilen, dass dieser Schlüssel als Mandantenschlüssel verwendet werden soll.

Verwenden Sie dann das Cmdlet [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy), um den Azure Rights Management-Dienstprinzipal für den Zugriff auf den Schlüsseltresor zu autorisieren. Die erforderlichen Berechtigungen sind „decrypt“, „encrypt“, „unwrapkey“, „wrapkey“, „verify“ und „sign“.

Wenn beispielsweise der Schlüsseltresor, den Sie für Azure Information Protection erstellt haben, „contosorms-byok-kv“ heißt und die Ressourcengruppe „contosorms-byok-rg“, führen Sie den folgenden Befehl aus:
    
    Set-AzureRmKeyVaultAccessPolicy -VaultName "contosorms-byok-kv" -ResourceGroupName "contosorms-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get

Nachdem Sie Ihren HSM-Schlüssel an Azure Key Vault übertragen haben, können Sie Ihre AD RMS-Konfigurationsdaten importieren.

## <a name="part-3-import-the-configuration-data-to-azure-information-protection"></a>Teil 3: Importieren der Konfigurationsdaten in Azure Information Protection

1. Azure Information Protection-Administrator: Kopieren Sie Ihre neuen Konfigurationsdatendateien (.xml), deren SLC-Schlüssel nach Ausführung des TpdUtil-Tools entfernt wird, auf der Arbeitsstation mit Internetverbindung in die PowerShell-Sitzung.

2. Laden Sie die einzelnen XML-Dateien mithilfe des Cmdlets [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) hoch. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben.

    Um dieses Cmdlet auszuführen, benötigen Sie das Kennwort, das Sie zuvor für die Konfigurationsdatendatei angegeben haben, sowie die URL für den Schlüssel, der im vorherigen Schlüssel identifiziert wurde.

    Führen Sie den folgenden Befehl aus, um das Kennwort zu speichern. Als Beispiel dienen hier die Konfigurationsdatendatei „C:\contoso_keyless.xml“ und der Wert für die Schlüssel-URL aus dem vorherigen Schritt:
    
    ```
    $TPD_Password = Read-Host -AsSecureString
    ```
    
   Geben Sie das Kennwort ein, das Sie für den Export der Konfigurationsdatendatei angegeben haben. Führen Sie dann den folgenden Befehl aus, und bestätigen Sie, dass Sie diese Aktion ausführen möchten:

    ```
    Import-AadrmTpd -TpdFile "C:\contoso_keyless.xml" -ProtectionPassword $TPD_Password –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Verbose
    ```

    Im Rahmen dieses Importvorgangs wird der SLC-Schlüssel importiert und automatisch als archiviert festgelegt.

3. Wenn Sie alle Dateien hochgeladen haben, führen Sie [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) aus, um anzugeben, welcher importierte Schlüssel mit dem derzeit aktiven SLC-Schlüssel in Ihrem AD RMS-Cluster übereinstimmt.

4. Verwenden Sie das Cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice), um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Verwenden Sie das Azure RMS-Cmdlet [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys), wenn Sie später bestätigen müssen, welchen Schlüssel Ihr Azure Information Protection-Mandantenschlüssel in Azure Key Vault verwendet.


Sie können jetzt mit [Schritt 5 beginnen: Aktivieren Sie den Azure Rights Management-Dienst](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).


