---
# required metadata

title: Schritt 2&colon; Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Schritt 2: Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln

*Gilt für: Active Directory Rights Management Services, Azure Rights Management*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Rights Management mit einem HSM-geschützten Mandantenschlüssel durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-to-azure-rms.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) zurückkehren und eine andere Konfiguration auswählen.

Das Verfahren zum Importieren der AD RMS-Konfiguration in Azure RMS, um den von Ihnen verwalteten Azure RMS-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in drei Phasen.

Sie müssen zuerst den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC) aus den Konfigurationsdaten extrahieren und an ein lokales Thales-HSM übertragen, dann Ihren HSM-Schlüssel verpacken und an Azure RMS übertragen und schließlich die Konfigurationsdaten importieren.

## Teil 1: Extrahieren des SLC aus den Konfigurationsdaten und Importieren des Schlüssels in das lokale HSM

1.  Verwenden Sie die folgenden Schritte im Abschnitt [Implementierung von „Bring Your Own Key“ (BYOK)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) im Thema [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md):

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Vorbereiten Ihrer Arbeitsstation mit Internetverbindung**

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Vorbereiten Ihrer nicht verbundenen Arbeitsstation**

    Führen Sie die Schritte zum Generieren Ihres Mandantenschlüssels nicht aus, da Sie bereits über das Äquivalent in der XML-Datei mit den exportierten Konfigurationsdaten verfügen. Führen Sie stattdessen einen Befehl zum Extrahieren dieses Schlüssels aus der Datei und Importieren des Schlüssels in das lokale HSM aus.

2.  Führen Sie auf der nicht verbundenen Arbeitsstation den folgenden Befehl aus:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Für Nordamerika z.B.: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Zusätzliche Informationen:

    -   Der Parameter "ImportRmsCentrallyManagedKey" gibt an, dass es sich um den Vorgang zum Importieren des SLC-Schlüssels handelt.

    -   Wenn Sie das Kennwort im Befehl nicht angeben, werden Sie zur Angabe aufgefordert.

    -   Der Parameter "KeyIdentifier" ist für einen Schlüsselanzeigenamen da, der den Schlüsseldateinamen erstellt. Sie dürfen nur kleingeschriebene ASCII-Zeichen verwenden.

    -   Der Parameter "ExchangeKeyPackage" gibt ein regionsspezifisches KEK-Paket (Paket mit Schlüsselaustauschschlüssel) an, dessen Name mit BYOK-KEK-pkg- beginnt.

    -   Der Parameter "NewSecurityWorldPackage" gibt ein regionsspezifisches Security World-Paket an, dessen Name mit BYOK-SecurityWorld-pkg- beginnt.

    Mit diesem Befehl ergibt sich Folgendes:

    -   Eine HSM-Schlüsseldatei: %NFAST_KMDATA%\local\key_mscapi_&lt;SchlüsselID&gt;

    -   Eine RMS-Konfigurationsdatendatei mit entferntem SLC: %NFAST_KMDATA%\local\no_key_tpd_&gt;SchlüsselID&lt;.xml

3.  Wenn mehrere RMS-Konfigurationsdatendateien vorliegen, wiederholen Sie Schritt 2 für die restlichen Dateien.

Nachdem Ihr SLC nun extrahiert wurde, sodass Sie über einen HSM-basierten Schlüssel verfügen, können Sie ihn verpacken und an Azure RMS übertragen.

## Teil 2: Verpacken des HSM-Schlüssels und Übertragen des Schlüssels an Azure RMS

1.  Verwenden Sie die folgenden Schritte im Abschnitt [Implementierung von „Bring Your Own Key“ (BYOK)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) im Thema [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md):

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Vorbereiten Ihres Mandantenschlüssels für die Übertragung**

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Übertragen Ihres Mandantenschlüssels an Azure RMS**

Nachdem Sie nun Ihren HSM-Schlüssel an Azure RMS übertragen haben, können Sie Ihre AD RMS-Konfigurationsdaten importieren, die nur einen Zeiger auf den gerade übertragenen Mandantenschlüssel enthalten.

## Teil 3: Importieren der Konfigurationsdaten in Azure RMS

1.  Kopieren Sie auf der Arbeitsstation mit Internetverbindung und in der Windows PowerShell-Sitzung die RMS-Konfigurationsdateien mit entferntem SLC (aus der nicht verbundenen Arbeitsstation, %NFAST_KMDATA%\local\no_key_tpd_&lt;SchlüsselID&gt;.xml).

2.  Laden Sie die erste Datei hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Beispiel: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml –ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok –Active $true -Verbose**

    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

3.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 2 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen. Beispiel: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Sie können jetzt mit [Schritt 3: Aktivieren Sie Ihren RMS-Mandanten](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).




<!--HONumber=Apr16_HO4-->


