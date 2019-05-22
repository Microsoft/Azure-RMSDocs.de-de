---
title: 'Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails – AIP'
description: Konfigurieren Sie eine Bezeichnung, die eine E-Mail für einen Benutzer schützt, indem die Schutzrichtlinie „Nicht weiterleiten“ automatisch angewendet wird.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 05/20/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.openlocfilehash: 1485020b6edd47aae75486bf3a8215cf5cb14a1b
ms.sourcegitcommit: 8532536b778a26b971dba89436772158869ab84d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65935000"
---
# <a name="quickstart-configure-a-label-for-users-to-easily-protect-emails-that-contain-sensitive-information"></a>Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails, die vertrauliche Informationen enthalten

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

In dieser Schnellstartanleitung konfigurieren Sie eine vorhandene Bezeichnung zum automatischen Anwenden der Schutzeinstellung „Nicht weiterleiten“.

Die aktuelle Azure Information Protection-Richtlinie enthält bereits zwei Bezeichnungen, die diese Konfiguration aufweisen:

- **Vertraulich\Nur Empfänger**

- **Streng Vertraulich\Nur Empfänger**

Wenn Ihre Richtlinie jedoch älter ist oder die Schutzrichtlinie nicht aktiviert war, als die Richtlinie Ihrer Organisation erstellt wurde, sind diese Bezeichnungen nicht für Sie verfügbar. 

Für diese Konfiguration benötigen Sie 5 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

2. Sie haben das Azure Information Protection-Blatt zum Azure-Portal hinzugefügt und sich vergewissert, dass der Schutzdienst aktiviert ist.

    Wenn Sie Hilfe bei diesen Aktionen benötigen, lesen Sie [Schnellstart: Erste Schritte im Azure-Portal](quickstart-viewpolicy.md).

3. Eine Azure Information Protection-Bezeichnung, die konfiguriert werden soll. 
    
    Sie können eine der Standardbezeichnungen verwenden oder eine Bezeichnung, die Sie erstellt haben. Wenn Sie Hilfe beim Erstellen einer neuen Bezeichnung benötigen, lesen Sie [Schnellstart: Erstellen einer neuen Azure Information Protection-Bezeichnung für bestimmte Benutzer](quickstart-label-specificusers.md).

4. So testen Sie die neue Bezeichnung: Der Azure Information Protection-Client muss auf Computern für Benutzer installiert werden. 
    
    Um die Bezeichnung selbst zu testen, können Sie den Client installieren, indem Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) navigieren und **AzInfoProtection.exe** herunterladen.

5. So testen Sie die neue Bezeichnung: Ein Computer unter Windows (mindestens Windows 7 mit Service Pack 1), auf dem Sie bei Office-Apps aus einer der folgenden Kategorien angemeldet sind:
    
    - Mindestversion 1805 von Office-Apps, Build 9330.2078 von Office 365 Business oder Microsoft 365 Business, wenn Ihnen eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.
    
    - Office 365 ProPlus.
    
    - Office Professional Plus 2019.
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 mit Service Pack 1.
    
    - Office Professional Plus 2010 mit Service Pack 2.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="configure-an-existing-label-to-apply-the-do-not-forward-protection"></a>Konfigurieren einer vorhandenen Bezeichnung zum Anwenden der Schutzrichtlinie „Nicht weiterleiten“

1. Öffnen Sie ein neues Browserfenster, und melden Sie sich als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zu **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Wählen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** die Bezeichnung aus, die für die Anwendung des Schutzes konfiguriert werden soll. 

3. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**. Wählen Sie **Schützen** aus. Das Blatt **Schutz** wird automatisch geöffnet, wenn zuvor eine der anderen Optionen ausgewählt wurde. 
    
    Wenn das Blatt **Schutz** nicht automatisch geöffnet wird, wählen Sie **Schutz** aus:
    
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

1. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Wählen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** die konfigurierte Bezeichnung aus. 

3. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und klicken Sie auf **Nicht konfiguriert** und dann auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wurden die mindestens erforderlichen Optionen beschrieben, damit Sie schnell eine Bezeichnung konfigurieren können, die es Benutzern einfacher macht, ihre E-Mails zu schützen. Wenn die Konfiguration allerdings zu restriktiv oder nicht restriktiv genug ist, ziehen Sie die anderen Beispielkonfigurationen in Erwägung:

- [Bezeichnung für geschützte E-Mails, die weniger einschränkende Berechtigungen als „Nicht weiterleiten“ unterstützt](configure-policy-protection.md#example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward)

- [Bezeichnung, die Inhalt verschlüsselt, aber nicht einschränkt, wer darauf zugreifen kann](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)

Ausführliche Anweisungen zum Konfigurieren einer Bezeichnung, die Schutz anwendet, finden Sie unter [Gewusst wie: Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md). 
