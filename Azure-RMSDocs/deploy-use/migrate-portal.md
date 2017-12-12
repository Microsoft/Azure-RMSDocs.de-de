---
title: "Migrieren aus dem klassischen Azure-Portal – AIP"
description: "Sofort erkennbare Administratoraufgaben, die Sie bisher im klassischen Azure-Portal ausgeführt haben"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 57a1073c-02e0-441b-bf49-c6b72fdba24f
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 3beb637b4a9ffe662455f32281e24ecfeb230bca
ms.sourcegitcommit: 43d77093d97509170bbdfa72bc28e1c2100228ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2017
---
# <a name="tasks-that-you-used-to-do-with-the-azure-classic-portal"></a>Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben

>*Gilt für: Azure Information Protection, Office 365*

Sind Sie mit der Verwaltung des Azure Rights Management-Diensts über das klassische Azure-Portal vertraut und benötigen Hilfe beim Übergang zum Azure-Portal? 

> [!NOTE]
> Das klassische Azure-Portal wird am **08. Januar 2018** abgeschaltet. Wenn Sie nach diesem Datum versuchen, auf das Portal zuzugreifen, werden Sie automatisch an das neue Azure-Portal weitergeleitet. 
> 
> Weitere Informationen finden Sie in der Ankündigung im Blog [Marching into the future of the Azure AD admin experience: retiring the Azure classic portal (Auf dem Weg in die Zukunft der Azure AD-Administratorbenutzeroberfläche: Abschalten des klassischen Azure-Portals)](https://blogs.technet.microsoft.com/enterprisemobility/2017/09/18/marching-into-the-future-of-the-azure-ad-admin-experience-retiring-the-azure-classic-portal/). Informationen zur kurzfristigen Verschiebung des Abschaltdatums finden Sie unter [Update on retirement of Azure AD classic portal experience and migration of conditional access policies](https://cloudblogs.microsoft.com/enterprisemobility/2017/11/29/update-on-retirement-of-azure-ad-classic-portal-experience-and-migration-of-conditional-access-policies/) (Update zur Abschaltung des klassischen Azure AD-Portals und Migration der Richtlinien für den bedingten Zugriff).

## <a name="how-to-do-your-familiar-admin-tasks"></a>Ausführen Ihrer bekannten Administratoraufgaben

Verwenden Sie die folgenden Informationen, um schnell zum neueren Portal überzugehen:

|Klassisches Azure-Portal|So führen Sie die Aufgabe im Azure-Portal aus
|-----------|--------------------|
|Erstmaliges Zugreifen auf die Konfigurationseinstellungen|1. Melden Sie sich als globaler Administrator oder Sicherheitsadministrator für Ihren Mandanten beim Azure-Portal an.<br /><br />2. Klicken Sie im Hubmenü auf **Neu**, und wählen Sie dann in der Liste **MARKETPLACE** die Option **Sicherheit und Identität** aus.<br /><br />3. Wählen Sie auf dem Blatt **Sicherheit und Identität** in der Liste **AUSGEWÄHLTE APPS** die Option **Azure Information Protection** aus. Klicken Sie dann auf dem Blatt **Azure Information Protection** auf **Erstellen**.<br /><br />Dadurch wird das Blatt **Azure Information Protection** erstellt. Wenn Sie sich das nächste Mal beim Portal anmelden, können Sie den Dienst im Hubmenü aus der Liste unter **Weitere Dienste** auswählen.
|Erstellen einer neuen Vorlage|Erstellen Sie eine Bezeichnung, die Schutz anwendet, und verwenden Sie **Set permissions** (Berechtigungen festlegen), um die Berechtigungen, das Ablaufdatum und den Offlinezugriff zu definieren. <br /><br />Im Hintergrund wird durch diese Konfiguration eine neue benutzerdefinierte Vorlage erstellt, auf die dann über Dienste und Anwendungen zugegriffen werden kann, die in Rights Management-Vorlagen integriert werden.<br /><br />Weitere Informationen finden Sie unter [So erstellen Sie eine neue Vorlage](configure-policy-templates.md#to-create-a-new-template).
|Bearbeiten der Vorlageneigenschaften: <br /><br />– Vorlagenname und -beschreibung<br /><br />– Einstellungen zu Nutzungsrechten, zum Ablauf von Inhalten und zum Offlinezugriff|Wenn nicht bereits geschehen, [konvertieren Sie die Vorlage in eine Bezeichnung](configure-policy-templates.md#to-convert-templates-to-labels), und gehen Sie dann wie folgt vor:<br /><br />1. Ändern Sie den Namen und die Beschreibung der Bezeichnung<br /><br />2. Ändern Sie die Projekteinstellungen der Bezeichnung, um die Einstellungen für Berechtigungen, das Ablaufdatum und den Offlinezugriff zu aktualisieren.<br /><br />Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection).
|Archivieren einer Vorlage|Legen Sie den Status der Bezeichnung auf **Deaktiviert** fest.
|Erstellen einer bereichsbezogenen Vorlage|Erstellen Sie eine bereichsbezogene Richtlinie, und erstellen Sie in diesem Bereich eine Bezeichnung, die Schutz anwendet. <br /><br />Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md).
|Kopieren einer Vorlage|Sie können eine Vorlage im Azure-Portal nicht kopieren. Wenn Sie möchten, dass zwei Vorlagen über die gleichen Schutzeinstellungen verfügen, müssen Sie die Berechtigungen für jede Bezeichnung festlegen. <br /><br />Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection).
|Löschen einer Vorlage|Das Löschen von Vorlagen kann zu nicht zugreifbaren Daten führen, weshalb das Azure-Portal diesen Vorgang nicht unterstützt. Sie können die Bezeichnung jedoch löschen und dann das PowerShell-Cmdlet [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) verwenden, um die Vorlage zu entfernen. <br /><br />Weitere Informationen finden Sie unter [Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection](configure-policy-delete-reorder.md).
|Unterstützung mehrerer Sprachen|Wählen Sie in der Menüauswahl **Verwalten** **Sprachen (Vorschau)** aus, um die anpassbaren Felder zu exportieren, die den Namen und die Beschreibung der Vorlage umfassen. Übersetzen Sie die Zeichenfolgen, und importieren Sie diese anschließend in das Portal. <br /><br />Weitere Informationen finden Sie unter [Vorgehensweise beim Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection](configure-policy-languages.md).
|Rights Management-Webberichte|Verwenden Sie das PowerShell-Cmdlet [Get-AadrmUsageLog](/powershell/module/aadrm/Get-AadrmUsageLog), um Nutzungsprotokolle für den Azure Rights Management-Dienst herunterzuladen. Sie können diese Daten dann dazu verwenden, benutzerdefinierte Berichte zu erstellen. <br /><br />Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](log-analyze-usage.md).<br /><br />Tipp: Im [Blog von Enterprise Mobility and Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) finden Sie immer die aktuellsten Ankündigungen einer neuen zentralisierten Berichterstellungslösung für Azure Information Protection. 
|Aktivieren und Deaktivieren des Rights Management-Diensts|Wählen Sie aus den Menüoptionen **VERWALTEN** **RMS-Einstellungen** oder **Protection activation** (Schutzaktivierung) aus. Diese Option wird zurzeit umbenannt.<br /><br />Weitere Informationen finden Sie unter [How to activate Azure Rights Management from the Azure portal (Aktivieren von Azure Rights Management aus dem Azure-Portal)](activate-azure.md).

Bevor Sie Ihre Vorlagen im Azure-Portal bearbeiten oder in Bezeichnungen konvertieren, informieren Sie sich unter [Überlegungen zu Vorlagen im Azure-Portal](configure-policy-templates.md#considerations-for-templates-in-the-azure-portal).


## <a name="what-else-has-changed"></a>Was sich sonst noch geändert hat

Neue Funktionen im Azure-Portal:

- Sie können die [Standardvorlagen](configure-policy-templates.md#default-templates) bearbeiten, die automatisch für Ihre Organisation erstellt werden.

- Sie können Vorlagen in Bezeichnungen konvertieren, sodass Sie ein einzelnes Objekt verwalten, anstatt eine Vorlage und eine Bezeichnung unabhängig zu verwalten. Anweisungen finden Sie unter [Konvertieren von Vorlagen in Bezeichnungen](configure-policy-templates.md#to-convert-templates-to-labels).

Unterstützung für die Rolle „Sicherheitsadministrator“: Während Sie sich beim klassischen Azure-Portal als globaler Administrator anmelden mussten, um Azure Rights Management zu konfigurieren, können Sie sich beim Azure-Portal für die Konfiguration von Azure Information Protection mit einem Konto anmelden, das über die Rolle „Globaler Administrator“ oder „Sicherheitsadministrator“ verfügt. 

Die PowerShell-Cmdlets zum Erstellen und Verwalten von Vorlagen und zum Aktivieren oder Deaktivieren des Diensts bleiben unverändert unterstützt.


## <a name="see-also"></a>Weitere Informationen:
Ausführlichere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](../deploy-use/configure-policy-templates.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]