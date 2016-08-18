---
title: Aktivieren von E-Mail-Benachrichtigungen | Azure RMS
description: "Mit E-Mail-Benachrichtigungen können Besitzer von geschützten Inhalten benachrichtigt werden, wenn auf ihre Inhalte zugegriffen wird."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5FB975EE-E4E5-4089-B8E1-CAFD5B9B34EC
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b2234f2209962d3dfda10958e740e04a5e5a4f13
ms.openlocfilehash: 54fc5037eaaa5c9ae2557aa6e4c67aa99a4143e6


---

# Exemplarische Vorgehensweise: Aktivieren von E-Mail-Benachrichtigungen

Mit E-Mail-Benachrichtigungen können Besitzer von geschützten Inhalten benachrichtigt werden, wenn auf ihre Inhalte zugegriffen wird.

Um die E-Mail-Benachrichtigungen für eine bestimmte Lizenz einzurichten, verwenden Sie [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty) zusammen mit dem Eigenschaftentypparameter *dwPropID* als [**IPC\_LI\_APP\_SPECIFIC\_DATA**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA) und die als [**IPC\_NAME\_VALUE\_LIST**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_name_value_list) formatierten Anwendungsdatenfelder.

    C++

    int numDataPairs = 3;

    IPC_NAME_VALUE propertyValuePairs [numDataPairs];

    // lcid field set to 0 causes the default lcid to be used

    propertyValuePairs[0] = {&quot;MS.Conetent.Name&quot;, 0, &quot;FinancialReport.docx&quot;};
    propertyValuePairs[1] = {&quot;MS.Notify.Enabled&quot;,0 , &quot;true&quot;};
    propertyValuePairs[2] = {&quot;MS.Notify.Culture&quot;,0 , “en-US”};

    IPC_NAME_VALUE_LIST emailNotificationAppData = {numDataPairs, propertyValuePairs};

    result = IpcSetLicenseProperty( licenseHandle, FALSE, IPC_LI_APP_SPECIFIC_DATA, emailNotificationAppData);
        

Die folgende Tabelle enthält die Anwendungsdatenfelder, also die Eigenschaftenname-Wert-Paare, für die RMS-E-Mail-Benachrichtigungen.


|Eigenschaftsname | Datentyp | Beispielwert | Hinweise |
|--------------|-----------|---------------|-------|
|MS.Content.Name|string|"FinancialReport.docx"|Dies ist ein Bezeichner, der dem geschützten Inhalt zugeordnet ist.<br><br> Für geschützte Dateien sollte dieser Wert den Namen der Datei ohne Pfadinformationen enthalten.<br><br> Bei anderen Arten von Inhalten, z. B. eine E-Mail-Nachricht sollte er den Betreff der E-Mail enthalten oder kann er leer sein.|
|MS.Notify.Enabled|string|"true" &#124; "false"|Wenn dieser Wert auf „true“ festgelegt ist, wird eine E-Mail-Benachrichtigung an den Besitzer der Veröffentlichungslizenz gesendet, sobald jemand versucht, diese zum Abrufen einer Endbenutzerlizenz zu verwenden.|
|MS.Notify.Culture|string|"de-DE"| **Quelle:** System.Globalization.CultureInfo.CurrentUICulture.Name <br><br>Dieser Wert wird verwendet, um die lokalisierte Sprache der E-Mail-Benachrichtigung sowie das Datums-/Uhrzeitformat und das Zahlenformat zu ermitteln, die in der E-Mail-Nachricht verwendet werden sollten.<br><br>Er sollte anhand der Benutzereinstellungen des Computers, auf dem die Veröffentlichungslizenz erstellt wird, oder basierend auf der bevorzugten Kultur des Besitzers der Veröffentlichungslizenz festgelegt werden.|
|MS.Notify.TZID|string|"Pacific Standard Time"|**Quelle:** TimeZoneInfo.Local.Id – Windows-Zeitzonen-ID.<br><br>Dieser Wert ist der Zeitzonenbezeichner des Microsoft Windows-Betriebssystems, der eine bestimmten Zeitzone und deren Eigenschaften beschreibt.|
|MS.Notify.TZO|string|"-480"|Dies ist das in Minuten angegebene Zeitzonenoffset der Zeitzone des Besitzers der Veröffentlichungslizenz von der UTC-Zeit.<br><br>Bei Angabe eines gültigen TZID-Werts wird der Offset der angegebenen Zeitzone verwendet, und dieser Wert wird ignoriert.<br><br>Dieser Wert wird eher von Veröffentlichungsplattformen, die nicht auf Windows basieren, verwendet, da diese keinen Zugriff auf die Liste der Zeitzone-ID-Werte des Windows-Betriebssystems haben.<br><br>Wenn kein Wert TZID-Wert angegeben wird, wird dieser Wert zur Berechnung des Zeitoffsets von Benachrichtigungen verwendet, und der TZSN-Wert wird (unabhängig von der Zeitzonenwert) zur Angabe des Namens der Zeitzone verwendet. Dies bewirkt, dass die Zeitzone fest ist und ggf. nicht für die Sommerzeit aktualisiert wird.<br><br>Beispiel:<br><br>Wenn TXID leer ist und TZ0 auf "-420" festgelegt ist und wenn für TZSN "Pacific Daylight Time" angegeben ist, werden alle Werte in der E-Mail-Benachrichtigung der Zeitzone "Pacific Daylight Time" angepasst und als solche angezeigt, selbst wenn die Sommerzeit derzeit nicht mehr in Kraft ist.<br><br>Wird dagegen ein TZID-Wert zusammen mit Werten für TZSN und TZDN angegeben, dann wird der in der E-Mail-Benachrichtigung angegebene Zeitpunkt entsprechend der Maßgabe, ob Datum und Uhrzeit im Sommerzeitmodus oder Standardmodus angezeigt werden sollen, angepasst und angezeigt.|
|MS.Notify.TZSN|string|"Pacific Standard Time"|**Quelle:** TimeZoneInfo.Local.StandardName – Standardzeitzonenname.<br><br>Dies sollte der lokalisierte Name des Standardzeitzonennamens der Zeitzone sein.|
|MS.Notify.TZDN|string|"Pazifische Sommerzeit"|**Quelle:** TimeZoneInfo.Local.DaylightName – Name der Sommerzeitzeitzone.<br><br>Dies sollte der lokalisierte Name der Sommerzeitzeitzone sein. Er kann mit dem Standardnamen identisch sein, wenn in der Zeitzone keine Sommerzeit unterstützt wird.|

## Verwandte Themen

* [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty)
* [**IPC\_LI\_APP\_SPECIFIC\_DATA**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA)
* [**IPC\_NAME\_VALUE\_LIST**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_name_value_list)
 

 



<!--HONumber=Jun16_HO4-->


