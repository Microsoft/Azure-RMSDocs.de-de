---
title: "Azure RMS Quick Start-Lernprogramm – Schritt 1 | Azure RMS"
description: "Dies ist der erste Schritt eines Tutorials, in dem Sie Microsoft Azure Rights Management in nur fünf Schritten und weniger als 15 Minuten für Ihr Unternehmen testen können."
keywords: 
author: Cabailey
manager: mbaldwin
ms.date: 06/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.assetid: 7c4798e6-34a0-4c3f-a47f-505764ddf322
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: c00264e6c8b99d95e8eedf9b91781484611880c3


---



# Azure RMS Quick Start – Schritt 1: Aktivieren des Rights Management-Diensts

>*Gilt für: Azure Rights Management, Office 365*


Wechseln zu: 
> [!div class="op_single_selector"]
- [Einführung](quick-start-tutorial.md)
- [Schritt 1: Aktivieren von Azure RMS](tutorial-step1.md)
- [Schritt 2: Installieren der RMS-Freigabe-App](tutorial-step2.md)
- [Schritt 3: Senden des vertraulichen Dokuments per E-Mail](tutorial-step3.md)
- [Schritt 4: Lesen des Dokuments durch den Empfänger](tutorial-step4.md)
- [Schritt 5: Nachverfolgen des Dokuments](tutorial-step5.md)


![Azure RMS Schnellstart-Tutorial Schritt 1](../media/AzRMS_QuickStartSteps1.PNG)

Auch wenn Sie über ein Abonnement mit Unterstützung von Azure Rights Management verfügen, ist der Dienst standardmäßig deaktiviert. Zur Aktivierung können Sie entweder das Office 365 Admin Center oder das klassische Azure-Portal verwenden:

-   Wenn Sie über ein Office 365-Abonnement mit Azure Rights Management oder ein Office 365-Abonnement ohne Azure Rights Management aber mit einem Abonnement für Azure RMS Premium verfügen: **Verwenden Sie das Office 365 Admin Center**.

-   Wenn Sie nicht über ein Office 365-Abonnement verfügen: **Verwenden Sie das klassische Azure-Portal**.

![Screenshots zu Schritt 1 des Tutorials](../media/AzRMS_Tutorial_1_Screenshots.png)

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

Klicken Sie zu diesem Zeitpunkt nicht auf **Erweiterte Funktionen**. Dadurch gelangen Sie zum klassischen Azure-Portal, wo Sie Vorlagen konfigurieren können, die für dieses Tutorial jedoch nicht benötigt werden. Stattdessen können Sie das Office 365 Admin Center schließen.

### So aktivieren Sie Rights Management über das klassische Azure-Portal

1.  Gehen Sie zum [klassischen Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=275081), und melden Sie sich mit Ihrem globalen Azure Active Directory-Administratorkonto an.

2.  Klicken Sie im linken Bereich auf **ACTIVE DIRECTORY**.

3.  Klicken Sie auf der Seite **Active Directory** auf **RIGHTS MANAGEMENT**.

4.  Wählen Sie das Verzeichnis aus, für das Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] verwalten möchten, klicken Sie auf **AKTIVIEREN**, und bestätigen Sie Ihre Aktion.

Der **RECHTEVERWALTUNGSSTATUS** sollte nun **Aktiv** anzeigen, und die Option **AKTIVIEREN** wird durch **DEAKTIVIEREN**ersetzt.

Im Portal können Sie weitere Rights Management-Optionen konfigurieren, die für dieses Tutorial jedoch nicht erforderlich sind. Sie können das klassische Azure-Portal also schließen.

Dies ist bereits alles im ersten Schritt. Der Dienst ist aktiviert, sodass alle Benutzer Ihrer Organisation sofort beginnen können, wichtige und vertrauliche Dokumente zu schützen. In einer Produktionsumgebung können Sie die Zahl der Benutzer anfangs einschränken, um ein schrittweises Rollout auszuführen. In diesem Tutorial ist dieser Schritt jedoch nicht erforderlich.

Obwohl hier nicht auf benutzerdefinierte Vorlagen eingegangen wird, müssen Sie diese in einer Produktionsbereitstellung wahrscheinlich konfigurieren. Mithilfe von Vorlagen können Benutzer die richtigen Einstellungen zum Dateischutz schnell anwenden. Bei der Rights Management-Aktivierung erhalten Sie automatisch zwei Standardvorlagen. Es ist davon auszugehen, dass Sie in einer Produktionsumgebung eigene benutzerdefinierte Vorlagen hinzufügen werden. Da in diesem Tutorial keine Vorlagen erforderlich sind, können Sie direkt zum nächsten Schritt übergehen.

|Weitere Informationen zu...|Weitere Informationen|
|--------------------------------|--------------------------|
|Aktivieren von Rights Management und Festlegen der Benutzer, die Dateien und E-Mails nach der Dienstaktivierung schützen können|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|
|Standardvorlagen und Erstellung neuer benutzerdefinierter Vorlagen|[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md)|


>[!div class="step-by-step"]
[« Einleitung](quick-start-tutorial.md)
[Schritt 2 »](tutorial-step2.md)


<!--HONumber=Aug16_HO4-->


