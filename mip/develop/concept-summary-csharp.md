---
title: Übersicht über den C# Microsoft Information Protection SDK-Wrapper
description: Eine kurze Übersicht über die ersten Schritte mit dem MIP SDK .net-Wrapper und den Unterschieden zwischen dem .net-Wrapper C++ und dem SDK.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 01/04/2019
ms.author: tommos
ms.openlocfilehash: 21fc590388615b2917ca62fdd848b3a63ce26912
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556111"
---
# <a name="getting-started-with-the-microsoft-information-protection-net-wrapper"></a>Einstieg in den Microsoft Information Protection .net-Wrapper

Mit dem Microsoft Information Protection SDK .net-Wrapper können Entwickler die Microsoft Information Protection-Funktion in in Ihre eigenen Anwendungen und Dienste integrieren. Mithilfe der Klassifizierungs-, Bezeichnungs-und Schutzfunktionen des SDK können Sie sicherstellen, dass die Informationen unabhängig von der Art der Übertragung klassifiziert, gekennzeichnet und geschützt werden. 

Der verwaltete Wrapper und alle Abhängigkeiten können über nuget in Visual Studio installiert werden.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Der Microsoft Information Protection .net-Wrapper wird auf den folgenden .net-Plattformen unterstützt:

* .NET Standard 2.0
* .NET 4,0

## <a name="installing-the-package"></a>Installieren des Pakets

Installieren Sie das Paket über die Paket-Manager-Konsole in Visual Studio 2017, indem Sie Folgendes ausführen:

`install-package Microsoft.InformationProtection.File`

Es sind keine zusätzlichen Pakete erforderlich. Alle Bibliotheken von Drittanbietern sind enthalten und werden beim Build in den Ausgabeordner kopiert.

## <a name="wrapper-details"></a>Wrapper Details

Der .net-Wrapper ist ein von [swig](https://swig.org/) generierter verwalteter Wrapper. Der Wrapper verwendet kompilierte C++ Bibliotheken aus dem Microsoft Information Protection SDK. Diese DLLs sind dieselben DLLs, die in der C++ SDK-Version enthalten sind.

## <a name="concept-overlap"></a>Überlappende Konzept

Es gibt einige grundlegende Unterschiede zwischen C++ der SDK-Version und dem verwalteten Wrapper.

* Der .net-Wrapper erfordert nicht die Verwendung von Beobachtern für asynchrone Vorgänge. Alle asynchronen Vorgänge werden über das [aufgabenbasierte asynchrone Muster](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)implementiert.
* Der .net-Wrapper erfordert die Delegaten, die Teil des C++ SDK sind: authdelegat und genehmidelegat. Diese Delegaten werden über die Schnittstellen implementiert `IAuthDelegate` und `IConsentDelegate`

## <a name="next-steps"></a>Nächste Schritte

Lesen Sie als nächstes das [SDK C# für die Schnellstart-Initialisierung für Microsoft Information Protection (MIP)](quick-app-initialization-csharp.md) , um mit dem Aufbau einer grundlegenden, MIP-fähigen Konsolenanwendung zu beginnen.
