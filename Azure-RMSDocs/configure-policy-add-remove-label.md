---
title: Hinzufügen oder Entfernen einer Bezeichnung zu oder aus einer Azure Information Protection-Richtlinie
description: Sie können eine Azure Information Protection-Bezeichnung für alle Benutzer zur globalen Richtlinie hinzufügen oder daraus entfernen oder für eine Gruppe von Benutzern zu einer bereichsbezogenen Richtlinie hinzufügen oder daraus entfernen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: 8ec20dd43e2be245eba01d0f3f93aee062c9e0f6
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42806181"
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Hinzufügen oder Entfernen einer Bezeichnung zu oder aus einer Azure Information Protection-Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Nachdem Sie eine Azure Information Protection-Bezeichnung erstellt haben, können Sie diese zu einer Richtlinie hinzufügen und sie auf diese Weise für Benutzer zur Verfügung stellen. Wenn die Bezeichnung für alle Benutzer vorgesehen ist, fügen Sie sie zur globalen Richtlinie hinzu. Wenn die Bezeichnung für eine Gruppe von Benutzern vorgesehen ist, fügen Sie sie zu einer bereichsbezogenen Richtlinie hinzu. Derzeit kann eine Bezeichnung nur zu einer Richtlinie hinzugefügt werden. Damit eine untergeordnete Bezeichnung hinzugefügt werden kann, muss sich die übergeordnete Bezeichnung in der gleichen Richtlinie oder in der globalen Richtlinie befinden.

Bezeichnungen, die bereits in einer Richtlinie enthalten sind, können aus der Richtlinie entfernt werden. Durch diese Aktion wird die Bezeichnung nicht gelöscht. Sie ist weiterhin verfügbar und kann in einer anderen Richtlinie verwendet werden.

Wenn Sie die Bezeichnung noch nicht erstellt haben, finden Sie unter [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md) weitere Informationen.

Wenn Sie eine bereichsbezogene Richtlinie erstellen müssen, sodass die Bezeichnung für eine Gruppe von Benutzern gilt, finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) weitere Informationen.

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>So fügen Sie eine Bezeichnung zu einer Richtlinie hinzu oder entfernen sie daraus

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoption **Klassifizierungen** > **Richtlinien**: Wählen Sie auf dem Blatt **Azure Information Protection** - **Richtlinien** den Eintrag **Global** aus, wenn die hinzuzufügende oder zu entfernende Bezeichnung für alle Benutzer gilt.

    Wenn die hinzuzufügende oder zu entfernende Bezeichnung für eine Gruppe von Benutzern gilt, wählen Sie stattdessen Ihre bereichsbezogene Richtlinie aus.

3. Wählen Sie auf dem Blatt **Richtlinie** den Eintrag **Bezeichnungen hinzufügen oder entfernen** aus.

4. Auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** können Sie sämtliche Ihrer Bezeichnungen sehen. Die zugehörigen Kontrollkästchen sind aktiviert, wenn die Bezeichnungen bereits in einer Richtlinie enthalten sind. In der Spalte **Richtlinie** wird der entsprechende Richtlinienname angezeigt.
     
    Untergeordnete Bezeichnungen werden eingezogen dargestellt. In einer bereichsbezogenen Richtlinie werden von der globalen Richtlinie geerbte Bezeichnungen als nicht verfügbar angezeigt.
    
    Führen Sie mindestens eine der folgenden Aktionen aus, und klicken Sie anschließend auf **OK**:
    
    - Wählen Sie eine Bezeichnung aus, um diese hinzuzufügen. Dadurch wird ein aktiviertes Kontrollkästchen hinzugefügt.
    
    - Deaktivieren Sie das Kontrollkästchen einer Bezeichnung, um diese zu entfernen.
  
5. Klicken Sie auf **Save** (Speichern), um Ihre Änderungen zu speichern.
   
    Ihre vorgenommenen Änderungen sind automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

