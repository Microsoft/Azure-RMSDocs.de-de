---
title: 'Bezeichnung und Schutz: Microsoft Information Protection SDK'
description: Microsoft Information Protection Software Development Kit-Vorgänge.
author: msmbaldwin
ms.author: mbaldwin
ms.date: 08/20/2020
ms.topic: conceptual
ms.service: information-protection
ms.openlocfilehash: 2e18b9ae65a4915807fdcb8fc37dd18396270fee
ms.sourcegitcommit: 8e48016754e6bc6d051138b3e3e3e3edbff56ba5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865009"
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
