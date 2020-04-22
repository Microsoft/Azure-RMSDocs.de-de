---
title: 'Schnellstart: Auflisten der Vertraulichkeitsbezeichnungen in einem MSIP-Mandanten (Microsoft Information Protection) mithilfe des C#-Wrappers für das MSIP SDK'
description: In diesen Schnellstart wird veranschaulicht, wie Sie den C#-Wrapper für das Microsoft Information Protection SDK nutzen können, um die Vertraulichkeitsbezeichnungen in Ihrem Mandanten aufzulisten.
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 9f12ff856e7d70c76e3c89700d05aeb653d030cd
ms.sourcegitcommit: a3f901e479abbe056f8936a96b7253f0826d1415
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "75555278"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C#)

In diesem Schnellstart erfahren Sie, wie Sie die Datei-API für das MSIP SDK verwenden können, um die für Ihre Organisation konfigurierten Vertraulichkeitsbezeichnungen aufzulisten.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Schließen Sie zuerst den [Schnellstart für die Initialisierung der Clientanwendung (C#)](quick-app-initialization-csharp.md) ab, in dem Sie eine Visual Studio-Projektmappe für den Einstieg erstellen. Dieser Schnellstart zum „Auflisten der Vertraulichkeitsbezeichnungen“ baut auf der vorherigen Erstellung der Startprojektmappe auf.
- Optional: Lesen Sie sich die Konzepte zu [Klassifizierungsbezeichnungen](concept-classification-labels.md) durch.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Hinzufügen von Logik zur Liste der Vertraulichkeitsbezeichnungen

Im Folgenden fügen Sie der Liste von Vertraulichkeitsbezeichnungen Ihrer Organisation Logik mithilfe des FileEnginge-Objekts hinzu. 

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie im vorherigen Artikel „Schnellstart: Initialisierung der Clientanwendung (C#)“ erstellt haben.

2. Öffnen Sie mithilfe des **Projektmappen-Explorers** die CS-Datei im Projekt, die die Implementierung der `Main()`-Methode enthält. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben. 

3. Fügen Sie am Ende von `Main()` oberhalb des Abschnitts zum Herunterfahren der Anwendung der `Main()`-Funktion (wo Sie in der vorherigen Schnellstartanleitung aufgehört haben) den folgenden Code ein:

  ```csharp
  // List sensitivity labels from fileEngine and display name and id  
  foreach(var label in fileEngine.SensitivityLabels)
  {
      Console.WriteLine(string.Format("{0} : {1}", label.Name, label.Id));

      if (label.Children.Count != 0)
      {
          foreach (var child in label.Children)
          {
              Console.WriteLine(string.Format("{0}{1} : {2}", "\t",child.Name, child.Id));
          }
      }
  }
  ```

## <a name="build-and-test-the-application"></a>Erstellen und Testen der Anwendung

Letztendlich erstellen und testen Sie die Clientanwendung.

1. Drücken Sie STRG+UMSCHALT+B (**Projektmappe erstellen**), um Ihre Clientanwendung zu erstellen. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn das Projekt erfolgreich erstellt und ausgeführt wird, *kann* die Anwendung Sie jedes Mal zur Authentifizierung über ADAL auffordern, wenn das SDK Ihre `AcquireToken()`-Methode aufruft. Wenn bereits zwischengespeicherte Anmeldeinformationen vorhanden sind, werden Sie nicht zur Anmeldung aufgefordert. Die Liste der Bezeichnungen wird sofort angezeigt. 

     [![Anmeldung in Visual Studio zum Erhalten des Tokens](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Möglicherweise müssen Sie Ihre Zustimmung erteilen, um der Anwendung den Zugriff auf die MIP-APIs zu gewähren, während die Ausführung unter dem Anmeldekonto erfolgt. Dies geschieht, wenn der Azure AD-Anwendungsregistrierung nicht (wie in der Einrichtung und Konfiguration des MIP SDKs beschrieben) vorab zugestimmt wurde, oder wenn Sie sich mit einem Konto von einem anderen Mandanten anmelden (der sich von dem unterscheidet, bei dem Ihre Anwendung registriert ist). Klicken Sie einfach auf **Akzeptieren**, damit Ihre Einwilligung erfasst wird.

     [![Visual Studio-Einwilligung](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

3. Nach der Authentifizierung sollten die Vertraulichkeitsbezeichnungen in der Konsolenausgabe ähnlich dem folgenden Beispiel angezeigt werden:

  ```console
  Personal : 73c47c6a-eb00-4a6a-8e19-efaada66dee6
  Public : 73254501-3d5b-4426-979a-657881dfcb1e
  General : da480625-e536-430a-9a9e-028d16a29c59
  Confidential : 569af77e-61ea-4deb-b7e6-79dc73653959
        Recipients Only (C) : d98c4267-727b-430e-a2d9-4181ca5265b0
        All Employees (C) : 2096f6a2-d2f7-48be-b329-b73aaa526e5d
        Anyone (not protected) (C) : 63a945ec-1131-420d-80da-2fedd15d3bc0
  Highly Confidential : 905845d6-b548-439c-9ce5-73b2e06be157
        Recipients Only : 05ee72d9-1a75-441f-94e2-dca5cacfe012
        All Employees : 922b06ef-044b-44a3-a8aa-df12509d1bfe
        Anyone (not protected) : c83fc820-961d-40d4-ba12-c63f72a970a3
  Press a key to continue.
  ```

   > [!NOTE]
   > Kopieren und speichern Sie die ID von mindestens einer Vertraulichkeitsbezeichnung (z.B. `f42a3342-8706-4288-bd31-ebb85995028z`), da Sie diese im nächsten Schnellstart benötigen.

## <a name="troubleshooting"></a>Problembehandlung

### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung der C#-Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Ungültiges Zugriffstoken | *An exception occurred... is the access token incorrect/expired?<br> (Ein Fehler ist aufgetreten. Das Zugriffstoken ist möglicherweise falsch oder abgelaufen.)<br>Failed API call: profile_add_engine_async Failed with: [class mip::PolicySyncException] Failed acquiring policy, Request failed with http status code: 401, x-ms-diagnostics: [2000001;reason="OAuth token submitted with the request cannot be parsed.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672]'<br> (Fehlerhafter API-Aufruf: profile_add_engine_async Fehler: [class mip::PolicySyncException] Fehler beim Abrufen der Richtlinie, Anforderung fehlgeschlagen – HTTP-Statuscode: 401, x-ms-diagnostics: [2000001;reason="Das mit der Anforderung übermittelte OAuth-Token kann nicht analysiert werden.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672])<br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (process 29924) exited with code 0.<br> (Die Ausführung von „C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe“ (Prozess 29924) wurde mit dem Code 0 beendet.)<br>Press any key to close this window . . .* (Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen.) | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, enthält Ihre `AcquireOAuth2Token()`-Methode wahrscheinlich ein ungültiges oder abgelaufenes Token. Navigieren Sie zurück zu [Erstellen und Testen der Anwendung](#build-and-test-the-application), stellen Sie das Zugriffstoken wieder her, aktualisieren Sie `AcquireOAuth2Token()` erneut, und führen Sie die Tests und die Erstellung erneut durch. Sie können das Token und dessen Ansprüche auch untersuchen und überprüfen, indem Sie die einseitige Webanwendung [jwt.ms](https://jwt.ms/) verwenden. |
| Vertraulichkeitsbezeichnungen sind nicht konfiguriert | Nicht zutreffend | Wenn Ihr Projekt erfolgreich erstellt wird, Sie aber keine Ausgabe im Konsolenfenster erhalten, stellen Sie sicher, dass die Vertraulichkeitsbezeichnungen Ihrer Organisation ordnungsgemäß konfiguriert sind. Ausführliche Informationen finden Sie unter „Definieren des Bezeichnungsschemas und der Schutzeinstellungen“ im Artikel zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md).  |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie die Vertraulichkeitsbezeichnungen für Ihre Organisation aufführen, können Sie nun mit dem nächsten Schnellstart fortfahren:

> [!div class="nextstepaction"]
> [Set and get a sensitivity label (Festlegen und Abrufen einer Vertraulichkeitsbezeichnung)](quick-file-set-get-label-csharp.md)
