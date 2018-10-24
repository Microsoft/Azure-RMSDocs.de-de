---
title: 'Konzepte: Verwenden von PowerShell zum Abrufen eines Zugriffstoken'
description: In diesem Artikel erfahren Sie, wie Sie mithilfe von PowerShell ein OAuth2-Zugriffstoken abrufen. Dieser Aufruf ist für die Implementierung des Authentifizierungsdelegaten erforderlich.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3206fb99cd72c5d609375ec673e7798d33c735c3
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453383"
---
# <a name="acquire-an-access-token-powershell"></a>Abrufen eines Zugriffstoken (PowerShell)

Dieses Beispiel veranschaulicht den Abruf eines OAuth2-Token mithilfe des Aufrufs eines externen PowerShell-Skripts. Dieser Aufruf ist für die Implementierung des Authentifizierungsdelegaten erforderlich.

Der hier verwendete Code soll nicht für die Produktion verwendet werden, sondern nur zum Entwickeln und Nachvollziehen von Authentifizierungskonzepten. 

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

### <a name="authh"></a>auth.h

In diesem Beispiel wird deine einfache Funktion mit dem Namen AcquireToken erstellt. Da der Rückgabewert für dieses Tutorial hartcodiert wird, werden keine Parameter akzeptiert, und es wird nur eine Zeichenfolge zurückgegeben (das Token).

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();
  }
}
```

### <a name="authcpp"></a>auth.cpp

Die hier verwendete Quelldatei gibt einen Tokenwert zurück, der in einem späteren Schritt hartcodiert wird.

```cpp
//auth.cpp
#include <string>
#include "auth.h"

namespace sample {
  namespace auth {
    string AcquireToken() {
      std::string mToken = "your token here";
      return mToken;
    }
  }
}
```

## <a name="mint-a-token"></a>Erstellen eines Token

Erstellen Sie zuletzt ein Token, das der mToken-Variablen hinzugefügt werden soll. Im nachfolgenden Beispiel wird das PowerShell-Skript veranschaulicht, das verwendet werden kann, um unter Windows schnell ein OAuth2-Token über die Active Directory-Authentifizierungsbibliothek und PowerShell abzurufen. Dieses Token darf nur für den Office 365 Security & Compliance Center-Endpunkt verwendet werden. Aus diesem Grund schlagen die Aktionen zum Schutz fehl, wenn die Ressourcen-URL nicht aktualisiert wird. Wenn Sie an diesem Punkt unter Verwendung von Bezeichnungen und des Schutzes Tests durchführen möchten, sollten Sie die [nächsten Schritte](#next-steps) überspringen.

### <a name="install-adalpshttpswwwpowershellgallerycompackagesadalps31942-from-ps-gallery"></a>Installieren von [ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2) über den PS-Katalog

```PowerShell
Install-Module -Name ADAL.PS
```

### <a name="use-get-adaltoken-to-obtain-the-access-token"></a>Verwenden des Get-ADALToken zum Abrufen des Zugriffstoken

```PowerShell
#Install the ADAL.PS package if it's not installed.
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps }

$authority = "https://login.windows.net/common/oauth2/authorize" 
#this is the security and compliance center endpoint
$resourceUrl = "https://dataservice.o365filtering.com"
#clientId and redirectUri are from the RMS Sharing Application. 
#Once custom app registration is supported, a custom id and uri will be required. 
$clientId = "6b069eef-9dde-4a29-b402-8ce866edc897"
$redirectUri = "com.microsoft.rms-sharing-for-win://authorize"

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip
```

Kopieren Sie das Token aus der Zwischenablage in auth.cpp als Wert für `string mToken`. Sie ersetzen also „your token here“ im obenstehenden Code. Es ist unter Umständen erforderlich, das Skript erneut auszuführen. Dies ist davon abhängig, wie lange es dauert, die folgenden Schritte auszuführen.


