---
title: Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center – AIP
description: Migrieren Sie Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center für Clients, die einheitliche Bezeichnungen unterstützen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 03/14/2019
ms.topic: article
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: ed3c77df8da01a4b87b30875a315eac5c075b438
ms.sourcegitcommit: d716d3345a6a5adc63814dee28f7c01b55b96770
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57829058"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-the-office-365-security--compliance-center"></a>Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Dieses Feature befindet sich in der Vorschau und migriert Ihren Mandanten zu einer neuen Plattform. Die Migration kann nicht rückgängig gemacht werden. Die neue Plattform unterstützt einheitliche Bezeichnungen. Das bedeutet, dass die Bezeichnungen, die Sie erstellen und verwalten, von Clients und Diensten verwendet werden können, die [Microsoft Azure Information Protection-Lösungen](faqs.md#whats-the-difference-between-azure-information-protection-and-microsoft-information-protection) unterstützen.

Migrieren Sie Ihre Bezeichnungen aus dem Office 365 Security & Compliance Center, damit diese von [Clients, die einheitliche Bezeichnungen unterstützen](#clients-and-services-that-support-unified-labeling), als Office 365-Vertraulichkeitsbezeichnungen verwendet werden können. Der Azure Information Protection-Client lädt die Bezeichnungen mit ihrer Azure Information Protection-Richtlinie nach der Migration weiterhin aus dem Azure-Portal herunter. 

Bevor Sie sich die ausführlichen Anweisungen zum Migrieren Ihrer Bezeichnungen durchlesen, sehen Sie nach, ob die folgenden häufig gestellten Fragen hilfreich für Sie sind:

- [Was ist der Unterschied zwischen Bezeichnungen in Azure Information Protection und Office 365?](faqs.md#whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365)

- [Wann ist der richtige Zeitpunkt, um meine Bezeichnungen zu Office 365 zu migrieren?](faqs.md#when-is-the-right-time-to-migrate-my-labels-to-office-365)

- [Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?](faqs.md?#after-ive-migrated-my-labels-which-management-portal-do-i-use )

### <a name="important-information-about-administrative-roles"></a>Wichtige Informationen zu Administratorrollen

Die [Azure AD-Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) **Sicherheitsadministrator** und **Information Protection-Administrator** werden von der Plattform für einheitliche Bezeichnungen nicht unterstützt. Wenn diese Administratorrollen in Ihrer Organisation verwendet werden, fügen Sie vor der Migration Ihrer Bezeichnungen die Benutzer, die diese Rollen haben, dem **Complianceadministrator** oder den Rollengruppen für die **Organisationsverwaltung** für das Office 365 Security & Compliance Center hinzu. Alternativ können Sie für diese Benutzer eine neue Rollengruppe erstellen und dieser Gruppe entweder Rollen für die **Aufbewahrungsverwaltung** oder die **Organisationskonfiguration** hinzufügen. Anleitungen finden Sie unter [Gewähren von Benutzerzugriff auf das Office 365 Security & Compliance Center](https://docs.microsoft.com/office365/securitycompliance/grant-access-to-the-security-and-compliance-center).

Wenn Sie diesen Benutzern nicht über eine dieser Konfigurationen den Zugriff auf das Security & Compliance Center gewähren, können sie nach der Migration Ihrer Bezeichnungen nicht mehr auf die Bezeichnungen und Richtlinien im Azure-Portal zugreifen.

Globale Administratoren für Ihren Mandanten können nach der Migration Ihrer Bezeichnungen weiterhin Bezeichnungen und Richtlinien sowohl im Azure-Portal als auch im Security & Compliance Center verwalten.


## <a name="considerations-for-unified-labels"></a>Überlegungen zu einheitlichen Bezeichnungen

Beachten Sie die folgenden Änderungen und Überlegungen, bevor Sie Bezeichnungen migrieren:

- Nicht alle Clients unterstützen derzeit einheitliche Bezeichnungen. Stellen Sie sicher, dass Sie über [unterstützte Clients](#clients-and-services-that-support-unified-labeling) verfügen. Die Verwaltung erfolgt im Azure-Portal (Clients, die einheitliche Bezeichnungen nicht unterstützen) und im Security & Compliance Center (Clients, die einheitliche Bezeichnungen unterstützen).

- Wenn Sie gerade dabei sind, die gewünschten Bezeichnungen zu definieren und zu konfigurieren, empfehlen wir Ihnen, diesen Vorgang im Azure-Portal abzuschließen und die Bezeichnungen danach zu migrieren. Dadurch werden beim Migrationsvorgang doppelte Bezeichnungen vermieden, die dann im Security & Compliance Center bearbeitet werden müssen.

- Richtlinien, einschließlich Richtlinieneinstellungen und der entsprechenden Zugriffberechtigungen (bereichsbezogene Richtlinien), sowie alle erweiterten Clienteinstellungen werden nicht migriert. Für nicht migrierte Änderungen müssen Sie nach der Migration der Bezeichnungen die entsprechenden Optionen im Security & Compliance Center konfigurieren.
    
    Zur Optimierung der Benutzerfreundlichkeit empfehlen wir, die gleichen Bezeichnungen in den gleichen Bereichen im Security & Compliance Center zu veröffentlichen.

- Nicht alle Einstellungen einer migrierten Bezeichnung werden vom Security & Compliance Center unterstützt. Verwenden Sie die Tabelle im Abschnitt [Im Security & Compliance Center nicht unterstützte Bezeichnungseinstellungen](#label-settings-that-are-not-supported-in-the-security--compliance-center), um die entsprechenden Einstellungen sowie die empfohlene Vorgehensweise zu ermitteln.

- Schutzvorlagen:
    
    - Vorlagen, die einen cloudbasierten Schlüssel verwenden und Teil einer Bezeichnungskonfiguration sind, werden ebenfalls mit der Bezeichnung migriert. Andere Schutzvorlagen werden nicht migriert. 
    
    - Wenn Sie über Bezeichnungen verfügen, die für eine vordefinierte Vorlage konfiguriert sind, [konvertieren Sie diese Vorlagen in Bezeichnungen](configure-policy-templates.md#to-convert-templates-to-labels), bevor Sie Ihre Bezeichnungen migrieren. Diese Konfiguration verhindert die Bezeichnungsmigration nicht, wird jedoch im Security & Compliance Center nicht unterstützt.
    
    - Nach der Migration einer Bezeichnung mit cloudbasierten Schutzeinstellungen ist der Ergebnisbereich der Schutzvorlage der Bereich, der im Azure-Portal (bzw. unter Verwendung des ADDRM PowerShell-Moduls) und im Security & Compliance Center definiert ist. 

- Wenn Sie Ihre Bezeichnungen migrieren, zeigen die Migrationsergebnisse an, ob eine Bezeichnung **erstellt**, **aktualisiert** oder zum Vermeiden von Duplikaten **umbenannt** wurde:

    - Wenn Sie eine Bezeichnung erstellen, veröffentlichen Sie sie anschließend im Security & Compliance Center, um sie Anwendungen und Diensten zur Verfügung zu stellen.
    
    - Wenn Sie eine Bezeichnung umbenennen, bearbeiten Sie sie anschließend im Security & Compliance Center oder im Azure-Portal. 

- Das Azure-Portal zeigt nur den Anzeigenamen der jeweiligen Bezeichnung an, den Sie bearbeiten können. Das Security & Compliance Center zeigt sowohl den Anzeigenamen als auch den Bezeichnungsnamen an. Der Bezeichnungsname ist der ursprüngliche Name, den Sie beim Erstellen der Bezeichnung angeben. Diese Eigenschaft nutzt der Back-End-Dienst zur Identifizierung.

- Lokalisierte Zeichenfolgen für die Bezeichnungen werden nicht migriert. Sie müssen im Security & Compliance Center neue lokalisierte Zeichenfolgen für die migrierten Bezeichnungen definieren.

- Wenn Sie nach der Migration eine migrierte Bezeichnung im Azure-Portal bearbeiten, wird die entsprechende Änderung automatisch im Security & Compliance Center angezeigt. Wenn Sie jedoch eine migrierte Kennzeichnung im Security & Compliance Center bearbeiten, müssen Sie im Azure-Portal zum Blatt **Azure Information Protection – Einheitliche Bezeichnung** zurückkehren und **Veröffentlichen** auswählen. Diese zusätzliche Aktion ist erforderlich, damit die Clients von Azure Information Protection die Bezeichnungsänderungen übernehmen können.

### <a name="label-settings-that-are-not-supported-in-the-security--compliance-center"></a>Im Security & Compliance Center nicht unterstützte Bezeichnungseinstellungen

Anhand der folgenden Tabelle können Sie feststellen, welche Konfigurationseinstellungen einer migrierten Bezeichnung vom Security & Compliance Center nicht unterstützt werden. Wenn Sie über Bezeichnungen mit diesen Einstellungen verfügen, verwenden Sie nach der Migration den Verwaltungsleitfaden in der letzten Spalte, bevor Sie Ihre Bezeichnungen im Office 365 Security & Compliance Center veröffentlichen.

Azure Information Protection-Clients können alle aufgeführten Bezeichnungseinstellungen problemlos verwenden, weil sie die Bezeichnungen weiterhin aus dem Azure-Portal herunterladen.

|Bezeichnungskonfiguration|Unterstützt von Clients für einheitliche Bezeichnungen| Leitfaden für das Security & Compliance Center|
|-------------------|---------------------------------------------|-------------------------|
|Statusangabe „Aktiviert“/„Deaktiviert“<br /><br />Hinweise: Keine Synchronisierung im Security & Compliance Center |Nicht verfügbar|Das Äquivalent ist, ob die Bezeichnung veröffentlicht wurde oder nicht. |
|Die Bezeichnungsfarbe, die Sie aus der Liste auswählen oder mit einem RGB-Code angeben |Ja|Keine Konfigurationsoption für Bezeichnungsfarben. Stattdessen können Sie Bezeichnungsfarben im Azure-Portal konfigurieren.|
|Cloudbasierter Schutz oder HYOK-Schutz (Hold Your Own Key) mit vordefinierter Vorlage |Nein|Keine Konfigurationsoption für vordefinierte Vorlagen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.|
|Cloudbasierter Schutz mit benutzerdefinierten Berechtigungen für Word, Excel und PowerPoint |Nein|Keine Konfigurationsoption für benutzerdefinierte Berechtigungen für diese Office-Anwendungen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.|
|HYOK-Schutz mit benutzerdefinierten Berechtigungen für Outlook („Nicht weiterleiten“) |Nein|Keine Konfigurationsoption für HYOK. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.|
|Entfernen von Schutz |Nein|Keine Konfigurationsoption, um Schutz zu entfernen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.<br /><br /> Wenn Sie diese Bezeichnung mit dieser Konfiguration veröffentlichen, wird der Schutz entfernt, wenn dieser zuvor von einer Bezeichnung angewendet wurde. Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt der Schutz bestehen.|
|Benutzerdefinierte Schriftart und -farbe (RGB-Code) für optische Kennzeichnungen (Kopfzeile, Fußzeile, Wasserzeichen)|Ja|Die Konfiguration für optische Kennzeichnungen ist begrenzt auf eine Farb- und Schriftgradliste. Sie können diese Bezeichnung ohne Änderungen veröffentlichen, obwohl Sie sich die konfigurierten Werte im Security & Compliance Center nicht ansehen können. <br /><br />Wenn Sie diese Optionen ändern möchten, verwenden Sie dazu das Azure-Portal. Sie sollten jedoch in Betracht ziehen, die Farbe in eine der im Security & Compliance Center aufgelisteten Optionen zu ändern, um die Verwaltung zu vereinfachen.|
|Visuelle Kennzeichnungsvariablen (Kopfzeile, Fußzeile)|Nein|Wenn Sie diese Bezeichnung ohne Änderungen veröffentlichen, werden Variablen auf Clients als Text und nicht als dynamische Werte angezeigt. Bearbeiten Sie die Zeichenfolgen, um die Variablen zu entfernen, bevor Sie die Bezeichnung veröffentlichen.|
|Visuelle Kennzeichnungen pro App|Nein|Wenn Sie diese Bezeichnung ohne Änderungen veröffentlichen, werden die Anwendungsvariablen auf Clients in allen Anwendungen als Text angezeigt und zeigen nicht Ihre Textzeichenfolgen auf ausgewählten Anwendungen an. Veröffentlichen Sie diese Bezeichnung nur, wenn Sie sich für alle Anwendungen eignet, und bearbeiten Sie die Zeichenfolgen, um die Anwendungsvariablen zu entfernen.|
|Bedingungen und entsprechende Einstellungen <br /><br />Hinweise: Einschließlich automatischer und empfohlener Bezeichnungen samt QuickInfos|Nicht verfügbar|Konfigurieren Sie Ihre Bedingungen neu, indem Sie die automatische Bezeichnung als eine von den Bezeichnungseinstellungen eigenständige Konfiguration verwenden.|


## <a name="to-migrate-azure-information-protection-labels"></a>Migrieren von Azure Information Protection-Bezeichnungen

Verwenden Sie die folgenden Anweisungen, um Ihre Mandanten- und Azure Information Protection-Bezeichnungen zu migrieren und den neuen Speicher für einheitliche Bezeichnungen zu verwenden.

Sie müssen globaler Administrator sein, um Ihre Bezeichnungen zu migrieren.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wählen Sie im Menü **Verwalten** die Option **Einheitliche Bezeichnungen (Vorschau)** aus.

3. Wählen Sie auf dem Blatt **Azure Information Protection – Einheitliche Bezeichnungen** **Aktivieren** aus, und befolgen Sie die Onlineanweisungen.

Die Bezeichnungen, die erfolgreich migriert wurden, können nun von [Clients und Diensten, die einheitliche Bezeichnungen unterstützen](#clients-and-services-that-support-unified-labeling), verwendet werden. Zunächst müssen Sie jedoch diese Bezeichnungen im Security & Compliance Center veröffentlichen.

> [!IMPORTANT]
> Wenn Sie die Bezeichnungen außerhalb des Azure-Portals für Azure Information Protection-Clients bearbeiten, kehren Sie zu diesem Blatt **Azure Information Protection – Einheitliche Bezeichnung** zurück, und wählen Sie **Veröffentlichen**.

### <a name="clients-and-services-that-support-unified-labeling"></a>Clients und Dienste, die einheitliche Bezeichnungen unterstützen

Wenn Sie herausfinden möchten, ob die von Ihnen verwendeten Clients und Dienste einheitliche Bezeichnungen unterstützen, können Sie in den jeweiligen Dokumentationen nachlesen, ob diese Vertraulichkeitsbezeichnungen verwenden können, die im Office 365 Security & Compliance Center veröffentlicht wurden. 

##### <a name="clients-that-currently-support-unified-labeling-include"></a>Folgende Clients unterstützen derzeit einheitliche Bezeichnungen:

- [Azure Information Protection-Client für einheitliche Bezeichnungen](./rms-client/unifiedlabelingclient-version-release-history.md) (Vorschau)

- Apps von Office, die sich in verschiedenen Stadien der Verfügbarkeit befinden. Weitere Informationen finden Sie im Abschnitt **Wo ist das Feature heute verfügbar?** unter [Anwenden von Vertraulichkeits-Beschriftungen auf Ihre Dokumente und E-Mails in Office](https://support.office.com/en-us/article/apply-sensitivity-labels-to-your-documents-and-email-within-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) in der Office-Dokumentation.
    
- Apps von Softwarevertreibern und -herstellern, die das [Microsoft Azure Information Protection SDK](https://docs.microsoft.com/en-us/information-protection/develop/overview) verwenden.

##### <a name="services-that-currently-support-unified-labeling-include"></a>Folgende Dienste unterstützen derzeit einheitliche Bezeichnungen:

- Windows Defender Advanced Threat Protection

- Microsoft Cloud App Security
    
    Dieser Dienst unterstützt Bezeichnungen sowohl vor der Migration in den einheitlichen Bezeichnungsspeicher, als auch nach der Migration, und verwendet dabei die folgende Logik:
    
    - Wenn es im Office 365 Security & Compliance Center dieselben Bezeichnungen gibt wie im Azure-Portal: Einheitliche Bezeichnungen werden aus dem Office 365 Security & Compliance Center abgerufen. Wenn Sie diese Bezeichnungen in Cloud App Security auswählen möchten, muss mindestens eine Bezeichnung für mindestens einen Benutzer veröffentlicht worden sein.
    
    - Wenn es im Office 365 Security & Compliance Center nicht dieselben Bezeichnungen gibt wie im Azure-Portal: Einheitliche Bezeichnungen werden vom Office 365 Security & Compliance Center nicht verwendet. Stattdessen werden Bezeichnungen aus dem Azure-Portal abgerufen.

- Dienste von Softwarevertreibern und -herstellern, die das [Microsoft Azure Information Protection SDK](https://docs.microsoft.com/en-us/information-protection/develop/overview) verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Ihren migrierten Bezeichnungen, die nun im Office 365 Security & Compliance Center konfiguriert und veröffentlicht werden können, finden Sie unter [Übersicht über Vertraulichkeitsbezeichnungen](/Office365/SecurityCompliance/sensitivity-labels).

Den Blogbeitrag mit der Ankündigung finden Sie hier: [Bekanntgabe der Verfügbarkeit der Verwaltung einheitlicher Bezeichnungen im Security & Compliance Center](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).
