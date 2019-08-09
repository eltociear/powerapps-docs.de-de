---
title: Erhalten von Tools für das PowerApps component framework | MicrosoftDocs
description: 'Rufen Sie die Microsoft PowerApps CLI ab, um benutzerdefinierte Komponenten mithilfe des PowerApps component framework zu erstellen, zu debuggen und bereitzustellen.'
keywords: 'PowerApps-Komponentframework-Tooling, Benutzerdefinierte Komponenten, Komponentenframework'
ms.author: nabuthuk
manager: kvivek
ms.date: 06/18/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
---

# <a name="get-tooling-for-powerapps-component-framework"></a>Erhalten von Tools für das PowerApps component framework

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Verwenden Sie die **Microsoft PowerApps CLI** (Command Line Interface), um benutzerdefinierte Komponenten mithilfe des PowerApps component framework zu erstellen, zu debuggen und bereitzustellen. Die PowerApps CLI ermöglicht es Entwicklern, schnell PowerApps component framework-Komponenten zu erstellen und wird in Zukunft erweitert, um Unterstützung für weitere Entwicklungs- und Application Lifecycle Management (ALM)-Erfahrungen zu umfassen. 

## <a name="what-is-microsoft-powerapps-cli"></a>Was ist die Microsoft PowerApps CLI? 

Die Microsoft PowerApps CLI ist eine einfache Befehlszeilenschnittstelle für Entwickler, mit der Sie benutzerdefinierte Komponenten erstellen können. PowerApps CLI ist außerdem der erste Schritt in Richtung einer umfassenden ALM-Story, in der Unternehmensentwickler und ISVs ihre PowerApps und Dynamics 365 for Customer Engagement-App-Erweiterungen sowie Anpassungen schnell und effizient erstellen, debuggen und veröffentlichen können.  

> [!IMPORTANT]
> - Microsoft PowerApps CLI-Tools sind eine Vorversion und können sich von der kommerziell veröffentlichten Version unterscheiden.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 
> - Wenn Sie uns Feedback zur Software an Microsoft geben, erteilen Sie Microsoft, ohne Erhebung einer Gebührt, das Recht, Ihr Feedback in jeder Form und für jeden Zweck zu verwenden, zu teilen und kommerziell zu nutzen. 
> - Microsoft bietet keinen Support für diese Vorschaufunktion. Der technische Support von Microsoft kann Ihnen bei Problemen und Fragen nicht helfen.

## <a name="install-microsoft-powerapps-cli"></a>Installieren der Microsoft PowerApps CLI

So können Sie die Microsoft PowerApps CLI verwenden:

1. Installieren Sie [Npm](https://www.npmjs.com/get-npm)(wird mit Node.js geliefert) oder installieren Sie [Node.js](https://nodejs.org/en/) (wird mit npm geliefert). Wir empfehlen LTS (Long Term Support) Version 10.15.3 LTS, da es am stabilsten zu sein scheint.

1. Installieren Sie das [.NET Framework 4.6.2-Entwicklerpaket](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Wenn Sie Visual Studio 2017 oder später noch nicht haben, folgen Sie einer der folgenden Optionen:
   - Option 1: Installieren Sie [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) oder später.
   - Option 2: Installieren Sie das [.NET Core 2.2-SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) und dann [Visual Studio Code](https://code.visualstudio.com/Download).

1. Installieren Sie die [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI).



> [!NOTE]
> - Zur Bereitstellung Ihrer benutzerdefinierten Komponente mithilfe der PowerApps CLI müssen Sie eine Common Data Service-Umgebung mit Systemadministrator- oder Systemanpasserrechten haben.
> - Derzeit wird die PowerApps CLI nur auf Windows 10 unterstützt.

## <a name="update-microsoft-powerapps-cli-to-the-latest-version"></a>Aktualisieren der Microsoft PowerApps CLI auf die neuste Version

Um Ihre Microsoft PowerApps CLI auf die neueste Version zu aktualisieren und von den gesamten neuen Funktionen zu profitieren, führen Sie den folgenden Befehl in der Entwicklereingabeaufforderung für VS 2017 aus:

```CLI
pac install latest
```

### <a name="what-else-do-i-need-to-know"></a>Was muss ich sonst noch wissen?

Wenn Sie bereits ein Lösungs- oder PowerApps component framework-Projekt erstellt haben, stellen Sie sicher, dass Sie diese Projekte auf die neuesten Pakete aktualisieren. Hierdurch können Sie neu hinzugefügte Funktionen bei Ihren vorhandenen Projekten nutzen. Neu erstellte Projekte enthalten diese Einstellungen bereits.

- Aktualisieren Sie das Versionstag in `pcfproj`, das sich innerhalb Ihres PowerApps component framework-Projektordners befindet:

   ```XML
   <PackageReference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="0.*"/>
   ```
- Aktualisieren Sie das Versionstag in `cdsproj`, das sich innerhalb Ihres Lösungsprojektordners befindet:

   ```XML
   <PackageReference Include="Microsoft.PowerApps.MSBuild.Solution" Version="0.*"/>
   ```

    > [!NOTE] 
    > Nachdem Sie die oben beschriebenen Änderungen vorgenommen haben, führen Sie den Befehl `msbuild /t:restore` aus, um Ihr Projekt auf die korrekte Version zu aktualisieren.


- Aktualisieren Sie das Versionstag in Ihrer `package.json`-Datei, die sich innerhalb Ihres PowerApps component framework-Projektordners befindet:

  ```JSON
  "devDependencies":{
   "pcf-scripts": "^0",
   "pcf-start": "^0"
    }
  ```
   > [!NOTE]
   > Nachdem Sie die oben genannten Änderungen vorgenommen haben, wird bei Verwendung von „npm update” in der Eingabeaufforderung Ihr Projekt immer auf die korrekte Version aktualisiert.

## <a name="microsoft-powerapps-cli-telemetry"></a>Microsoft PowerApps CLI-Telemetrie

Das Funktionsteam aggregiert anonymisierte Telemetrie, um zu verstehen, welche Funktionen im PowerApps-CLI am häufigsten von den Entwicklern verwendet werden. Die aggregierten Daten ermöglichen es uns, dem Kunden die beste Erfahrung zu bieten, indem wir uns auf das wirklich Wichtige konzentrieren.

> [!NOTE]
> Um die Telemetrie zu deaktivieren, führe Sie den Befehl `pac telemetry --enable false` aus. Um die Telemetrie wieder einzuschalten, verwenden Sie den Befehl `pac telemetry --enable true`.

## <a name="uninstall-microsoft-powerapps-cli"></a>Deinstallieren der Microsoft PowerApps CLI

Um das PowerApps CLI-Tool zu deinstallieren, führen Sie MSI von [hier](https://aka.ms/PowerAppsCLI) aus. 

Wenn Sie ein privater Vorschauteilnehmer sind und eine ältere Version der CLI haben, führen Sie diese Schritte aus:

1. Um zu finden, wo PowerApps-CLI installiert ist, öffnen Sie eine Eingabeaufforderung und geben `where pac` ein
1. Löschen Sie den PowerAppsCLI-Ordner.
1. Öffnen Sie das Tool Environment Variables, indem Sie den Befehl `rundll32 sysdm.cpl,EditEnvironmentVariables` in der Eingabeaufforderung ausführen.
1. Klicken Sie zweimal im Abschnitt `User variable for...` auf `Path`.
1. Wählen Sie die Zeile mit dem PowerAppsCLI-Pfad aus, und klicken Sie rechts auf die Schaltfläche "Löschen".
1. Klicken Sie zwei Mal auf **OK**.

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten in TypeScript](implementing-controls-using-typescript.md)<br/>

