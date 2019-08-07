---
title: Nachverfolgen und Widerrufen von Dokumenten – Azure Information Protection
description: Nachdem Sie Ihre Dokumente geschützt haben, können Sie verfolgen, wie sie von Benutzern verwendet werden. Bei Bedarf können Sie auch den Zugriff auf diese Dokumente widerrufen, wenn Benutzer nicht mehr in der Lage sein sollen, sie zu lesen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.subservice: doctrack
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 4c95177d767d6047071b4f9c578de4d374e28bfe
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68793482"
---
# <a name="user-guide-track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Benutzerhandbuch: Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung von Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Nachdem Sie Ihre Dokumente mithilfe von Azure Information Protection geschützt haben, können Sie nachverfolgen, wie andere mit Ihren geschützten Dokumenten verfahren. Bei Bedarf können Sie auch den Zugriff auf diese Dokumente widerrufen, wenn Benutzer nicht mehr in der Lage sein sollen, sie zu lesen. Hierfür verwenden Sie die **Website zum Nachverfolgen von Dokumenten**. Auf diese Website können Sie über Windows-Computer, Mac-Computer und sogar Tablets und Smartphones zugreifen.

Wenn Sie auf diese Website zugreifen möchten, melden Sie sich dort an, um Ihre Dokumente zu nachzuverfolgen. Wenn Ihre Organisation über ein [Abonnement verfügt, das das Nachverfolgen und Sperren von Dokumenten unterstützt](https://www.microsoft.com/cloud-platform/azure-information-protection-features), und Ihnen eine Lizenz für dieses Abonnement zugewiesen ist, können Sie sehen, wer versucht hat, die geschützten Dateien zu öffnen. Sie können außerdem sehen, ob dieser Versuch erfolgreich war (ob die betreffenden Personen erfolgreich authentifiziert wurden) oder nicht. Sie können auch jeden Zugriffsversuch der Personen auf das Dokument sowie deren Position zu diesem Zeitpunkt sehen. In seltenen Fällen ist der berichtete Standort möglicherweise nicht genau. Dies ist beispielsweise dann der Fall, wenn ein Benutzer, der ein geschütztes Dokument öffnet, eine VPN-Verbindung verwendet oder sein Computer eine IPv6-Adresse aufweist.

Folgende Aktionen können Sie auf der Website zum Nachverfolgen von Dokumenten ausführen:

- Wenn Sie die Freigabe eines Dokuments aufheben müssen: 
    
    - Klicken Sie auf **Zugriff widerrufen**. Beachten Sie den Zeitraum, für den das Dokument weiterhin verfügbar ist. Entscheiden Sie, ob Sie Personen wissen lassen möchten, dass Sie den Zugriff auf das Dokument widerrufen, das Sie zuvor freigegeben haben, indem Sie eine benutzerdefinierte Meldung bereitstellen. Wenn Sie den Zugriff auf ein Dokument widerrufen, wird das freigegebene Dokument nicht gelöscht, aber autorisierte Benutzer können es nicht mehr öffnen:
        
        ![Symbol zum Widerrufen des Zugriffs auf der Website für die Dokumentenverfolgung](../media/tracking-site-revoke-access-icon.png)
        
- Wenn Sie nach Excel exportieren möchten: 
    
    - Klicken Sie auf **Nach CSV exportieren**, sodass Sie dann die Daten ändern und eigene Ansichten und Diagramme erstellen können:
         
        ![Symbol „In CSV-Datei exportieren“ auf der Website zur Dokumentenverfolgung](../media/tracking-site-export-icon.png)
         
- Wenn Sie E-Mail-Benachrichtigungen konfigurieren möchten: 
     
    - Klicken Sie auf **Einstellungen**, und wählen Sie, wie und ob Sie eine E-Mail erhalten möchten, wenn auf das Dokument zugegriffen wird:
        
        ![Konfigurieren von e-Mail-Benachrichtigungen auf der Website zur Dokument](../media/tracking-site-settings-email.png)

- Wenn Sie für andere Benutzer freigegebene Dokumente nachverfolgen und widerrufen möchten:
    
    - Administratoren für Azure Information Protection können auf das Administratorsymbol klicken, um geschützte Dokumente für Benutzer nachzuverfolgen und wieder zu sperren, wenn diese Benutzer Ihre Dokumente über die Website zum Nachverfolgen von Dokumenten registriert haben. Dieses Symbol wird ausschließlich Administratoren angezeigt:
        
        ![Adminsymbol auf der Website zur Dokumentenverfolgung](../media/tracking-site-admin-icon.png)
        
        Wenn Sie dieses Symbol nicht sehen, obwohl Sie über globale Administratorrechte verfügen, liegt das daran, dass Sie selbst noch keine Dokumente freigegeben haben. Verwenden Sie in diesem Fall die folgende URL, um auf die Website zur Dokumentenverfolgung zu gelangen: https://portal.azurerms.com/#/admin

Sie können nur die von Ihnen geschützten Dokumente nachverfolgen und widerrufen, es sei denn, Sie sind ein Administrator. Sie können nicht Ihre geschützten E-Mails mithilfe der Website für die Dokumentnachverfolgung nachverfolgen.

> [!NOTE] 
> Wenn Ihr Administrator Datenschutzkontrollen für die Website für die Dokumentnachverfolgung konfiguriert hat, können Sie möglicherweise nicht sehen, wenn Benutzer in Ihrer Organisation auf ein von Ihnen nachverfolgtes Dokument zugegriffen haben. Administratoren können alle Benutzer oder nur bestimmte Benutzer ausschließen. Sie können jedoch den Zugriff auf die nachverfolgten Dokumente jederzeit widerrufen.

Um ein von Ihnen geschütztes Dokument nachzuverfolgen, müssen Sie es mit Ihrem Windows-Computer bei der Website für die Dokumentnachverfolgung registrieren. Zu diesem Zweck verwenden Sie entweder den Datei-Explorer oder die Office-Apps.

Wenn Sie über die aktuelle allgemein verfügbare Version des Azure Information Protection Clients verfügen, können Sie das geschützte Dokument auch mit PowerShell registrieren, wenn Sie den *enabletracking* -Parameter mit dem Cmdlet " [Set-aipfilelabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel) " verwenden.

## <a name="using-office-to-track-or-revoke-the-document"></a>Verwenden von Office zum Nachverfolgen oder Widerrufen des Dokuments

Bei den Office-Anwendungen wie Word, Excel und PowerPoint: 

1. Öffnen Sie das geschützte Dokument, das Sie nachverfolgen oder widerrufen möchten.

2. Klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen** > **Nachverfolgen und widerrufen**:

    ![Option „Verwendung nachverfolgen“](../media/track-usage-callout.png)
    
    Wenn Ihnen diese Optionen nicht in Ihren Office-Anwendungen angezeigt werden, hat dies wahrscheinlich einen der folgenden Gründe:
    
    - Der Azure Information Protection-Client ist auf Ihrem Computer nicht installiert.
    
    - Ihre Office-Anwendungen müssen neu gestartet werden.
    
    - Zum Abschließen der Installation muss Ihr Computer neu gestartet werden.
    
Weitere Informationen zum Installieren des Azure Information Protection-Clients finden Sie unter [Herunterladen und Installieren des Azure Information Protection-Clients](install-client-app.md).

## <a name="using-file-explorer-to-track-or-revoke-the-document"></a>Verwenden des Datei-Explorer zum Nachverfolgen oder Widerrufen des Dokuments

1. Klicken Sie mit der rechten Maustaste auf die geschützte Datei, und wählen Sie **Klassifizieren und schützen** aus.

2. Wählen Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Option **Track and revoke** (Nachverfolgen und widerrufen) aus.

    ![Symbol für „Nachverfolgen und widerrufen“ im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“](../media/track-and-revoke.png)


### <a name="using-a-web-browser-to-track-and-revoke-documents-that-you-have-registered"></a>Verwenden eines Webbrowser zum Nachverfolgen und Widerrufen von registrierten Dokumenten

Nachdem Sie das geschützte Dokument mithilfe der Office-Apps oder des Datei-Explorer registriert haben, können Sie diese Dokumente mithilfe eines unterstützten Webbrowsers nachverfolgen und widerrufen:

- Besuchen Sie die [Website für die Dokumentverfolgung](https://go.microsoft.com/fwlink/?LinkId=529562) über Ihren Windows-PC, Macintosh-Computer oder Ihr mobiles Gerät.

    **Unterstützte Browser**: Es wird empfohlen, Internet Explorer mit mindestens Version 10 zu verwenden. Sie können jedoch einen der folgenden Browser verwenden, um die Website für die Dokument Nachverfolgung zu verwenden:

    - Internet Explorer: Mindestens Version 10

    - Internet Explorer 9 mit mindestens MS12-037: Kumulatives Sicherheits Update für Internet Explorer: 12. Juni 2012

    - Mozilla Firefox: Mindestens Version 12

    - Apple Safari 5: Mindestens Version 5

    - Google Chrome: Mindestens Version 18


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    
Weitere Informationen finden Sie im [Administratorhandbuch](client-admin-guide.md) unter [Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection](client-admin-guide-document-tracking.md).
