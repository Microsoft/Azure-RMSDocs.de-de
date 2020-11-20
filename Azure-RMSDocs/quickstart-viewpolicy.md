---
title: 'Schnellstart: Anzeigen von Azure Information Protection (AIP) im Azure-Portal'
description: Wenn Ihre Organisation keine Erfahrungswerte mit Azure Information Protection (AIP) besitzt, beginnen Sie hier, um den Dienst zum Azure-Portal hinzuzufügen, die Aktivierung des Schutzdiensts zu überprüfen und Bezeichnungen und Richtlinieneinstellungen zu veröffentlichen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/19/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: b0128abb8d75418596459ac142a49dbbfa06b646
ms.sourcegitcommit: df6ee1aca02e089e3a72006ecf0747f14213979c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94503620"
---
# <a name="quickstart-get-started-with-azure-information-protection-in-the-azure-portal"></a>Schnellstart: Erste Schritte mit Azure Information Protection im Azure-Portal

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Klassischer Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

In dieser Schnellstartanleitung fügen Sie Azure Information Protection zum Azure-Portal hinzu, bestätigen die Aktivierung des Schutzdiensts, erstellen Standardbezeichnungen (falls noch keine Bezeichnungen vorhanden sind) und zeigen die Richtlinieneinstellungen für den Azure Information Protection-Client (klassisch) an.

**Benötigte Zeit:** Für diese Schnellstartanleitung benötigen Sie maximal 10 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Für die Durchführung dieses Schnellstarts benötigen Sie Folgendes:

- Zugriff auf Ihr Konto im [**Azure-Portal**](https://portal.azure.com/).

- Ein Abonnement, das [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) umfasst.

    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="add-azure-information-protection-to-the-azure-portal"></a>Hinzufügen von Azure Information Protection zum Azure-Portal

Auch wenn Sie über ein Abonnement verfügen, das [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) umfasst, ist das Feature nicht automatisch im Azure-Portal verfügbar.

Führen Sie die folgenden Schritte aus, um AIP zum Azure-Portal hinzuzufügen:

1. Melden Sie sich mit dem globalen Administratorkonto für Ihren Mandanten im [Azure-Portal](https://portal.azure.com) an.

    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

1. Wählen Sie **+ Ressource erstellen** aus. Geben Sie im Suchfeld für den Marketplace den Begriff **Azure Information Protection** ein, und wählen Sie die Option aus. Klicken Sie auf der Azure Information Protection-Seite auf **Erstellen** und dann erneut auf **Erstellen**.

    :::image type="content" source="media/gifs/quickstart-add-aip-to-portal.gif" alt-text="Hinzufügen von Azure Information Protection zum Azure-Portal":::

    > [!TIP]
    > Wenn Sie diesen Schritt zum ersten Mal durchführen, wird neben dem Namen des Bereichs das Symbol **An Dashboard anheften** ![Symbol „An Dashboard anheften“](media/qs-tutor/pin-to-dashboard.png "Symbol „An Dashboard anheften“") angezeigt. Wählen Sie dieses Symbol aus, um eine Kachel auf Ihrem Dashboard zu erstellen, sodass Sie beim nächsten Mal direkt hierher navigieren können.

## <a name="confirm-that-the-protection-service-is-activated"></a>Überprüfen, ob der Schutzdienst aktiviert ist

Der Schutzdienst ist jetzt für neue Kunden automatisch aktiviert. Überprüfen Sie – jetzt oder zu einem späteren Zeitpunkt –, ob der Dienst aktiviert ist. Gehen Sie dazu folgendermaßen vor:

1. Klicken Sie im Bereich **Azure Information Protection** auf die Optionen **Verwalten** > **Schutzaktivierung**.

1. Überprüfen Sie, ob der Schutz für Ihren Mandanten aktiviert ist. Beispiel:

    :::image type="content" source="media/qs-tutor/confirm-activation.PNG" alt-text="AIP-Aktivierung bestätigen":::

    Wenn der Schutz zu irgendeinem Zeitpunkt nicht aktiviert ist und Sie ihn aktivieren müssen, wählen Sie **Aktivieren** ![AIP aktivieren](media/qs-tutor/activate.png "AIP aktivieren") aus. Wenn die Aktivierung abgeschlossen ist, zeigt die Informationsleiste **Activation finished successfully** (Aktivierung erfolgreich) an.

## <a name="create-and-publish-labels"></a>Erstellen und Veröffentlichen von Bezeichnungen

Ihre Organisation verfügt möglicherweise bereits über Bezeichnungen, die automatisch für Ihren Mandanten erstellt wurden. Oder es wurden Vertraulichkeitsbezeichnungen im Office 365 Security & Compliance Center, Microsoft Security Center oder Microsoft-Compliance Center generiert. Sehen Sie sich dazu das folgende Beispiel an.

1. Wählen Sie unter **Klassifizierungen** die Option **Bezeichnungen** aus.

    Möglicherweise haben Sie schon einige Standardbezeichnungen erstellt. Die folgende Abbildung zeigt die Bezeichnungen, die bei Azure Information Protection standardmäßig erstellt werden:

    :::image type="content" source="media/info-protect-defaultlabels.png" alt-text="Azure Information Protection – Standardbezeichnungen":::

    **Wenn keine Standardbezeichnungen oder sonstigen Bezeichnungen angezeigt werden, gehen Sie folgendermaßen vor**:

    Wenn Sie weder Standardbezeichnungen noch andere Bezeichnungen sehen können, wählen Sie **Standardbezeichnungen generieren** aus, um diese für die Verwendung im klassischen Client zu erstellen.

    Wenn die Schaltfläche **Standardbezeichnungen generieren** oberhalb des Rasters nicht angezeigt wird, wählen Sie unter **Verwalten** die Option **Einheitliche Bezeichnungen** aus. Wenn der Status für einheitliche Bezeichnungen als **Nicht aktiviert** angezeigt wird, wählen Sie **Aktivieren** aus, und kehren Sie dann zum Bereich **Klassifizierung** > **Bezeichnungen** zurück.

    > [!NOTE]
    > Beim Client für einheitliche Bezeichnungen werden Bezeichnungen in Microsoft M365 verwaltet. Weitere Informationen finden Sie unter [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/encryption-sensitivity-labels).
    >

1. Veröffentlichen Sie Ihre Bezeichnungen im Azure-Portal, um diese für den klassischen Azure Information Protection-Client zur Verfügung zu stellen:

    1. Öffnen Sie die Richtlinie **Global**. Wählen Sie unter **Klassifizierungen** die Option **Richtlinien** > **Global** aus.

    1. Wählen Sie **Bezeichnungen hinzufügen oder entfernen** aus.

    1. Wählen Sie auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** alle Bezeichnungen aus, und klicken Sie dann auf **OK**.

    1. Wählen Sie auf dem Blatt **Richtlinie: Global** die Schaltfläche **Speichern** ![Speichern](media/qs-tutor/save-icon.png "Speichern") aus.

        Klicken Sie in der Eingabeaufforderung auf **OK**, um Ihre Änderungen zu veröffentlichen.

## <a name="view-your-labels"></a>Anzeigen von Bezeichnungen

Jetzt können Sie sich mit Bezeichnungen vertraut machen.

Wenn die Richtlinie **Global** noch geöffnet ist, klicken Sie oben rechts auf das **X**, um den Bereich zu schließen. Wählen Sie unter **Klassifizierungen** die Option **Bezeichnungen** aus.

Folgende Azure Information Protection-Klassifizierungsbezeichnungen stehen standardmäßig zur Verfügung:

- **Privat**
- **Allgemein**
- **Vertraulich**
- **Streng vertraulich**

Für einige Bezeichnungen sind standardmäßig optische Kennzeichnungen konfiguriert. Hierbei kann es sich um eine Fußzeile, eine Kopfzeile und/oder ein Wasserzeichen handeln. Auch für andere Bezeichnungen ist ein Schutz konfiguriert.

Wählen Sie eine Bezeichnung aus, und sehen Sie sich die detaillierte Konfiguration für diese Bezeichnung an.

> [!TIP]
> Erweitern Sie die Bezeichnung **Streng vertraulich**, um ein Beispiel für die Unterkategorien anzuzeigen, die in einer Klassifizierung enthalten sein können.
>

## <a name="view-your-policy-settings"></a>Anzeigen von Richtlinieneinstellungen

Wenn Sie das erste Mal über das Azure-Portal eine Verbindung mit dem Azure Information Protection-Dienst herstellen, werden automatisch Standardrichtlinieneinstellungen für Sie erstellt, die vom Azure Information Protection-Client verwendet werden.

- **Klassischer Client**: Beim klassischen Client werden sowohl Bezeichnungen als auch Richtlinieneinstellungen in den Client heruntergeladen, der in der Azure Information Protection-Richtlinie angegeben ist.

- **Client für einheitliche Bezeichnungen**: Beim Client für einheitliche Bezeichnungen werden nur Bezeichnungen in den Client heruntergeladen. Richtlinieneinstellungen werden aus dem Office 365 Compliance & Security Center, Microsoft 365 Compliance Center oder Microsoft 365 Security Center heruntergeladen. Verwenden Sie diese Admin Centers statt des Azure-Portals, um Ihre Bezeichnungen und Bezeichnungsrichtlinien zu bearbeiten.

    Weitere Informationen finden Sie in der Dokumentation zu Microsoft 365 im Artikel [Informationen zu Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/sensitivity-labels).

**Anleitung für den klassischen Client**:

So zeigen Sie die Standardrichtlinieneinstellungen für Azure Information Protection für den klassischen Client an:

1. Wählen Sie unter **Klassifizierungen** die Option **Richtlinien** > **Global** aus, um die standardmäßigen Azure Information Protection-Richtlinieneinstellungen anzuzeigen, die für Ihren Mandanten erstellt wurden.

1. Die Richtlinieneinstellungen werden nach den Bezeichnungen angezeigt, im Abschnitt **Einstellungen konfigurieren, die für Information Protection-Endbenutzer angezeigt und angewendet werden**. Zum Beispiel ist keine Standardbezeichnung festgelegt, Dokumente und E-Mails müssen keine Bezeichnungen aufweisen, und Benutzer müssen keine Begründung angeben, wenn sie Bezeichnungen ändern:

    :::image type="content" source="media/defaultsettings-aip.png" alt-text="Globale Richtlinieneinstellungen für Azure Information Protection":::

1. Sie können jetzt alle geöffneten Bereiche im Portal schließen.

## <a name="next-steps"></a>Nächste Schritte

Die nächsten Schritte fallen etwas unterschiedlich aus, je nachdem, ob Sie den klassischen Client oder den Client für einheitliche Bezeichnungen verwenden. Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, sehen Sie sich diese [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients) an.

**Bei Verwendung des klassischen Clients**:

- Für den nächsten Schritt ist das folgende Tutorial möglicherweise hilfreich: [Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md)

- Anstelle der ausführlichen Anweisungen zum Konfigurieren sämtlicher Aspekte der Azure Information Protection-Richtlinie können Sie [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md) lesen.

**Bei Verwendung des Clients für einheitliche Bezeichnungen**:

Weitere Informationen finden Sie in der Dokumentation für die Microsoft 365-Compliance unter [Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/sensitivity-labels)