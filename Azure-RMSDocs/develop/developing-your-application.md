---
title: Entwickeln Ihrer Anwendung – AIP
description: Anleitung mithilfe einer einfachen Konsolen-App zum Implementieren des Dokumentschutz mit AIP
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: 2fc3fecd33d6e461156e8c608eae91dee17dff2b
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568321"
---
# <a name="developing-your-application"></a>Entwickeln Ihrer Anwendung

In diesem Beispiel erstellen Sie eine einfache Konsolenanwendung, die mit dem AIP-Dienst (Azure Information Protection-Dienst) interagiert.  Sie übernimmt als Eingabe den Pfad eines zu schützenden Dokuments und schützt es anschließend mit einer Ad-hoc-Richtlinie oder einer Azure-Vorlage. Die Anwendung wendet dann die richtigen Richtlinien entsprechend den Eingaben an, um ein geschütztes Dokument zu erstellen. Der zu verwendende Beispielcode ist eine [Azure IP-Testanwendung](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test), die sich auf Github befindet.

## <a name="sample-app-prerequisites"></a>Voraussetzungen für die Beispiel-App
- **Betriebssystem**: Windows 10, Windows 8, Windows 7, Windows Server 2008, Windows Server 2008 R2 oder Windows Server 2012
- **Programmiersprache**: C# (.NET Framework 3.0 und höher)
- **Entwicklungsumgebung**: Visual Studio 2015 (und höher)

## <a name="setting-up-your-azure-configuration"></a>Einrichten der Azure-Konfiguration

Das Einrichten von Azure für diese App erfordert, dass Sie eine Mandanten-ID, einen symmetrischen Schlüssel und eine Anwendungsprinzipal-ID erstellen.

### <a name="azure-ad-tenant-configuration"></a>Azure AD-Mandantenkonfiguration

Wenn Sie die Azure AD Umgebung für Azure Information Protection konfigurieren möchten, befolgen Sie die Anweisungen unter [Aktivieren des Schutz Dienstanbieter von Azure Information Protection](/information-protection/deploy-use/activate-service).

Nachdem der Dienst aktiviert wurde, benötigen Sie PowerShell-Komponenten für die nächsten Schritte. Befolgen Sie hierzu die Schritte zum [Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](/information-protection/deploy-use/administer-powershell) .

### <a name="getting-your-tenant-id"></a>Abrufen der Mandanten-ID

- Führen Sie PowerShell als Administrator aus.
- Importieren Sie das RMS-Modul: `Import-Module AIPService`.
- Stellen Sie eine Verbindung mit dem Dienst mithilfe der zugewiesenen Benutzeranmeldeinformationen her: `Connect-AipService –Verbose`
- Stellen Sie sicher, dass RMS aktiviert ist: `enable-aipservice`
- Rufen Sie Ihre Mandanten-ID ab, indem Sie Folgendes ausführen: `Get-AipServiceConfiguration`

>Notieren Sie den BPOSId-Wert (Mandanten-ID). Sie wird später benötigt.

*Beispielausgabe* 
 ![ Cmdlet-Ausgabe](../media/develop/output-of-Get-AadrmConfiguration.png)

- Trennen Sie die Verbindung mit dem Dienst: `Disconnect-AipServiceService`

### <a name="create-a-service-principal"></a>Erstellen eines Dienstprinzipals
Führen Sie die folgenden Schritte aus, um einen Dienstprinzipal zu erstellen:
> Ein Dienstprinzipal besteht aus Anmeldeinformationen, die für die globale Zugriffssteuerung konfiguriert sind und einem Dienst die Authentifizierung mit Microsoft Azure AD und das Schützen von Informationen mithilfe von Microsoft Azure AD Rights Management ermöglichen.

- Führen Sie PowerShell als Administrator aus.
- Importieren Sie das Microsoft Azure AD-Modul mithilfe von: `Import-Module MSOnline`
- Stellen Sie eine Verbindung mit Ihrem Onlinedienst mithilfe der zugewiesenen Benutzeranmeldeinformationen her: `Connect-MsolService`
- Erstellen sie einen neuen Dienstprinzipal, indem Sie Folgendes ausführen: `New-MsolServicePrincipal`
- Geben Sie einen Namen für Ihre Dienstprinzipal an.
  > Notieren Sie den symmetrischen Schlüssel und die Anwendungsprinzipal-ID für die spätere Verwendung.

*Beispielausgabe* 
 ![ Cmdlet-Ausgabe](../media/develop/output-of-NewMsolServicePrincipal.png)

- Fügen Sie Ihre Anwendungsprinzipal-ID, den symmetrischen Schlüssel und die Mandanten-ID zur Datei „App.config“ der Anwendung hinzu.

*Beispiel App.config Datei* 
 ![ Cmdlet-Ausgabe](../media/develop/example-App.config-file.png)

- *ClientID* und *RedirectUri* wurden Ihnen beim Registrieren Ihrer Anwendung in Azure zur Verfügung gestellt. Weitere Informationen zum Registrieren Ihrer Anwendung in Azure und zum Abrufen von *ClientID* und *RedirectUri* finden Sie unter [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md).


## <a name="design-summary"></a>Entwurfszusammenfassung
Im folgenden Diagramm sind der Architektur- und Prozessverlauf für die zu erstellende App veranschaulicht und die erforderlichen Schritte unten erläutert.
![Entwurfszusammenfassung](../media/develop/design-summary.png)

1. Benutzereingabe:
   - Pfad zu der zu schützenden Datei
   - Vorlage auswählen oder Ad-hoc-Richtlinie erstellen
2. Anwendung fordert Authentifizierung mit AIP an
3. AIP bestätigt Authentifizierung
4. Anwendung fordert Vorlagen von AIP an
5. Vordefinierte Vorlagen werden von AIP zurückgegeben
6. Anwendung sucht angegebene Datei am bereitgestellten Speicherort
7. Anwendung wendet AIP-Schutzrichtlinie auf die Datei an

## <a name="how-the-code-works"></a>Funktionsweise des Codes

Im Beispiel zum Azure IP-Test beginnt die Lösung mit der Datei „Iprotect.cs“. Dies ist ein C#-Konsolenanwendungsprojekt, und wie bei jeder anderen AIP-fähigen Anwendung beginnen Sie mit beim Laden der Datei *„msipc.dll“*, wie in der `main()`-Methode veranschaulicht.

```csharp
//Loads MSIPC.dll
SafeNativeMethods.IpcInitialize();
SafeNativeMethods.IpcSetAPIMode(APIMode.Server);
```

Laden der für die Verbindung mit Azur erforderlichen Parameter

```csharp
//Loads credentials for the service principal from App.Config
SymmetricKeyCredential symmetricKeyCred = new SymmetricKeyCredential();
symmetricKeyCred.AppPrincipalId = ConfigurationManager.AppSettings["AppPrincipalId"];
symmetricKeyCred.Base64Key = ConfigurationManager.AppSettings["Base64Key"];
symmetricKeyCred.BposTenantId = ConfigurationManager.AppSettings["BposTenantId"];
```

Wenn Sie den Dateipfad in der Konsolenanwendung angeben, prüft die Anwendung, ob das Dokument bereits verschlüsselt ist. Die Methode stammt aus der Klasse **SafeFileApiNativeMethods**.

```csharp
var checkEncryptionStatus = SafeFileApiNativeMethods.IpcfIsFileEncrypted(filePath);
```

Wenn das Dokument nicht verschlüsselt ist, wird mit der Verschlüsselung des Dokuments mit der bei der Aufforderung bereitgestellten Auswahl fortgefahren.

```csharp
if (!checkEncryptionStatus.ToString().ToLower().Contains(alreadyEncrypted))
{
  if (method == EncryptionMethod1)
  {
    //Encrypt a file via AIP template
    ProtectWithTemplate(symmetricKeyCred, filePath);

  }
  else if (method == EncryptionMethod2)
  {
    //Encrypt a file using ad-hoc policy
    ProtectWithAdHocPolicy(symmetricKeyCred, filePath);
  }
}
```

Die Option zum Schützen mit Vorlage fährt mit dem Abrufen der Vorlagenliste vom Server fort und bietet dem Benutzer die Auswahlmöglichkeit.
>Wenn Sie keine Vorlagen geändert haben, erhalten Sie Standardvorlagen von AIP.

```csharp
public static void ProtectWithTemplate(SymmetricKeyCredential symmetricKeyCredential, string filePath)
{
  // Gets the available templates for this tenant
  Collection<TemplateInfo> templates = SafeNativeMethods.IpcGetTemplateList(null, false, true,
      false, true, null, null, symmetricKeyCredential);

  //Requests tenant template to use for encryption
  Console.WriteLine("Please select the template you would like to use to encrypt the file.");

  //Outputs templates available for selection
  int counter = 0;
  for (int i = 0; i < templates.Count; i++)
  {
    counter++;
    Console.WriteLine(counter + ". " + templates.ElementAt(i).Name + "\n" +
        templates.ElementAt(i).Description);
  }

  //Parses template selection
  string input = Console.ReadLine();
  int templateSelection;
  bool parseResult = Int32.TryParse(input, out templateSelection);

  //Returns error if no template selection is entered
  if (parseResult)
  {
    //Ensures template value entered is valid
    if (0 < templateSelection && templateSelection <= counter)
    {
      templateSelection -= templateSelection;

      // Encrypts the file using the selected template
      TemplateInfo selectedTemplateInfo = templates.ElementAt(templateSelection);

      string encryptedFilePath = SafeFileApiNativeMethods.IpcfEncryptFile(filePath,
          selectedTemplateInfo.TemplateId,
          SafeFileApiNativeMethods.EncryptFlags.IPCF_EF_FLAG_KEY_NO_PERSIST, true, false, true, null,
          symmetricKeyCredential);
    }
  }
}
```

Wenn Sie die Ad-hoc-Richtlinie auswählen, muss der Benutzer der Anwendung E-Mails der Personen bereitstellen, die Berechtigungen erhalten sollen. In diesem Abschnitt wird die Lizenz mit der Methode **IpcCreateLicenseFromScratch()** erstellt und die neue Richtlinie auf die Vorlage angewendet.

```csharp
if (issuerDisplayName.Trim() != "")
{
  // Gets the available issuers of rights policy templates.
  // The available issuers is a list of RMS servers that this user has already contacted.
  try
  {
    Collection<TemplateIssuer> templateIssuers = SafeNativeMethods.IpcGetTemplateIssuerList(
                                                    null,
                                                    true,
                                                    false,
                                                    false, true, null, symmetricKeyCredential);

    // Creates the policy and associates the chosen user rights with it
    SafeInformationProtectionLicenseHandle handle = SafeNativeMethods.IpcCreateLicenseFromScratch(
                                                        templateIssuers.ElementAt(0));
    SafeNativeMethods.IpcSetLicenseOwner(handle, owner);
    SafeNativeMethods.IpcSetLicenseUserRightsList(handle, userRights);
    SafeNativeMethods.IpcSetLicenseDescriptor(handle, new TemplateInfo(null, CultureInfo.CurrentCulture,
                                                            policyName,
                                                            policyDescription,
                                                            issuerDisplayName,
                                                            false));

    //Encrypts the file using the ad hoc policy
    string encryptedFilePath = SafeFileApiNativeMethods.IpcfEncryptFile(
                                    filePath,
                                    handle,
                                    SafeFileApiNativeMethods.EncryptFlags.IPCF_EF_FLAG_KEY_NO_PERSIST,
                                    true,
                                    false,
                                    true,
                                    null,
                                    symmetricKeyCredential);
    }
}
```

## <a name="user-interaction-example"></a>Beispiel für die Benutzerinteraktion

Nachdem alles erstellt und ausgeführt wurde, sollte die Ausgabe der Anwendung wie folgt aussehen:

1. Sie werden aufgefordert, eine Verschlüsselungsmethode auszuwählen.
   ![App-Ausgabe – Schritt 1](../media/develop/app-output-1.png)

2. Sie werden aufgefordert, den Pfad zu der zu schützenden Datei bereitzustellen.
   ![App-Ausgabe – Schritt 2](../media/develop/app-output-2.png)

3. Sie werden aufgefordert, eine E-Mail-Adresse des Lizenzbesitzers einzugeben (dieser Besitzer muss über globale Administratorrechte auf dem Azure AD-Mandanten verfügen).
   ![App-Ausgabe – Schritt 3](../media/develop/app-output-3.png)

4. Sie geben E-Mail-Adressen von Benutzern ein, die Zugriff auf die Datei haben sollen (E-Mails müssen durch Leerzeichen getrennt werden).
   ![App-Ausgabe – Schritt 4](../media/develop/app-output-4.png)

5. Sie wählen aus einer Liste die Rechte aus, die die autorisierten Benutzer erhalten sollen.
   ![App-Ausgabe – Schritt 5](../media/develop/app-output-5.png)

6. Abschließend geben Sie einige Richtlinienmetadaten ein: Richtlinienname, Beschreibung und Anzeigename des Ausstellers (Azure AD-Mandant) ![App-Ausgabe – Schritt 6](../media/develop/app-output-6.png)