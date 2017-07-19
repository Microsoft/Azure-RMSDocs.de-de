---
title: Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie
description: "Derzeit können Sie in der Vorschau nun Rights Management-Vorlagen aus der Azure Information Protection-Richtlinie konfigurieren und verwalten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 1f41aad2d132e087e9122b2683be4b45185527de
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-and-managing-templates-in-the-azure-information-protection-policy"></a>Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection*

>[!NOTE]
>Diese Funktion ist derzeit in der Vorschau vorhanden und ist häufigen Änderungen vorbehalten.
>
>Bevor Sie diese Vorschaufunktion mit benutzerdefinierten Vorlagen testen, die Sie im klassischen Azure-Portal erstellt haben, prüfen Sie, ob Sie über eine aktuelle Sicherung Ihrer Vorlagen verfügen. Sie können Ihre benutzerdefinierten Vorlagen anhand des PowerShell-Cmdlets [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) sichern und bei Bedarf mit [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate) wiederherstellen.
>
>Aufgrund der Unterschiede bei der Implementierung wird davon abgeraten, dieselben Vorlagen aus dem klassischen Azure-Portal und dem Azure-Portal zu verwalten.


Rights Management-Vorlagen sind nun in der Azure Information Protection-Richtlinie integriert. 

**Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst (Azure Information Protection P1 oder P2):**

- Rights Management-Vorlagen für Ihren Mandanten werden im neuen Abschnitt **Vorlagen** neben den Bezeichnungen angezeigt. Sie können diese Vorlagen in Bezeichnungen konvertieren oder weiterhin als separate Vorlagen verwalten und verknüpfen, wenn Sie den Schutz für Ihre Bezeichnungen konfigurieren. 

**Bei einem Abonnement, das nur Schutz umfasst (ein Office 365-Abonnement mit dem Azure Rights Management-Dienst):**

- Rights Management-Vorlagen für Ihren Mandanten werden als Bezeichnungen angezeigt. Konfigurationseinstellungen speziell für die Klassifizierung und Bezeichnung sind zurzeit ebenfalls verfügbar. 


## <a name="considerations-for-templates-in-the-azure-portal"></a>Überlegungen zu Vorlagen im Azure-Portal

Bevor Sie diese Vorlagen im Azure-Portal bearbeiten oder in Bezeichnungen konvertieren, beachten Sie bei der Verwaltung von Vorlagen im klassischen Azure-Portal die folgenden Änderungen an der Implementierung. Während der Vorschau werden voraussichtlich einige Beschränkungen aufgelöst:

- Nachdem Sie eine Vorlage bearbeitet oder konvertiert und die Azure Information Protection-Richtlinie gespeichert haben, werden folgende Änderungen an den ursprünglichen [Nutzungsrechten](configure-usage-rights.md) vorgenommen. Bei Bedarf können Sie einzelne Nutzungsrechte durch PowerShell mithilfe der Cmdlets [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) und [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition) hinzufügen oder entfernen.
    
    - **Speichern unter, Exportieren** (allgemeiner Name) wird entfernt. Im Azure-Portal können Sie dieses Nutzungsrecht nicht manuell festlegen, es ist jedoch im Nutzungsrecht „Vollzugriff“ inbegriffen, das Sie bei Bedarf hinzufügen können.
    
    - **Makros zulassen** (allgemeiner Name) wird automatisch hinzugefügt. Dieses Nutzungsrecht ist für die Azure Information Protection-Leiste in Office-Apps erforderlich.
    
- Derzeit werden die Standardvorlagen angezeigt, können jedoch nicht bearbeitet oder konvertiert werden. 

- Sie können eine Vorlage weder kopieren noch löschen. Um eine Vorlage zu entfernen, verwenden Sie das PowerShell-Cmdlet [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate). 

- Derzeit werden diese Sprachen in Vorlagen, die mit dem klassischen Azure-Portal oder PowerShell für Sprachen konfiguriert wurden, nicht für den Namen und Beschreibungen angezeigt, werden jedoch beibehalten.

- Für die Einstellungen **Veröffentlicht** und **Archiviert** werden auf dem Blatt **Bezeichnung** die Optionen **Aktiviert**: **Ein** bzw. **Aktiviert**: **Aus** angezeigt.

- Abteilungsvorlagen (für einen Bereich konfigurierte Vorlagen) werden in der globalen Richtlinie angezeigt. Wenn Sie derzeit eine Abteilungsvorlage bearbeiten und speichern, wird die Bereichskonfiguration entfernt. Eine bereichsbezogene Vorlage entspricht in der Azure Information Protection-Richtlinie einer [bereichsbezogenen Richtlinie](configure-policy-scope.md). Wenn Sie die Vorlage in eine Bezeichnung konvertieren, können Sie einen vorhandenen Bereich auswählen.
    
    Darüber hinaus können Sie derzeit nicht die Anwendungskompatibilitätseinstellung für eine Abteilungsvorlage festlegen. Falls erforderlich, können Sie diese durch PowerShell mithilfe des Cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) festlegen.

- Statt eine neue Vorlage über den **Vorlagen**-Container zu erstellen, erstellen Sie eine Bezeichnung, die die Einstellung **Schützen** aufweist, und konfigurieren Sie die Nutzungsrechte und -einstellungen auf dem Blatt **Schutz**. Vollständige Anweisungen finden Sie unter [Erstellen einer neuen Vorlage](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Konfigurieren von Vorlagen in der Azure Information Protection-Richtlinie

1. Melden Sie sich in einem neuen Browserfenster als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an.

2. Navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Weitere Dienste**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 

2. Wenn die zu konfigurierende Vorlage für alle Benutzer gilt, wählen Sie auf dem Blatt **Azure Information Protection** die Option **Global** aus. Wenn sich die zu konfigurierende Vorlage in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, wählen Sie stattdessen die bereichsbezogene Richtlinie aus.

3. Suchen Sie auf dem Blatt „Richtlinie“ die Vorlage, die Sie konfigurieren möchten:
    
    - Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst: Erweitern Sie **Vorlagen** neben Ihren Bezeichnungen.
    
    - Bei einem Abonnement, das nur Schutz umfasst: Vorlagen werden als Bezeichnungen angezeigt.

4. Wählen Sie die Vorlage aus. Auf dem Blatt **Bezeichnung** können Sie ggf. den Vorlagennamen und die Beschreibung ändern, indem Sie bei Bedarf **Bezeichnungsname** und **Beschreibung** bearbeiten. Wählen Sie dann **Schutz** mit dem Wert **Azure RMS**, um das Blatt **Schutz** zu öffnen.

5. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren der Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.

6. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Veröffentlichen**, um Ihre Änderungen für Benutzeranwendungen und -dienste verfügbar zu machen.

## <a name="to-convert-templates-to-labels"></a>Konvertieren von Vorlagen in Bezeichnungen

Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst, können Sie eine Vorlage in eine Bezeichnung konvertieren. Dabei wird die ursprüngliche Vorlage beibehalten, jedoch im Azure-Portal nun als in einer neuen Bezeichnung enthalten angezeigt.

Wenn Sie beispielsweise eine Bezeichnung mit dem Namen **Marketing** konvertieren, die der Marketinggruppe Nutzungsrechte gewährt, wird sie im Azure-Portal nun als Bezeichnung mit dem Namen **Marketing** angezeigt, die dieselben Schutzeinstellungen aufweist. Wenn Sie die Schutzeinstellungen in dieser neu erstellten Bezeichnung ändern, ändern Sie sie in der Vorlage. Die neuen Schutzeinstellungen werden bei der nächsten Aktualisierung der Vorlage auf Benutzer oder Dienste angewendet, die diese Vorlage verwenden. 

Es ist nicht erforderlich, alle Vorlagen in Bezeichnungen zu konvertieren, aber falls Sie es tun sollten, werden die Schutzeinstellungen vollständig in die gesamte Funktionalität der Bezeichnungen integriert, sodass Sie die Einstellungen nicht separat verwalten müssen.

Um eine Vorlage in eine Bezeichnung zu konvertieren, klicken Sie mit der rechten Maustaste auf die Vorlage und wählen Sie **In Bezeichnung konvertieren** aus. Wählen Sie diese Option wahlweise über das Kontextmenü aus.

Bei der Konvertierung einer Vorlage in eine Bezeichnung:

- Der Name der Vorlage wird in den neuen Bezeichnungsnamen konvertiert, während die Beschreibung der Vorlage in eine QuickInfo für die Bezeichnung konvertiert wird. 

- Wenn der Status der Vorlage veröffentlicht wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Ein** festgelegt. Diese wird Benutzern nun angezeigt, wenn Sie die Azure Information Protection-Richtlinie das nächste Mal veröffentlichen. Wenn der Status der Vorlage archiviert wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Aus** festgelegt und Benutzern nicht als verfügbare Bezeichnung angezeigt.

- Die Schutzeinstellungen werden beibehalten. Sie können diese bei Bedarf bearbeiten und auch andere Bezeichnungseinstellungen wie visuelle Kennzeichnungen und Bedingungen hinzufügen.

- Die Originalvorlage wird nicht mehr unter **Vorlagen** angezeigt. Um diese im Azure-Portal zu bearbeiten, bearbeiten Sie nun die erstellte Bezeichnung. Die Vorlage ist weiterhin für den Azure Rights Management-Dienst verfügbar und kann nach wie vor mit [PowerShell-Befehlen](administer-powershell.md) verwaltet werden.  

## <a name="to-create-a-new-template"></a>So erstellen Sie eine neue Vorlage

Wenn Sie eine neue Bezeichnung mit der Schutzeinstellung **Azure RMS** erstellen, wird hierdurch im Hintergrund eine neue benutzerdefinierte Vorlage erstellt. Auf diese kann dann über Dienste und Anwendungen, die in Rights Management-Vorlagen integriert werden, zugegriffen werden.

1. Wenn die neue Vorlage, die Sie erstellen möchten, für alle Benutzer gilt, klicken Sie auf dem Blatt **Richtlinie: Global** auf **Neue Bezeichnung hinzufügen**.
    
     Wenn die neue zu erstellende Vorlage als Abteilungsvorlage eingesetzt wird, die nur für ausgewählte Benutzer gilt, wählen Sie zunächst auf dem ersten Blatt **Azure Information Protection** die bereichsbezogene Richtlinie aus oder erstellen Sie eine.

2. Behalten Sie auf dem Blatt **Bezeichnung** die Standardeinstellung **Aktiviert**: **Ein** bei, um diese neue Vorlage zu veröffentlichen, oder ändern Sie diese Einstellung in **Aus**, um die Vorlage als archiviert zu erstellen. Geben Sie dann einen Bezeichnungsnamen und eine Beschreibung für den Vorlagennamen und die Beschreibung ein.

3. Wählen Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** die Optionen **Schützen** und dann **Schutz** aus:
    
     ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar.png)

4. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren dieser Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.

5. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Veröffentlichen**, um diese Vorlagen für Benutzeranwendungen und -dienste verfügbar zu machen.


## <a name="next-steps"></a>Nächste Schritte

Wie bei allen Änderungen an der Azure Information Protection-Richtlinie kann es bis zu 15 Minuten dauern, bis der Download dieser Vorlagen auf einem Computer abgeschlossen ist, auf dem der Azure Information Protection-Client ausgeführt wird. Informationen zum Herunterladen und Aktualisieren von Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
