---
title: Übersicht über das RMS SDK 4.2 | Azure RMS
description: AD RMS und Azure RMS sind eine Datenschutztechnologie, die zum Schutz digitaler Informationen vor nicht autorisierter Verwendung beiträgt.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8A13494E-C1D7-407D-BCD1-A406915EA578
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 1e7e2badcd57ce6896c9850729ba546efe22b778
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60176028"
---
# <a name="overview"></a>Übersicht

Das Microsoft Rights Management SDK 4.2 ist eine Technologie, die dem Schutz von Informationen dient und für mehrere Plattformen zur Verfügung steht.  Sie stellt ein Software Development Kit (SDK) bzw. ein Framework bereit, das für Clientcomputer und Geräte entwickelt wurde, um den Zugriff auf und die Verwendung von Informationen zu schützen, die rechtlich geschützte Anwendungen durchlaufen. Die SDKs für diese Plattformen bieten eine einfache API, mit der Anwendungsentwickler digitale Inhalte schützen oder nutzen, Vorlagen und Richtlinien von einem Server abrufen und andere relevante Aufgaben zur Rechteverwaltung ausführen können.

Weitere Informationen zu den derzeit unterstützten Plattformen finden Sie auf unserem Entwicklerdokumentationsportal für das [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md).

Nachfolgend sind ein paar der zahlreichen möglichen Szenarien aufgeführt:

-   Eine Anwaltskanzlei möchte verhindern, dass vertrauliche E-Mail-Nachrichten ausgedruckt oder auf mobilen Geräten weitergeleitet werden.
-   Die Entwickler von CAD/CAM-Software möchten den Zugriff auf eine kleine Gruppe von Benutzern in der Entwicklungsabteilung beschränken, ohne Kennwörter verwenden zu müssen.
-   Die Besitzer einer mobilen Grafikdesign-App möchten eine Lizenz verwenden, die das kostenlose Anzeigen der Bilder in niedriger Auflösung zulässt, jedoch für den Zugriff auf die Versionen in hoher Auflösung eine Zahlung erfordert.
-   Der Besitzer einer Online-Dokumentationsbibliothek möchten die Rechte zum Anzeigen, Drucken oder Bearbeiten der Dokumente auf Grundlage der Identität des Benutzers aktivieren, wenn die Dokumente auf ein Mobilgerät heruntergeladen werden.
-   Ein Unternehmen möchte vertrauliche Informationen zu Mitarbeitern auf einer internen Website veröffentlichen, auf der die Anzeige- und Bearbeitungsrechte auf bestimmte Benutzer beschränkt sind.

Das MS RMS SDK 4.2 kann einschließlich Bestätigung und Akzeptanz der Lizenzvereinbarung heruntergeladen und frei mit Software von Drittanbietern verteilt werden. Dies ermöglicht den Clientzugriff auf Inhalte, die durch die Nutzung und Bereitstellung von AD RMS-Servern in Ihrer Umgebung oder in Azure RMS-Diensten rechtlich geschützt sind. Weitere Informationen finden Sie unter [Erste Schritte](get-started.md).

## <a name="sdk-highlights"></a>SDK-Highlights


Das MS RMS SDK 4.2 bietet unter anderem die folgenden praktischen neuen Funktionen:

-   **Überarbeitete API**: Die MS RMS SDK 4.2-API wurde überarbeitet, damit sie möglichst einfach zu bedienen ist. Entwickler profitieren von einer einfachen und transparenten Verschlüsselungs- und Entschlüsselungs-API, die mit minimalem Aufwand ein konsistentes RMS-Verhalten bietet.
-   **Hybrid-Unterstützung für AD RMS und Azure RMS**: Eine einzelne RMS-fähige APP kann Inhalt vom AD RMS-Server (mithilfe der AD RMS-Erweiterung für Mobilgeräte) und vom Azure RMS-Dienst nutzen und schützen. Das MS RMS SDK 4.2 ermittelt auf transparente Weise den relevanten Endpunkt, der von IT-Administratoren konfiguriert werden kann.
-   **Nutzung Ihrer eigenen Authentifizierungsbibliothek:** Als App-Entwickler können Sie auswählen, welche Authentifizierungsbibliothek mit dem MS RMS SDK 4.2 verwendet werden soll. Unabhängig davon, ob Sie die [Azure AD-Authentifizierungsbibliothek](https://msdn.microsoft.com/library/jj573266.aspx) oder die benutzerdefinierte Bibliothek Ihrer Organisation verwenden, trennt das MS RMS SDK 4.2 den Authentifizierungsstapel, damit Sie die für Ihre Anforderungen ideale Bibliothek auswählen können.
-   **Nutzung Ihrer eigenen Benutzeroberfläche:** Das MS RMS SDK 4.2 ermöglicht jetzt die Implementierung Ihrer individuellen Benutzeroberfläche. Das MS RMS SDK 4.2 erzwingt keine integrierte Benutzeroberfläche für Ihre Apps, weder zum Schutz von Inhalten noch zur Auswahl von Vorlagen oder zum Anzeigen und Ändern von Berechtigungen bei der Nutzung geschützter Inhalte. Wenn Sie möchten, Sie können jedoch Microsoft RMS-UI-Bibliotheken für alle Plattformen über unser [GitHub-Konto](https://github.com/AzureAD/) verwenden.
-   **Offlinezugriff auf geschützte Inhalte**: Mit dem MS RMS SDK 4.2 können Ihre App-Benutzer auch ohne Internetverbindung auf geschützte Inhalte zugreifen. Das MS RMS SDK 4.2 speichert die Nutzungsrichtlinien der geschützten Inhalte sicher zwischen, damit die Benutzer die durch RMS geschützten Daten offline aufrufen können.

Befolgen Sie die [Ersten Schritte](get-started.md), um mit dem Erstellen einer Geräte-App für geschützte Daten zu beginnen.

## <a name="related-topics"></a>Verwandte Themen

* [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)
* [Erste Schritte](get-started.md)
* [Azure AD-Authentifizierungsbibliothek](https://msdn.microsoft.com/library/jj573266.aspx)
* [GitHub-Konto](https://github.com/AzureAD/)
