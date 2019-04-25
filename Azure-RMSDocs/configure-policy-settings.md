---
title: Konfigurieren der Azure Information Protection – AIP-Richtlinieneinstellungen
description: Konfigurieren Sie die Einstellungen in der Azure Information Protection-Richtlinie, die für alle Benutzer und alle Geräte gelten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: 0c77eb5df06ca3a7ba78b4671cc9e52cdb89a34d
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60180102"
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Konfigurieren der Richtlinieneinstellungen für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anleitungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Zusätzlich zum Titel und der QuickInfo für die Information Protection-Leiste gibt es einige Einstellungen in der Azure Information Protection-Richtlinie, die Sie unabhängig von den Bezeichnungen konfigurieren können:

![Globale Richtlinieneinstellungen für Azure Information Protection](./media/info-protect-policy-default-settingsv3.png)

Beachten Sie, dass Ihre Richtlinieneinstellungen möglicherweise unterschiedliche Standardwerte aufweisen, je nachdem, wann Sie Ihr Azure Information Protection-Abonnement erworben haben. Einige Einstellungen können auch durch eine [benutzerdefinierte Clienteinstellung](./rms-client/client-admin-guide-customizations.md) festgelegt werden.

So konfigurieren Sie diese Einstellungen:

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoption **Klassifizierungen** > **Richtlinien**: Wählen Sie auf dem Blatt **Azure Information Protection – Richtlinien** die Option **Global** aus, wenn die Einstellungen, die Sie konfigurieren möchten, für alle Benutzer gelten sollen.
    
    Wenn sich die zu konfigurierenden Einstellungen in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befinden, sodass sie nur für ausgewählte Benutzer verfügbar sind, wählen Sie stattdessen Ihre bereichsbezogene Richtlinie aus.

3. Konfigurieren Sie auf dem Blatt **Richtlinie** folgende Einstellungen:
    
   - **Standardbezeichnung auswählen**: Wählen Sie bei Festlegung dieser Option die Bezeichnung aus, die Dokumenten und E-Mails zugewiesen werden sollen, die nicht über eine Bezeichnung verfügen. Bezeichnungen mit untergeordneten Bezeichnungen können nicht als Standardbezeichnungen festgelegt werden.
        
        Diese Einstellung gilt für Office-Apps und den Scanner. Sie gilt nicht für Datei-Explorer oder PowerShell.
    
    - **Senden Sie Überwachungsdaten an Azure Information Protection-Analysen**: Bevor Sie einen Azure Log Analytics-Arbeitsbereich für [Azure Information Protection-Analysen](reports-aip.md) erstellen, zeigen die Werte für diese Einstellung **Aus** und **Nicht konfiguriert** an. Wenn Sie den Arbeitsbereich erstellen, ändern sich die Werte auf **Aus** und **Ein**.
        
        Wenn die Einstellung **Ein** ist, senden Endpunkte, die die zentrale Berichterstellung unterstützen, ihre Überwachungsdaten an den Azure Information Protection-Dienst. Weitere Informationen darüber, welche Informationen gesendet und gespeichert werden, finden Sie im Abschnitt [Gesammelte und an Microsoft gesendete Informationen](reports-aip.md#information-collected-and-sent-to-microsoft). Setzen Sie diese Option auf **Aus**, um zu verhindern, dass diese Daten gesendet werden.
    
    - **Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen**: Bei Festlegung dieser Option auf **On** (Ein) muss auf alle gespeicherten Dokumente und gesendeten E-Mails eine Bezeichnung angewendet werden. Die Bezeichnung kann manuell von einem Benutzer, automatisch als Ergebnis einer erfüllten [Bedingung](configure-policy-classification.md) oder standardmäßig (durch Festlegung der Option **Select the default label** [Standardbezeichnung auswählen]) zugewiesen werden.
        
       Wenn beim Speichern eines Dokuments oder beim Senden einer E-Mail keine Bezeichnung zugewiesen ist, wird der Benutzer zur Auswahl einer Bezeichnung aufgefordert. Zum Beispiel:
        
       ![Azure Information Protection-Aufforderung, wenn Beschriftung erzwungen wird](./media/info-protect-enforce-labelv2.png)
        
       Diese Option gilt nicht, wenn Sie eine Bezeichnung mit dem PowerShell-Cmdlet [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) mit dem Parameter *RemoveLabel* entfernen.
        
   - **Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten**: Ist diese Option auf **On** (Ein) festgelegt und der Benutzer führt eine dieser Aktionen aus (z.B. Ändern der Bezeichnung von **Public** (Öffentlich) auf **Personal** (Persönlich)), so wird er aufgefordert, eine Begründung für diese Aktion anzugeben. Der Benutzer kann z. B. angeben, dass das Dokument keine sensiblen Informationen mehr enthält. Die Aktion und die Begründung werden im lokalen Windows-Ereignisprotokoll protokolliert: **Anwendungs- und Dienstprotokolle** > **Azure Information Protection**.  
        
       ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](./media/info-protect-lower-justification.png)
        
       Diese Option gilt nicht für die Senkung der Klassifizierung untergeordneter Bezeichnungen unter der gleichen übergeordneten Bezeichnung.
        
   - **Wenden Sie für E-Mails mit Anlagen eine Bezeichnung an, die der höchsten Klassifizierung dieser Anlagen entspricht**: Wenn Sie diese Option auf **Recommended** (Empfohlen) festlegen, werden Benutzer aufgefordert, ihrer E-Mail-Nachricht eine Bezeichnung zuzuweisen. Die Bezeichnung wird dynamisch ausgewählt, basierend auf den Klassifizierungsbezeichnungen, die auf die Anlagen angewendet werden, und es wird die höchste Klassifizierungsbezeichnung ausgewählt. Die Anlage muss eine physische Datei sein, es darf sich nicht um einen Link zu einer Datei handeln (beispielsweise um einen Link zu einer Datei in SharePoint oder OneDrive for Business). Benutzer können die Empfehlung akzeptieren oder ablehnen. Wenn Sie diese Option auf **Automatisch** festlegen, wird die Bezeichnung automatisch angewendet, aber Benutzer können die Bezeichnung entfernen oder vor dem Senden der E-Mail eine andere Bezeichnung auswählen.
        
        Um die Reihenfolge der untergeordneten Bezeichnungen bei der Verwendung dieser Richtlinieneinstellung zu berücksichtigen, müssen Sie [eine erweiterte Clienteinstellung konfigurieren](./rms-client/client-admin-guide-customizations.md#enable-order-support-for-sublabels-on-attachments).
        
        Wenn die Anlage mit die höchste klassifizierungsbezeichnung für den Schutz mit der Einstellung für die Vorschau von benutzerdefinierten Berechtigungen konfiguriert ist:: Wenn der Bezeichnung benutzerdefinierte Berechtigungen umfassen, Outlook (Do Not Forward), wird die Bezeichnung angewendet "und" nicht weiterleiten Schutz wird auf die e-Mail angewendet. Wenn die benutzerdefinierten Berechtigungen der Bezeichnung nur für Word, Excel, PowerPoint und den Dateiexplorer gelten, wird diese Bezeichnung nicht auf die E-Mail angewendet, der Schutz ebenfalls nicht.
    
   - **Information Protection-Leiste in Office-Apps anzeigen**: Wenn diese Einstellung deaktiviert ist, können Benutzer keine Bezeichnungen aus einer Leiste in Word, Excel, PowerPoint und Outlook auswählen. Stattdessen müssen sie Bezeichnungen über die Schaltfläche **Schützen** auf dem Menüband auswählen. Wenn diese Einstellung aktiviert ist, können Benutzer Bezeichnungen entweder über die Leiste oder die Schaltfläche auswählen.
        
       Wenn diese Einstellung aktiviert ist, kann Sie in Verbindung mit einer erweiterten Clienteinstellung verwendet werden, sodass Benutzer [die Azure Information Protection-Leiste dauerhaft ausblenden können](./rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar), wenn Sie diese nicht anzeigen möchten. Dafür müssen sie die Option **Leiste anzeigen** über die Schaltfläche **Schützen** deaktivieren.
    
   - **Dem Outlook-Menüband die Schaltfläche „Nicht weiterleiten“ hinzufügen**: Wenn diese Einstellung aktiviert ist, können Benutzer diese Schaltfläche aus der **Schutzgruppe** auf dem Outlook-Menüband zusätzlich zur Auswahl der Option **Nicht weiterleiten** im Outlook-Menü auswählen. Um sicherzustellen, dass Benutzer ihre E-Mails neben der Klassifizierung zusätzlich schützen, fügen Sie diese Schaltfläche nicht hinzu. [Konfigurieren Sie stattdessen eine Bezeichnung für den Schutz](configure-policy-protection.md) sowie eine benutzerdefinierte Berechtigung für Outlook. Wenn Sie diese Schutzeinstellung verwenden, geschieht das gleiche wie beim Klick auf **Nicht weiterleiten**. Wenn jedoch die Funktion in einer Bezeichnung enthalten ist, werden E-Mails ebenso als geschützt klassifiziert.
    
       Diese Schutzeinstellung kann auch mit einer erweiterten Clienteinstellung als [Clientanpassung](./rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook) konfiguriert werden.
    
   - **Option für benutzerdefinierte Berechtigungen für Benutzer verfügbar machen**: Wenn diese Einstellung aktiviert ist, können Benutzer ihre eigenen Schutzeinstellungen festlegen und jene außer Kraft setzen, die Sie möglicherweise in einer Bezeichnungskonfiguration eingeschlossen haben. Benutzer können außerdem eine Option zum Entfernen des Schutzes sehen. Wenn diese Einstellung deaktiviert ist, sehen Benutzer keine dieser Optionen.
        
       Beachten Sie, dass diese Richtlinieneinstellung keine Auswirkungen auf benutzerdefinierte Berechtigungen hat, die Benutzer über Office-Menüoptionen konfigurieren können. Sie kann jedoch auch mit einer erweiterten Clienteinstellung als [Clientanpassung](./rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) konfiguriert werden.
        
       Die benutzerdefinierten Berechtigungsoptionen befinden sich hier:
        
       - In Office-Anwendungen: Auf dem Menüband, Registerkarte **Start** > Gruppe **Schutz** > **Schützen** > **Benutzerdefinierte Berechtigungen**
        
       - Im Datei-Explorer: Klicken mit der rechten Maustaste > **Klassifizieren und schützen** > **Benutzerdefinierte Berechtigungen**
    
   - **Geben Sie eine benutzerdefinierte URL für die Webseite „Weitere Informationen“ für den Azure Information Protection-Client an**: Benutzer sehen diesen Link im Dialogfeld **Microsoft Azure Information Protection** im Abschnitt **Hilfe und Feedback**, wenn sie in ihren Office-Clientanwendungen auf der Registerkarte **Startseite** die Option **Schützen** > **Hilfe und Feedback** auswählen. Standardmäßig gelangen Sie über diesen Link zur [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)-Website. Sie können eine HTTP- oder HTTPS-URL (empfohlen) eingeben, wenn dieser Link auf eine andere Webseite verweisen soll. Es wird nicht überprüft, ob die eingegebene benutzerdefinierte URL erreichbar ist oder auf allen Geräten ordnungsgemäß angezeigt wird.
        
       Sie können z.B. für Ihren Helpdesk eine Seite aus der Microsoft-Dokumentation angeben, die Informationen zur Installation und Verwendung des Clients (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) oder zu Release-Versionen enthält (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Alternativ können Sie eine eigene Webseite veröffentlichen, die Benutzern Informationen zur Kontaktaufnahme mit Ihrem Helpdesk bereitstellt oder ein Video enthält, das Benutzern zeigt, wie die konfigurierten Bezeichnungen verwendet werden.

4. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern und diese für Benutzer verfügbar zu machen.

Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

## <a name="next-steps"></a>Nächste Schritte

Um anzuzeigen, wie einige dieser Richtlinieneinstellungen zusammen funktionieren, absolvieren Sie das [Tutorial: Konfigurieren von Azure Information Protection-Richtlinieneinstellungen, die nahtlos funktionieren](infoprotect-settings-tutorial.md).

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).

