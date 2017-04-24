---
title: "Migrieren von AD RMS-Azure Information Protection – Phase 1"
description: Phase 1 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 1 bis 3 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d954d3ee-3c48-4241-aecf-01f4c75fa62c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 42cdcb888656df1b623c34775bd3bfe20daee952
ms.sourcegitcommit: 89e13f6be15a96293e0af0b2529a2e39563a63b6
translationtype: HT
---
# <a name="migration-phase-1---preparation"></a>Migrationsphase 1: Vorbereitung

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Verwenden Sie die folgenden Informationen für Phase 1 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren behandeln die Schritte 1 bis 3 von [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und bereiten Ihre Umgebung für die Migration vor, ohne Ihre Benutzer zu beeinflussen.


## <a name="step-1-download-the-azure-rights-management-administration-tool-and-identify-your-tenant-url"></a>Schritt 1: Herunterladen des Azure Rights Management-Verwaltungstools und Identifizieren Ihrer Mandanten-URL

Wechseln Sie zum Microsoft Download Center, und laden Sie das [Azure Rights Management-Verwaltungstool](https://go.microsoft.com/fwlink/?LinkId=257721) herunter, welches das Azure Rights Management-Verwaltungsmodul für Windows PowerShell enthält. Azure Rights Management (Azure RMS) ist der Dienst, der den Schutz von Daten für Azure Information Protection bereitstellt.

Installieren Sie das Tool. Anweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

> [!NOTE]
> Wenn Sie dieses Windows PowerShell-Modul bereits heruntergeladen haben, überprüfen Sie anhand des folgenden Befehls, ob Sie Version 2.5.0.0 oder höher verwenden: `(Get-Module aadrm -ListAvailable).Version`

Um einige der Migrationsanweisungen abzuschließen, müssen Sie die Azure Rights Management-Dienst-URL für Ihren Mandanten kennen, damit Sie sie ersetzen können, wenn Sie Verweise auf *\<Ihre Mandanten-URL\>* sehen. Die Azure Rights Management-Dienst-URL weist das folgende Format auf: **{GUID}.rms.[Region].aadrm.com**.

Beispiel: **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

### <a name="to-identify-your-azure-rights-management-service-url"></a>So identifizieren Sie Ihre Azure Rights Management-Dienst-URL

1. Stellen Sie eine Verbindung mit dem Azure Rights Management-Dienst her, und geben Sie die Anmeldeinformationen für den globalen Administrator Ihres Mandanten an, wenn Sie dazu aufgefordert werden:
    
        Connect-AadrmService
    
2. Abrufen der Konfiguration Ihres Mandanten:
    
        Get-AadrmConfiguration
    
3. Kopieren Sie den Wert für die **LicensingIntranetDistributionPointUrl**, und entfernen Sie `/_wmcs\licensing` aus dieser Zeichenfolge. 
    
    Was übrig bleibt, ist Ihre Azure Rights Management-Dienst-URL für Ihren Azure Information Protection-Mandanten, die in den folgenden Migrationsanweisungen oft mit *Ihre Mandanten-URL* abgekürzt wird.

## <a name="step-2-prepare-for-client-migration"></a>Schritt 2. Vorbereitung für die Clientmigration

Für die meisten Migrationen ist es nicht sehr praktisch, alle Clients auf einmal zu migrieren, also werden Sie diese eher in Batches migrieren. Das bedeutet, dass einige Clients über einen Zeitraum Azure Information Protection und einige noch immer AD RMS verwenden. Um jeweils zuvor migrierte und migrierte Benutzer zu unterstützen, verwenden Sie Onboarding-Steuerelemente, und stellen Sie ein Skript vor der Migration bereit. Dieser Schritt ist während der Migration erforderlich, damit Benutzer, die noch nicht migriert haben, Inhalt verwenden, der durch migrierte Benutzer geschützt wurde, die jetzt Azure Rights Management verwenden.

1. Erstellen Sie eine Gruppe, z.B. mit dem Namen **AIPMigrated**. Diese Gruppe kann in Active Directory erstellt und mit der Cloud synchronisiert werden. Alternativ kann sie auch in Office 365 oder Azure Active Directory erstellt werden. Weisen Sie zu diesem Zeitpunkt keinen Benutzer dieser Gruppe zu. Sie fügen Benutzer erst später hinzu, wenn sie migriert werden.

    Notieren Sie sich die Objekt-ID dieser Gruppe. Die können dazu Azure AD PowerShell verwenden: Verwenden Sie z.B. für die Version 1.0 des Moduls den Befehl [Get-MsolGroup](/powershell/msonline/v1/Get-MsolGroup). Oder Sie können die Objekt-ID der Gruppe aus dem Azure-Portal kopieren.

2. Konfigurieren Sie diese Gruppe für Onboarding-Steuerelemente, um nur Benutzern in dieser Gruppe zu erlauben, Azure Rights Management zu verwenden, um Inhalte zu schützen. Stellen Sie dazu in einer PowerShell-Sitzung eine Verbindung mit dem Azure Rights Management-Dienst her, und geben Sie Ihre globalen Administratoranmeldeinformationen an, wenn Sie dazu aufgefordert werden:

        Connect-Aadrmservice

    Konfigurieren Sie anschließend diese Gruppe für Onboarding-Steuerelemente, und ersetzen Sie Ihre Objekt-ID der Gruppe mit jener in diesem Beispiel. Geben Sie anschließend **Y** zur Bestätigung ein, wenn Sie dazu aufgefordert werden:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501"

3. [Laden Sie die folgende Datei herunter](https://go.microsoft.com/fwlink/?LinkId=524619), die Clientmigrationsskripts enthält:
    
    **ClientMigration.zip**
    
4. Extrahieren Sie die Dateien, und befolgen Sie die Anweisungen in **PrepareClient.cmd**, damit sie den Servernamen für Ihre Extranetlizenzierungs-URL des AD RMS-Clusters enthält. 
    
    So suchen Sie nach diesem Namen: Klicken Sie in der Active Directory Rights Management Services-Konsole auf den Clusternamen. Kopieren Sie unter **Clusterdetails** den Servernamen aus dem Wert **Lizenzierung** aus dem Abschnitt Extranetcluster-URLs. Zum Beispiel: **rmscluster.contoso.com**.

    > [!IMPORTANT]
    > Diese Anleitung behandelt auch das Ersetzen der Beispieladressen **adrms.contoso.com** durch de Adressen Ihrer AD RMS-Server. Wenn Sie diese Änderungen vornehmen, sollten Sie auf zusätzliche Leerzeichen vor und hinter Ihren Adressen achten. Da sie das Migrationsskript fehlschlagen lassen und schwer als Problemursache zu identifizieren sind, dürfen dort keine Leerzeichen vorhanden sein. Nach dem Einfügen von Text fügen einige Bearbeitungstools automatisch ein Leerzeichen an.
    >

5. Stellen Sie dieses Skript für alle Windows-Computer bereit, um sicherzustellen, dass wenn Sie mit dem Migrieren von Clients beginnen, Clients, die noch migriert werden müssen, weiterhin mit AD RMS kommunizieren, auch wenn Sie Inhalt verwenden, der durch migrierte Clients geschützt ist, die nun den Azure Rights Management-Dienst nutzen.

    Sie können Gruppenrichtlinien oder einen anderen Mechanismus zum Bereitstellen von Software zur Bereitstellung dieser Skripts verwenden.

## <a name="step-3-prepare-your-exchange-deployment-for-migration"></a>Schritt 3: Vorbereiten Ihrer Exchange-Bereitstellung für die Migration vor

Wenn Sie Exchange lokal oder Exchange Online verwenden, verfügen Sie womöglich über den zuvor integrierten Exchange-Knoten mit Ihrer AD RMS-Bereitstellung. In diesem Schritt konfigurieren Sie sie so, damit Sie die vorhandene AD RMS-Konfiguration verwenden, um Inhalt zu unterstützen, der durch Azure RMS geschützt ist. 

Stellen Sie sicher, dass Sie über Ihre [Azure Rights Management-Dienst-URL für Ihren Mandanten](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url) verfügen, damit Sie diesen Wert mit *&lt;IhrerMandantenURL&gt;* in den folgenden Befehlen austauschen können. Führen Sie diese Befehle einmal für jede Exchange-Organisation aus.

**Wenn Sie über den integrierten Exchange Online-Dienst mit AD RMS verfügen**: Öffnen Sie eine Exchange Online PowerShell-Sitzung, und führen Sie die folgenden PowerShell-Befehle entweder nacheinander oder in einem Skript aus:

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -internallicensingenabled $true 

**Wenn Sie über den integrierten Dienst Exchange lokal mit AD RMS verfügen**: Führen Sie die folgenden PowerShell-Befehle entweder nacheinander oder in einem Skript aus: 

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -RefreshServerCertificates
    Set-IRMConfiguration -internallicensingenabled $true
    IISReset

Darüber hinaus müssen Sie für Exchange lokal auf jedem Exchange-Server Registrierungswerte hinzufügen.


Für Exchange 2013 und Exchange 2016:


**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://\<Ihre Mandanten-URL\>/_wmcs/licensing

**Daten:** https://\<AD RMS-Extranetlizenzierungs-URL\>/_wmcs/licensing


---

Für Exchange 2010:


**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://\<Ihre Mandanten-URL\>/_wmcs/licensing

**Daten:** https://\<AD RMS-Extranetlizenzierungs-URL>/_wmcs/licensing


---


Nach dem Ausführen dieser Befehle unterstützen Ihre Exchange-Server, wenn Sie konfiguriert wurden, von AD RMS geschützten Inhalt zu unterstützen, auch den Inhalt, der von Azure RMS nach der Migration geschützt wird. Sie verwenden weiterhin AD RMS, um geschützten Inhalt bis zu einem späteren Schritt in der Migration zu schützen.



## <a name="next-steps"></a>Nächste Schritte
Gehen Sie unter [Phase 2: Serverseitige Konfiguration](migrate-from-ad-rms-phase2.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
