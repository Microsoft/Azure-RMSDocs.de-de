---
title: Verwenden von PowerShell mit dem klassischen Azure Information Protection-Client
description: Anweisungen und Informationen für Administratoren zum Verwalten des Azure Information Protection des klassischen Clients mithilfe von PowerShell.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 05/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ROBOTS: NOINDEX
ms.subservice: v1client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 7df480389741a900326477e8d6088ac9dc6da596
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98808674"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-classic-client"></a>Administrator Handbuch: Verwenden von PowerShell mit dem klassischen Azure Information Protection-Client

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified-Bezeichnungs Client finden Sie im Unified-Bezeichnungs [Client-Administrator Handbuch](clientv2-admin-guide-powershell.md). *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn Sie den Azure Information Protection klassischen Client installieren, werden PowerShell-Befehle automatisch installiert. Dadurch können Sie den Client durch Ausführen von Befehlen, die Sie in Skripts zur Automatisierung einfügen können, verwalten.

Die Cmdlets werden mit dem PowerShell-Modul **AzureInformationProtection** installiert. Dieses Modul umfasst alle Rights Management-Cmdlets aus dem RMS Protection-Tool (wird nicht mehr unterstützt). Es gibt auch Cmdlets, die Azure Information Protection für die Bezeichnung verwenden. Beispiel:

|Cmdlet für die Bezeichnung|Beispielverwendung|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|Für einen freigegebenen Ordner werden alle Dateien mit einer bestimmten Bezeichnung ermittelt.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|Überprüfen Sie bei einem freigegebenen Ordner die Dateiinhalte, und versehen Sie Dateien ohne Bezeichnung automatisch gemäß den von Ihnen festgelegten Bedingungen mit Bezeichnungen.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|Für einen freigegebenen Ordner wird eine bestimmte Bezeichnung auf alle Dateien ohne Bezeichnung angewendet.|
|[Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)|Bezeichnen Sie Dateien nicht interaktiv, z.B. durch Verwenden eines Skripts, das nach einem Zeitplan ausgeführt wird.|

> [!TIP]
> Um Cmdlets mit Pfadlängen zu verwenden, die mehr als 260 Zeichen umfassen, können Sie die folgende [Gruppenrichtlinieneinstellung](/archive/blogs/jeremykuhne/net-4-6-2-and-long-paths-on-windows-10) verwenden, die ab Windows 10, Version 1607 verfügbar ist:<br /> **Richtlinie**  >  für lokale Computer **Computer Konfiguration**  >  **Administrative Vorlagen**  >  **Alle Einstellungen**  >  **Lange Win32-Pfade aktivieren** 
> 
> Bei Windows Server 2016 können Sie die gleiche Gruppenrichtlinieneinstellung verwenden, wenn Sie die neuesten administrativen Vorlagen (ADMX-Dateien) für Windows 10 installieren.
>
> Weitere Informationen finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

Die [Azure Information Protection-Überprüfung](../deploy-aip-scanner.md) verwendet Cmdlets aus dem AzureInformationProtection-Modul, um einen Dienst unter Windows Server zu installieren und zu konfigurieren. Mit der Überprüfung können Sie anschließend Dateien in Datenspeichern suchen, klassifizieren und schützen.

Eine Übersicht über alle Cmdlets und die entsprechende Hilfe finden Sie unter [AzureInformationProtection-Modul](/powershell/module/azureinformationprotection). Geben Sie in einer PowerShell-Sitzung `Get-Help <cmdlet name> -online` ein, um die neueste Hilfe aufzurufen.  

Dieses Modul installiert **\ProgramFiles (x86) \Microsoft Azure Information Protection** und fügt diesen Ordner der Systemvariablen **PSModulePath** hinzu. Die DLL-Datei für dieses Modul lautet **AIP.dll**.

Wenn Sie derzeit das Modul als ein Benutzer installieren und die Cmdlets auf dem gleichen Computer als ein anderer Benutzer ausführen, müssen Sie zuerst den Befehl `Import-Module AzureInformationProtection` ausführen. In diesem Szenario wird das Modul beim erstmaligen Ausführen eines Cmdlets nicht automatisch geladen.

Bevor Sie mit der Verwendung dieser Cmdlets beginnen, betrachten Sie die zusätzlichen Voraussetzungen und Anweisungen, die Ihrer Bereitstellung entsprechen:

- [Azure Information Protection und Azure Rights Management-Dienst](#azure-information-protection-and-azure-rights-management-service)

    - Zutreffend, wenn Sie die ausschließliche Klassifizierung oder die Klassifizierung mit Rights Management-Schutz verwenden: Sie verfügen über ein Abonnement, das Azure Information Protection (z. B. „Enterprise Mobility + Security“) enthält.
    - Zutreffend, wenn Sie den ausschließlichen Schutz mit dem Azure Rights Management-Dienst verwenden: Sie verfügen über ein Abonnement, das den Azure Rights Management-Dienst (z. B. Office 365 E3 und Office 365 E5) enthält.

- [Active Directory-Rechteverwaltungsdienste](#active-directory-rights-management-services)

    - Zutreffend, wenn Sie den ausschließlichen Schutz mit der lokalen Version von Azure Rights Management, Active Directory Rights Management Services (AD RMS), verwenden.

Weitere Informationen finden Sie in der relevanten Sammlung [Azure Information Protection bekannter Probleme](../known-issues.md#powershell-support-for-the-azure-information-protection-client).

## <a name="azure-information-protection-and-azure-rights-management-service"></a>Azure Information Protection und Azure Rights Management-Dienst

Lesen Sie diesen Abschnitt, bevor Sie die PowerShell-Befehle verwenden, wenn Ihre Organisation Azure Information Protection für die Klassifizierung und den Schutz oder nur den Azure Rights Management-Dienst für den Datenschutz verwendet.


### <a name="prerequisites"></a>Voraussetzungen

Zusätzlich zu den Voraussetzungen für die Installation des Moduls „AzureInformationProtection“ sind weitere Komponenten für die Azure Information Protection-Bezeichnung und den Azure Rights Management-Datenschutzdienst erforderlich:

1. Der Azure Rights Management-Dienst muss aktiviert werden.

2. So entfernen Sie den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos: 

    - Die Administratorfunktion muss für Ihre Organisation aktiviert werden. Zudem muss Ihr Konto als Administrator für Azure Rights Management konfiguriert sein.

3. So werden Dateien direkt ohne Benutzerinteraktion geschützt oder ihr Schutz entsprechend aufgehoben: 

    - Erstellen Sie ein Dienstprinzipalkonto, führen Sie „Set-RMSServerAuthentication“ aus und erwägen Sie, diesen Dienstprinzipal zum Administrator für Azure Rights Management zu machen.

4. Für Regionen außerhalb von Nordamerika: 

    - Bearbeiten Sie die Registrierung für die Diensterkennung.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Voraussetzung 1: Der Azure Rights Management-Dienst muss aktiviert werden.

Für diese Voraussetzung können Sie den Datenschutz mithilfe von Bezeichnungen anwenden oder eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen, um den Datenschutz anzuwenden.

Wenn Ihr Azure Information Protection Mandanten nicht aktiviert ist, lesen Sie die Anweisungen zum [Aktivieren des Schutz Dienstanbieter von Azure Information Protection](../activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Voraussetzung 2: Den Schutz von Dateien für andere Benutzer mithilfe Ihres eigenen Kontos entfernen.

Typische Szenarien für das Entfernen des Schutzes von Dateien für andere Benutzer umfassen die Datenermittlung oder Datenwiederherstellung. Wenn Sie den Schutz mithilfe von Bezeichnungen anwenden, können Sie den Schutz durch Festlegen einer neuen Bezeichnung entfernen, durch die kein Schutz angewendet wird. Sie können dazu aber auch die Bezeichnung entfernen. Aber Sie werden wahrscheinlich eher eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen, um den Schutz zu entfernen.

Sie müssen über ein Rights Management-Nutzungsrecht verfügen oder Administrator sein, um den Schutz von Dateien zu entfernen. Für die Datenermittlung oder Datenwiederherstellung wird in der Regel die Administratorfunktion verwendet. Informationen zum Aktivieren dieses Feature und zum Konfigurieren Ihres Kontos als Administrator finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](../configure-super-users.md).

#### <a name="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction"></a>Voraussetzungen 3: Dateien ohne Benutzerinteraktion schützen oder deren Schutz aufheben.

Sie können ohne Interaktion eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen, um Dateien zu schützen oder ihren Schutz aufzuheben.

Sie müssen ein Dienstprinzipalkonto verwenden, um die Verbindung mit dem Azure Rights Management-Dienst nicht interaktiv herzustellen, wozu Sie das `Set-RMSServerAuthentication`-Cmdlet verwenden. Sie müssen entsprechend für jede Windows PowerShell-Sitzung vorgehen, in der Cmdlets ausgeführt werden, die eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen. Bevor Sie dieses Cmdlet ausführen, müssen Sie über die folgenden drei Bezeichner verfügen:

- BposTenantId

- AppPrincipalId

- Symmetrischer Schlüssel

Sie können die folgenden PowerShell-Befehle und kommentierte Anweisungen verwenden, um die Werte für die Bezeichner automatisch zu erhalten und um das Set-RMSServerAuthentication-Cmdlet auszuführen. Sie können alternativ die Werte manuell abrufen und angeben.

So rufen Sie die Werte automatisch ab und führen Set-RMSServerAuthentication aus:

```ps
# Make sure that you have the AIPService and MSOnline modules installed

$ServicePrincipalName="<new service principal name>"
Connect-AipService
$bposTenantID=(Get-AipServiceConfiguration).BPOSId
Disconnect-AipService
Connect-MsolService
New-MsolServicePrincipal -DisplayName $ServicePrincipalName

# Copy the value of the generated symmetric key

$symmetricKey="<value from the display of the New-MsolServicePrincipal command>"
$appPrincipalID=(Get-MsolServicePrincipal | Where { $_.DisplayName -eq $ServicePrincipalName }).AppPrincipalId
Set-RMSServerAuthentication -Key $symmetricKey -AppPrincipalId $appPrincipalID -BposTenantId $bposTenantID
```

In den nächsten Abschnitten wird erklärt, wie Sie diese Werte manuell abrufen und angeben. Zudem erhalten Sie weitere Informationen über jeden Wert.

##### <a name="to-get-the-bpostenantid"></a>So rufen Sie „BposTenantId“ ab

Führen Sie das Cmdlet "Get-AipServiceConfiguration" über das Azure RMS Windows PowerShell-Modul aus:

1. Wenn dieses Modul nicht bereits auf Ihrem Computer installiert ist, finden Sie weitere Informationen unter [Installieren des aipservice-PowerShell-Moduls](../install-powershell.md).

2. Starten Sie Windows PowerShell mit der Option **als Administrator ausführen** .

3. Stellen Sie die Verbindung mit dem Azure Rights Management-Dienst mithilfe des Cmdlets `Connect-AipService` her:
   ```ps 
    Connect-AipService
    ```

    Geben Sie bei entsprechender Aufforderung die Anmeldeinformationen für den Azure Information Protection-Mandantenadministrator ein. In der Regel verwenden Sie ein Konto, das ein globaler Administrator für Azure Active Directory oder Microsoft 365 ist.
    
4. Führen Sie `Get-AipServiceConfiguration` aus, und erstellen Sie eine Kopie des BPOSId-Werts.
    
    Ein Beispiel für die Ausgabe von "Get-aipserviceconfiguration":

    ```ps    
    BPOSId                                   : 23976bc6-dcd4-4173-9d96-dad1f48efd42
        
    RightsManagement ServiceId               : 1a302373-f233-440600909-4cdf305e2e76
        
    LicensingIntranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
    LicensingExtranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
    CertificationIntranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
        
    CertificationExtranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
    ```

5. Trennen Sie die Verbindung mit dem Dienst:

    ```
    Disconnect-AipService
    ```

##### <a name="to-get-the-appprincipalid-and-symmetric-key"></a>So rufen Sie „AppPrincipalId“ und den symmetrischen Schlüssel ab

Erstellen Sie einen neuen Dienstprinzipal, indem Sie das Cmdlet `New-MsolServicePrincipal` aus dem MSOnline-PowerShell-Modul für Azure Active Directory ausführen und den nachstehenden Anweisungen folgen. 

> [!IMPORTANT]
> Erstellen Sie diesen Dienstprinzipal nicht mit dem neueren Azure AD PowerShell-Cmdlet „New-AzureADServicePrincipal“. „New-AzureADServicePrincipal“ wird vom Azure Rights Management-Dienst nicht unterstützt. 

1. Wenn das MSOnline-Modul nicht bereits auf Ihrem Computer installiert ist, führen Sie `Install-Module MSOnline` aus.

2. Starten Sie Windows PowerShell mit der Option **als Administrator ausführen** .

3. Verwenden Sie das Cmdlet **Connect-MsolService** zum Herstellen der Verbindung mit Azure AD:

    ```ps
    Connect-MsolService
    ```

    Wenn Sie dazu aufgefordert werden, geben Sie Ihre Azure AD Mandanten Administrator-Anmelde Informationen ein (in der Regel verwenden Sie ein Konto, das ein globaler Administrator für Azure Active Directory oder Microsoft 365 ist).

4. Führen Sie das Cmdlet „New-MsolServicePrincipal“ aus, um einen neuen Dienstprinzipal zu erstellen:

    ```ps
    New-MsolServicePrincipal
    ```

    Wenn Sie aufgefordert werden, geben Sie Ihren gewünschten Anzeigenamen für diesen Dienstprinzipal ein, der Ihnen dabei hilft, später seinen Zweck als Konto zu identifizieren, sobald Sie die Verbindung mit dem Azure Rights Management-Dienst herstellen, um Dateien zu schützen oder den Schutz aufzuheben.

    Beispielausgabe von „New-MsolServicePrincipal“:

    ```ps
    Supply values for the following parameters:

    DisplayName: AzureRMSProtectionServicePrincipal
    The following symmetric key was created as one was not supplied
    zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=

    Display Name: AzureRMSProtectionServicePrincipal
    ServicePrincipalNames: (b5e3f7g1-b5c2-4c96-a594-a0807f65bba4)
    ObjectId: 23720996-593c-4122-bfc7-1abb5a0b5109
    AppPrincialId: b5e3f76a-b5c2-4c96-a594-a0807f65bba4
    TrustedForDelegation: False
    AccountEnabled: True
    Addresses: ()
    KeyType: Symmetric
    KeyId: 8ef61651-ca11-48ea-a350-25834a1ba17c
    StartDate: 3/7/2014 4:43:59 AM
    EndDate: 3/7/2014 4:43:59 AM
    Usage: Verify
    ```

5. Notieren Sie sich in dieser Ausgabe den symmetrischen Schlüssel und die „AppPrincialId“.

    Es ist wichtig, dass Sie sich jetzt eine Kopie dieses symmetrischen Schlüssels machen. Sie können diesen Schlüssel später nicht abrufen, wenn Sie ihn also bei der nächsten Authentifizierung für den Azure Rights Management-Dienst nicht kennen, müssen Sie einen neuen Dienstprinzipal erstellen.

In diesen Anweisungen und Beispielen finden wir die drei Bezeichner, die zum Ausführen von „RMSServerAuthentication“ erforderlich sind:

- Mandanten-ID: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- Symmetrischer Schlüssel: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

Unser Beispielbefehl würde wie folgt aussehen:

```ps
Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42
```

Wie im vorherigen Befehl gezeigt, können Sie die Werte mit einem einzigen Befehl bereitstellen. Dieser würde in einem Skript ohne Benutzereingriff ausgeführt werden. Zu Testzwecken können Sie jedoch einfach „Set-RMSServerAuthentication“ eintippen und die Werte nacheinander eingeben, wenn Sie dazu aufgefordert werden. Wenn der Befehl abgeschlossen ist, arbeitet der Client nun im „Servermodus“, der für die Verwendung ohne Benutzereingriff wie bei Skripts und Windows Server-Dateiklassifizierungsinfrastruktur geeignet ist.

Erwägen Sie, dieses Dienstprinzipalkonto zum Administrator zu machen: Dieses Dienstprinzipalkonto kann als Administrator konfiguriert werden, um sicherzustellen, dass es für andere Benutzer immer Dateien schützen oder deren Schutz aufheben kann. Auf dieselbe Weise wie bei der Konfiguration eines Standardbenutzer Kontos als Administrator verwenden Sie dasselbe Azure RMS Cmdlet [Add-aipservicesuperuser](/powershell/module/aipservice/add-aipservicesuperuser), aber geben Sie den **serviceprincipalid-** Parameter mit Ihrem appprincipalid-Wert an.

Weitere Informationen zu Administratoren finden Sie unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](../configure-super-users.md).

> [!NOTE]
> Wenn Sie Ihr eigenes Konto zum Authentifizieren für den Azure Rights Management-Dienst verwenden möchten, müssen Sie „Set-RMSServerAuthentication“ nicht ausführen, bevor Sie Dateien schützen, den Schutz von Dateien aufheben oder Vorlagen abrufen.

#### <a name="prerequisite-4-for-regions-outside-north-america"></a>Voraussetzung 4: Für Regionen außerhalb von Nordamerika

Wenn Sie ein Dienstprinzipalkonto zum Schützen von Dateien und zum Herunterladen von Vorlagen außerhalb der Azure-Region Nordamerika verwenden, müssen Sie die Registrierung bearbeiten: 

1. Führen Sie das Get-AipServiceConfiguration-Cmdlet erneut aus, und notieren Sie sich die Werte für **certificationextranetdistributionpointurl** und **licensingextranetdistributionpointurl**.

2. Öffnen Sie auf jedem Computer, auf dem Sie die AzureInformationProtection-Cmdlets ausführen möchten, den Registrierungs-Editor.

3. Navigieren Sie zu folgendem Pfad: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation`. 

    Wenn die Schlüssel **MSIPC** oder **ServiceLocation** nicht angezeigt werden, erstellen Sie sie.

4. Erstellen Sie für den Schlüssel **ServiceLocation** zwei Schlüssel, wenn diese nicht bereits vorhanden sind: **EnterpriseCertification** und **EnterprisePublishing**. 

    Ändern Sie für den Zeichenfolgenwert, der für diese Schlüssel automatisch erstellt wird, nicht den Namen „(Default)“ (Standard), bearbeiten Sie jedoch die Zeichenfolge, um die Wertdaten festzulegen:

   - Fügen Sie für **EnterpriseCertification** den „CertificationExtranetDistributionPointUrl“-Wert ein.

   - Fügen Sie für **EnterprisePublishing** den „LicensingExtranetDistributionPointUrl“-Wert ein.

     Beispielsweise sollte Ihr Registrierungseintrag für EnterpriseCertification in etwa wie folgt aussehen:

     ![Bearbeiten der Registrierung für das PowerShell-Modul von Azure Information Protection für Regionen außerhalb von Nordamerika](../media/registry-example-rmsprotection.png)

5. Schließen Sie den Registrierungs-Editor. Sie müssen den Computer nicht neu starten. Wenn Sie jedoch ein Dienstprinzipalkonto anstelle Ihres eigenen Benutzerkontos verwenden, müssen Sie den Befehl „Set-RMSServerAuthentication“ ausführen, nachdem dieser Registrierungseintrag bearbeitet wurde.

### <a name="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service"></a>Beispielszenarien für die Verwendung der Cmdlets für Azure Information Protection und den Azure Rights Management-Dienst

Zum klassifizieren und schützen von Dateien ist es effizienter, Bezeichnungen zu klassifizieren und zu schützen, weil Sie nur zwei Cmdlets benötigen, die Sie selbst oder in kombinieren können: [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) und [Set-aipfilelabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel). Weitere Informationen und Beispiele finden Sie in der Hilfe zu diesen beiden Cmdlets.

Wenn Sie Dateien jedoch über eine direkte Verbindung mit dem Azure Rights Management-Dienst schützen oder den Schutz aufheben möchten, müssen Sie in der Regel eine Reihe von Cmdlets gemäß der folgenden Beschreibung ausführen.

Geben Sie zunächst in einer PowerShell-Sitzung Folgendes ein, wenn Sie sich für den Azure Rights Management-Dienst mit einem Dienstprinzipalkonto authentifizieren müssen, anstatt Ihr eigenes Konto zu verwenden:

```ps
Set-RMSServerAuthentication
```

Geben Sie nach der entsprechenden Aufforderung die drei Bezeichner ein, wie unter [Voraussetzung 3: Dateien ohne Benutzerinteraktion schützen oder deren Schutz aufheben](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction) beschrieben.

Bevor Sie Dateien schützen können, müssen Sie die Rights Management-Vorlagen auf Ihren Computer herunterladen und die zu verwendende Vorlage sowie ihre zugehörige ID-Nummer ermitteln. In der Ausgabe können Sie dann die Vorlagen-ID kopieren:

```ps
Get-RMSTemplate
```
Ihre Ausgabe sieht etwa wie folgt aus:

```ps
TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
CultureInfo       : en-US
Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
Name              : Contoso, Ltd - Confidential View Only
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True

TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
CultureInfo       : en-US
Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
Name              : Contoso, Ltd - Confidential
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True
FromTemplate      : True
```

Wenn Sie nicht den Befehl „Set-RMSServerAuthentication“ ausgeführt haben, werden Sie beim Azure Rights Management-Dienst mit Ihrem eigenen Benutzerkonto authentifiziert. Wenn Sie sich auf einem in eine Domäne eingebundenen Computer befinden, werden immer automatisch Ihre aktuellen Anmeldeinformationen verwendet. Wenn Sie sich auf einem Arbeitsgruppencomputer befinden, werden Sie zur Anmeldung bei Azure aufgefordert, und diese Anmeldeinformationen werden dann für nachfolgende Befehle zwischengespeichert. Verwenden Sie in diesem Szenario das Cmdlet `Clear-RMSAuthentication`, wenn Sie sich später als anderer Benutzer anmelden müssen.

Nachdem Sie die Vorlagen-ID kennen, können Sie sie mit dem Cmdlet `Protect-RMSFile` verwenden, um eine einzelne Datei oder alle Dateien in einem Ordner zu schützen. Wenn Sie z. B. nur eine einzelne Datei schützen und das Original mithilfe der Vorlage „Contoso, Ltd – Vertraulich“ überschreiben möchten:

```ps
Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
InputFile             EncryptedFile
---------             -------------
C:\Test.docx          C:\Test.docx
```

Verwenden Sie den Parameter **-Folder** mit einem Laufwerkbuchstaben und Pfad oder UNC-Pfad, um alle Dateien in einem Ordner zu schützen. Beispiel:

```ps
Protect-RMSFile -Folder \Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
InputFile                          EncryptedFile
---------                          -------------
\Server1\Documents\Test1.docx     \Server1\Documents\Test1.docx
\Server1\Documents\Test2.docx     \Server1\Documents\Test2.docx
\Server1\Documents\Test3.docx     \Server1\Documents\Test3.docx
\Server1\Documents\Test4.docx     \Server1\Documents\Test4.docx
```

Wenn die Dateierweiterung nicht geändert wird, nachdem der Schutz angewendet wurde, können Sie später immer das Cmdlet `Get-RMSFileStatus` verwenden, um zu prüfen, ob die Datei geschützt ist. Beispiel:

```ps
Get-RMSFileStatus -File \Server1\Documents\Test1.docx
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
FileName                              Status
--------                              ------
\Server1\Documents\Test1.docx         Protected
```

Sie müssen die Rechte „Besitzer“ oder „Extrahieren“ für das Konto besitzen, mit dem die Datei geschützt wurde, um den Schutz einer Datei aufheben zu können. Oder Sie müssen Die Cmdlets als Administrator ausführen. Verwenden Sie anschließend das Cmdlet zum Aufheben des Schutzes. Beispiel:

```ps
Unprotect-RMSFile C:\test.docx -InPlace
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
InputFile                             DecryptedFile
---------                             -------------
C:\Test.docx                          C:\Test.docx
```

Beachten Sie: Wenn die Rights Management-Vorlagen geändert werden, müssen Sie sie erneut mit `Get-RMSTemplate -force` herunterladen. 

## <a name="active-directory-rights-management-services"></a>Active Directory-Rechteverwaltungsdienste

Lesen Sie diesen Abschnitt, bevor Sie damit beginnen, Dateien mithilfe der PowerShell-Befehle zu schützen bzw. deren Schutz aufzuheben, wenn in Ihrer Organisation nur Active Directory Rights Management Services verwendet werden.


### <a name="prerequisites"></a>Voraussetzungen

Zusätzlich zu den Voraussetzungen für die Installation des Moduls „AzureInformationProtection“ muss das für den Schutz bzw. die Aufhebung des Schutzes verwendete Konto über die Berechtigungen zum Lesen und Ausführen verfügen, um auf „ServerCertification.asmx“ zugreifen zu können:

1. Melden Sie sich an einem AD RMS-Server an.

2. Klicken Sie auf **Start** und dann auf **Computer**.

3. Navigieren Sie im Datei-Explorer zu „%systemdrive%\Initpub\wwwroot\_Wmsc\Certification“.

4. Klicken Sie mit der rechten Maustaste auf **ServerCertification.asmx**, und klicken Sie dann auf **Eigenschaften**.

5. Klicken Sie im Dialogfeld mit den Eigenschaften von **ServerCertification.asmx** auf die Registerkarte **Sicherheit**. 

6. Klicken Sie auf die Schaltfläche **Weiter** oder **Bearbeiten**. 

7. Klicken Sie im Dialogfeld **Berechtigungen für ServerCertification.asmx** auf **Hinzufügen**. 

8. Fügen Sie Ihren Kontonamen hinzu. Wenn diese Cmdlets auch von anderen AD RMS-Administratoren oder Dienstkonten verwendet werden, um Dateien zu schützen oder deren Schutz aufzuheben, fügen Sie auch diese Konten hinzu. 

    Um Dateien nicht interaktiv zu schützen oder deren Schutz aufzuheben, fügen Sie die relevanten Computerkonten hinzu. Fügen Sie beispielsweise das Computerkonto des Windows Server-Computers hinzu, für den die Dateiklassifizierungsinfrastruktur konfiguriert ist und der ein PowerShell-Skript verwendet, um Dateien zu schützen.

9. Stellen Sie in der Spalte **Zulassen** sicher, dass die Kontrollkästchen für **Lesen und Ausführen** und **Lesen** aktiviert sind.

Klicken Sie zweimal auf **OK**.

### <a name="example-scenarios-for-using-the-cmdlets-for-active-directory-rights-management-services"></a>Beispielszenarien für die Verwendung der Cmdlets für Active Directory Rights Management Services

Ein typisches Szenario für diese Cmdlets ist das Schützen aller Dateien in einem Ordner mithilfe einer Vorlage für Benutzerrichtlinien oder das Aufheben des Schutzes einer Datei. 

Wenn Sie über mehrere Bereitstellungen von AD RMS verfügen, benötigen Sie zunächst die Namen der AD RMS-Server, die Sie mithilfe des Cmdlets „Get-RMSServer“ zum Anzeigen aller verfügbaren Server erhalten:

```ps
Get-RMSServer
```
Ihre Ausgabe sieht etwa wie folgt aus:

```ps
Number of RMS Servers that can provide templates: 2 
ConnectionInfo             DisplayName          AllowFromScratch
--------------             -------------        ----------------
Microsoft.InformationAnd…  RmsContoso                       True
Microsoft.InformationAnd…  RmsFabrikam                      True
```

Bevor Sie Dateien schützen können, müssen Sie eine Liste von RMS-Vorlagen abrufen, um die zu verwendende Vorlage und ihre zugehörige ID-Nummer zu ermitteln. Der RMS-Server muss nur angegeben werden, wenn Sie über mehrere AD RMS-Bereitstellungen verfügen. 

In der Ausgabe können Sie dann die Vorlagen-ID kopieren:

```ps
Get-RMSTemplate -RMSServer RmsContoso
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
CultureInfo       : en-US
Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
Name              : Contoso, Ltd - Confidential View Only
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True

TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
CultureInfo       : en-US
Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
Name              : Contoso, Ltd - Confidential
IssuerDisplayName : Contoso, Ltd
FromTemplate      : True
FromTemplate      : True
```

Nachdem Sie die Vorlagen-ID kennen, können Sie sie mit dem Cmdlet „Protect-RMSFile“ verwenden, um eine einzelne Datei oder alle Dateien in einem Ordner zu schützen. Wenn Sie z. B. nur eine einzelne Datei schützen und das Original mithilfe der Vorlage „Contoso, Ltd – Vertraulich“ ersetzen möchten:

```ps
Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
InputFile             EncryptedFile
---------             -------------
C:\Test.docx          C:\Test.docx   
```

Verwenden Sie den Parameter „-Folder“ mit einem Laufwerkbuchstaben und Pfad oder UNC-Pfad, um alle Dateien in einem Ordner zu schützen. Beispiel:

```ps
Protect-RMSFile -Folder \\Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
InputFile                          EncryptedFile
---------                          -------------
\\Server1\Documents\Test1.docx     \\Server1\Documents\Test1.docx   
\\Server1\Documents\Test2.docx     \\Server1\Documents\Test2.docx   
\\Server1\Documents\Test3.docx     \\Server1\Documents\Test3.docx   
\\Server1\Documents\Test4.docx     \\Server1\Documents\Test4.docx   
```

Wenn die Dateierweiterung nicht geändert wird, nachdem der Schutz angewendet wurde, können Sie später immer das Cmdlet „Get-RMSFileStatus“ verwenden, um zu prüfen, ob die Datei geschützt ist. Beispiel: 

```ps
Get-RMSFileStatus -File \\Server1\Documents\Test1.docx
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
FileName                              Status
--------                              ------
\\Server1\Documents\Test1.docx        Protected
```

Sie müssen die Nutzungsrechte „Besitzer“ oder „Extrahieren“ für das Konto besitzen, mit dem die Datei geschützt wurde, oder Sie müssen Administrator für AD RMS sein, um den Schutz einer Datei aufheben zu können. Verwenden Sie anschließend das Cmdlet zum Aufheben des Schutzes. Beispiel:

```ps
Unprotect-RMSFile C:\test.docx -InPlace
```

Ihre Ausgabe sieht etwa wie folgt aus:

```ps
InputFile                             DecryptedFile
---------                             -------------
C:\Test.docx                          C:\Test.docx
```

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection

Sie können die Bezeichnungs-Cmdlets nicht interaktiv ausführen, indem Sie das Cmdlet **Set-AIPAuthentication** verwenden. Auch für die Azure Information Protection-Überprüfung ist ein nicht interaktiver Vorgang erforderlich.

Wenn Sie die Cmdlets für die Bezeichnung ausführen, werden die Befehle in Ihrem eigenen Benutzerkontext in einer interaktiven PowerShell-Sitzung ausgeführt. Um sie unbeaufsichtigt auszuführen, erstellen Sie für diesen Zweck ein neues Azure AD-Benutzerkonto. Führen Sie dann im Kontext dieses Benutzers das Cmdlet „Set-AIPAuthentication“ zum Festlegen und Speichern von Anmeldeinformationen mithilfe eines Azure AD-Zugriffstokens aus. Dieses Benutzerkonto wird dann authentifiziert und für den Azure Rights Management-Dienst gestartet. Das Konto lädt die Azure Information Protection-Richtlinie und alle Rights Management-Vorlagen herunter, die die Bezeichnungen verwenden.

> [!NOTE]
> Wenn Sie [bereichsbezogene Richtlinien](../configure-policy-scope.md) verwenden, denken Sie bitte daran, dass Sie dieses Konto möglicherweise zu Ihren bereichsbezogenen Richtlinien hinzufügen müssen.

Bei der ersten Ausführung dieses Cmdlets werden Sie aufgefordert, sich bei Azure Information Protection anzumelden. Geben Sie den Namen und das Kennwort des Benutzerkontos ein, das Sie für den unbeaufsichtigten Benutzer erstellt haben. Danach kann dieses Konto dann die Bezeichnungs-Cmdlets bis zum Ablaufen des Authentifizierungstokens ohne Benutzereingriff ausführen. 

Damit sich das Benutzerkonto beim ersten Mal interaktiv anmelden kann, muss dem Konto die Berechtigung **Lokales Anmelden** zugewiesen sein. Diese Berechtigung ist Benutzerkonten standardmäßig zugewiesen, aber Ihre Unternehmensrichtlinien lassen diese Konfiguration für Dienstkonten unter Umständen nicht zu. In diesem Fall können Sie „Set-AIPAuthentication“ mit dem *Token*-Parameter ausführen, sodass die Authentifizierung ohne Anmeldeaufforderung abgeschlossen wird. Sie können diesen Befehl als geplanten Task ausführen und dem Konto die niedrigere Berechtigung **Als Batchauftrag anmelden** erteilen. Weitere Informationen finden Sie in den folgenden Abschnitten. 

Wenn das Token abläuft, führen Sie das Cmdlet erneut aus, um ein neues Token abzurufen.

Wenn Sie dieses Cmdlet ohne Parameter ausführen, erhält das Konto ein Zugriffstoken, das 90 Tage oder bis zum Ablauf des Kennworts gültig ist.  

Um zu steuern, wann das Zugriffstoken abläuft, führen Sie dieses Cmdlet mit Parametern aus. Dadurch können Sie konfigurieren, dass das Zugriffstoken ein oder zwei Jahre gültig ist bzw. nie abläuft. Diese Konfiguration erfordert, dass Sie zwei Anwendungen in Azure Active Directory registrieren: eine **Web-App-/API**-Anwendung und eine **native Anwendung**. Die Parameter für dieses Cmdlet sind Werte dieser Anwendungen.

Nachdem Sie dieses Cmdlet ausgeführt haben, können Sie die Bezeichnungs-Cmdlets im Kontext des Benutzerkontos ausführen, das Sie erstellt haben.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>So erstellen und konfigurieren Sie die Azure AD-Anwendungen für „Set-AIPAuthentication“

1. Melden Sie sich in einem neuen Browserfenster beim [Azure-Portal](https://portal.azure.com/) an.

2. Navigieren Sie für den Azure AD Mandanten, den Sie mit Azure Information Protection verwenden, zu **Azure Active Directory**  >  **Manage**  >  **App-Registrierungen**. 

3. Wählen Sie **+ neue Registrierung** aus, um Ihre Web-App/API-Anwendung zu erstellen. Geben Sie im Bereich **Anwendung registrieren** die folgenden Werte an, und klicken Sie dann auf **registrieren**:

   - **Name**: `AIPOnBehalfOf`
        
        Wenn Sie möchten, können Sie auch einen anderen Namen angeben. Der Name muss pro Mandant eindeutig sein.
    
    - **Unterstützte Konto Typen**: **nur Konten in diesem Organisations Verzeichnis**
    
    - **Umleitungs-URI (optional)**: **Web** und `http://localhost`

4. Kopieren Sie im Bereich **aiponbehalfof** den Wert für die **Anwendungs-ID (Client)**. Der Wert sieht in etwa wie im folgenden Beispiel aus: `57c3c1c3-abf9-404e-8b2b-4652836c8c66` . Dieser Wert wird für den *webappid* -Parameter verwendet, wenn Sie das Set-AIPAuthentication-Cmdlet ausführen. Fügen Sie den Wert ein, und speichern Sie ihn später.

5. Wählen Sie im Bereich **aiponbehalfof** im Menü **Verwalten** die Option **Authentifizierung** aus.

6. Aktivieren Sie im Bereich **aiponbehalfof-Authentication** im Abschnitt **Erweiterte Einstellungen** das Kontrollkästchen **ID Tokens** , und wählen Sie dann **Speichern** aus.

7. Wählen Sie im Bereich **aiponbehalfof-Authentication** im Menü **Verwalten** die Option **Zertifikate & Geheimnissen** aus.

8. Wählen Sie im Bereich **aiponbehalfof--Zertifikate &** geheimen Schlüssel im Abschnitt geheime **Client** Schlüssel die Option **+ neuer geheimer Client** Schlüssel aus. 

9. Geben Sie unter **geheimen Client Schlüssel hinzufügen** Folgendes an, und wählen Sie dann **Hinzufügen** aus:
    
    - **Beschreibung**: `Azure Information Protection client`
    - **Läuft** ab: Geben Sie die gewünschte Dauer an (1 Jahr, 2 Jahre oder läuft nie ab).

9. Kopieren Sie im Bereich **aiponbehalfof--Zertifikate & geheimen** Schlüssel im Abschnitt geheime **Client** Schlüssel die Zeichenfolge für den **Wert**. Diese Zeichenfolge sieht in etwa wie im folgenden Beispiel aus: `+LBkMvddz?WrlNCK5v0e6_=meM59sSAn` . Um sicherzustellen, dass Sie alle Zeichen kopieren, wählen Sie das Symbol aus, das **in die Zwischenablage kopiert** wird. 
    
    Es ist wichtig, dass diese Zeichenfolge gespeichert wird, da sie nicht erneut angezeigt wird und nicht abgerufen werden kann. Speichern Sie wie bei allen vertraulichen Informationen, die Sie verwenden, den gespeicherten Wert sicher, und beschränken Sie den Zugriff darauf.

10. Wählen Sie im Bereich **aiponbehalfof--Zertifikate & geheimen** Schlüssel im Menü **Verwalten** die **Option API** verfügbar machen aus.

11. Wählen Sie im Bereich **aiponbehalfof-macht eine API** den Wert für die **Option Anwendungs-ID-URI** **festlegen** aus, und ändern Sie im Wert Anwendungs- **ID-URI** den Wert **API** zu **http**. Diese Zeichenfolge sieht in etwa wie im folgenden Beispiel aus: `http://d244e75e-870b-4491-b70d-65534953099e` . 
    
    Wählen Sie **Speichern** aus.

12. Wählen Sie im Bereich **aiponbehalfof-API verfügbar** machen die Option **+ Bereich hinzufügen** aus.

13. Geben Sie im **Bereich Bereich hinzufügen** Folgendes an, und verwenden Sie die vorgeschlagenen Zeichen folgen als Beispiele, und wählen Sie dann **Bereich hinzufügen** aus:
    - **Bereichsname**: `user-impersonation`
    - **Zum Einwilligen berechtigte Personen**: **Administratoren und Benutzer**
    - **Anzeigename der Administratoreinwilligung**: `Access Azure Information Protection scanner`
    - **Beschreibung der Administratoreinwilligung**: `Allow the application to access the scanner for the signed-in user`
    - **Anzeigename der Benutzereinwilligung**: `Access Azure Information Protection scanner`
    - **Beschreibung der Benutzereinwilligung**: `Allow the application to access the scanner for the signed-in user`
    - **Status**: **aktiviert** (Standard)


14. Schließen Sie den Bereich " **aiponbehalfof-API verfügbar** machen" in diesem Bereich.

15. Wählen Sie **API-Berechtigungen anfordern** aus.

16. Wählen Sie im Bereich **aiponbehalfof**  |  **API-Berechtigungen** die Option **+ Berechtigung hinzufügen** aus.

17. Wählen Sie **Azure Right Management** aus, wählen Sie **Delegierte Berechtigungen** aus, und wählen Sie dann **geschützte Inhalte für Benutzer erstellen und zugreifen aus**.

18. Klicken Sie auf **Berechtigung hinzufügen**.

19. Wählen Sie im **Bereich API-Berechtigungen** im Abschnitt **Zustimmung erteilen** die Option **Administrator Zustimmung erteilen für <your tenant name>** aus, und wählen Sie für die Bestätigungsaufforderung **Ja** aus.

20. Wählen Sie im Bereich **App-Registrierungen** die Option **+ neue Anwendungs Registrierung** aus, um die native Anwendung jetzt zu erstellen.

21. Geben Sie im Bereich **Anwendung registrieren** die folgenden Einstellungen an, und klicken Sie dann auf **registrieren**:
    - **Name**: `AIPClient`
    - **Unterstützte Konto Typen**: **nur Konten in diesem Organisations Verzeichnis**
    - **Umleitungs-URI (optional)**: **öffentlicher Client (Mobile & Desktop)** und `http://localhost`

22. Kopieren Sie im Bereich **aipclient** den Wert der Anwendungs- **ID (Client)**. Der Wert sieht in etwa wie im folgenden Beispiel aus: `8ef1c873-9869-4bb1-9c11-8313f9d7f76f` . 
    
    Dieser Wert wird für den nativeappid-Parameter verwendet, wenn Sie das Set-AIPAuthentication-Cmdlet ausführen. Fügen Sie den Wert ein, und speichern Sie ihn später.

23. Wählen Sie im Bereich **aipclient** im Menü **Verwalten** die Option **Authentifizierung** aus.

24. Wählen Sie im Bereich **aipclient-Authentifizierung** im Menü **Verwalten** die Option **API-Berechtigungen** aus.

25. Wählen Sie im Bereich **aipclient-Berechtigungen** die Option **+ Berechtigung hinzufügen** aus.

26. Wählen Sie im Bereich **API-Berechtigungen anfordern** die Option **meine APIs** aus.

27. Wählen Sie im Abschnitt **API auswählen** die Option **apionbehalfof** aus, und aktivieren Sie dann das Kontrollkästchen für den **Benutzer** Identitätswechsel als Berechtigung. Wählen Sie **Berechtigungen hinzufügen** aus. 

28. Wählen Sie im **Bereich API-Berechtigungen** im Abschnitt **Zustimmung erteilen** die Option **Administrator Zustimmung erteilen für \<*your tenant name*>** aus, und wählen Sie für die Bestätigungsaufforderung **Ja** aus.

Sie haben nun die Konfiguration der beiden apps abgeschlossen, und Sie verfügen über die Werte, die Sie zum Ausführen von [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) mit den Parametern *webappid*, *webappkey* und *nativeappid* benötigen. Aus unseren Beispielen:

```ps
Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "+LBkMvddz?WrlNCK5v0e6_=meM59sSAn" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"
```

Führen Sie diesen Befehl im Kontext des Kontos aus, das die Dokumente ohne Benutzereingriff bezeichnet und schützt. Beispiel: Ein Benutzerkonto für Ihre PowerShell-Skripts oder das Dienstkonto zum Ausführen der Azure Information Protection-Überprüfung.  

Wenn Sie diesen Befehl zum ersten Mal ausführen, werden Sie zur Anmeldung aufgefordert. Dadurch wird das Zugriffstoken für Ihr Konto erstellt und sicher unter „%localappdata%\Microsoft\MSIP“ gespeichert. Nach dieser ersten Anmeldung können Sie Dateien auf dem Computer ohne Benutzereingriff bezeichnen und schützen. Wenn Sie jedoch ein Dienstkonto zum Bezeichnen und Schützen von Dateien verwenden und sich dieses Dienstkonto nicht interaktiv anmelden kann, befolgen Sie die Anweisungen im folgenden Abschnitt, damit das Dienstkonto mithilfe eines Token authentifiziert werden kann.

### <a name="specify-and-use-the-token-parameter-for-set-aipauthentication"></a>Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“

Führen Sie die folgenden zusätzlichen Schritte und Anweisungen aus, um die erste interaktive Anmeldung für ein Konto zu verhindern, das Dateien bezeichnet und schützt. In der Regel sind diese zusätzlichen Schritte nur erforderlich, wenn diesem Konto nicht die Berechtigung **Lokale Anmeldung** erteilt werden kann, ihm jedoch die Berechtigung **Als Batchauftrag anmelden** zugewiesen wird. Dies kann beispielsweise bei Ihrem Dienstkonto der Fall sein, das die Azure Information Protection-Überprüfung ausführt.

Allgemeine Schritte:

1. Erstellen Sie ein PowerShell-Skript auf dem lokalen Computer.

2. Führen Sie „Set-AIPAuthentication“ aus, um ein Zugriffstoken abzurufen und in die Zwischenablage zu kopieren.

3. Ändern Sie das PowerShell-Skript, um das Token aufzunehmen.

4. Erstellen Sie einen Task, der das PowerShell-Skript im Kontext des Dienstkontos ausführt, das zum Bezeichnen und Schützen von Dateien verwendet wird.

5. Vergewissern Sie sich, dass das Token für das Dienstkonto gespeichert wurde, und löschen Sie das PowerShell-Skript.

#### <a name="step-1-create-a-powershell-script-on-your-local-computer"></a>Schritt 1: Erstellen eines PowerShell-Skripts auf dem lokalen Computer

1. Erstellen Sie auf Ihrem Computer ein neues PowerShell-Skript mit dem Namen „Aipauthentication.ps1“.

2. Kopieren Sie den folgenden Befehl, und fügen Sie ihn in das folgende Skript ein:

    ```ps
    Set-AIPAuthentication -WebAppId <ID of the "Web app / API" application> -WebAppKey <key value generated in the "Web app / API" application> -NativeAppId <ID of the "Native" application > -Token <token value>
    ```

3. Ändern Sie anhand der Anweisungen im vorhergehenden Abschnitt diesen Befehl. Geben Sie dabei Ihre eigenen Werte für die Parameter **WebAppId**, **WebAppkey** und **NativeAppId** an. Zu diesem Zeitpunkt besitzen Sie den Wert für den **Token**-Parameter noch nicht. Sie geben ihn später an. 

    Beispiel: 

    ```ps
    Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f -Token <token value>
    ```

#### <a name="step-2-run-set-aipauthentication-to-get-an-access-token-and-copy-it-to-the-clipboard"></a>Schritt 2: Ausführen von „Set-AIPAuthentication“ zum Abrufen eines Zugriffstokens und Kopieren des Tokens in die Zwischenablage

1. Öffnen Sie eine Windows PowerShell-Sitzung.

2. Führen Sie den folgenden Befehl aus. Verwenden Sie dabei die gleichen Werte wie im Skript:

    ```ps
    (Set-AIPAuthentication -WebAppId <ID of the "Web app / API" application>  -WebAppKey <key value generated in the "Web app / API" application> -NativeAppId <ID of the "Native" application >).token | clip
    ```

    Beispiel: 

    ```ps
    (Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip`
    ```

#### <a name="step-3-modify-the-powershell-script-to-supply-the-token"></a>Schritt 3: Ändern des PowerShell-Skripts zum Bereitstellen des Tokens

1. Geben Sie in Ihrem PowerShell-Skript den Tokenwert ein, indem Sie die Zeichenfolge aus der Zwischenablage einfügen. Speichern Sie anschließend die Datei.

2. Signieren Sie das Skript. Sollten Sie das Skript nicht signieren (eine Signatur erhöht die Sicherheit), muss Windows PowerShell auf dem Computer konfiguriert werden, auf dem die Befehle zum Bezeichnen ausgeführt werden. Führen Sie beispielsweise eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen** aus, und geben Sie Folgendes ein: `Set-ExecutionPolicy RemoteSigned`. Diese Konfiguration ermöglicht allerdings die Ausführung aller unsignierten Skripts, wenn diese auf diesem Computer gespeichert sind (weniger sicher).

    Weitere Informationen zum Signieren von Windows PowerShell-Skripts finden Sie in der PowerShell-Dokumentationsbibliothek unter [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

3. Kopieren Sie dieses PowerShell-Skript auf den Computer, der zum Bezeichnen und Schützen von Dateien verwendet wird, und löschen Sie das Original auf Ihrem Computer. Beispielsweise Kopieren Sie das PowerShell-Skript in **C:\Scripts\Aipauthentication.ps1** auf einem Windows Server-Computer.

#### <a name="step-4-create-a-task-that-runs-the-powershell-script"></a>Schritt 4: Erstellen eines Tasks zum Ausführen des PowerShell-Skripts

1. Stellen Sie sicher, dass das Dienstkonto, mit dem Dateien bezeichnet und geschützt werden, über die Berechtigung **Als Batchauftrag anmelden** verfügt.

2. Öffnen Sie auf dem Computer, der zum Bezeichnen und Schützen von Dateien verwendet wird, die Aufgabenplanung, und erstellen Sie einen neuen Task. Konfigurieren Sie diesen Task so, dass er als Dienstkonto ausgeführt wird, mit dem Dateien bezeichnet und geschützt werden. Konfigurieren Sie anschließend die folgenden Werte für die **Aktionen**:

   - **Aktion**: `Start a program`
   - **Programm/Skript**: `Powershell.exe`
   - **Argumente hinzufügen (optional)**: `-NoProfile -WindowStyle Hidden -command "&{C:\Scripts\Aipauthentication.ps1}"` 

     Geben Sie als Argumentzeile Ihren eigenen Pfad und Dateinamen an, wenn diese vom Beispiel abweichen.

3. Führen Sie diesen Task manuell aus.

#### <a name="step-5-confirm-that-the-token-is-saved-and-delete-the-powershell-script"></a>Schritt 5: Vergewissern Sie sich, dass das Token gespeichert ist, und löschen Sie das PowerShell-Skript.

1. Vergewissern Sie sich, dass das Token jetzt im Ordner **%LocalAppData%\microsoft\msip** für das Dienst Konto Profil gespeichert ist. Dieser Wert wird durch das Dienstkonto geschützt.

2. Löschen Sie das PowerShell-Skript, das den Tokenwert enthält (z. b. **Aipauthentication.ps1)**.

    Löschen Sie optional den Task. Wenn das Token abläuft, müssen Sie diese Schritte wiederholen. Daher ist es unter Umständen praktischer, den konfigurierten Task zu behalten, damit er einfacher erneut ausgeführt werden kann, wenn Sie das neue PowerShell-Skript mit dem neuen Tokenwert kopieren.

## <a name="next-steps"></a>Nächste Schritte
Wenn Sie in einer PowerShell-Sitzung Hilfe zum Cmdlet benötigen, geben Sie `Get-Help <cmdlet name> cmdlet` ein, und verwenden Sie dann den Parameter „-online“, um die neuesten Informationen abzurufen. Beispiel: 

```ps
Get-Help Get-RMSTemplate -online
```

Weitere Informationen, die möglicherweise zur Unterstützung des Azure Information Protection-Clients erforderlich sind, finden Sie unter den folgenden Themen:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentkontrolle](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)