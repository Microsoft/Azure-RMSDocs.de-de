---
title: Schnellstart – Listet die vertraulichkeitsbezeichnungen in einem Microsoft Information Protection (MIP)-Mandanten, die mit dem MIP SDK C# Wrapper
description: Einen Schnellstart zeigt Ihnen, wie Sie mit der Microsoft Information Protection SDK C# Wrapper um die Liste der vertraulichkeitsbezeichnungen in Ihrem Mandanten.
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.date: 01/04/2019
ms.author: mbaldwin
ms.openlocfilehash: 0b1b110fe3b2e96c258c7b94a3d356b9404d6e7e
ms.sourcegitcommit: 1d444b17e3d096f3e867e0240182ae3143fc1b71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59892407"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C#)

In dieser Schnellstartanleitung erfahren Sie, wie Sie die MIP SDK-Datei-API zu verwenden, um die Liste der vertraulichkeitsbezeichnungen für Ihre Organisation konfiguriert werden.

## <a name="prerequisites"></a>Vorraussetzungen

Stellen Sie vor dem Fortfahren sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Vollständige [Schnellstart: Initialisieren der Client-Anwendung (C#)](quick-app-initialization-csharp.md) erste, die eine Starter-Visual Studio-Projektmappe erstellt. Dieser Schnellstart zum „Auflisten der Vertraulichkeitsbezeichnungen“ baut auf der vorherigen Erstellung der Startprojektmappe auf.
- Optional: Überprüfen Sie [klassifizierungsbezeichnungen](concept-classification-labels.md) Konzepte.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Hinzufügen von Logik zur Liste der Vertraulichkeitsbezeichnungen

Im Folgenden fügen Sie der Liste von Vertraulichkeitsbezeichnungen Ihrer Organisation Logik mithilfe des FileEnginge-Objekts hinzu. 

1. Öffnen Sie die Visual Studio-Projektmappe, die Sie erstellt, in der vorherigen haben "Schnellstart: Initialisieren der Client-Anwendung (C#) "Artikel.

2. Mithilfe von **Projektmappen-Explorer**, öffnen Sie die CS-Datei im Projekt, das die Implementierung enthält die `Main()` Methode. Standardmäßig weist sie den gleichen Namen wie das Projekt auf, in dem sie enthalten ist. Diesen Namen haben Sie bei Projekterstellung angegeben. 

3. Gegen Ende der `Main()` Text unterhalb der schließenden geschweiften Klammer `}` von der `Main()` funktionieren (im vorherigen Schnellstart Stelle), fügen Sie den folgenden Code:

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

1. Verwenden Sie STRG + UMSCHALT + B (**Projektmappe**) zum Erstellen der Clientanwendung. Wenn keine Buildfehler auftreten, verwenden Sie F5 (**Debuggen starten**) zum Ausführen der Anwendung.

2. Wenn Ihr Projekt erstellt und ausgeführt wird, auf die Anwendung *möglicherweise* Aufforderung zur Authentifizierung über ADAL jedes Mal die SDK-Aufrufe Ihrer `AcquireToken()` Methode. Wenn die zwischengespeicherte Anmeldeinformationen bereits vorhanden sind, wird nicht Sie anmelden und die Liste der Bezeichnungen aufgefordert. 

     [![Anmeldung in Visual Studio zum Erhalten des Tokens](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Möglicherweise müssen Sie Ihre Zustimmung erteilen, um der Anwendung den Zugriff auf die MIP-APIs zu gewähren, während die Ausführung unter dem Anmeldekonto erfolgt. Dies geschieht, wenn der Azure AD-Anwendungsregistrierung nicht (wie in der Einrichtung und Konfiguration des MIP SDKs beschrieben) vorab zugestimmt wurde, oder wenn Sie sich mit einem Konto von einem anderen Mandanten anmelden (der sich von dem unterscheidet, bei dem Ihre Anwendung registriert ist). Klicken Sie einfach auf **Akzeptieren**, damit Ihre Einwilligung erfasst wird.

     [![Visual Studio-Einwilligung](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

3. Nach der Authentifizierung sollte die vertraulichkeitsbezeichnungen, ähnlich wie im folgenden Beispiel von der Konsolenausgabe angezeigt werden:

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

### <a name="problems-during-execution-of-c-application"></a>Probleme bei der Ausführung von C# Anwendung

| Zusammenfassung | Fehlermeldung | Lösung |
|---------|---------------|----------|
| Ungültiges Zugriffstoken | *Es ist eine Ausnahme aufgetreten... ist das Zugriffstoken falsche/abgelaufen? <br> <br>Fehler bei API-Aufruf: Fehler bei der Profile_add_engine_async: [Klasse mip::PolicySyncException] Fehler beim Abrufen der Richtlinie, Fehler bei Anforderung mit http-Statuscode: 401, X-ms-Diagnostics: [2000001; Reason = "OAuth-Token, die mit der Anforderung übermittelte kann nicht analysiert werden."; Error_category = "Invalid_token"], CorrelationId: [35bc0023-3727-4eff-8062-000006d5d672]'<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (Process 29924) wurde beendet mit Code 0.<br> <br>Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen...* | Wenn Ihr Projekt erfolgreich erstellt wird und dennoch eine Ausgabe ähnlich der linken angezeigt wird, enthält Ihre `AcquireOAuth2Token()`-Methode wahrscheinlich ein ungültiges oder abgelaufenes Token. Wechseln Sie zurück zur [erstellen und Testen Sie die Anwendung](#build-and-test-the-application) und erneutes Generieren der Access-token-Update `AcquireOAuth2Token()` in diesem Fall und Neuerstellung/neuen Test. Sie können das Token und dessen Ansprüche auch untersuchen und überprüfen, indem Sie die einseitige Webanwendung [jwt.ms](https://jwt.ms/) verwenden. |
| Vertraulichkeitsbezeichnungen sind nicht konfiguriert | Nicht zutreffend | Wenn Ihr Projekt erfolgreich erstellt wird, Sie aber keine Ausgabe im Konsolenfenster erhalten, stellen Sie sicher, dass die Vertraulichkeitsbezeichnungen Ihrer Organisation ordnungsgemäß konfiguriert sind. Ausführliche Informationen finden Sie unter „Definieren des Bezeichnungsschemas und der Schutzeinstellungen“ im Artikel zur [Einrichtung und Konfiguration des MIP SDKs](setup-configure-mip.md).  |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie die Vertraulichkeitsbezeichnungen für Ihre Organisation aufführen, können Sie nun mit dem nächsten Schnellstart fortfahren:

> [!div class="nextstepaction"]
> [Set and get a sensitivity label (Festlegen und Abrufen einer Vertraulichkeitsbezeichnung)](quick-file-set-get-label-csharp.md)
