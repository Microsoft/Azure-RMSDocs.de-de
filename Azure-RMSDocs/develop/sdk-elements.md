---
title: Dateien der Entwicklungsumgebung | Azure RMS
description: Dieses Thema zeigt die Dateien der Entwicklungsumgebung und ihren relativen Installationsort auf Ihrem Computer.
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B57AC6F3-733C-42A8-AF83-0E15FBF27C99
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4e96ba043584c5d8c140d6804c72cf63362f58c5
ms.openlocfilehash: a251723b6c42058091d57067724e89a1816bcaa1


---

# <a name="development-environment-files"></a>Dateien der Entwicklungsumgebung

Dieses Thema zeigt die Dateien der Entwicklungsumgebung und ihren relativen Installationsort auf Ihrem Computer.

Das Rights Management Services SDK 2.1 umfasst die folgenden Dateien, die auf Ihrem Computer im Standardverzeichnis oder dem von Ihnen angegebenen Verzeichnis installiert sind: %MsipcSDKDir%.

|Datei|Pfad|Beschreibung|
|----|----|-----------|
|ReadMe.htm| \ | Enthält einen Link zur RMS-Hilfe und zu den [Versionshinweisen](release-notes-rtm.md).|
|Isvtier5appsigningprivkey.dat|\bin|Enthält den privaten Schlüssel, um ein Manifest für die Verwendung während der Entwicklung einer RMS-fähigen Anwendung zu generieren.|
|Isvtier5appsigningpubkey.dat|\bin|Enthält den öffentlichen Schlüssel, um ein Manifest für die Verwendung während der Entwicklung einer RMS-fähigen Anwendung zu generieren.|
|Isvtier5appsignsdk_client.xml|\bin|Dient zum Generieren eines Manifest für die Verwendung während der Entwicklung einer RMS-fähigen Anwendung.|
|YourAppName.isv.mcf|\bin|Eine Manifestkonfigurationsdatei für einen Textbaustein, mit der Sie während der Entwicklung einer RMS-fähigen Anwendung ein Manifest generieren können.|
|Ipcsecproc_isv.dll|\bin\x86|Intern von Active Directory Rights Management Services Client 2.1 während des Betriebs in der ISV-Hierarchie für x86-Anwendungen verwendete DLL.|
|Ipcsecproc_ssp_isv.dll|\bin\x86|Intern von AD RMS 2.1 während des Betriebs in der ISV-Hierarchie für x86-Anwendungen verwendete DLL.|
|Ipcsecproc_isv.dll|\bin\x64|Intern von AD RMS Client 2.1 während des Betriebs in der ISV-Hierarchie für x64-Anwendungen verwendete DLL.|
|Ipcsecproc_ssp_isv.dll|\bin\x64|Intern von AD RMS Client 2.1 während des Betriebs in der ISV-Hierarchie für x64-Anwendungen verwendete DLL.|
|Msipc.h|\inc|Hauptdatei, die für das RMS SDK 2.1 einzuschließen ist.|
|Ipcprot.h|\inc|Enthält die vom RMS SDK 2.1 exportierte öffentliche Schnittstelle.|
|Ipcbase.h|\inc|Enthält grundlegende Typen und Hilfsfunktionen, die vom RMS SDK 2.1 exportiert wurden.|
|Ipcerror.h|\inc|Enthält die vom RMS SDK 2.1 exportierten öffentlichen Fehlercodes.|
|Ipcfile.h|\inc|Enthält die vom RMS SDK 2.1 exportierten Datei-API-Schnittstellen.|
|Msipc.lib|\lib|Zu verknüpfende Bibliothek, wenn mithilfe des RMS SDK 2.1 x86-Anwendungen erstellt werden sollen.|
|Msipc_s.lib|\lib|Bietet einen Einstiegspunkt für [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) für x86-Anwendungen.|
|Msipc.lib|\lib\x64|Zu verknüpfende Bibliothek, wenn mithilfe des RMS SDK 2.1 x64-Anwendungen erstellt werden sollen.|
|Msipc_s.lib|\lib\x64|Bietet einen Einstiegspunkt für [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) für x64-Anwendungen.|
|Genmanifest.exe|\tools|Generiert ein Manifest für die Verwendung während der Entwicklung einer RMS-fähigen Anwendung.|
 

 

 



<!--HONumber=Oct16_HO3-->


