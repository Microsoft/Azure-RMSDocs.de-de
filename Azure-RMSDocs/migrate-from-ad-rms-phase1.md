---
title: Migrieren von AD RMS-Azure Information Protection – Phase 1
description: Phase 1 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 1 bis 3 der Migration von AD RMS zu Azure Information Protection ab.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/26/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: d954d3ee-3c48-4241-aecf-01f4c75fa62c
ms.subservice: migration
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: ee761ef8ae12d638df7e05c83a5ed5d635d25b9b
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384365"
---
# <a name="migration-phase-1---preparation"></a>Migrationsphase 1: Vorbereitung

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Verwenden Sie die folgenden Informationen für Phase 1 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren behandeln die Schritte 1 bis 3 von [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und bereiten Ihre Umgebung für die Migration vor, ohne Ihre Benutzer zu beeinflussen.

## <a name="step-1-install-the-aipservice-powershell-module-and-identify-your-tenant-url"></a>Schritt 1: Installieren des aipservice-PowerShell-Moduls und identifizieren ihrer Mandanten-URL

Installieren Sie das **aipservice** -Modul, damit Sie den Dienst konfigurieren und verwalten können, der den Datenschutz für Azure Information Protection bereitstellt.

Anweisungen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](./install-powershell.md).

Um einige der Migrations Anweisungen abzuschließen, müssen Sie die URL des Azure-Rights Management Dienstanbieter für Ihren Mandanten kennen, damit Sie Sie ersetzen können, wenn Verweise auf angezeigt werden *\<Your Tenant URL\>* . 

Die Azure Rights Management-Dienst-URL weist das folgende Format auf: **{GUID}.rms.[Region].aadrm.com**. Beispiel: **5c6bb73b-1038-4eec-863d-49bded473437.RMS.na.aadrm.com**

### <a name="to-identify-your-azure-rights-management-service-url"></a>So identifizieren Sie Ihre Azure Rights Management-Dienst-URL

1. Stellen Sie eine Verbindung mit dem Azure Rights Management-Dienst her, und geben Sie die Anmeldeinformationen für den globalen Administrator Ihres Mandanten an, wenn Sie dazu aufgefordert werden:

    ```PowerShell
    Connect-AipService
    ```

2. Abrufen der Konfiguration Ihres Mandanten:

    ```PowerShell
    Get-AipServiceConfiguration
    ```

3. Kopieren Sie den Wert für die **LicensingIntranetDistributionPointUrl**, und entfernen Sie `/_wmcs\licensing` aus dieser Zeichenfolge.

    Was zurück bleibt, ist Ihre Azure Rights Management-Dienst-URL für Ihren Azure Rights Management-Mandanten. Dieser Wert wird auf mit *Ihre Mandanten-URL* in den folgenden Migrationsanweisungen abgekürzt.

    Sie können überprüfen, ob Sie den korrekten Wert besitzen, indem Sie den folgenden PowerShell-Befehl ausführen.

    ```PowerShell
    (Get-AipServiceConfiguration).LicensingIntranetDistributionPointUrl -match "https:\/\/[0-9A-Za-z\.-]*" | Out-Null; $matches[0]
    ```

## <a name="step-2-prepare-for-client-migration"></a>Schritt 2: Vorbereitung für die Clientmigration

Für die meisten Migrationen ist es nicht sehr praktisch, alle Clients auf einmal zu migrieren, also werden Sie diese eher in Batches migrieren. 

Das bedeutet, dass einige Clients über einen Zeitraum Azure Information Protection und einige noch immer AD RMS verwenden. Um jeweils zuvor migrierte und migrierte Benutzer zu unterstützen, verwenden Sie Onboarding-Steuerelemente, und stellen Sie ein Skript vor der Migration bereit. 

> [!NOTE]
> Dieser Schritt ist während der Migration erforderlich, damit Benutzer, die noch nicht migriert haben, Inhalt verwenden, der durch migrierte Benutzer geschützt wurde, die jetzt Azure Rights Management verwenden.
> 

**So bereiten Sie die Client Migration vor**

1. Erstellen Sie eine Gruppe, z.B. mit dem Namen **AIPMigrated**. Diese Gruppe kann in Active Directory erstellt und mit der Cloud synchronisiert werden, oder Sie kann in Microsoft 365 oder Azure Active Directory erstellt werden. 

    Weisen Sie zu diesem Zeitpunkt keinen Benutzer dieser Gruppe zu. Sie fügen Benutzer erst später hinzu, wenn sie migriert werden.

1. Notieren Sie sich die Objekt-ID dieser Gruppe, indem Sie eine der folgenden Methoden verwenden:

    - **Verwenden Sie Azure AD PowerShell.** Verwenden Sie z. b. für Version 1,0 des Moduls den Befehl [Get-msolgroup](/powershell/msonline/v1/Get-MsolGroup) . 
    - **Kopieren Sie die Objekt-ID** der Gruppe aus dem Azure-Portal.

1. Konfigurieren Sie diese Gruppe für Onboarding-Steuerelemente, um nur Benutzern in dieser Gruppe zu erlauben, Azure Rights Management zu verwenden, um Inhalte zu schützen. 

    Stellen Sie zu diesem Zweck in einer PowerShell-Sitzung eine Verbindung mit dem Azure Rights Management-Dienst her. Geben Sie bei entsprechender Aufforderung Ihre globalen Administrator Anmelde Informationen an:

    ```PowerShell
    Connect-AipService
    ```

    Konfigurieren Sie diese Gruppe für Onboarding-Steuerelemente, indem Sie die Gruppen Objekt-ID für den in diesem Beispiel ersetzen. Geben Sie bei entsprechender Aufforderung **Y** zur Bestätigung ein.

    ```PowerShell
    Set-AipServiceOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501" -Scope WindowsApp
    ```

1. Laden Sie die [**Migration-Scripts.zip**](https://go.microsoft.com/fwlink/?LinkId=524619) -Datei herunter.

1. Extrahieren Sie die Dateien, und befolgen Sie die Anweisungen in **Prepare-Client. cmd**, damit Sie den Servernamen für Ihre AD RMS-Cluster-extranetlizenzierungs-URL enthält. Gehen Sie folgendermaßen vor, um diesen Namen zu finden:

    1. Klicken Sie in der Active Directory Rights Management Services-Konsole auf den Clusternamen. 

    1. Kopieren Sie unter **Clusterdetails** den Servernamen aus dem Wert **Lizenzierung** aus dem Abschnitt Extranetcluster-URLs. Beispiel: **rmscluster.contoso.com**.

    > [!IMPORTANT]
    > Diese Anleitung behandelt auch das Ersetzen der Beispieladressen **adrms.contoso.com** durch de Adressen Ihrer AD RMS-Server. 
    >
    > Wenn Sie dies tun, achten Sie darauf, dass keine zusätzlichen Leerzeichen vor oder nach Ihren Adressen vorhanden sind. Zusätzliche Leerzeichen unterbrechen das Migrations Skript und sind sehr schwer zu erkennen als die Grundursache des Problems. 
    >
    > Nach dem Einfügen von Text fügen einige Bearbeitungstools automatisch ein Leerzeichen an.
    >

5. Stellen Sie dieses Skript für alle Windows-Computer bereit, um sicherzustellen, dass wenn Sie mit dem Migrieren von Clients beginnen, Clients, die noch migriert werden müssen, weiterhin mit AD RMS kommunizieren, auch wenn Sie Inhalt verwenden, der durch migrierte Clients geschützt ist, die nun den Azure Rights Management-Dienst nutzen.

    Sie können Gruppenrichtlinien oder einen anderen Mechanismus zum Bereitstellen von Software zur Bereitstellung dieser Skripts verwenden.

## <a name="step-3-prepare-your-exchange-deployment-for-migration"></a>Schritt 3: Vorbereiten Ihrer Exchange-Bereitstellung für die Migration vor

Wenn Sie Exchange lokal oder Exchange Online verwenden, verfügen Sie womöglich über den zuvor integrierten Exchange-Knoten mit Ihrer AD RMS-Bereitstellung. In diesem Schritt konfigurieren Sie sie so, damit Sie die vorhandene AD RMS-Konfiguration verwenden, um Inhalt zu unterstützen, der durch Azure RMS geschützt ist.

Stellen Sie sicher, dass Sie über Ihre [Azure Rights Management-Dienst-URL für Ihren Mandanten](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url) verfügen, damit Sie diesen Wert mit *&lt;IhrerMandantenURL&gt;* in den folgenden Befehlen austauschen können.

Führen Sie einen der folgenden Schritte aus, je nachdem, ob Sie Exchange lokal oder Exchange Online mit AD RMS integriert haben:

- [Integrierte lokale Exchange-Integration mit AD RMS](#if-you-have-integrated-exchange-on-premises-with-ad-rms)
- [Integration von Exchange Online mit AD RMS](#if-you-have-integrated-exchange-online-with-ad-rms)
### <a name="if-you-have-integrated-exchange-online-with-ad-rms"></a>Wenn Sie Exchange Online mit AD RMS integriert haben

1. Öffnen Sie eine Exchange Online-PowerShell-Sitzung.

1. Führen Sie die folgenden PowerShell-Befehle entweder nacheinander oder in einem Skript aus:

    ```PowerShell
    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -internallicensingenabled $true 
    ```

### <a name="if-you-have-integrated-exchange-on-premises-with-ad-rms"></a>Wenn Sie Exchange lokal mit AD RMS integriert haben

Fügen Sie für jede Exchange-Organisation Registrierungs Werte auf jedem Exchange-Server hinzu, und führen Sie dann PowerShell-Befehle aus:

1. Wenn Sie über Exchange 2013 oder Exchange 2016 verfügen, fügen Sie den folgenden Registrierungs Wert hinzu:

    - **Registrierungs Pfad**: `HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection`

    - **Typ**: REG_SZ

    - **Wert**: `https://\<Your Tenant URL\>/_wmcs/licensing`

    - **Daten**: `https://\<AD RMS Extranet Licensing URL\>/_wmcs/licensing`

1. Führen Sie die folgenden PowerShell-Befehle entweder nacheinander oder in einem Skript aus:

    ```PowerShell
    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -RefreshServerCertificates
    Set-IRMConfiguration -internallicensingenabled $true
    IISReset
    ```

Nach dem Ausführen dieser Befehle für Exchange Online oder lokales Exchange unterstützt Ihre Exchange-Bereitstellung, wenn sie konfiguriert wurde, von AD RMS geschützten Inhalt zu unterstützen, auch den Inhalt, der von Azure RMS nach der Migration geschützt wird. 

Ihre Exchange-Bereitstellung verwendet weiterhin AD RMS, um geschützten Inhalt bis zu einem späteren Schritt in der Migration zu schützen.

## <a name="next-steps"></a>Nächste Schritte

Gehen Sie unter [Phase 2: Serverseitige Konfiguration](migrate-from-ad-rms-phase2.md).
