---
title: Der Client für Azure Information Protection
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 03/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ms.suite: ems
ms.openlocfilehash: b8f19a4953d5cfead99e96386bd65d070ac8ae77
ms.sourcegitcommit: 0df1cd6000f72ec8cac60a5ace0fa441974464e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58524369"
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- Der Client kann der Azure Information Protection-Client oder der Rights Management-Client sein. Er ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden. 

- Der Dienst wird in der Cloud (Azure Information Protection verwendet den Azure Rights Management-Dienst für den Schutz von Daten) oder lokal (Active Directory Rights Management Services, besser bekannt als AD RMS) ausgeführt. 

Der Azure Information Protection-Client unterstützt zusätzlich zum Schutz ohne Bezeichnungen auch Klassifizierung und Schutz mit Bezeichnungen. Dieser Client kann in Office-Anwendung integriert werden und muss separat installiert werden.

Der Rights Management-Client (RMS) wird automatisch mit einigen Anwendungen installiert, z. B. Office-Anwendungen, der Azure Information Protection-Client und RMS-fähige Anwendungen von Softwareanbietern. Er kann jedoch auch [eigenständig installiert](https://www.microsoft.com/en-us/download/details.aspx?id=38396) werden, um das [Synchronisieren von Dateien von IRM-geschützten Bibliotheken und OneDrive for Business](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668) zu unterstützen sowie für Entwickler, die den Rights Management-Schutz in branchenspezifische Anwendungen integrieren möchten.

## <a name="choose-which-azure-information-protection-client-to-use"></a>Auswählen des zu verwendenden Azure Information Protection-Clients

Der **Azure Information Protection-Client**, der zum Herunterladen von Bezeichnungen und Richtlinieneinstellungen aus dem Azure-Portal dient, ist allgemein verfügbar und liegt in einer Vorschauversion vor, mit der neue Funktionen und Fehlerbehebungen getestet werden können. Weitere Informationen über diese Versionen des Clients finden Sie unter [Azure Information Protection-Client: Versionsveröffentlichungsverlauf und Supportrichtlinie](client-version-release-history.md). 

Der **Azure Information Protection-Client für einheitliche Bezeichnungen** dient zum Herunterladen von Bezeichnungen und Richtlinieneinstellungen aus dem Office 365 Security & Compliance Center. Dieser Client liegt derzeit zum Testen in der Vorschau vor. Weitere Informationen zu dieser Version finden Sie unter [Azure Information Protection-Client für einheitliche Bezeichnungen: Informationen zum Release](unifiedlabelingclient-version-release-history.md).

Welchen Client sollten Sie installieren?

- Wenn Sie eine Bereitstellung in der Produktionsumgebung planen, verwenden Sie den allgemein verfügbaren Azure Information Protection-Client.

- Wenn Sie sich in der Test- und Bewertungsphase befinden, verwenden Sie einen der Vorschauclients.
    
    Zurzeit besteht keine Featureparität für die Vorschauversionen des Azure Information Protection-Clients und des Azure Information Protection-Clients für einheitliche Bezeichnungen. Diese Lücke wird jedoch in Zukunft geschlossen, und dann werden neue Features nur noch zum Azure Information Protection-Client für einheitliche Bezeichnungen hinzugefügt. Aus diesem Grund wird empfohlen, dass Sie den Azure Information Protection-Client für einheitliche Bezeichnungen testen, wenn der aktuelle Satz an Features und Funktionen Ihre geschäftlichen Anforderungen erfüllt. Wenn dies nicht der Fall ist oder wenn Sie Bezeichnungen im Azure-Portal konfiguriert haben, die noch nicht [zum Store für einheitliche Bezeichnungen migriert wurden](../configure-policy-migrate-labels.md), verwenden Sie den Azure Information Protection-Client.

### <a name="feature-comparisons-for-the-clients"></a>Vergleich zwischen den Features der Clients

Anhand der folgenden Tabelle können Sie die Features, die von den beiden aktuellen Vorschauversionen unterstützt werden, miteinander vergleichen.

|Komponente|Azure Information Protection-Client|Azure Information Protection<br /> Client für einheitliche Bezeichnungen|
|-------|-----------------------------------|----------------------------------------------------|
|Bezeichnungsaktionen: Manuell, empfohlen, automatisch| Ja | Ja |
|Zentrale Berichterstellung (Analysen):| Ja | Ja |
|Einstellungen zurücksetzen und Protokolle exportieren:| Ja | Ja |
|Benutzerdefinierte Berechtigungen:| Ja | Nur für Outlook (Nicht weiterleiten) |
|Kundenspezifische Berechtigungen:| Ja | Nur Datei-Explorer <br /><br /> In Office-Apps können Benutzer alternativ auch **Dateiinfo** > **Dokument schützen** > **Zugriff einschränken** auswählen |
|Information Protection-Leiste in Office-Apps:| Ja | Ja mit Einschränkungen:<br /><br /> – kein Titel oder anpassbare QuickInfo<br /><br /> – die Bezeichnungsfarbe wird für die angewendete Bezeichnung nicht angezeigt|
|Bezeichnungen können optische Kennzeichnungen anwenden (Kopfzeile, Fußzeile, Wasserzeichen):| Ja | Ja mit Einschränkungen:<br /><br /> – Kopf- und Fußzeilen unterstützen keine Variablen für dynamische Werte. <br /><br /> – Das Verwenden unterschiedlicher optischer Kennzeichnungen für Word, Excel, PowerPoint und Outlook wird nicht unterstützt.|
|Datei-Explorer, Rechtsklickaktionen:| Ja | Ja mit Einschränkungen:<br /><br /> – Kein Schutz für PDF-Dokumente im PPDF-Format <br /><br />  – Keine Unterstützung für den reinen Schutzmodus|
|Viewer für geschützte Dateien:| Ja | Ja mit Einschränkungen:<br /><br /> – Bei generisch geschützten Dateien (PFILE-Format) können im Gegensatz zum Azure Information Protection-Client Änderungen an der ursprünglich geöffneten Datei nicht gespeichert werden|
|PowerShell-Befehle:| Ja | Ja mit Einschränkungen:<br /><br />– Enthaltene Cmdlets: [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus), [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification), [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel), [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) <br /><br />– Cmdlets, die eine direkte Verbindung zu einem Schutzdienst herstellen, sind nicht enthalten|
|Offlineunterstützung für Schutzaktionen:| Ja | Ja mit Einschränkungen: <br /><br />– Bei Datei-Explorer und PowerShell-Befehlen muss der Benutzer mit dem Internet verbunden sein, um Dateien zu schützen |
|HYOK-Unterstützung:| Ja | Nein<br /><br /> Bezeichnungen, die aus dem Azure-Portal migriert wurden und für den HYOK-Schutz konfiguriert sind, werden vom Azure Information Protection-Client für einheitliche Bezeichnungen angezeigt, wenden aber keinen Schutz an |
|Nutzungsprotokollierung in der Ereignisanzeige:| Ja | Nein|
|Vererbung von Bezeichnungen aus E-Mail-Anhängen:| Ja | Nein |
|Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen| Ja | Nein |
|[Anpassungen](client-admin-guide-customizations.md#available-advanced-client-settings) wie z.B. folgende:<br />– Standardbezeichnung für E-Mails<br />– Ermöglichen von benutzerdefinierten Berechtigungen <br />– S/MIME-Unterstützung<br />– Option zum Melden eines Problems| Ja | Nein |
|Überprüfung für lokale Datenspeicher:| Ja | Nein |
|Nachverfolgen und widerrufen:| Ja | Nein |
|Reiner Schutzmodus (keine Bezeichnungen):| Ja | Nein |
|Schaltfläche „Nicht weiterleiten“ in Outlook:| Ja | Nein |
|Unterstützung für mehrere Sprachen:| Ja | Nein |
|Unterstützung für AD RMS:| Ja | Nur folgende Aktion wird unterstützt:<br /><br /> – Der Viewer kann geschützte Dokumente öffnen, wenn Sie die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\)) bereitstellen|

#### <a name="functional-comparison-for-the-clients"></a>Vergleich zwischen den Funktionen der Clients

Wenn beide Clients das gleiche Feature unterstützen, ziehen Sie die folgende Tabelle zurate, um Funktionsunterschiede zwischen den aktuellen Vorschauversionen zu ermitteln.

|Funktionalität |Azure Information Protection-Client|Azure Information Protection<br /> Client für einheitliche Bezeichnungen|
|--------------|-----------------------------------|-----------------------------------------------------------|
|Setup:| Option zum Installieren der lokalen Demorichtlinie | Keine lokale Demorichtlinie|
|Auswahl und Anzeige von Bezeichnungen, wenn diese in Office-Apps angewendet werden:|Über die Schaltfläche **Schützen** im Menüband <br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|Über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|
|Verwalten der Information Protection-Leiste in Office-Apps:|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Schützen** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App ausgeblendet, aber in neu geöffneten Apps weiterhin automatisch angezeigt <br /><br /> Für Administratoren: <br /><br />– Richtlinieneinstellungen zum automatischen Anzeigen oder Ausblenden der Leiste beim ersten Öffnen einer App sowie zum Steuern, ob die Leiste bei neu geöffneten Apps automatisch ausgeblendet wird, nachdem ein Benutzer die Leiste in einer App ausgeblendet hat|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App und in neu geöffneten Apps ausgeblendet <br /><br />Für Administratoren: <br /><br />– Keine Richtlinieneinstellungen zum Verwalten der Leiste|
|Bezeichnungsfarbe: | Konfigurieren im Azure-Portal | Wird nach der Migration der Bezeichnung zu Office 365 beibehalten <br /><br /> Im Security & Compliance Center neu erstellte Bezeichnungen haben keine Farbe|
|Richtlinienaktualisierung: | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 24 Stunden | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 4 Stunden|
|Unterstützte Formate für PDF:| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung (Standardeinstellung) <br /><br /> – PPDF <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br /> <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz|
|Unterstützte Cmdlets:| Alle für [AzureInformatioProtection](/powershell/module/azureinformationprotection) dokumentierten Cmdlets | Set-AIPFileClassification und Set-AIPFileLabel unterstützen weder den Parameter *Owner* noch SharePoint Server-Bibliotheken <br /><br /> Darüber hinaus gibt es einen einzelnen Kommentar „Keine anzuwendende Bezeichnung“ für alle Szenarien, in denen keine Bezeichnung angewendet wird <br /><br /> Set-AIPFileLabel unterstützt den Parameter *EnableTracking* nicht <br /><br /> Get-AIPFileStatus gibt keine Bezeichnungsinformationen aus anderen Mandanten zurück und zeigt den Parameter *RMSIssuedTime* nicht an<br /><br />Darüber hinaus zeigt der Parameter *LabelingMethod* für Get-AIPFileStatus **Privilegiert**, **Standard** oder **Auto** anstelle von **Manuell** oder **Automatisch** an. Weitere Informationen finden Sie in der [Onlinedokumentation](/powershell/module/azureinformationprotection/get-aipfilestatus).|
|Aufforderungen zur Angabe einer Begründung (sofern konfiguriert) für Aktionen in Office: | Häufigkeit: Pro Datei <br /><br /> Herabsetzen der Vertraulichkeitsstufe <br /><br /> Entfernen einer Bezeichnung<br /><br /> Entfernen des Schutzes | Häufigkeit: Pro Sitzung <br /><br /> Herabsetzen der Vertraulichkeitsstufe<br /><br /> Entfernen einer Bezeichnung|
|Angewendete Bezeichnungsaktionen entfernen: | Benutzer wird zur Bestätigung aufgefordert <br /><br />Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App nicht automatisch angewendet  <br /><br />| Benutzer wird nicht zur Bestätigung aufgefordert<br /><br /> Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App automatisch angewendet|
|Automatische und empfohlene Klassifizierung: | Wird im Azure-Portal als [Bezeichnungsbedingungen](../configure-policy-classification.md) mit integrierten Informationstypen und benutzerdefinierten Bedingungen konfiguriert, die Begriffe oder reguläre Ausdrücke verwenden <br /><br />Zu den Konfigurationsoptionen gehören: <br /><br />– Anzahl eindeutiger und nicht eindeutiger Vorkommnisse <br /><br /> – Mindestanzahl| Konfiguration im Security & Compliance Center mit integrierten vertraulichen Informationstypen und [benutzerdefinierten Informationstypen](https://docs.microsoft.com/office365/securitycompliance/create-a-custom-sensitive-information-type)<br /><br />Zu den Konfigurationsoptionen gehören:  <br /><br />– Nur Anzahl eindeutiger Vorkommnisse <br /><br />– Mindest- und Höchstanzahl <br /><br />– Unterstützung von AND und OR bei Informationstypen <br /><br />– Wörterbuch mit Schlüsselwörtern<br /><br />– Anpassbare Vertraulichkeitsstufe und Zeichennähe|

Einen ausführlicheren Vergleich der Verhaltensunterschiede für bestimmte Schutzeinstellungen finden Sie unter [Vergleichen des Verhaltens von Schutzeinstellungen für eine Bezeichnung](../configure-policy-migrate-labels.md#comparing-the-behavior-of-protection-settings-for-a-label).

#### <a name="features-that-will-not-be-in-the-azure-information-protection-unified-labeling-client"></a>Features, die nicht im Azure Information Protection-Client für einheitliche Bezeichnungen enthalten sein werden

Obwohl sich der Azure Information Protection-Client für einheitliche Bezeichnungen noch in der Entwicklungsphase befindet, werden die folgenden Features und Verhaltensunterschiede zum Azure Information Protection-Client in zukünftigen Releases des Azure Information Protection-Clients für einheitliche Bezeichnungen nicht verfügbar sein: 

- Benutzerdefinierte Berechtigungen in Office-Apps: Word, Excel und PowerPoint

- Nachverfolgen und widerrufen von Office-Apps und dem Datei-Explorer

- Titel und QuickInfo der Information Protection-Leiste

- Offlinesupport für Schutzaktionen in PowerShell und im Datei-Explorer

- Reiner Schutzmodus (keine Bezeichnungen)

- Schutz von PDF-Dokumenten im .ppdf-Format

- Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen

- Demorichtlinien

- Begründung für das Entfernen eines Schutzes

- Bestätigungsaufforderung vor dem Löschen einer angewendeten Bezeichnung

- „Problem melden“-Link im Dialogfeld „Hilfe und Feedback“

- Hinzufügen einer Bezeichnung zu einem Office-Dokument mithilfe einer vorhandenen benutzerdefinierten Eigenschaft (die erweiterten Clienteinstellungen „SyncPropertyName“ und „SyncPropertyState“)

- Unabhängige PowerShell-Cmdlets zur Verbindung mit einem Rights Management-Dienst

- Reiner AD RMS-Schutz


#### <a name="parent-labels-and-their-sublabels"></a>Übergeordnete und untergeordnete Bezeichnungen 

Der Azure Information Protection-Client unterstützt keine Konfigurationen, die eine übergeordnete Bezeichnung mit untergeordneten Bezeichnungen festlegen. Diese Konfigurationen umfassen die Angabe einer Standardbezeichnung sowie einer Bezeichnung für die empfohlene oder automatische Klassifizierung. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, können Sie eine der untergeordneten Bezeichnungen angeben, aber nicht die übergeordnete Bezeichnung.

Aus Paritätsgründen unterstützt der Azure Information Protection-Client für einheitliche Bezeichnungen die Anwendung von übergeordneten Bezeichnungen mit untergeordneten Bezeichnungen ebenfalls nicht, auch wenn Sie diese Bezeichnungen im Office 365 Security & Compliance Center auswählen können. In diesem Szenario wendet der Azure Information Protection-Client für einheitliche Bezeichnungen die übergeordnete Bezeichnung nicht an.

## <a name="see-also"></a>Siehe auch
Weitere Informationen zum Bereitstellen und Verwenden dieser Clients finden Sie in der folgenden Dokumentation:

- [Azure Information Protection-Client](AIP-client.md)

- [Azure Information Protection-Client für einheitliche Bezeichnungen](unifiedlabelingclient-version-release-history.md)

- [Hinweise zur Bereitstellung des RMS-Clients](client-deployment-notes.md)

Der Azure Information Protection-Client kann zwar mit AD RMS verwendet werden, eignet sich aber am besten für die Arbeit mit den zugehörigen Azure-Diensten: Azure Information Protection und zugehöriger Datenschutzdienst, Azure Rights Management. Einen Vergleich der Dienstseite von Azure Information Protection finden Sie unter [Vergleich von Azure Information Protection und AD RMS](../compare-on-premise.md).
