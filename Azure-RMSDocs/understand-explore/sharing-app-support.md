---
# required metadata

title: RMS-Freigabeanwendung für Windows und mobile Plattformen | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1da6e372-2b3f-4af7-80f7-6b9073dff7f5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# RMS-Freigabeanwendung für Windows und mobile Plattformen
Die RMS-Freigabeanwendung ist eine kostenlose, herunterladbare Anwendung, die für die Unterstützung von Office 2010 erforderlich ist, aber auch für Windows-Computer, Mac-Computer und mobile Geräte empfohlen wird. Einer ihrer Vorteile besteht darin, dass sie generischen Schutz für Anwendungen und Dateien anwenden kann, die keine systemeigene Unterstützung für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] bieten, was bedeutet, dass alle Dateien geschützt werden können. Weitere Informationen zu den verschiedenen Schutzstufen finden Sie im Abschnitt [Schutzstufen – systemeigen und generisch](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) im [Rights Management-Freigabeanwendung – Administratorhandbuch](../rms-client/sharing-app-admin-guide.md).

Wenn Benutzer ihre Dateien mit der RMS-Freigabeanwendung schützen, können sie auch von ihnen geschützte Dokumente nachverfolgen und bei Bedarf den Zugriff hierauf widerrufen. Hierfür wird die [Website zum Nachverfolgen von Dokumenten](http://go.microsoft.com/fwlink/?LinkId=529562)verwendet.

Bei Windows-Computern integriert sich die RMS-Freigabeanwendung unauffällig in die bereits von Benutzern verwendeten Anwendungen und erweitert deren Funktionsumfang:

-   Ein Office-Add-In für Word, Excel, PowerPoint und Outlook wird installiert. Dieses bietet Benutzern im Menüband eine Schaltfläche **Geschützt freigeben**, über die ein bequem zu verwendendes Dialogfeld mit den Einstellungen aufgerufen wird, die am häufigsten zum Schützen von Dateien, die per E-Mail gesendet werden, verwendet werden. Diese Schaltfläche bietet zudem eine schnelle Möglichkeit für den Zugriff auf die Website zum Nachverfolgen von Dokumenten.

-   Eine neue Kontextmenüoption für Datei-Explorer. Benutzer erhalten die Option **Direkt schützen** zum Aufrufen eines benutzerfreundlichen Dialogfelds mit den Einstellungen, die am häufigsten zum Schützen von auf einem Datenträger gespeicherten Dateien verwendet werden.

-   Eine Anzeige zum Öffnen von Dateien, die durch [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] geschützt sind. Diese Anzeige wird automatisch aufgerufen, wenn keine andere Anwendung installiert ist, mit der die geschützte Datei geöffnet werden kann.

-   Back-End-Konfiguration für Office 2010, die Word, Excel, PowerPoint und Outlook aus dieser Suite die nahtlose Zusammenarbeit mit [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] ermöglicht.

Obwohl die RMS-Freigabeanwendung für Windows über die [Microsoft Rights Management-Seite](http://go.microsoft.com/fwlink/?LinkId=303970)auf einzelnen Computer heruntergeladen und installiert werden kann, wird auch eine Unternehmensbereitstellung mit automatischer Installation und benutzerdefinierter Konfiguration unterstützt. Weitere Informationen finden Sie in den folgenden Ressourcen:

-   [Administratorhandbuch der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md)

Die RMS-Freigabeanwendung für mobile Geräte unterstützt die gängigsten verwendeten mobilen Geräte wie iPad und iPhone, Android, Windows Phone und Windows RT. Benutzer können diese App aus dem relevanten Store herunterladen, zu denen es Links auf der Seite [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)gibt.

**Bei Verwendung von Microsoft Intune**: Da die RMS-Freigabe-App das Microsoft Intune App Software Development Kit enthält, können Sie die folgenden Optionen verwenden:

-   Bereitstellen und Verwalten der App für iOS- und Android-Geräte, die per Intune registriert sind

-   Verwalten der App für Android-Geräte, die nicht per Intune registriert sind


## Nächste Schritte
Informationen dazu, wie andere Anwendungen und Dienste Rights Management unterstützen, finden Sie unter [Unterstützung von Azure Rights Management durch Anwendungen](applications-support.md).



<!--HONumber=Apr16_HO3-->

