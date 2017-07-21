---
title: "Aktivieren von Azure RMS mit dem klassischen Azure-Portal – AIP"
description: "Aktivierungsanweisungen für den Azure Rights Management-Dienst, wenn Sie auf das Azure-Portal zugreifen können. Sie verfügen z.B. über ein Abonnement für Enterprise Mobility Suite oder Azure Information Protection Premium."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/19/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1066ff9dc628c5df379fe3ce9126b42639ed23b1
ms.sourcegitcommit: 52ad844cd42479a56b1ae0e56ba0614f088d8a1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2017
---
# <a name="how-to-activate-azure-rights-management-from-the-azure-classic-portal"></a>Aktivieren von Azure Rights Management über das klassische Azure-Portal

>*Gilt für: Azure Information Protection*


Verwenden Sie diese Anleitung, wenn Sie Zugriff auf das Azure-Portal haben. Sie verfügen z.B. über ein Abonnement für Enterprise Mobility Suite oder Azure Information Protection Premium.

> [!TIP]
> Zweiminütiges Video [How to activate Azure RMS](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms) (Aktivieren von Azure RMS)

1.  Nachdem Sie sich für Ihr Azure-Konto registriert haben, [melden Sie sich am klassischen Azure-Portal an](http://go.microsoft.com/fwlink/p/?LinkID=275081). Verwenden Sie ein globales Administratorkonto wie z.B. das Konto, das Sie verwendet haben, um das Abonnement abzuschließen, das Azure Rights Management enthält.

2.  Klicken Sie im linken Bereich auf **ACTIVE DIRECTORY**.

3.  Klicken Sie auf der Seite **Active Directory** auf **RIGHTS MANAGEMENT**.

4.  Wählen Sie das Verzeichnis aus, für das Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] verwalten möchten, klicken Sie auf **AKTIVIEREN**, und bestätigen Sie Ihre Aktion.

    > [!NOTE]
    >Wenn ein Aktivierungsfehler angezeigt wird, kann der Grund dafür sein, dass Ihr Serviceplan oder Ihre Produktversion den Azure Rights Management-Dienst für Azure Information Protection nicht beinhaltet.
    >
    >Zum Aktivieren des Azure Rights Management-Diensts benötigen Sie entweder einen [Azure Information Protection Premium-Plan](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) oder einen [Office 365-Plan, der Rights Management umfasst](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Wenn Sie Hilfe zu diesem Problem benötigen, senden Sie eine E-Mail-Nachricht an das [Askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).


Der **RECHTEVERWALTUNGSSTATUS** sollte nun **Aktiv** anzeigen, und die Option **AKTIVIEREN** wird durch **DEAKTIVIEREN**ersetzt.

## <a name="rights-management-status-values-and-descriptions-in-the-azure-classic-portal"></a>Rights Management-Statuswerte und -Beschreibungen im klassischen Azure-Portal
Zusätzlich zum Status **Aktiv** , der angibt, dass der Rights Management-Dienst aktiviert und einsatzbereit ist, wird darüber hinaus möglicherweise **Inaktiv**, **Nicht verfügbar**oder **Nicht autorisiert**angezeigt.

|Statuswert|Beschreibung|
|----------------|---------------|
|**Aktiv**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ist aktiviert und kann verwendet werden.|
|**Inaktiv**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ist deaktiviert und muss aktiviert werden, bevor Ihre Organisation Dateien schützen kann.|
|**Nicht verfügbar**|Der [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] Service ist nicht verfügbar. Versuchen Sie es später erneut.|
|**Nicht autorisiert**|Sie sind nicht berechtigt, den Status des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] Services anzuzeigen. Ihr Konto ist z. B. gesperrt, oder Sie sind nicht der globale Administrator für den ausgewählten Mandanten.|

## <a name="next-steps"></a>Nächste Schritte
Zurück zu [Aktivieren von Azure Rights Management](activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]