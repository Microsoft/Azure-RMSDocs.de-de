---
title: 'Konzepte: Verwenden von PowerShell zum Abrufen eines Zugriffstoken'
description: In diesem Artikel erfahren Sie, wie Sie mithilfe von PowerShell ein OAuth2-Zugriffstoken abrufen. Dieser Aufruf ist für die Implementierung des Authentifizierungsdelegaten erforderlich.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 02/04/2019
ms.author: mbaldwin
ms.openlocfilehash: 68ae6bc02f671f0a4d18c382ccde4f53873b2fd4
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60175308"
---
# <a name="acquire-an-access-token-powershell"></a>Abrufen eines Zugriffstoken (PowerShell)

Das Beispiel veranschaulicht rufen Sie ein externes Powershellskript, um eine OAuth2-Token zu erhalten. Ein gültiger OAuth2-Zugriffstoken ist durch die Implementierung von der authentifizierungsdelegat erforderlich.

## <a name="prerequisites"></a>Vorraussetzungen

- Vollständige [(MIP) SDK-Setup und Konfiguration](setup-configure-mip.md). U.a. müssen Sie Ihre Client-Anwendung in Ihrem Mandanten für Azure Active Directory (Azure AD) registrieren. Azure AD bietet eine Anwendungs-ID, auch bekannt als Client-ID, die in Ihrer Logik tokenabruf verwendet wird.

Dieser Code ist nicht für Produktionszwecke vorgesehen. Es kann nur für Entwicklungs- und Grundlegendes zu Auth Konzepten verwendet werden. 

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

### <a name="authh"></a>auth.h

In diesem Beispiel wird deine einfache Funktion mit dem Namen AcquireToken erstellt. Da der Rückgabewert hartcodierte für dieses Tutorial ist, werden wir keine Parameter annehmen und Zurückgeben einer Zeichenfolge (das Token).

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

Die Quelldatei gibt einen Tokenwert, der in einem späteren Schritt hartcodiert werden.

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

Erstellen Sie zuletzt ein Token, das der mToken-Variablen hinzugefügt werden soll. Im nachfolgenden Beispiel wird das PowerShell-Skript veranschaulicht, das verwendet werden kann, um unter Windows schnell ein OAuth2-Token über die Active Directory-Authentifizierungsbibliothek und PowerShell abzurufen. Dieses Token darf nur für den Office 365 Security & Compliance Center-Endpunkt verwendet werden. Aus diesem Grund schlagen die Aktionen zum Schutz fehl, wenn die Ressourcen-URL nicht aktualisiert wird. 

### <a name="install-adalpshttpswwwpowershellgallerycompackagesadalps31942-from-ps-gallery"></a>Installieren von [ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2) über den PS-Katalog

Sie können diesen Schritt überspringen, wenn Sie diese zuvor im abgeschlossen [(MIP) SDK-Setup und Konfiguration](setup-configure-mip.md).

```PowerShell
Install-Module -Name ADAL.PS
```

### <a name="use-get-adaltoken-to-obtain-the-access-token"></a>Verwenden des Get-ADALToken zum Abrufen des Zugriffstoken

```PowerShell
#Install the ADAL.PS package if it's not installed.
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps }

$authority = "https://login.windows.net/common/oauth2/authorize" 
#this is the security and compliance center endpoint
$resourceUrl = "https://syncservice.o365syncservice.com/"
#replace <application-id> and <redirect-uri>, with the Redirect URI and Application ID from your Azure AD application registration.
$clientId = "<application-id>"
$redirectUri = "<redirect-uri>"

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip
```

Kopieren Sie das Token aus der Zwischenablage in auth.cpp als Wert für `string mToken`. Sie ersetzen also „your token here“ im obenstehenden Code. Es ist unter Umständen erforderlich, das Skript erneut auszuführen. Dies ist davon abhängig, wie lange es dauert, die folgenden Schritte auszuführen.


