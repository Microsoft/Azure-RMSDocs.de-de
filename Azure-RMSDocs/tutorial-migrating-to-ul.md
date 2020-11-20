---
title: 'Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen'
description: Ein Tutorial, in dem Schritt für Schritt das Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen beschrieben wird.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/19/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: f988ba63671164463a4ad1b566daab7df123e057
ms.sourcegitcommit: df6ee1aca02e089e3a72006ecf0747f14213979c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94503637"
---
# <a name="tutorial-migrating-from-the-azure-information-protection-aip-classic-client-to-the-unified-labeling-client"></a>Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Klassischer Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> [!NOTE]
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden der klassische Azure Information Protection-Client und die Bezeichnungsverwaltung im Azure-Portal zum 31. März 2021 eingestellt.
> 
> Dieser Zeitrahmen ermöglicht allen derzeitigen Benutzern des klassischen Azure Information Protection-Clients den Umstieg auf den AIP-Client für einheitliche Bezeichnungen, der die Microsoft Information Protection-Lösung für einheitliche Bezeichnungen nutzt. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>

In diesem Tutorial wird beschrieben, wie Sie die Azure Information Protection-Bereitstellung Ihrer Organisation vom klassischen Client zum Client für einheitliche Bezeichnungen migrieren.

**Benötigte Zeit:** Die zum Durchführen einer Migration erforderliche Zeit hängt von der Komplexität Ihrer Richtlinien und den von Ihnen verwendeten AIP-Features ab. Sie können weiterhin mit dem klassischen Client arbeiten, während Sie die Migration im Hintergrund durchführen.

Dieses Tutorial bietet eine detaillierte Beschreibung der einzelnen Schritte sowie Verweise auf die entsprechenden Abschnitte an anderer Stelle der Microsoft-Dokumentation für weitere Einzelheiten.

In diesem Tutorial gehen Sie wie folgt vor:
> [!div class="checklist"]
> * Vorgehensweise bei der Planung der Migration
> * Migrieren Ihrer Bezeichnungen zur Plattform für einheitliche Bezeichnungen
> * Konfigurieren der erweiterten Einstellungen im neuen Admin Center für Bezeichnungen
> * Kopieren Ihrer Richtlinien zur Plattform für einheitliche Bezeichnungen
> * Bereitstellen des Clients für einheitliche Bezeichnungen

## <a name="why-migrate-to-the-unified-labeling-platform"></a>Gründe für die Migration zum Client für einheitliche Bezeichnungen

Zusätzlich zur [geplanten Einstellung des klassischen Clients](https://aka.ms/aipclassicsunset) gibt es auch weitere Gründe, die für eine Migration auf den Client für einheitliche Bezeichnungen sprechen, wie ein effektiver Schutz vertraulicher Daten in Ihrem gesamten digitalen Bestand. Nach der Migration verwenden Sie Microsoft Information Protection (MIP) z. B. in Microsoft 365-Clouddiensten, lokalen Anwendungen oder SaaS-Drittanbieteranwendungen.

MIP unterstützt integrierte Bezeichnungsdienste für viele grundlegende Datenschutzfunktionen, sodass Sie den Client ausschließlich für zusätzliche Features einsetzen können, die von den integrierten Bezeichnungsdiensten nicht unterstützt werden.

- **Senken Sie Ihre Wartungskosten**, indem Sie weniger zusätzliche Software bereitstellen und warten.
- **Erhöhen Sie die Office-Leistung**, ohne dass zusätzliche Add-Ins erforderlich sind.
- **Optimieren Sie die Verwaltung von Bezeichnungen und Schutzrichtlinien** für AIP, Office 365 und Windows mithilfe des Admin Centers für Bezeichnungen. 

    Zu den unterstützten Admin Centers gehören das Microsoft 365 Compliance Center, das Microsoft 365 Security Center bzw. das Microsoft 365 Security & Compliance Center.

Weitere Informationen finden Sie im [Blog mit grundlegenden Informationen zur Migration für einheitliche Bezeichnungen](https://techcommunity.microsoft.com/t5/microsoft-security-and/understanding-unified-labeling-migration/ba-p/783185).

## <a name="planning-your-migration"></a>Planen der Migration

Die meisten Funktionen, die für den klassischen AIP-Client verfügbar sind, stehen auch für den Client für einheitliche Bezeichnungen zur Verfügung. Einige Features sind jedoch noch nicht vollständig verfügbar, und einige sind für eine einheitliche Bezeichnung anders konfiguriert.

Lesen Sie die folgenden Artikel, um zu verstehen, wie sich die von Ihnen verwendeten Datenschutzfunktionen bei der Verwendung des Clients für einheitliche Bezeichnungen unterscheiden können:

- [Erfahren Sie mehr über integrierte Funktionen für Bezeichnungen in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps)
- [Vergleichen der Unterstützung zwischen dem klassischen Client und dem Client für einheitliche Bezeichnungen](rms-client/use-client.md#compare-the-labeling-clients-for-windows-computers)
- [Erfahren Sie, wie Sie Bezeichnungseinstellungen verwalten, die in den Admin Centers für einheitliche Bezeichnungen standardmäßig nicht unterstützt werden.](configure-policy-migrate-labels.md#label-settings-that-are-not-supported-in-the-admin-centers)

> [!TIP]
> Wenn es dokumentierte Unterschiede zwischen den Clients gibt, die sich auf das Verhalten Ihrer Endbenutzer auswirken, empfiehlt es sich, diese Änderungen effektiv an Ihre Benutzer zu kommunizieren, bevor Sie den Client für einheitliche Bezeichnungen bereitstellen und Ihre neue Richtlinie veröffentlichen.

Nachdem Sie die Migration geplant und sich mit den damit einhergehenden Änderungen auseinandergesetzt haben, fahren Sie mit dem Abschnitt [Migrieren von Bezeichnungen zur Plattform für einheitliche Bezeichnungen](#migrating-labels-to-the-unified-labeling-platform) fort.

## <a name="migrating-labels-to-the-unified-labeling-platform"></a>Migrieren von Bezeichnungen zur Plattform für einheitliche Bezeichnungen

Sobald Sie Ihre Migration geplant und überlegt haben, wie Sie mit den Unterschieden der Clients umgehen möchten, können Sie einheitliche Bezeichnungen aktivieren und Ihre Bezeichnungen migrieren.

Während der Migration verwenden Sie einfach weiterhin den klassischen AIP-Client und die Richtlinien im Bereich „Azure Information Protection“ des Azure-Portals. Die beiden Clients lassen sich ohne weitere Konfiguration parallel ausführen.

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) als Administrator mit einer der folgenden Rollen an:

    - **Complianceadministrator**
    - **Compliancedatenadministrator**
    - **Sicherheitsadministrator**
    - **Globaler Administrator**
    

1. Wählen Sie im Bereich „Azure Information Protection“ links unter **Verwalten** die Option **Einheitliche Bezeichnungen** aus.

    Wählen Sie oben auf der Seite :::image type="icon" source="media/qs-tutor/activate.PNG" border="false"::: **Aktivieren** aus, um einheitliche Bezeichnungen zu aktivieren.

    Ihre Bezeichnungen werden aus Azure Information Protection in die Plattform für einheitliche Bezeichnungen kopiert und nun in beiden Systemen gespeichert.

    Öffnen Sie Ihr Admin Center für Bezeichnungen, um die dort und im Bereich „Azure Information Protection“ angezeigten Bezeichnungen miteinander zu vergleichen. Die beiden Listen sollten identisch sein. Hier ist ein Beispiel beim Vergleich mit dem Microsoft 365 Security & Compliance Center:

    :::image type="content" source="media/qs-tutor/compare-migrated-labels-small.png" alt-text="Vergleichen der migrierten Bezeichnungen zwischen dem Azure-Portal und dem Security & Compliance Center" lightbox="media/qs-tutor/compare-migrated-labels.png":::

    > [!NOTE]
    > Verwenden Sie die Bezeichnungen bei Bedarf in beiden Systemen, bis Sie die Migration abgeschlossen haben. Weitere Informationen finden Sie unter [Synchronisieren von bearbeiteten Bezeichnungen](#synchronizing-labeling-edits).

Fahren Sie mit dem Abschnitt [Kopieren von Richtlinien zur Plattform für einheitliche Bezeichnungen](#copy-policies-to-the-unified-labeling-platform) fort.

### <a name="synchronizing-labeling-edits"></a>Synchronisieren von bearbeiteten Bezeichnungen

Sobald Sie Ihre Bezeichnungen in Ihr Admin Center für Bezeichnungen migriert haben (z. B. Microsoft 365 Security Center, Microsoft 365 Compliance Center oder Microsoft 365 Security & Compliance Center), werden alle Änderungen, die Sie noch an den migrierten Bezeichnungen im Azure-Portal vornehmen, automatisch mit derselben Bezeichnung im Admin Center synchronisiert, um eine einheitliche Bezeichnung zu gewährleisten.

Änderungen, die Sie an migrierten Bezeichnungen im Admin Center vornehmen, werden jedoch *nicht* mit dem Azure-Portal synchronisiert. Wenn Sie Änderungen im Admin Center vornehmen und diese im Azure-Portal aktualisiert werden müssen, kehren Sie zum Portal zurück, um das Update zu veröffentlichen.

**So veröffentlichen Sie eine aktualisierte Bezeichnung im Azure-Portal:**

1. Wählen Sie im Bereich „Azure Information Protection“ links unter **Verwalten** die Option **Einheitliche Bezeichnungen** aus.

1. Wählen Sie :::image type="icon" source="media/i-publish.PNG" border="false"::: **Veröffentlichen**. 

> [!NOTE]
> Dieser Schritt ist nur erforderlich, wenn Sie Änderungen an Ihren migrierten Bezeichnungen in der Plattform für einheitliche Bezeichnungen vorgenommen haben und diese Änderungen mit dem Azure-Portal synchronisiert werden müssen. 

### <a name="migrating-labels-via-powershell"></a>Migrieren von Bezeichnungen über PowerShell

Sie können auch mithilfe von PowerShell vorhandene Bezeichnungen migrieren, z. B. für eine GCC High-Umgebung.

Verwenden Sie das Cmdlet [New-Label](/powershell/module/exchange/new-label), um Ihre vorhandenen Vertraulichkeitsbezeichnungen zu migrieren.

Wenn Ihre Vertraulichkeitsbezeichnung beispielsweise über eine Verschlüsselung verfügt, nutzen Sie das Cmdlet **New-Label** wie folgt:

```PowerShell
New-Label -Name 'aipscopetest' -Tooltip 'aipscopetest' -Comment 'admin notes' -DisplayName 'aipscopetest' -Identity 'b342447b-eab9-ea11-8360-001a7dda7113' -EncryptionEnabled $true -EncryptionProtectionType 'template' -EncryptionTemplateId 'a32027d7-ea77-4ba8-b2a9-7101a4e44d89' -EncryptionAipTemplateScopes "['allcompany@labelaction.onmicrosoft.com','admin@labelaction.onmicrosoft.com']"
```

Weitere Informationen über die Arbeit in GCC-, GCC High- und DoD-Umgebungen finden Sie unter [Azure Information Protection Premium für Behörden – Beschreibung des Diensts](/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description#label-migration). 

## <a name="copy-policies-to-the-unified-labeling-platform"></a>Kopieren von Richtlinien zur Plattform für einheitliche Bezeichnungen

Kopieren Sie alle Richtlinien, die Sie im Azure-Portal gespeichert haben und in der Plattform für einheitliche Bezeichnungen verwenden möchten.

Dieses Feature befindet sich derzeit in der VORSCHAU. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind.

> [!NOTE]
> Beim Kopieren von Richtlinien gibt es bestimmte Einschränkungen. Sie können auch von Grund auf neu beginnen und die Richtlinien manuell in Ihrem Admin Center für Bezeichnungen erstellen. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy).
> 

**So kopieren Sie Ihre Richtlinien:** 

1. Beachten Sie die folgenden Punkte, und vergewissern Sie sich, dass Sie die Richtlinien jetzt kopieren möchten:

    |Aspekt  |Beschreibung  |
    |---------|---------|
    |**Beim Kopieren von Richtlinien werden *alle* Ihre Richtlinien kopiert**     |     Es ist nicht möglich, nur bestimmte Richtlinien zu kopieren. Sie können alle Ihre Richtlinien kopieren oder keine davon.   |
    |**Beim Kopieren werden Ihre Richtlinien automatisch veröffentlicht**     |  Beim Kopieren Ihrer Richtlinien auf den Client für einheitliche Bezeichnungen werden diese automatisch auf allen unterstützten Clients für einheitliche Bezeichnungen veröffentlicht. <br /><br />   **Wichtig:** Kopieren Sie Ihre Richtlinien nicht, wenn Sie diese nicht veröffentlichen möchten.     |
    |**Beim Kopieren werden vorhandene Richtlinien mit demselben Namen überschrieben**     |   Wenn Sie bereits über eine Richtlinie mit demselben Namen im Admin Center verfügen, werden beim Kopieren Ihrer Richtlinien alle in dieser Richtlinie definierten Einstellungen überschrieben.   <br /><br />Alle aus der Azure-Portal kopierten Richtlinien werden entsprechend der folgenden Syntax benannt: `AIP_<policy name>`.    |
    |**Einige Clienteinstellungen werden nicht kopiert**     | Einige Clienteinstellungen werden nicht auf die Plattform für einheitliche Bezeichnungen kopiert und müssen nach der Migration manuell konfiguriert werden. <br /><br />Weitere Informationen finden Sie unter [Konfigurieren von erweiterten Einstellungen für Bezeichnungen](#configuring-advanced-labeling-settings).|
    | | |

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) als Administrator mit einer der folgenden Rollen an:

    - **Complianceadministrator**
    - **Compliancedatenadministrator**
    - **Sicherheitsadministrator**
    - **Globaler Administrator**


1. Wählen Sie im Bereich „Azure Information Protection“ links unter **Verwalten** die Option **Einheitliche Bezeichnungen** aus.

1. Wählen Sie :::image type="icon" source="media/i-copy-policies.PNG" border="false"::: **Richtlinien kopieren (Vorschau)** aus. Alle Richtlinien, die Sie im Azure-Portal gespeichert haben, werden in das Admin Center kopiert.

    Wenn bereits Richtlinien mit denselben Namen im Admin Center vorhanden sind, werden diese mit den Einstellungen aus dem Azure-Portal überschrieben.

    > [!IMPORTANT]
    > Wenn Sie derzeit Bezeichnungen von Microsoft Cloud App Security und Azure Information Protection verwenden, vergewissern Sie sich, dass Sie mindestens eine Richtlinie mit den mindestens erforderlichen Bezeichnungen in Ihrem Admin Center für Bezeichnungen veröffentlicht haben, auch wenn die Richtlinie auf einen einzelnen Benutzer beschränkt ist. 
    >
    > Diese Richtlinie ist erforderlich, damit Microsoft Cloud App Security alle Bezeichnungen im Admin Center für Bezeichnungen identifizieren und im Microsoft Cloud App Security-Portal anzeigen kann.

Nachdem Sie Ihre Bezeichnungen und Richtlinien migriert haben, fahren Sie mit dem [Konfigurieren von erweiterten Einstellungen für Bezeichnungen](#configuring-advanced-labeling-settings) fort, um erweiterte Konfigurationseinstellungen abzudecken, die nicht migriert wurden.

## <a name="configuring-advanced-labeling-settings"></a>Konfigurieren von erweiterten Einstellungen für Bezeichnungen

Wie während der [Planungsphase](#planning-your-migration) erklärt wurde, werden einige erweiterte Einstellungen für Bezeichnungen nicht automatisch migriert und müssen für die Plattform für einheitliche Bezeichnungen neu konfiguriert werden.

Weitere Informationen finden Sie in folgenden Quellen:

- [Konfigurieren von erweiterten Einstellungen für Bezeichnungen in PowerShell](#configure-advanced-labeling-settings-in-powershell)
- [Definieren von Bezeichnungsbedingungen im Admin Center für Bezeichnungen](#define-label-conditions-in-the-labeling-admin-center)

### <a name="configure-advanced-labeling-settings-in-powershell"></a>Konfigurieren von erweiterten Einstellungen für Bezeichnungen in PowerShell

1. Stellen Sie eine Verbindung mit dem PowerShell-Modul Office 365 Security & Compliance Center her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).

1. Um eine erweiterte Einstellung für Bezeichnungen zu definieren, verwenden Sie das Cmdlet **Set-Label**, wobei Sie den Parameter **AdvancedSettings**, die Bezeichnung, auf die Sie die Einstellung anwenden möchten, sowie Schlüssel-Wert-Paare zum Definieren Ihrer Einstellung angeben.
    
    Verwenden Sie die folgende Syntax:

    ```PowerShell
    Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{<Key>="<value1>,<value2>"}
    ```

    Hierbei gilt:
    - **`<LabelGUIDorName>`** identifiziert Ihre Bezeichnung unter Verwendung des Bezeichnungsnamens oder der GUID.
    - **`<Key>`** ist der Schlüssel oder Name der erweiterten Einstellung, die Sie für das Gerät festlegen möchten.
    - **`<Value>`** ist der Einstellungswert, den Sie definieren möchten. Umschließen Sie Ihren Wert in Anführungszeichen, und trennen Sie mehrere Werte durch Kommas. Leerzeichen werden nicht unterstützt.

1. Beginnen Sie, indem Sie die folgenden erweiterten Einstellungen konfigurieren:

    - [Festlegen einer Farbe für die Bezeichnung](rms-client/clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)
    - [Festlegen einer standardmäßigen untergeordneten Bezeichnung für eine übergeordnete Bezeichnung](rms-client/clientv2-admin-guide-customizations.md#specify-a-default-sublabel-for-a-parent-label)
    - [Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](rms-client/clientv2-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)
    - [Definieren von Bezeichnungen mit benutzerdefinierten Eigenschaften](rms-client/clientv2-admin-guide-customizations.md#migrate-labels-from-secure-islands-and-other-labeling-solutions) 
    - [Definieren von Bezeichnungsübersetzungen](https://docs.microsoft.com/powershell/module/exchange/set-label) 

    Weitere Informationen zu den verfügbaren erweiterten Konfigurationseinstellungen finden Sie im [Admin Guide: Custom configurations for the Azure Information Protection unified labeling client](rms-client/clientv2-admin-guide-customizations.md) (Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client für einheitliche Bezeichnungen).

> [!NOTE]
> Damit Sie die Einstellungen nutzen können, die Sie für die Plattform für einheitliche Bezeichnungen definiert haben, muss der Client für einheitliche Bezeichnungen auf den Computern der Endbenutzer installiert sein. 
>
> Diese erweiterten Einstellungen können nicht für Benutzer vorgenommen werden, die nur über integrierte Bezeichnungen von Office 365 verfügen.
> 

### <a name="define-label-conditions-in-the-labeling-admin-center"></a>Definieren von Bezeichnungsbedingungen im Admin Center für Bezeichnungen

Durch Bedingungen für einheitliche Bezeichnungen wird eine größere Flexibilität und eine bessere Genauigkeit erreicht als bei ihren Pendants, die im Azure-Portal erstellt wurden. 

Wenn Sie die Bedingungsfeatures für einheitliche Bezeichnungen nutzen möchten, erstellen Sie manuell eigene Bezeichnungsbedingungen in Ihrem Admin Center für Bezeichnungen, wie z. B.:

- Microsoft 365 Compliance Center
- Microsoft 365 Security Center
- Microsoft 365 Security & Compliance Center

Weitere Informationen finden Sie in der Dokumentation zu Microsoft 365 im Artikel [Informationen zu Vertraulichkeitsbezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#what-sensitivity-labels-can-do).

> [!TIP]
> Wenn Sie über benutzerdefinierte vertrauliche Datentypen verfügen, die für die Verwendung mit Office 365 DLP oder Microsoft Cloud App Security erstellt wurden, wenden Sie diese unverändert auf die einheitlichen Bezeichnungen an. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically).
>  

## <a name="deploy-a-unified-labeling-client"></a>Bereitstellen eines Clients für einheitliche Bezeichnungen

Stellen Sie einen Client bereit, der einheitliche Bezeichnungen für alle Computer der Benutzer unterstützt. So können Sie gewährleisten, dass diese Ihre Richtlinien für einheitliche Bezeichnungen und die Bezeichnungen selbst tatsächlich nutzen können. 

Die Benutzer benötigen einen unterstützten Clientcomputer, der eine Verbindung mit Ihrem Admin Center für Bezeichnungen herstellen und die Richtlinie für einheitliche Bezeichnungen abrufen kann. 

Weitere Informationen finden Sie in folgenden Quellen:
- [Nicht-Windows-Plattformen](#non-windows-platforms)
- [Windows-Plattformen](#windows-platforms)
- [Was ändert sich für Endbenutzer des klassischen Clients?](#what-changes-for-classic-client-end-users)

### <a name="non-windows-platforms"></a>Nicht-Windows-Plattformen

Für Benutzer von Nicht-Windows-Plattformen werden die Funktionen für einheitliche Bezeichnungen direkt in die Office-Clients integriert, sodass sie sämtliche von Ihnen veröffentlichten Bezeichnungen umgehend verwenden können. 

Zu den Office-Clients mit integrierten Funktionen für einheitliche Bezeichnungen gehören: 

- Office-Clients für macOS
- Office für das Web (Vorschau)
- Outlook Web App
- Outlook für mobile Geräte

Weitere Informationen zur einheitlichen Bezeichnungen auf diesen Plattformen finden Sie auf der Website des Microsoft-Supports unter [Anwenden von Vertraulichkeitsbezeichnungen auf Ihre Dateien und E-Mails in Office](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9). 

### <a name="windows-platforms"></a>Windows-Plattformen

Verwenden Sie für Windows-Computer mit Microsoft 365 Apps for Enterprise die integrierte Unterstützung für Bezeichnungen, die in Office-Versionen 1910 und höher bereitgestellt wird, oder installieren Sie den Azure Information Protection-Client für einheitliche Bezeichnungen, um die AIP-Funktionalität auf den Datei-Explorer oder PowerShell zu erweitern.

Weitere Informationen finden Sie in folgenden Quellen: 

- [Vergleichen der Bezeichnungsclients für Windows-Computer](rms-client/use-client.md#compare-the-labeling-clients-for-windows-computers)
- [Schnellstart: Bereitstellen des Azure Information Protection-Clients (AIP) für einheitliche Bezeichnungen](quickstart-deploy-client.md)

Der Azure Information Protection-Client für einheitliche Bezeichnungen kann aus dem [Microsoft Download Center](https://aka.ms/aipclient) heruntergeladen werden. 

Stellen Sie sicher, dass Sie die Datei **AzInfoProtection_UL** verwenden, um den Client bereitzustellen. Wenn Sie zurzeit den klassischen Client auf dem Computer installiert haben, wird bei der Installation des Clients für einheitliche Bezeichnungen ein direktes Upgrade durchgeführt.

> [!NOTE]
> Achten Sie darauf, welche AIP-Funktionalität aktuell von Ihrer Organisation benötigt wird, wenn Sie bestimmen, wann die integrierte Bezeichnung und wann der Client für einheitliche Bezeichnungen verwendet werden soll. 
>> 

### <a name="what-changes-for-classic-client-end-users"></a>Was ändert sich für Endbenutzer des klassischen Clients?

Der wichtigste, am meisten sichtbare Unterschied für Endbenutzer, die den klassischen Azure Information Protection -Client verwendet haben, besteht darin, dass die Schaltfläche **Schutz** in Office-Apps durch die Schaltfläche **Vertraulichkeit** ersetzt wurde. 

Wenn Sie die zusätzlichen Funktionen nutzen, die von Vertraulichkeitsbezeichnungen und einheitlichen Bezeichnungen unterstützt werden, sehen Endbenutzer diese Änderungen auch in Ihren Office-Anwendungen.

Beispiel:

- **Klassischer Windows-AIP-Client**

    :::image type="content" source="media/infoprotect-protectbutton-pulldown.png" alt-text="Schaltfläche „Schutz“ im klassischen Client":::

- **Windows-AIP-Client für einheitliche Bezeichnungen**

    :::image type="content" source="media/qs-tutor/sample-aip-client-office.PNG" alt-text="Schaltfläche „Beispiel“ für den Client für einheitliche Bezeichnungen in Microsoft Office":::

> [!TIP]
> Wenn Sie Ihre Bezeichnungen veröffentlicht haben und die Clients mit integrierter Unterstützung nicht die Schaltfläche **Vertraulichkeit** anzeigen, überprüfen Sie ggf. das entsprechende Handbuch zur Problembehandlung.
>
 
## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihre Bezeichnungen, Richtlinien und bereitgestellten Clients nach Bedarf migriert haben, verwalten Sie die Bezeichnungen und Bezeichnungsrichtlinien weiterhin [ ausschließlich in Ihrem Admin Center für Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels), z. B. im Microsoft 365 Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Security & Compliance Center.

Bei Verwendung der Plattform für einheitliche Bezeichnungen müssen Sie zurück zum Bereich „Azure Information Protection“ im Azure-Portal kehren, um Folgendes auszuführen:

- [Verwenden des AIP-Scanners](deploy-aip-scanner.md)
- [Überwachen der Bezeichnungsaktivitäten mithilfe von AIP-Analysen](reports-aip.md)

Es wird empfohlen, dass Endbenutzer integrierte Bezeichnungsfunktionen in den neuesten Office-Apps für Web, Mac, iOS und Android sowie Microsoft 365 Apps for Enterprise nutzen. 

Um zusätzliche AIP-Features zu nutzen, die noch nicht von integrierten Bezeichnungen unterstützt werden, wird die Verwendung des neuesten Clients für einheitliche Bezeichnungen für Windows empfohlen.
