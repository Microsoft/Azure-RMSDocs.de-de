---
title: Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center
description: Migrieren Sie Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center für Clients, die einheitliche Bezeichnungen unterstützen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/28/2018
ms.topic: article
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 64063af186f01a5829b7aa668260928e3b13656d
ms.sourcegitcommit: 304702a3f2f2ab2b32493c4aedeb5ee8424b925c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2018
ms.locfileid: "47415008"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-the-office-365-security--compliance-center"></a>Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Dieses Feature befindet sich in der Vorschau und migriert Ihren Mandanten zu einer neuen Plattform, die ebenfalls als Vorschau verfügbar ist. Die Migration kann nicht rückgängig gemacht werden. Die neue Plattform unterstützt einheitliche Bezeichnungen. Das bedeutet, dass die Bezeichnungen, die Sie erstellen und verwalten, von mehreren Clients und Diensten verwendet werden können.

Migrieren Sie Ihre Bezeichnungen, um Sie im Office 365 Security & Compliance Center zu verwenden. Dort können sie veröffentlicht und dann von [Clients, die einheitliche Bezeichnungen unterstützen](#clients-that-support-unified-labeling), heruntergeladen werden. Der Azure Information Protection-Client lädt die Bezeichnungen mit ihrer Azure Information Protection-Richtlinie aus dem Azure-Portal herunter. 

Nachdem Sie Ihre Bezeichnungen migriert haben, können Sie diese im Azure-Portal oder im Office 365 Security & Compliance Center ändern. Die jeweiligen Clients laden dann ebendiese Änderungen herunter.

## <a name="considerations-for-unified-labels"></a>Überlegungen zu einheitlichen Bezeichnungen

Beachten Sie die folgenden Änderungen und Überlegungen, bevor Sie Bezeichnungen migrieren:

- Nicht alle Clients unterstützen derzeit einheitliche Bezeichnungen. Stellen Sie sicher, dass Sie über [unterstützte Clients](#clients-that-support-unified-labeling) verfügen. Die Verwaltung erfolgt im Azure-Portal (Clients, die einheitliche Bezeichnungen nicht unterstützen) und im Security & Compliance Center (Clients, die einheitliche Bezeichnungen unterstützen).

- Wenn Sie gerade dabei sind, die gewünschten Bezeichnungen zu definieren und zu konfigurieren, empfehlen wir Ihnen, diesen Vorgang im Azure-Portal abzuschließen und die Bezeichnungen danach zu migrieren. Dadurch werden beim Migrationsvorgang doppelte Bezeichnungen vermieden, die dann im Security & Compliance Center bearbeitet werden müssen.

- Richtlinien, einschließlich Richtlinieneinstellungen und der entsprechenden Zugriffberechtigungen (bereichsbezogene Richtlinien), sowie alle erweiterten Clienteinstellungen werden nicht migriert. Für nicht migrierte Änderungen müssen Sie nach der Migration der Bezeichnungen die entsprechenden Optionen im Security & Compliance Center konfigurieren.
    
    Zur Optimierung der Benutzerfreundlichkeit empfehlen wir, die gleichen Bezeichnungen in den gleichen Bereichen im Security & Compliance Center zu veröffentlichen.

- Nicht alle Einstellungen einer migrierten Bezeichnung werden vom Security & Compliance Center unterstützt. Verwenden Sie die Tabelle in Abschnitt [Im Security & Compliance Center nicht unterstützte Bezeichnungseinstellungen](#label-settings-that-are-not-supported-in-the-security--compliance-center), um die entsprechenden Einstellungen zu ermitteln und festzulegen, ob die migrierten Bezeichnungen von der Veröffentlichung im Security & Compliance Center ausgeschlossen werden sollen.

- Schutzvorlagen:
    
    - Vorlagen, die einen cloudbasierten Schlüssel verwenden und Teil einer Bezeichnungskonfiguration sind, werden ebenfalls mit der Bezeichnung migriert. Andere Schutzvorlagen werden nicht migriert. 
    
    - Nach der Migration einer Bezeichnung mit cloudbasierten Schutzeinstellungen ist der Ergebnisbereich der Schutzvorlage der Bereich, der im Azure-Portal (bzw. unter Verwendung des ADDRM PowerShell-Moduls) und im Security & Compliance Center definiert ist. 

- Wenn Sie Ihre Bezeichnungen migrieren, zeigen die Migrationsergebnisse an, ob eine Bezeichnung **erstellt**, **aktualisiert** oder zum Vermeiden von Duplikaten **umbenannt** wurde:

    - Wenn Sie eine Bezeichnung erstellen, veröffentlichen Sie sie anschließend im Security & Compliance Center, um sie Anwendungen und Diensten zur Verfügung zu stellen.
    
    - Wenn Sie eine Bezeichnung umbenennen, bearbeiten Sie sie anschließend im Security & Compliance Center oder im Azure-Portal. 

- Das Azure-Portal zeigt nur den Anzeigenamen der jeweiligen Bezeichnung an, den Sie bearbeiten können. Das Security & Compliance Center zeigt sowohl den Anzeigenamen als auch den Bezeichnungsnamen an. Der Bezeichnungsname ist der ursprüngliche Name, den Sie beim Erstellen der Bezeichnung angeben. Diese Eigenschaft nutzt der Back-End-Dienst zur Identifizierung.

- Lokalisierte Zeichenfolgen für die Bezeichnungen werden nicht migriert. Sie müssen im Security & Compliance Center neue lokalisierte Zeichenfolgen für die migrierten Bezeichnungen definieren.

- Wenn Sie nach der Migration eine migrierte Bezeichnung im Azure-Portal bearbeiten, wird die entsprechende Änderung automatisch im Security & Compliance Center angezeigt. Wenn Sie eine migrierte Bezeichnung jedoch im Security & Compliance Center bearbeiten, müssen Sie sie im Azure-Portal aktualisieren, damit die Änderung übernommen wird. Bearbeiten Sie z.B. das Feld **Hinweise zur Verwendung durch den Administrator hinzufügen** auf dem Blatt **Bezeichnung**. 

- Einheitliche Bezeichnungen werden weiterhin für Mandanten bereitgestellt. Wenn sie noch nicht für Ihren Mandanten unterstützt werden, wird die Migration fehlschlagen, und Änderungen werden rückgängig gemacht. Solange nicht alle Mandanten unterstützt werden, müssen Sie über einen speziellen Link auf die Option zum Migrieren Ihrer Mandanten und Bezeichnungen zugreifen. Diesen Link finden Sie in den folgenden Anweisungen.

### <a name="label-settings-that-are-not-supported-in-the-security--compliance-center"></a>Im Security & Compliance Center nicht unterstützte Bezeichnungseinstellungen

Die folgende Tabelle zeigt, welche Konfigurationseinstellungen von migrierten Bezeichnungen nicht für Clients unterstützt werden, die diese Bezeichnungen verwenden, und ob Sie die migrierte Bezeichnung im Security & Compliance Center bearbeiten und veröffentlichen sollten. Wenn Sie Bezeichnungen veröffentlichen, die Sie vorher von der Veröffentlichung ausgeschlossen haben, werden für die Clients, die einheitliche Bezeichnungen unterstützen, keine Bezeichnungen angezeigt.

Azure Information Protection-Clients können diese Bezeichnungseinstellungen problemlos verwenden, weil sie die Bezeichnungen weiterhin aus dem Azure-Portal herunterladen.

|Bezeichnungskonfiguration|Im Security & Compliance Center unterstützt|Im Security & Compliance Center von Bearbeitung und Veröffentlichung ausgeschlossen|
|-------------------|---------------------------------------------|-------------------------|
|Statusangabe „Aktiviert“/„Deaktiviert“<br /><br />Hinweis: Keine Synchronisierung im Security & Compliance Center |Nicht verfügbar|Nicht verfügbar|
|Bezeichnungsfarbe: Auswahl aus der Liste oder Angabe mit RGB-Code<br /><br />Hinweis: Keine Unterstützung im Security & Compliance Center |Nicht verfügbar|Nicht verfügbar|
|Cloudbasierter Schutz oder HYOK-Schutz (Hold Your Own Key) mit vordefinierter Vorlage |Nein|Ja |
|Cloudbasierter Schutz mit benutzerdefinierten Berechtigungen in Word, Excel und PowerPoint |Nein|Ja |
|HYOK-Schutz mit benutzerdefinierten Berechtigungen in Outlook für „Nicht weiterleiten“ |Nein|Ja |
|Entfernen von Schutz |Nein|Ja |
|Optische Kennzeichnungen (Kopfzeile, Fußzeile, Wasserzeichen): Benutzerdefinierte Schriftart und -farbe (RGB-Code)|Nein|Empfohlen beim Verwenden von Variablen<br /><br />– Auf Clients werden Variablen nicht als dynamische Werte, sondern als Text angezeigt|
|Visuelle Kennzeichnungen pro App|Nein|Empfohlen beim Verwenden von Variablen<br /><br />– Auf Clients werden Variablen nicht als dynamische Werte, sondern als Text angezeigt|
|Bedingungen und entsprechende Einstellungen <br /><br />Hinweis: Einschließlich automatischer und empfohlener Bezeichnungen samt QuickInfos|Nicht verfügbar|Nein|


## <a name="to-migrate-azure-information-protection-labels"></a>Migrieren von Azure Information Protection-Bezeichnungen

> [!IMPORTANT]
> Migrieren Sie Bezeichnungen erst, wenn Sie Vertraulichkeitsbezeichnungen im Office 365 Security & Compliance Center bearbeiten und veröffentlichen können. Vertraulichkeitsbezeichnungen werden allmählich für Office 365-Mandanten bereitgestellt, sind allerdings noch nicht für alle Mandanten verfügbar.
> 
> So überprüfen Sie die Verfügbarkeit: Rufen Sie im Office 365 Security & Compliance Center **Klassifizierungen** > **Bezeichnungen** auf, und überprüfen Sie, ob die Registerkarte **Vertraulichkeit** vorhanden ist. Wenn diese Registerkarte nicht angezeigt wird, unterstützt Ihr Mandant noch nicht Vertraulichkeitsbezeichnungen. Migrieren Sie Ihre Azure Information Protection-Bezeichnungen nicht zu diesem Zeitpunkt.

Wenn Ihr Mandant Vertraulichkeitsbezeichnungen im Security & Compliance Center unterstützt, verwenden Sie die folgenden Anweisungen zum Migrieren Ihrer Mandanten und Azure Information Protection-Bezeichnungen.

1. Öffnen Sie ein neues Browserfenster, und melden Sie sich über diesen Link im Azure-Portal an: https://portal.azure.com/?ActivateMigration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/migrationActivationBlade 

2. Wählen Sie auf dem Blatt **Azure Information Protection – Einheitliche Bezeichnungen** **Aktivieren** aus, und befolgen Sie die Onlineanweisungen.

Erfolgreich migrierte Bezeichnungen können nun von [Clients verwendet werden, die einheitliche Bezeichnungen](#clients-that-support-unified-labeling) unterstützen, wenn diese Bezeichnungen im Security & Compliance Center veröffentlicht werden.


### <a name="clients-that-support-unified-labeling"></a>Clients, die einheitliche Bezeichnungen unterstützen

Folgende Clients unterstützen derzeit einheitliche Bezeichnungen:

- Apps aus dem Office Insider-Programm. Weitere Informationen finden Sie in der Office-Dokumentation im Abschnitt [Wo ist das Feature heute verfügbar?](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?ad=US#bkmk_whereavailable).
    
- Clients von Softwareherstellern und Entwicklern, die das [Microsoft Information Protection SDK](https://docs.microsoft.com/azure/information-protection/develop/mip/mip-sdk-reference) verwenden.


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Konfigurieren migrierter Bezeichnungen im Office 365 Security & Compliance Center finden Sie im Blogbeitrag [Ankündigung der Verfügbarkeit einheitlicher Bezeichnungsverwaltung im Security & Compliance Center](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492) (in englischer Sprache).