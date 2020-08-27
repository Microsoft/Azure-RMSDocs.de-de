---
title: Bring your own Key (Byok) Details-Azure Information Protection
description: Informieren Sie sich über die Details und Einschränkungen, wenn Sie von Kunden verwaltete Schlüssel (die als "Bring your own Key" bezeichnet werden, oder Byok) mit Azure Information Protection.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/14/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 3e25ff7d202b7cef964f6b83259b4ff2588c2616
ms.sourcegitcommit: 2cb5fa2a8758c916da8265ae53dfb35112c41861
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88953166"
---
# <a name="bring-your-own-key-byok-details-for-azure-information-protection"></a>Byok-Details (Bring your own Key) für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Organisationen mit einem Azure Information Protection Abonnement können Ihren Mandanten anstelle eines von Microsoft generierten Standard Schlüssels mit einem eigenen Schlüssel konfigurieren. Diese Konfiguration wird häufig als Bring your own Key (Byok) bezeichnet.

Byok und die [Verwendungs Protokollierung](log-analyze-usage.md) funktionieren nahtlos mit Anwendungen, die in den von Azure Information Protection verwendeten Azure-Rights Management Dienst integriert sind.

Zu den unterstützten Anwendungen gehören:

- **Clouddienste** wie Microsoft SharePoint oder Office 365

- **Lokale Dienste** , die Exchange-und SharePoint-Anwendungen ausführen, die den Azure Rights Management-Dienst über den RMS-Connector verwenden

- **Client Anwendungen,** z. b. Office 2019, Office 2016 und Office 2013

> [!TIP]
> Wenden Sie bei Bedarf zusätzliche Sicherheit auf bestimmte Dokumente an, indem Sie einen zusätzlichen lokalen Schlüssel verwenden. Weitere Informationen finden Sie unter [Hold Your Own Key (Hyok) Protection](configure-adrms-restrictions.md) (klassischer Client) oder [DKE-Schutz (Double Key Encryption](plan-implement-tenant-key.md#double-key-encryption-dke-aip-unified-labeling-client-only)).
> 

## <a name="azure-key-vault-key-storage"></a>Azure Key Vault Schlüsselspeicher

Vom Kunden generierte Schlüssel müssen im Azure Key Vault für den Byok-Schutz gespeichert werden.

> [!NOTE]
> Die Verwendung von HSM-geschützten Schlüsseln in der Azure Key Vault erfordert eine [Azure Key Vault Premium-Dienst Ebene](https://azure.microsoft.com/pricing/details/key-vault/), die eine zusätzliche monatliche Abonnementgebühr verursacht.

### <a name="sharing-key-vaults-and-subscriptions"></a>Freigeben von Schlüssel Tresoren und Abonnements

Es wird empfohlen, einen **dedizierten Schlüssel** Tresor für Ihren Mandanten Schlüssel zu verwenden. Dedizierte Schlüssel Tresore helfen sicherzustellen, dass Aufrufe von anderen Diensten nicht dazu führen, dass [Dienst Limits](https://docs.microsoft.com/azure/key-vault/general/service-limits) überschritten werden. Wenn Sie die Grenzwerte für den Schlüssel Tresor überschreiten, in dem Ihr Mandanten Schlüssel gespeichert ist, kann dies zu einer Antwortzeit Drosselung für Azure Rights Management Service führen.

Da für verschiedene Dienste abweichende Schlüssel Verwaltungsanforderungen gelten, empfiehlt Microsoft auch, **ein dediziertes Azure-Abonnement** für Ihren Schlüssel Tresor zu verwenden. Dedizierte Azure-Abonnements:

- Schutz vor Fehlkonfigurationen

- Sind sicherer, wenn verschiedene Dienste verschiedene Administratoren haben

Um ein Azure-Abonnement für andere Dienste freizugeben, die Azure Key Vault verwenden, stellen Sie sicher, dass das Abonnement eine gemeinsame Gruppe von Administratoren verwendet. Wenn Sie bestätigen, dass alle Administratoren, die das Abonnement verwenden, ein solides Verständnis für jeden Schlüssel haben, auf den Sie zugreifen können, bedeutet dies weniger wahrscheinlich, dass Sie Ihre Schlüssel falsch konfigurieren.

**Beispiel:** Die Verwendung eines freigegebenen Azure-Abonnements, wenn Administratoren für Ihren Azure Information Protection Mandanten Schlüssel dieselben Personen sind, die Ihre Schlüssel für den Kundenschlüssel von Office 365 und CRM Online verwalten. Wenn die Schlüssel Administratoren für diese Dienste verschieden sind, wird die Verwendung dedizierter Abonnements empfohlen.

### <a name="benefits-of-using-azure-key-vault"></a>Vorteile der Verwendung von Azure Key Vault

Azure Key Vault bietet eine zentralisierte und konsistente Schlüssel Verwaltungs Lösung für viele cloudbasierte und lokale Dienste, die Verschlüsselung verwenden.

Zusätzlich zum Verwalten von Schlüsseln bietet Azure Key Vault Ihren Sicherheitsadministratoren die gleiche Verwaltungsumgebung zum Speichern von, Zugreifen auf und Verwalten von Zertifikaten und geheimen Schlüsseln (z. B. Kennwörtern) für andere Dienste und Anwendungen, die Verschlüsselung verwenden.

Das Speichern Ihres Mandanten Schlüssels im Azure Key Vault bietet die folgenden Vorteile:

|Vorteil  |Beschreibung  |
|---------|---------|
|**Integrierte Schnittstellen**| Azure Key Vault unterstützt eine Reihe von integrierten Schnittstellen für die Schlüsselverwaltung, einschließlich PowerShell, CLI, REST-APIs und das Azure-Portal. </br></br>Andere Dienste und Tools wurden in Key Vault integriert, um optimierte Funktionen für bestimmte Aufgaben, z. b. die Überwachung, zu integrieren. </br></br>Analysieren Sie z. b. Ihre Schlüssel Verwendungs Protokolle mit Operations Management Suite Log Analytics, legen Sie Warnungen fest, wenn bestimmte Kriterien erfüllt sind usw.        |
|**Rollen Trennung**| Azure Key Vault bietet eine Rollen Trennung als bewährte Sicherheitsmaßnahme. </br></br>Durch die Rollen Trennung wird sichergestellt, dass Azure Information Protection Administratoren sich auf die höchsten Prioritäten konzentrieren können, einschließlich der Verwaltung von Datenklassifizierung und-Schutz sowie von Verschlüsselungsschlüsseln und Richtlinien für bestimmte Sicherheits-oder Konformitätsanforderungen. |
|**Speicherort des Haupt Schlüssels**| Azure Key Vault ist an verschiedenen Standorten verfügbar und unterstützt Organisationen mit Einschränkungen, bei denen Hauptschlüssel verfügbar sind. </br></br>Weitere Informationen finden Sie auf der Seite [Verfügbare Produkte nach Region](https://azure.microsoft.com/regions/services/) auf der Azure-Website.|
|**Getrennte Sicherheits Domänen**|Azure Key Vault verwendet separate Sicherheits Domänen für seine Rechenzentren in Regionen wie Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien. </br></br>Außerdem verwendet Azure Key Vault verschiedene Azure-Instanzen wie Microsoft Azure Deutschland und Azure Government. |
|**Einheitliche Darstellung**| Mit Azure Key Vault können Sicherheits Administratoren außerdem Zertifikate und geheime Schlüssel (z. b. Kenn Wörter) für andere Dienste, die Verschlüsselung verwenden, speichern, darauf zugreifen und diese verwalten. <br></br>Die Verwendung von Azure Key Vault für Ihre Mandanten Schlüssel bietet Administratoren, die all diese Elemente verwalten, eine nahtlose Benutzer Leistung.|

Die neuesten Updates und Informationen darüber, wie andere Dienste  [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/general/basic-concepts)verwenden, finden Sie im [Azure Key Vault Teamblog](https://blogs.technet.microsoft.com/kv/).

## <a name="usage-logging-for-byok"></a>Verwendungs Protokollierung für Byok

Verwendungs Protokolle werden von jeder Anwendung generiert, die Anforderungen an den Azure Rights Management-Dienst sendet.

Obwohl die Verwendungs Protokollierung optional ist, empfehlen wir die Verwendung von Near Real-Time-Verwendungs Protokollen aus Azure Information Protection, um genau zu sehen, wie und wann Ihr Mandanten Schlüssel verwendet wird.

Weitere Informationen zur Schlüssel Verwendungs Protokollierung für Byok finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](log-analyze-usage.md).

> [!TIP]
> Zur weiteren Sicherheit kann die Azure Information Protection Verwendungs Protokollierung mit [Azure Key Vault Protokollierung](https://docs.microsoft.com/azure/key-vault/general/logging)quer referenziert werden. Key Vault Protokolle bieten eine zuverlässige Methode, um unabhängig zu überwachen, ob Ihr Schlüssel nur von Azure Rights Management Service verwendet wird.
>
> Wenn erforderlich, können Sie den Zugriff auf Ihren Schlüssel sofort widerrufen, indem Sie die Berechtigungen für den Schlüssel Tresor entfernen.

## <a name="options-for-creating-and-storing-your-key"></a>Optionen zum Erstellen und Speichern Ihres Schlüssels

Byok unterstützt Schlüssel, die entweder in Azure Key Vault oder lokal erstellt werden.

Wenn Sie Ihren Schlüssel lokal erstellen, müssen Sie ihn dann übertragen oder in Ihr Key Vault importieren und Azure Information Protection für die Verwendung des Schlüssels konfigurieren. Führen Sie in Azure Key Vault eine beliebige zusätzliche Schlüsselverwaltung aus.

Optionen zum Erstellen und Speichern Ihres eigenen Schlüssels:

- **Erstellt in Azure Key Vault.** Erstellen und speichern Sie Ihren Schlüssel in Azure Key Vault als HSM-geschützten Schlüssel oder einem Software geschützten Schlüssel.

- **Lokal erstellt.** Erstellen Sie Ihren Schlüssel lokal, und übertragen Sie ihn mithilfe einer der folgenden Optionen auf Azure Key Vault:

    - **HSM-geschützter Schlüssel, der als HSM-geschützter Schlüssel übertragen wird.** Die am häufigsten gewählte Methode.

        Wenngleich diese Methode den meisten Verwaltungsaufwand hat, kann es erforderlich sein, dass Ihre Organisation bestimmte Vorschriften befolgt. Bei den von Azure Key Vault verwendeten HSMs handelt es 140-2 sich um eine Überprüfung auf der Basis der von

    - **Software geschützter Schlüssel, der konvertiert und in Azure Key Vault als HSM-geschützter Schlüssel übertragen wird.** Diese Methode wird nur bei der [Migration von Active Directory Rights Management Services (AD RMS)](migrate-from-ad-rms-to-azure-rms.md)unterstützt.

    - **Wird lokal als Software geschützter Schlüssel erstellt und auf Azure Key Vault als Software geschützter Schlüssel übertragen.** Diese Methode erfordert. Pfx-Zertifikat Datei.

Gehen Sie beispielsweise wie folgt vor, um einen lokal erstellten Schlüssel zu verwenden:

1. Generieren Sie Ihren Mandanten Schlüssel lokal, gemäß den IT-und Sicherheitsrichtlinien Ihres Unternehmens. Der Schlüssel dient als Masterkopie. Sie bleibt lokal, und Sie sind für die Sicherung erforderlich.

1. Erstellen Sie eine Kopie des Haupt Schlüssels, und übertragen Sie Sie auf sichere Weise aus Ihrem HSM in Azure Key Vault. Während dieses Vorgangs verlässt die Master Kopie des Schlüssels niemals die Hardware Schutz Grenze.

Nach der Übertragung wird die Kopie des Schlüssels durch Azure Key Vault geschützt.

## <a name="exporting-your-trusted-publishing-domain"></a>Exportieren Ihrer vertrauenswürdigen Veröffentlichungs Domäne

Wenn Sie sich entscheiden, Azure Information Protection zu verwenden, benötigen Sie eine vertrauenswürdige Veröffentlichungs Domäne (Trusted Publishing Domain, TPD) zum Entschlüsseln von Inhalten, die durch Azure Information Protection geschützt wurden.

Der Export der TPD wird jedoch nicht unterstützt, wenn Sie Byok für Ihren Azure Information Protection Schlüssel verwenden.

Um dieses Szenario vorzubereiten, stellen Sie sicher, dass Sie eine geeignete TPD im Voraus erstellen. Weitere Informationen finden Sie unter [Vorbereiten eines Azure Information Protection "Cloud Exit"-Plans](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/How-to-prepare-an-Azure-Information-Protection-Cloud-Exit-plan/ba-p/382631).

## <a name="implementing-byok-for-your-azure-information-protection-tenant-key"></a>BYOK-Implementierung für Ihren Azure Information Protection-Mandantenschlüssel

Verwenden Sie die folgenden Schritte, um Byok zu implementieren:

1. [Überprüfen der Byok-Komponenten](#prerequisites-for-byok)
1. [Wählen Sie einen Key Vault Standort aus.](#choosing-your-key-vault-location)
1. [Erstellen und Konfigurieren Ihres Schlüssels](#create-and-configure-your-key)

### <a name="prerequisites-for-byok"></a>Voraussetzungen für BYOK

Die Byok-Voraussetzungen variieren abhängig von der Systemkonfiguration. Stellen Sie sicher, dass Ihr System nach Bedarf die folgenden Voraussetzungen erfüllt:

|Anforderung  |Beschreibung  |
|---------|---------|
|**Azure-Abonnement**     |Für alle Konfigurationen erforderlich. </br>Weitere Informationen finden Sie unter [überprüfen, ob Sie über ein Byok-kompatibles Azure-Abonnement verfügen](#verifying-that-you-have-a-byok-compatible-azure-subscription).         |
|**Aipservice-PowerShell-Modul für Azure Information Protection**|Für alle Konfigurationen erforderlich. </br>Weitere Informationen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](./install-powershell.md).|
|**Azure Key Vault Voraussetzungen für Byok** | Wenn Sie einen HSM-geschützten Schlüssel verwenden, der lokal erstellt wurde, stellen Sie sicher, dass Sie auch die [Voraussetzungen für Byok](https://docs.microsoft.com/azure/key-vault/keys/hsm-protected-keys-byok#prerequisites) erfüllen, die in der Azure Key Vault-Dokumentation aufgeführt sind.         |
|**Thales-Firmwareversion 11,62**    |Sie müssen über eine Thales-Firmwareversion von 11,62 verfügen, wenn Sie von AD RMS zu Azure Information Protection migrieren, indem Sie den Software Schlüssel zum Hardwareschlüssel verwenden und Thales Firmware für Ihr HSM verwenden.
|**Umgehung der Firewall für vertrauenswürdige Microsoft-Dienste** |Wenn der Schlüssel Tresor, der ihren Mandanten Schlüssel enthält, Virtual Network Dienst Endpunkte für Azure Key Vault verwendet, müssen Sie vertrauenswürdigen Microsoft-Diensten gestatten, diese Firewall zu umgehen. </br>Weitere Informationen finden Sie im Blog [Virtual Network Service Endpoints for Azure Key Vault (Virtual Network-Dienstendpunkte für Azure Key Vault)](https://docs.microsoft.com/azure/key-vault/general/overview-vnet-service-endpoints).       |

#### <a name="verifying-that-you-have-a-byok-compatible-azure-subscription"></a>Überprüfen, ob Sie über ein Byok-kompatibles Azure-Abonnement verfügen

Ihr Azure Information Protection-Mandant muss über ein Azure-Abonnement verfügen. Wenn Sie noch kein Konto haben, können Sie sich für ein [kostenloses Konto](https://azure.microsoft.com/pricing/free-trial/)registrieren. Wenn Sie jedoch einen HSM-geschützten Schlüssel verwenden möchten, müssen Sie über die Dienst Ebene "Azure Key Vault Premium" verfügen.

Das kostenlose Azure-Abonnement, das den Zugriff auf Azure Active Directory Konfiguration und die Konfiguration der benutzerdefinierten Rights Management Azure-Vorlage ermöglicht, reicht *nicht* für die Verwendung Azure Key Vault aus.

Gehen Sie wie folgt vor [Azure PowerShell](https://docs.microsoft.com/powershell/azure/) , um zu überprüfen, ob Sie über ein Azure-Abonnement verfügen, das mit Byok kompatibel ist:

1. Starten Sie eine Azure PowerShell Sitzung als Administrator.

1. Melden Sie sich mithilfe von als globaler Administrator für Ihren Azure Information Protection Mandanten an `Connect-AzAccount` .

1. Kopieren Sie das in die Zwischenablage angezeigte Token. Wechseln Sie dann in einem Browser zu, https://microsoft.com/devicelogin und geben Sie das kopierte Token ein.

    Weitere Informationen finden Sie [unter Anmelden mit Azure PowerShell](https://docs.microsoft.com/powershell/azure/authenticate-azureps).

1. Geben Sie in der PowerShell-Sitzung ein `Get-AzSubscription` , und vergewissern Sie sich, dass die folgenden Werte angezeigt werden:

    - Name und ID Ihres Abonnements
    - Ihre Azure Information Protection Mandanten-ID
    - Bestätigung, dass der Status aktiviert ist

    Wenn keine Werte angezeigt werden und Sie zur Eingabeaufforderung zurückkehren, verfügen Sie nicht über ein Azure-Abonnement, das für Byok verwendet werden kann.

### <a name="choosing-your-key-vault-location"></a>Auswählen eines Speicherorts für Ihren Schlüsseltresor

Wenn Sie einen Schlüsseltresor für den Schlüssel erstellen, der als Ihr Mandantenschlüssel für Azure Information verwendet werden soll, müssen Sie einen Speicherort bestimmen. Dieser Speicherort ist eine Azure-Region oder -Instanz.

Treffen Sie Ihre Entscheidung vorrangig anhand von Konformitätsgründen. Die Minimierung der Netzwerklatenz ist zweitrangig:

- Wenn Sie die Byok-Schlüsselmethode aus Kompatibilitätsgründen ausgewählt haben, können diese Konformitätsanforderungen auch vorschreiben, welche Azure-Region oder-Instanz zum Speichern Ihres Azure Information Protection Mandanten Schlüssels verwendet werden kann.

- Alle kryptografischen Aufrufe der Schutzkette an Ihren Azure Information Protection Schlüssel. Daher empfiehlt es sich, die Netzwerk Latenz zu minimieren, die für diese Aufrufe erforderlich ist, indem Sie Ihren Schlüssel Tresor in derselben Azure-Region oder-Instanz wie Ihre Azure Information Protection Mandanten erstellen.

Um den Speicherort Ihres Azure Information Protection Mandanten zu identifizieren, verwenden Sie das PowerShell-Cmdlet [Get-aipserviceconfiguration](https://docs.microsoft.com/powershell/module/aipservice/get-aipserviceconfiguration) , und identifizieren Sie die Region aus den URLs. Beispiel:

```ps
LicensingIntranetDistributionPointUrl : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing
```
    
**rms.na.aadrm.com** weist z.B. auf die Region Nordamerika hin.

In der folgenden Tabelle sind die empfohlenen Azure-Regionen und-Instanzen zum Minimieren der Netzwerk Latenz aufgeführt

|Azure-Region oder -Instanz|Empfohlener Speicherort für Ihren Schlüsseltresor|
|---------------|--------------------|
|rms.**na**.aadrm.com|**USA, Norden-Mitte** oder **USA, Osten**|
|rms.**eu**.aadrm.com|**Nordeuropa** oder **West Europa**|
|rms.**ap**.aadrm.com|**Asien, Osten** oder **Südostasien**|
|rms.**sa**.aadrm.com|**USA, Westen** oder **USA, Osten**|
|rms.**govus**.aadrm.com|**USA, Mitte** oder **USA, Osten 2**|
|RMS.**aadrm.US**|**US gov Virginia** oder **US gov Arizona**|
|RMS.**aadrm.cn**|**China, Osten 2** oder **China, Norden 2**|

### <a name="create-and-configure-your-key"></a>Erstellen und Konfigurieren Ihres Schlüssels

Erstellen Sie eine Azure Key Vault und den Schlüssel, den Sie für die Azure Information Protection verwenden möchten. Weitere Informationen finden Sie in der [Azure Key Vault-Dokumentation](https://docs.microsoft.com/azure/key-vault/).

Beachten Sie Folgendes, wenn Sie Ihre Azure Key Vault und den Schlüssel für Byok konfigurieren:

- [Schlüssellängen Anforderungen](#key-length-requirements)
- [Lokales Erstellen eines HSM-geschützten Schlüssels und übertragen des Schlüssels in Ihren Schlüssel Tresor](#creating-an-hsm-protected-key-on-premises-and-transferring-it-to-your-key-vault)
- [Konfigurieren von Azure Information Protection mit Ihrer Schlüssel-ID](#configuring-azure-information-protection-with-your-key-id)
- [Autorialisieren des Azure Rights Management-Dienstanbieter für die Verwendung Ihres Schlüssels](#authorizing-the-azure-rights-management-service-to-use-your-key)

#### <a name="key-length-requirements"></a>Schlüssellängen Anforderungen

Stellen Sie beim Erstellen des Schlüssels sicher, dass die Schlüssellänge entweder 2048 Bits (empfohlen) oder 1024 Bits ist. Andere Schlüssellängen werden von Azure Information Protection nicht unterstützt.

> [!NOTE]
> 1024-Bit-Schlüssel werden nicht als eine angemessene Schutz Ebene für aktive Mandanten Schlüssel betrachtet.
>
>Microsoft unterstützt nicht die Verwendung niedrigerer Schlüssellängen, wie z. b. 1024-Bit-RSA-Schlüssel, und die zugehörige Verwendung von Protokollen, die unzureichende Schutz Ebenen bieten, z. b. SHA-1.
>

#### <a name="creating-an-hsm-protected-key-on-premises-and-transferring-it-to-your-key-vault"></a>Lokales Erstellen eines HSM-geschützten Schlüssels und übertragen des Schlüssels in Ihren Schlüssel Tresor

Wenn Sie einen HSM-geschützten Schlüssel lokal erstellen und in Ihren Schlüssel Tresor als HSM-geschützten Schlüssel übertragen möchten, befolgen Sie die Verfahren in der Azure Key Vault-Dokumentation: [generieren und übertragen von HSM-geschützten Schlüsseln für Azure Key Vault](https://docs.microsoft.com/azure/key-vault/keys/hsm-protected-keys-byok).

Damit Azure Information Protection den übertragenen Schlüssel verwenden können, müssen alle Key Vault Vorgänge für den Schlüssel zulässig sein, einschließlich:

- encrypt
- Entschlüsseln
- wrapKey
- unwrapKey
- Signieren
- Überprüfen

Standardmäßig sind alle Key Vault Vorgänge zulässig.

Um die zulässigen Vorgänge für einen bestimmten Schlüssel zu überprüfen, führen Sie den folgenden PowerShell-Befehl aus:

```ps
(Get-AzKeyVaultKey -VaultName <key vault name> -Name <key name>).Attributes.KeyOps
```

Fügen Sie bei Bedarf zugelassene Vorgänge hinzu, indem Sie " [Update-azkeyvaultkey](https://docs.microsoft.com/powershell/module/az.keyvault/update-azkeyvaultkey) " und den *keyops* -Parameter verwenden.

#### <a name="configuring-azure-information-protection-with-your-key-id"></a>Konfigurieren von Azure Information Protection mit Ihrer Schlüssel-ID

Die im Azure Key Vault gespeicherten Schlüssel verfügen jeweils über eine Schlüssel-ID.

Bei der Schlüssel-ID handelt es sich um eine URL, die den Namen des Schlüssel Tresors, den Schlüssel Container, den Namen des Schlüssels und die Schlüssel Version enthält. Beispiel:

**https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**.

Konfigurieren Sie Azure Information Protection, um Ihren Schlüssel zu verwenden, indem Sie seine Key Vault-URL angeben.

#### <a name="authorizing-the-azure-rights-management-service-to-use-your-key"></a>Autorialisieren des Azure Rights Management-Dienstanbieter für die Verwendung Ihres Schlüssels

Der Azure Rights Management-Dienst muss für die Verwendung Ihres Schlüssels autorisiert sein. Azure Key Vault Administratoren können diese Autorisierung mithilfe der Azure-Portal oder Azure PowerShell aktivieren.

##### <a name="enabling-key-authorization-using-the-azure-portal"></a>Aktivieren der Schlüssel Autorisierung mithilfe der Azure-Portal

1. Melden Sie sich beim Azure-Portal an, und wechseln Sie zu **Schlüssel Tresoren**  >  **\<*your key vault name*>**  >  **Zugriffsrichtlinien**  >  **Hinzufügen neu**.

1. Wählen Sie im Bereich **Zugriffs Richtlinie hinzufügen** im Listenfeld **aus Vorlage konfigurieren (optional)** **Azure Information Protection Byok**aus, und klicken Sie dann auf **OK**.

    Die ausgewählte Vorlage weist die folgende Konfiguration auf:

    - Der Wert **Select Principal** ist auf **Microsoft Rights Management Services** festgelegt.
    - Zu den ausgewählten **Schlüssel Berechtigungen** zählen **Get,** **entschlüsseln** und **Sign.**

##### <a name="enabling-key-authorization-using-powershell"></a>Aktivieren der Schlüssel Autorisierung mithilfe von PowerShell

Führen Sie das Key Vault PowerShell-Cmdlet [Set-azkeyvaultaccesspolicy](https://docs.microsoft.com/powershell/module/az.keyvault/set-azkeyvaultaccesspolicy)aus, und erteilen Sie dem Azure Rights Management-Dienst Prinzipal mithilfe der GUID **00000012-0000-0000-C000-000000000000**Berechtigungen.

Beispiel:

```ps
Set-AzKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,sign,get
```

### <a name="configure-azure-information-protection-to-use-your-key"></a>Konfigurieren von Azure Information Protection für die Verwendung Ihres Schlüssels

Nachdem Sie alle obigen Schritte abgeschlossen haben, können Sie Azure Information Protection so konfigurieren, dass dieser Schlüssel als Mandanten Schlüssel Ihrer Organisation verwendet wird.

Führen Sie mit Azure RMS Cmdlets die folgenden Befehle aus:

1. Stellen Sie eine Verbindung mit dem Azure Rights Management Dienst her, und melden Sie sich
    ```ps
    Connect-AipService
    ```

1. Führen Sie das [Cmdlet use-aipservicekeyvaultkey](https://docs.microsoft.com/powershell/module/aipservice/use-aipservicekeyvaultkey)aus, und geben Sie dabei die Schlüssel-URL an. Beispiel:

    ```ps
    Use-AipServiceKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/<key-version>"
    ```

    > [!IMPORTANT]
    > In diesem Beispiel `<key-version>` ist die Version des Schlüssels, den Sie verwenden möchten. Wenn Sie die Version nicht angeben, wird standardmäßig die aktuelle Version des Schlüssels verwendet, und der Befehl funktioniert möglicherweise als funktionsfähig. Wenn Ihr Schlüssel jedoch später aktualisiert oder erneuert wird, funktioniert der Azure Rights Management-Dienst nicht mehr für Ihren Mandanten, auch wenn Sie den Befehl " **use-aipservicekeyvaultkey** " erneut ausführen.
    >
    > Verwenden Sie den Befehl [Get-azkeyvaultkey](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvaultkey) , um die Versionsnummer des aktuellen Schlüssels zu erhalten.
    >
    > Beispiel: `Get-AzKeyVaultKey -VaultName 'contosorms-kv' -KeyName 'contosorms-byok'`

    Um zu bestätigen, dass die Schlüssel-URL für Azure Information Protection richtig festgelegt ist, führen Sie den Befehl [Get-azkeyvaultkey](https://docs.microsoft.com/powershell/module/az.keyvault/get-azkeyvaultkey) in der Azure Key Vault aus, um die Schlüssel-URL anzuzeigen.

1. Wenn der Azure-Rights Management Dienst bereits aktiviert ist, führen Sie [Set-aipservicekeyproperties](https://docs.microsoft.com/powershell/module/aipservice/set-aipservicekeyproperties) aus, um Azure Information Protection, diesen Schlüssel als aktiven Mandanten Schlüssel für den Azure Rights Management-Dienst zu verwenden.

Azure Information Protection ist nun so konfiguriert, dass der Schlüssel anstelle des von Microsoft erstellten Standard Schlüssels verwendet wird, der automatisch für Ihren Mandanten erstellt wurde.

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Byok-Schutz konfiguriert haben, fahren Sie [mit den ersten Schritten mit Ihrem](get-started-tenant-root-keys.md) Mandanten Stamm Schlüssel fort, um weitere Informationen zum verwenden und Verwalten Ihres Schlüssels zu erhalten.
