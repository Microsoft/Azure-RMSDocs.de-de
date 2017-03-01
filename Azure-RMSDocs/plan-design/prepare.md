---
title: "Vorbereiten für den Schutz durch Azure Rights Management – AIP"
description: "Überprüfen Sie, ob alles für die Verwendung des Azure Rights Management-Diensts bereit ist, sodass Ihre Organisation Dokumente und E-Mails schützen kann."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 909becbdf902d552a967506b80f173e59cf756c7
ms.lasthandoff: 02/24/2017


---

# <a name="preparing-for-azure-information-protection"></a>Vorbereiten für Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Damit Sie Azure Information Protection für Ihre Organisation bereitstellen können, muss Folgendes vorhanden sein:

-   Benutzerkonten und -gruppen in der Cloud, die Sie manuell erstellt haben oder die aus den Active Directory-Domänendiensten (AD DS) automatisch erstellt und synchronisiert wurden.

    Wenn Sie Ihre lokalen Konten und Gruppen synchronisieren, müssen nicht alle Attribute synchronisiert werden. Eine Liste mit den Attributen, die für den in Azure Information Protection verwendeten Azure Rights Management-Dienst synchronisiert werden müssen, finden Sie im [Abschnitt zu Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) in der Azure Active Directory-Dokumentation. Zur Vereinfachung der Bereitstellung empfehlen wir die Verwendung von [Azure Connect AD](/active-directory/active-directory-aadconnectsync-whatis) zum Verbinden Ihrer lokalen Verzeichnisse mit Azure Active Directory. Sie können aber auch jede andere Synchronisierungsmethode wählen, mit der dasselbe Ergebnis erzielt wird.

-   E-Mail-aktivierte Gruppen in der Cloud, die Sie für Azure Information Protection verwenden möchten. Das können integrierte oder manuell erstellte Gruppen sein, die Benutzer enthalten, die geschützte Dokumente und E-Mails verwenden sollen.

    Wenn Sie über Exchange Online verfügen, können Sie im Exchange Admin Center E-Mail-fähige Gruppen erstellen und nutzen. Wenn Sie AD DS haben und die Synchronisierung mit Azure AD vornehmen, können Sie E-Mail-fähige Gruppen erstellen und verwenden, die entweder Sicherheits- oder Verteilergruppen sind.

## <a name="activate-the-rights-management-service-for-data-protection"></a>Aktivieren des Rights Management-Diensts für den Schutz von Daten
Wenn alles für den Schutz von Dokumenten und E-Mails bereit ist, aktivieren Sie den Rights Management-Dienst, um diese Technologie anzuwenden. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



