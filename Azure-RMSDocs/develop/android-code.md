---
title: Codebeispiele für Android | Azure RMS
description: In diesem Thema werden wichtige Codeelemente der Android-Version des RMS SDK vorgestellt.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 58CC2E50-1E4D-4621-A947-25312C3FF519
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: e9015fab186df95fa88706674276edb2f8c9ef09
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56255477"
---
# <a name="android-code-examples"></a>Codebeispiele für Android

In diesem Artikel wird das Codieren von Elementen für die Android-Version des Rights Management Services SDK veranschaulicht.

**Hinweis:** In diesem Artikel bezieht sich der Begriff _MSIPC_ (Microsoft Information Protection and Control) auf den Clientprozess.


## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Verwenden von Microsoft Rights Management SDK 4.2 – Schlüsselszenarien

Diese Codebeispiele stammen aus einer größeren Beispielanwendung, die wichtige Entwicklungsszenarios für die Einführung in dieses SDK darstellt. Sie veranschaulichen, wie Folgendes verwendet wird:

- Das Microsoft Protected File-Format, das auch als _geschützte Datei_ bezeichnet wird.
- Formate für benutzerdefinierte geschützte Dateien
- Benutzerdefinierte Steuerelemente der Benutzeroberfläche

Die Beispielanwendung *MSIPCSampleApp* ist zur Verwendung mit diesem SDK für Android-Betriebssysteme verfügbar. Weitere Informationen finden Sie unter [rms-sdk-ui-for-android](https://github.com/AzureAD/rms-sdk-ui-for-android).

### <a name="scenario-consume-an-rms-protected-file"></a>Szenario: Nutzen einer RMS-geschützten Datei

- **Schritt 1**: Erstellen Sie ein [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx)-Objekt.

    **Quelle**: *MsipcAuthenticationCallback.java*

    **Beschreibung**: Instanziieren Sie ein [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx)-Objekt, und implementieren Sie die Dienstauthentifizierung.  Verwenden Sie die [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758250.aspx)-Schnittstelle, um ein Token durch die Übergabe einer Instanz von **AuthenticationRequestCallback** (z.B. der Parameter *mRmsAuthCallback*) an die MSIPC-API abzurufen. Betrachten Sie dazu den Aufruf von [ProtectedFileInputStream.create](https://msdn.microsoft.com/library/dn790851.aspx) kurz vor dem Ende des folgenden Beispielcodeabschnitts.

    ``` java
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
    ```

- **Schritt 2**: Richten Sie die Authentifizierung mithilfe der Active Directory-Authentifizierungsbibliothek (ADAL) ein.

    **Quelle**: *MsipcAuthenticationCallback.java*.

    **Beschreibung**: In diesem Schritt wird die ADAL verwendet, um eine [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx)-Schnittstelle mit den Beispielparametern für die Authentifizierung zu implementieren. Weitere Informationen finden Sie unter [Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx).


~~~
``` java
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
```
~~~

- **Schritt 3:** Überprüfen Sie mit der Methode [UserPolicy.accessCheck](https://msdn.microsoft.com/library/dn790885.aspx), ob dieser Benutzer für diesen Inhalt über die Berechtigung **Bearbeiten** verfügt.

    **Quelle**: *TextEditorFragment.java*

    ``` java
         //check if user has edit rights and apply enforcements
                if (!mUserPolicy.accessCheck(EditableDocumentRights.Edit))
                {
                    mTextEditor.setFocusableInTouchMode(false);
                    mTextEditor.setFocusable(false);
                    mTextEditor.setEnabled(false);
                    …
                }
    ```


### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Szenario: Erstellen einer neuen geschützten Datei mithilfe einer Vorlage

In diesem Szenario wird zunächst eine Liste von Vorlagen abgerufen und die erste Vorlage zum Erstellen einer Richtlinie ausgewählt, und dann wird die neue geschützte Datei erstellt und in sie geschrieben.

- **Schritt 1**: Abrufen der Liste der Vorlagen über ein [TemplateDescriptor](https://msdn.microsoft.com/library/dn790871.aspx)-Objekt.

    **Quelle**: *MsipcTaskFragment.java*

    ``` java
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
    ```

- **Schritt 2**: Erstellen eines [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)-Objekts mithilfe der ersten Vorlage in der Liste.

    **Quelle**: *MsipcTaskFragment.java*

    ``` java
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
    ```

-  **Schritt 3:** Erstellen eines [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx)-Objekts und Schreiben von Inhalt in dieses Objekt.

    **Quelle**: *MsipcTaskFragment.java*

    ``` java
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
    ```


### <a name="scenario-open-a-custom-protected-file"></a>Szenario: Öffnen einer benutzerdefinierten geschützten Datei

- **Schritt 1**: Erstellen eines [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)-Objekts aus einem *serializedContentPolicy*-Objekt.

    **Quelle**: *MsipcTaskFragment.java*

    ``` java
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


~~~
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
```
~~~


- **Step 2**: Create a [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx) using the [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) from **Step 1**.

    **Source**: *MsipcTaskFragment.java*

    ``` java
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
    ```

- **Step 3**: Read content from the [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx) into *mDecryptedContent* then close.

    **Source**: *MsipcTaskFragment.java*

    ``` java
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
    ```

### Scenario: Create a custom protected file using a custom policy

- **Step 1**: With an email address provided by the user, create a policy descriptor.

    **Source**: *MsipcTaskFragment.java*

    **Description**: In practice, the following objects would be created by using user inputs from the device interface; [UserRights](https://msdn.microsoft.com/library/dn790911.aspx) and [PolicyDescriptor](https://msdn.microsoft.com/library/dn790843.aspx).

    ``` java
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
    ```


- **Step 2**: Create a custom [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) from the policy descriptor, *selectedDescriptor*.

    **Source**: *MsipcTaskFragment.java*

    ``` java
       mIAsyncControl = UserPolicy.create((PolicyDescriptor)selectedDescriptor,
         mEmailId, mRmsAuthCallback, UserPolicyCreationFlags.NONE, userPolicyCreationCallback);
    ```


- **Step 3**: Create and write content to the [CustomProtectedOutputStream](https://msdn.microsoft.com/library/dn758274.aspx) and then close.

    **Source**: *MsipcTaskFragment.java*

    ``` java
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
    ```
