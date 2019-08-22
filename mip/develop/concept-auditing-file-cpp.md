---
title: 'Konzepte: Überwachung mit der Datei-API für das Microsoft Information Protection SDK'
description: In diesem Artikel erfahren Sie, wie Sie das Microsoft Information Protection SDK verwenden können, um Datei-API-Überwachungsereignisse an die Azure Information Protection-Analyse zu übermitteln.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: tommos
ms.openlocfilehash: df67886f53d697e47f6e812cdcbbac394acaa98d
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884746"
---
# <a name="auditing-in-the-mip-sdk-file-api"></a>Überwachung mit der Datei-API im MIP SDK

Über das Administrationsportal von Azure Information Protection können Sie auf Administratorberichte zugreifen. Diese Berichte bieten Aufschluss darüber, welche Bezeichnungen Benutzer, manuell oder automatisch, über alle Anwendungen oder Dienste, die das MIP SDK integriert haben, anwenden. Entwicklungspartner, die das SDK verwenden, können diese Funktion aktivieren, um Informationen aus Ihren Anwendungen in Kunden berichten zu erhalten.

## <a name="event-types"></a>Ereignis Typen

Es gibt drei Typen von Ereignissen, die über das SDK an die Azure Informationen Protection-Analyse übermittelt werden können. **Taktereignisse**, **Ermittlungsereignisse** und **Änderungsereignisse**

### <a name="heartbeat-events"></a>Taktereignisse

Taktereignisse werden für jede Anwendung, in der die Datei-API integriert ist, automatisch generiert. Taktereignisse enthalten Folgendes:

* TenantId
* Erstellungszeit
* Benutzerprinzipalname
* Name des Computers, auf dem die Überwachung generiert wurde
* Prozessname
* Platform
* Die Anwendungs-ID entspricht der Azure AD-Anwendungs-ID.

Diese Ereignisse sind hilfreich, um Anwendungen in Ihrem Unternehmen zu erkennen, die das Microsoft Information Protection SDK verwenden.

### <a name="discovery-events"></a>Ermittlungsereignisse

Ermittlungsereignisse liefern Informationen über Daten mit Bezeichnungen, die von der Datei-API gelesen oder verwendet werden. Diese Ereignisse sind hilfreich, da sie die Geräte, den Standort und die Benutzer erfassen, die auf Informationen in einer Organisation zugreifen.

Diese Ereignisse werden durch Festlegen des Parameters `AuditDiscoveryEnabled` auf TRUE beim Erstellen eines neuen `mip::FileHandler`-Elements an die Azure Informationen Protection-Analyse übermittelt. Darüber hinaus wird eine Inhaltsbezeichner bereitgestellt, der die Datei in einem lesbaren Format identifiziert. Es wird empfohlen, den Dateipfad als Bezeichner zu verwenden.

Im folgenden Beispiel wird ein neues `mip::FileHandler`-Element mit Überwachungsermittlung aktiviert. Die `CreateFileHandler()`-Methode wird für `mip::FileEngine` aufgerufen und `AuditDiscoveryEnabled` auf TRUE festgelegt. Sobald das `FileHanlder`-Element die Bezeichnung liest, wird ein Element für die Ermittlungsüberwachung generiert.

```cpp
// Create FileHandler with discovery enabled
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
auto handlerFuture = handlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(inputFilePath, actualFilePath, true /*AuditDiscoveryEnabled*/, make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = handlerFuture.get();

// Read label. This generates the discovery audit.
auto label = handler->GetLabel();
```

### <a name="change-events"></a>Änderungsereignisse

Änderungsereignisse liefern Informationen über die Datei, die Bezeichnung, die angewendet oder geändert wurde, und alle vom Benutzer angegebenen Begründungen. Ereignisse werden generiert, indem `NotifyCommitSuccessful()` für das `mip::FileHandler`-Element nach dem erfolgreichen Commit einer Änderung in eine Datei aufgerufen wird.

```cpp
// Create labeling options, set label
string contentId = "C:\users\myuser\Documents\MyPlan.docx";
mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED);
handler->SetLabel(labelId, labelingOptions, mip::ProtectionSettings());
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();

// CommitAsync() returns a bool. If the change was successful, call NotifyCommitSuccessful().
fileHandler->CommitAsync(outputFile, commitPromise);
if(commitFuture.get()) {

    // Submit audit event.
    handler->NotifyCommitSuccessful(contentId);
}
```

## <a name="audit-dashboard"></a>Überwachungsdashboard

An die Überwachungspipeline von Azure Information Protection übermittelte Ereignisse werden in Berichten unter https://portal.azure.com angezeigt. 

## <a name="next-steps"></a>Nächste Schritte

Ausführliche Informationen zur Überwachungsfunktion in Azure Information Protection finden Sie im [Vorschau Ankündigungs Blog in der Tech Community](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).
