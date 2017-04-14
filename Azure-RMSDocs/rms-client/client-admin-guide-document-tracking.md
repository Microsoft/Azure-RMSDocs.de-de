---
title: "Dokumentenverfolgung für Azure Information Protection"
description: "Anweisungen und Informationen für Administratoren zum Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: dad69e37e2908d155fd1be370d190fd91d5739a3
ms.sourcegitcommit: 7b773ca5bf1abf30e527c34717ecb2dc96f88033
translationtype: HT
---
# <a name="configuring-and-using-document-tracking-for-azure-information-protection"></a>Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Wenn Sie ein [Abonnement haben, das die Dokumentenverfolgung unterstützt](https://www.microsoft.com/cloud-platform/azure-information-protection-features), ist die Website für die Dokumentnachverfolgung standardmäßig für alle Benutzer in Ihrer Organisation aktiviert. Die Dokumentenverfolgung zeigt Informationen, wie z. B. E-Mail-Adressen der Personen, die auf geschützte Dokumente zugegriffen haben, die von Benutzern freigegeben wurden, wann diese Benutzer versucht haben, darauf zuzugreifen, sowie deren Standort. Wenn das Anzeigen dieser Informationen in Ihrer Organisation aufgrund von Datenschutzanforderungen nicht zulässig ist, können Sie den Zugriff auf die Website der Dokumentenverfolgung mithilfe des Cmdlets [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) deaktivieren. Sie können den Zugriff auf die Website jederzeit mit dem Cmdlet [Enable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) wieder aktivieren und mit [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) überprüfen, ob der Zugriff derzeit aktiviert oder deaktiviert ist.

Zum Ausführen dieser Cmdlets benötigen Sie mindestens Version **2.3.0.0** des Azure Rights Management-Moduls für Windows PowerShell. Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

> [!TIP]
> Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm –ListAvailable).Version`

Die folgenden URLs werden für die Dokumentenverfolgung verwendet und müssen zulässig sein (z. B. durch Hinzufügen zu Ihren vertrauenswürdigen Websites, wenn Sie Internet Explorer mit erhöhter Sicherheit verwenden):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Dieser URL ist für Bing-Karten.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

## <a name="tracking-and-revoking-documents-for-users"></a>Nachverfolgen und Sperren von Dokumenten für Benutzer

Wenn sich Benutzer auf der Website zur Dokumentenverfolgung anmelden, können sie Dokumente nachverfolgen und sperren, die sie mithilfe des Azure Information Protection-Clients oder der RMS-Freigabeanwendung freigegeben haben. Wenn Sie sich als Administrator für Azure Information Protection anmelden (globaler Administrator), können Sie auf das Adminsymbol klicken, um in den Administratormodus zu wechseln. So können Sie die Dokumente anzeigen, die von den Benutzern in Ihrer Organisation freigegeben wurden:

![Adminsymbol auf der Website zur Dokumentenverfolgung](../media/tracking-site-admin-icon.png)

Aktionen, die Sie im Administratormodus durchführen, werden geprüft und in Verwendungsprotokolldateien protokolliert, und Sie müssen Ihre Einwilligung geben, um den Vorgang fortzusetzen. Weitere Informationen über diese Protokollierung finden Sie im nächsten Abschnitt.

Wenn Sie sich im Administratormodus befinden, können Sie nach Benutzern oder Dokumenten suchen. Wenn Sie nach Benutzern suchen, werden Ihnen alle Dokumente angezeigt, die dem angegebenen Benutzer freigegeben wurden. Wenn Sie nach Dokumenten suchen, sehen alle Benutzer in Ihrer Organisation, die das Dokument freigegeben haben. Sie können die Suchergebnisse näher betrachten, um Dokumente zu überwachen, die Benutzer freigegeben haben, und diese Dokumente, falls erforderlich, wieder zu sperren. 

Klicken Sie auf das **X** neben **Administratormodus beenden**, um den Administratormodus zu verlassen.

![Administratormodus auf der Website für die Dokumentenverfolgung beenden](../media/tracking-site-exit-admin-icon.png)

Eine Anleitung zur Verwendung der Website zur Dokumentnachverfolgung finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](client-track-revoke.md) im Benutzerhandbuch.

## <a name="usage-logging-for-the-document-tracking-site"></a>Verwendungsprotokollierung für die Website zur Dokumentnachverfolgung

Für die Dokumentnachverfolgung kommen zwei Felder in den Verwendungsprotokolldateien infrage: **AdminAction** und **ActingAsUser**.

**AdminAction** – Dieses Feld weist den Wert TRUE auf, wenn ein Administrator die Website zur Dokumentnachverfolgung im Administratormodus verwendet, z.B. um ein Dokument im Auftrag des Benutzers zu sperren oder um festzustellen, wann es freigegeben wurde. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer.

**ActingAsUser** – Wenn das Feld „AdminAction“ TRUE aufweist, enthält dieses Feld den Benutzernamen, in dessen Auftrag der Administrator als der gesuchte Benutzer oder Besitzer des Dokuments handelt. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer. 

Einige der Anforderungstypen protokollieren die Verwendungsweise der Website zur Dokumentnachverfolgung vonseiten der Benutzer und Administratoren. **RevokeAccess** ist beispielsweise der verwendete Anforderungstyp, wenn ein Benutzer oder Administrator im Auftrag eines Benutzers ein Dokument auf der Website zur Dokumentnachverfolgung gesperrt hat. Verwenden Sie diesen Anforderungstyp in Kombination mit dem AdminAction-Feld, um zu ermitteln, ob ein Benutzer sein eigenes Dokument gesperrt hat (AdminAction ist leer) oder ob der Administrator dies im Namen eines Benutzers getan hat (AdminAction ist TRUE).


Weitere Informationen zur Verwendungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).



## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Website für die Dokumentenverfolgung für den Azure Information Protection-Client konfiguriert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
