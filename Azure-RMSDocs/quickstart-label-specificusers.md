---
title: 'Schnellstart: neue Azure Information Protection-Bezeichnung für bestimmte Benutzer – AIP'
description: Erstellen und konfigurieren Sie eine neue Bezeichnung, die Dokumente und E-Mails für eine Teilmenge von Benutzern mithilfe einer bereichsbezogenen Richtlinie klassifiziert.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/19/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: d452f2c6c1d58af8f352664e087514f798bc1b5b
ms.sourcegitcommit: df6ee1aca02e089e3a72006ecf0747f14213979c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94503569"
---
# <a name="quickstart-create-a-new-azure-information-protection-label-for-specific-users"></a>Schnellstart: Erstellen einer neuen Azure Information Protection-Bezeichnung für bestimmte Benutzer

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Klassischer Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE]
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

In dieser Schnellstartanleitung erstellen Sie eine neue Azure Information Protection-Bezeichnung, die nur bestimmte Benutzer sehen und anwenden können, um ihre Dokumente und E-Mails zu klassifizieren und zu schützen.

In dieser Konfiguration wird eine bereichsbezogene Richtlinie verwendet.

**Benötigte Zeit:** Für diese Konfiguration benötigen Sie maximal 10 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

|Anforderung  |Beschreibung  |
|---------|---------|
|**Ein unterstützendes Abonnement**     |  Sie benötigen ein Abonnement, das [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) umfasst. </br></br>Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.       |
|**AIP zum Azure-Portal hinzugefügt**    |  Sie haben den Azure Information Protection-Bereich zum Azure-Portal hinzugefügt und sich vergewissert, dass der Schutzdienst aktiviert ist. </br></br>Weitere Informationen finden Sie unter [Schnellstart: Erste Schritte im Azure-Portal](quickstart-viewpolicy.md).       |
|**Eine für E-Mails aktivierte Gruppe in Azure AD**     | Sie benötigen eine für E-Mails aktivierte Gruppe in Azure AD mit den Benutzern, die die neue Bezeichnung sehen und anwenden können. </br></br>Wenn keine geeignete Gruppe vorhanden ist, erstellen Sie eine mit dem Namen **Vertriebsteam** und fügen mindestens einen Benutzer hinzu. |
|**Klassischer Client installiert**    |   Damit Sie die neue Bezeichnung testen können, muss der klassische Client auf Ihrem Computer installiert sein. </br></br>Der klassische Azure Information Protection-Client gilt ab März 2021 als veraltet. Zum Bereitstellen des klassischen AIP-Clients eröffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.  |
| | |

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="create-a-new-label"></a>Erstellen einer neuen Bezeichnung

Erstellen Sie zunächst Ihre neue Bezeichnung.

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.

    Beginnen Sie beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumentation mit der Eingabe von **Information**, und wählen Sie **Azure Information Protection** aus.

    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

1. Wählen Sie unter **Klassifizierungen** die Option **Bezeichnungen** aus, und klicken Sie dann auf **+ Neue Bezeichnung hinzufügen**.

1. Füllen Sie im Bereich **Bezeichnung** mindestens die folgenden Felder aus:

    |Feld  |Beschreibung  |
    |---------|---------|
    |**Anzeigename der Bezeichnung**     |    Ein Name für die neue Bezeichnung, die Benutzern angezeigt wird und die Klassifizierung für den Inhalt identifiziert. </br>Beispiel: **Vertrieb – eingeschränkt**    |
    |**Beschreibung**     |   Eine QuickInfo, damit Benutzer ermitteln können, wann diese neue Bezeichnung auszuwählen ist. </br> Beispiel: **Geschäftsdaten, auf die nur das Vertriebsteam zugreifen darf.**     |
    | | | 

1. Stellen Sie sicher, dass **Aktiviert** auf **Ein** (Standardeinstellung) festgelegt ist, und klicken Sie auf **Speichern** ![Speichern](media/qs-tutor/save-icon.png "Speichern").

    Klicken Sie auf das **X** in der oberen rechten Ecke, um den Bereich **Neue Bezeichnung** zu schließen.

## <a name="add-the-label-to-a-new-scoped-policy"></a>Hinzufügen der Bezeichnung zu einer neuen bereichsbezogenen Richtlinie

Fügen Sie nun Ihre neu erstellte Bezeichnung zu einer neuen bereichsbezogenen Richtlinie hinzu.

1. Wählen Sie auf der linken Seite unter **Klassifizierungen** die Option **Richtlinien** aus, und klicken Sie dann auf **Neue Richtlinie hinzufügen**.

1. Geben Sie im Feld **Richtlinienname** einen aussagekräftigen Wert zur Beschreibung der Benutzer ein, denen Ihre neue Bezeichnung angezeigt wird.

    Beispiel: **Vertrieb**.

1. Wählen Sie die Zeile **Wählen Sie aus, welche Benutzer oder Gruppen diese Richtlinie erhalten** aus, um den Bereich **AAD-Benutzer und -Gruppen** zu öffnen.

1. Suchen Sie im Bereich **AAD-Benutzer und -Gruppen** die Gruppe, die Sie im Rahmen der Vorbereitung ermittelt haben, und wählen Sie diese aus. Beispiel: **Vertriebsteam**.

    Klicken Sie auf **Auswählen**, um den Bereich zu schließen.

1. Klicken Sie im Bereich **Richtlinie** unter **Anzeigename für Bezeichnung** auf **Bezeichnungen hinzufügen oder entfernen**.

1. Auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** wählen Sie die Bezeichnung aus, die Sie erstellt haben (z. B. **Vertrieb – Eingeschränkt**), und klicken Sie dann auf **OK**.

1. Klicken Sie dann im Bereich **Richtlinie** auf **Speichern** ![Speichern](media/qs-tutor/save-icon.png "Speichern").

Ihre neue Bezeichnung wird jetzt nur für die Mitglieder der Gruppe veröffentlicht, die Sie angegeben haben.

## <a name="test-your-new-label"></a>Testen Ihrer neuen Bezeichnung

Um diese Bezeichnung testen zu können, benötigen Sie mindestens zwei Computer, da der Azure Information Protection-Client nicht mehrere Benutzer auf demselben Computer unterstützt:

- Melden Sie sich **auf dem ersten Computer** als Mitglied der Gruppe „Vertriebsteam“ an. Öffnen Sie Word, und vergewissern Sie sich, dass Sie die neue Bezeichnung sehen können. Wenn Word bereits geöffnet ist, starten Sie es neu, um eine Richtlinienaktualisierung zu erzwingen.

- Melden Sie sich **auf dem zweiten Computer** als Benutzer an, der *nicht* Mitglied der Gruppe „Vertriebsteam“ ist. Öffnen Sie Word, und vergewissern Sie sich, dass Sie die neue Bezeichnung nicht sehen können. Wenn Word bereits geöffnet ist, starten Sie es wie zuvor neu.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Führen Sie die folgenden Schritte durch, wenn Sie diese Bezeichnung und die bereichsbezogene Richtlinie nicht beibehalten möchten:

1. Über den Bereich **Klassifizierungen** > **Richtlinien**: Wählen Sie im Bereich **Azure Information Protection – Richtlinien** das Kontextmenü ( **...** ) für die bereichsbezogene Richtlinie aus, die Sie erstellt haben. Beispiel: **Vertrieb**.

1. Klicken Sie auf **Richtlinie löschen**, und wenn Sie aufgefordert werden, klicken Sie auf **OK**.

1. Über den Bereich **Klassifizierungen** > **Bezeichnung**: Wählen Sie im Bereich **Azure Information Protection – Bezeichnung** das Kontextmenü ( **...** ) für die Bezeichnung aus, die Sie erstellt haben.  Beispiel: **Vertrieb – Eingeschränkt**.

1. Klicken Sie auf **Diese Bezeichnung löschen**, und wenn Sie aufgefordert werden, klicken Sie auf **OK**.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung wurden die mindestens erforderlichen Optionen beschrieben, damit Sie mit dem klassischen Client schnell eine neue Bezeichnung für bestimmte Benutzer erstellen können. Weitere Anweisungen finden Sie in den folgenden Artikeln:

- [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md)

- [Konfigurieren der Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md)

Wenn Sie möchten, dass die Bezeichnung den Inhalt schützt, sodass nur die Mitglieder des Vertriebsteams diese öffnen können, müssen Sie die Bezeichnung für die Anwendung von Schutzmaßnahmen konfigurieren. Weitere Anweisungen finden Sie unter [Gewusst wie: Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
