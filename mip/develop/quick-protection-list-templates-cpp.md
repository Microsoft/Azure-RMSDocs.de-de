---
title: 'Schnellstart: Auflisten der verfügbaren Schutzvorlagen für einen authentifizierten Benutzer in einem Microsoft Information Protection-Mandanten (MIP) mit dem MIP SDK für C++'
description: Dieser Schnellstart zeigt die Verwendung der Schutz-API im Microsoft Information Protection SDK für C++, um die für einen Benutzer verfügbaren Schutzvorlagen aufzulisten (C++).
author: Pathak-Aniket
ms.service: information-protection
ms.topic: quickstart
ms.date: 01/18/2019
ms.author: v-anikep
ms.custom: has-adal-ref
ms.openlocfilehash: d319af8e65e2eae958ef215d30dfa84c09ae7145
ms.sourcegitcommit: 437057990372948c9435b620052a7398360264b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2020
ms.locfileid: "97701644"
---
# <a name="quickstart-list-protection-templates-c"></a>Schnellstart: Auflisten von Schutzvorlagen (C++)

Dieser Schnellstart zeigt, wie Sie die MIP-Schutz-API verwenden, um die für einen Benutzer verfügbaren Schutzvorlagen aufzulisten.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zunächst den [Schnellstart: Initialisierung der Clientanwendung für Schutz-APIs (C++)](quick-protection-app-initialization-cpp.md) ab, in dem Sie eine Visual Studio-Startprojektmappe erstellen. Der vorliegende Schnellstart zum Auflisten von Schutzvorlagen basiert darauf, dass zuvor eine Startprojektmappe erstellt wurde.
- Optional: Sehen Sie sich die Konzepte in [RMS-Vorlagen](/azure/information-protection/configure-policy-templates) an.

## <a name="add-logic-to-list-the-protection-templates"></a>Hinzufügen von Logik zum Auflisten der Schutzvorlagen

Fügen Sie Logik zum Auflisten der für einen Benutzer verfügbaren Schutzvorlagen hinzu, indem Sie das Schutz-Engine-Objekt verwenden.

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen „Schnellstart: Initialisierung der Clientanwendung für Schutz-APIs (C++)“ erstellt haben.

2. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CPP-Datei im Projekt, die die Implementierung der `main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Fügen Sie Folgendes der `using`-Anweisung nach `using mip::ProtectionEngine;` oben in der Datei hinzu:

   ```cpp
   using std::endl;
   ```

4. Fügen Sie den folgenden Code gegen Ende des `main()`-Texts zwischen der schließenden Klammer `}` des letzten `catch`-Blocks und über `return 0;` (wo Sie im vorherigen Schnellstart aufgehört haben) ein:

   ```cpp
    // List protection templates
    const shared_ptr<ProtectionEngineObserver> engineObserver = std::make_shared<ProtectionEngineObserver>();
    // Create a context to pass to 'ProtectionEngine::GetTemplateListAsync'. That context will be forwarded to the
    // corresponding ProtectionEngine::Observer methods. In this case, we use promises/futures as a simple way to detect
    // the async operation completes synchronously.
    auto loadPromise = std::make_shared<std::promise<vector<shared_ptr<mip::TemplateDescriptor>>>>();
    std::future<vector<shared_ptr<mip::TemplateDescriptor>>> loadFuture = loadPromise->get_future();
    engine->GetTemplatesAsync(engineObserver, loadPromise);
    auto templates = loadFuture.get();

    cout << "**_ Template List: " << endl;

    for (const auto& protectionTemplate : templates) {
        cout << "Name: " << protectionTemplate->GetName() << " : " << protectionTemplate->GetId() << endl;
    }

   ```

## <a name="create-a-powershell-script-to-generate-access-tokens"></a>Erstellen eines PowerShell-Skripts zum Generieren von Zugriffstoken

Verwenden Sie das folgende PowerShell-Skript, um die Zugriffstoken zu generieren, die vom SDK in Ihrer `AuthDelegateImpl::AcquireOAuth2Token`-Implementierung gefordert werden. Das Skript nutzt das Cmdlet `Get-ADALToken` aus dem ADAL.PS-Modul, das Sie zuvor bei der „Einrichtung und Konfiguration des MIP SDKs“ installiert haben.

1. Erstellen Sie eine PowerShell-Skriptdatei (mit der Erweiterung „.ps1“), und fügen Sie das folgende Skript in die Datei ein:

   - Die Variablen `$authority` und `$resourceUrl` werden später im nachfolgenden Abschnitt aktualisiert.
   - Aktualisieren Sie `$appId` und `$redirectUri`, sodass diese den Werten entsprechen, die in Ihrer Azure AD-Anwendungsregistrierung angegeben wurden.

   ```powershell
   $authority = '<authority-url>'                   # Specified when SDK calls AcquireOAuth2Token()
   $resourceUrl = '<resource-url>'                  # Specified when SDK calls AcquireOAuth2Token()
   $appId = '<app-ID>'                              # App ID of the Azure AD app registration
   $redirectUri = '<redirect-uri>'                  # Redirect URI of the Azure AD app registration
   $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession
   $response.AccessToken | clip                     # Copy the access token text to the clipboard
   ```

2. Speichern Sie die Skriptdatei, damit Sie sie später ausführen können, wenn die Clientanwendung Sie dazu auffordert.

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Letztendlich erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B (_*Projektmappe erstellen **), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, drücken Sie F5 (** Debuggen starten**), um Ihre Anwendung auszuführen.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, fragt die Anwendung jedes Mal nach einem Zugriffstoken, wenn das SDK Ihre `AcquireOAuth2Token()`-Methode aufruft. Sie können ein zuvor generiertes Token erneut verwenden, wenn Sie mehrmals dazu aufgefordert werden und die Werte gleich sind:

3. Sie können ein Zugriffstoken für die Aufforderung erstellen, indem Sie wieder zu Ihrem PowerShell-Skript wechseln und Folgendes durchführen:

   - Aktualisieren Sie die Variablen `$authority` und `$resourceUrl`. Sie müssen den Werten entsprechen, die in der Konsolenausgabe von Schritt 2 angegeben wurden.
   - Führen Sie das PowerShell-Skript aus. Das Cmdlet `Get-ADALToken` löst eine Eingabeaufforderung für die Azure AD-Authentifizierung ähnlich dem folgenden Beispiel aus. Geben Sie das gleiche Konto an, das in der Konsolenausgabe von Schritt 2 angegeben wurde. Nachdem Sie sich erfolgreich angemeldet haben, wird das Zugriffstoken in der Zwischenablage gespeichert.

     [![Anmeldung in Visual Studio zum Erhalten des Tokens](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Möglicherweise müssen Sie Ihre Zustimmung erteilen, um der Anwendung den Zugriff auf die MIP-APIs zu gewähren, während die Ausführung unter dem Anmeldekonto erfolgt. Dies geschieht, wenn der Azure AD-Anwendungsregistrierung nicht (wie in der Einrichtung und Konfiguration des MIP SDKs beschrieben) vorab zugestimmt wurde, oder wenn Sie sich mit einem Konto von einem anderen Mandanten anmelden (der sich von dem unterscheidet, bei dem Ihre Anwendung registriert ist). Klicken Sie einfach auf **Akzeptieren**, damit Ihre Einwilligung erfasst wird.

     [![Visual Studio-Einwilligung](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

4. Nachdem das Zugriffstoken in die Eingabeaufforderung aus Schritt 2 eingefügt wurden, sollten in der Konsolenausgabe die Schutzvorlagen für den authentifizierten Benutzer angezeigt werden, ähnlich wie im folgenden Beispiel:

   ```console
   **_ Template List:
   Name: Confidential \ All Employees : a74f5027-f3e3-4c55-abcd-74c2ee41b607
   Name: Highly Confidential \ All Employees : bb7ed207-046a-4caf-9826-647cff56b990
   Name: Confidential : 174bc02a-6e22-4cf2-9309-cb3d47142b05
   Name: Contoso Employees Only : 667466bf-a01b-4b0a-8bbf-a79a3d96f720

   C:\MIP Sample Apps\ProtectionQS\Debug\ProtectionQS.exe (process 8252) exited with code 0.
   To automatically close the console when debugging stops, enable Tools->Options->Debugging->Automatically close the console when debugging stops.

   Press any key to continue . . .
   ```

   > [!NOTE]
   > Kopieren und speichern Sie die ID von mindestens einer Schutzvorlage (z. B. `f42a3342-8706-4288-bd31-ebb85995028z`), da Sie diese im nächsten Schnellstart benötigen.

## <a name="troubleshooting"></a>Problembehandlung
### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C++-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Ungültiges Zugriffstoken | _Eine Ausnahme ist aufgetreten... ist das Zugriffstoken falsch/abgelaufen?<br><br>Fehlerhafter API-Aufruf: profile_add_engine_async Fehler bei: [class mip::PolicySyncException] Fehler bei Abrufen der Richtlinie, Fehler bei Anforderung mit HTTP-Statuscode: 401, x-ms-diagnostics: [2000001;reason="Mit der Anforderung übermitteltes OAuth-Token kann nicht analysiert werden.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672]'<br><br>„C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe“ (Prozess 29924) wurde mit Code 0 beendet.<br><br>Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen. . .* | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, enthält Ihre `AcquireOAuth2Token()`-Methode wahrscheinlich ein ungültiges oder abgelaufenes Token. Wechseln Sie wieder zu [Erstellen eines PowerShell-Skripts zum Generieren von Zugriffstoken](#create-a-powershell-script-to-generate-access-tokens), generieren Sie das Zugriffstoken neu, aktualisieren Sie `AcquireOAuth2Token()` erneut, und führen Sie die Erstellung und die Tests erneut durch. Sie können das Token und dessen Ansprüche auch untersuchen und überprüfen, indem Sie die einseitige Webanwendung [jwt.ms](https://jwt.ms/) verwenden. |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun erfahren haben, wie Sie die für einen authentifizierten Benutzer verfügbaren Schutzvorlagen auflisten können, bearbeiten Sie den nächsten Schnellstart:

> [!div class="nextstepaction"]
> [Verschlüsseln und Entschlüsseln von Text](quick-protection-encrypt-decrypt text-cpp.md)