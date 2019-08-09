---
title: 'Schnellstart: Organisationsservicebeispiel (C#) (Common Data Service) | Microsoft Docs'
description: 'Dieser Schnellstart zeigt, wie Sie mit dem Organisationsservice des Common Data Service eine Verbindung herstellen.'
ms.custom: ''
ms.date: 04/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="quick-start-organization-service-sample-c"></a>Schnellstart: Organisationsservicebeispiel (C#)

Hier beginnen Sie Ihre Arbeit mit den .NET-SDK-Assemblys, um mit Daten unter Verwendung von Common Data Service zu arbeiten.

In diesem Schnellstart erstellen Sie eine minimale Konsolenanwendung, um unter Verwendung der Klasse <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> eine Verbindung mit dem Organisationsservice herzustellen. Sie übergeben Ihre Verbindungsdaten mithilfe einer Verbindungszeichenfolge, die dem Konstruktor übergeben wird.

Sie werden den <xref:Microsoft.Xrm.Sdk.IOrganizationService> verwenden.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode zum Übergeben einer Instanz an die Klasse <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest>, und Sie zeigen die <xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse> an.<xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse.UserId> Wert.

> [!NOTE]
> Dieses Schnellstartbeispiel enthält keine Fehlerbehandlung. Dies ist ein minimales Beispiel dafür, was Sie benötigen, um eine Verbindung mit dem Organisationsservice herzustellen und ihn zu verwenden.


## <a name="prerequisites"></a>Voraussetzungen

 - Visual Studio (2017 empfohlen)
 - Internetverbindung
 - Gültiges Benutzerkonto für eine Common Data Service-Instanz
    - Ihr Benutzername
    - Ihr Kennwort
 - URL zur Common Data Service-Umgebung, mit der Sie eine Verbindung herstellen möchten
 - Grundlegendes Verständnis der Visual C#-Sprache

## <a name="create-visual-studio-project"></a>Visual Studio-Projekt erstellen

1. Erstellen eines neuen Konsolen-App (.NET Framework)-Projekts mit .NET Framework 4.6.2

    ![Starten eines Konsolen-App-Projekts](../media/quick-start-org-service-console-app-1.png)

    > [!NOTE]
    > Dieser Screenshot zeigt den Namen `OrgServiceQuickStart` an, aber Sie können für das Projekt und die Lösung einen beliebigen Namen auswählen. 

1. Klicken Sie im **Lösungs-Explorer** mit der rechten Maustaste auf das von Ihnen erstellte Projekt und wählen Sie im Kontextmenü **NuGet-Pakete verwalten...** aus.

    ![NuGet-Paket hinzufügen](../media/quick-start-org-service-console-app-2.png)

1. Navigieren Sie zur neuesten Version des NuGet-Pakets `Microsoft.CrmSdk.XrmTooling.CoreAssembly` und installieren Sie es.

    ![Installieren des NuGet-Pakets Microsoft.CrmSdk.XrmTooling.CoreAssembly](../media/quick-start-org-service-console-app-3.png)

> [!NOTE]
> Sie müssen **Ich stimme zu** im Dialogfeld **Lizenz-Abnahme** auswählen.

## <a name="edit-programcs"></a>Bearbeiten von Program.cs

1. Fügen Sie diese Using-Anweisungen am Anfang von `Program.cs` hinzu

    ```csharp
    using Microsoft.Crm.Sdk.Messages;
    using Microsoft.Xrm.Tooling.Connector;
    ```

1. Ersetzen Sie die `Main`-Methode durch den folgenden Code. Die unterstützten Werte für *AuthType* sind unter [Parameter für Verbindungszeichenfolgen](/dynamics365/customer-engagement/developer/xrm-tooling/use-connection-strings-xrm-tooling-connect#connection-string-parameters) aufgeführt.

    ```csharp
    static void Main(string[] args)
    {            
        // e.g. https://yourorg.crm.dynamics.com
        string url = "<your environment url>";
        // e.g. you@yourorg.onmicrosoft.com
        string userName = "<your user name>";
        // e.g. y0urp455w0rd 
        string password = "<your password>";

        string conn = $@"
        Url = {url};
        AuthType = Office365;
        UserName = {userName};
        Password = {password};
        RequireNewInstance = True";

        using (var svc = new CrmServiceClient(conn))
        {

            WhoAmIRequest request = new WhoAmIRequest();

            WhoAmIResponse response = (WhoAmIResponse)svc.Execute(request);

            Console.WriteLine("Your UserId is {0}", response.UserId);

            Console.WriteLine("Press any key to exit.");
            Console.ReadLine();
        }
    }
    ```

1. Bearbeiten Sie die folgenden Werte, um Informationen für die Umgebung hinzuzufügen. Ihre Umgebungs-URL finden Sie in der Webanwendung unter **Einstellungen > Anpassung > Entwicklerressourcen**.

    ```csharp
    // e.g. https://yourorg.crm.dynamics.com
    string url = "<your environment url>";
    // e.g. you@yourorg.onmicrosoft.com
    string userName = "<your user name>";
    // e.g. y0urp455w0rd
    string password = "<your password>";
    ```

## <a name="run-the-program"></a>Ausführen des Programms

1. Drücken Sie F5, um das Programm auszuführen. Die Ausgabe sollte wie folgt aussehen:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

### <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich eine Verbindung mit dem Organisationsservice hergestellt.


## <a name="next-steps"></a>Nächste Schritte

Diese Themen erklären mehr über das Arbeiten mit Common Data Service-Entitäten:

[Entitäts-Vorgänge mithilfe des Organisationsservice](entity-operations.md)<br />
[Erstellen von Entitäten mit dem Organisationsservice](entity-operations-create.md)<br />
[Abrufen einer Entität mithilfe des Organisationsdienstes](entity-operations-retrieve.md)<br />
[Aktualisieren und Löschen von Entitäten mit dem Organisationsservice](entity-operations-update-delete.md)<br />
[Entitäten mithilfe des Organisations-Service zuordnen oder trennen](entity-operations-associate-disassociate.md)