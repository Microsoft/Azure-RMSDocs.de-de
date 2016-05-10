---
# required metadata

title: Schritt 2: Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Schritt 2: Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln

Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel HSM-geschützt ist und Sie die Migration zu Azure Rights Management mit einem HSM-geschützten Mandantenschlüssel durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-to-azure-rms.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) zurückkehren und eine andere Konfiguration auswählen.

> [!NOTE]
> Für diese Anweisungen wird angenommen, dass Ihr AD RMS-Schlüssel modulgeschützt ist. Dies ist der Normalfall. Wenn Ihr AD RMS-Schlüssel mit OCS geschützt ist, wenden Sie sich an [AskIPTeam@microsoft.com](mailto: askipteam@microsoft.com?subject=AD%20RMS%20migration%20with%20OCS-protected%20key), bevor Sie diese Anweisungen verwenden.

Das Verfahren zum Importieren des HSM-Schlüssels und der AD RMS-Konfiguration in Azure RMS, um den von Ihnen verwalteten Azure RMS-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in zwei Phasen.

Sie müssen zuerst Ihren HSM-Schlüssel verpacken, damit er an Azure RMS übertragen werden kann, und ihn dann mit den Konfigurationsdaten importieren.

## Teil 1: Verpacken Ihres HSM-Schlüssel, damit er an Azure RMS übertragen werden kann

1.  Führen Sie die Schritte im Abschnitt [Implementierung von „Bring Your Own Key“ (BYOK)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md) mithilfe der Prozedur **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet** mit den folgenden Ausnahmen aus:

    -   Führen Sie nicht die Schritten zum **Generieren Ihres Mandantenschlüssels**aus, da Sie bereits über das Äquivalent aus Ihrer AD RMS-Bereitstellung verfügen. Sie müssen den vom AD RMS-Server verwendeten Schlüssel aus der Thales-Installation bestimmen und diesen Schlüssel während der Migration verwenden. Verschlüsselte Thales-Schlüsseldateien weisen meist einen Namen nach dem Muster **Schlüssel_(Schlüsselanwendungsname)_(Schlüsselbezeichner)** auf dem lokalen Server auf.

    -   Führen Sie nicht die Schritte zum **Übertragen Ihres Mandantenschlüssels an Azure RMS** aus, da hier der Befehl „Add-AadrmKey“ verwendet wird.  Stattdessen übertragen Sie Ihren vorbereiteten HSM-Schlüssel beim Hochladen der exportierten vertrauenswürdigen Veröffentlichungsdomäne mithilfe des Befehls „Import-AadrmTpd“.

2.  Stellen Sie auf der Arbeitsstation mit Internetzugang in der Windows PowerShell-Sitzung erneut eine Verbindung mit dem Azure RMS-Dienst her.

Nun, da Sie Ihren HSM-Schlüssel für Azure RMS vorbereitet haben, können Sie die HSM-Schlüsseldatei und die AD RMS-Konfigurationsdaten importieren.

## Teil 2: Importieren des HSM-Schlüssels und der Konfigurationsdaten in Azure RMS

1.  Laden Sie auf der mit dem Internet verbundenen Arbeitsstation und in der Windows PowerShell-Sitzung die erste exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Beispiel: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

2.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 1 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen.  Beispiel: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Sie können jetzt mit [Schritt 3: Aktivieren des RMS-Mandanten](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration) fortfahren.



<!--HONumber=Apr16_HO3-->

