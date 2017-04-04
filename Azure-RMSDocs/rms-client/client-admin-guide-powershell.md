---
title: Verwenden von PowerShell mit dem Azure Information Protection-Client
description: "Anweisungen und Informationen für Administratoren zum Verwalten des Azure Information Protection-Clients mithilfe von PowerShell."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 90b26239979b42eadb008b11a963e35a74698910
ms.sourcegitcommit: 16fec44713c7064959ebb520b9f0857744fecce9
translationtype: HT
---
# <a name="using-powershell-with-the-azure-information-protection-client"></a>Verwenden von PowerShell mit dem Azure Information Protection-Client

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Wenn Sie den Azure Information Protection-Client installieren, werden automatisch PowerShell-Befehle installiert, damit Sie den Client durch Ausführen von Befehlen verwalten können, die Sie zur Automatisierung in Skripts einfügen können.

Die Cmdlets werden mit dem PowerShell-Modul **AzureInformationProtection** installiert, das das Modul „RMSProtection“ ersetzt, das mit dem RMS Protection Tool installiert wurde. Wenn beim Installieren des Azure Information Protection-Clients das RMS Protection-Tool installiert ist, wird das Modul „RMSProtection“ automatisch deinstalliert.

Das Modul „AzureInformationProtection“ umfasst alle Rights Management-Cmdlets aus dem RMS Protection Tool sowie zwei neue Cmdlets, die den Azure Information Protection-Dienst für die Bezeichnung verwenden:

|Cmdlet für die Bezeichnung|Beispielsyntax|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/azureinformationprotection/vlatest/get-aipfilestatus)|Für einen freigegebenen Ordner werden alle Dateien mit einer bestimmten Bezeichnung ermittelt.|
|[Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel)|Für einen freigegebenen Ordner wird eine bestimmte Bezeichnung auf alle Dateien ohne Bezeichnung angewendet.|

Eine Übersicht über alle Cmdlets und die entsprechende Hilfe finden Sie unter [AzureInformationProtection-Modul](/powershell/azureinformationprotection/vlatest/aip).

Dieses Modul installiert **\ProgramFiles (x86) \Microsoft Azure Information Protection** und fügt diesen Ordner der Systemvariablen **PSModulePath** hinzu. Die DLL-Datei für dieses Modul lautet **AIP.dll**.

Wie beim Modul „RMSProtection“ weist die aktuelle Version des Moduls „AzureInformationProtection“ die folgenden Einschränkungen auf:

- Sie können den Schutz von persönlichen Outlook-Ordnern (PST-Dateien) aufheben, aber Sie können diese Dateien oder andere Containerdateien derzeit nicht mithilfe dieses PowerShell-Moduls systemeigen schützen.

- Sie können den Schutz von geschützten Outlook-E-Mails (RPMSG-Dateien) aufheben, wenn sie sich im persönlichen Outlook-Ordner (PST) befinden, aber Sie können den Schutz von RPMSG-Dateien nicht außerhalb eines persönlichen Ordners aufheben.

Bevor Sie mit der Verwendung dieser Cmdlets beginnen, betrachten Sie die zusätzlichen Voraussetzungen und Anweisungen, die Ihrer Bereitstellung entsprechen:

- [Azure Information Protection-Dienst und Azure Rights Management-Dienst](#azure-information-protection-service-and-azure-rights-management-service)

    - Zutreffend, wenn Sie die ausschließliche Klassifizierung oder die Klassifizierung mit Rights Management-Schutz verwenden: Sie verfügen über ein Abonnement, das Azure Information Protection (z. B. „Enterprise Mobility + Security“) enthält.
    - Zutreffend, wenn Sie den ausschließlichen Schutz mit dem Azure Rights Management-Dienst verwenden: Sie verfügen über ein Abonnement, das den Azure Rights Management-Dienst (z. B. Office 365 E3 und Office 365 E5) enthält.

- [Active Directory Rights Management Services](#active-directory-rights-management-services)

    - Zutreffend, wenn Sie den ausschließlichen Schutz mit der lokalen Version von Azure Rights Management, Active Directory Rights Management Services (AD RMS), verwenden.


## <a name="azure-information-protection-service-and-azure-rights-management-service"></a>Azure Information Protection-Dienst und Azure Rights Management-Dienst

Lesen Sie diesen Abschnitt, bevor Sie die PowerShell-Befehle verwenden, wenn Ihre Organisation Azure Information Protection und den Azure Rights Management-Datenschutzdienst oder nur den Azure Rights Management-Dienst verwendet.


### <a name="prerequisites-for-aip-and-azure-rms"></a>Voraussetzungen für Azure Information Protection (AIP) und Azure RMS

Zusätzlich zu den Voraussetzungen für die Installation des Moduls „AzureInformationProtection“ sind weitere Komponenten für den Azure Information Protection-Dienst und den Azure Rights Management-Datenschutzdienst erforderlich:

1. Der Azure Rights Management-Dienst muss aktiviert werden.

2. So entfernen Sie den Schutz von Dateien für andere mithilfe Ihres eigenen Kontos: Die Administratorfunktion muss für Ihre Organisation aktiviert werden. Zudem muss Ihr Konto als Administrator für Azure Rights Management konfiguriert sein.

3. So werden Dateien direkt ohne Benutzerinteraktion geschützt oder ihr Schutz entsprechend aufgehoben: Erstellen Sie ein Dienstprinzipalkonto, führen Sie „Set-RMSServerAuthentication“ aus und erwägen Sie, diesen Dienstprinzipal zum Administrator für Azure Rights Management zu machen.

4. Für Regionen außerhalb von Nordamerika: Bearbeiten Sie die Registrierung für die Authentifizierung für den Dienst.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Voraussetzung 1: Der Azure Rights Management-Dienst muss aktiviert werden.

Für diese Voraussetzung können Sie den Datenschutz mithilfe von Bezeichnungen anwenden oder eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen. Konfiguration zur Anwendung des Datenschutzes.

Wenn Ihr Azure Information Protection-Mandant nicht aktiviert ist, finden Sie entsprechende Anweisungen zum [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Voraussetzung 2: Den Schutz von Dateien für andere Benutzer mithilfe Ihres eigenen Kontos entfernen.

Typische Szenarien für das Entfernen des Schutzes von Dateien für andere Benutzer umfassen die Datenermittlung oder Datenwiederherstellung. Wenn Sie den Schutz mithilfe von Bezeichnungen anwenden, können Sie den Schutz durch Festlegen einer neuen Bezeichnung entfernen, durch die kein Schutz angewendet wird. Sie können dazu aber auch die Bezeichnung entfernen. Aber Sie werden wahrscheinlich eher eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen, um den Schutz zu entfernen.

Sie müssen über Rights Management-Berechtigungen verfügen oder Administrator sein, um den Schutz von Dateien zu entfernen. Für die Datenermittlung oder Datenwiederherstellung wird in der Regel die Administratorfunktion verwendet. Informationen zum Aktivieren dieses Feature und zum Konfigurieren Ihres Kontos als Administrator finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](../deploy-use/configure-super-users.md).

#### <a name="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction"></a>Voraussetzungen 3: Dateien ohne Benutzerinteraktion schützen oder deren Schutz aufheben.

Derzeit können Sie Bezeichnungen nicht ohne Interaktion anwenden, aber Sie können ohne Interaktion eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen, um Dateien zu schützen oder ihren Schutz aufzuheben.

Sie müssen einen Dienstprinzipal verwenden, um die Verbindung mit dem Azure Rights Management-Dienst nicht interaktiv herzustellen, wozu Sie das `Set-RMSServerAuthentication`-Cmdlet verwenden. Sie müssen entsprechend für jede Windows PowerShell-Sitzung vorgehen, in der Cmdlets ausgeführt werden, die eine direkte Verbindung mit dem Azure Rights Management-Dienst herstellen. Bevor Sie dieses Cmdlet ausführen, stellen Sie sicher, dass Sie über die folgenden drei Bezeichner verfügen:

- BposTenantId

- AppPrincipalId

- Symmetrischer Schlüssel

In den nächsten Abschnitten wird erläutert, wie Sie diese Bezeichner erhalten.

##### <a name="to-get-the-bpostenantid"></a>So rufen Sie „BposTenantId“ ab

Führen Sie das Cmdlet „Get-AadrmConfiguration“ aus dem Azure RMS Windows PowerShell-Modul aus:

1. Wenn dieses Modul nicht bereits auf Ihrem Computer installiert ist, finden Sie entsprechende Informationen unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

2. Starten Sie die Windows PowerShell mit der Option **Als Administrator ausführen**.

3. Stellen Sie die Verbindung mit dem Azure Rights Management-Dienst mithilfe des Cmdlets `Connect-AadrmService` her:
    
        Connect-AadrmService
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des Azure Information Protection-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).
    
4. Führen Sie `Get-AadrmConfiguration` aus, und erstellen Sie eine Kopie des BPOSId-Werts.
    
    Nachfolgend finden Sie ein Beispiel für die Ausgabe von „Get-AadrmConfiguration“:
    
            BPOSId                                   : 23976bc6-dcd4-4173-9d96-dad1f48efd42
        
            RightsManagement ServiceId               : 1a302373-f233-440600909-4cdf305e2e76
        
            LicensingIntranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            LicensingExtranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            CertificationIntranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
        
            CertificationExtranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification

5. Trennen Sie die Verbindung mit dem Dienst:
    
        Disconnect-AadrmService

##### <a name="to-get-the-appprincipalid-and-symmetric-key"></a>So rufen Sie „AppPrincipalId“ und den symmetrischen Schlüssel ab

Erstellen Sie einen neuen Dienstprinzipal, indem Sie das Cmdlet `New-MsolServicePrincipal` aus dem MSOnline-PowerShell-Modul für Azure Active Directory ausführen: 

1. Wenn dieses Modul nicht bereits auf Ihrem Computer installiert ist, finden Sie entsprechende Informationen unter [Installieren des Azure AD-Moduls](/powershell/azuread/#install-the-azure-ad-module).

2. Starten Sie die Windows PowerShell mit der Option **Als Administrator ausführen**.

3. Verwenden Sie das Cmdlet **Connect-MsolService** zum Herstellen der Verbindung mit Azure AD:
    
        Connect-MsolService
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des Azure AD-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

4. Führen Sie das Cmdlet „New-MsolServicePrincipal“ aus, um einen neuen Dienstprinzipal zu erstellen:
    
        New-MsolServicePrincipal
    
    Wenn Sie aufgefordert werden, geben Sie Ihren gewünschten Anzeigenamen für diesen Dienstprinzipal ein, der Ihnen dabei hilft, später seinen Zweck als Konto zu identifizieren, wenn Sie die Verbindung mit dem Azure Rights Management-Dienst herstellen, um Dateien zu schützen oder den Schutz aufzuheben.
    
    Beispielausgabe von „New-MsolServicePrincipal“:
    
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

5. Notieren Sie sich in dieser Ausgabe den symmetrischen Schlüssel und die „AppPrincialId“.

    Es ist besonders wichtig, dass Sie eine Kopie des symmetrischen Schlüssels erstellen, da Sie ihn später nicht vollständig abrufen können. Wenn Sie den Schlüssel nicht kennen, müssen Sie einen neuen Dienstprinzipal erstellen, wenn Sie sich das nächste Mal für den Azure Rights Management-Dienst authentifizieren müssen.

In diesen Anweisungen und Beispielen finden wir die drei Bezeichner, die zum Ausführen von „RMSServerAuthentication“ erforderlich sind:

- Mandanten-ID: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- Symmetrischer Schlüssel: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

Unser Beispielbefehl würde wie folgt aussehen:

    Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42

Wie im vorherigen Befehl gezeigt, können Sie die Werte mit einem einzelnen Befehl bereitstellen oder nur „RMSServerAuthentication“ eingeben und die Werte nacheinander bereitstellen, wenn Sie dazu aufgefordert werden. Wenn der Befehl abgeschlossen ist, wird „**RmsServerAuthentication ist auf EIN festgelegt**“ angezeigt. Das bedeutet, dass Sie Dateien jetzt mithilfe des Dienstprinzipals schützen oder deren Schutz aufheben können.

Erwägen Sie es, diesen Dienstprinzipal zum Administrator zu machen: Dieser Dienstprinzipal kann als Administrator konfiguriert werden, um sicherzustellen, dass er für andere Benutzer immer Dateien schützen oder deren Schutz aufheben kann. Wie beim Konfigurieren eines Standardbenutzerkontos als Administrator verwenden Sie dasselbe Azure RMS-Cmdlet, [Add-AadrmSuperUser](/powershell/aadrm/vlatest/Add-AadrmSuperUser.md), wobei Sie jedoch für den Parameter **-ServicePrincipalId** Ihren AppPrincipalId-Wert angeben.

Weitere Informationen zu Administratoren finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](../deploy-use/configure-super-users.md).

> [!NOTE]
> Wenn Sie Ihr eigenes Konto zum Authentifizieren für den Azure Rights Management-Dienst verwenden möchten, müssen Sie „Set-RMSServerAuthentication“ nicht ausführen, bevor Sie Dateien schützen, den Schutz von Dateien aufheben oder Vorlagen abrufen.

#### <a name="prerequisite-4-for-regions-outside-north-america"></a>Voraussetzung 4: Für Regionen außerhalb von Nordamerika

Für die Authentifizierung außerhalb von Azure-Nordamerika müssen Sie die Registrierung wie folgt bearbeiten. Wenn sich Ihr Azure Information Protection-Mandant in Nordamerika befindet, führen Sie diesen Schritt nicht aus:

1. Führen Sie das Cmdlet „Get-AadrmConfiguration“ erneut aus, und notieren Sie sich die Werte für **CertificationExtranetDistributionPointUrl** und **LicensingExtranetDistributionPointUrl**.

2. Öffnen Sie auf jedem Computer, auf dem Sie die „AzureInformationProtection“-Cmdlets ausführen, den Registrierungs-Editor und navigieren Sie zu: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC`

3. Wenn der Schlüssel **ServiceLocation** nicht angezeigt wird, erstellen Sie ihn, damit der Registrierungspfad wie folgt aussieht: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation**

4. Erstellen Sie für den Schlüssel **ServiceLocation** zwei Schlüssel, wenn diese nicht bereits vorhanden sind: **EnterpriseCertification** und **EnterprisePublishing**. 
    
    Wenn Sie diese REG_SZ-Schlüssel erstellen, ändern Sie nicht den Namen „(Standard)“, aber bearbeiten Sie sie, um die Daten für den Wert festzulegen:

    - Fügen Sie für **EnterpriseCertification** den „CertificationExtranetDistributionPointUrl“-Wert ein.
    
    - Fügen Sie für **EnterprisePublishing** den „LicensingExtranetDistributionPointUrl“-Wert ein.

5. Schließen Sie den Registrierungs-Editor. Sie müssen den Computer nicht neu starten. Wenn Sie jedoch ein Dienstprinzipalkonto anstelle Ihres eigenen Benutzerkontos verwenden, müssen Sie den Befehl „Set-RMSServerAuthentication“ ausführen, nachdem dieser Registrierungseintrag bearbeitet wurde.

### <a name="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service"></a>Beispielszenarien für die Verwendung der Cmdlets für Azure Information Protection und den Azure Rights Management-Dienst

Es ist effizienter, Dateien mithilfe von Bezeichnungen zu klassifizieren und zu schützen, da nur zwei Cmdlets erforderlich sind, die einzeln oder gemeinsam ausgeführt werden können: [Get-AIPFileStatus](/powershell/azureinformationprotection/vlatest/get-aipfilestatus) und [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel). Weitere Informationen und Beispiele finden Sie in der Hilfe zu diesen beiden Cmdlets.

Wenn Sie Dateien jedoch über eine direkte Verbindung mit dem Azure Rights Management-Dienst schützen oder den Schutz aufheben möchten, müssen Sie in der Regel eine Reihe von Cmdlets gemäß der folgenden Beschreibung ausführen.

Geben Sie zunächst in einer PowerShell-Sitzung Folgendes ein, wenn Sie sich für den Azure Rights Management-Dienst mit einem Dienstprinzipal authentifizieren müssen, anstatt Ihr eigenes Konto zu verwenden:

    Set-RMSServerAuthentication

Geben Sie nach der entsprechenden Aufforderung die drei Bezeichner ein, wie unter [Voraussetzung 3: Dateien ohne Benutzerinteraktion schützen oder deren Schutz aufheben](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction) beschrieben.

Bevor Sie Dateien schützen können, müssen Sie die Rights Management-Vorlagen auf Ihren Computer herunterladen und die zu verwendende Vorlage sowie ihre zugehörige ID-Nummer ermitteln. In der Ausgabe können Sie dann die Vorlagen-ID kopieren:

    Get-RMSTemplate
    
Ihre Ausgabe sieht etwa wie folgt aus:

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

Wenn Sie nicht den Befehl „Set-RMSServerAuthentication“ ausgeführt haben, werden Sie für den Azure Rights Management-Dienst mit Ihrem eigenen Benutzerkonto authentifiziert. Wenn Sie auf einem in eine Domäne eingebundenen Computer befinden, werden immer automatisch Ihre aktuellen Anmeldeinformationen verwendet. Wenn Sie sich auf einem Arbeitsgruppencomputer befinden, werden Sie zur Anmeldung bei Azure aufgefordert, und diese Anmeldeinformationen werden dann für nachfolgende Befehle zwischengespeichert. Verwenden Sie in diesem Szenario das Cmdlet `Clear-RMSAuthentication`, wenn Sie sich später als anderer Benutzer anmelden müssen.

Nachdem Sie die Vorlagen-ID kennen, können Sie sie mit dem Cmdlet `Protect-RMSFile` verwenden, um eine einzelne Datei oder alle Dateien in einem Ordner zu schützen. Wenn Sie z. B. nur eine einzelne Datei schützen und das Original mithilfe der Vorlage „Contoso, Ltd – Vertraulich“ überschreiben möchten:

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Ihre Ausgabe sieht etwa wie folgt aus:

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx

Verwenden Sie den Parameter **-Folder** mit einem Laufwerkbuchstaben und Pfad oder UNC-Pfad, um alle Dateien in einem Ordner zu schützen. Beispiel:

    Protect-RMSFile -Folder \Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Ihre Ausgabe sieht etwa wie folgt aus:

    InputFile                          EncryptedFile
    ---------                          -------------
    \Server1\Documents\Test1.docx     \Server1\Documents\Test1.docx
    \Server1\Documents\Test2.docx     \Server1\Documents\Test2.docx
    \Server1\Documents\Test3.docx     \Server1\Documents\Test3.docx
    \Server1\Documents\Test4.docx     \Server1\Documents\Test4.docx

Wenn die Dateierweiterung nicht geändert wird, nachdem der Schutz angewendet wurde, können Sie später immer das Cmdlet `Get-RMSFileStatus` verwenden, um zu prüfen, ob die Datei geschützt ist. Beispiel:

    Get-RMSFileStatus -File \Server1\Documents\Test1.docx

Ihre Ausgabe sieht etwa wie folgt aus:

    FileName                              Status
    --------                              ------
    \Server1\Documents\Test1.docx         Protected

Sie müssen die Rechte „Besitzer“ oder „Extrahieren“ für das Konto besitzen, mit dem die Datei geschützt wurde, oder Sie müssen die Cmdlets als Administrator ausführen, um den Schutz einer Datei aufheben zu können. Verwenden Sie anschließend das Cmdlet zum Aufheben des Schutzes. Beispiel:

    Unprotect-RMSFile C:\test.docx -InPlace

Ihre Ausgabe sieht etwa wie folgt aus:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

Beachten Sie: Wenn die Rights Management-Vorlagen geändert werden, müssen Sie sie erneut mit `Get-RMSTemplate -force` herunterladen. 

## <a name="active-directory-rights-management-services"></a>Active Directory-Rechteverwaltungsdienste

Lesen Sie diesen Abschnitt, bevor Sie damit beginnen, Dateien mithilfe der PowerShell-Befehle zu schützen bzw. deren Schutz aufzuheben, wenn in Ihrer Organisation nur Active Directory Rights Management Services verwendet werden.


### <a name="prerequisites-for-ad-rms"></a>Voraussetzungen für AD RMS

Zusätzlich zu den Voraussetzungen für die Installation des Moduls „AzureInformationProtection“ muss Ihr Konto über die Berechtigungen zum Lesen und Ausführen verfügen, um auf „ServerCertification.asmx“ zugreifen zu können:

1. Melden Sie sich an einem AD RMS-Server an.

2. Klicken Sie auf **Start** und dann auf **Computer**.

3. Navigieren Sie im Datei-Explorer zu „%systemdrive%\Initpub\wwwroot\_Wmsc\Certification“.

4. Klicken Sie mit der rechten Maustaste auf **ServerCertification.asmx**, und klicken Sie dann auf **Eigenschaften**.

5. Klicken Sie im Dialogfeld mit den Eigenschaften von **ServerCertification.asmx** auf die Registerkarte **Sicherheit**. 

6. Klicken Sie auf die Schaltfläche **Weiter** oder **Bearbeiten**. 

7. Klicken Sie im Dialogfeld **Berechtigungen für ServerCertification.asmx** auf **Hinzufügen**. 

8. Fügen Sie Ihren Kontonamen hinzu. Wenn diese Cmdlets auch von anderen AD RMS-Administratoren verwendet werden, um Dateien zu schützen oder deren Schutz aufzuheben, fügen Sie auch deren Namen hinzu.

9. Stellen Sie in der Spalte **Zulassen** sicher, dass die Kontrollkästchen für **Lesen und Ausführen** und **Lesen** aktiviert sind.

Klicken Sie zweimal auf **OK**.

### <a name="example-scenarios-for-using-the-cmdlets-for-active-directory-rights-management-services"></a>Beispielszenarien für die Verwendung der Cmdlets für Active Directory Rights Management Services

Ein typisches Szenario für diese Cmdlets ist das Schützen aller Dateien in einem Ordner mithilfe einer Vorlage für Benutzerrichtlinien oder das Aufheben des Schutzes einer Datei. 

Wenn Sie über mehrere Bereitstellungen von AD RMS verfügen, benötigen Sie zunächst die Namen der AD RMS-Server, die Sie mithilfe des Cmdlets „Get-RMSServer“ zum Anzeigen aller verfügbaren Server erhalten:

    Get-RMSServer

Ihre Ausgabe sieht etwa wie folgt aus:

    Number of RMS Servers that can provide templates: 2 
    ConnectionInfo             DisplayName          AllowFromScratch
    --------------             -------------        ----------------
    Microsoft.InformationAnd…  RmsContoso                       True
    Microsoft.InformationAnd…  RmsFabrikam                      True

Bevor Sie Dateien schützen können, müssen Sie eine Liste von RMS-Vorlagen abrufen, um die zu verwendende Vorlage und ihre zugehörige ID-Nummer zu ermitteln. Der RMS-Server muss nur angegeben werden, wenn Sie über mehrere AD RMS-Bereitstellungen verfügen. 

In der Ausgabe können Sie dann die Vorlagen-ID kopieren:

    Get-RMSTemplate -RMSServer RmsContoso

Ihre Ausgabe sieht etwa wie folgt aus:

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

Nachdem Sie die Vorlagen-ID kennen, können Sie sie mit dem Cmdlet „Protect-RMSFile“ verwenden, um eine einzelne Datei oder alle Dateien in einem Ordner zu schützen. Wenn Sie z. B. nur eine einzelne Datei schützen und das Original mithilfe der Vorlage „Contoso, Ltd – Vertraulich“ ersetzen möchten:

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Ihre Ausgabe sieht etwa wie folgt aus:

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx   

Verwenden Sie den Parameter „-Folder“ mit einem Laufwerkbuchstaben und Pfad oder UNC-Pfad, um alle Dateien in einem Ordner zu schützen. Beispiel:

    Protect-RMSFile -Folder \\Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Ihre Ausgabe sieht etwa wie folgt aus:

    InputFile                          EncryptedFile
    ---------                          -------------
    \\Server1\Documents\Test1.docx     \\Server1\Documents\Test1.docx   
    \\Server1\Documents\Test2.docx     \\Server1\Documents\Test2.docx   
    \\Server1\Documents\Test3.docx     \\Server1\Documents\Test3.docx   
    \\Server1\Documents\Test4.docx     \\Server1\Documents\Test4.docx   

Wenn die Dateierweiterung nicht geändert wird, nachdem der RMS-Schutz angewendet wurde, können Sie später immer das Cmdlet „Get-RMSFileStatus“ verwenden, um zu prüfen, ob die Datei geschützt ist. Beispiel: 

    Get-RMSFileStatus -File \\Server1\Documents\Test1.docx

Ihre Ausgabe sieht etwa wie folgt aus:

    FileName                              Status
    --------                              ------
    \\Server1\Documents\Test1.docx        Protected

Sie müssen die Rechte „Besitzer“ oder „Extrahieren“ für das Konto besitzen, mit dem die Datei geschützt wurde, oder Sie müssen Administrator für AD RMS sein, um den Schutz einer Datei aufheben zu können. Verwenden Sie anschließend das Cmdlet zum Aufheben des Schutzes. Beispiel:

    Unprotect-RMSFile C:\test.docx -InPlace

Ihre Ausgabe sieht etwa wie folgt aus:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx


## <a name="next-steps"></a>Nächste Schritte
Verwenden Sie das Cmdlet „Get-Help <cmdlet name>“ wobei <cmdlet name> der Name des Cmdlets ist, das Sie untersuchen möchten, um die Cmdlet-Hilfe in einer PowerShell-Sitzung aufzurufen. Beispiel: 

    Get-Help Get-RMSTemplate

Weitere Informationen, die möglicherweise zur Unterstützung des Azure Information Protection-Clients erforderlich sind, finden Sie unter den folgenden Themen:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
