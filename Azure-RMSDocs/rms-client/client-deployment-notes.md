---
title: Anmerkungen zur Bereitstellung des RMS-Clients – Azure Information Protection
description: Informationen zu Installation, unterstützten Betriebssystemen, Registrierungseinstellungen und Dienstermittlung für den RMS-Client (Rights Management Service), Version 2, der auch MSIPC-Client genannt wird.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: ca6c4f693bd8466503242be49662bc3358fbd019
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97385793"
---
# <a name="rights-management-service-client-deployment-notes"></a>Hinweise zur Bereitstellung von Rights Management Dienst Clients

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 8, Windows 8.1, Windows 10, Windows Server 2012, Windows Server 2012 R2, Windows Server 2016 *
>
>***Relevant für**: [AIP Unified Bezeichnung Client und Classic Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). *

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Der RMS-Client, Version 2 (Rights Management Services) wird auch als MSIPC-Client bezeichnet. Es handelt sich um Software für Windows-Computer, die mit den Microsoft Rights Management Services, lokal oder in der Cloud, kommuniziert. Zweck ist der Schutz des Zugriffs auf die Nutzung von Informationen, die durch Anwendungen und Geräte fließen, und zwar innerhalb der Begrenzungen Ihrer Organisation oder außerhalb dieser verwalteten Begrenzungen. 

Der RMS-Client ist nicht nur mit dem [Azure Information Protection Unified](use-client.md)-Bezeichnungs Client ausgeliefert, [sondern ist als optionaler Download](https://www.microsoft.com/download/details.aspx?id=38396) verfügbar, der mit Bestätigung und Annahme des Lizenzvertrags frei mit Drittanbieter Software verteilt werden kann. so können Clients Inhalte schützen und nutzen, die durch Rights Management Dienste geschützt wurden.


## <a name="redistributing-the-rms-client"></a>Weiterverbreiten des RMS-Clients
Der RMS-Client kann kostenlos zusammen mit anderen Anwendungen und IT-Lösungen weiterverbreitet und gebündelt werden. Anwendungsentwickler und Lösungsanbieter, die den RMS-Client weiterverbreiten möchten, haben zwei Möglichkeiten:

- Empfehlung: Einbettung des Installationsprogramms des RMS-Clients in die Anwendungsinstallation und Ausführung im unbeaufsichtigten Modus (der Schalter **/quiet** wird im nächsten Abschnitt detailliert vorgestellt).

- Einrichten des RMS-Clients als Voraussetzung für die Anwendung. Bei dieser Option müssen Sie ggf. den Benutzern zusätzliche Anweisungen zum Abrufen, Installieren und Aktualisieren ihrer Computer mit dem RMS-Client bereitstellen, bevor sie Ihre Anwendung verwenden können.

## <a name="installing-the-rms-client"></a>Installieren des RMS-Clients
Der RMS-Client befindet sich in einer ausführbaren Installationsdatei mit dem Namen **setup_msipc_ *\<arch\>*.exe**, wobei *\<arch>* entweder **x86** (für 32-Bit-Clientcomputer) oder **x64** (für 64-Bit-Clientcomputer) ist. Das 64-Bit-Installationspaket (x64) installiert sowohl eine ausführbare 32-Bit-Runtime-ausführbare Datei für die Kompatibilität mit 32-Bit-Anwendungen, die auf einer 64-Bit-Betriebssystem Installation ausgeführt werden, als auch eine ausführbare 64-Bit-Laufzeit für die Unterstützung integrierter 64-Bit-Anwendungen. Das 32-Bit-Installationsprogramm (x86) kann nicht in einer 64-Bit-Windows-Installation ausgeführt werden.

> [!NOTE]
> Für die Installation des RMS-Clients benötigen Sie erhöhte Berechtigungen, z. B. als Mitglied der Gruppe „Administratoren“ auf dem lokalen Computer.

Sie können den RMS-Client mithilfe einer der folgenden Installationsmethoden installieren:

- **Unbeaufsichtigter Modus.** Durch Verwendung des Schalters **/quiet** als Teil der Befehlszeilenoptionen können Sie den RMS-Client unbeaufsichtigt auf Clientcomputern installieren. Das folgende Beispiel zeigt eine unbeaufsichtigte Installation des RMS-Clients auf einem 64-Bit-Clientcomputer:

    ```
    setup_msipc_x64.exe /quiet
    ```

- **Interaktiver Modus.** Alternativ können Sie den RMS-Client über das interaktive GUI-basierte Setup installieren, das vom Installations-Assistenten für den RMS-Client bereitgestellt wird. Um interaktiv zu installieren, doppelklicken Sie auf das Stammverzeichnis des RMS-Clients (**setup_msipc_ *\<arch\>* . exe**) in dem Ordner, in den das Paket kopiert oder auf den lokalen Computer heruntergeladen wurde.

## <a name="questions-and-answers-about-the-rms-client"></a>Fragen und Antworten zum RMS-Client
Der folgende Abschnitt enthält häufig gestellte Fragen zum RMS-Client und die dazugehörigen Antworten.

### <a name="which-operating-systems-support-the-rms-client"></a>Welche Betriebssysteme unterstützen den RMS-Client?
Der RMS-Client wird von den folgenden Betriebssystemen unterstützt:

|Windows Server-Betriebssystem|Windows-Clientbetriebssystem|
|-----------------------------------|-----------------------------------|
|Windows Server 2016|Windows 10|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 mit mindestens SP1|
| | |


### <a name="which-processors-or-platforms-support-the--rms-client"></a>Welche Prozessoren oder Plattformen unterstützen den RMS-Client?
Der RMS-Client wird auf x86- und x64-Computerplattformen unterstützt.

### <a name="where-is-the--rms-client-installed"></a>Wo wird der RMS-Client installiert?
In der Standardeinstellung wird der RMS-Client in „%Programme%\Active Directory Rights Management Services Client 2.“ installiert\<minor version number>.

### <a name="what-files--are-associated-with-the-rms-client-software"></a>Welche Dateien sind der RMS-Clientsoftware zugeordnet?
Die folgenden Dateien werden als Teil der RMS-Clientsoftware installiert:

-   **Msipc.dll**

-   **Ipcsecproc.dll**

-   **Ipcsecproc_ssp.dll**

-   **MSIPCEvents.man**

Zusätzlich zu diesen Dateien werden mit dem RMS-Client auch Unterstützungsdateien für mehrsprachige Benutzeroberflächen in 44 Sprachen installiert. Wenn Sie überprüfen möchten, welche Sprachen unterstützt werden, führen Sie die Installation des RMS-Clients aus, und prüfen Sie nach Abschluss der Installation den Inhalt der Ordner für die mehrsprachige Unterstützung unter dem Standardpfad.

### <a name="is-the-rms-client-included-by-default-when-i-install-a-supported-operating-system"></a>Ist der RMS-Client standardmäßig enthalten, wenn ich ein unterstütztes Betriebssystem installiere?
Nein. Diese Version des RMS-Client wird als optionaler Download bereitgestellt, der separat auf Computern mit unterstützten Versionen des Betriebssystems Microsoft Windows installiert werden kann.

### <a name="is-the-rms-client-automatically-updated-by-microsoft-update"></a>Wird der RMS-Client von Microsoft Update automatisch aktualisiert?
Wenn Sie diesen RMS-Client mit der Option für die unbeaufsichtigte Installation installiert haben, übernimmt der RMS-Client Ihre aktuellen Einstellungen für Microsoft Update. Bei einer Installation des RMS-Clients mithilfe des GUI-basierten Setups werden Sie vom Installationsassistenten für den RMS-Client aufgefordert, Microsoft Update zu aktivieren.

## <a name="rms-client-settings"></a>RMS-Clienteinstellungen
Der folgende Abschnitt enthält Einstellungsinformationen zum RMS-Client. Diese Informationen sind möglicherweise hilfreich, wenn Probleme mit Anwendungen oder Diensten haben, die den RMS-Client verwenden.

> [!NOTE]
> Einige Einstellungen hängen davon ab, ob die RMS-fähige Anwendung als Clientmodusanwendung (z. B. Microsoft Word und Outlook oder der Azure Information Protection-Client mit Windows-Datei-Explorer) oder Servermodusanwendung (z. B. SharePoint und Exchange) ausgeführt wird. In den folgenden Tabellen werden diese Einstellungen als **Clientmodus** bzw. **Servermodus** bezeichnet.

### <a name="where-the-rms-client-stores-licenses-on-client-computers"></a>Speicherorte, an denen der RMS-Client Lizenzen auf Clientcomputern speichert
Der RMS-Client speichert Lizenzen auf dem lokalen Datenträger. Außerdem weden einige Informationen in der Windows-Registrierung zwischengespeichert.

|Beschreibung|Clientmoduspfade|Servermoduspfade|
|---------------|---------------------|---------------------|
|**Lizenzenspeicherort**|%localappdata%\Microsoft\MSIPC|%ALLUSERSPROFILE%\microsoft\msipc\server\\*\<SID\>*|
|**Vorlagenspeicherort**|%localappdata%\Microsoft\MSIPC\Templates|%ALLUSERSPROFILE%\microsoft\msipc\server\\*\<SID\>*|
|**Registrierungs Speicherort**|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local Settings<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \\*\<SID*\>|
| | | |

> [!NOTE]
> *\<SID*> ist der sichere Bezeichner (SID) für das Konto, unter dem die Serveranwendung ausgeführt wird. Wenn die Anwendung beispielsweise unter dem integrierten Netzwerkdienst Konto ausgeführt wird, ersetzen Sie *\<SID\>* durch den Wert der bekannten sid für dieses Konto (S-1-5-20).

### <a name="windows-registry-settings-for-the-rms-client"></a>Windows-Registrierungseinstellungen für den RMS-Client
Sie können Windows-Registrierungsschlüssel zum Festlegen oder Ändern einiger RMS-Clientkonfigurationen verwenden. Als Administrator von RMS-fähigen Anwendungen, die mit AD RMS-Servern kommunizieren, können Sie beispielsweise den Dienstspeicherort im Unternehmen je nach aktuellem Speicherort des Clientcomputers in Ihrer Active Directory-Topologie aktualisieren (d. h. den AD RMS-Server außer Kraft seten, der aktuell für die Veröffentlichung ausgewählt ist). Oder Sie können AD RMS-Ablaufverfolgung auf dem Clientcomputer aktivieren, um das Beheben eines Problems mit einer RMS-fähigen Anwendung zu unterstützen. In der folgenden Tabelle finden Sie die Registrierungseinstellungen, die Sie für den RMS-Client ändern können.


|                                                                                                  Aufgabe                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Einstellungen                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                  Wenn der Client Version 1.03102.0221 oder höher ist:<br /><br />**Steuern der Datensammlung für die Anwendung**                                                  | **Wichtig**: Um die Datenschutzaspekte für Benutzer zu berücksichtigen, müssen Sie als Administrator den Benutzer um seine Zustimmung bitten, bevor Sie die Datensammlung aktivieren.<br /><br />Wenn Sie die Datensammlung aktivieren, stimmen Sie zu, dass Sie Daten über das Internet an Microsoft senden. Microsoft verwendet diese Daten, um die Qualität, Sicherheit und Integrität von Microsoft-Produkten und -Diensten sicherzustellen und zu verbessern. Beispielsweise analysiert Microsoft die Leistung und Zuverlässigkeit, die von Ihnen verwendeten Features, die Reaktionsschnelligkeit der Features, die Geräteleistung, Interaktionen mit der Benutzeroberfläche und etwaige Probleme, die bei der Nutzung des Produkts auftreten. Zu den Daten gehören auch Informationen zur Konfiguration Ihrer Software, z.B. der Software, die derzeit ausgeführt wird, und die IP-Adresse.<br /><br />In Version 1.0.3356 und höher: <br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\MSIPC<br />REG_DWORD: DiagnosticAvailability<br /><br />In Versionen niedriger als 1.0.3356: <br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\MSIPC<br />REG_DWORD: DiagnosticState<br /><br />**Wert**: 0 für die Anwendung definiert (Standard) mithilfe der Umgebungs Eigenschaft [IPC_EI_DATA_COLLECTION_ENABLED](/previous-versions/windows/desktop/msipc/environment-properties), 1 für deaktiviert, 2 für aktiviert<br /><br />**Hinweis**:Der Speicherort ist HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC, wenn Ihre MSIPC-basierte 32-Bit-Anwendung auf einer 64-Bit-Version von Windows ausgeführt wird. |
|                                                       Nur AD RMS:<br /><br />**Aktualisieren des Unternehmensdienstspeicherorts für einen Clientcomputer**                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Aktualisieren Sie die folgenden Registrierungsschlüssel:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />REG_SZ: default<br /><br />**Wert**: \<http or https> ://*RMS_Cluster_Name*/_wmcs/Certification<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />REG_SZ: default<br /><br />**Wert**: \<http or https> ://*RMS_Cluster_Name*/_wmcs/licensing                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|                                                                                    **Aktivieren und Deaktivieren der Ablaufverfolgung**                                                                                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Aktualisieren Sie den folgenden Registrierungsschlüssel:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />REG_DWORD: Trace<br /><br />**Wert**: 1 zum Aktivieren der Ablauf Verfolgung, 0 zum Deaktivieren der Ablauf Verfolgung (Standard)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                                                                        **Ändern der Häufigkeit (in Tagen), mit der Vorlagen aktualisiert werden**                                                                         |                                                                                                                                                                                                                                                                                Mit den folgenden Registrierungs Werten wird festgelegt, wie oft Vorlagen auf dem Computer des Benutzers aktualisiert werden, wenn der Wert "templateupdatefrequencyinseconds" nicht festgelegt ist.  Wenn keiner dieser Werte festgelegt ist, ist das Standardaktualisierungsintervall für Anwendungen, die den RMS-Client (Version 1.0.1784.0) zum Herunterladen von Vorlagen verwenden, 1 Tag. Bei Vorversionen dieser Version ist der Standardwert 7 Tage.<br /><br />**Client Modus**:<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Value**: ein ganzzahliger Wert, der die Anzahl der Tage (mindestens 1) zwischen Downloads angibt.<br /><br />**Server Modus**:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\<SID\><br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Value**: ein ganzzahliger Wert, der die Anzahl der Tage (mindestens 1) zwischen Downloads angibt.                                                                                                                                                                                                                                                                                 |
| **Ändern der Häufigkeit (in Sekunden), mit der Vorlagen aktualisiert werden**<br /><br />Wichtig: Wenn diese Einstellung angegeben ist, wird der Wert für das Aktualisieren von Vorlagen in Tagen ignoriert. Geben Sie einen oder den anderen, aber nicht beide an. |                                                                                                                                                                                                                                                                   Mit den folgenden Registrierungs Werten wird festgelegt, wie oft Vorlagen auf dem Computer des Benutzers aktualisiert werden. Wenn dieser Wert oder der Wert zum Ändern der Häufigkeit in Tagen (TemplateUpdateFrequency) nicht festgelegt ist, ist das Standardaktualisierungsintervall für Anwendungen, die den RMS-Client (Version 1.0.1784.0) zum Herunterladen von Vorlagen verwenden, 1 Tag. Bei Vorversionen dieser Version ist der Standardwert 7 Tage.<br /><br />**Client Modus**:<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Value**: ein ganzzahliger Wert, der die Anzahl der Sekunden zwischen Downloads (mindestens 1) angibt.<br /><br />**Server Modus**:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\ < *sid*><br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Value**: ein ganzzahliger Wert, der die Anzahl der Sekunden zwischen Downloads (mindestens 1) angibt.                                                                                                                                                                                                                                                                    |
|                                                      Nur AD RMS:<br /><br />**Sofortiges Herunterladen der Vorlagen bei der nächsten Veröffentlichungsanforderung**                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                 Bei Tests und Bewertungen kann es wünschenswert sein, dass der RMS-Client Vorlagen so schnell wie möglich herunterlädt. Entfernen Sie für diese Konfiguration den folgenden Registrierungsschlüssel, damit der RMS-Client Vorlagen sofort bei der nächsten Veröffentlichungsanfrage herunterlädt, anstatt auf den in der Registrierungseinstellung „TemplateUpdateFrequency“ festgelegten Zeitpunkt zu warten:<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\\<*Servername*>\Template <br /><br />**Hinweis: Sie** \<*Server Name*> können sowohl externe (corprights.contoso.com) als auch interne (corprights) URLs und damit zwei verschiedene Einträge haben.                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                                                               Nur AD RMS:<br /><br />**Aktivieren der Unterstützung der Verbundauthentifizierung**                                                                |                                                                                                                                                                                                                                                                             Wenn der RMS-Clientcomputer mithilfe einer Verbundvertrauensstellung mit einem AD RMS-Cluster verbunden ist, müssen Sie den Verbundstartbereich konfigurieren.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_SZ: FederationHomeRealm<br /><br />**Wert**: der Wert dieses Registrierungs Eintrags ist der Uniform Resource Identifier (URI) für den Verbund Dienst (z <http://TreyADFS.trey.net/adfs/services/trust> . b. "").<br /><br /> **Hinweis**: Es ist wichtig, dass Sie HTTP und nicht HTTPS für diesen Wert angeben. Zudem ist der Speicherort HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Federation, wenn Ihre MSPIC-basierte 32-Bit-Anwendung auf einer 64-Bit-Version von Windows ausgeführt wird. Ein Beispiel für die Konfiguration finden Sie unter [Bereitstellen von Active Directory Rights Management Services mit Active Directory-Verbunddiensten](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn758110(v=ws.11)).                                                                                                                                                                                                                                                                             |
|                                        Nur AD RMS:<br /><br />**Unterstützen von Partnerverbundservern, die für Benutzereingaben die formularbasierte Authentifizierung erfordern**                                         |                                                                                                                                                                                                                                                                                                                                                             Standardmäßig wird der RMS-Client im unbeaufsichtigten Modus betrieben, in dem keine Benutzereingabe erforderlich ist. Partnerverbundserver können allerdings so konfiguriert werden, dass Benutzereingaben, z. B. über formularbasierte Authentifizierung, erforderlich sind. In diesem Fall muss der RMS-Client so konfiguriert werden, dass der unbeaufsichtigte Modus ignoriert wird, sodass das Formular für die Verbundauthentifizierung in einem Browserfenster angezeigt und der Benutzer für die Authentifizierung heraufgestuft wird.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_DWORD: EnableBrowser<br /><br />**Hinweis**: Wenn der Verbundserver für die formularbasierte Authentifizierung konfiguriert ist, ist dieser Schlüssel erforderlich. Wenn der Verbundserver für eine Verwendung der integrierten Windows-Authentifizierung konfiguriert ist, ist dieser Schlüssel nicht erforderlich.                                                                                                                                                                                                                                                                                                                                                             |
|                                                                      Nur AD RMS:<br /><br />**Blockieren der ILS-Dienstnutzung**                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                 Standardmäßig ermöglicht der RMS Client die Verwendung von durch den ILS-Dienst geschützten Inhalten. Er kann allerdings durch Einstellung des folgenden Registrierungsschlüssels so konfiguriert werden, dass dieser blockiert wird. Wenn dieser Registrierungsschlüssel für die Deaktivierung des ILS-Diensts festgelegt ist, wird bei allen Versuchen, vom ILS-Dienst geschützte Inhalte zu öffnen und zu nutzen, der folgende Fehler zurückgegeben:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: **DisablePassportCertification**<br /><br />**Wert**: 1 zum Blockieren der ILS-Nutzung, 0 zum Zulassen der ILS-Nutzung (Standard)                                                                                                                                                                                                                                                                                                                                                                                                                  |
| | |

### <a name="managing-template-distribution-for-the-rms-client"></a>Verwalten der Vorlagenverteilung für den RMS-Client
Vorlagen erleichtern Benutzern und Administratoren das Anwenden des Rights Management-Schutzes. Der RMS-Client lädt Vorlagen von seinen RMS-Servern oder aus seinem RMS-Dienst automatisch herunter. Wenn Sie die Vorlagen im folgenden Ordner ablegen, lädt der RMS-Client keine Vorlagen aus seinem Standardspeicherort herunter und lädt stattdessen die Vorlagen herunter, die Sie in diesem Ordner abgelegt haben. Der RMS-Client fährt möglicherweise mit dem Herunterladen von Vorlagen von anderen verfügbaren AD RMS-Servern fort.

**Client Modus**:%localappdata%\microsoft\msipc\unmanagedtemplates

**Server Modus**:%ALLUSERSPROFILE%\microsoft\msipc\server\unmanagedtemplates\\*\<SID\>*

Für das Verwenden dieses Ordners gibt es keine spezielle Benennungskonvention mit der Ausnahme, dass die Vorlage vom AD RMS-Server ausgegeben werden und mit der Dateinamenerweiterung XML benannt werden muss. Beispielsweise sind "Contoso-Confidential.xml" oder "Contoso-ReadOnly.xml" gültige Namen.

## <a name="ad-rms-only-limiting-the-rms-client-to-use-trusted-ad-rms-servers"></a>Nur AD RMS: Beschränken des RMS-Clients auf das Verwenden vertrauenswürdiger AD RMS-Server
Der RMS-Client kann durch folgende Änderungen an der Windows-Registrierung auf dem lokalen Computer auf die Verwendung bestimmter vertrauenswürdiger AD RMS-Server beschränkt werden.

**So aktivieren Sie das Beschränken des RMS-Clients auf das Verwenden vertrauenswürdiger AD RMS-Server**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\

    REG_DWORD:AllowTrustedServersOnly

    **Wert**: Wenn ein Wert ungleich NULL angegeben wird, vertraut der RMS-Client nur den angegebenen Servern, die in der Liste der vertrauenswürdigen Server und im Azure Rights Management-Dienst konfiguriert sind.

**So fügen Sie Mitglieder zur Liste vertrauenswürdiger AD RMS-Server hinzu**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\

    REG_SZ:*\<URL_or_HostName>*

    **Wert**: die Zeichen folgen Werte in diesem Registrierungsschlüssel Speicherort können entweder das DNS-Domänen Namen Format (z. b. **ADRMS.contoso.com**) oder vollständige URLs für vertrauenswürdige AD RMS Server (z **`https://adrms.contoso.com`** . b.) sein. Wenn eine angegebene URL mit **https://** beginnt, verwendet der RMS-Client SSL oder TLS zum Kontaktieren des angegebenen AD RMS-Servers.

## <a name="rms-service-discovery"></a>RMS-Diensterkennung
Die RMS-Diensterkennung ermöglicht dem RMS-Client das Überprüfen, mit welchem RMS-Server oder -Dienst vor dem Schützen von Inhalten kommuniziert werden muss. Die Diensterkennung kann auch erfolgen, wenn der RMS-Client geschützte Inhalte nutzt. Diese Art der Erkennung ist allerdings weniger wahrscheinlich, da die den Inhalten zugeordnete Richtlinie den bevorzugten RMS-Server oder -Dienst enthält. Nur wenn diese Quellen nicht erfolgreich sind, führt der Client die Diensterkennung aus.

Um die Diensterkennung durchzuführen, prüft der RMS-Client Folgendes:

1. **Die Windows-Registrierung auf dem lokalen Computer**: Wenn Diensterkennungseinstellungen in der Registrierung konfiguriert sind, werden diese Einstellungen zuerst ausprobiert. 

    Standardmäßig sind diese Einstellungen nicht in der Registrierung konfiguriert. Ein Administrator kann diese jedoch für AD RMS gemäß den Angaben in einem [folgenden Abschnitt](#enabling-client-side-service-discovery-by-using-the-windows-registry) konfigurieren. Ein Administrator konfiguriert diese Einstellungen für den Azure Rights Management-Dienst in der Regel während des [Migrationsvorgangs](../migrate-from-ad-rms-phase2.md) von AD RMS zu Azure Information Protection.

2. **Active Directory Domain Services**: Ein der Domäne beigetretener Computer fragt Active Directory auf einen Dienstverbindungspunkt ab. 

    Wenn ein Dienstverbindungspunkt gemäß dem [folgenden Abschnitt](#ad-rms-only-enabling-server-side-service-discovery-by-using-active-directory) registriert ist, wird an den AD RMS-Client die URL des RMS-Servers zurückgegeben, die dieser verwenden soll.

3. **Der Azure Rights Management-Ermittlungsdienst**: Der RMS-Client verbindet sich mit **`https://discover.aadrm.com`**. Der Benutzer wird zur Authentifizierung aufgefordert.

    Nach erfolgreicher Authentifizierung werden der Benutzername (und die Domäne) aus der Authentifizierung zum Bestimmen des zu verwendenden Azure Information Protection-Mandanten genutzt. Die für dieses Benutzerkonto zu verwendende Azure Information Protection-URL wird an den RMS-Client zurückgegeben. Die URL weist das folgende Format auf: **https://** \<YourTenantURL\> **/_wmcs/licensing** 

    Beispiel: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing

    *\<YourTenantURL\>* weist das folgende Format auf: **{GUID}. RMS. [Region]. aadrm. com**. Sie finden diesen Wert, indem Sie den Wert von **rightionmanagementserviceid** ermitteln, wenn Sie das Cmdlet [Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration) ausführen.

> [!NOTE]
> Bei diesem Dienstermittlungsfluss gibt es vier wichtige Ausnahmen:
> 
> - Mobile Geräte sind am besten für die Nutzung eines Clouddiensts geeignet, weshalb sie standardmäßig die Dienstermittlung für den Azure Rights Management-Dienst (https://discover.aadrm.com)) verwenden. Um diesen Standard so anzupassen, dass mobile Geräte AD RMS anstelle des Azure Rights Management-Diensts verwenden, geben Sie SRV-Einträge in DNS, und installieren Sie die Erweiterung für mobile Geräte (siehe dazu die Angaben unter [Active Directory Rights Management Services-Erweiterung für mobile Geräte](https://technet.microsoft.com/library/dn673574\(v=ws.11\).aspx)). 
>
> - Wenn der Rights Management-Dienst über eine Azure Information Protection-Bezeichnung aufgerufen wird, erfolgt keine Dienstermittlung. Stattdessen wird die URL direkt in der Einstellung der Bezeichnung angegeben, die in der Azure Information Protection-Richtlinie konfiguriert ist. 
>  
> - Wenn ein Benutzer eine Anmeldung aus einer Office-Anwendung einleitet, werden der Benutzername (und die Domäne) in den Authentifizierungsdaten zum Bestimmen des zu verwendenden Azure Information Protection-Mandanten genutzt. In diesem Fall sind keine Registrierungseinstellungen erforderlich, und der Dienstverbindungspunkt wird nicht überprüft.
> 
> - Wenn Sie die [DNS-Umleitung](../migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection) für Klick-und-Los-Desktop-Apps für Office konfiguriert haben, sucht der RMS-Client den Azure Rights Management-Dienst, wenn ihm der Zugriff auf den AD RMS-Cluster verweigert wird, den er zuvor gefunden hat. Aufgrund dieser Ablehnungsaktion sucht der Client nach dem SRV-Eintrag, der den Client an den Azure Rights Management-Dienst für Ihren Mandanten umleitet. Mit diesem SRV-Eintrag kann Exchange Online E-Mails entschlüsseln, die durch Ihren AD RMS-Cluster geschützt wurden. 

### <a name="ad-rms-only-enabling-server-side-service-discovery-by-using-active-directory"></a>Nur AD RMS: Aktivieren der serverseitigen Diensterkennung mithilfe von Active Directory
Wenn Ihr Konto über ausreichende Berechtigungen (Organisationsadministrator und lokaler Administrator für den AD RMS-Server) verfügt, können Sie bei der Installation des AD RMS-Stammclusterservers einen Dienstverbindungspunkt automatisch registrieren. Wenn bereits ein AD RMS-Dienstverbindungspunkt in der Gesamtstruktur vorhanden ist, müssen Sie zunächst den vorhandenen Dienstverbindungspunkt löschen, ehe Sie einen neuen erstellen können.

Sie können nach der Installation von AD RMS mithilfe des folgenden Verfahrens einen Dienstverbindungspunkt registrieren und löschen. Bevor Sie beginnen, stellen Sie sicher, dass Ihr Konto die erforderlichen Berechtigungen (Organisations-Admin und lokaler Administrator für den AD RMS-Server) hat.

#### <a name="to-enable-ad-rms-service-discovery-by-registering-an-scp-in-active-directory"></a>So aktivieren Sie die AD RMS-Diensterkennung durch Registrierung eines Dienstverbindungspunkts in Active Directory

1.  Öffnen Sie auf dem AD RMS-Server die Active Directory Management Services-Konsole:

    - Wählen Sie unter Windows Server 2012 R2 oder Windows Server 2012 in Server-Manager **Tools**  >  **Active Directory Rights Management Services** aus.

    - Wählen Sie unter Windows Server 2008 R2 die Option  >  **Verwaltungs Tools**  >  **Active Directory Rights Management Services** starten aus.

2.  Klicken Sie in der AD RMS-Konsole mit der rechten Maustaste auf den AD RMS-Cluster, und klicken Sie dann auf **Eigenschaften**.

3.  Klicken Sie auf die Registerkarte **SCP**.

4.  Aktivieren Sie das Kontrollkästchen **SCP ändern**.

5.  Wählen Sie die Option **SCP auf aktuellen Zertifizierungscluster festlegen** aus, und klicken Sie auf **OK**.

### <a name="enabling-client-side-service-discovery-by-using-the-windows-registry"></a>Aktivieren der clientseitigen Diensterkennung mithilfe der Windows-Registrierung
Als Alternative zur Verwendung eines Dienstverbindungspunkt oder für den Fall, dass ein solcher nicht vorhanden ist, kann die Registrierung auf dem Clientcomputer so konfiguriert werden, dass der RMS-Client seinen AD RMS-Server finden kann.

#### <a name="to-enable-client-side-ad-rms-service-discovery-by-using-the-windows-registry"></a>So aktivieren Sie die clientseitige AD RMS-Diensterkennung mithilfe der Windows-Registrierung

1. Öffnen Sie den Windows-Registrierungseditor "Regedit.exe":

    - Geben Sie auf dem Clientcomputer im Fenster "Ausführen" **regedit** ein, und drücken Sie dann die EINGABETASTE, um den Registrierungs-Editor zu öffnen.

2. Navigieren Sie im Registrierungseditor zu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!NOTE]
    > Wenn Sie eine 32-Bit-Anwendung auf einem 64-Bit-Computer ausführen, navigieren Sie zu **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**.

3. Klicken Sie zum Erstellen des Unterschlüssels ServiceLocation mit der rechten Maustaste auf **MSIPC**, zeigen Sie auf **Neu**, klicken Sie auf **Schlüssel**, und geben Sie dann **ServiceLocation** ein.

4. Klicken Sie zum Erstellen des Unterschlüssels EnterpriseCertification mit der rechten Maustaste auf **ServiceLocation**, zeigen Sie auf **Neu**, klicken Sie auf **Schlüssel**, und geben Sie dann **EnterpriseCertification** ein.

5. Um die Unternehmenszertifizierungs-URL festzulegen, doppelklicken Sie unter dem Unterschlüssel **EnterpriseCertification** auf den **(Default)**-Wert. Wenn das Dialogfeld **Zeichenfolge bearbeiten** geöffnet wird, geben Sie als **Wertdaten**`<http or https>://<AD RMS_cluster_name>/_wmcs/Certification` ein, und klicken Sie anschließend auf **OK**.

6. Klicken Sie zum Erstellen des Unterschlüssels "EnterprisePublishing" mit der rechten Maustaste auf **ServiceLocation**, zeigen Sie auf **Neu**, klicken Sie auf **Schlüssel**, und geben Sie dann `EnterprisePublishing` ein.

7. Doppelklicken Sie unter dem Unterschlüssel **EnterprisePublishing** auf **(Default)**, um die Unternehmensveröffentlichungs-URL festzulegen. Wenn das Dialogfeld **Zeichenfolge bearbeiten** geöffnet wird, geben Sie als **Wertdaten**`<http or https>://<AD RMS_cluster_name>/_wmcs/Licensing` ein, und klicken Sie anschließend auf **OK**.

8.  Schließen Sie den Registrierungs-Editor.

Wenn der RMS-Client durch Abfragen von Active Directory keinen Dienstverbindungspunkt finden kann und ein solcher nicht in der Registrierung angegeben ist, haben Aufrufe der Diensterkennung für AD RMS keinen Erfolg.

### <a name="redirecting-licensing-server-traffic"></a>Umleiten des Datenverkehrs des Lizenzierungsservers
Mitunter müssen Sie ggf. Datenverkehr während einer Diensterkennung umleiten, z. B. wenn zwei Organisationen zusammengeführt werden und der alte Lizenzierungsserver in einer Organisation außer Betrieb genommen wird und Clients zu einem neuen Lizenzierungsserver umgeleitet werden müssen. Ein weiterer Fall ist die Migration von AD RMS zu Azure RMS. Gehen Sie folgendermaßen vor, um eine Umleitung von Lizenzierungsinformationen zu aktivieren.

#### <a name="to-enable-rms-licensing-redirection-by-using-the-windows-registry"></a>So aktivieren Sie die Umleitung des AD RMS-Lizenzierungsservers mithilfe der Windows-Registrierung

1.  Öffnen Sie den Windows-Registrierungseditor „Regedit.exe“.

2.  Navigieren Sie im Registrierungseditor zu einem der folgenden Schlüssel:

    -   Für die 64-Bit-Version von Office auf x64-Plattform: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Für die 32-Bit-Version von Office auf x64-Plattform: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Erstellen Sie den Unterschlüssel „LicensingRedirection“, indem Sie mit der rechten Maustaste auf **Servicelocation** klicken, auf **Neu** zeigen, auf **Schlüssel** klicken und dann **LicensingRedirection** eingeben.

4.  Klicken Sie zum Festlegen der Lizenzierungsumleitung mit der rechten Maustaste auf den Unterschlüssel **LicensingRedirection**, wählen Sie **Neu** aus, und wählen Sie dann **Zeichenfolgenwert** aus.  Geben Sie unter **Name** die vorherige Serverlizenzierungs-URL und als **Wert** die neue Serverlizenzierungs-URL an.

    Wenn Sie z. B. die Lizenzierungsdaten von einem Server bei Contoso.com auf einen Server bei Fabrikam.com umleiten möchten, könnten Sie die folgenden Werte eingeben:

    **Name**: `https://contoso.com/_wmcs/licensing`

    **Wert**: `https://fabrikam.com/_wmcs/licensing`

    > [!NOTE]
    > Wenn für den alten Lizenzserver sowohl eine Intranet- als auch eine Extranet-URL festgelegt sind, muss für beide URLs eine neue Name/Wert-Zuordnung unter dem Schlüssel **LicensingRedirection** festgelegt werden.

5.  Wiederholen Sie den vorherigen Schritt für alle Server, die umgeleitet werden müssen.

6.  Schließen Sie den Registrierungs-Editor.