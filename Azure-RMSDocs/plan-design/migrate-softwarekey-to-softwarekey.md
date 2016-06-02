---
# required metadata

title: Schritt 2&colon; Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Schritt 2: Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln

*Gilt für: Active Directory Rights Management Services, Azure Rights Management*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Rights Management mit einem softwaregeschützten Mandantenschlüssel durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-to-azure-rms.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) zurückkehren und eine andere Konfiguration auswählen.

Verwenden Sie das folgende Verfahren zum Importieren der AD RMS-Konfiguration in Azure RMS, um Ihren Azure RMS-Mandantenschlüssel zu erhalten, der von Microsoft verwaltet wird.

## So importieren Sie die Konfigurationsdaten in Azure RMS

1.  Laden Sie auf einer Arbeitsstation mit Internetverbindung das Windows PowerShell-Modul für Azure RMS (Mindestversion 2.1.0.0) herunter, in dem das [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)-Cmdlet enthalten ist, und installieren Sie es.

    > [!TIP]
    > Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm -ListAvailable).Version`

    Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md)..

2.  Starten Sie Windows PowerShell mit der Option **Als Administrator ausführen** , und stellen Sie mit dem Cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) eine Verbindung mit dem Azure RMS-Dienst her:

    ```
    Connect-AadrmService
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

3.  Laden Sie mit dem [Import-AadrmTdp](http://msdn.microsoft.com/library/azure/dn857523.aspx)-Cmdlet die erste exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Beispiel: **Import-AadrmTpd -TpdFile E:\contosokey1.xml –ProtectionPassword –Active $true -Verbose**

    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

4.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 3 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen. Beispiel: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Sie können jetzt mit [Schritt 3: Aktivieren Sie Ihren RMS-Mandanten](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).



<!--HONumber=Apr16_HO4-->


