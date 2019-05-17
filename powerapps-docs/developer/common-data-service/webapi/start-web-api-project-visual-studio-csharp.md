---
title: 'Starten eines Dynamics 365 for Customer Engagement-Web-API-Projekts in Visual Studio (C#) (Common Data Service) | MicrosoftDocs'
description: 'Erstellen Sie ein neues Projekt in Visual Studio, um eine Konsolenanwendung zu unterstützen, die Common Data Service-Web-API verwendet'
ms.custom: null
ms.date: 04/22/2019
ms.reviewer: null
ms.service: powerapps
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: get-started-article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
ms.assetid: F96B384D-EF70-490D-BE3D-2E3883278B99
caps.latest.revision: 14
author: JimDaly
ms.author: jdaly
manager: annbe
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="start-a-common-data-service-web-api-project-in-visual-studio-c"></a>Ein Common Data Service-Web-API-Projekt in Visual Studio (C#) starten

Dieses Thema zeigt, wie Sie ein neues Projekt in Visual Studio 2017 erstellt, das eine Konsolenanwendung erstellt, die die Common Data Service-Web-API verwendet. Es zeigt die allgemeinen Verweise werden Projektressourcen, die die meisten Anwendungen, einschließlich den SDK-C#-Beispielen, verwenden, um Web-API-basierte Lösungen zu implementieren.  
  
<a name="bkmk_prerequisites"></a>   
## <a name="prerequisites"></a>Voraussetzungen  
 Die folgenden Voraussetzungen sind zur Erstellung der Konsolenanwendung in diesem Abschnitt erforderlich.  
  
- Visual Studio 2017, das auf dem Entwicklungscomputer installiert ist. Jede Edition, inkl. [Visual Studio Express](https://www.visualstudio.com/products/visual-studio-express-vs.aspx), sollte ausreichend sein, um mit der Common Data Service-Web-API zu arbeiten.
  
- Ein NuGet-Client muss installiert sein. Entweder mit dem Befehlszeilenprogramm oder der Visual Studio-Erweiterung. Weitere Informationen finden Sie unter [Installieren von NuGet](https://docs.nuget.org/consume/installing-nuget).  
  
<a name="bkmk_createProject"></a>   

## <a name="create-a-project"></a>Erstellen eines Projekts  
Im folgenden Verfahren wird veranschaulicht, wie ein Konsolenanwendungsprojekt in C# erstellt wird, die Microsoft .NET Framework verwendet.
  
<a name="bkmk_newProject"></a> 

### <a name="new-project"></a>Neues Projekt  
  
1. Klicken Sie in Visual Studio auf **Neues Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2. Wählen Sie im linken Navigationsbereich unter **Vorlagen** die Option **Visual C#** aus.  
  
3. Über der Liste verfügbarer Vorlagen, wählen Sie **.NET Framework 4.6.2**.  
  
4. Wählen Sie aus der Vorlagenliste **Konsolen-App (.NET Framework)** aus. (Alternativ wählen Sie den Projekttyp aus, der aus, der Ihrer Lösung entspricht). Alle Web API C#-Beispiele sind Konsolenanwendungen.  
  
   ![Dialog für ein neues Konsolen-App-Projekt in Common Data Service](media/new-project.PNG "Dialog für ein neues Konsolen-App-Projekt in Common Data Service")  
  
5. Geben Sie für das Projekt in den Feldern in der Nähe des unteren Bereichs des Formulars einen Speicherort und einen Namen an, und wählen Sie dann OK aus. (In diesem Thema, wurde der Lösungsname “StartWebAPI-CS” verwendet.) Die Ausgangslösungsdateien wird generiert und die Lösung in Visual Studio geladen.  
  
6. Öffnen Sie im Menü **Projekt** das Eigenschaftenformular des Projekts und überprüfen Sie, ob das Zielframework auf **.NET Framework 4.6.2** festgelegt ist.  
  
#### <a name="install-and-verify-the-required-assembly-references"></a>Installieren und prüfen der erforderlichen Assembly-Verweise  

1. Nachdem das Projekt geöffnet wird, klicken Sie auf **Extras** in der Steuerleiste oben in Ihrem Projekt. Wählen Sie **NuGet-Paket-Manager** > **Paket-Manager-Konsole** aus und installieren Sie die folgenden NuGet-Pakete.

```
install-package Newtonsoft.Json
install-package System.Net.Http
```
2. Erweitern Sie im **Lösungs-Explorer** den Knoten **Referenzen**.  
  
3. Bestätigen Sie, dass alle erforderlichen Verweise zum Projekt hinzugefügt wurden.  
  
4. Wenn Sie zusätzliche Funktionalitäten nutzen, die Sie routinemäßig in den Anwendungen verwenden, können Sie die zugeordneten Verweise auf die erforderlichen Assemblys jetzt hinzufügen. Weitere Informationen finden Sie unter [Anleitung: Hinzufügen oder Entfernen von Verweisen über das 'Verweise Hinzufügen-Dialogfeld'.](https://msdn.microsoft.com/library/wkze6zky.aspx).  
  
   Da die Common Data Service-Web-API auf REST-Prinzipien basiert, benötigt sie keine clientseitigen Assemblys für den Zugriff.  Allerdings werden diese von andere APIs, die von Common Data Service-Apps unterstützt werden, benötigt.
  
#### <a name="add-typical-using-statements"></a>Hinzufügen typische Using-Anweisungen  
  
1.  Öffnen Sie im **Lösungs-Explorer** die Datei **Program.cs** zum Bearbeiten.  
  
2.  Fügen Sie oben in der Datei können die folgenden `using`-Anweisungen hinzu. Diese Namespaces werden im Allgemeinen in Dynamics 365 for Customer Engagement-Web-API-basierten Lösungen verwendet.  
  
    ```csharp
    using Newtonsoft.Json;  
    using Newtonsoft.Json.Linq;  
    using System.Net.Http;  
    using System.Net.Http.Headers;
    ```  
  
3.  Wenn Sie routinemäßig verwendete Assemblys oder Verweise in den vorherigen Abschnitten hinzugefügt haben, sollten Sie die Entsprechenden `using`-Anweisungen für diese Ressourcen hinzufügen.  
  
4.  Speichern Sie die Datei.  
  
<a name="bkmk_addConnectionCode"></a>
 
### <a name="add-connection-code"></a>Verbindungscode hinzufügen

In diesem Abschnitt wird beschrieben, wie eine grundlegende Einstellungen und Anweisungen für diese Vorgänge hinzufügen.  
  
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
  
2.  Wenn Sie eine Lösung entwickeln oder bereitstellen, müssen die tatsächlichen und Anwendungsregistrierungswerte statt der Beispielsplatzhalterwerte verwendet werden.  
  
### <a name="next-steps"></a>Nächste Schritte

 An dieser Stelle kann die Lösung ohne Fehler erstellt werden. Wenn Sie die Anwendungskonfigurationsdatei bearbeiten, um Werte für Dynamics 365 Server bereitzustellen, sollten sich das Programm mit diesem Server verbinden. Die Lösung stellt einen grundlegenden Rahmen dar, der für benutzerdefinierten Code verwendet werden kann (inkl. Aufrufe der Common Data Service-Web-API).  
  
> [!TIP]
>  Bevor Sie das Thema verlassen, sollten Sie darüber nachdenken, das Projekt als Projektvorlage zu speichern. Sie können die Vorlage dann wieder für zukünftige Lernprojekte verwenden und sich etwas Zeit und Aufwand bei der Erstellung neue Projekte ersparen. Wählen Sie dazu im Menü **Datei** die Option **Exportvorlage**, aus, während das Projekt in Microsoft Visual Studio geöffnet ist. Befolgen Sie Anweisungen des [Vorlagenexportassistenten](https://msdn.microsoft.com/library/xkh1wxd8.aspx) zum Erstellen der Vorlage.  
  
### <a name="see-also"></a>Siehe auch

 [Erste Schritte mit dem Web API (C#)](get-started-dynamics-365-web-api-csharp.md)   
 [Verwenden Sie das Dynamics 365 for Customer Engagement Web API Hilfe-Bibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md)   
 [Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)