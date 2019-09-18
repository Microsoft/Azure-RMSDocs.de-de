---
title: Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client
description: Anweisungen und Informationen für Administratoren zum Verwalten des Azure Information Protection Unified Bezeichnung-Clients mithilfe von PowerShell.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: d14ab94a045a31ccf22b862d91c224246866d48d
ms.sourcegitcommit: 908ca5782fe86e88502dccbd0e82fa18db9b96ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71060049"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-unified-client"></a>Administratorhandbuch: Verwenden von PowerShell mit dem Azure Information Protection Unified Client

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Unified Bezeichnung-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Wenn Sie den Azure Information Protection Unified Bezeichnung-Client installieren, werden PowerShell-Befehle automatisch installiert. Dadurch können Sie den Client durch Ausführen von Befehlen, die Sie in Skripts zur Automatisierung einfügen können, verwalten.

Die Cmdlets werden mit dem PowerShell-Modul **azureinformationprotection**installiert, das über Cmdlets für die Bezeichnung verfügt. Beispiel:

|Cmdlet für die Bezeichnung|Beispielsyntax|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|Für einen freigegebenen Ordner werden alle Dateien mit einer bestimmten Bezeichnung ermittelt.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|Überprüfen Sie bei einem freigegebenen Ordner die Dateiinhalte, und versehen Sie Dateien ohne Bezeichnung automatisch gemäß den von Ihnen festgelegten Bedingungen mit Bezeichnungen.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|Für einen freigegebenen Ordner wird eine bestimmte Bezeichnung auf alle Dateien ohne Bezeichnung angewendet.|
|[Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)|Bezeichnen Sie Dateien nicht interaktiv, z.B. durch Verwenden eines Skripts, das nach einem Zeitplan ausgeführt wird.|

> [!TIP]
> Um Cmdlets mit Pfadlängen zu verwenden, die mehr als 260 Zeichen umfassen, können Sie die folgende [Gruppenrichtlinieneinstellung](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/) verwenden, die ab Windows 10, Version 1607 verfügbar ist:<br /> **Lokale Computer Richtlinie** > **Computerkonfiguration** > **Administrative Vorlagen** **alle Einstellungen**Aktivieren von**Win32 Long-Pfaden**  >  >  
> 
> Bei Windows Server 2016 können Sie die gleiche Gruppenrichtlinieneinstellung verwenden, wenn Sie die neuesten administrativen Vorlagen (ADMX-Dateien) für Windows 10 installieren.
>
> Weitere Informationen finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

Dieses Modul installiert **\ProgramFiles (x86) \Microsoft Azure Information Protection** und fügt diesen Ordner der Systemvariablen **PSModulePath** hinzu. Die DLL-Datei für dieses Modul lautet **AIP.dll**.

> [!IMPORTANT]
> Das azureinformationprotection-Modul unterstützt das Konfigurieren erweiterter Einstellungen für Bezeichnungen oder Bezeichnungs Richtlinien nicht. Für diese Einstellungen benötigen Sie das Office 365 Security & Compliance Center PowerShell. Weitere Informationen finden Sie unter [benutzerdefinierte Konfigurationen für den Azure Information Protection Unified Bezeichnung-Client](clientv2-admin-guide-customizations.md).

### <a name="prerequisites-for-using-the-azureinformationprotection-module"></a>Voraussetzungen für die Verwendung des Moduls "azureinformationprotection"

Zusätzlich zu den Voraussetzungen für die Installation des Moduls "azureinformationprotection" müssen bei der Verwendung der Bezeichnungs-Cmdlets für Azure Information Protection zusätzliche Voraussetzungen erfüllt werden:

1. Der Azure Rights Management-Dienst muss aktiviert werden.

2. So entfernen Sie den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos: 

    - Die Administratorfunktion muss für Ihre Organisation aktiviert werden. Zudem muss Ihr Konto als Administrator für Azure Rights Management konfiguriert sein.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Voraussetzung 1: Der Azure Rights Management-Dienst muss aktiviert sein

Wenn Ihr Azure Information Protection Mandanten nicht aktiviert ist, lesen Sie die Anweisungen unter [[Aktivieren des Schutz Dienstanbieter von Azure Information Protection](../activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Voraussetzung 2: Sie entfernen den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos

Typische Szenarien für das Entfernen des Schutzes von Dateien für andere Benutzer umfassen die Datenermittlung oder Datenwiederherstellung. Wenn Sie den Schutz mithilfe von Bezeichnungen anwenden, können Sie den Schutz durch Festlegen einer neuen Bezeichnung entfernen, durch die kein Schutz angewendet wird. Sie können dazu aber auch die Bezeichnung entfernen.

Sie müssen über ein Rights Management-Nutzungsrecht verfügen oder Administrator sein, um den Schutz von Dateien zu entfernen. Für die Datenermittlung oder Datenwiederherstellung wird in der Regel die Administratorfunktion verwendet. Informationen zum Aktivieren dieses Feature und zum Konfigurieren Ihres Kontos als Administrator finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](../configure-super-users.md).

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection

Sie können die Bezeichnungs-Cmdlets nicht interaktiv ausführen, indem Sie das Cmdlet **Set-AIPAuthentication** verwenden.

Wenn Sie die Cmdlets für die Bezeichnung ausführen, werden die Befehle in Ihrem eigenen Benutzerkontext in einer interaktiven PowerShell-Sitzung ausgeführt. Um sie unbeaufsichtigt auszuführen, erstellen Sie für diesen Zweck ein neues Azure AD-Benutzerkonto. Führen Sie dann im Kontext dieses Benutzers das Cmdlet „Set-AIPAuthentication“ zum Festlegen und Speichern von Anmeldeinformationen mithilfe eines Azure AD-Zugriffstokens aus. Dieses Benutzerkonto wird dann authentifiziert und für den Schutzdienst vom Azure Information Protection gestartet. Das Konto lädt die Azure Information Protection-Richtlinie und alle von den Bezeichnungen verwendeten Schutz Vorlagen herunter.

> [!NOTE]
> Beachten Sie bei der Verwendung von Bezeichnungs Richtlinien für verschiedene Benutzer, dass Sie dieses Konto möglicherweise einer bestimmten Bezeichnungs Richtlinie hinzufügen müssen.

Bei der ersten Ausführung dieses Cmdlets werden Sie aufgefordert, sich bei Azure Information Protection anzumelden. Geben Sie den Benutzerkonto Namen und das Kennwort an, die Sie für das unbeaufsichtigte Konto erstellt haben. Danach kann dieses Konto die Bezeichnungs-Cmdlets nicht interaktiv ausführen, bis das Authentifizierungs Token in Azure AD abläuft. 

Damit das Benutzerkonto sich beim ersten Mal interaktiv anmelden kann, muss das Konto über die Berechtigung " **Lokal anmelden** " verfügen. Diese Berechtigung ist Benutzerkonten standardmäßig zugewiesen, aber Ihre Unternehmensrichtlinien lassen diese Konfiguration für Dienstkonten unter Umständen nicht zu. Wenn dies der Fall ist, können Sie "Set-aipauthentication" mit dem Parameter " *onbehalfof* " ausführen, damit die Authentifizierung ohne die Anmeldeaufforderung abgeschlossen wird.

Wenn das Token in Azure AD abläuft, führen Sie das Cmdlet erneut aus, um ein neues Token abzurufen.

Wenn Sie dieses Cmdlet ohne Parameter ausführen, erhält das Konto ein Zugriffstoken, das 90 Tage oder bis zum Ablauf des Kennworts gültig ist.  

Um zu steuern, wann das Zugriffstoken abläuft, führen Sie dieses Cmdlet mit Parametern aus. Mit dieser Konfiguration können Sie das Zugriffs Token in Azure AD für ein Jahr, zwei Jahre oder so konfigurieren, dass es nie abläuft. Die Parameter für "Set-aipauthentication" verwenden Werte aus einem App-Registrierungsprozess in Azure AD.

Nachdem Sie dieses Cmdlet ausgeführt haben, können Sie die Bezeichnungs-Cmdlets im Kontext des Dienst Kontos ausführen, das Sie erstellt haben.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>So erstellen und konfigurieren Sie die Azure AD-Anwendungen für „Set-AIPAuthentication“

> [!NOTE]
> Wenn Sie die aktuelle Vorschauversion des Unified-Bezeichnungs Clients verwenden, verwenden Sie dieses Verfahren nicht. lesen Sie stattdessen den Abschnitt so [Erstellen und konfigurieren Sie die Azure AD Anwendungen für den "Set-aipauthentication-Preview"-Client](#to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication---preview-client).

1. Melden Sie sich in einem neuen Browserfenster beim [Azure-Portal](https://portal.azure.com/) an.

2. Navigieren Sie für den Azure AD Mandanten, den Sie mit Azure Information Protection verwenden, zu **Azure Active Directory** > **Manage** > **App-Registrierungen**. 

3. Wählen Sie **+ neue Registrierung**aus, um Ihre Web-App/API-Anwendung zu erstellen. Geben Sie auf dem Blatt **Anwendung registrieren** die folgenden Werte an, und klicken Sie dann auf **registrieren**:

   - **Name**:`AIPOnBehalfOf`
        
        Wenn Sie möchten, können Sie auch einen anderen Namen angeben. Der Name muss pro Mandant eindeutig sein.
    
    - **Unterstützte Konto Typen**: **Nur Konten in diesem Organisations Verzeichnis**
    
    - **Umleitungs-URI (optional)** : **Web** und`http://localhost`

4. Kopieren Sie auf dem Blatt " **aiponbehalfof** " den Wert für die **Anwendungs-ID (Client-ID)** . Der Wert sieht in etwa wie im folgenden Beispiel `57c3c1c3-abf9-404e-8b2b-4652836c8c66`aus:. Dieser Wert wird für den *webappid* -Parameter verwendet, wenn Sie das Cmdlet "Set-aipauthentication" ausführen. Fügen Sie den Wert ein, und speichern Sie ihn später.

5. Wählen Sie auf dem Blatt **aiponbehalfof** im Menü **Verwalten** die Option **Authentifizierung**aus.

6. Aktivieren Sie auf dem Blatt **aiponbehalfof-Authentication** im Abschnitt **Erweiterte Einstellungen** das Kontrollkästchen **ID Tokens** , und wählen Sie dann **Speichern**aus.

7. Wählen Sie auf dem Blatt **aiponbehalfof-Authentication** im Menü **Verwalten** die Option **Zertifikate & Geheimnissen**aus.

8. Wählen Sie auf dem Blatt **aiponbehalfof-Zertifikate & Geheimnisse** im Abschnitt geheime **Client** Schlüssel die Option **+ neuer geheimer Client**Schlüssel aus. 

9. Geben Sie unter **geheimen Client Schlüssel hinzufügen**Folgendes an, und wählen Sie dann **Hinzufügen**aus:
    
    - **Beschreibung**:`Azure Information Protection client`
    - **Läuft**ab: Geben Sie die gewünschte Dauer an (1 Jahr, 2 Jahre oder läuft nie ab).

9. Kopieren Sie auf dem Blatt **aiponbehalfof--Zertifikate & geheimen** Schlüssel im Abschnitt geheime **Client** Schlüssel die Zeichenfolge für den **Wert**. Diese Zeichenfolge sieht in etwa wie im folgenden `+LBkMvddz?WrlNCK5v0e6_=meM59sSAn`Beispiel aus:. Um sicherzustellen, dass Sie alle Zeichen kopieren, wählen Sie das Symbol aus, das **in die Zwischenablage kopiert**wird. 
    
    Es ist wichtig, dass diese Zeichenfolge gespeichert wird, da sie nicht erneut angezeigt wird und nicht abgerufen werden kann. Speichern Sie wie bei allen vertraulichen Informationen, die Sie verwenden, den gespeicherten Wert sicher, und beschränken Sie den Zugriff darauf.

10. Wählen Sie auf dem Blatt **aiponbehalfof-Zertifikate & geheimen** Schlüssel im Menü **Verwalten** die **Option API**verfügbar machen aus.

11. Wählen Sie auf dem Blatt **aiponbehalfof-macht eine API** die Option für die Option **Anwendungs-ID-URI** **festlegen** aus, und ändern Sie im Wert Anwendungs- **ID-URI** den Wert **API** zu **http**. Diese Zeichenfolge sieht in etwa wie im folgenden `http://d244e75e-870b-4491-b70d-65534953099e`Beispiel aus:. 
    
    Wählen Sie **Speichern** aus.

12. Wählen Sie auf dem Blatt **aiponbehalfof-API verfügbar** machen die Option **+ Bereich hinzufügen**aus.

13. Geben Sie auf dem Blatt **Bereich hinzufügen** Folgendes an, und verwenden Sie die vorgeschlagenen Zeichen folgen als Beispiele, und wählen Sie dann **Bereich hinzufügen**aus:
    - **Bereichs Name**:`user-impersonation`
    - **Wem kann zugestimmt werden?** : **Administratoren und Benutzer**
    - **Anzeige Name für die Administrator Zustimmung**:`Access Azure Information Protection scanner`
    - **Beschreibung der Administrator Zustimmung**:`Allow the application to access the scanner for the signed-in user`
    - **Anzeige Name der Benutzer Zustimmung**:`Access Azure Information Protection scanner`
    - **Beschreibung der Benutzer Zustimmung**:`Allow the application to access the scanner for the signed-in user`
    - **Status**: **Aktiviert** (Standard)

14. Schließen Sie das Blatt " **aiponbehalfof-API verfügbar** machen", und schließen Sie dieses Blatt.

15. Wählen Sie auf dem Blatt **App-Registrierungen** die Option **+ neue Anwendungs Registrierung** aus, um Ihre native Anwendung zu erstellen.

16. Geben Sie auf dem Blatt **Anwendung registrieren** die folgenden Einstellungen an, und klicken Sie dann auf **registrieren**:
    - **Name**:`AIPClient`
    - **Unterstützte Konto Typen**: **Nur Konten in diesem Organisations Verzeichnis**
    - **Umleitungs-URI (optional)** : **Öffentlicher Client (Mobile & Desktop)** und`http://localhost`

17. Kopieren Sie auf dem Blatt **aipclient** den Wert der **Anwendungs-ID (Client)** . Der Wert sieht in etwa wie im folgenden Beispiel `8ef1c873-9869-4bb1-9c11-8313f9d7f76f`aus:. 
    
    Dieser Wert wird für den nativeappid-Parameter verwendet, wenn Sie das Cmdlet "Set-aipauthentication" ausführen. Fügen Sie den Wert ein, und speichern Sie ihn später.

18. Wählen Sie auf dem Blatt **aipclient** im Menü **Verwalten** die Option **Authentifizierung**aus.

19. Geben Sie auf dem Blatt **aipclient-Authentifizierung** Folgendes an, und wählen Sie dann **Speichern**aus:
    - Wählen Sie im Abschnitt **Erweiterte Einstellungen** die Option **ID-Token**aus.
    - Wählen Sie im Abschnitt **Standard Clienttyp** die Option **Ja**aus.

20. Wählen Sie auf dem Blatt **aipclient-Authentifizierung** im Menü **Verwalten** die Option **API-Berechtigungen**aus.

21. Wählen Sie auf dem Blatt **aipclient-Berechtigungen** die Option **+ Berechtigung hinzufügen**aus.

22. Wählen Sie auf dem Blatt **API-Berechtigungen anfordern** die Option **meine APIs**aus.

23. Wählen Sie im Abschnitt **API auswählen** die Option **apionbehalfof**aus, und aktivieren Sie dann das Kontrollkästchen für den **Benutzer**Identitätswechsel als Berechtigung. Wählen Sie **Berechtigungen hinzufügen**aus. 

24. Wählen Sie auf dem Blatt **API-Berechtigungen** im Abschnitt **Zustimmung erteilen** die Option **Administrator Zustimmung für Ihren \<Mandanten *Namen* > erteilen aus** , und wählen Sie für die Bestätigungsaufforderung **Ja** aus.

Sie haben soeben die Konfiguration der beiden Apps abgeschlossen und verfügen nun über die Werte, die Sie zum Ausführen von [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) mit den Parametern *WebAppId*, *WebAppKey* und *NativeAppId* benötigen. Aus unseren Beispielen:

`Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"`

Führen Sie diesen Befehl im Kontext des Kontos aus, das die Dokumente ohne Benutzereingriff bezeichnet und schützt. Beispiel: Ein Benutzerkonto für Ihre PowerShell-Skripts oder das Dienstkonto zum Ausführen der Azure Information Protection-Überprüfung.

Wenn Sie diesen Befehl zum ersten Mal ausführen, werden Sie zur Anmeldung aufgefordert. Dadurch wird das Zugriffstoken für Ihr Konto erstellt und sicher unter „%localappdata%\Microsoft\MSIP“ gespeichert. Nach dieser ersten Anmeldung können Sie Dateien auf dem Computer ohne Benutzereingriff bezeichnen und schützen. Wenn Sie jedoch ein Dienst Konto verwenden, um Dateien zu bezeichnen und zu schützen, und sich dieses Dienst Konto nicht interaktiv anmelden kann, verwenden Sie den *onbehalfof* -Parameter mit "Set-aipauthentication":

1. Erstellen Sie eine Variable zum Speichern der Anmelde Informationen eines Active Directory Kontos, dem die Benutzerrechte Zuweisung zur interaktiven Anmeldung erteilt wird. Beispiel:
    
        $pscreds = Get-Credential "scv_scanner@contoso.com"

2. Führen Sie das Cmdlet "Set-aipauthentication" mit dem Parameter " *onbehalfof" aus* , und geben Sie als Wert die soeben erstellte Variable an. Zum Beispiel:
    
        Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f" -OnBehalfOf $pscreds


#### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication---preview-client"></a>So erstellen und konfigurieren Sie die Azure AD Anwendungen für den "Set-aipauthentication-Preview"-Client

Verwenden Sie das folgende Verfahren als Alternative Anweisungen nur, wenn Sie die Vorschauversion des Unified-Beschriftungs Clients installiert haben. 

Für diese Version des Clients müssen Sie für die Parameter " *AppID* " und " *appsecret* " für "Set-aipauthentication" eine neue APP-Registrierung erstellen. Wenn Sie ein Upgrade von einer früheren Version des Clients durchgeführt und eine APP-Registrierung für die vorherigen *webappid* -und *nativeappid* -Parameter erstellt haben, funktionieren Sie nicht mit dieser Version des Clients.

1. Melden Sie sich in einem neuen Browserfenster beim [Azure-Portal](https://portal.azure.com/) an.

2. Navigieren Sie für den Azure AD Mandanten, den Sie mit Azure Information Protection verwenden, zu **Azure Active Directory** > **Manage** > **App-Registrierungen**. 

3. Wählen Sie **+ neue Registrierung**aus. Geben Sie auf dem Blatt **Anwendung registrieren** die folgenden Werte an, und klicken Sie dann auf **registrieren**:

   - **Name**:`AIPv2OnBehalfOf`
        
        Wenn Sie möchten, können Sie auch einen anderen Namen angeben. Der Name muss pro Mandant eindeutig sein.
    
    - **Unterstützte Konto Typen**: **Nur Konten in diesem Organisations Verzeichnis**
    
    - **Umleitungs-URI (optional)** : **Web** und`https://localhost`

4. Kopieren Sie auf dem Blatt **AIPv2OnBehalfOf** den Wert für die **Anwendungs-ID (Client)** . Der Wert sieht in etwa wie im folgenden Beispiel `77c3c1c3-abf9-404e-8b2b-4652836c8c66`aus:. Dieser Wert wird für den *AppID* -Parameter verwendet, wenn Sie das Cmdlet "Set-aipauthentication" ausführen. Fügen Sie den Wert ein, und speichern Sie ihn später.

5. Wählen Sie auf dem Blatt **AIPv2OnBehalfOf** im Menü **Verwalten** die Option **Zertifikate & Geheimnissen**aus.

6. Wählen Sie auf dem Blatt **AIPv2OnBehalfOf-Zertifikate & Geheimnissen** im Abschnitt geheime **Client** Schlüssel die Option **+ neuer geheimer Client**Schlüssel aus.

7. Geben Sie unter **geheimen Client Schlüssel hinzufügen**Folgendes an, und wählen Sie dann **Hinzufügen**aus:
    
    - **Beschreibung**:`Azure Information Protection unified labeling client`
    - **Läuft**ab: Geben Sie die gewünschte Dauer an (1 Jahr, 2 Jahre oder läuft nie ab).

8. Kopieren Sie auf dem Blatt **AIPv2OnBehalfOf-Zertifikate & geheimen** Schlüssel im Abschnitt **Client Geheimnisse** die Zeichenfolge für den **Wert**. Diese Zeichenfolge sieht in etwa wie im folgenden `OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4`Beispiel aus:. Um sicherzustellen, dass Sie alle Zeichen kopieren, wählen Sie das Symbol aus, das **in die Zwischenablage kopiert**wird. 
    
    Es ist wichtig, dass diese Zeichenfolge gespeichert wird, da sie nicht erneut angezeigt wird und nicht abgerufen werden kann. Speichern Sie wie bei allen vertraulichen Informationen, die Sie verwenden, den gespeicherten Wert sicher, und beschränken Sie den Zugriff darauf.

9. Wählen Sie im Menü **Verwalten** die Option **API-Berechtigungen**aus.

10. Wählen Sie auf dem Blatt **AIPv2OnBehalfOf-API-Berechtigungen** die Option **+ Berechtigung hinzufügen**aus.

11. Wählen Sie auf dem Blatt **API-Berechtigungen anfordern** die Option **Azure Rights Management Services** aus, und wenn Sie zur Eingabe des Berechtigungs Typs aufgefordert werden, den Ihre Anwendung benötigt, wählen Sie **Anwendungs Berechtigungen**aus.

12. Erweitern **Sie für SELECT-Berechtigungen**den Eintrag **Inhalt** , und wählen Sie Folgendes aus:
    
    -  **Content. delegatedwriter** (immer erforderlich)
    -  **Content. Writer** (immer erforderlich)
    -  **Content. Superuser** (erforderlich, wenn das Administrator [Feature](../configure-super-users.md) erforderlich ist) 
    
    Die Administrator Funktion ermöglicht es dem Konto, Inhalte immer zu entschlüsseln. Zum erneuten schützen von Dateien und zum Überprüfen von Dateien, die von anderen geschützt wurden.

13. Wählen Sie **Berechtigungen hinzufügen**aus.

14. Wählen Sie auf dem Blatt **AIPv2OnBehalfOf-API-Berechtigungen** die Option **Administrator Zustimmung \<für *ihren Mandanten Namen* > erteilen aus** , und wählen Sie für die Bestätigungsaufforderung **Ja** aus.

Nachdem Sie die Registrierung dieser APP mit einem geheimen Schlüssel abgeschlossen haben, können Sie " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " mit den Parametern " *AppID*" und " *appsecret*" ausführen. Außerdem benötigen Sie Ihre Mandanten-ID. 

> [!TIP]
>Sie können Ihre Mandanten-ID schnell mithilfe Azure-Portal kopieren: **Azure Active Directory** >  > Verzeichnis-ID für die Verwaltung von Eigenschaften. > 

Aus unserem Beispiel mit der Mandanten-ID 9c11c87a-ac8b-46A3-8d5c-f 4d0b72ee29a:

`Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a"`

Wenn Sie diesen Befehl zum ersten Mal ausführen, werden Sie zur Anmeldung aufgefordert. Dadurch wird das Zugriffstoken für Ihr Konto erstellt und sicher unter „%localappdata%\Microsoft\MSIP“ gespeichert. Nach dieser ersten Anmeldung können Sie Dateien auf dem Computer ohne Benutzereingriff bezeichnen und schützen. Wenn Sie jedoch ein Dienst Konto verwenden, um Dateien zu bezeichnen und zu schützen, und sich dieses Dienst Konto nicht interaktiv anmelden kann, verwenden Sie den *onbehalfof* -Parameter mit "Set-aipauthentication":

1. Erstellen Sie eine Variable zum Speichern der Anmelde Informationen eines Active Directory Kontos, dem die Benutzerrechte Zuweisung zur interaktiven Anmeldung erteilt wird. Zum Beispiel:
    
        $pscreds = Get-Credential "scv_scanner@contoso.com"

2. Führen Sie das Cmdlet "Set-aipauthentication" mit dem Parameter " *onbehalfof" aus* , und geben Sie als Wert die soeben erstellte Variable an. Zum Beispiel:
    
        Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds


## <a name="next-steps"></a>Nächste Schritte
Wenn Sie in einer PowerShell-Sitzung eine Hilfe zu Cmdlets benötigen `Get-Help <cmdlet name> -online`, geben Sie ein. Beispiel: 

    Get-Help Set-AIPFileLabel -online

Weitere Informationen, die möglicherweise zur Unterstützung des Azure Information Protection-Clients erforderlich sind, finden Sie unter den folgenden Themen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)
