---
title: 'Erforderliche API-Berechtigungen: Microsoft Information Protection SDK'
description: Technische Details zu API-Berechtigungen, die für Microsoft Information Protection Software Development Kit-Vorgänge erforderlich sind.
author: Pathak-Aniket
ms.author: v-anikep
ms.date: 08/20/2020
ms.topic: conceptual
ms.service: information-protection
ms.openlocfilehash: ce44c0d8b65f477fdd7b08f34cfe2aacc890d259
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "95567925"
---
# <a name="api-permissions-for-the-microsoft-information-protection-sdk"></a>API-Berechtigungen für das Microsoft Information Protection SDK

Das MIP SDK verwendet zwei Azure-Back-End-Dienste für die Bezeichnung und den Schutz. Auf dem Blatt "Azure Active Directory App-Berechtigungen" sind die folgenden Dienste:

- Azure Rights Management-Dienst
- Microsoft Information Protection Sync-Dienst

Anwendungs Berechtigungen müssen für eine oder mehrere APIs erteilt werden, wenn das MIP-SDK für die Bezeichnung und den Schutz verwendet wird. Verschiedene Anwendungs Authentifizierungs Szenarien erfordern möglicherweise unterschiedliche Anwendungs Berechtigungen. Informationen zu Anwendungs Authentifizierungs Szenarien finden Sie unter [Authentifizierungs Szenarien](/azure/active-directory/develop/authentication-flows-app-scenarios).

Die Mandanten weite Zustimmung des Administrators sollte für Anwendungs Berechtigungen erteilt werden, bei denen die Zustimmung des Administrators erforderlich ist, wie in der [Aad-Dokumentation](/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-in-app-registrations)beschrieben.

## <a name="application-permissions"></a>Anwendungsberechtigungen

Anwendungs Berechtigungen ermöglichen, dass eine Anwendung in Azure Active Directory als eigene Entität agiert und nicht im Auftrag eines bestimmten Benutzers.

| Dienst                         | Berechtigungsname           | BESCHREIBUNG                                  | Zustimmung des Administrators erforderlich |
| ------------------------------- | ------------------------- | -------------------------------------------- | ---------------------- |
| Azure Rights Management-Dienst | Content. Superuser         | Alle geschützten Inhalte für diesen Mandanten lesen   | Ja                    |
| Azure Rights Management-Dienst | Content. delegatedreader   | Lesen geschützter Inhalte im Namen eines Benutzers   | Ja                    |
| Azure Rights Management-Dienst | Content. delegatedwriter   | Erstellen geschützter Inhalte im Namen eines Benutzers | Ja                    |
| Azure Rights Management-Dienst | Content. Writer            | Geschützte Inhalte erstellen                     | Ja                    |
| MIP-Synchronisierungs Dienst                | Unifedpolicy. Tenant. Read | Alle vereinheitlichten Richtlinien des Mandanten lesen      | Ja                    |

### <a name="contentsuperuser"></a>Content. Superuser

Diese Berechtigung ist erforderlich, wenn eine Anwendung berechtigt sein muss, den gesamten für den jeweiligen Mandanten geschützten Inhalt zu entschlüsseln. Beispiele für Dienste, die Administratorrechte erfordern, sind die Verhinderung von Datenverlust oder Cloud Access Security Broker-Dienste, die in der Lage sein müssen, den gesamten Inhalt im Klartext anzuzeigen, um Richtlinien Entscheidungen über den Speicherort der Daten zu treffen.  

### <a name="contentdelegatedwriter"></a>Content. delegatedwriter

Diese Berechtigung ist erforderlich, wenn eine Anwendung berechtigt sein muss, Inhalte zu verschlüsseln, die von einem bestimmten Benutzer geschützt werden. Beispiele für Dienste, die Delegierte Schreibrechte erfordern, sind Geschäftsanwendungen, die Inhalte auf der Grundlage der Bezeichnungs Richtlinien des Benutzers verschlüsseln müssen, um Bezeichnungen anzuwenden und Inhalte nativ zu verschlüsseln. Diese Berechtigung ermöglicht es der Anwendung, Inhalte im Kontext des Benutzers zu verschlüsseln.

### <a name="contentdelegatedreader"></a>Content. delegatedreader

Diese Berechtigung ist erforderlich, wenn eine Anwendung berechtigt sein muss, alle Inhalte zu entschlüsseln, die für einen bestimmten Benutzer geschützt sind. Beispiele für Dienste, die Delegierte readerrechte erfordern, sind Geschäftsanwendungen, die Inhalte basierend auf den Bezeichnungs Richtlinien des Benutzers entschlüsseln müssen, um den Inhalt nativ anzuzeigen. Diese Berechtigung ermöglicht der Anwendung das Entschlüsseln und Lesen von Inhalten im Kontext des Benutzers.

### <a name="contentwriter"></a>Content. Writer

Diese Berechtigung ist erforderlich, wenn eine Anwendung berechtigt sein muss, Inhalte zu verschlüsseln. Beispiele für Dienste, die Writer erfordern, sind Line-of-Business-Anwendungen, die Klassifizierungs Bezeichnungen auf Dateien beim Export anwenden. Content. Writer verschlüsselt den Inhalt als Dienst Prinzipal Identität, sodass der Besitzer der geschützten Dateien die Dienst Prinzipal Identität ist.

### <a name="unifiedpolicytenantread"></a>Unifedpolicy. Tenant. Read

Diese Berechtigung ist erforderlich, wenn eine Anwendung berechtigt ist, einheitliche Bezeichnungs Richtlinien für den Mandanten herunterzuladen. Beispiele für Dienste, die einheitliche Richtlinien für Mandanten Lesevorgänge erfordern, sind Anwendungen, die mit Bezeichnungen als Dienst Prinzipal Identität arbeiten müssen.

## <a name="delegated-permissions"></a>Berechtigungen der Stellvertretung

Delegierte Berechtigungen ermöglichen einer Anwendung in Azure Active Directory das Ausführen von Aktionen im Auftrag eines bestimmten Benutzers.

| Dienst                         | Berechtigungsname         | BESCHREIBUNG                                      | Zustimmung des Administrators erforderlich |
| ------------------------------- | ----------------------- | ------------------------------------------------ | ---------------------- |
| Azure Rights Management-Dienst | user_impersonation      | Erstellen und Zugreifen auf geschützte Inhalte für den Benutzer | Nein                     |
| MIP-Synchronisierungs Dienst                | Unifedpolicy. User. Read | Alle vereinheitlichten Richtlinien lesen, auf die ein Benutzer Zugriff hat   | Nein                     |

### <a name="user_impersonation"></a>user_impersonation

Diese Berechtigung ist erforderlich, wenn eine Anwendung im Auftrag des Benutzers für den Benutzer von Azure Rights Management Services zugelassen werden muss. Beispiele für Dienste, die User_Impersonation-Rechte erfordern, sind Anwendungen, die auf der Grundlage von Richtlinien für die Benutzer Bezeichnung Inhalte verschlüsseln oder darauf zugreifen müssen, um Bezeichnungen anzuwenden oder Inhalte System intern zu verschlüsseln.
  
### <a name="unifiedpolicyuserread"></a>Unifedpolicy. User. Read

Diese Berechtigung ist erforderlich, wenn eine Anwendung berechtigt ist, einheitliche Bezeichnungs Richtlinien zu lesen, die mit einem Benutzer verknüpft sind. Verschlüsseln von Inhalten, die von einem bestimmten Benutzer geschützt werden. Beispiele für Dienste, die Delegierte Schreibrechte erfordern, sind Anwendungen, die Inhalte auf der Grundlage der Bezeichnungs Richtlinien des Benutzers verschlüsseln müssen, um Bezeichnungen anzuwenden und Inhalte nativ zu verschlüsseln.