---
title: "Vorbereiten für den Schutz durch Azure Rights Management – AIP"
description: "Überprüfen Sie, ob alles für die Verwendung des Azure Rights Management-Diensts bereit ist, sodass Ihre Organisation Dokumente und E-Mails schützen kann."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4b074f9a9a3d72b4d1ab5810b69e92b4792b0711
ms.sourcegitcommit: 16fec44713c7064959ebb520b9f0857744fecce9
translationtype: HT
---
# <a name="preparing-for-azure-information-protection"></a>Vorbereiten für Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Damit Sie Azure Information Protection für Ihre Organisation bereitstellen können, muss Folgendes vorhanden sein:

-   Benutzerkonten und -gruppen in der Cloud, die Sie manuell erstellt haben oder die aus den Active Directory-Domänendiensten (AD DS) automatisch erstellt und synchronisiert wurden.

    Wenn Sie Ihre lokalen Konten und Gruppen synchronisieren, müssen nicht alle Attribute synchronisiert werden. Eine Liste mit den Attributen, die für den in Azure Information Protection verwendeten Azure Rights Management-Dienst synchronisiert werden müssen, finden Sie im [Abschnitt zu Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) in der Azure Active Directory-Dokumentation. Zur Vereinfachung der Bereitstellung empfehlen wir die Verwendung von [Azure Connect AD](/active-directory/active-directory-aadconnectsync-whatis) zum Verbinden Ihrer lokalen Verzeichnisse mit Azure Active Directory. Sie können aber auch jede andere Synchronisierungsmethode wählen, mit der dasselbe Ergebnis erzielt wird.

-   E-Mail-aktivierte Gruppen in der Cloud, die Sie für Azure Information Protection verwenden möchten. Das können integrierte oder manuell erstellte Gruppen sein, die Benutzer enthalten, die geschützte Dokumente und E-Mails verwenden sollen.

    Wenn Sie über Exchange Online verfügen, können Sie im Exchange Admin Center E-Mail-fähige Gruppen erstellen und nutzen. Wenn Sie AD DS haben und die Synchronisierung mit Azure AD vornehmen, können Sie E-Mail-fähige Gruppen erstellen und verwenden, die entweder Sicherheits- oder Verteilergruppen sind.

### <a name="group-membership-caching"></a>Zwischenspeichern der Gruppenmitgliedschaft

Aus Leistungsgründen wird die Gruppenmitgliedschaft vom Azure Rights Management-Dienst zwischengespeichert. Dies bedeutet, dass die Änderungen an der Gruppenmitgliedschaft bis zu drei Stunden benötigen, bis sie wirksam sind. Änderungen dieses Zeitraums sind vorbehalten. Denken Sie daran, diese Verzögerung in alle Änderungen oder Tests mit einzubeziehen, die Sie während der Verwendung von Gruppen in Ihrer Konfiguration des Azure Rights Management-Diensts vornehmen, z.B. das Konfigurieren von [benutzerdefinierten Vorlagen](../deploy-use/configure-custom-templates.md), oder wenn Sie eine Gruppe für die [Administratorfunktion](../deploy-use/configure-super-users.md) verwenden. 

### <a name="considerations-if-email-addresses-change"></a>Überlegungen bei einer Änderung der E-Mail-Adressen

Wenn Sie Nutzungsrechte für Benutzer oder Gruppen konfigurieren und diese nach ihrem Anzeigenamen auswählen, wird Ihre Auswahl mit der E-Mail-Adresse des jeweiligen Objekts gespeichert. Wenn die E-Mail-Adresse später geändert wird, werden die ausgewählten Benutzer nicht erfolgreich autorisiert.

Bei einer Änderung von E-Mail-Adressen wird empfohlen, dass Sie die alte E-Mail-Adresse als Proxy-E-Mail-Adresse (auch Alias oder alternative E-Mail-Adresse genannt) zum Benutzer oder zur Gruppe hinzufügen. Auf diese Weise bleiben die zuvor zugewiesenen Nutzungsrechte erhalten. Wenn diese Vorgehensweise nicht möglich ist, müssen Sie den Benutzer oder die Gruppe aus Ihrer Konfiguration entfernen und erneut auswählen, um die aktualisierte E-Mail-Adresse zu speichern. Anschließend wird für neu geschützten Inhalt die neue E-Mail-Adresse verwendet.

Beispielsweise können Benutzer oder Gruppen für benutzerdefinierte Rights Management-Vorlagen nach dem Anzeigenamen ausgewählt werden, um Nutzungsrechte zuzuweisen. Benutzer können Benutzer und Gruppen auch nach ihrem Anzeigenamen auswählen, wenn sie benutzerdefinierte Berechtigungen mit dem Azure Information Protection-Client konfigurieren.

## <a name="activate-the-rights-management-service-for-data-protection"></a>Aktivieren des Rights Management-Diensts für den Schutz von Daten
Wenn alles für den Schutz von Dokumenten und E-Mails bereit ist, aktivieren Sie den Rights Management-Dienst, um diese Technologie anzuwenden. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


