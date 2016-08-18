---
title: "Aktivieren von Azure Rights Management über das klassische Azure-Portal | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/27/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b214d7951820c8cb98c5d6f81af3325597ea72ec
ms.openlocfilehash: 9cde79791e8c2b04d1d7622f5aa69d654a70646e


---

# Aktivieren von Azure Rights Management über das klassische Azure-Portal

*Gilt für: Azure Rights Management*


Verwenden Sie diese Anleitung, wenn Sie Zugriff auf das Azure-Portal haben. Sie verfügen z.B. über ein Abonnement für Enterprise Mobility Suite oder Azure Rights Management Premium.

> [!TIP]
> Zweiminütiges Video [How to activate Azure RMS](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms) (Aktivieren von Azure RMS)

1.  Nachdem Sie sich für Ihr Azure-Konto registriert haben, [melden Sie sich am klassischen Azure-Portal an](http://go.microsoft.com/fwlink/p/?LinkID=275081). Verwenden Sie ein globales Administratorkonto wie z.B. das Konto, das Sie verwendet haben, um das Abonnement abzuschließen, das Azure Rights Management enthält.

2.  Klicken Sie im linken Bereich auf **ACTIVE DIRECTORY**.

3.  Klicken Sie auf der Seite **Active Directory** auf **RIGHTS MANAGEMENT**.

4.  Wählen Sie das Verzeichnis aus, für das Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] verwalten möchten, klicken Sie auf **AKTIVIEREN**, und bestätigen Sie Ihre Aktion.

    > [!NOTE]
    >Wenn ein Aktivierungsfehler angezeigt wird, kann der Grund dafür sein, dass Ihr Serviceplan oder Ihre Produktversion [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] nicht beinhaltet.
    >
    >Verwenden Sie die Informationen unter [Cloud-Abonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md), um die RMS-Unterstützung zu bestätigen. Wenn Sie Hilfe zu diesem Problem benötigen, senden Sie eine E-Mail-Nachricht an das [Askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).


Der **RECHTEVERWALTUNGSSTATUS** sollte nun **Aktiv** anzeigen, und die Option **AKTIVIEREN** wird durch **DEAKTIVIEREN**ersetzt.

## Rights Management-Statuswerte und -Beschreibungen im klassischen Azure-Portal
Zusätzlich zum Status **Aktiv** , der angibt, dass der Rights Management-Dienst aktiviert und einsatzbereit ist, wird darüber hinaus möglicherweise **Inaktiv**, **Nicht verfügbar**oder **Nicht autorisiert**angezeigt.

|Statuswert|Beschreibung|
|----------------|---------------|
|**Aktiv**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ist aktiviert und kann verwendet werden.|
|**Inaktiv**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ist deaktiviert und muss aktiviert werden, bevor Ihre Organisation Dateien schützen kann.|
|**Nicht verfügbar**|Der [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] Service ist nicht verfügbar. Versuchen Sie es später erneut.|
|**Nicht autorisiert**|Sie sind nicht berechtigt, den Status des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] Services anzuzeigen. Ihr Konto ist z. B. gesperrt, oder Sie sind nicht der globale Administrator für den ausgewählten Mandanten.|

## Nächste Schritte
Zurück zu [Aktivieren von Azure Rights Management](activate-service.md).


<!--HONumber=Jun16_HO4-->


