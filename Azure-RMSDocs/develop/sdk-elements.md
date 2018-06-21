---
title: Dateien der Entwicklungsumgebung | Azure RMS
description: Dieses Thema zeigt die Dateien der Entwicklungsumgebung und ihren relativen Installationsort auf Ihrem Computer.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B57AC6F3-733C-42A8-AF83-0E15FBF27C99
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f79c0d60bf460c0f8cca68f6b0447303a383c686
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
ms.locfileid: "27765781"
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

[!INCLUDE[Commenting house rules](../includes/houserules.md)]