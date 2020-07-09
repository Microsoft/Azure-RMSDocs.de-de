---
title: Ihr Azure Information Protection-Mandantenschlüssel
description: Anstatt Microsoft den Stamm Schlüssel für Azure Information Protection zu verwalten, empfiehlt es sich, diesen Schlüssel (als "Bring your own Key" oder Byok bezeichnet) für Ihren Mandanten zu erstellen und zu verwalten, um bestimmte Vorschriften einzuhalten.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 11/11/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: d704ca679ce7d36f3e3956443b3b2a013366382d
ms.sourcegitcommit: 551e3f5b8956da49383495561043167597a230d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "86137005"
---
# <a name="planning-and-implementing-your-azure-information-protection-tenant-key"></a>Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Verwenden Sie die Informationen in diesem Artikel zum Planen und Verwalten Ihres Azure Information Protection-Mandantenschlüssels. Angenommen, Sie möchten die Standardeinstellung ändern, dass Microsoft Ihren Mandantenschlüssel verwaltet, und Ihren eigenen Mandantenschlüssel verwalten, um bestimmte Vorschriften in Ihrer Organisation einzuhalten. Das Verwalten Ihres eigenen Mandantenschlüssels wird auch als „Bring Your Own Key“ (BYOK) bezeichnet.

Der Azure Information Protection-Mandantenschlüssel

- Der Azure Information Protection-Mandantenschlüssel ist ein Stammschlüssel für Ihre Organisation. Andere Schlüssel wie Benutzer-, Computer- und Verschlüsselungsschlüssel für Dokumente können von diesem Stammschlüssel abgeleitet werden. Immer wenn Azure Information Protection diese Schlüssel für Ihre Organisation verwendet, werden sie kryptographisch an Ihren Azure Information Protection-Mandantenschlüssel gekettet.

- Der Azure Information Protection-Mandantenschlüssel ist das online verfügbare Äquivalent zum Schlüssel des lizenzgebenden Serverzertifikats (Server Licensor Certificate, SLC) des Tools Active Directory Rights Management Services (AD RMS). 

**Kurz zusammengefasst:** Verwenden Sie die folgende Tabelle als eine kurze Einführung in die empfohlene Mandantenschlüsseltopologie. Weitere Informationen finden Sie in der Zusatzdokumentation.

|Geschäftsanforderung|Empfohlene Mandantenschlüsseltopologie|
|------------------------|-----------------------------------|
|Setzen Sie Azure Information Protection schnell und ohne besondere Hardware, zusätzliche Software oder Azure-Abonnement ein.<br /><br />Setzen Sie es beispielsweise in Testumgebungen ein oder wenn in Ihrem Unternehmen keine rechtlichen Bestimmungen für die Schlüsselverwaltung bestehen.|Von Microsoft verwaltet|
|Konformitäts Bestimmungen und Kontrolle über alle Lebenszyklus Vorgänge. <br /><br />Beispielsweise muss Ihr Schlüssel durch ein Hardwaresicherheitsmodul (HSM) geschützt sein.|BYOK|


Falls erforderlich, können Sie Ihre Mandanten Schlüssel Topologie nach der Bereitstellung mithilfe des Cmdlets " [Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties) " ändern.


## <a name="choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok"></a>Wählen Sie Ihre Mandantenschlüsseltopologie aus: Verwaltet von Microsoft (Standard) oder verwaltet von Ihnen (BYOK)

Entscheiden Sie, welche Mandantenschlüsseltopologie für Ihre Organisation am besten geeignet ist:

- **Von Microsoft verwaltet**: Microsoft generiert automatisch einen Mandantenschlüssel für Ihre Organisation. Dieser Schlüssel wird nur für Azure Information Protection verwendet. Standardmäßig verwendet Microsoft diesen Schlüssel für Ihren Mandanten und verwaltet die meisten Aspekte des Lebenszyklusvorgangs für Ihren Mandantenschlüssel. 
    
    Dies ist die einfachste Möglichkeit mit dem geringsten Verwaltungsaufwand. In den meisten Fällen müssen Sie noch nicht einmal wissen, dass Sie einen Mandantenschlüssel besitzen. Sie registrieren sich einfach für Azure Information Protection, und der restliche Schlüsselverwaltungsprozess wird von Microsoft erledigt.

- **Von Ihnen verwaltet (BYOK)**: Verwenden Sie [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) zusammen mit Azure Information Protection, um die vollständige Kontrolle über Ihren Mandantenschlüssel zu erlangen. Erstellen Sie den Schlüssel für diese Mandantenschlüsseltopologie entweder in Key Vault direkt oder lokal. Wenn Sie ihn lokal erstellen, übertragen oder importieren Sie ihn anschließend auf bzw. in Key Vault. Konfigurieren Sie dann Azure Information Protection, um den Schlüssel zu verwenden. Verwalten Sie den Schlüssel in Azure Key Vault.
    

### <a name="more-information-about-byok"></a>Nähere Informationen zu BYOK
Sie haben folgende Optionen, um Ihren eigenen Schlüssel zu erstellen:

- **Erstellen Sie den Schlüssel lokal, und übertragen oder importieren Sie ihn auf bzw. in Key Vault**:
    
    - Ein HSM-geschützter Schlüssel, den Sie lokal erstellen und auf Key Vault als HSM-geschützten Schlüssel übertragen.
    
    - Ein softwaregeschützter Schlüssel, den Sie lokal erstellen, konvertieren und auf Key Vault als HSM-geschützten Schlüssel übertragen. Diese Option wird nur unterstützt, wenn Sie eine [Migration von Active Directory Rights Management Services (AD RMS) vornehmen](migrate-from-ad-rms-to-azure-rms.md).
    
    - Ein softwaregeschützter Schlüssel, den Sie lokal erstellen, konvertieren und auf Key Vault als HSM-geschützten Schlüssel übertragen. Für diese Option benötigen Sie eine PFX-Zertifikatdatei.
    
- **Erstellen Sie den Schlüssel in Key Vault**:
    
    - Ein HSM-geschützter Schlüssel, den Sie in Key Vault erstellen.
    
    - Ein softwaregeschützter Schlüssel, den Sie in Key Vault erstellen.

Aus diesen BYOK-Optionen wird üblicherweise der HSM-geschützte Schlüssel ausgewählt, der lokal erstellt und auf Key Vault als HSM-geschützter Schlüssel übertragen wird. Obwohl der Verwaltungsaufwand bei dieser Option am höchsten ist, muss Sie für Ihre Organisation möglicherweise ausgewählt werden, damit bestimmte Vorschriften eingehalten werden können. Die HSM, die von Azure Key Vault verwendet werden, sind FIPS 140-2 Level 2 geprüft.

Bei dieser Option geschieht Folgendes:

1. Sie generieren Ihren Mandantenschlüssel lokal, entsprechend Ihrer IT- und Sicherheitsrichtlinien. Der Schlüssel dient als Masterkopie. Er verbleibt auf lokaler Ebene, und Sie sind für das Backup verantwortlich.

2. Sie erstellen eine Kopie des Schlüssels, die Sie anschließend sicher von Ihrem HSM auf Azure Key Vault übertragen. Während dieses Vorgangs verlässt die Masterkopie dieses Schlüssels nie die Hardwareschutzgrenzen.

3. Die Kopie des Schlüssels wird durch Azure Key Vault geschützt.

> [!NOTE]
> 
> Als zusätzliche Schutzmaßnahme verwendet Azure Key Vault in Regionen wie Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien getrennte Sicherheitsdomänen für seine Rechenzentren. Außerdem verwendet Azure Key Vault verschiedene Azure-Instanzen wie Microsoft Azure Deutschland und Azure Government. 

Auch wenn dies optional ist, möchten Sie wahrscheinlich auch die beinahe in Echtzeit erstellten Nutzungsprotokolle von Azure Information Protection verwenden, um genau verfolgen zu können, wie und wann Ihr Mandantenschlüssel verwendet wird.

Wenn Sie Byok für Ihren Azure Information Protection Mandanten Schlüssel verwenden, können Sie Ihre vertrauenswürdige Veröffentlichungs Domäne (Trusted Publishing Domain, TPD) nicht exportieren. Die TPD wird benötigt, wenn Sie sich entscheiden, Azure Information Protection nicht mehr zu verwenden, aber weiterhin in der Lage sein müssen, Inhalte zu entschlüsseln, die durch Azure Information Protection geschützt wurden. Wenn Sie sich für dieses Szenario vorbereiten möchten, indem Sie eine geeignete TPD im Voraus erstellen, lesen Sie die folgenden Anweisungen, [wie Sie einen Azure Information Protection "Cloud Exit"-Plan vorbereiten](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/How-to-prepare-an-Azure-Information-Protection-Cloud-Exit-plan/ba-p/382631).

### <a name="when-you-have-decided-your-tenant-key-topology"></a>Vorgehensweise, nachdem Sie sich für eine Mandantenschlüsseltopologie entschlossen haben

Gehen Sie wie folgt vor, wenn Sie sich dafür entschieden haben, dass ihr Mandantenschlüssel von Microsoft verwaltet werden soll: 

- Wenn Sie keine Migration von AD RMS vornehmen, ist kein weiterer Schritt notwendig, damit der Schlüssel generiert wird. Sie können der Anleitung unter [Nächste Schritte](plan-implement-tenant-key.md#next-steps) folgen.

- Nutzen Sie die folgenden Anweisungen, wenn Sie derzeit über AD RMS verfügen und zu Azure Information Protection migrieren möchten: [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md). 

Wenn Sie sich entschließen, Ihren Mandantenschlüssel selbst zu verwalten, finden Sie in den folgenden Abschnitten weitere Informationen hierzu, die Sie lesen sollten.

## <a name="implementing-byok-for-your-azure-information-protection-tenant-key"></a>BYOK-Implementierung für Ihren Azure Information Protection-Mandantenschlüssel

Verwenden Sie die Informationen und Verfahren in diesem Abschnitt, wenn Sie sich entschieden haben, Ihren Mandantenschlüssel selber zu generieren und zu verwalten – das BYOK-Szenario (Bring Your Own Key):

> [!NOTE]
> Wenn Sie Azure Information Protection zunächst mit einem von Microsoft verwalteten Mandantenschlüssel verwendet haben und jetzt Ihren Mandantenschlüssel selbst verwalten möchten (BYOK), bleiben die zuvor geschützten Dokumente und E-Mails über einen archivierten Schlüssel zugänglich. 

### <a name="prerequisites-for-byok"></a>Voraussetzungen für BYOK
In der folgenden Tabelle finden Sie eine Liste der Voraussetzungen für „Bring Your Own Key“ (BYOK).

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Ihr Azure Information Protection-Mandant muss über ein Azure-Abonnement verfügen. Falls Sie über kein Abonnement verfügen, können Sie sich für ein [kostenloses Konto](https://azure.microsoft.com/pricing/free-trial/)registrieren. <br /><br /> Sie müssen über den Premiumtarif von Azure Key Vault verfügen, um einen HSM-geschützten Schlüssel verwenden zu können.|Das kostenlose Azure-Abonnement, das Zugriff zum Konfigurieren von Azure Active Directory und benutzerdefinierten Azure Rights Management-Vorlagen bietet (**Zugriff auf Azure Active Directory**), reicht zum Verwenden von Azure Key Vault nicht aus. Verwenden Sie [Azure PowerShell](/powershell/azure/overview) -Cmdlets, um zu bestätigen, dass Sie über ein Azure-Abonnement verfügen, das Sie für Byok verwenden können: <br /><br /> 1. Starten Sie eine Azure PowerShell Sitzung mit der Option **als Administrator ausführen** , und melden Sie sich als globaler Administrator für Ihren Azure Information Protection-Mandanten mithilfe von an. `Connect-AzAccount` Kopieren Sie anschließend die resultierende Tokenzeichenfolge in mithilfe eines Browsers, und fügen Sie Sie in `https://microsoft.com/devicelogin` ein. <br /><br /> Weitere Informationen finden Sie [unter Anmelden mit Azure PowerShell](/powershell/azure/authenticate-azureps). <br /><br />2. Geben Sie Folgendes ein, und vergewissern Sie sich, dass die Werte für Name und ID Ihres Abonnements angezeigt werden, ihre Azure Information Protection Mandanten-ID und der Status aktiviert ist:`Get-AzSubscription`<br /><br />Wenn keine Werte angezeigt werden und Sie lediglich an die Eingabeaufforderung zurückverwiesen werden, haben Sie kein Azure-Abonnement, das sich für BYOK eignet. <br /><br />**Hinweis**: Zusätzlich zu den Voraussetzungen für Byok müssen Sie, wenn Sie von AD RMS zu Azure Information Protection mithilfe von Software Schlüssel zu Hardware Schlüsseln migrieren, mindestens eine Version von 11,62 verwenden, wenn Sie Thales Firmware für Ihr HSM verwenden.|
|Für die Verwendung eines HSM-geschützten Schlüssels, den Sie lokal erstellen: <br /><br />– Alle Voraussetzungen, die für Key Vault-BYOK aufgeführt sind. |Siehe die [Voraussetzungen für BYOK](/azure/key-vault/key-vault-hsm-protected-keys#prerequisites-for-byok) in der Azure Key Vault-Dokumentation. <br /><br /> **Hinweis**: Zusätzlich zu den Voraussetzungen für Byok müssen Sie, wenn Sie von AD RMS zu Azure Information Protection mithilfe von Software Schlüssel zu Hardware Schlüsseln migrieren, mindestens eine Version von 11,62 verwenden, wenn Sie Thales Firmware für Ihr HSM verwenden.|
|Wenn der Schlüsseltresor, der Ihren Mandantenschlüssel enthalten soll, Virtual Network-Dienstendpunkte für Azure Key Vault verwendet: <br /><br />– Erlauben Sie vertrauenswürdigen Microsoft-Diensten, diese Firewall zu umgehen.|Weitere Informationen finden Sie im Blog [Virtual Network Service Endpoints for Azure Key Vault (Virtual Network-Dienstendpunkte für Azure Key Vault)](/azure/key-vault/key-vault-overview-vnet-service-endpoints).|
|Das aipservice-PowerShell-Modul für Azure Information Protection.|Installationsanweisungen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](./install-powershell.md).|

Weitere Informationen zu nCipher nShield Hardware Security Module (HSM) und deren Verwendung mit Azure Key Vault finden Sie auf der [nCipher-Website](https://www.ncipher.com/products/key-management/cloud-microsoft-azure/how-to-buy).

### <a name="choosing-your-key-vault-location"></a>Auswählen eines Speicherorts für Ihren Schlüsseltresor

Wenn Sie einen Schlüsseltresor für den Schlüssel erstellen, der als Ihr Mandantenschlüssel für Azure Information verwendet werden soll, müssen Sie einen Speicherort bestimmen. Dieser Speicherort ist eine Azure-Region oder -Instanz.

Treffen Sie Ihre Entscheidung vorrangig anhand von Konformitätsgründen. Die Minimierung der Netzwerklatenz ist zweitrangig:

- Wenn Sie die BYOK-Mandantenschlüsseltopologie aus Konformitätsgründen ausgewählt haben sollten, wird die Azure-Region oder -Instanz, in der Ihr Azure Information Protection-Mandantenschlüssel gespeichert ist, anhand derselben Konformitätsgründe bestimmt.

- Da alle kryptografischen Aufrufe zum Schutz mit Ihrem Azure Information Protection-Mandantenschlüssel verkettet sind, möchten Sie sicherlich die Netzwerklatenz minimieren, die durch diese Aufrufe hervorgerufen wird. Erstellen Sie dafür Ihren Schlüsseltresor in derselben Azure-Region oder -Instanz wie Ihren Azure Information Protection-Mandanten.

Um den Speicherort Ihres Azure Information Protection Mandanten zu identifizieren, verwenden Sie das PowerShell-Cmdlet [Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration) , und identifizieren Sie die Region aus den URLs. Beispiel:

```ps
LicensingIntranetDistributionPointUrl : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing
```

**rms.na.aadrm.com** weist z.B. auf die Region Nordamerika hin.

Anhand der folgenden Tabelle können Sie ermitteln, welche Azure-Region oder -Instanz empfohlen wird, um die Netzwerklatenz zu minimieren.

|Azure-Region oder -Instanz|Empfohlener Speicherort für Ihren Schlüsseltresor|
|---------------|--------------------|
|rms.**na**.aadrm.com|**USA, Norden-Mitte** oder **USA, Osten**|
|rms.**eu**.aadrm.com|**Nordeuropa** oder **West Europa**|
|rms.**ap**.aadrm.com|**Asien, Osten** oder **Südostasien**|
|rms.**sa**.aadrm.com|**USA, Westen** oder **USA, Osten**|
|rms.**govus**.aadrm.com|**USA, Mitte** oder **USA, Osten 2**|
|RMS.**aadrm.US**|**US gov Virginia** oder **US gov Arizona**|
|RMS.**aadrm.cn**|**China, Osten 2** oder **China, Norden 2**|


### <a name="instructions-for-byok"></a>Hinweise zu BYOK

Verwenden Sie die Azure Key Vault-Dokumentation, um einen Schlüsseltresor und den Schlüssel zu erstellen, den Sie für Azure Information Protection verwenden möchten. Weitere Informationen finden Sie unter [Get started with Azure Key Vault (Erste Schritte mit Azure Key Vault)](/azure/key-vault/key-vault-get-started).

Stellen Sie sicher, dass die Schlüssellänge bei 2048 Bits (empfohlen) oder 1024 Bits liegt. Andere Schlüssellängen werden von Azure Information Protection nicht unterstützt. 

Verwenden Sie keinen 1024-Bit-Schlüssel als aktiven Mandanten Schlüssel, da er als unzureichender Schutzgrad angesehen wird. Microsoft unterstützt nicht die Verwendung niedrigerer Schlüssellängen wie z. b. 1024-Bit-RSA-Schlüssel und die damit verbundene Verwendung von Protokollen, die unzureichende Schutz Ebenen bieten, z. b. SHA-1. Es wird empfohlen, zu einer höheren Schlüssellänge zu wechseln.

Folgen Sie der Anleitung unter [Vorgehensweise: Generieren und Übertragen von HSM-geschützten Schlüsseln für Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys), um einen HSM-geschützten Schlüssel lokal zu erstellen und übertragen Sie ihn auf Ihren Azure Key Vault als einen HSM-geschützten Schlüssel.

Damit Azure Information Protection den Schlüssel verwenden kann, müssen alle Key Vault-Vorgänge für diesen Schlüssel zulässig sein. Dies ist die Standardkonfiguration, und die Vorgänge sind verschlüsseln, entschlüsseln, wrapkey, unwrapkey, Sign und Verify. Mit dem folgenden PowerShell-Befehl können Sie die zulässigen Vorgänge eines Schlüssels überprüfen: `(Get-AzKeyVaultKey -VaultName <key vault name> -Name <key name>).Attributes.KeyOps` . Fügen Sie bei Bedarf zugelassene Vorgänge hinzu, indem Sie " [Update-azkeyvaultkey](/powershell/module/az.keyvault/update-azkeyvaultkey) " und den *keyops* -Parameter verwenden.

Jeder Schlüssel, der in Key Vault gespeichert wird, hat eine Schlüssel-ID. Bei der Schlüssel-ID handelt es sich um eine URL, die den Namen des Schlüsseltresor, den Schlüsselcontainer, den Namen des Schlüssels und die Schlüsselversion enthält. Beispiel: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333** . Um den Schlüssel verwenden zu können, müssen Sie Azure Information Protection konfigurieren, indem Sie die Schlüsseltresor-URL angeben.

Bevor Azure Information Protection den Schlüssel verwenden kann, muss der Azure Rights Management-Dienst zum Verwenden des Schlüssels im Schlüsseltresor Ihres Unternehmens autorisiert werden. Hierzu kann der Azure Key Vault-Administrator das Azure-Portal oder Azure PowerShell benutzen:

Konfiguration mithilfe des Azure-Portals:

1. Navigieren Sie zu **Schlüssel**Tresore  >  **\<*your key vault name*>**  >  **Zugriffsrichtlinien**  >  **Hinzufügen neu**.

2. Wählen Sie im Bereich **Zugriffs Richtlinie hinzufügen** im Listenfeld **aus Vorlage konfigurieren (optional)** **Azure Information Protection Byok** aus, und klicken Sie auf **OK**.
    
    Die ausgewählte Vorlage weist die folgende Konfiguration auf:
    
    - Für **Select principal** (Prinzipal auswählen) ist automatisch **Microsoft Rights Management Services** zugewiesen.
    - Für die Schlüsselberechtigungen sind automatisch **Get**, **Decrypt** und **Sign** ausgewählt. 

Konfiguration mithilfe von PowerShell:

- Führen Sie das Key Vault PowerShell-Cmdlet [Set-azkeyvaultaccesspolicy](/powershell/module/az.keyvault/set-azkeyvaultaccesspolicy)aus, und erteilen Sie dem Azure Rights Management-Dienst Prinzipal mithilfe der GUID **00000012-0000-0000-C000-000000000000**Berechtigungen. Beispiel:

    ```ps
    Set-AzKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,sign,get
    ```

Sie können Azure Information Protection jetzt so konfigurieren, dass dieser Schlüssel als Azure Information Protection-Mandantenschlüssel Ihrer Organisation verwendet wird. Stellen Sie unter Verwendung des Azure RMS-Cmdlets zunächst eine Verbindung mit dem Azure Rights Management-Dienst her, und melden Sie sich an:

```ps
    Connect-AipService
```

Führen Sie dann das [Cmdlet use-aipservicekeyvaultkey](/powershell/module/aipservice/use-aipservicekeyvaultkey)aus, und geben Sie dabei die Schlüssel-URL an. Beispiel:

```ps
    Use-AipServiceKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"
```

> [!IMPORTANT]
> In diesem Beispiel ist „aaaabbbbcccc111122223333“ die Version des zu verwendenden Schlüssels. Wenn Sie die Version nicht angeben, wird ohne Warnung die aktuelle Version des Schlüssels verwendet, und der Befehl scheint zu funktionieren. Wenn Ihr Schlüssel in Key Vault später jedoch aktualisiert (erneuert) wird, funktioniert der Azure Rights Management-Dienst nicht mehr für Ihren Mandanten, auch wenn Sie den Befehl "Use-aipservicekeyvaultkey" erneut ausführen.
> 
> Stellen Sie sicher, dass Sie die Schlüsselversion zusätzlich zum Schlüsselnamen angeben, wenn Sie diesen Befehl ausführen. Sie können den Azure Key Vault cmd get [-azkeyvaultkey](/powershell/module/az.keyvault/get-azkeyvaultkey)verwenden, um die Versionsnummer des aktuellen Schlüssels zu erhalten. Beispiel: `Get-AzKeyVaultKey -VaultName 'contosorms-kv' -KeyName 'contosorms-byok'`

Wenn Sie sicherstellen müssen, dass die Schlüssel-URL für Azure Information Protection richtig festgelegt ist: führen Sie in Azure Key Vault [Get-azkeyvaultkey](/powershell/module/az.keyvault/get-azkeyvaultkey) aus, um die Schlüssel-URL anzuzeigen.

Wenn der Azure-Rights Management Dienst bereits aktiviert ist, führen Sie [Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties) aus, um Azure Information Protection zu informieren, dass dieser Schlüssel als aktiver Mandanten Schlüssel für den Azure Rights Management-Dienst verwendet werden soll. Wenn Sie diesen Schritt nicht ausführen, verwendet Azure Information Protection weiterhin den von Microsoft verwalteten Standardschlüssel, der automatisch für Ihren Mandanten erstellt wurde.


## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihren Mandantenschlüssel nun geplant und gegebenenfalls erstellt und konfiguriert haben, führen Sie folgende Schritte aus:

1.  Beginnen Sie mit der Verwendung Ihres Mandantenschlüssels:
    
    - Wenn der Schutzdienst noch nicht aktiviert ist, müssen Sie jetzt den Rights Management-Dienst aktivieren, damit Ihre Organisation mit der Verwendung von Azure Information Protection beginnen kann. Die Benutzer beginnen sofort mit der Verwendung Ihres Mandantenschlüssels (verwaltet von Microsoft oder von Ihnen in Azure Key Vault).
    
        Weitere Informationen zur Aktivierung finden Sie unter [Aktivieren des Schutz Dienstanbieter von Azure Information Protection](./activate-service.md).
        
    - Wenn der Rights Management-Dienst bereits aktiviert wurde und Sie sich dann zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, erfolgt ein gestaffelter Übergang der Benutzer vom alten zum neuen Mandantenschlüssel. Dieser gestaffelte Übergang kann bis zum vollständigen Abschluss einige Wochen in Anspruch nehmen. Auf Dokumente und Dateien, die mit dem alten Mandantenschlüssel geschützt wurden, können autorisierte Benutzer weiterhin zugreifen.
        
2. Erwägen Sie die Aktivierung der Verwendungsprotokollierung, durch die jede vom Azure Rights Management-Dienst durchgeführte Transaktion protokolliert wird.
    
    Wenn Sie sich zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, enthält die Protokollierung Informationen über die Nutzung Ihres Mandantenschlüssels. Dies wird im folgenden Ausschnitt einer in Excel angezeigten Protokolldatei dargestellt, in der die Anforderungstypen **KeyVaultDecryptRequest** und **KeyVaultSignRequest** anzeigen, dass der Mandantenschlüssel verwendet wird.
    
    ![Protokolldatei in Excel, in der der Mandantenschlüssel verwendet wird.](./media/RMS_Logging.png)
    
    Weitere Informationen zur Verwendungs Protokollierung finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md).
    
3.  Verwaltung Ihres Mandantenschlüssels.
    
    Weitere Informationen über die Lebenszyklusvorgänge für Ihren Mandantenschlüssel finden Sie unter [Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel](./operations-tenant-key.md).
