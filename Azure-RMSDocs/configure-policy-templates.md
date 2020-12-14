---
title: Konfigurieren und Verwalten von Vorlagen für Azure Information Protection – AIP
description: Konfigurieren und Verwalten von Schutz Vorlagen (auch als Rights Management-Vorlagen bezeichnet) aus dem Azure-Portal.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 09/16/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.subservice: aiplabels
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: c2ce080c290bf3e2b04cc433e9347e3a1e074746
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97383056"
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Konfigurieren und Verwalten von Vorlagen für Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden [Sie unter Informationen zu Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) und [Einschränken des Zugriffs auf Inhalte mithilfe von Verschlüsselung in sensiblen Bezeichnungen](/microsoft-365/compliance/encryption-sensitivity-labels) aus der Microsoft 365-Dokumentation. *

> [!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>

Schutzvorlagen, auch als Rights Management-Vorlagen bekannt, sind eine Reihe von vom Administrator definierten Schutzeinstellungen für Azure Information Protection. Diese Einstellungen enthalten Ihre ausgewählten [Nutzungsrechte](configure-usage-rights.md) für autorisierte Benutzer sowie Zugriffssteuerungen für den Ablauf und den Offlinezugriff. Diese Vorlagen sind in der Azure Information Protection-Richtlinie integriert. 

**Wenn Sie über ein Abonnement verfügen, das Klassifizierung, Bezeichnung und Schutz umfasst (Azure Information Protection P1 oder P2)**:

- Vorlagen, die nicht in ihre Bezeichnungen für Ihren Mandanten integriert sind, werden im Bereich " **Schutz Vorlagen** " angezeigt, nachdem ihre Bezeichnungen im Bereich " **Azure Information Protection-Bezeichnungen** " angezeigt wurden. Um zu diesem Bereich zu navigieren, wählen Sie die Menüoption **Klassifizierungen**  >  **Bezeichnungen** aus. Sie können diese Vorlagen in Bezeichnungen konvertieren, oder Sie können eine Verknüpfung mit ihnen herstellen, wenn Sie den Schutz ihrer Bezeichnungen konfigurieren. 

**Wenn Sie über ein Abonnement verfügen, das nur Schutz umfasst (ein Microsoft 365 Abonnement, das den Azure Rights Management-Dienst umfasst)**:

- Vorlagen für Ihren Mandanten werden im Bereich " **Schutz Vorlagen** " im Bereich " **Azure Information Protection-Bezeichnungen** " angezeigt. Um zu diesem Bereich zu navigieren, wählen Sie die Menüoption **Klassifizierungen**  >  **Bezeichnungen** aus. Es werden keine Bezeichnungen angezeigt. Darüber hinaus sehen Sie Konfigurationseinstellungen, die für die Klassifizierung und die Bezeichnung spezifisch sind. Diese Einstellungen haben jedoch entweder keinen Einfluss auf Ihre Vorlagen oder können nicht konfiguriert werden. 

>[!NOTE]
>In einigen Anwendungen und Diensten wird möglicherweise die Option [Nicht weiterleiten](configure-usage-rights.md#do-not-forward-option-for-emails) und [Nur verschlüsseln](configure-usage-rights.md#encrypt-only-option-for-emails) (oder **Verschlüsseln**) als Vorlage angezeigt. Dabei handelt es sich nicht um Vorlagen, die Sie bearbeiten oder löschen können, sondern vielmehr um Optionen, die standardmäßig mit dem Exchange-Dienst geliefert werden.

## <a name="default-templates"></a>Standardvorlagen

Wenn Sie Ihr Abonnement für Azure Information Protection oder für ein Microsoft 365 Abonnement erwerben, das den Azure-Rights Management Dienst umfasst, werden automatisch zwei Standardvorlagen für Ihren Mandanten erstellt. Diese Vorlagen gewähren nur autorisierten Benutzern in Ihrer Organisation Zugriff. Wenn diese Vorlagen erstellt werden, verfügen Sie über die Berechtigungen, die in der Dokumentation [Konfigurieren von Nutzungsrechten für Azure Information Protection](configure-usage-rights.md#rights-included-in-the-default-templates) aufgeführt sind.

Zusätzlich werden die Vorlagen so konfiguriert, dass sie einen Offlinezugriff für sieben Tage zulassen und kein Ablaufdatum haben.

>[!NOTE]
> Sie können diese Einstellungen und die Namen und Beschreibungen der Standardvorlagen ändern. Dies war mit dem klassischen Azure-Portal nicht möglich und wird auch weiterhin nicht für PowerShell unterstützt.

Diese Standardvorlagen erleichtern es Ihnen und anderen Personen, sofort mit dem Schutz sensibler Daten Ihrer Organisation zu beginnen. Diese Vorlagen können mit Azure Information Protection-Bezeichnungen oder alleine mit [Anwendungen und Diensten](applications-support.md) verwendet werden, die Rights Management-Vorlagen verwenden können.

Sie können auch eigene, benutzerdefinierte Vorlagen erstellen. Sie benötigen wahrscheinlich nur einige Vorlagen, aber in Azure ist es möglich, maximal 500 benutzerdefinierte Vorlagen zu speichern.


### <a name="default-template-names"></a>Namen für die Standardvorlage

Wenn Sie Ihr Abonnement vor Kurzem erworben haben, werden Ihre Standardvorlagen mit folgenden Namen erstellt:

- **Vertraulich \ alle Mitarbeiter**

- **Streng vertraulich \ alle Mitarbeiter**

Wenn Sie Ihr Abonnement vor einiger Zeit erworben haben, werden Ihre Standardvorlagen möglicherweise mit den folgenden Namen erstellt:

- **\<organization name> -Vertraulich**

- **\<organization name> -Nur vertrauliche Ansicht** 

Sie können diese Standardvorlagen umbenennen (und neu konfigurieren), wenn Sie das Azure-Portal verwenden.

>[!NOTE]
>Wenn Ihre Standardvorlagen im Bereich " **Azure Information Protection-Bezeichnungen** " nicht angezeigt werden, werden Sie in Bezeichnungen konvertiert oder mit einer Bezeichnung verknüpft. Diese sind noch immer als Vorlage vorhanden. Sie werden im Azure-Portal jedoch als Teil einer Konfiguration der Bezeichnung angezeigt, die Schutzeinstellungen für einen Cloud-Schlüssel enthält. Sie können jederzeit überprüfen, welche Vorlagen Ihr Mandant hat, indem Sie " [Get-aipservicetemplate](/powershell/module/aipservice/get-aipservicetemplate) " aus dem [PowerShell-Modul von aipservice](administer-powershell.md)ausführen.
>
>Sie können Vorlagen manuell konvertieren (siehe weiter unten unter [Konvertieren von Vorlagen in Bezeichnungen](#to-convert-templates-to-labels)) und bei Bedarf umbenennen. Sie werden automatisch konvertiert, wenn Ihre Azure Information Protection-Standardrichtlinie vor Kurzem erstellt und der Azure Rights Management-Dienst für Ihren Mandanten zu diesem Zeitpunkt aktiviert wurde.

Vorlagen, die archiviert werden, werden im Bereich **Azure Information Protection-Bezeichnungen** als nicht verfügbar angezeigt. Diese Vorlagen können nicht für Bezeichnungen ausgewählt, können aber in Bezeichnungen konvertiert werden.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Überlegungen zu Vorlagen im Azure-Portal

Bevor Sie diese Vorlagen bearbeiten oder in Bezeichnungen konvertieren, stellen Sie sicher, dass Sie die folgenden Änderungen und Überlegungen zur Kenntnis genommen haben. Aufgrund der Implementierungsänderungen ist die folgende Liste besonders wichtig, falls Sie zuvor Vorlagen im klassischen Azure-Portal verwaltet haben.

- Nachdem Sie eine Vorlage bearbeitet oder konvertiert und die Azure Information Protection-Richtlinie gespeichert haben, werden folgende Änderungen an den ursprünglichen [Nutzungsrechten](configure-usage-rights.md) vorgenommen. Bei Bedarf können Sie einzelne Nutzungsrechte mithilfe des Azure-Portals hinzufügen oder entfernen. Oder verwenden Sie PowerShell mit den Cmdlets [New-aipservicerightiondefinition](/powershell/module/aipservice/new-aipservicerightsdefinition) und [Set-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty) .
    
    - **Makros zulassen** (allgemeiner Name) wird automatisch hinzugefügt. Dieses Nutzungsrecht ist für die Azure Information Protection-Leiste in Office-Apps erforderlich.

- **Veröffentlichte** und **Archivierte** Einstellungen werden als **aktiviert** angezeigt: **on** und **aktiviert**: **Off** im Bereich **Bezeichnung** . Legen Sie für Vorlagen, die beibehalten werden, aber nicht für Benutzer oder Dienste sichtbar sein sollen, **Aktiviert**: **Aus** fest.

- Sie können eine Vorlage im Azure-Portal nicht kopieren oder löschen. Wenn die Vorlage in eine Bezeichnung konvertiert wird, können Sie die Bezeichnung so konfigurieren, dass sie die Vorlage nicht mehr verwendet. Legen Sie dafür für **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** die Option **Nicht konfiguriert** fest. Sie können die Bezeichnung auch löschen. In beiden Szenarien wird die Vorlage jedoch nicht gelöscht und bleibt archiviert.
    
    Das Löschen von Vorlagen mit dem PowerShell-Cmdlet " [Remove-aipservicetemplate](/powershell/module/aipservice/remove-aipservicetemplate) " ist **permanent**. Sie können dieses PowerShell-Cmdlet auch für Vorlagen verwenden, die nicht in Bezeichnungen konvertiert werden. Es wird allerdings in der Regel empfohlen, keine Vorlagen zu löschen, denn dadurch wird sichergestellt, dass zuvor geschützte Inhalte geöffnet und wie gewünscht verwendet werden können. Als bewährte Methode wird empfohlen, Vorlagen nur zu löschen, wenn Sie sicher sind, dass sie nicht zum Schützen von Dokumenten oder E-Mails in der Produktion verwendet wurden. Als Vorsichtsmaßnahme vor dem permanenten Löschen einer Vorlage mithilfe von PowerShell empfiehlt es sich, die Vorlage mithilfe des Cmdlets [Export-aipservicetemplate](/powershell/module/aipservice/export-aipservicetemplate) als Sicherung zu exportieren. 

- Wenn Sie eine Abteilungsvorlage bearbeiten und speichern, wird derzeit die Bereichskonfiguration entfernt. Eine bereichsbezogene Vorlage entspricht in der Azure Information Protection-Richtlinie einer [bereichsbezogenen Richtlinie](configure-policy-scope.md). Wenn Sie die Vorlage in eine Bezeichnung konvertieren, können Sie einen vorhandenen Bereich auswählen.
    
    Darüber hinaus können Sie die Anwendungskompatibilitätseinstellung für eine Abteilungsvorlage nicht über das Azure-Portal festlegen. Falls erforderlich, können Sie diese Einstellung für die Anwendungs Kompatibilität mithilfe des Cmdlets [Set-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty) und des Parameters *enableinlegacyapps* festlegen.

- Wenn Sie eine Vorlage in eine Bezeichnung konvertieren oder mit einer Bezeichnung verknüpfen, kann sie nicht länger von anderen Bezeichnungen verwendet werden. Darüber hinaus wird diese Vorlage nicht mehr im Abschnitt **Schutzvorlagen** angezeigt. 

- Sie erstellen keine neue Vorlage im Abschnitt **Schutzvorlagen**. Erstellen Sie stattdessen eine Bezeichnung, die die Einstellung **schützen** aufweist, und konfigurieren Sie die Nutzungsrechte und-Einstellungen im Bereich **Schutz** . Vollständige Anweisungen finden Sie unter [So erstellen Sie eine neue Vorlage](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>So konfigurieren Sie die Vorlagen in der Azure Information Protection-Richtlinie

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich am Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies nicht bereits getan haben. Navigieren Sie dann zum Bereich **Azure Information Protection-Bezeichnungen** .
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Über die Menüoption **Klassifizierungen**  >  **Bezeichnungen** : Erweitern Sie im Bereich **Azure Information Protection-Bezeichnungen** den Knoten **Schutz Vorlagen**, und suchen Sie dann die Vorlage, die Sie konfigurieren möchten.
    
3. Wählen Sie die Vorlage aus. im Bereich **Bezeichnung** können Sie ggf. den Vorlagen Namen und die Beschreibung ändern, indem Sie den **anzeigen Amen** und die **Beschreibung** der Bezeichnung bearbeiten. Wählen Sie dann **Schutz** mit dem Wert **Azure (cloudschlüssel)** aus, um den **Schutz** Bereich zu öffnen.

4. Im Bereich **Schutz** können Sie die Berechtigungen, den Inhalts Ablauf und die Offline Zugriffs Einstellungen ändern. Weitere Informationen zum Konfigurieren der Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK** , um Ihre Änderungen beizubehalten, und klicken Sie im Bereich **Bezeichnung** auf **Speichern**.
    
> [!NOTE]
> Sie können eine Vorlage auch bearbeiten, indem Sie die Schaltfläche **Vorlage bearbeiten** im Bereich **Schutz** verwenden, wenn Sie eine Bezeichnung für die Verwendung einer vordefinierten Vorlage konfiguriert haben. Sofern keine andere Bezeichnung die ausgewählte Vorlage verwendet, wird mit dieser Schaltfläche die Vorlage in eine Bezeichnung konvertiert, und Sie gelangen zu Schritt 5. Weitere Informationen dazu, was beim Konvertieren von Bezeichnungen in Vorlagen geschieht, finden Sie im nächsten Abschnitt.

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

Vorlagen können über das Portal oder mithilfe von PowerShell erstellt werden. 

### <a name="template-creation-using-powershell"></a>Vorlagen Erstellung mithilfe von PowerShell

Zum Erstellen einer neuen Schutz Vorlage mithilfe von PowerShell mit dem angegebenen Namen, der Beschreibung, der Richtlinie und der gewünschten Statuseinstellung verwenden Sie das Cmdlet [Add-aipservicetemplate](/powershell/module/aipservice/add-aipservicetemplate) . 


### <a name="template-creation-using-the-portal"></a>Vorlagen Erstellung über das Portal

Wenn Sie eine neue Bezeichnung mithilfe des Portals mit der Schutz Einstellung **Azure (Cloud Key)** erstellen, wird mit dieser Aktion eine neue benutzerdefinierte Vorlage erstellt, auf die von Diensten und Anwendungen zugegriffen werden kann, die in Rights Management Vorlagen integriert werden.

1. Über die Menüoption **Klassifizierungen**  >  **Bezeichnungen** : Wählen Sie im Bereich **Azure Information Protection-Bezeichnungen** die Option **neue Bezeichnung hinzufügen** aus.

2. Behalten Sie im Bereich **Bezeichnung** die Standardeinstellung **aktiviert** **: ein**, und geben Sie dann einen Bezeichnungs Namen und eine Beschreibung für den Vorlagen Namen und die Beschreibung ein.

3. Wählen Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** die Optionen **Schützen** und dann **Schutz** aus:
    
     ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](./media/info-protect-protection-bar-configured.png)

4. Im Bereich **Schutz** können Sie die Berechtigungen, den Inhalts Ablauf und die Offline Zugriffs Einstellungen ändern. Weitere Informationen zum Konfigurieren dieser Schutzeinstellungen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md).
    
    Klicken Sie auf **OK** , um Ihre Änderungen beizubehalten, und klicken Sie im Bereich **Bezeichnung** auf **Speichern**.
    
    Im Bereich **Azure Information Protection-Bezeichnungen** sehen Sie nun, dass Ihre neue Bezeichnung mit der Spalte " **Schutz** " angezeigt wird, um anzugeben, dass Sie Schutzeinstellungen enthält. Diese Schutzeinstellungen werden Anwendungen und Diensten, die den Azure Rights Management-Dienst unterstützen, als Vorlagen angezeigt.
    
    Obwohl die Bezeichnung aktiviert ist, wird die Vorlage standardmäßig archiviert. Damit Anwendungen und Dienste die Vorlage zum Schützen von Dokumenten und E-Mails verwenden können, führen Sie den letzten Schritt zum Veröffentlichen der Vorlage aus.

5. Wählen Sie in der Menüoption **Klassifizierungen**  >  **Richtlinien** die Richtlinie aus, die die neuen Schutzeinstellungen enthalten soll. Wählen Sie dann **Bezeichnungen hinzufügen oder entfernen** aus. Wählen Sie im Bereich **Richtlinie: Bezeichnungen hinzufügen oder entfernen** die neu erstellte Bezeichnung aus, die die Schutzeinstellungen enthält, wählen Sie **OK** aus, und klicken Sie dann auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

Es kann bis zu 15 Minuten in Anspruch nehmen, bis ein Computer, auf dem der Azure Information Protection-Client ausgeführt wird, diese geänderten Einstellungen abrufen kann. Informationen dazu, wie Computer und Dienste Vorlagen herunterladen und aktualisieren, finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

Alle Vorgänge, die Sie im Azure-Portal zum Erstellen und Verwalten von Vorlagen konfigurieren können, können Sie auch mithilfe von PowerShell durchführen. PowerShell bietet darüber hinaus weitere Optionen, die nicht im Portal verfügbar sind. Weitere Informationen finden Sie unter [PowerShell-Referenz für benutzerdefinierte Vorlagen](configure-templates-with-powershell.md). 

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).