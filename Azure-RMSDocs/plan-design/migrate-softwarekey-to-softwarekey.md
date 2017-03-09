---
title: "Migrieren softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP"
description: "Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 707d31d8cd2f012a4223a3654b2c1bbcefa2d1a8
ms.lasthandoff: 02/24/2017


---


# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>Schritt 2: Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 2: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) zurückkehren und eine andere Konfiguration auswählen.

Wenden Sie das folgende Verfahren zum Importieren der AD RMS-Konfiguration in Azure Information Protection an, um den von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel zu erhalten.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>So importieren Sie die Konfigurationsdaten in Azure Information Protection

1.  Laden Sie auf einer Arbeitsstation mit Internetverbindung das Windows PowerShell-Modul für Azure Rights Management (Mindestversion 2.5.0.0) herunter, in dem das Cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) enthalten ist, und installieren Sie es. Der Azure Rights Management-Dienst (Azure RMS) stellt den Schutz von Daten für Azure Information Protection bereit.

    > [!TIP]
    > Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm -ListAvailable).Version`

    Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

2.  Starten Sie Windows PowerShell mit der Option **Als Administrator ausführen** , und stellen Sie mit dem Cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) eine Verbindung mit dem Azure RMS-Dienst her:

    ```
    Connect-AadrmService
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

3.  Laden Sie mit dem [Import-AadrmTdp](http://msdn.microsoft.com/library/azure/dn857523.aspx)-Cmdlet die erste exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Wenn mehrere dieser XML-Dateien vorliegen, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen verwendet haben, wählen Sie die Datei mit der exportierten vertrauenswürdigen Domäne aus, die Sie nach der Migration in Azure Information Protection zum Schutz von Inhalten verwenden möchten. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword <secure string> -Active $True -Verbose
    ```
    Sie können entweder[ConvertTo-SecureString -AsPlaintext](https://technet.microsoft.com/library/hh849818.aspx) oder [Read-Host](https://technet.microsoft.com/library/hh849945.aspx) verwenden, um das Kennwort als sichere Zeichenfolge festzulegen. Wenn Sie „ConvertTo-SecureString“ verwenden und das Kennwort Sonderzeichen enthält, geben Sie das Kennwort in einfachen Anführungszeichen ein, oder fügen Sie Escapezeichen für die Sonderzeichen ein.
    
    Beispiel: Führen Sie zunächst **$TPD_Password = Read-Host -AsSecureString** aus, und geben Sie dann das zuvor festgelegte Kennwort ein. Führen Sie anschließend **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Active $true -Verbose** aus. Bestätigen Sie bei Aufforderung, dass Sie die Aktion ausführen möchten.
    
4.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 3 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben. Legen Sie für diese Dateien aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen. Beispiel: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword $TPD_Password -Active $false -Verbose**

5.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx), um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```


Sie können jetzt mit [Schritt 3: Aktivieren Ihres Azure Information Protection-Mandanten](migrate-from-ad-rms-phase1.md#step-3-activate-your-azure-information-protection-tenant).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


