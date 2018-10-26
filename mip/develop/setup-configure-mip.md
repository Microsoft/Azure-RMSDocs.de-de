---
title: 'Microsoft Information Protection (MIP) SDK: Setup und Konfiguration'
description: Beschreibt die Setup- und Konfigurationsvoraussetzungen, um Anwendungen zu verwenden, die mit dem Microsoft Information Protection SDK erstellt wurden.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 430e130a5ba2026c0a3c69a59dddd6f9d6b4e8f0
ms.sourcegitcommit: cc65c3851d4b8169a1a62c83afaf0f75402f7631
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2018
ms.locfileid: "49476203"
---
# <a name="microsoft-information-protection-mip-sdk-setup-and-configuration"></a>Microsoft Information Protection (MIP) SDK: Setup und Konfiguration 

Der Schnellstart und die Tutorialartikel drehen sich um das Erstellen von Anwendungen, die die MIP SDK-Bibliotheken und -APIs verwenden. Dieser Artikel zeigt Ihnen, wie Sie Ihr Office 365-Abonnement und Ihre Clientarbeitsstation einrichten und konfigurieren, um sich auf die Verwendung des SDK vorzubereiten.

Das MIP SDK wird auf den folgenden Plattformen unterstützt:  

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

Lesen Sie unbedingt die folgenden Themen, bevor Sie beginnen:

- [Was ist Office 365 Security and Compliance Center?](https://docs.microsoft.com/office365/securitycompliance/security-and-compliance)
- [Was ist Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
- [Wie funktioniert der Schutz in Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

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

Wenn Sie zurzeit Azure Information Protection verwenden, müssen Schritte ausgeführt werden, um Ihre Bezeichnungen zum Office 365 Security & Compliance Center zu migrieren. Weitere Information zu diesem Vorgang finden Sie unter [Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center](/azure/information-protection/configure-policy-migrate-labels) 

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

3. Installieren Sie das [ADAL.PS-PowerShell-Modul](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2). 

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

4. Herunterladen von SDK-Beispielen von GitHub 

   - Wenn Sie noch kein Profil besitzen, erstellen Sie zunächst ein [GitHub-Profil](https://github.com/join).
   - Installieren Sie dann die neueste Version der [Git-Clienttools von Software Freedom Conservancy (Git Bash)](https://git-scm.com/download/)
   - Laden Sie mit Git Bash die Beispiele herunter, die Sie interessieren:
     - Verwenden Sie die folgende Abfrage, um die Repositorys anzuzeigen: https://github.com/Azure-Samples?utf8=%E2%9C%93&q=MipSdk. 
     - Verwenden Sie `git clone https://github.com/azure-samples/<repo-name>` mit Git Bash, um die einzelnen Beispielrepositorys herunterzuladen.

5. Herunterladen der SDK-Binär- und -Headerdateien

   Eine ZIP-Datei, die die SDK-Binärdateien und Header für alle Plattformen enthält, finden Sie unter https://aka.ms/mipsdkbinaries. Die ZIP-Datei enthält mehrere zusätzliche ZIP-Dateien, eine für jede Plattform und API. Die Dateien sind wie folgt benannt. Dabei ist \<API\> = `file`, `protection` oder `upe` und \<OS\> = die Plattform: `mip_sdk_<API>_<OS>_1.0.0.0.zip (or .tar.gz)`.

   Beispielsweise würde die ZIP-Datei für die Protection-API-Binärdateien und -Header unter Debian den folgenden Namen tragen: `mip_sdk_protection_debian9_1.0.0.0.tar.gz`.

   Jede ZIP- oder TAR-Datei enthält drei Verzeichnisse:

   - **Bins:** Die kompilierten Binärdateien für jede Plattformarchitektur, sofern zutreffend.
   - **Include:** Die Microsoft Information Protection SDK-Headerdateien.
   - **Samples:** Quellcode für Beispielanwendungen.

   Wenn Sie Visual Studio-Entwicklung durchführen, kann das SDK auch über die NuGet-Paket-Manager-Konsole installiert werden:

    ```console
    Install-Package Microsoft.InformationProtection.File
    Install-Package Microsoft.InformationProtection.Policy
    Install-Package Microsoft.InformationProtection.Protection
    ```  
    
6. Fügen Sie die Pfade der SDK-Binärdateien (Dynamic Link Librarys, DLLs) der Umgebungsvariablen PATH hinzu. Die PATH-Variable ermöglicht es, dass die abhängigen DLLs zur Laufzeit von Clientanwendungen gefunden werden:
   - Klicken Sie auf das Windows-Symbol in der linken unteren Ecke.
   - Geben Sie „Path“ ein, und drücken Sie die EINGABETASTE, wenn das Element **Systemumgebungsvariablen bearbeiten** angezeigt wird.
   - Klicken Sie im Dialogfeld **Systemeigenschaften** auf **Umgebungsvariablen**.
   - Klicken Sie im Dialogfeld **Umgebungsvariablen** auf die Zeile **Pfad** der Variablen unter **Benutzervariablen für \<Benutzer\>**, und klicken Sie dann auf **Bearbeiten**.
   - Klicken Sie im Dialogfeld **Umgebungsvariable bearbeiten** auf **Neu**. Es wird eine neue bearbeitbare Zeile erstellt. Fügen Sie unter Verwendung des vollständigen Pfads zu jedem der Unterverzeichnisse `file\bins\debug\amd64`, `protection\bins\debug\amd64` und `upe\bins\debug\amd64` eine neue Zeile für jedes Unterverzeichnis hinzu. Die SDK-Verzeichnisse werden in einem `<API>\bins\<target>\<platform>`-Format gespeichert. Dabei gilt Folgendes:
     - \<API\> = `file`, `protection`, `upe`
     - \<target\> = `debug`, `release`
     - \<platform\> = `amd64` (auch: x64), `x86` usw.
   
   - Wenn Sie die Aktualisierung der Variablen **Path** abgeschlossen haben, klicken Sie auf **OK**. Klicken Sie dann auf **OK**, wenn Sie zum die Dialogfeld **Umgebungsvariablen** zurückkehren.

## <a name="register-a-client-application-with-azure-active-directory"></a>Registrieren einer Clientanwendung in Azure Active Directory

Als Teil des Bereitstellungsvorgangs des Office 365-Abonnements wird ein zugeordneter Azure AD-Mandant erstellt. Der Azure AD-Mandant stellt Identitäts- und Zugriffsverwaltung für Office 365-*Benutzerkonten* und -*Anwendungskonten* bereit. Anwendungen, die Zugriff auf gesicherte APIs (z.B. MIP-APIs) erfordern, benötigen ein Anwendungskonto.

Konten werden für die Authentifizierung und Autorisierung zur Laufzeit durch einen *Sicherheitsprinzipal* dargestellt, der aus den Identitätsinformationen des Kontos abgeleitet wird. Sicherheitsprinzipale, die ein Anwendungskonto darstellen, werden als ein [*Dienstprinzipal*](/azure/active-directory/develop/developer-glossary#service-principal-object) bezeichnet. 

So registrieren Sie ein Anwendungskonto in Azure AD für die Verwendung mit den Schnellstarts und MIP SDK-Beispielen:

  > [!IMPORTANT] 
  > Für den Zugriff auf die Azure AD-Mandantenverwaltung für die Kontoerstellung müssen Sie sich am Azure-Portal mit einem Benutzerkonto anmelden, das ein Mitglied der [Rolle „Besitzer“ für das Abonnement](/azure/billing/billing-add-change-azure-subscription-administrator) ist. Abhängig von der Konfiguration Ihres Mandanten müssen Sie möglicherweise auch Mitglied der Verzeichnisrolle „Globaler Administrator“ sein, um [eine Anwendung registrieren zu können](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
  > Es wird empfohlen, Tests mit einem eingeschränkten Konto auszuführen. Stellen Sie sicher, dass das Konto nur Zugriffsrechte für die erforderlichen SCC-Endpunkte besitzt. Klartextkennwörter, die über die Befehlszeile übergeben werden, können von Protokollierungssystemen erfasst werden.

1. Führen Sie die Schritte unter [Integrieren von Anwendungen in Azure Active Directory im Abschnitt „Hinzufügen eines Anwendung“](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#adding-an-application) aus. Verwenden Sie zu Testzwecken die folgenden Werte für die angegebenen Eigenschaften, wenn Sie die Schritte der Anleitung durchlaufen: 
    - **Anwendungstyp**: Wählen Sie „Nativ“ aus, da die Anwendungen, die durch das SDK veranschaulicht werden, nativ installierte Konsolenanwendungen sind. Native Anwendungen werden von OAuth2 als „öffentliche“ Clients betrachtet, da sie Anwendungsanmeldeinformationen nicht auf sichere Weise speichern bzw. verwenden können. Sie stehen im Gegensatz zu einer „vertraulichen“ serverbasierten Anwendung, z.B. einer Webanwendung, die mit ihren eigenen Anmeldeinformationen registriert ist. 
    - **Umleitungs-URI**: Da das SDK einfache Konsolenclientanwendungen verwendet, verwenden Sie einen URI im Format `<app-name>://authorize`.

2. Wenn Sie fertig sind, gelangen Sie zurück auf die Seite **Registrierte App** für Ihre neue Anwendungsregistrierung. Kopieren Sie die GUID, und speichern Sie sie im Feld **Anwendungs-ID**, da Sie sie für die Schnellstarts benötigen. 

3. Klicken Sie dann auf **Einstellungen**, um die APIs und Berechtigungen hinzuzufügen, auf die der Client Zugriff benötigt. Klicken Sie auf der Seite **Einstellungen** auf **Erforderliche Berechtigungen**.

4. Fügen Sie nun die MIP-APIs und Berechtigungen hinzu, die die Anwendung zur Laufzeit benötigt:
   - Klicken Sie auf der Seite **Erforderliche Berechtigungen** auf **Hinzufügen**. 
   - Klicken Sie auf der Seite **API-Zugriff hinzufügen** auf **API auswählen**.
   - Klicken Sie auf der Seite **API auswählen** auf **Microsoft Rights Management Services**-API, und klicken Sie dann auf **Auswählen**.
   - Klicken Sie auf der Seite **Zugriff aktivieren** für die verfügbaren Berechtigungen der API auf **Geschützte Inhalte für Benutzer erstellen und darauf zugreifen**, klicken Sie auf **Auswählen** und dann auf **Fertig**.

5. Wiederholen Sie Schritt Nr. 4. Wenn Sie auf die Seite **Auswählen einer API** gelangen, müssen Sie dieses Mal jedoch nach der API suchen.
   - Geben Sie auf der Seite **API auswählen** im Suchfeld **Microsoft Information Protection-Synchronisierungsdienst** ein, klicken Sie auf die API und dann auf **Auswählen**.
   - Klicken Sie auf der Seite **Zugriff aktivieren** für die verfügbaren Berechtigungen der API auf **Alle vereinheitlichten Richtlinien lesen, auf die ein Benutzer Zugriff besitzt**, klicken Sie auf **Auswählen** und dann auf **Fertig**.

6. Wenn Sie zurück auf die Seite **Erforderliche Berechtigungen** gelangen, klicken Sie auf **Berechtigungen erteilen** und dann auf **Ja**. Dieser Schritt erteilt der Anwendung, die diese Registrierung verwendet, die Vorabzustimmung, um auf die APIs mit den angegebenen Berechtigungen zuzugreifen. Wenn Sie sich als globaler Administrator angemeldet haben, wird die Zustimmung für alle Benutzer im Mandanten aufgezeichnet, die die Anwendung ausführen. Andernfalls gilt sie nur für Ihr Benutzerkonto. 

Wenn Sie fertig sind, sollten die Anwendungsregistrierung und die API-Berechtigungen ähnlich wie im folgenden Beispiel aussehen:

   [![Azure AD App-Registrierung](media/setup-mip-client/aad-app-registration.png)](media/setup-mip-client/aad-app-registration.png#lightbox)


Weitere Informationen zum Hinzufügen von APIs und Berechtigungen zu einer Registrierung finden Sie unter [„Aktualisieren einer Anwendung“ im Abschnitt „Konfigurieren einer Clientanwendung für den Zugriff auf Web-APIs“](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#updating-an-application). Hier finden Sie Informationen zum Hinzufügen von APIs und Berechtigungen, die von einer Clientanwendung benötigt werden.  

## <a name="next-steps"></a>Nächste Schritte

- Bevor Sie mit dem Abschnitt „Schnellstarts“ beginnen, sollten Sie sich unbedingt über [Observer-Objekte im MIP SDK](concept-async-observers.md) informieren, da das MIP SDK fast vollständig asynchron konzipiert ist.
- Wenn Sie bereit sind, praktische Erfahrungen mit dem SDK zu sammeln, beginnen Sie mit [Schnellstart: Initialisierung von Clientanwendungen (C++)](quick-app-initialization-cpp.md).
