---
title: 'Vorgehensweise: Verwenden integrierter Rechte | Azure RMS'
description: "Erläutert die integrierten Rechte, die das RMS SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: 9d99bc0589d3dbbc1669d08941d991363f224221
ms.openlocfilehash: 09d9b357e9bde0fe0f4fbb7870a415953b8df59b


---

# Vorgehensweise: Verwenden integrierter Rechte

Dieses Thema erläutert die integrierten Rechte, die das Microsoft Rights Management SDK 4.2 bereitstellt, und die Nutzungseinschränkungen, die eine App im Rahmen dieser Einschränkungen erzwingen soll. Die folgende Tabelle zeigt die integrierten Rechte, allgemeinen Rechte, editierbaren Dokumentrechte und E-Mail-Rechte gefolgt von einer Beschreibung und den Werten je nach Betriebssystem an.

**Hinweis**: Weitere Informationen zum Linux-SDK finden Sie in der Quelldatei *rights.h*.

## Allgemeine Rechte ##

| Right | Beschreibung | Android | iOS und OS X | Windows Store und Windows Phone | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **All** | Eine Auflistung aller allgemeinen Rechte. | [CommonRights.All](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL) | [MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)| [CommonRights.All</strong>](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)| [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)|
| **Besitzer**| Erteilt die vollständige Kontrolle über die geschützten Inhalte. |  [CommonRights.Owner](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner) |[MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_) |[CommonRights.Owner](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner) |  [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)|
| **Anzeigen** | Das Recht, geschützte Inhalte anzuzeigen. Wenn dieses Recht gewährt wird, ermöglicht die Anwendung in der Regel dem Benutzer das Öffnen und Anzeigen von geschützten Inhalten; allerdings sind zusätzliche Rechte erforderlich, um den Inhalt zu ändern, zu extrahieren, weiterzuleiten oder zu speichern. |  [CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View) | [MSCommonRights view](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)|[CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View) | [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html) |


## Editierbare Dokumentrechte ##

| Right | Beschreibung | Android | iOS und OS X | Windows Store und Windows Phone | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **All** | Eine Auflistung, die alle editierbaren Dokumentrechte enthält.| [EditableDocumentRights.All](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL) | [MSEditableDocumentRights all](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.All](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all) |[EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Kommentar** | Das Recht, dem Dokument Kommentare hinzuzufügen. | [EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)|[MSEditableDocumentRights comment](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) |[EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)| [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Bearbeiten** | Das Recht, geschützte Inhalte zu bearbeiten und im gleichen geschützten Format zu speichern. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Ändern geschützter Inhalte und das Speichern der Änderungen in der gleichen Datei. | [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit) | [MSEditableDocumentRights edit](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit) | [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html) |
| **Exportieren** | Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem anderen durch AD RMS geschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App dem Benutzer das Speichern geschützter Inhalte in anderen AD RMS-geschützten Formaten; zum Beispiel, wenn die Anwendung eine *Speichern unter*-Funktionalität implementiert. | [EditableDocumentRights.Export](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export) | [MSEditableDocumentRights exportable](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) |[EditableDocumentRights.Export](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export) | [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Extrahieren** | Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Kopieren und Einfügen von Daten aus geschützten Inhalten. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Benutzer auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für E-Mails. |  [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract) |[MSEditableDocumentRights extract](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract) |  [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Drucken** | Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel dem Benutzer das Drucken geschützter Inhalte. Dieses Recht hat den gleichen Wert wie das Print-Recht für E-Mails. | [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print) |  [MSEditableDocumentRights print](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)| [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print) | [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
 

## E-Mail-Rechte ##

| Right | Beschreibung | Android | iOS und OS X | Windows Store und Windows Phone | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **All** |Eine Auflistung, die alle E-Mail-Rechte enthält. |  [EmailRights.All](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL) | [MSEmailRights all](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.All](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)|[EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Extrahieren** | Das Recht zum Extrahieren des Inhalts aus einem geschützten Format und das Einfügen in einem ungeschützten Format. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Kopieren und Einfügen von Daten aus einer geschützten Nachricht. Wenn die App eine <em>Speichern unter</em>-Funktionalität implementiert, kann die Anwendung es dem Empfänger auch ermöglichen, andere geschützte Inhalte in ungeschützten Formaten und anderen geschützten Formaten zu speichern. Dieses Recht hat den gleichen Wert wie das Extract-Recht für editierbare Dokumente. | [EmailRights.Extract](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract) | [MSEmailRights extract](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Extract</strong>](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract) | [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html) |
|**Weiterleiten**| Das Recht, eine geschützte Nachricht weiterzuleiten. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Weiterleiten einer geschützten Nachricht.| [<strong>EmailRights.Forward</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward) | [MSEmailRights forward](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Forward](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward) | [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html) |
|**Drucken** | Das Recht, geschützte Inhalte zu drucken. Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Drucken einer geschützten Nachricht. Dieses Recht hat den gleichen Wert wie das Print-Recht für editierbare Dokumente. | [EmailRights.Print](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print) |[MSEmailRights print](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Print](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print) | [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Antwort** | Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht. | [EmailRights.Reply](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply) | [MSEmailRights reply](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Reply](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply) | [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Allen antworten** | Wenn dieses Recht gewährt wird, ermöglicht die App in der Regel einem E-Mail-Empfänger das Beantworten einer geschützten Nachricht an alle Empfänger der Nachricht und das Einschließen einer Kopie der ursprünglichen Nachricht. | [EmailRights.ReplyAll</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll) | [MSEmailRights replyAll](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.ReplyAll](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall) | [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|



<!--HONumber=Sep16_HO3-->


