---
title: Dokumentkontrolle für Azure Information Protection
description: Dieser Artikel enthält Anweisungen und Informationen für Administratoren, die die Dokumentkontrolle für Azure Information Protection konfigurieren und verwenden möchten.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/16/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.subservice: doctrack
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 66ad27bb61e4cdc24d5c047b8f2c464ba98e5a8d
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "95567613"
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>Administratorhandbuch: Konfigurieren und Verwenden der Dokumentkontrolle für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Bei Verwendung eines [Abonnements, das die Dokumentkontrolle unterstützt](https://www.microsoft.com/cloud-platform/azure-information-protection-features), ist die Website für die Dokumentkontrolle standardmäßig für alle Benutzer in Ihrer Organisation aktiviert. Durch die Dokumentkontrolle erhalten Benutzer und Administratoren Informationen dazu, wann auf ein geschütztes Dokument zugegriffen wird und ob ein nachverfolgtes Dokument ggf. gesperrt werden kann.

## <a name="using-powershell-to-manage-the-document-tracking-site"></a>Verwalten der Website für die Dokumentnachverfolgung mithilfe von PowerShell

In den folgenden Abschnitten finden Sie Informationen dazu, wie Sie die Website für die Dokumentnachverfolgung mithilfe von PowerShell verwalten können. Installationsanweisungen für das PowerShell-Modul finden Sie unter [Installieren des aipservice-PowerShell-Moduls](../install-powershell.md).

Weitere Informationen zu den einzelnen Cmdlets finden Sie unter den angegebenen Links.

### <a name="privacy-controls-for-your-document-tracking-site"></a>Steuerung des Datenschutzes für Ihre Website für die Dokumentkontrolle

Wenn die Anzeige aller Informationen zur Dokument Nachverfolgung in Ihrer Organisation aufgrund von Datenschutzanforderungen nicht zulässig ist, können Sie die dokumentenverfolgung mithilfe des Cmdlets " [Deaktivieren-aipservicedocumenttrackingfeature](/powershell/module/aipservice/disable-aipservicedocumenttrackingfeature) " deaktivieren. 

Dieses Cmdlet deaktiviert den Zugriff auf die Website für die Dokumentkontrolle, damit keine Benutzer in Ihrer Organisation die von ihnen geschützten Dokumente nachverfolgen oder den Zugriff darauf widerrufen können. Sie können die Dokument Nachverfolgung jederzeit mithilfe von [enable-aipservicedocumenttrackingfeature](/powershell/module/aipservice/enable-aipservicedocumenttrackingfeature)wieder aktivieren und mithilfe von [Get-aipservicedocumenttrackingfeature](/powershell/module/aipservice/get-aipservicedocumenttrackingfeature)überprüfen, ob die Dokument Nachverfolgung derzeit aktiviert oder deaktiviert ist. 

Wenn die Website für die Dokumentkontrolle aktiviert ist, werden standardmäßig bestimmte Informationen angezeigt. Hierzu zählen beispielsweise die E-Mail-Adressen der Personen, die versucht haben, auf geschützte Dokumente zuzugreifen, sowie der Zeitpunkt des Zugriffsversuchs und der Standort. Diese Informationen können hilfreich sein, um zu bestimmen, wie die freigegebenen Dokumente verwendet werden und ob sie bei verdächtigen Aktivitäten gesperrt werden sollen. Aus Datenschutzgründen müssen diese Benutzerinformationen allerdings unter Umständen für einige oder alle Benutzer deaktiviert werden. 

Wenn Sie über Benutzer verfügen, für die diese Aktivität von anderen Benutzern nicht nachverfolgt werden soll, fügen Sie Sie einer in Azure AD gespeicherten Gruppe hinzu, und geben Sie diese Gruppe mit dem Cmdlet [Set-aipservicedonottrackusergroup](/powershell/module/aipservice/Set-AipServiceDoNotTrackUserGroup) an. Bei der Ausführung dieses Cmdlets darf nur eine einzelne Gruppe angegeben werden. Diese Gruppe kann allerdings geschachtelte Gruppen enthalten. 

Anderen Benutzern werden auf der Website für die Dokumentkontrolle keine Aktivitäten für die Mitglieder dieser Gruppe angezeigt, wenn die Aktivitäten mit Dokumenten zusammenhängen, die für sie freigegeben wurden. Darüber hinaus werden keine E-Mail-Benachrichtigungen an den Benutzer gesendet, der das Dokument freigegeben hat.

Bei Verwendung dieser Konfiguration können alle Benutzer weiterhin die Website für die Dokumentkontrolle verwenden und den Zugriff auf die von ihnen geschützten Dokumente widerrufen. Es werden jedoch keine Aktivitäten für die Benutzer angezeigt, die Sie mit dem Cmdlet "Set-AipServiceDoNotTrackUserGroup" angegeben haben.

Diese Einstellung gilt nur für Endbenutzer. Administratoren für Azure Information Protection können die Aktivitäten aller Benutzer immer nachverfolgen, auch wenn diese Benutzer mithilfe von "Set-aipservicedonottrackusergroup" angegeben werden. Weitere Informationen dazu, wie Administratoren Dokumente für Benutzer nachverfolgen können, finden Sie im Abschnitt [Nachverfolgen und Sperren von Dokumenten für Benutzer](#tracking-and-revoking-documents-for-users).


### <a name="logging-information-from-the-document-tracking-site"></a>Protokollieren von Informationen aus der Website für die Dokumentnachverfolgung

Sie können die folgenden Cmdlets verwenden, um Protokollierungs Informationen von der Website für die Dokument Nachverfolgung herunterzuladen:

- [Get-aipservicetrackinglog](/powershell/module/aipservice/Get-AipServiceTrackingLog)
    
    Dieses Cmdlet gibt Informationen zu geschützten Dokumenten für einen angegebenen Benutzer zurück, der Dokumente geschützt hat (Rights Management-Aussteller) oder der auf geschützte Dokumente zugegriffen hat. Mithilfe dieses Cmdlets können Sie die Frage beantworten, auf welche geschützten Dokumente ein bestimmter Benutzer zugegriffen und welche er nachverfolgt hat.

- [Get-aipservicedocumentlog](/powershell/module/aipservice/Get-AipServiceDocumentLog)
    
    Dieses Cmdlet gibt Informationen zum Schutz der nachverfolgten Dokumente für einen bestimmten Benutzer zurück (Rights Management-Aussteller), falls dieser Benutzer Dokumente geschützt hat, Rights Management-Besitzer von Dokumenten war oder Dokumente geschützt hat, die so konfiguriert waren, dass dem Benutzer direkter Zugriff gewährt werden sollte. Mithilfe dieses Cmdlets können Sie die Frage beantworten, wie Dokumente für einen bestimmten Benutzer geschützt werden.

## <a name="destination-urls-used-by-the-document-tracking-site"></a>Von der Website für die Dokumentkontrolle verwendete Ziel-URLs

Die folgenden URLs werden für die dokumentenverfolgung verwendet und müssen auf allen Geräten und Diensten zwischen den Clients, auf denen der Azure Information Protection Client und das Internet ausgeführt werden, zulässig sein. Fügen Sie diese URLs beispielsweise Firewalls oder (bei Verwendung von Internet Explorer mit erhöhter Sicherheit) Ihren vertrauenswürdigen Websites hinzu.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Dies sind die Standard-URLs für den Azure Rights Management-Dienst. Einzige Ausnahme: virtualearth.net (wird bei Bing-Karten zum Anzeigen des Benutzerstandorts verwendet).

## <a name="tracking-and-revoking-documents-for-users"></a>Nachverfolgen und Sperren von Dokumenten für Benutzer

Wenn sich Benutzer auf der Website zur Dokumentenverfolgung anmelden, können sie mithilfe des Azure Information Protection-Clients Dokumente nachverfolgen und sperren, die sie freigegeben haben. Wenn Sie sich für Ihren Mandanten als globaler Azure AD-Administrator anmelden, können Sie auf das Administratorsymbol klicken, um in den Administratormodus zu wechseln. Dieser Modus für die Website zum Nachverfolgen von Dokumenten wird von anderen Administratorrollen nicht unterstützt. 

![Administratorsymbol auf der Website für die Dokumentkontrolle](../media/tracking-site-admin-icon.png)

Im Administratormodus können Sie die Dokumente anzeigen, die von den Benutzern in Ihrer Organisation zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt wurden.

> [!NOTE] 
> Wenn Sie dieses Symbol nicht sehen, obwohl Sie über globale Administratorrechte verfügen, liegt das daran, dass Sie selbst noch keine Dokumente freigegeben haben. Verwenden Sie in diesem Fall die folgende URL, um auf die Website zur Dokumentenverfolgung zu gelangen: https://portal.azurerms.com/#/admin

Im Administratormodus ausgeführte Aktionen werden überwacht, in Verwendungsprotokolldateien protokolliert und müssen bestätigt werden, um den Vorgang fortsetzen zu können. Weitere Informationen zu dieser Protokollierung finden Sie im nächsten Abschnitt.

Im Administratormodus können Sie nach Benutzer oder nach Dokumente suchen. Wenn Sie nach Benutzer suchen, können Sie alle Dokumente anzeigen, die vom angegebenen Benutzer zum Nachverfolgen durch den Azure Information Protection-Client ausgewählt wurden. 

Wenn Sie nach Dokument suchen, können Sie alle Benutzer in Ihrer Organisation anzeigen, die dieses Dokument durch den Azure Information Protection-Client nachverfolgt haben. Sie können die Suchergebnisse genauer untersuchen, um die Dokumente nachzuverfolgen, die Benutzer geschützt haben, und diese Dokumente ggf. sperren. 

Klicken Sie neben **Administratormodus beenden** auf **X**, um den Administratormodus zu beenden:

![Beenden des Administratormodus auf der Website für die Dokumentkontrolle](../media/tracking-site-exit-admin-icon.png)

Eine Anleitung zur Verwendung der Website für die Dokumentkontrolle finden Sie unter [Benutzerhandbuch: Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung von Azure Information Protection](client-track-revoke.md).

### <a name="using-powershell-to-register-labeled-documents-with-the-document-tracking-site"></a>Verwenden von PowerShell zum Registrieren von bezeichneten Dokumenten bei der Website zur Dokumentennachverfolgung

Zum Nachverfolgen und Widerrufen eines Dokuments muss es zunächst bei der Website zur Dokumentnachverfolgung registriert werden. Diese Aktion wird ausgeführt, wenn Benutzer bei Verwendung des Azure Information Protection-Clients im Datei-Explorer oder über ihre Office-Apps die Option **Track and revoke** (Verfolgen und widerrufen) auswählen.

Wenn Sie Dateien für Benutzer mit dem Cmdlet [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel) bezeichnen und schützen, können Sie den Parameter *EnableTracking* verwenden, um die Dateien bei der Website zur Dokumentnachverfolgung zu registrieren. Beispiel:

```ps
Set-AIPFileLabel -Path C:\Projects\ -LabelId ade72bf1-4714-4714-4714-a325f824c55a -EnableTracking
```

## <a name="usage-logging-for-the-document-tracking-site"></a>Verwendungsprotokollierung für die Website für die Dokumentkontrolle

Für die Dokumentkontrolle sind zwei Felder in den Verwendungsprotokolldateien relevant: **AdminAction** und **ActingAsUser**.

**AdminAction:** Dieses Feld hat den Wert „true“, wenn ein Administrator die Website für die Dokumentkontrolle im Administratormodus verwendet, um beispielsweise ein Dokument im Auftrag eines Benutzers zu sperren oder um zu ermitteln, wann es freigegeben wurde. Wenn sich ein Benutzer bei der Website für die Dokumentkontrolle anmeldet, ist dieses Feld leer.

**ActingAsUser:** Wenn das Feld „AdminAction“ den Wert „true“ hat, enthält dieses Feld den Namen des Benutzers, in dessen Auftrag der Administrator als gesuchter Benutzer oder Besitzer des Dokuments handelt. Wenn sich ein Benutzer bei der Website für die Dokumentkontrolle anmeldet, ist dieses Feld leer. 

Bei einigen Anforderungstypen wird auch protokolliert, wie Benutzer und Administratoren die Website für die Dokumentkontrolle verwenden. Der Anforderungstyp **RevokeAccess** wird beispielsweise verwendet, wenn ein Benutzer oder Administrator im Auftrag eines Benutzers ein Dokument auf der Website für die Dokumentkontrolle gesperrt hat. Verwenden Sie diesen Anforderungstyp in Kombination mit dem Feld „AdminAction“, um zu ermitteln, ob ein Benutzer sein eigenes Dokument gesperrt hat („AdminAction“ ist leer) oder ob ein Administrator ein Dokument im Namen eines Benutzers gesperrt hat („AdminAction“ hat den Wert „true“).

Weitere Informationen zur Verwendungs Protokollierung finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](../log-analyze-usage.md)

## <a name="next-steps"></a>Nächste Schritte
Sie haben nun die Website für die Dokumentkontrolle für den Azure Information Protection-Client konfiguriert. Unter den folgenden Links finden Sie zusätzliche Informationen, die Sie ggf. zur Unterstützung dieses Clients benötigen:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

