---
title: Neue Azure Information Protection-Bezeichnung – AIP
description: Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: 7302e0e0e76f6ca94eba678390e7d938172e40c4
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304994"
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Erstellen einer neuen Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen.

Sie können eine neue Bezeichnung hinzufügen oder einer vorhandenen Bezeichnung eine neue untergeordnete Bezeichnung hinzufügen, wenn eine weitere Klassifizierungsebene erforderlich ist. Die letzte Bezeichnung in der [Standardrichtlinie](configure-policy-default.md) enthält z.B. untergeordnete Bezeichnungen.

Wenn Sie die erste untergeordnete Bezeichnung für eine Bezeichnung erstellen, können Benutzer nicht länger die ursprüngliche Bezeichnung, also die übergeordnete Bezeichnung, auswählen. Erstellen Sie falls nötig eine neue untergeordnete Bezeichnung, um die Einstellungen der übergeordneten Bezeichnung neu zu erstellen, sodass Benutzer die gleichen Einstellungen anwenden können.

Fügen Sie mithilfe der folgenden Anweisungen eine neue Bezeichnung hinzu, die zur Azure Information Protection-Richtlinie hinzugefügt werden kann.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Führen Sie auf dem Blatt **Azure Information Protection-Bezeichnungen** eine der folgenden Aktionen aus:
    
    - So erstellen Sie eine neue Bezeichnung: Klicken Sie auf **Add a new label** (Neue Bezeichnung hinzufügen).
    
    - So erstellen Sie eine neue untergeordnete Bezeichnung: Klicken Sie mit der rechten Maustaste, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, für die Sie eine untergeordnete Bezeichnung erstellen möchten, und klicken Sie dann auf **Add a sub-label** (Untergeordnete Bezeichnung hinzufügen).

4. Wählen Sie auf dem Blatt **Label** (Bezeichnung) oder **Sub-label** (Untergeordnete Bezeichnung) die gewünschten Optionen für diese neue Bezeichnung, und klicken Sie dann auf **Save** (Speichern).
    
    Wenn Sie einen Anzeigenamen angeben, dürfen Sie einige Zeichen nicht verwenden (z.B. den umgekehrten Schrägstrich und das kaufmännische Und-Zeichen), da diese Zeichen nicht von allen Diensten und Anwendungen unterstützt werden, die Azure Information Protection nutzen. Verwenden Sie – neben den gesperrten Zeichen – auch das **#**-Zeichen nicht.    
    
    Beachten Sie, dass neuen Bezeichnungen automatisch die Farbe Schwarz zugewiesen wird. Wählen Sie eine eindeutige Farbe aus der Liste der Farben aus, oder geben Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe ein. Beispiel: **#DAA520**. Wenn Sie eine Referenz für diese Codes benötigen, ist [Colors by Name (Farben nach Namen)](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) aus der MSDN-Dokumentation ein hilfreicher Ausgangspunkt. Sie finden diese Codes in vielen Bildbearbeitungsprogrammen wie Microsoft Paint, wo Sie eine benutzerdefinierte Farbe aus einer Palette auswählen und automatisch die RGB-Werte angezeigt werden.

5. So stellen Sie Ihre neue Bezeichnung Benutzern zur Verfügung: Wählen Sie über die Menüoption **Klassifizierungen** > **Richtlinien** die Richtlinie aus, die die neue Bezeichnung enthalten soll. Wählen Sie **Bezeichnungen hinzufügen oder entfernen** aus. Wählen Sie die Bezeichnung auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** aus, und klicken Sie anschließend auf **OK** und **Speichern**.
    
    >[!TIP]
    >Bei neuen Bezeichnungen sollten Sie in Erwägung ziehen, diese zuerst zu einer bereichsbezogenen Richtlinie hinzuzufügen, die Sie zu Testzwecken verwenden. Wenn Sie mit den Ergebnissen zufrieden sind, können Sie die Bezeichnung aus diesem Testbereich entfernen und sie anschließend zu einer Richtlinie hinzufügen, die Sie zu Produktionszwecken verwenden.     
    
    Weitere Informationen zum Hinzufügen von Bezeichnungen finden Sie unter [Hinzufügen oder Entfernen einer Bezeichnung](configure-policy-add-remove-label.md).
    
    Ihre vorgenommenen Änderungen sind automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

6. Wenn Sie den neuen Bezeichnungsnamen und eine Beschreibung in verschiedenen Sprachen für Benutzer anzeigen möchten: Gehen Sie wie unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md) beschrieben vor. 

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  


