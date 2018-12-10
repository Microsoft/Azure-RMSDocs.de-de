---
title: 'Schnellstart: Erstellen einer neuen Azure Information Protection-Bezeichnung für bestimmte Benutzer – AIP'
description: Erstellen und konfigurieren Sie eine neue Bezeichnung, die Dokumente und E-Mails für bestimmte Benutzer mithilfe einer bereichsbezogenen Richtlinie klassifiziert.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 1a8af09681411e49936c067c6161376c9d4f9f16
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023569"
---
# <a name="quickstart-create-a-new-azure-information-protection-label-for-specific-users"></a>Schnellstart: Erstellen einer neuen Azure Information Protection-Bezeichnung für bestimmte Benutzer

In dieser Schnellstartanleitung erstellen Sie eine neue Bezeichnung, die nur für bestimmte Benutzer sehen und anwenden können, um ihre Dokumente und E-Mails zu klassifizieren und zu schützen.

In dieser Konfiguration wird eine bereichsbezogene Richtlinie verwendet.

Für diese Konfiguration benötigen Sie maximal 10 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

2. Sie haben das Azure Information Protection-Blatt zum Azure-Portal hinzugefügt und sich vergewissert, dass der Schutzdienst aktiviert ist.

    Wenn Sie Hilfe bei diesen Aktionen benötigen, lesen Sie [Schnellstart: Erste Schritte im Azure-Portal](quickstart-viewpolicy.md).

3. Eine per E-Mail aktivierte Gruppe in Azure AD mit den Benutzern, die die neue Bezeichnung sehen und anwenden können.
    
    Wenn keine geeignete Gruppe vorhanden ist, erstellen Sie eine mit dem Namen **Vertriebsteam** und fügen mindestens einen Benutzer hinzu.

4. Um die neue Bezeichnung testen zu können, muss der Azure Information Protection-Client auf Computern für Benutzer installiert werden. 
    
    Um die Bezeichnung selbst zu testen, können Sie den Client installieren, indem Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) navigieren und **AzInfoProtection.exe** herunterladen.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
    
## <a name="create-a-new-label"></a>Erstellen einer neuen Bezeichnung

Erstellen Sie zunächst Ihre neue Bezeichnung.

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich beim [Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen**: Klicken Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** auf den Eintrag **Neue Bezeichnung hinzufügen**.

3. Geben Sie auf dem Blatt **Bezeichnung** mindestens Folgendes an:
    
    - **Anzeigename der Bezeichnung**: Ein Name für die neue Bezeichnung, die Benutzern angezeigt wird und die Klassifizierung für den Inhalt identifiziert. Beispiel: `Sales - Restricted`.
    
    - **Beschreibung**: Eine QuickInfo, damit Benutzer ermitteln können, wann diese neue Bezeichnung auszuwählen ist. Beispiel: `Business data that is restricted to the Sales Team.`

4. Stellen Sie sicher, dass **Aktiviert** auf **Ein** (Standardeinstellung) festgelegt ist, und klicken Sie auf **Speichern**.

## <a name="add-the-label-to-a-new-scoped-policy"></a>Hinzufügen der Bezeichnung zu einer neuen bereichsbezogenen Richtlinie

Fügen Sie nun Ihre neu erstellte Bezeichnung zu einer neuen bereichsbezogenen Richtlinie hinzu.

1. Über die Menüoption **Klassifizierungen** > **Richtlinien**: Wählen Sie auf dem Blatt **Azure Information Protection: Richtlinien** den Eintrag **Neue Richtlinie hinzufügen** aus. 

2. Geben Sie auf dem Blatt **Richtlinie** für das Feld **Richtlinienname** einen Namen ein, der die Gruppe von Benutzern bezeichnet, die die neue erstellte Bezeichnung sehen können. Beispiel: `Sales`.

3. Klicken Sie auf die Option **Auswählen, für welche Benutzer oder Gruppen diese Richtlinie gilt**.

4. Klicken Sie auf dem Blatt **AAD-Benutzer und -Gruppen** auf **Benutzer/Gruppen**. Suchen Sie dann auf dem neuen Blatt **Benutzer/Gruppen** die Gruppe, die Sie im Rahmen der Vorbereitung angegeben haben, und wählen Sie sie aus. Beispiel: **Vertriebsteam**. Klicken Sie auf diesem Blatt auf **Auswählen** und dann auf **OK**.

5. Wählen Sie wieder auf dem Blatt **Richtlinie** den Eintrag **Bezeichnungen hinzufügen oder entfernen** aus.

6. Wählen Sie auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** die Bezeichnung aus, die Sie erstellt haben, z.B. **Vertrieb – Eingeschränkt**, und klicken Sie dann auf **OK**.

7. Klicken Sie auf **Speichern**, wenn Sie das Blatt **Richtlinie** wieder aufgerufen haben. 

Ihre neue Bezeichnung wird jetzt nur für die Mitglieder der Gruppe veröffentlicht, die Sie angegeben haben. 

## <a name="test-your-new-label"></a>Testen Ihrer neuen Bezeichnung

Um diese Bezeichnung testen zu können, benötigen Sie mindestens zwei Computer, da der Azure Information Protection-Client nicht mehrere Benutzer auf demselben Computer unterstützt:

 - Melden Sie sich auf dem ersten Computer als Mitglied der Gruppe „Vertriebsteam“ an. Öffnen Sie Word, und vergewissern Sie sich, dass Sie die neue Bezeichnung sehen können. Wenn Word bereits geöffnet ist, starten Sie es neu, um eine Richtlinienaktualisierung zu erzwingen.

- Melden Sie sich auf dem zweiten Computer als Benutzer an, der nicht Mitglied der Gruppe „Vertriebsteam“ ist. Öffnen Sie Word, und vergewissern Sie sich, dass Sie die neue Bezeichnung nicht sehen können. Wenn Word bereits geöffnet ist, starten Sie es wie zuvor neu.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Führen Sie die folgenden Schritte durch, wenn Sie diese Bezeichnung und die bereichsbezogene Richtlinie nicht beibehalten möchten:

1. Über die Menüoption **Klassifizierungen** > **Richtlinien**: Rufen Sie auf dem Blatt **Azure Information Protection: Richtlinien** das Kontextmenü (**...**) für die bereichsbezogene Richtlinie auf, die Sie zuvor erstellt haben. Beispiel: **Vertrieb**.

2. Klicken Sie auf **Richtlinie löschen**, und wenn Sie aufgefordert werden, klicken Sie auf **OK**.

3. Über die Menüoption **Klassifizierungen** > **Bezeichnung**: Rufen Sie auf dem Blatt **Azure Information Protection: Bezeichnung** das Kontextmenü (**...**) für die Bezeichnung auf, die Sie zuvor erstellt haben.  Beispiel: **Vertrieb – Eingeschränkt**.

4.  Klicken Sie auf **Diese Bezeichnung löschen**, und wenn Sie aufgefordert werden, klicken Sie auf **OK**.


## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wurden die mindestens erforderlichen Optionen beschrieben, damit Sie schnell eine neue Bezeichnung für bestimmte Benutzer erstellen können. Weitere Anweisungen finden Sie in den folgenden Artikeln:

- [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md)

- [Konfigurieren der Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md)

Wenn Sie möchten, dass die Bezeichnung den Inhalt schützt, sodass nur die Mitglieder des Vertriebsteams diese öffnen können, müssen Sie die Bezeichnung für die Anwendung von Schutzmaßnahmen konfigurieren. Weitere Anweisungen finden Sie unter [Gewusst wie: Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).

