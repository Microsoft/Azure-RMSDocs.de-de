---
title: Dokumentenverfolgung für Azure Information Protection
description: Anweisungen und Informationen für Administratoren zum Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 181183d701cb5fa4891be0aa3e0ea3028682bea7
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44150839"
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>Administratorhandbuch: Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Wenn Sie ein [Abonnement haben, das die Dokumentenverfolgung unterstützt](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), ist die Website für die Dokumentnachverfolgung standardmäßig für alle Benutzer in Ihrer Organisation aktiviert. Durch die Dokumentkontrolle erhalten Benutzer und Administratoren Informationen darüber, wann auf ein geschütztes Dokument zugegriffen wird und ob ein nachverfolgtes Dokument ggf. gesperrt werden kann.

## <a name="using-powershell-to-manage-the-document-tracking-site"></a>Verwalten der Website für die Dokumentnachverfolgung mithilfe von PowerShell

In den folgenden Abschnitten finden Sie Informationen dazu, wie Sie die Website für die Dokumentnachverfolgung mithilfe von PowerShell verwalten können. Installationsanweisungen für dieses PowerShell-Modul finden Sie unter [Installieren des AADRM-PowerShell-Moduls](../install-powershell.md). Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm –ListAvailable).Version`

Weitere Informationen zu den einzelnen Cmdlets finden Sie unter den angegebenen Links.

### <a name="privacy-controls-for-your-document-tracking-site"></a>Datenschutzkontrollen für Ihre Website für die Dokumentnachverfolgung

Wenn das Anzeigen aller Informationen zur Dokumentnachverfolgung in Ihrer Organisation aufgrund von Datenschutzanforderungen nicht zulässig ist, können Sie die Dokumentnachverfolgung mithilfe des Cmdlets [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature) deaktivieren. 

Dieses Cmdlet deaktiviert den Zugriff auf die Website für die Dokumentnachverfolgung, damit keine Benutzer in Ihrer Organisation die von ihnen geschützten Dokumente nachverfolgen oder den Zugriff auf diese widerrufen können. Sie können die Dokumentnachverfolgung jederzeit mit dem Cmdlet [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) wieder aktivieren und mit [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature) überprüfen, ob die Dokumentnachverfolgung derzeit aktiviert oder deaktiviert ist. Zum Ausführen dieser Cmdlets benötigen Sie mindestens Version **2.3.0.0** des AADRM-Moduls für PowerShell. 

Wenn die Website für die Dokumentnachverfolgung aktiviert ist, werden standardmäßig Informationen angezeigt, wie z.B. E-Mail-Adressen der Personen, die auf geschützte Dokumente zugegriffen haben, wann diese Benutzer versucht haben, darauf zuzugreifen, sowie deren Standort. Diese Art von Informationen kann hilfreich sein, um festzulegen, wie die freigegebenen Dokumente verwendet und ob sie widerrufen werden sollen, wenn verdächtige Aktivitäten festgestellt werden. Aus Datenschutzgründen müssen diese Benutzerinformationen allerdings u.U. für einige oder alle Benutzer deaktiviert werden. 

Wenn Benutzer vorhanden sind, bei denen die Nachverfolgung dieser Aktivität durch andere Benutzer unterbunden werden soll, fügen Sie sie einer in Azure AD gespeicherten Gruppe hinzu, und geben Sie diese Gruppe mit dem Cmdlet [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup) an. Wenn Sie dieses Cmdlet ausführen, dürfen Sie nur eine einzelne Gruppe angeben. Allerdings kann die Gruppe verschachtelte Gruppen enthalten. 

Für diese Gruppenmitglieder wird anderen Benutzern keine Aktivität auf der Website für die Dokumentnachverfolgung angezeigt, wenn die Aktivität zu Dokumenten gehört, die für sie freigegeben wurden. Darüber hinaus werden keine E-Mail-Benachrichtigungen an den Benutzer gesendet, der das Dokument freigegeben hat.

Wenn Sie diese Konfiguration verwenden, können alle Benutzer weiterhin die Website für die Dokumentnachverfolgung verwenden und den Zugriff auf die von ihnen geschützten Dokumente widerrufen. Sie können jedoch keine Aktivitäten von Benutzern einsehen, die Sie mit dem Cmdlet „Set-AadrmDoNotTrackUserGroup“ angegeben haben.

Diese Einstellung gilt nur für Endbenutzer. Administratoren für Azure Information Protection können die Aktivitäten aller Benutzer immer nachverfolgen, selbst wenn die Benutzer mithilfe von Set-AadrmDoNotTrackUserGroup angegeben wurden. Weitere Informationen dazu, wie Administratoren Dokumente für Benutzer nachverfolgen können, finden Sie im Abschnitt [Nachverfolgen und Sperren von Dokumenten für Benutzer](#tracking-and-revoking-documents-for-users).


### <a name="logging-information-from-the-document-tracking-site"></a>Protokollieren von Informationen aus der Website für die Dokumentnachverfolgung

Wenn Sie für das AADRM-Modul die Mindestversion **2.13.0.0** haben, können Sie mithilfe der folgenden Cmdlets Protokollinformationen von der Website für die Dokumentnachverfolgung herunterladen:

- [Get-AadrmTrackingLog](/powershell/module/aadrm/Get-AadrmTrackingLog)
    
    Dieses Cmdlet gibt Informationen zu geschützten Dokumenten für einen angegebenen Benutzer zurück, der Dokumente geschützt hat (Rights Management-Aussteller) oder der auf geschützte Dokumente zugegriffen hat. Mithilfe dieses Cmdlets können Sie die Frage beantworten, auf welche geschützten Dokumente ein bestimmter Benutzer zugegriffen und welche er nachverfolgt hat.

- [Get-AadrmDocumentLog](/powershell/module/aadrm/Get-AadrmDocumentLog)
    
    Dieses Cmdlet gibt Informationen zum Schutz der nachverfolgten Dokumente für einen bestimmten Benutzer zurück (Rights Management-Aussteller), falls dieser Benutzer Dokumente geschützt hat, Rights Management-Besitzer von Dokumenten war oder Dokumente geschützt hat, die so konfiguriert waren, dass dem Benutzer direkter Zugriff gewährt werden sollte. Mithilfe dieses Cmdlets können Sie die Frage beantworten, wie Dokumente für einen bestimmten Benutzer geschützt werden.
 
## <a name="destination-urls-used-by-the-document-tracking-site"></a>Von der Website für die Dokumentnachverfolgung verwendete Ziel-URLs

Die folgenden URLs dienen zum Nachverfolgen von Dokumenten und müssen auf allen Geräten und in allen Diensten zwischen den Clients zugelassen werden, auf denen der Azure Information Protection-Client und das Internet ausgeführt werden. Beispiel: Fügen Sie diese URLs zu Firewalls oder zu Ihren vertrauenswürdigen Websites hinzu, wenn Sie Internet Explorer mit erhöhter Sicherheit verwenden.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Dies sind die Standard-URLs für den Azure Rights Management-Dienst mit Ausnahme der URL virtualearth.net, die für Bing-Karten zur Anzeige des Benutzerstandorts verwendet wird.

## <a name="tracking-and-revoking-documents-for-users"></a>Nachverfolgen und Sperren von Dokumenten für Benutzer

Wenn sich Benutzer auf der Website zur Dokumentenverfolgung anmelden, können sie Dokumente nachverfolgen und sperren, die sie mithilfe des Azure Information Protection-Clients oder der RMS-Freigabeanwendung freigegeben haben. Wenn Sie sich für Ihren Mandanten als globaler Azure AD-Administrator anmelden, können Sie auf das Administratorsymbol klicken, um in den Administratormodus zu wechseln. Dieser Modus für die Website zum Nachverfolgen von Dokumenten wird von anderen Administratorrollen nicht unterstützt. 

![Adminsymbol auf der Website zur Dokumentenverfolgung](../media/tracking-site-admin-icon.png)

Im Administratormodus können Sie die Dokumente anzeigen, die von den Benutzern in Ihrer Organisation zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt oder mithilfe der Freigabeanwendung von Rights Management freigegeben wurden.

> [!NOTE] 
> Wenn Sie dieses Symbol nicht sehen, obwohl Sie über globale Administratorrechte verfügen, liegt das daran, dass Sie selbst noch keine Dokumente freigegeben haben. Verwenden Sie in diesem Fall die folgende URL, um auf die Website zur Dokumentenverfolgung zu gelangen: https://portal.azurerms.com/#/admin

Aktionen, die Sie im Administratormodus durchführen, werden geprüft und in Verwendungsprotokolldateien protokolliert, und Sie müssen Ihre Einwilligung geben, um den Vorgang fortzusetzen. Weitere Informationen über diese Protokollierung finden Sie im nächsten Abschnitt.

Wenn Sie sich im Administratormodus befinden, können Sie nach Benutzern oder Dokumenten suchen. Wenn Sie nach Benutzer suchen, können Sie alle Dokumente anzeigen, die vom angegebenen Benutzer zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt oder mithilfe der Freigabeanwendung von Rights Management freigegeben wurden. 

Wenn Sie nach Dokument suchen, können Sie alle Benutzer in Ihrer Organisation anzeigen, die dieses Dokument durch den Azure Information Protection-Client nachverfolgt oder mithilfe der Freigabeanwendung von Rights Management freigegeben haben. Sie können die Suchergebnisse näher betrachten, um die Dokumente zu überwachen, die Benutzer geschützt haben, und diese Dokumente, falls erforderlich, wieder zu sperren. 

Klicken Sie auf das **X** neben **Administratormodus beenden**, um den Administratormodus zu verlassen.

![Administratormodus auf der Website für die Dokumentenverfolgung beenden](../media/tracking-site-exit-admin-icon.png)

Eine Anleitung zur Verwendung der Website zur Dokumentnachverfolgung finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](client-track-revoke.md) im Benutzerhandbuch.

## <a name="usage-logging-for-the-document-tracking-site"></a>Verwendungsprotokollierung für die Website zur Dokumentnachverfolgung

Für die Dokumentnachverfolgung kommen zwei Felder in den Verwendungsprotokolldateien infrage: **AdminAction** und **ActingAsUser**.

**AdminAction** – Dieses Feld weist den Wert TRUE auf, wenn ein Administrator die Website zur Dokumentnachverfolgung im Administratormodus verwendet, z.B. um ein Dokument im Auftrag des Benutzers zu sperren oder um festzustellen, wann es freigegeben wurde. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer.

**ActingAsUser** – Wenn das Feld „AdminAction“ TRUE aufweist, enthält dieses Feld den Benutzernamen, in dessen Auftrag der Administrator als der gesuchte Benutzer oder Besitzer des Dokuments handelt. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer. 

Einige der Anforderungstypen protokollieren die Verwendungsweise der Website zur Dokumentnachverfolgung vonseiten der Benutzer und Administratoren. **RevokeAccess** ist beispielsweise der verwendete Anforderungstyp, wenn ein Benutzer oder Administrator im Auftrag eines Benutzers ein Dokument auf der Website zur Dokumentnachverfolgung gesperrt hat. Verwenden Sie diesen Anforderungstyp in Kombination mit dem AdminAction-Feld, um zu ermitteln, ob ein Benutzer sein eigenes Dokument gesperrt hat (AdminAction ist leer) oder ob der Administrator dies im Namen eines Benutzers getan hat (AdminAction ist TRUE).


Weitere Informationen zur Verwendungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../log-analyze-usage.md).



## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Website für die Dokumentenverfolgung für den Azure Information Protection-Client konfiguriert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

