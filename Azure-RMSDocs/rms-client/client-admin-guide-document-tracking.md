---
title: "Dokumentkontrolle für Azure Information Protection"
description: "Dieser Artikel enthält Anweisungen und Informationen für Administratoren, die die Dokumentkontrolle für Azure Information Protection konfigurieren und verwenden möchten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: bbbc9a274ea815577109276bceb0b08617f03809
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>Administratorhandbuch: Konfigurieren und Verwenden der Dokumentkontrolle für Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Bei Verwendung eines [Abonnements, das die Dokumentkontrolle unterstützt](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), ist die Website für die Dokumentkontrolle standardmäßig für alle Benutzer in Ihrer Organisation aktiviert. Durch die Dokumentkontrolle erhalten Benutzer und Administratoren Informationen dazu, wann auf ein geschütztes Dokument zugegriffen wird und ob ein nachverfolgtes Dokument ggf. gesperrt werden kann.

## <a name="privacy-controls-for-your-document-tracking-site"></a>Steuerung des Datenschutzes für Ihre Website für die Dokumentkontrolle

Wenn das Anzeigen aller Dokumentkontrollinformationen in Ihrer Organisation aufgrund von Datenschutzanforderungen nicht zulässig ist, können Sie die Dokumentkontrolle mithilfe des Cmdlets [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature) deaktivieren. 

Dieses Cmdlet deaktiviert den Zugriff auf die Website für die Dokumentkontrolle, damit keine Benutzer in Ihrer Organisation die von ihnen geschützten Dokumente nachverfolgen oder den Zugriff darauf widerrufen können. Mit dem Cmdlet [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) können Sie die Dokumentkontrolle jederzeit wieder aktivieren, und mit [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature) können Sie den Aktivierungsstatus der Dokumentkontrolle überprüfen. Zum Ausführen dieser Cmdlets benötigen Sie mindestens Version **2.3.0.0** des AADRM-Moduls (Azure Rights Management) für PowerShell. 

Wenn die Website für die Dokumentkontrolle aktiviert ist, werden standardmäßig bestimmte Informationen angezeigt. Hierzu zählen beispielsweise die E-Mail-Adressen der Personen, die versucht haben, auf geschützte Dokumente zuzugreifen, sowie der Zeitpunkt des Zugriffsversuchs und der Standort. Diese Informationen können hilfreich sein, um zu bestimmen, wie die freigegebenen Dokumente verwendet werden und ob sie bei verdächtigen Aktivitäten gesperrt werden sollen. Aus Datenschutzgründen müssen diese Benutzerinformationen allerdings unter Umständen für einige oder alle Benutzer deaktiviert werden. 

Wenn Benutzer vorhanden sind, bei denen die Nachverfolgung dieser Aktivität durch andere Benutzer unterbunden werden soll, fügen Sie sie einer in Azure AD gespeicherten Gruppe hinzu, und geben Sie diese Gruppe mit dem Cmdlet [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup) an. Bei der Ausführung dieses Cmdlets darf nur eine einzelne Gruppe angegeben werden. Diese Gruppe kann allerdings geschachtelte Gruppen enthalten. 

Anderen Benutzern werden auf der Website für die Dokumentkontrolle keine Aktivitäten für die Mitglieder dieser Gruppe angezeigt, wenn die Aktivitäten mit Dokumenten zusammenhängen, die für sie freigegeben wurden. Darüber hinaus werden keine E-Mail-Benachrichtigungen an den Benutzer gesendet, der das Dokument freigegeben hat.

Bei Verwendung dieser Konfiguration können alle Benutzer weiterhin die Website für die Dokumentkontrolle verwenden und den Zugriff auf die von ihnen geschützten Dokumente widerrufen. Sie können jedoch keine Aktivitäten von Benutzern einsehen, die Sie mit dem Cmdlet „Set-AadrmDoNotTrackUserGroup“ angegeben haben.

Diese Einstellung gilt nur für Endbenutzer. Administratoren für Azure Information Protection können die Aktivitäten aller Benutzer immer nachverfolgen, selbst wenn die Benutzer mithilfe von „Set-AadrmDoNotTrackUserGroup“ angegeben wurden. Weitere Informationen dazu, wie Administratoren Dokumente für Benutzer nachverfolgen können, finden Sie im Abschnitt [Nachverfolgen und Sperren von Dokumenten für Benutzer](#tracking-and-revoking-documents-for-users).

Wenn Sie diese Option nicht mehr benötigen, können Sie das Cmdlet [Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup) verwenden. Benutzer können auch einzeln aus der Gruppe entfernt werden. Achten Sie dabei jedoch auf die [Gruppenzwischenspeicherung](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). Ob diese Option derzeit verwendet wird, können Sie mithilfe von [Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup) ermitteln. Zum Ausführen der Cmdlets für diese Gruppenkonfiguration benötigen Sie mindestens Version **2.10.0.0** des AADRM-Moduls (Azure Rights Management) für PowerShell.

Weitere Informationen zu den einzelnen Cmdlets finden Sie unter den bereitgestellten Links. Installationsanweisungen zum PowerShell-Modul finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md). Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm –ListAvailable).Version`


## <a name="destination-urls-used-by-the-document-tracking-site"></a>Von der Website für die Dokumentkontrolle verwendete Ziel-URLs

Die folgenden URLs dienen zum Nachverfolgen von Dokumenten und müssen auf allen Geräten und in allen Diensten zwischen den Clients, auf denen der Azure Information Protection-Client ausgeführt wird, und dem Internet zugelassen werden. Fügen Sie diese URLs beispielsweise Firewalls oder (bei Verwendung von Internet Explorer mit erhöhter Sicherheit) Ihren vertrauenswürdigen Websites hinzu.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Dies sind die Standard-URLs für den Azure Rights Management-Dienst. Einzige Ausnahme: virtualearth.net (wird bei Bing-Karten zum Anzeigen des Benutzerstandorts verwendet).

## <a name="tracking-and-revoking-documents-for-users"></a>Nachverfolgen und Sperren von Dokumenten für Benutzer

Wenn sich Benutzer auf der Website für die Dokumentkontrolle anmelden, können sie Dokumente nachverfolgen und sperren, die sie mithilfe des Azure Information Protection-Clients oder der Rights Management-Freigabeanwendung freigegeben haben. Wenn Sie sich als Administrator für Azure Information Protection anmelden (globaler Administrator), können Sie durch Klicken auf das Administratorsymbol in den Administratormodus wechseln. In diesem Modus können Sie die Dokumente anzeigen, die von den Benutzern in Ihrer Organisation zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt oder mithilfe der Rights Management-Freigabeanwendung freigegeben wurden:

![Administratorsymbol auf der Website für die Dokumentkontrolle](../media/tracking-site-admin-icon.png)

> [!NOTE] 
> Sollte dieses Symbol nicht angezeigt werden, obwohl Sie über globale Administratorrechte verfügen, liegt das daran, dass Sie selbst noch keine Dokumente freigegeben haben. Verwenden Sie in diesem Fall die folgende URL, um die Website für die Dokumentkontrolle aufzurufen: https://portal.azurerms.com/#/admin

Im Administratormodus ausgeführte Aktionen werden überwacht, in Verwendungsprotokolldateien protokolliert und müssen bestätigt werden, um den Vorgang fortsetzen zu können. Weitere Informationen zu dieser Protokollierung finden Sie im nächsten Abschnitt.

Im Administratormodus können Sie nach Benutzer oder nach Dokumente suchen. Bei der Suche nach Benutzer werden alle Dokumente angezeigt, die vom angegebenen Benutzer zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt oder mithilfe der Rights Management-Freigabeanwendung freigegeben wurden. 

Bei der Suche nach Dokument werden alle Benutzer in Ihrer Organisation angezeigt, die dieses Dokument über den Azure Information Protection-Client nachverfolgt oder mithilfe der Rights Management-Freigabeanwendung freigegeben haben. Sie können die Suchergebnisse genauer untersuchen, um die Dokumente nachzuverfolgen, die Benutzer geschützt haben, und diese Dokumente ggf. sperren. 

Klicken Sie neben **Administratormodus beenden** auf **X**, um den Administratormodus zu beenden:

![Beenden des Administratormodus auf der Website für die Dokumentkontrolle](../media/tracking-site-exit-admin-icon.png)

Eine Anleitung zur Verwendung der Website für die Dokumentkontrolle finden Sie unter [Benutzerhandbuch: Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung von Azure Information Protection](client-track-revoke.md).

## <a name="usage-logging-for-the-document-tracking-site"></a>Verwendungsprotokollierung für die Website für die Dokumentkontrolle

Für die Dokumentkontrolle sind zwei Felder in den Verwendungsprotokolldateien relevant: **AdminAction** und **ActingAsUser**.

**AdminAction:** Dieses Feld hat den Wert „true“, wenn ein Administrator die Website für die Dokumentkontrolle im Administratormodus verwendet, um beispielsweise ein Dokument im Auftrag eines Benutzers zu sperren oder um zu ermitteln, wann es freigegeben wurde. Wenn sich ein Benutzer bei der Website für die Dokumentkontrolle anmeldet, ist dieses Feld leer.

**ActingAsUser:** Wenn das Feld „AdminAction“ den Wert „true“ hat, enthält dieses Feld den Namen des Benutzers, in dessen Auftrag der Administrator als gesuchter Benutzer oder Besitzer des Dokuments handelt. Wenn sich ein Benutzer bei der Website für die Dokumentkontrolle anmeldet, ist dieses Feld leer. 

Bei einigen Anforderungstypen wird auch protokolliert, wie Benutzer und Administratoren die Website für die Dokumentkontrolle verwenden. Der Anforderungstyp **RevokeAccess** wird beispielsweise verwendet, wenn ein Benutzer oder Administrator im Auftrag eines Benutzers ein Dokument auf der Website für die Dokumentkontrolle gesperrt hat. Verwenden Sie diesen Anforderungstyp in Kombination mit dem Feld „AdminAction“, um zu ermitteln, ob ein Benutzer sein eigenes Dokument gesperrt hat („AdminAction“ ist leer) oder ob ein Administrator ein Dokument im Namen eines Benutzers gesperrt hat („AdminAction“ hat den Wert „true“).


Weitere Informationen zur Verwendungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).



## <a name="next-steps"></a>Nächste Schritte
Sie haben nun die Website für die Dokumentkontrolle für den Azure Information Protection-Client konfiguriert. Unter den folgenden Links finden Sie zusätzliche Informationen, die Sie ggf. zur Unterstützung dieses Clients benötigen:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Verwendungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
