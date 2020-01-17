---
title: Dokumentenverfolgung für Azure Information Protection
description: Anweisungen und Informationen für Administratoren zum Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.subservice: doctrack
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 9a04156d41bd062f4f182fd4133d938c189157e5
ms.sourcegitcommit: ad3e55f8dfccf1bc263364990c1420459c78423b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76117832"
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>Administratorhandbuch: Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


Wenn Sie ein [Abonnement haben, das die Dokumentenverfolgung unterstützt](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), ist die Website für die Dokumentnachverfolgung standardmäßig für alle Benutzer in Ihrer Organisation aktiviert. Durch die Dokumentkontrolle erhalten Benutzer und Administratoren Informationen darüber, wann auf ein geschütztes Dokument zugegriffen wird und ob ein nachverfolgtes Dokument ggf. gesperrt werden kann.

## <a name="using-powershell-to-manage-the-document-tracking-site"></a>Verwalten der Website für die Dokumentnachverfolgung mithilfe von PowerShell

In den folgenden Abschnitten finden Sie Informationen dazu, wie Sie die Website für die Dokumentnachverfolgung mithilfe von PowerShell verwalten können. Installationsanweisungen für das PowerShell-Modul finden Sie unter [Installieren des aipservice-PowerShell-Moduls](../install-powershell.md).

Weitere Informationen zu den einzelnen Cmdlets finden Sie unter den angegebenen Links.

### <a name="privacy-controls-for-your-document-tracking-site"></a>Datenschutzkontrollen für Ihre Website für die Dokumentnachverfolgung

Wenn die Anzeige aller Informationen zur Dokument Nachverfolgung in Ihrer Organisation aufgrund von Datenschutzanforderungen nicht zulässig ist, können Sie die dokumentenverfolgung mithilfe des Cmdlets " [Deaktivieren-aipservicedocumenttrackingfeature](/powershell/module/aipservice/disable-aipservicedocumenttrackingfeature) " deaktivieren. 

Dieses Cmdlet deaktiviert den Zugriff auf die Website für die Dokumentnachverfolgung, damit keine Benutzer in Ihrer Organisation die von ihnen geschützten Dokumente nachverfolgen oder den Zugriff auf diese widerrufen können. Sie können die Dokument Nachverfolgung jederzeit mithilfe von [enable-aipservicedocumenttrackingfeature](/powershell/module/aipservice/enable-aipservicedocumenttrackingfeature)wieder aktivieren und mithilfe von [Get-aipservicedocumenttrackingfeature](/powershell/module/aipservice/get-aipservicedocumenttrackingfeature)überprüfen, ob die Dokument Nachverfolgung derzeit aktiviert oder deaktiviert ist. 

Wenn die Website für die Dokumentnachverfolgung aktiviert ist, werden standardmäßig Informationen angezeigt, wie z.B. E-Mail-Adressen der Personen, die auf geschützte Dokumente zugegriffen haben, wann diese Benutzer versucht haben, darauf zuzugreifen, sowie deren Standort. Diese Art von Informationen kann hilfreich sein, um festzulegen, wie die freigegebenen Dokumente verwendet und ob sie widerrufen werden sollen, wenn verdächtige Aktivitäten festgestellt werden. Aus Datenschutzgründen müssen diese Benutzerinformationen allerdings u.U. für einige oder alle Benutzer deaktiviert werden. 

Wenn Sie über Benutzer verfügen, für die diese Aktivität von anderen Benutzern nicht nachverfolgt werden soll, fügen Sie Sie einer in Azure AD gespeicherten Gruppe hinzu, und geben Sie diese Gruppe mit dem Cmdlet [Set-aipservicedonottrackusergroup](/powershell/module/aipservice/Set-AipServiceDoNotTrackUserGroup) an. Wenn Sie dieses Cmdlet ausführen, dürfen Sie nur eine einzelne Gruppe angeben. Allerdings kann die Gruppe verschachtelte Gruppen enthalten. 

Für diese Gruppenmitglieder wird anderen Benutzern keine Aktivität auf der Website für die Dokumentnachverfolgung angezeigt, wenn die Aktivität zu Dokumenten gehört, die für sie freigegeben wurden. Darüber hinaus werden keine E-Mail-Benachrichtigungen an den Benutzer gesendet, der das Dokument freigegeben hat.

Wenn Sie diese Konfiguration verwenden, können alle Benutzer weiterhin die Website für die Dokumentnachverfolgung verwenden und den Zugriff auf die von ihnen geschützten Dokumente widerrufen. Es werden jedoch keine Aktivitäten für die Benutzer angezeigt, die Sie mit dem Cmdlet "Set-aipservicedonottrackusergroup" angegeben haben.

Diese Einstellung gilt nur für Endbenutzer. Administratoren für Azure Information Protection können die Aktivitäten aller Benutzer immer nachverfolgen, auch wenn diese Benutzer mithilfe von "Set-aipservicedonottrackusergroup" angegeben werden. Weitere Informationen dazu, wie Administratoren Dokumente für Benutzer nachverfolgen können, finden Sie im Abschnitt [Nachverfolgen und Sperren von Dokumenten für Benutzer](#tracking-and-revoking-documents-for-users).


### <a name="logging-information-from-the-document-tracking-site"></a>Protokollieren von Informationen aus der Website für die Dokumentnachverfolgung

Sie können die folgenden Cmdlets verwenden, um Protokollierungs Informationen von der Website für die Dokument Nachverfolgung herunterzuladen:

- [Get-AipServiceTrackingLog](/powershell/module/aipservice/Get-AipServiceTrackingLog)
    
    Dieses Cmdlet gibt Informationen zu geschützten Dokumenten für einen angegebenen Benutzer zurück, der Dokumente geschützt hat (Rights Management-Aussteller) oder der auf geschützte Dokumente zugegriffen hat. Mithilfe dieses Cmdlets können Sie die Frage beantworten, auf welche geschützten Dokumente ein bestimmter Benutzer zugegriffen und welche er nachverfolgt hat.

- [Get-AipServiceDocumentLog](/powershell/module/aipservice/Get-AipServiceDocumentLog)
    
    Dieses Cmdlet gibt Informationen zum Schutz der nachverfolgten Dokumente für einen bestimmten Benutzer zurück (Rights Management-Aussteller), falls dieser Benutzer Dokumente geschützt hat, Rights Management-Besitzer von Dokumenten war oder Dokumente geschützt hat, die so konfiguriert waren, dass dem Benutzer direkter Zugriff gewährt werden sollte. Mithilfe dieses Cmdlets können Sie die Frage beantworten, wie Dokumente für einen bestimmten Benutzer geschützt werden.

## <a name="destination-urls-used-by-the-document-tracking-site"></a>Von der Website für die Dokumentnachverfolgung verwendete Ziel-URLs

Die folgenden URLs werden für die dokumentenverfolgung verwendet und müssen auf allen Geräten und Diensten zwischen den Clients, auf denen der Azure Information Protection Client und das Internet ausgeführt werden, zulässig sein. Beispiel: Fügen Sie diese URLs zu Firewalls oder zu Ihren vertrauenswürdigen Websites hinzu, wenn Sie Internet Explorer mit erhöhter Sicherheit verwenden.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Dies sind die Standard-URLs für den Azure Rights Management-Dienst mit Ausnahme der URL virtualearth.net, die für Bing-Karten zur Anzeige des Benutzerstandorts verwendet wird.

## <a name="tracking-and-revoking-documents-for-users"></a>Nachverfolgen und Sperren von Dokumenten für Benutzer

Wenn sich Benutzer auf der Website zur Dokumentenverfolgung anmelden, können sie mithilfe des Azure Information Protection-Clients Dokumente nachverfolgen und sperren, die sie freigegeben haben. Wenn Sie sich für Ihren Mandanten als globaler Azure AD-Administrator anmelden, können Sie auf das Administratorsymbol klicken, um in den Administratormodus zu wechseln. Dieser Modus für die Website zum Nachverfolgen von Dokumenten wird von anderen Administratorrollen nicht unterstützt. 

![Adminsymbol auf der Website zur Dokumentenverfolgung](../media/tracking-site-admin-icon.png)

Im Administratormodus können Sie die Dokumente anzeigen, die von den Benutzern in Ihrer Organisation zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt wurden.

> [!NOTE] 
> Wenn Sie dieses Symbol nicht sehen, obwohl Sie über globale Administratorrechte verfügen, liegt das daran, dass Sie selbst noch keine Dokumente freigegeben haben. Verwenden Sie in diesem Fall die folgende URL, um auf die Website zur Dokumentenverfolgung zu gelangen: https://portal.azurerms.com/#/admin

Aktionen, die Sie im Administratormodus durchführen, werden geprüft und in Verwendungsprotokolldateien protokolliert, und Sie müssen Ihre Einwilligung geben, um den Vorgang fortzusetzen. Weitere Informationen über diese Protokollierung finden Sie im nächsten Abschnitt.

Wenn Sie sich im Administratormodus befinden, können Sie nach Benutzern oder Dokumenten suchen. Wenn Sie nach Benutzer suchen, können Sie alle Dokumente anzeigen, die vom angegebenen Benutzer zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt wurden. 

Wenn Sie nach Dokument suchen, können Sie alle Benutzer in Ihrer Organisation anzeigen, die dieses Dokument durch den Azure Information Protection-Client nachverfolgt haben. Sie können die Suchergebnisse näher betrachten, um die Dokumente zu überwachen, die Benutzer geschützt haben, und diese Dokumente, falls erforderlich, wieder zu sperren. 

Klicken Sie auf das **X** neben **Administratormodus beenden**, um den Administratormodus zu verlassen.

![Administratormodus auf der Website für die Dokumentenverfolgung beenden](../media/tracking-site-exit-admin-icon.png)

Eine Anleitung zur Verwendung der Website zur Dokumentnachverfolgung finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](client-track-revoke.md) im Benutzerhandbuch.

### <a name="using-powershell-to-register-labeled-documents-with-the-document-tracking-site"></a>Verwenden von PowerShell zum Registrieren von bezeichneten Dokumenten bei der Website zur Dokumentennachverfolgung

Zum Nachverfolgen und Widerrufen eines Dokuments muss es zunächst bei der Website zur Dokumentnachverfolgung registriert werden. Diese Aktion wird ausgeführt, wenn Benutzer bei Verwendung des Azure Information Protection-Clients im Datei-Explorer oder über ihre Office-Apps die Option **Track and revoke** (Verfolgen und widerrufen) auswählen.

Wenn Sie Dateien für Benutzer mit dem Cmdlet [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel) bezeichnen und schützen, können Sie den Parameter *EnableTracking* verwenden, um die Dateien bei der Website zur Dokumentnachverfolgung zu registrieren. Zum Beispiel:

    Set-AIPFileLabel -Path C:\Projects\ -LabelId ade72bf1-4714-4714-4714-a325f824c55a -EnableTracking

## <a name="usage-logging-for-the-document-tracking-site"></a>Verwendungsprotokollierung für die Website zur Dokumentnachverfolgung

Für die Dokumentnachverfolgung kommen zwei Felder in den Verwendungsprotokolldateien infrage: **AdminAction** und **ActingAsUser**.

**AdminAction** – Dieses Feld weist den Wert TRUE auf, wenn ein Administrator die Website zur Dokumentnachverfolgung im Administratormodus verwendet, z.B. um ein Dokument im Auftrag des Benutzers zu sperren oder um festzustellen, wann es freigegeben wurde. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer.

**ActingAsUser** – Wenn das Feld „AdminAction“ TRUE aufweist, enthält dieses Feld den Benutzernamen, in dessen Auftrag der Administrator als der gesuchte Benutzer oder Besitzer des Dokuments handelt. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer. 

Einige der Anforderungstypen protokollieren die Verwendungsweise der Website zur Dokumentnachverfolgung vonseiten der Benutzer und Administratoren. **RevokeAccess** ist beispielsweise der verwendete Anforderungstyp, wenn ein Benutzer oder Administrator im Auftrag eines Benutzers ein Dokument auf der Website zur Dokumentnachverfolgung gesperrt hat. Verwenden Sie diesen Anforderungstyp in Kombination mit dem AdminAction-Feld, um zu ermitteln, ob ein Benutzer sein eigenes Dokument gesperrt hat (AdminAction ist leer) oder ob der Administrator dies im Namen eines Benutzers getan hat (AdminAction ist TRUE).

Weitere Informationen zur Verwendungs Protokollierung finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](../log-analyze-usage.md)

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Website für die Dokumentenverfolgung für den Azure Information Protection-Client konfiguriert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

