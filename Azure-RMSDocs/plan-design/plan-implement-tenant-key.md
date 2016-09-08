---
title: "Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels | Azure RMS"
description: "Verwenden Sie die Informationen in diesem Artikel, um Ihren Rights Management (RMS)-Mandantenschlüssel für Azure RMS zu planen und zu verwalten. Angenommen, Sie möchten die Standardeinstellung ändern, dass Microsoft Ihren Mandantenschlüssel verwaltet, und Ihren eigenen Mandantenschlüssel verwalten, um bestimmte Vorschriften in Ihrer Organisation einzuhalten. Das Verwalten Ihres eigenen Mandantenschlüssels wird auch als &quot;Bring Your Own Key&quot; (kurz BYOK) bezeichnet."
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 3a45a12cba766fed074d8b5fcf861164802d2441


---

# Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels

>*Gilt für: Azure Rights Management, Office 365*

Verwenden Sie die Informationen in diesem Artikel, um Ihren Rights Management (RMS)-Mandantenschlüssel für Azure RMS zu planen und zu verwalten. Angenommen, Sie möchten die Standardeinstellung ändern, dass Microsoft Ihren Mandantenschlüssel verwaltet, und Ihren eigenen Mandantenschlüssel verwalten, um bestimmte Vorschriften in Ihrer Organisation einzuhalten.  Das Verwalten Ihres eigenen Mandantenschlüssels wird auch als "Bring Your Own Key" (kurz BYOK) bezeichnet.

> [!NOTE]
> Der RMS-Mandantenschlüssel ist auch als SLC-Schlüssel (Server Licensor Certificate, lizenzgebendes Serverzertifikat) bekannt. Azure RMS pflegt für jede Organisation, die Azure RMS abonniert, mindestens einen Schlüssel. Immer, wenn ein Schlüssel für RMS in einer Organisation verwendet wird (z. B. Benutzerschlüssel, Computerschlüssel, Dokumentationsverschlüsselungsschlüssel), wird dieser kryptografisch mit Ihrem RMS-Mandantenschlüssel verkettet.

**Kurz zusammengefasst:** Verwenden Sie die folgende Tabelle als eine kurze Einführung in die empfohlene Mandantenschlüsseltopologie. Weitere Informationen finden Sie in der Zusatzdokumentation.

Wenn Sie Azure RMS mit einem Mandantenschlüssel bereitstellen, der von Microsoft verwaltet wird, können Sie später zu BYOK wechseln. Sie können allerdings derzeit noch nicht Ihren Azure RMS-Mandantenschlüssel von BYOK in die Verwaltung durch Microsoft ändern.

|Geschäftliche Anforderung|Empfohlene Mandantenschlüsseltopologie|
|------------------------|-----------------------------------|
|Schnelles Bereitstellen von Azure RMS ohne spezielle Hardware|Von Microsoft verwaltet|
|Volle IRM-Funktionalität in Exchange Online mit Azure RMS|Von Microsoft verwaltet|
|Schlüssel werden von Ihnen erstellt und in einem Hardwaresicherheitsmodul (HSM) geschützt|BYOK<br /><br />Derzeit führt diese Konfiguration zu eingeschränkter IRM-Funktionalität in Exchange Online. Weitere Informationen finden Sie unter [BYOK – Preise und Einschränkungen](byok-price-restrictions.md).|

## Wählen Sie Ihre Mandantenschlüsseltopologie aus: Verwaltet von Microsoft (Standard) oder verwaltet von Ihnen (BYOK)
Entscheiden Sie, welche Mandantenschlüsseltopologie für Ihre Organisation am besten geeignet ist. Standardmäßig generiert Azure RMS Ihren Mandantenschlüssel und verwaltet die meisten Aspekte des Lebenszyklus des Mandantenschlüssels. Dies ist die einfachste Möglichkeit mit dem geringsten Verwaltungsaufwand. In den meisten Fällen müssen Sie noch nicht einmal wissen, dass Sie einen Mandantenschlüssel besitzen. Sie registrieren sich einfach für Azure RMS, und der restliche Schlüsselverwaltungsprozess wird von Microsoft erledigt.

Alternativ könnten Sie uneingeschränkte Kontrolle über Ihren Mandantenschlüssel erreichen, indem Sie [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) verwenden. Dieses Szenario umfasst die Erstellung Ihres Mandantenschlüssels und die lokale Aufbewahrung Ihrer Masterkopie. Dieses Szenario wird häufig als „Bring Your Own Key“ (BYOK) bezeichnet. Bei dieser Option geschieht Folgendes:

1.  Sie generieren Ihren Mandantenschlüssel lokal, entsprechend Ihrer IT- und Sicherheitsrichtlinien.

2.  Sie übertragen unter Verwendung von Azure Key Vault den Mandantenschlüssel sicher von einem Hardwaresicherheitsmodul (HSM), das sich in Ihrem Besitz befindet, auf HSMs, die Microsoft gehören und von Microsoft verwaltet werden. Während dieses Prozesses verlässt Ihr Mandantenschlüssel nie die Hardwareschutzgrenzen.

3.  Wenn Sie Ihren Mandantenschlüssel an Microsoft übertragen, bleibt er durch Azure Key Vault geschützt.

Obgleich dies optional ist, möchten Sie wahrscheinlich auch die beinahe in Echtzeit erstellten Nutzungsprotokolle von Azure RMS verwenden, um genau verfolgen zu können, wie und wann Ihr Mandantenschlüssel verwendet wird.

> [!NOTE]
> Als zusätzliche Schutzmaßnahme verwendet Azure Key Vault in Regionen wie Nordamerika, EMEA (Europa, Naher Osten und Afrika) und Asien getrennte Sicherheitsdomänen für seine Rechenzentren. Gleiches gilt für verschiedene Azure-Instanzen wie Microsoft Azure Deutschland und Azure für Behörden. Wenn Sie Ihren eigenen Mandantenschlüssel verwalten, ist dieser an die Sicherheitsdomäne der Region oder Instanz gebunden, in der Ihr RMS-Mandant registriert ist. Ein Mandantenschlüssel eines europäischen Kunden kann beispielsweise nicht in Rechenzentren in Nordamerika oder Asien verwendet werden.

## Der Lebenszyklus des Mandantenschlüssels
Wenn Sie sich entschließen, dass Microsoft Ihren Mandantenschlüssel verwalten soll, wickelt Microsoft die meisten aller Vorgänge des Schlüssellebenszyklus ab. Wenn Sie sich jedoch entschließen, Ihren Mandantenschlüssel selbst zu verwalten, sind Sie für zahlreiche der Vorgänge des Schlüssellebenszyklus sowie einige zusätzliche Verfahren in Azure Key Vault verantwortlich.

Die folgenden Diagramme zeigen und vergleichen diese zwei Optionen. Das erste Diagramm zeigt, wie niedrig der Verwaltungsaufwand in der Standardkonfiguration ist, wenn Microsoft den Mandantenschlüssel verwaltet.

![Lebenszyklus des Azure RMS-Mandantenschlüssels – verwaltet von Microsoft, Standardeinstellung](../media/RMS_BYOK_cloud.png)

Das zweite Diagramm zeigt die zusätzlichen Schritte, die erforderlich sind, wenn Sie Ihren eigenen Mandantenschlüssel verwalten.

![Lebenszyklus des Azure RMS-Mandantenschlüssels – verwaltet von Ihnen, BYOK](../media/RMS_BYOK_onprem4.png)

Wenn Sie sich entschließen, Ihren Mandantenschlüssel von Microsoft verwalten zu lassen, müssen Sie nichts weiter unternehmen, damit der Schlüssel generiert wird. Sie können direkt unter [Nächste Schritte](plan-implement-tenant-key.md#next-steps) fortfahren.

Wenn Sie sich entschließen, Ihren Mandantenschlüssel selbst zu verwalten, finden Sie in den folgenden Abschnitten weitere Informationen hierzu, die Sie lesen sollten.

## Implementieren Ihres Azure Rights Management-Mandantenschlüssels

Verwenden Sie die Informationen und Verfahren in diesem Abschnitt, wenn Sie sich entschieden haben, Ihren Mandantenschlüssel selber zu generieren und zu verwalten – das BYOK-Szenario (Bring Your Own Key):


> [!IMPORTANT]
> Wenn Sie bereits begonnen haben, [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu verwenden (der Dienst ist aktiviert), und Benutzer haben, die Office 2010 ausführen, [wenden Sie sich an den Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support), bevor Sie diese Prozeduren ausführen. Abhängig von Ihrem Szenario und den Voraussetzungen können Sie immer noch BYOK verwenden, allerdings mit einigen Einschränkungen bzw. zusätzlichen Schritten.
> 
> Wenden Sie sich auch an den [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support), wenn Ihre Organisation über bestimmte Richtlinien für den Umgang mit Schlüsseln verfügt.

### Voraussetzungen für BYOK
In der folgenden Tabelle finden Sie eine Liste der Voraussetzungen für „Bring Your Own Key“ (BYOK).

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Abonnement, das Azure RMS unterstützt.|Weitere Informationen zu den verfügbaren Abonnements finden Sie unter [Cloud-Abonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).|
|Sie verwenden nicht RMS for Individuals oder Exchange Online. Oder, falls Sie doch Exchange Online verwenden, verstehen und akzeptieren Sie die Einschränkungen, die bei der Verwendung von BYOK mit dieser Konfiguration einhergehen.|Weitere Informationen zu diesen und anderen Einschränkungen für BYOK finden Sie unter [BYOK – Preise und Einschränkungen](byok-price-restrictions.md) .<br /><br />**Wichtig**: Derzeit ist BYOK nicht mit Exchange Online kompatibel.|
|Alle Voraussetzungen, die für Key Vault-BYOK aufgeführt sind.|Siehe [Voraussetzungen für BYOK](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) in der Azure Key Vault-Dokumentation. <br /><br />**Hinweis**: Wenn Sie von AD RMS zu Azure RMS mit der Softwareschlüssel-zu-Hardwareschlüssel-Migration migrieren, muss die Thales-Firmware mindestens in der Version 11.62 vorliegen.|
|Das Azure RMS-Verwaltungsmodul für Windows PowerShell.|Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md). <br /><br />Wenn Sie dieses Windows PowerShell-Modul zuvor installiert haben, überprüfen Sie mit dem folgenden Befehl, ob Sie Version **2.5.0.0** oder höher verwenden: `(Get-Module aadrm -ListAvailable).Version`|

Weitere Informationen zu Thales-HSMs und deren Verwendung mit Azure Key Vault finden Sie auf der [Thales-Website](https://www.thales-esecurity.com/msrms/cloud).

Gehen Sie wie im Abschnitt [Gewusst wie: Generieren und Übertragen von HSM-geschützten Schlüsseln für Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/) der Azure Key Vault-Dokumentation beschrieben vor, um Ihren eigenen Mandantenschlüssel zu generieren und an Azure Key Vault zu übertragen.

Wenn der Schlüssel an Key Vault übertragen wird, wird ihm in Key Vault eine Schlüssel-ID zugewiesen, bei der es sich um eine URL handelt, die den Namen des Tresors, den Schlüsselcontainer, den Namen des Schlüssels und die Schlüsselversion enthält. Zum Beispiel: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Sie müssen Azure RMS mitteilen, dass dieser Schlüssel verwendet werden soll, indem Sie diese URL angeben.

Bevor Azure RMS den Schlüssel jedoch verwenden kann, muss Azure RMS dazu autorisiert werden, den Schlüssel im Schlüsseltresor Ihrer Organisation verwenden zu dürfen. Hierzu verwendet der Azure Key Vault-Administrator das Key Vault-PowerShell-Cmdlet [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx) und erteilt dem Azure RMS-Dienstprinzipal, **Microsoft.Azure.RMS**, die Berechtigung. Beispiel:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign 

Sie können Azure RMS jetzt so konfigurieren, dass dieser Schlüssel als Azure RMS-Mandantenschlüssel Ihrer Organisation verwendet wird. Verbinden Sie sich zunächst unter Verwendung der Azure RMS-Cmdlets mit Azure RMS, und melden Sie sich an:

    Connect-AadrmService

Führen Sie dann das Cmdlet [Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx) aus, und geben Sie dabei die Schlüssel-URL an. Beispiel:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

Falls Sie sicherstellen müssen, dass die Schlüssel-URL in Azure RMS korrekt festgelegt wurde, können Sie in Azure Key Vault [Get-AzureKeyVaultKey](https://msdn.microsoft.com/library/dn868053.aspx) ausführen, um die Schlüssel-URL anzuzeigen.


## Nächste Schritte

Nachdem Sie Ihren Mandantenschlüssel geplant und gegebenenfalls generiert haben, führen Sie folgende Schritte aus:

1.  Beginnen Sie mit der Verwendung Ihres Mandantenschlüssels:

    -   Wenn noch nicht geschehen, müssen Sie jetzt Rights Management aktivieren, damit Ihre Organisation mit der Verwendung von RMS beginnen kann. Benutzer beginnen sofort mit der Verwendung Ihres Mandantenschlüssels (verwaltet von Microsoft oder von Ihnen in Azure Key Vault).

        Weitere Informationen zur Aktivierung finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

    -   Wenn Sie Rights Management bereits aktiviert hatten und sich dann zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, erfolgt ein gestaffelter Übergang der Benutzer vom alten zum neuen Mandantenschlüssel, wobei dieser gestaffelte Übergang ein paar Wochen bis zum vollständigen Abschluss in Anspruch nehmen kann. Auf Dokumente und Dateien, die mit dem alten Mandantenschlüssel geschützt wurden, können autorisierte Benutzer weiterhin zugreifen.

2.  Erwägen Sie die Aktivierung der Verwendungsprotokollierung, durch die jede von Azure Rights Management durchgeführte Transaktion protokolliert wird.

    Wenn Sie sich zur Verwaltung des eigenen Mandantenschlüssels entschlossen haben, enthält die Protokollierung Informationen über die Nutzung Ihres Mandantenschlüssels. Dies wird im folgenden Ausschnitt einer in Excel angezeigten Protokolldatei dargestellt, in der die Anforderungstypen **KeyVaultDecryptRequest** und **KeyVaultSignRequest** anzeigen, dass der Mandantenschlüssel verwendet wird.

    ![Protokolldatei in Excel, in der der Mandantenschlüssel verwendet wird.](../media/RMS_Logging.png)

    Weitere Informationen zur Nutzungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Nutzung von Azure Rights Management](../deploy-use/log-analyze-usage.md).

3.  Pflegen Sie Ihren Mandantenschlüssel.

    Weitere Informationen finden Sie unter [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](../deploy-use/operations-tenant-key.md).




<!--HONumber=Aug16_HO4-->


