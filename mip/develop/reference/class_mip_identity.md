---
title: 'MIP:: Identity-Klasse'
description: 'Dokumentiert die MIP:: Identity-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 8bb4e30398e6f12214605df6f5ad194334d3eeff
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054778"
---
# <a name="class-mipidentity"></a>MIP:: Identity-Klasse 
Abstraktion für Identity.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Identität ()  |  Standardmäßiger [identitätskonstruktor](class_mip_identity.md) , der verwendet wird, wenn eine Benutzer-e-Mail-Adresse
öffentliche Identität (Konstante Identität & andere)  |  Kopierkonstruktor von [Identity](class_mip_identity.md)
öffentliche explizite Identität (konstant Std:: String & e-Mail)  |  [Identitätskonstruktor](class_mip_identity.md) , der verwendet wird, wenn eine e-Mail-Adresse des Benutzers
Public Konstanten Std:: String & GetEmail () konstant  |  Senden Sie die e-Mail.
  
## <a name="members"></a>Member
  
### <a name="identity-function"></a>Identity-Funktion
Standardmäßiger [identitätskonstruktor](class_mip_identity.md) , der verwendet wird, wenn eine Benutzer-e-Mail-Adresse
  
### <a name="identity-function"></a>Identity-Funktion
Kopierkonstruktor von [Identity](class_mip_identity.md)

Parameter:  
* **[Identität](class_mip_identity.md)** : wird zum Erstellen der Kopie verwendet.


  
### <a name="identity-function"></a>Identity-Funktion
[Identitätskonstruktor](class_mip_identity.md) , der verwendet wird, wenn eine e-Mail-Adresse des Benutzers

Parameter:  
* **e-Mail**: e-Mail-Adresse des Benutzers.


  
### <a name="getemail-function"></a>GetEmail-Funktion
Senden Sie die e-Mail.

  
**Gibt Folgendes zurück**: Die e-Mail.