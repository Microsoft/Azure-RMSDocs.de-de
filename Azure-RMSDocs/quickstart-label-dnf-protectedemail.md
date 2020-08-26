---
title: 'Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails mit Azure Information Protection (AIP)'
description: Konfigurieren Sie eine Bezeichnung, die eine E-Mail für einen Benutzer schützt, indem die Schutzrichtlinie „Nicht weiterleiten“ automatisch angewendet wird.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/04/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: acdf61bfbcd46ba58d65ccc4ecc5a387fce123dc
ms.sourcegitcommit: 0f10998e9623f59c36edf89e4661c9c953787aed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810302"
---
# <a name="quickstart-configure-a-label-for-users-to-easily-protect-emails-that-contain-sensitive-information"></a>Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails, die vertrauliche Informationen enthalten

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Klassischer Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE]
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

In dieser Schnellstartanleitung konfigurieren Sie eine vorhandene Azure Information Protection-Bezeichnung zum automatischen Anwenden der Schutzeinstellung **Nicht weiterleiten**.

Die aktuelle Azure Information Protection-Richtlinie enthält bereits zwei Bezeichnungen, die diese Konfiguration aufweisen:

- **Vertraulich\Nur Empfänger**

- **Streng Vertraulich\Nur Empfänger**

Wenn Ihre Richtlinie jedoch älter ist oder die Schutzrichtlinie nicht aktiviert war, als die Richtlinie Ihrer Organisation erstellt wurde, sind diese Bezeichnungen nicht für Sie verfügbar.

**Benötigte Zeit:** Für diese Konfiguration benötigen Sie 5 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

|Anforderung  |Beschreibung  |
|---------|---------|
|**Ein unterstützendes Abonnement**     |  Sie benötigen ein Abonnement, das [**Azure Information Protection-Plan 1 oder -Plan 2**](https://azure.microsoft.com/pricing/details/information-protection/) umfasst. </br></br>Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.       |
|**AIP zum Azure-Portal hinzugefügt**    |  Sie haben den Azure Information Protection-Bereich zum Azure-Portal hinzugefügt und sich vergewissert, dass der Schutzdienst aktiviert ist. </br></br>Weitere Informationen finden Sie unter [Schnellstart: Erste Schritte im Azure-Portal](quickstart-viewpolicy.md).       |
|**Eine vorhandene Azure Information Protection-Bezeichnung, die konfiguriert werden soll**     | Verwenden Sie eine der Standardbezeichnungen oder eine von Ihnen erstellte Bezeichnung. Weitere Informationen finden Sie unter [Schnellstart: Erstellen einer neuen Azure Information Protection-Bezeichnung für bestimmte Benutzer](quickstart-label-specificusers.md). |
|**Klassischer Client installiert**    |   Damit Sie die neue Bezeichnung testen können, muss der klassische Client auf Ihrem Computer installiert sein. </br></br>Der klassische Azure Information Protection-Client gilt ab März 2021 als veraltet. Zum Bereitstellen des klassischen AIP-Clients eröffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.  |
|**Ein Windows-Computer, der bei Office-Apps angemeldet ist** |Um die neue Bezeichnung testen zu können, benötigen Sie einen Computer, auf dem Windows ausgeführt wird (mindestens Windows 7 mit Service Pack 1). </br></br>Melden Sie sich auf diesem Computer bei einer der folgenden Office-App-Versionen an: </br>– Mindestversion 1805 von Office-Apps, Build 9330.2078 von Office 365 Business oder Microsoft 365 Business, wenn Ihnen eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde </br>– Office 365 ProPlus </br>– Office Professional Plus 2019. </br>– Office Professional Plus 2016.</br>– Office Professional Plus 2013 mit Service Pack 1. </br>– Office Professional Plus 2010 mit Service Pack 2.|
| | |

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="configure-an-existing-label-to-apply-the-do-not-forward-protection"></a>Konfigurieren einer vorhandenen Bezeichnung zum Anwenden der Schutzrichtlinie „Nicht weiterleiten“

1. Öffnen Sie ein neues Browserfenster, und melden Sie sich als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zu **Azure Information Protection**.

    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

1. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Wählen Sie im Bereich **Azure Information Protection – Bezeichnungen** die Bezeichnung aus, die für die Anwendung des Schutzes konfiguriert werden soll.

1. Suchen Sie im Bereich **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**. Klicken Sie auf **Schützen**. Der Bereich **Schutz** wird automatisch geöffnet, wenn zuvor **Nicht konfiguriert** oder **Schutz entfernen** ausgewählt wurde.

    Klicken Sie auf **Schutz**, wenn der Bereich **Schutz** nicht automatisch geöffnet wird:

    :::image type="content" source="media/info-protect-protection-bar-configured.png" alt-text="Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung":::

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.

1. Wählen Sie die Option **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus.

1. Stellen Sie sicher, dass die folgende Option ausgewählt ist: **In Outlook apply Do Not Forward** („Nicht weiterleiten“ in Outlook anwenden).

1. Wenn die Option ausgewählt ist, deaktivieren Sie die folgende Option: **In Word, Excel, PowerPoint and File Explorer prompt user for custom permissions** (Vom Benutzer in Word, Excel, PowerPoint und dem Datei-Explorer benutzerdefinierte Berechtigungen verlangen).

1. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.

Ihre Bezeichnung ist jetzt so konfiguriert, dass sie nur in Outlook angezeigt wird, und der Schutz **Nicht weiterleiten** wird auf E-Mails angewendet.

## <a name="test-your-new-label"></a>Testen Ihrer neuen Bezeichnung

Ihre konfigurierte Bezeichnung wird nur in Outlook angezeigt und eignet sich für E-Mails, die an einen beliebigen Empfänger außerhalb Ihrer Organisation gesendet wird, wenn Exchange Online für die [neuen Funktionen in Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist.

1. Öffnen Sie auf Ihrem Computer Outlook, und erstellen Sie eine neue E-Mail-Nachricht. Wenn Outlook bereits geöffnet ist, starten Sie es neu, um eine Richtlinienaktualisierung zu erzwingen.

2. Geben Sie die Empfänger sowie Text für die E-Mail-Nachricht an, und wenden Sie dann die Bezeichnung an, die Sie gerade erstellt haben.

    Die E-Mail-Nachricht ist gemäß den Namen der Bezeichnung klassifiziert und mit der Einschränkung „Nicht weiterleiten“ geschützt.

3. Senden Sie die E-Mail.

Dies führt dazu, dass die Empfänger die E-Mail weder weiterleiten noch drucken oder Inhalte daraus kopieren, Anhänge speichern oder die E-Mail unter einem anderen Namen speichern können. Die geschützte E-Mail-Nachricht kann von allen Benutzern auf jedem Gerät gelesen werden.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Führen Sie die folgenden Schritte durch, wenn Sie diese Konfiguration nicht beibehalten möchten und kein Schutz auf Ihre Bezeichnung angewendet werden soll:

1. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Wählen Sie im Bereich **Azure Information Protection – Bezeichnungen** die konfigurierte Bezeichnung aus.

1. Suchen Sie im Bereich **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und klicken Sie auf **Nicht konfiguriert** und dann auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wurden die mindestens erforderlichen Optionen beschrieben, damit Sie schnell eine Bezeichnung konfigurieren können, die es Benutzern einfacher macht, ihre E-Mails zu schützen. Wenn die Konfiguration allerdings zu restriktiv oder nicht restriktiv genug ist, ziehen Sie die anderen Beispielkonfigurationen in Erwägung:

- [Bezeichnung für geschützte E-Mails, die weniger einschränkende Berechtigungen als „Nicht weiterleiten“ unterstützt](configure-policy-protection.md#example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward)

- [Bezeichnung, die Inhalt verschlüsselt, aber nicht einschränkt, wer darauf zugreifen kann](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)

Ausführliche Anweisungen zum Konfigurieren einer Bezeichnung, die Schutz anwendet, finden Sie unter [Gewusst wie: Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
