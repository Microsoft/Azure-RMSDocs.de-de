---
title: Grundlegendes zu Nutzungseinschränkungen | Azure RMS
description: Für alle RMS-fähigen Anwendungen müssen Nutzungseinschränkungen erzwungen werden.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8ebd4808d2cd16a7410d7958c149da4595eaab9f
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804825"
---
# <a name="understanding-usage-restrictions"></a>Grundlegendes zu Nutzungseinschränkungen

Für alle RMS-fähigen Anwendungen müssen Nutzungseinschränkungen erzwungen werden. Eine Nutzungseinschränkung liegt vor, wenn ein Benutzer eine Aktion durchführen möchte (z.B. das Drucken eines Dokuments) und die RMS-Richtlinie für dieses Dokument keine Berechtigung bzw. kein Recht für die Durchführung der Aktion gewährt (z.B. das Recht DRUCKEN).

Die Berechtigungen eines Benutzers für ein Dokument können mit der [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)-Funktion abgefragt werden.

## <a name="designing-with-usage-restrictions"></a>Entwerfen mit Nutzungsbeschränkungen

-   Kennenlernen der standardmäßigen RMS-Rechte

    Eine Übersicht über alle RMS-Rechte, die von der Anwendung erzwungen werden können, finden Sie unter [Referenz für die Nutzungseinschränkung](#usage-restriction-reference).

    Beachten Sie hierbei, dass unter Umständen von der Anwendung definierte Rechte erstellt werden, die speziell für Ihre Situation gelten und über die standardmäßigen RMS-Rechte hinausreichen.

-   Identifizieren von Erzwingungspunkten für die Nutzungseinschränkung

    Ein *Erzwingungspunkt für die Nutzungseinschränkung* ist ein Punkt in der Ablaufsteuerung der Anwendung, an dem Sie eine Nutzungseinschränkung erzwingen müssen. Das Thema [Referenz für die Nutzungseinschränkung](#usage-restriction-reference) enthält mehrere Beispiele für häufige Erzwingungspunkte.

    Bewerten Sie Ihre eigene Anwendung, um zu ermitteln, welche Erzwingungspunkte für die Nutzungseinschränkung gelten.

    In Ihrer Anwendung sind unter Umständen nicht alle Erzwingungspunkte erforderlich, die unter [Referenz für die Nutzungseinschränkung](#usage-restriction-reference) beschrieben sind. Falls Ihre Anwendung für Benutzer beispielsweise das Drucken von Inhalten nicht zulässt, muss keine Prüfung auf das Recht **IPC\_GENERIC\_PRINT** durchgeführt werden.

-   Aktualisieren des Codes zum Durchführen einer Zugriffsüberprüfung an jedem Erzwingungspunkt

    Eine Anleitung, wie Sie bestimmte Rechte durchsetzen, finden Sie unter [Referenz für die Nutzungseinschränkung](#usage-restriction-reference).

## <a name="usage-restriction-reference"></a>Referenz für die Nutzungseinschränkung

Nutzungsbeschränkungen werden durch folgende Konstanten definiert.

Jedes Benutzerrecht, das in der AD RMS-Rechtespalte aufgeführt wird, hat eine Beschreibung, einen Erzwingungspunkt und empfohlene Methoden für die Erzwingung.

| AD RMS-Recht/Beschreibung | Erzwingungsmethode |
|--------------------------|----------------|
|**IPC_GENERIC_ALL** <br><br> Erteilt dem Benutzer alle Rechte. <br><br> **Allgemeine Erzwingungspunkte**: Keine |Dieses Recht wird vom System verwendet und sollte in der Regel nicht direkt aktiviert werden. <br><br> [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx) verwendet diese Berechtigung, um zu bestimmen, ob dem Benutzer andere Zugriffsrechte als in diesem Beispiel erteilt werden sollen.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`|
|**IPC_GENERIC_READ** <br><br> Das Recht, Dokumentinhalte zu lesen. <br><br> **Allgemeine Erzwingungspunkte**: Laden von Dokumenten|Dokumentinhalte nicht laden oder darstellen.|
|**IPC_GENERIC_WRITE** <br><br> Das Recht, Dokumentinhalte zu bearbeiten <br><br> **Allgemeine Erzwingungspunkte**: Änderung von Dokumenten|Alle UI-Steuerelemente, die verwendet werden können, um Dokumentinhalte zu ändern, mit einem Schreibschutz versehen. <br><br> Alle Menüelemente, die Dokumentänderungen auslösen, deaktivieren. **Bearbeiten** > **Ausschneiden**, **Bearbeiten** > **Einfügen** und **Einfügen** sind typische Beispiele. <br><br>Alle Tastenkombinations-Menüelemente, die Dokumentänderungen auslösen, deaktivieren.|
|Kein AD RMS-Recht <br><br> Keine Beschreibung <br><br> **Allgemeine Erzwingungspunkte**: Speichern | Deaktivieren Sie das Menü **Datei** > **Speichern**. <br><br> **Hinweis**: Dieses Recht steuert nicht **Datei** > **Speichern unter**, da dieses Recht keine Änderung des ursprünglichen Dokuments darstellt.<br><br> Alle Tastenkombination deaktivieren, die zum Auslösen eines Speichervorgangs verwendet werden können (z. B. STRG + S).<br><br> **Tipp**: Eine bewährte Methode ist das Aktualisieren des Kerncodes von **Datei** > **Speichern** dahingehend, dass ein Fehler auftritt, wenn der Benutzer nicht über dieses Recht verfügt. Dies dient als Sicherheitsnetz, falls Sie UX-Mechanismen übersehen, die verwendet werden können, um einen Speichervorgang auszulösen. |
|**IPC_GENERIC_EXTRACT** <br><br> Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. <br><br> **Allgemeine Erzwingungspunkte**: In Zwischenablage kopieren | Deaktivieren Sie das Menü **Bearbeiten** > **Kopieren**. Deaktivieren Sie das Menü **Bearbeiten** > **Ausschneiden**. <br><br>**Kopieren** und **Ausschneiden** in allen Kontextmenüs deaktivieren.<br><br>Alle Tastenkombination deaktivieren, die zum Auslösen eines Kopiervorgangs verwendet werden können (z. B. STRG + C oder STRG + X).<br><br>Fenstermeldungshandler für [**WM_CUT**](https://msdn.microsoft.com/library/ms649023) aktualisieren, um das Kopieren von Daten abzulehnen, wenn der Benutzer nicht über dieses Recht verfügt. Wenn das Fenster den standardmäßigen, von Windows bereitgestellten Meldungshandler verwendet, dieses Fenster als Unterklasse markieren und eigene Handler für **WM_COPY** und **WM_CUT** bereitstellen. |
|Kein AD RMS-Recht <br><br> Keine Beschreibung <br><br> **Allgemeine Erzwingungspunkte**: Speichern unter |Im Dialogfeld **Speichern unter** alle Dateiformate deaktivieren, die zu einem Speichern des Dokuments ohne RMS-Schutz führen würden.|
|Kein AD RMS-Recht <br><br> Keine Beschreibung <br><br> **Allgemeine Erzwingungspunkte**: ALT+DRUCK|Rufen Sie [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) für alle Fenster auf, die Dokumentinhalte rendern.|
|**IPC_GENERIC_EXPORT** <br><br> Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem anderen durch AD RMS geschützten Format. <br><br> **Allgemeine Erzwingungspunkte**: Speichern unter|Im Dialogfeld **Speichern unter** die Möglichkeit deaktivieren, in anderen Dateiformaten zu speichern.<br><br>**Tipp**: Eine bewährte Methode besteht darin, Ihren Kerncode von **Datei** > **Speichern unter** dahingehend zu aktualisieren, dass ein Fehler auftritt, wenn der Benutzer versucht, diese Datei in einem anderen Format zu speichern und nicht über dieses Recht verfügt. Dies dient als Sicherheitsnetz, falls Sie UX-Mechanismen übersehen, die verwendet werden können, um einen Speichern-unter-Vorgang auszulösen.|
|**IPC_GENERIC_PRINT** <br><br> Das Recht, Dokumentinhalte zu drucken <br><br> **Allgemeine Erzwingungspunkte**: Drucken|Deaktivieren Sie das Menü **Datei** > **Drucken**.<br><br>Alle Tastenkombination deaktivieren, die zum Auslösen eines Druckvorgangs verwendet werden können (z. B. STRG + P).<br><br>Alle Kontextmenüeinträge deaktivieren, die verwendet werden können, um einen Druck auszulösen.<br><br>**Tipp**: Eine bewährte Methode ist das Aktualisieren des Kerncodes von **Datei** > **Drucken** dahingehend, dass ein Fehler auftritt, wenn der Benutzer nicht über dieses Recht verfügt. Dies dient als Sicherheitsnetz, falls Sie UX-Mechanismen übersehen, die verwendet werden können, um einen Druckvorgang auszulösen.|
|**IPC_GENERIC_COMMENT** <br><br> Einige Programme unterstützen die Möglichkeit, Kommentare und Anmerkungen dem Dokument hinzuzufügen, ohne Dokumentkerninhalte zu aktualisieren.<br><br>Dieses Recht erteilt den Benutzer Zugriff auf diese Funktion. <br><br> **Allgemeine Erzwingungspunkte**: <br><br> Prüfung > Kommentar einfügen <br><br> Prüfung > Kommentar löschen | Alle Menüelemente deaktivieren, die zum Ändern von Dokumentkommentaren oder -anmerkungen verwendet werden können. **Prüfen** > **Kommentar einfügen** und **Prüfen** > **Kommentar löschen** sind Beispiele. <br><br>Alle Tastenkombination deaktivieren, die Änderungen der Dokumentkommentare auslösen könnten.<br><br>**Hinweis**: Eine standardmäßige Implementierung setzt voraus, dass **IPC_GENERIC_COMMENT** und **IPC_GENERIC_WRITE** neue Kommentare in einer Datei beibehalten. Anwendungen können Unterstützung für den Fall hinzufügen, dass das **IPC_GENERIC_COMMENT**-Recht erteilt wird, das **IPC_GENERIC_WRITE**-Recht aber nicht. In diesem Fall ist es zulässig, das Speichern zu ermöglichen, sofern Dokumentänderungen nur auf Kommentare beschränkt sind.|
|**IPC_VIEW_RIGHTS** <br><br> Keine Beschreibung <br><br> **Allgemeine Erzwingungspunkte**: N/V|Durch das System erzwungen. Das System lässt es nicht zu, dass der Entwickler die [**Liste mit Benutzerrechten**](https://msdn.microsoft.com/library/hh535286.aspx) aus einer Lizenz abfragt, sofern dieses Recht nicht erteilt wird.
|**IPC_EDIT_RIGHTS** <br><br> Einige Anwendungen ermöglichen Benutzern das Ändern des Satzes aus Benutzern und Rechten für AD RMS-geschützte Inhalte.<br><br>Dieses Recht erteilt den Benutzer Zugriff auf diese Funktion. <br><br> **Allgemeine Erzwingungspunkte**: UI-Steuerelemente für das Bearbeiten von Anwendungsrechten|Benutzerzugriff auf alle Steuerelemente, die verwendet werden können, um die RMS-Richtlinie für ein Dokument zu bearbeiten, deaktivieren.|


## <a name="related-topics"></a>Verwandte Themen

* [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)
