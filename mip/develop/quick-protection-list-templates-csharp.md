---
title: 'Schnellstart: Auflisten der für einen authentifizierten Benutzer verfügbaren Schutzvorlagen in einem Microsoft Information Protection-Mandanten (MIP) mit dem Wrapper aus dem MIP SDK für C#'
description: Dieser Schnellstart zeigt die Verwendung des Wrappers der Schutz-API im Microsoft Information Protection SDK für C#, um die für einen Benutzer verfügbaren Schutzvorlagen aufzulisten (C#).
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.date: 03/30/2020
ms.author: mbaldwin
ms.custom: has-adal-ref
ms.openlocfilehash: 28de8cb2b14aef158707dc0b4dd7cb2e3f8a6947
ms.sourcegitcommit: 8e48016754e6bc6d051138b3e3e3e3edbff56ba5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865060"
---
# <a name="quickstart-list-templates-c"></a>Schnellstart: Auflisten von Vorlagen (C#)

Dieser Schnellstart zeigt, wie Sie die Schutz-API im MIP SDK verwenden, um die für einen Benutzer verfügbaren Schutzvorlagen aufzulisten.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Bearbeiten Sie zunächst den [Schnellstart Initialisierung der Clientanwendung – Schutz-API (C#)](quick-protection-app-initialization-csharp.md), in dem Sie eine Visual Studio-Startprojektmappe erstellen. Der vorliegende Schnellstart zum Auflisten von Schutzvorlagen basiert darauf, dass zuvor eine Startprojektmappe erstellt wurde.
- Optional: Sehen Sie sich die Konzepte in [RMS-Vorlagen](/azure/information-protection/configure-policy-templates) an.

## <a name="add-logic-to-list-the-protection-templates"></a>Hinzufügen von Logik zum Auflisten der Schutzvorlagen

Fügen Sie Logik zum Auflisten der für einen Benutzer verfügbaren Schutzvorlagen hinzu, indem Sie das Schutz-Engine-Objekt verwenden.

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Initialisierung der Clientanwendung – Schutz-API (C#)“ erstellt haben.

2. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CS-Datei im Projekt, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben.

3. Fügen Sie gegen Ende des `Main()`-Texts, oberhalb des Abschnitts zum Herunterfahren der Anwendung für die `Main()`-Funktion (an der Stelle, an der Sie im vorherigen Schnellstart aufgehört haben) den folgenden Code ein:

  ```csharp
  // List protection templates using protectionEngine and display the list

  var templates=protectionEngine.GetTemplates();

  for(int i = 0; i < templates.Count; i++)
  {
      Console.WriteLine("{0}: {1}", i.ToString(), templates[i].Name + " : " + templates[i].Id);
  }

  Console.WriteLine("Press a key to continue...");
  ```

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Letztendlich erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B (**Projektmappe erstellen**), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, *kann* die Anwendung Sie jedes Mal zur Authentifizierung über ADAL auffordern, wenn das SDK Ihre `AcquireToken()`-Methode aufruft. Wenn bereits zwischengespeicherte Anmeldeinformationen vorhanden sind, werden Sie nicht zur Anmeldung aufgefordert. Die Liste der Bezeichnungen wird sofort angezeigt.

     [![Anmeldung in Visual Studio zum Erhalten des Tokens](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Möglicherweise müssen Sie Ihre Zustimmung erteilen, um der Anwendung den Zugriff auf die MIP-APIs zu gewähren, während die Ausführung unter dem Anmeldekonto erfolgt. Dies geschieht, wenn der Azure AD-Anwendungsregistrierung nicht (wie in der Einrichtung und Konfiguration des MIP SDKs beschrieben) vorab zugestimmt wurde, oder wenn Sie sich mit einem Konto von einem anderen Mandanten anmelden (der sich von dem unterscheidet, bei dem Ihre Anwendung registriert ist). Klicken Sie einfach auf **Akzeptieren**, damit Ihre Einwilligung erfasst wird.

     [![Visual Studio-Einwilligung](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

3. Nach der Authentifizierung sollten in der Konsolenausgabe die Schutzvorlagen für den authentifizierten Benutzer angezeigt werden, ähnlich wie im folgenden Beispiel:

  ```console
  0: Confidential \ All Employees : a74f5027-f3e3-4c55-abcd-74c2ee41b607
  1: Highly Confidential \ All Employees : bb7ed207-046a-4caf-9826-647cff56b990
  2: Confidential : 174bc02a-6e22-4cf2-9309-cb3d47142b05
  3: Contoso Employees Only : 667466bf-a01b-4b0a-8bbf-a79a3d96f720
  Press a key to continue.
  ```

   > [!NOTE]
   > Kopieren und speichern Sie die ID von mindestens einer Schutzvorlage (z. B. `bb7ed207-046a-4caf-9826-647cff56b990`), da Sie diese im nächsten Schnellstart benötigen.

## <a name="troubleshooting"></a>Problembehandlung

### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C#-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Ungültiges Zugriffstoken | *An exception occurred... is the access token incorrect/expired?<br> (Ein Fehler ist aufgetreten. Das Zugriffstoken ist möglicherweise falsch oder abgelaufen.)<br>Failed API call: profile_add_engine_async Failed with: [class mip::PolicySyncException] Failed acquiring policy, Request failed with http status code: 401, x-ms-diagnostics: [2000001;reason="OAuth token submitted with the request cannot be parsed.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672]'<br> (Fehlerhafter API-Aufruf: profile_add_engine_async Fehler: [class mip::PolicySyncException] Fehler beim Abrufen der Richtlinie, Anforderung fehlgeschlagen – HTTP-Statuscode: 401, x-ms-diagnostics: [2000001;reason="Das mit der Anforderung übermittelte OAuth-Token kann nicht analysiert werden.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672])<br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (process 29924) exited with code 0.<br> (Die Ausführung von „C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe“ (Prozess 29924) wurde mit dem Code 0 beendet.)<br>Press any key to close this window . . .* (Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen.) | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, enthält Ihre `AcquireOAuth2Token()`-Methode wahrscheinlich ein ungültiges oder abgelaufenes Token. Navigieren Sie zurück zu [Erstellen und Testen der Anwendung](#build-and-test-the-application), stellen Sie das Zugriffstoken wieder her, aktualisieren Sie `AcquireOAuth2Token()` erneut, und führen Sie die Tests und die Erstellung erneut durch. Sie können das Token und dessen Ansprüche auch untersuchen und überprüfen, indem Sie die einseitige Webanwendung [jwt.ms](https://jwt.ms/) verwenden. |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun erfahren haben, wie Sie die für einen authentifizierten Benutzer verfügbaren Schutzvorlagen auflisten können, bearbeiten Sie den nächsten Schnellstart:

> [!div class="nextstepaction"]
> [Schnellstart: Verschlüsseln und Entschlüsseln von Text](quick-protection-encrypt-decrypt-text-csharp.md)