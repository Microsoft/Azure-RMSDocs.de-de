---
title: Der Client für Azure Information Protection-aip
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/09/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: 24a0ee1b4627002284d5861287ec7a3133813902
ms.sourcegitcommit: a38af4741017cd745efc011cf29a0fedb62f9be7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827552"
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*


Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- Der Client kann der integrierte Bezeichnungs Client für Office, der Azure Information Protection Unified-Bezeichnungs Client für Windows, der Azure Information Protection-Client (klassisch) für Windows oder der Rights Management-Client sein.
    
    Diese Clients werden oft als **integrierter Office-Bezeichnungs Client, einheitlicher Bezeichnungs** **Client**, **klassischer Client**und **RMS-Client**bezeichnet. Je nachdem, welchen Client Sie verwenden, kann er in Anwendungen integriert werden, die Sie auf Computern und mobilen Geräten ausführen.

- Der Dienst befindet sich in der Cloud oder lokal. Der clouddienst ist Azure Information Protection, der den Azure Rights Management-Dienst für den Datenschutz verwendet. Der lokale Dienst wird Active Directory Rights Management Services, die üblicherweise als AD RMS bezeichnet wird. 

Alle diese Clients können in Office-Anwendungen integriert werden, aber der Unified-Bezeichnungs Client und der klassische Client müssen separat installiert werden und zusätzliche Features und Komponenten unterstützen. Diese Clients enthalten beispielsweise Unterstützung für den Datei-Explorer, sodass Sie Dateien außerhalb von Office klassifizieren und schützen können. Zu den zusätzlichen Komponenten gehören ein Viewer für geschützte PDF-Dokumente und geschützte Images sowie ein Scanner für lokale Datenspeicher.

Der RMS-Client bietet nur Schutz. Dieser Client wird automatisch mit einigen Anwendungen installiert, z. b. Office-Anwendungen, den Azure Information Protection Clients und RMS-fähigen Anwendungen von Softwareanbietern. Er kann jedoch auch [eigenständig installiert](https://www.microsoft.com/en-us/download/details.aspx?id=38396) werden, um das [Synchronisieren von Dateien von IRM-geschützten Bibliotheken und OneDrive for Business](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668) zu unterstützen sowie für Entwickler, die den Rights Management-Schutz in branchenspezifische Anwendungen integrieren möchten.

## <a name="choose-which-labeling-client-to-use-for-windows-computers"></a>Wählen Sie aus, welche Bezeichnung für Windows-Computer verwendet werden soll.

Verwenden Sie nach Möglichkeit einen der Bezeichnungs enden Clients, da Bezeichnungen die Komplexität der Anwendung des Schutzes für Benutzer abstrahieren und Bezeichnungen auch Klassifizierungen bieten, sodass Sie Ihre Daten nachverfolgen und verwalten können.

Die Auswahl der Bezeichnung Client für Ihre Windows-Computer kann von dem verwendeten Verwaltungs Portal beeinflusst werden:

- Der integrierte Office-Beschriftungs Client und der Azure Information Protection Unified Label-Client laden Bezeichnungen und Richtlinien Einstellungen aus den folgenden admin Centers herunter: 
    - Office 365 Security & Compliance Center
    - Microsoft 365 Security Center
    - Microsoft 365 Compliance Center

- Der Azure Information Protection-Client (klassisch) lädt die Bezeichnung und die Richtlinien Einstellungen aus dem Azure-Portal herunter.

Da der Unified-Bezeichnungs Client und der klassische Client eine separate Installation für Office erfordern, müssen Sie diese Clients aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen und installieren. 

Welchen Client sollten Sie verwenden?

- Verwenden Sie den **Bezeichnungs Client, der in Office** für Ihre Windows-Computer integriert ist, wenn Sie über Office 365-apps verfügen, die mindestens Version 1910 haben. Sie möchten dieselben Bezeichnungen und Richtlinien Einstellungen verwenden, die auch von MacOS, IOS und Android verwendet werden können, und Sie benötigen keine Features in Ihren Office-Apps, für die der Unified Label-Client oder der klassische Client erforderlich ist. Diese Features enthalten die Information Protection Leiste unter dem Menüband zur einfacheren Auswahl und Sichtbarkeit von Bezeichnungen. 
    
    Dieser Client unterstützt das Wechseln von Konten, und da er kein Office-Add-in verwendet, hat er eine bessere Leistung in Office-Apps als die Verwendung eines der Azure Information Protection Clients. Da die Bezeichnung in Office integriert ist, gibt es keine separate Installation und Wartung für diesen Bezeichnungs Client. Außerdem kann es im Gegensatz zu einem Office-Add-in nicht deaktiviert werden.

- Verwenden Sie den **Azure Information Protection Unified** Label-Client auf Windows-Computern für Bezeichnungen und Richtlinien Einstellungen, die auch von MacOS, IOS und Android verwendet werden können. Sie möchten Dateien unabhängig von Office 365-apps bezeichnen, und Sie benötigen keine Features, die nur vom klassischen Client unterstützt werden. Diese Features umfassen derzeit den Schutz von Inhalten mit einem lokalen Schlüssel (Hyok) und eine allgemein verfügbare Version des Scanners für lokale Datenspeicher.

- Installieren Sie den **Azure Information Protection-Client (klassisch)** auf Windows-Computern, wenn Sie eine Version des Clients benötigen, die über Features verfügt, die noch nicht mit dem Unified-Bezeichnungs Client verfügbar sind. Obwohl dieser Client die gleichen Bezeichnungen wie die von MacOS, IOS und Android verwenden kann, verfügt er über unterschiedliche Richtlinien Einstellungen. Der Kompromiss besteht also in der Verwaltung mithilfe eines anderen Verwaltungs Portals und einer anderen Benutzer Darstellung für Benutzer.

Mit der neuesten Version des Unified-Bezeichnungs Clients wird die Parität der Features mit dem klassischen Client geschlossen. Wenn diese Lücke geschlossen wird, können Sie davon ausgehen, dass neue Features nur dem Unified-Beschriftungs Client hinzugefügt werden. Aus diesem Grund wird empfohlen, den Unified-Bezeichnungs Client bereitzustellen, wenn der aktuelle Funktionsumfang und seine Funktionalität ihren Geschäftsanforderungen entsprechen. Falls nicht, oder wenn Sie Bezeichnungen in der Azure-Portal konfiguriert haben, die Sie noch nicht [zum vereinheitlichten Bezeichnungs Speicher migriert](../configure-policy-migrate-labels.md)haben, verwenden Sie den klassischen Client.

Sie können verschiedene Clients in derselben Umgebung verwenden, um unterschiedliche Geschäftsanforderungen zu unterstützen, wie im folgenden Beispiel für die Bereitstellung veranschaulicht. In einer gemischten Client Umgebung empfiehlt es sich, einheitliche Bezeichnungen zu verwenden, damit Clients denselben Satz von Bezeichnungen für die einfache Verwaltung verwenden. Neue Kunden haben standardmäßig einheitliche Bezeichnungen, da sich Ihre Mandanten auf der vereinheitlichten Beschriftungs Plattform befinden. Weitere Informationen finden Sie unter [wie kann ich feststellen, ob mein Mandant auf der Unified-Beschriftungs Plattform ist?](../faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)

Wenn Sie über einen Windows-Computer verfügen, auf dem Office 365-apps ausgeführt werden, die mindestens eine Version 1910 haben und einer der Azure Information Protection Clients installiert ist, wird der integrierte Bezeichnungs Client standardmäßig in Office-Apps deaktiviert. Sie können dieses Verhalten jedoch ändern, um den integrierten Bezeichnungs Client nur für Ihre Office-Apps zu verwenden. Mit dieser Konfiguration bleibt der Azure Information Protection Client (klassisch oder vereinheitlichte Bezeichnung) für die Bezeichnung im Datei-Explorer, PowerShell und Scanner verfügbar. Anweisungen zum Deaktivieren des Azure Information Protection Clients in Office 365-apps finden Sie in der Office-Dokumentation im Abschnitt über das [Ausführen von Vertraulichkeits Bezeichnungen neben dem Azure Information Protection-Client in Office für Windows](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps#can-sensitivity-labels-run-alongside-the-azure-information-protection-client-in-office-for-windows) .

##### <a name="example-deployment-strategy"></a>Beispiel für eine Bereitstellungs Strategie:

- Für die Mehrheit der Benutzer stellen Sie den Azure Information Protection Unified-Bezeichnungs Client bereit, da dieser Client die geschäftlichen Anforderungen für diese Benutzer erfüllt. 
    
    Für diese Benutzer ist Ihre Bezeichnung in Windows, Mac, IOS und Android sehr ähnlich, da Ihnen dieselben Bezeichnungen und die gleichen Richtlinien Einstellungen zur Verfügung stehen. Als Administrator verwalten Sie diese Bezeichnungen und Richtlinien Einstellungen im selben Verwaltungs Center.

- Außerdem installieren Sie den Unified-Bezeichnung-Client für sich selbst, um die Vorschauversion des Azure Information Protection Scanners zu testen.

- Für eine Teilmenge der Benutzer stellen Sie den klassischen Client bereit, da diese Benutzer Bezeichnungen benötigen, die den Hyok-Schutz (Hold Your Own Key) anwenden.
    
    Diese Benutzer haben bei der Verwendung dieses Clients eine etwas andere Bezeichnung. Beispielsweise wird eine Schaltfläche **schützen** anstelle einer **Vertraulichkeits** Schaltfläche in Office-Apps angezeigt. Als Administrator müssen Sie Ihre Bezeichnungen für Hyok-Einstellungen und Richtlinien Einstellungen in einem anderen Verwaltungs Center mit den Bezeichnungen und Einstellungen für die anderen Client Plattformen verwalten.

- Sie verfügen über lokale Datenspeicher mit Dokumenten, die auf sensible Informationen überprüft oder klassifiziert und geschützt werden müssen. Zur Verwendung in der Produktion stellen Sie den klassischen-Client auf Servern bereit, um den Azure Information Protection Scanner auszuführen.

## <a name="compare-the-labeling-clients-for-windows-computers"></a>Vergleichen der Beschriftungs Clients für Windows-Computer

Verwenden Sie die folgende Tabelle, um zu vergleichen, welche Funktionen von den drei Bezeichnungs enden Clients für Windows-Computer unterstützt werden.

In der Office-Dokumentation finden Sie Informationen zur [Unterstützung von Sensitivität-Funktionen in apps](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps#support-for-sensitivity-label-capabilities-in-apps), um die integrierten Features für die Vertraulichkeits Bezeichnung von Office auf verschiedenen Betriebssystemplattformen (Windows, MacOS, IOS und Android) und für das Web zu vergleichen.

|Komponente|Klassischer Client|Einheitlicher Bezeichnungs Client|Integrierter Office-Beschriftungs Client|
|:------|:------------:|:---------------------:|:-----------------------------:|
|Manuelle Bezeichnung:| **Ja** | **Ja** |**Ja** |
|Standard Bezeichnung:| **Ja** | **Ja** | **Ja** |
|Empfohlene oder automatische Bezeichnung:| **Ja** | **Ja** | Nein |
|Obligatorische Bezeichnung:| **Ja** | **Ja** | Nein |
|Benutzerdefinierte Berechtigungen für eine Bezeichnung:<br />-Nicht weiterleiten für e-Mails<br />-Benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint, Datei-Explorer| **Ja** | **Ja** | Nein |
|Unterstützung mehrerer Sprachen für Bezeichnungen:| **Ja** | **Ja** |**Ja** |
|Vererbung von Bezeichnungen aus E-Mail-Anhängen:| **Ja** | **Ja**  |Nein |
|Anpassungen, die Folgendes umfassen:<br />– Standardbezeichnung für E-Mails<br />-Popup Meldungen in Outlook <br />– S/MIME-Unterstützung<br />– Option zum Melden eines Problems| **Ja** <sup>1</sup> | **Ja** <sup>2</sup> | Nein |
|Überprüfung für lokale Datenspeicher:| **Ja** | **Ja <br />(Vorschau)** | Nein |
|Zentrale Berichterstellung (Analysen):| **Ja** | **Ja** | Nein |
|Benutzerdefinierte Berechtigungen werden unabhängig von einer Bezeichnung festgelegt:| **Ja** | **Ja** <sup>3</sup>| Nein |
|Information Protection-Leiste in Office-Apps:| **Ja** | **Ja**| Nein |
|Visuelle Kennzeichnungen als Bezeichnungs Aktion (Kopfzeile, Fußzeile, Wasserzeichen):| **Ja** | **Ja** | **Ja**|
|Visuelle Kennzeichnungen pro App:| **Ja** | Nein | Nein |
|Dynamische visuelle Kennzeichnungen mit Variablen:| **Ja** | Nein | Nein |
|Bezeichnung mit dem Datei-Explorer:| **Ja** | **Ja** | Nein |
|Ein Viewer für geschützte Dateien (Text, Bilder, PDF, Pfile):| **Ja** | **Ja** | Nein|
|Ppdf-Unterstützung für das Anwenden von Bezeichnungen:| **Ja** | Nein | Nein |
|PowerShell-Cmdlets für die Bezeichnung:| **Ja** | **Ja** <sup>4</sup> | Nein |
|Offlineunterstützung für Schutzaktionen:| **Ja** | **Ja** <sup>5</sup> | **Ja** |
|Manuelle Richtlinien Dateiverwaltung für getrennte Computer:| **Ja** |**Ja** <sup>6</sup>| Nein |
|HYOK-Unterstützung:| **Ja** | Nein | Nein |
|Verwendungs Protokollierung in Ereignisanzeige:| **Ja** | Nein |Nein |
|Anzeigen der Schaltfläche "nicht weiterleiten" in Outlook:| **Ja** | Nein | Nein |
|Nachverfolgung geschützt dokumentiert:| **Ja** | **Ja** <sup>7</sup> | Nein |
|Geschützte Dokumente widerrufen:| **Ja** | Nein | Nein |
|Reiner Schutzmodus (keine Bezeichnungen):| **Ja** | Nein | Nein |
|Unterstützung für Kontowechsel:| Nein | Nein | **Ja** |
|Unterstützung für Remotedesktopdienste:| **Ja** | **Ja** | **Ja** |
|Unterstützung für AD RMS:| **Ja** | Nein <sup>8</sup> | Nein |

Fußnoten:

<sup>1</sup> diese Einstellungen und viele weitere werden als [Erweiterte Client Einstellungen unterstützt, die Sie im Azure-Portal konfigurieren](client-admin-guide-customizations.md#how-to-configure-advanced-client-configuration-settings-in-the-portal).

<sup>2</sup> diese Einstellungen und viele weitere werden als erweiterte Einstellungen unterstützt, [die Sie mit PowerShell konfigurieren](clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell).

<sup>3</sup> wird vom Datei-Explorer und PowerShell unterstützt. In Office-Apps können Benutzer **Dateiinformationen** >  > **schützen** auswählen, um den **Zugriff einzuschränken**.

<sup>4</sup> es wird nicht unterstützt, den Schutz von Container Dateien (ZIP, rar, 7z,. msg und. PST) zu entfernen.

<sup>5</sup> für den Datei-Explorer und PowerShell-Befehlen muss der Benutzer mit dem Internet verbunden sein, um Dateien zu schützen.

<sup>6</sup> unterstützt für die Bezeichnung mit dem Datei-Explorer, PowerShell und dem Scanner. Wird für die Bezeichnung in Office-Apps nicht unterstützt.

<sup>7</sup> die Website zum Nachverfolgen von Dokumenten, die vom klassischen Client unterstützt wird, wird vom Unified-Bezeichnung-Client nicht unterstützt. Allerdings können Administratoren die [zentrale Bericht](../reports-aip.md) Erstellung verwenden, um zu ermitteln, ob der Zugriff auf geschützte Dokumente von Windows-Computern aus erfolgt und ob der Zugriff gewährt oder verweigert wurde, ohne dass Sie zuerst das Dokument für die Nachverfolgung registrieren müssen. 

<sup>8</sup> Bezeichnungs-und Schutz Aktionen werden nicht unterstützt. Allerdings kann der Viewer bei einer AD RMS Bereitstellung geschützte Dokumente öffnen, wenn Sie die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\))verwenden.


### <a name="detailed-comparisons-for-the-azure-information-protection-clients"></a>Ausführliche Vergleiche der Azure Information Protection Clients

Wenn sowohl der Azure Information Protection Client (klassisch) als auch der Azure Information Protection Unified-Bezeichnungs Client dieselbe Funktion unterstützen, verwenden Sie die folgende Tabelle, um einige funktionale Unterschiede zwischen den beiden Clients zu identifizieren.

|Funktion |Klassischer Client|Einheitlicher Bezeichnungs Client|
|--------------|-----------------------------------|-----------------------------------------------------------|
|Setup:| Option zum Installieren der lokalen Demorichtlinie | Keine lokale Demorichtlinie|
|Auswahl und Anzeige von Bezeichnungen, wenn diese in Office-Apps angewendet werden:|Über die Schaltfläche **Schützen** im Menüband <br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|Über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|
|Verwalten der Information Protection-Leiste in Office-Apps:|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Schützen** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App ausgeblendet, aber in neu geöffneten Apps weiterhin automatisch angezeigt <br /><br /> Für Administratoren: <br /><br />– Richtlinieneinstellungen zum automatischen Anzeigen oder Ausblenden der Leiste beim ersten Öffnen einer App sowie zum Steuern, ob die Leiste bei neu geöffneten Apps automatisch ausgeblendet wird, nachdem ein Benutzer die Leiste in einer App ausgeblendet hat|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App und in neu geöffneten Apps ausgeblendet <br /><br />Für Administratoren: <br /><br />-PowerShell-Einstellung zum Verwalten des Balkens |
|Bezeichnungsfarbe: | Konfigurieren im Azure-Portal | Nach der Bezeichnungs Migration beibehalten und mit [PowerShell](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label) konfigurierbar|
|Bezeichnungen unterstützen verschiedene Sprachen:| Konfigurieren im Azure-Portal | Konfigurieren mithilfe von Office 365 Security & Compliance PowerShell und des Parameters *localesettings* für [New-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-label?view=exchange-ps) und [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps)|
|Richtlinienaktualisierung: | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 24 Stunden <br /><br />Für den Scanner: stündlich und wenn der Dienst gestartet wird und die Richtlinie älter als eine Stunde ist| Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 4 Stunden <br /><br />Für den Scanner: alle 4 Stunden|
|Unterstützte Formate für PDF:| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung (Standardeinstellung) <br /><br /> – PPDF <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br /> <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz|
|Generisch geschützte Dateien (Pfile-Dateien), die mit dem Viewer geöffnet wurden:| Die Datei wird in der ursprünglichen app geöffnet, in der Sie angezeigt, geändert und ohne Schutz gespeichert werden kann. | Die Datei wird in der ursprünglichen app geöffnet, in der Sie angezeigt und geändert, jedoch nicht gespeichert werden kann.|
|Unterstützte Cmdlets:| Cmdlets für Bezeichnungen und Cmdlets für den reinen Schutz | Cmdlets für die Bezeichnung:<br /><br /> "Set-aipfileclassification" und "Set-aipfilelabel" unterstützen den *Owner* -Parameter nicht. <br /><br /> Darüber hinaus gibt es einen einzelnen Kommentar „Keine anzuwendende Bezeichnung“ für alle Szenarien, in denen keine Bezeichnung angewendet wird <br /><br /> "Set-aipfileclassification" unterstützt den Parameter " *WhatIf* ", damit er im Ermittlungs Modus ausgeführt werden kann. <br /><br /> Set-AIPFileLabel unterstützt den Parameter *EnableTracking* nicht <br /><br /> Get-AIPFileStatus gibt keine Bezeichnungsinformationen aus anderen Mandanten zurück und zeigt den Parameter *RMSIssuedTime* nicht an<br /><br />Außerdem zeigt der Parameter " *labelingmethod* " für "Get-aipfilestatus" den Wert " **privilegiert** " oder " **Standard** " anstelle von **manuell** oder **automatisch**an Weitere Informationen finden Sie in der [Onlinedokumentation](/powershell/module/azureinformationprotection/get-aipfilestatus).|
|Aufforderungen zur Angabe einer Begründung (sofern konfiguriert) für Aktionen in Office: | Häufigkeit: pro Datei <br /><br /> Herabsetzen der Vertraulichkeitsstufe <br /><br /> Entfernen einer Bezeichnung<br /><br /> Entfernen des Schutzes | Häufigkeit: pro Sitzung <br /><br /> Herabsetzen der Vertraulichkeitsstufe<br /><br /> Entfernen einer Bezeichnung|
|Angewendete Bezeichnungsaktionen entfernen: | Benutzer wird zur Bestätigung aufgefordert <br /><br />Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App nicht automatisch angewendet  <br /><br />| Benutzer wird nicht zur Bestätigung aufgefordert<br /><br /> Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App automatisch angewendet|
|Automatische und empfohlene Bezeichnungen: | Wird im Azure-Portal als [Bezeichnungsbedingungen](../configure-policy-classification.md) mit integrierten Informationstypen und benutzerdefinierten Bedingungen konfiguriert, die Begriffe oder reguläre Ausdrücke verwenden <br /><br />Zu den Konfigurationsoptionen gehören: <br /><br />– Anzahl eindeutiger und nicht eindeutiger Vorkommnisse <br /><br /> – Mindestanzahl| Konfiguration in den Admin-Centers mit integrierten vertraulichen Informationstypen und [benutzerdefinierten Informationstypen](https://docs.microsoft.com/microsoft-365/compliance/create-a-custom-sensitive-information-type)<br /><br />Zu den Konfigurationsoptionen gehören:  <br /><br />– Nur Anzahl eindeutiger Vorkommnisse <br /><br />– Mindest- und Höchstanzahl <br /><br />– Unterstützung von AND und OR bei Informationstypen <br /><br />– Wörterbuch mit Schlüsselwörtern<br /><br />– Anpassbare Vertraulichkeitsstufe und Zeichennähe|
|Bestell Unterstützung für untergeordnete Bezeichnungen auf Anlagen: | Aktiviert mit einer [erweiterten Client Einstellung](client-admin-guide-customizations.md#enable-order-support-for-sublabels-on-attachments) | Standardmäßig aktiviert, keine Konfiguration erforderlich|
|Ändern Sie das standardmäßige Schutzverhalten für Dateitypen: | Sie können [Registrierungs Änderungen](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) verwenden, um die Standardwerte für systemeigenen und generischen Schutz zu überschreiben. | Sie können [PowerShell](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect) verwenden, um zu ändern, welche Dateitypen geschützt werden.|

Einen ausführlichen Vergleich der Verhaltensunterschiede für bestimmte Schutzeinstellungen finden Sie unter [Vergleichen des Verhaltens von Schutzeinstellungen für eine Bezeichnung](../configure-policy-migrate-labels.md#comparing-the-behavior-of-protection-settings-for-a-label).

### <a name="features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client"></a>Features, die im Azure Information Protection Unified-Bezeichnungs Client nicht geplant sind

Obwohl sich der Azure Information Protection Unified Bezeichnung-Client noch in der Entwicklungsphase befindet, sind die folgenden Features und Verhaltensunterschiede vom klassischen Client derzeit nicht für die Verfügbarkeit in zukünftigen Versionen des Unified-Bezeichnungs Clients geplant: 

- Benutzerdefinierte Berechtigungen als separate Option, die Benutzer in Office-Apps auswählen können: Word, Excel und PowerPoint

- Nachverfolgen und widerrufen von Office-Apps und dem Datei-Explorer

- Titel und QuickInfo der Information Protection-Leiste

- Nur Schutzmodus (keine Bezeichnungen) mithilfe von Vorlagen

- Schutz von PDF-Dokumenten im .ppdf-Format

- Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen

- Demorichtlinien

- Begründung für das Entfernen eines Schutzes

- Bestätigungsaufforderung möchten **Sie diese Bezeichnung löschen?** für Benutzer, wenn Sie die Richtlinien Einstellung nicht zur Begründung verwenden

- Unabhängige PowerShell-Cmdlets zur Verbindung mit einem Rights Management-Dienst


### <a name="parent-labels-and-their-sublabels"></a>Übergeordnete und untergeordnete Bezeichnungen 

Der Azure Information Protection-Client (klassisch) unterstützt keine Konfigurationen, die eine übergeordnete Bezeichnung angeben, die über untergeordnete Bezeichnungen verfügt. Diese Konfigurationen umfassen die Angabe einer Standardbezeichnung sowie einer Bezeichnung für die empfohlene oder automatische Klassifizierung. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, können Sie eine der untergeordneten Bezeichnungen angeben, aber nicht die übergeordnete Bezeichnung.

Aus Paritätsgründen unterstützt der Azure Information Protection-Client für einheitliche Bezeichnungen die Anwendung von übergeordneten Bezeichnungen mit untergeordneten Bezeichnungen ebenfalls nicht, auch wenn Sie diese Bezeichnungen in den Admin-Centers auswählen können. In diesem Szenario wendet der Azure Information Protection-Client für einheitliche Bezeichnungen die übergeordnete Bezeichnung nicht an.

## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie die folgende Dokumentation, um die Azure Information Protection Clients zu installieren und zu konfigurieren:

- [Azure Information Protection-Client](AIP-client.md)

- [Azure Information Protection-Client für einheitliche Bezeichnungen](unifiedlabelingclient-version-release-history.md)

Weitere Informationen zur Verwendung des integrierten Bezeichnungs Clients für Office 365-apps finden Sie unter [Vertraulichkeits Bezeichnungen in Office-Apps](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps).
