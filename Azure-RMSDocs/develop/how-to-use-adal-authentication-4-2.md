---
title: "Verwenden des Azure-Portals zur Konfiguration für die RMS-Authentifizierung | Azure RMS"
description: "Skizziert den Prozess für die Authentifizierung mit ADAL"
keywords: authentication, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 06/14/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2680b399-febb-4bd6-b844-ac3d1e69aca4
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f43f5605b1c341d7be618327038d1a86a305a5b
ms.openlocfilehash: cb82f0333ed17ee2994608baa3bbb50d42f19073


---

# Vorgehensweise: Verwenden des Azure-Portals zur Konfiguration für die RMS-Authentifizierung

Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory Authentication Library (ADAL).

Für diesen Ansatz muss Ihre Anwendung ihre eigene OAuth-Authentifizierung verwalten. Bei diesem Ansatz führt der RMS-Client einen anwendungsdefinierten Rückruf aus, wenn eine Authentifizierung erforderlich ist.

## Konfiguration über das Azure-Portal
Befolgen Sie zunächst die Anleitungen zur Konfiguration über das Azure-Portal, die unter [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md) beschrieben sind. Kopieren und speichern Sie die *Client-ID* und den *Umleitungs-URI* aus diesem Prozess zur späteren Verwendung.

## Codebeispiel
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


## Verwandte Themen

- [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)
- [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md)



<!--HONumber=Jun16_HO4-->


