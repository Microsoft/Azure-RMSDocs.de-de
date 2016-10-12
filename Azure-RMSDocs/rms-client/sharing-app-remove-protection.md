---
title: Entfernen des Schutzes von einer Datei mithilfe der Rights Management-Freigabeanwendung | Azure Information Protection
description: "Anweisungen zum Aufheben des Schutzes für eine Datei, die zuvor mit der RMS-Freigabeanwendung geschützt wurde."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: da95b938-eaad-4c83-a21e-ff1d4872aae4
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aac3c6c7b5167d729d9ac89d9ae71c50dd1b6a10
ms.openlocfilehash: ceb726e47c4eb9413b7d7eb5b1469e2a99992dda


---

# Entfernen des Schutzes von einer Datei mithilfe der Rights Management-Freigabeanwendung

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Um den Schutz von einer zu entfernen (d.h. den Dateischutz aufzuheben), die zuvor von der RMS-Freigabeanwendung geschützt wurde, verwenden Sie die Option **Schutz entfernen** im Datei-Explorer.

> [!IMPORTANT]
> Sie müssen einen Besitzer der Datei sein, um den Schutz zu entfernen.

## Vorgehensweise beim Entfernen des Schutzes von einer Datei

1.  Klicken Sie im Datei-Explorer mit der rechten Maustaste auf die Datei (z.B. Beispiel.ptxt), wählen Sie **Mit RMS schützen** aus, klicken Sie auf **Direkt schützen**, und klicken Sie dann auf **Schutz entfernen**:

    ![Die Menüoption „Schutz entfernen“ für RMS-Freigabeanwendung](../media/ADRMS_MSRMSApp_RemoveProtection.png)

    Sie werden möglicherweise zum Eingeben von Anmeldeinformationen aufgefordert.

Hinweis: Wenn diese Optionen nicht angezeigt werden, ist die RMS-Freigabeanwendung entweder nicht oder nicht in der neuesten Version auf Ihrem Computer installiert, oder der Computer muss neu gestartet werden, um die Installation abzuschließen. Weitere Informationen zum Installieren der Freigabeanwendung finden Sie unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md).

Die ursprüngliche geschützte Datei (z. B. Sample.ptxt) ist gelöscht und wurde von einer Datei mit dem gleichen Namen, jedoch mit der ungeschützten Dateinamenerweiterung (z. B. "Sample.txt") ersetzt.

## Beispiele und weitere Anweisungen
Beispiele für die Verwendung der Rights Management-Freigabeanwendung sowie weitere Anweisungen finden Sie in den folgenden Abschnitten des Benutzerhandbuchs für die Rights Management-Freigabeanwendung

-   [Beispiele für die Nutzung der RMS-Freigabeanwendung](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Was möchten Sie tun?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Weitere Informationen
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)



<!--HONumber=Sep16_HO4-->


