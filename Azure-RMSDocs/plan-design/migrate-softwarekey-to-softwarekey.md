---
title: "Migrieren softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP"
description: "Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 60370cc34184b28f5cdecf6ad51f9ba58dd4816a
ms.sourcegitcommit: 77b0936bea2700eb12b580e5738e077d447d5686
translationtype: HT
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>Schritt 2: Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 4 zurückwechseln: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) zurückkehren und eine andere Konfiguration auswählen.

Wenden Sie das folgende Verfahren zum Importieren der AD RMS-Konfiguration in Azure Information Protection an, um den von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel zu erhalten.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>So importieren Sie die Konfigurationsdaten in Azure Information Protection

1. Verwenden Sie auf einer Arbeitsstation mit Internetverbindung das Cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) verwenden, um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen.

    ```
    Connect-AadrmService
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

2. Laden Sie mit dem [Import-AadrmTdp](/powershell/aadrm/vlatest/import-aadrmtpd)-Cmdlet die erste exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Wenn mehrere dieser XML-Dateien vorliegen, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen verwendet haben, wählen Sie die Datei mit der exportierten vertrauenswürdigen Domäne aus, die Sie nach der Migration in Azure Information Protection zum Schutz von Inhalten verwenden möchten. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword <secure string> -Active $True -Verbose
    ```
    Sie können entweder[ConvertTo-SecureString -AsPlaintext](https://technet.microsoft.com/library/hh849818.aspx) oder [Read-Host](https://technet.microsoft.com/library/hh849945.aspx) verwenden, um das Kennwort als sichere Zeichenfolge festzulegen. Wenn Sie „ConvertTo-SecureString“ verwenden und das Kennwort Sonderzeichen enthält, geben Sie das Kennwort in einfachen Anführungszeichen ein, oder fügen Sie Escapezeichen für die Sonderzeichen ein.
    
    Beispiel: Führen Sie zunächst **$TPD_Password = Read-Host -AsSecureString** aus, und geben Sie dann das zuvor festgelegte Kennwort ein. Führen Sie anschließend **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Active $true -Verbose** aus. Bestätigen Sie bei Aufforderung, dass Sie die Aktion ausführen möchten.
    
3.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 3 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen. Beispiel: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword $TPD_Password -Active $false -Verbose**

4.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice), um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```


Sie können jetzt mit [Schritt 5 beginnen: Aktivieren Ihres Azure Information Protection-Mandanten](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

