---
title: 'Vorgehensweise: Verwenden integrierter Rechte | Azure RMS'
description: "Erläutert die integrierten Rechte, die das RMS SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experimental: true
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: d8fb04fd80e9a84bd7784e48b77e3aa8b045bf2d


---

# Vorgehensweise: Verwenden integrierter Rechte

Dieses Thema erläutert die integrierten Rechte, die das Microsoft Rights Management SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll. Im Folgenden werden die integrierten Rechte, allgemeinen Rechte, editierbaren Dokumentrechte und E-Mail-Rechte gefolgt von einer Beschreibung und den Werten je nach Betriebssystem erläutert.

**Hinweis**: Weitere Informationen zum Linux-SDK finden Sie in der Quelldatei *rights.h*.

## Allgemeine Rechte ##

**All** – Eine Auflistung aller allgemeinen Rechte.
- Android: [CommonRights.All](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL)
- iOS und OS X: [MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Store und Windows Phone: [CommonRights.All</strong>](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)
- Linux: [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

** Owner** – Das Owner-Recht erteilt die vollständige Kontrolle über die geschützten Inhalte.
- Android: [<strong>CommonRights.Owner](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner)
- iOS und OS X: [MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Store und Windows Phone: [CommonRights.Owner](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner)
- Linux: [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**View** – Das Recht, geschützte Inhalte anzuzeigen. Wenn dieses Recht gewährt wird, ermöglicht die Anwendung in der Regel dem Benutzer das Öffnen und Anzeigen von geschützten Inhalten; allerdings sind zusätzliche Rechte erforderlich, um den Inhalt zu ändern, zu extrahieren, weiterzuleiten oder zu speichern.

- Android: [CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- iOS und OS X: [MSCommonRights view](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Store und Windows Phone: [CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- Linux: [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## Editierbare Dokumentrechte ##
**All** – Eine Auflistung, die alle editierbaren Dokumentrechte enthält.
- Android:[EditableDocumentRights.All](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL)
- iOS und OS X: [MSEditableDocumentRights all](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.All](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all)
- Linux: [EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Comment** – Das Recht, dem Dokument Kommentare hinzuzufügen.
- Android: [EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)
- iOS und OS X: [MSEditableDocumentRights comment](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)
- Linux: [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Edit** – Das Recht, geschützte Inhalte zu bearbeiten und im gleichen geschützten Format zu speichern. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Ändern geschützter Inhalte und das Speichern der Änderungen in der gleichen Datei.
- Android: [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit)
- iOS und OS X: [MSEditableDocumentRights edit](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit)
- Linux: [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Export** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem anderen durch AD RMS geschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App dem Benutzer das Speichern geschützter Inhalte in anderen AD RMS-geschützten Formaten; zum Beispiel, wenn die Anwendung eine *Speichern unter*-Funktionalität implementiert.

- Android: [EditableDocumentRights.Export](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export)
- iOS und OS X: [MSEditableDocumentRights exportable](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Export](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export)
- Linux: [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Kopieren und Einfügen von Daten aus geschützten Inhalten. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Benutzer auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für E-Mails.

- Android: [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract)
- iOS und OS X: [MSEditableDocumentRights extract](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract)
- Linux: [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Drucken geschützter Inhalte. Dieses Recht hat den gleichen Wert wie das Print-Recht für E-Mails.

- Android: [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print)
- iOS und OS X: [MSEditableDocumentRights print](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print)
- Linux: [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## E-Mail-Rechte ##

**All** – Eine Auflistung, die alle E-Mail-Rechte enthält.
- Android: [EmailRights.All](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL)
- iOS und OS X: [MSEmailRights all](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.All](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)
- Linux: [EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Kopieren und Einfügen von Daten aus einer geschützten Nachricht. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Empfänger auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für editierbare Dokumente.

- Android: [EmailRights.Extract](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract)
- iOS und OS X: [MSEmailRights extract](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Extract</strong>](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract)
- Linux: [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Forward** – Das Recht, eine geschützte Nachricht weiterzuleiten. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Weiterleiten einer geschützten Nachricht.
- Android: [<strong>EmailRights.Forward</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward)
- iOS und OS X: [MSEmailRights forward](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Forward](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward)
- Linux: [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Drucken einer geschützten Nachricht. Dieses Recht hat den gleichen Wert wie das Print-Recht für editierbare Dokumente.

- Android: [EmailRights.Print](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print)
- iOS und OS X: [MSEmailRights print](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Print](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print)
- Linux: [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Reply** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.Reply](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply)
- iOS und OS X: [MSEmailRights reply](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Reply](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply)
- Linux: [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**ReplyAll** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht an alle Empfänger der Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.ReplyAll</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll)
- iOS und OS X: [MSEmailRights replyAll](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.ReplyAll](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall)
- Linux: [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

 

 

 



<!--HONumber=Sep16_HO5-->


