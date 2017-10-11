---
title: "Mit der RMS-Freigabeanwendung ausgeführte Aufgaben – AIP"
description: "Anweisungen für Benutzer, die ein Upgrade von der RMS-Freigabeanwendung auf den Azure Information Protection-Client durchgeführt haben."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d7bc2478-c22f-4e19-9992-012658362b25
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 417294ff0890f2371909915a867fbdf56669e972
ms.sourcegitcommit: faaab68064f365c977dfd1890f7c8b05a144a95c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2017
---
# <a name="tasks-that-you-used-to-do-with-the-rms-sharing-application"></a>Üblicherweise mit der RMS-Freigabeanwendung ausgeführte Aufgaben

Haben Sie kürzlich ein Upgrade von der Rights Management-Freigabeanwendung (auch einfach nur als „RMS-Freigabeanwendung“ bezeichnet) auf den Azure Information Protection-Client durchgeführt? 

Verwenden Sie die folgenden Informationen als Hilfestellung, um schnell einsatzbereit zu sein.

|RMS-Freigabeanwendung|Vorgehensweise mit dem Azure Information Protection-Client
|-----------|--------------------|
|Schützen einer Datei auf einem Gerät <br /><br />Auch bekannt als „direkter Schutz“|Für Office-Apps: Wählen Sie eine Bezeichnung aus, die den erforderlichen Schutz anwendet, oder legen Sie benutzerdefinierte Berechtigungen fest.<br /><br />Für andere Dateien: Verwenden Sie die Datei-Explorer-Option **Klassifizieren und schützen**, um das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** zu öffnen. Dann wählen Sie eine Bezeichnung aus, die den erforderlichen Schutz anwendet, oder geben Sie Ihre eigenen benutzerdefinierten Berechtigungen an. <br /><br />Weitere Informationen finden Sie unter [Klassifizieren und Schützen einer Datei oder E-Mail](client-classify-protect.md).
|Schützen einer Datei, die per E-Mail freigegeben ist <br /><br />Auch bekannt als „geschütztes Freigeben“|Wenden Sie in Outlook eine Bezeichnung mit dem erforderlichen Schutz auf eine E-Mail an, oder wählen Sie die Outlook-Option **Nicht weiterleiten** aus. Ungeschützte Anhänge mit [unterstütztem Dateityp](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) werden automatisch geschützt.<br /><br />Hinweis: Zur Nachverfolgung eines geschützten Dokuments, das Sie per E-Mail senden, müssen Sie das Dokument erst schützen und dann der E-Mail anfügen.<br /><br />Weitere Informationen finden Sie unter [Klassifizieren und Schützen einer Datei oder E-Mail](client-classify-protect.md).
|Ändern von Berechtigungen für geschützte Dateien <br /><br />Auch als „erneutes Schützen“ bezeichnet|Für Office-Anwendungen, die die Azure Information Protection-Leiste anzeigen: Wählen Sie eine Bezeichnung aus, die den erforderlichen Schutz anwendet.<br /><br />Für andere Dateien und den Fall, dass sich der Azure Information Protection-Client im [reinen Schutzmodus](client-protection-only-mode.md) befindet: Verwenden Sie die Datei-Explorer-Menüoption **Klassifizieren und schützen**, um das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** zu öffnen. Dann wählen Sie eine Bezeichnung aus, die den erforderlichen Schutz anwendet, oder geben Sie Ihre eigenen benutzerdefinierten Berechtigungen an.<br /><br />Weitere Informationen finden Sie unter [Klassifizieren und Schützen einer Datei oder E-Mail](client-classify-protect.md).
|Nachverfolgen und Widerrufen von Dokumenten|Für Office-Anwendungen: Öffnen Sie das Dokument, und klicken Sie dann auf der Registerkarte **Start** in der Gruppe **Protection (Schutz)** auf **Protect (Schützen)** > **Track and revoke (Nachverfolgen und widerrufen)**.<br /><br />Über den Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine Datei oder einen Ordner > **Klassifizieren und schützen**. Klicken Sie dann im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf die Option **Track and revoke** (Nachverfolgen und widerrufen). <br /><br />Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen von Dokumenten](client-track-revoke.md).
|Anzeigen und Verwenden von Dateien, die geschützt wurden|Für geschützte Office-Dokumente muss Office installiert sein. Der Azure Information Protection-Viewer kann viele andere geschützte Dateien öffnen, damit Sie sie lesen, drucken und auch speichern können, wenn Sie über die entsprechenden Berechtigungen für diese Aktionen verfügen. Dieser Viewer wird automatisch mit dem Client oder separat installiert.<br /><br />Weitere Informationen finden Sie unter [Öffnen von geschützten Dateien](client-view-use-files.md).
|Entfernen des Schutzes von Dateien|Verwenden Sie die Datei-Explorer-Option **Klassifizieren und schützen**, um das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** zu öffnen. <br /><br />Deaktivieren Sie dann für eine einzelne Datei die Option **Protect with custom permissions** (Mit benutzerdefinierten Berechtigungen schützen). Klicken Sie bei mehreren Dateien oder einem Ordner auf die Option **Remove custom permissions** (Benutzerdefinierte Berechtigungen entfernen).<br /><br />Weitere Informationen finden Sie unter [Entfernen von Bezeichnungen und des Schutzes von Dateien und E-Mails](client-remove-label-protection.md).|

## <a name="cant-find-the-option-youre-looking-for"></a>Sie können die gewünschte Option nicht finden?

Wenn Sie nach einer bestimmten Option suchen, die Sie häufig für die RMS-Freigabeanwendung verwendet haben, überprüfen Sie die folgende Tabelle.

|Option in der RMS-Freigabeanwendung|Informationen
|-----------|--------------------|
|**Geschütztes Freigeben**|Diese Option ist im Office-Menüband nicht mehr verfügbar. Verwenden Sie anstelle der direkten Freigabe in der Office-Anwendung die Kontextmenüoption des Datei-Explorer, **Klassifizieren und schützen**, um eine Kopie des Dokuments mit benutzerdefinierten Berechtigungen zu schützen. Anschließend geben Sie die Datei mit dem gewünschten E-Mail-Client oder am gewünschten Freigabeort frei. <br /><br /> Sie können auch ein ungeschütztes Dokument an eine zu schützende E-Mail anfügen. Das Dokument wird in diesem Fall automatisch mit denselben Einschränkungen geschützt. Sie können das Dokument jedoch nicht nachverfolgen und widerrufen.
|**E-Mail an mich, wenn jemand versucht, diese Dokumente zu öffnen**|Verwenden Sie die Website für die Dokumentenverfolgung, um Ihre bevorzugte Einstellung für die E-Mail-Benachrichtigung zu konfigurieren: Suchen Sie das freigegebene geschützte Dokument > **Einstellungen** > **E-Mail-Benachrichtigungen**.
|**Zulassen, dass ich den Zugriff auf diese Dokumente sofort widerrufe**|Diese Option ist nicht mehr verfügbar. Konfigurieren Sie Vorlagen, die keinen Offlinezugriff zulassen. Darüber hinaus sollten Sie erwägen, ob Sie die Gültigkeitsdauer der Nutzungslizenz für Ihren Mandanten reduzieren, indem Sie das Cmdlet [Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime) ausführen.







[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
