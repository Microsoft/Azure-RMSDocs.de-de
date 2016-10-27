---
title: "Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android | Azure Information Protection"
description: 
keywords: "Einige häufig gestellte Fragen, die Ihnen beim Verwenden der Azure Information Protection-App für iOS und Android helfen sollen"
author: cabailey
manager: mbaldwin
ms.date: 10/12/2016
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7ca40550f16dff0cc4979eb029d9eb7dd68414f
ms.openlocfilehash: da77d799128e110679c972629fa9f816487ccb4f


---

# Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android

*Gilt für: Active Directory Rights Management Services, Azure Information Protection*

Auf dieser Seite finden Sie Antworten auf einige häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android.

## Was kann ich mit der Azure Information Protection-App machen?

Mit dieser App können Sie durch Rechte geschützte E-Mail-Nachrichten anzeigen (RPMSG-Dateien), wenn Ihre E-Mail-App von sich aus keinen Datenschutz durch Rechteverwaltung unterstützt. Zusätzlich können Sie sich durch Rechte geschützte PDF-Dateien, Bilder und Textdateien sowie generisch geschützte Dateien (Dateinamenerweiterung „.pfile“) anzeigen lassen. Derzeit können Sie mit dieser App keine neuen geschützten E-Mail-Nachrichten erstellen oder beantworten und keine geschützten Dateien erstellen oder bearbeiten.

## Kann ich PDF-Dateien aus geschützten SharePoint-Bibliotheken und OneDrive for Business öffnen?

Ja, Sie können geschützte PDF-Dateien öffnen, die andere über SharePoint und OneDrive for Business für Sie freigegeben haben. Tippen Sie auf den Link, und wählen Sie diese App für das Öffnen der Datei aus. 

## Wie beginne ich mit der Viewer-App?

Sie müssen auf Ihrem mobilen Gerät eine Datei eines Formats öffnen, das die App unterstützt, um den Viewer ausprobieren zu können. Beispiel:

- **Eine RPMSG-Datei**: Dies ist eine durch Rechte geschützte E-Mail-Nachricht, die einer E-Mail als Anhang beigefügt ist, wenn Ihre E-Mail-App von sich aus keinen Datenschutz durch Rechteverwaltung unterstützt. 
    
    Verwenden Sie ein anderes Gerät, um sich selbst eine durch Rechte geschützte E-Mail zu senden, auf die Sie von Ihrem mobilen Gerät aus zugreifen können. Verwenden Sie z.B. Outlook von einem Windows-Computer aus. Eine Liste der E-Mail-Clients, die von sich aus Rights Management unterstützen, finden Sie in der Spalte E-MAIL der Seite [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-applications.md).

- **Eine durch Rechte geschützte PDF-Datei**: Verwenden Sie die Rights Management-Freigabeanwendung auf einem Windows-Computer oder eine PDF-Anwendung, die Rights Management von sich aus unterstützt, um sich selbst eine durch Rechte geschützte PDF-Datei als Anhang in einer E-Mail zu senden. Alternativ können Sie eine PDF-Datei in eine von SharePoint geschützte Bibliothek hochladen und anschließend mithilfe Ihrer E-Mail-Adresse freigeben.

- **Eine PTXT-, PJPG- oder PFILE-Datei**: Verwenden Sie die Rights Management-Freigabeanwendung auf einem Windows-Computer sowie die Option [Geschützt freigeben](sharing-app-protect-by-email.md), um sich selbst eine geschützte Datei als Anhang in einer E-Mail zu senden. Die vollständige Liste der Dateitypen, die Sie für Tests verwenden können, finden Sie in der ersten Tabelle des Abschnitts [Unterstützte Dateitypen und Dateinamenerweiterungen](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) im Administratorhandbuch zur Rights Management-Freigabeanwendung. 

Um diese Dateien in der Azure Information Protection-Viewer-App anzuzeigen, tippen Sie auf den E-Mail-Anhang oder den Link. Wenn Sie aufgefordert werden, eine App zum Öffnen auszuwählen, wählen Sie die **AIP Viewer**-App. Anschließend werden Sie aufgefordert, sich an Ihrem Arbeits- oder Schulkonto anzumelden. Nachdem Sie sich erfolgreich authentifiziert haben, zeigt Ihnen die Azure Information Protection-App die E-Mail oder Datei zum Lesen an.

## Welche Anmeldeinformationen sollte ich bei dieser App verwenden?

Wenn Ihre Organisation lokal bereits AD RMS (mit der Erweiterung für mobile Geräte) oder den Azure Rights Management-Dienst verwendet, können Sie Ihre Anmeldeinformationen für die Anmeldung verwenden. Andernfalls können Sie sich auf der Seite [Azure Rights Management](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload) für ein kostenloses neues Konto anmelden.

## Kann ich für die Anmeldung bei einem kostenlosen Konto eine persönliche E-Mail-Adresse, z.B. ein Hotmail- oder Gmail-Konto, verwenden?

Bisher nicht. Derzeit können Sie sich nur mit Ihrer geschäftlichen E-Mail-Adresse (Geschäfts-, Schul- oder Unikonto) anmelden. Wir arbeiten an einer Unterstützung für persönliche E-Mail-Adressen und werden diesen Eintrag aktualisieren, sobald diese verfügbar ist.

## Welche Dateierweiterungen kann ich mit dieser App öffnen?

Sie können Dateien mit den Erweiterungen „.rpmsg“, „.pdf“, „.ppdf“, „.pjpg“, „.ptxt“ sowie viele weitere Text- und Bilddateiformate öffnen.

## Warum muss ich zustimmen, bevor eine geschützte PFILE-Datei angezeigt wird?

Die Zustimmung ist erforderlich, um sicherzustellen, dass Sie über Folgendes informiert sind:

- Der Besitzer des Dokuments verlangt von Ihnen, dass Sie seine Rechte beachten.

- Das Öffnen dieser Inhalte in einer Anwendung eines Drittanbieters wird überwacht.

##  Wie gebe ich Feedback zu dieser App?

Wechseln Sie in der App zu **Einstellungen** > **Feedback senden**.


## Meine Frage wurde hier nicht beantwortet – was soll ich tun?

Veröffentlichen Sie Ihre Frage auf unserer [Yammer-Website](http://www.yammer.com/AskIPTeam), oder [senden Sie eine E-Mail an das Information Protection-Team](mailto:askIPteam@microsoft.com?subject=Question%20about%20Azure%20Information%20Protection%20app).



<!--HONumber=Oct16_HO2-->


