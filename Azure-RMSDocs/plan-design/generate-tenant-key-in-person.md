---
title: "Generieren und Übertragen Ihres Mandantenschlüssels – persönlich | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3281e45e-cf69-4dc5-946b-3029851d3152
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: 8e77298121a84f6feb16a992da81bd9c3bb7b20b


---

# Generieren und Übertragen Ihres Mandantenschlüssels – persönlich

*Gilt für: Azure Rights Management, Office 365*


Verwenden Sie die folgenden Vorgehensweisen, wenn Sie sich für die [Verwaltung Ihres eigenen Mandantenschlüssels](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok) entschieden haben und ihn nicht über das Internet, sondern persönlich übertragen möchten.

## Generieren Ihres Mandantenschlüssels
Um Ihren eigenen Mandantenschlüssel zu generieren, befolgen Sie diese 3 Schritte:

-   [Schritt 1: Bereiten Sie eine Arbeitsstation mit Thales HSM vor](#step-1-prepare-a-workstation-with-thales-hsm)

-   [Schritt 2: Erstellen Sie eine Security World](#step-2-create-a-security-world)

-   [Schritt 3: Erstellen Sie einen neuen Schlüssel](#step-3-create-a-new-key)

### Schritt 1: Bereiten Sie eine Arbeitsstation mit Thales HSM vor
Installieren Sie die unterstützende nCipher-Software (Thales) auf einem Windows-Computer. Schließen Sie ein Thales HSM an diesen Computer an. Stellen Sie sicher, dass sich die Thales-Tools in Ihrem Pfad befinden. Weitere Informationen finden Sie im Benutzerhandbuch, das im Lieferumfang des Thales HSM enthalten ist, oder besuchen Sie die Thales-Website für Azure RMS unter [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

### Schritt 2: Erstellen Sie eine Security World
Starten Sie eine Eingabeaufforderung, und führen Sie das Thales-Programm „new-world“ aus.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Dieses Programm erstellt eine **Security World**-Datei unter „%NFAST_KMDATA%\local\world“. Dies entspricht dem Ordner „C:\ProgramData\nCipher\Key Management Data\local“. Sie können verschiedene Werte für das Quorum verwenden, aber in unserem Beispiel werden Sie aufgefordert, für jeden Wert drei leere Karten und PINs einzugeben. Dann verleihen alle Kombinationen aus zwei Karten vollständigen Zugriff auf die Security World.  Diese Karten werden dann zum **Administrator Card Set** für die neue Security World.

Führen Sie dann Folgendes durch:

1.  Installieren Sie den Thales CNG-Anbieter, wie in der Thales-Dokumentation beschrieben, und konfigurieren Sie ihn für die Verwendung der neuen Security World.

2.  Sichern Sie die World-Datei. Sichern und schützen Sie die World-Datei, die Administrator Cards und deren PINs, und stellen Sie sicher, dass keine einzelne Person Zugriff auf mehr als eine Karte hat.

Sie sind jetzt bereit, um einen neuen Schlüssel zu erstellen, der dann Ihr RMS-Mandantenschlüssel ist.

### Schritt 3: Erstellen Sie einen neuen Schlüssel
Generieren Sie einen CNG-Schlüssel unter Verwendung der Thales-Programme **generatekey** und **cngimport** .

Führen Sie folgenden Befehl aus, um den Schlüssel zu generieren:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
Wenn Sie diesen Befehl ausführen, verwenden Sie diese Anleitungen:

-   Der Parameter **protect** muss wie gezeigt auf den Wert **module** festgelegt werden. Dadurch wird ein modulgeschützter Schlüssel erstellt. Das BYOK-Toolset unterstützt OCS-geschützte Schlüssel nicht.

-   Als Schlüsselgröße empfehlen wir 2048, unterstützt werden aber auch 1024-Bit-RSA-Schlüssel für bestehende AD RMS-Kunden, die solche Schlüssel haben und zu Azure RMS migrieren.

-   Ersetzen Sie *ident* durch den Wert von **contosokey** und **plainname** durch einen beliebigen Zeichenfolgenwert. Zur Minimierung des Verwaltungsaufwands und zur Verringerung des Fehlerrisikos empfehlen wir Ihnen die Verwendung desselben Werts für beide sowie die Verwendung von ausschließlich Kleinbuchstaben.

-   Der „pubexp“ bleibt in diesem Beispiel leer (Standard), aber Sie können spezifische Wert angeben. Weitere Informationen finden Sie in der Thales-Dokumentation.

Führen Sie dann den folgenden Befehl aus, um den Schlüssel in CNG zu importieren:

```
cngimport --import –M --key=contosokey --appname=simple contosokey
```
Wenn Sie diesen Befehl ausführen, verwenden Sie diese Anleitungen:

-   Ersetzen Sie *contosokey* durch denselben Wert, den Sie in Schritt 1 angegeben haben.

-   Verwenden Sie die Option **-M**, damit der Schlüssel für dieses Szenario geeignet ist. Ohne dies wird das Resultat ein Schlüssel, der für den aktuellen Benutzer spezifisch ist.

Dieser Befehl erstellt eine Tokenschlüsseldatei in Ihrem Ordner „%NFAST_KMDATA%\local“ mit einem Namen, der mit **key_caping`_`** gefolgt von einer SID beginnt. Beispiel: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Diese Datei enthält einen verschlüsselten Schlüssel.

Sichern Sie diese Tokenschlüsseldatei an einem sicheren Ort.

> [!IMPORTANT]
> Wenn Sie Ihren Schlüssel später in Azure RMS übertragen, besitzt Microsoft eine nicht wiederherstellbare Kopie Ihres Schlüssels. Dies bedeutet, dass niemand Ihren Schlüssel von den HSMs bei Microsoft abrufen kann. Dies ermöglicht Ihnen die exklusive Kontrolle über Ihren Mandantenschlüssel. Daher ist es äußerst wichtig, dass Sie Ihren Schlüssel und die Security World gut geschützt sichern. Anleitungen und bewährte Methoden zum Sichern Ihres Schlüssels erhalten Sie von Thales.

Sie sind jetzt bereit, Ihren Mandantenschlüssel an Azure RMS zu übertragen.

## Übertragen Ihres Mandantenschlüssels an Azure RMS
Nachdem Sie Ihren eigenen Schlüssel generiert haben, müssen Sie ihn in Azure RMS übertragen, bevor Sie ihn verwenden. Um maximale Sicherheit zu garantieren, handelt es sich bei dieser Übertragung um einen manuellen Prozess, bei dem Sie zu einer Microsoft-Niederlassung in Redmond, Washington, USA, fliegen müssen. Um diesen Prozess durchzuführen, befolgen Sie diese 3 Schritte:

-   [Schritt 1: Bringen Sie Ihren Schlüssel zu Microsoft](#step-1-bring-your-key-to-microsoft)

-   [Schritt 2: Übertragen Sie Ihren Schlüssel in die Azure RMS Security World](#step-2-transfer-your-key-to-the-azure-rms-security-world)

-   [Schritt 3: Abschließende Verfahren](#step-3-closing-procedures)

### Schritt 1: Bringen Sie Ihren Schlüssel zu Microsoft

-   Wenden Sie sich an den Microsoft-Kundendienst wenden, um einen Termin für die Schlüsselübertragung für Azure RMS zu vereinbaren. Bringen Sie Folgendes mit zu Microsoft in Redmond:

    -   Ein Quorum Ihrer Administrator Cards. Wenn Sie die vorherigen Anweisungen in [Schritt 2: Erstellen Sie eine Security World](#step-2-create-a-security-world) befolgt haben, sind dies beliebige zwei Ihrer drei Karten.

    -   Mitarbeiter, die zum Transport Ihrer Administrator Cards und PINs, normalerweise zwei (einer pro Karte), autorisiert sind.

    -   Ihre Security World-Datei (%NFAST_KMDATA%\local\world) auf einem USB-Laufwerk.

    -   Ihre Tokenschlüsseldatei auf einem USB-Laufwerk.

### Schritt 2: Übertragen Sie Ihren Schlüssel in die Azure RMS Security World

1.  Wenn Sie bei Microsoft ankommen, um Ihren Schlüssel zu übertragen, passiert Folgendes:

    -   Microsoft stellt Ihnen eine Offlinearbeitsstation zur Verfügung, an der ein Thales HSM angeschlossen ist, auf der Thales-Software installiert ist und an der zuvor eine Azure RMS Security World-Datei in den Ordner „C:\Temp\Destination“ geladen wurde.

    -   An dieser Arbeitsstation laden Sie Ihre Security World-Datei und die Tokenschlüsseldatei von Ihrem USB-Laufwerk in den Ordner „C:\Temp\Source“.

    -   Azure RMS-Bediener übertragen Ihren Schlüssel mithilfe von Thales-Hilfsprogrammen sicher in die Azure RMS Security World.

    Dieser Prozess ähnelt dem folgenden, wobei der letzte Parameter von „key-xfer-im“ in diesem Beispiel durch den Namen Ihrer Tokenschlüsseldatei ersetzt wird:

    **C:\&gt; mk-reprogram.exe --owner c:\Temp\Destination add c:\Temp\Source**

    **C:\&gt; key-xfer-im.exe c:\Temp\Source c:\Temp\Destination --module c:\Temp\Source\key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**

2.  Sie und die Azure RMS-Bediener werden von „Mk-reprogram“ aufgefordert, ihre jeweiligen Administrator Cards einzustecken und die PINs einzugeben. Diese Befehle geben eine Tokenschlüsseldatei in „C:\Temp\Destination“ aus, die Ihren von der Azure RMS Security World geschützten Schlüssel enthält.

### Schritt 3: Abschließende Verfahren

-   In Ihrer Anwesenheit führen die Azure RMS-Bediener Folgendes aus:

    -   Ausführen eines Tools, das Microsoft in Zusammenarbeit mit Thales entwickelt hat, das zwei Berechtigungen entfernt: Die Berechtigung zum Wiederherstellen des Schlüssels und die Berechtigung zum Ändern von Berechtigungen. Nachdem dies erfolgt ist, ist Ihr Schlüssel gesperrt in der Azure RMS Security World. Thales HSMs gestatten Azure RMs-Bedienern mit ihren Administrator Cards nicht, die unverschlüsselte Textkopie Ihres Schlüssels wiederherzustellen.

    -   Kopieren Sie die sich ergebende Schlüsseldatei auf ein USB-Laufwerk, um sie später in den Azure RMS-Dienst hochzuladen.

    -   Setzen Sie das HSM auf die Werkseinstellungen zurück, und bereinigen Sie die Arbeitsstation vollständig.

Sie haben die erforderlichen Schritte der persönlichen Übertragung für „Bring Your Own Key“ jetzt abgeschlossen und können zu Ihrer Organisation zurückkehren, um die nächsten Schritte der Planung und Implementierung Ihres Mandantenschlüssels auszuführen.

> [!div class="button"]
[Nächste Schritte >>](plan-implement-tenant-key.md#next-steps)






<!--HONumber=Jul16_HO3-->


