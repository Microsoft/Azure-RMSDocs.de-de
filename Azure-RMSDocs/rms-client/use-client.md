---
title: Der Client für Azure Information Protection – AIP
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: b51ebdb55212e2a29b6a8ce950bd69d578e98ed9
ms.sourcegitcommit: b92f60a87f824fc2da1e599f526898e3a0c919c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2019
ms.locfileid: "67343669"
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- Der Client kann es sich um den Azure Information Protection-Client (klassisch), der Azure Information Protection unified bezeichnungs-Client oder Rights Management-Client sein. Je nachdem, was dieser Clients Sie verwenden, integriert es Anwendungen, die Sie auf Computern und mobilen Geräten ausführen. 
- Der Dienst wird in der Cloud (Azure Information Protection verwendet den Azure Rights Management-Dienst für den Schutz von Daten) oder lokal (Active Directory Rights Management Services, besser bekannt als AD RMS) ausgeführt. 

Der Azure Information Protection-Client (klassisch) und der einheitliche Bezeichnung Azure Information Protection-Client unterstützt die Klassifizierung und Schutz mit Bezeichnungen. Die klassische Client unterstützt auch Schutz ohne Bezeichnung. Beide Clients mit Office-Anwendungen integrieren und müssen separat installiert werden.

Der Rights Management (RMS)-Client wird automatisch mit einigen Anwendungen wie Office-Anwendungen, die Azure Information Protection-Client (klassisch) und Azure Information Protection unified bezeichnungs-Client und RMS-fähige Anwendungen installiert werden. von Softwareherstellern. Er kann jedoch auch [eigenständig installiert](https://www.microsoft.com/en-us/download/details.aspx?id=38396) werden, um das [Synchronisieren von Dateien von IRM-geschützten Bibliotheken und OneDrive for Business](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668) zu unterstützen sowie für Entwickler, die den Rights Management-Schutz in branchenspezifische Anwendungen integrieren möchten.

## <a name="choose-which-azure-information-protection-client-to-use"></a>Auswählen des zu verwendenden Azure Information Protection-Clients

Die **Azure Information Protection-Client (klassisch)** Bezeichnungen und Einstellungen im Azure-Portal heruntergeladen. Weitere Informationen zu dieser finden Sie unter den [Azure Information Protection-Client: Versionsveröffentlichungsverlauf und Supportrichtlinie](client-version-release-history.md).

Der **Azure Information Protection-Client für einheitliche Bezeichnungen** dient zum Herunterladen von Bezeichnungen und Richtlinieneinstellungen aus den Admin-Centers: Das Office 365 Security & Compliance Center, das Microsoft 365 Security Center, und das Microsoft 365 Compliance Center. Weitere Informationen zu dieser finden Sie unter den [Azure Information Protection – einheitliche bezeichnungs-Client: Informationen zum Release](unifiedlabelingclient-version-release-history.md).

Welchen Client sollten Sie installieren?

- Installieren Sie die aktuelle verfügbare Version des Azure Information Protection unified bezeichnungs-Clients für Bezeichnungen, die können auch sein, die von Mac OS, iOS und Android verwendet und wenn Sie nicht, erweiterte Funktionen benötigen, z. B. erweiterte Clienteinstellungen, benutzerdefinierte Berechtigungen, eine lokale Key (HYOK), oder die Überprüfung für lokale Datenspeicher.
    
    Die Vorschauversion des Azure Information Protection unified bezeichnungs-Clients unterstützt, erweiterte Clienteinstellungen und benutzerdefinierte Berechtigungen keine lokale Key (HYOK) oder für die Überprüfung für die lokalen Daten speichert.

- Installieren Sie den Azure Information Protection-Client (klassisch) Wenn Sie eine Version des Clients benötigen im allgemeinen Verfügbarkeit mit erweiterten Features, die noch nicht im aktuellen allgemeiner Verfügbarkeit einheitliche bezeichnungs-Client verfügbar sind. Ihr Nachteil besteht darin, dass die Bezeichnungen auf anderen Clientplattformen verwendet werden können.

Derzeit aufweisen nicht die klassische Client und der einheitliche bezeichnungs Client Parität für ihre Funktionen. Allerdings mit der aktuellen Vorschau sind diese Lücke wird geschlossen, und Sie erwarten können neue Features, die nur für den einheitlichen bezeichnungs-Client hinzugefügt werden. Aus diesem Grund wird empfohlen, dass Sie den einheitlichen bezeichnungs-Client bereitstellen, wenn die aktuellen Features und Funktionalität Ihrer geschäftlichen Anforderungen zu erfüllen. Falls nicht, oder wenn Sie Bezeichnungen im Azure-Portal konfiguriert haben, die Sie noch nicht getan haben [beim einheitlichen bezeichnungs Store migriert](../configure-policy-migrate-labels.md), verwenden Sie die klassische Client.

Sie können auch beide Clients in der gleichen Umgebung zur Unterstützung von unterschiedlichen geschäftsanforderungen, installieren, wie im folgenden Beispiel gezeigt. In diesem Szenario wird empfohlen, dass Sie die Bezeichnungen im Azure-Portal migrieren, sodass beide Sätze von Clients über den gleichen Satz von Bezeichnungen zur Vereinfachung der Verwaltung verwenden.

##### <a name="example-deployment-strategy"></a>Beispiel-Bereitstellungsstrategie:

- Für die Mehrheit der Benutzer stellen Sie den Azure Information Protection unified bezeichnungs-Client bereit, da die meisten Benutzer nicht benötigen, Features oder Funktionen, die nur mit dem Azure Information Protection-Client (klassisch) verfügbar sind. 
    
    Einkaufserlebnis Bezeichnung ist für diese Benutzer müssen sehr ähnlich, wenn sie auch Geräte, auf denen Mac OS, iOS und Android ausgeführt haben und diese Geräte eine Version von Office verfügt haben, vertraulichkeitsbezeichnungen unterstützt.

- Nur für sich selbst installieren Sie die Vorschauversion des einheitlichen bezeichnungs-Client die neuen Funktionen zu testen, die benutzerdefinierte Berechtigungen und erweiterte Clienteinstellungen.

- Stellen Sie für eine Teilmenge von Benutzern die klassische Client aus, da diese Benutzer, dass Bezeichnungen, die zum Anwenden von aufzunehmen erfordern, Ihre eigenen Key (HYOK)-Schutz oder die Eingabeaufforderung für benutzerdefinierte Berechtigungen.
    
    Diese Benutzer verfügen über zusätzliche Features und Funktionen, aber eine etwas abweichende Optionen, wenn sie auch über Geräte, auf denen Mac OS, iOS und Android ausgeführt wird, und diese Geräte haben eine Version von Office verfügt, vertraulichkeitsbezeichnungen unterstützt. Beispielsweise sehen sie eine **schützen** Schaltfläche anstelle eines **Vertraulichkeit** -Taste auf das Menüband und die Information Protection-Leiste wird standardmäßig angezeigt werden kann.

- Sie müssen auf lokale Datenspeicher mit Dokumenten, die vertrauliche Informationen überprüft oder klassifiziert und geschützt werden müssen. Sie haben den klassischen Client auf Servern führen Sie die Azure Information Protection-Überprüfung bereitstellen.

### <a name="compare-the-clients"></a>Vergleichen Sie die clients

Verwenden Sie in der folgende Tabelle, um zu vergleichen, welche Funktionen von den beiden Azure Information Protection-Clients unterstützt werden.

|Komponente|Klassische client|einheitliche bezeichnungs-client|
|-------|-----------------------------------|----------------------------------------------------|
|Bezeichnungsaktionen: Manuell, empfohlen, automatisch| Ja | Ja |
|Zentrale Berichterstellung (Analysen):| Ja | Ja mit Einschränkungen:<br /><br /> – Keine Unterstützung für [inhaltsübereinstimmungen](../reports-aip.md#content-matches-for-deeper-analysis) |
|Einstellungen zurücksetzen und Protokolle exportieren:| Ja | Ja |
|Benutzerdefinierte Berechtigungen:| Ja | Ja mit Einschränkungen: <br /><br />– Bei Outlook nur (Do Not Forward): Unterstützt<br /><br />– Für Word, Excel, PowerPoint und Datei-Explorer: Mit der Preview-Client unterstützt werden, wenn Sie die Bezeichnung im Azure-Portal konfigurieren |
|Kundenspezifische Berechtigungen:| Ja | Datei-Explorer und PowerShell (Vorschauversion) <br /><br /> In Office-Apps können Benutzer alternativ auch **Dateiinfo** > **Dokument schützen** > **Zugriff einschränken** auswählen |
|Information Protection-Leiste in Office-Apps:| Ja | Ja mit Einschränkungen:<br /><br /> – kein Titel oder anpassbare QuickInfo<br /><br /> – die Bezeichnungsfarbe wird für die angewendete Bezeichnung nicht angezeigt|
|Bezeichnungen können optische Kennzeichnungen anwenden (Kopfzeile, Fußzeile, Wasserzeichen):| Ja | Ja mit Einschränkungen:<br /><br /> – Kopf- und Fußzeilen unterstützen keine Variablen für dynamische Werte. <br /><br /> – Das Verwenden unterschiedlicher optischer Kennzeichnungen für Word, Excel, PowerPoint und Outlook wird nicht unterstützt.|
|Datei-Explorer, Rechtsklickaktionen:| Ja | Ja mit Einschränkungen:<br /><br /> – Kein Schutz für PDF-Dokumente im PPDF-Format <br /><br />  – Keine Unterstützung für den reinen Schutzmodus|
|Viewer für geschützte Dateien:| Ja | Ja mit Einschränkungen:<br /><br /> -Bei generisch geschützte Dateien (Erweiterung ".pFile"), im Gegensatz zu den Viewer aus der klassischen Client besteht es keine Möglichkeit, die ursprünglich geöffnete Datei zu speichern.|
|PowerShell-Befehle:| Ja | Ja mit Einschränkungen:<br /><br />– Enthaltene Cmdlets: [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus), [New-AIPCustomPermissions](/powershell/module/azureinformationprotection/New-AIPCustomPermissions) (Preview-Client), [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification), [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel), [ Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) <br /><br />– Derzeit können Sie Schutz von Dateien des Containers (Zip, RAR, 7Z, Meldung und PST) nicht entfernen|
|Offlineunterstützung für Schutzaktionen:| Ja | Ja mit Einschränkungen: <br /><br />– Bei Datei-Explorer und PowerShell-Befehlen muss der Benutzer mit dem Internet verbunden sein, um Dateien zu schützen |
|Unterstützung für nicht verbundene Computer mit manueller Verwaltung von Richtliniendateien:| Ja |Nein |
|HYOK-Unterstützung:| Ja | Nein<br /><br /> Bezeichnungen, die aus dem Azure-Portal migriert wurden und für den HYOK-Schutz konfiguriert sind, werden vom Azure Information Protection-Client für einheitliche Bezeichnungen angezeigt, wenden aber keinen Schutz an |
|Nutzungsprotokollierung in der Ereignisanzeige:| Ja | Nein|
|Vererbung von Bezeichnungen aus E-Mail-Anhängen:| Ja | Ja (nur vorschauclient) |
|Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen| Ja | Nein |
|[Anpassungen](client-admin-guide-customizations.md#available-advanced-client-settings) wie z.B. folgende:<br />– Standardbezeichnung für E-Mails<br />– Ermöglichen von benutzerdefinierten Berechtigungen <br />– S/MIME-Unterstützung<br />– Option zum Melden eines Problems| Ja | Ja, mithilfe von [PowerShell](clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) (nur vorschauclient) |
|Überprüfung für lokale Datenspeicher:| Ja | Nein |
|Nachverfolgen und widerrufen:| Ja | Nein |
|Reiner Schutzmodus (keine Bezeichnungen) mithilfe von Vorlagen:| Ja | Nein |
|Unterstützung für mehrere Sprachen:| Ja | Nein |
|Unterstützung für AD RMS:| Ja | Nur folgende Aktion wird unterstützt:<br /><br /> – Der Viewer kann geschützte Dokumente öffnen, wenn Sie die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\)) bereitstellen|

#### <a name="detailed-comparisons-for-the-clients"></a>Ein ausführlicher Vergleich für clients

Wenn beide Clients dasselbe Feature unterstützen, verwenden Sie in der folgende Tabelle, um einige Funktionsunterschiede zwischen den beiden Clients zu identifizieren.

|Funktionalität |Klassische client|einheitliche bezeichnungs-client|
|--------------|-----------------------------------|-----------------------------------------------------------|
|Setup:| Option zum Installieren der lokalen Demorichtlinie | Keine lokale Demorichtlinie|
|Auswahl und Anzeige von Bezeichnungen, wenn diese in Office-Apps angewendet werden:|Über die Schaltfläche **Schützen** im Menüband <br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|Über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|
|Verwalten der Information Protection-Leiste in Office-Apps:|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Schützen** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App ausgeblendet, aber in neu geöffneten Apps weiterhin automatisch angezeigt <br /><br /> Für Administratoren: <br /><br />– Richtlinieneinstellungen zum automatischen Anzeigen oder Ausblenden der Leiste beim ersten Öffnen einer App sowie zum Steuern, ob die Leiste bei neu geöffneten Apps automatisch ausgeblendet wird, nachdem ein Benutzer die Leiste in einer App ausgeblendet hat|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App und in neu geöffneten Apps ausgeblendet <br /><br />Für Administratoren: <br /><br />-PowerShell Einstellung aus, um die Leiste zu verwalten (nur vorschauclient)|
|Bezeichnungsfarbe: | Konfigurieren im Azure-Portal | Nach der Label-Migration zu Office 365 beibehalten werden und mit PowerShell konfigurierbar <br /><br /> Neue Bezeichnungen, die in das Admin Center erstellt haben sich nicht auf eine Farbe, aber Farben können konfiguriert werden, mithilfe von [PowerShell](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)|
|Richtlinienaktualisierung: | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 24 Stunden | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 4 Stunden|
|Unterstützte Formate für PDF:| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung (Standardeinstellung) <br /><br /> – PPDF <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br /> <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz|
|Unterstützte Cmdlets:| Alle für [AzureInformatioProtection](/powershell/module/azureinformationprotection) dokumentierten Cmdlets | Set-AIPAuthentication unterstützt nicht interaktive Sitzungen, mit der Preview-client <br /><br /> Set-AIPFileClassification und Set-AIPFileLabel unterstützen weder den Parameter *Owner* noch SharePoint Server-Bibliotheken <br /><br /> Darüber hinaus gibt es einen einzelnen Kommentar „Keine anzuwendende Bezeichnung“ für alle Szenarien, in denen keine Bezeichnung angewendet wird <br /><br /> Set-AIPFileClassification im Preview-Client unterstützt die *"WhatIf"* an, damit sie im Suchmodus ausgeführt werden kann <br /><br /> Set-AIPFileLabel unterstützt den Parameter *EnableTracking* nicht <br /><br /> Get-AIPFileStatus gibt keine Bezeichnungsinformationen aus anderen Mandanten zurück und zeigt den Parameter *RMSIssuedTime* nicht an<br /><br />Darüber hinaus die *LabelingMethod* zeigt Parameter für die Get-AIPFileStatus **privilegierten** oder **Standard** anstelle von **manuelle** oder **Automatische**. Weitere Informationen finden Sie in der [Onlinedokumentation](/powershell/module/azureinformationprotection/get-aipfilestatus).|
|Aufforderungen zur Angabe einer Begründung (sofern konfiguriert) für Aktionen in Office: | Häufigkeit: Pro Datei <br /><br /> Herabsetzen der Vertraulichkeitsstufe <br /><br /> Entfernen einer Bezeichnung<br /><br /> Entfernen des Schutzes | Häufigkeit: Pro Sitzung <br /><br /> Herabsetzen der Vertraulichkeitsstufe<br /><br /> Entfernen einer Bezeichnung|
|Angewendete Bezeichnungsaktionen entfernen: | Benutzer wird zur Bestätigung aufgefordert <br /><br />Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App nicht automatisch angewendet  <br /><br />| Benutzer wird nicht zur Bestätigung aufgefordert<br /><br /> Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App automatisch angewendet|
|Automatische und empfohlene Bezeichnungen: | Wird im Azure-Portal als [Bezeichnungsbedingungen](../configure-policy-classification.md) mit integrierten Informationstypen und benutzerdefinierten Bedingungen konfiguriert, die Begriffe oder reguläre Ausdrücke verwenden <br /><br />Zu den Konfigurationsoptionen gehören: <br /><br />– Anzahl eindeutiger und nicht eindeutiger Vorkommnisse <br /><br /> – Mindestanzahl| Konfiguration in den Admin-Centers mit integrierten vertraulichen Informationstypen und [benutzerdefinierten Informationstypen](https://docs.microsoft.com/office365/securitycompliance/create-a-custom-sensitive-information-type)<br /><br />Zu den Konfigurationsoptionen gehören:  <br /><br />– Nur Anzahl eindeutiger Vorkommnisse <br /><br />– Mindest- und Höchstanzahl <br /><br />– Unterstützung von AND und OR bei Informationstypen <br /><br />– Wörterbuch mit Schlüsselwörtern<br /><br />– Anpassbare Vertraulichkeitsstufe und Zeichennähe|
|Anpassbare richtlinientipp für automatische und empfohlene Bezeichnungen: | Ja <br /><br />Verwenden Sie das Azure-Portal, um die Standardnachricht für Benutzer ersetzen | Nein <br /><br /> Obwohl die Admin Center eine Option aus, um einen Tipp für die benutzerdefinierte Richtlinie angeben haben, wird diese Option derzeit nicht vom einheitlichen bezeichnungs-Client unterstützt|
|Ändern der standardschutzebene von Dateien: | Ja <br /><br />Sie können [registrierungsänderungen](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) überschreiben die Standards von nativem und generischem Schutz | Nein |

Einen ausführlichen Vergleich der Unterschiede im Verhalten für bestimmte Protection-Einstellungen finden Sie unter [vergleichen das Verhalten der schutzeinstellungen für eine Bezeichnung](../configure-policy-migrate-labels.md#comparing-the-behavior-of-protection-settings-for-a-label).

#### <a name="features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client"></a>Funktionen, die in der Azure Information Protection unified bezeichnungs-Client nicht geplant.

Obwohl die einheitliche Bezeichnung Azure Information Protection-Client noch in Entwicklung ist, werden die folgenden Features und Unterschiede im Verhalten von der klassischen Client nicht derzeit geplant in zukünftigen Versionen für den einheitlichen bezeichnungs-Client verfügbar sein: 

- Benutzerdefinierte Berechtigungen in Office-Apps: Word, Excel und PowerPoint

- Nachverfolgen und widerrufen von Office-Apps und dem Datei-Explorer

- Titel und QuickInfo der Information Protection-Leiste

- Reiner Schutzmodus (keine Bezeichnungen) mithilfe von Vorlagen

- Schutz von PDF-Dokumenten im .ppdf-Format

- Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen

- Demorichtlinien

- Begründung für das Entfernen eines Schutzes

- Bestätigungsaufforderung **möchten Sie diese Bezeichnung löschen?** für Benutzer, wenn Sie die richtlinieneinstellung nicht zur Eingabe einer Begründung verwenden

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

Obwohl der Azure Information Protection-Client (klassisch) mit AD RMS verwendet werden kann, wird dieser Client am besten für die Arbeit mit der Azure-Diensten geeignet; Azure Information Protection und seine Datenschutzdienste, Azure Rights Management. Einen Vergleich der Dienstseite von Azure Information Protection finden Sie unter [Vergleich von Azure Information Protection und AD RMS](../compare-on-premise.md).
