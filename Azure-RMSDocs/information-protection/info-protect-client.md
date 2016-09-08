---
title: Installieren des Azure Information Protection-Clients | Azure Rights Management
description: "Um Dokumente und E-Mail-Nachrichten mithilfe von Azure Information Protection zu klassifizieren, müssen Sie zunächst den Azure Information Protection-Client installieren. Durch diese Installation wird eine Information Protection-Leiste zu Ihren Office-Anwendungen (Word, Excel, PowerPoint, Outlook) hinzugefügt, auf der die Klassifizierungsbezeichnungen für Ihre Organisation angezeigt werden. Außerdem wird auf der Registerkarte „Start“ (Word, Excel, PowerPoint) eine neue Gruppe „Schutz“ mit einer Schaltfläche „Schützen“ angezeigt."
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: ab8388e03803d32a6891785f905a1ddef796bc25


---

# Installieren des Azure Information Protection-Clients

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Um Dokumente und E-Mail-Nachrichten mithilfe von Azure Information Protection zu klassifizieren, müssen Sie zunächst den Azure Information Protection-Client installieren. Durch diese Installation wird eine Information Protection-Leiste zu Ihren Office-Anwendungen (Word, Excel, PowerPoint, Outlook) hinzugefügt, auf der die Klassifizierungsbezeichnungen für Ihre Organisation angezeigt werden. Außerdem wird auf der Registerkarte **Start** (Word, Excel, PowerPoint) eine neue Gruppe **Protection** (Schutz) mit einer Schaltfläche **Protect** (Schützen) angezeigt:

Die folgende Abbildung zeigt diese Information Protection-Leiste sowie die Bezeichnungen der [Standardrichtlinie](configure-policy-default.md):

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/info-protect-bar-default.png)

Laden Sie den Azure Information Protection-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunter.

Überprüfen Sie vor der Installation des Clients, ob Sie über die erforderlichen Betriebssystemversionen und Anwendungen verfügen: [Voraussetzungen für Azure Information Protection](requirements-azure-infoprotect.md).


## Manuelle Installation des Azure Information Protection-Clients

1. Nachdem Sie [den Client heruntergeladen haben](https://www.microsoft.com/en-us/download/details.aspx?id=53018), führen Sie **AZInfoProtection.exe** aus, und befolgen Sie die Aufforderungen zum Installieren des Clients. Für diese Installation sind lokale Administratorrechte erforderlich.

    Wenn Sie sich nicht mit Office 365 oder Azure Active Directory verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer Demorichtlinie, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt. 

2. So beginnen Sie mit der Verwendung des Azure Information Protection-Clients: Wenn auf Ihrem Computer Office 2010 ausgeführt wird, starten Sie Ihren Computer neu. Bei anderen Office-Versionen starten Sie eine beliebige Office-Anwendung neu.

## Installieren des Azure Information Protection-Clients für Benutzer

- Sie können ein Skript für die Installation des Azure Information Protection-Clients erstellen und die Installation automatisieren, indem Sie „AZInfoProtection.exe“ verpacken und die standardmäßigen [Windows Installer-Befehlszeilenoptionen (msiexec)](https://technet.microsoft.com/library/cc759262(v=ws.10).aspx) verwenden.

    Beispiel, wenn der Name der verpackten Version „InfoProtect.msi“ lautet und Sie den Client unbeaufsichtigt installieren möchten: `msiexec /qn InfoProtection.msi`


## Deinstallieren des Azure Information Protection-Clients

- Deinstallieren Sie ein Programm über die Systemsteuerung: Klicken Sie auf **Microsoft Azure Information Protection** > **Deinstallieren**

## Überprüfen der Installation und des Verbindungsstatus oder Melden von Problemen

1. Öffnen Sie eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen) und anschließend auf **Help and feedback** (Hilfe und Feedback).

2. Beachten Sie im Dialogfeld **Microsoft Azure Information Protection** Folgendes:

    - Der Wert **Last connection** (Letzte Verbindung) gibt an, wann der Client sich zuletzt mit dem Azure Information Protection-Dienst Ihrer Organisation verbunden hat. Wenn der Client eine Verbindung mit dem Dienst herstellt, lädt er automatisch die letzte Richtlinie herunter (sofern diese von der aktuellen Richtlinie abweicht). Wenn Sie nach dem angezeigten Zeitpunkt Änderungen vorgenommen haben, schließen Sie die Office-Anwendung, und öffnen Sie sie erneut.

    - Ihr angezeigter Benutzername gibt das Konto an, mit dem Sie gegenüber Azure Information Protection authentifiziert werden. Dieser Benutzername muss mit einem Konto übereinstimmen, das für Office 365 oder Azure Active Directory verwendet wird.

    - Die Version des Azure Information Protection-Clients.

    - Über den Link **Send feedback** (Feedback senden) können Sie automatisch Clientprotokolle an eine E-Mail-Nachricht anfügen, um diese zur Untersuchung an das Information Protection-Team zu senden.

    - Der Link **Run diagnostics** (Diagnose ausführen): Diese Funktionalität ist aktuell nicht implementiert.

## Dateispeicherorte

Clientdateien:   

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Clientprotokolldateien und aktuell installierte Richtliniendatei:

- Für 64-Bit- und 32-Bit-Betriebssysteme: **%localappdata%\Microsoft\MSIP**


## Nächste Schritte

Um die Bezeichnungen auf der Information Protection-Leiste zu ändern, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](infoprotect-quick-start-tutorial.md). 



<!--HONumber=Aug16_HO4-->


