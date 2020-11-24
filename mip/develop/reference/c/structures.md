---
title: Strukturen
description: Gebäuden.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 9/22/2020
ms.openlocfilehash: 2939a4c64ab3e1a47704811875c6a7e941bcfe3c
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567343"
---
# <a name="structures"></a>Strukturen

## <a name="mip_cc_application_info"></a>mip_cc_application_info

Eine Struktur, die anwendungsspezifische Informationen enthält. 

| Feld | BESCHREIBUNG |
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

| Feld | BESCHREIBUNG |
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

## <a name="mip_cc_handle"></a>mip_cc_handle

Nicht transparenter Handle für MIP-Objekt.

| Feld | BESCHREIBUNG |
|---|---|
| typeId | Magische Zahl, die einen bestimmten behandetyp eindeutig identifiziert  |
| Daten | Rohdatenhandle  |


```c
typedef struct {
  uint32_t typeId; 
  void* data;      
} mip_cc_handle;

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

| Feld | BESCHREIBUNG |
|---|---|
| Schlüssel | Schlüssel  |
| value | Wert  |


```c
typedef struct {
  const char* key;   
  const char* value; 
} mip_cc_kv_pair;

```

## <a name="mip_cc_error"></a>mip_cc_error

Fehlerinformationen

```c
typedef struct {
  mip_cc_result result;
  char description[ERROR_STRING_BUFFER_SIZE];

  // MIP_RESULT_ERROR_NETWORK details
  mip_cc_network_error_category networkError_Category;
  int32_t networkError_ResponseCode;

  // MIP_RESULT_ERROR_NO_PERMISSIONS details
  char noPermissionsError_Owner[ERROR_STRING_BUFFER_SIZE];
  char noPermissionsError_Referrer[ERROR_STRING_BUFFER_SIZE];

  // MIP_RESULT_ERROR_SERVICE_DISABLED details
  mip_cc_service_disabled_error_extent serviceDisabledError_Extent;
} mip_cc_error;

```

## <a name="mip_cc_http_header"></a>mip_cc_http_header

HTTP-Anforderungs-/Antwortheader

| Feld | BESCHREIBUNG |
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

| Feld | BESCHREIBUNG |
|---|---|
| id | Eindeutige Anforderungs-ID: korreliert mit derselben Eigenschaft in mip_cc_http_response  |
| Typ | HTTP-Anforderungstyp (z. b. Get vs. Post)  |
| url | HTTP-Anforderungs-URL  |
| bodysize | Größe des HTTP-Anforderungs Texts in Bytes  |
| body | Puffer Verbindungs Text für HTTP-Anforderung  |
| Header Anzahl | Anzahl von HTTP-Anforderungs Headern  |
| headers | Puffer mit HTTP-Anforderungs Headern  |


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

| Feld | BESCHREIBUNG |
|---|---|
| id | Eindeutige Anforderungs-ID: korreliert mit derselben Eigenschaft in mip_cc_http_request  |
| statusCode | Statuscode der HTTP-Antwort  |
| bodysize | Größe des HTTP-Antwort Texts in Bytes  |
| body | Puffer Verbindung mit HTTP-Antworttext  |
| Header Anzahl | Anzahl von HTTP-Antwort Headern  |
| headers | Puffer mit HTTP-Antwort Headern  |


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

Eine Struktur, die Benutzer Identifikationsinformationen enthält.

| Feld | BESCHREIBUNG |
|---|---|
| email | E-Mail-Adresse des Benutzers  |
| name | Anzeige Name des Benutzers, der zum Markieren von Inhalten verwendet wird.  |


```c
typedef struct {
  const char* email;          
  const char* name;           
} mip_cc_identity;

```

## <a name="mip_cc_feature_override"></a>mip_cc_feature_override

Definiert einen aktivierten/deaktivierten Status eines einzelnen Features.

| Feld | BESCHREIBUNG |
|---|---|
| Feature | Feature name  |
| value | Aktivierter/deaktivierter Zustand  |


```c
typedef struct {
  mip_cc_flighting_feature feature; 
  bool value;                       
} mip_cc_feature_override;

```

## <a name="mip_cc_user_rights"></a>mip_cc_user_rights

Eine Gruppe von Benutzern und die Ihnen zugeordneten Rechte

| Feld | BESCHREIBUNG |
|---|---|
| users | Liste der Benutzer  |
| userscount | Anzahl an Benutzern  |
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

| Feld | BESCHREIBUNG |
|---|---|
| users | Liste der Benutzer  |
| userscount | Anzahl an Benutzern  |
| roles | Liste der Rollen  |
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

| Feld | BESCHREIBUNG |
|---|---|
| id | Aufgaben-ID  |
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

| Feld | BESCHREIBUNG |
|---|---|
| Aktions Status | Beschreibt, ob bzw. wie eine Anwendung versucht, den Bezeichnungs Zustand zu ändern.  |
| newlabel | Wenn ' Aktionstyp ' ' Update ' ist: neue Bezeichnung.  |
| newlabelextendedproperties | Wenn ' Aktionstyp ' ' Update ' ist: zusätzliche Eigenschaften, die in Metadaten geschrieben werden sollen.  |
| newlabelaccessmentmethod | Wenn ' Aktionstyp ' ' Update ' ist: die Zuweisungs Methode der neuen Bezeichnung.  |
| isdowngradebug | Wenn ' Aktionstyp ' ' Update ' ist: gibt an, ob ein Bezeichnungs Downgrade vom Benutzer gerechtfertigt wurde.  |
| Herabstufung | If ' Aktionstyp ' ist ' Update ': der vom Benutzer bereitgestellte Bezeichnungs Text für die Bezeichnungs Herabstufung.  |
| supportedactions | Enum-Maske, die die Bezeichnungs bezogenen Aktionen beschreibt, die eine Anwendung ausführen kann.  |


```c
typedef struct {
  mip_cc_label_action_state actionState;                    
  mip_cc_label newLabel;                                    
  mip_cc_dictionary newLabelExtendedProperties;             
  mip_cc_label_assignment_method newLabelAssignmentMethod;  
  bool isDowngradeJustified;                                
  const char* downgradeJustification;                       
  mip_cc_label_action_type supportedActions;                
} mip_cc_application_action_state;

```

## <a name="mip_cc_document_state"></a>mip_cc_document_state

Rückruf Funktionsdefinition zum Abrufen von Dokument Metatdaten, gefiltert nach Name/Präfix.

| Feld | BESCHREIBUNG |
|---|---|
| datastate | Status der Dokument Daten, wenn die Anwendung mit ihr interagiert. |
| contentMetadataCallback | Rückruf für die Dokument Metadaten. |
| Schutz Deskriptor | Schutz Deskriptor, wenn das Dokument derzeit geschützt ist, andernfalls NULL.  |
| contentformat | Dokument Format (Datei oder e-Mail).  |
| auditmetadata | Optionale anwendungsspezifische Metadaten, die beim Senden von Überwachungsberichten verwendet werden. Erkannte Werte: "Absender": Absender-e-Mail-Adresse; "Empfänger": JSON-Array von e-Mail-Empfängern; ' LastModifiedBy ': e-Mail-Adresse des Benutzers, der das Dokument zuletzt geändert hat. ' LastModifiedDate ': Datum der letzten Änderung eines Dokuments  |
| contentMetadataVersion | Version der Dokument Metadaten, der Standardwert ist 0.  |
| contentMetadataVersionFormat | Beschreibt, wie die metadatenversionierung verarbeitet wird.  |

```c
typedef struct {

  const char* contentId;


  mip_cc_data_state dataState;

  mip_cc_metadata_callback contentMetadataCallback;

  mip_cc_protection_descriptor protectionDescriptor;

  mip_cc_content_format contentFormat;

  mip_cc_dictionary auditMetadata;

  uint32_t contentMetadataVersion;

  mip_cc_metadata_version_format contentMetadataVersionFormat;

} mip_cc_document_state;

```

## <a name="mip_cc_metadata_entry"></a>mip_cc_metadata_entry

Metadateneintrag

| Feld | BESCHREIBUNG |
|---|---|
| Schlüssel | Schlüssel Eintrag |
| value | Wert Eintrag  |
| Version | Der Versions Eintrag muss mit 0 initialisiert werden, sofern nicht anders bekannt. |


```c
typedef struct {
  const char* key;        
  const char* value;      
  uint32_t version;       
} mip_cc_metadata_entry;

```

