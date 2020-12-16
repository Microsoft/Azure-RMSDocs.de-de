---
title: Nachverfolgen und widerrufen des Zugriffs Azure Information Protection
description: Beschreibt, wie Administratoren den Dokument Zugriff für geschützte Dokumente nachverfolgen und bei Bedarf den Zugriff widerrufen können.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/08/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.subservice: doctrack
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: ac4e506d3c3a6f582975a435a7e9f1e327068ac2
ms.sourcegitcommit: efeb486e49c3e370d7fd8244687cd3de77cd8462
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97592747"
---
# <a name="administrator-guide-track-and-revoke-document-access-with-azure-information-protection-public-preview"></a>Administrator Handbuch: nachverfolgen und widerrufen des Zugriffs auf Dokumente mit Azure Information Protection (öffentliche Vorschau)

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden [Sie unter Administrator Handbuch: Konfigurieren und Verwenden der dokumentenverfolgung für AIP mit dem klassischen Client](client-admin-guide-document-tracking.md). *

Wenn Sie ein Upgrade auf [Version 2.9.109.0](unifiedlabelingclient-version-release-history.md#version-291090-public-preview) oder höher durchgeführt haben, werden alle geschützten Dokumente, die noch nicht für die Nachverfolgung registriert sind, automatisch registriert, wenn Sie das nächste Mal über den einheitlichen AIP-Beschriftungs Client geöffnet werden.

Wenn Sie ein Dokument für die Nachverfolgung registrieren, können globale Administratoren von AIP Zugriffs Details verfolgen, einschließlich erfolgreicher Zugriffsereignisse und verweigerter Versuche, und den Zugriff bei Bedarf widerrufen. 

Nachverfolgen und widerrufen von Features für den Unified-Bezeichnungs Client befinden sich derzeit in der Vorschau In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

## <a name="track-document-access"></a>Dokument Zugriff überprüfen

Administratoren können den Zugriff auf geschützte Dokumente über PowerShell mithilfe der für das geschützte Dokument bei der Registrierung generierten contentid nachverfolgen.

So zeigen **Sie Details zum Dokument Zugriff an**:

Verwenden Sie die folgenden Cmdlets, um nach Details für das Dokument zu suchen, das Sie nachverfolgen möchten:

1. Suchen Sie den Wert **contentid** für das Dokument, das Sie nachverfolgen möchten.
    
    Verwenden Sie das [Get-aipservicedocumentlog](/powershell/module/aipservice/get-aipservicedocumentlog) , um mithilfe des Datei namens und/oder der e-Mail-Adresse des Benutzers, der den Schutz angewendet hat, nach einem Dokument zu suchen.
    
    Beispiel:
        
    ```PowerShell
    PS C:\>Get-AipServiceDocumentLog -ContentName "test.docx" -OwnerEmail “alice@contoso.com” -FromTime "12/01/2020 00:00:00" -ToTime "12/31/2020 23:59:59"
    ```
 
    Dieser Befehl gibt die **contentid** für alle übereinstimmenden, geschützten Dokumente zurück, die für die Nachverfolgung registriert sind.

    > [!NOTE]
    > Geschützte Dokumente werden für die Überwachung registriert, wenn Sie zum ersten Mal auf einem Computer geöffnet werden, auf dem der Unified-Bezeichnungs Client installiert ist Wenn dieser Befehl die contentid für die geschützte Datei nicht zurückgibt, öffnen Sie Sie auf einem Computer, auf dem der Unified-Bezeichnung-Client installiert ist, um das Dokument für die Nachverfolgung zu registrieren.

1. Verwenden Sie das Cmdlet [Get-aipservicetrackinglog](/powershell/module/aipservice/get-aipservicetrackinglog) mit der **contentid** Ihres Dokuments, um die Verfolgungs Daten zurückzugeben.

    Beispiel:
    
    ```PowerShell
    PS C:\>Get-Get-AipServiceTrackingLog -ContentId c03bf90c-6e40-4f3f-9ba0-2bcd77524b87
    ```

    Es werden nach Verfolgungs Daten zurückgegeben, einschließlich e-Mail-Nachrichten, die versuchen, auf zuzugreifen, ob der Zugriff gewährt oder verweigert wurde, Uhrzeit und Datum des Versuchs sowie Domäne und Speicherort, aus denen der Zugriffs Versuch stammt.

## <a name="revoke-document-access-from-powershell"></a>Aufheben des Zugriffs auf Dokumente von PowerShell aus

Administratoren können den Zugriff für alle geschützten Dokumente, die in Ihren lokalen Inhalts Freigaben gespeichert sind, mithilfe des Cmdlets [Set-aipservicedocumentrevoked](/powershell/module/aipservice/set-aipservicedocumentrevoked) widerrufen. 

1. Suchen Sie den Wert contentid für das Dokument, für das Sie den Zugriff widerrufen möchten.
    
    Verwenden Sie das [Get-aipservicedocumentlog](/powershell/module/aipservice/get-aipservicedocumentlog) , um mithilfe des Datei namens und/oder der e-Mail-Adresse des Benutzers, der den Schutz angewendet hat, nach einem Dokument zu suchen.
    
    Beispiel:
        
    ```PowerShell
    PS C:\>Get-AipServiceDocumentLog -ContentName "test.docx" -OwnerEmail “alice@contoso.com” -FromTime "12/01/2020 00:00:00" -ToTime "12/31/2020 23:59:59"
    ```

    Die zurückgegebenen Daten enthalten den Wert "contentid" für Ihr Dokument.

    > [!TIP]
    > Nur Dokumente, die für die Nachverfolgung geschützt und registriert wurden, haben einen contentid-Wert. 
    >
    > Wenn Ihr Dokument keine contentid hat, öffnen Sie es auf einem Computer mit installiertem Unified-Bezeichnung-Client, um die Datei für die Nachverfolgung zu registrieren.

1. Verwenden Sie [Set-aipservicedocumentrevoked](/powershell/module/aipservice/set-aipservicedocumentrevoked) mit der contentid Ihres Dokuments, um den Zugriff zu widerrufen.

    Beispiel:

    ```PowerShell
    Set-AipServiceDocumentRevoked -ContentId 0e421e6d-ea17-4fdb-8f01-93a3e71333b8 -IssuerName testIssuer
    ```

> [!TIP]
> Benutzer können auch den Zugriff für alle Dokumente widerrufen, in denen Sie den Schutz direkt über das **Vertraulichkeits** Menü in Ihren Office-Apps angewendet haben. Weitere Informationen finden Sie [im Benutzerhandbuch: widerrufen des Zugriffs auf Dokumente mit Azure Information Protection](revoke-access-user.md)

### <a name="un-revoke-access"></a>Aufheben der Sperrung des Zugriffs

Wenn Sie den Zugriff auf ein bestimmtes Dokument versehentlich widerrufen haben, verwenden Sie den gleichen **contentid** -Wert mit dem Cmdlet " [Clear-aipservicedocumentrevoke](/powershell/module/aipservice/clear-aipservicedocumentrevoke) ", um die Sperrung des Zugriffs aufzuheben. 

Beispiel: 

```PowerShell
Clear-AipServiceDocumentRevoke -ContentId   0e421e6d-ea17-4fdb-8f01-93a3e71333b8 -IssuerName testIssuer
```

Der Benutzer, den Sie im **IssuerName** -Parameter definiert haben, wird der Zugriff auf Dokumente gewährt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie unter

- [AIP Unified Bezeichnung Client-Benutzerhandbuch](clientv2-user-guide.md)
- [AIP Unified Bezeichnung Client-Administrator Handbuch](clientv2-admin-guide.md)
- [Bekannte Probleme beim Nachverfolgen und widerrufen des Zugriffs auf Dokumente](../known-issues.md#tracking-and-revoking-document-access-public-preview)