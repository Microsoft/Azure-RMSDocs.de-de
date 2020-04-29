---
title: Active Directory Rights Management Services-Erweiterung für mobile Geräte für aip
description: Erfahren Sie mehr über Active Directory Erweiterungen für mobile Geräte für aip.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 04/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: cb9393c637b71771789efcdcfa7b9b5aeb378226
ms.sourcegitcommit: 479b3aaea7011750ff85a217298e5ae9185c1dd1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82230813"
---
# <a name="active-directory-rights-management-services-mobile-device-extension"></a>Active Directory Rights Management Services-Mobilgeräteerweiterung

 
Gilt für: Windows Server 2019, 2016, 2012 R2 und 2012

Sie können die Erweiterung für mobile Geräte für Active Directory Rights Management Services (AD RMS) aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=43738) herunterladen und diese Erweiterung zusätzlich zu einer vorhandenen AD RMS Bereitstellung installieren. Dadurch können Benutzer sensible Daten schützen und nutzen, wenn Ihr Gerät die neuesten API-aktivierten Apps unterstützt. Beispielsweise können Benutzer folgende Aktionen ausführen:
- Verwenden Sie die Azure Information Protection-APP, um geschützte Textdateien in verschiedenen Formaten (einschließlich txt, CSV und XML) zu verwenden.
- Verwenden Sie die Azure Information Protection-App für die Nutzung geschützter Bilddateien (einschließlich jpg, GIF und TIF).
- Verwenden Sie die Azure Information Protection-APP, um eine beliebige Datei zu öffnen, die generisch geschützt ist (Pfile-Format).
- Verwenden Sie die Azure Information Protection-App zum Öffnen einer Office-Datei (Word, Excel, PowerPoint), bei der es sich um eine PDF-Kopie (PDF-und ppdf-Format) handelt.
- Verwenden Sie die Azure Information Protection-App zum Öffnen geschützter e-Mail-Nachrichten (rpmsg) und geschützter PDF-Dateien in SharePoint Online.
- Verwenden Sie einen AIP-fähigen PDF-Viewer für die plattformübergreifende Anzeige oder zum Öffnen von PDF-Dateien, die mit einer beliebigen AIP-fähigen Anwendung geschützt wurden.
- Verwenden Sie Ihre intern entwickelten AIP-fähigen apps, die mithilfe des [MIP SDK](https://aka.ms/mipsdkdocs)geschrieben wurden.

> [!NOTE]
> Sie können die Azure Information Protection-APP von der [Microsoft Rights Management](https://go.microsoft.com/fwlink/?linkid=303970) -Seite der Microsoft-Website herunterladen. Informationen zu anderen apps, die mit der Erweiterung für mobile Geräte unterstützt werden, finden Sie in der Tabelle auf der Seite " [Anwendungen](https://docs.microsoft.com/azure/information-protection/requirements-applications) " in dieser Dokumentation. Weitere Informationen zu den verschiedenen Dateitypen, die RMS unterstützt, finden Sie im Abschnitt [Unterstützte Dateitypen und Dateinamen Erweiterungen](https://docs.microsoft.com/rights-management/rms-client/sharing-app-admin-guide-technical%23supported-file-types-and-file-name-extensions) im Administrator Handbuch für die Rights Management Freigabe Anwendung.

> [!IMPORTANT]
> Achten Sie darauf, dass Sie die Voraussetzungen lesen und konfigurieren, bevor Sie die Erweiterung für mobile Geräte installieren.

Um weitere Informationen zu erhalten, laden Sie das Whitepaper "Microsoft Azure Information Protection" und die zugehörigen Skripts aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=40333)herunter.

## <a name="prerequisites-for-ad-rms-mobile-device-extension"></a>Voraussetzungen für AD RMS-Erweiterung für mobile Geräte

Stellen Sie vor der Installation der AD RMS-Erweiterung für mobile Geräte sicher, dass die folgenden Abhängigkeiten vorhanden sind.


|Anforderung|Weitere Informationen|
|---------------|------------------------|
|Eine vorhandene AD RMS Bereitstellung auf Windows Server 2019, 2016, 2012 R2 oder 2012, die Folgendes umfasst:<br /><br /> -Ihr AD RMS Cluster muss über das Internet zugänglich sein. <br /><br /> -AD RMS muss eine voll Microsoft SQL Server basierte Datenbank auf einem separaten Server und nicht die interne Windows-Datenbank verwenden, die häufig zum Testen auf demselben Server verwendet wird. <br /><br />-Das Konto, das Sie zum Installieren der Erweiterung für mobile Geräte verwenden, muss über Systemadministrator Rechte für die SQL Server Instanz verfügen, die Sie für die AD RMS verwenden. <br /><br />-Die AD RMS Server müssen für die Verwendung von SSL/TLS mit einem gültigen x. 509-Zertifikat konfiguriert werden, das von den Clients für mobile Geräte als vertrauenswürdig eingestuft wird.<br /><br /> Wenn sich die AD RMS Server hinter einer Firewall befinden oder mithilfe eines Reverseproxys veröffentlicht werden, müssen Sie zusätzlich zum Veröffentlichen des **/_wmcs-** Ordners im Internet auch den Ordner "/My" (z. b. **\/\/_https: RMSserver.contoso.com/My**) veröffentlichen.|Ausführliche Informationen zu AD RMS Voraussetzungen und Bereitstellungs Informationen finden Sie im Abschnitt "Voraussetzungen" in diesem Artikel.|
|AD FS auf Ihrem Windows-Server bereitgestellt:<br /><br /> -Die AD FS Serverfarm muss über das Internet zugänglich sein (Sie haben Verbund Server Proxys bereitgestellt). <br /><br />-Die Formular basierte Authentifizierung wird nicht unterstützt. Sie müssen die integrierte Windows-Authentifizierung verwenden. <br /><br /> **Wichtig**: AD FS müssen auf dem Computer, auf dem AD RMS ausgeführt wird, und der Erweiterung für mobile Geräte einen anderen Computer ausführen.|Dokumentation zu AD FS finden Sie im [Bereitstellungs Handbuch für Windows Server AD FS](https://docs.microsoft.com/office365/troubleshoot/active-directory/set-up-adfs-for-single-sign-on) in der Windows Server-Bibliothek.<br /><br /> AD FS muss für die Mobilgeräteerweiterung konfiguriert werden. Anweisungen hierzu finden Sie im Abschnitt **Konfigurieren von AD FS für die AD RMS Erweiterung für mobile Geräte** in diesem Thema.|
|Mobile Geräte müssen den PKI-Zertifikaten auf dem RMS-Server (oder den Servern) Vertrauen.|Wenn Sie Ihre Server Zertifikate von einer öffentlichen Zertifizierungsstelle erwerben, wie z. b. VeriSign oder Comodo, ist es wahrscheinlich, dass Mobile Geräte bereits der Stamm Zertifizierungsstelle für diese Zertifikate Vertrauen, damit diese Geräte den Server Zertifikaten ohne zusätzliche Konfiguration Vertrauen.<br /><br /> Wenn Sie jedoch eine eigene interne Zertifizierungsstelle verwenden, um die Server Zertifikate für RMS bereitzustellen, müssen Sie zusätzliche Schritte ausführen, um das Zertifikat der Stamm Zertifizierungsstelle auf den mobilen Geräten zu installieren. Wenn dies nicht der Fall ist, können mobile Geräte keine Verbindung mit dem RMS-Server herstellen.|
|SRV-Einträge im DNS|Erstellen Sie einen oder mehrere SRV-Einträge in Ihrer/Ihren Unternehmensdomäne(n):<br /><br />1: Erstellen eines Datensatzes für jedes e-Mail-Domänen Suffix, das Benutzer verwenden werden <br /><br />2: Erstellen Sie einen Datensatz für jeden FQDN, der von ihren RMS-Clustern verwendet wird, um Inhalte zu schützen, ohne den Cluster Namen einzuschließen. <br /><br />Diese Datensätze müssen in jedem Netzwerk aufgelöst werden können, das von den mobilen Geräten, die eine Verbindung herstellen, verwendet wird. Dies umfasst das Intranet, wenn Ihre mobilen Geräte eine Verbindung über das Intranet<br /><br /> Wenn Benutzer Ihre e-Mail-Adresse von Ihrem mobilen Gerät angeben, wird das Domänen Suffix verwendet, um zu ermitteln, ob Sie eine AD RMS-Infrastruktur oder Azure AIP verwenden sollten. Wenn der SRV-Eintrag gefunden wird, werden Clients zu dem AD RMS-Server umgeleitet, der auf diese URL reagiert.<br /><br /> Wenn Benutzer geschützte Inhalte mit einem mobilen Gerät nutzen, sucht die Client Anwendung in DNS nach einem Datensatz, der mit dem voll qualifizierten Namen in der URL des Clusters übereinstimmt, mit dem der Inhalt geschützt wurde (ohne den Cluster Namen). Das Gerät wird dann zu dem im DNS-Eintrag angegebenen AD RMS-Cluster geleitet und erhält eine Lizenz zum Öffnen des Inhalts. In den meisten Fällen ist der RMS-Cluster mit dem RMS-Cluster identisch, der die Inhalte schützt.<br /><br /> Weitere Informationen zum Angeben der SRV-Einträge finden Sie im Abschnitt **angeben der DNS-SRV-Einträge für die AD RMS-Erweiterung für mobile Geräte** in diesem Thema.|
|Unterstützte Clients, die Anwendungen verwenden, die mithilfe des MIP SDK für diese Plattform entwickelt wurden. |Laden Sie die unterstützten Apps für die von Ihnen verwendeten Geräte mithilfe der Links auf der [Microsoft Azure Information Protection](https://www.microsoft.com/download/details.aspx?id=40333) Downloadseite herunter.|

### <a name="configuring-ad-fs-for-the-ad-rms-mobile-device-extension"></a>Konfigurieren von AD FS für die AD RMS-Mobilgeräteerweiterung

Sie müssen zunächst AD FS konfigurieren und dann die AIP-App für die Geräte autorisieren, die Sie verwenden möchten.

#### <a name="step-1-to-configure-ad-fs"></a>Schritt 1: so konfigurieren Sie AD FS

- Sie können entweder ein Windows PowerShell-Skript ausführen, um AD FS automatisch für eine Unterstützung der AD RMS-Mobilgeräteerweiterung zu konfigurieren, oder Sie können die Konfigurationsoptionen und -werte manuell eingeben:
    - Wenn Sie AD FS für die AD RMS-Erweiterung für mobile Geräte automatisch konfigurieren möchten, kopieren Sie Folgendes in eine Windows PowerShell-Skriptdatei, und führen Sie es dann aus:

```powershell
# This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

# Check if Microsoft Rights Management Mobile Device Extension is configured on the Server
$CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
if ($CheckifConfigured)
{
Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
Write-Host $CheckifConfigured
}
else
{
Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

# TransformaRules used by Microsoft Rights Management Mobile Device Extension
# Claims: E-mail, UPN and ProxyAddresses
$TransformRules = @"
@RuleTemplate = "LdapClaims"
@RuleName = "Jwt Token"
c:[Type ==
"https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
Issuer == "AD AUTHORITY"]
 => issue(store = "Active Directory", types =
("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
"http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
"http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

@RuleTemplate = "PassThroughClaims"
@RuleName = "JWT pass through"
c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
 => issue(claim = c);

@RuleTemplate = "PassThroughClaims"
@RuleName = "JWT pass through"
c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
 => issue(claim = c);

@RuleTemplate = "PassThroughClaims"
@RuleName = "JWT pass through Proxy addresses"
c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
 => issue(claim = c);
"@

# AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
# Allow All users
$AuthorizationRules = @"
@RuleTemplate = "AllowAllAuthzRule"
 => issue(Type = "https://schemas.microsoft.com/authorization/claims/permit",
Value = "true");
"@

# Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
}
```

- Verwenden Sie die folgenden Einstellungen, um AD FS für die AD RMS-Erweiterung für mobile Geräte manuell zu konfigurieren:

|**Configuration**|**Wert**|
|-----|-----|
|**Vertrauende Seite Vertrauensstellung**|_api. RMS. Rest. com|
|**Anspruchsregel**|**Attribut Speicher**: Active Directory <br /><br />E-Mail- **Adressen**: e-Mail-Adresse<br /><br>**Benutzer Prinzipal Name**: UPN<br /><br /> **Proxy Adresse**: _https:\/\/Schemas.xmlsoap.org/Claims/proxyAddresses|

> [!TIP]
> Schritt-für-Schritt-Anleitungen für eine Beispiel Bereitstellung von AD RMS mit AD FS finden Sie unter Bereitstellen von [Active Directory Rights Management Services mit Active Directory-Verbunddienste (AD FS)](https://docs.microsoft.com/office365/troubleshoot/active-directory/set-up-adfs-for-single-sign-on).

#### <a name="step-2-authorize-apps-for-your-devices"></a>Schritt 2: Autorisieren von Apps für Ihre Geräte

1. Führen Sie den folgenden Windows PowerShell-Befehl aus, nachdem Sie die Variablen ersetzt haben, um Unterstützung für die Azure Information Protection App hinzuzufügen


```powershell
Add-AdfsClient -Name "R<your application name> " -ClientId "<YOUR CLIENT ID >" -RedirectUri @("<YOUR REDIRECT URI >")
```

**PowerShell-Beispiel**
```powershell
Add-AdfsClient -Name "Fabrikam application for MIP" -ClientId "96731E97-2204-4D74-BEA5-75DCA53566C3" -RedirectUri @("com.fabrikam.MIPAPP://authorize")
```

### <a name="specifying-the-dns-srv-records-for-the-ad-rms-mobile-device-extension"></a>Festlegen der DNS-SRV-Einträge für die AD RMS-Mobilgeräteerweiterung

Sie müssen DNS-SRV-Einträge für jede E-Mail-Domäne erstellen, die Ihre Benutzer verwenden. Wenn alle Ihre Benutzer untergeordnete Domänen aus einer einzigen übergeordneten Domäne verwenden und alle Benutzer aus diesem zusammenhängenden Namespace denselben RMS-Cluster verwenden, reicht ein SVR-Eintrag in der übergeordneten Domäne aus, damit RMS die entsprechenden DMS-Einträge findet.
Die SRV-Datensätze haben das folgende Format: _rmsdisco. _http. _tcp. \<rmsclusterfqdn>\<portNumber>\<rmsclusterf>

> [!NOTE]
> Geben Sie 443 für \<die portNumber-> an. Obwohl Sie eine andere Portnummer in DNS angeben können, verwenden Geräte mit der Erweiterung für mobile Geräte immer 443.

Beispiel: Wenn es in Ihrer Organisation Benutzer mit den folgenden E-Mail-Adressen gibt:
  - _user@contoso.com
  - _user@sales.contoso.com
  - _user@fabrikam.comWenn keine anderen untergeordneten Domänen für _contoso. com vorhanden sind, die einen anderen RMS-Cluster als den mit dem Namen _rmsserver....... com verwenden, erstellen Sie zwei DNS-SRV-Einträge, die diese Werte aufweisen:
- _rmsdisco. _http. _tcp 443. _rmsserver....................
- _rmsdisco. _http. _tcp. fabrikam. com 443 _rmsserver. ".

Wenn Sie die DNS-Server Rolle unter Windows Server verwenden, verwenden Sie die folgenden Tabellen als Leitfaden für die SRV-Daten Satz Eigenschaften in der DNS-Manager-Konsole:

|Feld|Wert|
|------|------|
|Domain|_tcp....
|Dienst|_rmsdisco
|Protocol|_http
|Priority|0
|Weight|0
|Portnummer|443
|Host, der diesen Dienst anbietet|_rmsserver....

|Feld|Wert|
|------|------|
|Domain|_tcp. fabrikam. com
|Dienst|_rmsdisco
|Protocol|_http
|Priority|0
|Weight|0
|Portnummer|443
|Host, der diesen Dienst anbietet|_rmsserver....|

Zusätzlich zu diesen DNS-SRV-Einträgen für Ihre e-Mail-Domäne müssen Sie einen weiteren DNS-SRV-Eintrag in der RMS-Cluster Domäne erstellen. Dieser Datensatz muss die FQDNs Ihres RMS-Clusters angeben, der Inhalte schützt. Jede Datei, die von RMS geschützt wird, enthält eine URL für den Cluster, der diese Datei schützt. Mobile Geräte verwenden den DNS-SRV-Eintrag und den im Eintrag angegebenen URL-FQDN, um den entsprechenden RMS-Cluster zu finden, der mobile Geräte unterstützen kann.

Wenn Ihr RMS-Cluster z. b **. _rmsserver...**........, wenn Sie einen DNS-SRV-Datensatz mit den folgenden Werten erstellen: **_rmsdisco. _http. _tcp _rmsserver 443.**

Wenn Sie die DNS-Server Rolle unter Windows Server verwenden, verwenden Sie die folgende Tabelle als Richtlinie für die SRV-Daten Satz Eigenschaften in der DNS-Manager-Konsole:

|Feld|Wert|
|------|------|
|Domain|_tcp....
|Dienst|_rmsdisco
|Protocol|_http
|Priority|0
|Weight|0
|Portnummer|443
|Host, der diesen Dienst anbietet|_rmsserver....|

## <a name="deploying-the-ad-rms-mobile-device-extension"></a>Bereitstellen der AD RMS-Mobilgeräteerweiterung

Stellen Sie vor der Installation der AD RMS-Erweiterung für mobile Geräte sicher, dass die Voraussetzungen aus dem vorherigen Abschnitt vorhanden sind und dass Sie die URL Ihres AD FS Servers kennen. Gehen Sie wie folgt vor:

1. Laden Sie die AD RMS-Erweiterung für mobile Geräte (ADRMS) herunter. Mobiledeviceextension. exe) aus dem Microsoft Download Center.
1. Führen Sie **ADRMS aus. Mobiledeviceextension. exe** , um den Active Directory Rights Management Services Setup-Assistenten für die mobile Geräte Erweiterung zu starten.
Wenn Sie dazu aufgefordert werden, geben Sie die URL des AD FS-Server an, den Sie zuvor konfiguriert haben.
1. Schließen Sie den Assistenten ab.

Führen Sie den Assistenten auf allen Knoten in Ihrem RMS-Cluster aus.

Wenn Sie über einen Proxy Server zwischen dem AD RMS Cluster und den AD FS Servern verfügen, kann der AD RMS Cluster standardmäßig keine Verbindung mit dem Verbund Dienst aufnehmen. In diesem Fall können AD RMS das vom mobilen Client empfangene Token nicht überprüfen und die Anforderung ablehnen. Wenn Sie über einen Proxy Server verfügen, der diese Kommunikation blockiert, müssen Sie die Datei "Web. config" von der AD RMS Website für die mobile Geräte Erweiterung aktualisieren, damit AD RMS den Proxy Server umgehen kann, wenn er die AD FS Server kontaktieren muss.

#### <a name="updating-proxy-settings-for-the-ad-rms-mobile-device-extension"></a>Proxy Einstellungen für die AD RMS-Erweiterung für mobile Geräte werden aktualisiert

1. Öffnen Sie die Datei "Web. config", die sich im Ordner " **\Programme\Active Directory Rights Management Services Mobile Device extension\web Service**" befindet.

1. Fügen Sie der Datei den folgenden Knoten hinzu:

```powershell
   <system.net>
    <defaultProxy>
        <proxy  proxyaddress="http://<proxy server>:<port>"
                bypassonlocal="true"
        />
        <bypasslist>
            <add address="<AD FS URL>" />
        </bypasslist>
    </defaultProxy>
<system.net>
```
1. Nehmen Sie die folgenden Änderungen vor, und speichern Sie dann die Datei:
- Ersetzen \<Sie Proxy-Server> durch den Namen oder die Adresse des Proxy Servers.
- Ersetzen \<Sie Port> durch die Portnummer, für deren Verwendung der Proxy Server konfiguriert ist.
- Ersetzen \<Sie AD FS URL-> durch die URL des Verbund Dienstanbieter. Fügen Sie das http-Präfix nicht ein.

    > [!NOTE]
    > Weitere Informationen zum Überschreiben der Proxy Einstellungen finden Sie in der Dokumentation zur [Proxykonfiguration](https://msdn.microsoft.com/library/dkwyc043(v=vs.110).aspx) .

1. Setzen Sie IIS zurück, indem Sie z. b. **iisreset** über eine Eingabeaufforderung als Administrator ausführen.

Wiederholen Sie diesen Vorgang auf allen Knoten im RMS-Cluster.


## <a name="see-also"></a>Weitere Informationen

Erfahren Sie mehr über Azure Information Protection, wenden Sie sich an andere AIP-Kunden, und verwenden Sie AIP-Produktmanager, die die [API-Yammer-Gruppe](https://www.yammer.com/askipteam/)verwenden. 

