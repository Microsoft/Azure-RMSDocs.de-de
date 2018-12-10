---
title: 'Schnellstart: Erste Schritte mit Azure Information Protection im Azure-Portal – AIP'
description: Wenn Ihre Organisation keine Erfahrungswerte mit Azure Information Protection besitzt, beginnen Sie an dieser Stelle, um den Dienst zum Azure-Portal hinzuzufügen, die Aktivierung des Schutzdiensts zu überprüfen und die Richtlinie anzuzeigen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: f5cf70b0827e36ffae6644634ef198385ef6d11a
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023514"
---
# <a name="quickstart-get-started-with-azure-information-protection-in-the-azure-portal"></a>Schnellstart: Erste Schritte mit Azure Information Protection im Azure-Portal

In dieser Schnellstartanleitung fügen Sie Azure Information Protection zum Azure-Portal hinzu, überprüfen, ob der Schutzdienst aktiviert ist, und zeigen die Standardrichtlinie Ihrer Organisation an. 

Für diese Schnellstartanleitung benötigen Sie 5 Minuten.

## <a name="prerequisites"></a>Voraussetzungen

Voraussetzungen für diesen Schnellstart:

- Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

## <a name="add-azure-information-protection-to-the-azure-portal"></a>Hinzufügen von Azure Information Protection zum Azure-Portal

Azure Information Protection wird nicht automatisch im Azure-Portal zur Verfügung gestellt. Sie müssen es hinzufügen.

1. Melden Sie sich mit dem globalen Administratorkonto für Ihren Mandanten im [Azure-Portal](https://portal.azure.com) an. 
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Wählen Sie im Hubmenü die Option **Ressource erstellen** aus, und geben Sie dann im Suchfeld für den Marketplace **Azure Information Protection** ein. 
    
3. Wählen Sie aus den Ergebnisliste **Azure Information Protection** aus. Klicken Sie dann auf dem Blatt **Azure Information Protection** auf **Erstellen**.
    
    > [!TIP] 
    > Wählen Sie optional **An Dashboard anheften** aus, um eine **Azure Information Protection**-Kachel auf Ihrem Dashboard zu erstellen, damit Sie bei der nächsten Anmeldung beim Portal nicht erneut nach dem Dienst suchen müssen können.
    
    Klicken Sie erneut auf **Erstellen**.

## <a name="confirm-the-protection-service-is-activated"></a>Überprüfen, ob der Schutzdienst aktiviert ist

Der Schutzdienst ist jetzt automatisch für neue Mandanten aktiviert, es empfiehlt sich jedoch, sich zu vergewissern, dass er nicht manuell aktiviert werden muss. 

1. Wählen Sie auf dem Blatt **Azure Information Protection** die Optionen **Verwalten** > **Schutzaktivierung** aus.

2. Überprüfen Sie, ob der Schutz für Ihren Mandanten aktiviert ist: 
    
    - Wenn der Schutz aktiviert ist, wird Ihnen die folgende Bestätigung angezeigt:
        
        ![Azure Information Protection-Status für Azure RMS](./media/info-protect-azurerms-activated.png)
        
    - Wenn der Schutz nicht aktiviert ist, werden Ihnen eine entsprechende Statusmeldung und die Option angezeigt, um ihn zu aktivieren:
        
        ![Azure Information Protection-Status für Azure RMS](./media/info-protect-azurerms-deactivated.png)

3. Wenn der Schutz noch nicht aktiviert ist, klicken Sie auf **Aktivieren**. 

    Wenn die Aktivierung abgeschlossen ist, zeigt die Informationsleiste **Activation finished successfully** (Aktivierung erfolgreich) an.

## <a name="view-your-organizations-default-policy---labels-and-policy-settings"></a>Anzeigen der Standardrichtlinie Ihrer Organisation: Bezeichnungen und Richtlinieneinstellungen

Wenn Sie erstmals über das Azure-Portal eine Verbindung mit dem Azure Information Protection-Dienst herstellen, wird eine Standardrichtlinie für Ihren Mandanten erstellt. Die Standardrichtlinie enthält Bezeichnungen und Einstellungen, die Sie im vorliegenden Zustand verwenden oder anpassen können.

1. Klicken Sie auf **Klassifizierungen** > **Richtlinien** > **Global**, um die Azure Information Protection-Standardrichtlinie anzuzeigen, die für Ihren Mandanten erstellt wurde.
    
2. Nehmen Sie sich ein paar Minuten Zeit, um sich mit den angezeigten Bezeichnungen vertraut zu machen:
    
    - Bezeichnungen für die Klassifizierung: **Personal** (Persönlich), **Public** (Öffentlich), **General** (Allgemein), **Confidential** (Vertraulich) und **Highly Confidential** (Streng vertraulich). Die beiden letzten Bezeichnungen können erweitert werden, um untergeordnete Bezeichnungen anzuzeigen, die Beispiele für eine Klassifizierung mit Unterkategorien bereitstellen:
    
    - In der Standardkonfiguration verfügen einige Bezeichnungen nicht über optische Kennzeichnungen. Die optischen Kennzeichnungen sind eine Fußzeile, ein Header und ein Wasserzeichen. Je nach Ihrer Standardrichtlinie ist für einige Bezeichnungen auch ein Schutz festgelegt. Beispiel: 
    
    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie](./media/info-protect-policy-default-labelsv2.png)
    
3. Nach den Bezeichnungen werden im Abschnitt **Konfigurieren von Einstellungen, die für Information Protection-Endbenutzer angezeigt und angewendet werden** außerdem einige Richtlinieneinstellungen angezeigt. Zum Beispiel ist keine Standardbezeichnung festgelegt, Dokumente und E-Mails müssen keine Bezeichnungen aufweisen, und Benutzer müssen keine Begründung angeben, wenn sie Bezeichnungen ändern:
    
    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie](./media/info-protect-policy-default-settings.png) 

4. Da Sie nur die Bezeichnungen und Einstellungen anzeigen, können Sie alle Blätter schließen, die Sie geöffnet haben.

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun die Bezeichnungen und Richtlinieneinstellungen im Azure-Portal gesehen haben, können Sie als nächsten Schritt das folgende Tutorial durchführen: [Tutorial: Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md).

Anstelle der ausführlichen Anweisungen zum Konfigurieren sämtlicher Aspekte der Azure Information Protection-Richtlinie können Sie [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md) lesen.
