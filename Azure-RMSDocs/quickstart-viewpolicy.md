---
title: 'Schnellstart: Anzeigen von Azure Information Protection im Azure-Portal – AIP'
description: Wenn Ihre Organisation keine Erfahrungswerte mit Azure Information Protection besitzt, beginnen Sie an dieser Stelle, um den Dienst zum Azure-Portal hinzuzufügen, die Aktivierung des Schutzdiensts zu überprüfen sowie die Bezeichnungen und Richtlinieneinstellungen zu veröffentlichen.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 12/04/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 38f18cebc7d819d0a5afeb3c3a14b1b56ef0aca6
ms.sourcegitcommit: 223e26b0ca4589317167064dcee82ad0a6a8d663
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86049053"
---
# <a name="quickstart-get-started-with-azure-information-protection-in-the-azure-portal"></a>Schnellstart: Erste Schritte mit Azure Information Protection im Azure-Portal

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

In dieser Schnellstartanleitung fügen Sie Azure Information Protection zum Azure-Portal hinzu, bestätigen die Aktivierung des Schutzdiensts, erstellen Standardbezeichnungen (falls noch keine Bezeichnungen vorhanden sind) und zeigen die Richtlinieneinstellungen für den Azure Information Protection-Client (klassisch) an.

Für diese Schnellstartanleitung benötigen Sie maximal 10 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

- Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="add-azure-information-protection-to-the-azure-portal"></a>Hinzufügen von Azure Information Protection zum Azure-Portal

Azure Information Protection wird nicht automatisch im Azure-Portal zur Verfügung gestellt. Sie müssen es hinzufügen.

1. Melden Sie sich mit dem globalen Administratorkonto für Ihren Mandanten im [Azure-Portal](https://portal.azure.com) an. 
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Klicken Sie auf die Option **+ Ressource erstellen**, und geben Sie dann im Suchfeld für den Marketplace **Azure Information Protection** ein. 
    
3. Wählen Sie aus den Ergebnisliste **Azure Information Protection** aus. Klicken Sie dann im Bereich **Azure Information Protection** auf **Erstellen**.
    
    > [!TIP] 
    > Wählen Sie optional **An Dashboard anheften** aus, um eine **Azure Information Protection**-Kachel auf Ihrem Dashboard zu erstellen, damit Sie bei der nächsten Anmeldung beim Portal nicht erneut nach dem Dienst suchen müssen können.
    
    Klicken Sie erneut auf **Erstellen**.

## <a name="confirm-the-protection-service-is-activated"></a>Überprüfen, ob der Schutzdienst aktiviert ist

Der Schutzdienst ist jetzt automatisch für Neukunden aktiviert. Sie sollten sich jedoch vergewissern, dass er nicht manuell aktiviert werden muss. 

1. Klicken Sie im Bereich **Azure Information Protection** auf die Optionen **Verwalten** > **Schutzaktivierung**.

2. Überprüfen Sie, ob der Schutz für Ihren Mandanten aktiviert ist: 
    
    - Wenn der Schutz aktiviert ist, wird Ihnen die folgende Bestätigung angezeigt:
        
        ![Azure Information Protection-Status für Azure RMS (aktiviert)](./media/info-protect-azurerms-activated.png)
        
    - Wenn der Schutz nicht aktiviert ist, werden Ihnen eine entsprechende Statusmeldung und die Option angezeigt, um ihn zu aktivieren:
        
        ![Azure Information Protection-Status für Azure RMS (nicht aktiviert)](./media/info-protect-azurerms-deactivated.png)

3. Wenn der Schutz noch nicht aktiviert ist, klicken Sie auf **Aktivieren**. 

    Wenn die Aktivierung abgeschlossen ist, zeigt die Informationsleiste **Activation finished successfully** (Aktivierung erfolgreich) an.

## <a name="create-and-publish-labels"></a>Erstellen und Veröffentlichen von Bezeichnungen

Ihre Organisation verfügt möglicherweise bereits über Bezeichnungen, die automatisch für Ihren Mandanten erstellt wurden. Oder es wurden Vertraulichkeitsbezeichnungen im Office 365 Security & Compliance Center, Microsoft Security Center oder Microsoft-Compliance Center generiert. Sehen Sie sich dazu das folgende Beispiel an.

1. Wählen Sie **Klassifizierungen** > **Bezeichnungen** aus:
    
    Wenn die Option **Standardbezeichnungen generieren** angezeigt wird, sind noch keine Bezeichnungen verfügbar:
    
     ![Azure Information Protection – keine Standardbezeichnungen](./media/info-protect-nodefaultlabels.png)
    
    Wenn die Option zum Generieren von Standardbezeichnungen nicht angezeigt wird, verfügen Sie möglicherweise bereits über Bezeichnungen. Diese ähneln wahrscheinlich den Standardbezeichnungen für Azure Information Protection in der folgenden Abbildung:
    
    ![Azure Information Protection – Standardbezeichnungen](./media/info-protect-defaultlabels.png)
    
    Wenn die Option zum Generieren von Standardbezeichnungen und auch keine Bezeichnungen angezeigt werden, navigieren Sie zu **Verwalten** > **Einheitliche Bezeichnungen**, und sehen Sie sich den Status von **Einheitliche Bezeichnungen** an. Wenn **Nicht aktiviert** angezeigt wird, wählen Sie **Aktivieren** aus, und kehren Sie dann zum Bereich **Klassifizierungen** > **Bezeichnungen** zurück.

2. Wenn Sie noch nicht über Bezeichnungen verfügen, wählen Sie die Option **Standardbezeichnungen generieren** aus.

4. Um die Bezeichnungen für alle Benutzer zu veröffentlichen, wählen Sie **Klassifizierungen** > **Richtlinien** > **Global** aus:
    
    a. Wählen Sie **Bezeichnungen hinzufügen oder entfernen** aus.
    
    b. Wählen Sie auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** alle Bezeichnungen aus, und klicken Sie dann auf **OK**.
    
    c. Wählen Sie auf dem Blatt **Richtlinie: Global** die Option **Speichern** aus.

Durch Veröffentlichen der Bezeichnungen im Azure-Portal werden diese für den Azure Information Protection-Client (klassisch) zur Verfügung gestellt.

## <a name="view-your-labels"></a>Anzeigen von Bezeichnungen

Wählen Sie **Klassifizierungen** > **Bezeichnungen** aus, und nehmen Sie sich einige Minuten Zeit, um sich mit den Bezeichnungen im Bereich **Azure Information Protection – Bezeichnungen** vertraut zu machen.

Wenn die Bezeichnungen nicht den Bezeichnungen in der Abbildung des vorigen Abschnitts ähneln, verwenden Sie keine Azure Information Protection-Standardbezeichnungen, sondern Bezeichnungen, die möglicherweise aus dem Office 365 Security & Compliance Center, dem Microsoft 365 Security Center oder dem Microsoft 365 Compliance Center stammen.

> [!TIP]
> So gehen Sie vor, um anstelle von benutzerdefinierten Bezeichnungen Azure Information Protection-Standardbezeichnungen zu verwenden: 
> - Löschen Sie die benutzerdefinierten Bezeichnungen, damit im Bereich **Bezeichnungen** die Option zum Generieren von Standardbezeichnungen angezeigt wird, wie im [vorangehenden Abschnitt](#create-and-publish-labels) beschrieben. 

Bereich **Azure Information Protection – Bezeichnungen**:

- Die Standardbezeichnungen für die Klassifizierung sind **Persönlich**, **Öffentlich**, **Allgemein**, **Vertraulich** und **Streng vertraulich**. Die beiden letzten Bezeichnungen können erweitert werden, um untergeordnete Bezeichnungen anzuzeigen, die Beispiele für eine Klassifizierung mit Unterkategorien bereitstellen.

- Anhand der Spalten **KENNZEICHNUNG** und **SCHUTZ** erkennen Sie, dass für einige Bezeichnungen optische Kennzeichnungen konfiguriert wurden. Die optischen Kennzeichnungen sind eine Fußzeile, ein Header und ein Wasserzeichen. Für einige Bezeichnungen kann zusätzlich auch eine Schutzfunktion festgelegt werden. 

Beispiel: 

![Azure Information Protection-Schnellstart – Übersicht über Standardbezeichnungen](./media/info-protect-policy-default-labelsv2.png)

Wenn Sie eine Bezeichnung auswählen, werden in einem neuen Bereich Details zur Bezeichnungskonfiguration angezeigt.

## <a name="view-your-policy-settings"></a>Anzeigen von Richtlinieneinstellungen

Wenn Sie das erste Mal über das Azure-Portal eine Verbindung mit dem Azure Information Protection-Dienst herstellen, werden automatisch Standardrichtlinieneinstellungen für Sie erstellt, die vom Azure Information Protection-Client (klassisch) verwendet werden. Beim klassischen Client werden Richtlinieneinstellungen und die Bezeichnungen, die wir hier gezeigt haben, auf den Client heruntergeladen, der in der Azure Information Protection-Richtlinie angegeben ist.

Wenn Sie den Azure Information Protection-Client für einheitliche Bezeichnungen verwenden, macht dieser Client keinen Gebrauch von diesen Richtlinieneinstellungen. Stattdessen lädt dieser Client die gleichen Bezeichnungen, aber andere Richtlinieneinstellungen aus dem Office 365 Compliance & Security Center, dem Microsoft 365 Compliance Center oder dem Microsoft 365 Security Center herunter. Verwenden Sie diese Admin Centers statt des Azure-Portals, um Ihre Bezeichnungen und Bezeichnungsrichtlinien zu bearbeiten.

So zeigen Sie die Standardrichtlinieneinstellungen für Azure Information Protection für den klassischen Client an:

1. Klicken Sie auf **Klassifizierungen** > **Richtlinien** > **Global**, um die standardmäßigen Azure Information Protection-Richtlinieneinstellungen anzuzeigen, die für Ihren Mandanten erstellt wurde.
    
2. Nach den Bezeichnungen im Abschnitt **Einstellungen konfigurieren, die für Information Protection-Endbenutzer angezeigt und angewendet werden** werden die Richtlinieneinstellungen angezeigt. Zum Beispiel ist keine Standardbezeichnung festgelegt, Dokumente und E-Mails müssen keine Bezeichnungen aufweisen, und Benutzer müssen keine Begründung angeben, wenn sie Bezeichnungen ändern:
    
    ![Globale Richtlinieneinstellungen für Azure Information Protection](./media/defaultsettings-aip.png)

3. Sie können jetzt alle geöffneten Bereiche im Portal schließen.

## <a name="next-steps"></a>Nächste Schritte

Bei Verwendung des klassischen Clients:

- Für den nächsten Schritt ist das folgende Tutorial möglicherweise hilfreich: [Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md)
- Anstelle der ausführlichen Anweisungen zum Konfigurieren sämtlicher Aspekte der Azure Information Protection-Richtlinie können Sie [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md) lesen.

Bei Verwendung des Clients für einheitliche Bezeichnungen:

- Weitere Informationen finden Sie in der Dokumentation für die Microsoft 365-Compliance unter [Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/sensitivity-labels)

Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, sehen Sie sich diese [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients) an.
