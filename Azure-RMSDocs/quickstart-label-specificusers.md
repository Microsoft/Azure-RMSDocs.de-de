---
title: 'Schnellstart: neue Azure Information Protection-Bezeichnung für bestimmte Benutzer – AIP'
description: Erstellen und konfigurieren Sie eine neue Bezeichnung, die Dokumente und E-Mails für eine Teilmenge von Benutzern mithilfe einer bereichsbezogenen Richtlinie klassifiziert.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/16/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 33df03d97caf6fea6ca084bedcbb0dac131067d6
ms.sourcegitcommit: 223e26b0ca4589317167064dcee82ad0a6a8d663
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86049002"
---
# <a name="quickstart-create-a-new-azure-information-protection-label-for-specific-users"></a>Schnellstart: Erstellen einer neuen Azure Information Protection-Bezeichnung für bestimmte Benutzer

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

In dieser Schnellstartanleitung erstellen Sie eine neue Azure Information Protection-Bezeichnung, die nur bestimmte Benutzer sehen und anwenden können, um ihre Dokumente und E-Mails zu klassifizieren und zu schützen.

In dieser Konfiguration wird eine bereichsbezogene Richtlinie verwendet.

Für diese Konfiguration benötigen Sie maximal 10 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

2. Sie haben den Azure Information Protection-Bereich zum Azure-Portal hinzugefügt und sich vergewissert, dass der Schutzdienst aktiviert ist.

    Wenn Sie Hilfe bei diesen Aktionen benötigen, lesen Sie [Schnellstart: Erste Schritte im Azure-Portal](quickstart-viewpolicy.md).

3. Eine per E-Mail aktivierte Gruppe in Azure AD mit den Benutzern, die die neue Bezeichnung sehen und anwenden können.
    
    Wenn keine geeignete Gruppe vorhanden ist, erstellen Sie eine mit dem Namen **Vertriebsteam** und fügen mindestens einen Benutzer hinzu.

4. So testen Sie die neue Bezeichnung: Der Azure Information Protection-Client (klassisch) muss auf einem Windows-Computer installiert sein. 
    
    Sie installieren den Client, indem Sie zum [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018) navigieren und auf der Azure Information Protection-Seite **AzInfoProtection.exe** herunterladen.
     
    Wenn Sie einen anderen Bezeichnungsclient als den klassischen Client verwenden, finden Sie entsprechende Anweisungen für dieses Tutorial in der Dokumentation zur Microsoft 365-Compliance. [Weitere Informationen: Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/sensitivity-labels).

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
    
## <a name="create-a-new-label"></a>Erstellen einer neuen Bezeichnung

Erstellen Sie zunächst Ihre neue Bezeichnung.

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich beim [Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal) an. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Klicken Sie im Bereich **Azure Information Protection – Bezeichnungen** auf **Neue Bezeichnung hinzufügen**.

3. Geben Sie im Bereich **Bezeichnung** mindestens Folgendes an:
    
    - **Anzeigename der Bezeichnung**: Ein Name für die neue Bezeichnung, die Benutzern angezeigt wird und die Klassifizierung für den Inhalt identifiziert. Beispiel: `Sales - Restricted`.
    
    - **Beschreibung:** Eine QuickInfo, damit Benutzer ermitteln können, wann diese neue Bezeichnung auszuwählen ist. Beispiel: `Business data that is restricted to the Sales Team.`

4. Stellen Sie sicher, dass **Aktiviert** auf **Ein** (Standardeinstellung) festgelegt ist, und klicken Sie auf **Speichern**.

## <a name="add-the-label-to-a-new-scoped-policy"></a>Hinzufügen der Bezeichnung zu einer neuen bereichsbezogenen Richtlinie

Fügen Sie nun Ihre neu erstellte Bezeichnung zu einer neuen bereichsbezogenen Richtlinie hinzu.

1. Über die Menüoption **Klassifizierungen** > **Richtlinien**: Klicken Sie im Bereich **Azure Information Protection – Richtlinien** auf die Option **Neue Richtlinie hinzufügen**. 

2. Geben Sie im Bereich **Richtlinie** für das Feld **Richtlinienname** einen Namen ein, der die Gruppe von Benutzern bezeichnet, die die neue erstellte Bezeichnung sehen können. Beispiel: `Sales`.

3. Klicken Sie auf die Option **Auswählen, für welche Benutzer oder Gruppen diese Richtlinie gilt**.

4. Klicken Sie im Bereich **AAD-Benutzer und -Gruppen** auf **Benutzer/Gruppen**. Suchen Sie dann im Bereich **Benutzer/Gruppen** die Gruppe, die Sie im Rahmen der Vorbereitung angegeben haben, und wählen Sie sie aus. Beispiel: **Vertriebsteam**. Klicken Sie in diesem Bereich auf **Auswählen** und dann auf **OK**.

5. Klicken Sie dann im Bereich **Richtlinie** auf den Eintrag **Bezeichnungen hinzufügen oder entfernen**.

6. Auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** wählen Sie die Bezeichnung aus, die Sie erstellt haben (z. B. **Vertrieb – Eingeschränkt**), und klicken Sie dann auf **OK**.

7. Klicken Sie dann im Bereich **Richtlinie** auf **Speichern**. 

Ihre neue Bezeichnung wird jetzt nur für die Mitglieder der Gruppe veröffentlicht, die Sie angegeben haben. 

## <a name="test-your-new-label"></a>Testen Ihrer neuen Bezeichnung

Um diese Bezeichnung testen zu können, benötigen Sie mindestens zwei Computer, da der Azure Information Protection-Client nicht mehrere Benutzer auf demselben Computer unterstützt:

 - Melden Sie sich auf dem ersten Computer als Mitglied der Gruppe „Vertriebsteam“ an. Öffnen Sie Word, und vergewissern Sie sich, dass Sie die neue Bezeichnung sehen können. Wenn Word bereits geöffnet ist, starten Sie es neu, um eine Richtlinienaktualisierung zu erzwingen.

- Melden Sie sich auf dem zweiten Computer als Benutzer an, der nicht Mitglied der Gruppe „Vertriebsteam“ ist. Öffnen Sie Word, und vergewissern Sie sich, dass Sie die neue Bezeichnung nicht sehen können. Wenn Word bereits geöffnet ist, starten Sie es wie zuvor neu.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Führen Sie die folgenden Schritte durch, wenn Sie diese Bezeichnung und die bereichsbezogene Richtlinie nicht beibehalten möchten:

1. Über die Menüoption **Klassifizierungen** > **Richtlinien**: Klicken Sie im Bereich **Azure Information Protection – Richtlinien** auf das Kontextmenü ( **...** ) für die bereichsbezogene Richtlinie, die Sie zuvor erstellt haben. Beispiel: **Vertrieb**.

2. Klicken Sie auf **Richtlinie löschen**, und wenn Sie aufgefordert werden, klicken Sie auf **OK**.

3. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Klicken Sie im Bereich **Azure Information Protection – Bezeichnungen** auf das Kontextmenü ( **...** ) für die Bezeichnung, die Sie zuvor erstellt haben.  Beispiel: **Vertrieb – Eingeschränkt**.

4.  Klicken Sie auf **Diese Bezeichnung löschen**, und wenn Sie aufgefordert werden, klicken Sie auf **OK**.


## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wurden die mindestens erforderlichen Optionen beschrieben, damit Sie schnell eine neue Bezeichnung für bestimmte Benutzer erstellen können. Weitere Anweisungen finden Sie in den folgenden Artikeln:

- [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md)

- [Konfigurieren der Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md)

Wenn Sie möchten, dass die Bezeichnung den Inhalt schützt, sodass nur die Mitglieder des Vertriebsteams diese öffnen können, müssen Sie die Bezeichnung für die Anwendung von Schutzmaßnahmen konfigurieren. Weitere Anweisungen finden Sie unter [Gewusst wie: Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).

