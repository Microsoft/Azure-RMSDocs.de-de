---
title: 'Konzepte: die Kernkonzepte in den benutzerdefinierten MIP SDK-Berechtigungen.'
description: In diesem Artikel erfahren Sie, wie Sie das Core SDK-Konzept namens "benutzerdefinierte Berechtigungen" verstehen.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 02/02/2021
ms.author: tommos
ms.openlocfilehash: 27d17b14ed34ae72fafdf1084d277d3389a1790c
ms.sourcegitcommit: 314f8109920a706bd1000dd4e63ba9cdd12cd671
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2021
ms.locfileid: "99554192"
---
# <a name="microsoft-information-protection-sdk---user-defined-permissions"></a>Microsoft Information Protection SDK: benutzerdefinierte Berechtigungen

Das Microsoft Information Protection SDK unterstützt zwei primäre Typen von Beschriftungs gesteuerten Berechtigungen: Vorlagen basiert und Benutzer definiert.

- **Vorlagenbasierte Berechtigungen:** Diese Rechte werden von der Bezeichnung Administrator im Security and Compliance Center definiert. Diese Bezeichnungen werden zentral verwaltet, und Änderungen an der Konfiguration wirken sich auf Benutzer aus, die bereits Kopien der Dateien haben. Wenn der Administrator beispielsweise einen Benutzer aus der Liste der autorisierten Benutzer entfernt, erhält dieser Benutzer keinen Zugriff mehr auf die geschützten Daten, wenn er das nächste Mal versucht, eine Lizenz abzurufen.

- **Benutzerdefinierte Berechtigungen**: diese Rechte werden **zum Zeitpunkt der Bezeichnung** durch den Endbenutzer oder die Anwendung definiert. Berechtigungen werden an das MIP SDK in Form einer Auflistung von Benutzer-zu-Rollen-Zuordnungen oder Benutzer-zu-Rechte-Zuordnungen übermittelt. Diese Rechte werden in die Veröffentlichungs Lizenz für das geschützte Dokument geschrieben und können im Gegensatz zu Vorlagen basierten Berechtigungen nicht zentral verwaltet oder geändert werden, nachdem die Freigabe ohne direkten Zugriff und Änderung des Dokuments aufgehoben wurde.

## <a name="users-rights-and-roles"></a>Benutzer, Rechte und Rollen

Da erwartet wird, dass Rechte vom Benutzer zum Zeitpunkt der Bezeichnung definiert werden, muss Ihre Anwendung eine Schnittstelle bereitstellen, damit der Benutzer oder der Dienst Eingaben für die e-Mail-Adressen und-Rechte oder Rollen bereitstellen kann, die der Benutzer erhält. Diese Konfiguration erfolgt durch Übergeben einer Auflistung von- `UserRoles` Objekten oder- `UserRights` Objekten, die speziell definieren, wer welche Zugriffsebene auf die Dokumente haben soll.

```csharp
// Create a List<string> of the first set of permissions. 
List<string> users = new List<string>()
{
    "alice@contoso.com",
    "bob@contoso.com"
};

// Create a List<string> of the Rights the above users should have. 
List<string> rights = new List<string>()
{
    Rights.View,
    Rights.Edit                
};

// Create a UserRights object containing the defined users and rights.
UserRights userRights = new UserRights(users, rights);

// Add them to a new List<UserRights>
List<UserRights> userRightsList = new List<UserRights>()
{
    userRights
};
```

Das Ergebnis ist, dass Sie über eine `List<UserRights>` Sammlung verfügen, die angibt, dass sowohl Alice als auch Bob die geschützte Datei anzeigen und bearbeiten können. Wenn Sie weitere Benutzer mit einem *anderen* Berechtigungs Satz hinzufügen möchten, wiederholen Sie den Vorgang, um ein zweites Objekt zu erstellen `UserRights` , indem Sie die neuen Benutzer und Berechtigungen übergeben und dann der Auflistung hinzufügen, `List<UserRights>` indem Sie aufrufen `userRightsList.Add(userRights2)` .

Dieses Muster gilt auch für `UserRoles` und kann einfach durch Ersetzen von **rechten** durch **Rollen** und Erstellen einer Sammlung implementiert werden `List<UserRoles>` .

### <a name="apply-protection"></a>Schutz anwenden

Das Festlegen des Schutzes kann erreicht werden, indem ein `ProtectionDescriptor` aus dem- `List<UserRights>` Objekt oder dem-Objekt erstellt `List<UserRoles>` und dann an übergeben wird `FileHandler.SetProtection()` . Übertragen Sie schließlich die Änderung an der Datei, um eine neue Datei zu schreiben. 

### <a name="when-to-apply-protection-to-files"></a>Anwenden des Schutzes auf Dateien

Wenn Sie eine Bezeichnung über `FileHandler.SetLabel()` MIP SDK festgelegt haben, müssen Sie nur eine Aktion durchführen und jeglichen Schutz anwenden. Wenn die Bezeichnung für benutzerdefinierte Berechtigungen (UDP) konfiguriert ist, kann Ihre Anwendung nicht im Voraus wissen, dass es sich bei der Bezeichnung um eine UDP-Bezeichnung handelt. Das MIP-SDK zeigt diese Informationen an, indem eine Ausnahme des Typs ausgelöst wird `Microsoft.InformationProtection.Exceptions.AdhocProtectionRequiredException` . `FileHandler`Der Code sollte diese Ausnahme abfangen und dann die Benutzer-oder Dienst Schnittstelle zum Definieren der benutzerdefinierten Berechtigungen veranlassen. Nach Abschluss des Vorgangs können Sie den Schutz festlegen. Im folgenden Beispiel wird das End-to-End-Muster gezeigt, es wird jedoch davon ausgegangen, dass Sie bereits eine Funktion zum Erstellen des Objekts implementiert haben `List<UserRights>` .

```csharp
try
{
    // Attempt to set the label. If it's a UDP label, this will throw. 
    handler.SetLabel(engine.GetLabelById(options.LabelId), labelingOptions, new ProtectionSettings());
}

catch (Microsoft.InformationProtection.Exceptions.AdhocProtectionRequiredException)
{
    // Assumes you've create a function that returns the List<UserRights> as previously detailed. 
    List<UserRights> userRightsList = GetUserRights();

    // Create a ProtectionDescriptor using the set of UserRights.
    ProtectionDescriptor protectionDescriptor = new ProtectionDescriptor(userRightsList);
    
    // Apply protection to the file using the new ProtectionDescriptor. 
    handler.SetProtection(protectionDescriptor, new ProtectionSettings());

    // Set the label. This will now succeed as protection has been defined. 
    handler.SetLabel(engine.GetLabelById(options.LabelId), labelingOptions, new ProtectionSettings());

    // Commit the change. 
    var result = Task.Run(async () => await handler.CommitAsync("myFileOutput.xlsx")).Result;
}
```

## <a name="custom-protection"></a>Benutzerdefinierter Schutz

Dieser Prozess kann auch verwendet werden, um nur den Schutz festzulegen, indem der Schutz festgelegt und der Schritt übersprungen wird `SetLabel()` . Wenn die Anwendung keine Bezeichnung anwenden muss, ist der Ausnahmehandler nicht erforderlich, und der Schutz kann mithilfe des Musters festgelegt werden `ProtectionDescriptor`  ->  `SetProtection()`  ->  `CommitAsync()` .

## <a name="next-steps"></a>Nächste Schritte

- [Überprüfen Sie die Konfiguration der Bezeichnungs Verschlüsselung in der Microsoft 365 Dokumentation.](https://docs.microsoft.com/en-us/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#understand-how-the-encryption-works)
