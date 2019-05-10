---
title: Konfigurieren und Verwalten von Vorlagen für Azure Information Protection – AIP
description: Konfigurieren und Verwalten von schutzvorlagen, auch bekannt als Rights Management-Vorlagen, aus dem Azure-Portal.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 28b2c670c3204d5e69a963b8d2f5cabc3eeaa872
ms.sourcegitcommit: 2fe9333c3e6c98e7dd9003c5f4cd7c1e7a48b297
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64880104"
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Konfigurieren und Verwalten von Vorlagen für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Schutzvorlagen, auch als Rights Management-Vorlagen bekannt, sind eine Reihe von vom Administrator definierten Schutzeinstellungen für Azure Information Protection. Diese Einstellungen enthalten Ihre ausgewählten [Nutzungsrechte](configure-usage-rights.md) für autorisierte Benutzer sowie Zugriffssteuerungen für den Ablauf und den Offlinezugriff. Diese Vorlagen sind in der Azure Information Protection-Richtlinie integriert. 

**Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst (Azure Information Protection P1 oder P2):**

- Vorlagen, die nicht in Ihren Bezeichnungen für Ihren Mandanten enthalten sind, werden im Abschnitt **Schutzvorlagen** nach den Bezeichnungen auf dem Blatt **Azure Information Protection: Bezeichnungen** angezeigt. Klicken Sie auf die Menüoption **Klassifizierungen** > **Bezeichnungen**, um zu diesem Blatt zu navigieren. Sie können diese Vorlagen in Bezeichnungen konvertieren, oder Sie können eine Verknüpfung zu diesen herstellen, wenn Sie den Schutz ihrer Bezeichnungen konfigurieren. 

**Bei einem Abonnement, das nur Schutz umfasst (ein Office 365-Abonnement mit dem Azure Rights Management-Dienst):**

- Vorlagen für Ihren Mandanten werden auf dem Blatt **Azure Information Protection: Bezeichnungen** im Abschnitt **Schutzvorlagen** angezeigt. Klicken Sie auf die Menüoption **Klassifizierungen** > **Bezeichnungen**, um zu diesem Blatt zu navigieren. Es werden keine Bezeichnungen angezeigt. Darüber hinaus sehen Sie Konfigurationseinstellungen, die für die Klassifizierung und die Bezeichnung spezifisch sind. Aber diese Einstellungen haben entweder keinen Einfluss auf Ihre Vorlagen oder können nicht konfiguriert werden. 

>[!NOTE]
>In einigen Anwendungen und Diensten wird möglicherweise die Option [Nicht weiterleiten](configure-usage-rights.md#do-not-forward-option-for-emails) und [Nur verschlüsseln](configure-usage-rights.md#encrypt-only-option-for-emails) (oder **Verschlüsseln**) als Vorlage angezeigt. Dabei handelt es sich nicht um Vorlagen, die Sie bearbeiten oder löschen können, sondern vielmehr um Optionen, die standardmäßig mit dem Exchange-Dienst geliefert werden.

## <a name="default-templates"></a>Standardvorlagen

Wenn Sie Ihr Abonnement für Azure Information Protection oder für ein Office 365-Abonnement, das den Azure Rights Management-Dienst enthält, anfordern, werden automatisch zwei Standardvorlagen für Ihren Mandanten erstellt. Diese Vorlagen gewähren den Zugriff nur autorisierten Benutzern in Ihrer Organisation. Wenn diese Vorlagen erstellt werden, verfügen sie über die Berechtigungen, die in der Dokumentation [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md#rights-included-in-the-default-templates) aufgelistet sind.

Zusätzlich werden die Vorlagen so konfiguriert, dass sie einen Offlinezugriff für sieben Tage zulassen und kein Ablaufdatum haben.

>[!NOTE]
> Sie können diese Einstellungen und die Namen und Beschreibungen der Standardvorlagen ändern. Dies war mit dem klassischen Azure-Portal nicht möglich und wird auch weiterhin nicht für PowerShell unterstützt.

Diese Standardvorlagen erleichtern es Ihnen und anderen Personen, sofort mit dem Schutz sensibler Daten Ihrer Organisation zu beginnen. Diese Vorlagen können mit Azure Information Protection-Bezeichnungen oder alleine mit [Anwendungen und Diensten](applications-support.md) verwendet werden, die Rights Management-Vorlagen verwenden.

Sie können auch eigene, benutzerdefinierte Vorlagen erstellen. Sie benötigen wahrscheinlich nur einige Vorlagen, aber in Azure ist es möglich, maximal 500 gespeicherte benutzerdefinierte Vorlagen zu verwenden.


### <a name="default-template-names"></a>Namen für die Standardvorlage

Wenn Sie Ihr Abonnement erst vor Kurzem erworben haben, werden Ihre Standardvorlagen mit folgenden Namen erstellt:

- **Vertraulich\Alle Mitarbeiter** erteilt Lese- und Änderungsberechtigungen für den geschützten Inhalt.

- **Streng vertraulich\Alle Mitarbeiter** erteilt Leseberechtigungen für den geschützten Inhalt.

Wenn Sie Ihr Abonnement schon vor einiger Zeit erworben haben, werden Ihre Standardvorlagen mit folgenden Namen erstellt:

- **\<Name der Organisation> – Vertraulich** erteilt Lese- und Änderungsberechtigungen für den geschützten Inhalt.

- **\<Name der Organisation> – Nur vertrauliche Ansicht** erteilt Leseberechtigungen für den geschützten Inhalt. 

Sie können diese Standardvorlagen umbenennen (und neu konfigurieren), wenn Sie das Azure-Portal verwenden.

>[!NOTE]
>Wenn Sie Ihre Standardvorlagen auf dem Blatt **Azure Information Protection: Bezeichnungen** nicht sehen können, werden diese zu Bezeichnungen konvertiert oder mit einer Bezeichnung verknüpft. Diese sind noch immer als Vorlage vorhanden. Sie werden im Azure-Portal jedoch als Teil einer Konfiguration der Bezeichnung angezeigt, die Schutzeinstellungen für einen Cloud-Schlüssel enthält. Sie können stets überprüfen, über welche Vorlagen Ihr Mandant verfügt, indem Sie [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) aus dem [AADRM-PowerShell-Modul](administer-powershell.md) ausführen.
>
>Sie können Vorlagen manuell konvertieren und diese bei Bedarf umbenennen, so wie unter [Konvertieren von Vorlagen in Bezeichnungen](#to-convert-templates-to-labels) beschrieben. Wenn Ihre Azure Information Protection-Standardrichtlinie kürzlich erstellt und der Azure Rights Management-Dienst für Ihren Mandanten zu diesem Zeitpunkt aktiviert wurde, werden sie automatisch konvertiert.

Vorlagen, die archiviert werden, werden auf dem Blatt **Azure Information Protection: Bezeichnungen** als nicht verfügbar angezeigt. Diese Vorlagen können nicht für Bezeichnungen ausgewählt werden, aber sie können zu Bezeichnungen konvertiert werden.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Überlegungen zu Vorlagen im Azure-Portal

Bevor Sie diese Vorlagen bearbeiten oder zu Bezeichnungen konvertieren, stellen Sie sicher, dass Sie die folgenden Änderungen und Überlegungen zur Kenntnis genommen haben. Aufgrund der Implementierungsänderungen ist die folgende Liste besonders wichtig, falls Sie zuvor Vorlagen im klassischen Azure-Portal verwaltet haben.

- Nachdem Sie eine Vorlage bearbeitet oder konvertiert und die Azure Information Protection-Richtlinie gespeichert haben, werden folgende Änderungen an den ursprünglichen [Nutzungsrechten](configure-usage-rights.md) vorgenommen. Falls erforderlich, können Sie individuelle Nutzungsrechte über das Azure-Portal hinzufügen oder entfernen. Alternativ können Sie auch PowerShell mit den Cmdlets [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) und [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) verwenden.
    
    - **Makros zulassen** (allgemeiner Name) wird automatisch hinzugefügt. Dieses Nutzungsrecht ist für die Azure Information Protection-Leiste in Office-Apps erforderlich.

- Die Einstellungen **Veröffentlicht** und **Archiviert** werden entsprechend als **Aktiviert** dargestellt: **Ein** und **Aktiviert**: **Aus** angezeigt **.** Legen Sie für Vorlagen, die beibehalten werden, aber nicht für Benutzer oder Dienste sichtbar sein sollen, **Aktiviert**: **Aus** fest.

- Sie können eine Vorlage im Azure-Portal weder kopieren noch löschen. Wenn die Vorlage zu einer Bezeichnung konvertiert wird, können Sie die Bezeichnung so konfigurieren, dass sie die Vorlage nicht mehr verwendet. Dies erreichen Sie, indem Sie für die Option **Berechtigungen für Dokumente und E-Mails mit Bezeichnung festlegen** **Nicht konfiguriert** auswählen. Alternativ können Sie die Bezeichnung löschen. In beiden Szenarios wird die Vorlage jedoch nicht gelöscht und bleibt aktiviert.
    
    Sie können nun die Vorlage mithilfe des PowerShell-Cmdlets [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) löschen. Sie können dieses PowerShell-Cmdlet auch für Vorlagen verwenden, die nicht zu Bezeichnungen konvertiert werden. Es wird allerdings in der Regel empfohlen, keine Vorlagen zu löschen, denn dadurch wird sichergestellt, dass zuvor geschützte Inhalte geöffnet und wie gewünscht verwendet werden können. Als bewährte Methode wird empfohlen, Vorlagen nur zu löschen, wenn Sie sicher sind, dass sie nicht zum Schützen von Dokumenten oder E-Mails in der Produktion verwendet wurden. Als Vorsichtsmaßnahme sollten Sie zuerst die Vorlage als Sicherung mithilfe des [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)-Cmdlets exportieren. 

- Wenn Sie derzeit eine Abteilungsvorlage bearbeiten und speichern, wird die Bereichskonfiguration entfernt. Eine bereichsbezogene Vorlage entspricht in der Azure Information Protection-Richtlinie einer [bereichsbezogenen Richtlinie](configure-policy-scope.md). Wenn Sie die Vorlage in eine Bezeichnung konvertieren, können Sie einen vorhandenen Bereich auswählen.
    
    Darüber hinaus können Sie die Anwendungskompatibilitätseinstellung für eine Abteilungsvorlage nicht über das Azure-Portal festlegen. Falls erforderlich, können Sie die Einstellung für Anwendungskompatibilität durch das Cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) und den Parameter *EnableInLegacyApps* festlegen.

- Wenn Sie eine Vorlage zu einer Bezeichnung konvertieren oder mit einer verknüpfen, kann sie nicht länger von anderen Bezeichnungen verwendet werden. Darüber hinaus wird diese Vorlage nicht mehr im Abschnitt **Protection Templates** (Schutzvorlagen) angezeigt. 

- Sie erstellen keine neue Vorlage über den Abschnitt **Protection Templates** (Schutzvorlagen). Sie erstellen stattdessen eine Bezeichnung, die die Einstellung **Schützen** aufweist, und konfigurieren die Nutzungsrechte und -einstellungen auf dem Blatt **Schutz**. Vollständige Anweisungen finden Sie unter [Erstellen einer neuen Vorlage](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Konfigurieren von Vorlagen in der Azure Information Protection-Richtlinie

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection: Bezeichnungen**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Erweitern Sie auf dem Blatt **Azure Information Protection - Bezeichnungen** den Eintrag **Schutzvorlagen**, und suchen Sie anschließend nach der zu konfigurierenden Vorlage.
    
3. Wählen Sie die Vorlage aus. Auf dem Blatt **Bezeichnung** können Sie ggf. den Vorlagennamen und die Beschreibung ändern, indem Sie bei Bedarf den **Anzeigename für Bezeichnung** und die **Beschreibung** bearbeiten. Wählen Sie dann **Schutz** mit dem Wert **Azure (cloud key)** (Azure (Cloud-Schlüssel)) aus, um das Blatt **Schutz** zu öffnen.

4. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren der Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.
    
> [!NOTE]
> Sie können eine Vorlage auch bearbeiten, indem Sie die Schaltfläche **Vorlage bearbeiten** auf dem Blatt **Schutz** verwenden, wenn Sie eine Bezeichnung so konfiguriert haben, dass eine vordefinierte Vorlage verwendet wird. Vorausgesetzt, dass keine andere Bezeichnung die ausgewählte Vorlage verwendet, konvertiert diese Schaltfläche die Vorlage in eine Bezeichnung, und Sie gelangen zu Schritt 5. Weitere Informationen darüber, was beim Konvertieren von Vorlagen zu Bezeichnungen geschieht, finden Sie im nächsten Abschnitt.

## <a name="to-convert-templates-to-labels"></a>Konvertieren von Vorlagen in Bezeichnungen

Bei einem Abonnement, das Klassifizierung, Bezeichnung und Schutz umfasst, können Sie eine Vorlage in eine Bezeichnung konvertieren. Wenn Sie eine Vorlage konvertieren, wird die ursprüngliche Vorlage beibehalten, wird jedoch im Azure-Portal als in einer neuen Bezeichnung enthalten angezeigt.

Wenn Sie beispielsweise eine Bezeichnung mit dem Namen **Marketing** konvertieren, die der Marketinggruppe Nutzungsrechte gewährt, wird sie im Azure-Portal nun als Bezeichnung mit dem Namen **Marketing** angezeigt, die dieselben Schutzeinstellungen aufweist. Wenn Sie die Schutzeinstellungen in dieser neu erstellten Bezeichnung ändern, ändern Sie sie in der Vorlage. Die neuen Schutzeinstellungen werden bei der nächsten Aktualisierung der Vorlage auf Benutzer oder Dienste angewendet, die diese Vorlage verwenden. 

Es ist nicht erforderlich, alle Vorlagen in Bezeichnungen zu konvertieren, aber falls Sie es tun sollten, werden die Schutzeinstellungen vollständig in die gesamte Funktionalität der Bezeichnungen integriert, sodass Sie die Einstellungen nicht separat verwalten müssen.

Um eine Vorlage in eine Bezeichnung zu konvertieren, klicken Sie mit der rechten Maustaste auf die Vorlage und wählen Sie **In Bezeichnung konvertieren** aus. Wählen Sie diese Option wahlweise über das Kontextmenü aus. 

Sie können eine Vorlage auch zu einer Bezeichnung konvertieren, wenn Sie eine Bezeichnung für den Schutz und eine vordefinierte Vorlage konfigurieren, indem Sie die Schaltfläche **Vorlage bearbeiten** verwenden. 

Bei der Konvertierung einer Vorlage in eine Bezeichnung:

- Der Name der Vorlage wird in den neuen Bezeichnungsnamen konvertiert, während die Beschreibung der Vorlage in eine QuickInfo für die Bezeichnung konvertiert wird. 

- Wenn der Status der Vorlage veröffentlicht wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Ein** festgelegt. Diese wird Benutzern nun angezeigt, wenn Sie die Azure Information Protection-Richtlinie das nächste Mal veröffentlichen. Wenn der Status der Vorlage archiviert wurde, wird diese Einstellung für die Bezeichnung auf **Aktiviert**: **Aus** festgelegt, und die Bezeichnung wird dem Benutzer nicht als verfügbare Bezeichnung angezeigt.

- Die Schutzeinstellungen werden beibehalten. Sie können diese bei Bedarf bearbeiten und auch andere Bezeichnungseinstellungen wie visuelle Kennzeichnungen und Bedingungen hinzufügen.

- Die ursprüngliche Vorlage wird nicht mehr unter **Protection templates** (Schutzvorlagen) angezeigt und kann nicht als eine vordefinierte Vorlage ausgewählt werden, wenn Sie den Schutz für eine Bezeichnung konfigurieren. Um diese Vorlage im Azure-Portal zu bearbeiten, bearbeiten Sie nun die Bezeichnung, die bei der Konvertierung der Vorlage erstellt wurde. Die Vorlage ist weiterhin für den Azure Rights Management-Dienst verfügbar und kann nach wie vor mit [PowerShell-Befehlen](administer-powershell.md) verwaltet werden.  

## <a name="to-create-a-new-template"></a>So erstellen Sie eine neue Vorlage

Wenn Sie eine neue Bezeichnung mit der Schutzeinstellung **Azure (Cloud-Schlüssel)** erstellen, wird hierdurch im Hintergrund eine neue benutzerdefinierte Vorlage erstellt. Auf diese kann dann über Dienste und Anwendungen, die mit Rights Management-Vorlagen integriert werden, zugegriffen werden.

1. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Klicken Sie auf dem Blatt **Azure Information Protection - Bezeichnungen** auf **Neue Bezeichnung hinzufügen**.

2. Behalten Sie auf dem Blatt **Bezeichnung** die Standardeinstellung **Aktiviert**: **Ein** bei, und geben Sie dann einen Bezeichnungsnamen und eine Beschreibung für den Vorlagennamen und die Beschreibung ein.

3. Wählen Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** die Optionen **Schützen** und dann **Schutz** aus:
    
     ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](./media/info-protect-protection-bar-configured.png)

4. Auf dem Blatt **Schutz** können Sie die Berechtigungen, den Inhaltsablauf und die Offlinezugriffseinstellungen ändern. Weitere Informationen zum Konfigurieren dieser Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK**, um Ihre Änderungen beizubehalten, und klicken Sie dann auf dem Blatt **Bezeichnung** auf **Speichern**.
    
    Auf dem Blatt **Azure Information Protection: Bezeichnungen** können Sie jetzt Ihre neue Bezeichnung sehen, die mit der Spalte **Schutz** angezeigt wird. Dies bedeutet, dass sie Schutzeinstellungen enthält. Diese Schutzeinstellungen werden Anwendungen und Diensten, die den Azure Rights Management-Dienst unterstützen, als Vorlagen angezeigt.
    
    Obwohl die Bezeichnung aktiviert ist, wird die Vorlage standardmäßig archiviert. Damit Anwendungen und Dienste die Vorlage zum Schützen von Dokumenten und E-Mails verwenden können, führen Sie den letzten Schritt zum Veröffentlichen der Vorlage aus.

5. Wählen Sie in der Menüoption **Klassifizierungen** > **Richtlinien** die Richtlinie aus, die die neuen Schutzeinstellungen enthalten soll. Wählen Sie dann **Bezeichnungen hinzufügen oder entfernen** aus. Wählen Sie auf dem Blatt **Richtlinie: Bezeichnungen hinzufügen oder entfernen** die neu erstellte Bezeichnung aus, die Ihre Schutzeinstellungen enthält, und klicken Sie erst auf **OK** und dann auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

Es kann bis zu 15 Minuten in Anspruch nehmen, bis ein Computer, auf dem der Azure Information Protection-Client ausgeführt wird, diese geänderten Einstellungen abrufen kann. Informationen zum Herunterladen und Aktualisieren von Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

Alle Vorgänge, die Sie im klassischen Azure-Portal zum Erstellen und Verwalten von Vorlagen konfigurieren können, können Sie auch mithilfe von PowerShell durchführen. PowerShell bietet darüber hinaus weitere Optionen, die nicht im Portal verfügbar sind. Weitere Informationen finden Sie in der [PowerShell-Referenz zum Schutz von Vorlagen](configure-templates-with-powershell.md). 

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

