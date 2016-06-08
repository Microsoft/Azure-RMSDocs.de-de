---
# required metadata

title: Nachverfolgung von Inhalten | Azure RMS
description: Grundlegende Leitfäden zum Implementieren der Dokumentnachverfolgung
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Dieser SDK-Inhalt ist nicht aktuell. Für kurze Zeit finden Sie die [aktuelle Version](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) der Dokumentation auf MSDN. **
# Nachverfolgung von Inhalten

Dieses Thema enthält grundlegende Leitfäden zum Implementieren der Dokumentnachverfolgung von Inhalten, die durch Rights Management Services SDK 2.1 geschützt sind.

Dokumentnachverfolgung ist ein Feature des Rights Management-Systems. Durch das Hinzufügen bestimmter Metadaten während des Dokumentschutzprozesses kann ein Dokument beim Nachverfolgungsdienstportal registriert werden, das dann mehrere Optionen für die Nachverfolgung bereitstellt.

Verwenden Sie diese APIs zum Hinzufügen/Aktualisieren einer Inhaltslizenz mit Metadaten für die Dokumentnachverfolgung.

-   [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
-   [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

    Wir erwarten, dass Sie alle Metadateneigenschaften festlegen. Diese werden im Folgenden nach Typ aufgelistet.

    Weitere Informationen finden Sie unter [**Lizenzmetadaten-Eigenschaftstypen**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types).

    -   **IPC\_MD\_CONTENT\_PATH**

        Damit identifizieren Sie das nachverfolgte Dokument. In Fällen, in denen ein vollständiger Pfad nicht möglich ist, geben Sie nur den Dateinamen an.

    -   **IPC\_MD\_CONTENT\_NAME**

        Damit identifizieren Sie den Namen des nachverfolgten Dokuments.

    -   **IPC\_MD\_NOTIFICATION\_TYPE**

        Damit geben Sie an, wann eine Benachrichtigung gesendet wird. Weitere Informationen finden Sie unter [**Benachrichtigungstyp**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type).

    -   **IPC\_MD\_NOTIFICATION\_PREFERENCE**

        Damit geben Sie den Benachrichtigungstyp an. Weitere Informationen finden Sie unter [**Benachrichtigungseinstellungen**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference).

    -   **IPC\_MD\_DATE\_MODIFIED**

        Es wird empfohlen, dieses Datum bei jedem Klicken des Benutzers auf **Speichern** festzulegen.

    -   **IPC\_MD\_DATE\_CREATED**

        Das Ursprungsdatum der Datei.

-   [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

Verwenden Sie die richtige dieser APIs, um die Metadaten Ihrer Datei oder Ihrem Stream hinzuzufügen.

-   [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
-   [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

Verwenden Sie schließlich diese API, um das nachverfolgte Dokument beim Nachverfolgungssystem zu registrieren.

-   [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

Es folgt ein Codeausschnitt, der ein Beispiel für das Festlegen der Metadaten für die Dokumentnachverfolgung und das Aufrufen für die Registrierung beim Nachverfolgungssystem zeigt.



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

    LOGSTATUS_EX(L&quot;Encrypt file with official template...&quot;);

    hr =IpcfEncryptFileWithMetadata(  wszWorkingFile.c_str(),
                                       m_wszTestTemplateID.c_str(),
                                       IPCF_EF_TEMPLATE_ID,
                                       0,
                                       NULL,
                                       NULL,
                                       &amp;md,
                                       &amp;wszOutputFile);

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


## Verwandte Themen


* [**Lizenzmetadaten-Eigenschaftstypen**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types)
* [**Benachrichtigungseinstellungen**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [**Benachrichtigungtyp**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type)
* [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)
 

 


<!--HONumber=Jun16_HO1-->


