---
title: Migrieren softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln – AIP
description: Anweisungen, die Teil des Migrationspfads von AD RMS zu Azure Information Protection sind und nur gelten, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/11/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ee5ee97c6ff7a1bc3f817fa5ce6a086e7e691dd4
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60184143"
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>Schritt 2: Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Diese Anweisungen sind Teil des [Migrationspfads von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und gelten nur, wenn Ihr AD RMS-Schlüssel softwaregeschützt ist und Sie die Migration zu Azure Information Protection mit einem softwaregeschützten Mandantenschlüssel durchführen möchten. 

Falls dies nicht Ihr gewünschtes Konfigurationsszenario ist, sollten Sie zu [Schritt 4 zurückwechseln: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) zurückkehren und eine andere Konfiguration auswählen.

Wenden Sie das folgende Verfahren zum Importieren der AD RMS-Konfiguration in Azure Information Protection an, um den von Microsoft verwalteten Azure Information Protection-Mandantenschlüssel zu erhalten.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>So importieren Sie die Konfigurationsdaten in Azure Information Protection

1. Verwenden Sie auf einer Arbeitsstation mit Internetverbindung das Cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) verwenden, um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen.

    ```
    Connect-AadrmService
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des Azure Rights Management-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

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


