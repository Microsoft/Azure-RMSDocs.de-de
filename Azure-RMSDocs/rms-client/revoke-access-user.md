---
title: Dokument Zugriff widerrufen-Azure Information Protection
description: Beschreibt, wie Endbenutzer den AIP-Client verwenden können, um den Dokument Zugriff für Dokumente aufzuheben, die Sie geschützt haben.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/21/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.subservice: doctrack
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: abb96719d51658226211653b4ab4d171fcaa6b2e
ms.sourcegitcommit: efeb486e49c3e370d7fd8244687cd3de77cd8462
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97592744"
---
# <a name="user-guide-revoke-document-access-with-azure-information-protection-public-preview"></a>Benutzerhandbuch: widerrufen des Dokument Zugriffs mit Azure Information Protection (öffentliche Vorschau)

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden [Sie im Benutzerhandbuch: nachverfolgen und widerrufen Ihrer Dokumente bei Verwendung des klassischen AIP-Clients](client-track-revoke.md). *

In diesem Artikel wird beschrieben, wie Sie den Zugriff für Dokumente widerrufen, die Sie vor Microsoft Office geschützt haben.

Durch das Aufheben des Zugriffs auf ein geschütztes Dokument wird verhindert, dass andere Benutzer auf das Dokument zugreifen, auch wenn Sie Ihnen zuvor Zugriff erteilt haben. Weitere Informationen finden Sie unter [User Guide: klassifizieren und schützen mit dem Azure Information Protection Unified Bezeichnung-Client](clientv2-classify-protect.md).

Nachverfolgen und widerrufen von Features für den Unified-Bezeichnungs Client befinden sich derzeit in der Vorschau In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

## <a name="revoke-access-from-microsoft-office-apps"></a>Zugriff von Microsoft Office-Apps widerrufen

So widerrufen Sie den Zugriff aus Word, Excel oder PowerPoint:

1. Öffnen Sie die geschützte Datei, deren Zugriff Sie widerrufen möchten. Dabei muss es sich um eine Datei handeln, in der *Sie* den Schutz mithilfe Ihres *aktuellen* Benutzerkontos angewendet haben.

    > [!TIP]
    > Wenn Sie nur eine Bezeichnung und einen Schutz angewendet haben, können Sie den Zugriff in derselben Sitzung nicht widerrufen. Öffnen Sie das Dokument erneut, wenn Sie den Zugriff widerrufen müssen.

1. Klicken Sie **auf der Register** Karte **Startseite** auf die Schaltfläche Vertraulichkeit, und wählen Sie **Zugriff widerrufen**

    :::image type="content" source="../media/track-revoke-word.png" alt-text="Wählen Sie Zugriff von Microsoft Word widerrufen aus.":::

    > [!NOTE]
    > Diese Option wird nicht angezeigt? Weitere Informationen finden Sie [unten](#dont-see-the-revoke-access-option)in den möglichen Szenarios.
    >
 
1. Klicken Sie in der angezeigten Bestätigungsmeldung auf **Ja** , um den Vorgang fortzusetzen.

Der Zugriff wird widerrufen, und andere Benutzer können nicht mehr auf das Dokument zugreifen.

### <a name="dont-see-the-revoke-access-option"></a>Wird die Option "Zugriff widerrufen" nicht angezeigt?

Wenn die Option zum **widerrufen des Zugriffs** im Menü **Sensitivität** nicht angezeigt wird, können Sie eines der folgenden Szenarien verwenden:

- Sie haben möglicherweise soeben den Schutz in dieser Sitzung angewendet. Wenn dies der Fall ist, schließen Sie das Dokument, und öffnen Sie es erneut, um es erneut zu versuchen.

- Möglicherweise wird ein ungeschütztes Dokument angezeigt. Das Aufheben des Zugriffs ist nur für geschützte Dokumente relevant.

- Möglicherweise ist die neueste Version von AIP Unified Bezeichnung-Client nicht installiert, oder Sie müssen Ihre Office-Apps oder den Computer nach der Installation neu starten. 

    Weitere Informationen finden [Sie im Benutzerhandbuch: herunterladen und Installieren des Azure Information Protection Clients](install-client-app.md).

## <a name="revoking-access-where-the-document-protection-has-been-changed-on-a-copy"></a>Aufheben des Zugriffs, bei dem der Dokument Schutz für eine Kopie geändert wurde

Wenn ein anderer Benutzer die Bezeichnung oder den Schutz für eine Kopie des Dokuments geändert hat, wird der Zugriff in dieser Kopie des Dokuments *nicht widerrufen* . 

Dies liegt daran, dass das Nachverfolgen und widerrufen des Zugriffs mithilfe eines eindeutigen contentid-Werts erfolgt, der sich bei jeder Änderung des Schutzes ändert.

> [!IMPORTANT]
> Wenn Sie der Ansicht sind, dass ein Benutzer die Bezeichnung oder Schutz Ebene für ein Dokument geändert hat und Sie den Zugriff widerrufen müssen, wenden Sie sich an einen Systemadministrator, damit Sie den Zugriff auf diese Kopie des Dokuments widerrufen können.
> 
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie unter

- [AIP Unified Bezeichnung Client-Benutzerhandbuch](clientv2-user-guide.md)
- [AIP Unified Bezeichnung Client-Administrator Handbuch](clientv2-admin-guide.md)
- [Bekannte Probleme beim Nachverfolgen und widerrufen des Zugriffs auf Dokumente](../known-issues.md#tracking-and-revoking-document-access-public-preview)