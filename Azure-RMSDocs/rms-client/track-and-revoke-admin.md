---
title: Nachverfolgen und widerrufen des Zugriffs Azure Information Protection
description: Beschreibt, wie Administratoren den Dokument Zugriff für geschützte Dokumente nachverfolgen und bei Bedarf den Zugriff widerrufen können.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 01/20/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.subservice: doctrack
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: e3d9c81c42c202fc09dd6ab11559c915bdfeafef
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809852"
---
# <a name="administrator-guide-track-and-revoke-document-access-with-azure-information-protection-public-preview"></a>Administrator Handbuch: nachverfolgen und widerrufen des Zugriffs auf Dokumente mit Azure Information Protection (öffentliche Vorschau)

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden [Sie unter Administrator Handbuch: Konfigurieren und Verwenden der dokumentenverfolgung für AIP mit dem klassischen Client](client-admin-guide-document-tracking.md). *

Wenn Sie ein Upgrade auf [Version 2.9.111.0](unifiedlabelingclient-version-release-history.md#version-291110) oder höher durchgeführt haben, werden alle geschützten Dokumente, die noch nicht für die Nachverfolgung registriert sind, automatisch registriert, wenn Sie das nächste Mal über den einheitlichen AIP-Beschriftungs Client geöffnet werden. Geschützte Dokumente werden zum Nachverfolgen und widerrufen unterstützt, auch wenn Sie nicht als bezeichnet werden.

Wenn Sie ein Dokument für die Nachverfolgung registrieren, können [Microsoft 365 globalen Administratoren](/microsoft-365/admin/add-users/about-admin-roles#commonly-used-microsoft-365-admin-center-roles) Zugriffs Details verfolgen, einschließlich erfolgreicher Zugriffsereignisse und abgelehnter Versuche, und den Zugriff bei Bedarf widerrufen. 

Nachverfolgen und widerrufen von Features für den Unified-Bezeichnungs Client befinden sich derzeit in der Vorschau In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

## <a name="track-document-access"></a>Dokument Zugriff überprüfen

Globale Administratoren können den Zugriff auf geschützte Dokumente über PowerShell mithilfe der für das geschützte Dokument bei der Registrierung generierten **contentid** nachverfolgen.

So zeigen **Sie Details zum Dokument Zugriff an**:

Verwenden Sie die folgenden Cmdlets, um nach Details für das Dokument zu suchen, das Sie nachverfolgen möchten:

1. Suchen Sie den Wert **contentid** für das Dokument, das Sie nachverfolgen möchten.
    
    Verwenden Sie das [Get-aipservicedocumentlog](/powershell/module/aipservice/get-aipservicedocumentlog) , um mithilfe des Datei namens und/oder der e-Mail-Adresse des Benutzers, der den Schutz angewendet hat, nach einem Dokument zu suchen.
    
    Beispiel:
        
    ```PowerShell
    Get-AipServiceDocumentLog -ContentName "test.docx" -Owner “alice@contoso.com” -FromTime "12/01/2020 00:00:00" -ToTime "12/31/2020 23:59:59"
    ```
 
    Dieser Befehl gibt die **contentid** für alle übereinstimmenden, geschützten Dokumente zurück, die für die Nachverfolgung registriert sind.

    > [!NOTE]
    > Geschützte Dokumente werden für die Überwachung registriert, wenn Sie zum ersten Mal auf einem Computer geöffnet werden, auf dem der Unified-Bezeichnungs Client installiert ist Wenn dieser Befehl die contentid für die geschützte Datei nicht zurückgibt, öffnen Sie Sie auf einem Computer, auf dem der Unified-Bezeichnung-Client installiert ist, um das Dokument für die Nachverfolgung zu registrieren.

1. Verwenden Sie das Cmdlet [Get-aipservicetrackinglog](/powershell/module/aipservice/get-aipservicetrackinglog) mit der **contentid** Ihres Dokuments, um die Verfolgungs Daten zurückzugeben.

    Beispiel:
    
    ```PowerShell
    Get-AipServiceTrackingLog -ContentId c03bf90c-6e40-4f3f-9ba0-2bcd77524b87
    ```

    Es werden nach Verfolgungs Daten zurückgegeben, einschließlich e-Mail-Nachrichten, die versuchen, auf zuzugreifen, ob der Zugriff gewährt oder verweigert wurde, Uhrzeit und Datum des Versuchs sowie Domäne und Speicherort, aus denen der Zugriffs Versuch stammt.

## <a name="revoke-document-access-from-powershell"></a>Aufheben des Zugriffs auf Dokumente von PowerShell aus

Globale Administratoren können den Zugriff für jedes geschützte Dokument, das in Ihren lokalen Inhalts Freigaben gespeichert ist, mithilfe des Cmdlets [Set-aipservicedocumentrevoked](/powershell/module/aipservice/set-aipservicedocumentrevoked) widerrufen.

1. Suchen Sie den Wert **contentid** für das Dokument, für das Sie den Zugriff widerrufen möchten.
    
    Verwenden Sie das [Get-aipservicedocumentlog](/powershell/module/aipservice/get-aipservicedocumentlog) , um mithilfe des Datei namens und/oder der e-Mail-Adresse des Benutzers, der den Schutz angewendet hat, nach einem Dokument zu suchen.
    
    Beispiel:
        
    ```PowerShell
    Get-AipServiceDocumentLog -ContentName "test.docx" -Owner “alice@contoso.com” -FromTime "12/01/2020 00:00:00" -ToTime "12/31/2020 23:59:59"
    ```

    Die zurückgegebenen Daten enthalten den Wert "contentid" für Ihr Dokument.

    > [!TIP]
    > Nur Dokumente, die für die Nachverfolgung geschützt und registriert wurden, haben einen **contentid** -Wert. 
    >
    > Wenn Ihr Dokument keine **contentid** hat, öffnen Sie es auf einem Computer mit installiertem Unified-Bezeichnung-Client, um die Datei für die Nachverfolgung zu registrieren.

1. Verwenden Sie [Set-aipservicedocumentrevoked](/powershell/module/aipservice/set-aipservicedocumentrevoked) mit der contentid Ihres Dokuments, um den Zugriff zu widerrufen.

    Beispiel:

    ```PowerShell
    Set-AipServiceDocumentRevoked -ContentId 0e421e6d-ea17-4fdb-8f01-93a3e71333b8 -IssuerName testIssuer
    ```

> [!NOTE]
> Wenn der [Offline Zugriff](/microsoft-365/compliance/encryption-sensitivity-labels#assign-permissions-now) zulässig ist, können Benutzer weiterhin auf die Dokumente zugreifen, die widerrufen wurden, bis der Offline Richtlinien Zeitraum abläuft. 
> 

> [!TIP]
> Benutzer können auch den Zugriff für alle Dokumente widerrufen, in denen Sie den Schutz direkt über das **Vertraulichkeits** Menü in Ihren Office-Apps angewendet haben. Weitere Informationen finden Sie [im Benutzerhandbuch: widerrufen des Zugriffs auf Dokumente mit Azure Information Protection](revoke-access-user.md)

### <a name="un-revoke-access"></a>Aufheben der Sperrung des Zugriffs

Wenn Sie den Zugriff auf ein bestimmtes Dokument versehentlich widerrufen haben, verwenden Sie den gleichen **contentid** -Wert mit dem Cmdlet " [Clear-aipservicedocumentrevoked](/powershell/module/aipservice/clear-aipservicedocumentrevoked) ", um den Zugriff aufzuheben. 

Beispiel:

```PowerShell
Clear-AipServiceDocumentRevoked -ContentId   0e421e6d-ea17-4fdb-8f01-93a3e71333b8 -IssuerName testIssuer
```

Der Benutzer, den Sie im **IssuerName** -Parameter definiert haben, wird der Zugriff auf Dokumente gewährt.

## <a name="turn-off-track-and-revoke-features-for-your-tenant"></a>Deaktivieren der Nachverfolgung und widerrufen von Features für Ihren Mandanten

Wenn Sie die Funktionen zum Nachverfolgen und widerrufen für Ihren Mandanten deaktivieren müssen, z. b. für Datenschutzanforderungen in Ihrer Organisation oder Region, führen Sie die beiden folgenden Schritte aus:

1. Führen Sie das Cmdlet " [Deaktivieren-aipservicedocumenttrackingfeature](/powershell/module/aipservice/disable-aipservicedocumenttrackingfeature) " aus.

1. Legen Sie die erweiterte Client Einstellung [enabletrackandrevoke](clientv2-admin-guide-customizations.md#turn-off-document-tracking-features-public-preview) auf **false** fest. 

Die dokumentenverfolgung und die Optionen zum Widerrufen des Zugriffs werden für Ihren Mandanten deaktiviert:

- Durch das Öffnen geschützter Dokumente mit dem AIP Unified Bezeichnung-Client werden die Dokumente nicht mehr für die Nachverfolgung und den Widerruf registriert.
- Zugriffsprotokolle werden nicht gespeichert, wenn geschützte Dokumente, die bereits registriert sind, geöffnet werden. Zugriffsprotokolle, die gespeichert wurden, bevor Sie diese Features ausschalten, sind weiterhin verfügbar. 
- Administratoren können den Zugriff über PowerShell nicht nachverfolgen oder widerrufen, und Endbenutzern wird die Menüoption " [**widerrufen**](revoke-access-user.md#revoke-access-from-microsoft-office-apps) " in Ihren Office-Apps nicht mehr angezeigt.

> [!NOTE]
> Legen Sie zum Aktivieren und widerrufen von " [enabletrackandrevoke](clientv2-admin-guide-customizations.md#turn-off-document-tracking-features-public-preview) " den Wert " **true**" fest, und führen Sie auch das Cmdlet " [enable-aipservicedocumenttrackingfeature](/powershell/module/aipservice/enable-aipservicedocumenttrackingfeature) " aus.
>
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie unter

- [AIP Unified Bezeichnung Client-Benutzerhandbuch](clientv2-user-guide.md)
- [AIP Unified Bezeichnung Client-Administrator Handbuch](clientv2-admin-guide.md)
- [Bekannte Probleme beim Nachverfolgen und widerrufen von Features](../known-issues.md#known-issues-for-track-and-revoke-features-public-preview)
