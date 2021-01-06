---
title: 'Schnellstart: Auflisten der Vertraulichkeitsbezeichnungen in einem MIP-Mandanten (Microsoft Information Protection) mithilfe des C++-MIP SDKs'
description: In diesen Schnellstart wird veranschaulicht, wie Sie das Microsoft Information Protection SDK mit C++ nutzen, um die Vertraulichkeitsbezeichnungen in Ihrem Mandanten aufzulisten.
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.date: 01/18/2019
ms.author: mbaldwin
ms.custom: has-adal-ref
ms.openlocfilehash: 14b36ecee7fc49c5b50d627e6ef1ab95d436d7ee
ms.sourcegitcommit: 8e48016754e6bc6d051138b3e3e3e3edbff56ba5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865262"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C++)

In diesem Schnellstart erfahren Sie, wie Sie die MIP-File-API verwenden, um die für Ihre Organisation konfigurierten Vertraulichkeitsbezeichnungen aufzulisten.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart für die Initialisierung der Clientanwendung (C++)](quick-app-initialization-cpp.md) ab, in dem Sie eine Visual Studio-Projektmappe für den Einstieg erstellen. Dieser Schnellstart zum „Auflisten der Vertraulichkeitsbezeichnungen“ baut auf der vorherigen Erstellung der Startprojektmappe auf.
- Optional: Lesen Sie sich die Konzepte zu [Klassifizierungsbezeichnungen](concept-classification-labels.md) durch.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Hinzufügen von Logik zur Liste der Vertraulichkeitsbezeichnungen

Im Folgenden fügen Sie der Liste von Vertraulichkeitsbezeichnungen Ihrer Organisation Logik mithilfe des FileEnginge-Objekts hinzu.

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Initialisierung der Clientanwendung (C++)“ erstellt haben.

2. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Fügen Sie Folgendes der `using`-Anweisung nach `using mip::FileEngine;` oben in der Datei hinzu:

   ```cpp
   using std::endl;
   ```

4. Fügen Sie den folgenden Code gegen Ende des `main()`-Texts zwischen der schließenden Klammer `}` des letzten `catch`-Blocks und über `return 0;` (wo Sie im vorherigen Schnellstart aufgehört haben) ein:

   ```cpp
   // List sensitivity labels
   cout << "\nSensitivity labels for your organization:\n";
   auto labels = engine->ListSensitivityLabels();
   for (const auto& label : labels)
   {
      cout << label->GetName() << " : " << label->GetId() << endl;

      for (const auto& child : label->GetChildren())
      {
        cout << "->  " << child->GetName() << " : " << child->GetId() << endl;
      }
   }
   system("pause");
   ```

## <a name="create-a-powershell-script-to-generate-access-tokens"></a>Erstellen eines PowerShell-Skripts zum Generieren von Zugriffstoken

Verwenden Sie das folgende PowerShell-Skript, um die Zugriffstoken zu generieren, die vom SDK in Ihrer `AuthDelegateImpl::AcquireOAuth2Token`-Implementierung gefordert werden. Das Skript nutzt das Cmdlet `Get-ADALToken` aus dem ADAL.PS-Modul, das Sie zuvor bei der „Einrichtung und Konfiguration des MIP SDKs“ installiert haben.

1. Erstellen Sie eine PowerShell-Skriptdatei (mit der Erweiterung „.ps1“), und fügen Sie das folgende Skript in die Datei ein:

   - Die Variablen `$authority` und `$resourceUrl` werden später im nachfolgenden Abschnitt aktualisiert.
   - Aktualisieren Sie `$appId` und `$redirectUri`, sodass diese den Werten entsprechen, die in Ihrer Azure AD-Anwendungsregistrierung angegeben wurden.

   ```powershell
   $authority = '<authority-url>'                   # Specified when SDK calls AcquireOAuth2Token()
   $resourceUrl = '<resource-url>'                  # Specified when SDK calls AcquireOAuth2Token()
   $appId = '0edbblll-8773-44de-b87c-b8c6276d41eb'  # App ID of the Azure AD app registration
   $redirectUri = 'bltest://authorize'              # Redirect URI of the Azure AD app registration
   $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession
   $response.AccessToken | clip                     # Copy the access token text to the clipboard
   ```

2. Speichern Sie die Skriptdatei, damit Sie sie später ausführen können, wenn die Clientanwendung Sie dazu auffordert.

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Letztendlich erstellen und testen Sie die Clientanwendung.

1. Verwenden Sie F6 (**Projektmappe erstellen**) zum Erstellen der Clientanwendung. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, fragt die Anwendung jedes Mal nach einem Zugriffstoken, wenn das SDK Ihre `AcquireOAuth2Token()`-Methode aufruft. Sie können ein zuvor generiertes Token erneut verwenden, wenn Sie mehrmals dazu aufgefordert werden und die Werte gleich sind.

3. Sie können ein Zugriffstoken für die Aufforderung erstellen, indem Sie wieder zu Ihrem PowerShell-Skript wechseln und Folgendes durchführen:

   - Aktualisieren Sie die Variablen `$authority` und `$resourceUrl`. Sie müssen den Werten entsprechen, die in der Konsolenausgabe von Schritt 2 angegeben wurden. Diese Werte werden von dem MIP SDK im `challenge`-Parameter von `AcquireOAuth2Token()` bereitgestellt:
   - Führen Sie das PowerShell-Skript aus. Das Cmdlet `Get-ADALToken` löst eine Eingabeaufforderung für die Azure AD-Authentifizierung ähnlich dem folgenden Beispiel aus. Geben Sie das gleiche Konto an, das in der Konsolenausgabe von Schritt 2 angegeben wurde. Nachdem Sie sich erfolgreich angemeldet haben, wird das Zugriffstoken in der Zwischenablage gespeichert.

     [![Anmeldung in Visual Studio zum Erhalten des Tokens](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Möglicherweise müssen Sie Ihre Zustimmung erteilen, um der Anwendung den Zugriff auf die MIP-APIs zu gewähren, während die Ausführung unter dem Anmeldekonto erfolgt. Dies geschieht, wenn der Azure AD-Anwendungsregistrierung nicht (wie in der Einrichtung und Konfiguration des MIP SDKs beschrieben) vorab zugestimmt wurde, oder wenn Sie sich mit einem Konto von einem anderen Mandanten anmelden (der sich von dem unterscheidet, bei dem Ihre Anwendung registriert ist). Klicken Sie einfach auf **Akzeptieren**, damit Ihre Einwilligung erfasst wird.

     [![Visual Studio-Einwilligung](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

4. Nachdem die Zugriffstoken in die Eingabeaufforderung aus Schritt 2 eingefügt wurden, sollten die Vertraulichkeitsbezeichnungen in der Konsolenausgabe ähnlich dem folgenden Beispiel angezeigt werden:

   ```console
   Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
   Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
   General : f42a3342-8706-4288-bd31-ebb85995028z
   Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
   Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z

   Press any key to continue . . .
   ```

   > [!NOTE]
   > Kopieren und speichern Sie die ID von mindestens einer Vertraulichkeitsbezeichnung (z.B. `f42a3342-8706-4288-bd31-ebb85995028z`), da Sie diese im nächsten Schnellstart benötigen.

## <a name="troubleshooting"></a>Problembehandlung
### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C++-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Ungültiges Zugriffstoken | *An exception occurred... is the access token incorrect/expired?<br> (Ein Fehler ist aufgetreten. Das Zugriffstoken ist möglicherweise falsch oder abgelaufen.)<br>Failed API call: profile_add_engine_async Failed with: [class mip::PolicySyncException] Failed acquiring policy, Request failed with http status code: 401, x-ms-diagnostics: [2000001;reason="OAuth token submitted with the request cannot be parsed.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672]'<br> (Fehlerhafter API-Aufruf: profile_add_engine_async Fehler: [class mip::PolicySyncException] Fehler beim Abrufen der Richtlinie, Anforderung fehlgeschlagen – HTTP-Statuscode: 401, x-ms-diagnostics: [2000001;reason="Das mit der Anforderung übermittelte OAuth-Token kann nicht analysiert werden.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672])<br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (process 29924) exited with code 0.<br> (Die Ausführung von „C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe“ (Prozess 29924) wurde mit dem Code 0 beendet.)<br>Press any key to close this window . . .* (Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen.) | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, enthält Ihre `AcquireOAuth2Token()`-Methode wahrscheinlich ein ungültiges oder abgelaufenes Token. Wechseln Sie wieder zu [Erstellen eines PowerShell-Skripts zum Generieren von Zugriffstoken](#create-a-powershell-script-to-generate-access-tokens), generieren Sie das Zugriffstoken neu, aktualisieren Sie `AcquireOAuth2Token()` erneut, und führen Sie die Erstellung und die Tests erneut durch. Sie können das Token und dessen Ansprüche auch untersuchen und überprüfen, indem Sie die einseitige Webanwendung [jwt.ms](https://jwt.ms/) verwenden. |
| Vertraulichkeitsbezeichnungen sind nicht konfiguriert | Nicht zutreffend | Wenn Ihr Projekt erfolgreich erstellt wird, Sie aber keine Ausgabe im Konsolenfenster erhalten, stellen Sie sicher, dass die Vertraulichkeitsbezeichnungen Ihrer Organisation ordnungsgemäß konfiguriert sind. Ausführliche Informationen finden Sie unter „Definieren des Bezeichnungsschemas und der Schutzeinstellungen“ im Artikel zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md).  |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie die Vertraulichkeitsbezeichnungen für Ihre Organisation aufführen, können Sie nun mit dem nächsten Schnellstart fortfahren:

> [!div class="nextstepaction"]
> [Set and get a sensitivity label (Festlegen und Abrufen einer Vertraulichkeitsbezeichnung)](quick-file-set-get-label-cpp.md)
