---
# required metadata

title: Codebeispiele für Linux | Azure RMS
description: In diesem Thema werden wichtige Szenarien Codeelemente der Linux-Version des RMS SDK vorgestellt.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0F7714CA-1D3E-4846-B187-739825B7DE26
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Codebeispiele für Linux

In diesem Thema werden wichtige Szenarien Codeelemente der Linux-Version des RMS SDK vorgestellt.

Die folgenden Codeausschnitte stammen aus den Beispielanwendungen *rms\_sample* und *rmsauth\_sample*. Weitere Informationen finden Sie im GitHub-Repository unter [Beispiele](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples).

## Szenario: Zugriff auf Informationen der Schutzrichtlinie einer geschützten Datei

**Öffnet und liest eine RMS-geschützte Datei**
**Quelle**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Nachdem ein Dateinamen vom Benutzer erhalten wurde, werden die Zertifikate gelesen (siehe *MainWindow::addCertificates*), der Autorisierungsrückruf mit Client-ID und Umleitungs-URL wird eingerichtet und *ConvertFromPFile* wird aufgerufen (siehe folgendes Codebeispiel). Anschließend werden der Name der Schutzrichtlinie, die Beschreibung und das Gültigkeitsdatum des Inhalts ausgelesen.

**C++**:

    void MainWindow::ConvertFromPFILE(const string&amp; fileIn,
        const string&amp; clientId,
        const string&amp; redirectUrl,
        const string&amp; clientEmail) 
    {
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared&lt;ifstream&gt;(
    fileIn, ios_base::in | ios_base::binary);
    
    if (!inFile-&gt;is_open()) {
     AddLog(&quot;ERROR: Failed to open &quot;, fileIn.c_str());
    return;
    }
    
    string fileOut;
    
    // generate output filename
    auto pos = fileIn.find_last_of(&#39;.&#39;);
    
    if (pos != string::npos) {
     fileOut = fileIn.substr(0, pos);
    }
    
     // create streams
    auto outFile = make_shared&lt;fstream&gt;(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!outFile-&gt;is_open()) {
     AddLog(&quot;ERROR: Failed to open &quot;, fileOut.c_str());
     return;
      }
    
    try
    {
    // create authentication context
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    auto pfs = PFileConverter::ConvertFromPFile(
      clientEmail,
      inFile,
      outFile,
      auth,
      this-&gt;consent);
    
    AddLog(&quot;Successfully converted to &quot;, fileOut.c_str());
    }
    catch (const rmsauth::Exception&amp; e)
    {
    AddLog(&quot;ERROR: &quot;, e.error().c_str());
    }
    catch (const rmscore::exceptions::RMSException&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.what());
    }
    inFile-&gt;close();
    outFile-&gt;close();
    }

**Erstellen eines geschützten Dateidatenstroms**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Diese Methode erstellt mithilfe der SDK-Methode *ProtectedFileStream::Aquire* einen geschützte Dateidatenstrom aus dem eingehenden Sicherungsdatenstrom, der dann an den Aufrufer zurückgegeben wird.

**C++**:

    shared_ptr&lt;GetProtectedFileStreamResult&gt;PFileConverter::ConvertFromPFile(
    const string           &amp; userId,
    shared_ptr&lt;istream&gt;      inStream,
    shared_ptr&lt;iostream&gt;     outStream,
    IAuthenticationCallback&amp; auth,
    IConsentCallback       &amp; consent)
    {
    auto inIStream = rmscrypto::api::CreateStreamFromStdStream(inStream);
    
    auto fsResult = ProtectedFileStream::Acquire(
    inIStream,
    userId,
    auth,
    consent,
    POL_None,
    static_cast&lt;ResponseCacheFlags&gt;(RESPONSE_CACHE_INMEMORY
                                    | RESPONSE_CACHE_ONDISK));
    
    if ((fsResult.get() != nullptr) &amp;&amp; (fsResult-&gt;m_status == Success) &amp;&amp;
      (fsResult-&gt;m_stream != nullptr)) {
    auto pfs = fsResult-&gt;m_stream;
    
    // preparing
    readPosition  = 0;
    writePosition = 0;
    totalSize     = pfs-&gt;Size();
    
    // start threads
    for (size_t i = 0; i &lt; THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast&lt;iostream&gt;(outStream), pfs,
                                  false));
    }
    
    for (thread&amp; t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    }
      return fsResult;
    }

## Szenario: Erstellen einer neuen geschützten Datei mithilfe einer Vorlage

**Schützt eine Datei mit einer vom Benutzer ausgewählten Vorlage**
**Quelle**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Nachdem ein Dateinamen vom Benutzer erhalten wurde, werden die Zertifikate gelesen (siehe *MainWindow::addCertificates*) und der Autorisierungsrückruf mit Client-ID und Umleitungs-URL wird eingerichtet. Die ausgewählte Datei wird durch den Aufruf von *ConvertToPFileTemplates* geschützt (siehe folgendes Codebeispiel).

**C++**:

    void MainWindow::ConvertToPFILEUsingTemplates(const string&amp; fileIn,
                                              const string&amp; clientId,
                                              const string&amp; redirectUrl,
                                              const string&amp; clientEmail) 
    {
    // generate output filename
    string fileOut = fileIn + &quot;.pfile&quot;;
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared&lt;ifstream&gt;(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared&lt;fstream&gt;(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileIn.c_str());
    return;
    }
    
    if (!outFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of(&#39;.&#39;);
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFileTemplates(
      clientEmail, inFile, fileExt, outFile, auth,
      this-&gt;consent, this-&gt;templates);
    
    AddLog(&quot;Successfully converted to &quot;, fileOut.c_str());
    }
   catch (const rmsauth::Exception&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.error().c_str());
    outFile-&gt;close();
    remove(fileOut.c_str());
    }
    catch (const rmscore::exceptions::RMSException&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.what());
    
    outFile-&gt;close();
    remove(fileOut.c_str());
    }
    inFile-&gt;close();
    outFile-&gt;close();
    }


**Schützt eine Datei mithilfe einer Richtlinie, die aus einer Vorlage erstellt wurde**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Eine Liste mit dem Benutzer zugeordneten Vorlagen wird abgerufen. Mithilfe der ausgewählte Vorlage wird dann eine Richtlinie zum Schutz der Datei erstellt.

**C++**:

    void PFileConverter::ConvertToPFileTemplates(const string           &amp; userId,
                                             shared_ptr&lt;istream&gt;      inStream,
                                             const string           &amp; fileExt,
                                             std::shared_ptr&lt;iostream&gt;outStream,
                                             IAuthenticationCallback&amp; auth,
                                             IConsentCallback&amp; /*consent*/,
                                             ITemplatesCallback     &amp; templ)
    {
    auto templates = TemplateDescriptor::GetTemplateList(userId, auth);
    
    rmscore::modernapi::AppDataHashMap signedData;
    
    size_t pos = templ.SelectTemplate(templates);
    
    if (pos &lt; templates.size()) {
    auto policy = UserPolicy::CreateFromTemplateDescriptor(
      templates[pos],
      userId,
      auth,
      USER_AllowAuditedExtraction,
      signedData);
   
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    }
    }

**Schützt eine Datei auf Grundlage eine Richtlinie**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Hierbei wird ein geschützter Dateidatenstrom mithilfe der angegebenen Richtlinie erstellt und anschließend die Datei geschützt.

**C++**:

    void PFileConverter::ConvertToPFileUsingPolicy(shared_ptr&lt;UserPolicy&gt;   policy,
                                               shared_ptr&lt;istream&gt;      inStream,
                                               const string           &amp; fileExt,
                                               std::shared_ptr&lt;iostream&gt;outStream)
    {
    if (policy.get() != nullptr) {
    auto outIStream = rmscrypto::api::CreateStreamFromStdStream(outStream);
    auto pStream    = ProtectedFileStream::Create(policy, outIStream, fileExt);
    
    // preparing
    readPosition  = 0;
    writePosition = pStream-&gt;Size();
    
    inStream-&gt;seekg(0, ios::end);
    totalSize = inStream-&gt;tellg();
    
    // start threads
    for (size_t i = 0; i &lt; THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast&lt;iostream&gt;(inStream),
                                  pStream,
                                  true));
    }
    
    for (thread&amp; t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    
    pStream-&gt;Flush();
    }
    


## Szenario: Schützen einer Datei mit benutzerdefiniertem Schutz

**Schützt eine Datei mit benutzerdefiniertem Schutz**
**Quelle**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Nachdem ein Dateinamen vom Benutzer erhalten wurde, werden die Zertifikate gelesen (siehe *MainWindow::addCertificates*), Informationen zu den jeweiligen Benutzerrechten abgerufen und der Autorisierungsrückruf mit Client-ID und Umleitungs-URL eingerichtet. Die ausgewählte Datei wird durch den Aufruf von *ConvertToPFilePredefinedRights* geschützt (siehe folgendes Codebeispiel).

**C++**:

    void MainWindow::ConvertToPFILEUsingRights(const string            &amp; fileIn,
                                           const vector&lt;UserRights&gt;&amp; userRights,
                                           const string            &amp; clientId,
                                           const string            &amp; redirectUrl,
                                           const string            &amp; clientEmail)
    {
    // generate output filename
    string fileOut = fileIn + &quot;.pfile&quot;;
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared&lt;ifstream&gt;(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared&lt;fstream&gt;(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileIn.c_str());
    return;
    }
    
    if (!outFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of(&#39;.&#39;);
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    // is anything to add
    if (userRights.size() == 0) {
    AddLog(&quot;ERROR: &quot;, &quot;Please fill email and check rights&quot;);
    return;
    }
    
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFilePredefinedRights(
      clientEmail,
      inFile,
      fileExt,
      outFile,
      auth,
      this-&gt;consent,
      userRights);
    
    AddLog(&quot;Successfully converted to &quot;, fileOut.c_str());
    }
    catch (const rmsauth::Exception&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.error().c_str());
    
    outFile-&gt;close();
    remove(fileOut.c_str());
    }
    catch (const rmscore::exceptions::RMSException&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.what());
    
    outFile-&gt;close();
    remove(fileOut.c_str());
    }
    inFile-&gt;close();
    outFile-&gt;close();
    }


**Erstellt einer Schutzrichtlinie, um Benutzern ausgewählte Rechte zu erteilen**
**Quelle**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Beschreibung**: Hierbei wird eine Richtlinienbeschreibung erstellt und mit den Informationen zu den jeweiligen Benutzerrechten gefüllt. Anschließend wird mit der Richtlinienbeschreibung eine Benutzerrichtlinie erstellt. Diese Richtlinie dient zum Schutz der ausgewählten Datei. Dabei wird *ConvertToPFileUsingPolicy* aufgerufen. (Eine Beschreibung hierzu finden Sie weiter oben in diesem Thema.)

**C++**:

    void PFileConverter::ConvertToPFilePredefinedRights(
    const string            &amp; userId,
    shared_ptr&lt;istream&gt;       inStream,
    const string            &amp; fileExt,
    shared_ptr&lt;iostream&gt;      outStream,
    IAuthenticationCallback &amp; auth,
    IConsentCallback&amp; /*consent*/,
    const vector&lt;UserRights&gt;&amp; userRights)
    {
    auto endValidation = chrono::system_clock::now() + chrono::hours(48);
    
    
    PolicyDescriptor desc(userRights);
    
    desc.Referrer(make_shared&lt;string&gt;(&quot;https://client.test.app&quot;));
    desc.ContentValidUntil(endValidation);
    desc.AllowOfflineAccess(false);
    desc.Name(&quot;Test Name&quot;);
    desc.Description(&quot;Test Description&quot;);
    
    auto policy = UserPolicy::Create(desc, userId, auth,
                                   USER_AllowAuditedExtraction);
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    

## WorkerThread – eine unterstützende Methode


Die *WorkerThread()*-Methode wird in den beiden vorherigen Szenarien **Erstellen eines geschützten Dateidatenstroms** und **Schützt eine Datei auf Grundlage eine Richtlinie** auf folgende Weise aufgerufen:

**C++**:

    threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast&lt;iostream&gt;(outStream), pfs,
                                  false));


**Unterstützende Methode, WorkerThread()**

**C++**:

    static mutex   threadLocker;
    static int64_t totalSize     = 0;
    static int64_t readPosition  = 0;
    static int64_t writePosition = 0;
    static vector&lt;thread&gt; threadPool;
    
    static void WorkerThread(shared_ptr&lt;iostream&gt;           stdStream,
                         shared_ptr&lt;ProtectedFileStream&gt;pStream,
                         bool                           modeWrite) {
    vector&lt;uint8_t&gt; buffer(4096);
    int64_t bufferSize = static_cast&lt;int64_t&gt;(buffer.size());
    
    while (totalSize - readPosition &gt; 0) {
    // lock
    threadLocker.lock();
    
    // check remain
    if (totalSize - readPosition &lt;= 0) {
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
    
        stdStream-&gt;seekg(offsetRead);
        stdStream-&gt;read(reinterpret_cast&lt;char *&gt;(&amp;buffer[0]), toProcess);
        threadLocker.unlock();
        auto written =
          pStream-&gt;WriteAsync(
            buffer.data(), toProcess, offsetWrite, std::launch::deferred).get();
    
        if (written != toProcess) {
          throw rmscore::exceptions::RMSStreamException(&quot;Error while writing data&quot;);
        }
      }
      catch (exception&amp; e) {
        qDebug() &lt;&lt; &quot;Exception: &quot; &lt;&lt; e.what();
      }
    } else {
      auto read =
        pStream-&gt;ReadAsync(&amp;buffer[0],
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
        stdStream-&gt;seekp(offsetWrite);
        stdStream-&gt;write(reinterpret_cast&lt;const char *&gt;(buffer.data()), read);
        threadLocker.unlock();
      }
      catch (exception&amp; e) {
        qDebug() &lt;&lt; &quot;Exception: &quot; &lt;&lt; e.what();
      }
    }
    }
    }


## Szenario: RMS-Authentifizierung

Die folgenden Beispiele zeigen zwei verschiedene Authentifizierungsmethoden, bei denen das Azure-Authentifizierungstoken oAuth2 mit und ohne Benutzeroberfläche abgerufen wird.
**Abrufen des oAuth2-Authentifizierungstokens mit Benutzeroberfläche**
**Quelle**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Schritt 1**: Erstellen eines gemeinsamen Punkts des **rmsauth::FileCache**-Objekts
Beschreibung: Sie können den Cachepfad festlegen oder die Standardeinstellung verwenden.

**C++**:

    auto FileCachePtr = std::make_shared&lt; rmsauth::FileCache&gt;();


**Schritt 2**: Erstellen eines **rmsauth::AuthenticationContext**-Objekts
Beschreibung: Legen Sie den Azure-*Registrierungsstellen-URI* und das *FileCache*-Objekt fest.

**C++**:

    AuthenticationContext authContext(
                              std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                              AuthorityValidationType::False,
                              FileCachePtr);


**Schritt 3**: Aufrufen der **aquireToken**-Methode des **authContext**-Objekts und Festlegen der folgenden Parameter:
Beschreibung:

-   *Angeforderte Ressource*: die geschützte Ressource, auf die Sie zugreifen möchten
-   *Eindeutige Client-ID*: normalerweise eine GUID
-   *Umleitungs-URI*: der URI, der nach Abruf des Authentifizierungstokens neu adressiert wird
-   *Verhalten der Authentifizierungeingabeaufforderung*: Wenn Sie **PromptBehavior::Auto** festlegen, versucht die Bibliothek bei Bedarf, den Cache und das Aktualisierungstoken zu verwenden.
-   *Benutzer-ID*: der im Eingabeaufforderungsfenster angezeigte Benutzername

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                std::string(“https://client.test.app”),
                PromptBehavior::Auto,
                std::string(“john.smith@msopentechtest01.onmicrosoft.com”));


**Schritt 4**: Abrufen des Zugriffstokens aus den Ergebnissen
Beschreibung: Rufen Sie die **result-&gt; accessToken()**-Methode auf.

**Hinweis**  Die Authentifizierungsbibliotheksmethoden können **rmsauth::Exception** auslösen.

 
**Abrufen des oAuth2-Authentifizierungstokens ohne Benutzeroberfläche**
**Quelle**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Schritt 1**: Erstellen eines gemeinsamen Punkts des **rmsauth::FileCache**-Objekts
Beschreibung: Sie können den Cachepfad festlegen oder die Standardeinstellung verwenden.

**C++**:

    auto FileCachePtr = std::make_shared&lt; rmsauth::FileCache&gt;();


**Schritt 2**: Erstellen eines **UserCredential**-Objekts
Beschreibung: Legen Sie den *Benutzernamen* und das *Kennwort* fest.

**C++**:

    auto userCred = std::make_shared&lt;UserCredential&gt;(&quot;john.smith@msopentechtest01.onmicrosoft.com&quot;,
                                                 &quot;SomePass&quot;);


**Schritt 3**: Erstellen eines **rmsauth::AuthenticationContext**-Objekts
Beschreibung: Legen Sie den Azure-*Registrierungsstellen-URI* und das *FileCache*-Objekt fest.

**C++**:

    AuthenticationContext authContext(
                        std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                        AuthorityValidationType::False,
                        FileCachePtr);


**Schritt 4**: Aufrufen der **aquireToken**-Methode des **authContext**-Objekts und Festlegen der Parameter:
-   *Angeforderte Ressource*: die geschützte Ressource, auf die Sie zugreifen möchten
-   *Eindeutige Client-ID*: normalerweise eine GUID
-   *Benutzeranmeldeinformationen*: Übergeben Sie das erstellte Objekt.

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                userCred);


**Schritt 5**: Abrufen des Zugriffstokens aus den Ergebnissen
Beschreibung: Rufen Sie die **result-&gt; accessToken()**-Methode auf.

**Hinweis**  Die Authentifizierungsbibliotheksmethoden können **rmsauth::Exception** auslösen.



<!--HONumber=Apr16_HO4-->


