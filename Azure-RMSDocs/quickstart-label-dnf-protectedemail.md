---
title: 'Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails, die vertraulichen Informationen enthalten'
description: Konfigurieren Sie eine Bezeichnung, die eine E-Mail für einen Benutzer schützt, indem die Schutzrichtlinie „Nicht weiterleiten“ automatisch angewendet wird.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 793c3ff3b68de66dce5876c25cb4ba5455d19c33
ms.sourcegitcommit: ad37950f6a747c86f6496c6de859e18446f9b03f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51644691"
---
# <a name="quickstart-configure-a-label-for-users-to-easily-protect-emails-that-contain-sensitive-information"></a>Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails, die vertraulichen Informationen enthalten

In dieser Schnellstartanleitung konfigurieren Sie eine vorhandene Bezeichnung zum automatischen Anwenden der Schutzeinstellung „Nicht weiterleiten“.

Die aktuelle Azure Information Protection-Richtlinie enthält bereits zwei Bezeichnungen, die diese Konfiguration aufweisen:

- **Vertraulich\Nur Empfänger**

- **Streng Vertraulich\Nur Empfänger**

Wenn Ihre Richtlinie jedoch älter ist oder die Schutzrichtlinie nicht aktiviert war, als die Richtlinie Ihrer Organisation erstellt wurde, sind diese Bezeichnungen nicht für Sie verfügbar. 

Für diese Konfiguration benötigen Sie 5 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

2. Sie haben das Azure Information Protection-Blatt zum Azure-Portal hinzugefügt und sich vergewissert, dass der Schutzdienst aktiviert ist.

    Wenn Sie Hilfe bei diesen Aktionen benötigen, lesen Sie [Schnellstart: Erste Schritte im Azure-Portal](quickstart-viewpolicy.md).

3. Eine Azure Information Protection-Bezeichnung, die konfiguriert werden soll. 
    
    Sie können eine der Standardbezeichnungen verwenden oder eine Bezeichnung, die Sie erstellt haben. Wenn Sie Hilfe bei der Erstellung einer neuen Bezeichnung benötigen, lesen Sie [Schnellstart: Erstellen einer neuen Azure Information Protection-Bezeichnung für bestimmte Benutzer](quickstart-label-specificusers.md).

4. Um die neue Bezeichnung testen zu können, muss der Azure Information Protection-Client auf Computern für Benutzer installiert werden. 
    
    Um die Bezeichnung selbst zu testen, können Sie den Client installieren, indem Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) navigieren und **AzInfoProtection.exe** herunterladen.

5. Um die neue Bezeichnung zu testen, benötigen Sie einen Computer unter Windows (mindestens Windows 7 mit Service Pack 1), auf dem Sie bei Office-Apps aus einer der folgenden Kategorien angemeldet sind:
    
    - Office 365 mit Office 2016-Apps (mindestens Version 1805, Build 9330.2078). Um diese Option zu nutzen, muss Ihrem Konto eine Azure Rights Management-Lizenz zugewiesen sein. Diese Lizenz ist im Azure Information Protection-Abonnement enthalten.
    
    - Office 365 ProPlus mit 2016-Apps oder 2013-Apps (Klick-und-Los- oder Windows Installer-basierte Installation).
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 mit Service Pack 1.
    
    - Office Professional Plus 2010 mit Service Pack 2.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="configure-an-existing-label-to-apply-the-do-not-forward-protection"></a>Konfigurieren einer vorhandenen Bezeichnung zum Anwenden der Schutzrichtlinie „Nicht weiterleiten“

1. Öffnen Sie ein neues Browserfenster, und melden Sie sich als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zu **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen**: Wählen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** die Bezeichnung aus, die für die Anwendung des Schutzes konfiguriert werden soll. 

3. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**. Klicken Sie auf **Schützen** und dann auf **Schutz**:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](./media/info-protect-protection-bar-configured.png).

4. Stellen Sie sicher, dass auf dem Blatt **Schutz** die Option **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt ist.
    
5. Wählen Sie die Option **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus.

6. Stellen Sie sicher, dass die folgende Option ausgewählt ist: **In Outlook apply Do Not Forward** („Nicht weiterleiten“ in Outlook anwenden).

7. Wenn die Option ausgewählt ist, deaktivieren Sie die folgende Option: **In Word, Excel, PowerPoint and File Explorer prompt user for custom permissions** (Vom Benutzer in Word, Excel, PowerPoint und dem Datei-Explorer benutzerdefinierte Berechtigungen verlangen).

8. Klicken Sie auf dem Blatt **Schutz** auf **OK**, und klicken Sie auf dem Blatt **Bezeichnung** auf **Speichern**.

Ihre Bezeichnung ist nun für die ausschließliche Anzeige in Outlook konfiguriert, und der Schutz „Nicht weiterleiten“ wird auf E-Mails angewendet.

## <a name="test-your-new-label"></a>Testen Ihrer neuen Bezeichnung

Ihre konfigurierte Bezeichnung wird nur in Outlook angezeigt und eignet sich für E-Mails, die an einen beliebigen Empfänger außerhalb Ihrer Organisation gesendet wird, wenn Exchange Online für die [neuen Funktionen in Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist.

1. Öffnen Sie auf Ihrem Computer Outlook, und erstellen Sie eine neue E-Mail-Nachricht. Wenn Outlook bereits geöffnet ist, starten Sie es neu, um eine Richtlinienaktualisierung zu erzwingen.

2. Geben Sie die Empfänger sowie Text für die E-Mail-Nachricht an, und wenden Sie dann die Bezeichnung an, die Sie gerade erstellt haben. 
    
    Die E-Mail-Nachricht ist gemäß den Namen der Bezeichnung klassifiziert und mit der Einschränkung „Nicht weiterleiten“ geschützt.

3. Senden Sie die E-Mail. 

Dadurch können Empfänger die E-Mail nicht weiterleiten, drucken, etwas daraus kopieren, Anhänge speichern oder die E-Mail unter einem anderem Namen speichern. Die geschützte E-Mail-Nachricht kann von allen Benutzern auf jedem Gerät gelesen werden.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Führen Sie die folgenden Schritte durch, wenn Sie diese Konfiguration nicht beibehalten möchten und kein Schutz auf Ihre Bezeichnung angewendet werden soll:

1. Über die Menüoption **Klassifizierungen** > **Bezeichnungen**: Wählen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** die Bezeichnung aus, die Sie konfigurieren möchten. 

3. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und klicken Sie auf **Nicht konfiguriert** und dann auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wurden die mindestens erforderlichen Optionen beschrieben, damit Sie schnell eine Bezeichnung konfigurieren können, die es Benutzern einfacher macht, ihre E-Mails zu schützen. Wenn die Konfiguration allerdings zu restriktiv oder nicht restriktiv genug ist, ziehen Sie die anderen Beispielkonfigurationen in Erwägung:

- [Bezeichnung für geschützte E-Mails, die weniger einschränkende Berechtigungen als „Nicht weiterleiten“ unterstützt](configure-policy-protection.md#example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward)

- [Bezeichnung, die Inhalt verschlüsselt, aber nicht einschränkt, wer darauf zugreifen kann](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)

Ausführliche Anweisungen zum Konfigurieren einer Bezeichnung, die Schutz anwendet, finden Sie unter [Gewusst wie: Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md). 