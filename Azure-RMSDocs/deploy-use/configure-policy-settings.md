---
title: Konfigurieren der Azure Information Protection-Richtlinieneinstellungen
description: "Konfigurieren Sie die Einstellungen in der Azure Information Protection-Richtlinie, die für alle Benutzer und alle Geräte gelten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: f651a621b961bfba63ad43e5372eec9a68c170d4
ms.sourcegitcommit: f1d0b899e6d79ebef3829f24711f947316bca8ef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2017
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Konfigurieren der Richtlinieneinstellungen für Azure Information Protection

>*Gilt für: Azure Information Protection*

Zusätzlich zum Titel und der QuickInfo für die Information Protection-Leiste gibt es einige Einstellungen in der Azure Information Protection-Richtlinie, die Sie unabhängig von den Bezeichnungen konfigurieren können:

![Globale Richtlinieneinstellungen für Azure Information Protection](../media/info-protect-policy-default-settingsv3.png)

Beachten Sie, dass Ihre Richtlinieneinstellungen möglicherweise unterschiedliche Standardwerte aufweisen, je nachdem, wann Sie Ihr Azure Information Protection-Abonnement erworben haben. Einige Einstellungen können auch durch eine [benutzerdefinierte Clienteinstellung](../rms-client/client-admin-guide-customizations.md) festgelegt werden.

So konfigurieren Sie diese Einstellungen:

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierenden Einstellungen für alle Benutzer gelten, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien).
    
    Wenn sich die zu konfigurierenden Einstellungen in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befinden, sodass sie nur für ausgewählte Benutzer verfügbar sind, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

3. Konfigurieren Sie die Einstellungen auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) oder auf dem Blatt **Richtlinie:\<name>**:
    
    - **Select the default label** (Standardbezeichnung auswählen): Wählen Sie bei Festlegung dieser Option die Bezeichnung aus, die Dokumenten und E-Mails zugewiesen werden sollen, die nicht über eine Bezeichnung verfügen. Bezeichnungen mit untergeordneten Bezeichnungen können nicht als Standardbezeichnungen festgelegt werden. 
        
    - **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen): Bei Festlegung dieser Option auf **On** (Ein) muss auf alle gespeicherten Dokumente und gesendeten E-Mails eine Bezeichnung angewendet werden. Die Bezeichnung kann manuell von einem Benutzer, automatisch als Ergebnis einer erfüllten [Bedingung](configure-policy-classification.md) oder standardmäßig (durch Festlegung der Option **Select the default label** [Standardbezeichnung auswählen]) zugewiesen werden.
        
        Wenn beim Speichern eines Dokuments oder beim Senden einer E-Mail keine Bezeichnung zugewiesen ist, wird der Benutzer zur Auswahl einer Bezeichnung aufgefordert. Beispiel:
        
        ![Azure Information Protection-Aufforderung, wenn Beschriftung erzwungen wird](../media/info-protect-enforce-labelv2.png)
        
    - **Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten**: Ist diese Option auf **On** (Ein) festgelegt und der Benutzer führt eine dieser Aktionen aus (z.B. Ändern der Bezeichnung von **Public** (Öffentlich) auf **Personal** (Persönlich)), so wird er aufgefordert, eine Begründung für diese Aktion anzugeben. Der Benutzer kann z. B. angeben, dass das Dokument keine sensiblen Informationen mehr enthält. Die Aktion und die Begründung werden im lokalen Windows-Ereignisprotokoll protokolliert: **Anwendungs- und Dienstprotokolle** > **Azure Information Protection**.  
        
        ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](../media/info-protect-lower-justification.png)
        
        Diese Option gilt nicht für untergeordnete Bezeichnungen.
        
    - **Wenden Sie für E-Mail-Nachrichten mit Anlagen eine Bezeichnung an, die der höchsten Einstufung dieser Anlagen entspricht**: Wenn Sie diese Option auf **Recommended** (Empfohlen) festlegen, werden Benutzer aufgefordert, ihrer E-Mail-Nachricht eine Bezeichnung zuzuweisen. Die Bezeichnung wird dynamisch ausgewählt, basierend auf den Klassifizierungsbezeichnungen, die auf die Anlagen angewendet werden, und es wird die höchste Klassifizierungsbezeichnung ausgewählt. Die Anlage muss eine physische Datei sein, es darf sich nicht um einen Link zu einer Datei handeln (beispielsweise um einen Link zu einer Datei in SharePoint oder OneDrive for Business). Benutzer können die Empfehlung akzeptieren oder ablehnen. Wenn Sie diese Option auf **On** (Ein) festlegen, wird die Bezeichnung automatisch angewendet, aber Benutzer können die Bezeichnung entfernen oder vor dem Senden der E-Mail eine andere Bezeichnung auswählen.  
    
    - **Display the Information Protection bar in Office apps** (Information Protection-Leiste in Office-Apps anzeigen): Wenn diese Einstellung deaktiviert ist, können Benutzer keine Bezeichnungen aus einer Leiste in Word, Excel, PowerPoint und Outlook auswählen. Stattdessen müssen sie Bezeichnungen über die Schaltfläche **Schützen** auf dem Menüband auswählen. Wenn diese Einstellung aktiviert ist, können Benutzer Bezeichnungen entweder über die Leiste oder die Schaltfläche auswählen.
    
    Wenn diese Einstellung aktiviert ist, kann Sie in Verbindung mit einer erweiterten Clienteinstellung verwendet werden, sodass Benutzer [die Azure Information Protection-Leiste dauerhaft ausblenden können](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar), wenn Sie diese nicht anzeigen möchten. Deaktivieren Sie dafür die Option **Leiste anzeigen** über die Schaltfläche **Schützen**.
    
    - **Add the Do Not Forward button to the Outlook ribbon** (Die Schaltfläche „Nicht weiterleiten“ dem Outlook-Menüband hinzufügen): Wenn diese Einstellung aktiviert ist, können Benutzer diese Schaltfläche aus der **Schutzgruppe** auf dem Outlook-Menüband zusätzlich zur Auswahl der Option **Nicht weiterleiten** im Outlook-Menü auswählen. Um sicherzustellen, dass Benutzer ihre E-Mails neben der Klassifizierung zusätzlich schützen, fügen Sie diese Schaltfläche nicht hinzu. [Konfigurieren Sie stattdessen eine Bezeichnung für den Schutz](configure-policy-protection.md) sowie eine benutzerdefinierte Berechtigung für Outlook. Wenn Sie diese Schutzeinstellung verwenden, geschieht das gleiche wie beim Klick auf **Nicht weiterleiten**. Wenn jedoch die Funktion in einer Bezeichnung enthalten ist, werden E-Mails ebenso als geschützt klassifiziert.
    
    Diese Schutzeinstellung kann auch mit einer erweiterten Clienteinstellung als [Clientanpassung](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook) konfiguriert werden.
    
    - **Make the custom permissions option available to users** (Die Option der benutzerdefinierten Berechtigungen für Benutzer verfügbar machen): Wenn diese Einstellung aktiviert ist, können Benutzer ihre eigenen Schutzeinstellungen festlegen und jene außer Kraft setzen, die Sie möglicherweise in einer Bezeichnungskonfiguration eingeschlossen haben. Wenn diese Einstellung deaktiviert ist, sind die Optionen für die benutzerdefinierte Berechtigungen nicht für Benutzer verfügbar.
        
        > [!IMPORTANT]
        > Sofern Sie nicht die aktuelle Vorschauversion des Clients verwenden, verwenden Sie die Einstellung **Off** (Aus) nicht, wenn Sie über Bezeichnungen verfügen, die für benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer konfiguriert sind. Wenn Sie dies tun, wenn die Bezeichnung angewendet ist, werden Benutzer nicht dazu aufgefordert, die benutzerdefinierten Berechtigungen zu konfigurieren. Das führt dazu, dass das Dokument bezeichnet ist, aber nicht über den von Ihnen beabsichtigten Schutz verfügt.
        
        Beachten Sie, dass diese Richtlinieneinstellung keine Auswirkungen auf benutzerdefinierte Berechtigungen hat, die Benutzer über Office-Menüoptionen konfigurieren können. Sie kann jedoch auch mit einer erweiterten Clienteinstellung als [Clientanpassung](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) konfiguriert werden.
        
        Die benutzerdefinierten Berechtigungsoptionen befinden sich hier:
        
        - In Office-Anwendungen: Auf dem Menüband, Registerkarte **Start** > Gruppe **Schutz** > **Schützen** > **Benutzerdefinierte Berechtigungen**
        
        - In Datei-Explorer: Klicken mit der rechten Maustaste > **Klassifizieren und schützen** > **Benutzerdefinierte Berechtigungen**
    
    - **Geben Sie eine benutzerdefinierte URL für die „Weitere Infos“-Webseite des Azure Information Protection-Clients an**: Benutzer sehen diesen Link im Dialogfeld **Microsoft Azure Information Protection** im Abschnitt **Hilfe und Feedback**, wenn sie in ihren Office-Clientanwendungen auf der Registerkarte **Startseite** die Option **Schützen** > **Hilfe und Feedback** auswählen. Standardmäßig gelangen Sie über diesen Link zur [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)-Website. Sie können eine HTTP- oder HTTPS-URL (empfohlen) eingeben, wenn dieser Link auf eine andere Webseite verweisen soll. Es wird nicht überprüft, ob die eingegebene benutzerdefinierte URL erreichbar ist oder auf allen Geräten ordnungsgemäß angezeigt wird.
        
        Sie könnten beispielsweise für Ihr Helpdesk die Seite der Microsoft-Dokumentation eingeben, die Informationen zum Installieren und Verwenden des Clients enthält (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) oder Informationen zur Version (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Alternativ können Sie eine eigene Webseite veröffentlichen, die Benutzern Informationen zur Kontaktaufnahme mit Ihrem Helpdesk bereitstellt oder ein Video enthält, das Benutzern zeigt, wie die konfigurierten Bezeichnungen verwendet werden.

3. Klicken Sie auf **Save** (Speichern), um Ihre Änderungen zu speichern.

4. Klicken Sie auf dem anfänglichen Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
