---
title: Herunterladen und Installieren der Rights Management-Freigabeanwendung | Azure Information Protection
description: "Anweisungen zur interaktiven Installation der RMS-Freigabeanwendung für Windows, damit Sie problemlos Dokumente für andere Benutzer freigeben können."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aac3c6c7b5167d729d9ac89d9ae71c50dd1b6a10
ms.openlocfilehash: c705bfec85bb93cb03d7e3edc9f3ce5949a8b61d


---

# Herunterladen und Installieren der Rights Management-Freigabeanwendung

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Sie müssen kein lokaler Administrator sein, um die RMS-Freigabeanwendung zu installieren. Wenn Sie es jedoch nicht sind und Office 2010 verwenden, bestehen einige Einschränkungen. Weitere Informationen finden Sie im Abschnitt [Wenn Sie kein lokaler Administrator sind und Office 2010 verwenden](#if-you-are-not-a-local-administrator-and-use-office-2010) auf dieser Seite.

## So laden Sie die Rights Management-Freigabeanwendung herunter und installieren sie

1.  Navigieren Sie auf der Microsoft-Website zur Seite [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) .

2.  Klicken Sie im Abschnitt **Computer** auf das Symbol für **RMS-App für Windows** , und speichern Sie die Datei **Setup.exe** , um die Microsoft Rights Management-Freigabeanwendung zu installieren.

3.  Doppelklicken Sie auf die heruntergeladene Datei „Setup.exe“. Wenn Sie aufgefordert werden, den Vorgang fortzusetzen, klicken Sie auf **Ja**.

4.  Klicken Sie auf der Seite **Microsoft RMS-Setup** auf **Weiter**, und warten Sie das Ende der Installation ab.

    > [!NOTE]
    > Die RMS-Freigabeanwendung setzt mindestens Microsoft .NET Framework 4.0 voraus. Beim Setup wird überprüft, ob diese Version installiert ist. Falls nicht, wird eine Nachricht mit einem Link zur Installationsquelle angezeigt.

5.  Am Ende der Installation klicken Sie auf **Neu starten** , um Ihren Computer neu zu starten und die Installation damit abzuschließen. Sie können auch auf **Schließen** klicken, um den Computer später neu zu starten und die Installation abzuschließen.

Damit sind Sie bereit, Ihre Dateien zu schützen und von anderen geschützte Dateien zu lesen.

## Wenn Sie kein lokaler Administrator sind und Office 2010 verwenden
Wenn Sie sich ohne lokale Administratorrechte bei Ihrem Computer anmelden und Setup erkennt, dass Office 2010 installiert ist, werden Sie in einer Warnmeldung darauf hingewiesen, dass einige Szenarien in dieser Konfiguration nicht funktionieren. Dies sind folgende Szenarien:

-   Wenn Ihre Organisation den Azure Rights Management-Dienst von Azure Information Protection anstelle einer lokalen Version von Rights Management verwendet:

    -   Das Microsoft Office-Feature „Information Rights Management“ (IRM) ist nicht verfügbar. Das betrifft z.B. die Option **Nicht weiterleiten** für E-Mails und die Berechtigungen unter **Zugriff einschränken**, die Sie in Word und Excel im Menü **Datei** festlegen können. Sie können die Option „Geschützt freigeben“ im Menüband verwenden, und Sie können im Datei-Explorer die Kontextmenüoptionen verwenden.

-   Wenn Ihre Organisation eine lokale Version von Rights Management anstelle des Azure Rights Management-Diensts von Azure Information Protection verwendet:

    -   Sie können keine geschützten Dokumente lesen, die Sie aus einer anderen Organisation erhalten, die den Azure Rights Management-Dienst verwendet.

Wenn Sie kein lokaler Administrator sind und Office 365 oder Office 2013 verwenden, wird Ihnen diese Meldung nicht angezeigt, und diese Szenarien werden unterstützt.

Sie können die Installation mit diesen bekannten Einschränkungen fortsetzen. Alternativ beenden Sie die Installation und führen sie erneut aus, wählen aber in Schritt 3 beim Ausführen von „Setup.exe“ die Option **Als Administrator ausführen**. Sie können auch einen Administrator bitten, die Installation für Sie durchzuführen. Administratoren können diese [Installation per Skript](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application) ausführen, sodass sie ohne Ihr Zutun automatisch erfolgt.

## Beispiele und weitere Anweisungen
Beispiele für die Verwendung der Rights Management-Freigabeanwendung sowie weitere Anweisungen finden Sie in den folgenden Abschnitten des Benutzerhandbuchs für die Rights Management-Freigabeanwendung

-   [Beispiele für die Nutzung der RMS-Freigabeanwendung](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Was möchten Sie tun?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Weitere Informationen
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)




<!--HONumber=Sep16_HO4-->


