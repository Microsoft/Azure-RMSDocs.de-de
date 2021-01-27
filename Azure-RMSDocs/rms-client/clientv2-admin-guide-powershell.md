---
title: Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client
description: Anweisungen und Informationen für Administratoren zum Verwalten des Azure Information Protection Unified Bezeichnung-Clients mithilfe von PowerShell.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 01/14/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 2a4bd98e22789e71cf090efb4c83a2a1ba000df2
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809919"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-unified-client"></a>Administrator Handbuch: Verwenden von PowerShell mit dem Azure Information Protection Unified Client

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen unter [AIP und ältere Windows-und Office-Versionen](../known-issues.md#aip-and-legacy-windows-and-office-versions).*
>
>***Relevant für**: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie im [klassischen Client Administrator Handbuch](client-admin-guide-powershell.md). *

Wenn Sie den Azure Information Protection Unified Bezeichnung-Client installieren, werden PowerShell-Befehle automatisch als Teil des Moduls " [azureinformationprotection](/powershell/module/azureinformationprotection) " mit Cmdlets für die Bezeichnung installiert. 

Mit dem **azureinformationprotection** -Modul können Sie den-Client verwalten, indem Sie Befehle für Automatisierungs Skripts ausführen.

Beispiel:

- [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus): Ruft die Azure Information Protection Bezeichnung und die Schutz Informationen für eine angegebene Datei oder Dateien ab.
- [Set-aipfileclassification](/powershell/module/azureinformationprotection/set-aipfileclassification): scannt eine Datei, um automatisch eine Azure Information Protection Bezeichnung für eine Datei festzulegen, gemäß den Bedingungen, die in der Richtlinie konfiguriert sind.
- [Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel): legt eine Azure Information Protection Bezeichnung für eine Datei fest oder entfernt Sie und legt den Schutz entsprechend der Bezeichnungs Konfiguration oder benutzerdefinierten Berechtigungen fest oder entfernt diesen.
- [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication): legt die Anmelde Informationen für die Authentifizierung für den Azure Information Protection Client fest.

Das Modul " **azureinformationprotection** " ist im Ordner " **\ProgramFiles (x86) \Microsoft Azure Information Protection** " installiert und fügt diesen Ordner dann der Systemvariablen " **psmodulepath** " hinzu. Die DLL-Datei für dieses Modul lautet **AIP.dll**.

> [!IMPORTANT]
> Das **azureinformationprotection** -Modul unterstützt das Konfigurieren erweiterter Einstellungen für Bezeichnungen oder Bezeichnungs Richtlinien nicht. 
>
>Für diese Einstellungen benötigen Sie das Office 365 Security & Compliance Center PowerShell. Weitere Informationen finden Sie unter [benutzerdefinierte Konfigurationen für den Azure Information Protection Unified Bezeichnung-Client](clientv2-admin-guide-customizations.md).

> [!TIP]
> Um Cmdlets mit Pfadlängen zu verwenden, die mehr als 260 Zeichen umfassen, können Sie die folgende [Gruppenrichtlinieneinstellung](/archive/blogs/jeremykuhne/net-4-6-2-and-long-paths-on-windows-10) verwenden, die ab Windows 10, Version 1607 verfügbar ist:<br /> **Richtlinie**  >  für lokale Computer **Computer Konfiguration**  >  **Administrative Vorlagen**  >  **Alle Einstellungen**  >  **Lange Win32-Pfade aktivieren** 
> 
> Bei Windows Server 2016 können Sie die gleiche Gruppenrichtlinieneinstellung verwenden, wenn Sie die neuesten administrativen Vorlagen (ADMX-Dateien) für Windows 10 installieren.
>
> Weitere Informationen finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

## <a name="prerequisites-for-using-the-azureinformationprotection-module"></a>Voraussetzungen für die Verwendung des Moduls "azureinformationprotection"

Zusätzlich zu den Voraussetzungen für die Installation des Moduls " **azureinformationprotection** " müssen Sie die folgenden zusätzlichen Voraussetzungen erfüllen, wenn Sie die Bezeichnungs-Cmdlets für Azure Information Protection verwenden:

- **Der Azure Rights Management-Dienst muss aktiviert werden**.

    Wenn Ihr Azure Information Protection Mandanten nicht aktiviert ist, lesen Sie die Anweisungen zum [Aktivieren des Schutz Dienstanbieter von Azure Information Protection](../activate-service.md).

- **So entfernen Sie den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos**:

    - Die [Administrator](../configure-super-users.md) Funktion muss für Ihre Organisation aktiviert sein.
    - Ihr Konto muss als Administrator für Azure Rights Management konfiguriert werden.

    Beispielsweise können Sie den Schutz für andere Personen für die Daten Ermittlung oder-Wiederherstellung aufheben. Wenn Sie den Schutz mithilfe von Bezeichnungen anwenden, können Sie diesen Schutz entfernen, indem Sie eine neue Bezeichnung festlegen, die keinen Schutz anwendet, oder Sie können die Bezeichnung entfernen.

    Um den Schutz zu entfernen, verwenden Sie das Cmdlet [Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel) mit dem Parameter *removeprotection* . Die Funktion zum Entfernen des Schutzes ist standardmäßig deaktiviert und muss zunächst mithilfe des Cmdlets " [Set-labelpolicy](/powershell/module/azureinformationprotection/set-labelpolicy) " aktiviert werden.

## <a name="rms-to-unified-labeling-cmdlet-mapping"></a>Zuordnung von RMS zu Unified-Beschriftungs-Cmdlets

Wenn Sie von Azure RMS migriert haben, beachten Sie, dass die RMS-bezogenen Cmdlets für die Verwendung in vereinheitlichter Bezeichnung veraltet sind. 

Einige der Legacy-Cmdlets wurden durch neue Cmdlets für die vereinheitlichte Bezeichnung ersetzt. Wenn Sie z. b. **New-rmsprotectionlicense** mit dem RMS-Schutz verwendet und zu Unified-Bezeichnung migriert haben, verwenden Sie stattdessen **New-aipcustomrights** .

In der folgenden Tabelle sind RMS-bezogene Cmdlets mit den aktualisierten Cmdlets für die vereinheitlichte Bezeichnung zugeordnet:

|RMS-Cmdlet  |Unified-Bezeichnung-Cmdlet  |
|---------|---------|
|[Get-rmsfilestatus](/powershell/module/azureinformationprotection/get-rmsfilestatus)     |  [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)        |
|[Get-rmsserver](/powershell/module/azureinformationprotection/get-rmsserver)     |  Nicht relevant für vereinheitlichte Bezeichnung.      |
|[Get-rmsserverauthentication](/powershell/module/azureinformationprotection/get-rmsserverauthentication)      |   [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)       |
|[Clear-rmsauthentication](/powershell/module/azureinformationprotection/clear-rmsauthentication)     | [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)       |
|[Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication)     |  [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)      |
|[Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate)     |       Nicht relevant für vereinheitlichte Bezeichnung  |
|[New-rmsprotectionlicense](/powershell/module/azureinformationprotection/new-rmsprotectionlicense)     |  [New-aipcustom-Berechtigungen](/powershell/module/azureinformationprotection/new-aipcustompermissions)und [Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel)mit dem **customberechtigungs** -Parameter      |
|[Schützen-rmsfile](/powershell/module/azureinformationprotection/protect-rmsfile) |[Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel)mit dem Parameter " **removeprotection** " |
| | |


## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection

Wenn Sie die Cmdlets für die Bezeichnung ausführen, werden die Befehle in Ihrem eigenen Benutzerkontext in einer interaktiven PowerShell-Sitzung ausgeführt.

Weitere Informationen finden Sie unter

- [Erforderliche Komponenten für die unbeaufsichtigte Ausführung von AIP-Cmdlets](#prerequisites-for-running-aip-labeling-cmdlets-unattended)
- [Erstellen und Konfigurieren von Azure AD Anwendungen für "Set-aipauthentication"](#create-and-configure-azure-ad-applications-for-set-aipauthentication)
- [Ausführen des Set-AIPAuthentication Cmdlets](#running-the-set-aipauthentication-cmdlet)

> [!NOTE]
> Wenn der Computer nicht über Internet Zugriff verfügen kann, muss die APP nicht in Azure AD erstellt und das Cmdlet " **Set-aipauthentication** " ausgeführt werden. Befolgen Sie stattdessen die Anweisungen für nicht [verbundene Computer](clientv2-admin-guide-customizations.md#support-for-disconnected-computers).  

### <a name="prerequisites-for-running-aip-labeling-cmdlets-unattended"></a>Erforderliche Komponenten für die unbeaufsichtigte Ausführung von AIP-Cmdlets

Wenn Sie Azure Information Protection Bezeichnungs-Cmdlets unbeaufsichtigt ausführen möchten, verwenden Sie die folgenden Zugriffs Details:

- **Ein Windows-Konto** , das sich interaktiv anmelden kann.

- **Ein Azure AD Konto** für den Delegierten Zugriff. Verwenden Sie zur Erleichterung der Verwaltung ein einzelnes Konto, das von Active Directory mit Azure AD synchronisiert wird.

    Für das Delegierte Benutzerkonto:

    |Anforderung  |Details  |
    |---------|---------|
    |**Bezeichnungs Richtlinie**     |  Stellen Sie sicher, dass Sie über eine Bezeichnungs Richtlinie verfügen, die diesem Konto zugewiesen ist, und dass die Richtlinie die veröffentlichten Bezeichnungen enthält, die Sie verwenden möchten.   <br><br>Wenn Sie für verschiedene Benutzer Bezeichnung-Richtlinien verwenden, müssen Sie möglicherweise eine neue Bezeichnungs Richtlinie erstellen, die alle ihre Bezeichnungen veröffentlicht und die Richtlinie nur für dieses Delegierte Benutzerkonto veröffentlicht.    |
    |**Entschlüsseln von Inhalten**     |    Wenn dieses Konto Inhalt entschlüsseln muss, z. b. um Dateien erneut zu schützen und von anderen geschützte Dateien zu überprüfen, sollten Sie ihn als [Administrator für Azure Information Protection](../configure-super-users.md) festlegen und sicherstellen, dass die Administrator Funktion aktiviert ist.     |
    |**Onboarding-Steuerelemente**     |    Wenn Sie [Onboarding](../activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) -Steuerelemente für eine stufenweise Bereitstellung implementiert haben, stellen Sie sicher, dass dieses Konto in den Onboarding-Steuerelementen enthalten ist, die Sie konfiguriert haben.     |
    |     |         |

- **Ein Azure AD Zugriffs Token**, mit dem Anmelde Informationen für den Delegierten Benutzer festgelegt und gespeichert werden, um sich bei Azure Information Protection zu authentifizieren. Wenn das Token in Azure AD abläuft, müssen Sie das Cmdlet erneut ausführen, um ein neues Token abzurufen. 

    Die Parameter für " **Set-aipauthentication** " verwenden Werte aus einem App-Registrierungsprozess in Azure AD. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Azure AD Anwendungen für "Set-aipauthentication](#create-and-configure-azure-ad-applications-for-set-aipauthentication)".

Führen Sie die Bezeichnungs-Cmdlets nicht interaktiv aus, indem Sie zunächst das Cmdlet " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " ausführen.

Auf dem Computer, auf dem das **aipauthentication** -Cmdlet ausgeführt wird, wird die Bezeichnungs Richtlinie heruntergeladen, die Ihrem Delegierten Benutzerkonto in Ihrem Beschriftungs Verwaltungs Center zugewiesen ist, z. b. das Microsoft 365 Security & Compliance Center

### <a name="create-and-configure-azure-ad-applications-for-set-aipauthentication"></a>Erstellen und Konfigurieren von Azure AD Anwendungen für Set-AIPAuthentication

Das Cmdlet " **Set-aipauthentication** " erfordert eine APP-Registrierung für die Parameter " *AppID* " und " *appsecret* ". 

Für Benutzer, die vor kurzem vom klassischen Client migriert wurden und eine APP-Registrierung für die vorherigen *webappid* -und *nativeappid* -Parameter erstellt haben, müssen Sie eine neue APP-Registrierung für den Unified-Bezeichnungs Client erstellen.

**So erstellen Sie eine neue APP-Registrierung für den Unified-Bezeichnungs Client Set-AIPAuthentication Cmdlet**:

1. [Azure-Portal](https://portal.azure.com/) melden Sie sich in einem neuen Browserfenster beim Azure AD-Mandanten an, den Sie mit Azure Information Protection verwenden.

1. Navigieren Sie zu **Azure Active Directory**  >    >  **App-Registrierungen** verwalten, und wählen Sie **neue Registrierung** aus. 

1. Geben Sie im Bereich **Anwendung registrieren** die folgenden Werte an, und klicken Sie dann auf **registrieren**:

    |Option  |Wert  |
    |---------|---------|
    |**Name**     |  `AIP-DelegatedUser` <br>Geben Sie bei Bedarf einen anderen Namen an. Der Name muss pro Mandant eindeutig sein.       |
    |**Unterstützte Kontotypen**     |   Wählen Sie **Nur Konten in diesem Organisationsverzeichnis** aus.      |
    |**Umleitungs-URI (optional)**     |     Wählen Sie **Web** aus, und geben Sie dann ein `https://localhost` .    |
    |     |         |

1. Kopieren Sie im Bereich **AIP-delegateduser** den Wert für die **Anwendungs-ID (Client)**. 

    Der Wert sieht in etwa wie im folgenden Beispiel aus: `77c3c1c3-abf9-404e-8b2b-4652836c8c66` . 

    Dieser Wert wird für den *AppID* -Parameter verwendet, wenn Sie das **Cmdlet "Set-aipauthentication**" ausführen. Fügen Sie den Wert ein, und speichern Sie ihn später.

1. Wählen Sie in der Rand Leiste die Option Zertifikate **Verwalten**  >  **& geheimen** Schlüssel aus.

    Wählen Sie dann im Bereich **AIP-delegateduser-Zertifikate &** geheimen Schlüssel im Abschnitt geheime **Client** Schlüssel die Option **neuer geheimer Client** Schlüssel aus.

1. Geben Sie unter **geheimen Client Schlüssel hinzufügen** Folgendes an, und wählen Sie dann **Hinzufügen** aus:

    |Feld  |Wert  |
    |---------|---------|
    |**Beschreibung**     |  `Azure Information Protection unified labeling client`       |
    |**Laufzeit**     |   Geben Sie die gewünschte Dauer an (1 Jahr, 2 Jahre oder läuft nie ab).     |
    |     |         |

1. Kopieren Sie im Bereich **AIP-delegateduser--Zertifikate & geheimen** Schlüssel im Abschnitt geheime **Client** Schlüssel die Zeichenfolge für den **Wert**. 

    Diese Zeichenfolge sieht in etwa wie im folgenden Beispiel aus: `OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4` . 

    Um sicherzustellen, dass Sie alle Zeichen kopieren, wählen Sie das Symbol aus, das **in die Zwischenablage kopiert** wird. 
    
    > [!IMPORTANT]
    > Es ist wichtig, dass diese Zeichenfolge gespeichert wird, da sie nicht erneut angezeigt wird und nicht abgerufen werden kann. Speichern Sie wie bei allen vertraulichen Informationen, die Sie verwenden, den gespeicherten Wert sicher, und beschränken Sie den Zugriff darauf.
    > 

1. Wählen Sie in der Rand Leiste  >  **API-Berechtigungen** verwalten aus.

    Wählen Sie im Bereich **AIP-delegateduser-API-Berechtigungen** die Option **Berechtigung hinzufügen** aus.

1. Stellen Sie sicher, dass Sie auf der Registerkarte " **API-Berechtigungen** " auf der Registerkarte " **Microsoft-APIs** " die Option **Azure Rights Management Services** auswählen. 

    Wenn Sie aufgefordert werden, den für Ihre Anwendung erforderlichen Berechtigungs Typen einzugeben, wählen Sie **Anwendungs Berechtigungen** aus.

1. Erweitern **Sie für Berechtigungen auswählen** den Eintrag **Inhalt** , wählen Sie den folgenden Eintrag aus, und klicken Sie dann auf **Berechtigungen hinzufügen**
    
    -  **Content. delegatedreader** 
    -  **Content. delegatedwriter**

1. Wählen Sie im Bereich **AIP-delegateduser-API-Berechtigungen** erneut **Berechtigung hinzufügen** aus.

    Wählen Sie im Bereich " **AIP-Berechtigungen anfordern** " die APIs aus, die **Meine Organisation verwendet**, und suchen Sie nach **Microsoft Information Protection Sync Service**.

1. Wählen Sie im Bereich **API-Berechtigungen anfordern** die Option **Anwendungs Berechtigungen** aus.
    
    Erweitern **Sie für SELECT-Berechtigungen** den Eintrag **unifedpolicy**, wählen Sie **unifedpolicy. Tenant. Read** aus, und wählen Sie dann **Berechtigungen hinzufügen** aus.

1. Wählen Sie im Bereich **AIP-delegateduser-API-Berechtigungen** die Option **Administrator Zustimmung erteilen \<*your tenant name*> für** aus, und wählen Sie für die Bestätigungsaufforderung **Ja** aus.
    
    Die API-Berechtigungen sollten wie in der folgenden Abbildung aussehen:

    :::image type="content" source="../media/api-permissions-app.png" alt-text="API-Berechtigungen für die registrierte app in Azure AD":::

Nachdem Sie die Registrierung dieser APP mit einem geheimen Schlüssel abgeschlossen haben, können Sie " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " mit den Parametern " *AppID*" und " *appsecret*" ausführen. Außerdem benötigen Sie Ihre Mandanten-ID. 

> [!TIP]
>Sie können Ihre Mandanten-ID schnell kopieren, indem Sie Azure-Portal: **Azure Active Directory**  >  **Manage**  >  **Properties**  >  **Directory ID**.

### <a name="running-the-set-aipauthentication-cmdlet"></a>Ausführen des Set-AIPAuthentication Cmdlets

1. Öffnen Sie Windows PowerShell mit der **Option als Administrator ausführen**. 

1. Erstellen Sie in ihrer PowerShell-Sitzung eine Variable zum Speichern der Anmelde Informationen für das Windows-Benutzerkonto, das nicht interaktiv ausgeführt wird. Wenn Sie z. b. ein Dienst Konto für den Scanner erstellt haben:

    ```PowerShell
    $pscreds = Get-Credential "CONTOSO\srv-scanner"
    ```

    Sie werden zur Angabe des Kennworts für dieses Konto aufgefordert.

1. Führen Sie das Cmdlet " **Set-aipauthentication** " mit dem Parameter " *onbehalfof" aus* , und geben Sie als Wert die Variable an, die Sie erstellt haben. 

    Geben Sie außerdem Ihre APP-Registrierungs Werte, Ihre Mandanten-ID und den Namen des Delegierten Benutzerkontos in Azure AD an. Beispiel:
    
    ```PowerShell
    Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -DelegatedUser scanner@contoso.com -OnBehalfOf $pscreds
    ```
## <a name="next-steps"></a>Nächste Schritte

Wenn Sie in einer PowerShell-Sitzung eine Hilfe zu Cmdlets benötigen, geben Sie ein `Get-Help <cmdlet name> -online` . Beispiel: 

```PowerShell
Get-Help Set-AIPFileLabel -online
```

Weitere Informationen finden Sie unter

- [Vereinheitlichte Bezeichnungen von Client Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)