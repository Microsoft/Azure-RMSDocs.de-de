---
title: "Verwenden des Azure-Portals zur Konfiguration für die RMS-Authentifizierung | Azure RMS"
description: "Skizziert den Prozess für die Authentifizierung mit ADAL"
keywords: Authentifizierung, RMS, ADAL
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2680b399-febb-4bd6-b844-ac3d1e69aca4
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 9a777b9a13c5ecff3083f4552a8c81f4e42c5cb2


---

# <a name="how-to-use-azure-portal-to-configure-for-rms-authentication"></a>Vorgehensweise: Verwenden des Azure-Portals zur Konfiguration für die RMS-Authentifizierung

Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory Authentication Library (ADAL).

Für diesen Ansatz muss Ihre Anwendung ihre eigene OAuth-Authentifizierung verwalten. Bei diesem Ansatz führt der RMS-Client einen anwendungsdefinierten Rückruf aus, wenn eine Authentifizierung erforderlich ist.

## <a name="configure-via-azure-portal"></a>Konfiguration über das Azure-Portal
Befolgen Sie zunächst die Anleitungen zur Konfiguration über das Azure-Portal, die unter [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md) beschrieben sind. Kopieren und speichern Sie die *Client-ID* und den *Umleitungs-URI* aus diesem Prozess zur späteren Verwendung.

## <a name="code-sample"></a>Codebeispiel
Nachfolgend ist ein Codeausschnitt aus dem größeren Codebeispiel für mobile Clients zur Aktivierung der Azure ADAL gezeigt. Weitere Informationen finden Sie im vollständigen Beispiel unter [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)

       /**
       * Instantiates a new rms authentication callback.
       *
       * @param parentActivity the parent activity
       * @throws NoSuchAlgorithmException the no such algorithm exception
       * @throws InvalidKeySpecException the invalid key spec exception
       * @throws UnsupportedEncodingException the unsupported encoding exception
       */

       public MsipcAuthenticationCallback(Activity parentActivity) throws NoSuchAlgorithmException, InvalidKeySpecException, UnsupportedEncodingException
       {
         mParentActivity = parentActivity;
         setADALKeyStore();

         /**
         * Note: Following values of are client_id and redirect_uri are for demo purpose only.
         * Your values will come from the preceeding Azure Portal process.
         */
         mClientId = "com.microsoft.rightsmanagement.sampleapp";
         mRedirectURI = mClientId + "://authorize";
       }


## <a name="related-topics"></a>Verwandte Themen

- [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)
- [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


