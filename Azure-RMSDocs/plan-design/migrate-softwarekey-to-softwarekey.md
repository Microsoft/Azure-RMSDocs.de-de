---
title: "Migrieren softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP"
description: "Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bc87379406d45f3fb39cae214839e127f71a366f
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
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

2. Laden Sie mit dem [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd)-Cmdlet jede exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben. 
    
    Zum Ausführen dieses Cmdlets benötigen Sie die Kennwörter, die Sie zuvor für die einzelnen Konfigurationsdatendatei angegeben haben. 
    
    Führen Sie z.B. zuerst folgenden Befehl aus, um ein Kennwort zu speichern:
    
        $TPD_Password = Read-Host -AsSecureString
    
    Geben Sie das Kennwort ein, das Sie für den Export der ersten Konfigurationsdatendatei angegeben haben. Führen Sie den folgenden Befehl aus, und bestätigen Sie, dass Sie diese Aktion ausführen möchten („E:\contosokey1.xml“ dient hier als Beispiel für diese Konfigurationsdatei):
    ```
    Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Verbose
    ```
    
3. Wenn Sie alle Dateien hochgeladen haben, führen Sie [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) aus, um den importierten Schlüssel zu identifizieren, der mit dem derzeit aktiven SLC-Schlüssel in AD RMS übereinstimmt. Dieser Schlüssel wird zum aktiven Mandantenschlüssel für Ihren Azure Rights Management-Dienst.

4.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice), um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Sie können jetzt mit [Schritt 5 beginnen: Aktivieren Sie den Azure Rights Management-Dienst](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

