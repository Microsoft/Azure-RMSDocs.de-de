---
title: Migrieren softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP
description: Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.subservice: migration
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: a9ef31330b5bc0039ad01f76134ebb5075edd1e6
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97383736"
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>Schritt 2: Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln

>**Gilt für*: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten. 

Wenn dies nicht Ihr ausgewähltes Konfigurations Szenario ist, fahren Sie mit [Schritt 4 fort. Exportieren Sie Konfigurationsdaten aus AD RMS, und importieren Sie Sie in Azure RMS,](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) und wählen Sie eine andere Konfiguration aus.

Wenden Sie das folgende Verfahren zum Importieren der AD RMS-Konfiguration in Azure Information Protection an, um den von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel zu erhalten.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>So importieren Sie die Konfigurationsdaten in Azure Information Protection

1. Verwenden Sie auf einer Arbeitsstation mit Internetverbindung das Cmdlet [Connect-aipservice](/powershell/module/aipservice/connect-aipservice) , um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen:

    ```PowerShell
    Connect-AipService
    ```
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des Azure Rights Management-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

2. Verwenden Sie das [Import-aipservicetpd-](/powershell/module/aipservice/import-aipservicetpd) Cmdlet, um jede exportierte XML-Datei (Trusted Publishing Domain) hochzuladen. Sie müssen beispielsweise mindestens eine weitere Datei importieren, wenn Sie Ihren AD RMS-Cluster auf den Kryptografiemodus 2 aktualisiert haben. 
    
    Zum Ausführen dieses Cmdlets benötigen Sie die Kennwörter, die Sie zuvor für die einzelnen Konfigurationsdatendatei angegeben haben. 
    
    Führen Sie z.B. zuerst folgenden Befehl aus, um ein Kennwort zu speichern:
    
    ```PowerShell
    $TPD_Password = Read-Host -AsSecureString
    ```

    Geben Sie das Kennwort ein, das Sie für den Export der ersten Konfigurationsdatendatei angegeben haben. Führen Sie den folgenden Befehl aus, und bestätigen Sie, dass Sie diese Aktion ausführen möchten („E:\contosokey1.xml“ dient hier als Beispiel für diese Konfigurationsdatei):

    ```PowerShell
    Import-AipServiceTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Verbose
    ```
    
3. Wenn Sie jede Datei hochgeladen haben, führen Sie [Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties) aus, um den importierten Schlüssel zu identifizieren, der mit dem derzeit aktiven SLC-Schlüssel in AD RMS übereinstimmt. Dieser Schlüssel wird zum aktiven Mandantenschlüssel für Ihren Azure Rights Management-Dienst.

4.  Verwenden Sie das [Disconnect-aipserviceservice-](/powershell/module/aipservice/disconnect-aipservice) Cmdlet, um die Verbindung mit dem Azure Rights Management-Dienst zu trennen:

    ```PowerShell
    Disconnect-AipServiceService
    ```

Nun können Sie mit [Schritt 5 fortfahren. Aktivieren Sie den Azure Rights Management-Dienst](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).


