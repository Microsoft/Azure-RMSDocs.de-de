---
title: "Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1bff9b06-8c5a-4b1d-9962-6668219210e6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: 7ec87b63b31d0b41c93dab7998df63e208308811


---


# Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet

*Gilt für: Azure Rights Management, Office 365*

Verwenden Sie die folgenden Vorgehensweisen, wenn Sie beschlossen haben, [Ihren eigenen Mandantenschlüssel zu verwalten](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok) und ihn über das Internet zu übertragen, anstatt zu einer Microsoft-Einrichtung zu reisen, um den Mandantenschlüssel persönlich zu übertragen:


## Vorbereiten Ihrer Arbeitsstation mit Internetverbindung
Um Ihre Arbeitsstation mit Internetverbindung vorzubereiten, führen Sie diese 3 Schritte aus:

-   [Schritt 1: Installieren Sie die Windows PowerShell für Azure Rights Management](#step-1-install-windows-powershell-for-azure-rights-management)

-   [Schritt 2: Rufen Sie Ihre Azure Active Directory-Mandanten-ID ab](#step-2-get-your-azure-active-directory-tenant-id)

-   [Schritt 3: Laden Sie das BYOK-Toolset herunter](#step-3-download-the-byok-toolset)

### Schritt 1: Installieren Sie die Windows PowerShell für Azure Rights Management
Laden Sie auf der Arbeitsstation mit Internetverbindung das Windows PowerShell-Modul für Rights Management herunter, und installieren Sie es.

> [!NOTE]
> Wenn Sie dieses Windows PowerShell-Modul zuvor heruntergeladen haben, führen Sie den folgenden Befehl aus, um zu überprüfen, ob Ihre Version mindestens 2.1.0.0 ist: `(Get-Module aadrm -ListAvailable).Version`

Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

### Schritt 2: Rufen Sie Ihre Azure Active Directory-Mandanten-ID ab
Starten Sie die Windows PowerShell mit der Option **Als Administrator ausführen** , und führen Sie dann die folgenden Befehle aus:

-   Verwenden Sie das Cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629415.aspx) , um eine Verbindung mit dem Azure RMS-Dienst herzustellen:

    ```
    Connect-AadrmService
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

-   Verwenden Sie das Cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) , um die Konfiguration Ihres Mandanten anzuzeigen.

    ```
    Get-AadrmConfiguration
    ```
    Speichern Sie aus der Ausgabe die GUID aus der ersten Zeile (BPOSId). Dies ist Ihre Azure Active Directory-Mandanten-ID, die Sie später benötigen, wenn Sie Ihren Mandantenschlüssel für den Upload vorbereiten.

-   Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen, bis Sie bereit sind, um den Schlüssel hochzuladen:

    ```
    Disconnect-AadrmService
    ```

Schließen Sie das Windows PowerShell-Fenster nicht.

### Schritt 3: Laden Sie das BYOK-Toolset herunter
Wechseln Sie zum Microsoft Download Center, und [laden Sie das BYOK-Toolset](http://go.microsoft.com/fwlink/?LinkId=335781) für Ihre Region herunter:

|Region|Paketname|
|----------|----------------|
|Nordamerika|AzureRMS-BYOK-tools-UnitedStates.zip|
|Europa|AzureRMS-BYOK-tools-Europe.zip|
|Asien|AzureRMS-BYOK-tools-AsiaPacific.zip|
Das Toolset enthält Folgendes:

-   Ein KEK-Paket (Schlüsselaustauschschlüssel) mit einem Namen, der mit **BYOK-KEK-pkg-** beginnt.

-   Ein Security World-Paket mit einem Namen, der mit **BYOK-SecurityWorld-pkg-** beginnt.

-   Ein Python-Skript namens **verifykeypackage.py**.

-   Eine ausführbare Befehlszeilendatei namens **KeyTransferRemote.exe**, eine Metadatendatei namens **KeyTransferRemote.exe.config** und die zugehörigen DLLs.

-   Ein Visual C++ Redistributable Package namens **vcredist_x64.exe**.

Kopieren Sie das Paket auf ein USB-Laufwerk oder einen anderen mobilen Speicher.

## Vorbereiten Ihrer nicht verbundenen Arbeitsstation
Um Ihre nicht mit einem Netzwerk (entweder das Internet oder Ihr internes Netzwerk) verbundene Arbeitsstation vorzubereiten, führen Sie diese 2 Schritte aus:

-   [Schritt 1: Bereiten Sie die nicht verbundene Arbeitsstation mit Thales HSM vor](#step-1-prepare-the-disconnected-workstation-with-thales-hsm)

-   [Schritt 2: Installieren Sie das BYOK-Toolset auf der nicht verbundenen Arbeitsstation](#step-2-install-the-byok-toolset-on-the-disconnected-workstation)

### Schritt 1: Bereiten Sie die nicht verbundene Arbeitsstation mit Thales HSM vor
Installieren Sie auf der nicht verbundenen Arbeitsstation die unterstützende nCipher-Software (Thales) auf einem Windows-Computer, und schließen Sie dann ein Thales HSM an diesen Computer an.

Stellen Sie sicher, dass sich die Thales-Tools im Pfad **(%nfast_home%\bin** und **%nfast_home%\python\bin**) befinden. Geben Sie zum Beispiel Folgendes ein:

```
set PATH=%PATH%;”%nfast_home%\bin”;”%nfast_home%\python\bin”
```
Weitere Informationen finden Sie im Benutzerhandbuch, das im Lieferumfang des Thales HSM enthalten ist, oder besuchen Sie die Thales-Website für Azure RMS unter [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

### Schritt 2: Installieren Sie das BYOK-Toolset auf der nicht verbundenen Arbeitsstation
Kopieren Sie das BYOK-Toolsetpaket von dem USB-Laufwerk oder dem anderen mobilen Speicher, und gehen Sie dann wie folgt vor:

1.  Extrahieren Sie die Dateien aus dem heruntergeladenen Paket in einen beliebigen Ordner.

2.  Führen Sie aus diesem Ordner heraus „vcredist_x64.exe“ aus.

3.  Befolgen Sie die Anweisungen zum Installieren der Visual C++-Laufzeitkomponenten für Visual Studio 2012.

## Generieren Ihres Mandantenschlüssels
Befolgen Sie auf der nicht verbundenen Arbeitsstation diese 3 Schritte, um Ihren eigenen Mandantenschlüssel zu generieren:

-   [Schritt 1: Erstellen Sie eine Security World](#step-1-create-a-security-world)

-   [Schritt 2: Überprüfen Sie das heruntergeladene Paket](#step-2-validate-the-downloaded-package)

-   [Schritt 3: Erstellen Sie einen neuen Schlüssel](#step-3-create-a-new-key)

### Schritt 1: Erstellen Sie eine Security World
Starten Sie eine Eingabeaufforderung, und führen Sie das Thales-Programm „new-world“ aus.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Dieses Programm erstellt eine **Security World**-Datei unter „%NFAST_KMDATA%\local\world“. Dies entspricht dem Ordner „C:\ProgramData\nCipher\Key Management Data\local“. Sie können verschiedene Werte für das Quorum verwenden, aber in unserem Beispiel werden Sie aufgefordert, für jeden Wert drei leere Karten und PINs einzugeben. Anschließend benötigen Sie zwei Karten, um administrativen Zugriff auf die Security World (das angegebene Quorum) zu erhalten.  Diese Karten werden dann zum **Administrator Card Set** für die neue Security World. Sie können zu diesem Zeitpunkt das Kennwort oder die PIN für jede ACS-Karte angeben, oder dies später mit einem Befehl hinzufügen.

> [!TIP]
> Sie können den aktuellen Konfigurationsstatus Ihres HSMs mit dem Befehl `nkminfo` überprüfen.

Führen Sie dann Folgendes durch:

1.  Installieren Sie den Thales CNG-Anbieter, wie in der Thales-Dokumentation beschrieben, und konfigurieren Sie ihn für die Verwendung der neuen Security World.

2.  Sichern Sie die World-Datei unter **%nfast_kmdata%\local**. Sichern und schützen Sie die World-Datei, die Administrator Cards und deren PINs, und stellen Sie sicher, dass keine einzelne Person Zugriff auf mehr als eine Karte hat.

### Schritt 2: Überprüfen Sie das heruntergeladene Paket
Dieser Schritt ist optional, wird aber empfohlen, damit Sie Folgendes überprüfen können:

-   Der in dem Toolset enthaltene Schlüsselaustauschschlüssel wurde auf einem Original-HSM von Thales generiert.

-   Der Hash der Azure RMS Security World, die in dem Toolset enthalten ist, wurde in einem Original-HSM von Thales generiert.

-   Der Schlüsselaustauschschlüssel kann nicht exportiert werden.

> [!NOTE]
> Um das heruntergeladene Paket zu überprüfen, muss das HSM angeschlossen und eingeschaltet sein, und es muss sich eine Security World darauf befinden (beispielsweise die gerade von Ihnen erstellte).

#### So überprüfen Sie das heruntergeladene Paket

1.  Führen Sie das Skript „verifykeypackage.py“ aus, indem Sie in Abhängigkeit von Ihrer Region einen der folgenden Befehle eingeben:

    -   Für Nordamerika:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-NA-1 -w BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Für Europa:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-EU-1 -w BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Für Asien:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-AP-1 -w BYOK-SecurityWorld-pkg-AP-1
        ```

    > [!TIP]
    > Die Thales-Software umfasst einen Python-Interpreter unter %NFAST_HOME%\python\bin.

2.  Vergewissern Sie sich, dass Folgendes angezeigt wird, was eine erfolgreiche Überprüfung anzeigt: **Ergebnis:  ERFOLG (SUCCESS)**

Dieses Skript überprüft die Kette der Signaturgeber bis hinauf zum Thales-Stammschlüssel. Der Hash dieses Stammschlüssels ist in das Skript eingebettet, und sein Wert sollte **59178a47 de508c3f 291277ee 184f46c4 f1d9c639**sein. Sie können diesen Wert auch gesondert überprüfen, indem Sie die [Thales-Website](http://www.thalesesec.com/)besuchen.

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
cngimport --import -M --key=contosokey --appname=simple contosokey
```
Wenn Sie diesen Befehl ausführen, verwenden Sie diese Anleitungen:

-   Ersetzen Sie *contosokey* durch den Wert, den Sie in [Schritt 1: Erstellen Sie eine Security World](#step-1-create-a-security-world) im Abschnitt *Generieren Ihres Mandantenschlüssels* angegeben haben.

-   Verwenden Sie die Option **-M**, damit der Schlüssel für dieses Szenario geeignet ist. Ohne dies wird das Resultat ein Schlüssel, der für den aktuellen Benutzer spezifisch ist.

-   Die **appname**-Option ist der in der Schlüsseldatei angegebene Name der Anwendung. Wenn Sie sich beim Erstellen eines neuen Schlüssels an diese Anweisungen gehalten haben, wird der Wert „simple“ verwendet, wie im Befehl gezeigt. Wenn Sie aber einen vorhandenen HSM-geschützten Schlüssel für eine AD RMS-Migration zu Azure RMS migrieren, geben Sie den vorhandenen Namen in diesem Befehl und die nachfolgenden Befehle an, wenn diese auch die appname-Option verwenden.

Dieser Befehl erstellt eine Tokenschlüsseldatei in Ihrem Ordner „%NFAST_KMDATA%\local“ mit einem Namen, der mit **key_caping`_`** gefolgt von einer SID beginnt. Beispiel: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Diese Datei enthält einen verschlüsselten Schlüssel.

> [!TIP]
> Sie können den aktuellen Konfigurationsstatus Ihrer Schlüssel mit dem Befehl `nkminfo –k` anzeigen.

Sichern Sie diese Tokenschlüsseldatei an einem sicheren Ort.

> [!IMPORTANT]
> Wenn Sie Ihren Schlüssel später an Azure RMS übertragen, kann Microsoft diesen Schlüssel nicht an Sie zurückexportieren, weshalb es äußerst wichtig ist, dass Sie Ihren Schlüssel und die Security World gut geschützt sichern. Anleitungen und bewährte Methoden zum Sichern Ihres Schlüssels erhalten Sie von Thales.

Sie sind jetzt bereit, um Ihren Mandantenschlüssel an Azure RMS zu übertragen.

## Vorbereiten Ihres Mandantenschlüssels für die Übertragung
Befolgen Sie auf der nicht verbundenen Arbeitsstation diese 4 Schritte, um Ihren eigenen Mandantenschlüssel vorzubereiten:

-   [Schritt 1: Erstellen Sie eine Kopie Ihres Schlüssels mit verringerten Berechtigungen](#step-1-create-a-copy-of-your-key-with-reduced-permissions)

-   [Schritt 2: Untersuchen Sie die neue Kopie des Schlüssels](#step-2-inspect-the-new-copy-of-the-key)

-   [Schritt 3: Verschlüsseln Sie Ihren Schlüssel mithilfe des Schlüsselaustauschschlüssels von Microsoft](#step-3-encrypt-your-key-by-using-microsoft-s-key-exchange-key)

-   [Schritt 4: Kopieren Sie Ihr Schlüsselübertragungspaket auf die Arbeitsstation mit Internetverbindung](#step-4-copy-your-key-transfer-package-to-the-internet-connected-workstation)

### Schritt 1: Erstellen Sie eine Kopie Ihres Schlüssels mit verringerten Berechtigungen
Um die Berechtigungen für Ihren Mandantenschlüssel zu verringern, gehen Sie wie folgt vor:

-   Führen Sie in Abhängigkeit von Ihrer Region einen der folgenden Befehle an einer Eingabeaufforderung aus:

    -   Für Nordamerika:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Für Europa:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Für Asien:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1
        ```

Wenn Sie diesen Befehl ausführen, ersetzen Sie *contosokey* durch den Wert, den Sie in [Schritt 1: Erstellen Sie eine Security World](#step-1-create-a-security-world) im Abschnitt *Generieren Ihres Mandantenschlüssels* angegeben haben.

Sie werden aufgefordert, Ihre Security World ACS-Karten einzustecken und, falls festgelegt, das Kennwort oder die PIN.

Wenn der Befehl abgeschlossen wird, wird **Result: SUCCESS** angezeigt, und die Kopie Ihres Mandantenschlüssels mit verringerten Berechtigungen befindet sich in der Datei mit dem Namen „key_xferacId_*&lt;contosokey&gt;*“.

### Schritt 2: Untersuchen Sie die neue Kopie des Schlüssels
Führen Sie optional die Thales-Hilfsprogramme aus, um die minimalen Berechtigungen des neuen Mandantenschlüssels sicherzustellen:

-   aclprint.py:

    ```
    "%nfast_home%\bin\preload.exe" -m 1 -A xferacld -K contosokey "%nfast_home%\python\bin\python" "%nfast_home%\python\examples\aclprint.py"
    ```

-   kmfile-dump.exe:

    ```
    "%nfast_home%\bin\kmfile-dump.exe" "%NFAST_KMDATA%\local\key_xferacld_contosokey"
    ```

Wenn Sie diesen Befehl ausführen, ersetzen Sie *contosokey* durch den Wert, den Sie in [Schritt 1: Erstellen Sie eine Security World](#step-1-create-a-security-world) im Abschnitt *Generieren Ihres Mandantenschlüssels* angegeben haben.

### Schritt 3: Verschlüsseln Sie Ihren Schlüssel mithilfe des Schlüsselaustauschschlüssels von Microsoft
Führen Sie in Abhängigkeit von Ihrer Region einen der folgenden Befehle aus:

-   Für Nordamerika:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Für Europa:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Für Asien:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

Wenn Sie diesen Befehl ausführen, verwenden Sie diese Anleitungen:

-   Ersetzen Sie *contosokey* durch den Bezeichner, den Sie in [Schritt 1: Erstellen Sie eine Security World](#step-1-create-a-security-world) im Abschnitt *Generieren Ihres Mandantenschlüssels* angegeben haben.

-   Ersetzen Sie *GUID* durch Ihre Azure Active Directory-Mandanten-ID, die Sie in [Schritt 2: Rufen Sie Ihre Azure Active Directory-Mandanten-ID ab](#step-2-get-your-azure-active-directory-tenant-id) im Abschnitt *Vorbereiten Ihrer Arbeitsstation mit Internetverbindung* abgerufen haben.

-   Ersetzen Sie *ContosoFirstKey* durch eine Bezeichnung, die als Ausgabedateiname verwendet werden soll.

Wenn dieser Vorgang erfolgreich abgeschlossen wird, wird **Ergebnis: ERFOLG** angezeigt, und im aktuellen Ordner ist eine neue Datei vorhanden, die folgenden Namen trägt: TransferPackage-*ContosoFirstkey*.byok.

### Schritt 4: Kopieren Sie Ihr Schlüsselübertragungspaket auf die Arbeitsstation mit Internetverbindung
Verwenden Sie ein USB-Laufwerk oder einen anderen mobilen Speicher, um die Ausgabedatei aus dem vorherigen Schritt (KeyTransferPackage-*ContosoFirstkey*.byok) auf Ihre Arbeitsstation mit Internetverbindung zu kopieren.

> [!NOTE]
> Verwenden Sie Sicherheitsmaßnahmen, um die Datei zu schützen, denn sie enthält Ihren privaten Schlüssel.

## Übertragen Ihres Mandantenschlüssels an Azure RMS
Befolgen Sie auf der Arbeitsstation mit Internetverbindung diese 3 Schritte, um Ihren neuen Mandantenschlüssel in Azure RMS zu übertragen:

-   [Schritt 1: Stellen Sie eine Verbindung mit Azure RMS her](#step-1-connect-to-azure-rms)

-   [Schritt 2: Laden Sie das Schlüsselpaket hoch](#step-2-upload-the-key-package)

-   [Schritt 3: Zählen Sie Ihre Mandantenschlüssel auf – nach Bedarf](#step-3-enumerate-your-tenant-keys-as-needed)

### Schritt 1: Stellen Sie eine Verbindung mit Azure RMS her
Kehren Sie zum Windows PowerShell-Fenster zurück, und geben Sie Folgendes ein:

1.  Stellen Sie wieder eine Verbindung mit dem [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Dienst her:

    ```
    Connect-AadrmService
    ```

2.  Verwenden Sie das Cmdlet [Get-AadrmKeys](http://msdn.microsoft.com/library/windowsazure/dn629420.aspx) , um die aktuelle Konfiguration Ihres Mandantenschlüssels anzuzeigen:

    ```
    Get-AadrmKeys
    ```

### Schritt 2: Laden Sie das Schlüsselpaket hoch
Verwenden Sie das Cmdlet [Add-AadrmKey](http://msdn.microsoft.com/library/windowsazure/dn629418.aspx) , um das Schlüsselübertragungspaket, das Sie von der nicht verbundenen Arbeitsstation kopiert haben, hochzuladen:

```
Add-AadrmKey –KeyFile <PathToPackageFile> -Verbose
```
> [!WARNING]
> Sie werden zur Bestätigung dieser Aktion aufgefordert. Es ist wichtig, dass Ihnen klar ist, dass Sie diese Aktion nicht rückgängig machen können. Wenn Sie einen Mandantenschlüssel hochladen, wird er automatisch der primäre Mandantenschlüssel Ihrer Organisation, und Benutzer beginnen, diesen Mandantenschlüssel zu verwenden, wenn sie Dokumente und Dateien schützen.

Wenn der Upload erfolgreich verläuft, wird folgende Meldung angezeigt: **Der Rechteverwaltungsdienst hat den Schlüssel erfolgreich hinzugefügt.**

Rechnen Sie mit einer Verzögerung der Replikation der Änderung in alle [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Rechenzentren.

### Schritt 3: Zählen Sie Ihre Mandantenschlüssel auf – nach Bedarf
Verwenden Sie erneut das Cmdlet „Get-AadrmKeys“, um die Änderungen an Ihrem Mandantenschlüssel anzuzeigen und immer, wenn Sie eine Liste Ihrer Mandantenschlüssel anzeigen möchten. Die angezeigten Mandantenschlüssel umfassen den anfänglichen Mandantenschlüssel, den Microsoft für Sie generiert hat, sowie alle von Ihnen hinzugefügten Mandantenschlüssel:

```
Get-AadrmKeys
```
Der Mandantenschlüssel, der als **Aktiv** markiert ist, ist der, den Ihre Organisation im Moment verwendet, um Dokumente und Dateien zu schützen.

Sie haben jetzt alle Schritte abgeschlossen, die für „Bring Your Own Key“ über das Internet erforderlich sind, und können mit den nächsten Schritten zum Planen und Implementieren des Mandantenschlüssels fortfahren.


> [!div class="button"]
[Nächste Schritte >>](plan-implement-tenant-key.md#next-steps)





<!--HONumber=Jul16_HO3-->


