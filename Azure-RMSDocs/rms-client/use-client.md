---
title: Der Client für Azure Information Protection – AIP
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/05/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: 0c757c8b599215e78bc30f50a05fbedf83d67481
ms.sourcegitcommit: 746bb029d185ac13f36482bb9a39200ab5445dbe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66507133"
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- Der Client kann es sich um den Azure Information Protection-Client, der Azure Information Protection unified bezeichnungs-Client oder Rights Management-Client sein. Je nachdem, was dieser Clients Sie verwenden, integriert es Anwendungen, die Sie auf Computern und mobilen Geräten ausführen. 

- Der Dienst wird in der Cloud (Azure Information Protection verwendet den Azure Rights Management-Dienst für den Schutz von Daten) oder lokal (Active Directory Rights Management Services, besser bekannt als AD RMS) ausgeführt. 

Der Azure Information Protection-Client und der einheitliche Bezeichnung Azure Information Protection-Client unterstützt die Klassifizierung und Schutz mit Bezeichnungen. Der Azure Information Protection-Client unterstützt auch Schutz ohne Bezeichnung. Beide Clients mit Office-Anwendungen integrieren und müssen separat installiert werden.

Der Rights Management (RMS)-Client wird automatisch mit einigen Anwendungen wie Office-Anwendungen, die Azure Information Protection-Client und Azure Information Protection unified bezeichnungs-Client und RMS-fähige Anwendungen von installiert. Softwareanbieter. Er kann jedoch auch [eigenständig installiert](https://www.microsoft.com/en-us/download/details.aspx?id=38396) werden, um das [Synchronisieren von Dateien von IRM-geschützten Bibliotheken und OneDrive for Business](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668) zu unterstützen sowie für Entwickler, die den Rights Management-Schutz in branchenspezifische Anwendungen integrieren möchten.

## <a name="choose-which-azure-information-protection-client-to-use"></a>Auswählen des zu verwendenden Azure Information Protection-Clients

Die **Azure Information Protection-Client** Bezeichnungen und Einstellungen im Azure-Portal heruntergeladen. Weitere Informationen zu dieser finden Sie unter den [Azure Information Protection-Client: Versionsveröffentlichungsverlauf und Supportrichtlinie](client-version-release-history.md).

Der **Azure Information Protection-Client für einheitliche Bezeichnungen** dient zum Herunterladen von Bezeichnungen und Richtlinieneinstellungen aus den Admin-Centers: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, und das Microsoft 365 Compliance Center. Weitere Informationen zu dieser finden Sie unter den [Azure Information Protection – einheitliche bezeichnungs-Client: Informationen zum Release](unifiedlabelingclient-version-release-history.md).

Welchen Client sollten Sie installieren?

- Installieren der Azure Information Protection unified bezeichnungs-Client für Bezeichnungen, die auch von Mac OS, iOS und Android verwendet werden kann und wenn Sie nicht, erweiterte Funktionen wie erweiterte Clienteinstellungen benötigen, der benutzerdefinierte Berechtigungen, einem lokalen Schlüssel (HYOK), oder Scanner für lokale Datenspeicher.

- Installieren Sie den Azure Information Protection-Client, wenn Sie erweiterte Funktionen benötigen, die noch nicht im einheitlichen bezeichnungs-Client verfügbar sind, aber die Bezeichnungen auf anderen Clientplattformen verwendet werden können.

Derzeit verfügen nicht über den Azure Information Protection-Client und der einheitliche Bezeichnung Azure Information Protection-Client Parität für ihre Funktionen. Diese Lücke wird jedoch in Zukunft geschlossen, und dann werden neue Features nur noch zum Azure Information Protection-Client für einheitliche Bezeichnungen hinzugefügt. Aus diesem Grund wird empfohlen, dass Sie den Azure Information Protection unified bezeichnungs-Client bereitstellen, wenn die aktuellen Features und Funktionalität Ihrer geschäftlichen Anforderungen zu erfüllen. Wenn dies nicht der Fall ist oder wenn Sie Bezeichnungen im Azure-Portal konfiguriert haben, die noch nicht [zum Store für einheitliche Bezeichnungen migriert wurden](../configure-policy-migrate-labels.md), verwenden Sie den Azure Information Protection-Client.

Sie können auch beide Clients in der gleichen Umgebung zur Unterstützung von unterschiedlichen geschäftsanforderungen, installieren, wie im folgenden Beispiel gezeigt. In diesem Szenario wird empfohlen, dass Sie die Bezeichnungen im Azure-Portal migrieren, sodass beide Sätze von Clients über den gleichen Satz von Bezeichnungen zur Vereinfachung der Verwaltung verwenden.

##### <a name="example-deployment-strategy"></a>Beispiel-Bereitstellungsstrategie:

- Für die Mehrheit der Benutzer stellen Sie den Azure Information Protection unified bezeichnungs-Client bereit, da die meisten Benutzer nicht benötigen, Features oder Funktionen, die nur mit dem Azure Information Protection-Client verfügbar sind. 
    
    Einkaufserlebnis Bezeichnung ist für diese Benutzer müssen sehr ähnlich, wenn sie auch Geräte, auf denen Mac OS, iOS und Android ausgeführt haben und diese Geräte eine Version von Office verfügt haben, vertraulichkeitsbezeichnungen unterstützt.

- Stellen Sie für eine Teilmenge von Benutzern die Azure Information Protection-Client aus, da diese Benutzer, dass Bezeichnungen, die zum Anwenden von aufzunehmen erfordern, Ihre eigenen Key (HYOK)-Schutz oder die Eingabeaufforderung für benutzerdefinierte Berechtigungen.
    
    Diese Benutzer verfügen über zusätzliche Features und Funktionen, aber eine etwas abweichende Optionen, wenn sie auch über Geräte, auf denen Mac OS, iOS und Android ausgeführt wird, und diese Geräte haben eine Version von Office verfügt, vertraulichkeitsbezeichnungen unterstützt. Beispielsweise sehen sie eine **schützen** Schaltfläche anstelle eines **Vertraulichkeit** -Taste auf das Menüband und die Information Protection-Leiste wird standardmäßig angezeigt werden kann.

- Sie müssen auf lokale Datenspeicher mit Dokumenten, die vertrauliche Informationen überprüft oder klassifiziert und geschützt werden müssen. Sie stellen den Azure Information Protection-Client auf Servern führen Sie die Azure Information Protection-Überprüfung bereit.

### <a name="compare-the-clients"></a>Vergleichen Sie die clients

Verwenden Sie in der folgende Tabelle, um zu vergleichen, welche Funktionen von den beiden Azure Information Protection-Clients unterstützt werden.

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
|Unterstützung für nicht verbundene Computer mit manueller Verwaltung von Richtliniendateien:| Ja |Nein |
|HYOK-Unterstützung:| Ja | Nein<br /><br /> Bezeichnungen, die aus dem Azure-Portal migriert wurden und für den HYOK-Schutz konfiguriert sind, werden vom Azure Information Protection-Client für einheitliche Bezeichnungen angezeigt, wenden aber keinen Schutz an |
|Nutzungsprotokollierung in der Ereignisanzeige:| Ja | Nein|
|Vererbung von Bezeichnungen aus E-Mail-Anhängen:| Ja | Nein |
|Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen| Ja | Nein |
|[Anpassungen](client-admin-guide-customizations.md#available-advanced-client-settings) wie z.B. folgende:<br />– Standardbezeichnung für E-Mails<br />– Ermöglichen von benutzerdefinierten Berechtigungen <br />– S/MIME-Unterstützung<br />– Option zum Melden eines Problems| Ja | Nein |
|Überprüfung für lokale Datenspeicher:| Ja | Nein |
|Nachverfolgen und widerrufen:| Ja | Nein |
|Reiner Schutzmodus (keine Bezeichnungen):| Ja | Nein |
|Unterstützung für mehrere Sprachen:| Ja | Nein |
|Unterstützung für AD RMS:| Ja | Nur folgende Aktion wird unterstützt:<br /><br /> – Der Viewer kann geschützte Dokumente öffnen, wenn Sie die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\)) bereitstellen|

#### <a name="detailed-comparisons-for-the-clients"></a>Ein ausführlicher Vergleich für clients

Wenn beide Clients dasselbe Feature unterstützen, verwenden Sie in der folgende Tabelle, um einige Funktionsunterschiede zwischen den beiden Clients zu identifizieren.

|Funktionalität |Azure Information Protection-Client|Azure Information Protection<br /> Client für einheitliche Bezeichnungen|
|--------------|-----------------------------------|-----------------------------------------------------------|
|Setup:| Option zum Installieren der lokalen Demorichtlinie | Keine lokale Demorichtlinie|
|Auswahl und Anzeige von Bezeichnungen, wenn diese in Office-Apps angewendet werden:|Über die Schaltfläche **Schützen** im Menüband <br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|Über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|
|Verwalten der Information Protection-Leiste in Office-Apps:|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Schützen** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App ausgeblendet, aber in neu geöffneten Apps weiterhin automatisch angezeigt <br /><br /> Für Administratoren: <br /><br />– Richtlinieneinstellungen zum automatischen Anzeigen oder Ausblenden der Leiste beim ersten Öffnen einer App sowie zum Steuern, ob die Leiste bei neu geöffneten Apps automatisch ausgeblendet wird, nachdem ein Benutzer die Leiste in einer App ausgeblendet hat|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App und in neu geöffneten Apps ausgeblendet <br /><br />Für Administratoren: <br /><br />– Keine Richtlinieneinstellungen zum Verwalten der Leiste|
|Bezeichnungsfarbe: | Konfigurieren im Azure-Portal | Wird nach der Migration der Bezeichnung zu Office 365 beibehalten <br /><br /> Neue Bezeichnungen, die in den Admin-Centers erstellt wurden, haben keine Farbe.|
|Richtlinienaktualisierung: | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 24 Stunden | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 4 Stunden|
|Unterstützte Formate für PDF:| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung (Standardeinstellung) <br /><br /> – PPDF <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br /> <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz|
|Unterstützte Cmdlets:| Alle für [AzureInformatioProtection](/powershell/module/azureinformationprotection) dokumentierten Cmdlets | Set-AIPAuthentication nicht interaktive Sitzungen nicht unterstützt werden. <br /><br /> Set-AIPFileClassification und Set-AIPFileLabel unterstützen weder den Parameter *Owner* noch SharePoint Server-Bibliotheken <br /><br /> Darüber hinaus gibt es einen einzelnen Kommentar „Keine anzuwendende Bezeichnung“ für alle Szenarien, in denen keine Bezeichnung angewendet wird <br /><br /> Set-AIPFileLabel unterstützt den Parameter *EnableTracking* nicht <br /><br /> Get-AIPFileStatus gibt keine Bezeichnungsinformationen aus anderen Mandanten zurück und zeigt den Parameter *RMSIssuedTime* nicht an<br /><br />Darüber hinaus die *LabelingMethod* zeigt Parameter für die Get-AIPFileStatus **privilegierten** oder **Standard** anstelle von **manuelle** oder **Automatische**. Weitere Informationen finden Sie in der [Onlinedokumentation](/powershell/module/azureinformationprotection/get-aipfilestatus).|
|Aufforderungen zur Angabe einer Begründung (sofern konfiguriert) für Aktionen in Office: | Häufigkeit: Pro Datei <br /><br /> Herabsetzen der Vertraulichkeitsstufe <br /><br /> Entfernen einer Bezeichnung<br /><br /> Entfernen des Schutzes | Häufigkeit: Pro Sitzung <br /><br /> Herabsetzen der Vertraulichkeitsstufe<br /><br /> Entfernen einer Bezeichnung|
|Angewendete Bezeichnungsaktionen entfernen: | Benutzer wird zur Bestätigung aufgefordert <br /><br />Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App nicht automatisch angewendet  <br /><br />| Benutzer wird nicht zur Bestätigung aufgefordert<br /><br /> Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App automatisch angewendet|
|Automatische und empfohlene Bezeichnungen: | Wird im Azure-Portal als [Bezeichnungsbedingungen](../configure-policy-classification.md) mit integrierten Informationstypen und benutzerdefinierten Bedingungen konfiguriert, die Begriffe oder reguläre Ausdrücke verwenden <br /><br />Zu den Konfigurationsoptionen gehören: <br /><br />– Anzahl eindeutiger und nicht eindeutiger Vorkommnisse <br /><br /> – Mindestanzahl| Konfiguration in den Admin-Centers mit integrierten vertraulichen Informationstypen und [benutzerdefinierten Informationstypen](https://docs.microsoft.com/office365/securitycompliance/create-a-custom-sensitive-information-type)<br /><br />Zu den Konfigurationsoptionen gehören:  <br /><br />– Nur Anzahl eindeutiger Vorkommnisse <br /><br />– Mindest- und Höchstanzahl <br /><br />– Unterstützung von AND und OR bei Informationstypen <br /><br />– Wörterbuch mit Schlüsselwörtern<br /><br />– Anpassbare Vertraulichkeitsstufe und Zeichennähe|
|Anpassbare richtlinientipp für automatische und empfohlene Bezeichnungen: | Ja <br /><br />Verwenden Sie das Azure-Portal, um die Standardnachricht für Benutzer ersetzen | Nein <br /><br /> Obwohl die Admin Center eine Option aus, um einen Tipp für die benutzerdefinierte Richtlinie angeben haben, wird diese Option derzeit nicht vom einheitlichen bezeichnungs-Client unterstützt|
|Ändern der standardschutzebene von Dateien: | Ja <br /><br />Sie können [registrierungsänderungen](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) überschreiben die Standards von nativem und generischem Schutz | Nein |

Einen ausführlichen Vergleich der Unterschiede im Verhalten für bestimmte Protection-Einstellungen finden Sie unter [vergleichen das Verhalten der schutzeinstellungen für eine Bezeichnung](../configure-policy-migrate-labels.md#comparing-the-behavior-of-protection-settings-for-a-label).

#### <a name="features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client"></a>Funktionen, die in der Azure Information Protection unified bezeichnungs-Client nicht geplant.

Obwohl die einheitliche Bezeichnung Azure Information Protection-Client noch in Entwicklung ist, werden die folgenden Features und Unterschiede im Verhalten von der Azure Information Protection-Client nicht derzeit geplant in zukünftigen Versionen für Azure verfügbar sind Information Protection – einheitliche bezeichnungs-Client: 

- Benutzerdefinierte Berechtigungen in Office-Apps: Word, Excel und PowerPoint

- Nachverfolgen und widerrufen von Office-Apps und dem Datei-Explorer

- Titel und QuickInfo der Information Protection-Leiste

- Reiner Schutzmodus (keine Bezeichnungen)

- Schutz von PDF-Dokumenten im .ppdf-Format

- Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen

- Demorichtlinien

- Begründung für das Entfernen eines Schutzes

- Bestätigungsaufforderung **möchten Sie diese Bezeichnung löschen?** für Benutzer, wenn Sie die richtlinieneinstellung nicht zur Eingabe einer Begründung verwenden

- Hinzufügen einer Bezeichnung zu einem Office-Dokument mithilfe einer vorhandenen benutzerdefinierten Eigenschaft (die erweiterten Clienteinstellungen „SyncPropertyName“ und „SyncPropertyState“)

- Unabhängige PowerShell-Cmdlets zur Verbindung mit einem Rights Management-Dienst


#### <a name="parent-labels-and-their-sublabels"></a>Übergeordnete und untergeordnete Bezeichnungen 

Der Azure Information Protection-Client unterstützt keine Konfigurationen, die eine übergeordnete Bezeichnung mit untergeordneten Bezeichnungen festlegen. Diese Konfigurationen umfassen die Angabe einer Standardbezeichnung sowie einer Bezeichnung für die empfohlene oder automatische Klassifizierung. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, können Sie eine der untergeordneten Bezeichnungen angeben, aber nicht die übergeordnete Bezeichnung.

Aus Paritätsgründen unterstützt der Azure Information Protection-Client für einheitliche Bezeichnungen die Anwendung von übergeordneten Bezeichnungen mit untergeordneten Bezeichnungen ebenfalls nicht, auch wenn Sie diese Bezeichnungen in den Admin-Centers auswählen können. In diesem Szenario wendet der Azure Information Protection-Client für einheitliche Bezeichnungen die übergeordnete Bezeichnung nicht an.

## <a name="see-also"></a>Siehe auch
Weitere Informationen zum Bereitstellen und Verwenden dieser Clients finden Sie in der folgenden Dokumentation:

- [Azure Information Protection-Client](AIP-client.md)

- [Azure Information Protection-Client für einheitliche Bezeichnungen](unifiedlabelingclient-version-release-history.md)

- [Hinweise zur Bereitstellung des RMS-Clients](client-deployment-notes.md)

Der Azure Information Protection-Client kann zwar mit AD RMS verwendet werden, eignet sich aber am besten für die Arbeit mit den zugehörigen Azure-Diensten: Azure Information Protection und zugehöriger Datenschutzdienst, Azure Rights Management. Einen Vergleich der Dienstseite von Azure Information Protection finden Sie unter [Vergleich von Azure Information Protection und AD RMS](../compare-on-premise.md).
