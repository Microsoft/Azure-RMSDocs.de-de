![](../media/AzRMS_QuickStartSteps3.PNG)

Für diesen Schritt erstellen und speichern Sie zuerst ein Word-Dokument, das Sie schützen möchten, und geben ihm den Namen **Confidential.docx**. In diesem Tutorial spielt der enthaltene Text keine Rolle. Etwas Text ist jedoch sinnvoll, damit Sie einfacher überprüfen können, ob der Inhalt vom autorisierten Empfänger gelesen werden kann. Beispielsweise können Sie folgenden Text eingeben: **Wenn dieser Text in der E-Mail-Anlage lesbar ist, hat der Absender eine mit Azure RMS geschützte Datei erfolgreich freigegeben.**

Anschließend können Sie das Dokument sicher per E-Mail freigeben.

![Azure RMS-Freigabe per E-Mail – Screenshots](../media/AzRMS_Tutorial_3_Screenshots.png)

#### So geben Sie Ihr Dokument sicher per E-Mail frei

1.  Erstellen Sie in Outlook eine neue Nachricht, und fügen Sie die gerade erstellte Datei an.

2.  Geben Sie in das Feld **An** eine oder mehrere geschäftliche E-Mail-Adressen ein. Sie müssen eine geschäftliche E-Mail-Adresse wie **janetm@contoso.com** oder **p.dover@fabrikam.com** angeben, weil Azure Rights Management momentan keine personenbezogenen E-Mail-Adressen von Internetanbietern unterstützt. Es spielt keine Rolle, ob der Empfänger über Azure Rights Management verfügt oder nicht.

3.  Geben Sie einen Betreff wie  **Vertrauliches Dokument** und dann eine kurze E-Mail-Nachricht wie **Vertrauliches Dokument lesen und nicht weiterleiten**ein.

4.  Klicken Sie dann auf der Registerkarte **Nachricht** in der Gruppe **RMS** auf **Geschützt freigeben** und dann erneut auf **Geschützt freigeben** :

5.  Im Dialogfeld **Geschützt freigeben** :

    1.  Wählen Sie **Anzeigender Benutzer - Nur anzeigen**.

        Dies bedeutet, dass die Empfänger das Dokument anzeigen, jedoch nicht bearbeiten oder ausdrucken können.

    2.  Wählen Sie **E-Mail an mich bei Öffnungsversuchen dieser Dokumente durch andere Benutzer**.

        Sie erhalten jedes Mal eine E-Mail-Benachrichtigung, wenn der Empfänger oder eine andere Person (falls der Empfänger die E-Mail an einen Kollegen weiterleitet) versucht, das Dokument zu öffnen. Im Fall der Weiterleitung sehen Sie, dass der Zugriff verweigert wurde. Sie können dann anhand der Benutzerdetails entscheiden, ob Sie dieser Person eine Kopie des Dokuments zum Öffnen senden möchten.

    3.  Wählen Sie **Sofortigen Widerruf des Zugriffs auf diese Dokumente zulassen**.

        Bei dieser Option muss der Empfänger bei jedem Öffnen der Anlage mit dem Internet verbunden sein. Das hat für den Absender den Vorteil, dass ein nachträglich widerrufenes Dokument beim nächsten Mal nicht mehr geöffnet werden kann. Wenn Sie diese Option nicht auswählen, können die Empfänger das Dokument möglicherweise auch ohne Internetverbindung öffnen. Das hat für den Absender den Nachteil, dass ein Widerruf u. U. erst mit Verzögerung wirksam wird.

    4.  Klicken Sie auf **Jetzt senden**.

        Die E-Mail mit der Anlage wird an die angegebenen E-Mail-Adressen gesendet. Zusätzlich zu Ihrer E-Mail erhält der Empfänger Anweisungen zum Lesen des angehängten und durch Azure Rights Management geschützten Dokuments.

Nachdem Sie Ihr geschütztes Dokument nun gesendet haben, bitten Sie die Empfänger, das Dokument anzunehmen und zu öffnen. Outlook sollte zu diesem Zeitpunkt nicht geschlossen werden, da wir es im letzten Schritt zum Verfolgen der Anlage benötigen.

|Weitere Informationen zu...|Zusätzliche Informationen|
|--------------------------------|--------------------------|
|Umfassende Anweisungen und alternative Methoden zum Schutz der per E-Mail freigegebenen Dateien   →|[Schützen einer per E-Mail freigegebenen Datei mithilfe der Rights Management-Freigabeanwendung](../rms-client/sharing-app-protect-by-email.md)|
|Optionen im Dialogfeld **Geschützt freigeben** →|[Dialogfeldoptionen der Rights Management-Freigabeanwendung](../rms-client/sharing-app-dialog-box.md)|


<!--HONumber=Apr16_HO3-->


