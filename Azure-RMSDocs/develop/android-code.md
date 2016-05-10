---
# required metadata

title: Codebeispiele für Android | Azure RMS
description: In diesem Thema werden wichtige Codeelemente der Android-Version des RMS SDK vorgestellt.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: afe062d5-a507-45e5-a4ec-613f9c46772e

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# Codebeispiele für Android

In diesem Thema werden wichtige Codeelemente der Android-Version des RMS SDK vorgestellt.

**Hinweis**: Im Beispielcode und in den nachfolgenden Beschreibungen verwenden wir den Begriff MSIPC (Microsoft Information Protection und Steuerelement) zur Bezeichnung des Clientprozesses.


## Verwenden von Microsoft Rights Management SDK 4.2 – Schlüsselszenarien

Es folgen Codebeispiele aus einer größeren Beispielanwendung, die für die Einführung in dieses SDK wichtig sind. Diese veranschaulichen die Verwendung des Microsoft Protected File-Dateiformats, das auch als geschützte Datei bezeichnet wird, die Verwendung benutzerdefinierter geschützter Dateiformate und die Verwendung benutzerdefinierter Benutzeroberflächen-Steuerelemente.



Die Beispielanwendung *MSIPCSampleApp* ist zur Verwendung mit diesem SDK für Android-Betriebssysteme verfügbar. Unter [rms-sdk-ui-for-android](https://github.com/AzureAD/rms-sdk-ui-for-android) auf GitHub können Sie auf diese Anwendung zugreifen.

### Szenario: Nutzen einer RMS-geschützten Datei

-   **Schritt 1**: Erstellen eines [**ProtectedFileInputStream**](https://stage.docs.microsoft.com/en-us/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_protectedfileinputstream_class_java)-Objekts.

    **Quelle**: *MsipcAuthenticationCallback.java*

    **Beschreibung**: Instanziieren Sie ein [**ProtectedFileInputStream**](https://stage.docs.microsoft.com/en-us/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_protectedfileinputstream_class_java)-Objekt mit dessen create-Methode. Diese Methode implementiert die Dienstauthentifizierung mit [**AuthenticationRequestCallback**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_authenticationrequestcallback_interface_java), um durch die Übergabe einer Instanz von **AuthenticationRequestCallback** als Parameter *mRmsAuthCallback* an die MSIPC-API ein Token abzurufen. Betrachten Sie dazu den Aufruf von [**ProtectedFileInputStream.create**](/rights-management/sdk/4.2/api/android/protectedfileinputstream#msipcthin2_protectedfileinputstream_create_method) kurz vor dem Ende des folgenden Beispielcodeabschnitts.

        public void startContentConsumptionFromPtxtFileFormat(InputStream inputStream)
        {
            CreationCallback<ProtectedFileInputStream> protectedFileInputStreamCreationCallback =
              new CreationCallback<ProtectedFileInputStream>()
            {
                @Override
                public Context getContext()
                {
                   …
               }

                @Override
                public void onCancel()
                {
                   …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                   …
                }

                @Override
                public void onSuccess(ProtectedFileInputStream protectedFileInputStream)
                {
                   …
                   …
                    byte[] dataChunk = new byte[16384];
                    try
                    {
                        while ((nRead = protectedFileInputStream.read(dataChunk, 0,
                                dataChunk.length)) != -1)
                        {
                            …
                        }
                         …
                        protectedFileInputStream.close();
                    }
                    catch (IOException e)
                    {
                      …
                    }  
              }
            };
            try
            {
               …
                ProtectedFileInputStream.create(inputStream, null, mRmsAuthCallback,
                                                PolicyAcquisitionFlags.NONE,
                                                protectedFileInputStreamCreationCallback);
            }
            catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
            {
                …
            }
        }


-   **Schritt 2**: Einrichten der Authentifizierung mit der Active Directory-Authentifizierungsbibliothek (ADAL).

    **Quelle**: *MsipcAuthenticationCallback.java*.

    **Beschreibung**: In diesem Schritt erfahren Sie, wie ADAL zum Implementieren einer [**AuthenticationRequestCallback**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_authenticationrequestcallback_interface_java)-Funktion mit Beispielauthentifizierungsparametern verwendet wird. Weitere Informationen zur Verwendung von ADAL finden Sie unter [Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/en-us/library/jj573266.aspx).


        class MsipcAuthenticationCallback implements AuthenticationRequestCallback
        {

        …

        @Override
        public void getToken(Map<String, String> authenticationParametersMap,
                             final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
        {
            String authority = authenticationParametersMap.get("oauth2.authority");
            String resource = authenticationParametersMap.get("oauth2.resource");
            String userId = authenticationParametersMap.get("userId");
            final String userHint = (userId == null)? "" : userId;
            AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
            if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
            {
                try
                {
                    authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                    App.getInstance().setAuthenticationContext(authenticationContext);
                }
                catch (NoSuchAlgorithmException e)
                {
                    …
                    authenticationCompletionCallbackToMsipc.onFailure();
                }
                catch (NoSuchPaddingException e)
                {
                    …
                    authenticationCompletionCallbackToMsipc.onFailure();
                }
           }
            App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                           "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                            {
                                @Override
                                public void onError(Exception exc)
                                {
                                    …
                                    if (exc instanceof AuthenticationCancelError)
                                    {
                                         …
                                        authenticationCompletionCallbackToMsipc.onCancel();
                                    }
                                    else
                                    {
                                         …
                                        authenticationCompletionCallbackToMsipc.onFailure();
                                    }
                                }

                                @Override
                                public void onSuccess(AuthenticationResult result)
                                {
                                    …
                                    if (result == null || result.getAccessToken() == null
                                            || result.getAccessToken().isEmpty())
                                    {
                                         …
                                    }
                                    else
                                    {
                                        // request is successful
                                        …
                                        authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                    }
                                }
                            }

                            );
                      }


-   **Schritt 3**: Überprüfen mit der [**AccessCheck**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_accesscheck_method_java)-Methode von [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy), ob dieser Benutzer für diesen Inhalt über die Berechtigung **Bearbeiten** verfügt.

    **Quelle**: *TextEditorFragment.java*


         //check if user has edit rights and apply enforcements
                if (!mUserPolicy.accessCheck(EditableDocumentRights.Edit))
                {
                    mTextEditor.setFocusableInTouchMode(false);
                    mTextEditor.setFocusable(false);
                    mTextEditor.setEnabled(false);
                    …
                }


### Szenario: Erstellen einer neuen geschützten Datei mithilfe einer Vorlage

In diesem Szenario wird zunächst eine Liste von Vorlagen abgerufen und die erste Vorlage zum Erstellen einer Richtlinie ausgewählt, und dann wird die neue geschützte Datei erstellt und in sie geschrieben.

-   **Schritt 1**: Abrufen der Liste der Vorlagen über ein [**TemplateDescriptor**](/rights-management/sdk/4.2/api/android/templatedescriptor#msipcthin2_templatedescriptor_class_java)-Objekt.

    **Quelle**: *MsipcTaskFragment.java*



    CreationCallback<List<TemplateDescriptor>> getTemplatesCreationCallback = new CreationCallback<List<TemplateDescriptor>>()
      {
          @Override
          public Context getContext()
          {
              …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(List<TemplateDescriptor> templateDescriptors)
          {
             …
          }
      };
      try
      {
              …
          mIAsyncControl = TemplateDescriptor.getTemplates(emailId, mRmsAuthCallback, getTemplatesCreationCallback);
      }
      catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
      {
              …
      }


-    **Schritt 2**: Erstellen einer [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy) verwenden die erste Vorlage in der Liste.

    **Source**: *MsipcTaskFragment.java*



      CreationCallback<UserPolicy> userPolicyCreationCallback = new CreationCallback<UserPolicy>()
      {
          @Override
          public Context getContext()
          {
              …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(final UserPolicy item)
          {
              …
          }
      };
      try
      {
           …
          mIAsyncControl = UserPolicy.create((TemplateDescriptor)selectedDescriptor, mEmailId, mRmsAuthCallback,
                            UserPolicyCreationFlags.NONE, userPolicyCreationCallback);
           …
      }
      catch (InvalidParameterException e)
      {
              …
      }


-    **Schritt 3**: Erstellen eines [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)-Objekts und Schreiben von Inhalt in dieses Objekt.

    **Source**: *MsipcTaskFragment.java*


    private void createPTxt(final byte[] contentToProtect)
        {
             …
            CreationCallback<ProtectedFileOutputStream> protectedFileOutputStreamCreationCallback = new CreationCallback<ProtectedFileOutputStream>()
            {
                @Override
                public Context getContext()
                {
                 …
                }

                @Override
                public void onCancel()
                {
                 …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                 …
                }

                @Override
                public void onSuccess(ProtectedFileOutputStream protectedFileOutputStream)
                {
                    try
                    {
                        // write to this stream
                        protectedFileOutputStream.write(contentToProtect);
                        protectedFileOutputStream.flush();
                        protectedFileOutputStream.close();
                        …
                    }
                    catch (IOException e)
                    {
                        …
                    }
                }
            };
            try
            {
                File file = new File(filePath);
                outputStream = new FileOutputStream(file);
                mIAsyncControl = ProtectedFileOutputStream.create(outputStream, mUserPolicy, originalFileExtension,
                        protectedFileOutputStreamCreationCallback);
            }
            catch (FileNotFoundException e)
            {
                 …
            }
            catch (InvalidParameterException e)
            {
                 …
            }
        }



### Szenario: Öffnen einer benutzerdefinierten geschützten Datei

-   **Schritt 1**: Erstellen eines [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy)-Objekts aus einem *SerializedContentPolicy*-Objekts.

    **Quelle**: *MsipcTaskFragment.java*


    CreationCallback<UserPolicy> userPolicyCreationCallbackFromSerializedContentPolicy = new CreationCallback<UserPolicy>()
            {
                @Override
                public void onSuccess(UserPolicy userPolicy)
                {
                  …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                  …
                }

                @Override
                public void onCancel()
                {
                  …
                }

                @Override
                public Context getContext()
                {
                  …
                }
            };


    try
    {
      ...

      // Read the serializedContentPolicyLength from the inputStream.
      long serializedContentPolicyLength = readUnsignedInt(inputStream);

      // Read the PL bytes from the input stream using the PL size.
      byte[] serializedContentPolicy = new byte[(int)serializedContentPolicyLength];
      inputStream.read(serializedContentPolicy);

      ...

      UserPolicy.acquire(serializedContentPolicy, null, mRmsAuthCallback, PolicyAcquisitionFlags.NONE,
              userPolicyCreationCallbackFromSerializedContentPolicy);
    }
    catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
    {
      ...
    }
    catch (IOException e)
    {
      ...
    }



-    **Schritt 2**: Erstellen eines [**CustomProtectedInputStream**](/rights-management/sdk/4.2/api/android/customprotectedinputstream#msipcthin2_customprotectedinputstream_class_java)-Objekts mithilfe des [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy)-Objekts aus **Schritt 1**.

    **Source**: *MsipcTaskFragment.java*



      CreationCallback<CustomProtectedInputStream> customProtectedInputStreamCreationCallback = new CreationCallback<CustomProtectedInputStream>()
      {
         @Override
         public Context getContext()
         {
             …
         }

         @Override
         public void onCancel()
         {
             …
         }

         @Override
         public void onFailure(ProtectionException e)
         {
             …
         }

         @Override
         public void onSuccess(CustomProtectedInputStream customProtectedInputStream)
         {
            …

             byte[] dataChunk = new byte[16384];
             try
             {
                 while ((nRead = customProtectedInputStream.read(dataChunk, 0, dataChunk.length)) != -1)
                 {
                      …
                 }
                  …
                 customProtectedInputStream.close();
             }
             catch (IOException e)
             {
                …
             }
             …
         }
     };

    try
    {
      ...

      // Retrieve the encrypted content size.
      long encryptedContentLength = readUnsignedInt(inputStream);

      updateTaskStatus(new TaskStatus(TaskState.Starting, "Consuming content", true));

      CustomProtectedInputStream.create(userPolicy, inputStream,
                                     encryptedContentLength,
                                     customProtectedInputStreamCreationCallback);
    }
    catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
    {
      ...
    }
    catch (IOException e)
    {
      ...
    }


-    **Schritt 3**: Lesen von Inhalt aus dem [**CustomProtectedInputStream**](/rights-management/sdk/4.2/api/android/customprotectedinputstream#msipcthin2_customprotectedinputstream_class_java)-Objekt in die *mDecryptedContent*-Instanz und anschließendes Schließen.

    **Source**: *MsipcTaskFragment.java*


    @Override
    public void onSuccess(CustomProtectedInputStream customProtectedInputStream)
    {
      mUserPolicy = customProtectedInputStream.getUserPolicy();
      ByteArrayOutputStream buffer = new ByteArrayOutputStream();

      int nRead;                      
      byte[] dataChunk = new byte[16384];

      try
      {
        while ((nRead = customProtectedInputStream.read(dataChunk, 0,
                                                            dataChunk.length)) != -1)
        {
           buffer.write(dataChunk, 0, nRead);
        }

        buffer.flush();
        mDecryptedContent = new String(buffer.toByteArray(), Charset.forName("UTF-8"));

        buffer.close();
        customProtectedInputStream.close();
      }
      catch (IOException e)
      {
        ...
      }
    }


### Szenario: Erstellen einer benutzerdefinierten geschützten Datei mit einer benutzerdefinierten (Ad-Hoc)-Richtlinie

-   **Schritt 1**: Erstellen einer Richtlinienbeschreibung mit einer vom Benutzer angegebenen E-Mail-Adresse.

    **Quelle**: *MsipcTaskFragment.java*

    **Beschreibung**: In der Praxis würden die folgenden Objekte mithilfe von Benutzereingaben von der Geräteschnittstelle erstellt werden: [**UserRights**](/rights-management/sdk/4.2/api/android/userrights#msipcthin2_userrights_class_java) und [**PolicyDescriptor**](https://stage.docs.microsoft.com/en-us/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_interface_java).



      // create userRights list
      UserRights userRights = new UserRights(Arrays.asList("consumer@domain.com"),
        Arrays.asList( CommonRights.View, EditableDocumentRights.Print));
      ArrayList<UserRights> usersRigthsList = new ArrayList<UserRights>();
      usersRigthsList.add(userRights);

      // Create PolicyDescriptor using userRights list
      PolicyDescriptor policyDescriptor = PolicyDescriptor.createPolicyDescriptorFromUserRights(
                                                             usersRigthsList);
      policyDescriptor.setOfflineCacheLifetimeInDays(10);
      policyDescriptor.setContentValidUntil(new Date());



-    **Schritt 2**: Erstellen eines benutzerdefinierten [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy)-Objekts aus dem Richtliniendeskriptor *selectedDescriptor*.

    **Source**: *MsipcTaskFragment.java*


       mIAsyncControl = UserPolicy.create((PolicyDescriptor)selectedDescriptor,
                                              mEmailId, mRmsAuthCallback,
                                              UserPolicyCreationFlags.NONE,
                                              userPolicyCreationCallback);



-   **Schritt 3**: Erstellen und Schreiben von Inhalt in das [**CustomProtectedOutputStream**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_class_java)-Objekt und anschließendes Schließen.

    **Quelle**: *MsipcTaskFragment.java*


    File file = new File(filePath);
        final OutputStream outputStream = new FileOutputStream(file);
        CreationCallback<CustomProtectedOutputStream> customProtectedOutputStreamCreationCallback = new CreationCallback<CustomProtectedOutputStream>()
        {
            @Override
            public Context getContext()
            {
              …
            }

            @Override
            public void onCancel()
            {
              …
            }

            @Override
            public void onFailure(ProtectionException e)
            {
              …
            }

            @Override
            public void onSuccess(CustomProtectedOutputStream protectedOutputStream)
            {
                try
                {
                    // write serializedContentPolicy
                    byte[] serializedContentPolicy = mUserPolicy.getSerializedContentPolicy();
                    writeLongAsUnsignedIntToStream(outputStream, serializedContentPolicy.length);
                    outputStream.write(serializedContentPolicy);
                    // write encrypted content
                    if (contentToProtect != null)
                    {
                        writeLongAsUnsignedIntToStream(outputStream,
                                CustomProtectedOutputStream.getEncryptedContentLength(contentToProtect.length,
                                        protectedOutputStream.getUserPolicy()));
                        protectedOutputStream.write(contentToProtect);
                        protectedOutputStream.flush();
                        protectedOutputStream.close();
                    }
                    else
                    {
                        outputStream.flush();
                        outputStream.close();
                    }
                    …
                }
                catch (IOException e)
                {
                  …
                }
            }
        };
        try
        {
            mIAsyncControl = CustomProtectedOutputStream.create(outputStream, mUserPolicy,
                    customProtectedOutputStreamCreationCallback);
        }
        catch (InvalidParameterException e)
        {
          …
        }


 

 


<!--HONumber=Apr16_HO3-->

