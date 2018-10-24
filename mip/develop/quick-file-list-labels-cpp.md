---
title: 'Schnellstart: Auflisten der Vertraulichkeitsbezeichnungen in einem MIP-Mandanten (Microsoft Information Protection) mithilfe des C++-MIP SDKs'
description: In diesen Schnellstart wird veranschaulicht, wie Sie das Microsoft Information Protection SDK mit C++ nutzen, um die Vertraulichkeitsbezeichnungen in Ihrem Mandanten aufzulisten.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fc8d4b43bae9a7b74edef10947ef5aa22e5d1267
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251776"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Schnellstart: Auflisten der Vertraulichkeitsbezeichnungen (C++)

In diesem Schnellstart erfahren Sie, wie Sie die MIP-File-API verwenden, um die für Ihre Organisation konfigurierten Vertraulichkeitsbezeichnungen aufzulisten.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zunächst den [Schnellstart für die Initialisierung der Clientanwendung (C++)](quick-app-initialization-cpp.md) ab, in dem Sie eine Visual Studio-Startprojektmappe erstellen. Dieser Schnellstart zum „Auflisten der Vertraulichkeitsbezeichnungen“ baut auf der vorherigen Erstellung der Startprojektmappe auf.
- Optional können Sie sich zusätzlich die Konzepte zu [Klassifizierungsbezeichnungen](concept-classification-labels.md) ansehen.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Hinzufügen von Logik zur Liste der Vertraulichkeitsbezeichnungen

Im Folgenden fügen Sie der Liste von Vertraulichkeitsbezeichnungen Ihrer Organisation Logik mithilfe des FileEnginge-Objekts hinzu. 

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Schnellstart (Initialisierung der Clientanwendung (C++)) erstellt haben.

2. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben. 

3. Fügen Sie Folgendes der `using`-Anweisung nach `using mip::FileEngine;` oben in der Datei hinzu:

   ```cpp
   using std::endl;
   ```

4. Fügen Sie den folgenden Code gegen Ende des `main()`-Texts zwischen der schließenden Klammer `}` des `catch`-Blocks und `return 0;` (wo Sie im vorherigen Schnellstart aufgehört haben) ein:

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

Verwenden Sie das folgende PowerShell-Skript, um Zugriffstoken gemäß der Anforderungen des SDKs zu generieren. Das Skript nutzt das Cmdlet `Get-ADALToken` aus dem ADAL.PS-Modul, das Sie zuvor bei der „Einrichtung und Konfiguration des MIP SDKs“ installiert haben. 

1. Erstellen Sie eine PowerShell-Skriptdatei (mit der Erweiterung „.ps1“), und fügen Sie das folgende Skript in die Datei ein:

   - Aktualisieren Sie die Variablen `$appId` und `$redirectUri`, sodass Sie den Werten entsprechen, die in Ihrer Azure AD-Anwendungsregistrierung angegeben werden. 
   - Die Variablen `$authority` und `$resourceUrl` werden später im nachfolgenden Abschnitt aktualisiert.

   ```powershell
   $authority = '<authority-url>'                   # Enforced by MIP SDK
   $resourceUrl = '<resource-url>'                  # Enforced by MIP SDK; matches a resource/API URL requested in the app registration
   $appId = '0edbblll-8773-44de-b87c-b8c6276d41eb'  # App ID of the Azure AD app registration
   $redirectUri = 'bltest://authorize'              # Must match the redirect URI of the Azure AD app registration
   $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession 
   $response.AccessToken | clip                     # Copy the access token text to the clipboard
   ```

2. Speichern Sie die Skriptdatei, damit Sie sie später gemäß Ihrer Clientanwendung ausführen können.

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Letztendlich erstellen und testen Sie die Clientanwendung. 

1. Verwenden Sie F6 (**Projektmappe erstellen**) zum Erstellen der Clientanwendung. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, fragt die Anwendung jedes Mal nach einem Zugriffstoken, wenn das SDK Ihre `AcquireOAuth2Token()`-Methode aufruft. Sie können ein zuvor generiertes Token erneut verwenden, wenn Sie mehrmals dazu aufgefordert werden und die Werte gleich sind:

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Be sure to sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token:
   ```

3. Um eine Antwort für die obige Eingabeaufforderung anzugeben, navigieren Sie zurück zu Ihrem PowerShell-Skript, und führen Sie die folgenden Anweisungen aus:

   - Aktualisieren Sie die Variablen `$authority` und `$resourceUrl`. Sie müssen den Werten entsprechen, die in der Konsolenausgabe von Schritt 2 angegeben wurden. Diese Werte werden von dem MIP SDK im `challenge`-Parameter von `AcquireOAuth2Token()` bereitgestellt:
     - `$authority` sollte `https://login.windows.net/common/oauth2/authorize` entsprechen
     - `$resourceUrl` sollte `https://syncservice.o365syncservice.com/` oder `https://aadrm.com` entsprechen
   - Führen Sie das PowerShell-Skript aus. Das Cmdlet `Get-ADALToken` löst eine Eingabeaufforderung für die Azure AD-Authentifizierung ähnlich dem folgenden Beispiel aus. Geben Sie das gleiche Konto an, das in der Konsolenausgabe von Schritt 2 angegeben wurde. Nachdem Sie sich erfolgreich angemeldet haben, wird das Zugriffstoken in der Zwischenablage gespeichert.

     [![Anmeldung in Visual Studio zum Erhalten des Tokens](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Möglicherweise müssen Sie Ihre Zustimmung erteilen, um der Anwendung den Zugriff auf die MIP-APIs zu gewähren, während die Ausführung unter dem Anmeldekonto erfolgt. Dies geschieht, wenn der Azure AD-Anwendungsregistrierung nicht (wie in der Einrichtung und Konfiguration des MIP SDKs beschrieben) vorab zugestimmt wurde, oder wenn Sie sich mit einem Konto von einem anderen Mandanten anmelden (der sich von dem unterscheidet, bei dem Ihre Anwendung registriert ist). Klicken Sie einfach auf **Akzeptieren**, damit Ihre Einwilligung erfasst wird.

     [![Visual Studio-Einwilligung](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

4. Nachdem die Zugriffstoken bereitgestellt wurden, sollten die Vertraulichkeitsbezeichnungen in der Konsolenausgabe ähnlich dem folgenden Beispiel angezeigt werden:

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

### <a name="problems-during-execution-of-powershell-script"></a>Probleme bei der Ausführung des PowerShell-Skripts 

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Falscher Umleitungs-URI in der Anwendungsregistrierung oder im PowerShell-Skript (AADSTS50011) |*AADSTS50011: The reply url specified in the request does not match the reply urls configured for the application: 'ac6348d6-0d2f-4786-af33-07ad46e69bfc'. (AADSTS50011: Die in der Anforderung angegebene Antwort-URL entspricht nicht den für die Anwendung konfigurierten Antwort-URLs: „ac6348d6-0d2f-4786-af33-07ad46e69bfc“.)* | Überprüfen Sie den verwendeten Umleitungs-URI, indem Sie einen der folgenden Schritte ausführen:<br><br><li>Aktualisieren Sie den Umleitungs-URI in der Azure AD-Anwendungskonfiguration, sodass er mit Ihrem PowerShell-Skript übereinstimmt. Überprüfen Sie anhand des Artikels zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md#register-a-client-application-with-azure-active-directory), ob Sie den Umleitungs-URI ordnungsgemäß konfiguriert haben.<br><li>Aktualisieren Sie die `redirectUri`-Variable in Ihrem PowerShell-Skript entsprechend Ihrer Anwendungsregistrierung. |
| Falsches Anmeldekonto (AADSTS50020) | *AADSTS50020: User account 'user@domain.com' from identity provider 'https://sts.windows.net/72f988bl-86f1-41af-91ab-2d7cd011db47/' does not exist in tenant 'Organization name' and cannot access the application '0edbblll-8773-44de-b87c-b8c6276d41eb' in that tenant. (Das Benutzerkonto „user@domain.com“ vom Identitätsanbieter „https://sts.windows.net/72f988bl-86f1-41af-91ab-2d7cd011db47/“ ist im Mandanten „Name der Organisation“ nicht vorhanden und kann in diesem Mandanten nicht auf die Anwendung „0edbblll-8773-44de-b87c-b8c6276d41eb“ zugreifen.)* | Führen Sie einen der folgenden Schritte aus:<br><br><li>Führen Sie das PowerShell-Skript erneut aus, aber achten Sie darauf, ein Konto vom gleichen Mandanten zu verwenden, bei dem Ihre Azure AD-Anwendung registriert ist.<br><li>Wenn Ihr Anmeldekonto richtig war, ist Ihre PowerShell-Hostsitzung möglicherweise unter einem anderen Konto authentifiziert. Beenden Sie in diesem Fall den Skripthost, und öffnen Sie ihn erneut. Versuchen Sie dann erneut, das Skript auszuführen.<br><li>Wenn Sie diesen Schnellstart mit einer Web-App (anstelle einer nativen App) durchführen und sich mit einem Konto von einem anderen Mandanten anmelden müssen, stellen Sie sicher, dass Ihre Azure AD-Anwendungsregistrierung für die Verwendung mehrerer Mandanten aktiviert ist. Dies können Sie überprüfen, indem Sie das Feature „Manifest bearbeiten“ in der Anwendungsregistrierung verwenden und sicherstellen, dass `"availableToOtherTenants": true,` angegeben wird. |
| Falsche Berechtigungen in der Anwendungsregistrierung (AADSTS65005) | *AADSTS65005: Invalid resource. The client has requested access to a resource, which is not listed in the requested permissions in the client's application registration. Client app ID: 0edbblll-8773-44de-b87c-b8c6276d41eb. Resource value from request: https://syncservice.o365syncservice.com/. Resource app ID: 870c4f2e-85b6-4d43-bdda-6ed9a579b725. List of valid resources from app registration: 00000002-0000-0000-c000-000000000000. (Ungültige Ressource. Der Client hat den Zugriff auf eine Ressource angefordert, die in den angeforderten Berechtigungen in der Anwendungsregistrierung des Clients nicht aufgeführt ist. Client-App-ID: „0edbblll-8773-44de-b87c-b8c6276d41eb“. Liste der gültigen Ressourcen aus der Anwendungsregistrierung: „00000002-0000-0000-c000-000000000000“.)* | Aktualisieren Sie die Berechtigungsanforderungen in der Azure AD-Anwendungskonfiguration. Überprüfen Sie anhand des Artikels zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md#register-a-client-application-with-azure-active-directory), ob Sie die Berechtigungsanforderungen in Ihrer Anwendungsregistrierung ordnungsgemäß konfiguriert haben. |

### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C++-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Ungültiges Zugriffstoken | *An exception occurred... is the access token incorrect/expired?<br><br>Failed API call: profile_add_engine_async Failed with: [class mip::PolicySyncException] Failed acquiring policy, Request failed with http status code: 401, x-ms-diagnostics: [2000001;reason="OAuth token submitted with the request cannot be parsed.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672]'<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (process 29924) exited with code 0.<br><br>Press any key to close this window . . .

(Eine Ausnahme ist aufgetreten... ist das Zugriffstoken fehlerhaft/abgelaufen?

Fehlgeschlagener API-Aufruf: profile_add_engine_async Fehler bei: [class mip::PolicySyncException] Abrufen der Richtlinie fehlgeschlagen, Anforderung fehlgeschlagen mit HTTP-Statuscode: 401, x-ms-diagnostics: [2000001;reason=„Mit der Anforderung übermitteltes OAuth-Token kann nicht analysiert werden.“;error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672]'

C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (Prozess 29924) wurde mit Code 0 beendet.

Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen . . .)* | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, enthält Ihre `AcquireOAuth2Token()`-Methode wahrscheinlich ein ungültiges oder abgelaufenes Token. Navigieren Sie zurück zum [Aktualisieren der Logik zum Abrufen des Tokens](#update-the-token-acquisition-logic-with-a-valid-access-token), stellen Sie das Zugriffstoken wieder her, aktualisieren Sie `AcquireOAuth2Token()` erneut, und führen Sie die Tests und die Erstellung erneut durch. Sie können das Token und dessen Ansprüche auch untersuchen und überprüfen, indem Sie die einseitige Webanwendung [jwt.ms](https://jwt.ms/) verwenden. |
| Vertraulichkeitsbezeichnungen sind nicht konfiguriert | Nicht zutreffend | Wenn Ihr Projekt erfolgreich erstellt wird, Sie aber keine Ausgabe im Konsolenfenster erhalten, stellen Sie sicher, dass die Vertraulichkeitsbezeichnungen Ihrer Organisation ordnungsgemäß konfiguriert sind. Ausführliche Informationen finden Sie unter „Definieren des Bezeichnungsschemas und der Schutzeinstellungen“ im Artikel zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md).  |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie die Vertraulichkeitsbezeichnungen für Ihre Organisation aufführen, können Sie nun mit dem nächsten Schnellstart fortfahren:

> [!div class="nextstepaction"]
> [Set and get a sensitivity label (Festlegen und Abrufen einer Vertraulichkeitsbezeichnung)](quick-file-set-get-label-cpp.md)
