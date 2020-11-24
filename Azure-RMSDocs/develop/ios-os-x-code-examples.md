---
title: Codebeispiele für iOS/OS X | Azure RMS
description: In diesem Thema werden wichtige Codeelemente der iOS/OS X-Version des RMS SDK vorgestellt.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 7E12EBF2-5A19-4A8D-AA99-531B09DA256A
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: 3c50c4579d32add393b680616106b37e92d2364c
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568297"
---
# <a name="iosos-x-code-examples"></a>Codebeispiele für iOS/OS X

[!INCLUDE [deprecation notice](../includes/deprecation-warning.md)]

In diesem Thema werden wichtige Codeelemente der iOS/OS X-Version des RMS SDK vorgestellt.

**Hinweis**: Im Beispielcode und in den nachfolgenden Beschreibungen verwenden wir den Begriff MSIPC (Microsoft Information Protection und Steuerelement) zur Bezeichnung des Clientprozesses.



## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Verwenden von Microsoft Rights Management SDK 4.2 – Schlüsselszenarien


Es folgen Codebeispiele für **Objective C** aus einer größeren Beispielanwendung, die für die Einführung in dieses SDK wichtig sind. Diese veranschaulichen die Verwendung des Microsoft Protected File-Dateiformats (geschützte Datei), benutzerdefinierter geschützter Dateiformate und benutzerdefinierter Benutzeroberflächen-Steuerelemente.

### <a name="scenario-consume-an-rms-protected-file"></a>Szenario: Nutzen einer RMS-geschützten Datei


- **Schritt 1**: Erstellen eines [MSProtectedData](/previous-versions/windows/desktop/msipcthin2/msprotecteddata-interface-objc)-Objekts

  **Beschreibung**: Instanziieren Sie ein [MSProtectedData](/previous-versions/windows/desktop/msipcthin2/msprotecteddata-interface-objc)-Objekt mit dessen create-Methode. Diese Methode implementiert die Dienstauthentifizierung mit [MSAuthenticationCallback](/previous-versions/windows/desktop/msipcthin2/msauthenticationcallback-protocol-objc), um durch die Übergabe einer Instanz von **MSAuthenticationCallback** als Parameter *authenticationCallback* an die MSIPC-API ein Token abzurufen. Den Aufruf von [MSProtectedData protectedDataWithProtectedFile](/previous-versions/windows/desktop/msipcthin2/msprotecteddata-protecteddatawithprotectedfile-completionblock-method-objc) finden Sie im folgenden Beispielcodeabschnitt.

    ```objectivec
        + (void)consumePtxtFile:(NSString *)path authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // userId can be provided as a hint for authentication
            [MSProtectedData protectedDataWithProtectedFile:path
                                                 userId:nil
                                 authenticationCallback:authenticationCallback
                                                options:Default
                                        completionBlock:^(MSProtectedData *data, NSError *error)
            {
                //Read the content from the ProtectedData, this will decrypt the data
                NSData *content = [data retrieveData];
            }];
        }
    ```

- **Schritt 2**: Einrichten der Authentifizierung mit der Active Directory-Authentifizierungsbibliothek (ADAL).

  **Beschreibung**: In diesem Schritt erfahren Sie, wie ADAL zum Implementieren von [MSAuthenticationCallback](/previous-versions/windows/desktop/msipcthin2/msauthenticationcallback-protocol-objc) mit Beispielauthentifizierungsparametern verwendet wird. Weitere Informationen zur Verwendung von ADAL finden Sie in der Azure AD-Authentifizierungsbibliothek (ADAL).

    ```objectivec
      // AuthenticationCallback holds the necessary information to retrieve an access token.
      @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

      @end

      @implementation MsipcAuthenticationCallback

      - (void)accessTokenWithAuthenticationParameters:
             (MSAuthenticationParameters *)authenticationParameters
                                    completionBlock:
             (void(^)(NSString *accessToken, NSError *error))completionBlock
      {
          ADAuthenticationError *error;
          ADAuthenticationContext* context = [
              ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority
                                                                error:&error
          ];
          NSString *appClientId = @"com.microsoft.sampleapp";
          NSURL *redirectURI = [NSURL URLWithString:@"local://authorize"];
          // Retrieve token using ADAL
          [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result) {
                              if (result.status != AD_SUCCEEDED)
                              {
                                  NSLog(@"Auth Failed");
                                  completionBlock(nil, result.error);
                              }
                              else
                              {
                                  completionBlock(result.accessToken, result.error);
                              }
                          }];
       }
    ```

- **Schritt 3**: Überprüfen der Bearbeitungsrechte dieses Benutzers mit diesem Inhalt mithilfe der [MSUserPolicy accessCheck](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-accesscheck-method-objc)-Methode eines [MSUserPolicy](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-interface-objc)-Objekts

    ```objectivec
      - (void)accessCheckWithProtectedData:(MSProtectedData *)protectedData
      {
          //check if user has edit rights and apply enforcements
          if (!protectedData.userPolicy.accessCheck(EditableDocumentRights.Edit))
          {
              // enforce on the UI
              textEditor.focusableInTouchMode = NO;
              textEditor.focusable = NO;
              textEditor.enabled = NO;
          }
      }
    ```

### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Szenario: Erstellen einer neuen geschützten Datei mithilfe einer Vorlage

In diesem Szenario wird zunächst eine Liste mit Vorlagen ([MSTemplateDescriptor](/previous-versions/windows/desktop/msipcthin2/mstemplatedescriptor-interface-objc)) abgerufen. Dabei wird die erste Vorlage zum Erstellen einer Richtlinie ausgewählt und anschließend die neue geschützte Datei erstellt und in diese geschrieben.

-   **Schritt 1**: Abrufen der Liste der Vorlagen

    ```objectivec
        + (void)templateListUsageWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSTemplateDescriptor templateListWithUserId:@"user@domain.com"
                            authenticationCallback:authenticationCallback
                                   completionBlock:^(NSArray/*MSTemplateDescriptor*/ *templates, NSError *error)
                                   {
                                     // use templates array of MSTemplateDescriptor (Note: will be nil on error)
                                   }];
        }
    ```

-   **Schritt 2**: Erstellen eines [MSUserPolicy](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-interface-objc)-Objekts mit der ersten Vorlage in der Liste

    ```objectivec
        + (void)userPolicyCreationFromTemplateWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSUserPolicy userPolicyWithTemplateDescriptor:[templates objectAtIndex:0]
                                            userId:@"user@domain.com"
                                     signedAppData:nil
                            authenticationCallback:authenticationCallback
                                           options:None
                                   completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
            // use userPolicy (Note: will be nil on error)
            }];
        }
    ```

-   **Schritt 3**: Erstellen eines [MSMutableProtectedData](/previous-versions/windows/desktop/msipcthin2/msmutableprotecteddata-interface-objc)-Objekts und Füllen des Objekts mit Inhalt

    ```objectivec
        + (void)createPtxtWithUserPolicy:(MSUserPolicy *)userPolicy contentToProtect:(NSData *)contentToProtect
        {
            // create an MSMutableProtectedData to write content
            [contentToProtect protectedDataInFile:filePath
                        originalFileExtension:kDefaultTextFileExtension
                               withUserPolicy:userPolicy
                              completionBlock:^(MSMutableProtectedData *data, NSError *error)
            {
             // use data (Note: will be nil on error)
            }];
        }
    ```

### <a name="scenario-open-a-custom-protected-file"></a>Szenario: Öffnen einer benutzerdefinierten geschützten Datei


-   **Schritt 1**: Erstellen eines [MSUserPolicy](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-interface-objc)-Objekts aus einem *serializedContentPolicy*-Objekt

    ```objectivec
        + (void)userPolicyWith:(NSData *)protectedData
        authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // Read header information from protectedData and extract the  PL
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger serializedPolicySize;
            NSMutableData *serializedPolicy;
            [protectedData getBytes:&serializedPolicySize length:sizeof(serializedPolicySize)];
            [protectedData getBytes:[serializedPolicy mutableBytes] length:serializedPolicySize];

            // Get the user policy , this is an async method as it hits the REST service
            // for content key and usage restrictions
            // userId provided as a hint for authentication
            [MSUserPolicy userPolicyWithSerializedPolicy:serializedPolicy
                                              userId:@"user@domain.com"
                              authenticationCallback:authenticationCallback
                                             options:Default
                                     completionBlock:^(MSUserPolicy *userPolicy,
                                                       NSError *error)
            {

            }];
         }
    ```

-   **Schritt 2**: Erstellen Sie ein [MSCustomProtectedData](/previous-versions/windows/desktop/msipcthin2/msmutablecustomprotecteddata-interface-objc)-Objekt mithilfe des [MSUserPolicy](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-interface-objc)-Objekts aus **Schritt 1**, und lesen Sie daraus.

    ```objectivec
        + (void)customProtectedDataWith:(NSData *)protectedData
        {
            // Read header information from protectedData and extract the  protectedContentSize
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger protectedContentSize;
            [protectedData getBytes:&protectedContentSize
                         length:sizeof(protectedContentSize)];

            // Create the MSCustomProtector used for decrypting the content
            // The content start position is the header length
            [MSCustomProtectedData customProtectedDataWithPolicy:userPolicy
                                               protectedData:protectedData
                                        contentStartPosition:sizeof(NSUInteger) + serializedPolicySize
                                                 contentSize:protectedContentSize
                                             completionBlock:^(MSCustomProtectedData *customProtector,
                                                               NSError *error)
            {
             //Read the content from the custom protector, this will decrypt the data
             NSData *content = [customProtector retrieveData];
             NSLog(@"%@", content);
            }];
         }
    ```

### <a name="scenario-create-a-custom-protected-file-using-a-custom-ad-hoc-policy"></a>Szenario: Erstellen einer benutzerdefinierten geschützten Datei mit einer benutzerdefinierten (Ad-Hoc)-Richtlinie


-   **Schritt 1**: Erstellen einer Richtlinienbeschreibung mit einer vom Benutzer angegebenen E-Mail-Adresse.

    **Beschreibung**: In der Praxis würden die Objekte [MSUserRights](/previous-versions/windows/desktop/msipcthin2/msuserrights-interface-objc) und [MSPolicyDescriptor](/previous-versions/windows/desktop/msipcthin2/mspolicydescriptor-interface-objc) mithilfe von Benutzereingaben von der Geräteschnittstelle erstellt werden.

    ```objectivec
        + (void)policyDescriptor
        {
            MSUserRights *userRights = [[MSUserRights alloc] initWithUsers:[NSArray arrayWithObjects: @"user1@domain.com", @"user2@domain.com", nil] rights:[MSEmailRights all]];

            MSPolicyDescriptor *policyDescriptor = [[MSPolicyDescriptor alloc] initWithUserRights:[NSArray arrayWithObjects:userRights, nil]];
            policyDescriptor.contentValidUntil = [[NSDate alloc] initWithTimeIntervalSinceNow:NSTimeIntervalSince1970 + 3600.0];
            policyDescriptor.offlineCacheLifetimeInDays = 10;
        }
    ```

-   **Schritt 2**: Erstellen eines benutzerdefinierten [MSUserPolicy](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-interface-objc)-Objekts aus der Richtlinienbeschreibung *selectedDescriptor*

    ```objectivec
        + (void)userPolicyWithPolicyDescriptor:(MSPolicyDescriptor *)policyDescriptor
        {
            [MSUserPolicy userPolicyWithPolicyDescriptor:policyDescriptor
                                          userId:@"user@domain.com"
                          authenticationCallback:authenticationCallback
                                         options:None
                                 completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
              // use userPolicy (Note: will be nil on error)
            }];
        }
    ```

-   **Schritt 3**: Erstellen und Füllen des [MSMutableCustomProtectedData](/previous-versions/windows/desktop/msipcthin2/msmutablecustomprotecteddata-interface-objc)-Objekts mit Inhalt und anschließendes Schließen des Objekts

    ```objectivec
        + (void)mutableCustomProtectedData:(NSMutableData *)backingData policy:(MSUserPolicy *)policy contentToProtect:(NSString *)contentToProtect
        {
            //Get the serializedPolicy from a given policy
            NSData *serializedPolicy = [policy serializedPolicy];

            // Write header information to backing data including the PL
            // ------------------------------------
            // | PL length | PL | ContetSizeLength |
            // -------------------------------------
            NSUInteger serializedPolicyLength = [serializedPolicy length];
            [backingData appendData:[NSData dataWithBytes:&serializedPolicyLength length:sizeof(serializedPolicyLength)]];
            [backingData appendData:serializedPolicy];
            NSUInteger protectedContentLength = [MSCustomProtectedData getEncryptedContentLengthWithPolicy:policy contentLength:unprotectedData.length];
            [backingData appendData:[NSData dataWithBytes:&protectedContentLength length:sizeof(protectedContentLength)]];

            NSUInteger headerLength = sizeof(serializedPolicyLength) + serializedPolicyLength + sizeof(protectedContentLength);

            // Create the MSMutableCustomProtector used for encrypting content
            // The content start position is the current length of the backing data
            // The encryptedContentSize content size is 0 since there is no content yet
            [MSMutableCustomProtectedData customProtectorWithUserPolicy:policy
                                                        backingData:backingData
                                             protectedContentOffset:headerLength
                                                    completionBlock:^(MSMutableCustomProtectedData *customProtector,
                                                                      NSError *error)
            {
                //Append data to the custom protector, this will encrypt the data and write it to the backing data
                [customProtector appendData:[contentToProtect dataUsingEncoding:NSUTF8StringEncoding] error:&error];

                //close the custom protector so it will flush and finalise encryption
                [customProtector close:&error];

            }];
          }
    ```