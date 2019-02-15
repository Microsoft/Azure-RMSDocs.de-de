---
title: 'Gewusst wie: Hinzufügen expliziter Besitzerrechte | Azure RMS'
description: In Ihrer Anwendung sollten explizit Rechte vom Typ „Besitzer“ hinzugefügt werden, wenn eine Lizenz von Grund auf neu erstellt wird.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: EF43FAC4-ABB4-459D-B173-972B5716F816
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 2bb0ef4652a58a1658e6d0cd64577a02f3af039c
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56255766"
---
# <a name="how-to-add-explicit-owner-rights"></a>Exemplarische Vorgehensweise: Hinzufügen expliziter Besitzerrechte

In Ihrer Anwendung sollten explizit Berechtigungen vom Typ „Besitzer“ hinzugefügt werden, wenn eine Lizenz von Grund auf mit [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx) neu erstellt wird.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Ihre Anwendung ein Lizenzhandle mit [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx) erstellt, muss sie dem Besitzer auch explizit einen Vollzugriff (Berechtigungen) gewähren.

> [!NOTE]
> Wenn ein Benutzer über [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx) mit der **IPC\_LI\_OWNER**-Eigenschaft als Besitzer (Owner) festgelegt wird, werden dem Besitzer damit alle Berechtigungen gewährt.

In diesem Codebeispiel werden nur die Schritte gezeigt, die zum Erstellen und Hinzufügen bestimmter Rechte zu einer Lizenz erforderlich sind.

## <a name="instructions"></a>Anweisungen
 
## <a name="step-1-example-scenario"></a>Schritt 1: Beispielszenario

In diesem Beispiel werden einer Lizenz, die mit [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx) erstellt wurde, die benötigten Rechte hinzugefügt. Im Beispiel wird die Erstellung und Zuweisung der Rechte zur Lizenz über eine Liste mit Rechten veranschaulicht.

Den Benutzern werden die folgenden beiden Rechte hinzugefügt:

- joe@contoso.com zugewiesene *Lese*berechtigungen
- *Alle* Berechtigungen, die mary\_kay@contoso.com zugewiesen sind

      // Create User Rights structure
      IPC_USER_RIGHTS ownerRightForOwner = {0};

      // Create rights
      LPCWSTR rgwszOwnerRights[1] = {IPC_GENERIC_ALL};

      // Assign values to members of Rights structure
      ownerRightForOwner.User.dwType = IPC_USER_TYPE_IPC;
      ownerRightForOwner.User.wszID = IPC_USER_ID_OWNER;
      ownerRightForOwner.rgwszRights = rgwszOwnerRights;
      ownerRightForOwner.cRights = 1;

      // Create User Rights structure for Joe with Read permissions
      IPC_USER_RIGHTS joeReadRight = {0};
      LPCWSTR rgwszReadRights[1] = {IPC_GENERIC_READ};

      // Assign values to members of Rights structure for Joe
      joeReadRight.User.dwType = IPC_USER_TYPE_EMAIL;
      joeReadRight.User.wszID = "joe@contoso.com";
      joeReadRight.rgwszRights = rgwszReadRights;
      joeReadRight.cRights = 1;

      // Create User Rights structure for Mary Kay with Full permissions
      IPC_USER_RIGHTS mary_kayFullRight = {0};
      LPCWSTR rgwszFullRights[1] = {IPC_GENERIC_ALL};

      // Assign values to members of Rights structure for Mary Kay
      mary_kayFullRight.User.dwType = IPC_USER_TYPE_EMAIL;
      mary_kayFullRight.User.wszID = L"mary_kay@contoso.com";
      mary_kayFullRight.rgwszRights = rgwszFullRights;
      mary_kayFullRight.cRights = 1;

      // Create User Rights List and assign the above rights
      size_t uNoOfUserRights = 3;
      PIPC_USER_RIGHTS_LIST pUserRightsList = NULL;
      pUserRightsList = reinterpret_cast<PIPC_USER_RIGHTS_LIST>
      (new BYTE[ sizeof(IPC_USER_RIGHTS_LIST) + uNoOfUserRights * sizeof(IPC_USER_RIGHTS)]);

      if(pUserRightsList == NULL)
      {
        // Handle error
      }

      // Assign values to members of Rights List structure for Joe and Mary Kay
      (*pUserRightsList).cbSize = sizeof(IPC_USER_RIGHTS_LIST);
      (*pUserRightsList).cUserRights = uNoOfUserRights;
      (*pUserRightsList).rgUserRights[0] = ownerRightForOwner;
      (*pUserRightsList).rgUserRights[1] = joeReadRight;
      (*pUserRightsList).rgUserRights[2] = mary_kayFullRight;

      // Set the Rights List property on the license via its handle
      // hLicense is a license handle created with IpcCreateLicenseFromScratch
      hr = IpcSetLicenseProperty(hLicense, FALSE, IPC_LI_USER_RIGHTS_LIST, pUserRightsList);

      if(FAILED(hr))
      {
        // Handle the error
      }



## <a name="related-topics"></a>Verwandte Themen

- [Hinweise für Entwickler](developer-notes.md)
- [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx)
- [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)
