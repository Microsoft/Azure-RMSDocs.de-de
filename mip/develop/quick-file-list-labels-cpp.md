---
title: 'Schnellstart: Auflisten der Vertraulichkeitsbezeichnungen in einem MIP-Mandanten (Microsoft Information Protection) mithilfe des C++-MIP SDKs'
description: In diesen Schnellstart wird veranschaulicht, wie Sie das Microsoft Information Protection SDK mit C++ nutzen, um die Vertraulichkeitsbezeichnungen in Ihrem Mandanten aufzulisten.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.date: 01/18/2019
ms.author: bryanla
ms.openlocfilehash: 53ff9177bd17a87b64db3ec507e87236c9b12507
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257796"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C++)

In diesem Schnellstart erfahren Sie, wie Sie die MIP-File-API verwenden, um die für Ihre Organisation konfigurierten Vertraulichkeitsbezeichnungen aufzulisten.

## <a name="prerequisites"></a>Vorraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Vollständige [Schnellstart: Client-Anwendung-Initialisierung (C++)](quick-app-initialization-cpp.md) erste, die eine Starter-Visual Studio-Projektmappe erstellt. Dieser Schnellstart zum „Auflisten der Vertraulichkeitsbezeichnungen“ baut auf der vorherigen Erstellung der Startprojektmappe auf.
- Optional: Überprüfen Sie [klassifizierungsbezeichnungen](concept-classification-labels.md) Konzepte.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Hinzufügen von Logik zur Liste der Vertraulichkeitsbezeichnungen

Im Folgenden fügen Sie der Liste von Vertraulichkeitsbezeichnungen Ihrer Organisation Logik mithilfe des FileEnginge-Objekts hinzu. 

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie erstellt, in der vorherigen haben "Schnellstart: Client-Anwendung-Initialisierung (C++) "Artikel.

2. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben. 

3. Fügen Sie Folgendes der `using`-Anweisung nach `using mip::FileEngine;` oben in der Datei hinzu:

   ```cpp
   using std::endl;
   ```

4. Gegen Ende der `main()` Text unterhalb der schließenden geschweiften Klammer `}` des letzten `catch` Block und höher `return 0;` (im vorherigen Schnellstart Stelle), fügen Sie den folgenden Code:

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

Verwenden Sie das folgende PowerShell-Skript zum Generieren von Zugriffstoken, die vom SDK in angefordert werden Ihre `AuthDelegateImpl::AcquireOAuth2Token` Implementierung. Das Skript nutzt das Cmdlet `Get-ADALToken` aus dem ADAL.PS-Modul, das Sie zuvor bei der „Einrichtung und Konfiguration des MIP SDKs“ installiert haben. 

1. Erstellen Sie eine PowerShell-Skriptdatei (mit der Erweiterung „.ps1“), und fügen Sie das folgende Skript in die Datei ein:

   - Die Variablen `$authority` und `$resourceUrl` werden später im nachfolgenden Abschnitt aktualisiert.
   - Update `$appId` und `$redirectUri`, um die Werte übereinstimmen, Sie in Ihrem Azure AD-app-Registrierung angegeben haben. 

   ```powershell
   $authority = '<authority-url>'                   # Specified when SDK calls AcquireOAuth2Token() 
   $resourceUrl = '<resource-url>'                  # Specified when SDK calls AcquireOAuth2Token()
   $appId = '0edbblll-8773-44de-b87c-b8c6276d41eb'  # App ID of the Azure AD app registration
   $redirectUri = 'bltest://authorize'              # Redirect URI of the Azure AD app registration
   $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession 
   $response.AccessToken | clip                     # Copy the access token text to the clipboard
   ```

2. Speichern Sie die Skriptdatei aus, damit Sie später ausgeführt werden kann, wenn von der Clientanwendung angefordert.

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Letztendlich erstellen und testen Sie die Clientanwendung. 

1. Verwenden Sie F6 (**Projektmappe erstellen**) zum Erstellen der Clientanwendung. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erstellt und ausgeführt wird, die Anwendung fordert ein Zugriffstoken, jedes Mal, wenn der SDK-Aufrufe Ihrer `AcquireOAuth2Token()` Methode. Sie können ein zuvor generiertes Token erneut verwenden, wenn Sie mehrmals dazu aufgefordert werden und die Werte gleich sind:

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token:
   ```

3. Um ein Zugriffstoken für die Aufforderung zu generieren, wechseln Sie zurück zum PowerShell-Skript und:

   - Aktualisieren Sie die Variablen `$authority` und `$resourceUrl`. Sie müssen den Werten entsprechen, die in der Konsolenausgabe von Schritt 2 angegeben wurden. Diese Werte werden von dem MIP SDK im `challenge`-Parameter von `AcquireOAuth2Token()` bereitgestellt:
     - `$authority` sollte `https://login.windows.net/common/oauth2/authorize` entsprechen
     - `$resourceUrl` sollte `https://syncservice.o365syncservice.com/` oder `https://aadrm.com` entsprechen
   - Führen Sie das PowerShell-Skript aus. Die `Get-ADALToken` Cmdlet wird eine authentifizierungsaufforderung von Azure AD, ähnlich wie im folgenden Beispiel ausgelöst. Geben Sie das gleiche Konto an, das in der Konsolenausgabe von Schritt 2 angegeben wurde. Nachdem Sie sich erfolgreich angemeldet haben, wird das Zugriffstoken in der Zwischenablage gespeichert.

     [![Anmeldung in Visual Studio zum Erhalten des Tokens](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Möglicherweise müssen Sie Ihre Zustimmung erteilen, um der Anwendung den Zugriff auf die MIP-APIs zu gewähren, während die Ausführung unter dem Anmeldekonto erfolgt. Dies geschieht, wenn der Azure AD-Anwendungsregistrierung nicht (wie in der Einrichtung und Konfiguration des MIP SDKs beschrieben) vorab zugestimmt wurde, oder wenn Sie sich mit einem Konto von einem anderen Mandanten anmelden (der sich von dem unterscheidet, bei dem Ihre Anwendung registriert ist). Klicken Sie einfach auf **Akzeptieren**, damit Ihre Einwilligung erfasst wird.

     [![Visual Studio-Einwilligung](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

4. Nach dem Einfügen des Zugriffstokens in der Eingabeaufforderung aus Schritt #2, sollte die vertraulichkeitsbezeichnungen, ähnlich wie im folgenden Beispiel von der Konsolenausgabe angezeigt werden:

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
| Falscher Umleitungs-URI in der Anwendungsregistrierung oder im PowerShell-Skript (AADSTS50011) |*AADSTS50011: Die Antwort in der Anforderung angegebene Url entspricht nicht der Antwort-Urls, die für die Anwendung konfiguriert: "ac6348d6-0d2f-4786-af33-07ad46e69bfc".* | Überprüfen Sie den verwendeten Umleitungs-URI, indem Sie einen der folgenden Schritte ausführen:<br><br><li>Aktualisieren Sie den Umleitungs-URI in der Azure AD-Anwendungskonfiguration, sodass er mit Ihrem PowerShell-Skript übereinstimmt. Überprüfen Sie anhand des Artikels zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md#register-a-client-application-with-azure-active-directory), ob Sie den Umleitungs-URI ordnungsgemäß konfiguriert haben.<br><li>Aktualisieren Sie die `redirectUri`-Variable in Ihrem PowerShell-Skript entsprechend Ihrer Anwendungsregistrierung. |
| Falsches Anmeldekonto (AADSTS50020) | *AADSTS50020: Benutzerkonto "user@domain.com"vom Identitätsanbieter"https://sts.windows.net/72f988bl-86f1-41af-91ab-2d7cd011db47/" im Mandanten "Name der Organisation" nicht vorhanden und kann nicht auf die Anwendung "0edbblll-8773-44de-b87c-b8c6276d41eb" in diesem Mandanten zugreifen.* | Führen Sie einen der folgenden Schritte aus:<br><br><li>Führen Sie das PowerShell-Skript erneut aus, aber achten Sie darauf, ein Konto vom gleichen Mandanten zu verwenden, bei dem Ihre Azure AD-Anwendung registriert ist.<br><li>Wenn Ihr Anmeldekonto richtig war, ist Ihre PowerShell-Hostsitzung möglicherweise unter einem anderen Konto authentifiziert. Beenden Sie in diesem Fall den Skripthost, und öffnen Sie ihn erneut. Versuchen Sie dann erneut, das Skript auszuführen.<br><li>Wenn Sie diesen Schnellstart mit einer Web-App (anstelle einer nativen App) durchführen und sich mit einem Konto von einem anderen Mandanten anmelden müssen, stellen Sie sicher, dass Ihre Azure AD-Anwendungsregistrierung für die Verwendung mehrerer Mandanten aktiviert ist. Dies können Sie überprüfen, indem Sie das Feature „Manifest bearbeiten“ in der Anwendungsregistrierung verwenden und sicherstellen, dass `"availableToOtherTenants": true,` angegeben wird. |
| Falsche Berechtigungen in der Anwendungsregistrierung (AADSTS65005) | *AADSTS65005: Ungültige Ressource. The client has requested access to a resource, which is not listed in the requested permissions in the client's application registration. Client-app-ID: 0edbblll-8773-44de-b87c-b8c6276d41eb. Resource value from request: https://syncservice.o365syncservice.com/. Ressourcen-app-ID: 870c4f2e-85b6-4d43-bdda-6ed9a579b725. Liste von gültigen Ressourcen aus dem app-Registrierung: 00000002-0000-0000-c000-000000000000.* | Aktualisieren Sie die Berechtigungsanforderungen in der Azure AD-Anwendungskonfiguration. Überprüfen Sie anhand des Artikels zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md#register-a-client-application-with-azure-active-directory), ob Sie die Berechtigungsanforderungen in Ihrer Anwendungsregistrierung ordnungsgemäß konfiguriert haben. |

### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C++-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Ungültiges Zugriffstoken | *... Ist eine Ausnahme aufgetreten ist das Zugriffstoken falsche/abgelaufen? <br> <br>Fehler bei API-Aufruf: Fehler bei der Profile_add_engine_async: [Klasse mip::PolicySyncException] Fehler beim Abrufen der Richtlinie, Fehler bei Anforderung mit http-Statuscode: 401, X-ms-Diagnostics: [2000001; Reason = "OAuth-Token, die mit der Anforderung übermittelte kann nicht analysiert werden."; Error_category = "Invalid_token"], CorrelationId: [35bc0023-3727-4eff-8062-000006d5d672]'<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (Process 29924) wurde beendet mit Code 0.<br> <br>Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen...* | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, enthält Ihre `AcquireOAuth2Token()`-Methode wahrscheinlich ein ungültiges oder abgelaufenes Token. Navigieren Sie zurück zum [Aktualisieren der Logik zum Abrufen des Tokens](#update-the-token-acquisition-logic-with-a-valid-access-token), stellen Sie das Zugriffstoken wieder her, aktualisieren Sie `AcquireOAuth2Token()` erneut, und führen Sie die Tests und die Erstellung erneut durch. Sie können das Token und dessen Ansprüche auch untersuchen und überprüfen, indem Sie die einseitige Webanwendung [jwt.ms](https://jwt.ms/) verwenden. |
| Vertraulichkeitsbezeichnungen sind nicht konfiguriert | Nicht zutreffend | Wenn Ihr Projekt erfolgreich erstellt wird, Sie aber keine Ausgabe im Konsolenfenster erhalten, stellen Sie sicher, dass die Vertraulichkeitsbezeichnungen Ihrer Organisation ordnungsgemäß konfiguriert sind. Ausführliche Informationen finden Sie unter „Definieren des Bezeichnungsschemas und der Schutzeinstellungen“ im Artikel zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md).  |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie die Vertraulichkeitsbezeichnungen für Ihre Organisation aufführen, können Sie nun mit dem nächsten Schnellstart fortfahren:

> [!div class="nextstepaction"]
> [Set and get a sensitivity label (Festlegen und Abrufen einer Vertraulichkeitsbezeichnung)](quick-file-set-get-label-cpp.md)
