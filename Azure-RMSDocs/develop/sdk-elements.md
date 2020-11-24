---
title: Dateien der Entwicklungsumgebung | Azure RMS
description: Dieses Thema zeigt die Dateien der Entwicklungsumgebung und ihren relativen Installationsort auf Ihrem Computer.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: B57AC6F3-733C-42A8-AF83-0E15FBF27C99
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 0b2e741a1ad50c28248bc36fd3895971d429d5f5
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "95567814"
---
# <a name="development-environment-files"></a>Dateien der Entwicklungsumgebung

Dieses Thema zeigt die Dateien der Entwicklungsumgebung und ihren relativen Installationsort auf Ihrem Computer.

Das Rights Management Services SDK 2.1 umfasst die folgenden Dateien, die auf Ihrem Computer im Standardverzeichnis oder dem von Ihnen angegebenen Verzeichnis installiert sind: %MsipcSDKDir%.

|Datei|`Path`|BESCHREIBUNG|
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
|Msipc_s.lib|\lib|Bietet einen Einstiegspunkt für [IpcInitialize](/previous-versions/windows/desktop/msipc/ipcinitialize) für x86-Anwendungen.|
|Msipc.lib|\lib\x64|Zu verknüpfende Bibliothek, wenn mithilfe des RMS SDK 2.1 x64-Anwendungen erstellt werden sollen.|
|Msipc_s.lib|\lib\x64|Bietet einen Einstiegspunkt für [IpcInitialize](/previous-versions/windows/desktop/msipc/ipcinitialize) für x64-Anwendungen.|
|Genmanifest.exe|\tools|Generiert ein Manifest für die Verwendung während der Entwicklung einer RMS-fähigen Anwendung.|