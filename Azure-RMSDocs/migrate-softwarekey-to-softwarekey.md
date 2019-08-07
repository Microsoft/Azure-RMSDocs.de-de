---
title: Migrieren softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP
description: Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.subservice: migration
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 5bbf064cb019b663b62a779bf58322e0b23302e8
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68790536"
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>Schritt 2: Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 4 zurückwechseln: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) zurückkehren und eine andere Konfiguration auswählen.

Wenden Sie das folgende Verfahren zum Importieren der AD RMS-Konfiguration in Azure Information Protection an, um den von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel zu erhalten.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>So importieren Sie die Konfigurationsdaten in Azure Information Protection

1. Verwenden Sie auf einer Arbeitsstation mit Internet Verbindung das Cmdlet [Connect-aipservice](/powershell/module/aipservice/connect-aipservice) , um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen:

    ```
    Connect-AipService
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des Azure Rights Management-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

2. Verwenden Sie das [Import-aipservicetpd-](/powershell/module/aipservice/import-aipservicetpd) Cmdlet, um jede exportierte XML-Datei (Trusted Publishing Domain) hochzuladen. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben. 
    
    Zum Ausführen dieses Cmdlets benötigen Sie die Kennwörter, die Sie zuvor für die einzelnen Konfigurationsdatendatei angegeben haben. 
    
    Führen Sie z.B. zuerst folgenden Befehl aus, um ein Kennwort zu speichern:
    
        $TPD_Password = Read-Host -AsSecureString
    
    Geben Sie das Kennwort ein, das Sie für den Export der ersten Konfigurationsdatendatei angegeben haben. Führen Sie den folgenden Befehl aus, und bestätigen Sie, dass Sie diese Aktion ausführen möchten („E:\contosokey1.xml“ dient hier als Beispiel für diese Konfigurationsdatei):
    ```
    Import-AipServiceTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Verbose
    ```
    
3. Wenn Sie jede Datei hochgeladen haben, führen Sie [Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties) aus, um den importierten Schlüssel zu identifizieren, der mit dem derzeit aktiven SLC-Schlüssel in AD RMS übereinstimmt. Dieser Schlüssel wird zum aktiven Mandantenschlüssel für Ihren Azure Rights Management-Dienst.

4.  Verwenden Sie das [Disconnect-aipserviceservice-](/powershell/module/aipservice/disconnect-aipservice) Cmdlet, um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```
    Disconnect-AipServiceService
    ```

Sie können jetzt mit [Schritt 5 beginnen: Aktivieren Sie den Azure Rights Management-Dienst](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).


