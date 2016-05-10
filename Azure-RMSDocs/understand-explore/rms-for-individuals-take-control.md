---
# required metadata

title: Möglichkeiten der Kontrolle über die für RMS for Individuals erstellten Konten durch Administratoren | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a83880d0-f0f9-4a32-9e00-2f6635d7cc8d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Möglichkeiten der Kontrolle über die für RMS für Einzelpersonen erstellten Konten durch Administratoren

Wenn Sie das „RMS für Einzelpersonen“-Abonnement Ihrer Organisation nicht in ein kostenpflichtiges Abonnement umwandeln möchten, können Sie immer noch die Benutzerkonten im Azure-Verzeichnis, das für Ihre Organisation erstellt wurde, auf die folgenden Arten kontrollieren:

-   Implementieren Sie Verzeichnisintegrationslösungen für Azure Active Directory und Ihre Active Directory-Domänendienste-Infrastruktur. Sie können Konten und Kennwörter synchronisieren, sodass Benutzer keine neuen Konten für die Verwendung von Rights Management erstellen müssen, und Ihre lokalen Kennwortrichtlinien gelten weiterhin auch für die neuen Azure-Benutzerkonten. Sie können auch Kennwörter synchronisieren, sodass Benutzer sich kein anderes Kennwort für die Verwendung von Rights Management merken müssen.

-   Sie könnten Benutzer daran hindern, sich anzumelden, um Azure Rights Management mit dem RMS for Individuals-Abonnement zu verwenden. In den meisten Fällen bringt dies kaum Vorteile, weil Benutzer dann Dateien ohne Schutz freigeben (was ein Risiko für Ihr Unternehmen bedeuten kann) oder einen anderen Dateischutzmechanismus verwenden werden, der der IT-Abteilung nicht die Möglichkeit für den Zugriff auf die Daten bietet. Wenn Sie jedoch Benutzer an der Registrierung für die Verwendung von RMS for Individuals hindern möchten, führen Sie eine der folgenden Aktionen aus, nachdem Sie in Azure den Besitz des Verzeichnisses Ihrer Organisation übernommen haben:

    -   Hindern Sie alle Benutzer daran, sich für Self-Service-Abonnements zu registrieren, die RMS for Individuals umfassen.  Derzeit kann dies nicht nach Dienst festgelegt werden, sondern die Einstellung wird auf alle Azure-Abonnements angewendet, die den Self-Service-Prozess nutzen. Legen Sie hierzu den Parameter **AllowAdHocSubscriptions** mit dem Cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) aus dem Windows PowerShell-Modul für Azure Active Directory auf „false“ fest. Beispiel: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Hindern Sie Benutzer an der Erstellung eines neuen Kontos in Azure, was bedeutet, dass nur Benutzer, die bereits ein Konto in Azure haben, sich für Self-Service-Abonnements registrieren können, wozu auch RMS for Individuals gehört.  Legen Sie hierzu den Parameter **AllowEmailVerifiedUsers** mit dem Cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) aus dem Windows PowerShell-Modul für Azure Active Directory auf „false“ fest. Beispiel: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Synchronisieren Sie Ihre Active Directory-Domänendienste-Infrastruktur mit Azure Active Directory. Diese Aktion verhindert, dass neue Konten erstellt werden, wenn sich Benutzer für Self-Service-Abonnements wie RMS for Individuals registrieren, und Sie können Konten löschen oder deaktivieren, die zuvor im Azure-Verzeichnis erstellt wurden.

Um die Benutzerkonten im Azure-Verzeichnis zu kontrollieren oder Benutzer daran zu hindern, sich für RMS für Einzelpersonen zu registrieren, müssen Sie ein Azure-Abonnement besitzen und Besitzer des Verzeichnisses sein. Wenn Sie noch kein Azure-Abonnement haben, können Sie sich eines beschaffen, für das keine Kosten anfallen. Wenn während des Self-Service-Prozesses automatisch ein Verzeichnis für Sie erstellt wurde, übernehmen Sie den Besitz der Domäne, die zu dessen Erstellung verwendet wurde. Wenn Sie bereits ein Verzeichnis in Azure besitzen, Benutzer aber eine neue Domäne angegeben haben, die Sie in Ihrer Organisation verwenden, führen Sie diese Domäne mit Ihrem vorhandenen Verzeichnis zusammen. Weitere Informationen finden Sie in den Anweisungen in [Was ist die Self-Service-Registrierung für Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)


## Nächste Schritte

Wenn Benutzer anstelle von Administratoren ihre Konten in Azure Active Directory für RMS for Individuals erstellen können, wie kann dann ermittelt werden, ob sie diesen Schritt auch ausgeführt haben?  Weitere Informationen finden Sie unter [So ermitteln Sie, ob Ihre Benutzer sich für RMS for Individuals registriert haben](rms-for-individuals-identify-sign-up.md).


<!--HONumber=Apr16_HO3-->

