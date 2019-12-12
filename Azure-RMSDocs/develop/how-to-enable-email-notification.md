---
title: Aktivieren von E-Mail-Benachrichtigungen | Azure RMS
description: Mit E-Mail-Benachrichtigungen können Besitzer von geschützten Inhalten benachrichtigt werden, wenn auf ihre Inhalte zugegriffen wird.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5FB975EE-E4E5-4089-B8E1-CAFD5B9B34EC
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 4427eefb4dec3c2d5d4f8f07b3ef2c68ed1fd9d7
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "68788496"
---
# <a name="how-to-enable-email-notification"></a>Exemplarische Vorgehensweise: Aktivieren von E-Mail-Benachrichtigungen

Mit E-Mail-Benachrichtigungen können Besitzer von geschützten Inhalten benachrichtigt werden, wenn auf ihre Inhalte zugegriffen wird.

Um die E-Mail-Benachrichtigungen für eine bestimmte Lizenz einzurichten, verwenden Sie [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx) zusammen mit dem Eigenschaftentypparameter *dwPropID* als [IPC\_LI\_APP\_SPECIFIC\_DATA](https://msdn.microsoft.com/library/hh535287.aspx) und die als [IPC\_NAME\_VALUE\_LIST](https://msdn.microsoft.com/library/hh535277.aspx) formatierten Anwendungsdatenfelder.

    C++

    int numDataPairs = 3;

    IPC_NAME_VALUE propertyValuePairs [numDataPairs];

    // lcid field set to 0 causes the default lcid to be used

    propertyValuePairs[0] = {"MS.Conetent.Name", 0, "FinancialReport.docx"};
    propertyValuePairs[1] = {"MS.Notify.Enabled",0 , "true"};
    propertyValuePairs[2] = {"MS.Notify.Culture",0 , “en-US”};

    IPC_NAME_VALUE_LIST emailNotificationAppData = {numDataPairs, propertyValuePairs};

    result = IpcSetLicenseProperty( licenseHandle, FALSE, IPC_LI_APP_SPECIFIC_DATA, emailNotificationAppData);


Die folgende Tabelle enthält die Anwendungsdatenfelder, also die Eigenschaftenname-Wert-Paare, für die RMS-E-Mail-Benachrichtigungen.


|Eigenschaftsname | Datentyp | Beispielwert | Anmerkungen |
|--------------|-----------|---------------|-------|
|MS.Content.Name|string|"FinancialReport.docx"|Dies ist ein Bezeichner, der dem geschützten Inhalt zugeordnet ist.<br><br> Für geschützte Dateien sollte dieser Wert den Namen der Datei ohne Pfadinformationen enthalten.<br><br> Bei anderen Arten von Inhalten, z. B. eine E-Mail-Nachricht sollte er den Betreff der E-Mail enthalten oder kann er leer sein.|
|MS.Notify.Enabled|string|"true" &#124; "false"|Wenn dieser Wert auf „true“ festgelegt ist, wird eine E-Mail-Benachrichtigung an den Besitzer der Veröffentlichungslizenz gesendet, sobald jemand versucht, diese zum Abrufen einer Endbenutzerlizenz zu verwenden.|
|MS.Notify.Culture|string|"de-DE"| **Quelle:** System.Globalization.CultureInfo.CurrentUICulture.Name <br><br>Dieser Wert wird verwendet, um die lokalisierte Sprache der E-Mail-Benachrichtigung sowie das Datums-/Uhrzeitformat und das Zahlenformat zu ermitteln, die in der E-Mail-Nachricht verwendet werden sollten.<br><br>Er sollte anhand der Benutzereinstellungen des Computers, auf dem die Veröffentlichungslizenz erstellt wird, oder basierend auf der bevorzugten Kultur des Besitzers der Veröffentlichungslizenz festgelegt werden.|
|MS.Notify.TZID|string|"Pacific Standard Time"|**Quelle:** TimeZoneInfo.Local.Id – Windows-Zeitzonen-ID.<br><br>Dieser Wert ist der Zeitzonenbezeichner des Microsoft Windows-Betriebssystems, der eine bestimmten Zeitzone und deren Eigenschaften beschreibt.|
|MS.Notify.TZO|string|"-480"|Dies ist das in Minuten angegebene Zeitzonenoffset der Zeitzone des Besitzers der Veröffentlichungslizenz von der UTC-Zeit.<br><br>Bei Angabe eines gültigen TZID-Werts wird der Offset der angegebenen Zeitzone verwendet, und dieser Wert wird ignoriert.<br><br>Dieser Wert wird eher von Veröffentlichungsplattformen, die nicht auf Windows basieren, verwendet, da diese keinen Zugriff auf die Liste der Zeitzone-ID-Werte des Windows-Betriebssystems haben.<br><br>Wenn kein Wert TZID-Wert angegeben wird, wird dieser Wert zur Berechnung des Zeitoffsets von Benachrichtigungen verwendet, und der TZSN-Wert wird (unabhängig von der Zeitzonenwert) zur Angabe des Namens der Zeitzone verwendet. Dies bewirkt, dass die Zeitzone fest ist und ggf. nicht für die Sommerzeit aktualisiert wird.<br><br>Beispiele:<br><br>Wenn TXID leer ist und TZ0 auf "-420" festgelegt ist und wenn für TZSN "Pacific Daylight Time" angegeben ist, werden alle Werte in der E-Mail-Benachrichtigung der Zeitzone "Pacific Daylight Time" angepasst und als solche angezeigt, selbst wenn die Sommerzeit derzeit nicht mehr in Kraft ist.<br><br>Wird dagegen ein TZID-Wert zusammen mit Werten für TZSN und TZDN angegeben, dann wird der in der E-Mail-Benachrichtigung angegebene Zeitpunkt entsprechend der Maßgabe, ob Datum und Uhrzeit im Sommerzeitmodus oder Standardmodus angezeigt werden sollen, angepasst und angezeigt.|
|MS.Notify.TZSN|string|"Pacific Standard Time"|**Quelle:** TimeZoneInfo.Local.StandardName – Standardzeitzonenname.<br><br>Dies sollte der lokalisierte Name des Standardzeitzonennamens der Zeitzone sein.|
|MS.Notify.TZDN|string|"Pazifische Sommerzeit"|**Quelle:** TimeZoneInfo.Local.DaylightName – Name der Sommerzeitzeitzone.<br><br>Dies sollte der lokalisierte Name der Sommerzeitzeitzone sein. Er kann mit dem Standardnamen identisch sein, wenn in der Zeitzone keine Sommerzeit unterstützt wird.|

## <a name="related-topics"></a>Zugehörige Themen

- [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx)
- [IPC\_LI\_APP\_SPECIFIC\_DATA](https://msdn.microsoft.com/library/hh535287.aspx)
- [IPC\_NAME\_VALUE\_LIST](https://msdn.microsoft.com/library/hh535277.aspx)
