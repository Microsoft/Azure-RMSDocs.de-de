---
title: "Schritt 2&colon; Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln | Azure RMS"
description: "Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Rights Management sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Rights Management mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ada00b6f6298e7d359c73eb38dfdac169eacb708
ms.openlocfilehash: f4341d648b591922df93a4d2ba5e14151743fcdb


---

# Schritt 2: Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, Azure Rights Management*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Rights Management mit einem HSM-geschützten Mandantenschlüssel in Azure Key Vault durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) zurückkehren und eine andere Konfiguration auswählen.

Das Verfahren zum Importieren der AD RMS-Konfiguration in Azure RMS, um den von Ihnen in Azure Key Vault verwalteten Azure RMS-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in vier Phasen.

Sie müssen zuerst den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC) aus den AD RMS-Konfigurationsdaten extrahieren und an ein lokales Thales-HSM übertragen, als Nächstes Ihren HSM-Schlüssel paketieren und an Azure Key Vault übertragen, dann Azure RMS für den Zugriff auf Ihren Schlüsseltresor autorisieren und schließlich die Konfigurationsdaten importieren.

Da Ihr Azure RMS-Mandantenschlüssel von Azure Key Vault gespeichert und verwaltet wird, muss dieser Teil der Migration nicht nur in Azure Key RMS, sondern auch in Azure Key Vault verwaltet werden. Wenn Azure Key Vault für Ihre Organisation nicht von Ihnen, sondern von einem anderen Administrator verwaltet wird, müssen Sie sich mit diesem Administrator abstimmen und mit ihm zusammenarbeiten, um diese Prozeduren abzuschließen.

Stellen Sie zu Beginn sicher, dass Ihre Organisation über einen Schlüsseltresor verfügt, der in Azure Key Vault erstellt wurde, und dass er HSM-geschützte Schlüssel unterstützt. Auch wenn dies nicht erforderlich ist, empfehlen wir, einen dedizierten Schlüsseltresor für Azure RMS zu verwenden. Dieser Schlüsseltresor wird so konfiguriert, dass Azure RMS darauf zugreifen kann, sodass dieser Schlüsseltresor nur Azure RMS-Schlüssel enthält.


> [!TIP]
> Falls Sie die Konfigurationsschritte für Azure Key Vault ausführen möchten und noch nicht mit diesem Azure-Dienst vertraut sind, hilft Ihnen der Artikel [Erste Schritte mit Azure Key Vault ](https://azure.microsoft.com/documentation/articles/key-vault-get-started/) möglicherweise weiter. 


## Teil 1: Extrahieren des SLC-Schlüssels aus den Konfigurationsdaten und Importieren des Schlüssels in das lokale HSM

1.  Azure Key Vault-Administrator: Führen Sie die folgenden Schritte in der Azure Key Vault-Dokumentation im Abschnitt [Implementieren von „Bring Your Own Key“ (BYOK) für Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) durch:

    -   **Generieren und Übertragen Ihres Schlüssels an das Azure Key Vault-HSM**: [Schritt 1: Vorbereiten der Arbeitsstation mit Internetverbindung](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-1-prepare-your-internet-connected-workstation)

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: [Schritt 2: Vorbereiten der verbindungslosen Arbeitsstation](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-2-prepare-your-disconnected-workstation)

    Führen Sie die Schritte zum Generieren Ihres Mandantenschlüssels nicht aus, da Sie bereits über das Äquivalent in der XML-Datei mit den exportierten Konfigurationsdaten verfügen. Führen Sie stattdessen ein Tool zum Extrahieren dieses Schlüssels aus der Datei und zum Importieren des Schlüssels in das lokale HSM aus. Wenn Sie das Tool ausführen, werden zwei Dateien erstellt:

    - Eine neue Konfigurationsdatendatei ohne den Schlüssel, die dann auf Ihren Azure RMS-Mandanten importiert werden kann.

    - Eine PEM-Datei (Schlüsselcontainer) mit dem Schlüssel, die dann in Ihr lokales HSM importiert werden kann.

2. Azure RMS-Administrator oder Azure Key Vault-Administrator: Führen Sie auf der nicht verbundenen Arbeitsstation das TpdUtil-Tool aus dem [Azure RMS-Migrationstoolkit](https://go.microsoft.com/fwlink/?LinkId=524619) aus. Wenn das Tool beispielsweise auf Ihrem Laufwerk E: installiert ist, auf das Sie Ihre Konfigurationsdatendatei mit dem Namen „ContosoTPD.xml“ kopieren:

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

3. Fügen Sie zur gleichen nicht verbundenen Arbeitsstation Ihr Thales-HSM hinzu, und konfigurieren Sie es entsprechend der Thales-Dokumentation. Sie können nun Ihren Schlüssel anhand des folgenden Befehls in Ihr angefügtes Thales-HSM importieren. Ersetzen Sie dabei „ContosoTPD.pem“ durch Ihren eigenen Dateinamen:

        generatekey --import simple pemreadfile=e:\ContosoTPD.pem plainname=ContosoBYOK protect=module ident=contosobyok type=RSA

    > [!NOTE]
    >Wenn Sie über mehrere Dateien verfügen, wählen Sie die Datei aus, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS zum Schutz der Inhalte nach der Migration verwenden möchten.

    Dadurch wird eine Ausgabeanzeige generiert, die in etwa folgendermaßen aussieht:

    **key generation parameters:**

    **operation &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Durchzuführender Vorgang &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; import**

    **application &nbsp;&nbsp;&nbsp;&nbsp;Anwendung&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; simple**

    **verify &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sicherheit von Konfigurationsschlüssel prüfen&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yes**

    **type &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Schlüsseltyp &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RSA**

    **pemreadfile &nbsp;&nbsp; PEM-Datei mit RSA-Schlüssel &nbsp;&nbsp; e:\ContosoTPD.pem**

    **ident &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Schlüsselbezeichner &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contosobyok**

    **plainname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Schlüsselname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ContosoBYOK**

    **Key successfully imported.**

    **Path to key: C:\ProgramData\nCipher\Key Management Data\local\key_simple_contosobyok**

Diese Ausgabe bestätigt, dass der private Schlüssel zu Ihrem lokalen Thales-HSM-Gerät migriert wurde mit einer verschlüsselten Kopie, die in einem Schlüssel gespeichert ist (in unserem Beispiel „key_simple_contosobyok“). 

Nachdem Ihr SLC-Schlüssel extrahiert und auf Ihr lokales HSM importiert wurde, sind Sie bereit, den HSM-geschützten Schlüssel zu paketieren und an Azure Key Vault zu übertragen.

> [!IMPORTANT]
> Sorgen Sie im Anschluss an diesen Schritt dafür, dass diese PEM-Dateien sicher von der nicht verbundenen Arbeitsstation gelöscht werden, damit unbefugte Benutzer nicht darauf zugreifen können. Führen Sie beispielsweise „cipher /w:E“ aus, um alle Dateien sicher vom Laufwerk E: zu löschen.

## Teil 2: Paketieren und Übertragen des HSM-Schlüssels an Azure Key Vault

1.  Azure Key Vault-Administrator: Führen Sie die folgenden Schritte in der Azure Key Vault-Dokumentation im Abschnitt [Implementieren von „Bring Your Own Key“ (BYOK) für Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) durch:

    -   [Schritt 4: Vorbereiten des Schlüssels für die Übertragung](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-4-prepare-your-key-for-transfer)

    -   [Schritt 5: Übertragen des Schlüssels an Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-5-transfer-your-key-to-azure-key-vault)

    Führen Sie die Schritte zum Generieren des Schlüsselpaars nicht aus, da Sie bereits über den Schlüssel verfügen. Stattdessen führen Sie einen Befehl zum Übertragen dieses Schlüssels (in unserem Beispiel verwendet der KeyIdentifier-Parameter „contosobyok“) aus Ihrem lokalen HSM aus.

    Bevor Sie Ihren Schlüssel an Azure Key Vault übertragen, stellen Sie sicher, dass das Dienstprogramm „KeyTransferRemote.exe“ **Result: SUCCESS** (Ergebnis: ERFOLG) zurückgibt, wenn Sie eine Kopie Ihres Schlüssels mit eingeschränkten Berechtigungen erstellen (Schritt 4.1) und Ihren Schlüssel verschlüsseln (Schritt 4.3).

    Wenn der Schlüssel in Azure Key Vault hochgeladen wird, werden Ihnen die Schlüsseleigenschaften, einschließlich der Schlüssel-ID, angezeigt. Dies sieht etwa so aus: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Sie sollten sich diese URL notieren, da der Azure RMS-Administrator ihn benötigt, um Azure RMS mitzuteilen, dass dieser Schlüssel als Mandantenschlüssel verwendet werden soll.

    Nachdem Sie Ihren HSM-Schlüssel an Azure Key Vault übertragen haben, können Sie Ihre AD RMS-Konfigurationsdaten importieren.

## Teil 3: Importieren der Konfigurationsdaten in Azure RMS

1.  Azure RMS-Administrator: Kopieren Sie Ihre neuen Konfigurationsdatendateien (.xml), deren SLC-Schlüssel nach Ausführung des TpdUtil-Tools entfernt wird, auf die Arbeitsstation mit Internetverbindung und in die PowerShell-Sitzung.

2. Laden Sie die erste XML-Datei mithilfe des Cmdlets [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx) hoch. Wenn mehrere dieser Dateien vorliegen, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen verwendet haben, wählen Sie die Datei aus, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS zum Schutz von Inhalten nach der Migration verwenden möchten.

    Um dieses Cmdlet ausführen zu können, benötigen Sie die URL für den Schlüssel, der im vorherigen Schritt angegeben wurde.

    Beispielsweise würden Sie unter Verwendung unserer Schlüsselwert-URL aus dem vorherigen Schritt und der Konfigurationsdatendatei „C:\contoso_keyless.xml“ Folgendes ausführen:

    ```
    Import-AadrmTpd -TpdFile "C:\contoso_keyless.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```

    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor für die Konfigurationsdatendatei angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

    Wenn mehrere Konfigurationsdatendateien vorliegen, wiederholen Sie diesen Befehl für die restlichen Dateien. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen.



3.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Verwenden Sie das Azure RMS-Cmdlet [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx), wenn Sie später bestätigen müssen, welchen Schlüssel Ihr Azure RMS-Mandantenschlüssel in Azure Key Vault verwendet.


Sie können jetzt mit [Schritt 3: Aktivieren des RMS-Mandanten](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).






<!--HONumber=Aug16_HO4-->


