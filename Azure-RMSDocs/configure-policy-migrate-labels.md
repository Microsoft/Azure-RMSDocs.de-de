---
title: Migrieren von Azure Information Protection Bezeichnungen zu vereinheitlichten Vertraulichkeits Bezeichnungen-aip
description: Migrieren Sie Azure Information Protection Bezeichnungen zu Unified Sensitivität-Bezeichnungen für Clients und Dienste, die Microsoft Information Protection Framework unterstützen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/09/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: labelmigrate
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: f124e6c1bbf8b77760744885492e1c5663d02443
ms.sourcegitcommit: 0f76655985b49b4b8868d5f8893e20978f4dc4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97747119"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-unified-sensitivity-labels"></a>Vorgehensweise beim Migrieren von Azure Information Protection Bezeichnungen zu vereinheitlichten Vertraulichkeits Bezeichnungen

> **Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
> **Relevant für** [Azure Information Protection Clients für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Migrieren Sie Azure Information Protection Bezeichnungen zur vereinheitlichten Bezeichnung, sodass Sie Sie als Vertraulichkeits Bezeichnungen von [Clients und Diensten verwenden können, die vereinheitlichte Bezeichnungen unterstützen](#clients-and-services-that-support-unified-labeling).

> [!NOTE]
> Wenn Ihr Azure Information Protection-Abonnement recht neu ist, müssen Sie möglicherweise keine Bezeichnungen migrieren, da sich Ihr Mandant bereits auf der Unified Label-Plattform befindet. Weitere Informationen finden Sie unter [wie kann ich feststellen, ob mein Mandant auf der Unified-Beschriftungs Plattform ist?](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)

Nachdem Sie Ihre Bezeichnungen migriert haben, können Sie keinen Unterschied zum Azure Information Protection klassischen Client sehen, da dieser Client weiterhin die Bezeichnungen mit der Azure Information Protection Richtlinie aus dem Azure-Portal herunterlädt. Sie können die Bezeichnungen nun jedoch mit dem Azure Information Protection Unified Label-Client und anderen Clients und Diensten verwenden, die Vertraulichkeits Bezeichnungen verwenden.

Bevor Sie die Anweisungen zum Migrieren ihrer Bezeichnungen lesen, finden Sie möglicherweise die folgenden häufig gestellten Fragen:

- [Worin besteht der Unterschied zwischen Bezeichnungen in Microsoft 365 und Bezeichnungen in Azure Information Protection?](faqs.md#whats-the-difference-between-labels-in-microsoft-365-and-labels-in-azure-information-protection)

- [Wann ist der richtige Zeitpunkt für die Migration meiner Bezeichnungen?](faqs.md#when-is-the-right-time-to-migrate-my-labels)

- [Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?](faqs.md?#after-ive-migrated-my-labels-which-management-portal-do-i-use )

### <a name="administrative-roles-that-support-the-unified-labeling-platform"></a>Administrative Rollen zur Unterstützung der Unified-Bezeichnung-Plattform

Wenn Sie Administrator Rollen für die delegierte Administration in Ihrer Organisation verwenden, müssen Sie möglicherweise einige Änderungen an der Unified-Bezeichnung-Plattform vornehmen:

Die [Azure AD Rolle](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) **Azure Information Protection Administrators** (ehemals **Information Protection Administrator**) wird von der Unified-Beschriftungs Plattform nicht unterstützt. Wenn diese administrative Rolle in Ihrer Organisation für die Verwaltung von Azure Information Protection verwendet wird, fügen Sie die Benutzer mit dieser Rolle den Azure AD Rollen des Kompatibilitäts **Administrators**, des Kompatibilitäts **Daten Administrators** oder des **Sicherheits Administrators** hinzu. Wenn Sie bei diesem Schritt Hilfe benötigen, finden Sie weitere Informationen unter [Benutzer Zugriff auf das Microsoft 365 Security & Compliance Center](/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center). Diese Rollen können auch im Azure AD-Portal, Microsoft 365 Security Center und Microsoft 365 Compliance Center zugewiesen werden.

Statt Rollen zu verwenden, können Sie auch im jeweiligen Admin Center eine neue Rollengruppe für diese Benutzer erstellen und dieser Gruppe die Rolle **Administrator für Vertraulichkeitsbezeichnungen** oder **Organisationskonfiguration** zuweisen.

Wenn Sie diesen Benutzern nicht über eine dieser Konfigurationen Zugriff auf die Admin Centers gewähren, sind die Benutzer nach der Migration Ihrer Bezeichnungen nicht mehr in der Lage, Azure Information Protection im Azure-Portal zu konfigurieren.

Globale Administratoren für Ihren Mandanten können nach der Migration Ihrer Bezeichnungen weiterhin Bezeichnungen und Richtlinien sowohl im Azure-Portal als auch in den Admin-Centers verwalten.

## <a name="before-you-begin"></a>Voraussetzungen

Die Bezeichnung "Bezeichnung" hat viele Vorteile, ist jedoch nicht rückgängig. Stellen Sie vor der Migration sicher, dass Sie die folgenden Änderungen und Überlegungen beachten:

- [Client Unterstützung für vereinheitlichte Bezeichnung](#client-support-for-unified-labeling)
- [Richtlinienkonfiguration](#policy-configuration)
- [Schutzvorlagen](#protection-templates)
- [Anzeigen Amen](#display-names)
- [Lokalisierte Zeichen folgen in Bezeichnungen](#localized-strings-in-labels)
- [Bearbeiten von migrierten Bezeichnungen in admin Centers](#editing-migrated-labels-in-the-admin-centers)
- [In den Admin-Centers nicht unterstützte Bezeichnungseinstellungen](#label-settings-that-are-not-supported-in-the-admin-centers)
- [Vergleichen des Verhaltens von Schutzeinstellungen für eine Bezeichnung](#comparing-the-behavior-of-protection-settings-for-a-label)

### <a name="client-support-for-unified-labeling"></a>Client Unterstützung für vereinheitlichte Bezeichnung

Stellen Sie sicher, dass Sie über [Clients verfügen, die einheitliche Bezeichnungen unterstützen](#clients-and-services-that-support-unified-labeling) und ggf. für die Verwaltung sowohl im Azure-Portal (für Clients, die einheitliche Bezeichnungen nicht unterstützen) als auch für die Admin Center (für Clients, die einheitliche Bezeichnungen unterstützen) vorbereitet werden.

### <a name="policy-configuration"></a>Richtlinienkonfiguration

Richtlinien, einschließlich Richtlinieneinstellungen und der entsprechenden Zugriffberechtigungen (bereichsbezogene Richtlinien), sowie alle erweiterten Clienteinstellungen werden nicht migriert. Zum Konfigurieren dieser Einstellungen nach der Migration der Bezeichnung können Sie folgende Optionen angeben:

- Ihr Admin Center für Vertraulichkeits Bezeichnungen.
- [Office 365 Security & Compliance PowerShell](/powershell/exchange/office-365-scc/office-365-scc-powershell), die Sie verwenden müssen, um [Erweiterte Client Einstellungen zu konfigurieren](rms-client/clientv2-admin-guide-customizations.md#configuring-advanced-settings-for-the-client-via-powershell).
    
> [!IMPORTANT]
> Nicht alle Einstellungen einer migrierten Bezeichnung werden von den Admin-Centers unterstützt. Verwenden Sie die Tabelle im Abschnitt [In den Admin-Centers nicht unterstützte Bezeichnungseinstellungen](#label-settings-that-are-not-supported-in-the-admin-centers), um die entsprechenden Einstellungen sowie die empfohlene Vorgehensweise zu ermitteln.
> 

### <a name="protection-templates"></a>Schutzvorlagen

- Vorlagen, die einen cloudbasierten Schlüssel verwenden und Teil einer Bezeichnungskonfiguration sind, werden ebenfalls mit der Bezeichnung migriert. Andere Schutzvorlagen werden nicht migriert. 
    
- Wenn Sie über Bezeichnungen verfügen, die für eine vordefinierte Vorlage konfiguriert sind, können Sie diese Bezeichnungen bearbeiten und die Option **Berechtigungen festlegen** auswählen, um die gleichen Schutzeinstellungen wie in Ihrer Vorlage zu konfigurieren. Bezeichnungen mit vordefinierten Vorlagen verhindern die Bezeichnungsmigration nicht, diese Bezeichnungskonfiguration wird jedoch in den Admin-Centers nicht unterstützt.
        
    > [!TIP]
    > Um Ihnen bei der Neukonfiguration dieser Bezeichnungen zu helfen, ist es möglicherweise hilfreich, zwei Browserfenster zu verwenden: ein Fenster, in dem Sie die Schaltfläche **Vorlage bearbeiten** für die Bezeichnung auswählen, um die Schutzeinstellungen anzuzeigen, und das andere Fenster, in dem Sie die gleichen Einstellungen konfigurieren, wenn Sie **Berechtigungen festlegen** auswählen.
    
- Nachdem eine Bezeichnung mit cloudbasierten Schutzeinstellungen migriert wurde, ist der sich ergebende Bereich der Schutz Vorlage der Bereich, der in der Azure-Portal definiert ist (oder mithilfe des PowerShell-Moduls aipservice), und der Bereich, der in den Admin Centers definiert ist. 

### <a name="display-names"></a>Anzeigen Amen

Das Azure-Portal zeigt nur den Anzeigenamen der jeweiligen Bezeichnung an, den Sie bearbeiten können. Benutzer sehen diesen Bezeichnungs Namen in ihren apps. 

Die Admin-Centers zeigen sowohl den Anzeigenamen als auch den Bezeichnungsnamen an. Der Name der Bezeichnung ist der anfängliche Name, den Sie beim Erstellen der Bezeichnung angeben. diese Eigenschaft wird vom Back-End-Dienst zu Identifikationszwecken verwendet. Wenn Sie Ihre Bezeichnungen migrieren, bleibt der Anzeige Name unverändert, und der Bezeichnungs Name wird im Azure-Portal in die Bezeichnungs-ID umbenannt.

#### <a name="conflicting-display-names"></a>Widersprüchliche anzeigen Amen

Stellen Sie vor dem Migrieren sicher, dass nach Abschluss der Migration keine Konflikt verursachenden anzeigen Amen vorhanden sind. Anzeigen Amen an derselben Stelle in der Beschriftungs Hierarchie müssen eindeutig sein. 

Sehen Sie sich beispielsweise die folgende Liste von Bezeichnungen an:

- **Öffentlich**
- **Allgemein**
- **Vertraulich**
    - **Vertrauen\hr**
    - **Vertrauen\finance**
- **Geheimnis**
    - **Secret\hr**
    - **Secret\finance**
    
In dieser Liste sind **Public**, **General**, **Confidential** und **Secret** alle übergeordneten Bezeichnungen und dürfen keine doppelten Namen aufweisen. Darüber hinaus befinden sich " **confitial\hr** " und " **confitial\finance** " in der Hierarchie und können auch keine doppelten Namen aufweisen.

Untergeordnete Bezeichnungen über verschiedene übergeordnete Elemente, wie z. b. **confitial\hr** und **secret\hr** , befinden sich jedoch nicht an derselben Stelle in der Hierarchie und können daher dieselben individuellen Namen aufweisen. 

### <a name="localized-strings-in-labels"></a>Lokalisierte Zeichen folgen in Bezeichnungen

Lokalisierte Zeichenfolgen für die Bezeichnungen werden nicht migriert. Definieren Sie neue lokalisierte Zeichen folgen für die migrierten Bezeichnungen mithilfe von Office 365 Security & Compliance PowerShell und dem *localesettings* -Parameter für " [Set-Label](/powershell/module/exchange/policy-and-compliance/set-label)".

### <a name="editing-migrated-labels-in-the-admin-centers"></a>Bearbeiten von migrierten Bezeichnungen in admin Centers

Wenn Sie nach der Migration eine migrierte Bezeichnung im Azure-Portal bearbeiten, wird die entsprechende Änderung automatisch in den Admin-Centers angezeigt. 

Wenn Sie jedoch eine migrierte Bezeichnung in einem der Admin Center bearbeiten, müssen Sie zum Bereich Azure-Portal, **Azure Information Protection-vereinheitlichte Bezeichnung** zurückkehren und **veröffentlichen** auswählen. 

Diese zusätzliche Aktion ist erforderlich, damit die Azure Information Protection-Clients (klassisch) die Bezeichnungs Änderungen übernehmen können.

### <a name="label-settings-that-are-not-supported-in-the-admin-centers"></a>In den Admin-Centers nicht unterstützte Bezeichnungseinstellungen

Anhand der folgenden Tabelle können Sie feststellen, welche Konfigurationseinstellungen einer migrierten Bezeichnung vom Office 365 Security & Compliance Center, dem Microsoft 365 Security Center, oder dem Microsoft Compliance Center nicht unterstützt werden. Wenn Sie über Bezeichnungen mit diesen Einstellungen verfügen, verwenden Sie nach Abschluss der Migration die Anleitung zur Verwaltung in der letzten Spalte, bevor Sie Ihre Bezeichnungen in einem der referenzierten admin Centers veröffentlichen.

Wenn Sie nicht sicher sind, wie Ihre Bezeichnungen konfiguriert sind, zeigen Sie die zugehörigen Einstellungen im Azure-Portal an. Eine Anleitung zu diesem Schritt finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Azure Information Protection Clients (klassisch) können alle Bezeichnungs Einstellungen verwenden, die ohne Probleme aufgelistet sind, da Sie die Bezeichnungen weiterhin vom Azure-Portal herunterladen.

|Bezeichnungskonfiguration|Unterstützt von Clients für einheitliche Bezeichnungen| Leitfaden für die Admin-Centers|
|-------------------|---------------------------------------------|-------------------------|
|**Statusangabe „Aktiviert“/„Deaktiviert“**<br /><br />Dieser Status wird nicht mit den Admin Centers synchronisiert. |Nicht verfügbar|Das Äquivalent ist, ob die Bezeichnung veröffentlicht wurde oder nicht. |
|**Die Bezeichnungsfarbe, die Sie aus der Liste auswählen oder mit einem RGB-Code angeben** |Ja|Keine Konfigurationsoption für Bezeichnungsfarben. Stattdessen können Sie Bezeichnungs Farben im Azure-Portal konfigurieren oder [PowerShell](./rms-client/clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)verwenden.|
|**Cloudbasierter Schutz oder HYOK-Schutz (Hold Your Own Key) mit vordefinierter Vorlage** |Nein|Keine Konfigurationsoption für vordefinierte Vorlagen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.|
|**Cloudbasierter Schutz mit benutzerdefinierten Berechtigungen für Word, Excel und PowerPoint** |Ja|Die Admin Center verfügen jetzt über eine Konfigurationsoption für benutzerdefinierte Berechtigungen. <br /><br /> Wenn Sie eine Bezeichnung mit dieser Konfiguration veröffentlichen, überprüfen Sie die Ergebnisse der Anwendung der Bezeichnung aus der [folgenden Tabelle](#comparing-the-behavior-of-protection-settings-for-a-label).|
|**Hyok-basierter Schutz mithilfe von benutzerdefinierten Berechtigungen für Outlook** (nicht weiterleiten) |Nein|Keine Konfigurationsoption für HYOK. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen. Wenn Sie dies tun, finden Sie die Ergebnisse der Anwendung der Bezeichnung in der [folgenden Tabelle](#comparing-the-behavior-of-protection-settings-for-a-label).|
|**Benutzerdefinierter Schriftart Name, Größe und benutzerdefinierte Schriftfarbe durch RGB-Code für visuelle Kennzeichnungen** (Kopfzeile, Fußzeile, Wasserzeichen)  |Ja|Die Konfiguration für optische Kennzeichnungen ist begrenzt auf eine Farb- und Schriftgradliste. Sie können diese Bezeichnung ohne Änderungen veröffentlichen, obwohl Sie sich die konfigurierten Werte in den Admin-Centers nicht ansehen können. <br /><br />Um diese Optionen zu ändern, verwenden Sie das Cmdlet [**New-Label**](/powershell/module/exchange/new-label) Office 365 Security & Compliance Center. Um die Verwaltung zu vereinfachen, sollten Sie die Farbe in eine der aufgelisteten Optionen in den Admin Center ändern. <br /><br />**Hinweis**: das Security & Compliance Center Admin Center unterstützt eine vordefinierte Liste der Schriftart Definitionen. Benutzerdefinierte Schriftarten und Farben werden nur über das Cmdlet " [**New-Label**](/powershell/module/exchange/new-label) Office 365 Security & Compliance Center" unterstützt. <br><br>Wenn Sie mit dem klassischen Client arbeiten, nehmen Sie diese Änderungen an ihrer Bezeichnung im Azure-Portal vor.|
|**Variablen in visuellen Markierungen** (Kopfzeile, Fußzeile) |Ja|Diese Bezeichnung wird von den AIP-Clients und der integrierten Office-Bezeichnung für ausgewählte Apps unterstützt. <br /><br />Wenn Sie mit einer integrierten Bezeichnung arbeiten, die eine APP verwendet, die diese Konfiguration nicht unterstützt, und diese Bezeichnung ohne Änderungen veröffentlichen, werden Variablen als Text auf Clients angezeigt, anstatt den dynamischen Wert anzuzeigen.<br /><br />Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/sensitivity-labels-office-apps#dynamic-markings-with-variables). |
|**Visuelle Kennzeichnungen pro App**|Ja|Diese Bezeichnung wird nur von den AIP-Clients und nicht von der integrierten Office-Bezeichnung unterstützt. <br /><br />Wenn Sie mit integrierter Bezeichnung arbeiten und diese Bezeichnung ohne Änderungen veröffentlichen, wird die Konfiguration der visuellen Markierung als Variablen Text anstelle der visuellen Kennzeichnungen angezeigt, die Sie für die Anzeige in den einzelnen apps konfiguriert haben.  |
|**"Nur für mich" Schutz**|Ja|Die Admin Center erlauben Ihnen nicht, die von Ihnen geltenden Verschlüsselungseinstellungen zu speichern, ohne Benutzer anzugeben. Im Azure-Portal führt diese Konfiguration zu einer Bezeichnung, die den [Schutz "nur für mich](configure-policy-protection.md#example-6-label-that-applies-just-for-me-protection)" betrifft. <br /><br /> Erstellen Sie alternativ eine Bezeichnung, die die Verschlüsselung anwendet und einen Benutzer mit beliebigen Berechtigungen angibt, und bearbeiten Sie dann die zugehörige Schutz Vorlage mithilfe von PowerShell. Verwenden Sie zunächst das Cmdlet [New-aipservicerighundefinition](/powershell/module/aipservice/new-aipservicerightsdefinition) (siehe Beispiel 3), und legen Sie dann [-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty#examples) mit dem Parameter *rightiondefinitions* fest.|
|**Bedingungen und entsprechende Einstellungen** <br /><br /> Einschließlich automatischer und empfohlener Bezeichnungen samt QuickInfos|Nicht verfügbar|Konfigurieren Sie Ihre Bedingungen neu, indem Sie die automatische Bezeichnung als eine von den Bezeichnungseinstellungen eigenständige Konfiguration verwenden.|
| | | |

### <a name="comparing-the-behavior-of-protection-settings-for-a-label"></a>Vergleichen des Verhaltens von Schutzeinstellungen für eine Bezeichnung

Verwenden Sie die folgende Tabelle, um zu ermitteln, wie sich die gleiche Schutz Einstellung für eine Bezeichnung anders verhält, je nachdem, ob Sie vom Azure Information Protection klassischen Client, vom Azure Information Protection Unified Label-Client oder von Office-Apps verwendet wird, deren Bezeichnung in integriert ist (auch bekannt als "Native Büro Bezeichnung"). Die Unterschiede im Bezeichnungs Verhalten können Ihre Entscheidung ändern, ob die Bezeichnungen veröffentlicht werden sollen, insbesondere wenn Sie über eine Kombination von Clients in Ihrer Organisation verfügen.

Wenn Sie nicht sicher sind, wie Ihre Schutzeinstellungen konfiguriert sind, können Sie die Einstellungen im Bereich **Schutz** im Azure-Portal anzeigen. Eine Anleitung zu diesem Schritt finden Sie unter [So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen](configure-policy-protection.md#to-configure-a-label-for-protection-settings).

Schutzeinstellungen, die sich genauso verhalten, werden in der Tabelle nicht aufgeführt, mit den folgenden Ausnahmen:
- Wenn Sie Office-Apps mit integrierter Bezeichnungsfunktion verwenden, werden Bezeichnungen im Datei-Explorer nicht angezeigt, es sei denn, Sie installieren auch den Azure Information Protection Unified Labeling-Client.
- Wenn Sie Office-Apps mit integrierter Bezeichnungsfunktion verwenden, bleibt dieser Schutz bestehen, wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde [[1]](#footnote-1).

|Schutzeinstellung für eine Bezeichnung |Klassischer Azure Information Protection-Client |Azure Information Protection-Client für einheitliche Bezeichnungen| Office-Apps mit integrierter Bezeichnungsfunktion
|-------------------|-----------------------------------|-----------------------------------------------------------|---------------
|HYOK (AD RMS) mit Vorlage:| Wird in Word, Excel, PowerPoint, Outlook und im Datei-Explorer angezeigt<br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– HYOK-Schutz wird auf Dokumente und E-Mails angewendet | Wird in Word, Excel, PowerPoint, Outlook und im Datei-Explorer angezeigt  <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen |Wird in Word, Excel, PowerPoint und Outlook angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1) |
|HYOK (AD RMS) mit benutzerdefinierten Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer:| Wird in Word, Excel, PowerPoint und im Datei-Explorer angezeigt<br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – HYOK-Schutz wird auf Dokumente und E-Mails angewendet| Wird in Word, Excel und PowerPoint angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen|Wird in Word, Excel und PowerPoint angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen |
|HYOK (AD RMS) mit benutzerdefinierten Berechtigungen für Outlook:|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br />– „Nicht weiterleiten“ mit HYOK-Schutz wird auf E-Mails angewendet|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1)|

###### <a name="footnote-1"></a>Fußnote 1

In Outlook wird der Schutz mit einer Ausnahme beibehalten: Wenn eine e-Mail mit der Encrypt-Only-Option geschützt wurde, wird dieser Schutz entfernt.


###### <a name="footnote-2"></a>Fußnote 2

Der Schutz wird entfernt, wenn der Benutzer über ein Nutzungsrecht oder eine Nutzungsrolle verfügt, wovon diese Aktion unterstützt wird:
- Das [Nutzungsrecht](configure-usage-rights.md#usage-rights-and-descriptions) „Exportieren“ oder „Vollzugriff“.
- Die Rolle [Rights Management-Aussteller oder Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) oder [Administrator](configure-super-users.md).

Wenn der Benutzer über keine/s dieser Nutzungsrechte oder Nutzungsrollen verfügt, wird die Bezeichnung nicht angewendet, und der ursprüngliche Schutz wird beibehalten.


## <a name="to-migrate-azure-information-protection-labels"></a>Migrieren von Azure Information Protection-Bezeichnungen

Verwenden Sie die folgenden Anweisungen, um Ihre Mandanten-und Azure Information Protection Bezeichnungen zu migrieren, um den Unified Label-Speicher zu verwenden

Sie müssen Kompatibilitäts Administrator, Kompatibilitäts Daten Administrator, Sicherheitsadministrator oder globaler Administrator sein, um ihre Bezeichnungen zu migrieren.

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich am Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies nicht bereits getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Wählen Sie unter der Menüoption **Verwalten** die Option **Einheitliche Bezeichnungen** aus.

3. Wählen Sie im Bereich **Azure Information Protection vereinheitlichte Bezeichnung** die Option **aktivieren** aus, und befolgen Sie die Online Anweisungen.
    
    Wenn die Option zum Aktivieren nicht verfügbar ist, überprüfen Sie den **Status der vereinheitlichten Bezeichnung**: Wenn Sie **aktiviert** sehen, wird für Ihren Mandanten bereits der vereinheitlichte Bezeichnungs Speicher verwendet, und es ist nicht erforderlich, ihre Bezeichnungen zu migrieren.

Die Bezeichnungen, die erfolgreich migriert wurden, können nun von [Clients und Diensten, die einheitliche Bezeichnungen unterstützen](#clients-and-services-that-support-unified-labeling), verwendet werden. Allerdings müssen Sie [diese Bezeichnungen](/microsoft-365/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy) zuerst in einem der Admin Center veröffentlichen: Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center.

> [!IMPORTANT]
> Wenn Sie die Bezeichnungen außerhalb des Azure-Portal bearbeiten, kehren Sie für Azure Information Protection Clients (klassisch) zu diesem **Azure Information Protection vereinheitlichten Beschriftungs** Bereich zurück, und wählen Sie **veröffentlichen** aus.

### <a name="copy-policies"></a>Richtlinien kopieren

Nachdem Sie Ihre Bezeichnungen migriert haben, können Sie eine Option zum Kopieren von Richtlinien auswählen. Wenn Sie diese Option auswählen, wird eine einmalige Kopie Ihrer Richtlinien mit Ihren [Richtlinien Einstellungen](configure-policy-settings.md) und [erweiterten Client Einstellungen](./rms-client/client-admin-guide-customizations.md#available-advanced-classic-client-settings) an das Admin Center gesendet, in dem Sie Ihre Bezeichnungen verwalten: Office 365 Security & Compliance Center, Microsoft 365 Security Center, Microsoft 365 Compliance Center. 

Die Richtlinien wurden mit Ihren Einstellungen erfolgreich kopiert und dann automatisch für die Benutzer und Gruppen veröffentlicht, die den Richtlinien in der Azure-Portal zugewiesen wurden. Beachten Sie, dass dies für die globale Richtlinie alle Benutzer bedeutet. Wenn Sie nicht bereit sind, die migrierten Bezeichnungen in den kopierten Richtlinien zu veröffentlichen, können Sie nach dem Kopieren der Richtlinien die Bezeichnungen aus den Bezeichnungs Richtlinien in Ihrem Admin-Beschriftungs Center entfernen.

Beachten Sie Folgendes, bevor Sie die Option **Richtlinien kopieren (Vorschau)** im Bereich **Azure Information Protection vereinheitlichte Bezeichnung** auswählen:

- Die Option zum **Kopieren von Richtlinien (Vorschau)** ist erst verfügbar, wenn die einheitliche Bezeichnung für Ihren Mandanten aktiviert ist.

- Richtlinien und Einstellungen können nicht selektiv zum Kopieren ausgewählt werden. Alle Richtlinien (die **globale** Richtlinie und alle Bereichs bezogenen Richtlinien) werden automatisch zum Kopieren ausgewählt, und alle Einstellungen, die als Bezeichnungs Richtlinien Einstellungen unterstützt werden, werden kopiert. Wenn Sie bereits über eine Bezeichnungs Richtlinie mit demselben Namen verfügen, wird Sie mit den Richtlinien Einstellungen in der Azure-Portal überschrieben.

- Einige erweiterte Client Einstellungen werden nicht kopiert, da Sie für den Azure Information Protection Unified Label-Client als *Erweiterte Einstellungen* für die Bezeichnung anstelle von Richtlinien Einstellungen unterstützt werden. Sie können diese Bezeichnung Erweiterte Einstellungen mit [Microsoft 365 Security & Compliance Center PowerShell](rms-client/clientv2-admin-guide-customizations.md#configuring-advanced-settings-for-the-client-via-powershell)konfigurieren. Die erweiterten Client Einstellungen, die nicht kopiert werden:
    - [LabelbyCustomProperty](./rms-client/client-admin-guide-customizations.md#migrate-labels-from-secure-islands-and-other-labeling-solutions)
    - [LabelToSMIME](./rms-client/client-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)

- Anders als bei der Bezeichnung Migration, bei der nachfolgende Änderungen an Bezeichnungen synchronisiert werden, werden bei der Aktion **Richtlinien kopieren** keine nachfolgenden Änderungen an Ihren Richtlinien oder Richtlinien Einstellungen synchronisiert Sie können die Aktion "Richtlinie kopieren" wiederholen, nachdem Sie Änderungen an der Azure-Portal vorgenommen haben, und alle vorhandenen Richtlinien und deren Einstellungen werden erneut überschrieben. Oder verwenden Sie die Cmdlets Set-LabelPolicy oder Set-Label mit dem Parameter *advancedsettings* aus Office 365 Security & Compliance Center PowerShell.

- Die Aktion **Richtlinien kopieren** überprüft vor dem Kopieren Folgendes für jede Richtlinie:
    
    - Benutzer und Gruppen, die der Richtlinie zugewiesen sind, befinden sich zurzeit in Azure AD. Wenn mindestens ein Konto fehlt, wird die Richtlinie nicht kopiert. Die Gruppenmitgliedschaft ist nicht aktiviert.
    
    - Die globale Richtlinie enthält mindestens eine Bezeichnung. Da die Administrator Bezeichnungen keine Bezeichnungs Richtlinien ohne Bezeichnungen unterstützen, wird eine globale Richtlinie ohne Bezeichnungen nicht kopiert.

- Wenn Sie Richtlinien kopieren und Sie dann von Ihrem Administrator bezeichnen Center löschen, warten Sie mindestens zwei Stunden, bevor Sie die Aktion **Richtlinien kopieren** erneut verwenden, um ausreichend Zeit für die Replikation des Löschvorgangs sicherzustellen.

- Aus Azure Information Protection kopierte Richtlinien haben nicht denselben Namen, Sie werden stattdessen mit einem Präfix **AIP_** benannt. Richtlinien Namen können später nicht geändert werden. 

Weitere Informationen zum Konfigurieren der Richtlinien Einstellungen, der erweiterten Client Einstellungen und der Bezeichnungs Einstellungen für den Azure Information Protection Unified Label-Client finden Sie im Administrator Handbuch unter [benutzerdefinierte Konfigurationen für den Azure Information Protection Unified](./rms-client/clientv2-admin-guide-customizations.md) Label-Client.

> [!NOTE]
> Azure Information Protection Unterstützung für das Kopieren von Richtlinien ist derzeit in der Vorschau Phase In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 

### <a name="clients-and-services-that-support-unified-labeling"></a>Clients und Dienste, die einheitliche Bezeichnungen unterstützen

Um zu überprüfen, ob die von Ihnen verwendeten Clients und Dienste die einheitliche Bezeichnung unterstützen, lesen Sie die Dokumentation, um zu überprüfen, ob Sie Vertraulichkeits Bezeichnungen verwenden können, die von einem der Admin Center veröffentlicht werden: Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center. 

##### <a name="clients-that-currently-support-unified-labeling-include"></a>Folgende Clients unterstützen derzeit einheitliche Bezeichnungen:

- **Der [Azure Information Protection Unified Bezeichnung-Client für Windows](./rms-client/unifiedlabelingclient-version-release-history.md)** 

    Einen Vergleich dieses Clients mit dem Azure Information Protection klassischen Clients finden Sie unter [vergleichen der Beschriftungslösungen für Windows-Computer](rms-client/use-client.md#compare-the-labeling-solutions-for-windows-computers).

- **Apps aus Office, die sich in unterschiedlichen Verfügbarkeits Stufen befinden** 

    Weitere Informationen finden Sie [unter Unterstützung für Funktionen zur Vertraulichkeits Bezeichnung in apps](/microsoft-365/compliance/sensitivity-labels-office-apps#support-for-sensitivity-label-capabilities-in-apps) aus der Dokumentation zur Microsoft 365 Konformität.
    
- **Apps von Softwareanbietern und Entwicklern** , die das [Microsoft Information Protection SDK](/information-protection/develop/overview)verwenden.

##### <a name="services-that-currently-support-unified-labeling-include"></a>Folgende Dienste unterstützen derzeit einheitliche Bezeichnungen:

- **[Power BI](/power-bi/admin/service-security-data-protection-overview)**

- **Office Online und Outlook im Web**

    Weitere Informationen finden Sie unter [Aktivieren von Vertraulichkeits Bezeichnungen für Office-Dateien in SharePoint und onedrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files).

- **Microsoft SharePoint, onedrive for Work oder School, onedrive für Home, Teams und Microsoft 365 Gruppen**
    
    Weitere Informationen finden Sie unter [Verwenden von Vertraulichkeits Bezeichnungen zum Schützen von Inhalten in Microsoft Teams, Microsoft 365 Gruppen und SharePoint-Websites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

- **Microsoft Defender Advanced Threat Protection**

- **Microsoft Cloud App Security**
    
    Dieser Dienst unterstützt Bezeichnungen sowohl vor der Migration in den einheitlichen Bezeichnungsspeicher, als auch nach der Migration, und verwendet dabei die folgende Logik:
    
    - Wenn die Admin Center über Vertraulichkeits Bezeichnungen verfügen, werden diese Bezeichnungen aus den Admin Centers abgerufen. Wenn Sie diese Bezeichnungen in Cloud App Security auswählen möchten, muss mindestens eine Bezeichnung für mindestens einen Benutzer veröffentlicht worden sein.
    
    - Wenn die Admin Center keine Empfindlichkeits Bezeichnungen aufweisen, werden Azure Information Protection Bezeichnungen aus dem Azure-Portal abgerufen.

- **Dienste von Softwareanbietern und Entwicklern** , die das [Microsoft Information Protection SDK](/information-protection/develop/overview)verwenden.

## <a name="next-steps"></a>Nächste Schritte

**Anleitungen und Tipps von unserem Customer Customer-Team**:

- Blog Beitrag: Grundlegendes zur [Migration der vereinheitlichten Bezeichnung](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Understanding-Unified-Labeling-migration/ba-p/783185)

- Webinar: [einheitliche Bezeichnung für Aufzeichnung, Karten und FAQs](https://github.com/nihendle/MIP-Comp/tree/master/MIP/Webinars/Unified%20Labeling%20Migration)


**Informationen zu Vertraulichkeits Bezeichnungen**:
- [Informationen zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels)
- [Erstellen und konfigurieren Sie Vertraulichkeits Bezeichnungen und deren Richtlinien](/microsoft-365/compliance/create-sensitivity-labels).

Stellen Sie **den einheitlichen AIP-Beschriftungs Client** bereit:

Wenn Sie dies nicht bereits getan haben, installieren Sie den Azure Information Protection Unified-Bezeichnungs Client. 

Weitere Informationen finden Sie unter

- [Azure Information Protection Unified Bezeichnungs Verlauf des Client Versions Verlaufs und der Support Richtlinie](rms-client/unifiedlabelingclient-version-release-history.md)
- [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](rms-client/clientv2-admin-guide.md)
- [Azure Information Protection Unified-Bezeichnung (Benutzerhandbuch)](rms-client/clientv2-user-guide.md)
