---
title: Übersicht über den c#-Wrapper für Microsoft Information Protection SDK
description: Eine kurze Übersicht über die ersten Schritte mit dem MIP SDK .net-Wrapper und den Unterschieden zwischen .net Wrapper und C++ SDK.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 01/04/2019
ms.author: tommos
ms.openlocfilehash: da563bc385658d716d6813710495d91b42bbcc83
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "95567835"
---
# <a name="getting-started-with-the-microsoft-information-protection-net-wrapper"></a>Einstieg in den Microsoft Information Protection .net-Wrapper

Mit dem Microsoft Information Protection SDK .net-Wrapper können Entwickler die Microsoft Information Protection-Funktion in in Ihre eigenen Anwendungen und Dienste integrieren. Mithilfe der Klassifizierungs-, Bezeichnungs-und Schutzfunktionen des SDK können Sie sicherstellen, dass die Informationen unabhängig von der Art der Übertragung klassifiziert, gekennzeichnet und geschützt werden. 

Der verwaltete Wrapper und alle Abhängigkeiten können über nuget in Visual Studio installiert werden.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Der Microsoft Information Protection .net-Wrapper wird auf den folgenden .net-Plattformen unterstützt:

* .NET-Standard 2.0
* .NET 4,0

## <a name="installing-the-package"></a>Installieren des Pakets

Installieren Sie das Paket über die Paket-Manager-Konsole in Visual Studio 2017, indem Sie Folgendes ausführen:

`install-package Microsoft.InformationProtection.File`

Es sind keine zusätzlichen Pakete erforderlich. Alle Bibliotheken von Drittanbietern sind enthalten und werden beim Build in den Ausgabeordner kopiert.

## <a name="wrapper-details"></a>Wrapper Details

Der .net-Wrapper ist ein von [swig](https://swig.org/) generierter verwalteter Wrapper. Der Wrapper verwendet kompilierte C++-Bibliotheken aus dem Microsoft Information Protection SDK. Diese DLLs sind dieselben DLLs, die in der C++-Version des SDK enthalten sind.

## <a name="concept-overlap"></a>Überlappende Konzept

Es gibt einige grundlegende Unterschiede zwischen der C++-Version des SDK und dem verwalteten Wrapper.

* Der .net-Wrapper erfordert nicht die Verwendung von Beobachtern für asynchrone Vorgänge. Alle asynchronen Vorgänge werden über das [aufgabenbasierte asynchrone Muster](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)implementiert.
* Der .net-Wrapper erfordert die Delegaten, die Teil des C++ SDK sind: authdelegat und genehmidelegat. Diese Delegaten werden über die-Schnittstellen implementiert. `IAuthDelegate``IConsentDelegate`

## <a name="next-steps"></a>Nächste Schritte

Überprüfen Sie als nächstes die [Schnellstart-Initialisierung für das Microsoft Information Protection (MIP) SDK c#](quick-app-initialization-csharp.md) , um mit dem Aufbau einer grundlegenden, MIP-fähigen Konsolenanwendung zu beginnen.