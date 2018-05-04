---
title: Konfigurieren von Exchange Online IRM für den Azure Rights Management-Dienst von Azure Information Protection
description: Informationen und Anweisungen für Administratoren zum Konfigurieren von Exchange Online für den Azure Rights Management-Dienst, wenn der Office 365-Mandant nicht die neuen Funktionen in der Office 365-Nachrichtenverschlüsselung unterstützt.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ''
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e452f5ac4e3297106a54a2034d64f57d8f6d5302
ms.sourcegitcommit: affda7572064edaf9e3b63d88f4a18d0d6932b13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="exchange-online-irm-configuration-to-import-a-trusted-publishing-domain"></a>Konfigurieren von Exchange Online IRM zum Importieren einer vertrauenswürdigen Veröffentlichungsdomäne

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Diese Anleitung sollten Sie nur verwenden, wenn Ihr Mandant nicht die neuen Funktionen der Office 365-Nachrichtenverschlüsselung verwenden kann. Um dies herauszufinden, führen Sie den Exchange Online-Befehl „[Get-IRMConfiguration](https://technet.microsoft.com/library/dd776120(v=exchg.160\)aspx)“ aus, und prüfen Sie, ob ein **AzureRMSLicensingEnabled**-Parameter enthalten ist. Wenn dieser Parameter angezeigt wird, kann Ihr Mandant die neuen Funktionen der Office 365-Nachrichtenverschlüsselung nutzen:

- Wenn **AzureRMSLicensingEnabled** auf **TRUE** festgelegt ist, verwendet Ihr Mandant bereits die neuen Funktionen der Office 365-Nachrichtenverschlüsselung, und Sie sollten die Anleitung im nächsten Abschnitt überspringen.

- Wenn **AzureRMSLicensingEnabled** auf **FALSE** festgelegt ist, unterstützt Ihr Mandant zwar die neuen Funktionen der Office 365-Nachrichtenverschlüsselung, wurde jedoch noch nicht für diese konfiguriert. Um dies nachzuholen, lesen Sie den Artikel [Einrichten der neuen Office 365-Nachrichtenverschlüsselungsfunktionen, die auf Azure Information Protection aufbauen](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). 

Diese Anleitung sollten Sie nur verwenden, wenn Ihr Mandant nicht die neuen Funktionen der Office 365-Nachrichtenverschlüsselung verwenden kann.

## <a name="exchange-online-irm-configuration"></a>Exchange Online IRM-Konfiguration

Um Exchange Online IRM zu konfigurieren, verwenden Sie Windows PowerShell (es muss kein separates Modul installiert werden), und führen Sie [PowerShell-Befehle für Exchange Online](https://technet.microsoft.com/library/jj200677.aspx) aus.

> [!NOTE]
> Sie können Exchange Online nicht für die Unterstützung von Azure Rights Management konfigurieren, wenn Sie einen vom Kunden verwalteten Mandantenschlüssel (BYOK) für Azure Information Protection anstelle der Standardkonfiguration mit einem von Microsoft verwalteten Mandantenschlüssel verwenden. Eine solche Konfiguration ist erst nach der Migration Ihres Office 365-Mandaten durch Microsoft zwecks Unterstützung für die neuen Funktionen möglich.
>
> Wenn Sie versuchen, Exchange Online zu konfigurieren, wenn der Azure Rights Management-Dienst mit BYOK arbeitet, tritt beim Befehl zum Importieren des Schlüssels (Schritt 5 im folgenden Verfahren) mit der Fehlermeldung **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]** auf.

In den folgenden Schritten finden Sie einige typische Befehle, mit denen Sie Exchange Online aktivieren können:

1.  Wenn dies das erste Mal ist, dass Sie Windows PowerShell für Exchange Online auf Ihrem Computer verwendet haben, müssen Sie Windows PowerShell für das Ausführen signierter Skripts konfigurieren. Starten Sie Ihre Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen** , und geben Sie dann Folgendes ein:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  Melden Sie in Ihrer Windows PowerShell-Sitzung bei Exchange Online mit einem Konto an, das für den Remoteshellzugriff aktiviert ist. Standardmäßig sind alle Konten, die in Exchange Online erstellt werden, für den Remoteshellzugriff aktiviert. Diese Einstellung kann über den Befehl [Set-User &lt;Benutzer-ID&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) deaktiviert (und wieder aktiviert) werden.

    Um sich anzumelden, geben Sie Folgendes ein:

    ```
    $UserCredential = Get-Credential
    ```
    Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** Ihren Office 365-Benutzernamen und Ihr Kennwort ein.

3.  Stellen Sie eine Verbindung mit dem Exchange Online-Dienst her, indem Sie die folgenden beiden Befehle ausführen:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Geben Sie den Speicherort des Azure Information Protection-Mandantenschlüssels entsprechend dem Standort an, an dem der Mandant Ihrer Organisation erstellt wurde:

    Für Nordamerika:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Für Europa:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Für Asien:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Für Südamerika:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Für Office 365 Government (Government Community Cloud):

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Importieren Sie Konfigurationsdaten aus dem Azure Rights Management-Dienst in Exchange Online in Form der vertrauenswürdigen Veröffentlichungsdomäne (Trusted Publishing Domain, TPD). Dies umfasst den Azure Information Protection-Mandantenschlüssel und Azure Rights Management-Vorlagen:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    In diesem Befehl wird der Name **RMS Online** als Basisname für die vertrauenswürdige Veröffentlichungsdomäne (TPD) für Azure Rights Management in Exchange Online verwendet. Nach dem Importieren der vertrauenswürdigen Veröffentlichungsdomäne lautet der Name in Exchange Online **RMS Online - 1**.

6.  Aktivieren Sie die Azure Rights Management-Funktionalität, damit IRM-Features für Exchange Online zur Verfügung stehen:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    Nach der Ausführung dieses Befehls wird Rights Management für den Outlook-Client, Outlook Web App und Exchange Active Sync automatisch aktiviert.

7.  Testen Sie optional mit dem folgenden Befehl, ob diese Konfiguration erfolgreich ist:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Beispiel: **Test-IRMConfiguration -Sender adams@contoso.com**

    Dieser Befehl führt eine Reihe von Überprüfungen aus. Dazu zählen das Überprüfen der Verbindung mit dem Dienst sowie das Abrufen von Konfiguration-URIs, Lizenzen und Vorlagen. In der Windows PowerShell-Sitzung werden die Ergebnisse der einzelnen Überprüfungen angezeigt. Wenn alle diese Tests bestanden wurden, wird Folgendes eingeblendet: **GESAMTERGEBNIS: ERFOLG**

8.  Trennen Sie die PowerShell-Remotesitzung:

    ```
    Remove-PSSession $Session
    ```

Benutzer können ihre E-Mail-Nachrichten jetzt mithilfe des Azure Rights Management-Diensts schützen. Wählen Sie in Outlook Web App im erweiterten Menü (**...**) den Befehl **Berechtigungen festlegen** und dann **Nicht weiterleiten** oder eine der verfügbaren Vorlagen aus, um den Informationsschutz auf die E-Mail und sämtliche Anlagen anzuwenden. Da die Outlook Web App jedoch die Benutzeroberfläche für einen Tag zwischenspeichert, warten Sie diesen Zeitraum ab, bevor Sie versuchen, den Informationsschutz auf E-Mail-Nachrichten anzuwenden, nachdem Sie diese Konfigurationsbefehle ausgeführt haben. Ehe Benutzeroberfläche entsprechend der neuen Konfiguration aktualisiert wird, sehen Sie keine Optionen im Menü **Berechtigungen festlegen** .

> [!IMPORTANT]
> Wenn Sie neue [benutzerdefinierte Vorlagen](configure-custom-templates.md) für Azure Rights Management erstellen oder die Vorlagen aktualisieren, müssen Sie jedes Mal den folgenden Exchange Online-PowerShell-Befehl ausführen (führen Sie ggf. zunächst die Schritte 2 und 3 aus), um diese Änderungen mit Exchange Online zu synchronisieren: `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Als Exchange-Administrator können Sie jetzt Features konfigurieren, die den Informationsschutz automatisch anwenden, wie z. B. [Transportregeln](https://technet.microsoft.com/library/dd302432.aspx), [DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx)und [geschützte Voicemail](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).


### <a name="office-365-message-encryption"></a>Office 365-Nachrichtenverschlüsselung
Führen Sie dieselben im vorherigen Abschnitt beschriebenen Schritte aus. Wenn Sie nicht möchten, dass Vorlagen angezeigt werden, führen Sie vor Schritt 6 den folgenden Befehl aus, um zu verhindern, dass IRM-Vorlagen in Outlook Web App und im Outlook-Client verfügbar sind: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

Wenn Sie anschließend bereit sind, [Transportregeln](https://technet.microsoft.com/library/dd302432.aspx) für das automatische Ändern der Nachrichtensicherheit zu konfigurieren, wenn sich Empfänger außerhalb der Organisation befinden, wählen Sie die Option **Office 365-Nachrichtenverschlüsselung anwenden** aus.

Weitere Informationen zur Verschlüsselung von Nachrichten finden Sie unter [Verschlüsselung in Office 365](https://technet.microsoft.com/library/dn569286.aspx) in der Exchange-Bibliothek.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
