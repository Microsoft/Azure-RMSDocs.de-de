---
title: "Konfigurieren und Verwalten von Vorlagen für Azure Information Protection"
description: Konfigurieren und Verwalten von Rights Management-Vorlagen im Azure-Portal.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 671d1d5d706225fcd5c680ddc8687aa889b59b59
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Konfigurieren und Verwalten von Vorlagen für Azure Information Protection

>*Gilt für: Azure Information Protection*

>[!NOTE]
>Diese Funktion ersetzt das Konfigurieren benutzerdefinierter Vorlagen im klassischen Azure-Portal. Das klassische Portal ist nicht mehr verfügbar, daher müssen Sie das Azure-Portal verwenden. Eine kurze Anleitung finden Sie unter [Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben](migrate-portal.md).


Rights Management-Vorlagen sind nun in die Azure Information Protection-Richtlinie integriert. 

**Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst (Azure Information Protection P1 oder P2):**

- Rights Management-Vorlagen, die nicht in Ihren Bezeichnungen für Ihren Mandanten enthalten sind, werden nach den Bezeichnungen auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie) im Abschnitt **Schutzvorlagen** angezeigt. Sie können diese Vorlagen in Bezeichnungen konvertieren, oder Sie können eine Verknüpfung mit ihnen herstellen, wenn Sie den Schutz ihrer Bezeichnungen konfigurieren. 

**Bei einem Abonnement, das nur Schutz umfasst (ein Office 365-Abonnement mit dem Azure Rights Management-Dienst):**

- Rights Management-Vorlagen für Ihren Mandanten werden auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie) im Abschnitt **Schutzvorlagen** angezeigt. Es werden keine Bezeichnungen angezeigt. Darüber hinaus sehen Sie Konfigurationseinstellungen, die für die Klassifizierung und die Bezeichnung spezifisch sind. Diese Einstellungen haben jedoch entweder keinen Einfluss auf Ihre Vorlagen oder können nicht konfiguriert werden. 

## <a name="default-templates"></a>Standardvorlagen

Wenn Sie Ihr Abonnement für Azure Information Protection oder für ein Office 365-Abonnement anfordern, das den Azure Rights Management-Dienst enthält, werden automatisch zwei Standardvorlagen für Ihren Mandanten erstellt. Diese Vorlagen gewähren nur autorisierten Benutzern in Ihrer Organisation Zugriff. Wenn diese Vorlagen erstellt werden, verfügen sie über die Berechtigungen, die in der Dokumentation [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md#rights-included-in-the-default-templates) aufgeführt sind.

Zusätzlich werden die Vorlagen so konfiguriert, dass sie einen Offlinezugriff für sieben Tage zulassen und kein Ablaufdatum haben.

>[!NOTE]
> Sie können diese Einstellungen und die Namen und Beschreibungen der Standardvorlagen ändern. Dies war mit dem klassischen Azure-Portal nicht möglich und wird auch weiterhin nicht für PowerShell unterstützt.

Diese Standardvorlagen erleichtern es Ihnen und anderen Personen, sofort mit dem Schutz sensibler Daten Ihrer Organisation zu beginnen. Diese Vorlagen können mit Azure Information Protection-Bezeichnungen oder alleine mit [Anwendungen und Diensten](../understand-explore/applications-support.md) verwendet werden, die Rights Management-Vorlagen verwenden können.

Sie können auch eigene, benutzerdefinierte Vorlagen erstellen. Sie benötigen wahrscheinlich nur einige Vorlagen, aber in Azure ist es möglich, maximal 500 benutzerdefinierte Vorlagen zu speichern.

### <a name="default-template-names"></a>Namen für die Standardvorlage

Wenn Sie Ihr Abonnement vor Kurzem erworben haben, werden Ihre Standardvorlagen mit folgenden Namen erstellt:

- **Vertraulich\Alle Mitarbeiter** erteilt Lese- und Änderungsberechtigungen für den geschützten Inhalt.

- **Streng vertraulich\Alle Mitarbeiter** erteilt Leseberechtigungen für den geschützten Inhalt.

Wenn Sie Ihr Abonnement vor längerer Zeit erworben haben, werden Ihre Standardvorlagen mit folgenden Namen erstellt:

- **\<Name der Organisation> – Vertraulich** erteilt Lese- und Änderungsberechtigungen für den geschützten Inhalt.

- **\<Name der Organisation> – Nur vertrauliche Ansicht** erteilt Leseberechtigungen für den geschützten Inhalt. 

Sie können diese Standardvorlagen umbenennen (und neu konfigurieren), wenn Sie das Azure-Portal verwenden.

>[!NOTE]
>Werden Ihre Standardvorlagen auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie) nicht angezeigt, werden sie in Bezeichnungen konvertiert oder mit einer Bezeichnung verknüpft. Sie sind noch immer als Vorlage vorhanden, werden im Azure-Portal jedoch als Teil einer Konfiguration der Bezeichnung angezeigt, die Azure RMS-Schutz enthält. Sie können stets überprüfen, über welche Vorlagen Ihr Mandant verfügt, indem Sie [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) über das [AADRM-PowerShell-Modul](administer-powershell.md) ausführen.
>
>Sie können Vorlagen manuell konvertieren (siehe weiter unten unter [Konvertieren von Vorlagen in Bezeichnungen](#to-convert-templates-to-labels)) und bei Bedarf umbenennen. Sie werden automatisch konvertiert, wenn Ihre Azure Information Protection-Standardrichtlinie vor Kurzem erstellt und der Azure Rights Management-Dienst für Ihren Mandanten zu diesem Zeitpunkt aktiviert wurde.

Vorlagen, die archiviert werden, werden auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie) als nicht verfügbar angezeigt. Diese Vorlagen können nicht für Bezeichnungen ausgewählt, können aber in Bezeichnungen konvertiert werden.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Überlegungen zu Vorlagen im Azure-Portal

Bevor Sie diese Vorlagen bearbeiten oder in Bezeichnungen konvertieren, stellen Sie sicher, dass Sie die folgenden Änderungen und Überlegungen zur Kenntnis genommen haben. Aufgrund der Implementierungsänderungen ist die folgende Liste besonders wichtig, falls Sie zuvor Vorlagen im klassischen Azure-Portal verwaltet haben.

- Nachdem Sie eine Vorlage bearbeitet oder konvertiert und die Azure Information Protection-Richtlinie gespeichert haben, werden folgende Änderungen an den ursprünglichen [Nutzungsrechten](configure-usage-rights.md) vorgenommen. Bei Bedarf können Sie einzelne Nutzungsrechte mithilfe des Azure-Portals hinzufügen oder entfernen. Verwenden Sie alternativ PowerShell mit den Cmdlets [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) und [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition).
    
    - **Makros zulassen** (allgemeiner Name) wird automatisch hinzugefügt. Dieses Nutzungsrecht ist für die Azure Information Protection-Leiste in Office-Apps erforderlich.

- Für die Einstellungen **Veröffentlicht** und **Archiviert** werden auf dem Blatt **Bezeichnung** die Optionen **Aktiviert**: **Ein** bzw. **Aktiviert**: **Aus** angezeigt. Legen Sie für Vorlagen, die beibehalten werden, aber nicht für Benutzer oder Dienste sichtbar sein sollen, **Aktiviert**: **Aus** fest.

- Sie können eine Vorlage im Azure-Portal nicht kopieren oder löschen. Wenn die Vorlage in eine Bezeichnung konvertiert wird, können Sie die Bezeichnung so konfigurieren, dass sie die Vorlage nicht mehr verwendet. Legen Sie dafür für **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** die Option **Nicht konfiguriert** fest. Sie können die Bezeichnung auch löschen. In beiden Szenarien wird die Vorlage jedoch nicht gelöscht und bleibt archiviert.
    
    Sie können die Vorlage nun mithilfe des PowerShell-Cmdlets [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) löschen. Sie können dieses PowerShell-Cmdlet auch für Vorlagen verwenden, die nicht in Bezeichnungen konvertiert werden. Wenn Sie jedoch eine Vorlage löschen, die zum Schutz von Inhalt verwendet wurde, kann dieser Inhalt nicht mehr geöffnet werden. Löschen Sie Vorlagen nur, wenn Sie sicher sind, dass sie nicht zum Schützen von Dokumenten oder E-Mails in der Produktion verwendet wurden. Als Vorsichtsmaßnahme sollten Sie zuerst die Vorlage als Sicherung mithilfe des Cmdlets [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) exportieren. 

- Abteilungsvorlagen (für einen Bereich konfigurierte Vorlagen) werden in der globalen Richtlinie angezeigt. Wenn Sie eine Abteilungsvorlage bearbeiten und speichern, wird derzeit die Bereichskonfiguration entfernt. Eine bereichsbezogene Vorlage entspricht in der Azure Information Protection-Richtlinie einer [bereichsbezogenen Richtlinie](configure-policy-scope.md). Wenn Sie die Vorlage in eine Bezeichnung konvertieren, können Sie einen vorhandenen Bereich auswählen.
    
    Darüber hinaus können Sie derzeit nicht die Anwendungskompatibilitätseinstellung für eine Abteilungsvorlage festlegen. Bei Bedarf können Sie die Einstellung für Anwendungskompatibilität mit dem Cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) und dem Parameter *EnableInLegacyApps* festlegen.

- Wenn Sie eine Vorlage in eine Bezeichnung konvertieren oder mit einer Bezeichnung verknüpfen, kann sie nicht länger von anderen Bezeichnungen verwendet werden. Darüber hinaus wird diese Vorlage nicht mehr im Abschnitt **Schutzvorlagen** angezeigt. 

- Sie erstellen keine neue Vorlage im Abschnitt **Schutzvorlagen**. Stattdessen erstellen Sie eine Bezeichnung mit der Einstellung **Schützen** und konfigurieren die Nutzungsrechte und -einstellungen auf dem Blatt **Schutz**. Vollständige Anweisungen finden Sie unter [So erstellen Sie eine neue Vorlage](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>So konfigurieren Sie die Vorlagen in der Azure Information Protection-Richtlinie

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.     
    
    Klicken Sie beispielsweise im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Vorlage für alle Benutzer vorgesehen ist, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie).
    
    Wenn sich die zu konfigurierende Vorlage in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass Sie nur für ausgewählte Benutzer verfügbar ist, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien) aus.

3. Suchen Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie) oder auf dem Blatt **Richtlinie:\<Name>** nach der Vorlage, die Sie konfigurieren möchten:
    
    - Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst: Erweitern Sie **Schutzvorlagen** neben Ihren Bezeichnungen.
    
    - Bei einem Abonnement, das nur Schutz umfasst: Vorlagen werden als Bezeichnungen angezeigt.

4. Wählen Sie die Vorlage aus. Auf dem Blatt **Bezeichnung** können Sie ggf. den Vorlagennamen und die Beschreibung ändern, indem Sie **Anzeigename für Bezeichnung** und **Beschreibung** bearbeiten. Wählen Sie dann **Schutz** mit dem Wert **Azure (Cloudschlüssel)** aus, um das Blatt **Schutz** zu öffnen.

5. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren der Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.

6. Klicken Sie auf dem ersten Blatt **Azure Information Protection** auf **Veröffentlichen**, um Ihre Änderungen für Benutzeranwendungen und -dienste verfügbar zu machen.

> [!NOTE]
> Sie können eine Vorlage auch über die Schaltfläche **Vorlage bearbeiten** auf dem Blatt **Schutz** bearbeiten, wenn Sie eine Bezeichnung für die Verwendung einer vordefinierten Vorlage konfiguriert haben. Sofern keine andere Bezeichnung die ausgewählte Vorlage verwendet, wird mit dieser Schaltfläche die Vorlage in eine Bezeichnung konvertiert, und Sie gelangen zu Schritt 5. Weitere Informationen dazu, was beim Konvertieren von Bezeichnungen in Vorlagen geschieht, finden Sie im nächsten Abschnitt.

## <a name="to-convert-templates-to-labels"></a>So konvertieren Sie Vorlagen in Bezeichnungen

Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst, können Sie eine Vorlage in eine Bezeichnung konvertieren. Wenn Sie eine Vorlage konvertieren, wird die ursprüngliche Vorlage beibehalten, wird jedoch im Azure-Portal als in einer neuen Bezeichnung enthalten angezeigt.

Wenn Sie beispielsweise eine Bezeichnung mit dem Namen **Marketing** konvertieren, die der Marketinggruppe Nutzungsrechte gewährt, wird sie im Azure-Portal nun als Bezeichnung mit dem Namen **Marketing** angezeigt, die dieselben Schutzeinstellungen aufweist. Wenn Sie die Schutzeinstellungen in dieser neu erstellten Bezeichnung ändern, ändern Sie sie in der Vorlage. Benutzer oder Dienste, die diese Vorlage verwenden, erhalten die neuen Schutzeinstellungen bei der nächsten Aktualisierung der Vorlage. 

Es ist nicht erforderlich, alle Vorlagen in Bezeichnungen zu konvertieren. Falls Sie das aber tun, werden die Schutzeinstellungen vollständig in die gesamte Funktionalität der Bezeichnungen integriert, sodass Sie die Einstellungen nicht separat verwalten müssen.

Klicken Sie zum Konvertieren einer Vorlage in eine Bezeichnung mit der rechten Maustaste auf die Vorlage, und klicken Sie auf **In Bezeichnung konvertieren**. Alternativ können Sie diese Option auch über das Kontextmenü auswählen. 

Sie können eine Vorlage auch in eine Bezeichnung konvertieren, wenn Sie eine Bezeichnung für den Schutz und eine vordefinierte Vorlage konfigurieren. Verwenden Sie dazu die Schaltfläche **Vorlage bearbeiten**. 

Bei der Konvertierung einer Vorlage in eine Bezeichnung:

- Der Name der Vorlage wird in den neuen Bezeichnungsnamen konvertiert, und die Beschreibung der Vorlage wird in eine QuickInfo für die Bezeichnung konvertiert. 

- Wenn der Status der Vorlage veröffentlicht wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Ein** festgelegt. Diese wird Benutzern nun angezeigt, wenn Sie die Azure Information Protection-Richtlinie das nächste Mal veröffentlichen. Wenn der Status der Vorlage archiviert wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Aus** festgelegt und Benutzern nicht als verfügbare Bezeichnung angezeigt.

- Die Schutzeinstellungen werden beibehalten. Sie können diese bei Bedarf bearbeiten und auch andere Bezeichnungseinstellungen wie visuelle Kennzeichnungen und Bedingungen hinzufügen.

- Die ursprüngliche Vorlage wird nicht mehr unter **Schutzvorlagen** angezeigt und kann nicht als eine vordefinierte Vorlage ausgewählt werden, wenn Sie den Schutz für eine Bezeichnung konfigurieren. Um diese Vorlage im Azure-Portal zu bearbeiten, bearbeiten Sie nun die Bezeichnung, die beim Konvertieren der Vorlage erstellt wurde. Die Vorlage ist weiterhin für den Azure Rights Management-Dienst verfügbar und kann nach wie vor mit [PowerShell-Befehlen](administer-powershell.md) verwaltet werden.  

## <a name="to-create-a-new-template"></a>So erstellen Sie eine neue Vorlage

Wenn Sie eine neue Bezeichnung mit der Schutzeinstellung **Azure RMS** oder **Azure (Cloudschlüssel)** erstellen, wird hierdurch im Hintergrund eine neue benutzerdefinierte Vorlage erstellt. Auf diese kann dann über Dienste und Anwendungen zugegriffen werden, die in Rights Management-Vorlagen integriert werden.

1. Wenn die neue Vorlage für alle Benutzer vorgesehen ist, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie).
    
     Wenn es sich bei der neuen Vorlage um eine Abteilungsvorlage handelt, sodass sie nur für ausgewählte Benutzer verfügbar ist, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Erstellen Sie dann Ihre [bereichsbezogene Richtlinie](configure-policy-scope.md), oder wählen Sie sie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien) aus.

2. Klicken Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie) oder auf dem Blatt **Richtlinie:\<Name>** auf **Neue Bezeichnung hinzufügen**.

3. Behalten Sie auf dem Blatt **Bezeichnung** die Standardeinstellung **Aktiviert**: **Ein** bei, um diese neue Vorlage zu veröffentlichen, oder ändern Sie diese Einstellung in **Aus**, um die Vorlage als archiviert zu erstellen. Geben Sie dann einen Bezeichnungsnamen und eine Beschreibung für den Vorlagennamen und die Beschreibung ein.

4. Wählen Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** die Optionen **Schützen** und dann **Schutz** aus:
    
     ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar-configured.png)

5. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren dieser Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.

6. Klicken Sie auf dem ersten Blatt **Azure Information Protection** auf **Veröffentlichen**, um diese Vorlagen für Benutzeranwendungen und -dienste verfügbar zu machen.


## <a name="next-steps"></a>Nächste Schritte

Wie bei allen Änderungen an der Azure Information Protection-Richtlinie kann es bis zu 15 Minuten dauern, bis der Download dieser Vorlagen auf einem Computer abgeschlossen ist, auf dem der Azure Information Protection-Client ausgeführt wird. Informationen zum Herunterladen und Aktualisieren von Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Vorlagen konfigurieren können, können Sie auch mithilfe von PowerShell durchführen. PowerShell bietet darüber hinaus weitere Optionen, die nicht im Portal verfügbar sind. Weitere Informationen finden Sie unter [PowerShell-Referenz für benutzerdefinierte Vorlagen](configure-templates-with-powershell.md). 

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
