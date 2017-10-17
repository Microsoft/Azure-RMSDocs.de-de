---
title: "Konfigurieren und Verwalten von Vorlagen für Azure Information Protection"
description: Konfigurieren und Verwalten von Rights Management-Vorlagen im Azure-Portal.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 5afd71e059ef22eed61347e6916b9cbb6c2dc7f0
ms.sourcegitcommit: 326930de25b259c18469f4100ec5774a04bedc7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2017
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Konfigurieren und Verwalten von Vorlagen für Azure Information Protection

>*Gilt für: Azure Information Protection*

>[!NOTE]
>Diese Funktion ersetzt das Konfigurieren benutzerdefinierter Vorlagen im klassischen Azure-Portal. Eine schnelle Anleitung finden Sie unter [Tasks that you used to do with the Azure classic portal (Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben)](migrate-portal.md).
>
>Obwohl Sie noch immer Vorlagen im klassischen Azure-Portal erstellen und verwalten können, empfiehlt es sich jedoch nicht, dass Sie die gleichen Vorlagen vom klassischen Azure-Portal und dem Azure-Portal verwalten. Die Implementierung zum Konfigurieren von Vorlagen in diesen anderen Portalen wurde geändert, es kann also durch das Konfigurieren der gleichen Vorlage in unterschiedlichen Portalen zu einer unzuverlässigen Konfiguration kommen.


Rights Management-Vorlagen sind nun in der Azure Information Protection-Richtlinie integriert. 

**Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst (Azure Information Protection P1 oder P2):**

- Rights Management-Vorlagen, die nicht in Ihren Bezeichnungen für Ihren Mandanten enthalten sind, werden im Abschnitt **Vorlagen** nach den Bezeichnungen auf dem Blatt **Azure Information Protection – Globale Richtlinie** angezeigt. Sie können diese Vorlagen in Bezeichnungen konvertieren, oder Sie können eine Verknüpfung zu diesen herstellen, wenn Sie den Schutz ihrer Bezeichnungen konfigurieren. 

**Bei einem Abonnement, das nur Schutz umfasst (ein Office 365-Abonnement mit dem Azure Rights Management-Dienst):**

- Rights Management-Vorlagen für Ihren Mandanten werden auf dem Blatt **Azure Information Protection – Globale Richtlinie** im Abschnitt **Vorlagen** angezeigt. Es werden keine Bezeichnungen angezeigt. Darüber hinaus sehen Sie Konfigurationseinstellungen, die für die Klassifizierung und die Bezeichnung spezifisch sind, aber diese haben entweder keinen Einfluss auf Ihre Vorlagen oder können nicht konfiguriert werden. 

## <a name="default-templates"></a>Standardvorlagen

Wenn Sie Ihr Abonnement für Azure Information Protection oder für ein Office 365-Abonnement, das den Azure Rights Management-Dienst enthält, anfordern, werden automatisch zwei Standardvorlagen für Ihren Mandanten erstellt, die den Zugriff für autorisierte Benutzer in Ihrer Organisation beschränken. Wenn diese zwei Vorlagen erstellt werden, verfügen sie über die Berechtigungen, die in der Dokumentation [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md#rights-included-in-the-default-templates) aufgelistet sind.

Zusätzlich werden die Vorlagen so konfiguriert, dass sie einen Offlinezugriff für sieben Tage zulassen und kein Ablaufdatum haben.

>[!NOTE]
> Sie können diese Einstellungen und die Namen und Beschreibungen der Standardvorlagen ändern. Dies war mit dem klassischen Azure-Portal nicht möglich und wird auch weiterhin nicht für PowerShell unterstützt.

Diese Standardvorlagen erleichtern es Ihnen und anderen Personen, sofort mit dem Schutz sensibler Daten Ihrer Organisation zu beginnen. Diese Vorlagen können mit Azure Information Protection-Bezeichnungen oder alleine mit [Anwendungen und Diensten](../understand-explore/applications-support.md) verwendet werden, die Rights Management-Vorlagen verwenden.

Sie können auch eigene, benutzerdefinierte Vorlagen erstellen. Sie benötigen wahrscheinlich nur einige Vorlagen, aber in Azure ist es möglich, maximal 500 gespeicherte benutzerdefinierte Vorlagen zu verwenden.

### <a name="default-template-names"></a>Namen für die Standardvorlage

Wenn Sie vor kurzem ein Abonnement für Azure Information Protection erworben haben, werden Ihre Standardvorlagen mit folgenden Namen erstellt:

- **Vertraulich\Alle Mitarbeiter** erteilt Lese- und Änderungsberechtigungen für den geschützten Inhalt.

- **Streng vertraulich\Alle Mitarbeiter** erteilt Leseberechtigungen für den geschützten Inhalt.

Wenn Sie Ihr Abonnement für Azure Information Protection vor einer Weile erhalten haben, oder wenn Sie nicht über ein Azure Information Protection-Abonnement verfügen, aber ein Office 365-Abonnement mit Azure Rights Management besitzen, werden Ihre Standardvorlagen mit folgenden Namen erstellt:

- **\<Name der Organisation> – Vertraulich** erteilt Lese- und Änderungsberechtigungen für den geschützten Inhalt.

- **\<Name der Organisation> – Nur vertrauliche Ansicht** erteilt Leseberechtigungen für den geschützten Inhalt. 

Sie können diese Standardvorlagen umbenennen (und neu konfigurieren), wenn Sie das Azure-Portal verwenden.

>[!NOTE]
>Wenn Sie Ihre Standardvorlagen auf dem Blatt **Azure Information Protection – Globale Richtlinie** nicht sehen, werden sie zu Bezeichnungen konvertiert oder mit einer Bezeichnung verknüpft. Diese sind noch immer als Vorlage vorhanden, sie werden im Azure-Portal jedoch als Teil einer Konfiguration der Bezeichnung angezeigt, die Azure RMS-Schutz enthält. Sie können stets überprüfen, über welche Vorlagen Ihr Mandant verfügt, indem Sie [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) aus dem [AADRM-PowerShell-Modul](administer-powershell.md) ausführen.
>
>Sie können Vorlagen manuell konvertieren und diese bei Bedarf umbenennen, so wie unter [Konvertieren von Vorlagen in Bezeichnungen](#to-convert-templates-to-labels) beschrieben. Wenn Ihre Azure Information Protection-Standardrichtlinie kürzlich erstellt und der Azure Rights Management-Dienst für Ihren Mandanten zu diesem Zeitpunkt aktiviert wurde, werden sie automatisch konvertiert.

Vorlagen, die archiviert werden, werden auf dem Blatt **Azure Information Protection – Globale Richtlinie** als nicht verfügbar angezeigt. Diese Vorlagen können nicht für Bezeichnungen ausgewählt werden, aber sie können zu Bezeichnungen konvertiert werden.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Überlegungen zu Vorlagen im Azure-Portal

Bevor Sie diese Vorlagen bearbeiten oder zu Bezeichnungen konvertieren, stellen Sie sicher, dass Sie die folgenden Änderungen und Überlegungen zur Kenntnis genommen haben. Aufgrund der Implementierungsänderungen ist die folgende Liste besonders wichtig, falls Sie zuvor Vorlagen im klassischen Azure-Portal verwaltet haben.

- Nachdem Sie eine Vorlage bearbeitet oder konvertiert und die Azure Information Protection-Richtlinie gespeichert haben, werden folgende Änderungen an den ursprünglichen [Nutzungsrechten](configure-usage-rights.md) vorgenommen. Bei Bedarf können Sie einzelne Nutzungsrechte durch PowerShell mithilfe der Cmdlets [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) und [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition) hinzufügen oder entfernen.
    
    - **Speichern unter, Exportieren** (allgemeiner Name) wird entfernt. Im Azure-Portal können Sie dieses Nutzungsrecht nicht manuell festlegen, es ist jedoch im Nutzungsrecht „Vollzugriff“ inbegriffen, das Sie bei Bedarf hinzufügen können.
    
    - **Makros zulassen** (allgemeiner Name) wird automatisch hinzugefügt. Dieses Nutzungsrecht ist für die Azure Information Protection-Leiste in Office-Apps erforderlich.
    

- Für die Einstellungen **Veröffentlicht** und **Archiviert** werden auf dem Blatt **Bezeichnung** die Optionen **Aktiviert**: **Ein** bzw. **Aktiviert**: **Aus** angezeigt. Legen Sie Vorlagen, die beibehalten werden sollen, die aber nicht für Benutzer oder Dienste sichtbar sein sollen, auf **Aktiviert**: **Aus** fest.

- Sie können eine Vorlage im Azure-Portal weder kopieren noch löschen. Wenn die Vorlage zu einer Bezeichnung konvertiert wird, können Sie die Bezeichnung so konfigurieren, dass sie die Vorlage nicht mehr verwendet. Dies erreichen Sie, indem Sie für die Option **Berechtigungen für Dokumente und E-Mails mit Bezeichnung festlegen** **Nicht konfiguriert** auswählen. Alternativ können Sie die Bezeichnung löschen. In beiden Szenarios wird die Vorlage jedoch nicht gelöscht und bleibt aktiviert.
    
    Sie können nun die Vorlage mithilfe des PowerShell-Cmdlets [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) löschen. Sie können dieses PowerShell-Cmdlet auch für Vorlagen verwenden, die nicht zu Bezeichnungen konvertiert werden. Wenn Sie aber eine Vorlage löschen, die zum Schutz von Inhalt verwendet wurde, kann dieser Inhalt nicht länger geöffnet werden. Löschen Sie die Vorlagen nur, wenn Sie sicher sind, dass sie nicht zum Schützen von Dokumenten oder E-Mails in der Produktion verwendet wurden. Als Vorsichtsmaßnahme sollten Sie zuerst die Vorlage als Sicherung mithilfe des [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)-Cmdlets exportieren. 

- Abteilungsvorlagen (für einen Bereich konfigurierte Vorlagen) werden in der globalen Richtlinie angezeigt. Wenn Sie derzeit eine Abteilungsvorlage bearbeiten und speichern, wird die Bereichskonfiguration entfernt. Eine bereichsbezogene Vorlage entspricht in der Azure Information Protection-Richtlinie einer [bereichsbezogenen Richtlinie](configure-policy-scope.md). Wenn Sie die Vorlage in eine Bezeichnung konvertieren, können Sie einen vorhandenen Bereich auswählen.
    
    Darüber hinaus können Sie derzeit nicht die Anwendungskompatibilitätseinstellung für eine Abteilungsvorlage festlegen. Falls erforderlich, können Sie die Einstellung für Anwendungskompatibilität durch PowerShell und das Cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) festlegen.

- Wenn Sie eine Vorlage zu einer Bezeichnung konvertieren oder mit einer verknüpfen, kann sie nicht länger von anderen Bezeichnungen verwendet werden. Zusätzlich wird diese Vorlage nicht mehr im Abschnitt **Vorlagen** oder **Protection Templates** (Vorlagen zum Schutz) angezeigt. Dieser Abschnitt wird zurzeit umbenannt.

- Sie erstellen keine neue Vorlage aus dem Abschnitt **Vorlagen** oder **Protection Templates**. Sie erstellen stattdessen eine Bezeichnung, die die Einstellung **Schützen** aufweist, und konfigurieren die Nutzungsrechte und -einstellungen auf dem Blatt **Schutz**. Vollständige Anweisungen finden Sie unter [Erstellen einer neuen Vorlage](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Konfigurieren von Vorlagen in der Azure Information Protection-Richtlinie

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.     
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Vorlage für alle Benutzer verfügbar ist, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien).
    
    Wenn sich die zu konfigurierende Vorlage in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer verfügbar ist, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

3. Suchen Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) oder auf dem Blatt **Richtlinie\<name>** nach der Vorlage, die Sie konfigurieren möchten:
    
    - Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst: Erweitern Sie **Protection templates** (Schutzvorlagen) neben Ihren Bezeichnungen.
    
    - Bei einem Abonnement, das nur Schutz umfasst: Vorlagen werden als Bezeichnungen angezeigt.

4. Wählen Sie die Vorlage aus. Auf dem Blatt **Bezeichnung** können Sie ggf. den Vorlagennamen und die Beschreibung ändern, indem Sie bei Bedarf **Bezeichnungsname** und **Beschreibung** bearbeiten. Wählen Sie dann **Schutz** mit dem Wert **Azure (cloud key)** (Azure (Cloud-Schlüssel)) aus, um das Blatt **Schutz** zu öffnen.

5. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren der Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.

6. Klicken Sie auf dem ersten Blatt der **Azure Information Protection** auf **Veröffentlichen**, um Ihre Änderungen für Benutzeranwendungen und -dienste verfügbar zu machen.

> [!NOTE]
> Sie können eine Vorlage auch bearbeiten, indem Sie die Schaltfläche **Vorlage bearbeiten** auf dem Blatt **Schutz** verwenden, wenn Sie eine Bezeichnung so konfiguriert haben, dass eine vordefinierte Vorlage verwendet wird. Vorausgesetzt, dass keine andere Bezeichnung die ausgewählte Vorlage verwendet, konvertiert diese Schaltfläche die Vorlage in eine Bezeichnung, und Sie gelangen zu Schritt 5. Weitere Informationen darüber, was beim Konvertieren von Vorlagen zu Bezeichnungen geschieht, finden Sie im nächsten Abschnitt.

## <a name="to-convert-templates-to-labels"></a>Konvertieren von Vorlagen in Bezeichnungen

Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst, können Sie eine Vorlage in eine Bezeichnung konvertieren. Dabei wird die ursprüngliche Vorlage beibehalten, jedoch im Azure-Portal nun als in einer neuen Bezeichnung enthalten angezeigt.

Wenn Sie beispielsweise eine Bezeichnung mit dem Namen **Marketing** konvertieren, die der Marketinggruppe Nutzungsrechte gewährt, wird sie im Azure-Portal nun als Bezeichnung mit dem Namen **Marketing** angezeigt, die dieselben Schutzeinstellungen aufweist. Wenn Sie die Schutzeinstellungen in dieser neu erstellten Bezeichnung ändern, ändern Sie sie in der Vorlage. Die neuen Schutzeinstellungen werden bei der nächsten Aktualisierung der Vorlage auf Benutzer oder Dienste angewendet, die diese Vorlage verwenden. 

Es ist nicht erforderlich, alle Vorlagen in Bezeichnungen zu konvertieren, aber falls Sie es tun sollten, werden die Schutzeinstellungen vollständig in die gesamte Funktionalität der Bezeichnungen integriert, sodass Sie die Einstellungen nicht separat verwalten müssen.

Um eine Vorlage in eine Bezeichnung zu konvertieren, klicken Sie mit der rechten Maustaste auf die Vorlage und wählen Sie **In Bezeichnung konvertieren** aus. Wählen Sie diese Option wahlweise über das Kontextmenü aus. 

Sie können eine Vorlage auch zu einer Bezeichnung konvertieren, wenn Sie eine Bezeichnung für den Schutz und eine vordefinierte Vorlage konfigurieren, indem Sie die Schaltfläche **Vorlage bearbeiten** verwenden. 

Bei der Konvertierung einer Vorlage in eine Bezeichnung:

- Der Name der Vorlage wird in den neuen Bezeichnungsnamen konvertiert, während die Beschreibung der Vorlage in eine QuickInfo für die Bezeichnung konvertiert wird. 

- Wenn der Status der Vorlage veröffentlicht wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Ein** festgelegt. Diese wird Benutzern nun angezeigt, wenn Sie die Azure Information Protection-Richtlinie das nächste Mal veröffentlichen. Wenn der Status der Vorlage archiviert wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Aus** festgelegt und Benutzern nicht als verfügbare Bezeichnung angezeigt.

- Die Schutzeinstellungen werden beibehalten. Sie können diese bei Bedarf bearbeiten und auch andere Bezeichnungseinstellungen wie visuelle Kennzeichnungen und Bedingungen hinzufügen.

- Die Originalvorlage wird nicht mehr unter **Vorlagen** oder **Protection templates** angezeigt und kann nicht als eine vordefinierte Vorlage ausgewählt werden, wenn Sie Schutz für eine Bezeichnung konfigurieren. Um diese Vorlage im Azure-Portal zu bearbeiten, bearbeiten Sie nun die Bezeichnung, die bei der Konvertierung der Vorlage erstellt wurde. Die Vorlage ist weiterhin für den Azure Rights Management-Dienst verfügbar und kann nach wie vor mit [PowerShell-Befehlen](administer-powershell.md) verwaltet werden.  

## <a name="to-create-a-new-template"></a>So erstellen Sie eine neue Vorlage

Wenn Sie eine neue Bezeichnung mit der Schutzeinstellung **Azure RMS** oder **Azure (cloud key)** erstellen, wird hierdurch im Hintergrund eine neue benutzerdefinierte Vorlage erstellt. Auf diese kann dann über Dienste und Anwendungen, die in Rights Management-Vorlagen integriert werden, zugegriffen werden.

1. Wenn die neue Vorlage für alle Benutzer verfügbar ist, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien).
    
     Wenn es sich bei der neuen Vorlage um eine Abteilungsvorlage handelt, sodass sie nur für ausgewählte Benutzer verfügbar ist, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Erstellen Sie dann Ihre [bereichsbezogene Richtlinie](configure-policy-scope.md), oder wählen Sie sie auf dem Blatt **Azure Information Protection - Scoped polices** (Azure Information Protection – Bereichsbezogene Richtlinien) aus.

2. Klicken Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) oder auf dem Blatt **Richtlinie:\<name>** auf **Neue Bezeichnung hinzufügen**.

3. Behalten Sie auf dem Blatt **Bezeichnung** die Standardeinstellung **Aktiviert**: **Ein** bei, um diese neue Vorlage zu veröffentlichen, oder ändern Sie diese Einstellung in **Aus**, um die Vorlage als archiviert zu erstellen. Geben Sie dann einen Bezeichnungsnamen und eine Beschreibung für den Vorlagennamen und die Beschreibung ein.

4. Wählen Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** die Optionen **Schützen** und dann **Schutz** aus:
    
     ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar-configured.png)

5. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren dieser Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.

6. Klicken Sie auf dem ersten Blatt der **Azure Information Protection** auf **Veröffentlichen**, um diese Vorlagen für Benutzeranwendungen und -dienste verfügbar zu machen.


## <a name="next-steps"></a>Nächste Schritte

Wie bei allen Änderungen an der Azure Information Protection-Richtlinie kann es bis zu 15 Minuten dauern, bis der Download dieser Vorlagen auf einem Computer abgeschlossen ist, auf dem der Azure Information Protection-Client ausgeführt wird. Informationen zum Herunterladen und Aktualisieren von Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

Alle Vorgänge, die Sie im klassischen Azure-Portal zum Erstellen und Verwalten von Vorlagen konfigurieren können, können Sie auch mithilfe von PowerShell durchführen. PowerShell bietet darüber hinaus weitere Optionen, die nicht im Portal verfügbar sind. Weitere Informationen finden Sie in der [PowerShell-Referenz zum Schutz von Vorlagen](configure-templates-with-powershell.md). 

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
