---
title: Verwenden von PowerShell mit dem Azure Information Protection unified bezeichnungs-client
description: Anweisungen und Informationen für Administratoren des Azure Information Protection unified bezeichnungs-Clients mithilfe von PowerShell verwalten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: f90697e1e4df90ab8876843b45957b93c8ba8b07
ms.sourcegitcommit: a26e4e50165107efd51280b5c621dfe74be51a7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67236882"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-unified-client"></a>Administratorhandbuch: Mithilfe von PowerShell mit dem einheitlichen Azure Information Protection-client

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Wenn Sie den Azure Information Protection unified bezeichnungs-Client installieren, werden PowerShell-Befehle automatisch installiert. Dadurch können Sie den Client durch Ausführen von Befehlen, die Sie in Skripts zur Automatisierung einfügen können, verwalten.

Die Cmdlets sind mit dem PowerShell-Modul installiert **"azureinformationprotection"** , das Cmdlets für die Bezeichnung wurde. Zum Beispiel:

|Cmdlet für die Bezeichnung|Beispielsyntax|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|Für einen freigegebenen Ordner werden alle Dateien mit einer bestimmten Bezeichnung ermittelt.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|Überprüfen Sie bei einem freigegebenen Ordner die Dateiinhalte, und versehen Sie Dateien ohne Bezeichnung automatisch gemäß den von Ihnen festgelegten Bedingungen mit Bezeichnungen.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|Für einen freigegebenen Ordner wird eine bestimmte Bezeichnung auf alle Dateien ohne Bezeichnung angewendet.|
|[Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)|Bezeichnen Sie Dateien interaktiv mit einem anderen Benutzerkonto auf Ihre eigenen.|

> [!TIP]
> Um Cmdlets mit Pfadlängen zu verwenden, die mehr als 260 Zeichen umfassen, können Sie die folgende [Gruppenrichtlinieneinstellung](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/) verwenden, die ab Windows 10, Version 1607 verfügbar ist:<br /> **Lokale Computerrichtlinie** > **Computerkonfiguration** > **Administrative Vorlagen** > **alle Einstellungen**  >  **Ermöglichen Win32 lange Pfade** 
> 
> Bei Windows Server 2016 können Sie die gleiche Gruppenrichtlinieneinstellung verwenden, wenn Sie die neuesten administrativen Vorlagen (ADMX-Dateien) für Windows 10 installieren.
>
> Weitere Informationen finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

Dieses Modul installiert **\ProgramFiles (x86) \Microsoft Azure Information Protection** und fügt diesen Ordner der Systemvariablen **PSModulePath** hinzu. Die DLL-Datei für dieses Modul lautet **AIP.dll**.

> [!IMPORTANT]
> Das Modul "azureinformationprotection" unterstützt nicht das Konfigurieren erweiterter Einstellungen für die Bezeichnungen oder Richtlinien für die Bezeichnung. Für diese Einstellungen benötigen Sie die Office 365 Security & Compliance Center und PowerShell. Weitere Informationen finden Sie unter [benutzerdefinierte Konfigurationen für die Azure Information Protection unified bezeichnungs Client](clientv2-admin-guide-customizations.md).

### <a name="prerequisites-for-using-the-azureinformationprotection-module"></a>Voraussetzungen für die Verwendung des Moduls "azureinformationprotection"

Zusätzlich zu den Voraussetzungen für die Installation des Moduls "azureinformationprotection" gibt es zusätzliche Anforderungen an, wenn Sie die bezeichnungs-Cmdlets für Azure Information Protection verwenden:

1. Der Azure Rights Management-Dienst muss aktiviert werden.

2. So entfernen Sie den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos: 

    - Die Administratorfunktion muss für Ihre Organisation aktiviert werden. Zudem muss Ihr Konto als Administrator für Azure Rights Management konfiguriert sein.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Voraussetzung 1: Der Azure Rights Management-Dienst muss aktiviert sein

Wenn es sich bei Ihrem Azure Information Protection-Mandanten nicht aktiviert ist, um den Schutz anzuwenden, lesen Sie die Anweisungen für [Aktivieren von Azure Rights Management](../activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Voraussetzung 2: Sie entfernen den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos

Typische Szenarien für das Entfernen des Schutzes von Dateien für andere Benutzer umfassen die Datenermittlung oder Datenwiederherstellung. Wenn Sie den Schutz mithilfe von Bezeichnungen anwenden, können Sie den Schutz durch Festlegen einer neuen Bezeichnung entfernen, durch die kein Schutz angewendet wird. Sie können dazu aber auch die Bezeichnung entfernen.

Sie müssen über ein Rights Management-Nutzungsrecht verfügen oder Administrator sein, um den Schutz von Dateien zu entfernen. Für die Datenermittlung oder Datenwiederherstellung wird in der Regel die Administratorfunktion verwendet. Informationen zum Aktivieren dieses Feature und zum Konfigurieren Ihres Kontos als Administrator finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](../configure-super-users.md).

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection

Hinweis: Die Informationen in diesem Abschnitt sind für die Preview-Version nur aus den Azure Information Protection unified bezeichnungs-Client.

Sie können die Bezeichnungs-Cmdlets nicht interaktiv ausführen, indem Sie das Cmdlet **Set-AIPAuthentication** verwenden.

Wenn Sie die Cmdlets für die Bezeichnung ausführen, werden die Befehle in Ihrem eigenen Benutzerkontext in einer interaktiven PowerShell-Sitzung ausgeführt. Um sie unbeaufsichtigt auszuführen, erstellen Sie für diesen Zweck ein neues Azure AD-Benutzerkonto. Führen Sie dann im Kontext dieses Benutzers das Cmdlet „Set-AIPAuthentication“ zum Festlegen und Speichern von Anmeldeinformationen mithilfe eines Azure AD-Zugriffstokens aus. Dieses Benutzerkonto wird dann authentifiziert und einem Bootstrapping für den Schutzdienst von Azure Information Protection. Das Konto heruntergeladen, die Azure Information Protection-Richtlinie und alle schutzvorlagen, die die Bezeichnungen zu verwenden.

> [!NOTE]
> Wenn Sie [bereichsbezogene Richtlinien](../configure-policy-scope.md) verwenden, denken Sie bitte daran, dass Sie dieses Konto möglicherweise zu Ihren bereichsbezogenen Richtlinien hinzufügen müssen.

Bei der ersten Ausführung dieses Cmdlets werden Sie aufgefordert, sich bei Azure Information Protection anzumelden. Geben Sie den Benutzernamen und das Kennwort, die Sie für das unbeaufsichtigte Konto erstellt haben. Danach kann dieses Konto klicken Sie dann die bezeichnungs-Cmdlets nicht interaktiv ausführen bis zum Ablaufen des Authentifizierungstokens in Azure AD. 

Das Konto muss für das Benutzerkonto zum ersten Mal interaktiv anmelden kann, verfügen die **lokal anmelden** rechts von Benutzerrechten. Diese Berechtigung ist Benutzerkonten standardmäßig zugewiesen, aber Ihre Unternehmensrichtlinien lassen diese Konfiguration für Dienstkonten unter Umständen nicht zu. Wenn dies der Fall ist, können Sie ausführen, dass Set-AIPAuthentication, mit der *"onbehalfof"* an, damit die Authentifizierung ohne die anmeldeaufforderung abgeschlossen wird.

Wenn das in Azure AD-Token abläuft, führen Sie das Cmdlet erneut aus, um ein neues Token abzurufen.

Wenn Sie dieses Cmdlet ohne Parameter ausführen, erhält das Konto ein Zugriffstoken, das 90 Tage oder bis zum Ablauf des Kennworts gültig ist.  

Um zu steuern, wann das Zugriffstoken abläuft, führen Sie dieses Cmdlet mit Parametern aus. Diese Konfiguration ermöglicht Ihnen, konfigurieren das Zugriffstoken in Azure AD für ein Jahr beträgt zwei Jahre oder nie abläuft. Sie benötigen zwei Anwendungen, die in Azure Active Directory registriert: eine **Web-App-/API**-Anwendung und eine **native Anwendung**. Die Parameter für "Set-aipauthentication" verwenden Sie Werte aus diesen Anwendungen.

Nachdem Sie dieses Cmdlet ausgeführt haben, können Sie die bezeichnungs-Cmdlets im Kontext des Dienstkontos ausführen, die Sie erstellt haben.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>So erstellen und konfigurieren Sie die Azure AD-Anwendungen für „Set-AIPAuthentication“

1. Melden Sie sich in einem neuen Browserfenster beim [Azure-Portal](https://portal.azure.com/) an.

2. Für Azure AD-Mandanten, die Sie mit Azure Information Protection verwenden, wechseln Sie zu **Azure Active Directory** > **verwalten** > **App-Registrierungen**. 

3. Wählen Sie **+ Registrierung einer neuen**, um Ihre Web-app/API-Anwendung zu erstellen. Auf der **Registrieren einer Anwendung** auf dem Blatt die folgenden Werte fest, und klicken Sie dann auf **registrieren**:

   - **Namen**: `AIPOnBehalfOf`
        
        Wenn Sie möchten, können Sie auch einen anderen Namen angeben. Der Name muss pro Mandant eindeutig sein.
    
    - **Unterstützte Kontotypen**: **Konten in nur diese Organisationsverzeichnis**
    
    - **Umleitungs-URI (optional)** : **Web** und `http://localhost`

4. Auf der **AIPOnBehalfOf** auf dem Blatt, kopieren Sie den Wert für die **ID der Anwendung (Client)** . Der Wert sieht in etwa wie im folgenden Beispiel: `57c3c1c3-abf9-404e-8b2b-4652836c8c66`. Dieser Wert wird verwendet, für die *WebAppId* Parameter an, wenn Sie das Cmdlet "Set-AIPAuthentication" ausführen. Fügen Sie ein, und speichern Sie den Wert zur späteren Bezugnahme.

5. Fügen Sie auf die **AIPOnBehalfOf** Blatt aus der **verwalten** , wählen Sie im Menü **Authentifizierung**.

6. Auf der **AIPOnBehalfOf - Authentifizierung** Blatt in der **Erweiterte Einstellungen** wählen Sie im Abschnitt der **ID-Token** Kontrollkästchen, und wählen Sie dann **Speichern**.

7. Fügen Sie auf die **AIPOnBehalfOf - Authentifizierung** Blatt aus der **verwalten** , wählen Sie im Menü **Zertifikate und Geheimnisse**.

8. Auf der **AIPOnBehalfOf - Zertifikate und Geheimnisse** Blatt in der **geheime Clientschlüssel** wählen Sie im Abschnitt **+ neuer geheimer Clientschlüssel**. 

9. Für **fügen Sie einen geheimen Clientschlüssel**, geben Sie Folgendes ein, und wählen Sie dann **hinzufügen**:
    
    - **Beschreibung**: `Azure Information Protection client`
    - **Läuft ab**: Geben Sie den gewünschten Dauer (1 Jahr 2 Jahre oder nie abläuft)

9. Auf der **AIPOnBehalfOf - Zertifikate und Geheimnisse** auf dem Blatt in der **geheime Clientschlüssel** kopieren Sie die Zeichenfolge für die **Wert**. Diese Zeichenfolge sieht in etwa wie im folgenden Beispiel: `+LBkMvddz?WrlNCK5v0e6_=meM59sSAn`. Um sicherzustellen, dass Sie alle Zeichen kopieren, wählen Sie das Symbol, um **in Zwischenablage kopieren**. 
    
    Es ist wichtig, dass diese Zeichenfolge gespeichert wird, da sie nicht erneut angezeigt wird und nicht abgerufen werden kann. Wie bei vertraulichen Informationen, die Sie verwenden speichern Sie den gespeicherten Wert sicher zu, und beschränken Sie den Zugriff auf diese.

10. Fügen Sie auf die **AIPOnBehalfOf - Zertifikate und Geheimnisse** Blatt aus der **verwalten** , wählen Sie im Menü **eine API verfügbar machen**.

11. Auf der **AIPOnBehalfOf - machen eine API** Blatt **festgelegt** für die **Anwendungs-ID-URI** Option, und klicken Sie in der **Anwendungs-ID-URI** Wert Ändern Sie **api** zu **http**. Diese Zeichenfolge sieht in etwa wie im folgenden Beispiel: `http://d244e75e-870b-4491-b70d-65534953099e`. 
    
    Wählen Sie **Speichern** aus.

12. Auf der **AIPOnBehalfOf - machen eine API** Blatt **und Hinzufügen eines Bereichs**.

13. Auf der **Hinzufügen eines Bereichs** auf dem Blatt Folgendes angeben, verwenden Sie die vorgeschlagenen Zeichenfolgen als Beispiele und wählen Sie dann **Bereich hinzufügen**:
    - **Bereichsname**: `user-impersonation`
    - **Wer kann zustimmen?** : **Administratoren und Benutzer**
    - **Anzeigename der administratorzustimmung**: `Access Azure Information Protection scanner`
    - **Beschreibung der administratorzustimmung**: `Allow the application to access the scanner for the signed-in user`
    - **Anzeigename der benutzerzustimmung**: `Access Azure Information Protection scanner`
    - **Beschreibung der benutzerzustimmung**: `Allow the application to access the scanner for the signed-in user`
    - **Status**: **Aktiviert** (Standard)

14. Auf der **AIPOnBehalfOf - machen eine API** Blatt schließen Sie dieses Blatt.

15. Auf der **App-Registrierungen** Blatt **+ Registrierung einer neuen Anwendung** jetzt Ihre native Anwendung zu erstellen.

16. Auf der **Registrieren einer Anwendung** auf dem Blatt, geben Sie die folgenden Einstellungen, und wählen Sie dann **registrieren**:
    - **Namen**: `AIPClient`
    - **Unterstützte Kontotypen**: **Konten in nur diese Organisationsverzeichnis**
    - **Umleitungs-URI (optional)** : **Öffentliche Clients (mobile und desktop)** und `http://localhost`

17. Auf der **AIPClient** auf dem Blatt, kopieren Sie den Wert der **ID der Anwendung (Client)** . Der Wert sieht in etwa wie im folgenden Beispiel: `8ef1c873-9869-4bb1-9c11-8313f9d7f76f`. 
    
    Dieser Wert wird für den NativeAppId-Parameter verwendet, wenn Sie das Cmdlet "Set-AIPAuthentication" ausführen. Fügen Sie ein, und speichern Sie den Wert zur späteren Bezugnahme.

18. Fügen Sie auf die **AIPClient** Blatt aus der **verwalten** , wählen Sie im Menü **Authentifizierung**.

19. Auf der **AIPClient - Authentifizierung** auf dem Blatt, geben Sie Folgendes, und wählen Sie dann **speichern**:
    - In der **Erweiterte Einstellungen** wählen Sie im Abschnitt **ID-Token**.
    - In der **Standard Clienttyp** wählen Sie im Abschnitt **Ja**.

20. Fügen Sie auf die **AIPClient - Authentifizierung** Blatt aus der **verwalten** , wählen Sie im Menü **API-Berechtigungen**.

21. Auf der **AIPClient - Berechtigungen** Blatt **und Hinzufügen einer Berechtigung**.

22. Auf der **Anfordern von API-Berechtigungen** Blatt **Meine APIs**.

23. In der **wählen Sie eine API** Abschnitt **APIOnBehalfOf**, wählen Sie dann das Kontrollkästchen für **Benutzeridentitätswechsel**, wie die Berechtigung. Wählen Sie **Berechtigungen hinzufügen**. 

24. Auf der **API-Berechtigungen** auf dem Blatt in der **zuzustimmen** wählen Sie im Abschnitt **erteilen der Zustimmung des Administrators für \< *Ihren Mandantennamen* >**  , und wählen Sie **Ja** für die bestätigungsaufforderung.

Sie haben soeben die Konfiguration der beiden Apps abgeschlossen und verfügen nun über die Werte, die Sie zum Ausführen von [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) mit den Parametern *WebAppId*, *WebAppKey* und *NativeAppId* benötigen. In unseren Beispielen:

`Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"`

Führen Sie diesen Befehl im Kontext des Kontos aus, das die Dokumente ohne Benutzereingriff bezeichnet und schützt. Beispiel: Ein Benutzerkonto für Ihre PowerShell-Skripts oder das Dienstkonto zum Ausführen der Azure Information Protection-Überprüfung.

Wenn Sie diesen Befehl zum ersten Mal ausführen, werden Sie zur Anmeldung aufgefordert. Dadurch wird das Zugriffstoken für Ihr Konto erstellt und sicher unter „%localappdata%\Microsoft\MSIP“ gespeichert. Nach dieser ersten Anmeldung können Sie Dateien auf dem Computer ohne Benutzereingriff bezeichnen und schützen. Allerdings verwenden, wenn Sie ein Dienstkonto an, und Schützen von Dateien und dieses Dienstkonto nicht interaktiv anmelden kann, die *"onbehalfof"* Parameter mit der Set-AIPAuthentication:

1. Erstellen Sie eine Variable, um die Anmeldeinformationen des Active Directory-Konto zu speichern, die die Zuordnung der Benutzerrechte für die interaktive Anmeldung gewährt wird. Zum Beispiel:
    
        $pscreds = Get-Credential "scv_scanner@contoso.com"

2. Führen Sie das Cmdlet "Set-AIPAuthentication" mit der *"onbehalfof"* Parameter, der als Wert angibt, die Variable, die Sie gerade erstellt haben. Zum Beispiel:
    
        Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f" -OnBehalfOf $pscreds

## <a name="next-steps"></a>Nächste Schritte
Für ein Cmdlet-Hilfe, wenn Sie in einer PowerShell-Sitzung sind `Get-Help <cmdlet name> -online`. Zum Beispiel: 

    Get-Help Set-AIPFileLabel -online

Weitere Informationen, die möglicherweise zur Unterstützung des Azure Information Protection-Clients erforderlich sind, finden Sie unter den folgenden Themen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)
