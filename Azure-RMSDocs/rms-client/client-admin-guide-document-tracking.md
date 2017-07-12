---
title: "Dokumentenverfolgung für Azure Information Protection"
description: "Anweisungen und Informationen für Administratoren zum Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 3b7ed22afea6b8575d12f6f83dcfc8419200c003
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="configuring-and-using-document-tracking-for-azure-information-protection" class="xliff"></a>

# Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Wenn Sie ein [Abonnement haben, das die Dokumentenverfolgung unterstützt](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), ist die Website für die Dokumentnachverfolgung standardmäßig für alle Benutzer in Ihrer Organisation aktiviert. Durch die Dokumentkontrolle erhalten Benutzer und Administratoren Informationen darüber, wann auf ein geschütztes Dokument zugegriffen wird und ob ein nachverfolgtes Dokument ggf. gesperrt werden kann.

<a id="privacy-controls-for-your-document-tracking-site" class="xliff"></a>

## Datenschutzkontrollen für Ihre Website für die Dokumentnachverfolgung

Wenn das Anzeigen aller Informationen zur Dokumentnachverfolgung in Ihrer Organisation aufgrund von Datenschutzanforderungen nicht zulässig ist, können Sie die Dokumentnachverfolgung mithilfe des Cmdlets [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature) deaktivieren. 

Dieses Cmdlet deaktiviert den Zugriff auf die Website für die Dokumentnachverfolgung, damit keine Benutzer in Ihrer Organisation die von ihnen geschützten Dokumente nachverfolgen oder den Zugriff auf diese widerrufen können. Sie können die Dokumentnachverfolgung jederzeit mit dem Cmdlet [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) wieder aktivieren und mit [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature) überprüfen, ob die Dokumentnachverfolgung derzeit aktiviert oder deaktiviert ist. Zum Ausführen dieser Cmdlets benötigen Sie mindestens Version **2.3.0.0** des AADRM-Moduls (Azure Rights Management) für PowerShell. 

Wenn die Website für die Dokumentnachverfolgung aktiviert ist, werden standardmäßig Informationen angezeigt, wie z.B. E-Mail-Adressen der Personen, die auf geschützte Dokumente zugegriffen haben, wann diese Benutzer versucht haben, darauf zuzugreifen, sowie deren Standort. Diese Art von Informationen kann sehr hilfreich sein, um festzulegen, wie die freigegebenen Dokumente verwendet und ob sie widerrufen werden sollen, wenn verdächtige Aktivitäten festgestellt werden. Aus Datenschutzgründen müssen diese Benutzerinformationen allerdings u.U. für einige oder alle Benutzer deaktiviert werden. 

Wenn Benutzer vorhanden sind, bei denen die Nachverfolgung dieser Aktivität unterbunden werden soll, fügen Sie sie zu einer in Azure AD gespeicherten Gruppe hinzu, und legen Sie diese Gruppe mit dem Cmdlet [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup) fest. Wenn Sie dieses Cmdlet ausführen, dürfen Sie nur eine einzelne Gruppe angeben. Allerdings kann die Gruppe verschachtelte Gruppen enthalten. 

Bei diesen Gruppenmitgliedern werden Aktivitäten im Zusammenhang mit Dokumenten, die andere für sie freigegeben haben, nicht auf Ihrer Website für die Dokumentnachverfolgung protokolliert. Darüber hinaus werden keine E-Mail-Benachrichtigungen an den Benutzer gesendet, der das Dokument freigegeben hat.

Wenn Sie diese Konfiguration verwenden, können alle Benutzer weiterhin die Website für die Dokumentnachverfolgung verwenden und den Zugriff auf die von ihnen geschützten Dokumente widerrufen. Sie können jedoch keine Aktivitäten von Benutzern einsehen, die Sie mit dem Cmdlet „Set-AadrmDoNotTrackUserGroup“ angegeben haben.

Wenn Sie diese Option nicht mehr benötigen, können Sie das Cmdlet [Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup) verwenden. Um Benutzer selektiv zu entfernen, können Sie sie alternativ aus der Gruppe entfernen, müssen jedoch die [Gruppenzwischenspeicherung](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management) berücksichtigen. Mithilfe von [Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup) können Sie überprüfen, ob diese Option derzeit verwendet wird. Zum Ausführen dieser Cmdlets für diese Gruppenkonfiguration benötigen Sie mindestens Version **2.10.0.0** des AADRM-Moduls (Azure Rights Management) für PowerShell.

Weitere Informationen zu den einzelnen Cmdlets finden Sie unter den angegebenen Links. Installationsanweisungen zum PowerShell-Modul finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md). Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm –ListAvailable).Version`


<a id="destination-urls-used-by-the-document-tracking-site" class="xliff"></a>

## Von der Website für die Dokumentnachverfolgung verwendete Ziel-URLs

Die folgenden URLs dienen zum Nachverfolgen von Dokumenten und müssen auf allen Geräten und in allen Diensten zwischen den Clients zugelassen werden, auf denen der Azure Information Protection-Client und das Internet ausgeführt werden. Beispiel: Fügen Sie diese URLs zu Firewalls oder zu Ihren vertrauenswürdigen Websites hinzu, wenn Sie Internet Explorer mit erhöhter Sicherheit verwenden.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Dies sind die Standard-URLs für den Azure Rights Management-Dienst mit Ausnahme der URL virtualearth.net, die für Bing-Karten zur Anzeige des Benutzerstandorts verwendet wird.

<a id="tracking-and-revoking-documents-for-users" class="xliff"></a>

## Nachverfolgen und Sperren von Dokumenten für Benutzer

Wenn sich Benutzer auf der Website zur Dokumentenverfolgung anmelden, können sie Dokumente nachverfolgen und sperren, die sie mithilfe des Azure Information Protection-Clients oder der RMS-Freigabeanwendung freigegeben haben. Wenn Sie sich als Administrator für Azure Information Protection anmelden (globaler Administrator), können Sie auf das Adminsymbol klicken, um in den Administratormodus zu wechseln. So können Sie die Dokumente anzeigen, die von den Benutzern in Ihrer Organisation freigegeben wurden:

![Adminsymbol auf der Website zur Dokumentenverfolgung](../media/tracking-site-admin-icon.png)

Aktionen, die Sie im Administratormodus durchführen, werden geprüft und in Verwendungsprotokolldateien protokolliert, und Sie müssen Ihre Einwilligung geben, um den Vorgang fortzusetzen. Weitere Informationen über diese Protokollierung finden Sie im nächsten Abschnitt.

Wenn Sie sich im Administratormodus befinden, können Sie nach Benutzern oder Dokumenten suchen. Wenn Sie nach Benutzern suchen, werden Ihnen alle Dokumente angezeigt, die dem angegebenen Benutzer freigegeben wurden. Wenn Sie nach Dokumenten suchen, sehen alle Benutzer in Ihrer Organisation, die das Dokument freigegeben haben. Sie können die Suchergebnisse näher betrachten, um Dokumente zu überwachen, die Benutzer freigegeben haben, und diese Dokumente, falls erforderlich, wieder zu sperren. 

Klicken Sie auf das **X** neben **Administratormodus beenden**, um den Administratormodus zu verlassen.

![Administratormodus auf der Website für die Dokumentenverfolgung beenden](../media/tracking-site-exit-admin-icon.png)

Eine Anleitung zur Verwendung der Website zur Dokumentnachverfolgung finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](client-track-revoke.md) im Benutzerhandbuch.

<a id="usage-logging-for-the-document-tracking-site" class="xliff"></a>

## Verwendungsprotokollierung für die Website zur Dokumentnachverfolgung

Für die Dokumentnachverfolgung kommen zwei Felder in den Verwendungsprotokolldateien infrage: **AdminAction** und **ActingAsUser**.

**AdminAction** – Dieses Feld weist den Wert TRUE auf, wenn ein Administrator die Website zur Dokumentnachverfolgung im Administratormodus verwendet, z.B. um ein Dokument im Auftrag des Benutzers zu sperren oder um festzustellen, wann es freigegeben wurde. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer.

**ActingAsUser** – Wenn das Feld „AdminAction“ TRUE aufweist, enthält dieses Feld den Benutzernamen, in dessen Auftrag der Administrator als der gesuchte Benutzer oder Besitzer des Dokuments handelt. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer. 

Einige der Anforderungstypen protokollieren die Verwendungsweise der Website zur Dokumentnachverfolgung vonseiten der Benutzer und Administratoren. **RevokeAccess** ist beispielsweise der verwendete Anforderungstyp, wenn ein Benutzer oder Administrator im Auftrag eines Benutzers ein Dokument auf der Website zur Dokumentnachverfolgung gesperrt hat. Verwenden Sie diesen Anforderungstyp in Kombination mit dem AdminAction-Feld, um zu ermitteln, ob ein Benutzer sein eigenes Dokument gesperrt hat (AdminAction ist leer) oder ob der Administrator dies im Namen eines Benutzers getan hat (AdminAction ist TRUE).


Weitere Informationen zur Verwendungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).



<a id="next-steps" class="xliff"></a>

## Nächste Schritte
Nachdem Sie die Website für die Dokumentenverfolgung für den Azure Information Protection-Client konfiguriert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
