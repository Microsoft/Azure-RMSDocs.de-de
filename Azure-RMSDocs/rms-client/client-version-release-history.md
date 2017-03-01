---
title: "Azure Information Protection-Client&colon; Verlauf der Versionsveröffentlichungen"
description: "Erfahren Sie, was in einer Version des Azure Information Protection-Clients für Windows neu ist oder geändert wurde."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: fec4ca2541b28fd9d91286fceaee0466fc445364
ms.lasthandoff: 02/24/2017


---

# <a name="azure-information-protection-client-version-release-history"></a>Azure Information Protection-Client: Verlauf der Versionsveröffentlichungen

>*Gilt für: Azure Information Protection*

Das Azure Information Protection-Team aktualisiert den Azure Information Protection-Client regelmäßig, um Korrekturen und neue Funktionen zu implementieren. Der Client befindet sich im Microsoft Update-Katalog (Kategorie: **Azure Information Protection**). Die neueste Version können Sie stets aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen.

Verwenden Sie die folgenden Informationen, um zu sehen, welche Neuerungen oder Änderungen eine Version bietet. Die neueste Version ist zuerst aufgeführt. Versionen vor „General Availability“ (allgemeine Verfügbarkeit) sind nicht aufgeführt.

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn ein Problem mit dem Azure Information Protection-Client auftreten sollte, vergewissern Sie sich zuerst, dass es sich nicht um ein Problem mit der neuesten Version handelt.
>  
> Falls das Problem bestehen bleibt, finden Sie entsprechende Informationen unter [Supportoptionen und Communityressourcen](../get-started/information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

## <a name="version-131552"></a>Version 1.3.155.2

**Veröffentlicht**: 08.02.2017

**Neue Anforderungen**:

Microsoft .NET Framework

- Diese Version des Azure Information Protection-Clients erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Nach Abschluss der Installation des Azure Information Protection-Clients ist möglicherweise ein Neustart des Computers erforderlich.

- Wenn der Azure Information Protection-Viewer separat installiert wird, ist Microsoft .NET Framework 4.5.2 oder höher erforderlich. Wenn diese Version fehlt, wird sie vom Installationsprogramm nicht heruntergeladen oder installiert.

**Neue Features**:

- Ein neuer einheitlicher Client, der die Features der Rights Management-Freigabeanwendung für Windows mit dem Azure Information Protection-Client kombiniert. Dies umfasst Folgendes:
    
    - Integration mit dem Windows-Datei-Explorer (Rechtsklick), um Bezeichnungen und den Schutz anzuwenden. Unterstützt weitere Dateiformate und die Auswahl mehrerer Dateien.
    - Ein Viewer für geschützte Dokumente (umfasst geschützte PDF-Dateien für SharePoint).
    - PowerShell-Cmdlets zum Abrufen und Festlegen von Bezeichnungen für Dateien, die lokal oder auf Netzwerkfreigaben gespeichert werden. Diese Cmdlets werden mit den Cmdlets installiert, die zuvor mit dem RMS Protection Tool (RMSProtection-Modul) ausgeliefert wurden.
    - Clientverwendungsprotokolle, die entsprechende Informationen aufzeichnen, z. B. welche Bezeichnung auf welche Weise von welchem Benutzer angewendet wurde.

Diese Clientversion ist die [allgemein verfügbare Version](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/) für den Vorschauclient, der im Dezember 2016 erstmals angekündigt wurde. Weitere Informationen zu dieser Version des Clients finden Sie in den folgenden Handbüchern:

- [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)

- [Azure Information Protection-Benutzerhandbuch](client-user-guide.md)


## <a name="version-1240"></a>Version 1.2.4.0

**Veröffentlicht**: 27.10.2016

**Fixes**:

- Die Clientinstallation wird abgeschlossen, wenn der Windows Update-Dienst deaktiviert wird.

- Wenn Sie in Office 2016 ein Dokument speichern und eine Bezeichnung für eine Kopf- oder Fußzeile konfiguriert ist, springt der Cursor nicht zur Kopf- oder Fußzeile.

- Automatische Klassifizierung funktioniert in Word für Text in gebündelten Textfeldern.

**Neues Feature**:

- Diagnosetests und eine Option zum Zurücksetzen, die ein Benutzer in einer Office-Anwendung ausführen kann, wenn der Azure Information Protection-Client installiert ist: Klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, dann auf **Hilfe und Feedback** und schließlich auf **Diagnose ausführen**. 

    Weitere Informationen zu dieser Option finden Sie im Abschnitt [Überprüfen der Installation, des Verbindungsstatus oder Senden von Feedback](client-admin-guide.md#to-verify-installation-connection-status-or-send-feedback) der Dokumentation zur Clientinstallation.

## <a name="version-11230"></a>Version 1.1.23.0

**Veröffentlicht**: 01.10.2016

Allgemeine Verfügbarkeit.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren des Clients:

- Für Benutzer: [Herunterladen und Installieren des Clients](install-client-app.md)

- Für Administratoren: [Azure Information Protection-Client – Administratorhandbuch](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
