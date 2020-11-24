---
title: 'Bezeichnung und Schutz: Microsoft Information Protection SDK'
description: Microsoft Information Protection Software Development Kit-Vorgänge.
author: Pathak-Aniket
ms.author: v-anikep
ms.date: 08/20/2020
ms.topic: conceptual
ms.service: information-protection
ms.openlocfilehash: 22cea33a439d8d0ca014095f3f2b7144f112fd93
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566742"
---
# <a name="labeling-and-pre-existing-protection-in-microsoft-information-protection-sdk"></a>Bezeichnung und bereits vorhandener Schutz in Microsoft Information Protection SDK

Microsoft Information Protection unterstützt Bezeichnungen und Klassifizierungs Dienste. Benutzer und Anwendungen können Folgendes auf unterstützte Dateien anwenden:

- Klassifizierung nur durch Anwendung einer Bezeichnung

- Klassifizierung und Schutz durch Anwendung einer Bezeichnung

- Nur Schutz

In diesem Artikel wird erläutert, wie das SDK versucht, eine Bezeichnung auf eine Datei anzuwenden, die bereits über einen vorhandenen Schutz verfügt. Wenn für das Dokument ein bereits vorhandener Schutz durch Anwendung einer Bezeichnung oder anderweitig vorhanden ist, verarbeitet das SDK die Anwendung einer neuen Bezeichnung in Szenarios wie unten beschrieben.

## <a name="label-based-protection-when-label-metadata-has-been-stripped"></a>Bezeichnungs basierter Schutz, wenn Bezeichnungs Metadaten entfernt wurden

Wenn eine Datei eine Bezeichnung angewendet hat und die Bezeichnung Schutz angewendet hat, sollte das SDK in der Lage sein, den Datei Schutz auf die jeweilige Bezeichnung zu beheben. Wenn ein Benutzer, der über Bearbeitungs Berechtigungen für die Datei verfügt, die Bezeichnungs Metadaten entweder versehentlich oder böswillig entfernt, bleibt der Schutz weiterhin bestehen. Wenn das SDK das nächste Mal mit der Datei interagiert, prüft es die Schutz Daten, löst diese Schutz Vorlage in die ursprüngliche Bezeichnung auf und wendet die Bezeichnung erneut an. Dies ist ein Sicherheitsmechanismus, der in das SDK für den Informationsschutz integriert ist, wenn die Bezeichnungs Metadaten manipuliert werden.

## <a name="custom-protection-and-label-applications"></a>Benutzerdefinierte Schutz-und Bezeichnungs Anwendungen

Wenn für die Datei eine Art Schutzanwendung angewendet wird, muss das SDK zuerst den ursprünglichen Schutz in eine Bezeichnung auflösen können, wenn eine RMS-Vorlage verwendet wird, und der Benutzer versucht, eine Bezeichnung auf die Datei anzuwenden. Wenn dies nicht möglich ist, kann das SDK nicht auswerten, ob die neue Schutz Sensitivität restriktiver oder einschränkender als die ursprüngliche Schutz Sensitivität ist. Daher wendet das SDK die neue Bezeichnung nicht auf die Datei an.

## <a name="user-defined-permissions"></a>Benutzerdefinierte Berechtigungen

Wenn für eine Datei eine Bezeichnung angewendet wurde und die Bezeichnung benutzerdefinierten Schutz angewendet hat, wird der Schutz auf die Datei angewendet, aber es gibt keine Möglichkeit für das SDK, das gleiche in eine RMS-Vorlage aufzulösen. Wenn ein Benutzer in diesem Fall versucht, eine neue Bezeichnung auf die Datei anzuwenden, behandelt SDK die ähnliche Aktion wie oben und wendet die neue Bezeichnung nicht auf die Datei an.
