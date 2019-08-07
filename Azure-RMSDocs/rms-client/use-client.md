---
title: Der Client für Azure Information Protection-aip
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: cfe7d97bf7140b8f48f3f32b1d1f7a88de5ca933
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68789509"
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- Der Client kann der Azure Information Protection Client (klassisch), der Azure Information Protection Unified-Bezeichnungs Client oder der Rights Management-Client sein. Unabhängig von den Clients, die Sie verwenden, können Sie in Anwendungen integriert werden, die Sie auf Computern und mobilen Geräten ausführen. 
- Der Dienst wird in der Cloud (Azure Information Protection verwendet den Azure Rights Management-Dienst für den Schutz von Daten) oder lokal (Active Directory Rights Management Services, besser bekannt als AD RMS) ausgeführt. 

Der Azure Information Protection Client (klassisch) und der Azure Information Protection Unified Bezeichnung-Client unterstützen die Klassifizierung und den Schutz mit Bezeichnungen. Der klassische Client unterstützt auch den Schutz ohne Bezeichnung. Beide Clients können in Office-Anwendungen integriert werden und müssen separat installiert werden.

Der Rights Management (RMS)-Client wird automatisch mit einigen Anwendungen installiert, wie z. b. Office-Anwendungen, dem Azure Information Protection Client (klassisch) und Azure Information Protection Unified-Bezeichnungs Client und RMS-fähigen Anwendungen. von Softwareanbietern. Er kann jedoch auch [eigenständig installiert](https://www.microsoft.com/en-us/download/details.aspx?id=38396) werden, um das [Synchronisieren von Dateien von IRM-geschützten Bibliotheken und OneDrive for Business](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668) zu unterstützen sowie für Entwickler, die den Rights Management-Schutz in branchenspezifische Anwendungen integrieren möchten.

## <a name="choose-which-azure-information-protection-client-to-use"></a>Auswählen des zu verwendenden Azure Information Protection-Clients

Der **Azure Information Protection-Client (klassisch)** lädt Bezeichnungen und Richtlinien Einstellungen aus dem Azure-Portal herunter. Weitere Informationen zu diesem Client finden Sie unter [Azure Information Protection-Client: Versionsveröffentlichungsverlauf und Supportrichtlinie](client-version-release-history.md).

Der **Azure Information Protection-Client für einheitliche Bezeichnungen** dient zum Herunterladen von Bezeichnungen und Richtlinieneinstellungen aus den Admin-Centers: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, und das Microsoft 365 Compliance Center. Weitere Informationen zu diesem Client finden Sie im [Azure Information Protection Unified Bezeichnung-Client: Informationen zum Release](unifiedlabelingclient-version-release-history.md).

Welchen Client sollten Sie installieren?

- Installieren Sie den Azure Information Protection Unified Label-Client für Bezeichnungen und Richtlinien Einstellungen, die auch von MacOS, IOS und Android verwendet werden können, und wenn Sie nicht die wenigen Features benötigen, die noch nicht vom klassischen Client unterstützt werden. Zu diesen Features gehören der Schutz von Inhalten mit einem lokalen Schlüssel (Hyok) und ein Scanner für lokale Datenspeicher.

- Installieren Sie den Azure Information Protection Client (klassisch), wenn Sie eine Version des Clients benötigen, die über Features verfügt, die noch nicht mit dem Unified-Bezeichnungs Client verfügbar sind. Der Kompromiss besteht darin, dass nicht alle Bezeichnungs Einstellungen auf anderen Client Plattformen und die Verwaltung mit einem anderen Verwaltungs Portal verwendet werden können.

Derzeit verfügen der klassische Client und der Unified-Bezeichnungs Client nicht über Parität für seine Features. Diese Lücke wird jedoch geschlossen, und Sie können davon ausgehen, dass neue Features nur dem Unified-Bezeichnungs Client hinzugefügt werden. Aus diesem Grund wird empfohlen, den Unified-Bezeichnungs Client bereitzustellen, wenn der aktuelle Funktionsumfang und seine Funktionalität ihren Geschäftsanforderungen entsprechen. Falls nicht, oder wenn Sie Bezeichnungen in der Azure-Portal konfiguriert haben, die Sie noch nicht [zum vereinheitlichten](../configure-policy-migrate-labels.md)Bezeichnungs Speicher migriert haben, verwenden Sie den klassischen Client.

Sie können auch beide Clients in derselben Umgebung installieren, um unterschiedliche Geschäftsanforderungen zu unterstützen, wie im folgenden Beispiel gezeigt. Für dieses Szenario empfiehlt es sich, die Bezeichnungen in der Azure-Portal zu migrieren, sodass beide Gruppen von Clients für die einfache Verwaltung denselben Satz von Bezeichnungen gemeinsam verwenden.

##### <a name="example-deployment-strategy"></a>Beispiel für eine Bereitstellungs Strategie:

- Für die Mehrheit der Benutzer stellen Sie den Azure Information Protection Unified-Bezeichnungs Client bereit, da dieser Client die geschäftlichen Anforderungen für diese Benutzer erfüllt. 
    
    Für diese Benutzer ist Ihre Bezeichnung in Windows, Mac, IOS und Android sehr ähnlich, da Ihnen dieselben Bezeichnungen und die gleichen Richtlinien Einstellungen zur Verfügung stehen. Als Administrator verwalten Sie diese Bezeichnungen und Richtlinien Einstellungen im selben Verwaltungs Portal.

- Für eine Teilmenge der Benutzer stellen Sie den klassischen Client bereit, da diese Benutzer mindestens eine Bezeichnung benötigen, die den Hyok-Schutz (Hold Your Own Key) anwendet.
    
    Diese Benutzer haben bei der Verwendung dieses Clients eine etwas andere Bezeichnung. Beispielsweise wird eine Schaltfläche **schützen** anstelle einer Vertraulichkeits Schaltfläche in Office-Apps angezeigt. Als Administrator müssen Sie Ihre Bezeichnungen für Hyok-Einstellungen und Richtlinien Einstellungen in einem anderen Verwaltungs Portal für die Bezeichnungen und Einstellungen für die anderen Client Plattformen verwalten.

- Sie verfügen über lokale Datenspeicher mit Dokumenten, die auf sensible Informationen überprüft oder klassifiziert und geschützt werden müssen. Sie stellen den klassischen-Client auf Servern bereit, um den Azure Information Protection Scanner auszuführen.

### <a name="compare-the-clients"></a>Vergleichen der Clients

Verwenden Sie die folgende Tabelle, um zu vergleichen, welche Funktionen von den beiden Azure Information Protection Clients unterstützt werden.

|Feature|Klassischer Client|Einheitlicher Bezeichnungs Client|
|-------|-----------------------------------|----------------------------------------------------|
|Bezeichnungsaktionen: Manuell, empfohlen, automatisch| Ja | Ja |
|Zentrale Berichterstellung (Analysen):| Ja | Ja |
|Ein Viewer für geschützte Dateien (Text, Bilder, PDF, Pfile):| Ja | Ja |
|Unterstützung mehrerer Sprachen für Bezeichnungen:| Ja | Ja |
|Vererbung von Bezeichnungen aus E-Mail-Anhängen:| Ja | Ja  |
|Anpassungen, die Folgendes umfassen:<br />– Standardbezeichnung für E-Mails<br />-Popup Meldungen in Outlook <br />– S/MIME-Unterstützung<br />– Option zum Melden eines Problems| Ja <br /><br /> Wird als [Erweiterte Client Einstellungen unterstützt, die Sie im Azure-Portal](client-admin-guide-customizations.md#how-to-configure-advanced-client-configuration-settings-in-the-portal)| Ja <br /><br /> Unterstützt als [Erweiterte Einstellungen, die Sie mit PowerShell konfigurieren](clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) |
|Benutzerdefinierte Berechtigungen:| Ja | Ja <br /><br />Für Word, Excel, PowerPoint und den Datei-Explorer: Konfigurieren Sie die Bezeichnung im Azure-Portal |
|Kundenspezifische Berechtigungen:| Ja | Datei-Explorer und PowerShell <br /><br /> In Office-Apps können Benutzer als Alternative **Datei Info** > **schützen Dokument** > **Einschränken des Zugriffs** auswählen, oder Administratoren können eine Bezeichnung für benutzerdefinierte Berechtigungen konfigurieren.|
|Information Protection-Leiste in Office-Apps:| Ja | Ja mit Einschränkungen:<br /><br /> – kein Titel oder anpassbare QuickInfo<br /><br /> – die Bezeichnungsfarbe wird für die angewendete Bezeichnung nicht angezeigt|
|Bezeichnungen können optische Kennzeichnungen anwenden (Kopfzeile, Fußzeile, Wasserzeichen):| Ja | Ja mit Einschränkungen:<br /><br /> – Kopf- und Fußzeilen unterstützen keine Variablen für dynamische Werte. <br /><br /> – Das Verwenden unterschiedlicher optischer Kennzeichnungen für Word, Excel, PowerPoint und Outlook wird nicht unterstützt.|
|Datei-Explorer, Rechtsklickaktionen:| Ja | Ja mit Einschränkungen:<br /><br /> -PDF-Dokumente können nicht für das ältere ppdf-Format geschützt werden. <br /><br />  – Keine Unterstützung für den reinen Schutzmodus|
|PowerShell-Befehle:| Ja | Ja mit Einschränkungen:<br /><br />-Der Schutz von Container Dateien (ZIP,. rar,. 7z,. msg und. PST) kann nicht entfernt werden.|
|Offlineunterstützung für Schutzaktionen:| Ja | Ja mit Einschränkungen: <br /><br />– Bei Datei-Explorer und PowerShell-Befehlen muss der Benutzer mit dem Internet verbunden sein, um Dateien zu schützen |
|Unterstützung für nicht verbundene Computer mit manueller Verwaltung von Richtliniendateien:| Ja |Nein |
|HYOK-Unterstützung:| Ja | Nein <br /><br /> Bezeichnungen, die aus dem Azure-Portal migriert wurden und für den HYOK-Schutz konfiguriert sind, werden vom Azure Information Protection-Client für einheitliche Bezeichnungen angezeigt, wenden aber keinen Schutz an |
|Nutzungsprotokollierung in der Ereignisanzeige:| Ja | Nein|
|Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen| Ja | Nein |
|Überprüfung für lokale Datenspeicher:| Ja | Nein |
|Nachverfolgen und widerrufen:| Ja | Nein |
|Nur Schutzmodus (keine Bezeichnungen) mithilfe von Vorlagen:| Ja | Nein |
|Unterstützung für AD RMS:| Ja | Nur folgende Aktion wird unterstützt:<br /><br /> – Der Viewer kann geschützte Dokumente öffnen, wenn Sie die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\)) bereitstellen|

#### <a name="detailed-comparisons-for-the-clients"></a>Ausführliche Vergleiche der Clients

Wenn beide Clients dieselbe Funktion unterstützen, verwenden Sie die folgende Tabelle, um einige funktionale Unterschiede zwischen den beiden Clients zu ermitteln.

|Funktionalität |Klassischer Client|Einheitlicher Bezeichnungs Client|
|--------------|-----------------------------------|-----------------------------------------------------------|
|Setup:| Option zum Installieren der lokalen Demorichtlinie | Keine lokale Demorichtlinie|
|Auswahl und Anzeige von Bezeichnungen, wenn diese in Office-Apps angewendet werden:|Über die Schaltfläche **Schützen** im Menüband <br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|Über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|
|Verwalten der Information Protection-Leiste in Office-Apps:|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Schützen** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App ausgeblendet, aber in neu geöffneten Apps weiterhin automatisch angezeigt <br /><br /> Für Administratoren: <br /><br />– Richtlinieneinstellungen zum automatischen Anzeigen oder Ausblenden der Leiste beim ersten Öffnen einer App sowie zum Steuern, ob die Leiste bei neu geöffneten Apps automatisch ausgeblendet wird, nachdem ein Benutzer die Leiste in einer App ausgeblendet hat|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App und in neu geöffneten Apps ausgeblendet <br /><br />Für Administratoren: <br /><br />-PowerShell-Einstellung zum Verwalten des Balkens |
|Bezeichnungsfarbe: | Konfigurieren im Azure-Portal | Nach der Bezeichnung-Migration zu Office 365 beibehalten und mit PowerShell konfigurierbar <br /><br /> Farben können mithilfe von [PowerShell](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label) konfiguriert werden.|
|Bezeichnungen unterstützen verschiedene Sprachen:| Konfigurieren im Azure-Portal | Konfigurieren mithilfe von Office 365 Security & Compliance PowerShell und des Parameters *localesettings* für [New-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-label?view=exchange-ps) und [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps)|
|Richtlinienaktualisierung: | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 24 Stunden | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 4 Stunden|
|Unterstützte Formate für PDF:| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung (Standardeinstellung) <br /><br /> – PPDF <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br /> <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz|
|Generisch geschützte Dateien (Pfile-Dateien), die mit dem Viewer geöffnet wurden:| Die Datei wird in der ursprünglichen app geöffnet, in der Sie angezeigt, geändert und ohne Schutz gespeichert werden kann. | Die Datei wird in der ursprünglichen app geöffnet, in der Sie angezeigt und geändert, jedoch nicht gespeichert werden kann.|
|Unterstützte Cmdlets:| Alle für [AzureInformatioProtection](/powershell/module/azureinformationprotection) dokumentierten Cmdlets | "Set-aipfileclassification", "Set-aipfilelabel" und "Get-aipfilestatus" unterstützen keine SharePoint-Pfade. <br /><br /> "Set-aipfileclassification" und "Set-aipfilelabel" unterstützen den *Owner* -Parameter nicht. <br /><br /> Darüber hinaus gibt es einen einzelnen Kommentar „Keine anzuwendende Bezeichnung“ für alle Szenarien, in denen keine Bezeichnung angewendet wird <br /><br /> "Set-aipfileclassification" unterstützt den Parameter " *WhatIf* ", damit er im Ermittlungs Modus ausgeführt werden kann. <br /><br /> Set-AIPFileLabel unterstützt den Parameter *EnableTracking* nicht <br /><br /> Get-AIPFileStatus gibt keine Bezeichnungsinformationen aus anderen Mandanten zurück und zeigt den Parameter *RMSIssuedTime* nicht an<br /><br />Außerdem zeigt der Parameter " *labelingmethod* " für "Get-aipfilestatus" den Wert " **privilegiert** " oder " **Standard** " anstelle von **manuell** oder **automatisch**an Weitere Informationen finden Sie in der [Onlinedokumentation](/powershell/module/azureinformationprotection/get-aipfilestatus).|
|Aufforderungen zur Angabe einer Begründung (sofern konfiguriert) für Aktionen in Office: | Häufigkeit: Pro Datei <br /><br /> Herabsetzen der Vertraulichkeitsstufe <br /><br /> Entfernen einer Bezeichnung<br /><br /> Entfernen des Schutzes | Häufigkeit: Pro Sitzung <br /><br /> Herabsetzen der Vertraulichkeitsstufe<br /><br /> Entfernen einer Bezeichnung|
|Angewendete Bezeichnungsaktionen entfernen: | Benutzer wird zur Bestätigung aufgefordert <br /><br />Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App nicht automatisch angewendet  <br /><br />| Benutzer wird nicht zur Bestätigung aufgefordert<br /><br /> Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App automatisch angewendet|
|Automatische und empfohlene Bezeichnungen: | Wird im Azure-Portal als [Bezeichnungsbedingungen](../configure-policy-classification.md) mit integrierten Informationstypen und benutzerdefinierten Bedingungen konfiguriert, die Begriffe oder reguläre Ausdrücke verwenden <br /><br />Zu den Konfigurationsoptionen gehören: <br /><br />– Anzahl eindeutiger und nicht eindeutiger Vorkommnisse <br /><br /> – Mindestanzahl| Konfiguration in den Admin-Centers mit integrierten vertraulichen Informationstypen und [benutzerdefinierten Informationstypen](https://docs.microsoft.com/office365/securitycompliance/create-a-custom-sensitive-information-type)<br /><br />Zu den Konfigurationsoptionen gehören:  <br /><br />– Nur Anzahl eindeutiger Vorkommnisse <br /><br />– Mindest- und Höchstanzahl <br /><br />– Unterstützung von AND und OR bei Informationstypen <br /><br />– Wörterbuch mit Schlüsselwörtern<br /><br />– Anpassbare Vertraulichkeitsstufe und Zeichennähe|
|Anpassbarer richtlinientipp für automatische und empfohlene Bezeichnungen: | Ja <br /><br />Verwenden Sie die Azure-Portal, um die Standardmeldung an Benutzer zu ersetzen. | Nein <br /><br /> Obwohl die Admin Center über eine Option zum Bereitstellen eines angepassten Richtlinien Tipps verfügen, wird diese Option vom Unified-Bezeichnungs Client derzeit nicht unterstützt.|
|Ändern Sie die Standardschutz Ebene von Dateien: | Ja <br /><br />Sie können [Registrierungs Änderungen](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) verwenden, um die Standardwerte für systemeigenen und generischen Schutz zu überschreiben. | Nein |

Einen ausführlichen Vergleich der Verhaltensunterschiede für bestimmte Schutzeinstellungen finden Sie unter [Vergleichen des Verhaltens von Schutzeinstellungen für eine Bezeichnung](../configure-policy-migrate-labels.md#comparing-the-behavior-of-protection-settings-for-a-label).

#### <a name="features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client"></a>Features, die im Azure Information Protection Unified-Bezeichnungs Client nicht geplant sind

Obwohl sich der Azure Information Protection Unified Bezeichnung-Client noch in der Entwicklungsphase befindet, sind die folgenden Features und Verhaltensunterschiede vom klassischen Client derzeit nicht für die Verfügbarkeit in zukünftigen Versionen des Unified-Bezeichnungs Clients geplant: 

- Unterstützung von Office-Apps für nicht verbundene Computer mit manueller Richtlinien Dateiverwaltung

- Benutzerdefinierte Berechtigungen als separate Option, die Benutzer in Office-Apps auswählen können: Word, Excel und PowerPoint

- Nachverfolgen und widerrufen von Office-Apps und dem Datei-Explorer

- Titel und QuickInfo der Information Protection-Leiste

- Nur Schutzmodus (keine Bezeichnungen) mithilfe von Vorlagen

- Schutz von PDF-Dokumenten im .ppdf-Format

- Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen

- Demorichtlinien

- Begründung für das Entfernen eines Schutzes

- Bestätigungsaufforderung möchten **Sie diese Bezeichnung löschen?** für Benutzer, wenn Sie die Richtlinien Einstellung nicht zur Begründung verwenden

- Hinzufügen einer Bezeichnung zu einem Office-Dokument mithilfe einer vorhandenen benutzerdefinierten Eigenschaft (die erweiterten Clienteinstellungen „SyncPropertyName“ und „SyncPropertyState“)

- Unabhängige PowerShell-Cmdlets zur Verbindung mit einem Rights Management-Dienst


#### <a name="parent-labels-and-their-sublabels"></a>Übergeordnete und untergeordnete Bezeichnungen 

Der Azure Information Protection-Client (klassisch) unterstützt keine Konfigurationen, die eine übergeordnete Bezeichnung angeben, die über untergeordnete Bezeichnungen verfügt. Diese Konfigurationen umfassen die Angabe einer Standardbezeichnung sowie einer Bezeichnung für die empfohlene oder automatische Klassifizierung. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, können Sie eine der untergeordneten Bezeichnungen angeben, aber nicht die übergeordnete Bezeichnung.

Aus Paritätsgründen unterstützt der Azure Information Protection-Client für einheitliche Bezeichnungen die Anwendung von übergeordneten Bezeichnungen mit untergeordneten Bezeichnungen ebenfalls nicht, auch wenn Sie diese Bezeichnungen in den Admin-Centers auswählen können. In diesem Szenario wendet der Azure Information Protection-Client für einheitliche Bezeichnungen die übergeordnete Bezeichnung nicht an.

## <a name="see-also"></a>Siehe auch
Weitere Informationen zum Bereitstellen und Verwenden dieser Clients finden Sie in der folgenden Dokumentation:

- [Azure Information Protection-Client](AIP-client.md)

- [Azure Information Protection-Client für einheitliche Bezeichnungen](unifiedlabelingclient-version-release-history.md)

- [Hinweise zur Bereitstellung des RMS-Clients](client-deployment-notes.md)

Obwohl der Azure Information Protection-Client (klassisch) mit AD RMS verwendet werden kann, eignet sich dieser Client am besten für die Arbeit mit den Azure-Diensten. Azure Information Protection und dessen Schutzdienst Azure Rights Management. Einen Vergleich der Dienstseite von Azure Information Protection finden Sie unter [Vergleich von Azure Information Protection und AD RMS](../compare-on-premise.md).