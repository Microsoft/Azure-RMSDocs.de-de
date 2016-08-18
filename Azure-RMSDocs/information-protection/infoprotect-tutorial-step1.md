---
title: "Schnellstart-Tutorial für Azure Information Protection Schritt 1 | Azure Rights Management"
description: "Schritt 1 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in vier Schritten und weniger als zehn Minuten für Ihre Organisation testen können."
author: cabailey
manager: mbaldwin
ms.date: 07/291/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 128952778ec317584e558e409961e2921c4ecd07


---

# Schritt 1: Aktivieren des Rights Management-Diensts
 
>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

> [!NOTE]
>Wenn Sie Ihre Daten lediglich klassifizieren und nicht mit Azure Rights Management schützen möchten oder bereits Azure Rights Management für Ihren Mandanten aktiviert haben, können Sie direkt zum [nächsten Schritt](infoprotect-tutorial-step2.md) wechseln. 

Wenn Azure Rights Management aktiviert ist, können Sie Ihre vertraulichsten Dokumente und Dateien schützen, nachdem sie klassifiziert wurden. Zur Aktivierung von Azure Rights Management können Sie entweder das Office 365 Admin Center oder das klassische Azure-Portal verwenden:

-   Wenn Sie über ein Office 365-Abonnement mit Azure Rights Management oder ein Office 365-Abonnement ohne Azure Rights Management aber mit einem Abonnement für Azure RMS Premium verfügen: **Verwenden Sie das Office 365 Admin Center**.

-   Wenn Sie nicht über ein Office 365-Abonnement verfügen: **Verwenden Sie das klassische Azure-Portal**.

### So aktivieren Sie Rights Management über das klassische Office 365 Admin Center

> [!NOTE]
> Wenn Sie die **Office 365 Admin Center Preview** statt des klassischen Office 365 Admin Centers verwenden, können Sie entweder die Anweisungen unter [Aktivieren von Azure Rights Management über das Office 365 Admin Center (Vorschau)](../deploy-use/activate-office365-preview.md) ausführen oder zur klassischen Version wechseln, um die nachstehenden Anweisungen auszuführen. Klicken Sie dazu nach der Anmeldung auf der **Startseite** auf **Go to the old admin center** (Zum alten Admin Center wechseln).

1.  Gehen Sie zum [Office 365-Portal](https://portal.office.com/), und melden Sie sich mit Ihrem globalen Office 365-Administratorkonto an.

2.  Wenn das Office 365 Admin Center nicht automatisch angezeigt wird, wählen Sie in der linken oberen Ecke das Symbol für das App-Startprogramm und dann **Administrator** aus. Die Kachel **Administrator** wird nur für Office 365-Administratoren angezeigt.

  > [!TIP]
  > Hilfe zum Admin Center finden Sie in [Informationen zum Office 365 Admin Center - Hilfe für Administratoren](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  Klicken Sie im linken Bereich auf **DIENSTEINSTELLUNGEN**.

4.  Klicken Sie auf **Rights Management**.

5.  Klicken Sie auf der Seite **RIGHTS MANAGEMENT** auf **Verwalten**.

6.  Klicken Sie auf der Seite **Rights Management** auf **Aktivieren**.

7.  Wenn Sie gefragt werden **Möchten Sie die Rechteverwaltung aktivieren?**, klicken Sie auf **Aktivieren**.

**Rechteverwaltung ist aktiviert** und die Option zum Deaktivieren sollte jetzt angezeigt werden (Sie müssen die Seite u. U. manuell aktualisieren).

Klicken Sie zu diesem Zeitpunkt nicht auf **Erweiterte Funktionen**. Dadurch gelangen Sie zum klassischen Azure-Portal, wo Sie benutzerdefinierte Vorlagen konfigurieren können, die für dieses Tutorial jedoch nicht benötigt werden. Stattdessen können Sie das Office 365 Admin Center schließen.

### So aktivieren Sie Rights Management über das klassische Azure-Portal

1.  Gehen Sie zum [klassischen Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=275081), und melden Sie sich mit Ihrem globalen Azure Active Directory-Administratorkonto an.

2.  Klicken Sie im linken Bereich auf **ACTIVE DIRECTORY**.

3.  Klicken Sie auf der Seite **Active Directory** auf **RIGHTS MANAGEMENT**.

4.  Wählen Sie das Verzeichnis aus, für das Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] verwalten möchten, klicken Sie auf **AKTIVIEREN**, und bestätigen Sie Ihre Aktion.

Der **RECHTEVERWALTUNGSSTATUS** sollte nun **Aktiv** anzeigen, und die Option **AKTIVIEREN** wird durch **DEAKTIVIEREN**ersetzt.

Im Portal können Sie weitere Rights Management-Optionen konfigurieren, die für dieses Tutorial jedoch nicht erforderlich sind. Sie können das klassische Azure-Portal also schließen.

Dies ist bereits alles im ersten Schritt. Der Azure Rights Management-Dienst ist aktiviert, sodass Sie im Tutorial zu einem späteren Zeitpunkt eine der Standardvorlagen von Azure Rights Management für den Schutz von Dokumenten und E-Mails auswählen können, die als vertraulich eingestuft werden.

Für eine Produktionsbereitstellung sollten Sie benutzerdefinierte Vorlagen konfigurieren, zusätzlich zu den oder anstelle der beiden Standardvorlagen von Azure Rights Management. Da in diesem Tutorial aber keine benutzerdefinierten Vorlagen erforderlich sind, können Sie direkt zum zweiten Schritt übergehen.

|Weitere Informationen zu...|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zum Aktivieren von Rights Management|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|
|Standardvorlagen und Erstellung neuer benutzerdefinierter Vorlagen|[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; Einführung in](infoprotect-quick-start-tutorial.md)
[Schritt 2 &#187;](infoprotect-tutorial-step2.md)



<!--HONumber=Jul16_HO5-->


