---
title: Neue Azure Information Protection-Bezeichnung
description: Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: f24b4e8ac44377ab1c0b18244a376971ade87ebb
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Erstellen einer neuen Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden.

Sie können eine neue Bezeichnung hinzufügen oder einer vorhandenen Bezeichnung eine neue untergeordnete Bezeichnung hinzufügen, wenn eine weitere Klassifizierungsebene erforderlich ist. Die letzte Bezeichnung in der [Standardrichtlinie](configure-policy-default.md) enthält z.B. untergeordnete Bezeichnungen.

Wenn Sie die erste untergeordnete Bezeichnung für eine Bezeichnung erstellen, können Benutzer nicht länger die ursprüngliche Bezeichnung, also die übergeordnete Bezeichnung, auswählen. Erstellen Sie falls nötig eine neue untergeordnete Bezeichnung, um die Einstellungen der übergeordneten Bezeichnung neu zu erstellen, sodass Benutzer die gleichen Einstellungen anwenden können.

Verwenden Sie die folgenden Anleitungen, um der Azure Information Protection-Richtlinie eine neue Bezeichnung hinzuzufügen.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die hinzuzufügende neue Bezeichnung für alle Benutzer verfügbar ist, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien).
    
    Wenn die neue Bezeichnung, die Sie hinzufügen möchten, nur für ausgewählte Benutzer in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

3. Führen Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) oder auf dem Blatt **Richtlinie\<name>** eine der folgenden Aktionen durch:
    
    - So erstellen Sie eine neue Bezeichnung: Klicken Sie auf **Add a new label** (Neue Bezeichnung hinzufügen).
    
    - So erstellen Sie eine neue untergeordnete Bezeichnung: Klicken Sie mit der rechten Maustaste, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, für die Sie eine untergeordnete Bezeichnung erstellen möchten, und klicken Sie dann auf **Add a sub-label** (Untergeordnete Bezeichnung hinzufügen).

4. Wählen Sie auf dem Blatt **Label** (Bezeichnung) oder **Sub-label** (Untergeordnete Bezeichnung) die gewünschten Optionen für diese neue Bezeichnung, und klicken Sie dann auf **Save** (Speichern).
    
    Wenn Sie einen Anzeigenamen angeben, dürfen Sie einige Zeichen nicht verwenden (z.B. den umgekehrten Schrägstrich und das kaufmännische Und-Zeichen), da diese Zeichen nicht von allen Diensten und Anwendungen unterstützt werden, die Azure Information Protection nutzen. Verwenden Sie – neben den gesperrten Zeichen – auch das **#**-Zeichen nicht.    
    
    Beachten Sie, dass neuen Bezeichnungen automatisch die Farbe Schwarz zugewiesen wird. Wählen Sie eine eindeutige Farbe aus der Liste der Farben aus, oder geben Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe ein. Beispiel: **#DAA520**. Wenn Sie eine Referenz für diese Codes benötigen, ist [Colors by Name (Farben nach Namen)](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) aus der MSDN-Dokumentation ein hilfreicher Ausgangspunkt. Sie finden diese Codes in vielen Bildbearbeitungsprogrammen wie Microsoft Paint, wo Sie eine benutzerdefinierte Farbe aus einer Palette auswählen und automatisch die RGB-Werte angezeigt werden.

5. Klicken Sie auf dem anfänglichen Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

6. Wenn Sie diesen neuen Bezeichnungsnamen und eine Beschreibung in verschiedenen Sprachen anzeigen möchten, führen Sie die Verfahren unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md) aus. 

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

