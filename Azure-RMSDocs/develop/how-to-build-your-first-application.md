---
# required metadata

title: IPCHelloWorld – Beispiel-Anwendung | Azure RMS
description: Dieses Thema enthält eine Anleitung zum Erstellen einer rechtlich geschützten Beispielanwendung.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 581451A2-9558-4D0D-9D01-BEAB282C5A83
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
# IPCHelloWorld – Beispielanwendung

Dieses Thema enthält eine Anleitung zum Erstellen einer rechtlich geschützten Beispielanwendung.

Anhand dieser einfachen Anwendung IPCHelloWorld können Sie zu den grundlegenden Konzepten und den Code einer rechtlich geschützten Anwendung kennenlernen.

Laden Sie die Beispielanwendung [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440) von Microsoft Connect herunter. Die restlichen von dieser Website herunterladbaren Artikel sind der Einfachheit halber hier integriert.

**Hinweis** Das IPCHelloWorld-Projekt ist bereits für das Rights Management Services SDK 2.1 konfiguriert. Informationen zum Konfigurieren eines neuen Projekts, das RMS SDK 2.1 verwendet, finden Sie unter [Konfigurieren von Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md).

 
In den folgenden Abschnitten werden die grundlegende Schritte und erforderlichen Kenntnisse behandelt.

## Laden von „MSIPC.dll“

Bevor Sie eine RMS SDK 2.1-Funktion aufrufen können, müssen Sie zunächst die [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)-Funktion zum Laden der Datei „msipc.dll“ aufrufen.



    hr = IpcInitialize();

    if (FAILED(hr))
    {
      wprintf(L"Failed to initialize MSIPC. Are you sure the runtime is installed?\n");
      goto exit;
    }



## Auflisten von Vorlagen

Eine RMS-Vorlage definiert die zum Schutz der Daten verwendete Richtlinie, d. h. sie definiert die Benutzer, die Zugriff auf die Daten erhalten und ihre Rechte. RMS-Vorlagen werden auf dem RMS-Server installiert.

Der folgende Codeausschnitt listet die verfügbaren RMS-Vorlagen vom RMS-Standardserver auf.



    hr = IpcGetTemplateList(NULL, 0, 0, NULL, NULL, &pcTil);

    if (FAILED(hr))
    {
      DisplayError(L"IpcGetTemplateList failed", hr);
      goto exit;
    }



Dieser Aufruf ruft die RMS-Vorlagen ab, die auf dem Standardserver installiert sind, lädt die Ergebnisse in die [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)-Struktur, die durch die *pcTil*-Variable bezeichnet wird, und zeigt dann die Vorlagen an.



    if (0 == pcTil->cTi)
    {
      wprintf(L"* No templates configured for your RMS server * \n\n");
      wprintf(L"\\------------------------------------------------------\n\n");
      goto exit;
    }

    for (DWORD dw = 0; dw < pcTil->cTi; dw++)
    {
      wprintf(L"Template #%d:\n", dw);
      wprintf(L"    Name:         %s\n", pcTil->aTi[dw].wszName);
      wprintf(L"    Issued by:    %s\n", pcTil->aTi[dw].wszIssuerDisplayName);
      wprintf(L"    Description:  %s\n", pcTil->aTi[dw].wszDescription);
      wprintf(L"\n");
    }



## Serialisieren einer Lizenz

Bevor Sie Daten schützen können, müssen Sie eine Lizenz serialisieren und einen Inhaltsschlüssel erhalten. Der Inhaltsschlüssel wird zum Verschlüsseln vertraulicher Daten verwendet. Die serialisierte Lizenz wird in der Regel den verschlüsselten Daten angefügt und wird vom Consumer der geschützten Daten verwendet. Der Consumer muss die [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)-Funktion mit der serialisierten Lizenz aufrufen, um den Inhaltsschlüssel zum Entschlüsseln des Inhalts und zum Abrufen der mit dem Inhalt verknüpften Richtlinie zu erhalten.

Verwenden Sie der Einfachheit halber die RMS-Vorlage, die von [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) zuerst zurückgegeben wird, um eine Lizenz zu serialisieren.

In der Regel verwenden Sie ein Dialogfeld, um den Benutzer die gewünschte Vorlage auswählen zu lassen.



    hr = IpcSerializeLicense((LPCVOID)pcTil->aTi[0].wszID, IPC_SL_TEMPLATE_ID,
    0, NULL, &hContentKey, &pSerializedLicense);

    if (FAILED(hr))
    {
      DisplayError(L"IpcSerializeLicense failed", hr);
      goto exit;
    }



Nach diesem Schritt verfügen Sie über den Inhaltsschlüssel *hContentKey* und die serialisierte Lizenz *pSerializedLicense*, die Sie an die geschützten Daten anfügen müssen.

## Schützen von Daten

Nun können Sie die sensiblen Daten mit der [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)-Funktion verschlüsseln. Zunächst müssen Sie die **IpcEncrypt**-Funktion fragen, wie groß die verschlüsselten Daten sein werden.



    cbText = (DWORD)(sizeof(WCHAR)*(wcslen(wszText)+1));
    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    NULL, 0, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }



Hier enthält *wszText* den Nur-Text, den Sie schützen möchten. Die [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)-Funktion gibt die Größe der verschlüsselten Daten im *cbEncrypted*-Parameter zurück.

Nun reservieren Sie Arbeitsspeicher für die verschlüsselten Daten.



    pbEncrypted = (PBYTE)LocalAlloc(LPTR, cbEncrypted);

    if (NULL == pbEncrypted) {
      wprintf(L"Out of memory\n");
      goto exit;
    }


Schließlich können Sie die tatsächliche Verschlüsselung ausführen.



    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    pbEncrypted, cbEncrypted, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }


Nach diesem Schritt haben Sie die verschlüsselten Daten *pbEncrypted* und die serialisierten Lizenz *pSerializedLicense*, die von den Consumern zum Entschlüsseln der Daten verwendet werden.

## Fehlerbehandlung

In dieser Beispielanwendung wird die **DisplayError**-Funktion zur Fehlerbehandlung verwendet.



    void DisplayError(LPCWSTR wszErrorInfo, HRESULT hrError)
    {
        LPCWSTR wszErrorMessageText = NULL;

        if (SUCCEEDED(IpcGetErrorMessageText(hrError, 0, &wszErrorMessageText))) {
          wprintf(L"%s: 0x%08X (%s)\n", wszErrorInfo, hrError, wszErrorMessageText);
        }
        else {
          wprintf(L"%s: 0x%08X\n", wszErrorInfo, hrError);
        }
    }   


Die **DisplayError**-Funktion verwendet die [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext)-Funktion, um die Fehlermeldung aus dem entsprechenden Fehlercode abzurufen, und gibt sie an die Standardausgabe aus.

## Bereinigen

Bevor Sie fertig sind, müssen Sie auch alle reservierten Ressourcen freizugeben.



    if (NULL != pbEncrypted) {
      LocalFree((HLOCAL)pbEncrypted);
    }

    if (NULL != pSerializedLicense) {
      IpcFreeMemory((LPVOID)pSerializedLicense);
    }

    if (NULL != hContentKey) {
      IpcCloseHandle((IPC_HANDLE)hContentKey);
    }

    if (NULL != pcTil) {
      IpcFreeMemory((LPVOID)pcTil);
    }


## Verwandte Themen

* [Hinweise für Entwickler](developer-notes.md)
* [Konfigurieren von Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
* [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)
* [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext)
* [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
 

 


<!--HONumber=Jun16_HO1-->


