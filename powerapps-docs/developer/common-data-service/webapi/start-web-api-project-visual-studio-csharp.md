---
title: 'Ein Common Data Service for Apps Web API-Projekt in Visual Studio (C#) starten (Common Data Service for Apps)| Microsoft Docs'
description: 'Erstellen Sie ein neues Projekt in Visual Studio, um eine Konsolenanwendung zu unterstützen, die Common Data Service for Apps-Web-API verwendet'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 08377156-32c7-492a-8e66-50a47a330dc6
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="start-a-common-data-service-for-apps-web-api-project-in-visual-studio-c"></a>Ein Common Data Service for Apps Web API-Projekt in Visual Studio (C#) starten

Dieses Thema zeigt, wie Sie ein neues Projekt in Visual Studio erstellt, das eine Konsolenanwendung erstellt, die die Common Data Service for Apps-Web-API verwendet. Es zeigt die allgemeinen Verweise werden Projektressourcen, die die meisten Anwendungen, einschließlich den SDK-C#-Beispielen, verwenden, um Web-API-basierte Lösungen zu implementieren.  
  
<a name="bkmk_prerequisites"></a> 
  
## <a name="prerequisites"></a>Voraussetzungen  

 Die folgenden Voraussetzungen sind zur Erstellung der Konsolenanwendung in diesem Abschnitt erforderlich.  
  
- Visual Studio 2015, das auf dem Entwicklungscomputer installiert ist. Jede Edition, inkl. [Visual Studio Express](https://www.visualstudio.com/products/visual-studio-express-vs.aspx), sollte ausreichend sein, um mit der Common Data Service for Apps-Web-API zu arbeiten.
  
-   Ein NuGet-Client muss installiert sein. Entweder mit dem Befehlszeilenprogramm oder der Visual Studio-Erweiterung. Weitere Informationen finden Sie unter [Installieren von NuGet](https://docs.nuget.org/consume/installing-nuget).  
  
-   Eine Internetverbindung ist erforderlich, damit das NuGet-Paket, die Common Data Service for Apps-Web-API Hilfebibliothek und weitere abhängige Pakete heruntergeladen werden können.
  
<a name="bkmk_createProject"></a>
   
## <a name="create-a-project"></a>Erstellen eines Projekts  

<!-- TODO: The following procedure demonstrates how to create a console application project in C# that uses the Microsoft .NET Framework. For more information on supported versions of the .NET Framework, see [Supported extensions](../supported-extensions.md).   -->
  
<a name="bkmk_newProject"></a>

### <a name="new-project"></a>Neues Projekt  
  
1.  Klicken Sie in Visual Studio auf **Neues Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt.  
2.  Wählen Sie im linken Navigationsbereich unter **Vorlagen** die Option **Visual C#** aus.  
3.  Über der Liste verfügbarer Vorlagen, wählen Sie **.NET Framework 4.5.2**.  
4.  Wählen Sie in der Vorlagenliste die Option **Konsolenanwendung** aus. (Alternativ wählen Sie den Projekttyp aus, der aus, der Ihrer Lösung entspricht). Alle Web API C#-Beispiele sind Konsolenanwendungen.  
  
 <!-- TODO:
 ![A new console app project dialog in CDS for Apps](../media/new-project.PNG "A new console app project dialog in CDS for Apps")   -->
  
5.  Geben Sie für das Projekt in den Feldern in der Nähe des unteren Bereichs des Formulars einen Speicherort und einen Namen an, und wählen Sie dann OK aus. (In diesem Thema, wurde der Lösungsname `StartWebAPI-CS` verwendet.) Die Ausgangslösungsdateien wird generiert und die Lösung in Visual Studio geladen.  
  
6.  Öffnen Sie im Menü **Projekt** das Eigenschaftenformular des Projekts und überprüfen Sie, ob das Zielframework auf **.NET Framework 4.5.2** festgelegt ist.  
  
<a name="bkmk_addAllRequiredResources"></a>
   
### <a name="add-all-required-resources-to-your-project"></a>Fügen Sie dem Projekt alle benötigten Ressourcen hinzu  

Die folgenden Schritte zeigen Ihnen, wie dem Projekt alle erforderlichen verwalteten Verweise und Pakete hinzugefügt werden. Betrachten Sie das als einen Basissatz von Ressourcen, der von den meisten Code-Anwendungen mit verwaltetem Code zum Aufrufen von Web-API-Vorgängen benötigt wird.  
  
#### <a name="add-the-helper-library-nuget-package"></a>Hinzufügen des Hilfebibliothek-NuGet-Pakets

Die Common Data Service for Apps-Web-API-Hilfebibliothek enthält Klassen, zur Unterstützung über ergänzende Vorgänge, wie z. b. Anwendungskonfiguration, Common Data Service for Apps-Serverauthentifizierung, Ausnahmebehandlung und die Web-Kommunikation. Weitere Informationen finden Sie unter [Verwenden der "Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  Die Verwendung dieser Klassen ist optional, obwohl sie in den Web-API-Beispielen extensiv verwendet werden.  Die Common Data Service for Apps-Web-API-Hilfebibliothek wird in Quellcodeform als NuGet-Paket verteilt.  Zukünftige Updates werden als NuGet-Paketupdates verteilt.  
  
 Wenn Sie das NuGet-Befehlszeilenprogramm installiert haben oder die Paket-Manager-Konsole in Visual Studio verwenden:  
  
1.  Nutzen Sie den folgenden Befehl, um das Hilfebibliothekspaket zu installieren.  
  
     `Install-Package Microsoft.CrmSdk.WebApi.Samples.HelperCode`  
  
2.  Es werden einige Meldungen zur Verarbeitung von Abhängigkeitspaketen angezeigt. Wenn ein **Lizenz-Abnahme**-Dialogfeld angezeigt wird, lesen Sie die Lizenzbedingungen, und klicken Sie auf **Akzeptieren**.  
  
3.  Springen Sie zu Schritt 6 unten, um die Installation des Hilfebibliothekspakets zu bestätigen.  
  
 Wenn Sie die NuGet-Paket-Manager-Erweiterung installiert haben:  
  
1.  Im Menü **Projekt** wählen Sie die Option **NuGet-Pakete verwalten** aus.  Die Registerkarte **NuGet-Paket-Manager** wird angezeigt.  
  
2.  Klicken Sie in der oberen rechten Ecke legen Sie das Feld **Paket** auf **Nuget.org** fest.  
  
3.  Klicken Sie in der oberen linken Ecke klicken Sie auf **Durchsuchen**, geben Sie dann "`CDS for Apps HelperCode`" im Feld "Suche" ein und drücken Sie die EINGABETASTE.  
  
 <!-- TODO:
![NuGet Package Manager showing Common Data Service for Apps Helper Code Library &#40;C&#35;&#41;](../media/package-manifest-helper-code.png "NuGet Package Manager showing Common Data Service for Apps Helper Code Library (C#)")   -->
  
4.  Klicken Sie auf **Installieren**.  Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.  
  
5.  Das Dialogfeld **Lizenz-Abnahme** wird angezeigt. Lesen und akzeptieren Sie die Lizenzbedingungen, und klicken Sie auf **Ich akzeptiere**.  
  
6.  Navigieren Sie zum Fenster **Lösungs-Explorer**. Stellen Sie sicher, dass ein neuer Lösungsordner namens **Web API Helper Code** hinzugefügt wurde.  
  
 <!-- TODO:
 ![VS Solution Explorer showing helper library files](../media/solution-explorer-helper-code.PNG "VS Solution Explorer showing helper library files")   -->
  
 Das Common Data Service for Apps-SDK Web API Helper Library-Paket, [Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode) hängt von den folgenden weiteren Paketen ab (werden automatisch heruntergeladen und installiert):  
  
-   [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json) – enthält ein [Json.NET](http://www.newtonsoft.com/json), ein beliebtes JSON-Framework für .NET mit MIT-Lizenz.  
  
-   [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) – enthält die Binärdateien für Active Directory Authentication Library ([ADAL](https://msdn.microsoft.com/library/azure/mt417579.aspx)) für Authentifizierungsfunktion für .NET-Clients.  
  
> [!WARNING]
>  Das Common Data Service for Apps-SDK Web API Helper Library-Paket wurde für bestimmte Versionen dieser beiden unterstützenden Pakete erstellt.  Aus diesem Grund sollten Sie nur das Hilfebibliothek.NuGet-Paket direkt aktualisieren.  Dieser Vorgang aktualisiert nach Bedarf die richtigen unterstützenden Pakete.  Wenn Sie eines dieser unterstützenden Pakete separat aktualisieren, ist unter Umständen eine aktuellere Version dieses Pakets mit der Hilfebibliothek nicht kompatibel.  
  
#### <a name="verify-the-required-assembly-references"></a>Prüfen der erforderlichen Assembly-Verweise  
  
1.  Erweitern Sie im **Lösungs-Explorer** den Knoten **Referenzen**.  
  
2.  Bestätigen Sie, das die folgenden Verweise zum Projekt hinzugefügt wurden.  
  
 <!-- TODO:
![VS Solution Explorer showing references for the helper library](../media/solution-explorer-references-helper-code.png "VS Solution Explorer showing references for the helper library")   -->
  
3.  Wenn Sie zusätzliche Funktionalitäten nutzen, die Sie routinemäßig in den Anwendungen verwenden, können Sie die zugeordneten Verweise auf die erforderlichen Assemblys jetzt hinzufügen. Weitere Informationen finden Sie unter [Anleitung: Hinzufügen oder Entfernen von Verweisen über das 'Verweise Hinzufügen-Dialogfeld'.](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).  
  
 Da die Common Data Service for Apps-Web-API auf REST-Prinzipien basiert, benötigt sie keine clientseitigen Assemblys für den Zugriff. 
  
#### <a name="add-typical-using-statements"></a>Hinzufügen typische Using-Anweisungen  
  
1.  Öffnen Sie im **Lösungs-Explorer** die Datei **Program.cs** zum Bearbeiten.  
  
2.  Fügen Sie oben in der Datei können die folgenden `using`-Anweisungen hinzu. Diese Namespaces werden im Allgemeinen in Common Data Service for Apps-Web-API-basierten Lösungen verwendet.  
  
    ```csharp
    using Microsoft.Crm.Sdk.Samples.HelperCode;  
    using Newtonsoft.Json;  
    using Newtonsoft.Json.Linq;  
    using System.Net.Http;  
    using System.Net.Http.Headers;
    ```  
  
3.  Wenn Sie routinemäßig verwendete Assemblys oder Verweise in den vorherigen Abschnitten hinzugefügt haben, sollten Sie die Entsprechenden `using`-Anweisungen für diese Ressourcen hinzufügen.  
  
4.  Speichern Sie die Datei.  
  
<a name="bkmk_addConnectionCode"></a>
 
### <a name="add-connection-code"></a>Verbindungscode hinzufügen

In diesem Abschnitt wird beschrieben, wie eine grundlegende Einstellungen und Anweisungen für diese Vorgänge hinzufügen.  Weitere Informationen zum verwendeten allgemeinen Code finden Sie unter [Verwenden der "Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
#### <a name="edit-the-application-configuration-file"></a>Bearbeiten der Anwendungskonfigurationsdatei
  
1.  Öffnen Sie im **Lösungs-Explorer** die Datei **App.config** zum Bearbeiten.  Fügen Sie die folgenden zwei Abschnitte nach dem vorhandenen `<startup>`-Abschnitt hinzu, und speichern Sie die Datei.  
  
    ```xml  
  
    <connectionStrings>  
        <clear />  
  
        <!-- When providing a password, make sure to set the app.config file's security so that only you can read it. -->  
        <add name="default"   connectionString="Url=http://myserver/myorg/; Username=name; Password=password; Domain=domain" />  
        <add name="CrmOnline" connectionString="Url=https://mydomain.crm.dynamics.com/; Username=someone@mydomain.onmicrosoft.com; Password=password" />  
      </connectionStrings>  
  
      <appSettings>  
        <!--For information on how to register an app and obtain the ClientId and RedirectUrl  
            values see https://msdn.microsoft.com/dynamics/crm/mt149065 -->  
        <!--Active Directory application registration. -->  
        <!--These are dummy values and should be replaced with your actual app registration values.-->  
        <add key="ClientId" value="e5cf0024-a66a-4f16-85ce-99ba97a24bb2" />  
        <add key="RedirectUrl" value="http://localhost/SdkSample" />  
  
        <!-- Use an alternate configuration file for connection string and setting values. This optional setting  
        enables use of an app.config file shared among multiple applications. If the specified file does  
        not exist, this setting is ignored.-->  
        <add key="AlternateConfig" value="C:\Temp\crmsample.exe.config"/>  
      </appSettings>  
  
    ```  
  
2.  Wenn Sie eine Lösung entwickeln oder bereitstellen, müssen die tatsächlichen und Anwendungsregistrierungswerte statt der Beispielsplatzhalterwerte verwendet werden.  Weitere Informationen finden Sie unter: [Hilfecode: Konfigurationsklassen](web-api-helper-code-configuration-classes.md).  
  
<a name="bkmk_addCodeToCallHelperLibrary"></a>

#### <a name="add-code-to-call-the-helper-library"></a>Hinzufügen von Code zum Aufrufen der Hilfebibliothek
  
1.  Bearbeiten Sie die Program.cs-Datei.  
  
2.  Fügen Sie die Folgende Eigenschaft zur Program-Klasse hinzu.  Diese Eigenschaft wird nach einer erfolgreichen Verbindung mit einem Common Data Service for Apps Server initialisiert.  
  
     `private HttpClient httpClient;`  
  
3.  Fügen Sie in der `Main`-Methode die folgenden Anweisungen hinzu.  
  
    ```csharp  
  
    Program app = new Program();  
    try  
    {  
        String[] arguments = Environment.GetCommandLineArgs();  
        app.ConnectToCRM(arguments);  
    }  
    catch (System.Exception ex)  
    { ; }  
    finally  
    {  
        if (app.httpClient != null)  
        { app.httpClient.Dispose(); }  
    }  
  
    ```  
  
4.  Fügen Sie als Nächstes die `ConnectToCRM`-Methode hinzu, die die Hilfebibliothek-Klassen `Configuration` und `Authentication` verwendet.  Der folgende Code zweigt das Zuweisen von Werten zu den [HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient\(v=vs.118\).aspx)-Eigenschaften, damit Sie auf die veröffentlichte Version der Common Data Service for Apps-Web-API zugreifen können.  
  
    ```csharp  
  
    private void ConnectToCRM(String[] cmdargs)  
    {  
        Configuration config = null;  
        if (cmdargs.Length > 0)  
            config = new FileConfiguration(cmdargs[0]);  
        else  
            config = new FileConfiguration(null);  
        Authentication auth = new Authentication(config);  
        httpClient = new HttpClient(auth.ClientHandler, true);  
        httpClient.BaseAddress = new Uri(config.ServiceUrl + "api/data/v8.1/");  
        httpClient.Timeout = new TimeSpan(0, 2, 0);  
        httpClient.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");  
        httpClient.DefaultRequestHeaders.Add("OData-Version", "4.0");  
        httpClient.DefaultRequestHeaders.Accept.Add(  
            new MediaTypeWithQualityHeaderValue("application/json"));  
    }  
  
    ```  
  
<a name="bkmk_addErrorHandlingCode"></a>

### <a name="add-error-handling-code"></a>Fehlerbehandlungscode hinzufügen

 Die folgenden Änderungen fügen Code hinzu, über den Ausnahmen abgefangen und in der Konsole angezeigt werden (inkl. Web-API-Fehler).  Wenn Sie eine andere Umgebung entwickeln, ändern Sie den Ausnahmebehandlungscode entsprechend.  
  
1.  Fügen Sie in `Main` die folgende Anweisung zum `catch`-Block hinzu.  
  
     `DisplayException(ex);`  
  
2.  Fügen Sie die entsprechende Methode zur `Program`-Klasse hinzu.  
  
    ```csharp  
  
    private static void DisplayException(Exception ex)  
    {  
        Console.WriteLine("The application terminated with an error.");  
        Console.WriteLine(ex.Message);  
        while (ex.InnerException != null)  
        {  
            Console.WriteLine("\t* {0}", ex.InnerException.Message);  
            ex = ex.InnerException;  
        }  
    }  
  
    ```  
  
3.  Speichern Sie alle Dateien der Lösung.  
  
<a name="bkmk_nextSteps"></a>

### <a name="next-steps"></a>Nächste Schritte

 An dieser Stelle kann die Lösung ohne Fehler erstellt werden.  Wenn Sie die Anwendungskonfigurationsdatei bearbeiten, um Werte für Common Data Service for Apps bereitzustellen, sollten sich das Programm mit diesem Server verbinden.  Die Lösung stellt einen grundlegenden Rahmen dar, der für benutzerdefinierten Code verwendet werden kann (inkl. Aufrufe der Common Data Service for Apps-Web-API).  
  
> [!TIP]
>  Bevor Sie das Thema verlassen, sollten Sie darüber nachdenken, das Projekt als Projektvorlage zu speichern. Sie können die Vorlage dann wieder für zukünftige Lernprojekte verwenden und sich etwas Zeit und Aufwand bei der Erstellung neue Projekte ersparen. Wählen Sie dazu im Menü **Datei** die Option **Exportvorlage**, aus, während das Projekt in Microsoft Visual Studio geöffnet ist. Befolgen Sie Anweisungen des [Vorlagenexportassistenten](https://msdn.microsoft.com/library/xkh1wxd8.aspx) zum Erstellen der Vorlage.  
  
### <a name="see-also"></a>Siehe auch

[Erste Schritte mit dem Web API (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Verwenden der Common Data Service für Apps-Web-API-Hilfe-Bibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md)<br />  
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)
