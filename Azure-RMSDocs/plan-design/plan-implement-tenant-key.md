---
title: "Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels | Azure Information Protection"
description: "Informationen zum Planen und Verwalten Ihres Azure Information Protection-Mandantenschlüssels. Sie können die Standardeinstellung, nach der Microsoft Ihren Mandantenschlüssel verwaltet, ändern und Ihren eigenen Mandantenschlüssel verwalten, um bestimmte Vorschriften in Ihrer Organisation einzuhalten. Das Verwalten Ihres eigenen Mandantenschlüssels wird auch als &quot;Bring Your Own Key&quot; (kurz BYOK) bezeichnet."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 433a655870556ed045273713f6773f36c3d86fc1


---

# <a name="planning-and-implementing-your-azure-information-protection-tenant-key"></a>Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels

>*Gilt für: Azure Information Protection, Office 365*

Verwenden Sie die Informationen in diesem Artikel zum Planen und Verwalten Ihres Azure Information Protection-Mandantenschlüssels. Angenommen, Sie möchten die Standardeinstellung ändern, dass Microsoft Ihren Mandantenschlüssel verwaltet, und Ihren eigenen Mandantenschlüssel verwalten, um bestimmte Vorschriften in Ihrer Organisation einzuhalten. Das Verwalten Ihres eigenen Mandantenschlüssels wird auch als "Bring Your Own Key" (kurz BYOK) bezeichnet.

> [!NOTE]
> Die lokale Entsprechung des Azure Information Protection-Mandantenschlüssels wird als SLC-Schlüssel (Server Licensor Certificate) bezeichnet. Azure Information Protection verwaltet einen oder mehrere Schlüssel für jede Organisation, die über ein Abonnement von Azure Information Protection verfügt. Immer, wenn Schlüssel für Azure Information Protection in einer Organisation verwendet werden (z.B. Benutzerschlüssel, Computerschlüssel, Dokumentverschlüsselungsschlüssel), werden sie kryptografisch mit Ihrem Azure Information Protection-Mandantenschlüssel verkettet.

**Kurz zusammengefasst:** Verwenden Sie die folgende Tabelle als eine kurze Einführung in die empfohlene Mandantenschlüsseltopologie. Weitere Informationen finden Sie in der Zusatzdokumentation.

Wenn Sie Azure Information Protection mit einem von Microsoft verwalteten Mandantenschlüssel bereitstellen, können Sie später zu BYOK wechseln. Sie können allerdings derzeit noch nicht Ihren Azure Information Protection-Mandantenschlüssel von BYOK in die Verwaltung durch Microsoft ändern.

|Geschäftliche Anforderung|Empfohlene Mandantenschlüsseltopologie|
|------------------------|-----------------------------------|
|Schnelles Bereitstellen von Azure Information Protection ohne spezielle Hardware|Von Microsoft verwaltet|
|Volle IRM-Funktionalität in Exchange Online mit dem Azure Rights Management-Dienst|Von Microsoft verwaltet|
|Schlüssel werden von Ihnen erstellt und in einem Hardwaresicherheitsmodul (HSM) geschützt|BYOK<br /><br />Derzeit führt diese Konfiguration zu eingeschränkter IRM-Funktionalität in Exchange Online. Weitere Informationen finden Sie unter [BYOK – Preise und Einschränkungen](byok-price-restrictions.md).|

## <a name="choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok"></a>Wählen Sie Ihre Mandantenschlüsseltopologie aus: Verwaltet von Microsoft (Standard) oder verwaltet von Ihnen (BYOK)
Entscheiden Sie, welche Mandantenschlüsseltopologie für Ihre Organisation am besten geeignet ist. Standardmäßig generiert Azure Information Protection Ihren Mandantenschlüssel und verwaltet die meisten Aspekte des Lebenszyklus des Mandantenschlüssels. Dies ist die einfachste Möglichkeit mit dem geringsten Verwaltungsaufwand. In den meisten Fällen müssen Sie noch nicht einmal wissen, dass Sie einen Mandantenschlüssel besitzen. Sie registrieren sich einfach für Azure Information Protection, und der restliche Schlüsselverwaltungsprozess wird von Microsoft erledigt.

Alternativ könnten Sie uneingeschränkte Kontrolle über Ihren Mandantenschlüssel erreichen, indem Sie [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) verwenden. Dieses Szenario umfasst die Erstellung Ihres Mandantenschlüssels und die lokale Aufbewahrung Ihrer Masterkopie. Dieses Szenario wird häufig als „Bring Your Own Key“ (BYOK) bezeichnet. Bei dieser Option geschieht Folgendes:

1.  Sie generieren Ihren Mandantenschlüssel lokal, entsprechend Ihrer IT- und Sicherheitsrichtlinien.

2.  Sie übertragen unter Verwendung von Azure Key Vault den Mandantenschlüssel sicher von einem Hardwaresicherheitsmodul (HSM), das sich in Ihrem Besitz befindet, auf HSMs, die Microsoft gehören und von Microsoft verwaltet werden. Während dieses Prozesses verlässt Ihr Mandantenschlüssel nie die Hardwareschutzgrenzen.

3.  Wenn Sie Ihren Mandantenschlüssel an Microsoft übertragen, bleibt er durch Azure Key Vault geschützt.

Auch wenn dies optional ist, möchten Sie wahrscheinlich auch die beinahe in Echtzeit erstellten Nutzungsprotokolle von Azure Information Protection verwenden, um genau verfolgen zu können, wie und wann Ihr Mandantenschlüssel verwendet wird.

> [!NOTE]
> Als zusätzliche Schutzmaßnahme verwendet Azure Key Vault in Regionen wie Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien getrennte Sicherheitsdomänen für seine Rechenzentren. Gleiches gilt für verschiedene Azure-Instanzen wie Microsoft Azure Deutschland und Azure für Behörden. Wenn Sie Ihren eigenen Mandantenschlüssel verwalten, ist dieser an die Sicherheitsdomäne der Region oder Instanz gebunden, in der Ihr Azure Information Protection-Mandant registriert ist. Ein Mandantenschlüssel eines europäischen Kunden kann beispielsweise nicht in Rechenzentren in Nordamerika oder Asien verwendet werden.

## <a name="the-tenant-key-lifecycle"></a>Der Lebenszyklus des Mandantenschlüssels
Wenn Sie sich entschließen, dass Microsoft Ihren Mandantenschlüssel verwalten soll, wickelt Microsoft die meisten aller Vorgänge des Schlüssellebenszyklus ab. Wenn Sie sich jedoch entschließen, Ihren Mandantenschlüssel selbst zu verwalten, sind Sie für zahlreiche der Vorgänge des Schlüssellebenszyklus sowie einige zusätzliche Verfahren in Azure Key Vault verantwortlich.

Die folgenden Diagramme zeigen und vergleichen diese zwei Optionen. Das erste Diagramm zeigt, wie niedrig der Verwaltungsaufwand in der Standardkonfiguration ist, wenn Microsoft den Mandantenschlüssel verwaltet.

![Lebenszyklus des Azure Information Protection-Mandantenschlüssels – verwaltet von Microsoft, Standardeinstellung](../media/RMS_BYOK_cloud.png)

Das zweite Diagramm zeigt die zusätzlichen Schritte, die erforderlich sind, wenn Sie Ihren eigenen Mandantenschlüssel verwalten.

![Lebenszyklus des Azure Information Protection-Mandantenschlüssels – verwaltet von Ihnen, BYOK](../media/RMS_BYOK_onprem4.png)

Wenn Sie sich entschließen, Ihren Mandantenschlüssel von Microsoft verwalten zu lassen, müssen Sie nichts weiter unternehmen, damit der Schlüssel generiert wird. Sie können direkt unter [Nächste Schritte](plan-implement-tenant-key.md#next-steps) fortfahren.  

Wenn Sie sich entschließen, Ihren Mandantenschlüssel selbst zu verwalten, finden Sie in den folgenden Abschnitten weitere Informationen hierzu, die Sie lesen sollten.

## <a name="implementing-your-azure-information-protection-tenant-key"></a>Implementieren Ihres Azure Information Protection-Mandantenschlüssels

Verwenden Sie die Informationen und Verfahren in diesem Abschnitt, wenn Sie sich entschieden haben, Ihren Mandantenschlüssel selber zu generieren und zu verwalten – das BYOK-Szenario (Bring Your Own Key):


> [!IMPORTANT]
> Wenn Sie Azure Information Protection zunächst mit einem von Microsoft verwalteten Mandantenschlüssel verwendet haben und jetzt Ihren Mandantenschlüssel selbst verwalten möchten (BYOK), bleiben die zuvor geschützten Dokumente und E-Mails über einen archivierten Schlüssel zugänglich. Wenn einige Ihrer Benutzer jedoch Office 2010 ausführen, [wenden Sie sich vor dem Durchführen dieser Verfahren an den Microsoft-Support](../get-started/information-support.md#to-contact-microsoft-support). Für diese Computer sind einige zusätzliche Konfigurationsschritte erforderlich.
> 
> Wenden Sie sich auch an den [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support), wenn Ihre Organisation über bestimmte Richtlinien für den Umgang mit Schlüsseln verfügt.

### <a name="prerequisites-for-byok"></a>Voraussetzungen für BYOK
In der folgenden Tabelle finden Sie eine Liste der Voraussetzungen für „Bring Your Own Key“ (BYOK).

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Abonnement, das Azure Information Protection unterstützt.|Weitere Informationen zu den verfügbaren Abonnements finden Sie auf der [Preisseite](https://go.microsoft.com/fwlink/?LinkId=827589) zu Azure Information Protection.|
|Sie verwenden nicht RMS for Individuals oder Exchange Online. Oder, falls Sie doch Exchange Online verwenden, verstehen und akzeptieren Sie die Einschränkungen, die bei der Verwendung von BYOK mit dieser Konfiguration einhergehen.|Weitere Informationen zu diesen und anderen Einschränkungen für BYOK finden Sie unter [BYOK – Preise und Einschränkungen](byok-price-restrictions.md) .<br /><br />**Wichtig**: Derzeit ist BYOK nicht mit Exchange Online kompatibel.|
|Alle erforderlichen Komponenten für Key Vault BYOK, wozu ein kostenpflichtiges oder Testabonnement von Azure zählt. |Siehe die [Voraussetzungen für BYOK](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) in der Azure Key Vault-Dokumentation. <br /><br /> Das kostenlose Azure-Abonnement, das Zugriff zum Konfigurieren von Azure Active Directory und benutzerdefinierten Azure Rights Management-Vorlagen bietet (**Zugriff auf Azure Active Directory**), reicht zum Verwenden von Azure Key Vault nicht aus. Um zu bestätigen, dass Sie über ein Azure-Abonnement verfügen, das Sie für BYOK verwenden können, nutzen Sie die PowerShell-Cmdlets von [Azure Resource Manager](https://msdn.microsoft.com/library/azure/mt786812\(v=azure.300\).aspx): <br /><br /> 1. Starten Sie eine Azure PowerShell-Sitzung, und melden Sie sich bei Ihrem Azure-Konto mithilfe des folgenden Befehls an: `Login-AzureRmAccount`<br /><br />2. Geben Sie Folgendes ein, und vergewissern Sie sich, dass Werte für den Namen und die ID Ihres Abonnements und Ihre Mandanten-ID angezeigt werden und der Status „Aktiviert“ ist: `Get-AzureRmSubscription`<br /><br />Wenn keine Werte angezeigt werden und Sie lediglich an die Eingabeaufforderung zurückverwiesen werden, haben Sie kein Azure-Abonnement, das sich für BYOK eignet. <br /><br />**Hinweis** (zusätzlich zu den BYOK-Voraussetzungen): Wenn Sie von AD RMS zu Azure Information Protection mit der Softwareschlüssel-zu-Hardwareschlüssel-Migration migrieren, muss die Thales-Firmware mindestens in der Version 11.62 vorliegen.|
|Das Azure Rights Management-Verwaltungsmodul für Windows PowerShell.|Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md). <br /><br />Wenn Sie dieses Windows PowerShell-Modul zuvor installiert haben, überprüfen Sie mit dem folgenden Befehl, ob Sie Version **2.5.0.0** oder höher verwenden: `(Get-Module aadrm -ListAvailable).Version`|

Weitere Informationen zu Thales-HSMs und deren Verwendung mit Azure Key Vault finden Sie auf der [Thales-Website](https://www.thales-esecurity.com/msrms/cloud).

### <a name="instructions-for-byok"></a>Hinweise zu BYOK

Gehen Sie wie im Abschnitt [Gewusst wie: Generieren und Übertragen von HSM-geschützten Schlüsseln für Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/) der Azure Key Vault-Dokumentation beschrieben vor, um Ihren eigenen Mandantenschlüssel zu generieren und an Azure Key Vault zu übertragen.

Wenn der Schlüssel an Key Vault übertragen wird, wird ihm in Key Vault eine Schlüssel-ID zugewiesen, bei der es sich um eine URL handelt, die den Namen des Schlüsseltresors, den Schlüsselcontainer, den Namen des Schlüssels und die Schlüsselversion enthält. Zum Beispiel: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Sie müssen den Azure Rights Management-Dienst von Azure Information Protection anweisen, diesen Schlüssel zu verwenden, indem Sie diese URL angeben.

Bevor Azure Information Protection den Schlüssel verwenden kann, muss der Azure Rights Management-Dienst zum Verwenden des Schlüssels im Schlüsseltresor Ihrer Organisation autorisiert werden. Hierzu verwendet der Azure Key Vault-Administrator das Key Vault-PowerShell-Cmdlet [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/en-us/library/mt603625(v=azure.300\).aspx) und erteilt dem Azure Rights Management-Dienstprinzipal die Berechtigungen unter Verwendung der GUID 00000012-0000-0000-c000-000000000000. Beispiel:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get

Sie können Azure Information Protection jetzt so konfigurieren, dass dieser Schlüssel als Azure Information Protection-Mandantenschlüssel Ihrer Organisation verwendet wird. Stellen Sie unter Verwendung des Azure RMS-Cmdlets zunächst eine Verbindung mit dem Azure Rights Management-Dienst her, und melden Sie sich an:

    Connect-AadrmService

Führen Sie dann das Cmdlet [Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx) aus, und geben Sie dabei die Schlüssel-URL an. Beispiel:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

> [!IMPORTANT]
> In diesem Beispiel ist „aaaabbbbcccc111122223333“ die Version des zu verwendenden Schlüssels. Wenn Sie die Version nicht angeben, wird ohne Warnung die aktuelle Version des Schlüssels verwendet, und der Befehl scheint zu funktionieren. Wenn jedoch Ihr Schlüssel in Key Vault später aktualisiert (erneuert) wird, wird der Azure Rights Management-Dienst für Ihren Mandanten nicht mehr funktionieren, auch wenn Sie den Befehl „Use-AadrmKeyVaultKey“ erneut ausführen.
>
>Stellen Sie sicher, dass Sie die Schlüsselversion zusätzlich zum Schlüsselnamen angeben, wenn Sie diesen Befehl ausführen. Sie können den Azure Key Vault-Befehl [Get-AzureKeyVaultKey](https://docs.microsoft.com/powershell/resourcemanager/azurerm.keyvault\/v2.3.0\/get-azurekeyvaultkey) verwenden, um die Versionsnummer des aktuellen Schlüssels zu erhalten. Beispiel: `Get-AzureKeyVaultKey -VaultName 'contosorms-kv' -KeyName 'contosorms-byok'`

Falls Sie sicherstellen müssen, dass die Schlüssel-URL im Azure RMS-Dienst korrekt festgelegt wurde, können Sie in Azure Key Vault [Get-AzureKeyVaultKey](https://msdn.microsoft.com/en-us/library/dn868053(v=azure.300\).aspx) ausführen, um die Schlüssel-URL anzuzeigen.


## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihren Mandantenschlüssel geplant und gegebenenfalls generiert haben, führen Sie folgende Schritte aus:

1.  Beginnen Sie mit der Verwendung Ihres Mandantenschlüssels:

    -   Wenn noch nicht geschehen, müssen Sie jetzt den Rights Management-Dienst aktivieren, damit Ihre Organisation mit der Verwendung von Azure Information Protection beginnen kann. Benutzer beginnen sofort mit der Verwendung Ihres Mandantenschlüssels (verwaltet von Microsoft oder von Ihnen in Azure Key Vault).

        Weitere Informationen zur Aktivierung finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

    -   Wenn Sie den Rights Management-Dienst bereits aktiviert hatten und sich dann zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, erfolgt ein gestaffelter Übergang der Benutzer vom alten zum neuen Mandantenschlüssel, wobei dieser gestaffelte Übergang bis zum vollständigen Abschluss einige Wochen in Anspruch nehmen kann. Auf Dokumente und Dateien, die mit dem alten Mandantenschlüssel geschützt wurden, können autorisierte Benutzer weiterhin zugreifen.

2.  Erwägen Sie die Aktivierung der Verwendungsprotokollierung, durch die jede vom Azure Rights Management-Dienst durchgeführte Transaktion protokolliert wird.

    Wenn Sie sich zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, enthält die Protokollierung Informationen über die Nutzung Ihres Mandantenschlüssels. Dies wird im folgenden Ausschnitt einer in Excel angezeigten Protokolldatei dargestellt, in der die Anforderungstypen **KeyVaultDecryptRequest** und **KeyVaultSignRequest** anzeigen, dass der Mandantenschlüssel verwendet wird.

    ![Protokolldatei in Excel, in der der Mandantenschlüssel verwendet wird.](../media/RMS_Logging.png)

    Weitere Informationen zur Verwendungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).

3.  Pflegen Sie Ihren Mandantenschlüssel.

    Weitere Informationen finden Sie unter [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](../deploy-use/operations-tenant-key.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


