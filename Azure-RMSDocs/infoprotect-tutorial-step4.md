---
title: Schnellstart-Tutorial Schritt 4 – AIP
description: Schritt 4 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Bezeichnung und Schutz in Aktion.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
ms.openlocfilehash: 965725410fd3435f2468810b5cafcbfa91c4fa5b
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39475117"
---
# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Schritt 4: Klassifizierung, Bezeichnung und Schutz in Aktion 

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Nun, da Sie ein Word-Dokument mit dem installierten Azure Information Protection-Client geöffnet haben, können Sie sehen, wie einfach das Bezeichnen und Schützen Ihres Dokuments, mithilfe der Richtlinie ist, die wir konfiguriert haben.

Klassifizierung und Schutz treten in Kraft, wenn Sie das Dokument speichern. Bevor wir dies jedoch tun, verwenden wir unser nicht gespeichertes Dokument und können testen, wie einfach es ist, Bezeichnungen anzuwenden und zu ändern.

## <a name="to-manually-change-our-default-label"></a>So ändern Sie die Standardbezeichnung manuell

Wählen Sie auf der Leiste „Information Protection“ die letzte Bezeichnung aus. Nun sehen Sie, wie untergeordnete Bezeichnungen dargestellt werden:

![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Auswählen einer untergeordneten Bezeichnung](./media/info-protect-sub-labelsv2.png)

Wählen Sie eine dieser untergeordneten Bezeichnungen aus. Nun sehen Sie, wie die anderen Bezeichnungen nicht länger auf der Leiste angezeigt werden, sobald Sie eine Bezeichnung für dieses Dokument ausgewählt haben. Für den Wert **Sensitivity** (Vertraulichkeit) werden nun der Name der Bezeichnung und der untergeordneten Bezeichnung sowie die dazugehörige Farbe angezeigt. Beispiel:

![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – ausgewählte untergeordnete Bezeichnung](./media/info-protect-sub-label-selectedv2.png)

Klicken Sie auf der Information Protection-Leiste neben dem aktuell ausgewählten Bezeichnungswert auf das Symbol **Edit Label** (Bezeichnung bearbeiten):

![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Symbol „Bezeichnung bearbeiten“](./media/info-protect-edit-label-selectedv2.png)

Dadurch werden die verfügbaren Bezeichnungen erneut angezeigt.

Wählen Sie nun die erste Bezeichnung **Personal** (Persönlich) aus. Da Sie eine Bezeichnung ausgewählt haben, die eine niedrigere Klassifizierung als die ausgewählte Bezeichnung für dieses Dokument darstellt, werden Sie aufgefordert zu begründen, warum Sie die Klassifizierungsebene senken:

![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Bestätigungsaufforderung bei Reduzierung](./media/info-protect-lower-justification.png)

Wählen Sie **The previous label no longer applies** (Vorherige Bezeichnung gilt nicht mehr) aus, und klicken Sie auf **Bestätigen**. Der Wert **Sensitivity** (Vertraulichkeit) ändert sich in **Persönlich**, und die anderen Bezeichnungen werden wieder ausgeblendet.

## <a name="to-remove-the-classification-completely"></a>So entfernen Sie die Klassifizierung vollständig

Klicken Sie auf der Information Protection-Leiste erneut auf das Symbol **Edit label** (Bezeichnung bearbeiten). Klicken Sie auf das Symbol **Delete label** (Bezeichnung löschen), anstatt eine der Bezeichnungen auszuwählen:

![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Symbol „Löschen“](./media/delete-icon-from-personalv2.png)

Geben Sie dieses Mal „Dieses Dokument erfordert keine Klassifizierung“ ein, wenn Sie dazu aufgefordert werden, und klicken Sie dann auf **Confirm** (Bestätigen).  

Der Wert **Vertraulichkeit** wird mit **Nicht festgelegt** angezeigt. Dies sehen Benutzer zunächst, wenn Sie keine Standardbezeichnung festlegen.

## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>So wird eine Empfehlungsaufforderung für die Bezeichnung und den automatischen Schutz angezeigt

1. Geben Sie im Word-Dokument eine gültige Kreditkartennummer ein, zum Beispiel: **4242-4242-4242-4242**. 

2. Speichern Sie das Dokument lokal mit einem beliebigen Dateinamen. 

3. Nun sehen Sie eine Aufforderung zur Anwendung der Bezeichnung, die Sie für den Schutz konfiguriert haben, wenn Kreditkartennummern erkannt werden. Falls Sie mit der Empfehlung nicht einverstanden sind, ermöglicht Ihnen die Richtlinieneinstellung, diese durch Auswählen von **Dismiss** (Verwerfen) abzulehnen. Indem eine Empfehlung gegeben wird, der Benutzer sie jedoch außer Kraft setzen kann, werden falsch positive Ergebnisse bei der Verwendung der automatischen Klassifizierung reduziert. Klicken Sie für dieses Tutorial auf **Change now** (Jetzt ändern).

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Empfehlungsaufforderung](./media/change-nowv2.png)

    Das Dokument zeigt nun an, dass die konfigurierte Bezeichnung angewendet wird (z.B. **Confidential \ Finance** (Vertraulich\Finanzen)) und es wird auch sofort das Wasserzeichen Ihrer Organisation auf der Seite angezeigt. Zudem wird die Fußnote **Classified as Confidential** (Als vertraulich eingestuft) angewendet. 

    Das Dokument ist ebenfalls mit den Berechtigungen geschützt, die Sie für diese Bezeichnung angegeben haben. Sie können bestätigen, dass das Dokument geschützt ist, indem Sie auf die Registerkarte **Datei** klicken und die Informationen für **Dokument schützen** anzeigen lassen. Ihnen wird angezeigt, dass das Dokument durch **Confidential \ Finance** (Vertraulich\Finanzen) und die Beschreibung der Bezeichnung geschützt ist. 
    
    Durch die Schutzkonfiguration der Bezeichnung können nur Angestellte das Dokument öffnen und einige Aktionen sind für diese eingeschränkt. Da sie zum Beispiel nicht über die Berechtigungen zum Drucken und zum Kopieren und Extrahieren von Inhalt verfügen, können sie das Dokument nicht drucken oder Teile daraus kopieren. Mit solchen Einschränkungen kann Datenverlust verhindert werden. Als Besitzer des Dokuments können Sie daraus kopieren und es drucken, aber wenn Sie es an einen anderen Benutzer in Ihrer Organisation per E-Mail senden, kann dieser diese Aktionen nicht durchführen.

4. Sie können das Dokument jetzt schließen.

Sehen wir uns nach der Klassifizierung, der Bezeichnung und dem Schutz von Dokumenten nun an, wie Sie Ihre Dokumente schützen können, wenn diese für andere Benutzer in einer anderen Organisation freigegeben werden. Sie können sogar nachverfolgen, wie sie verwendet werden und den Zugriff auf diese Dokumente widerrufen.

|Weitere Informationen zu|Zusätzliche Informationen|
|--------------------------------|--------------------------|
|Vollständige Anweisungen zum Bezeichnen und Schützen von Dateien |[Klassifizieren und Schützen einer Datei oder E-Mail](./rms-client/client-classify-protect.md)|
|Bezeichnungsaktivität ist Protokollierung |[Protokollieren der Verwendung für den Azure Information Protection-Client](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client)|


>[!div class="step-by-step"]
[&#171; Schritt 3](infoprotect-tutorial-step3.md)
[Schritt 5 &#187;](infoprotect-tutorial-step5.md)
