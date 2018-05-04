---
title: Neue Azure Information Protection-Bezeichnung
description: Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: e36daed0dafe970a273d153512387dda9c1dca40
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2018
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Erstellen einer neuen Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> Dieser Artikel enthält die neuesten Updates für das Azure-Portal, durch die Sie eine Bezeichnung unabhängig von der globalen Richtlinie oder einer bereichsbezogenen Richtlinie erstellen können. Die Option für die Veröffentlichung von Richtlinien wird ebenfalls entfernt. Wenn Ihr Mandant noch nicht für diese Änderungen aktualisiert wurde (wenn Ihnen bei der Azure Information Protection-Richtlinie beispielsweise weiterhin die Option **Veröffentlichen** angezeigt wird und die Menüoption **Klassifizierungen** nicht angezeigt wird), sollten Sie einige Tage warten und anschließend zu diesen Anweisungen zurückkehren.

Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen.

Sie können eine neue Bezeichnung hinzufügen oder einer vorhandenen Bezeichnung eine neue untergeordnete Bezeichnung hinzufügen, wenn eine weitere Klassifizierungsebene erforderlich ist. Die letzte Bezeichnung in der [Standardrichtlinie](configure-policy-default.md) enthält z.B. untergeordnete Bezeichnungen.

Wenn Sie die erste untergeordnete Bezeichnung für eine Bezeichnung erstellen, können Benutzer nicht länger die ursprüngliche Bezeichnung, also die übergeordnete Bezeichnung, auswählen. Erstellen Sie falls nötig eine neue untergeordnete Bezeichnung, um die Einstellungen der übergeordneten Bezeichnung neu zu erstellen, sodass Benutzer die gleichen Einstellungen anwenden können.

Fügen Sie mithilfe der folgenden Anweisungen eine neue Bezeichnung hinzu, die zur Azure Information Protection-Richtlinie hinzugefügt werden kann.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen**: Führen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** eine der folgenden Aktionen aus:
    
    - So erstellen Sie eine neue Bezeichnung: Klicken Sie auf **Add a new label** (Neue Bezeichnung hinzufügen).
    
    - So erstellen Sie eine neue untergeordnete Bezeichnung: Klicken Sie mit der rechten Maustaste, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, für die Sie eine untergeordnete Bezeichnung erstellen möchten, und klicken Sie dann auf **Add a sub-label** (Untergeordnete Bezeichnung hinzufügen).

4. Wählen Sie auf dem Blatt **Label** (Bezeichnung) oder **Sub-label** (Untergeordnete Bezeichnung) die gewünschten Optionen für diese neue Bezeichnung, und klicken Sie dann auf **Save** (Speichern).
    
    Wenn Sie einen Anzeigenamen angeben, dürfen Sie einige Zeichen nicht verwenden (z.B. den umgekehrten Schrägstrich und das kaufmännische Und-Zeichen), da diese Zeichen nicht von allen Diensten und Anwendungen unterstützt werden, die Azure Information Protection nutzen. Verwenden Sie – neben den gesperrten Zeichen – auch das **#**-Zeichen nicht.    
    
    Beachten Sie, dass neuen Bezeichnungen automatisch die Farbe Schwarz zugewiesen wird. Wählen Sie eine eindeutige Farbe aus der Liste der Farben aus, oder geben Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe ein. Beispiel: **#DAA520**. Wenn Sie eine Referenz für diese Codes benötigen, ist [Colors by Name (Farben nach Namen)](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) aus der MSDN-Dokumentation ein hilfreicher Ausgangspunkt. Sie finden diese Codes in vielen Bildbearbeitungsprogrammen wie Microsoft Paint, wo Sie eine benutzerdefinierte Farbe aus einer Palette auswählen und automatisch die RGB-Werte angezeigt werden.

5. So stellen Sie Ihre neue Bezeichnung für Benutzer zur Verfügung: Wählen Sie über die Menüoption **Klassifizierungen** > **Richtlinien** die Richtlinie aus, die die neue Bezeichnung enthalten soll, und klicken Sie auf **Bezeichnungen hinzufügen oder entfernen**. Wählen Sie anschließend auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** die Bezeichnung aus, und klicken Sie auf **OK** und anschließend auf **Speichern**.
    
    >[!TIP]
    >Bei neuen Bezeichnungen sollten Sie in Erwägung ziehen, diese zuerst zu einer bereichsbezogenen Richtlinie hinzuzufügen, die Sie zu Testzwecken verwenden. Wenn Sie mit den Ergebnissen zufrieden sind, können Sie die Bezeichnung aus diesem Testbereich entfernen und sie anschließend zu einer Richtlinie hinzufügen, die Sie zu Produktionszwecken verwenden.     
    
    Weitere Informationen zum Hinzufügen von Bezeichnungen finden Sie unter [Hinzufügen oder Entfernen einer Bezeichnung](configure-policy-add-remove-label.md).
    
    Ihre vorgenommenen Änderungen sind automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

6. Wenn Sie diesen neuen Bezeichnungsnamen und eine Beschreibung in verschiedenen Sprachen anzeigen möchten, führen Sie die Verfahren unter [Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md) aus. 

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

