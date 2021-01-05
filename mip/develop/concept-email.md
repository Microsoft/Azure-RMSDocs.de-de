---
title: Verarbeiten von e-Mail-Nachrichten mithilfe des MIP SDK
description: In diesem Artikel erfahren Sie, wie Sie mithilfe der MIP SDK-Datei-API. msg-und rpmsg-Dateien verarbeiten.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: mbaldwin
ms.openlocfilehash: 52526409b6d08efde1064063b9f36564baa6a378
ms.sourcegitcommit: 8e48016754e6bc6d051138b3e3e3e3edbff56ba5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864769"
---
# <a name="file-api-email-message-file-processing"></a>Dateiverarbeitung der Datei-API-e-Mail

MIP SDK unterstützt das Entschlüsseln und Verschlüsseln von e-Mail-Nachrichten. Sowohl von Outlook oder Exchange generierte Nachrichten Dateien als auch rpmsg-Dateien werden vom SDK unterstützt, aber auf etwas andere Art und Weise, wie wir in diesem Szenario behandelt werden.

Zu den gängigen Anwendungsfällen für dieses Szenario gehören:

- Entschlüsseln von Nachrichten für eDiscovery
- Entschlüsseln von e-Mails und Anlagen für die DLP-Überprüfung
- Veröffentlichen geschützter Nachrichten direkt aus Branchen Anwendungen
- Entschlüsseln, ändern und erneutes schützen von Nachrichten während der Übertragung

## <a name="file-api-operations-for-msg-files"></a>Datei-API-Vorgänge für. msg-Dateien

Die Datei-API unterstützt Schutz Vorgänge für MSG-Dateien und identisch mit einem beliebigen anderen Dateityp, mit der Ausnahme, dass das SDK die Anwendung benötigt, um das msg-featureflag zu aktivieren. 

> [!IMPORTANT]
> Bezeichnungs Vorgänge für. msg-Dateien werden zurzeit nicht unterstützt.

Wie bereits erläutert, erfordert die Instanziierung von `mip::FileEngine` ein Einstellungsobjekt, `mip::FileEngineSettings`. `mip::FileEngineSettings` kann verwendet werden, um Parameter für benutzerdefinierte Einstellungen zu übergeben, die von der Anwendung für eine bestimmte Instanz festgelegt werden müssen. Die CustomSettings-Eigenschaft von fileenginesettings wird verwendet, um das-Flag für festzulegen `enable_msg_file_type` , um die Verarbeitung von msg-Dateien zu ermöglichen.

Der Datei Schutz für die Datei Schutz Vorgänge ". msg" könnte wie folgt aussehen:

- Legen `enable_msg_file_type` `mip::FileEngineSettings` Sie das-Flag in fest, und fügen Sie das `mip::FileEngine` `mip::FileProfile`
- Verwenden Sie die Schutz-API, um dem Benutzer verfügbare Schutz Vorlagen aufzulisten.
- Ein Konstrukt `mip::FileHandler` , das auf die zu schützende Datei zeigt.
- Wählen Sie eine Vorlage zum Schutz aus, und legen Sie den Schutz mithilfe der-Methode auf die Datei fest `mip::FileHandler` `SetProtection` .

Weitere Informationen zum Auflisten von Schutz Vorlagen finden Sie unter Schutz-API- [Schnellstart: Auflisten von Vorlagen](quick-protection-list-templates-cpp.md) .

## <a name="file-api-operations-for-rpmsg-files"></a>Datei-API-Vorgänge für rpmsg-Dateien

MIP SDK unterstützt keine MIME-kompatiblen (üblicherweise eml-) Nachrichten. Stattdessen macht das SDK eine Inspektions Funktion verfügbar, die die eingebettete **Message. rpmsg** -Datei entschlüsseln und einen Satz von Bytestreams als Ausgabe darstellen kann. Der SDK-Consumer muss die Datei Message. rpmsg extrahieren und an die API übergeben. Variationen dieses Datei namens sind für Szenarios der Office-Nachrichten Verschlüsselung vorhanden, und die API akzeptiert auch message_v2-, v3-oder V4-Dateien.

Im allgemeinen verarbeiten e-Mail-Gateways und DLP-Dienste (Data Loss Prevention, Verhinderung von Datenverlust) MIME-kompatible Nachrichten, während die e-Mail Wenn die e-Mail geschützt ist, wird der Inhalt der Nachricht in einer Anlage, *Message. rpmsg*, gespeichert. Diese Anhänge enthalten den verschlüsselten e-Mail-Text und alle Anhänge, die Teil der ursprünglichen Nachricht waren. Die *rpmsg* -Datei ist an eine nur-Text-Wrapper-e-Mail angefügt und wird dann an den e-Mail-Dienst gesendet. Sobald diese Nachricht die Exchange-oder Exchange Online-Grenze verlässt, liegt Sie im MIME-kompatiblen Format vor, damit Sie an Ihr Ziel gesendet werden kann.

In den meisten Fällen muss der DLP-Partner in der Lage sein, die Anhänge und Klartext-Bytes aus der Nachricht abzurufen, um DLP-Richtlinien zu überprüfen und zu evaluieren. Die Überprüfungs-API nimmt die Nachricht. rpmsg als Eingabe an und gibt Bytestreams als Ausgabe zurück. Diese Bytestreams enthalten sowohl die nur-Text-Bytes der Nachricht als auch die Anhänge. Es ist für den Anwendungsentwickler von Vorteil, diese Streams zu verarbeiten und etwas Nützliches zu tun (überprüfen, rekursiv entschlüsseln usw.).

Die- `Inspect` API wird über eine-Klasse implementiert `mip::FileInspector` , die Vorgänge für die Überprüfung unterstützter Dateitypen verfügbar macht. `mip::MsgInspector` die erweitert `mip::FileInspector` , macht Entschlüsselungs Vorgänge verfügbar, die für das rpmsg-Dateiformat spezifisch sind. MIP SDK unterstützt keine Veröffentlichungs Szenarien für *Message. rpmsg* -Dateien.

`mip::MsgInspector` die Klasse macht die folgenden Member verfügbar:

```cpp
public const std::vector<uint8_t>& GetBody()
public BodyType GetBodyType() const
public BodyType GetBodyType() const
public InspectorType GetInspectorType() const
public std::shared_ptr<Stream> GetFileStream() const
```

Weitere Informationen finden Sie in der [API-Referenz](./reference/mip-sdk-reference.md).

## <a name="next-steps"></a>Nächste Schritte

- Lesen Sie den [Schnellstart zu Datei-API-Prozess-e-Mail. Nachrichten Dateien (C++).](quick-email-msg-cpp.md)
- Lesen Sie den [Schnellstart zu Datei-API-Prozess-e-Mail. msg-Dateien (c#)](quick-email-msg-csharp.md)