---
title: Migrieren von Azure Information Protection-Bezeichnungen zu Office 365 – AIP
description: Migrieren Sie Azure Information Protection-Bezeichnungen zu Office 365-Vertraulichkeitsbezeichnungen für Clients und Dienste, die einheitliche Bezeichnungen unterstützen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 05/29/2019
ms.topic: article
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: a9cc458bb22c4b2c76b7aa80b58434a213ec5af1
ms.sourcegitcommit: e366a19300be4165da05ec7ee592f883c467bb51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66269750"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-office-365-sensitivity-labels"></a>Migrieren von Azure Information Protection-Bezeichnungen zu Office 365-Vertraulichkeitsbezeichnungen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Migrieren Sie Ihre Bezeichnungen in Azure Information Protection, damit Sie sie verwenden können, als vertraulichkeitsbezeichnungen von [Clients und Diensten, die Unterstützung für die einheitliche Bezeichnung](#clients-and-services-that-support-unified-labeling).

Klicken Sie nach der Migration verwalten Sie und veröffentlichen Sie diese Bezeichnungen über die Office 365 Security & Compliance Center oder das Microsoft 365-Security-Center und Microsoft 365 Compliance Center. Diese Bezeichnungen können von der Azure Information Protection unified bezeichnungs-Client verwendet werden. Wenn Sie fortfahren, den Azure Information Protection-Client verwenden, wird dieser Client zum Herunterladen von Bezeichnungen mit der Azure Information Protection-Richtlinie aus dem Azure-Portal fortgesetzt.

Bevor Sie sich die ausführlichen Anweisungen zum Migrieren Ihrer Bezeichnungen durchlesen, sehen Sie nach, ob die folgenden häufig gestellten Fragen hilfreich für Sie sind:

- [Was ist der Unterschied zwischen Bezeichnungen in Azure Information Protection und Office 365?](faqs.md#whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365)

- [Wann ist der richtige Zeitpunkt, um meine Bezeichnungen zu Office 365 zu migrieren?](faqs.md#when-is-the-right-time-to-migrate-my-labels-to-office-365)

- [Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?](faqs.md?#after-ive-migrated-my-labels-which-management-portal-do-i-use )

### <a name="important-information-about-administrative-roles"></a>Wichtige Informationen zu Administratorrollen

Die [Azure AD-Rolle](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) von **Azure Information Protection-Administrator** (früher **Information Protection-Administrator**) wird nicht unterstützt, durch die einheitliche Kennzeichnung die Plattform. Wenn diese administrative Rolle in Ihrer Organisation verwendet wird, fügen Sie die Benutzer, die über diese Rolle verfügen, den Azure AD-Rollen **Sicherheitsadministrator** oder **Complianceadministrator** hinzu, bevor Sie die Bezeichnungen migrieren. Eine Anleitung zu diesem Schritt finden Sie unter [Gewähren von Benutzerzugriff auf das Office 365 Security & Compliance Center](https://docs.microsoft.com/office365/securitycompliance/grant-access-to-the-security-and-compliance-center). Diese Rollen können auch im Azure AD-Portal, Microsoft 365 Security Center und Microsoft 365 Compliance Center zugewiesen werden.

Statt Rollen zu verwenden, können Sie auch im jeweiligen Admin Center eine neue Rollengruppe für diese Benutzer erstellen und dieser Gruppe die Rolle **Administrator für Vertraulichkeitsbezeichnungen** oder **Organisationskonfiguration** zuweisen.

Wenn Sie diesen Benutzern nicht über eine dieser Konfigurationen Zugriff auf die Admin Centers gewähren, sind die Benutzer nach der Migration Ihrer Bezeichnungen nicht mehr in der Lage, Azure Information Protection im Azure-Portal zu konfigurieren.

Globale Administratoren für Ihren Mandanten können nach der Migration Ihrer Bezeichnungen weiterhin Bezeichnungen und Richtlinien sowohl im Azure-Portal als auch in den Admin-Centers verwalten.


## <a name="considerations-for-unified-labels"></a>Überlegungen zu einheitlichen Bezeichnungen

Beachten Sie die folgenden Änderungen und Überlegungen, bevor Sie Bezeichnungen migrieren:

- Nicht alle Clients unterstützen derzeit einheitliche Bezeichnungen. Stellen Sie sicher, dass Sie über [unterstützte Clients](#clients-and-services-that-support-unified-labeling) verfügen. Die Verwaltung erfolgt im Azure-Portal (Clients, die einheitliche Bezeichnungen nicht unterstützen) und in den Admin-Centers (Clients, die einheitliche Bezeichnungen unterstützen).

- Richtlinien, einschließlich Richtlinieneinstellungen und der entsprechenden Zugriffberechtigungen (bereichsbezogene Richtlinien), sowie alle erweiterten Clienteinstellungen werden nicht migriert. Für nicht migrierte Änderungen müssen Sie nach der Migration der Bezeichnungen die entsprechenden Optionen in den Admin-Centers konfigurieren.
    
    Zur Optimierung der Benutzerfreundlichkeit empfehlen wir, die gleichen Bezeichnungen in den gleichen Bereichen in den Admin-Centers zu veröffentlichen.

- Nicht alle Einstellungen einer migrierten Bezeichnung werden von den Admin-Centers unterstützt. Verwenden Sie die Tabelle im Abschnitt [In den Admin-Centers nicht unterstützte Bezeichnungseinstellungen](#label-settings-that-are-not-supported-in-the-admin-centers), um die entsprechenden Einstellungen sowie die empfohlene Vorgehensweise zu ermitteln.

- Schutzvorlagen:
    
    - Vorlagen, die einen cloudbasierten Schlüssel verwenden und Teil einer Bezeichnungskonfiguration sind, werden ebenfalls mit der Bezeichnung migriert. Andere Schutzvorlagen werden nicht migriert. 
    
    - Wenn Sie über Bezeichnungen verfügen, die für eine vordefinierte Vorlage konfiguriert sind, können Sie diese Bezeichnungen bearbeiten und die Option **Berechtigungen festlegen** auswählen, um die gleichen Schutzeinstellungen wie in Ihrer Vorlage zu konfigurieren. Bezeichnungen mit vordefinierten Vorlagen verhindern die Bezeichnungsmigration nicht, diese Bezeichnungskonfiguration wird jedoch in den Admin-Centers nicht unterstützt.
        
        Tipp: Es kann nützlich sein, für die erneute Konfigurierung dieser Bezeichnungen zwei Browserfenster zu öffnen: In einem Fenster wählen Sie die Schaltfläche **Vorlage bearbeiten** für die Bezeichnung aus, um die Schutzeinstellungen anzuzeigen, und im anderen Fenster konfigurieren Sie die gleichen Einstellungen beim Auswählen von **Berechtigungen festlegen**.
    
    - Nach der Migration einer Bezeichnung mit cloudbasierten Schutzeinstellungen ist der Ergebnisbereich der Schutzvorlage der Bereich, der im Azure-Portal (bzw. unter Verwendung des ADDRM PowerShell-Moduls) und in den Admin-Centers definiert ist. 

- Wenn Sie Ihre Bezeichnungen migrieren, zeigen die Migrationsergebnisse an, ob eine Bezeichnung **erstellt**, **aktualisiert** oder zum Vermeiden von Duplikaten **umbenannt** wurde:

    - Wenn Sie eine Bezeichnung erstellen, veröffentlichen Sie sie anschließend in einem der Admin-Centers, um sie Anwendungen und Diensten zur Verfügung zu stellen.
    
    - Wenn Sie eine Bezeichnung umbenennen, bearbeiten Sie sie anschließend in einem der Admin-Centers oder im Azure-Portal.

- Das Azure-Portal zeigt nur den Anzeigenamen der jeweiligen Bezeichnung an, den Sie bearbeiten können. Die Admin-Centers zeigen sowohl den Anzeigenamen als auch den Bezeichnungsnamen an. Der Bezeichnungsname ist der ursprüngliche Name, den Sie beim Erstellen der Bezeichnung angeben. Diese Eigenschaft nutzt der Back-End-Dienst zur Identifizierung.

- Lokalisierte Zeichenfolgen für die Bezeichnungen werden nicht migriert. Sie müssen in den Admin-Centers neue lokalisierte Zeichenfolgen für die migrierten Bezeichnungen definieren.

- Wenn Sie nach der Migration eine migrierte Bezeichnung im Azure-Portal bearbeiten, wird die entsprechende Änderung automatisch in den Admin-Centers angezeigt. Wenn Sie jedoch eine migrierte Kennzeichnung in einem der Admin-Centers bearbeiten, müssen Sie im Azure-Portal zum Blatt **Azure Information Protection – Einheitliche Bezeichnung** zurückkehren und **Veröffentlichen** auswählen. Diese zusätzliche Aktion ist erforderlich, damit die Clients von Azure Information Protection die Bezeichnungsänderungen übernehmen können.

### <a name="label-settings-that-are-not-supported-in-the-admin-centers"></a>In den Admin-Centers nicht unterstützte Bezeichnungseinstellungen

Anhand der folgenden Tabelle können Sie feststellen, welche Konfigurationseinstellungen einer migrierten Bezeichnung vom Office 365 Security & Compliance Center, dem Microsoft 365 Security Center, oder dem Microsoft Compliance Center nicht unterstützt werden. Wenn Sie über Bezeichnungen mit diesen Einstellungen verfügen, verwenden Sie nach der Migration den Verwaltungsleitfaden in der letzten Spalte, bevor Sie Ihre Bezeichnungen in einem der Admin-Centers veröffentlichen.

Wenn Sie nicht sicher sind, wie Ihre Bezeichnungen konfiguriert sind, zeigen Sie die zugehörigen Einstellungen im Azure-Portal an. Eine Anleitung zu diesem Schritt finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Azure Information Protection-Clients können alle aufgeführten Bezeichnungseinstellungen problemlos verwenden, weil sie die Bezeichnungen weiterhin aus dem Azure-Portal herunterladen.

|Bezeichnungskonfiguration|Unterstützt von Clients für einheitliche Bezeichnungen| Leitfaden für die Admin-Centers|
|-------------------|---------------------------------------------|-------------------------|
|Statusangabe „Aktiviert“/„Deaktiviert“<br /><br />Hinweise: Nicht mit den Admin-Centers synchronisiert |Nicht verfügbar|Das Äquivalent ist, ob die Bezeichnung veröffentlicht wurde oder nicht. |
|Die Bezeichnungsfarbe, die Sie aus der Liste auswählen oder mit einem RGB-Code angeben |Ja|Keine Konfigurationsoption für Bezeichnungsfarben. Stattdessen können Sie Bezeichnungsfarben im Azure-Portal konfigurieren.|
|Cloudbasierter Schutz oder HYOK-Schutz (Hold Your Own Key) mit vordefinierter Vorlage |Nein|Keine Konfigurationsoption für vordefinierte Vorlagen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.|
|Cloudbasierter Schutz mit benutzerdefinierten Berechtigungen für Word, Excel und PowerPoint |Nein|Keine Konfigurationsoption für benutzerdefinierte Berechtigungen für diese Office-Anwendungen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen. Wenn Sie dies tun, finden Sie die Ergebnisse der Anwendung der Bezeichnung in der [folgenden Tabelle](#comparing-the-behavior-of-protection-settings-for-a-label).|
|HYOK-Schutz mit benutzerdefinierten Berechtigungen für Outlook („Nicht weiterleiten“) |Nein|Keine Konfigurationsoption für HYOK. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen. Wenn Sie dies tun, finden Sie die Ergebnisse der Anwendung der Bezeichnung in der [folgenden Tabelle](#comparing-the-behavior-of-protection-settings-for-a-label).|
|Entfernen von Schutz |Nein|Keine Konfigurationsoption, um Schutz zu entfernen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.<br /><br /> Wenn Sie das Label veröffentlichen, wenn es angewendet wird, wird Schutz entfernt werden, wenn sie bereits von einer Bezeichnung angewendet wurde. Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt der Schutz bestehen.|
|Benutzerdefinierte Schriftart und -farbe (RGB-Code) für optische Kennzeichnungen (Kopfzeile, Fußzeile, Wasserzeichen)|Ja|Die Konfiguration für optische Kennzeichnungen ist begrenzt auf eine Farb- und Schriftgradliste. Sie können diese Bezeichnung ohne Änderungen veröffentlichen, obwohl Sie sich die konfigurierten Werte in den Admin-Centers nicht ansehen können. <br /><br />Wenn Sie diese Optionen ändern möchten, verwenden Sie dazu das Azure-Portal. Sie sollten jedoch in Betracht ziehen, die Farbe in eine der in den Admin-Centers aufgelisteten Optionen zu ändern, um die Verwaltung zu vereinfachen.|
|Visuelle Kennzeichnungsvariablen (Kopfzeile, Fußzeile)|Nein|Wenn Sie diese Bezeichnung ohne Änderungen veröffentlichen, werden Variablen auf Clients als Text und nicht als dynamische Werte angezeigt. Bearbeiten Sie die Zeichenfolgen, um die Variablen zu entfernen, bevor Sie die Bezeichnung veröffentlichen.|
|Visuelle Kennzeichnungen pro App|Nein|Wenn Sie diese Bezeichnung ohne Änderungen veröffentlichen, werden die Anwendungsvariablen auf Clients in allen Anwendungen als Text angezeigt und zeigen nicht Ihre Textzeichenfolgen auf ausgewählten Anwendungen an. Veröffentlichen Sie diese Bezeichnung nur, wenn Sie sich für alle Anwendungen eignet, und bearbeiten Sie die Zeichenfolgen, um die Anwendungsvariablen zu entfernen.|
|Bedingungen und entsprechende Einstellungen <br /><br />Hinweise: Einschließlich automatischer und empfohlener Bezeichnungen samt QuickInfos|Nicht verfügbar|Konfigurieren Sie Ihre Bedingungen neu, indem Sie die automatische Bezeichnung als eine von den Bezeichnungseinstellungen eigenständige Konfiguration verwenden.|

### <a name="comparing-the-behavior-of-protection-settings-for-a-label"></a>Vergleichen des Verhaltens von Schutzeinstellungen für eine Bezeichnung

Verwenden Sie in der folgende Tabelle, um zu identifizieren, wie eine Einstellung für den gleichen Schutz für eine Bezeichnung anders verhält sich je nachdem, ob sie vom Azure Information Protection-Client die einheitliche Bezeichnung Azure Information Protection-Client oder von Office-apps, die verwendet wird Bezeichnung integriert (auch bekannt als "native Office 

Wenn Sie nicht sicher sind, wie Ihre Schutzeinstellungen konfiguriert sind, zeigen Sie die zugehörigen Einstellungen auf dem Blatt **Schutz** im Azure-Portal an. Eine Anleitung zu diesem Schritt finden Sie unter [So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen](configure-policy-protection.md#to-configure-a-label-for-protection-settings).

Schutzeinstellungen, die sich genauso verhalten, werden in der Tabelle nicht aufgeführt, mit den folgenden Ausnahmen:
- Wenn Sie Office-Apps mit integrierter Bezeichnungsfunktion verwenden, werden Bezeichnungen im Datei-Explorer nicht angezeigt, es sei denn, Sie installieren auch den Azure Information Protection Unified Labeling-Client.
- Wenn Sie Office-Apps mit integrierter Bezeichnungsfunktion verwenden, bleibt dieser Schutz bestehen, wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde [[1]](#footnote-1).

|Schutzeinstellung für eine Bezeichnung |Azure Information Protection-Client|Azure Information Protection-Client für einheitliche Bezeichnungen| Office-Apps mit integrierter Bezeichnungsfunktion
|-------------------|-----------------------------------|-----------------------------------------------------------|---------------
|Azure (Cloudschlüssel) mit benutzerdefinierten Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer:| Wird in Word, Excel, PowerPoint und im Datei-Explorer angezeigt <br /><br /> Wenn die Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> - Benutzer werden nach benutzerdefinierten Berechtigungen gefragt, die dann als Schutz mit einem cloudbasierten Schlüssel angewendet werden| Wird nicht angezeigt |Wird in Word, Excel, PowerPoint und Outlook angezeigt: <br /><br /> Wenn die Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – Benutzer werden nicht nach benutzerdefinierten Berechtigungen gefragt, und es wird kein Schutz angewendet <br /><br /> – Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1)|
|HYOK (AD RMS) mit Vorlage:| Wird in Word, Excel, PowerPoint, Outlook und im Datei-Explorer angezeigt<br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– HYOK-Schutz wird auf Dokumente und E-Mails angewendet | Wird in Word, Excel, PowerPoint, Outlook und im Datei-Explorer angezeigt  <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen |Wird in Word, Excel, PowerPoint und Outlook angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1) |
|HYOK (AD RMS) mit benutzerdefinierten Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer:| Wird in Word, Excel, PowerPoint und im Datei-Explorer angezeigt<br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – HYOK-Schutz wird auf Dokumente und E-Mails angewendet| Wird in Word, Excel und PowerPoint angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen|Wird in Word, Excel und PowerPoint angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen |
|HYOK (AD RMS) mit benutzerdefinierten Berechtigungen für Outlook:|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br />– „Nicht weiterleiten“ mit HYOK-Schutz wird auf E-Mails angewendet|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1)|

###### <a name="footnote-1"></a>Fußnote 1

In Outlook für Mac wird der Schutz mit einer Ausnahme beibehalten: Wenn eine E-Mail mit der Option „Nur verschlüsseln“ geschützt wurde, wird dieser Schutz entfernt.


###### <a name="footnote-2"></a>Fußnote 2

Der Schutz wird entfernt, wenn der Benutzer über ein Nutzungsrecht oder eine Nutzungsrolle verfügt, wovon diese Aktion unterstützt wird:
- Das [Nutzungsrecht](configure-usage-rights.md#usage-rights-and-descriptions) „Exportieren“ oder „Vollzugriff“.
- Die Rolle [Rights Management-Aussteller oder Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) oder [Administrator](configure-super-users.md).

Wenn der Benutzer über keine/s dieser Nutzungsrechte oder Nutzungsrollen verfügt, wird die Bezeichnung nicht angewendet, und der ursprüngliche Schutz wird beibehalten.


## <a name="to-migrate-azure-information-protection-labels"></a>Migrieren von Azure Information Protection-Bezeichnungen

Verwenden Sie die folgenden Anweisungen, um Ihre Mandanten- und Azure Information Protection-Bezeichnungen zu migrieren und den neuen Speicher für einheitliche Bezeichnungen zu verwenden.

Sie müssen als Compliance-Administrator, Sicherheitsadministrator oder globaler Administrator, migrieren Sie Ihre Bezeichnungen werden.

> [!NOTE]
> Wenn Sie die Retention-Bezeichnungen und DLP-Richtlinien für Office 365 verfügen, empfehlen wir, dass Sie die Kompatibilität der Rolle "Administrator" oder "globaler Administrator", migrieren Sie Ihre Bezeichnungen verfügen.
> 
> Administratoren für die Sicherheit haben Zugriff auf die datenaufbewahrung Bezeichnungen oder Daten DLP-Richtlinien, also wenn eines dieser sind und sie haben den gleichen Namen wie Ihre Azure Information Protection-Bezeichnungen, während der Migration nicht bis Sie abgeschlossen, manuell benennen Sie eine nicht die Duplikate. Wenn Sie eine der anderen Rollen verfügen, kann jedoch während der Migration die Azure Information Protection-Bezeichnung, umbenennen, damit die Migration abgeschlossen werden kann.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Von der **verwalten** Menüoption wählen **einheitliche Bezeichnungen**.

3. Wählen Sie auf dem Blatt **Azure Information Protection – Einheitliche Bezeichnungen** **Aktivieren** aus, und befolgen Sie die Onlineanweisungen.
    
    Wenn die Option zum Aktivieren nicht verfügbar ist, aktivieren Sie **Status einheitlicher Bezeichnungen**: Wenn **Aktiviert** angezeigt wird, verwendet Ihr Mandant bereits den einheitlichen Bezeichnungsspeicher, sodass keine Bezeichnungen migriert werden müssen.

Die Bezeichnungen, die erfolgreich migriert wurden, können nun von [Clients und Diensten, die einheitliche Bezeichnungen unterstützen](#clients-and-services-that-support-unified-labeling), verwendet werden. Zunächst müssen Sie jedoch diese Bezeichnungen in einem der Admin-Centers veröffentlichen: Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center.

> [!IMPORTANT]
> Wenn Sie die Bezeichnungen außerhalb des Azure-Portals für Azure Information Protection-Clients bearbeiten, kehren Sie zu diesem Blatt **Azure Information Protection – Einheitliche Bezeichnung** zurück, und wählen Sie **Veröffentlichen**.

### <a name="clients-and-services-that-support-unified-labeling"></a>Clients und Dienste, die einheitliche Bezeichnungen unterstützen

Wenn Sie herausfinden möchten, ob die von Ihnen verwendeten Clients und Dienste einheitliche Bezeichnungen unterstützen, können Sie in den jeweiligen Dokumentationen nachlesen, ob diese Vertraulichkeitsbezeichnungen verwenden können, die in einem der Admin-Centers veröffentlicht wurden. Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center. 

##### <a name="clients-that-currently-support-unified-labeling-include"></a>Folgende Clients unterstützen derzeit einheitliche Bezeichnungen:

- Die [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](./rms-client/unifiedlabelingclient-version-release-history.md)

- Apps von Office, die sich in verschiedenen Stadien der Verfügbarkeit befinden. Weitere Informationen finden Sie im Abschnitt **Wo ist das Feature heute verfügbar?** unter [Anwenden von Vertraulichkeits-Beschriftungen auf Ihre Dokumente und E-Mails in Office](https://support.office.com/en-us/article/apply-sensitivity-labels-to-your-documents-and-email-within-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) in der Office-Dokumentation.
    
- Apps von Softwarevertreibern und -herstellern, die das [Microsoft Azure Information Protection SDK](https://docs.microsoft.com/en-us/information-protection/develop/overview) verwenden.

##### <a name="services-that-currently-support-unified-labeling-include"></a>Folgende Dienste unterstützen derzeit einheitliche Bezeichnungen:

- Microsoft Defender Advanced Threat Protection

- Microsoft Cloud App Security
    
    Dieser Dienst unterstützt Bezeichnungen sowohl vor der Migration in den einheitlichen Bezeichnungsspeicher, als auch nach der Migration, und verwendet dabei die folgende Logik:
    
    - Wenn die Admin-Centers die gleichen Bezeichnungen wie die im Azure-Portal haben: Einheitliche Bezeichnungen werden über die Admin-Centers abgerufen. Wenn Sie diese Bezeichnungen in Cloud App Security auswählen möchten, muss mindestens eine Bezeichnung für mindestens einen Benutzer veröffentlicht worden sein.
    
    - Wenn die Admin-Centers nicht die gleichen Bezeichnungen wie die im Azure-Portal haben: Einheitliche Bezeichnungen werden von den Admin-Centers nicht verwendet. Stattdessen werden Bezeichnungen aus dem Azure-Portal abgerufen.

- Dienste von Softwarevertreibern und -herstellern, die das [Microsoft Azure Information Protection SDK](https://docs.microsoft.com/en-us/information-protection/develop/overview) verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Ihren migrierten Bezeichnungen, die nun in einem der Admin-Centers konfiguriert und veröffentlicht werden können, finden Sie unter [Übersicht über Vertraulichkeitsbezeichnungen](/Office365/SecurityCompliance/sensitivity-labels).

Wenn Sie nicht bereits geschehen, installieren Sie die einheitlichen Bezeichnung Azure Information Protection-Client. Informationen zur Freigabe ein Administratorhandbuch und Benutzerhandbuch, finden Sie unter [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](./rms-client/aip-clientv2.md).
