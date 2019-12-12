---
title: 'Konzepte: Bezeichnungs Metadaten im MIP SDK'
description: Dieser Artikel hilft Ihnen, die Metadaten zu verstehen, die vom Microsoft Information Protection SDK generiert werden.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 11/08/2018
ms.author: tommos
ms.openlocfilehash: 3ae27b1bf0b4f709e9621f00b1b3a16c2ba1882c
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "69886131"
---
# <a name="microsoft-information-protection-sdk---metadata"></a>Microsoft Information Protection SDK-Metadaten

Das Microsoft Information Protection SDK generiert den Satz von Metadaten, die auf eine Datei angewendet werden sollen. Diese Metadaten sind eine Darstellung der Bezeichnung. In diesem Dokument werden die Metadaten beschrieben, die das SDK für die Anwendung auf e-Mail, Dokumente und andere Datensätze generiert.

## <a name="labels"></a>Bezeichnungen

Die Bezeichnungen im Microsoft Information Protection SDK werden auf Informationen angewendet, um die Vertraulichkeit dieser Informationen zu beschreiben. Bezeichnungs Daten werden in einer Reihe von Schlüssel-Wert-Paaren, die die Bezeichnung beschreiben, dauerhaft in einer Datei oder in einem Datensatz gespeichert. Der Metadatenname basiert auf der folgenden Struktur:

`DefinedPrefix_ElementType_GlobalIdentifier_AttributeName`

Wenn Sie auf Daten angewendet werden, die mit Microsoft Information Protection bezeichnet werden, lautet das Ergebnis:

`MSIP_Label_GUID_Enabled = true`

Die GUID ist ein eindeutiger Bezeichner für jede Bezeichnung in einer Organisation.

## <a name="microsoft-information-protection-sdk-metadata"></a>Microsoft Information Protection SDK-Metadaten

Das MIP SDK wendet den folgenden Satz von Metadaten an.

| Attribut | Typ oder Wert                 | Description                                                                                                                                                                                                                                        | Verbindlich |
|-----------|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| **Enabled**   | „Wahr“ oder „Falsch“                 | Dieses Attribut gibt an, ob die Klassifizierung, die durch diesen Satz von Schlüssel-Wert-Paaren dargestellt wird, für das Datenelement aktiviert ist. DLP-Produkte überprüfen in der Regel, ob dieser Schlüssel vorhanden ist, um die Klassifizierungs Bezeichnung zu identifizieren. | Ja       |
| **SiteId**    | GUID                          | Azure Active Directory Mandanten-ID                                                                                                                                                                                                                   | Ja       |
| **ActionId**  | GUID                          | Die Aktions-ID wird jedes Mal geändert, wenn eine Bezeichnung festgelegt wird. Überwachungs Protokolle enthalten sowohl alte als auch neue Aktions-IDs, um das Verketten von Bezeichnungs Aktivitäten mit dem Datenelement zuzulassen.                                                                                 | Ja       |
| **Methode**    | Standard oder privilegiert        | Wird über [MIP:: zutragmethode](reference/mip-enums-and-structs.md#assignmentmethod-enum)festgelegt. Standard impliziert, dass die Bezeichnung standardmäßig oder automatisch angewendet wird. Privilegiert impliziert, dass die Bezeichnung manuell ausgewählt wurde.                                                                                                                                                                                                                 | Nein        |
| **SetDate**   | Erweitertes ISO 8601-Datums Format | Der Zeitstempel, zu dem die Bezeichnung festgelegt wurde.                                                                                                                                                                                                              | Nein        |
| **Name**      | string                        | Bezeichnungs eindeutiger Name innerhalb des Mandanten. Sie entspricht nicht notwendigerweise dem anzeigen Amen.                                                                                                                                                              | Nein      |
| **Contentbits** | integer | Bitmaske, die die Typen von Inhalts Markierungen beschreibt, die auf eine Datei angewendet werden sollen. CONTENT_HEADER = 0x1, CONTENT_FOOTER = 0x2, Wasserzeichen = 0x4, verschlüsseln = 0x8
 | Nein |

Das Ergebnis ähnelt der folgenden Tabelle, wenn es auf eine Datei angewendet wird.

| Key                                                         | Value                                |
|-------------------------------------------------------------|--------------------------------------|
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled     | wahr                                 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate     | 2018-11-08t21:13:16-0800             |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method      | Privilegierte                           |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name        | Confidential (Vertraulich)                         |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId      | cb46c030-1825-4e81-a295-151c039dbf02 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits | 2                                    |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId    | 88124cf5-1340-457d-90e1-0000a9427c99 |

## <a name="extending-metadata-with-custom-attributes"></a>Erweitern von Metadaten mit benutzerdefinierten Attributen

Benutzerdefinierte Metadaten können über die Datei-und Richtlinien-API angehängt werden. Benutzerdefinierte Attribute müssen das Basis `MSIP_Label_GUID` Präfix beibehalten. 

Beispielsweise muss eine von contso Corporation geschriebene Anwendung Metadaten anwenden, die angeben, welches System eine bezeichnete Datei generiert hat. Die Anwendung kann eine neue Bezeichnung mit dem Präfix `MSIP_Label_GUID`erstellen. Der Softwarehersteller Name und das benutzerdefinierte Attribut werden an das Präfix angehängt, um die benutzerdefinierten Metadaten zu generieren.

```
MSIP_Label_f048e7b8-f3aa-4857-bf32-a317f4bc3f29_ContosoCorp_GeneratedBy = HRReportingSystem
```

> [!Note]
> Um die Kompatibilität über gängige Anwendungen hinweg zu gewährleisten, beträgt die maximale Länge für jeden Schlüssel und einen Wert 255 Zeichen.

## <a name="versioning"></a>Versionsverwaltung

Im Laufe der Zeit werden Attribute eingeführt, geändert oder abgekoppelt. Es wird erwartet, dass Anwendungen diese alten oder außer Kraft gesetzte Attribute weiterhin verarbeiten, da der Wert für ein Unternehmen möglicherweise Jahre in Anspruch nimmt.

Wenn Sie ein Attribut durch eine neuere Version ersetzen, sollte dem Attribut ein Versions Suffix hinzugefügt werden:

`MSIP_Label_GUID_EnabledV2 = True | False | Condition`

## <a name="email"></a>E-Mail

Auf e-Mail angewendete Metadaten behalten ein Schlüssel-Wert-Paar-Format bei, das dem von Dokumenten ähnelt. Der Hauptunterschied besteht darin, dass alle Attribute in einen einzelnen e-Mail-Header mit dem Namen **MSIP_Labels**serialisiert werden. Die Schlüssel-Wert-Paare werden durch ein Semikolon und ein Leerzeichen getrennt und in den neuen Header eingefügt.

Verwenden der obigen Beispiel Metadaten:

```
MSIP_Labels: MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled=true; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate=2018-11-08T21:13:16-0800; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method=Privileged; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name=Confidential; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId=cb46c030-1825-4e81-a295-151c039dbf02; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits=2; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId=88124cf5-1340-457d-90e1-0000a9427c99
```
