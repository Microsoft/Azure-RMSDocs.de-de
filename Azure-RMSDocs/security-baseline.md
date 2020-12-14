---
title: Azure-Sicherheitsbaseline für Azure Information Protection
description: Die Azure Information Protection-Sicherheitsbasis Linie enthält Anleitungen und Ressourcen zum Implementieren der Sicherheitsempfehlungen, die im Azure Security Benchmark (Azure Security Benchmark) angegeben sind.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/18/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: 8cdeb7ec7bd30d6b15b832eeb080317d5b26ec08
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384620"
---
# <a name="azure-security-baseline-for-azure-information-protection"></a>Azure-Sicherheitsbaseline für Azure Information Protection

Diese Sicherheitsbasis Linie wendet eine Anleitung von der [Azure Security Benchmark-Version 2,0](https://docs.microsoft.com/azure/security/benchmarks/overview) auf Azure Information Protection an. Der Azure-Sicherheitsvergleichstest enthält Empfehlungen zum Schutz Ihrer Cloudlösungen in Azure. Der Inhalt ist nach den vom Azure Security Benchmark definierten **Sicherheitskontrollen** und den entsprechenden Richtlinien für Azure Information Protection gruppiert. Steuer **Elemente** , die nicht auf Azure Information Protection anwendbar sind, wurden ausgeschlossen.

Informationen dazu, wie Azure Information Protection dem Azure Security Benchmark vollständig zugeordnet ist, finden Sie unter [vollständige Azure Information Protection Sicherheitsbaseline](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines)-Zuordnungs Datei.

## <a name="network-security"></a>Netzwerksicherheit

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Netzwerksicherheit](/azure/security/benchmarks/security-controls-v2-network-security).*

### <a name="ns-6-simplify-network-security-rules"></a>NS-6: Vereinfachen von Netzwerksicherheitsregeln

**Leitfaden**: Verwenden von Virtual Network-Dienst Tags zum Definieren von Netzwerk Zugriffs Steuerungen in Netzwerk Sicherheitsgruppen oder der Azure-Firewall, die für Ihre Azure Information Protection-Ressourcen konfiguriert ist. 

Verwenden Sie beim Erstellen von Sicherheitsregeln Dienst Tags anstelle spezifischer IP-Adressen. Geben Sie den diensttag Namen (z. b. {azureinformationprotection}) im entsprechenden Quell-oder Zielfeld einer Regel an, um den Datenverkehr für den entsprechenden Dienst zuzulassen oder zu verweigern.

Microsoft verwaltet die Adresspräfixe, die mit dem Diensttag abgedeckt werden, und aktualisiert das Diensttag automatisch, wenn sich die Adressen ändern.

- [Grundlegendes zu Diensttags und Verwenden von Diensttags](https://docs.microsoft.com/azure/virtual-network/service-tags-overview)

- [Azure Information Protection diensttag](https://docs.microsoft.com/azure/information-protection/requirements#service-tags)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

## <a name="identity-management"></a>Identitätsverwaltung

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Identitätsverwaltung](/azure/security/benchmarks/security-controls-v2-identity-management).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Standardisieren von Azure Active Directory als zentrales Identitäts- und Authentifizierungssystem

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. Stellen Sie eine hohe Priorität dar, um Azure AD in der cloudsicherheitsübung Ihrer Organisation zu schützen. 

Überprüfen Sie das sichere Ergebnis der Azure AD Identität, um Sie bei der Beurteilung Ihres Identitäts Sicherheitsstatus in Bezug auf die Empfehlungen von Microsoft zu unterstützen. Verwenden Sie die Bewertung, um zu beurteilen, wie gut Ihre Konfiguration den Empfehlungen zu bewährten Methoden entspricht, und um Ihren Sicherheitsstatus zu verbessern.

Konfigurieren Sie Azure AD als Standardmethode für die Identitäts- und Zugriffsverwaltung Ihrer Organisation in folgenden Ressourcen:

- Microsoft Cloud Ressourcen, wie z. b. die Azure-Portal, Azure Storage, Azure Virtual Machines (Linux und Windows), Azure Key Vault, Platform-as-a-Service (PAS) und Software-as-a-Service (SaaS)-Anwendungen

- Die Ressourcen Ihrer Organisation, z. B. Anwendungen in Azure oder Ihre Unternehmensnetzwerkressourcen

Azure Ad unterstützt externe Identitäten, damit sich Benutzer ohne Microsoft-Konto bei Ihren Anwendungen und Ressourcen mit ihren nicht-Microsoft-Konten anmelden können.

- [Mandanten in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Erstellen und Konfigurieren einer Azure AD-Instanz](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [Verwenden externer Identitätsanbieter für eine Anwendung](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers)

- [Was ist der Identity Secure Score in Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2: Sicheres und automatisches Verwalten von Anwendungsidentitäten

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Identitäts-und Zugriffs Verwaltungsdienst von Azure handelt. Azure Rights Management Service verwendet eine Azure AD Anwendungs Identität beim Zugriff auf die Schlüssel der Kunden, die mit Azure Key Vault for Bring your own Key-Szenarios (Byok) gespeichert sind. Das autorialisieren von Azure Rights Management Service für den Zugriff auf Ihre Schlüssel erfolgt durch das Konfigurieren von Azure Key Vault Zugriffsrichtlinien. Dies kann entweder mithilfe der Azure-Portal oder mithilfe von PowerShell erfolgen.

- [Autorialisieren des Azure-Rights Management Dienstanbieter für Byok](https://docs.microsoft.com/azure/information-protection/byok-price-restrictions#authorizing-the-azure-rights-management-service-to-use-your-key)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: Verwenden von Azure AD Single Sign-on (SSO) für den Anwendungszugriff

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. 

Azure Information Protection Azure AD verwendet, um die Identitäts-und Zugriffs Verwaltung für Azure-Ressourcen, cloudanwendungen und lokale Anwendungen bereitzustellen. Dies umfasst sowohl Unternehmensidentitäten wie Mitarbeiter als auch externe Identitäten wie Partner, Anbieter und Zulieferer. Auf diese Weise kann der Zugriff auf die Daten und Ressourcen Ihrer Organisation lokal und in der Cloud über das Feature des einmaligen Anmeldens (Single Sign-On, SSO) verwaltet und geschützt werden. Verbinden Sie all Ihre Benutzer, Anwendungen und Geräte mit Azure AD, um einen nahtlosen, sicheren Zugriff sowie mehr Transparenz und Kontrolle zu ermöglichen.

- [Anmelden bei Azure Information Protection mit Azure Active Directory](https://docs.microsoft.com/azure/information-protection/requirements)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: Verwenden stärkerer Authentifizierungssteuerungen für den gesamten Azure Active Directory-basierten Zugriff

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, das eine sichere Authentifizierung über Multi-Factor Authentication unterstützt. Um die Authentifizierung und Autorisierung für Azure Information Protection zu unterstützen, müssen Sie über eine Azure AD verfügen. Wenn Sie Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, müssen Sie auch die Verzeichnisintegration konfigurieren.

- Einmaliges Anmelden wird für Azure Information Protection unterstützt, sodass Benutzer nicht wiederholt zur Eingabe Ihrer Anmelde Informationen aufgefordert werden. Wenn Sie die Lösung eines anderen Anbieters für den Verbund verwenden, fragen Sie beim Anbieter nach, wie die Lösung für Azure AD konfiguriert werden muss. WS-Trust ist eine häufige Anforderung für diese Lösungen zur Unterstützung des einmaligen Anmeldens.

- Die mehrstufige Authentifizierung wird mit Azure Information Protection unterstützt, wenn Sie über die erforderliche Client Software verfügen und die Infrastruktur zur Unterstützung der Multi-Factor Authentication ordnungsgemäß konfiguriert haben.

Weitere Informationen finden Sie in den folgenden Referenzen:

- [Azure Information Protection Authentifizierung über Azure Active Directory](https://docs.microsoft.com/azure/information-protection/requirements)

**Azure Security Center-Überwachung**: Ja

**Verantwortlichkeit**: Kunde

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5: Überwachen und Warnen bei Kontoanomalien

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. 

Weitere Anleitungen zu Azure AD:

- Anmeldung: der Anmelde Bericht enthält Informationen zur Verwendung verwalteter Anwendungen und Benutzer Anmelde Aktivitäten.
- Überwachungsprotokolle: Ermöglichen die Nachverfolgung sämtlicher Änderungen, die von verschiedenen Features in Azure AD vorgenommen wurden. Beispiele für Überwachungs Protokolle sind Änderungen, die an Ressourcen innerhalb Azure AD vorgenommen werden, z. b. das Hinzufügen oder Entfernen von Benutzern, apps, Gruppen, Rollen und Richtlinien.
- Riskante Anmeldungen: Eine riskante Anmeldung ist ein Hinweis auf einen Anmeldeversuch einer Person, die nicht der rechtmäßige Besitzer eines Benutzerkontos ist.
- Benutzer mit Risikomarkierung: Ein Benutzer mit Risikomarkierung ist ein Indikator für ein ggf. kompromittiertes Benutzerkonto.
Diese Datenquellen können mit Azure Monitor, Azure Sentinel oder SIEM-Systemen von Drittanbietern integriert werden.

Azure Security Center können auch Warnungen für bestimmte verdächtige Aktivitäten, z. b. eine übermäßige Anzahl fehlgeschlagener Authentifizierungs Versuche, oder für veraltete Konten im Abonnement angeben.

Azure Advanced Threat Protection (ATP) ist eine Sicherheitslösung, die Active Directory-Signale nutzen kann, um komplexe Bedrohungen, potenziell gefährdete Identitäten und schädliche Aktionen von Insidern zu identifizieren, zu erkennen und zu untersuchen.

- [Berichte zu Überwachungsaktivitäten in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-audit-logs) 

- [Anzeigen riskanter Azure AD-Anmeldungen](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-risky-sign-ins) 

- [Identifizieren von Azure AD-Benutzern, die aufgrund riskanter Aktivitäten gekennzeichnet wurden](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-user-at-risk) 

- [Überwachen der identitäts- und zugriffsbezogenen Aktivitäten von Benutzern in Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-identity-access) 

- [Warnungen im Threat Intelligence-Schutzmodul von Azure Security Center](https://docs.microsoft.com//azure/security-center/alerts-reference) 

- [Integrieren von Azure-Aktivitätsprotokollen in Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: Einschränken des Zugriffs auf Azure-Ressourcen basierend auf Bedingungen

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. Konfigurieren Sie in Azure AD den bedingten Zugriff für Azure Information Protection. Administratoren können auf der Grundlage der standardmäßigen bedingten Zugriffs Steuerung den Benutzern in Ihrem Mandanten den Zugriff auf von Azure Information Protection geschützte Dokumente blockieren oder gewähren.

Die mehrstufige Authentifizierung ist eine der am häufigsten angeforderten Bedingungen, während die Geräte Konformität mit konfigurierten InTune-Richtlinien eine andere ist. Sie können Bedingungen anfordern, damit Mobile Geräte die Anforderungen Ihres Unternehmens-Kennworts erfüllen, eine Mindestversion des Betriebssystems aufweisen und verbundene Computer in eine Domäne aufgenommen werden.

- [Richtlinien für bedingten Zugriff für Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

## <a name="privileged-access"></a>Privilegierter Zugriff

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Privilegierter Zugriff](/azure/security/benchmarks/security-controls-v2-privileged-access).*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1: Schützen und Einschränken stark privilegierter Benutzer

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. 

Azure Information Protection enthält eine Rolle auf Administratorebene in Azure AD. Benutzer, die der Administrator Rolle zugewiesen sind, verfügen über vollständige Berechtigungen für den Azure Information Protection-Dienst. Die Administrator Rolle kann verwendet werden, um Bezeichnungen für die Azure Information Protection-Richtlinie zu konfigurieren, Schutz Vorlagen zu verwalten und den Schutz zu aktivieren. Allerdings gewährt die Administrator Rolle keine Berechtigungen in Identity Protection Center, Privileged Identity Management, Monitor Microsoft 365 Service Health oder Office 365 Security &amp; Compliance Center.

Schränken Sie die Anzahl der Konten oder Rollen mit hohen Berechtigungen ein, und schützen Sie diese Konten auf höherer Ebene, da Benutzer mit dieser Berechtigung jede Ressource in ihrer Azure-Umgebung direkt oder indirekt lesen und ändern können. Aktivieren Sie den Just-in-time (JIT) privilegierten Zugriff auf Azure-Ressourcen und Azure AD mithilfe Privileged Identity Management (PIM). Der Just-in-Time-Zugriff gewährt temporäre Berechtigungen, um privilegierte Aufgaben nur dann auszuführen, wenn Sie von Benutzern benötigt werden. PIM kann auch Sicherheitswarnungen erzeugen, wenn es in Ihrer Azure AD-Organisation verdächtige oder unsichere Aktivitäten gibt.

- [Azure Information Protection Administrator Rolle](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#azure-information-protection-administrator)

- [Administratorrollenberechtigungen in Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)

- [Verwenden von Sicherheitswarnungen von Azure Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-configure-security-alerts) 

- [Schützen des privilegierten Zugriffs für hybride und Cloudbereitstellungen in Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: Einschränken des administrativen Zugriffs auf unternehmenskritische Systeme

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. 

Azure Information Protection enthält eine Rolle auf Administratorebene in Azure AD. Benutzer, die der Administrator Rolle zugewiesen sind, verfügen über vollständige Berechtigungen für den Azure Information Protection-Dienst. Die Administrator Rolle ermöglicht das Konfigurieren von Bezeichnungen für die Azure Information Protection Richtlinie, das Verwalten von Schutz Vorlagen und das Aktivieren des Schutzes. Die Administrator Rolle gewährt keine Berechtigungen in Identity Protection Center, Privileged Identity Management, Monitor Microsoft 365 Service Health oder Office 365 Security &amp; Compliance Center.

- [Azure Information Protection Administrator Rolle](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#azure-information-protection-administrator)

- [Aktionen Azure Information Protection Administrator durchführen kann](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#azure-information-protection-administrator-permissions)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3: Regelmäßiges Überprüfen und Abstimmen des Benutzerzugriffs

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt.

Verwenden Sie Azure AD, um Ressourcen zu verwalten, Benutzerkonten zu überprüfen und auf Zuweisungen regelmäßig zuzugreifen, um sicherzustellen, dass die Konten und deren Zugriff gültig sind. Führen Sie Azure AD Zugriffs Überprüfungen aus, um Gruppenmitgliedschaften, den Zugriff auf Unternehmensanwendungen und Rollenzuweisungen zu überprüfen. Ermitteln veralteter Konten mit Azure AD-Berichterstattung. Die Privileged Identity Management Features von Azure AD können zum Erstellen eines Zugriffs Überprüfungs Berichts Workflows verwendet werden, um den Überprüfungsprozess zu vereinfachen.

Darüber hinaus kann Azure Privileged Identity Management auch so konfiguriert werden, dass eine Warnung gesendet wird, wenn übermäßig viele Administratorkonten erstellt werden, und veraltete oder falsch konfigurierte Administratorkonten ermittelt werden. Beachten Sie, dass einige Azure-Dienste lokale Benutzer und Rollen unterstützen, die nicht über Azure AD verwaltet werden. Kunden müssen diese Benutzer separat verwalten.

- [Azure Information Protection Administrator Rolle](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#azure-information-protection-administrator)

- [Aktionen Azure Information Protection Administrator durchführen kann](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#azure-information-protection-administrator-permissions)

- [Erstellen einer Zugriffsüberprüfung für Azure-Ressourcenrollen in Privileged Identity Management (PIM)](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review) 

- [Was sind Azure AD-Zugriffsüberprüfungen?](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overvie)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Einrichten des Notfallzugriffs in Azure AD

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, um die zugehörigen Ressourcen zu verwalten. Um zu verhindern, dass Sie versehentlich aus Ihrer Azure AD-Organisation ausgesperrt werden, richten Sie ein Konto für den Notfallzugriff ein, für den Fall, dass normale Verwaltungskonten nicht verwendet werden können. Konten für den Notfallzugriff verfügen normalerweise über umfangreiche Berechtigungen und sollten keinen Einzelpersonen zugewiesen werden. Konten für den Notfallzugriff sind auf Notfallsituationen oder Szenarien beschränkt, in denen normale Administratorkonten nicht verwendet werden können.

Sie sollten sicherstellen, dass die Anmeldeinformationen (z. B. Kennwort, Zertifikat oder Smartcard) für Konten für den Notfallzugriff sicher aufbewahrt werden und nur den Personen bekannt sind, die für deren Verwendung im Notfall autorisiert sind.

- [Verwalten von Konten für den Notfallzugriff in Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pa-5-automate-entitlement-management"></a>PA-5: Automatisieren der Berechtigungsverwaltung 

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD), den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure integriert.

Azure Ad bietet Berechtigungs Verwaltungsfunktionen zum Automatisieren von Zugriffs Anforderungs Workflows, einschließlich Zugriffs Zuweisungen, Überprüfungen und Ablauf. Die duale oder die mehrstufige Genehmigung wird ebenfalls unterstützt.

- [Was sind Azure AD-Zugriffsüberprüfungen?](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview) 

- [Was ist die Azure AD-Berechtigungsverwaltung?](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6: Verwenden von Privileged Access Workstations

**Leitfaden**: Azure Information Protection können über PowerShell von einer Kunden Arbeitsstation aus verwaltet werden. 

Gesicherte, isolierte Arbeitsstationen sind für die Sicherheit sensibler Rollen (z. b. Administratoren, Entwickler und kritische Dienst Operatoren) äußerst wichtig. 

Verwenden Sie stark gesicherte Benutzerworkstations und/oder Azure Bastion für administrative Aufgaben. Verwenden Sie Azure Active Directory, Microsoft Defender Advanced Threat Protection (ATP) und/oder Microsoft Intune, um eine sichere und verwaltete Benutzerworkstation für administrative Aufgaben einzurichten. Die gesicherten Workstations können zentral verwaltet werden, um eine gesicherte Konfiguration einschließlich starker Authentifizierung, Software- und Hardwarebaselines sowie eingeschränktem logischen und Netzwerkzugang durchzusetzen.

- [Leitfaden zur Verwendung von PowerShell für Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/client-admin-guide-powershell)

- [Informationen zu sicheren, von Azure verwalteten Arbeitsstationen](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-managed-workstation) 

- [Bereitstellen einer sicheren, von Azure verwalteten Arbeitsstation](https://docs.microsoft.com/azure/active-directory/devices/howto-azure-managed-workstation)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pa-7-follow-just-enough-administration-least-privilege-principle"></a>PA-7: Befolgen Sie die Prinzipien der Just Enough Administration (Prinzip der geringsten Rechte) 

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. 

Azure Information Protection enthält eine Rolle auf Administratorebene in Azure AD. Benutzer, die der Administrator Rolle zugewiesen sind, verfügen über vollständige Berechtigungen für den Azure Information Protection-Dienst. Die Administrator Rolle kann verwendet werden, um Bezeichnungen für die Azure Information Protection-Richtlinie zu konfigurieren, Schutz Vorlagen zu verwalten und den Schutz zu aktivieren. Allerdings gewährt die Administrator Rolle keine Berechtigungen in Identity Protection Center, Privileged Identity Management, Monitor Microsoft 365 Service Health oder Office 365 Security &amp; Compliance Center.

Schränken Sie die Anzahl der Konten oder Rollen mit hohen Berechtigungen ein, und schützen Sie diese Konten auf höherer Ebene, da Benutzer mit dieser Berechtigung jede Ressource in ihrer Azure-Umgebung direkt oder indirekt lesen und ändern können. Aktivieren Sie den Just-in-time (JIT) privilegierten Zugriff auf Azure-Ressourcen und Azure AD mithilfe Privileged Identity Management (PIM). Der Just-in-Time-Zugriff gewährt temporäre Berechtigungen, um privilegierte Aufgaben nur dann auszuführen, wenn Sie von Benutzern benötigt werden. PIM kann auch Sicherheitswarnungen erzeugen, wenn es in Ihrer Azure AD-Organisation verdächtige oder unsichere Aktivitäten gibt.

- [In Berechtigungsstufen enthaltene Rechte für Azure Information Protection](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels)

- [Rights Management Aussteller und Rights Management Besitzer](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner)

- [Azure Information Protection Administrator Rolle](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#azure-information-protection-administrator)

- [Administratorrollenberechtigungen in Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)

- [Verwenden von Sicherheitswarnungen von Azure Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-configure-security-alerts) 

- [Schützen des privilegierten Zugriffs für hybride und Cloudbereitstellungen in Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pa-8-choose-approval-process-for-microsoft-support"></a>PA-8: Auswählen des Genehmigungsprozesses für Microsoft-Support  

**Leitfaden**: Azure Information Protection unterstützt Azure Kunden-Lockbox, um Kunden die Möglichkeit zu bieten, Datenzugriffs Anforderungen zu prüfen, zu genehmigen und abzulehnen sowie Anforderungen zu überprüfen. 

- [Übersicht über Lockbox](https://docs.microsoft.com/azure/security/fundamentals/customer-lockbox-overview)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

## <a name="data-protection"></a>Datenschutz

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Schutz von Daten](/azure/security/benchmarks/security-controls-v2-data-protection).*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1: Ermitteln, Klassifizieren und Bezeichnen von vertraulichen Daten

**Leitfaden**: Azure Information Protection bietet die Möglichkeit, vertrauliche Informationen zu ermitteln, zu klassifizieren und zu bezeichnen. 

Azure Information Protection ist eine cloudbasierte Lösung, mit der Organisationen Dokumente und e-Mails durch Anwenden von Bezeichnungen klassifizieren und schützen können. Bezeichnungen können automatisch durch Administratoren, die Regeln und Bedingungen definieren, manuell durch Benutzer oder durch eine Kombination von beiden Optionen angewendet werden, bei der Administratoren die Empfehlungen definieren, die Benutzern angezeigt werden.

- [Übersicht über Azure Information Protection](https://docs.microsoft.com/azure/information-protection/)

- [Leitfaden zum Einrichten des Unified-Bezeichnungs Clients](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-user-guide)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Shared

### <a name="dp-2-protect-sensitive-data"></a>DP-2: Schützen von vertraulichen Daten

**Leitfaden**: Azure Information Protection bietet Datenschutz, indem es die Möglichkeit bietet, vertrauliche Informationen zu bezeichnen und durch Verschlüsselung den Schutz für diese Daten zu gewährleisten. Der Schutz wird vom Azure Rights Management-Dienst bereitgestellt.

- [Azure Rights Management](https://docs.microsoft.com/azure/information-protection/what-is-azure-rms)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Shared

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3: Überwachung auf nicht autorisierte Übertragung vertraulicher Daten

**Leitfaden**: Azure Information Protection bietet die Möglichkeit, die nicht autorisierte Übertragung vertraulicher Daten durch die Funktion zum Nachverfolgen und widerrufen zu überwachen. Nachverfolgen und widerrufen ermöglicht es dem Kunden zu verfolgen, wie Benutzer von Ihnen gesendete Dokumente verwenden und den Zugriff widerrufen, wenn Sie nicht mehr in der Lage sein sollen, Sie zu lesen. 

- [Leitfaden zum Nachverfolgen und widerrufen](https://docs.microsoft.com/azure/information-protection/rms-client/client-track-revoke)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Shared

## <a name="asset-management"></a>Ressourcenverwaltung

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Ressourcenverwaltung](/azure/security/benchmarks/security-controls-v2-asset-management).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: Sicherstellen, dass das Sicherheitsteam Risiken für Ressourcen einsehen kann

**Leitfaden**: Stellen Sie sicher, dass Sicherheitsteams die Berechtigungen „Sicherheitsleseberechtigter“ in Ihrem Azure-Mandanten und Ihren Abonnements erhalten, damit sie mit Azure Security Center Sicherheitsrisiken überwachen können. 

Abhängig davon, wie die Verantwortungsbereiche des Sicherheitsteams strukturiert sind, kann die Überwachung auf Sicherheitsrisiken unter die Verantwortung eines zentralen Sicherheitsteams oder eines lokalen Teams fallen. Aus diesem Grund müssen Sicherheitserkenntnisse und -risiken immer innerhalb einer Organisation zentral aggregiert werden. 

Die Berechtigungen der Rolle „Sicherheitsleseberechtigter“ können weit gefasst auf einen gesamten Mandanten (Stammverwaltungsgruppe) angewandt oder auf Verwaltungsgruppen oder bestimmte Abonnements beschränkt werden. 

Hinweis: Möglicherweise sind zusätzliche Berechtigungen erforderlich, um Einblick in Workloads und Dienste zu erhalten. 

- [Übersicht über die Rolle „Sicherheitsleseberechtigter“](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#security-reader)

- [Übersicht über Azure-Verwaltungsgruppen](https://docs.microsoft.com/azure/governance/management-groups/overview)

**Azure Security Center-Überwachung**: Zurzeit nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: Ausschließliche Verwendung genehmigter Azure-Dienste

**Leitfaden**: Azure Information Protection unterstützt keine Azure Resource Manager Bereitstellungen und ermöglicht Kunden die Beschränkung von bereit Stellungen über integrierte Azure Policy Definitionen wie "Allow Resources" oder "Deny Resources". Allerdings können Kunden die Nutzung von Azure Information Protection durch bezeichnen von Richtlinien im Security and Compliance Center einschränken. 

- [Verwalten des Informationsschutzes über das Security and Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/protect-information?view=o365-worldwide&amp;preserve-view=true)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

## <a name="logging-and-threat-detection"></a>Protokollierung und Bedrohungserkennung

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Protokollierung und Bedrohungserkennung](/azure/security/benchmarks/security-controls-v2-logging-threat-protection).*

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2: Aktivieren der Bedrohungserkennung für die Identitäts- und Zugriffsverwaltung in Azure

**Leitfaden**: Azure Information Protection ist in Azure Active Directory (Azure AD) integriert, bei dem es sich um den Standard Dienst für die Identitäts-und Zugriffs Verwaltung von Azure handelt. 

Zeigen Sie Azure AD bereitgestellten Benutzer Protokollen mit Azure AD Berichterstellung und anderen Lösungen wie Azure Monitor, Azure Sentinel oder anderen Siem/Monitoring-Tools an, um anspruchsvollere Anwendungsfälle für die Überwachung und Analyse zu nutzen. 

Sie lauten wie folgt: 

-   Anmelde Bericht – der Anmelde Bericht enthält Informationen zur Verwendung verwalteter Anwendungen und Benutzer Anmelde Aktivitäten.

-   Überwachungsprotokolle: Ermöglichen die Nachverfolgung sämtlicher Änderungen, die von verschiedenen Features in Azure AD vorgenommen wurden. Beispiele für Überwachungs Protokolle sind Änderungen, die an Ressourcen innerhalb Azure AD vorgenommen werden, z. b. das Hinzufügen oder Entfernen von Benutzern, apps, Gruppen, Rollen und Richtlinien.

-   Riskante Anmeldungen: ein riskanter Anmeldeversuch ist ein Indikator für einen Anmeldeversuch, der möglicherweise von einem Benutzer durchgeführt wurde, der nicht der rechtmäßige Besitzer eines Benutzerkontos ist.

-   Benutzer mit Risikomarkierung: Ein Benutzer mit Risikomarkierung ist ein Indikator für ein ggf. kompromittiertes Benutzerkonto.

Azure Security Center können auch Warnungen für bestimmte verdächtige Aktivitäten, z. b. eine übermäßig viele fehlgeschlagene Authentifizierungs Versuche, und als veraltet markierte Konten im Abonnement angeben. Zusätzlich zur grundlegenden Überwachung der Sicherheitsüberwachung kann das Bedrohungsschutz Modul von Security Center auch ausführlichere Sicherheitswarnungen von einzelnen Azure-computeressourcen (z. b. virtuelle Computer, Container, App Service), Datenressourcen (z. b. SQL-Datenbank und Speicher) und Azure-Dienst Ebenen sammeln. So erhalten Sie Einblick in Kontoanomalien innerhalb einzelner Ressourcen.

- [Berichte zu Überwachungsaktivitäten in Azure AD](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-audit-logs)

- [Aktivieren von Azure Identity Protection](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection)

- [Bedrohungsschutz in Azure Security Center](https://docs.microsoft.com/azure/security-center/threat-protection)

**Azure Security Center-Überwachung:** Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4: Aktivieren der Protokollierung für Azure-Ressourcen

**Leitfaden**: Azure Information Protection bietet Datenschutz für Dokumente und e-Mails eines Unternehmens sowie ein Protokoll für jede Anforderung.  Diese Anforderungen beziehen sich auf den Fall, dass Benutzer Dokumente und e-Mails schützen, wenn diese Inhalte nutzen, von Administratoren für diesen Dienst ausgeführte Aktionen und von Microsoft-Operatoren durchgeführte Aktionen zur Unterstützung ihrer Azure Information Protection Bereitstellung.

Folgende Typen von Protokollen werden von Azure Information Protection erstellt:

- Administrator Protokoll: protokolliert administrative Aufgaben für den Schutzdienst. Beispiele: der Dienst wird deaktiviert, das Administratorfeature wird aktiviert, Administratorberechtigungen für den Dienst werden an Benutzer delegiert.

- Dokumentenverfolgung: ermöglicht Benutzern das Nachverfolgen und widerrufen Ihrer Dokumente, die Sie mit dem Azure Information Protection-Client verfolgt haben. Globale Administratoren können diese Dokumente im Auftrag von Benutzern nachverfolgen.

- Client Ereignisprotokolle: die Verwendungs Aktivität für den Azure Information Protection Client, die im lokalen Ereignisprotokoll für Windows-Anwendungen und-Dienste protokolliert wurde, Azure Information Protection.

- Client Protokolldateien: Problembehandlung bei Protokollen für den Azure Information Protection Client

Mithilfe der Schutz Verwendungs Protokolle können Sie feststellen, wer auf Ihre geschützten Daten, von welchen Geräten aus und von wo aus zugreift. In den Protokollen wird angezeigt, ob die Benutzer geschützte Inhalte erfolgreich lesen können. Außerdem können Sie feststellen, welche Personen ein wichtiges Dokument gelesen haben, das geschützt wurde. 

- [Protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](https://docs.microsoft.com/azure/information-protection/log-analyze-usage)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5: Zentralisieren der Verwaltung und Analyse von Sicherheitsprotokollen

**Leitfaden**: Stellen Sie sicher, dass Supportmitarbeiter eine vollständige Übersicht über die Vorgänge erstellen können, die während eines Ereignisses aufgetreten sind, indem Sie verschiedene Datenquellen Abfragen und verwenden, da Sie potenzielle Vorfälle untersuchen. 

Vermeiden Sie blind Flecken, indem Sie verschiedene Protokolle sammeln und Sie an eine zentrale Siem-Lösung wie Azure Sentinel senden, um die Aktivitäten eines potenziellen Angreifers in der Kill-Kette zu verfolgen. Die Protokolle können erkennen, ob Benutzer geschützte Inhalte erfolgreich lesen können, und Sie können feststellen, welche Personen ein wichtiges Dokument gelesen haben, das geschützt wurde. Stellen Sie sicher, dass Einblicke und Erkenntnisse für andere Analysten und für die zukünftige Verlaufs Referenz aufgezeichnet werden.  

Azure Sentinel bietet umfangreiche Datenanalysen über praktisch jede Protokollquelle sowie ein Fallverwaltungsportal zum Verwalten des gesamten Lebenszyklus von Vorfällen. Intelligenceinformationen während einer Untersuchung können zu Verfolgungs- und Berichtszwecken mit einem Vorfall verknüpft werden. 

- [Protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](https://docs.microsoft.com/azure/information-protection/log-analyze-usage)

- Lesen Sie [Untersuchen von Incidents mit Azure Sentinel](https://docs.microsoft.com/azure/sentinel/tutorial-investigate-cases).

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="lt-6-configure-log-storage-retention"></a>LT-6: Konfigurieren der Aufbewahrungsdauer von Protokollen im Speicher

**Leitfaden**: Azure Information Protection bietet Datenschutz für die Dokumente und e-Mails einer Organisation mit einem Protokoll für jede Anforderung an die Dokumente und e-Mails.  Diese Anforderungen beziehen sich auf den Fall, dass Benutzer Dokumente und e-Mails schützen, wenn diese Inhalte nutzen, von Administratoren für diesen Dienst ausgeführte Aktionen und von Microsoft-Operatoren durchgeführte Aktionen zur Unterstützung ihrer Azure Information Protection Bereitstellung.

Die Menge der Daten, die in Ihrem Azure Information Protection Arbeitsbereich erfasst und gespeichert werden, sowie die Beibehaltungs Dauer variieren für jeden Mandanten erheblich. Dies hängt von Faktoren ab, wie z. b. wie viele Azure Information Protection Clients und andere unterstützte Endpunkte vorliegen, ob Sie die Endpunkt Ermittlungs Daten sammeln, Scanner bereitgestellt haben, auf welche Anzahl geschützter Dokumente zugegriffen wird usw.

Verwenden Sie das Feature Verwendungs-und geschätzte Kosten Azure Monitor Protokolls, um die Menge der gespeicherten Daten zu schätzen und zu überprüfen. Außerdem können Sie die Beibehaltungs Dauer für Ihren Log Analytics Arbeitsbereich steuern. 

- [Protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](https://docs.microsoft.com/azure/information-protection/log-analyze-usage)

- [Verwalten von Nutzung und Kosten mit Azure Monitor-Protokollen](https://docs.microsoft.com/azure/azure-monitor/platform/manage-cost-storage)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

## <a name="incident-response"></a>Reaktion auf Vorfälle

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Reaktion auf Vorfälle](/azure/security/benchmarks/security-controls-v2-incident-response).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: Vorbereitung – Aktualisieren des Prozesses zur Reaktion auf Vorfälle für Azure

**Leitfaden**: Stellen Sie sicher, dass Ihre Organisation über Prozesse verfügt, um auf Sicherheitsvorfälle zu reagieren, dass diese Prozesse für Azure aktualisiert wurden und dass sie regelmäßig trainiert werden, um die Bereitschaft zu gewährleisten.

- [Implement security across the enterprise environment](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud) (Implementieren von Sicherheit in der gesamten Unternehmensumgebung)

- [Referenzleitfaden für die Reaktion auf Vorfälle](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: Vorbereitung – Einrichten von Ereignisbenachrichtigungen

**Leitfaden**: Richten Sie Kontaktinformationen für Sicherheitsvorfälle im Azure Security Center ein. Microsoft wendet sich unter den angegebenen Kontaktdaten an Sie, wenn das Microsoft Security Response Center (MSRC) feststellt, dass Personen unrechtmäßig oder unbefugt auf Ihre Daten zugegriffen haben. Sie haben auch die Möglichkeit, die Warnungen und Benachrichtigungen bei Vorfällen in verschiedenen Azure-Diensten entsprechend Ihrer Anforderungen bezüglich der Reaktion auf Vorfälle anzupassen. 

- [Festlegen der Kontaktinformationen in Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Azure Security Center-Überwachung**: Ja

**Verantwortlichkeit**: Kunde

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: Erkennung und Analyse – Erstellen von Vorfällen basierend auf Warnungen mit hoher Qualität

**Leitfaden**: Stellen Sie sicher, dass Sie über einen Prozess zum Erstellen hochwertiger Warnungen und zum Messen der Qualität von Warnungen verfügen. Auf diese Weise können Sie Lehren aus vergangenen Vorfällen ziehen und Warnungen für Analysten priorisieren, damit diese keine Zeit mit falsch-positiven Ergebnissen verschwenden. 

Qualitativ hochwertige Warnungen können auf der Grundlage von Erfahrungen aus früheren Vorfällen, validierten Communityquellen und Tools zur Generierung und Bereinigung von Warnmeldungen durch Verschmelzung und Korrelation verschiedener Signalquellen erstellt werden. 

Azure Security Center bietet qualitativ hochwertige Warnungen für viele Azure-Ressourcen. Sie können den ASC-Datenconnector verwenden, um die Warnungen an Azure Sentinel zu streamen. Mit Azure Sentinel können Sie erweiterte Warnregeln erstellen, um Vorfälle automatisch für eine Untersuchung zu generieren. 

Exportieren Sie Ihre Azure Security Center-Warnungen und -Empfehlungen über das Exportfeature, um Risiken für Azure-Ressourcen zu ermitteln. Exportieren Sie Warnungen und Empfehlungen entweder manuell oder fortlaufend, kontinuierlich.

- [Konfigurieren des Exports](https://docs.microsoft.com/azure/security-center/continuous-export)

- [Streamen von Warnungen in Azure Sentinel](https://docs.microsoft.com/azure/sentinel/connect-azure-security-center)

**Azure Security Center-Überwachung**: Zurzeit nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Erkennung und Analyse – Untersuchen eines Vorfalls

**Leitfaden**: Stellen Sie sicher, dass Analysten eine vollständige Übersicht darüber erstellen können, was passiert ist, indem Sie bei der Untersuchung potenzieller Vorfälle verschiedene Datenquellen Abfragen und verwenden. Vermeiden Sie blind Flecken, indem Sie verschiedene Protokolle sammeln, um die Aktivitäten eines potenziellen Angreifers in der Kill-Kette zu verfolgen. Außerdem sollten Sie sicherstellen, dass Einblicke und Erkenntnisse für andere Analysten und für zukünftige Verlaufs Referenzen aufgezeichnet werden.  

Zu den zu untersuchenden Datenquellen gehören die zentralisierten Protokollierungsquellen, die bereits von den zum Umfang gehörige Diensten und ausgeführten Systemen gesammelt werden, aber auch andere:

- Netzwerkdaten: Verwenden Sie die Datenflussprotokolle von Netzwerksicherheitsgruppen sowie Azure Network Watcher und Azure Monitor, um Netzwerkflussprotokolle und andere Analyseinformationen zu erfassen. 

- Momentaufnahmen von laufenden Systemen: 

    - Verwenden Sie die Momentaufnahmenfunktion des virtuellen Azure-Computers, um eine Momentaufnahme der Festplatte des laufenden Systems zu erstellen. 

    - Verwenden Sie die integrierte Speicher Abbild Funktion des Betriebssystems, um eine Momentaufnahme des Arbeitsspeichers des laufenden Systems zu erstellen.

    - Verwenden Sie das Momentaufnahmenfeature der Azure-Dienste oder die Funktion Ihrer Software, um Momentaufnahmen der laufenden Systeme zu erstellen.

Azure Sentinel bietet umfangreiche Datenanalysen über praktisch jede Protokollquelle sowie ein Fallverwaltungsportal zum Verwalten des gesamten Lebenszyklus von Vorfällen. Intelligenceinformationen während einer Untersuchung können zu Verfolgungs- und Berichtszwecken mit einem Vorfall verknüpft werden. 

- [Momentaufnahme des Datenträgers eines Windows-Computers](https://docs.microsoft.com/azure/virtual-machines/windows/snapshot-copy-managed-disk)

- [Momentaufnahme des Datenträgers eines Linux-Computers](https://docs.microsoft.com/azure/virtual-machines/linux/snapshot-copy-managed-disk)

- [Microsoft Azure-Supportdiagnoseinformationen und Speicherabbilderfassung](https://azure.microsoft.com/support/legal/support-diagnostic-information-collection/) 

- Lesen Sie [Untersuchen von Incidents mit Azure Sentinel](https://docs.microsoft.com/azure/sentinel/tutorial-investigate-cases).

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: Erkennung und Analyse – Priorisieren von Vorfällen

**Leitfaden**: Stellen Sie den Analysten Kontext bereit, auf welche Vorfälle sie sich zuerst konzentrieren sollten, je nach Schweregrad und Ressourcensensitivität. 

Azure Security Center weist jeder Warnung einen Schweregrad zu, damit Sie priorisieren können, welche Warnungen zuerst untersucht werden sollen. Der Schweregrad basiert darauf, wie zuversichtlich Security Center in Bezug auf den Befund oder die Analyse ist, die zum Auslösen der Warnung verwendet wird, sowie auf dem Zuverlässigkeitsgrad, dass hinter der Aktivität, die zu der Warnung führte, eine böswillige Absicht stand.

Markieren Sie Ressourcen außerdem mithilfe von Tags, und erstellen Sie ein Benennungssystem, um Azure-Ressourcen eindeutig zu identifizieren und zu kategorisieren – insbesondere solche, von denen vertrauliche Daten verarbeitet werden.  Die Priorisierung der Behebung von Warnungen basierend auf der Wichtigkeit der Azure-Ressourcen und der Umgebung, in der der Vorfall aufgetreten ist, liegt in Ihrer Verantwortung.

- [Sicherheitswarnungen in Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-alerts-overview)

- [Verwenden von Tags zum Organisieren von Azure-Ressourcen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags)

**Azure Security Center-Überwachung**: Zurzeit nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: Eindämmung, Ausmerzung und Wiederherstellung – Automatisieren der Behandlung von Vorfällen

**Leitfaden**: Automatisieren Sie manuelle, sich wiederholende Aufgaben, um die Antwortzeit zu beschleunigen und die Belastung der Analysten zu verringern. Manuelle Aufgaben dauern länger, verlangsamen jeden Vorfall und reduzieren die Anzahl der Vorfälle, die ein Analyst bewältigen kann. Manuelle Aufgaben erhöhen auch die Ermüdung der Analytiker. Dadurch erhöht sich das Risiko menschlicher Fehler, die zu Verzögerungen führen, und es verschlechtert sich die Fähigkeit der Analytiker, sich effektiv auf komplexe Aufgaben zu konzentrieren. Verwenden Sie die Workflowautomatisierungsfeatures in Azure Security Center und Azure Sentinel, um automatisch Aktionen auszulösen oder ein Playbook auszuführen, um auf eingehende Sicherheitswarnungen zu reagieren. Das Playbook führt Aktionen aus, wie das Versenden von Benachrichtigungen, das Deaktivieren von Konten und das Isolieren problematischer Netzwerke. 

- [Konfigurieren der Workflowautomatisierung in Security Center](https://docs.microsoft.com/azure/security-center/workflow-automation)

- [Einrichten automatisierter Reaktionen auf Bedrohungen in Azure Security Center](https://docs.microsoft.com/azure/security-center/tutorial-security-incident#triage-security-alerts)

- Machen Sie sich mit dem [Einrichten automatisierter Reaktionen auf Bedrohungen in Azure Sentinel](https://docs.microsoft.com/azure/sentinel/tutorial-respond-threats-playbook) vertraut.

**Azure Security Center-Überwachung**: Zurzeit nicht verfügbar

**Verantwortlichkeit**: Kunde

## <a name="posture-and-vulnerability-management"></a>Status- und Sicherheitsrisikoverwaltung

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Status- und Sicherheitsrisikoverwaltung](/azure/security/benchmarks/security-controls-v2-vulnerability-management).*

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1: Einrichten sicherer Konfigurationen für Azure-Dienste 

**Leitfaden**: Azure Information Protection können über das Security and Compliance Center oder über PowerShell konfiguriert werden. 

Innerhalb des Security and Compliance Centers kann ein Administrator Vertraulichkeits Bezeichnungen erstellen, definieren, was jede Bezeichnung tun kann, und die Bezeichnungen veröffentlichen. 

Erstellen der Bezeichnungen: Erstellen Sie Ihre Vertraulichkeits Bezeichnungen, und benennen Sie Sie entsprechend der Klassifizierungs Taxonomie Ihrer Organisation für verschiedene sensible Inhalts Ebenen. Verwenden Sie allgemeine Namen oder Begriffe, die für die Benutzer sinnvoll sind. Wenn Sie noch nicht über eine etablierte Taxonomie verfügen, sollten Sie mit Bezeichnungs Namen wie "Personal", "Public", "General", "Confidential" und "streng vertraulich" beginnen Sie können dann untergeordnete Bezeichnungen verwenden, um ähnliche Bezeichnungen nach Kategorie zu gruppieren. Wenn Sie eine Bezeichnung erstellen, verwenden Sie den QuickInfo-Text, um Benutzern die Auswahl der entsprechenden Bezeichnung zu erleichtern.

Definieren Sie, was die einzelnen Bezeichnungen tun können: Konfigurieren Sie die Schutzeinstellungen, die den einzelnen Bezeichnungen zugeordnet werden sollen. Beispielsweise kann es vorkommen, dass ein niedrigerer Vertraulichkeits Inhalt (z. b. eine "allgemeine" Bezeichnung) nur eine Kopf-oder Fußzeile angewendet werden soll, während ein höherer Vertraulichkeits Inhalt (z. b. eine "vertrauliche" Bezeichnung) ein Wasserzeichen und eine Verschlüsselung aufweisen sollte.

Veröffentlichen der Bezeichnungen: Nachdem Sie Ihre Vertraulichkeits Bezeichnungen konfiguriert haben, veröffentlichen Sie Sie mithilfe einer Bezeichnungs Richtlinie. Entscheiden Sie, welche Benutzer und Gruppen über die Bezeichnungen verfügen sollen und welche Richtlinien Einstellungen verwendet werden sollen. Eine einzelne Bezeichnung ist wiederverwendbar – Sie definieren Sie einmal, und dann können Sie Sie in mehrere Bezeichnungs Richtlinien einschließen, die unterschiedlichen Benutzern zugewiesen sind. Beispielsweise könnten Sie Ihre Vertraulichkeits Bezeichnungen per Pilotversuch durch Zuweisen einer Bezeichnungs Richtlinie nur wenigen Benutzern zuweisen. Wenn Sie zum Rollout der Bezeichnungen in Ihrer Organisation bereit sind, können Sie eine neue Bezeichnungs Richtlinie für ihre Bezeichnungen erstellen und dieses Mal alle Benutzer angeben.

Um PowerShell zu verwenden, installieren Sie das PowerShell-Modul aipservice. In PowerShell kann ein Administrator diese Aufgaben zusammen mit anderen durchführen: 

- Migrieren von lokalem Rights Management (AD RMS oder Windows RMS) zu Azure Information Protection
- Generieren und Verwalten Ihres eigenen Mandanten Schlüssels: Byok-Szenario (Bring your own Key)
- Aktivieren oder Deaktivieren des Rights Management Dienstanbieter für Ihre Organisation
- Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung von Azure Rights Management Service
- Erstellen und Verwalten von Rights Management Vorlagen für Ihre Organisation
- Verwalten von Benutzern und Gruppen, die autorisiert sind, Rights Management-Dienst für Ihre Organisation zu verwalten
- Protokollieren und Analysieren der Verwendung für Rights Management

Weitere Informationen finden Sie in den folgenden Referenzen:

- [Beginnen Sie mit Vertraulichkeits Bezeichnungen im Security and Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels?view=o365-worldwide&amp;preserve-view=true)

- [Erstellen und Veröffentlichen von Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels?view=o365-worldwide&amp;preserve-view=true)

- [Anwenden von Verschlüsselung auf Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide&amp;preserve-view=true)

- [PowerShell für Azure Information Protection](https://docs.microsoft.com/azure/information-protection/administer-powershell)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: Regelmäßiges Durchführen einer Angriffssimulation

**Leitfaden**: Führen Sie nach Bedarf Penetrationstests oder Red Team-Aktivitäten für Ihre Azure-Ressourcen durch, und stellen Sie sicher, dass alle kritischen Sicherheitsergebnisse behandelt werden.
Befolgen Sie die Einsatzregeln für Penetrationstests für die Microsoft Cloud, um sicherzustellen, dass die Penetrationstests nicht gegen Microsoft-Richtlinien verstoßen. Nutzen Sie die Microsoft-Strategie und Durchführung von Red Team- und Livewebsite-Penetrationstests für von Microsoft verwaltete Cloudinfrastruktur, Dienste und Anwendungen.

- [Penetrationstests in Azure](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [Penetrationstests – Rules of Engagement](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1) 

- [Microsoft Cloud Red Teaming](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Shared

## <a name="backup-and-recovery"></a>Sicherung und Wiederherstellung

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Sicherung und Wiederherstellung](/azure/security/benchmarks/security-controls-v2-backup-recovery).*

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4: Minimieren der Auswirkungen verlorener Schlüssel

**Leitfaden**: Azure Information Protection bietet Kunden die Möglichkeit, ihren Mandanten mit Ihrem eigenen Schlüssel über Bring your own Key (Byok) zu konfigurieren. Vom Kunden generierte Schlüssel müssen für den Schutz in Azure Key Vault gespeichert werden. Azure Key Vault hilft, den Verlust von Schlüsseln durch vorläufiges löschen, Rollen Trennung und getrennte Sicherheits Domänen zu verhindern. 

- [Azure Information Protection Bring your own Key und Integration mit Azure Key Vault](https://docs.microsoft.com/azure/information-protection/byok-price-restrictions)
- [Vorläufiges löschen in Key Vault aktivieren](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

**Azure Security Center-Überwachung**: Ja

**Verantwortlichkeit**: Kunde

## <a name="governance-and-strategy"></a>Governance und Strategie

*Weitere Informationen finden Sie unter [Azure-Sicherheitsvergleichstest: Governance und Strategie](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: Definieren der Strategie für Ressourcenverwaltung und Datenschutz 

**Leitfaden**: Stellen Sie sicher, dass Sie eine klare Strategie für die kontinuierliche Überwachung und den Schutz von Systemen und Daten dokumentieren und kommunizieren. Priorisieren Sie die Ermittlung, die Bewertung, den Schutz und die Überwachung unternehmenskritischer Daten und Systeme. 

Diese Strategie sollte dokumentierte Anleitungen, Richtlinien und Standards für die folgenden Elemente umfassen: 

-   Datenklassifizierungsstandard in Übereinstimmung mit den Geschäftsrisiken

-   Sicherheitsorganisationseinblick in Risiken und Ressourcenbestand 

-   Genehmigung durch die Sicherheitsorganisation für die Nutzung der Azure-Dienste 

-   Sicherheit von Ressourcen durch ihren gesamten Lebenszyklus

-   Erforderliche Zugriffssteuerungsstrategie in Übereinstimmung mit der Organisationsdatenklassifizierung

-   Verwendung von integrierten Azure-Funktionen und Datenschutzfunktionen von Drittanbietern

-   Datenverschlüsselungsanforderungen für Anwendungsfälle während der Übertragung und für ruhende Anwendungsfälle

-   Geeignete Verschlüsselungsstandards

Weitere Informationen finden Sie in den folgenden Referenzen:

- [Empfehlung für eine Azure-Sicherheitsarchitektur: Speicher, Daten, Verschlüsselung](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Grundlegende Azure-Sicherheitsinformationen: Sicherheit, Verschlüsselung und Speicherung von Azure-Daten](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [Cloud Adoption Framework: Bewährte Methoden für Datensicherheit und Datenverschlüsselung in Azure](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Azure-Sicherheitsvergleichstest: Ressorcenverwaltung](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Azure-Sicherheitsvergleichstest: Datenschutz](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: Definieren der Strategie für Unternehmenssegmentierung 

**Leitfaden**: Erstellen Sie eine unternehmensweite Strategie zum Segmentieren des Zugriffs auf Ressourcen durch eine Kombination aus Identität, Netzwerk, Anwendung, Abonnement, Verwaltungsgruppe und anderen Steuerelementen.

Wägen Sie die Notwendigkeit einer Sicherheitstrennung sorgfältig gegen die Notwendigkeit ab, den täglichen Betrieb der Systeme zu ermöglichen, die miteinander kommunizieren und auf Daten zugreifen müssen.

Stellen Sie sicher, dass die Segmentierungsstrategie einheitlich für alle Steuerelementtypen implementiert wird, einschließlich Netzwerksicherheit, Identitäts- und Zugriffsmodelle, Berechtigungs-/Zugriffsmodelle für Anwendungen sowie Steuerelemente für Benutzerprozesse.

- [Leitfaden für die Segmentierungsstrategie in Azure (Video)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Leitfaden für die Segmentierungsstrategie in Azure (Dokument)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [Ausrichten der Netzwerksegmentierung an der Segmentierungsstrategie des Unternehmens](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: Definieren der Strategie für die Sicherheitsstatusverwaltung

**Leitfaden**: Führen Sie kontinuierliche Messungen durch, und Mindern Sie die Risiken für Ihre individuellen Ressourcen und die Umgebung, in der diese gehostet werden. Priorisieren Sie Ressourcen mit hohem Wert und hoch exponierte Angriffsflächen, wie z. B. veröffentlichte Anwendungen, Eingangs- und Ausgangspunkte für Netzwerke, Benutzer- und Administratorendpunkte usw.

- [Azure-Sicherheitsvergleichstest: Verwaltung von Status und Sicherheitsrisiken](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: Ausrichten von Organisationsrollen, Zuständigkeiten und Verantwortlichkeiten

**Leitfaden**: Stellen Sie sicher, dass Sie eine klare Strategie für Rollen und Zuständigkeiten in ihrer Sicherheitsorganisation dokumentieren und kommunizieren. Priorisieren Sie durch Zuweisung klarer Verantwortlichkeiten für Sicherheitsentscheidungen, Schulung aller Beteiligten für das Modell der gemeinsamen Verantwortung und Schulung von technischen Teams hinsichtlich der Technologie zum Sichern der Cloud.

- [Azure Security Best Practice 1 – People: Educate Teams on Cloud Security Journey](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey) (Bewährte Methoden für die Sicherheit von Azure 1 – Personen: Schulen von Teams auf dem Weg zur Cloudsicherheit)

- [Azure Security Best Practice 2 – People: Educate Teams on Cloud Security Technology](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology) (Bewährte Methoden für die Sicherheit von Azure 1 – Personen: Schulen der Teams in Cloudsicherheitstechnologie)

- [Azure Security Best Practice 3 – Process: Assign Accountability for Cloud Security Decisions](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud) (Bewährte Methoden für die Sicherheit von Azure 1 – Prozess: Zuweisen von Verantwortlichkeit für Cloudsicherheitsentscheidungen)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="gs-5-define-network-security-strategy"></a>GS-5: Definieren einer Netzwerksicherheitsstrategie

**Leitfaden**: Richten Sie einen Ansatz für die Azure-Netzwerksicherheit im Rahmen der Gesamtstrategie Ihrer Organisation für die Sicherheitszugriffssteuerung ein.  

Diese Strategie sollte dokumentierte Anleitungen, Richtlinien und Standards für die folgenden Elemente umfassen: 

-   Zentralisieren der Verantwortlichkeit für Netzwerkverwaltung und -sicherheit

-   Segmentierungsmodell für virtuelle Netzwerke, das auf die Segmentierungsstrategie des Unternehmens abgestimmt ist

-   Wiederherstellungsstrategie in verschiedenen Bedrohungs- und Angriffsszenarien

-   Strategie für Internet-Randpunkte, -Eingangspunkte und -Ausgangspunkte

-   Strategie für Konnektivität zwischen Hybrid Cloud und lokalen Systemen

-   Aktuelle Netzwerksicherheitsartefakte (z. B. Netzwerkdiagramme, Referenznetzwerkarchitektur)

Weitere Informationen finden Sie in den folgenden Referenzen:
- [Azure Security Best Practice 11 – Architecture. Single unified security strategy](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy) (Bewährte Methoden für die Sicherheit von Azure 11 – Architektur: Zentralisierte einheitliche Sicherheitsstrategie)

- [Azure-Sicherheitsvergleichstest: Netzwerksicherheit](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Die Netzwerksicherheit in Azure in der Übersicht](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [Strategie für die Unternehmensnetzwerkarchitektur](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: Definieren der Strategie für Identität und privilegierten Zugriff

**Leitfaden**: Richten Sie einen Ansatz für Azure-Identität und privilegierten Zugriff im Rahmen der Gesamtstrategie Ihrer Organisation für die Sicherheitszugriffssteuerung ein.  

Diese Strategie sollte dokumentierte Anleitungen, Richtlinien und Standards für die folgenden Elemente umfassen: 

-   Zentralisiertes Identitäts- und Authentifizierungssystem mit Interkonnektivität zu anderen internen und externen Identitätssystemen

-   Starke Authentifizierungsmethoden in verschiedenen Anwendungsfällen und Bedingungen

-   Schutz stark privilegierter Benutzer

-   Überwachung und Behandlung von Anomalien bei Benutzeraktivitäten  

-   Benutzeridentität und Zugriffsüberprüfung und Abstimmungsprozess

Weitere Informationen finden Sie in den folgenden Referenzen:

- [Azure-Sicherheitsvergleichstest: Identitätsverwaltung](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Azure-Sicherheitsvergleichstest: Privilegierter Zugriff](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Azure Security Best Practice 11 – Architecture. Single unified security strategy](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy) (Bewährte Methoden für die Sicherheit von Azure 11 – Architektur: Zentralisierte einheitliche Sicherheitsstrategie)

- [Übersicht über die Sicherheit der Azure-Identitätsverwaltung](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: Definieren einer Strategie für Protokollierung und Reaktion auf Bedrohungen

**Leitfaden**: Richten Sie eine Strategie für Protokollierung und Reaktion auf Bedrohungen zur schnellen Erkennung und Behebung von Bedrohungen bei gleichzeitiger Erfüllung von Complianceanforderungen ein. Priorisieren Sie die Bereitstellung wertvoller Warnungen und nahtloser Funktionen für Analysten, damit sie sich auf Bedrohungen konzentrieren können, anstatt mit der Integration und der Ausführung manueller Schritte. 

Diese Strategie sollte dokumentierte Anleitungen, Richtlinien und Standards für die folgenden Elemente umfassen: 

-   Rolle und Verantwortlichkeiten der Organisation für Sicherheitsvorgänge (SecOps) 

-   Ein klar definierter Prozess zur Reaktion auf Vorfälle gemäß NIST oder einem anderen Branchenframework 

-   Erfassung und Aufbewahrung von Protokollen zur Unterstützung von Bedrohungserkennung, Reaktion auf Vorfälle und Complianceanforderungen

-   Zentralisierte Sichtbarkeit von und Korrelations Informationen zu Bedrohungen, Verwendung von Siem, integrierten Azure-Funktionen und anderen Quellen 

-   Kommunikations- und Benachrichtigungsplan mit Ihren Kunden, Lieferanten und öffentlichen Interessengruppen

-   Verwendung von integrierten Azure-und Drittanbieter Plattformen für die Behandlung von Vorfällen, wie z. b. Protokollierung und Bedrohungserkennung, Forensik sowie Behebung und Beseitigung von Angriffen

-   Prozesse für den Umgang mit Vorfällen und Aktivitäten nach Vorfällen, wie z. B. Erkenntnisse und Beweissicherung

Weitere Informationen finden Sie in den folgenden Referenzen:

- [Azure-Sicherheitsvergleichstest: Protokollierung und Bedrohungserkennung](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Azure-Sicherheitsvergleichstest: Reaktion auf Vorfälle](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Azure Security Best Practice 4 – Process. Update Incident Response Processes for Cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud) (Bewährte Methoden für die Sicherheit von Azure 4 – Prozess: Aktualisieren der Prozesse zur Reaktion auf Vorfälle für die Cloud)

- [Azure Adoption Framework, Entscheidungshilfe für Protokollierung und Berichterstattung](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Azure auf Unternehmensebene, Verwaltung und Überwachung](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Azure Security Center-Überwachung**: Nicht verfügbar

**Verantwortlichkeit**: Kunde

## <a name="next-steps"></a>Nächste Schritte

- Sehen Sie sich die [Übersicht über Version 2 des Azure-Sicherheitsvergleichstests](/azure/security/benchmarks/overview) an.
- Erfahren Sie mehr über [Azure-Sicherheitsbaselines](/azure/security/benchmarks/security-baselines-overview).
