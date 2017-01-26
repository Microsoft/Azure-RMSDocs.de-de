---
title: 'Gewusst wie: Erstellen einer neuen Bezeichnung | Azure Information Protection'
description: "Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 392dcaf1b28dc26b34ce04a9143c4a8947073e12


---

# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Erstellen einer neuen Bezeichnung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden.

Sie können eine neue Bezeichnung hinzufügen oder einer vorhandenen Bezeichnung eine neue untergeordnete Bezeichnung hinzufügen, wenn eine weitere Klassifizierungsebene erforderlich ist. Die in der [Standardrichtlinie](configure-policy-default.md) enthaltene Bezeichnung **Secret** (Geheim) umfasst z. B. untergeordnete Bezeichnungen.

Verwenden Sie die folgenden Anleitungen, um der Azure Information Protection-Richtlinie eine neue Bezeichnung hinzuzufügen.

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die neue Bezeichnung, die Sie hinzufügen möchten, für alle Benutzer gilt, führen Sie einen der folgenden Schritte auf dem Blatt **Policy:Global** (Richtlinie: Global) aus. 

    - So erstellen Sie eine neue Bezeichnung: Klicken Sie auf **Add a new label** (Neue Bezeichnung hinzufügen).

    - So erstellen Sie eine neue untergeordnete Bezeichnung: Klicken Sie mit der rechten Maustaste, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, für die Sie eine untergeordnete Bezeichnung erstellen möchten, und klicken Sie dann auf **Add a sub-label** (Untergeordnete Bezeichnung hinzufügen).


     Wenn sich die neue Bezeichnung, die Sie hinzufügen möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, wählen Sie zunächst die bereichsbezogene Richtlinie auf dem ersten Blatt **Azure Information Protection** aus.

3. Wählen Sie auf dem Blatt **Label** (Bezeichnung) oder **Sub-label** (Untergeordnete Bezeichnung) die gewünschten Optionen für diese neue Bezeichnung, und klicken Sie dann auf **Save** (Speichern).

    > [!NOTE]
    >Informationen zum Festlegen des Schutzes finden Sie unter [Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden](configure-policy-protection.md).

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]




<!--HONumber=Jan17_HO4-->


