---
title: 'Vorgehensweise: Aktivieren der Dokumentnachverfolgung und -sperrung | Azure RMS'
description: Dieser Artikel bietet grundlegende Anleitungen zum Implementieren der Dokumentnachverfolgung für Inhalte sowie Beispielcode für Metadatenaktualisierungen und zum Erstellen einer Schaltfläche „Verwendung nachverfolgen“ für Ihre App.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 35bcfbb8ea3afeb1cfce3703ca59131dbcacb040
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331767"
---
# <a name="how-to-enable-document-tracking-and-revocation"></a>Exemplarische Vorgehensweise: Aktivieren von Dokumentenverfolgung und -widerruf

Dieses Thema bietet grundlegende Anleitungen zum Implementieren der Dokumentnachverfolgung für Inhalte sowie Beispielcode für Metadatenaktualisierungen und zum Erstellen einer Schaltfläche **Verwendung nachverfolgen** für Ihre App.

## <a name="steps-to-implement-document-tracking"></a>Schritte zum Implementieren der Dokumentnachverfolgung

In den Schritten 1 und 2 wird die Nachverfolgung des Dokuments aktiviert. In Schritt 3 wird der Zugriff der App-Benutzer auf die Website für die Dokumentnachverfolgung eingerichtet, sodass Ihre geschützten Dokumente nachverfolgt und gesperrt werden können.

1. Hinzufügen von Metadaten für die Dokumentnachverfolgung
2. Registrieren des Dokuments beim RMS-Dienst
3. Hinzufügen einer Schaltfläche „Verwendung nachverfolgen“ zur App

Die Implementierungsdetails für diese Schritte folgen.

## <a name="1-add-document-tracking-metadata"></a>1. Hinzufügen von Metadaten für die Dokumentnachverfolgung

Dokumentnachverfolgung ist ein Feature des Rights Management-Systems. Durch das Hinzufügen bestimmter Metadaten während des Dokumentschutzprozesses kann ein Dokument beim Nachverfolgungsdienstportal registriert werden, das dann mehrere Optionen für die Nachverfolgung bereitstellt.

Verwenden Sie diese APIs zum Hinzufügen/Aktualisieren einer Inhaltslizenz mit Metadaten für die Dokumentnachverfolgung.


Im Prinzip sind nur für die Dokumentenverfolgung nur das **contentName**- und das **notificationType**-Objekt erforderlich.


- [IpcCreateLicenseMetadataHandle](https://msdn.microsoft.com/library/dn974050.aspx)
- [IpcSetLicenseMetadataProperty](https://msdn.microsoft.com/library/dn974059.aspx)

  Wir erwarten, dass Sie alle Metadateneigenschaften festlegen. Diese werden im Folgenden nach Typ aufgelistet.

  Weitere Informationen finden Sie unter [Lizenzmetadaten-Eigenschaftstypen](https://msdn.microsoft.com/library/dn974062.aspx).

  - **IPC_MD_CONTENT_PATH**

    Hiermit identifizieren Sie das nachverfolgte Dokument. In Fällen, in denen ein vollständiger Pfad nicht möglich ist, geben Sie nur den Dateinamen an.

  - **IPC_MD_CONTENT_NAME**

    Hiermit identifizieren Sie den Namen des nachverfolgten Dokuments.

  - **IPC_MD_NOTIFICATION_TYPE**

    Damit geben Sie an, wann eine Benachrichtigung gesendet wird. Weitere Informationen finden Sie unter „Benachrichtigungstyp“.

  - **IPC_MD_NOTIFICATION_PREFERENCE**

    Damit geben Sie den Benachrichtigungstyp an. Weitere Informationen finden Sie unter „Benachrichtigungseinstellungen“.

  - **IPC_MD_DATE_MODIFIED**

    Es wird empfohlen, dieses Datum bei jedem Klicken des Benutzers auf „Speichern“ festzulegen.

  - **IPC_MD_DATE_CREATED**

    Legen Sie hier das Ursprungsdatum der Datei fest.

- [IpcSerializeLicenseWithMetadata](https://msdn.microsoft.com/library/dn974058.aspx)

Verwenden Sie die richtige dieser APIs, um die Metadaten Ihrer Datei oder Ihrem Stream hinzuzufügen.

- [IpcfEncryptFileWithMetadata](https://msdn.microsoft.com/library/dn974052.aspx)
- [IpcfEncryptFileStreamWithMetadata](https://msdn.microsoft.com/library/dn974051.aspx)

Verwenden Sie schließlich diese API, um das nachverfolgte Dokument beim Nachverfolgungssystem zu registrieren.

- [IpcRegisterLicense](https://msdn.microsoft.com/library/dn974057.aspx)


## <a name="2-register-the-document-with-the-rms-service"></a>2. Registrieren des Dokuments beim RMS-Dienst

Es folgt ein Codeausschnitt, der ein Beispiel für das Festlegen der Metadaten für die Dokumentnachverfolgung und das Aufrufen für die Registrierung beim Nachverfolgungssystem zeigt.

      C++
      HRESULT hr = S_OK;
      LPCWSTR wszOutputFile = NULL;
      wstring wszWorkingFile;
      IPC_LICENSE_METADATA md = {0};

      md.cbSize = sizeof(IPC_LICENSE_METADATA);
      md.dwNotificationType = IPCD_CT_NOTIFICATION_TYPE_ENABLED;
      md.dwNotificationPreference = IPCD_CT_NOTIFICATION_PREF_DIGEST;
      //file origination date, current time for this example
      md.ftDateCreated = GetCurrentTime();
      md.ftDateModified = GetCurrentTime();

      LOGSTATUS_EX(L"Encrypt file with official template...");

      hr =IpcfEncryptFileWithMetadata( wszWorkingFile.c_str(),
                               m_wszTestTemplateID.c_str(),
                               IPCF_EF_TEMPLATE_ID,
                               0,
                               NULL,
                               NULL,
                               &md,
                               &wszOutputFile);

     /* This will contain the serialized license */
     PIPC_BUFFER pSerializedLicense;

     /* the context to use for the call */
     PCIPC_PROMPT_CTX pContext;

     wstring wstrContentName(“MyDocument.txt”);
     bool sendLicenseRegistrationNotificationEmail = FALSE;

     hr = IpcRegisterLicense( pSerializedLicense,
                        0,
                        pContext,
                        wstrContentName.c_str(),
                        sendLicenseRegistrationNotificationEmail);

## <a name="add-a-track-usage-button-to-your-app"></a>Hinzufügen einer Schaltfläche **Verwendung nachverfolgen** zur App

Das Hinzufügen einer Schaltfläche **Verwendung nachverfolgen** zur App ist genauso einfach wie die Verwendung eines der folgenden URL-Formate:

- Verwenden der Inhalts-ID
  - Rufen Sie die Inhalts-ID mit [IpcGetLicenseProperty](https://msdn.microsoft.com/library/hh535265.aspx) oder der [IpcGetSerializedLicenseProperty](https://msdn.microsoft.com/library/hh995038.aspx) ab, wenn die Lizenz serialisiert ist, und verwenden Sie die Lizenzeigenschaft **IPC_LI_CONTENT_ID**. Weitere Informationen finden Sie unter den Angaben zu [Lizenzeigenschaftstypen](https://msdn.microsoft.com/library/hh535287.aspx).
  - Verwenden Sie bei den Metadaten **ContentId** und **Issuer** das folgende Format: `https://track.azurerms.com/#/{ContentId}/{Issuer}`

    Beispiel – `https://track.azurerms.com/#/summary/05405df5-8ad6-4905-9f15-fc2ecbd8d0f7/janedoe@microsoft.com`

- Wenn Sie nicht auf die Metadaten zugreifen können (d.h., Sie untersuchen die ungeschützte Version des Dokuments), können Sie **Content_Name** im folgenden Format verwenden: `https://track.azurerms.com/#/?q={ContentName}`

  Beispiel: https://track.azurerms.com/#/?q=Secret!.txt

Der Client muss lediglich einen Browser mit der entsprechenden URL öffnen. Im Portal für die RMS-Dokumentnachverfolgung werden die Authentifizierung und alle erforderlichen Umleitungen verarbeitet.

## <a name="related-topics"></a>Verwandte Themen

* [License metadata property types (Lizenzmetadaten-Eigenschaftstypen)](https://msdn.microsoft.com/library/dn974062.aspx)
* [Notification preference (Benachrichtigungseinstellung)](https://msdn.microsoft.com/library/dn974063.aspx)
* [Notification type (Benachrichtigungtyp)](https://msdn.microsoft.com/library/dn974064.aspx)
* [IpcCreateLicenseMetadataHandle](https://msdn.microsoft.com/library/dn974050.aspx)
* [IpcSetLicenseMetadataProperty](https://msdn.microsoft.com/library/dn974059.aspx)
* [IpcSerializeLicenseWithMetadata](https://msdn.microsoft.com/library/dn974058.aspx)
* [IpcfEncryptFileWithMetadata](https://msdn.microsoft.com/library/dn974052.aspx)
* [IpcfEncryptFileStreamWithMetadata](https://msdn.microsoft.com/library/dn974051.aspx)
* [IpcRegisterLicense](https://msdn.microsoft.com/library/dn974057.aspx)

