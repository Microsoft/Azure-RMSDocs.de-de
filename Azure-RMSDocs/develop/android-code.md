---
title: "Codebeispiele für Android | Azure RMS"
description: In diesem Thema werden wichtige Codeelemente der Android-Version des RMS SDK vorgestellt.
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58CC2E50-1E4D-4621-A947-25312C3FF519
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503a99f01335f3085b5d13c9faaf0a6f05063490
ms.openlocfilehash: febc212cb6bc4b91058aa0e9f18d1e51f751b552


---

# <a name="android-code-examples"></a>Codebeispiele für Android

In diesem Thema werden wichtige Codeelemente der Android-Version des RMS SDK vorgestellt.

**Hinweis**: Im Beispielcode und in den nachfolgenden Beschreibungen verwenden wir den Begriff MSIPC (Microsoft Information Protection und Steuerelement) zur Bezeichnung des Clientprozesses.


## <a name="using-the-microsoft-rights-management-sdk-42-key-scenarios"></a>Verwenden von Microsoft Rights Management SDK 4.2 – Schlüsselszenarien

Es folgen Codebeispiele aus einer größeren Beispielanwendung, die für die Einführung in dieses SDK wichtig sind. Diese veranschaulichen die Verwendung des Microsoft Protected File-Dateiformats, das auch als geschützte Datei bezeichnet wird, die Verwendung benutzerdefinierter geschützter Dateiformate und die Verwendung benutzerdefinierter Benutzeroberflächen-Steuerelemente.



Die Beispielanwendung *MSIPCSampleApp* ist zur Verwendung mit diesem SDK für Android-Betriebssysteme verfügbar. Unter [rms-sdk-ui-for-android](https://github.com/AzureAD/rms-sdk-ui-for-android) auf GitHub können Sie auf diese Anwendung zugreifen.

### <a name="scenario-consume-an-rms-protected-file"></a>Szenario: Nutzen einer RMS-geschützten Datei

-   **Schritt 1**: Erstellen eines [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx)-Objekts

    **Quelle**: *MsipcAuthenticationCallback.java*

    **Beschreibung**: Instanziieren Sie ein [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx)-Objekt mit dessen create-Methode. Diese Methode implementiert die Dienstauthentifizierung mit [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758250.aspx), um durch die Übergabe einer Instanz von **AuthenticationRequestCallback** als Parameter *mRmsAuthCallback* an die MSIPC-API ein Token abzurufen. Betrachten Sie dazu den Aufruf von [ProtectedFileInputStream.create](https://msdn.microsoft.com/library/dn790851.aspx) kurz vor dem Ende des folgenden Beispielcodeabschnitts.

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

    **Beschreibung**: In diesem Schritt erfahren Sie, wie ADAL zum Implementieren einer [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx)-Funktion mit Beispielauthentifizierungsparametern verwendet wird. Weitere Informationen zur Verwendung von ADAL finden Sie in der [Azure AD-Authentifizierungsbibliothek (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx).


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


-   **Schritt 3**: Überprüfen mit der Methode [UserPolicy.accessCheck](https://msdn.microsoft.comlibrary/dn790885.aspx), ob dieser Benutzer für diesen Inhalt über die Berechtigung **Bearbeiten** verfügt.

    **Quelle**: *TextEditorFragment.java*


         //check if user has edit rights and apply enforcements
                if (!mUserPolicy.accessCheck(EditableDocumentRights.Edit))
                {
                    mTextEditor.setFocusableInTouchMode(false);
                    mTextEditor.setFocusable(false);
                    mTextEditor.setEnabled(false);
                    …
                }


### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Szenario: Erstellen einer neuen geschützten Datei mithilfe einer Vorlage

In diesem Szenario wird zunächst eine Liste von Vorlagen abgerufen und die erste Vorlage zum Erstellen einer Richtlinie ausgewählt, und dann wird die neue geschützte Datei erstellt und in sie geschrieben.

-   **Schritt 1**: Abrufen der Liste der Vorlagen über ein [TemplateDescriptor](https://msdn.microsoft.com/library/dn790871.aspx)-Objekt.

    **Quelle**: *MsipcTaskFragment.java*



    CreationCallback<List<TemplateDescriptor>> getTemplatesCreationCallback = new CreationCallback<List<TemplateDescriptor>>() { @Override public Context getContext() { …
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
      }; try { …
          mIAsyncControl = TemplateDescriptor.getTemplates(emailId, mRmsAuthCallback, getTemplatesCreationCallback); } catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e) { …
      }


-    **Schritt 2**: Erstellen einer [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) mithilfe der ersten Vorlage in der Liste.

    **Quelle**: *MsipcTaskFragment.java*



      CreationCallback<UserPolicy> userPolicyCreationCallback = new CreationCallback<UserPolicy>() { @Override public Context getContext() { …
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
      }; try { …
          mIAsyncControl = UserPolicy.create((TemplateDescriptor)selectedDescriptor, mEmailId, mRmsAuthCallback, UserPolicyCreationFlags.NONE, userPolicyCreationCallback); …
      } catch (InvalidParameterException e) { …
      }


-    **Schritt 3**: Erstellen eines [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx)-Objekts und Schreiben von Inhalt in dieses Objekt.

    **Quelle**: *MsipcTaskFragment.java*


    private void createPTxt(final byte[] contentToProtect) { …
            CreationCallback<ProtectedFileOutputStream> protectedFileOutputStreamCreationCallback = new CreationCallback<ProtectedFileOutputStream>() { @Override public Context getContext() { …
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



### <a name="scenario-open-a-custom-protected-file"></a>Szenario: Öffnen einer benutzerdefinierten geschützten Datei

-   **Schritt 1**: Erstellen eines [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)-Objekts aus einem *serializedContentPolicy*-Objekt.

    **Quelle**: *MsipcTaskFragment.java*


    CreationCallback<UserPolicy> userPolicyCreationCallbackFromSerializedContentPolicy = new CreationCallback<UserPolicy>() { @Override public void onSuccess(UserPolicy userPolicy) { …
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


    try {   ...

      // Lesen Sie die Eigenschaft serializedContentPolicyLength aus inputStream aus.
      long serializedContentPolicyLength = readUnsignedInt(inputStream);

      // Lesen Sie die PL-Bytes aus dem Eingabestream mithilfe der PL-Größe aus.
      byte[] serializedContentPolicy = new byte[(int)serializedContentPolicyLength]; inputStream.read(serializedContentPolicy);

      ...

      UserPolicy.acquire(serializedContentPolicy, null, mRmsAuthCallback, PolicyAcquisitionFlags.NONE,           userPolicyCreationCallbackFromSerializedContentPolicy); } catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e) {   ... } catch (IOException e) {   ... }



-    **Schritt 2**: Erstellen eines [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx)-Objekts mithilfe des [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)-Objekts aus **Schritt 1**.

    **Quelle**: *MsipcTaskFragment.java*



      CreationCallback<CustomProtectedInputStream> customProtectedInputStreamCreationCallback = new CreationCallback<CustomProtectedInputStream>() { @Override public Context getContext() { …
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

    try {  ...

      // Rufen Sie die Größe des verschlüsselten Inhalts ab.
      long encryptedContentLength = readUnsignedInt(inputStream);

      updateTaskStatus(new TaskStatus(TaskState.Starting, "Consuming content", true));

      CustomProtectedInputStream.create(userPolicy, inputStream,                                 encryptedContentLength,                                 customProtectedInputStreamCreationCallback); } catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e) {  ... } catch (IOException e) {  ... }


-    **Schritt 3**: Lesen von Inhalt aus dem [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx)-Objekt in die *mDecryptedContent*-Instanz und anschließendes Schließen.

    **Quelle**: *MsipcTaskFragment.java*


    @Override public void onSuccess(CustomProtectedInputStream customProtectedInputStream) {  mUserPolicy = customProtectedInputStream.getUserPolicy();  ByteArrayOutputStream buffer = new ByteArrayOutputStream();

      int nRead;                      
      byte[] dataChunk = new byte[16384];

      try  {    while ((nRead = customProtectedInputStream.read(dataChunk, 0,                                                        dataChunk.length)) != -1)    {       buffer.write(dataChunk, 0, nRead);    }

        buffer.flush();    mDecryptedContent = new String(buffer.toByteArray(), Charset.forName("UTF-8"));

        buffer.close();    customProtectedInputStream.close();  }  catch (IOException e)  {    ...  } }


### <a name="scenario-create-a-custom-protected-file-using-a-custom-adhoc-policy"></a>Szenario: Erstellen einer benutzerdefinierten geschützten Datei mit einer benutzerdefinierten (Ad-Hoc)-Richtlinie

-   **Schritt 1**: Erstellen einer Richtlinienbeschreibung mit einer vom Benutzer angegebenen E-Mail-Adresse.

    **Quelle**: *MsipcTaskFragment.java*

    **Beschreibung**: In der Praxis würden die Objekte [UserRights](https://msdn.microsoft.com/library/dn790911.aspx) und [PolicyDescriptor](https://msdn.microsoft.com/library/dn790843.aspx) mithilfe von Benutzereingaben über die Geräteschnittstelle erstellt werden.



      // Erstellen Sie eine userRights-Liste   UserRights userRights = new UserRights(Arrays.asList("consumer@domain.com"),     Arrays.asList( CommonRights.View, EditableDocumentRights.Print));   ArrayList<UserRights> usersRigthsList = new ArrayList<UserRights>();   usersRigthsList.add(userRights);

      // Erstellen Sie PolicyDescriptor mithilfe der userRights-Liste   PolicyDescriptor policyDescriptor = PolicyDescriptor.createPolicyDescriptorFromUserRights(                                                          usersRigthsList);   policyDescriptor.setOfflineCacheLifetimeInDays(10);   policyDescriptor.setContentValidUntil(new Date());



-    **Schritt 2**: Erstellen eines benutzerdefinierten [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)-Objekts aus dem Richtliniendeskriptor *selectedDescriptor*.

    **Quelle**: *MsipcTaskFragment.java*


       mIAsyncControl = UserPolicy.create((PolicyDescriptor)selectedDescriptor,                                          mEmailId, mRmsAuthCallback,                                          UserPolicyCreationFlags.NONE,                                          userPolicyCreationCallback);



-   **Schritt 3**: Erstellen und Schreiben von Inhalt in das [CustomProtectedOutputStream](https://msdn.microsoft.com/library/dn758274.aspx)-Objekt und anschließendes Schließen.

    **Quelle**: *MsipcTaskFragment.java*


    File file = new File(filePath); final OutputStream outputStream = new FileOutputStream(file); CreationCallback<CustomProtectedOutputStream> customProtectedOutputStreamCreationCallback = new CreationCallback<CustomProtectedOutputStream>() { @Override public Context getContext() { …
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


 

 



<!--HONumber=Oct16_HO3-->


