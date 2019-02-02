---
title: Microsoft Information Protection SDK C# Wrapper-Übersicht
description: Eine kurze Übersicht über zum Einstieg in den Wrapper MIP SDK für .NET sowie die Unterschiede zwischen den Wrapper für .NET und C++-SDK.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 01/04/2019
ms.author: tommos
ms.openlocfilehash: ec1d2083449f1cb4ffccb086f71a7085a9251604
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651978"
---
# <a name="getting-started-with-the-microsoft-information-protection-net-wrapper"></a>Erste Schritte mit dem Microsoft Information Protection .NET-Wrapper

Der Microsoft Informationen Protection SDK .NET Wrapper ermöglicht Entwicklern, die Microsoft Information Protection-Benutzeroberfläche in ihre eigenen Anwendungen und Diensten integrieren. SDK Klassifizierung, Bezeichnung und Schutz Features können, um sicherzustellen, dass Informationen klassifiziert wird, mit der Bezeichnung, und unabhängig davon, wo der Übertragung geschützt. 

Der verwaltete Wrapper und alle Abhängigkeiten können über NuGet in Visual Studio installiert werden.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Der Microsoft Informationen Protection .NET Wrapper wird auf den folgenden Plattformen für .NET unterstützt:

* .NET Standard 2.0
* .NET 4.0

## <a name="installing-the-package"></a>Installieren des Pakets

Installieren Sie über die Paket-Manager-Konsole in Visual Studio 2017 das Paket durch ausführen:

`install-package Microsoft.InformationProtection.File`

Es sind keine zusätzlichen Pakete erforderlich. Alle Bibliotheken von Drittanbietern sind enthalten und werden in den Ausgabeordner beim Erstellen kopiert.

## <a name="wrapper-details"></a>Wrapper-Details

Der Wrapper für .NET ist eine [SWIG](https://swig.org/) generierten verwalteten Wrapper. Der Wrapper wird kompilierte C++-Bibliotheken über das Microsoft Information Protection SDK verwendet. Diese DLLs sind die gleichen DLLs, die in der C++-Version des SDK enthalten sind.

## <a name="concept-overlap"></a>Konzept überlappen

Es gibt einige grundlegende Unterschiede zwischen der C++-Version des SDK und der verwaltete Wrapper.

* Der Wrapper für .NET nicht die Verwendung der Beobachter für asynchrone Vorgänge nicht erforderlich. Alle asynchronen Vorgänge werden implementiert, über die [aufgabenbasierte asynchrone Muster](https://docs.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap).
* Der Wrapper für .NET ist die Delegaten erforderlich, die Teil des C++-SDK sind: AuthDelegate und ConsentDelegate. Diese Delegaten werden über die Schnittstellen implementiert `IAuthDelegate` und `IConsentDelegate`

## <a name="next-steps"></a>Nächste Schritte

Überprüfen Sie dann [-Schnellstart – Initialisierung für Microsoft Information Protection (MIP) SDK C# ](quick-app-initialization-csharp.md) für den Einstieg in das Erstellen einer basic "," MIP-fähigen Konsolenanwendung.
