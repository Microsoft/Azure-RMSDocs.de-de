---
# required metadata

title: "Gewusst wie: Verwenden der Dokumentenverfolgung | Azure RMS"
description: Die Funktion für die Dokumentenverfolgung erfordert einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung bei dem Dienst.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Vorgehensweise: Verwenden der Dokumentenverfolgung

Zum Verwenden der Funktion für die Dokumentenverfolgung sind einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung bei dem Dienst erforderlich.

## Verwalten der Metadaten für die Dokumentenverfolgung

Die Betriebssysteme, die die Dokumentenverfolgung unterstützen, weisen ähnliche Implementierungen auf. Dazu gehören eine Reihe von Eigenschaften (die Metadaten), ein neuer Parameter, der den Erstellungsmethoden für Benutzerrichtlinien hinzugefügt wurde, sowie eine Methode zum Registrieren der Richtlinie, die mit dem Dokumentenverfolgungsdienst verfolgt werden soll.

Im Prinzip sind nur für die Dokumentenverfolgung nur das **contentName**- und das **notificationType**-Objekt erforderlich.

Führen Sie zum Einrichten der Dokumentenverfolgung für einen bestimmten Inhalt folgende Schritte aus:

-   Erstellen Sie ein **LicenseMetadata**-Objekt.

    Weitere Informationen finden Sie unter [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) oder [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc).

-   Legen Sie das **contentName** und das **notificationType**-Objekt fest. Dies sind die einzigen erforderlichen Eigenschaften.

    Weitere Informationen finden Sie unter den Methoden für den Eigenschaftenzugriff auf die der Plattform entsprechende Lizenzmetadatenklasse [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) oder [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc).

-   Nach Richtlinientyp, Vorlage oder Ad-hoc:

    -   Erstellen Sie für die vorlagenbasierte Dokumentenverfolgung ein **UserPolicy**-Objekts, das die Lizenzmetadaten als Parameter übergibt.

        Weitere Informationen finden Sie unter [**UserPolicy.create**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_class_java) und [**MSUserPolicy.userPolicyWithTemplateDescriptor**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_templatedescriptor_property_objc).

    -   Legen Sie für die Ad-hoc-basierte Dokumentenverfolgung die **LicenseMetadata**-Eigenschaft auf das **PolicyDescriptor**-Objekt fest.

        Weitere Informationen finden Sie unter [**PolicyDescriptor.getLicenseMetadata**](/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_interface_java), [**PolicyDescriptor.setLicenseMetadata**](/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_setlicensemetadata_java) und [**MSPolicyDescriptor.licenseMetadata**](/rights-management/sdk/4.2/api/iOS/mspolicydescriptor#msipcthin2_mspolicydescriptor_licensemetadata_property_objc).

    **Hinweis**  Das LicenseMetadata-Objekt ist nur während des Einrichtens der Dokumentenverfolgung für die angegebene Benutzerrichtlinie direkt zugänglich. Sobald das UserPolicy-Objekt erstellt wurde, kann auf die zugehörigen Lizenzmetadaten nicht mehr zugegriffen werden, d. h., die Werte der Lizenzmetadaten lassen sich nicht mehr ändern.

     

-   Rufen Sie die Plattformregistrierungsmethode für die Dokumentenverfolgung auf.

    Weitere Informationen finden Sie unter [**MSUserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc) oder [**UserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc).

 

 


<!--HONumber=Jun16_HO2-->


