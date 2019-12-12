---
title: Strukturen
description: Gebäuden.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 11/4/2019
ms.openlocfilehash: aa544dfbd046ae8c3137cbc115d9af6ea219bc07
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73591605"
---
# <a name="structures"></a>Strukturen

## <a name="mip_cc_application_info"></a>mip_cc_application_info

Eine Struktur, die anwendungsspezifische Informationen enthält. 

| Feld | Description |
|---|---|
| applicationId | Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).  |
| applicationName | Anwendungsname (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)  |
| applicationVersion | Die Version der verwendeten Anwendung (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)   |


```c
typedef struct {
  const char* applicationId;      
  const char* applicationName;    
  const char* applicationVersion; 
} mip_cc_application_info;

```

## <a name="mip_cc_oauth2_challenge"></a>mip_cc_oauth2_challenge

Von einem Server bereitgestellte Informationen zum Generieren eines OAuth2-Tokens

| Feld | Description |
|---|---|
| authority | OAuth2 Authority  |
| resource | OAuth2-Ressource  |
| scope | OAuth2 Bereich  |


```c
typedef struct {
  const char* authority; 
  const char* resource;  
  const char* scope;     
} mip_cc_oauth2_challenge;

```

## <a name="mip_cc_guid"></a>mip_cc_guid

GUID

```c
typedef struct {
  char guid[37];
} mip_cc_guid;

```

## <a name="mip_cc_kv_pair"></a>mip_cc_kv_pair

Schlüssel-Wert-Paar

| Feld | Description |
|---|---|
| key | Key  |
| value | Value  |


```c
typedef struct {
  const char* key;   
  const char* value; 
} mip_cc_kv_pair;

```

## <a name="mip_cc_http_header"></a>mip_cc_http_header

HTTP-Anforderungs-/Antwortheader

| Feld | Description |
|---|---|
| name | Header Name/-Schlüssel  |
| value | Headerwert  |


```c
typedef struct {
  const char* name;  
  const char* value; 
} mip_cc_http_header;

```

## <a name="mip_cc_http_request"></a>mip_cc_http_request

HTTP-Anforderung

| Feld | Description |
|---|---|
| id | Eindeutige Anforderungs-ID: korreliert mit derselben Eigenschaft in mip_cc_http_response  |
| Typ | HTTP-Anforderungstyp (z. b. Get vs. Post)  |
| URL | HTTP-Anforderungs-URL  |
| bodysize | Größe des HTTP-Anforderungs Texts in Bytes  |
| Textkörper | Puffer Verbindungs Text für HTTP-Anforderung  |
| Header Anzahl | Anzahl von HTTP-Anforderungs Headern  |
| Kopfzeilen | Puffer mit HTTP-Anforderungs Headern  |


```c
typedef struct {
  const char* id;                    
  mip_cc_http_request_type type;     
  const char* url;                   
  int64_t bodySize;                  
  const uint8_t* body;               
  int64_t headersCount;              
  const mip_cc_http_header* headers; 
} mip_cc_http_request;

```

## <a name="mip_cc_http_response"></a>mip_cc_http_response

HTTP-Antwort

| Feld | Description |
|---|---|
| id | Eindeutige Anforderungs-ID: korreliert mit derselben Eigenschaft in mip_cc_http_request  |
| statusCode | Statuscode der HTTP-Antwort  |
| bodysize | Größe des HTTP-Antwort Texts in Bytes  |
| Textkörper | Puffer Verbindung mit HTTP-Antworttext  |
| Header Anzahl | Anzahl von HTTP-Antwort Headern  |
| Kopfzeilen | Puffer mit HTTP-Antwort Headern  |


```c
typedef struct {
  const char* id;                    
  int32_t statusCode;                
  int64_t bodySize;                  
  const uint8_t* body;               
  int64_t headersCount;              
  const mip_cc_http_header* headers; 
} mip_cc_http_response;

```

## <a name="mip_cc_identity"></a>mip_cc_identity

Eine Struktur, die anwendungsspezifische Informationen enthält. 

| Feld | Description |
|---|---|
| E-Mail | E-Mail-Adresse des Benutzers  |


```c
typedef struct {
  const char* email;          
} mip_cc_identity;

```

## <a name="mip_cc_feature_override"></a>mip_cc_feature_override

Definiert einen aktivierten/deaktivierten Status eines einzelnen Features.

| Feld | Description |
|---|---|
| -Feature | Feature name  |
| value | Aktivierter/deaktivierter Zustand  |


```c
typedef struct {
  mip_cc_flighting_feature feature; 
  bool value;                       
} mip_cc_feature_override;

```

## <a name="mip_cc_user_rights"></a>mip_cc_user_rights

Eine Gruppe von Benutzern und die Ihnen zugeordneten Rechte

| Feld | Description |
|---|---|
| Benutzer | Liste der Benutzer  |
| userscount | Anzahl von Benutzern  |
| Rechte | Liste der Rechte  |
| righungscount | Anzahl der Rechte  |


```c
typedef struct {
  const char** users;  
  int64_t usersCount;  
  const char** rights; 
  int64_t rightsCount; 
} mip_cc_user_rights;

```

## <a name="mip_cc_user_roles"></a>mip_cc_user_roles

Eine Gruppe von Benutzern und den Ihnen zugeordneten Rollen

| Feld | Description |
|---|---|
| Benutzer | Liste der Benutzer  |
| userscount | Anzahl von Benutzern  |
| Rollen | Liste der Rollen  |
| rolescount | Anzahl von Rollen  |


```c
typedef struct {
  const char** users;  
  int64_t usersCount;  
  const char** roles; 
  int64_t rolesCount; 
} mip_cc_user_roles;

```

## <a name="mip_cc_async_task"></a>mip_cc_async_task

Definiert eine einzelne Anforderung für asynchrone Aufgaben Dispatch.

| Feld | Description |
|---|---|
| id | Task-ID  |
| Delta MS | Verzögerung bis zur Ausführung der Aufgabe (in Millisekunden)  |
| executeonindependentthread | Gibt an, ob dieser Task in einem vollständig unabhängigen Thread ausgeführt werden oder einen freigegebenen Thread wieder verwenden soll.  |


```c
typedef struct {
  const char* id;                   
  int64_t delayMs;                  
  bool executeOnIndependentThread;  
} mip_cc_async_task;

```

## <a name="mip_cc_application_action_state"></a>mip_cc_application_action_state

Stellt den aktuellen Zustand der Anwendung dar, während Sie einen Bezeichnungs bezogenen Vorgang ausführt.

| Feld | Description |
|---|---|
| Aktions Status | Beschreibt, ob bzw. wie eine Anwendung versucht, den Bezeichnungs Zustand zu ändern.  |
| newlabel | Wenn ' Aktionstyp ' ' Update ' ist: neue Bezeichnung.  |
| newlabelextendedproperties | Wenn ' Aktionstyp ' ' Update ' ist: zusätzliche Eigenschaften, die in Metadaten geschrieben werden sollen.  |
| newlabelassignetmentmethod | Wenn ' Aktionstyp ' ' Update ' ist: die Zuweisungs Methode der neuen Bezeichnung.  |
| isdowngradebug | Wenn ' Aktionstyp ' ' Update ' ist: gibt an, ob ein Bezeichnungs Downgrade vom Benutzer gerechtfertigt wurde.  |
| Herabstufung | If ' Aktionstyp ' ist ' Update ': der vom Benutzer bereitgestellte Bezeichnungs Text für die Bezeichnungs Herabstufung.  |
| supportedactions | Enum-Maske, die die Bezeichnungs bezogenen Aktionen beschreibt, die eine Anwendung ausführen kann.  |


```c
typedef struct {
  mip_cc_label_action_state actionState;                    
  mip_cc_label newLabel;                                    
  mip_cc_dictionary newLabelExtendedProperties;             
  mip_cc_label_assignment_method newLabelAssignementMethod; 
  bool isDowngradeJustified;                                
  const char* downgradeJustification;                       
  mip_cc_label_action_type supportedActions;                
} mip_cc_application_action_state;

```

## <a name="mip_cc_document_state"></a>mip_cc_document_state

Stellt den aktuellen Zustand eines Bezeichnungs fähigen Dokuments dar.

| Feld | Description |
|---|---|
| contentId | Lesbare Dokument Beschreibung, die im Mandanten Portal angezeigt wird. Beispiel für eine Datei: [Pfad\Dateiname]; Beispiel für eine e-Mail: [Betreff: Absender]. |
| datastate | Status von Dokument Daten, wenn die Anwendung mit ihr interagiert  |
| contentMetadataCallback | Metadatenrückruf für Dokumente  |
| Schutz Deskriptor | Schutz Beschreibung, wenn das Dokument derzeit geschützt ist, andernfalls NULL  |
| contentformat | Dokument Format (Datei oder e-Mail)  |
| auditmetadata | Optionale anwendungsspezifische Metadaten, die beim Senden von Überwachungsberichten verwendet werden. Erkannte Werte: "Absender": Absender-e-Mail-Adresse; "Empfänger": JSON-Array von e-Mail-Empfängern; ' LastModifiedBy ': e-Mail-Adresse des Benutzers, der das Dokument zuletzt geändert hat. ' LastModifiedDate ': Datum, an dem ein Dokument zuletzt geändert wurde. |

```c
typedef struct {
  const char* contentId;
  mip_cc_data_state dataState;
  mip_cc_metadata_callback contentMetadataCallback;
  mip_cc_protection_descriptor protectionDescriptor;
  mip_cc_content_format contentFormat;
  mip_cc_dictionary auditMetadata;
} mip_cc_document_state;