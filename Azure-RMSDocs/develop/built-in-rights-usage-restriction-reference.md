---
title: 'Vorgehensweise: Verwenden integrierter Rechte | Azure RMS'
description: Erläutert die integrierten Rechte, die das RMS SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: cd9c1ae8873b8f5a8d0440bd017d92d16801219b
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259608"
---
# <a name="how-to-use-built-in-rights"></a>Vorgehensweise: Verwenden integrierter Rechte

Dieses Thema erläutert die integrierten Rechte, die das Microsoft Rights Management SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll. Im Folgenden werden die integrierten Rechte, allgemeinen Rechte, editierbaren Dokumentrechte und E-Mail-Rechte gefolgt von einer Beschreibung und den Werten je nach Betriebssystem erläutert.

**Hinweis**: Weitere Informationen zum Linux-SDK finden Sie in der Quelldatei *rights.h*.

## <a name="common-rights"></a>Allgemeine Rechte

**All** – Eine Auflistung aller allgemeinen Rechte.
- Android: [CommonRights.All](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS und OS X: [MSCommonRights](https://msdn.microsoft.com/library/dn758314.aspx) – verwendet „owner“ (Besitzer) und „view“ (Ansicht) zum Implementieren von **All**
- Windows Store und Windows Phone: [CommonRights.All</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.all.aspx)
- Linux: [CommonRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Owner** – Das Owner-Recht erteilt die vollständige Kontrolle über die geschützten Inhalte.
- Android: [<strong>CommonRights.Owner](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS und OS X: [MSCommonRights owner](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows Store und Windows Phone: [CommonRights.Owner](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.owner.aspx)
- Linux: [CommonRights::Owner](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**View** – Das Recht, geschützte Inhalte anzuzeigen. Wenn dieses Recht gewährt wird, ermöglicht die Anwendung in der Regel dem Benutzer das Öffnen und Anzeigen von geschützten Inhalten; allerdings sind zusätzliche Rechte erforderlich, um den Inhalt zu ändern, zu extrahieren, weiterzuleiten oder zu speichern.

- Android: [CommonRights.View](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS und OS X: [MSCommonRights view](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows Store und Windows Phone: [CommonRights.View](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.view.aspx)
- Linux: [CommonRights::View](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## <a name="editable-document-rights"></a>Editierbare Dokumentrechte
**All** – Eine Auflistung, die alle editierbaren Dokumentrechte enthält.
- Android: [EditableDocumentRights.All](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS und OS X: [MSEditableDocumentRights all](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store und Windows Phone: [EditableDocumentRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.all.aspx)
- Linux: [EditableDocumentRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Comment** – Das Recht, dem Dokument Kommentare hinzuzufügen.
- Android: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS und OS X: [MSEditableDocumentRights comment](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store und Windows Phone: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.comment.aspx)
- Linux: [EditableDocumentRights::Comment](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Edit** – Das Recht, geschützte Inhalte zu bearbeiten und im gleichen geschützten Format zu speichern. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Ändern geschützter Inhalte und das Speichern der Änderungen in der gleichen Datei.
- Android: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS und OS X: [MSEditableDocumentRights edit](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store und Windows Phone: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.edit.aspx)
- Linux: [EditableDocumentRights::Edit](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Export** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem anderen durch AD RMS geschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App dem Benutzer das Speichern geschützter Inhalte in anderen AD RMS-geschützten Formaten; zum Beispiel, wenn die Anwendung eine *Speichern unter*-Funktionalität implementiert.

- Android: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS und OS X: [MSEditableDocumentRights exportable](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store und Windows Phone: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.export.aspx)
- Linux: [EditableDocumentRights::Export](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Kopieren und Einfügen von Daten aus geschützten Inhalten. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Benutzer auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für E-Mails.

- Android: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS und OS X: [MSEditableDocumentRights extract](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store und Windows Phone: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.extract.aspx)
- Linux: [EditableDocumentRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Drucken geschützter Inhalte. Dieses Recht hat den gleichen Wert wie das Print-Recht für E-Mails.

- Android: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS und OS X: [MSEditableDocumentRights print](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store und Windows Phone: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.print.aspx)
- Linux: [EditableDocumentRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## <a name="email-rights"></a>E-Mail-Rechte

**All** – Eine Auflistung, die alle E-Mail-Rechte enthält.
- Android: [EmailRights.All](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS und OS X: [MSEmailRights all](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store und Windows Phone: [EmailRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.all.aspx)
- Linux: [EmailRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Kopieren und Einfügen von Daten aus einer geschützten Nachricht. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Empfänger auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für editierbare Dokumente.

- Android: [EmailRights.Extract](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS und OS X: [MSEmailRights extract](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store und Windows Phone: [EmailRights.Extract</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.extract.aspx)
- Linux: [EmailRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Forward** – Das Recht, eine geschützte Nachricht weiterzuleiten. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Weiterleiten einer geschützten Nachricht.
- Android: [<strong>EmailRights.Forward</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS und OS X: [MSEmailRights forward](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store und Windows Phone: [EmailRights.Forward](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.forward.aspx)
- Linux: [EmailRights::Forward](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Drucken einer geschützten Nachricht. Dieses Recht hat den gleichen Wert wie das Print-Recht für editierbare Dokumente.

- Android: [EmailRights.Print](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS und OS X: [MSEmailRights print](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store und Windows Phone: [EmailRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.print.aspx)
- Linux: [EmailRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Reply** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.Reply](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS und OS X: [MSEmailRights reply](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store und Windows Phone: [EmailRights.Reply](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.reply.aspx)
- Linux: [EmailRights::Reply](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**ReplyAll** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht an alle Empfänger der Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.ReplyAll</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS und OS X: [MSEmailRights replyAll](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store und Windows Phone: [EmailRights.ReplyAll](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.replyall.aspx)
- Linux: [EmailRights::ReplyAll](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)
