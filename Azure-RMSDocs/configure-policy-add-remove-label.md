---
title: Hinzufügen oder Entfernen einer Bezeichnung zu oder aus einer Azure Information Protection-Richtlinie – AIP
description: Sie können eine Azure Information Protection-Bezeichnung für alle Benutzer zur globalen Richtlinie hinzufügen oder daraus entfernen oder für eine Gruppe von Benutzern zu einer bereichsbezogenen Richtlinie hinzufügen oder daraus entfernen.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: bb4b9ad8cc8b6ec642f8e0553c038488f9d27ab3
ms.sourcegitcommit: d0012de76c9156dd9239f7ba09c044a4b42ffc71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "75675056"
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Hinzufügen oder Entfernen einer Bezeichnung zu oder aus einer Azure Information Protection-Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

> [!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection Client (klassisch)** und die Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021**eingestellt. Dieser Zeitrahmen ermöglicht es allen aktuellen Azure Information Protection Kunden, mithilfe der Microsoft Information Protection Unified-Beschriftungs Plattform zu unserer vereinheitlichten Bezeichnungs Lösung zu wechseln. Weitere Informationen finden Sie in der offiziellen [veralteten Notiz](https://aka.ms/aipclassicsunset).

Nachdem Sie eine Azure Information Protection-Bezeichnung erstellt haben, können Sie diese zu einer Richtlinie hinzufügen und sie auf diese Weise für Benutzer zur Verfügung stellen. Wenn die Bezeichnung für alle Benutzer vorgesehen ist, fügen Sie sie zur globalen Richtlinie hinzu. Wenn die Bezeichnung für eine Gruppe von Benutzern vorgesehen ist, fügen Sie sie zu einer bereichsbezogenen Richtlinie hinzu. Eine Bezeichnung kann nur zu einer Richtlinie hinzugefügt werden. 

Damit eine untergeordnete Bezeichnung hinzugefügt werden kann, muss sich die übergeordnete Bezeichnung in der gleichen Richtlinie oder in der globalen Richtlinie befinden. Wenn Sie eine untergeordnete Bezeichnung hinzufügen, werden die Einstellungen der Hauptbezeichnung nicht geerbt. Bei Benutzern, denen in ihrer Richtlinie die untergeordnete Bezeichnung zugewiesen wird, wird die Hauptbezeichnung als Container zum ausschließlichen Anzeigen des Namens und der Farbe unterstützt. In diesem Szenario werden andere Konfigurationseinstellungen in der Hauptbezeichnung für optische Kennzeichnungen, den Schutz und Bedingungen nicht unterstützt. Obwohl Sie diese Einstellungen weiterhin konfigurieren können, werden sie in der Hauptbezeichnung nur bei Benutzern unterstützt, in deren Richtlinie die Hauptbezeichnung ohne die untergeordnete Bezeichnung vorhanden ist.

Bezeichnungen, die bereits in einer Richtlinie enthalten sind, können aus der Richtlinie entfernt werden. Durch diese Aktion wird die Bezeichnung nicht gelöscht. Sie ist weiterhin verfügbar und kann in einer anderen Richtlinie verwendet werden.

Wenn Sie die Bezeichnung noch nicht erstellt haben, finden Sie unter [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md) weitere Informationen.

Wenn Sie eine bereichsbezogene Richtlinie erstellen müssen, sodass die Bezeichnung für eine Gruppe von Benutzern gilt, finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) weitere Informationen.

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>So fügen Sie eine Bezeichnung zu einer Richtlinie hinzu oder entfernen sie daraus

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.

2. Über die Menüoption **Klassifizierungen** > **Richtlinien** : Wählen Sie im Bereich **Azure Information Protection** - **Richtlinien** die Option **Global** aus, wenn die Bezeichnung, die hinzugefügt oder entfernt werden soll, für alle Benutzer gilt.

    Wenn die hinzuzufügende oder zu entfernende Bezeichnung für eine Gruppe von Benutzern gilt, wählen Sie stattdessen Ihre bereichsbezogene Richtlinie aus.

3. Wählen Sie im Bereich **Richtlinie** die Option **Bezeichnungen hinzufügen oder entfernen**aus.

4. Im Bereich **Richtlinie: Bezeichnungen hinzufügen oder entfernen** werden alle Bezeichnungen mit aktivierten Kontrollkästchen angezeigt, wenn Sie sich bereits in einer Richtlinie befinden, und der entsprechende Richtlinien Name in der Spalte **Richtlinie** .
     
    Untergeordnete Bezeichnungen werden eingezogen dargestellt. In einer bereichsbezogenen Richtlinie werden von der globalen Richtlinie geerbte Bezeichnungen als nicht verfügbar angezeigt.
    
    Führen Sie mindestens eine der folgenden Aktionen aus, und klicken Sie anschließend auf **OK**:
    
    - Wählen Sie eine Bezeichnung aus, um diese hinzuzufügen. Dadurch wird ein aktiviertes Kontrollkästchen hinzugefügt.
    
    - Deaktivieren Sie das Kontrollkästchen einer Bezeichnung, um diese zu entfernen.
  
5. Klicken Sie auf **Save** (Speichern), um Ihre Änderungen zu speichern.
   
    Ihre vorgenommenen Änderungen sind automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).
