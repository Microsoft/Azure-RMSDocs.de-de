---
title: 'Vorgehensweise: Verwenden integrierter Rechte | Azure RMS'
description: "Erläutert die integrierten Rechte, die das RMS SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experimental: true
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 4da2bebb10965e99c2e788f035ae8151777700b9


---

# Vorgehensweise: Verwenden integrierter Rechte

Dieses Thema erläutert die integrierten Rechte, die das Microsoft Rights Management SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll. Im Folgenden werden die integrierten Rechte, allgemeinen Rechte, editierbaren Dokumentrechte und E-Mail-Rechte gefolgt von einer Beschreibung und den Werten je nach Betriebssystem erläutert.

**Hinweis**: Weitere Informationen zum Linux-SDK finden Sie in der Quelldatei *rights.h*.

## Allgemeine Rechte ##

**All** – Eine Auflistung aller allgemeinen Rechte.
- Android: [CommonRights.All](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL)
- iOS und OS X: [MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Store und Windows Phone: [CommonRights.All</strong>](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)
- Linux: [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

** Owner** – Das Owner-Recht erteilt die vollständige Kontrolle über die geschützten Inhalte.
- Android: [<strong>CommonRights.Owner](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner)
- iOS und OS X: [MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Store und Windows Phone: [CommonRights.Owner](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner)
- Linux: [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**View** – Das Recht, geschützte Inhalte anzuzeigen. Wenn dieses Recht gewährt wird, ermöglicht die Anwendung in der Regel dem Benutzer das Öffnen und Anzeigen von geschützten Inhalten; allerdings sind zusätzliche Rechte erforderlich, um den Inhalt zu ändern, zu extrahieren, weiterzuleiten oder zu speichern.

- Android: [CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- iOS und OS X: [MSCommonRights view](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Store und Windows Phone: [CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- Linux: [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## Editierbare Dokumentrechte ##
**All** – Eine Auflistung, die alle editierbaren Dokumentrechte enthält.
- Android:[EditableDocumentRights.All](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL)
- iOS und OS X: [MSEditableDocumentRights all](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.All](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all)
- Linux: [EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Comment** – Das Recht, dem Dokument Kommentare hinzuzufügen.
- Android: [EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)
- iOS und OS X: [MSEditableDocumentRights comment](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)
- Linux: [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Edit** – Das Recht, geschützte Inhalte zu bearbeiten und im gleichen geschützten Format zu speichern. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Ändern geschützter Inhalte und das Speichern der Änderungen in der gleichen Datei.
- Android: [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit)
- iOS und OS X: [MSEditableDocumentRights edit](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit)
- Linux: [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Export** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem anderen durch AD RMS geschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App dem Benutzer das Speichern geschützter Inhalte in anderen AD RMS-geschützten Formaten; zum Beispiel, wenn die Anwendung eine *Speichern unter*-Funktionalität implementiert.

- Android: [EditableDocumentRights.Export](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export)
- iOS und OS X: [MSEditableDocumentRights exportable](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Export](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export)
- Linux: [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Kopieren und Einfügen von Daten aus geschützten Inhalten. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Benutzer auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für E-Mails.

- Android: [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract)
- iOS und OS X: [MSEditableDocumentRights extract](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract)
- Linux: [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Drucken geschützter Inhalte. Dieses Recht hat den gleichen Wert wie das Print-Recht für E-Mails.

- Android: [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print)
- iOS und OS X: [MSEditableDocumentRights print](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Store und Windows Phone: [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print)
- Linux: [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## E-Mail-Rechte ##

**All** – Eine Auflistung, die alle E-Mail-Rechte enthält.
- Android: [EmailRights.All](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL)
- iOS und OS X: [MSEmailRights all](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.All](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)
- Linux: [EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Extract** – Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Kopieren und Einfügen von Daten aus einer geschützten Nachricht. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Empfänger auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für editierbare Dokumente.

- Android: [EmailRights.Extract](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract)
- iOS und OS X: [MSEmailRights extract](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Extract</strong>](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract)
- Linux: [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Forward** – Das Recht, eine geschützte Nachricht weiterzuleiten. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Weiterleiten einer geschützten Nachricht.
- Android: [<strong>EmailRights.Forward</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward)
- iOS und OS X: [MSEmailRights forward](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Forward](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward)
- Linux: [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Print** – Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Drucken einer geschützten Nachricht. Dieses Recht hat den gleichen Wert wie das Print-Recht für editierbare Dokumente.

- Android: [EmailRights.Print](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print)
- iOS und OS X: [MSEmailRights print](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Print](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print)
- Linux: [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Reply** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.Reply](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply)
- iOS und OS X: [MSEmailRights reply](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.Reply](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply)
- Linux: [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**ReplyAll** – Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht an alle Empfänger der Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht.

- Android: [EmailRights.ReplyAll</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll)
- iOS und OS X: [MSEmailRights replyAll](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Store und Windows Phone: [EmailRights.ReplyAll](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall)
- Linux: [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

 

 

 



<!--HONumber=Aug16_HO4-->


