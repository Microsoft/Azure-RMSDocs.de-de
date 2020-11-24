---
title: 'Vorgehensweise: Verwenden integrierter Rechte | Azure RMS'
description: Erläutert die integrierten Rechte, die das RMS SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
experimental: true
experiment_id: priyamo-TableVsFlatList-20160805
ms.openlocfilehash: 337cb03e6350bafb96f0672f9225ebe613044ea4
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95567973"
---
# <a name="how-to-use-built-in-rights"></a>Vorgehensweise: Verwenden integrierter Rechte

Dieses Thema erläutert die integrierten Rechte, die das Microsoft Rights Management SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll. Im Folgenden werden die integrierten Rechte, allgemeinen Rechte, editierbaren Dokumentrechte und E-Mail-Rechte gefolgt von einer Beschreibung und den Werten je nach Betriebssystem erläutert.

**Hinweis**: Weitere Informationen zum Linux-SDK finden Sie in der Quelldatei *rights.h*.

## <a name="common-rights"></a>Allgemeine Rechte

**All** – Eine Auflistung aller allgemeinen Rechte.
- Android: [CommonRights.All](/previous-versions/windows/desktop/msipcthin2/commonrights-class-java)
- iOS und OS X: [MSCommonRights](/previous-versions/windows/desktop/msipcthin2/mscommonrights-interface-objc) – verwendet „owner“ (Besitzer) und „view“ (Ansicht) zum Implementieren von **All**
- Windows Store und Windows Phone: [CommonRights.All</strong>](/previous-versions/windows/desktop/msipcthin2/commonrights-all)
- Linux: [CommonRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Besitzer** : das Besitzer Recht erteilt die vollständige Kontrolle über die geschützten Inhalte.
- Android: [ <strong> commonrights. Owner](/previous-versions/windows/desktop/msipcthin2/commonrights-class-java)
- iOS und OS X: [MSCommonRights owner](/previous-versions/windows/desktop/msipcthin2/mscommonrights-interface-objc)
- Windows Store und Windows Phone: [CommonRights.Owner](/previous-versions/windows/desktop/msipcthin2/commonrights-owner)
- Linux: [CommonRights::Owner](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**View** – Das Recht, geschützte Inhalte anzuzeigen. Wenn dieses Recht gewährt wird, ermöglicht die Anwendung in der Regel dem Benutzer das Öffnen und Anzeigen von geschützten Inhalten; allerdings sind zusätzliche Rechte erforderlich, um den Inhalt zu ändern, zu extrahieren, weiterzuleiten oder zu speichern.

- Android: [CommonRights.View](/previous-versions/windows/desktop/msipcthin2/commonrights-class-java)
- iOS und OS X: [MSCommonRights view](/previous-versions/windows/desktop/msipcthin2/mscommonrights-interface-objc)
- Windows Store und Windows Phone: [CommonRights.View](/previous-versions/windows/desktop/msipcthin2/commonrights-view)
- Linux: [CommonRights::View](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## <a name="editable-document-rights"></a>Editierbare Dokumentrechte
**All** – Eine Auflistung, die alle editierbaren Dokumentrechte enthält.
- Android: [EditableDocumentRights.All](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-class-java)
- iOS und OS X: [MSEditableDocumentRights all](/previous-versions/windows/desktop/msipcthin2/mseditabledocumentrights-interface-objc)
- Windows Store und Windows Phone: [EditableDocumentRights.All](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-all)
- Linux: [EditableDocumentRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Comment** – Das Recht, dem Dokument Kommentare hinzuzufügen.
- Android: [EditableDocumentRights.Comment](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-class-java)
- iOS und OS X: [MSEditableDocumentRights comment](/previous-versions/windows/desktop/msipcthin2/mseditabledocumentrights-interface-objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Comment](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights--comment)
- Linux: [EditableDocumentRights::Comment](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Edit** – Das Recht, geschützte Inhalte zu bearbeiten und im gleichen geschützten Format zu speichern. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Ändern geschützter Inhalte und das Speichern der Änderungen in der gleichen Datei.
- Android: [EditableDocumentRights.Edit](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-class-java)
- iOS und OS X: [MSEditableDocumentRights edit](/previous-versions/windows/desktop/msipcthin2/mseditabledocumentrights-interface-objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Edit](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-edit)
- Linux: [EditableDocumentRights::Edit](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Export** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem anderen durch AD RMS geschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App dem Benutzer das Speichern geschützter Inhalte in anderen AD RMS-geschützten Formaten; zum Beispiel, wenn die Anwendung eine *Speichern unter*-Funktionalität implementiert.

- Android: [EditableDocumentRights.Export](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-class-java)
- iOS und OS X: [MSEditableDocumentRights exportable](/previous-versions/windows/desktop/msipcthin2/mseditabledocumentrights-interface-objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Export](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-export)
- Linux: [EditableDocumentRights::Export](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Kopieren und Einfügen von Daten aus geschützten Inhalten. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Benutzer auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für E-Mails.

- Android: [EditableDocumentRights.Extract](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-class-java)
- iOS und OS X: [MSEditableDocumentRights extract](/previous-versions/windows/desktop/msipcthin2/mseditabledocumentrights-interface-objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Extract](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-extract)
- Linux: [EditableDocumentRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Drucken geschützter Inhalte. Dieses Recht hat den gleichen Wert wie das Print-Recht für E-Mails.

- Android: [EditableDocumentRights.Print](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-class-java)
- iOS und OS X: [MSEditableDocumentRights print](/previous-versions/windows/desktop/msipcthin2/mseditabledocumentrights-interface-objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Print](/previous-versions/windows/desktop/msipcthin2/editabledocumentrights-print)
- Linux: [EditableDocumentRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## <a name="email-rights"></a>E-Mail-Rechte

**All** – Eine Auflistung, die alle E-Mail-Rechte enthält.
- Android: [EmailRights.All](/previous-versions/windows/desktop/msipcthin2/emailrights-class-java)
- iOS und OS X: [MSEmailRights all](/previous-versions/windows/desktop/msipcthin2/msemailrights-interface-objc)
- Windows Store und Windows Phone: [EmailRights.All](/previous-versions/windows/desktop/msipcthin2/emailrights-all)
- Linux: [EmailRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Kopieren und Einfügen von Daten aus einer geschützten Nachricht. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Empfänger auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für editierbare Dokumente.

- Android: [EmailRights.Extract](/previous-versions/windows/desktop/msipcthin2/emailrights-class-java)
- iOS und OS X: [MSEmailRights extract](/previous-versions/windows/desktop/msipcthin2/msemailrights-interface-objc)
- Windows Store und Windows Phone: [EmailRights.Extract</strong>](/previous-versions/windows/desktop/msipcthin2/emailrights-extract)
- Linux: [EmailRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Forward** – Das Recht, eine geschützte Nachricht weiterzuleiten. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Weiterleiten einer geschützten Nachricht.
- Android: [<strong>EmailRights.Forward</strong>](/previous-versions/windows/desktop/msipcthin2/emailrights-class-java)
- iOS und OS X: [MSEmailRights forward](/previous-versions/windows/desktop/msipcthin2/msemailrights-interface-objc)
- Windows Store und Windows Phone: [EmailRights.Forward](/previous-versions/windows/desktop/msipcthin2/emailrights-forward)
- Linux: [EmailRights::Forward](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Drucken einer geschützten Nachricht. Dieses Recht hat den gleichen Wert wie das Print-Recht für editierbare Dokumente.

- Android: [EmailRights.Print](/previous-versions/windows/desktop/msipcthin2/emailrights-class-java)
- iOS und OS X: [MSEmailRights print](/previous-versions/windows/desktop/msipcthin2/msemailrights-interface-objc)
- Windows Store und Windows Phone: [EmailRights.Print](/previous-versions/windows/desktop/msipcthin2/emailrights-print)
- Linux: [EmailRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Reply** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.Reply](/previous-versions/windows/desktop/msipcthin2/emailrights-class-java)
- iOS und OS X: [MSEmailRights reply](/previous-versions/windows/desktop/msipcthin2/msemailrights-interface-objc)
- Windows Store und Windows Phone: [EmailRights.Reply](/previous-versions/windows/desktop/msipcthin2/emailrights-reply)
- Linux: [EmailRights::Reply](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**ReplyAll** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht an alle Empfänger der Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.ReplyAll</strong>](/previous-versions/windows/desktop/msipcthin2/emailrights-class-java)
- iOS und OS X: [MSEmailRights replyAll](/previous-versions/windows/desktop/msipcthin2/msemailrights-interface-objc)
- Windows Store und Windows Phone: [EmailRights.ReplyAll](/previous-versions/windows/desktop/msipcthin2/emailrights-replyall)
- Linux: [EmailRights::ReplyAll](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)