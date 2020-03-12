---
title: Neue Azure Information Protection-Bezeichnung – AIP
description: Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/09/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 6da2f54fbd3b3e22d93438b8b369c2d0fe145521
ms.sourcegitcommit: b66b249ab5681d02ec3b5af0b820eda262d5976a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "78972574"
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Erstellen einer neuen Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen.

Sie können eine neue Bezeichnung hinzufügen oder einer vorhandenen Bezeichnung eine neue untergeordnete Bezeichnung hinzufügen, wenn eine weitere Klassifizierungsebene erforderlich ist. Die letzte Bezeichnung in der [Standardrichtlinie](configure-policy-default.md) enthält z.B. untergeordnete Bezeichnungen.

Wenn Sie die erste untergeordnete Bezeichnung für eine Bezeichnung erstellen, können Benutzer nicht länger die ursprüngliche Bezeichnung, also die übergeordnete Bezeichnung, auswählen. Erstellen Sie falls nötig eine neue untergeordnete Bezeichnung, um die Einstellungen der übergeordneten Bezeichnung neu zu erstellen, sodass Benutzer die gleichen Einstellungen anwenden können.

Fügen Sie mithilfe der folgenden Anweisungen eine neue Bezeichnung hinzu, die zur Azure Information Protection-Richtlinie hinzugefügt werden kann.

## <a name="to-create-a-new-label"></a>So erstellen Sie eine neue Bezeichnung

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen** : führen Sie im Bereich **Azure Information Protection-Bezeichnungen** eine der folgenden Aktionen aus:
    
    - So erstellen Sie eine neue Bezeichnung: Klicken Sie auf **Add a new label** (Neue Bezeichnung hinzufügen).
    
    - So erstellen Sie eine neue untergeordnete Bezeichnung: Klicken Sie mit der rechten Maustaste, oder rufen Sie das Kontextmenü ( **...** ) für die Bezeichnung auf, für die Sie eine untergeordnete Bezeichnung erstellen möchten, und klicken Sie dann auf **Add a sub-label** (Untergeordnete Bezeichnung hinzufügen).

3. Wählen Sie im Bereich **Bezeichnung** oder **untergeordnete Bezeichnung** die gewünschten Optionen für diese neue Bezeichnung aus, und klicken Sie dann auf **Speichern**.
    
    Wenn Sie einen Anzeigenamen angeben, dürfen Sie einige Zeichen nicht verwenden (z.B. den umgekehrten Schrägstrich und das kaufmännische Und-Zeichen), da diese Zeichen nicht von allen Diensten und Anwendungen unterstützt werden, die Azure Information Protection nutzen. Verwenden Sie – neben den gesperrten Zeichen – auch das **#** -Zeichen nicht.    
    
    Beachten Sie, dass neuen Bezeichnungen automatisch die Farbe Schwarz zugewiesen wird. Wählen Sie eine eindeutige Farbe aus der Liste der Farben aus, oder geben Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe ein. Beispiel: **#DAA520**. Wenn Sie einen Verweis auf diese Codes benötigen, finden Sie in der MSDN-Webdokumentation auf der Seite [\<Color >](https://developer.mozilla.org/docs/Web/CSS/color_value) eine hilfreiche Tabelle. Außerdem finden Sie diese Codes in vielen Anwendungen, mit denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

4. Um die neue Bezeichnung Benutzern zur Verfügung zu stellen, wählen Sie in der Menüoption **Klassifizierungen** > **Richtlinien** die Richtlinie aus, die die neue Bezeichnung enthalten soll. Wählen Sie **Bezeichnungen hinzufügen oder entfernen** aus. Wählen Sie die Bezeichnung im Bereich **Richtlinie: Bezeichnungen hinzufügen oder entfernen** aus, klicken Sie auf **OK**, und wählen Sie dann **Speichern**aus.
    
    >[!TIP]
    >Bei neuen Bezeichnungen sollten Sie in Erwägung ziehen, diese zuerst zu einer bereichsbezogenen Richtlinie hinzuzufügen, die Sie zu Testzwecken verwenden. Wenn Sie mit den Ergebnissen zufrieden sind, können Sie die Bezeichnung aus diesem Testbereich entfernen und sie anschließend zu einer Richtlinie hinzufügen, die Sie zu Produktionszwecken verwenden.     
    
    Weitere Informationen zum Hinzufügen von Bezeichnungen finden Sie unter [Hinzufügen oder Entfernen einer Bezeichnung](configure-policy-add-remove-label.md).
    
    Ihre vorgenommenen Änderungen sind automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

5. Wenn Sie diesen neuen Bezeichnungsnamen und eine Beschreibung in verschiedenen Sprachen anzeigen möchten, führen Sie die Verfahren unter [Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md) aus. 

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  


