---
title: Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center – AIP
description: Migrieren Sie Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center für Clients, die einheitliche Bezeichnungen unterstützen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/17/20198
ms.topic: article
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 221b503fa3621e51c4822a6ad5a6d08fae4f1bad
ms.sourcegitcommit: 8dec864bf25c7da62b9e0f628f1bf673c81c15ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54356010"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-the-office-365-security--compliance-center"></a>Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Dieses Feature befindet sich in der Vorschau und migriert Ihren Mandanten zu einer neuen Plattform, die ebenfalls als Vorschau verfügbar ist. Die Migration kann nicht rückgängig gemacht werden. Die neue Plattform unterstützt einheitliche Bezeichnungen. Das bedeutet, dass die Bezeichnungen, die Sie erstellen und verwalten, von mehreren Clients und Diensten verwendet werden können.

Migrieren Sie Ihre Bezeichnungen, um Sie im Office 365 Security & Compliance Center zu verwenden. Dort können sie veröffentlicht und dann von [Clients, die einheitliche Bezeichnungen unterstützen](#clients-that-support-unified-labeling), heruntergeladen werden. Der Azure Information Protection-Client lädt die Bezeichnungen mit ihrer Azure Information Protection-Richtlinie aus dem Azure-Portal herunter. 

Nachdem Sie Ihre Bezeichnungen migriert haben, können Sie diese im Azure-Portal oder im Office 365 Security & Compliance Center ändern. Die jeweiligen Clients laden dann ebendiese Änderungen herunter.

### <a name="important-information-about-administrative-roles"></a>Wichtige Informationen zu Administratorrollen

Die [Azure AD-Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) **Sicherheitsadministrator** und **Information Protection-Administrator** werden von der Plattform für einheitliche Bezeichnungen nicht unterstützt. Wenn diese Administratorrollen in Ihrer Organisation verwendet werden, fügen Sie vor der Migration Ihrer Bezeichnungen die Benutzer, die diese Rollen haben, dem **Complianceadministrator** oder den Rollengruppen für die **Organisationsverwaltung** für das Office 365 Security & Compliance Center hinzu. Alternativ können Sie für diese Benutzer eine neue Rollengruppe erstellen und dieser Gruppe entweder Rollen für die **Aufbewahrungsverwaltung** oder die **Organisationskonfiguration** hinzufügen. Anleitungen finden Sie unter [Gewähren von Benutzerzugriff auf das Office 365 Security & Compliance Center](https://docs.microsoft.com/office365/securitycompliance/grant-access-to-the-security-and-compliance-center).

Wenn Sie diesen Benutzern nicht über eine dieser Konfigurationen den Zugriff auf das Security & Compliance Center gewähren, können sie nach der Migration Ihrer Bezeichnungen nicht mehr auf die Bezeichnungen und Richtlinien im Azure-Portal zugreifen.

Globale Administratoren für Ihren Mandanten können nach der Migration Ihrer Bezeichnungen weiterhin Bezeichnungen und Richtlinien sowohl im Azure-Portal als auch im Security & Compliance Center verwalten.


## <a name="considerations-for-unified-labels"></a>Überlegungen zu einheitlichen Bezeichnungen

Beachten Sie die folgenden Änderungen und Überlegungen, bevor Sie Bezeichnungen migrieren:

- Nicht alle Clients unterstützen derzeit einheitliche Bezeichnungen. Stellen Sie sicher, dass Sie über [unterstützte Clients](#clients-that-support-unified-labeling) verfügen. Die Verwaltung erfolgt im Azure-Portal (Clients, die einheitliche Bezeichnungen nicht unterstützen) und im Security & Compliance Center (Clients, die einheitliche Bezeichnungen unterstützen).

- Wenn Sie gerade dabei sind, die gewünschten Bezeichnungen zu definieren und zu konfigurieren, empfehlen wir Ihnen, diesen Vorgang im Azure-Portal abzuschließen und die Bezeichnungen danach zu migrieren. Dadurch werden beim Migrationsvorgang doppelte Bezeichnungen vermieden, die dann im Security & Compliance Center bearbeitet werden müssen.

- Richtlinien, einschließlich Richtlinieneinstellungen und der entsprechenden Zugriffberechtigungen (bereichsbezogene Richtlinien), sowie alle erweiterten Clienteinstellungen werden nicht migriert. Für nicht migrierte Änderungen müssen Sie nach der Migration der Bezeichnungen die entsprechenden Optionen im Security & Compliance Center konfigurieren.
    
    Zur Optimierung der Benutzerfreundlichkeit empfehlen wir, die gleichen Bezeichnungen in den gleichen Bereichen im Security & Compliance Center zu veröffentlichen.

- Nicht alle Einstellungen einer migrierten Bezeichnung werden vom Security & Compliance Center unterstützt. Verwenden Sie die Tabelle in Abschnitt [Im Security & Compliance Center nicht unterstützte Bezeichnungseinstellungen](#label-settings-that-are-not-supported-in-the-security--compliance-center), um die entsprechenden Einstellungen zu ermitteln, die vom Security & Compliance Center nicht unterstützt werden.

- Schutzvorlagen:
    
    - Vorlagen, die einen cloudbasierten Schlüssel verwenden und Teil einer Bezeichnungskonfiguration sind, werden ebenfalls mit der Bezeichnung migriert. Andere Schutzvorlagen werden nicht migriert. 
    
    - Nach der Migration einer Bezeichnung mit cloudbasierten Schutzeinstellungen ist der Ergebnisbereich der Schutzvorlage der Bereich, der im Azure-Portal (bzw. unter Verwendung des ADDRM PowerShell-Moduls) und im Security & Compliance Center definiert ist. 

- Wenn Sie Ihre Bezeichnungen migrieren, zeigen die Migrationsergebnisse an, ob eine Bezeichnung **erstellt**, **aktualisiert** oder zum Vermeiden von Duplikaten **umbenannt** wurde:

    - Wenn Sie eine Bezeichnung erstellen, veröffentlichen Sie sie anschließend im Security & Compliance Center, um sie Anwendungen und Diensten zur Verfügung zu stellen.
    
    - Wenn Sie eine Bezeichnung umbenennen, bearbeiten Sie sie anschließend im Security & Compliance Center oder im Azure-Portal. 

- Das Azure-Portal zeigt nur den Anzeigenamen der jeweiligen Bezeichnung an, den Sie bearbeiten können. Das Security & Compliance Center zeigt sowohl den Anzeigenamen als auch den Bezeichnungsnamen an. Der Bezeichnungsname ist der ursprüngliche Name, den Sie beim Erstellen der Bezeichnung angeben. Diese Eigenschaft nutzt der Back-End-Dienst zur Identifizierung.

- Lokalisierte Zeichenfolgen für die Bezeichnungen werden nicht migriert. Sie müssen im Security & Compliance Center neue lokalisierte Zeichenfolgen für die migrierten Bezeichnungen definieren.

- Wenn Sie nach der Migration eine migrierte Bezeichnung im Azure-Portal bearbeiten, wird die entsprechende Änderung automatisch im Security & Compliance Center angezeigt. Wenn Sie jedoch eine migrierte Kennzeichnung im Security & Compliance Center bearbeiten, müssen Sie im Azure-Portal zum Blatt **Azure Information Protection – Einheitliche Bezeichnung** zurückkehren und **Veröffentlichen** auswählen. Diese zusätzliche Aktion ist erforderlich, damit die Clients von Azure Information Protection die Bezeichnungsänderungen übernehmen können.

### <a name="label-settings-that-are-not-supported-in-the-security--compliance-center"></a>Im Security & Compliance Center nicht unterstützte Bezeichnungseinstellungen

Anhand der folgenden Tabelle können Sie feststellen, welche Konfigurationseinstellungen einer migrierten Bezeichnung von Clients für einheitliche Bezeichnungen nicht oder nur eingeschränkt unterstützt werden. Um Verwirrung zu vermeiden, empfehlen wir Ihnen, die Einstellungen, die keine Auswirkungen auf Clients für einheitliche Bezeichnungen haben, nicht zu konfigurieren.

Azure Information Protection-Clients können diese Bezeichnungseinstellungen problemlos verwenden, weil sie die Bezeichnungen weiterhin aus dem Azure-Portal herunterladen.

|Bezeichnungskonfiguration|Unterstützt von Clients für einheitliche Bezeichnungen|Im Security & Compliance Center von Bearbeitung ausgeschlossen|
|-------------------|---------------------------------------------|-------------------------|
|Statusangabe „Aktiviert“/„Deaktiviert“<br /><br />Hinweise: Keine Synchronisierung im Security & Compliance Center |Nicht verfügbar|Nicht verfügbar|
|Bezeichnungsfarbe: Auswahl aus der Liste oder Angabe mit RGB-Code<br /><br />Hinweise: Keine Unterstützung im Security & Compliance Center |Nicht verfügbar|Nicht verfügbar|
|Cloudbasierter Schutz oder HYOK-Schutz (Hold Your Own Key) mit vordefinierter Vorlage |Nein|Ja|
|Cloudbasierter Schutz mit benutzerdefinierten Berechtigungen in Word, Excel und PowerPoint |Nein|Ja|
|HYOK-Schutz mit benutzerdefinierten Berechtigungen in Outlook für „Nicht weiterleiten“ |Nein|Ja|
|Entfernen von Schutz |Nein|Ja|
|Visuelle Kennzeichnung (Kopfzeile, Fußzeile, Wasserzeichen): Benutzerdefinierte Schriftart und benutzerdefinierte Schriftfarbe nach RGB-Code|Nein|Empfohlen beim Verwenden von Variablen<br /><br />– Auf Clients werden Variablen nicht als dynamische Werte, sondern als Text angezeigt|
|Visuelle Kennzeichnungen pro App|Nein|Empfohlen beim Verwenden von Variablen<br /><br />– Auf Clients werden Variablen nicht als dynamische Werte, sondern als Text angezeigt|
|Bedingungen und entsprechende Einstellungen <br /><br />Hinweise: Einschließlich automatischer und empfohlener Bezeichnungen samt QuickInfos|Nicht verfügbar|Nein|


## <a name="to-migrate-azure-information-protection-labels"></a>Migrieren von Azure Information Protection-Bezeichnungen

Verwenden Sie die folgenden Anweisungen, um Ihre Mandanten- und Azure Information Protection-Bezeichnungen zu migrieren und den neuen Speicher für einheitliche Bezeichnungen zu verwenden.

Sie müssen globaler Administrator sein, um Ihre Bezeichnungen zu migrieren.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wählen Sie im Menü **Verwalten** die Option **Einheitliche Bezeichnungen (Vorschau)** aus.

3. Wählen Sie auf dem Blatt **Azure Information Protection – Einheitliche Bezeichnungen** **Aktivieren** aus, und befolgen Sie die Onlineanweisungen.

Die Bezeichnungen, die erfolgreich migriert wurden, können nun von [Kunden, die einheitliche Bezeichnungen unterstützen](#clients-that-support-unified-labeling), verwendet werden. Zunächst müssen Sie jedoch diese Bezeichnungen im Security & Compliance Center veröffentlichen.

> [!IMPORTANT]
> Wenn Sie die Bezeichnungen außerhalb des Azure-Portals für Azure Information Protection-Clients bearbeiten, kehren Sie zu diesem Blatt **Azure Information Protection – Einheitliche Bezeichnung** zurück, und wählen Sie **Veröffentlichen**.

### <a name="clients-that-support-unified-labeling"></a>Clients, die einheitliche Bezeichnungen unterstützen

Folgende Clients unterstützen derzeit einheitliche Bezeichnungen:

- [Azure Information Protection-Client für einheitliche Bezeichnungen](./rms-client/unifiedlabelingclient-version-release-history.md) (Vorschau)

- Apps aus dem Office Insider-Programm. Weitere Informationen finden Sie in der Office-Dokumentation im Abschnitt [Wo ist das Feature heute verfügbar?](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?ad=US#bkmk_whereavailable).
    
- Clients von Softwareherstellern und Entwicklern, die das [Microsoft Information Protection SDK](https://docs.microsoft.com/azure/information-protection/develop/mip/mip-sdk-reference) verwenden.


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Ihren migrierten Bezeichnungen, die nun im Office 365 Security & Compliance Center konfiguriert und veröffentlicht werden können, finden Sie unter [Übersicht über Vertraulichkeitsbezeichnungen](/Office365/SecurityCompliance/sensitivity-labels).

Den Blogbeitrag mit der Ankündigung finden Sie hier: [Bekanntgabe der Verfügbarkeit der Verwaltung einheitlicher Bezeichnungen im Security & Compliance Center](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).