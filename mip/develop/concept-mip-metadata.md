---
title: Konzepte – Bezeichnung-Metadaten in das MIP SDK
description: Dieser Artikel hilft Ihnen, die Metadaten zu verstehen, die von der Microsoft Information Protection SDK generiert wird.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 11/08/2018
ms.author: tommos
ms.openlocfilehash: 990f729edaa0a2e212812f84fc5a4c63f82e37fb
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56253968"
---
# <a name="microsoft-information-protection-sdk---metadata"></a>Microsoft Information Protection SDK - Metadaten

Das Microsoft Information Protection SDK generiert den Satz von Metadaten, die auf eine Datei angewendet werden soll. Diese Metadaten sind eine Darstellung der Bezeichnung. Dieses Dokument beschreibt die Metadaten, die das SDK generiert wird, um auf e-Mails, Dokumente und andere Datensätze anzuwenden.

## <a name="labels"></a>Bezeichnungen

Bezeichnungen in der Microsoft Information Protection SDK gelten für Informationen, um die Vertraulichkeit dieser Informationen zu beschreiben. Bezeichnungsdaten werden beibehalten, Datei oder ein Datensatz in einem Satz von Schlüssel-Wert-Paare, die die Bezeichnung zu beschreiben. Der Name der Metadaten ist auf der folgenden Struktur erstellt:

`DefinedPrefix_ElementType_GlobalIdentifier_AttributeName`

Bei Anwendung auf Daten, die mit der Bezeichnung Microsoft Information Protection ist das Ergebnis:

`MSIP_Label_GUID_Enabled = true`

Die GUID ist ein eindeutiger Bezeichner für jede Bezeichnung in einer Organisation.

## <a name="microsoft-information-protection-sdk-metadata"></a>Microsoft Information Protection SDK Metadaten

Das MIP SDK gilt den folgenden Satz von Metadaten.

| Attribut | Typ oder Wert                 | Beschreibung                                                                                                                                                                                                                                        | obligatorisch |
|-----------|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| **aktiviert**   | "True" oder "false"                 | Dieses Attribut gibt an, ob die Klassifizierung, die von dieser Gruppe von Schlüssel-Wert-Paare dargestellt, die für das Datenelement aktiviert ist. DLP-Produkten überprüfen in der Regel das Vorhandensein dieses Schlüssels auf die klassifizierungsbezeichnung zu identifizieren. | Ja       |
| **SiteId**    | GUID                          | Azure Active Directory-Mandanten-ID                                                                                                                                                                                                                   | Ja       |
| **ActionId**  | GUID                          | ActionID wird jedes Mal geändert, die eine Bezeichnung festgelegt ist. Überwachungsprotokolle enthalten die alten und neuen ActionID um Verkettung der Kennzeichnung von Aktivität, um das Datenelement zu ermöglichen.                                                                                 | Ja       |
| **Methode**    | Standard, Privileged oder automatisch        | Legen Sie über MIP:: assignmentmethod                                                                                                                                                                                                                 | Nein        |
| **SetDate**   | Erweiterte ISO 8601-Datumsformat | Der Zeitstempel für die Bezeichnung festgelegt wurde.                                                                                                                                                                                                              | Nein        |
| **Name**      | String                        | Bezeichnung eindeutiger Name innerhalb des Mandanten. Es entsprechen nicht unbedingt, um Namen anzuzeigen.                                                                                                                                                              | Nein      |
| **ContentBits** | integer | Bitmaske, die die Arten von Inhalten, die markieren, die beschreibt, sollte in eine Datei angewendet werden. CONTENT_HEADER = 0X1, CONTENT_FOOTER = 0X2, WATERMARK = 0X4
 | Nein |

Wenn in einer Datei angewendet wird, ist das Ergebnis ähnelt der folgenden Tabelle.

| Key                                                         | Wert                                |
|-------------------------------------------------------------|--------------------------------------|
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled     | true                                 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate     | 2018-11-08T21:13:16-0800             |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method      | Berechtigungen                           |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name        | Confidential (Vertraulich)                         |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId      | cb46c030-1825-4e81-a295-151c039dbf02 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits | 2                                    |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId    | 88124cf5-1340-457d-90e1-0000a9427c99 |

## <a name="extending-metadata-with-custom-attributes"></a>Erweitern von Metadaten mit benutzerdefinierten Attributen

Benutzerdefinierter Metadaten kann über Datei "und" Policy-API angefügt werden. Benutzerdefinierte Attribute müssen die Basis verwalten `MSIP_Label_GUID` Präfix. 

Beispielsweise anwenden eine Anwendung, die von Contoso Corporation geschrieben Metadaten, der angibt, welches System eine bezeichnete Datei generiert. Die Anwendung kann eine neue Bezeichnung, die mit dem Präfix erstellen `MSIP_Label_GUID`. Das Präfix, das die benutzerdefinierte Metadaten generiert werden die softwareherstellername und das benutzerdefinierte Attribut angefügt.

```
MSIP_Label_f048e7b8-f3aa-4857-bf32-a317f4bc3f29_ContosoCorp_GeneratedBy = HRReportingSystem
```

> [!Note]
> Um die Kompatibilität für allgemeine Anwendungen, die maximale Länge für die einzelnen gewährleisten beträgt einen Schlüssel und Wert 255 Zeichen.

## <a name="versioning"></a>Versionskontrolle

Im Laufe der Zeit werden Attribute eingeführt, geändert oder außer Kraft gesetzt werden. Es wird erwartet, dass Anwendungen weiterhin diese alten verarbeiten oder veraltet Attribute, wie das Ersetzen des Werts in einem Unternehmen können Jahre in Anspruch nehmen.

Wenn ein Attribut mit einer neueren Version ersetzt wird, sollte ein Versionssuffix für das Attribut hinzugefügt werden:

`MSIP_Label_GUID_EnabledV2 = True | False | Condition`

## <a name="email"></a>E-Mail

Auf die e-Mail angewendeten Metadaten verwaltet die Schlüssel/Wert-Paar-format ähnelt der von Dokumenten. Der Hauptunterschied besteht darin, dass alle Attribute in einer einzelnen e-Mail-Header mit dem Namen serialisiert wurden **MSIP_Labels**. Schlüssel/Wert-Paare sind durch ein Semikolon und ein Leerzeichen getrennt, und im neuen Header platziert.

Verwenden die oben genannten beispielmetadaten:

```
MSIP_Labels: MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled=true; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate=2018-11-08T21:13:16-0800; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method=Privileged; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name=Confidential; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId=cb46c030-1825-4e81-a295-151c039dbf02; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits=2; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId=88124cf5-1340-457d-90e1-0000a9427c99
```
