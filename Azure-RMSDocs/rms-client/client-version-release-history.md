---
title: "Azure Information Protection-Client&colon; Verlauf der Versionsveröffentlichungen"
description: "Erfahren Sie, was in einer Version des Azure Information Protection-Clients für Windows neu ist oder geändert wurde."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2b6e6e4d824c8f76be605d9e728c0405aba960e5
ms.sourcegitcommit: 2f1936753adf8d2fbea780d0a3878afa621daab5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2017
---
# <a name="azure-information-protection-client-version-release-history"></a>Azure Information Protection-Client: Verlauf der Versionsveröffentlichungen

>*Gilt für: Azure Information Protection*

Das Azure Information Protection-Team aktualisiert den Azure Information Protection-Client regelmäßig, um Korrekturen und neue Funktionen zu implementieren. Der Client befindet sich im Microsoft Update-Katalog (Kategorie: **Azure Information Protection**). Die aktuelle allgemein verfügbare Releaseversion und die anstehende Version (Vorschauversion) können Sie stets aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie die Vorschauversionen stattdessen, um neue Funktionalität oder Fixes kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein werden. 

Den folgenden Informationen können Sie entnehmen, welche Neuerungen oder Änderungen für eine allgemein verfügbare Version vorgenommen wurden. Die neueste Version ist zuerst aufgeführt. Änderungen in der aktuellen Vorschauversion finden Sie in den Informationen auf der Downloadseite.

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn ein Problem mit dem Azure Information Protection-Client auftreten sollte, vergewissern Sie sich zuerst, dass es sich nicht um ein Problem mit der neuesten allgemein verfügbaren Release handelt. Wenn dies der Fall, überprüfen Sie die aktuelle Vorschauversion.
>  
> Falls das Problem bestehen bleibt, finden Sie entsprechende Informationen unter [Supportoptionen und Communityressourcen](../get-started/information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

## <a name="version-110560"></a>Version 1.10.56.0

**Veröffentlicht**: 18.9.2017

Diese Version umfasst die MSIPC-Version 1.0.3219.0619 des RMS-Clients.

**Neue Features**:

- Unterstützung für Bezeichnungen, für die benutzerdefinierte Aktionen konfiguriert sind. Bei Outlook wendet diese Bezeichnung automatisch die Outlook-Option „Nicht weiterleiten“ an. Bei Word, Excel, PowerPoint und dem Datei-Explorer fordert diese Bezeichnung den Benutzer dazu auf, benutzerdefinierte Berechtigungen anzugeben. Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](../deploy-use/configure-policy-protection.md).

- Unterstützung für die neuen Office 365-DLP-Bedingungen, die Sie für eine Bezeichnung konfigurieren können. Weitere Informationen finden Sie unter [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](../deploy-use/configure-policy-classification.md).

- Bezeichnungen werden zusätzlich zu der Anzeige auf der Information Protection-Leiste über die Schaltfläche **Schützen** auf dem Office-Menüband angezeigt. 

- Unterstützung für erweiterte Clientkonfigurationen, die Sie im Azure-Portal konfigurieren können. Diese Konfigurationen umfassen Folgendes:
    
    - [Schaltfläche „Nicht weiterleiten“ in Outlook ausblenden](../rms-client/client-admin-guide-customizations.md#hide-the-do-not-forward-button-in-outlook)
    
    - [Die Optionen für benutzerdefinierte Berechtigungen für Benutzer nicht verfügbar machen](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-unavailable-to-users)
    
    - [Die Azure Information Protection-Leiste dauerhaft ausblenden](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-unavailable-to-users)
    
    - [Die empfohlene Klassifizierung in Outlook aktivieren](../rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook)

- Bei PowerShell: Unterstützung für die nicht interaktive Bezeichnung von Dateien unter Verwendung der neuen PowerShell-Cmdlets [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) und [Clear-AIPAuthentication](/powershell/module/azureinformationprotection/clear-aipauthentication). Weitere Informationen zur Verwendung dieser Cmdlets finden Sie im [PowerShell-Abschnitt](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) des Administratorhandbuchs.

- Für die PowerShell-Cmdlets [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) und [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification) gibt es die neuen Parameter **Owner** und **PreserveFileDetails**. Mit diesen Parametern können Sie eine E-Mail-Adresse für die benutzerdefinierte Eigenschaft „Owner“ angeben und das Datum für Dokumente, die Sie bezeichnen, unverändert lassen.

**Fixes**:

Fixes für Stabilität und für bestimmte Szenarios, die Folgendes umfassen:

- Unterstützung für den generischen Schutz von großen Dateien, die zuvor bei einer Größe von über 1 GB zu Beschädigungen führen konnten. Nun ist die Dateigröße nur durch den verfügbaren Festplattenspeicherplatz und Arbeitsspeicherplatz eingeschränkt. Weitere Informationen zu Einschränkungen bei der Dateigröße finden Sie unter [Für den Schutz unterstützte Dateigrößen](client-admin-guide-file-types.md#file-sizes-supported-for-protection) im Administratorhandbuch.

- Die Anzeige des Azure Information Protection-Clients öffnet geschützte PDF-Dateien (.ppdf) schreibgeschützt.

- Unterstützung für die Bezeichnung und den Schutz von Dateien, die auf dem SharePoint-Server gespeichert sind.

- Wasserzeichen unterstützen jetzt mehrere Zeilen. Darüber hinaus werden visuelle Kennzeichnungen jetzt [nur beim ersten Speichern](../deploy-use/configure-policy-markings.md#when-visual-markings-are-applied) angewendet, anstatt jedes Mal, wenn ein Dokument gespeichert wird.

- Die Option **Diagnose ausführen** im Dialogfeld **Hilfe und Feedback** wird durch **Einstellungen zum Zurücksetzen** ersetzt. Das Verhalten für diese Aktion wurde geändert, sodass das Abmelden des Benutzers und das Löschen der Azure Information Protection-Richtlinie mit eingeschlossen ist. Weitere Informationen finden Sie unter [Weitere Informationen über die Zurücksetzungsoption für die aktuelle Vorschauversion des Azure Information Protection-Clients](..\rms-client\client-admin-guide.md#more-information-about-the-reset-settings-option) im Administratorhandbuch.

- Unterstützung für die Proxyauthentifizierung.

Fixes für eine bessere Benutzererfahrung, die Folgendes umfassen:

- E-Mail-Validierung, wenn Benutzer benutzerdefinierte Berechtigungen angeben. Darüber hinaus können jetzt durch Drücken der EINGABETASTE mehrere E-Mail-Adressen angegeben werden.

- Die übergeordnete Bezeichnung wird nicht angezeigt, wenn ihre untergeordneten Bezeichnungen für den Schutz konfiguriert sind und der Client nicht über eine Edition von Office verfügt, die den Schutz unterstützt. 

## <a name="version-172100"></a>Version 1.7.210.0

**Veröffentlicht**: 06.06.2017

Diese Version umfasst die MSIPC-Version 1.0.2217.1 des RMS-Clients.

**Neue Features**:

- Neues PowerShell-Cmdlet [Set-AIPFileClassification](/powershell/module/azureinformationprotection/Set-AIPFileClassification). Wenn Sie dieses Cmdlet ausführen, werden die Dateiinhalte überprüft und die Bezeichnungen werden gemäß den Bedingungen, die Sie in der Azure Information Protection-Richtlinie angeben, automatisch auf nicht bezeichnete Dateien angewendet.

**Fixes**:

- Alle Bezeichnungs- und Klassifizierungs-Cmdlets werden nun auf Computern unterstützt, die nicht mit dem Internet verbunden sind, aber eine gültige Azure Information Protection-Richtlinie aufweisen.

- Aus Konsistenzgründen wird ein Ausgabeparameter des Cmdlets [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) von britischem Englisch (**IsLabelled**) in amerikanisches Englisch (**IsLabeled**) geändert. Wenn Sie Skripts oder automatisierte Prozesse verwenden, die nach diesem Parameter suchen, aktualisieren Sie die Schreibweise dieses Parameters.

- Die allgemeinen Fehlerbehebungen zur Verbesserung der Stabilität umfassen Folgende:

    - Für Outlook: Fehlerbehebungen für Abstürze, hohen Speicherverbrauch und Anzeigeprobleme bei Menüs.
    
    - Für Word, Excel und PowerPoint: Fehlerbehebungen für hohe CPU-Auslastung, Anzeigeprobleme beim Speichern großer Excel-Dateien oder keine Reaktion der Anwendung. 
    
    Um die Leistung von Office 2016 bei SharePoint Online und OneDrive for Business zu verbessern, werden bei diesen Anwendungen außerdem automatische und empfohlene Bezeichnungen beim Schließen der Datei statt beim Speichern (beim automatischen Speichern oder Speichervorgang durch den Benutzer) angewendet. Gleichermaßen gilt: Wenn die Einstellung **All documents and email must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung haben) aktiviert ist, werden Benutzer erst aufgefordert, eine Bezeichnung auszuwählen, wenn die Datei geschlossen wird. Die Ausnahme gilt für Word 2016 und Excel 2016, wenn der Benutzer die Option **Speichern unter** wählt. Diese Aktion löst dann diese Bezeichnungsverhalten aus, sofern diese konfiguriert sind. 

## <a name="version-14210"></a>Version 1.4.21.0

**Veröffentlicht**: 15.03.2017

**Geänderte Anforderungen**:

In der vorherigen Version wurde die neue Anforderung von Microsoft .NET Framework 4.6.2 für den vollständigen Client eingeführt. Sie können diese Anforderung mit dem benutzerdefinierten Installationsparameter **DowngradeDotNetRequirement** umgehen. Diese Vorgehensweise wird nicht empfohlen. Weitere Informationen finden Sie im [Abschnitt zur Clientinstallation](client-admin-guide.md#how-to-install-the-azure-information-protection-client-for-users) des Administratorhandbuchs.

**Neue Features**:

- Die Möglichkeit, benutzerdefinierte Berechtigungen aus Ihrer Office-Anwendung festzulegen, sodass Sie den Schutz nur für sich selbst, für externe Gruppen oder für alle Benutzer in einer anderen Organisation einrichten können. Weitere Informationen finden Sie unter [Festlegen von benutzerdefinierten Berechtigungen für ein Dokument](client-classify-protect.md#set-custom-permissions-for-a-document) im Benutzerhandbuch.
    
- PDF-Dateien unterstützen jetzt Bezeichnungen, die nur für Klassifizierungen gelten.

- Der Viewer unterstützt jetzt Optionen wie Suchen, Zoomen und Drehen für PDF-Dateien. Um diese Optionen zu verwenden, klicken Sie mit der rechten Maustaste auf die Datei, wenn sie im Viewer angezeigt wird.

**Fixes**:

- Unterstützung für zugeordnete Laufwerke zum Klassifizieren und Schützen von Dateien.

- Unterstützung für große Dateien (größer als 250 MB) in der Anzeige des Azure Information Protection-Clients. 

- Wenn HYOK konfiguriert ist, kann Outlook Bezeichnungen anwenden, die für die Verwendung von Azure Rights Management-Vorlagen oder AD RMS-Vorlagen konfiguriert sind.

## <a name="version-131552"></a>Version 1.3.155.2

**Veröffentlicht**: 08.02.2017

**Neue Anforderungen**:

Microsoft .NET Framework

- Diese Version des Azure Information Protection-Clients erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Nach Abschluss der Installation des Azure Information Protection-Clients ist möglicherweise ein Neustart des Computers erforderlich.

- Wenn der Azure Information Protection-Viewer separat installiert wird, ist Microsoft .NET Framework 4.5.2 oder höher erforderlich. Wenn diese Version fehlt, wird sie vom Installationsprogramm nicht heruntergeladen oder installiert.

**Neue Features**:

- Ein neuer einheitlicher Client, der die Features der Rights Management-Freigabeanwendung für Windows mit dem Azure Information Protection-Client kombiniert. Dies umfasst Folgendes:
    
    - Integration mit dem Windows-Datei-Explorer (Rechtsklick), um Bezeichnungen und den Schutz anzuwenden. Unterstützt zusätzliche Dateiformate und die Auswahl mehrerer Dateien.
    - Ein Viewer für geschützte Dokumente (umfasst geschützte PDF-Dateien für SharePoint).
    - PowerShell-Cmdlets zum Abrufen und Festlegen von Bezeichnungen für Dateien, die lokal oder auf Netzwerkfreigaben gespeichert werden. Diese Cmdlets werden mit den Cmdlets installiert, die zuvor mit dem RMS Protection Tool (RMSProtection-Modul) ausgeliefert wurden.
    - Clientverwendungsprotokolle, die entsprechende Informationen aufzeichnen, z. B. welche Bezeichnung auf welche Weise von welchem Benutzer angewendet wurde.

Diese Clientversion ist die [allgemein verfügbare Version](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/) für den Vorschauclient, der im Dezember 2016 erstmals angekündigt wurde. Weitere Informationen zu dieser Version des Clients finden Sie in den folgenden Handbüchern:

- [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)

- [Azure Information Protection-Benutzerhandbuch](client-user-guide.md)


## <a name="version-1240"></a>Version 1.2.4.0

**Veröffentlicht**: 27.10.2016

**Neues Feature**:

- Diagnosetests und eine Option zum Zurücksetzen, die ein Benutzer in einer Office-Anwendung ausführen kann, wenn der Azure Information Protection-Client installiert ist: Klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, dann auf **Hilfe und Feedback** und schließlich auf **Diagnose ausführen**. 

    Weitere Informationen zu dieser Option finden Sie im Abschnitt [Zusätzliche Überprüfungen](client-admin-guide.md#additional-checks-and-troubleshooting) im Administratorhandbuch.

**Fixes**:

- Die Clientinstallation wird abgeschlossen, wenn der Windows Update-Dienst deaktiviert wird.

- Wenn Sie in Office 2016 ein Dokument speichern und eine Bezeichnung für eine Kopf- oder Fußzeile konfiguriert ist, springt der Cursor nicht zur Kopf- oder Fußzeile.

- Automatische Klassifizierung funktioniert in Word für Text in gebündelten Textfeldern.


## <a name="version-11230"></a>Version 1.1.23.0

**Veröffentlicht**: 01.10.2016

Allgemeine Verfügbarkeit.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren und Verwenden des Clients:

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]