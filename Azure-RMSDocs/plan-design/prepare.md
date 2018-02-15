---
title: "Vorbereiten von Benutzern und Gruppen für Azure Information Protection"
description: "Überprüfen Sie, ob die Benutzer- und Gruppenkonten vorhanden sind, die Sie zum Klassifizieren, Bezeichnen und Schützen der Dokumente und E-Mails Ihrer Organisation benötigen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: de06bc202ff60e6850ba217fe7ded79c0753d925
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="preparing-users-and-groups-for-azure-information-protection"></a>Vorbereiten von Benutzern und Gruppen für Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Bevor Sie Azure Information Protection für Ihre Organisation bereitstellen, vergewissern Sie sich, dass Sie in Azure AD über Benutzer und Gruppenkonten für den Mandanten Ihrer Organisation verfügen.

Es gibt verschiedene Verfahren zum Erstellen dieser Konten für Benutzer und Gruppen:

- Sie erstellen die Benutzer im Office 365 Admin Center und die Gruppen im Exchange Online Admin Center.

- Sie erstellen die Benutzer und Gruppen im Azure-Portal.

- Sie erstellen die Benutzer und Gruppen mithilfe von Azure AD PowerShell- und Exchange Online-Cmdlets.

- Sie erstellen die Benutzer und Gruppen in Ihrer lokalen Active Directory-Instanz und synchronisieren sie mit Azure AD.

- Sie erstellen die Benutzer und Gruppen in einem anderen Verzeichnis und synchronisieren sie mit Azure AD.

Wenn Sie Benutzer und Gruppen mit den ersten drei Methoden aus dieser Liste erstellen, werden sie automatisch in Azure AD erstellt und können von Azure Information Protection direkt verwendet werden. Allerdings werden Benutzer und Gruppen in vielen Unternehmensnetzwerke in einem lokalen Verzeichnis erstellt und verwaltet. Diese Konten können von Azure Information Protection nicht direkt verwendet werden, sondern müssen erst mit Azure AD synchronisiert werden.

## <a name="how-users-and-groups-are-used-by-azure-information-protection"></a>Verwenden von Benutzern und Gruppen durch Azure Information Protection

Es gibt drei Szenarien für die Verwendung von Benutzern und Gruppen mit Azure Information Protection:

- **Zum Zuweisen von Bezeichnungen für Benutzer**, wenn Sie Bezeichnungen und Klassifizierungen verwenden. Diese Gruppen werden nur von Administratoren ausgewählt:

    - Die Azure Information Protection-Standardrichtlinie wird automatisch allen Benutzern in der Azure AD-Instanz Ihres Mandanten zugewiesen. Allerdings können Sie einzelnen Benutzern oder Gruppen mithilfe von bereichsbezogenen Richtlinien auch zusätzliche Bezeichnungen zuweisen.     

- **Zum Zuweisen von Nutzungsrechten und Zugriffssteuerungen**, wenn Sie Dokumente und E-Mails mithilfe des Azure Rights Management-Diensts schützen. Administratoren und Benutzer können diese Benutzer und Gruppen auswählen:

    - Nutzungsrechte bestimmen, ob ein Benutzer ein Dokument oder eine E-Mail öffnen kann und wie er das Dokument oder die E-Mail verwenden darf. Sie definieren beispielsweise, ob er das Dokument oder die E-Mail nur lesen oder lesen und drucken oder lesen und bearbeiten darf.

    - Zugriffssteuerungen umfassen ein Ablaufdatum und geben an, ob für den Zugriff eine Verbindung mit dem Internet erforderlich ist.

- **Zum Konfigurieren des Azure Rights Management-Diensts**, um bestimmte Szenarien zu unterstützen. Daher werden diese Gruppen nur von Administratoren ausgewählt. Beispiele umfassen die Konfiguration folgender Elemente:

    - Administratoren, damit bestimmte Dienste oder Personen verschlüsselte Inhalte öffnen können, wenn dies für eDiscovery oder die Wiederherstellung von Daten erforderlich ist

    - Delegierte Administration des Azure Rights Management-Diensts

    - Onboarding-Steuerelemente zur Unterstützung einer stufenweisen Bereitstellung

**Zum Zuweisen von Bezeichnungen für Benutzer** beim Konfigurieren der Azure Information Protection-Richtlinie, damit Bezeichnungen auf Dokumente und E-Mails angewendet werden können. Nur Administratoren können diese Benutzer und Gruppen auswählen:

- Die Azure Information Protection-Standardrichtlinie wird automatisch allen Benutzern in der Azure AD-Instanz Ihres Mandanten zugewiesen. Allerdings können Sie einzelnen Benutzern oder Gruppen mithilfe von bereichsbezogenen Richtlinien auch zusätzliche Bezeichnungen zuweisen.     

**Zum Zuweisen von Nutzungsrechten und Zugriffssteuerungen**, wenn Sie Dokumente und E-Mails mithilfe des Azure Rights Management-Diensts schützen. Administratoren und Benutzer können diese Benutzer und Gruppen auswählen:

- Nutzungsrechte bestimmen, ob ein Benutzer ein Dokument oder eine E-Mail öffnen kann und wie er das Dokument oder die E-Mail verwenden darf. Sie definieren beispielsweise, ob er das Dokument oder die E-Mail nur lesen oder lesen und drucken oder lesen und bearbeiten darf. 

- Zugriffssteuerungen umfassen ein Ablaufdatum und geben an, ob für den Zugriff eine Verbindung mit dem Internet erforderlich ist. 

**Zum Konfigurieren des Azure Rights Management-Diensts**, um bestimmte Szenarien zu unterstützen. Daher werden diese Gruppen nur von Administratoren ausgewählt. Beispiele umfassen die Konfiguration folgender Elemente:

- Administratoren, damit bestimmte Dienste oder Personen verschlüsselte Inhalte öffnen können, wenn dies für eDiscovery oder die Wiederherstellung von Daten erforderlich ist

- Delegierte Administration des Azure Rights Management-Diensts

- Onboarding-Steuerelemente zur Unterstützung einer stufenweisen Bereitstellung

## <a name="azure-information-protection-requirements-for-user-accounts"></a>Azure Information Protection-Anforderungen für Benutzerkonten

Zum Zuweisen von Bezeichnungen:

- Alle Benutzerkonten in Azure AD können zum Konfigurieren bereichsbezogener Richtlinien verwendet werden, die Benutzern zusätzliche Bezeichnungen zuweisen.

Zum Zuweisen von Nutzungsrechten und Zugriffssteuerungen sowie zum Konfigurieren des Azure Rights Management-Diensts:

- Für die Autorisierung von Benutzern werden in Azure AD zwei Attribute verwendet: **proxyAddresses** und **userPrincipalName**.

- Das Attribut **Azure AD proxyAddresses** speichert alle E-Mail-Adressen für ein Konto und kann auf unterschiedliche Weise aufgefüllt werden. Ein Benutzer in Office 365, der über ein Exchange Online-Postfach verfügt, erhält beispielsweise automatisch eine E-Mail-Adresse, die in diesem Attribut gespeichert ist. Wenn Sie einem Office 365-Benutzer eine alternative E-Mail-Adresse zuweisen, wird diese ebenfalls in diesem Attribut gespeichert. Das Attribut kann auch durch Synchronisierung mit den E-Mail-Adressen lokaler Konten aufgefüllt werden. 
    
    Azure Information Protection kann beliebige Werte im Attribut „Azure AD proxyAddresses“ verwenden, vorausgesetzt die Domäne wurde Ihrem Mandanten hinzugefügt („überprüfte Domäne“). Weitere Informationen zum Überprüfen von Domänen finden Sie in folgenden Artikeln:
    
    - Azure AD: [Schnellstart: Hinzufügen eines benutzerdefinierten Domänennamens zu Azure Active Directory](/active-directory/active-directory-add-domain)

    - Office 365: [Hinzufügen von Domäne und Benutzern zu Office 365](https://go.microsoft.com/fwlinkid/?linkid=847121)

- Das Attribut **Azure AD userPrincipalName** wird nur verwendet, wenn ein Konto in Ihrem Mandanten im Azure AD-Attribut „proxyAddresses“ keine Werte aufweist. Dies ist beispielsweise der Fall, wenn Sie einen Benutzer im Azure-Portal erstellen oder einen Benutzer für Office 365 erstellen, der kein Postfach besitzt.

### <a name="assigning-usage-rights-and-access-controls-to-external-users"></a>Zuweisen von Nutzungsrechten und Zugriffssteuerungen für externe Benutzer

Azure Information Protection verwendet die Attribute „Azure AD proxyAddresses“ und „Azure AD userPrincipalName“ nicht nur für Benutzer in Ihrem Mandanten, sondern auch in gleicher Weise zum Autorisieren von Benutzern aus einem anderen Mandanten.

Wenn eine E-Mail mit der Office 365-Nachrichtenverschlüsselung und deren neuen Funktionen an einen Benutzer gesendet wird, der kein Azure AD-Konto besitzt, wird dieser Benutzer zunächst authentifiziert, indem ein Verbund mit einem sozialen Netzwerk als Identitätsanbieter hergestellt oder eine Einmalkennung verwendet wird. Anschließend wird die in der geschützten E-Mail angegebene E-Mail-Adresse verwendet, um den Benutzer zu autorisieren.

## <a name="azure-information-protection-requirements-for-group-accounts"></a>Azure Information Protection-Anforderungen für Gruppenkonten

Zum Zuweisen von Bezeichnungen:

- Um bereichsbezogene Richtlinien zu konfigurieren, die Gruppenmitgliedern zusätzliche Bezeichnungen zuweisen, können Sie alle Arten von Gruppen in Azure AD verwenden, die über eine E-Mail-Adresse einer überprüften Domäne für den Mandanten des Benutzers verfügen. Eine Gruppe mit einer E-Mail-Adresse wird häufig als E-Mail-aktivierte Gruppe bezeichnet.
    
    Sie können beispielsweise eine E-Mail-aktivierte Sicherheitsgruppe, eine Verteilergruppe (statisch oder dynamisch) und eine Office 365-Gruppe verwenden. Sie können keine Sicherheitsgruppe (dynamisch oder statisch) verwenden, da dieser Gruppentyp keine E-Mail-Adresse besitzt.

Zum Zuweisen von Nutzungsrechten und Zugriffssteuerungen:

- Sie können alle Arten von Gruppen in Azure AD verwenden, die über eine E-Mail-Adresse einer überprüften Domäne für den Mandanten des Benutzers verfügen. Eine Gruppe mit einer E-Mail-Adresse wird häufig als E-Mail-aktivierte Gruppe bezeichnet. 

Zum Konfigurieren des Azure Rights Management-Diensts:

- Sie können alle Arten von Gruppen in Azure AD verwenden, die über eine E-Mail-Adresse einer überprüften Domäne für den Mandanten des Benutzers verfügen. Dabei gilt eine Ausnahme: Sie konfigurieren Onboarding-Steuerelemente für die Verwendung einer Gruppe, die in Azure AD eine Sicherheitsgruppe für Ihren Mandanten sein muss.

- Sie können alle Gruppen in Azure AD (mit oder ohne E-Mail-Adresse) aus einer überprüften Domäne in Ihrem Mandanten für die delegierte Administration des Azure Rights Management-Dienstes verwenden.

### <a name="assigning-usage-rights-and-access-controls-to-external-groups"></a>Zuweisen von Nutzungsrechten und Zugriffssteuerungen für externe Gruppen

Azure Information Protection verwendet das Attribut „Azure AD proxyAddresses“ nicht nur für Gruppen in Ihrem Mandanten, sondern auch in gleicher Weise zum Autorisieren von Gruppen aus einem anderen Mandanten.

## <a name="using-accounts-from-active-directory-on-premises-for-azure-information-protection"></a>Verwenden lokaler Konten aus Active Directory für Azure Information Protection

Wenn Sie über lokal verwaltete Konten verfügen, die Sie mit Azure Information Protection verwenden möchten, müssen Sie diese mit Azure AD synchronisieren. Zur einfacheren Bereitstellung empfehlen wir die Verwendung von [Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect). Sie können jedoch jede Verzeichnissynchronisierungsmethode verwenden, die das gleiche Ergebnis erzielt.

Wenn Sie Ihre Konten synchronisieren, brauchen Sie nicht alle Attribute zu synchronisieren. Eine Liste mit den Attributen, die synchronisiert werden müssen, finden Sie im Abschnitt zu [Azure RMS](/azure/active-directory/connect/active-directory-aadconnectsync-attributes-synchronized#azure-rms) in der Azure Active Directory-Dokumentation.

Anhand der Liste der Attribute für Azure Rights Management erkennen Sie, dass für Benutzer die lokalen AD-Attribute **mail**, **proxyAddresses** und **userPrincipalName** für die Synchronisierung erforderlich sind. Werte für **mail** und **proxyAddresses** werden mit dem Attribut „Azure AD proxyAddresses“ synchronisiert. Weitere Informationen finden Sie unter [How the proxyAddresses attribute is populated in Azure AD](https://support.microsoft.com/help/3190357/how-the-proxyaddresses-attribute-is-populated-in-azure-ad) (Auffüllen des Attributs „proxyAddresses“ in Azure AD).

## <a name="confirming-your-users-and-groups-are-prepared-for-azure-information-protection"></a>Bestätigen, dass Ihre Benutzer und Gruppen für Azure Information Protection vorbereitet sind

Sie können mithilfe von Azure AD PowerShell überprüfen, ob Benutzer und Gruppen mit Azure Information Protection verwendet werden können. Mit PowerShell können Sie auch die Werte bestätigen, die für deren Autorisierung verwendet werden können. 

Stellen Sie beispielsweise mithilfe des V1-PowerShell-Moduls für Azure Active Directory ([MSOnline](/powershell/module/msonline/?view=azureadps-1.0)) in einer PowerShell-Sitzung zunächst eine Verbindung mit dem Dienst her, und geben Sie Ihre globalen Administratoranmeldeinformationen an:

    Connect-MsolService


Hinweis: Wenn dieser Befehl nicht funktioniert, können Sie `Install-Module MSOnline` ausführen, um das MSOnline-Modul zu installieren.

Konfigurieren Sie anschließend die PowerShell-Sitzung so, dass die Werte nicht abgeschnitten werden:

    $Formatenumerationlimit =-1

### <a name="confirm-user-accounts-are-ready-for-azure-information-protection"></a>Bestätigen, dass Benutzerkonten für Azure Information Protection bereit sind

Um die Benutzerkonten zu bestätigen, führen Sie den folgenden Befehl aus:

    Get-Msoluser | select DisplayName, UserPrincipalName, ProxyAddresses

Ihre erste Überprüfung besteht jetzt darin, sicherzustellen, dass die Benutzer, die Sie mit Azure Information Protection verwenden möchten, angezeigt werden.

Überprüfen Sie anschließend, ob die Spalte **ProxyAddresses** aufgefüllt wurde. Wenn dies der Fall ist, können die E-Mail-Werte in dieser Spalte zur Autorisierung des Benutzers für Azure Information Protection genutzt werden.

Wenn die Spalte **ProxyAddresses** nicht aufgefüllt wurde, wird der Wert von **UserPrincipalName** verwendet, um den Benutzer für den Azure Rights Management-Dienst zu autorisieren.

Zum Beispiel:

|Anzeigename|UserPrincipalName|ProxyAddresses
|-------------------|-----------------|--------------------|
|Jagannath Reddy |jagannathreddy@contoso.com|{}|
|Ankur Roy|ankurroy@contoso.com|{SMTP:ankur.roy@contoso.com, smtp: ankur.roy@onmicrosoft.contoso.com}|

In diesem Beispiel:

- Das Benutzerkonto für Jagannath Reddy wird mit **jagannathreddy@contoso.com** autorisiert.

-  Das Benutzerkonto für Ankur Roy kann mit **ankur.roy@contoso.com** und **ankur.roy@onmicrosoft.contoso.com**, aber nicht mit **ankurroy@contoso.com** autorisiert werden.

In den meisten Fällen entspricht der Wert für „UserPrincipalName“ einem der Werte im Feld „ProxyAddresses“. Dies ist die empfohlene Konfiguration, aber wenn Sie Ihren UPN nicht entsprechend der E-Mail-Adresse ändern können, müssen Sie die folgenden Schritte ausführen:

1. Wenn der Domänenname im UPN-Wert eine überprüfte Domäne für Ihren Azure AD-Mandanten ist, fügen Sie den UPN-Wert als weitere E-Mail-Adresse in Azure AD hinzu, sodass der UPN-Wert nun verwendet werden kann, um das Benutzerkonto für Azure Information Protection zu autorisieren.

    Ist der Domänenname im UPN-Wert keine überprüfte Domäne für Ihren Mandanten, kann er nicht mit Azure Information Protection verwendet werden. Allerdings kann der Benutzer weiterhin als Mitglied einer Gruppe autorisiert werden, wenn die E-Mail-Adresse der Gruppe den Namen einer überprüften Domäne verwendet.

2. Wenn der UPN nicht geroutet werden kann (z.B. **ankurroy@contoso.local**), konfigurieren Sie alternative Anmelde-IDs für Benutzer, und erläutern Sie den Benutzern, wie sie sich mit dieser alternativen Anmelde-ID bei Office anmelden. Sie müssen außerdem einen Registrierungsschlüssel für Office festlegen.

    Weitere Informationen finden Sie unter [Configuring Alternate Login ID](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) (Konfigurieren einer alternativen Anmelde-ID) und [Office applications periodically prompt for credentials to SharePoint Online, OneDrive, and Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online) (Office-Anwendungen fordern regelmäßig Anmeldeinformationen für SharePoint Online, OneDrive und Lync Online an.).

> [!TIP]
> Mit dem Cmdlet „Export-Csv“ können Sie die Ergebnisse zur einfacheren Verwaltung (etwa zum Durchsuchen und zur Massenbearbeitung für den Import) in eine Kalkulationstabelle exportieren.
>
> Beispiel: `Get-MsolGroup | select DisplayName, ProxyAddresses | Export-Csv -Path UserAccounts.csv`

### <a name="confirm-group-accounts-are-ready-for-azure-information-protection"></a>Bestätigen, dass Gruppenkonten für Azure Information Protection bereit sind

Verwenden Sie den folgenden Befehl, um Gruppenkonten zu bestätigen:

    Get-MsolGroup | select DisplayName, ProxyAddresses

Stellen Sie sicher, dass die Gruppen, die Sie mit Azure Information Protection verwenden möchten, angezeigt werden. Die Gruppenmitglieder der angezeigten Gruppen können mithilfe der E-Mail-Adressen in der Spalte **ProxyAddresses** für den Azure Rights Management-Dienst autorisiert werden.

Überprüfen Sie anschließend, ob die Gruppen die gewünschten Benutzer (oder andere Gruppen) enthalten, die Sie für Azure Information Protection verwenden möchten. Sie können dazu PowerShell (z.B. [Get-MsolGroupMember](/powershell/module/msonline/Get-MsolGroupMember?view=azureadps-1.0)) oder das Verwaltungsportal verwenden.

In den beiden Konfigurationsszenarien des Azure Rights Management-Diensts, in denen Sicherheitsgruppen verwendet werden, können Sie mit dem folgenden PowerShell-Befehl die Objekt-ID und den Anzeigenamen suchen, die zum Identifizieren dieser Gruppen verwendet werden können. Sie können diese Gruppen auch im Azure-Portal suchen und die Werte für Objekt-ID und Anzeigenamen kopieren:

    Get-MsolGroup | where {$_.GroupType -eq "Security"}

## <a name="considerations-for-azure-information-protection-if-email-addresses-change"></a>Überlegungen für Azure Information Protection bei E-Mail-Adressänderungen

Wenn Sie die E-Mail-Adresse eines Benutzers oder einer Gruppe ändern, wird empfohlen, die alte E-Mail-Adresse als zweite E-Mail-Adresse (auch als Proxyadresse, Alias oder alternative E-Mail-Adresse bezeichnet) für den Benutzer oder die Gruppe hinzuzufügen. Dadurch wird die alte E-Mail-Adresse zum Attribut „Azure AD proxyAddresses“ hinzugefügt. Durch dieses Vorgehen wird die Geschäftskontinuität für alle Nutzungsrechte oder anderen Konfigurationen gewährleistet, die gespeichert wurden, als noch die alte E-Mail-Adresse verwendet wurde. 

Ist dies nicht möglich, riskiert der Benutzer oder die Gruppe mit der neuen E-Mail-Adresse, dass ihm bzw. ihr der Zugriff auf Dokumente und E-Mails verweigert wird, die zuvor mit der alten E-Mail-Adresse geschützt waren. In diesem Fall müssen Sie die Schutzkonfiguration wiederholen, um die neue E-Mail-Adresse zu speichern. Wenn dem Benutzer oder der Gruppe beispielsweise Nutzungsrechte in Vorlagen oder Bezeichnungen erteilt wurden, bearbeiten Sie diese Vorlagen oder Bezeichnungen, und geben Sie die neue E-Mail-Adresse mit den gleichen Nutzungsrechten an, die Sie der alten E-Mail-Adresse erteilt hatten.

Beachten Sie, dass Gruppen nur selten ihre E-Mail-Adresse ändern, und wenn Sie Nutzungsrechte einer Gruppe und nicht einzelnen Benutzer zuweisen, ist es unerheblich, ob sich E-Mail-Adressen von Benutzern ändern. Die Nutzungsrechte werden in diesem Szenario der Gruppen-E-Mail-Adresse und nicht den einzelnen Benutzer-E-Mail-Adressen zugewiesen. Dies ist die wahrscheinlichste (und empfohlene) Methode, wie ein Administrator Nutzungsrechte zum Schutz von Dokumenten und E-Mails konfiguriert. Allerdings ist es nicht unüblich, dass Benutzer einzelnen Benutzern benutzerdefinierte Berechtigungen zuweisen. Da Sie nicht immer wissen, ob der Zugriff einem Benutzerkonto oder einer Gruppe gewährt wurde, ist es am sichersten, die alte E-Mail-Adresse immer als zweite E-Mail-Adresse hinzuzufügen.

## <a name="group-membership-caching-by-azure-information-protection"></a>Zwischenspeichern von Gruppenmitgliedschaften durch Azure Rights Management

Aus Leistungsgründen wird die Gruppenmitgliedschaft vom Azure Rights Management-Dienst zwischengespeichert. Das bedeutet, dass es bis zu drei Stunden dauern kann, bis Änderungen an der Gruppenmitgliedschaft in Azure AD wirksam sind, wenn diese Gruppen von Azure Rights Management verwendet werden. Änderungen dieses Zeitraums sind vorbehalten. 

Berücksichtigen Sie diese Verzögerung bei Änderungen oder Tests, wenn Sie Gruppen verwenden, um Nutzungsrechte zuzuweisen oder den Azure Rights Management-Dienst zu konfigurieren, oder wenn Sie bereichsbezogene Richtlinien konfigurieren.


## <a name="next-steps"></a>Nächste Schritte

Wenn Sie sich vergewissert haben, dass Ihre Benutzer und Gruppen mit Azure Information Protection verwendet werden können und bereit sind, mit dem Schutz von Dokumenten und E-Mails zu beginnen, aktivieren Sie den Rights Management-Dienst als Datenschutzdienst. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
