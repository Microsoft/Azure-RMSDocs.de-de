---
title: Codebeispiele für Linux | Azure RMS
description: In diesem Thema werden wichtige Szenarien Codeelemente der Linux-Version des RMS SDK vorgestellt.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0F7714CA-1D3E-4846-B187-739825B7DE26
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: dec0a095b84d265d3594112b24beba8aae923959
ms.sourcegitcommit: e8c3def412267905871928448f3810731b5c0443
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632275"
---
# <a name="linux-code-examples"></a>Linux-Codebeispiele

In diesem Thema werden wichtige Szenarien Codeelemente der Linux-Version des RMS SDK vorgestellt.

Die folgenden Codeausschnitte stammen aus den Beispielanwendungen *rms\_sample* und *rmsauth\_sample*. Weitere Informationen finden Sie im GitHub-Repository unter [Beispiele](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples).

## <a name="scenario-access-protection-policy-information-from-a-protected-file"></a>Szenario: Zugriff auf Informationen der Schutzrichtlinie einer geschützten Datei

**Öffnet und liest eine RMS-geschützte Datei**
**Quelle**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Nachdem ein Dateinamen vom Benutzer erhalten wurde, werden die Zertifikate gelesen (siehe *MainWindow::addCertificates*), der Autorisierungsrückruf mit Client-ID und Umleitungs-URL wird eingerichtet und *ConvertFromPFile* wird aufgerufen (siehe folgendes Codebeispiel). Anschließend werden der Name der Schutzrichtlinie, die Beschreibung und das Gültigkeitsdatum des Inhalts ausgelesen.

**C++** :

    void MainWindow::ConvertFromPFILE(const string& fileIn,
        const string& clientId,
        const string& redirectUrl,
        const string& clientEmail) 
    {
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    
    if (!inFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    string fileOut;
    
    // generate output filename
    auto pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
     fileOut = fileIn.substr(0, pos);
    }
    
     // create streams
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!outFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileOut.c_str());
     return;
      }
    
    try
    {
    // create authentication context
    AuthCallback auth(clientId, redirectUrl);
    
    // process conversion
    auto pfs = PFileConverter::ConvertFromPFile(
      clientEmail,
      inFile,
      outFile,
      auth,
      this->consent);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e)
    {
    AddLog("ERROR: ", e.error().c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    }
    inFile->close();
    outFile->close();
    }

**Erstellen eines geschützten Dateidatenstroms**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Description**: Diese Methode erstellt einen geschützten Dateistream aus dem weiter gegebenen sicherungsstream über die SDK-Methode *protectedfilestream::* Abruf, die dann an den Aufrufer zurückgegeben wird.

**C++** :

    shared_ptr<GetProtectedFileStreamResult>PFileConverter::ConvertFromPFile(
    const string           & userId,
    shared_ptr<istream>      inStream,
    shared_ptr<iostream>     outStream,
    IAuthenticationCallback& auth,
    IConsentCallback       & consent)
    {
    auto inIStream = rmscrypto::api::CreateStreamFromStdStream(inStream);
    
    auto fsResult = ProtectedFileStream::Acquire(
    inIStream,
    userId,
    auth,
    consent,
    POL_None,
    static_cast<ResponseCacheFlags>(RESPONSE_CACHE_INMEMORY
                                    | RESPONSE_CACHE_ONDISK));
    
    if ((fsResult.get() != nullptr) && (fsResult->m_status == Success) &&
      (fsResult->m_stream != nullptr)) {
    auto pfs = fsResult->m_stream;
    
    // preparing
    readPosition  = 0;
    writePosition = 0;
    totalSize     = pfs->Size();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    }
      return fsResult;
    }

## <a name="scenario-create-a-new-protected-file-using-a-template"></a>Szenario: Erstellen einer neuen geschützten Datei mithilfe einer Vorlage

**Schützt eine Datei mit einer vom Benutzer ausgewählten Vorlage**
**Quelle**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Nachdem ein Dateinamen vom Benutzer erhalten wurde, werden die Zertifikate gelesen (siehe *MainWindow::addCertificates*) und der Autorisierungsrückruf mit Client-ID und Umleitungs-URL wird eingerichtet. Die ausgewählte Datei wird durch den Aufruf von *ConvertToPFileTemplates* geschützt (siehe folgendes Codebeispiel).

**C++** :

    void MainWindow::ConvertToPFILEUsingTemplates(const string& fileIn,
                                              const string& clientId,
                                              const string& redirectUrl,
                                              const string& clientEmail) 
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process conversion
    PFileConverter::ConvertToPFileTemplates(
      clientEmail, inFile, fileExt, outFile, auth,
      this->consent, this->templates);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
   catch (const rmsauth::Exception& e) { AddLog("ERROR: ", e.error().c_str()); outFile->close(); remove(fileOut.c_str()); } catch (const rmscore::exceptions::RMSException& e) { AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**Schützt eine Datei mithilfe einer aus einer Vorlage erstellten Richtlinie**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Eine Liste mit dem Benutzer zugeordneten Vorlagen wird abgerufen. Mithilfe der ausgewählte Vorlage wird dann eine Richtlinie zum Schutz der Datei erstellt.

**C++** :

    void PFileConverter::ConvertToPFileTemplates(const string           & userId,
                                             shared_ptr<istream>      inStream,
                                             const string           & fileExt,
                                             std::shared_ptr<iostream>outStream,
                                             IAuthenticationCallback& auth,
                                             IConsentCallback& /*consent*/,
                                             ITemplatesCallback     & templ)
    {
    auto templates = TemplateDescriptor::GetTemplateList(userId, auth);
    
    rmscore::modernapi::AppDataHashMap signedData;
    
    size_t pos = templ.SelectTemplate(templates);
    
    if (pos < templates.size()) {
    auto policy = UserPolicy::CreateFromTemplateDescriptor(
      templates[pos],
      userId,
      auth,
      USER_AllowAuditedExtraction,
      signedData);
   
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    }
    }

**Schützt eine Datei auf Grundlage einer Richtlinie**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Hierbei wird ein geschützter Dateidatenstrom mithilfe der angegebenen Richtlinie erstellt und anschließend die Datei geschützt.

**C++** :

    void PFileConverter::ConvertToPFileUsingPolicy(shared_ptr<UserPolicy>   policy,
                                               shared_ptr<istream>      inStream,
                                               const string           & fileExt,
                                               std::shared_ptr<iostream>outStream)
    {
    if (policy.get() != nullptr) {
    auto outIStream = rmscrypto::api::CreateStreamFromStdStream(outStream);
    auto pStream    = ProtectedFileStream::Create(policy, outIStream, fileExt);
    
    // preparing
    readPosition  = 0;
    writePosition = pStream->Size();
    
    inStream->seekg(0, ios::end);
    totalSize = inStream->tellg();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(inStream),
                                  pStream,
                                  true));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    
    pStream->Flush();
    }
    


## <a name="scenario-protect-a-file-using-custom-protection"></a>Szenario: Schützen einer Datei mit benutzerdefiniertem Schutz

**Schützt eine Datei mit benutzerdefiniertem Schutz**
**Quelle**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Nachdem ein Dateinamen vom Benutzer erhalten wurde, werden die Zertifikate gelesen (siehe *MainWindow::addCertificates*), Informationen zu den jeweiligen Benutzerrechten abgerufen und der Autorisierungsrückruf mit Client-ID und Umleitungs-URL eingerichtet. Die ausgewählte Datei wird durch den Aufruf von *ConvertToPFilePredefinedRights* geschützt (siehe folgendes Codebeispiel).

**C++** :

    void MainWindow::ConvertToPFILEUsingRights(const string            & fileIn,
                                           const vector<UserRights>& userRights,
                                           const string            & clientId,
                                           const string            & redirectUrl,
                                           const string            & clientEmail)
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    // is anything to add
    if (userRights.size() == 0) {
    AddLog("ERROR: ", "Please fill email and check rights");
    return;
    }
    
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process conversion
    PFileConverter::ConvertToPFilePredefinedRights(
      clientEmail,
      inFile,
      fileExt,
      outFile,
      auth,
      this->consent,
      userRights);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e) {
    AddLog("ERROR: ", e.error().c_str());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**Erstellt eine Schutzrichtlinie, um dem Benutzer ausgewählte Rechte zu erteilen**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Hierbei wird eine Richtlinienbeschreibung erstellt und mit den Informationen zu den jeweiligen Benutzerrechten gefüllt. Anschließend wird mit der Richtlinienbeschreibung eine Benutzerrichtlinie erstellt. Diese Richtlinie dient zum Schutz der ausgewählten Datei. Dabei wird *ConvertToPFileUsingPolicy* aufgerufen. (Eine Beschreibung hierzu finden Sie weiter oben in diesem Thema.)

**C++** :

    void PFileConverter::ConvertToPFilePredefinedRights(
    const string            & userId,
    shared_ptr<istream>       inStream,
    const string            & fileExt,
    shared_ptr<iostream>      outStream,
    IAuthenticationCallback & auth,
    IConsentCallback& /*consent*/,
    const vector<UserRights>& userRights)
    {
    auto endValidation = chrono::system_clock::now() + chrono::hours(48);
    
    
    PolicyDescriptor desc(userRights);
    
    desc.Referrer(make_shared<string>("https://client.test.app"));
    desc.ContentValidUntil(endValidation);
    desc.AllowOfflineAccess(false);
    desc.Name("Test Name");
    desc.Description("Test Description");
    
    auto policy = UserPolicy::Create(desc, userId, auth,
                                   USER_AllowAuditedExtraction);
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    

## <a name="workerthread---a-supporting-method"></a>WorkerThread – eine unterstützende Methode


Die *WorkerThread()* -Methode wird in den beiden vorherigen Szenarien **Erstellen eines geschützten Dateidatenstroms** und **Schützt eine Datei auf Grundlage eine Richtlinie** auf folgende Weise aufgerufen:

**C++** :

    threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));


**Unterstützende Methode, WorkerThread()**

**C++** :

    static mutex   threadLocker;
    static int64_t totalSize     = 0;
    static int64_t readPosition  = 0;
    static int64_t writePosition = 0;
    static vector<thread> threadPool;
    
    static void WorkerThread(shared_ptr<iostream>           stdStream,
                         shared_ptr<ProtectedFileStream>pStream,
                         bool                           modeWrite) {
    vector<uint8_t> buffer(4096);
    int64_t bufferSize = static_cast<int64_t>(buffer.size());
    
    while (totalSize - readPosition > 0) {
    // lock
    threadLocker.lock();
    
    // check remain
    if (totalSize - readPosition <= 0) {
      threadLocker.unlock();
      return;
    }
    
    // get read/write offset
    int64_t offsetRead  = readPosition;
    int64_t offsetWrite = writePosition;
    int64_t toProcess   = min(bufferSize, totalSize - readPosition);
    readPosition  += toProcess;
    writePosition += toProcess;
    
    // no need to lock more
    threadLocker.unlock();
    
    if (modeWrite) {
      // stdStream is not thread safe!!!
      try {
        threadLocker.lock();
    
        stdStream->seekg(offsetRead);
        stdStream->read(reinterpret_cast<char *>(&buffer[0]), toProcess);
        threadLocker.unlock();
        auto written =
          pStream->WriteAsync(
            buffer.data(), toProcess, offsetWrite, std::launch::deferred).get();
    
        if (written != toProcess) {
          throw rmscore::exceptions::RMSStreamException("Error while writing data");
        }
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    } else {
      auto read =
        pStream->ReadAsync(&buffer[0],
                           toProcess,
                           offsetRead,
                           std::launch::deferred).get();
    
      if (read == 0) {
        break;
      }
    
      try {
        // stdStream is not thread safe!!!
        threadLocker.lock();
    
        // seek to write
        stdStream->seekp(offsetWrite);
        stdStream->write(reinterpret_cast<const char *>(buffer.data()), read);
        threadLocker.unlock();
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    }
    }
    }


## <a name="scenario-rms-authentication"></a>Szenario: RMS-Authentifizierung

Die folgenden Beispiele zeigen zwei verschiedene Authentifizierungsmethoden, bei denen das Azure-Authentifizierungstoken oAuth2 mit und ohne Benutzeroberfläche abgerufen wird.
**Abrufen des OAuth2-Authentifizierungstokens mit Benutzeroberfläche**
**Quelle**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Schritt 1**: Erstellen eines gemeinsamen Punkts des **rmsauth::FileCache**-Objekts
Beschreibung: Sie können den Cachepfad festlegen oder die Standardeinstellung verwenden.

**C++** :

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**Schritt 2**: Erstellen des Objekts **rmsauth::AuthenticationContext**. Beschreibung: Angeben des Azure-*Registrierungsstellen-URI* und des Objekts *FileCache*.

**C++** :

    AuthenticationContext authContext(
                              std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                              AuthorityValidationType::False,
                              FileCachePtr);


**Schritt 3**: Aufrufen der **acquiretoken** -Methode des **authcontext** -Objekts und angeben der nächsten Parameter: Beschreibung:

-   *Angeforderte Ressource*: die geschützte Ressource, auf die Sie zugreifen möchten
-   *Eindeutige Client-ID*: normalerweise eine GUID
-   *Umleitungs-URI*: der URI, der nach Abruf des Authentifizierungstokens neu adressiert wird
-   *Verhalten der Authentifizierungeingabeaufforderung*: Wenn Sie **PromptBehavior::Auto** festlegen, versucht die Bibliothek bei Bedarf, den Cache und das Aktualisierungstoken zu verwenden.
-   *Benutzer-ID*: der im Eingabeaufforderungsfenster angezeigte Benutzername

**C++** :

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                std::string(“https://client.test.app”),
                PromptBehavior::Auto,
                std::string(“john.smith@msopentechtest01.onmicrosoft.com”));


**Schritt 4**: Abrufen des Zugriffstokens aus den Ergebnissen. Beschreibung: Aufrufen der **result-> accessToken()** -Methode

**Hinweis**  Die Authentifizierungsbibliotheksmethoden können **rmsauth::Exception** auslösen.

 
**Abrufen des OAuth2-Authentifizierungstokens ohne Benutzeroberfläche**
**Quelle**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Schritt 1**: Erstellen eines gemeinsamen Punkts des Objekts **rmsauth::FileCache**. Beschreibung: Sie können den Cachepfad festlegen oder die Standardeinstellung verwenden

**C++** :

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**Schritt 2**: Erstellen des Objekts **UserCredential**. Beschreibung: Angeben des *Benutzernamens* und des *Kennworts*

**C++** :

    auto userCred = std::make_shared<UserCredential>("john.smith@msopentechtest01.onmicrosoft.com",
                                                 "SomePass");


**Schritt 3**: Erstellen des Objekts **rmsauth::AuthenticationContext**. Beschreibung: Angeben des Azure-Registrierungsstellen-*URI* und des Objekts *FileCache*

**C++** :

    AuthenticationContext authContext(
                        std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                        AuthorityValidationType::False,
                        FileCachePtr);


**Schritt 4**: Aufrufen der **acquiretoken** -Methode von **authcontext** und Angeben von Parametern:
-   *Angeforderte Ressource*: die geschützte Ressource, auf die Sie zugreifen möchten
-   *Eindeutige Client-ID*: normalerweise eine GUID
-   *Benutzeranmeldeinformationen*: Übergeben Sie das erstellte Objekt.

**C++** :

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                userCred);


**Schritt 5**: Abrufen des Zugriffstokens aus den Ergebnissen. Beschreibung: Aufrufen der **result-> accessToken()** -Methode

**Hinweis**  Die Authentifizierungsbibliotheksmethoden können **rmsauth::Exception** auslösen.
