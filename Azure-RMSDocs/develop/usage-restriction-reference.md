---
# required metadata

title: Referenz für die Nutzungseinschränkung | Azure RMS
description:
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5c1b0de6-e6d6-4ec9-b810-017fd606866e

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿# Referenz für die Nutzungseinschränkung

Nutzungseinschränkungen werden durch die in diesem Thema aufgeführten Konstanten definiert.



Jedes Benutzerrecht, das in der AD RMS-Rechtespalte aufgeführt wird, hat eine Beschreibung, einen Erzwingungspunkt und empfohlene Methoden für die Erzwingung.

| AD RMS-Recht | Beschreibung | Allgemeine Erzwingungspunkte | Erzwingungsmethode |
|--------------|-------------|---------------------------|----------------|
|IPC_GENERIC_ALL |Erteilt dem Benutzer alle Rechte.| Keine |Dieses Recht wird vom System verwendet und sollte in der Regel nicht direkt aktiviert werden. <br><br> [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck) verwendet dieses Recht, um zu bestimmen, ob dem Benutzer andere Zugriffsrechte als in diesem Beispiel erteilt werden sollen.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`
|IPC_GENERIC_READ |Das Recht, Dokumentinhalte zu lesen.|Laden von Dokumenten|Dokumentinhalte nicht laden oder darstellen.|
|IPC_GENERIC_WRITE|Das Recht, Dokumentinhalte zu bearbeiten|Änderung von Dokumenten|Alle UI-Steuerelemente, die verwendet werden können, um Dokumentinhalte zu ändern, mit einem Schreibschutz versehen. <br><br> Alle Menüelemente, die Dokumentänderungen auslösen, deaktivieren. **Bearbeiten** > **Ausschneiden**, **Bearbeiten** > **Einfügen** und **Einfügen** sind typische Beispiele. <br><br>Alle Tastenkombinations-Menüelemente, die Dokumentänderungen auslösen, deaktivieren.|
|Kein AD RMS-Recht|Aufrufer hat keine AD RMS-Rechte|Speichern|Das Menü **Datei** > **Speichern** deaktivieren. <br><br> **Hinweis**: Dieses Recht steuert nicht **Datei** > **Speichern**, da dieses Recht keine Änderung des ursprünglichen Dokuments darstellt.<br><br> Alle Tastenkombination deaktivieren, die zum Auslösen eines Speichervorgangs verwendet werden können (z. B. STRG + S).<br><br> **Tipp**: Eine bewährte Methode ist das Aktualisieren des Kerncodes **Datei** > **Speichern** auf Fehler, wenn der Benutzer nicht über dieses Recht verfügt. Dies dient als Sicherheitsnetz, falls Sie UX-Mechanismen übersehen, die verwendet werden können, um einen Speichervorgang auszulösen.
|IPC_GENERIC_EXTRACT|Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format.|In Zwischenablage kopieren|Das Menü **Bearbeiten** > **Kopieren** deaktivieren. Das Menü **Bearbeiten** > **Ausschneiden** deaktivieren. <br><br>**Kopieren** und **Ausschneiden** in allen Kontextmenüs deaktivieren.<br><br>Alle Tastenkombination deaktivieren, die zum Auslösen eines Kopiervorgangs verwendet werden können (z. B. STRG + C oder STRG + X).<br><br>Fenstermeldungshandler für [**WM_CUT**](https://msdn.microsoft.com/library/windows/desktop/ms649023) aktualisieren, um das Kopieren von Daten abzulehnen, wenn der Benutzer nicht über dieses Recht verfügt. Wenn das Fenster den standardmäßigen, von Windows bereitgestellten Meldungshandler verwendet, dieses Fenster als Unterklasse markieren und eigene Handler für **WM_COPY** und **WM_CUT** bereitstellen.
|Kein AD RMS-Recht|Aufrufer hat keine AD RMS-Rechte|Speichern unter|Im Dialogfeld **Speichern unter** alle Dateiformate deaktivieren, die zu einem Speichern des Dokuments ohne RMS-Schutz führen würden.|
|Kein AD RMS-Recht|Aufrufer hat keine AD RMS-Rechte|ALT + Druck|[**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) für alle Fenster aufrufen, die Dokumentinhalte darstellen.|
|IPC_GENERIC_EXPORT|Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem anderen durch AD RMS geschützten Format.|Speichern unter|Im Dialogfeld **Speichern unter** die Möglichkeit deaktivieren, in anderen Dateiformaten zu speichern.<br><br>**Tipp**: Eine bewährte Methode besteht darin, Ihren Kerncode **Datei** > **Speichern** auf Fehler zu aktualisieren, wenn der Benutzer versucht, diese Datei in einem anderen Format zu speichern und nicht über dieses Recht verfügt. Dies dient als Sicherheitsnetz, falls Sie UX-Mechanismen übersehen, die verwendet werden können, um einen Speichern-unter-Vorgang auszulösen.|
|IPC_GENERIC_PRINT|Das Recht, Dokumentinhalte zu drucken|Drucken|Das Menü **Datei** > **Drucken** deaktivieren.<br><br>Alle Tastenkombination deaktivieren, die zum Auslösen eines Druckvorgangs verwendet werden können (z. B. STRG + P).<br><br>Alle Kontextmenüeinträge deaktivieren, die verwendet werden können, um einen Druck auszulösen.<br><br>**Tipp**: Eine bewährte Methode ist das Aktualisieren des Kerncodes **Datei** > **Drucken** auf Fehler, wenn der Benutzer nicht über dieses Recht verfügt. Dies dient als Sicherheitsnetz, falls Sie UX-Mechanismen übersehen, die verwendet werden können, um einen Druckvorgang auszulösen.|
|IPC_GENERIC_COMMENT|Einige Programme unterstützen die Möglichkeit, Kommentare und Anmerkungen dem Dokument hinzuzufügen, ohne Dokumentkerninhalte zu aktualisieren.<br><br>Dieses Recht erteilt den Benutzer Zugriff auf diese Funktion.|Prüfung > Kommentar einfügen <br><br> Prüfung > Kommentar löschen | Alle Menüelemente deaktivieren, die zum Ändern von Dokumentkommentaren oder -anmerkungen verwendet werden können. **Prüfung** > **Kommentar einfügen** und **Prüfung** > **Kommentar löschen** sind Beispiele. <br><br>Alle Tastenkombination deaktivieren, die Änderungen der Dokumentkommentare auslösen könnten.<br><br>**Hinweis**: Eine standardmäßige Implementierung setzt voraus, dass **IPC_GENERIC_COMMENT** und **IPC_GENERIC_WRITE** neue Kommentare in einer Datei beibehalten. Anwendungen können Unterstützung für den Fall hinzufügen, dass das **IPC_GENERIC_COMMENT**-Recht erteilt wird, das **IPC_GENERIC_WRITE**-Recht aber nicht. In diesem Fall ist es zulässig, das Speichern zu ermöglichen, sofern Dokumentänderungen nur auf Kommentare beschränkt sind.|
|IPC_VIEW_RIGHTS||N/V|Durch das System erzwungen. Das System lässt es nicht zu, dass der Entwickler die [**Liste mit Benutzerrechten**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_user_rights_list) aus einer Lizenz abfragt, sofern dieses Recht nicht erteilt wird.
|IPC_EDIT_RIGHTS|Einige Anwendungen ermöglichen Benutzern das Ändern des Satzes aus Benutzern und Rechten für AD RMS-geschützte Inhalte.<br><br>Dieses Recht erteilt den Benutzer Zugriff auf diese Funktion.|UI-Steuerelemente für das Bearbeiten von Anwendungsrechten|Benutzerzugriff auf alle Steuerelemente, die verwendet werden können, um die RMS-Richtlinie für ein Dokument zu bearbeiten, deaktivieren.|

 

 

 


<!--HONumber=Apr16_HO3-->


