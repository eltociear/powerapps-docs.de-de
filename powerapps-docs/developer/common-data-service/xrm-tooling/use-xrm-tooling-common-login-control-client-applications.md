---
title: Verwenden des allgemeinen XRM-Tooling-Anmeldesteuerelements in Ihren Client-Anwendungen (Common Data Service für Apps) | Microsoft Docs
description: 'Das „CDS für Apps”-SDK stellt Ihnen eine Vorlage für Visual Studio bereit, mit dessen Hilfe Sie das allgemeine Anmeldungssteuerelement in Ihren Client-Anwendungen verwenden können. Der Code für die „CDS für Apps”-Authentifizierung, das Speichern und Abrufen von Anmeldeinformationen und das diagnostische Protokollieren, sind in der Vorlage integriert, so dass Sie diese Funktionen in Ihren Windows-Client-Anwendungen für CDS für Apps schnell nutzen können.'
ms.custom: ''
ms.date: 1/16/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: f77b2a20-0a30-4211-a1d9-74923d3eeae1
caps.latest.revision: 27
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-xrm-tooling-common-login-control-in-your-client-applications"></a>Verwenden des allgemeinen Anmeldungssteuerelements der XRM-Tools in Ihren Client-Anwendungen

Es gibt eine Vorlage für Visual Studio, mit der Sie das allgemeine Anmeldungssteuerelement in den Client-Anwendungen verwenden können. Der Code für die „CDS für Apps”-Authentifizierung, das Speichern und Abrufen von Anmeldeinformationen und das diagnostische Protokollieren, sind in der Vorlage integriert, so dass Sie diese Funktionen in Ihren Windows-Client-Anwendungen für CDS für Apps schnell nutzen können. Das allgemeine Anmeldungssteuerelement ist eine Implementierung des <xref:Microsoft.Xrm.Tooling.CrmConnectControl>, wobei das Steuerelement dem folgenden Bild gleicht.  
  
 
 ![XRM-Tooling-Anmeldungssteuerelement](../media/crm-sdk-v6-commonlogincontrol.png "XRM-Tooling-Anmeldungssteuerelement")
  
<a name="Prereq"></a>

## <a name="prerequisites"></a>Voraussetzungen
  
- .NET Framework 4.6.2
- Visual Studio 2017 (empfohlen)
- Mit dem Internet verbunden, sodass Sie die erforderlichen Nuget-Pakete herunterzuladen und wiederherstellen können, während Sie die Projektvorlage verwenden.  
  
<a name="NewProjectUsingTemplate"></a>
   
## <a name="create-a-wpf-application-using-the-common-login-control-template"></a>Erstellen einer WPF-Anwendung mithilfe der allgemeinen Anmeldungssteuerelement-Vorlage
  
Im Anschluss finden Sie eine schnelle Methode, um eine Windows Presentation Foundation (WPF)-Anwendung zu erstellen, die das allgemeine Anmeldungssteuerelement verwendet sowie den zugrundeliegenden Code für die Authentifizierung, das Speichern und Wiederverwenden von Anmeldeinformationen und das standardmäßig Rückverfolgen oder Protokollieren.  
  
1.  Starten Sie Visual Studio, und erstellen Sie ein neues Projekt.  
2.  Im Dialogfeld **Neues Projekt**:  
    1.  Erweitern Sie in der Liste der installierten Vorlagen **Visual C#**, und wählen Sie **„CDS für Apps”-SDK Vorlagen** aus.  
    2.  Stellen Sie sicher, dass **.NET Framework 4.6.2** ausgewählt ist.  
    3.  Wählen Sie **WPF-Anwendung für Dynamics 365** aus.  
    4.  Geben Sie den Namen und den Standort des Projekts an, und klicken Sie auf **OK**.  
  
> [!div class="mx-imgBorder"]
> ![WPF-Anwendung für CDS für App-Vorlage](../media/crm-sdk-v6-xrm-tooling-newproject.png "WPF-Anwendung für CDS für App-Vorlage")   

> [!NOTE]
> **Bekannte Probleme mit Visual Studio 2015**
> 
> Wenn Sie Ihr Projekt/Lösung in VS 2015 im Debug-Modus ausführen, können Sie möglicherweise keine Verbindung herstellen. Dies geschieht unabhängig davon, ob Sie ein Zielframework von 4.6.2 oder höher verwenden. Dies kann auftreten, weil der Visual Studio-Hostingprozess gegen .NET 4.5 kompiliert ist, was bedeutet, dass er standardmäßig TLS 1.2 nicht unterstützt. Sie können den Visual Studio-Hostingprozess als Umgehung deaktivieren. 
>
> Klicken Sie mit der rechten Maustaste auf den Namen Ihres Projekts in Visual Studio und dann auf **Eigenschaften**. Auf der Registerkarte **Debuggen** können Sie die Option **Visual Studio Hostingprozess aktivieren** deaktivieren. 
>
> Dies wirkt sich nur auf das Debugging-Umgebung in VS 2015 aus. Es hat keinen Einfluss auf die erstellten Binärdateien bzw. ausführbaren Datei. Das gleiche Problem tritt nicht in Visual Studio 2017 auf.
  
3.  So testen Sie das Projekt:  
  
    1.  Speichern Sie das Projekt, und drücken Sie F5, oder klicken Sie auf **Debuggen** > **Debuggen starten**, um zu überprüfen, ob das Projekt erfolgreich kompiliert wird. Bei erfolgreicher Kompilierung sehen Sie ein MainWindow mit einer **Anmelden bei Dynamics 365**-Schaltfläche. Klicken Sie auf die Schaltfläche, um das Anmeldungssteuerelement anzuzeigen.  
  
    2.  Testen Sie die Authentifizierung, indem Sie Ihre Anmeldeinformationen zur Verbindung mit CDS für Apps angeben, und klicken Sie dann auf **Anmeldung**. Eine Meldung zeigt Ihren „CDS für Apps”-Verbindungsstatus an.  
  
 Ein Beispiel, bei dem die Vorlage des allgemeinen Anmeldungssteuerelements verwendet wird, um eine Verbindung mit CDS für Apps herzustellen und um unterschiedliche Vorgänge ausführen, finden Sie unter [Beispiel: Schnellstart für XRM-Tooling-API](sample-quick-start-xrm-tooling-api.md).  
  
<a name="Add"></a>

## <a name="add-the-common-login-control-template-to-your-existing-wpf-application"></a>Hinzufügen der allgemeinen Anmeldungssteuerelement-Vorlage zur vorhandenen WPF-Anwendung

 Wenn Sie bereits eine WPF-Client-Anwendung haben, können Sie ihr die Vorlage des allgemeinen Anmeldungssteuerelements problemlos hinzufügen zur Nutzung der einheitlichen Anmeldungserfahrung und des zugrunde liegenden Codes für die „CDS für Apps”-Authentifizierung, das Speichern und die Wiederverwendung von Anmeldeinformationen sowie die standardmäßige Nachverfolgung oder Protokollierung. In diesem Fall müssen Sie in der Benutzeroberfläche ein Steuerelement der vorhandenen Client-Anwendung erstellen, um das allgemeine Anmeldungssteuerelement aufzurufen, eine Instanz des „CDS für Apps”-Verbindungsobjekts zu instanziieren und anschließend das Verbindungsobjekt zu verwenden, um verschiedene Vorgänge in CDS für Apps auszuführen.  
  
1.  Öffnen Sie ein vorhandenes WPF-Anwendungsprojekt in Visual Studio. Für dieses Beispiel wird angenommen, dass der Name des WPF-Anwendungsprojekts SampleWPFApp ist.  
  
2.  Hinzufügen der allgemeinen Anmeldungssteuerelement-Vorlage zum Projekt  
  
    1.  Klicken Sie im **Projektmappen-Explorer**-Bereich mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Hinzufügen** > **Neues Element hinzufügen**.  
  
    2.  Erweitern Sie im Dialogfeld **Neues Element hinzufügen** in der Liste der installierten Vorlagen **Visual C#**, und wählen Sie **„CDS für Apps”-SDK-Vorlagen** aus. Klicken Sie auf **„CDS für Apps”„”-Anmeldungsformular für WPF-Anwendungen**, und klicken Sie auf **OK**.  
  
 
 > [!div class="mx-imgBorder"]
 > ![Hinzufügen der Anmeldungssteuerelementvorlage](../media/crm-sdk-v6-xrmtooling-addtemplate01.png "Hinzufügen der Anmeldungssteuerelementvorlage")
  
3.  Das neu hinzugefügte `CrmLoginForm1.xaml`-Anmeldungssteuerelement wirds im XAML-Designerbreich angezeigt. Falls es nicht angezeigt wird, doppelklicken Sie auf die Datei `CrmLoginForm1.xaml` im Bereich **Projektmappen-Explorer**.  
  
 
![Überprüfen, ob das Anmeldungssteuerelement ordnungsgemäß rendert](../media/crm-sdk-v6-xrmtooling-addtemplate03.png "Überprüfen, ob das Anmeldungssteuerelement ordnungsgemäß rendert")
  
4.  Sie müssen jetzt das neu hinzugefügte Anmeldungssteuerelement aus Ihrer Anwendung aufrufen. Fügen Sie dazu ein Steuerelement **Schaltfläche** für Ihre Datei `MainWindow.xaml` hinzu, und legen Sie den Namen und den Inhalt jeweils auf **btnSignIn** und **Bei CDS für Apps anmelden** fest.  
  
 
 > [!div class="mx-imgBorder"]
 > ![Hinzufügen eines Steuerelements zum Aufrufen des Anmeldeformulars](../media/crm-sdk-v6-xrmtooling-addtemplate02.png "Hinzufügen eines Steuerelements zum Aufrufen des Anmeldeformulars")
  
5.  Doppelklicken Sie auf die Schaltfläche, um Code für das Klickereignis der Schaltfläche **btnSignIn** in der Datei `MainWindow.xaml.cs` hinzuzufügen.  
  
6.  Fügen Sie den folgenden Beispielcode zum Klickereignis der Schaltfläche **btnSignIn** hinzu, um das Steuerelement `CrmLoginForm1` aufzurufen, und erstellen Sie eine Instanz des „CDS für Apps”-Verbindungsobjekts.  
  
    ```csharp
    // Establish the Login control.  
    CRMLoginForm1 ctrl = new CRMLoginForm1();  
  
    // Wire event to login response.   
    ctrl.ConnectionToCrmCompleted += ctrl_ConnectionToCrmCompleted;  
  
    // Show the login control.   
    ctrl.ShowDialog();  
  
    // Handle the returned CRM connection object.  
    // On successful connection, display the CRM version and connected org name   
    if (ctrl.CrmConnectionMgr != null && ctrl.CrmConnectionMgr.CrmSvc != null && ctrl.CrmConnectionMgr.CrmSvc.IsReady)  
    {  
        MessageBox.Show("Connected to CRM! Version: " + ctrl.CrmConnectionMgr.CrmSvc.ConnectedOrgVersion.ToString() +   
        " Org: " + ctrl.CrmConnectionMgr.CrmSvc.ConnectedOrgUniqueName, "Connection Status");  
  
        // Perform your actions here  
    }  
    else  
    {  
        MessageBox.Show("Cannot connect; try again!", "Connection Status");  
    }  
    ```  
  
7.  Fügen Sie die Definition des Ereignisses `ctrl_ConnectionToCrmCompleted` unter dem Klickereignis der Schaltfläche hinzu:  
  
    ```csharp  
    private void ctrl_ConnectionToCrmCompleted(object sender, EventArgs e)  
    {  
        if (sender is CRMLoginForm1)  
        {  
            this.Dispatcher.Invoke(() =>  
            {  
                ((CRMLoginForm1)sender).Close();  
            });  
        }  
    }  
    ```  
  
8.  So wird Ihre Datei `MainWindow.xaml.cs` angezeigt, nachdem Code von den vorherigen zwei Schritten hinzugefügt wurde:  
  
![Beispielcode](../media/crm-sdk-v6-xrmtooling-addtemplate04.png "Beispielcode")
  
9. So testen Sie das Projekt:  
  
    1.  Speichern Sie das Projekt, und drücken Sie F5, oder klicken Sie auf **Debuggen** > **Debuggen starten**, um zu überprüfen, ob das Projekt erfolgreich kompiliert wird. Bei erfolgreicher Kompilierung sehen Sie ein MainWindow mit der neuen Schaltfläche **Bei „CDS für Apps” anmelden**. Klicken Sie darauf, um das Anmeldungssteuerelement anzuzeigen.  
  
    2.  Testen Sie die Authentifizierung, indem Sie Ihre Anmeldeinformationen zur Verbindung mit CDS für Apps angeben, und klicken Sie dann auf **Anmeldung**. Wenn erfolgreich, erscheint eine Message darüber, die den Namen der Version und der Organisation, mit der Sie verbunden sind, angibt. Klicken Sie auf **OK**, um die Message zu schließen.  
  
 
> [!div class="mx-imgBorder"]
> ![Projekttestergebnisse](../media/crm-sdk-v6-xrmtooling-addtemplate05.png "Projekttestergebnisse") 
  
    3.  Wenn Sie erneut auf **Bei Dynamics 365 anmelden** klicken, fordert die Anwendung Sie entweder dazu auf, die gespeicherten Anmeldeinformationen aus der letzten Anmeldeaktivität zu wählen oder die neuen Anmeldeinformationen erneut einzugeben.  
  

> [!div class="mx-imgBorder"]
> ![Gespeicherte Anmeldeinformationen](../media/crm-sdk-v6-xrmtooling-addtemplate06.png "Gespeicherte Anmeldeinformationen")
  
### <a name="see-also"></a>Siehe auch  

[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)
