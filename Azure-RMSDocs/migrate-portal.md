---
title: Migrieren aus dem klassischen Azure-Portal – AIP
description: Sofort erkennbare Administratoraufgaben, die Sie bisher im klassischen Azure-Portal ausgeführt haben
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 57a1073c-02e0-441b-bf49-c6b72fdba24f
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: e6558bd8cf750c200ae6ec4dd177f34d6a1c84ea
ms.sourcegitcommit: a2542aec8cd2bf96e94923740bf396badff36b6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67535194"
---
# <a name="tasks-that-you-used-to-do-with-the-azure-classic-portal"></a>Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Sind Sie mit der Verwaltung des Azure Rights Management-Diensts über das klassische Azure-Portal vertraut und benötigen Hilfe beim Übergang zum Azure-Portal?

Das klassische Azure-Portal wurde am **08. Januar 2018** abgeschaltet. Danach können Sie über das klassische Portal nicht mehr den Azure Rights Management-Dienst und benutzerdefinierte Vorlagen verwalten. Wenn Sie versuchen, auf das klassische Portal zuzugreifen, wird ein Link zum neuen Azure-Portal angezeigt.

Weitere Informationen zur Abschaltung des klassischen Portals finden Sie in der Ankündigung zum Blogbeitrag: [Marching into the future of the Azure AD admin experience: retiring the Azure classic portal (Auf dem Weg in die Zukunft der Azure AD-Administratorbenutzeroberfläche: Abschalten des klassischen Azure-Portals)](https://cloudblogs.microsoft.com/enterprisemobility/2017/09/18/marching-into-the-future-of-the-azure-ad-admin-experience-retiring-the-azure-classic-portal/). Informationen zur kurzfristigen Verschiebung des ursprünglichen Verkaufs-/Ausmusterungsdatums finden Sie unter [Update on retirement of Azure AD classic portal experience and migration of conditional access policies](https://cloudblogs.microsoft.com/enterprisemobility/2017/11/29/update-on-retirement-of-azure-ad-classic-portal-experience-and-migration-of-conditional-access-policies/) (Update zur Abschaltung des klassischen Azure AD-Portals und Migration der Richtlinien für den bedingten Zugriff).

## <a name="how-to-do-your-familiar-admin-tasks"></a>Ausführen Ihrer bekannten Administratoraufgaben

Verwenden Sie die folgenden Informationen, um schnell zum neuen Portal überzugehen.

|Klassisches Azure-Portal|So führen Sie die Aufgabe im Azure-Portal aus
|-----------|--------------------|
|Erstmaliges Zugreifen auf die Konfigurationseinstellungen|1. [Melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal).<br /><br />2. Führen Sie die Anweisungen für [Der Erste Zugriff auf das Blatt „Azure Information Protection“](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time) durch.
|Erstellen einer neuen Vorlage|Erstellen Sie eine Bezeichnung, die Schutz anwendet, und verwenden Sie **Set permissions** (Berechtigungen festlegen), um die Berechtigungen, das Ablaufdatum und den Offlinezugriff zu definieren. <br /><br />Im Hintergrund wird durch diese Konfiguration eine neue benutzerdefinierte Vorlage erstellt, auf die dann über Dienste und Anwendungen zugegriffen werden kann, die in Rights Management-Vorlagen integriert werden.<br /><br />Weitere Informationen finden Sie unter [So erstellen Sie eine neue Vorlage](configure-policy-templates.md#to-create-a-new-template).
|Bearbeiten der Vorlageneigenschaften: <br /><br />– Vorlagenname und -beschreibung<br /><br />– Einstellungen zu Nutzungsrechten, zum Ablauf von Inhalten und zum Offlinezugriff|Wenn nicht bereits geschehen, [konvertieren Sie die Vorlage in eine Bezeichnung](configure-policy-templates.md#to-convert-templates-to-labels), und gehen Sie dann wie folgt vor:<br /><br />1. Ändern Sie den Namen und die Beschreibung der Bezeichnung<br /><br />2. Ändern Sie die Projekteinstellungen der Bezeichnung, um die Einstellungen für Berechtigungen, das Ablaufdatum und den Offlinezugriff zu aktualisieren.<br /><br />Weitere Informationen finden Sie unter [So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen](configure-policy-protection.md#to-configure-a-label-for-protection-settings).
|Archivieren einer Vorlage|Legen Sie den Status der Bezeichnung auf **Deaktiviert** fest.
|Erstellen einer bereichsbezogenen Vorlage|Erstellen Sie eine bereichsbezogene Richtlinie, und erstellen Sie in diesem Bereich eine Bezeichnung, die Schutz anwendet. <br /><br />Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md).
|Kopieren einer Vorlage|Sie können eine Vorlage im Azure-Portal nicht kopieren. Wenn Sie möchten, dass zwei Vorlagen über die gleichen Schutzeinstellungen verfügen, müssen Sie die Berechtigungen für jede Bezeichnung festlegen. <br /><br />Weitere Informationen finden Sie unter [So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen](configure-policy-protection.md#to-configure-a-label-for-protection-settings).
|Löschen einer Vorlage|Das Löschen von Vorlagen kann zu nicht zugreifbaren Daten führen, weshalb das Azure-Portal diesen Vorgang nicht unterstützt. Sie können jedoch die Bezeichnung auch löschen und dann verwenden Sie das PowerShell [Remove-AipServiceTemplate](/powershell/module/aipservice/remove-aipservicetemplate) Cmdlet, um die Vorlage zu entfernen. <br /><br />Weitere Informationen finden Sie unter [Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection](configure-policy-delete-reorder.md).
|Unterstützung mehrerer Sprachen|Wählen Sie im Menü **Verwalten** **Sprachen** aus, um die anpassbaren Felder zu exportieren, die den Namen und die Beschreibung der Vorlage umfassen. Übersetzen Sie die Zeichenfolgen, und importieren Sie diese anschließend in das Portal. <br /><br />Weitere Informationen finden Sie unter [Vorgehensweise beim Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection](configure-policy-languages.md).
|Rights Management-Webberichte|Die [zentralisierte Berichterstellung für Azure Information Protection](reports-aip.md) ist ab sofort in der Vorschauversion verfügbar.<br /><br />Sie können auch die PowerShell [Get-AipServiceUsageLog](/powershell/module/aipservice/get-aipserviceuserlog) -Cmdlet zum Herunterladen der Protokolle für den Azure Rights Management-Dienst. Sie können diese Daten dann dazu verwenden, benutzerdefinierte Berichte zu erstellen. Weitere Informationen finden Sie unter [protokollieren und analysieren die Verwendung der Schutz von Azure Information Protection](log-analyze-usage.md).
|Aktivieren und Deaktivieren des Rights Management-Diensts|Wählen Sie im Menü **Verwalten** die Option **Protection activation** (Schutzaktivierung) aus.<br /><br />Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren Sie den Rights Management-Schutzdienst von Azure-Portal](activate-azure.md).

Bevor Sie Ihre Vorlagen im Azure-Portal bearbeiten oder in Bezeichnungen konvertieren, informieren Sie sich unter [Überlegungen zu Vorlagen im Azure-Portal](configure-policy-templates.md#considerations-for-templates-in-the-azure-portal).


## <a name="what-else-has-changed"></a>Was sich sonst noch geändert hat

Neue Funktionen im Azure-Portal:

- Sie können die [Standardvorlagen](configure-policy-templates.md#default-templates) bearbeiten, die automatisch für Ihre Organisation erstellt werden.

- Sie können Vorlagen in Bezeichnungen konvertieren, sodass Sie ein einzelnes Objekt verwalten, anstatt eine Vorlage und eine Bezeichnung unabhängig zu verwalten. Anweisungen finden Sie unter [Konvertieren von Vorlagen in Bezeichnungen](configure-policy-templates.md#to-convert-templates-to-labels).

- Unterstützung für andere Administratorrollen: Während Sie sich beim klassischen Azure-Portal als globaler Administrator anmelden mussten, um Azure Rights Management zu konfigurieren, können Sie sich beim Azure-Portal für die Konfiguration von Azure Information Protection mit einem Konto anmelden, das über eine der folgenden Administratorrollen verfügt: **Globaler Administrator**, **Sicherheitsadministrator**, **complianceadministrator**, **Daten complianceadministrator**, oder **Azure Information Protection-Administrator**. Weitere Informationen zu diesen Rollen finden Sie im Abschnitt [Verfügbare Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) in der Azure Active Directory-Dokumentation.

Die PowerShell-Cmdlets zum Erstellen und Verwalten von Vorlagen und zum Aktivieren oder Deaktivieren des Diensts werden weiterhin ohne Änderungen unterstützt.

## <a name="see-also"></a>Siehe auch
Ausführlichere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).

