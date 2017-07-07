---
title: "So erneuern Sie einen symmetrischen Schlüssel in Azure Information Protection"
description: "Dieser Artikel beschreibt den Prozess der Erneuerung eines symmetrischen Schlüssels in Azure Information Protection."
keywords: 
author: kkanakas
manager: mbaldwin
ms.author: kartikk
ms.date: 03/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0b8c8f0-6ed5-48bb-8155-ac4f319ec178
ms.openlocfilehash: 6153067c308206cb93ad99de1075913c68d1fa3b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="how-to-renew-the-symmetric-key-in-azure-information-protection"></a>Vorgehensweise: Erneuern eines symmetrischen Schlüssels in Azure Information Protection

Ein **symmetrischer Schlüssel** ist ein Geheimnis, das eine Nachricht in der Kryptografie für symmetrische Schlüssel verschlüsselt und entschlüsselt.  

Wenn Sie in Azure Active Directory (Azure AD) ein Dienstprinzipalobjekt erstellen, um eine Anwendung darzustellen, generiert der Prozess ebenso einen 256-Bit symmetrischen Schlüssel, um die Anwendung zu verifizieren. Dieser symmetrische Schlüssel ist standardmäßig ein Jahr gültig. 

Die folgenden Schritte beschreiben, wie der symmetrische Schlüssel erneuert wird. 

## <a name="prerequisites"></a>Voraussetzungen

* Das Azure AD PowerShell-Modul (Azure Active Directory) muss wie in der [Azure AD Powershell Reference (Azure AD PowerShell-Referenz)](https://docs.microsoft.com/powershell/msonline/) beschrieben installiert werden.


## <a name="renewing-the-symmetric-key-after-expiry"></a>Erneuern des symmetrischen Schlüssels nach Ablauf

Sie müssen keinen neuen Dienstprinzipal erstellen, wenn der symmetrische Schlüssel, der Ihrer Anwendung zugeordnet ist, abgelaufen ist. Stattdessen können Sie die [PowerShell-Cmdlets](https://docs.microsoft.com/powershell/module/msonline) verwenden, die von Microsoft Online Services (MSol) bereitgestellt wurden, um einen neuen symmetrischen Schlüssel für einen vorhandenen Dienstprinzipal auszustellen.

Um diesen Prozess zu veranschaulichen, nehmen wir an, Sie haben bereits einen neuen Dienstprinzipal mithilfe des [`New-MsolServicePrincipal`](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential)-Befehls erstellt.

```
New-MsolServicePrincipalCredential -ServicePrincipalName "SupportExampleApp"
```

Der Erstellungsprozess erstellt einen symmetrischen Schlüssel und eine **AppPrincipalId**, so wie hier gezeigt.

```
The following symmetric key was created as one was not supplied
ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

DisplayName : SupportExampleApp
ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963
TrustedForDelegation : False
AccountEnabled : True
Addresses : []
KeyType : Symmetric
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

Der im oben dargestellten Beispiel erstellte symmetrische Schlüssel läuft am 22.3.2018 um 15:27:53 ab. Um weiterhin den Dienstprinzipal nach diesem Zeitpunkt verwenden zu können, müssten Sie den symmetrischen Schlüssel erneuern. Hierzu können Sie den Befehl [`New-MsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential) verwenden. 

```
New-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963
```

Dadurch wird ein neuer symmetrischer Schlüssel für die angegebene **AppPrincipalId** erstellt.

```
The following symmetric key was created as one was not supplied ON8YYaMYNmwSfMX625Ei4eC6N1zaeCxbc219W090v28-
```
Sie können den Befehl [`GetMsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/get-msolserviceprincipalcredential) verwenden, um zu überprüfen, dass der neue symmetrische Schlüssel mit dem richtigen Dienstprinzipal verknüpft ist, wie hier dargestellt ist. Beachten Sie, dass der Befehl alle Schlüssel auflistet, die derzeit mit dem Dienstprinzipal verknüpft sind.

```
Get-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963 -ReturnKeyValues true

Type : Symmetric
Value :
KeyId : c1ac145f-e899-4c90-8a02-2cef40054fc5
StartDate : 3/24/2017 10:11:07 PM
EndDate : 3/24/2018 10:11:07 PM
Usage : Verify

Type : Symmetric
Value :
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

Nachdem Sie überprüft haben, dass der symmetrische Schlüssel wirklich mit dem richtigen Dienstprinzipal verknüpft ist, können Sie die Authentifizierungsparameter des Dienstprinzipals mit dem neuen Schlüssel aktualisieren. 

Sie können anschließend den alten symmetrischen Schlüssel mit dem [`Remove-MsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/remove-msolserviceprincipalcredential)-Befehl entfernen und mit dem `Get-MsolServicePrincipalCredential`-Befehl überprüfen, dass der Schlüssel entfernt wurde.

```
Remove-MsolServicePrincipalCredential -KeyId acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe -ObjectId 0ee53770-ec86-409e-8939-6d8239880518
```

## <a name="related-topics"></a>Verwandte Themen

* [Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md)
* [Azure Active Directory MSOnline Powershell reference (MSOnline-PowerShell-Referenz für Azure Active Directory)](https://docs.microsoft.com/powershell/msonline/)
