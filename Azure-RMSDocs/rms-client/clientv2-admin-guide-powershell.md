---
title: Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client
description: Anweisungen und Informationen für Administratoren zum Verwalten des Azure Information Protection Unified Bezeichnung-Clients mithilfe von PowerShell.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 10/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: da0d578d06081667e4d8a25be841c2feb2c1fbd5
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73561247"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-unified-client"></a>Administrator Handbuch: Verwenden von PowerShell mit dem Azure Information Protection Unified Client

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Wenn Sie den Azure Information Protection Unified Bezeichnung-Client installieren, werden PowerShell-Befehle automatisch installiert. Dadurch können Sie den Client durch Ausführen von Befehlen, die Sie in Skripts zur Automatisierung einfügen können, verwalten.

Die Cmdlets werden mit dem PowerShell-Modul **azureinformationprotection**installiert, das über Cmdlets für die Bezeichnung verfügt. Beispiele:

|Cmdlet für die Bezeichnung|Beispielsyntax|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|Für einen freigegebenen Ordner werden alle Dateien mit einer bestimmten Bezeichnung ermittelt.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|Überprüfen Sie bei einem freigegebenen Ordner die Dateiinhalte, und versehen Sie Dateien ohne Bezeichnung automatisch gemäß den von Ihnen festgelegten Bedingungen mit Bezeichnungen.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|Für einen freigegebenen Ordner wird eine bestimmte Bezeichnung auf alle Dateien ohne Bezeichnung angewendet.|
|[Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)|Bezeichnen Sie Dateien nicht interaktiv, z.B. durch Verwenden eines Skripts, das nach einem Zeitplan ausgeführt wird.|

> [!TIP]
> Um Cmdlets mit Pfadlängen zu verwenden, die mehr als 260 Zeichen umfassen, können Sie die folgende [Gruppenrichtlinieneinstellung](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/) verwenden, die ab Windows 10, Version 1607 verfügbar ist:<br /> **Richtlinie für den lokalen Computer** > **Computer Konfiguration** > **Administrative Vorlagen** > **alle Einstellungen** > **lange Win32-Pfade aktivieren** 
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

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Voraussetzung 1: Der Azure Rights Management-Dienst muss aktiviert werden.

Wenn Ihr Azure Information Protection Mandanten nicht aktiviert ist, lesen Sie die Anweisungen unter [[Aktivieren des Schutz Dienstanbieter von Azure Information Protection](../activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Voraussetzung 2: Den Schutz von Dateien für andere Benutzer mithilfe Ihres eigenen Kontos entfernen.

Typische Szenarien für das Entfernen des Schutzes von Dateien für andere Benutzer umfassen die Datenermittlung oder Datenwiederherstellung. Wenn Sie den Schutz mithilfe von Bezeichnungen anwenden, können Sie den Schutz durch Festlegen einer neuen Bezeichnung entfernen, durch die kein Schutz angewendet wird. Sie können dazu aber auch die Bezeichnung entfernen.

Sie müssen über ein Rights Management-Nutzungsrecht verfügen oder Administrator sein, um den Schutz von Dateien zu entfernen. Für die Datenermittlung oder Datenwiederherstellung wird in der Regel die Administratorfunktion verwendet. Informationen zum Aktivieren dieses Features und zum Konfigurieren Ihres Kontos als Administrator finden Sie unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](../configure-super-users.md).

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection

Sie können die Bezeichnungs-Cmdlets nicht interaktiv ausführen, indem Sie das Cmdlet [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) verwenden.

Wenn Sie die Cmdlets für die Bezeichnung ausführen, werden die Befehle in Ihrem eigenen Benutzerkontext in einer interaktiven PowerShell-Sitzung ausgeführt. Um diese unbeaufsichtigt auszuführen, verwenden Sie ein Windows-Konto, das sich interaktiv anmelden kann, und verwenden Sie ein Konto in Azure AD, das für den Delegierten Zugriff verwendet wird. Verwenden Sie zur Erleichterung der Verwaltung ein einzelnes Konto, das von Active Directory mit Azure AD synchronisiert wird.

Außerdem müssen Sie ein Zugriffs Token von Azure AD anfordern, mit dem Anmelde Informationen für den Delegierten Benutzer zum Authentifizieren bei Azure Information Protection festgelegt und gespeichert werden.

Auf dem Computer, auf dem das aipauthentication-Cmdlet ausgeführt wird, werden die Bezeichnungs Richtlinien mit Bezeichnungen, die dem Delegierten Benutzerkonto zugewiesen sind, mithilfe Ihres Bezeichnungs Verwaltungs Centers (z. b. Office 365 Security & Compliance Center heruntergeladen.

> [!NOTE]
> Wenn Sie für verschiedene Benutzer Bezeichnung-Richtlinien verwenden, müssen Sie möglicherweise eine neue Bezeichnungs Richtlinie erstellen, die alle ihre Bezeichnungen veröffentlicht und die Richtlinie nur für dieses Delegierte Benutzerkonto veröffentlicht.

Wenn das Token in Azure AD abläuft, müssen Sie das Cmdlet erneut ausführen, um ein neues Token abzurufen. Sie können das Zugriffs Token in Azure AD für ein Jahr, zwei Jahre oder so konfigurieren, dass es nie abläuft. Die Parameter für "Set-aipauthentication" verwenden Werte aus einem App-Registrierungsprozess in Azure AD, wie im nächsten Abschnitt beschrieben.

Für das Delegierte Benutzerkonto:

- Stellen Sie sicher, dass Sie über eine Bezeichnungs Richtlinie verfügen, die diesem Konto zugewiesen ist, und dass die Richtlinie die veröffentlichten Bezeichnungen enthält, die Sie verwenden möchten.

- Wenn dieses Konto Inhalt entschlüsseln muss, z. b. um Dateien erneut zu schützen und von anderen geschützte Dateien zu überprüfen, sollten Sie ihn als [Administrator für Azure Information Protection](../configure-super-users.md) festlegen und sicherstellen, dass die Administrator Funktion aktiviert ist.

- Wenn Sie [Onboarding](../activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) -Steuerelemente für eine stufenweise Bereitstellung implementiert haben, stellen Sie sicher, dass dieses Konto in den Onboarding-Steuerelementen enthalten ist, die Sie konfiguriert haben.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>So erstellen und konfigurieren Sie die Azure AD-Anwendungen für „Set-AIPAuthentication“

> [!IMPORTANT]
> Diese Anweisungen gelten für die aktuelle allgemein verfügbare Version des Unified-Bezeichnungs Clients und gelten auch für die Vorschauversion des Scanners für diesen Client.

"Set-aipauthentication" erfordert eine APP-Registrierung für die Parameter " *AppID* " und " *appsecret* ". Wenn Sie ein Upgrade von einer früheren Version des Clients durchgeführt und eine APP-Registrierung für die vorherigen *webappid* -und *nativeappid* -Parameter erstellt haben, funktionieren Sie nicht mit dem Unified-Bezeichnungs Client. Sie müssen eine neue APP-Registrierung wie folgt erstellen:

1. Melden Sie sich in einem neuen Browserfenster beim [Azure-Portal](https://portal.azure.com/) an.

2. Navigieren Sie für den Azure AD Mandanten, den Sie mit Azure Information Protection verwenden, zu **Azure Active Directory** > **Verwalten** Sie > **App-Registrierungen**. 

3. Wählen Sie **+ neue Registrierung**aus. Geben Sie im Bereich **Anwendung registrieren** die folgenden Werte an, und klicken Sie dann auf **registrieren**:

   - **Name**: `AIP-DelegatedUser`
        
        Wenn Sie möchten, können Sie auch einen anderen Namen angeben. Der Name muss pro Mandant eindeutig sein.
    
    - **Unterstützte Konto Typen**: **nur Konten in diesem Organisations Verzeichnis**
    
    - **Umleitungs-URI (optional)** : **Web** und `https://localhost`

4. Kopieren Sie im Bereich **AIP-delegateduser** den Wert für die **Anwendungs-ID (Client)** . Der Wert sieht in etwa wie im folgenden Beispiel aus: `77c3c1c3-abf9-404e-8b2b-4652836c8c66`. Dieser Wert wird für den *AppID* -Parameter verwendet, wenn Sie das Cmdlet "Set-aipauthentication" ausführen. Fügen Sie den Wert ein, und speichern Sie ihn später.

5. Wählen Sie in der Rand Leiste die Option **Verwalten** > **Zertifikate & Geheimnissen**aus.

6. Wählen Sie im Bereich **AIP-delegateduser-Zertifikate &** geheimen Schlüssel im Bereich geheime **Client** Schlüssel die Option **+ neuer geheimer Client**Schlüssel aus.

7. Geben Sie unter **geheimen Client Schlüssel hinzufügen**Folgendes an, und wählen Sie dann **Hinzufügen**aus:
    
    - **Beschreibung**: `Azure Information Protection unified labeling client`
    - **Läuft**ab: Geben Sie die gewünschte Dauer an (1 Jahr, 2 Jahre oder läuft nie ab).

8. Kopieren Sie im Bereich **AIP-delegateduser--Zertifikate & geheimen** Schlüssel im Abschnitt geheime **Client** Schlüssel die Zeichenfolge für den **Wert**. Diese Zeichenfolge sieht in etwa wie im folgenden Beispiel aus: `OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4`. Um sicherzustellen, dass Sie alle Zeichen kopieren, wählen Sie das Symbol aus, das **in die Zwischenablage kopiert**wird. 
    
    Es ist wichtig, dass diese Zeichenfolge gespeichert wird, da sie nicht erneut angezeigt wird und nicht abgerufen werden kann. Speichern Sie wie bei allen vertraulichen Informationen, die Sie verwenden, den gespeicherten Wert sicher, und beschränken Sie den Zugriff darauf.

9. Wählen Sie in der Rand Leiste die Option **Verwalten** > **API-Berechtigungen**aus.

10. Wählen Sie im Bereich **AIP-delegateduser-API-Berechtigungen** die Option **+ Berechtigung hinzufügen**aus.

11. Stellen Sie sicher, dass Sie auf der Registerkarte " **API-Berechtigungen** " auf der Registerkarte " **Microsoft-APIs** " die Option **Azure Rights Management Services**auswählen. Wenn Sie aufgefordert werden, den für Ihre Anwendung erforderlichen Berechtigungs Typen einzugeben, wählen Sie **Anwendungs Berechtigungen**aus.

12. Erweitern **Sie für SELECT-Berechtigungen**den Eintrag **Inhalt** , und wählen Sie Folgendes aus:
    
    -  **Content. delegatedreader** 
    -  **Content. delegatedwriter**

13. Wählen Sie **Berechtigungen hinzufügen**aus.

14. Wählen Sie im Bereich **AIP-delegateduser-API-Berechtigungen** die Option **+ Berechtigung erneut hinzufügen** aus.

15. Wählen Sie im Bereich " **AIP-Berechtigungen anfordern** " die APIs aus, die **Meine Organisation verwendet**, und suchen Sie nach **Microsoft Information Protection Sync Service**.

16. Wählen Sie im Bereich **API-Berechtigungen anfordern** die Option **Anwendungs Berechtigungen**aus.

17. Erweitern **Sie für SELECT-Berechtigungen**den Eintrag **unifedpolicy** , und wählen Sie Folgendes aus:
    
    -  **Unifedpolicy. Tenant. Read**

18. Wählen Sie **Berechtigungen hinzufügen**aus.

19. Wählen Sie im Bereich **AIP-delegateduser-API-Berechtigungen** die Option **Administrator Zustimmung für \<*Ihres Mandanten namens* gewähren aus>** und klicken Sie für die Bestätigungsaufforderung auf **Ja** .
    
    Die API-Berechtigungen sollten wie folgt aussehen:
    
    ![API-Berechtigungen für die registrierte app in Azure AD](../media/api-permissions-app.png)

Nachdem Sie die Registrierung dieser APP mit einem geheimen Schlüssel abgeschlossen haben, können Sie " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " mit den Parametern " *AppID*" und " *appsecret*" ausführen. Außerdem benötigen Sie Ihre Mandanten-ID. 

> [!TIP]
>Sie können Ihre Mandanten-ID schnell kopieren, indem Sie Azure-Portal: **Azure Active Directory** >  ** > Eigenschaften** > **Verzeichnis-ID** **Verwalten** .

1. Öffnen Sie Windows PowerShell mit der **Option als Administrator ausführen**. 

2. Erstellen Sie in ihrer PowerShell-Sitzung eine Variable zum Speichern der Anmelde Informationen für das Windows-Benutzerkonto, das nicht interaktiv ausgeführt wird. Wenn Sie z. b. ein Dienst Konto für den Scanner erstellt haben:
    
        $pscreds = Get-Credential "CONTOSO\srv-scanner"
    
    Sie werden zur Angabe des Kennworts für dieses Konto aufgefordert.

2. Führen Sie das Cmdlet "Set-aipauthentication" mit dem Parameter " *onbehalfof" aus* , und geben Sie als Wert die soeben erstellte Variable an. Geben Sie außerdem Ihre APP-Registrierungs Werte, Ihre Mandanten-ID und den Namen des Delegierten Benutzerkontos in Azure AD an. Beispiele:
    
        Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -DelegatedUser scanner@contoso.com -OnBehalfOf $pscreds

> [!NOTE]
> Wenn der Computer nicht über Internet Zugriff verfügen kann, ist es nicht erforderlich, die app in Azure AD zu erstellen und Set-aipauthentication auszuführen. Befolgen Sie stattdessen die Anweisungen für nicht [verbundene Computer](clientv2-admin-guide-customizations.md#support-for-disconnected-computers).  

## <a name="next-steps"></a>Nächste Schritte
Wenn Sie in einer PowerShell-Sitzung die Cmdlet-Hilfe benötigen, geben Sie `Get-Help <cmdlet name> -online`ein. Beispiele: 

    Get-Help Set-AIPFileLabel -online

Weitere Informationen, die möglicherweise zur Unterstützung des Azure Information Protection-Clients erforderlich sind, finden Sie unter den folgenden Themen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)
