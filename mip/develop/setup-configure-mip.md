---
title: 'Microsoft Information Protection (MIP) SDK: Setup und Konfiguration'
description: Beschreibt die Setup- und Konfigurationsvoraussetzungen, um Anwendungen zu verwenden, die mit dem Microsoft Information Protection SDK erstellt wurden.
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.date: 01/30/2019
ms.author: mbaldwin
ms.openlocfilehash: c61b2c08cf0cb0fc59942bad3b5bb3fdbc47832c
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331969"
---
# <a name="microsoft-information-protection-mip-sdk-setup-and-configuration"></a>Microsoft Information Protection (MIP) SDK: Setup und Konfiguration 

Der Schnellstart und die Tutorialartikel drehen sich um das Erstellen von Anwendungen, die die MIP SDK-Bibliotheken und -APIs verwenden. Dieser Artikel zeigt Ihnen, wie Sie Ihr Office 365-Abonnement und Ihre Clientarbeitsstation einrichten und konfigurieren, um sich auf die Verwendung des SDK vorzubereiten.

## <a name="prerequisites"></a>Vorraussetzungen

Lesen Sie unbedingt die folgenden Themen, bevor Sie beginnen:

- [Was ist Office 365 Security and Compliance Center?](https://docs.microsoft.com/office365/securitycompliance/security-and-compliance)
- [Was ist Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
- [Wie funktioniert der Schutz in Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

> [!IMPORTANT]
> **Um die Datenschutzaspekte für Benutzer müssen Sie bitten, dass den Benutzer seine Zustimmung erteilen, bevor Sie automatische Protokollierung aktivieren.** Im folgende Beispiel wird eine Standardnachricht, die Microsoft zur protokollierungsbenachrichtigung nutzt:
>
> *Durch Aktivieren der Fehler- und Leistungsprotokollierung stimmen Sie dem Senden von Fehler- und Leistungsdaten an Microsoft zu. Microsoft erfasst Fehler- und Leistungsdaten automatisch über das Internet („Daten“). Microsoft verwendet diese Daten, um die Qualität, Sicherheit und Integrität von Microsoft-Produkten und -Diensten sicherzustellen und zu verbessern. Beispielsweise analysieren wir die Leistung und Zuverlässigkeit, die von Ihnen verwendeten Features, die Reaktionsschnelligkeit der Features, die Geräteleistung, Interaktionen mit der Benutzeroberfläche und etwaige Probleme, die bei der Nutzung des Produkts auftreten. Zu den Daten gehören auch Informationen zur Konfiguration Ihrer Software, z. B. der Software, die derzeit ausgeführt wird, und die IP-Adresse.*

## <a name="sign-up-for-an-office-365-subscription"></a>Registrieren für ein Office 365-Abonnement

Viele der SDK-Beispiele erfordern Zugriff auf ein Office 365-Abonnement. Wenn nicht bereits geschehen, registrieren Sie sich für einen der folgenden Abonnementtypen:

| Name | Registrieren |
|------|---------|
| Office 365 Enterprise E3-Testversion (kostenlose 30-Tage-Testversion) | https://go.microsoft.com/fwlink/p/?LinkID=403802 |
| Office 365 Enterprise E3 oder E5 | https://products.office.com/business/office-365-enterprise-e3-business-software |
| Enterprise Mobility and Security E3 oder E5 | https://www.microsoft.com/cloud-platform/enterprise-mobility-security |
| Azure Information Protection Premium P1 oder P2 | https://azure.microsoft.com/pricing/details/information-protection/ |
| Microsoft 365 E3, E5 oder F1 | https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans | 

## <a name="configure-sensitivity-labels"></a>Konfigurieren von Vertraulichkeitsbezeichnungen

Wenn Sie derzeit Azure Information Protection verwenden, müssen Sie Ihre Bezeichnungen auf Office 365 Security & Compliance Center migrieren. Weitere Information zu diesem Vorgang finden Sie unter [Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center](/azure/information-protection/configure-policy-migrate-labels) 

## <a name="configure-your-client-workstation"></a>Konfigurieren der Clientarbeitsstation

Führen Sie nun die folgenden Schritte aus, um sicherzustellen, dass Ihr Clientcomputer ordnungsgemäß eingerichtet und konfiguriert ist.

1. Wenn Sie eine Windows 10-Arbeitsstation verwenden:

   - Aktualisieren Sie Ihren Computer mit Windows Update auf Windows 10 Fall Creators Update (Version 1709) oder höher. So überprüfen Sie Ihre aktuelle Version:
     - Klicken Sie auf das Windows-Symbol in der linken unteren Ecke.
     - Geben Sie „PC-Informationen“ ein, und drücken Sie die EINGABETASTE.
     - Scrollen Sie nach unten bis zu **Windows-Spezifikationen**, und suchen Sie unter **Version** nach der Version.

   - Stellen Sie sicher, dass „Entwicklermodus“ auf Ihrer Arbeitsstation aktiviert ist:
     - Klicken Sie auf das Windows-Symbol in der linken unteren Ecke.
     - Geben Sie „Entwicklerfeatures verwenden“ ein, und drücken Sie die EINGABETASTE, wenn das Element **Entwicklerfeatures verwenden** angezeigt wird.
     - Wählen Sie im Dialogfeld **Einstellungen** auf der Registerkarte **Für Entwickler** unter „Entwicklerfeatures verwenden“ die Option **Entwicklermodus** aus.
     - Schließen das Dialogfeld **Einstellungen**.

2. Installieren Sie [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) mit den folgenden Workloads und optionalen Komponenten:
   - Windows-Workload **Entwicklung für die universelle Windows-Plattform** sowie die folgenden optionalen Komponenten:
     - **C++-Tools für die universelle Windows-Plattform**
     - **Windows 10 SDK 10.0.16299.0 SDK** oder höher, sofern nicht standardmäßig enthalten
   - Windows-Workload **Desktopentwicklung mit C++** sowie die folgenden optionalen Komponenten:
     - **Windows 10 SDK 10.0.16299.0 SDK** oder höher, sofern nicht standardmäßig enthalten 

     [![Visual Studio-Setup](media/setup-mip-client/visual-studio-install.png)](media/setup-mip-client/visual-studio-install.png#lightbox)

3. Installieren Sie die [ADAL.PS PowerShell-Modul](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2): 

   - Da Administratorrechte erforderlich sind, um Module zu installieren, müssen Sie zunächst eine der folgenden Aktionen ausführen:

     - Melden Sie sich an Ihrem Computer mit einem Konto an, das über Administratorrechte verfügt.
     - Führen Sie die Windows PowerShell-Sitzung mit erhöhten Rechten („Als Administrator ausführen“) aus.

   - Führen Sie dann das Cmdlet `install-module -name adal.ps` aus:

     ```powershell
     PS C:\WINDOWS\system32> install-module -name adal.ps

     Untrusted repository
     You are installing the modules from an untrusted repository. If you trust this repository, change its
     InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
     'PSGallery'?
     [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): A

     PS C:\WINDOWS\system32>
     ```

4. Laden Sie SDK-Dateien:

   Das MIP SDK wird auf den folgenden Plattformen, mit separaten Downloads für jede unterstützte Plattform/Sprache unterstützt:  

   [!INCLUDE [MIP SDK platform support](../includes/mip-sdk-platform-support.md)]

   **TAR.gz/. ZIP-downloads**

   TAR.gz und. ZIP-Downloads enthalten weitere komprimierte Dateien, die eine für jede API. Die komprimierten Dateien heißen wie folgt, in denen \<API\> = `file`, `protection`, oder `upe`, und \<OS\> = die Plattform: `mip_sdk_<API>_<OS>_1.0.0.0.zip (or .tar.gz)`. Beispielsweise wäre die Datei für die Datenschutz-API-Binärdateien und Header auf Debian: `mip_sdk_protection_debian9_1.0.0.0.tar.gz`. Jede enthaltene.tar.gz/.zip ist in drei Verzeichnisse unterteilt:

   - **Bins:** Für kompilierte Binärdateien für jede Plattformarchitektur, sofern zutreffend.
   - **Umfassen:** Headerdateien (C++).
   - **Beispiele:** Der Quellcode für Beispielanwendungen.
    
   **NuGet-Pakete**

   Wenn Sie Visual Studio-Entwicklung durchführen, kann das SDK auch über die NuGet-Paket-Manager-Konsole installiert werden:

    ```console
    Install-Package Microsoft.InformationProtection.File
    Install-Package Microsoft.InformationProtection.Policy
    Install-Package Microsoft.InformationProtection.Protection
    ```  

5. Wenn Sie das NuGet-Paket nicht verwenden, fügen Sie die Pfade der SDK-Binärdateien, um die PATH-Umgebungsvariablen angegeben. Der PATH-Variablen kann die abhängigen Binärdateien (DLLs) zur Laufzeit gefunden werden von Client-Anwendungen (OPTIONAL):

   Wenn Sie eine Windows 10-Arbeitsstation verwenden:

   - Klicken Sie auf das Windows-Symbol in der linken unteren Ecke.
   - Geben Sie „Path“ ein, und drücken Sie die EINGABETASTE, wenn das Element **Systemumgebungsvariablen bearbeiten** angezeigt wird.
   - Klicken Sie im Dialogfeld **Systemeigenschaften** auf **Umgebungsvariablen**.
   - Klicken Sie im Dialogfeld **Umgebungsvariablen** auf die Zeile **Pfad** der Variablen unter **Benutzervariablen für \<Benutzer\>**, und klicken Sie dann auf **Bearbeiten**.
   - Klicken Sie im Dialogfeld **Umgebungsvariable bearbeiten** auf **Neu**. Es wird eine neue bearbeitbare Zeile erstellt. Fügen Sie unter Verwendung des vollständigen Pfads zu jedem der Unterverzeichnisse `file\bins\debug\amd64`, `protection\bins\debug\amd64` und `upe\bins\debug\amd64` eine neue Zeile für jedes Unterverzeichnis hinzu. Die SDK-Verzeichnisse werden in einem `<API>\bins\<target>\<platform>`-Format gespeichert. Dabei gilt Folgendes:
     - \<API\> = `file`, `protection`, `upe`
     - \<target\> = `debug`, `release`
     - \<platform\> = `amd64` (x64), `x86`, etc.
   
   - Wenn Sie die Aktualisierung der Variablen **Path** abgeschlossen haben, klicken Sie auf **OK**. Klicken Sie dann auf **OK**, wenn Sie zum die Dialogfeld **Umgebungsvariablen** zurückkehren.

6. Laden Sie SDK-Beispiele von GitHub (OPTIONAL):

   - Wenn Sie noch kein Profil besitzen, erstellen Sie zunächst ein [GitHub-Profil](https://github.com/join).
   - Installieren Sie dann die neueste Version der [Git-Clienttools von Software Freedom Conservancy (Git Bash)](https://git-scm.com/download/)
   - Laden Sie mit Git Bash die Beispiele herunter, die Sie interessieren:
     - Verwenden Sie die folgende Abfrage, um die Repositorys anzuzeigen: https://github.com/Azure-Samples?utf8=%E2%9C%93&q=MipSdk. 
     - Verwenden Sie `git clone https://github.com/azure-samples/<repo-name>` mit Git Bash, um die einzelnen Beispielrepositorys herunterzuladen.

## <a name="register-a-client-application-with-azure-active-directory"></a>Registrieren einer Clientanwendung in Azure Active Directory

Als Teil der Office 365-Abonnement, Bereitstellung wird eine zugeordnete Azure Active Directory (Azure AD)-Mandant erstellt. Der Azure AD-Mandant stellt Identitäts- und Zugriffsverwaltung für Office 365-*Benutzerkonten* und -*Anwendungskonten* bereit. Anwendungen, die Zugriff auf gesicherte APIs (z.B. MIP-APIs) erfordern, benötigen ein Anwendungskonto.

Konten werden für die Authentifizierung und Autorisierung zur Laufzeit durch einen *Sicherheitsprinzipal* dargestellt, der aus den Identitätsinformationen des Kontos abgeleitet wird. Sicherheitsprinzipale, die ein Anwendungskonto darstellen, werden als ein [*Dienstprinzipal*](/azure/active-directory/develop/developer-glossary#service-principal-object) bezeichnet. 

So registrieren Sie ein Anwendungskonto in Azure AD für die Verwendung mit den Schnellstarts und MIP SDK-Beispielen:

  > [!IMPORTANT] 
  > Für den Zugriff auf die Azure AD-Mandantenverwaltung für die Kontoerstellung müssen Sie sich am Azure-Portal mit einem Benutzerkonto anmelden, das ein Mitglied der [Rolle „Besitzer“ für das Abonnement](/azure/billing/billing-add-change-azure-subscription-administrator) ist. Abhängig von der Konfiguration Ihres Mandanten müssen Sie möglicherweise auch Mitglied der Verzeichnisrolle „Globaler Administrator“ sein, um [eine Anwendung registrieren zu können](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
  > Es wird empfohlen, Tests mit einem eingeschränkten Konto auszuführen. Stellen Sie sicher, dass das Konto nur Zugriffsrechte für die erforderlichen SCC-Endpunkte besitzt. Klartextkennwörter, die über die Befehlszeile übergeben werden, können von Protokollierungssystemen erfasst werden.

1. Führen Sie die Schritte in [Registrieren einer app in Azure AD, eine neue Anwendung registrieren](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#register-a-new-application-using-the-azure-portal) Abschnitt. Verwenden Sie zu Testzwecken die folgenden Werte für die angegebenen Eigenschaften, wenn Sie die Schritte der Anleitung durchlaufen: 
    - **Anwendungstyp**: Wählen Sie „Nativ“ aus, da die Anwendungen, die durch das SDK veranschaulicht werden, nativ installierte Konsolenanwendungen sind. Native Anwendungen werden von OAuth2 als „öffentliche“ Clients betrachtet, da sie Anwendungsanmeldeinformationen nicht auf sichere Weise speichern bzw. verwenden können. Sie stehen im Gegensatz zu einer „vertraulichen“ serverbasierten Anwendung, z.B. einer Webanwendung, die mit ihren eigenen Anmeldeinformationen registriert ist. 
    - **Umleitungs-URI**: Da das SDK einfache Konsolenclientanwendungen verwendet, verwenden Sie einen URI im Format `<app-name>://authorize`.

2. Wenn Sie fertig sind, gelangen Sie zurück auf die Seite **Registrierte App** für Ihre neue Anwendungsregistrierung. Kopieren Sie die GUID, und speichern Sie sie im Feld **Anwendungs-ID**, da Sie sie für die Schnellstarts benötigen. 

3. Klicken Sie dann auf **Einstellungen**, um die APIs und Berechtigungen hinzuzufügen, auf die der Client Zugriff benötigt. Klicken Sie auf der Seite **Einstellungen** auf **Erforderliche Berechtigungen**.

4. Fügen Sie nun die MIP-APIs und Berechtigungen hinzu, die die Anwendung zur Laufzeit benötigt:
   - Klicken Sie auf der Seite **Erforderliche Berechtigungen** auf **Hinzufügen**. 
   - Klicken Sie auf der Seite **API-Zugriff hinzufügen** auf **API auswählen**.
   - Klicken Sie auf der Seite **API auswählen** auf **Microsoft Rights Management Services**-API, und klicken Sie dann auf **Auswählen**.
   - Auf der **Zugriff aktivieren** verfügbaren Berechtigungen für die API Seite, klicken Sie auf "**erstellen und den Zugriff geschützten Inhalte für Benutzer**", klicken Sie dann **wählen**, klicken Sie dann **abgeschlossen** .

5. Wiederholen Sie Schritt Nr. 4. Wenn Sie auf die Seite **Auswählen einer API** gelangen, müssen Sie dieses Mal jedoch nach der API suchen.
   - Geben Sie auf der Seite **API auswählen** im Suchfeld **Microsoft Information Protection-Synchronisierungsdienst** ein, klicken Sie auf die API und dann auf **Auswählen**.
   - Klicken Sie auf der Seite **Zugriff aktivieren** für die verfügbaren Berechtigungen der API auf **Alle vereinheitlichten Richtlinien lesen, auf die ein Benutzer Zugriff besitzt**, klicken Sie auf **Auswählen** und dann auf **Fertig**.

6. Wenn Sie zurück auf die Seite **Erforderliche Berechtigungen** gelangen, klicken Sie auf **Berechtigungen erteilen** und dann auf **Ja**. Dieser Schritt erteilt der Anwendung, die diese Registrierung verwendet, die Vorabzustimmung, um auf die APIs mit den angegebenen Berechtigungen zuzugreifen. Wenn Sie sich als globaler Administrator angemeldet haben, wird die Zustimmung für alle Benutzer im Mandanten aufgezeichnet, die die Anwendung ausführen. Andernfalls gilt sie nur für Ihr Benutzerkonto. 

Wenn Sie fertig sind, sollten die Anwendungsregistrierung und die API-Berechtigungen ähnlich wie im folgenden Beispiel aussehen:

   [![Azure AD App-Registrierung](media/setup-mip-client/aad-app-registration.png)](media/setup-mip-client/aad-app-registration.png#lightbox)


Weitere Informationen zum Hinzufügen von APIs und Berechtigungen zu einer Registrierung finden Sie unter [Konfigurieren einer Clientanwendung auf Web-APIs](/azure/active-directory/develop/quickstart-v1-update-azure-ad-app#configure-a-client-application-to-access-web-apis). Hier finden Sie Informationen zum Hinzufügen von APIs und Berechtigungen, die von einer Clientanwendung benötigt werden.  

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Anfordern einer Integrationsvereinbarung für Information Protection (Information Protection Integration Agreement, IPIA)

Bevor Sie eine mit MIP entwickelte Anwendung freigeben können, müssen Sie beantragen und eine formelle Vereinbarung mit Microsoft abschließen.

1. Beantragen Sie Ihre IPIA, indem Sie eine E-Mail mit folgenden Informationen an [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Requesting%20IPIA%20for%20<company-name>) senden:

   **Betreff:** Anfordern einer IPIA für *Name des Unternehmens*

   Geben Sie im E-Mail-Text folgende Informationen ein:
   - Anwendungs- oder Produktname
   - Vor- und Nachnamen des Antragstellers
   - E-Mail-Adresse des Antragstellers

2. Nach Erhalt Ihrer IPIA-Anforderung senden wir Ihnen ein Formular (als Word-Dokument). Überprüfen Sie die Vertragsbedingungen der IPIA, und senden Sie das Formular mit folgenden Informationen an [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=IPIA%20Response%20for%20<company-name>) zurück:

   - Offizieller Name des Unternehmens
   - Bundesstaat/Provinz (USA/Kanada) oder Land der Gründung oder Hauptverwaltung des Unternehmens
   - URL des Unternehmens
   - E-Mail-Adresse der Kontaktperson
   - Weitere Unternehmensanschriften (optional)
   - Name der Unternehmensanwendung
   - Kurze Beschreibung der Anwendung
   - *Azure-Mandanten-ID*
   - *App-ID* der Anwendung
   - Unternehmenskontakte, E-Mail-Adressen und Telefonnummern zur Kommunikation in kritischen Situationen

3. Nachdem wir Ihr Formular erhalten haben, senden wir Ihnen den Link zur endgültigen IPIA zur digitalen Unterzeichnung. Wenn Sie das Formular unterzeichnet haben, wird es vom zuständigen Microsoft-Vertreter ebenfalls unterzeichnet, womit die Vereinbarung abgeschlossen ist.

### <a name="already-have-a-signed-ipia"></a>Haben Sie bereits eine IPIA unterzeichnet?

Wenn Sie bereits über eine unterzeichnete IPIA verfügen und eine neue *App-ID* für eine zu veröffentlichende Anwendung hinzufügen möchten, senden Sie eine E-Mail an [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Updating%20IPIA%20for%20<company-name>), und geben Sie folgende Informationen an:

- Name der Unternehmensanwendung
- Kurze Beschreibung der Anwendung
- Azure-Mandanten-ID (auch wenn die gleiche wie zuvor)
- App-ID der Anwendung
- Unternehmenskontakte, E-Mail-Adressen und Telefonnummern zur Kommunikation in kritischen Situationen

Können Sie nach dem Senden der e-Mail bis zu 72 Stunden auf eine Bestätigung des Empfangs.

## <a name="next-steps"></a>Nächste Schritte

- Wenn Sie ein C++-Entwickler sind
  - Lesen Sie unbedingt [Beobachter Konzepte](concept-async-observers.md) vor der Installation im Schnellstart-Abschnitts, Informationen zu der asynchronen Natur der C++-APIs.
  - Wenn Sie einige Erfahrungen mit dem SDK abrufen möchten, beginnen Sie mit [Schnellstart: Client-Anwendung-Initialisierung (C++)](quick-app-initialization-cpp.md).
- Wenn Sie möchten eine C# Entwickler, wenn Sie bereit sind, beginnen Sie mit Informationen zum Abrufen von Erfahrungen mit dem SDK [Schnellstart: Initialisieren der Client-Anwendung (C#)](quick-app-initialization-csharp.md).


