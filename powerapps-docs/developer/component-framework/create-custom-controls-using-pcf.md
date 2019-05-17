---
title: Erstellen einer benutzerdefinierten Komponente mit PowerApp-Komponentenframework-Tooling| Microsoft Docs
description: Starten der Erstellung einer Komponente mit PowerApps-Komponentenframework-Tooling
keywords: 'PowerApps-Komponentframework-Tooling, Benutzerdefinierte Komponenten, Komponentenframework'
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---

# <a name="create-debug-and-deploy-a-component-using--microsoft-powerapps-cli"></a>Erstellen, Debuggen und Bereitstellen einer Komponente mit der Microsoft PowerApps-CLI

Verwenden Sie die PowerApps-Befehlszeilenschnittstelle (Command Line Interface - CLI), um benutzerdefinierte PowerApps-Komponentenframework-Komponenten zu erstellen, debuggen und bereitzustellen. Die PowerApps-CLI ermöglicht es Entwicklern, schnell PowerAppskomponentenframework-Komponenten zu erstellen und wird in Zukunft erweitert, um Unterstützung für weitere Entwicklungs- und Application Lifecycle Management (ALM)-Erfahrungen zu umfassen. 

## <a name="what-is-microsoft-powerapps-cli"></a>Was ist Microsoft PowerApps-CLI 

Microsoft PowerApps-CLI ist eine einfache Befehlszeilenschnittstelle für Entwickler, mit der Sie benutzerdefinierte Komponenten erstellen können. PowerApps CLI ist außerdem der erste Schritt in Richtung einer umfassenden ALM-Story, in der Unternehmensentwickler und ISVs ihre PowerApps und Dynamics 365 for Customer Engagement-App-Erweiterungen sowie Anpassungen schnell und effizient erstellen, debuggen und veröffentlichen können.  

## <a name="prerequisites-to-use-powerapps-cli"></a>Voraussetzungen zur Verwendung der PowerApps-CLI

Zur Verwendung der PowerApps-CLI benötigen Sie Folgendes:

- Installieren Sie [Npm](https://www.npmjs.com/get-npm)(wird mit Node.js geliefert) oder installieren Sie [Node.js](https://nodejs.org/en/) (wird mit npm geliefert). Wir empfehlen LTS (Long Term Support) Version 10.15.3 LTS, da es am stabilsten zu sein scheint.
- Wenn Sie Visual Studio 2017 oder später noch nicht haben, folgen Sie einer der folgenden Optionen:
   - Option 1: Installieren von Visual Studio 2017 oder später
   - Option 2: Installieren von .NET Core 2.2 SDK und Installieren von Visual Studio Code
- Installieren Sie Microsoft PowerApps-CLI von [hier](http://download.microsoft.com/download/D/B/E/DBE69906-B4DA-471C-8960-092AB955C681/powerapps-cli-0.1.51.msi)

> [!IMPORTANT]
> - Microsoft PowerApps-CLI-Tools sind eine Vorversion und können sich von der kommerziell veröffentlichten Version unterscheiden.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 
> - Wenn Sie uns Feedback zur Software an Microsoft geben, erteilen Sie Microsoft, ohne Erhebung einer Gebührt, das Recht, Ihr Feedback in jeder Form und für jeden Zweck zu verwenden, zu teilen und kommerziell zu nutzen. 
> - Microsoft bietet keinen Support für diese Vorschaufunktion. Der technische Support von Microsoft kann Ihnen bei Problemen und Fragen nicht helfen.

> [!NOTE]
> Zur Bereitstellung Ihrer benutzerdefinierten Komponente benötige Sie die Common Data Service-Umgebung mit Systemadministrator- oder Systemanpasserrechten.

> [!NOTE]
> Derzeit wird PowerApps-CLI nur auf Windows 10 unterstützt.

## <a name="creating-a-new-powerapps-component-framework-component"></a>Erstellen einer neuen PowerApps-Komponentenframework-Komponente

Für den Anfang öffnen Sie eine neue Entwicklereingabeaufforderung für VS 2017 nach der Installation von PowerApps-CLI.

1. In der Entwicklereingabeaufforderung für VS 2017 erstellen Sie einen neuen Ordner auf Ihrer lokalen Festplatte, z. B. `C:\Users\<your name>\Documents\My_PCF_Control`
2. Wechseln Sie mit dem Befehl `cd <specify your new folder path>` zum neu erstellen Ordner.
3. Führen Sie den folgenden Befehl aus, um ein neues Komponentenprojekt zu erstellen, indem Sie einige Basisparameter übergeben `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Heute bieten wir zwei Arten von Komponenten **Feld** und **Dataset**.

4. Um alle erforderlichen Projektabhängigkeiten abzurufen, führen Sie den Befehl `npm install` aus.
5. Öffnen Sie Ihren Projektordner (`C:\Users\<your name>\Documents\My_PCF_Control\<component name>`) in einer Entwicklerumgebung Ihrer Wahl und beginnen Sie mit der Entwicklung Ihrer benutzerdefinierten Komponente. Wenn Sie einer schrittweisen Anleitung folgen möchten, scrollen Sie nach unten, um zu sehen, wie eine einfache lineare Komponente implementiert wird.

## <a name="building-your-components"></a>Erstellen Ihrer Komponenten

Um Ihre Komponente zu erstellen, können Sie den Ordner in Visual Studio Code öffnen und den (Strg-Umschalt-B) Befehl verwenden. Dan wählen Sie Ihre Build-Optionen aus. Alternativ können Sie Ihr Steuerelement schnell mit dem `npm run build`-Befehl in Ihrem Entwicklereingabeaufforderung für VS 2017-Fenster erstellen.

## <a name="debugging-your-powerapps-component-framework-component"></a>Debuggen Ihrer PowerApps-Komponentenframework-Komponente

Sobald Sie Ihre benutzerdefinierte Komponentenlogik implementiert haben, führen Sie den folgenden Befehl aus, um den Debugging-Prozess zu starten `npm start`

> [!NOTE]
> Heute können Sie Ihre Feldkomponente nur visualisieren, aber bald ist Dataset-Unterstützung verfügbar. Die folgende Abbildung zeigt eine Beispielkomponente, die im folgenden Einstieg implementiert wird, nur als ein Beispiel. 

> [!div class="mx-imgBorder"]
> ![lokaler-Host](media/local-host.png "lokaler Host")

Wie in der obigen Abbildung gezeigt, wird das Durchsuchen-Fenster in 3 Abschnitten geöffnet. Ihre Komponente wird im linken Bereich gerendert. Der rechte Bereich besteht aus **Eingabe**- und **Ausgabe**-Abschnitten

  - Der **Eingabe**-Bereich ist eine interaktive Benutzeroberfläche, in der alle Eigenschaften und ihre im Manifest definierten Typen/Typ-Gruppen angezeigt werden. Damit können Sie Pseudodaten für jede Eigenschaft eingeben. 
  - Der **Ausgabe**-Bereich rendert die Ausgabe, wenn die `getOutputs`-Methode einer Komponente aufgerufen wird.  
 
> [!NOTE]
> Wenn Sie `manifest.xml` ändern oder weitere Eigenschaften erstellen möchten, müssen Sie den Debugging-Prozess erneut starten, bevor sie im Eingabebereich angezeigt werden.

Da Sie Pseudodaten eingeben, können Sie die Debugging-Funktionen Ihres Browsers verwenden, um das Komponentenverhalten zu beobachten. Jeder Browser bietet ein Debugging-Tool, das Ihnen hilft, Ihren Code systemeigen im Browser zu debuggen. In der Regel können Sie das Debugging in Ihrem Browser aktivieren, indem Sie die Taste **F12** drücken, um das systemeigene Entwicklungstool anzuzeigen,d as für das Debugging verwendet wird. Heute werden Chrome und Edge Browser unterstützt.

Beispiel: Bei **Microsoft Edge**

- Drücken Sie **F12**, um den Inspector zu öffnen.
- Klicken Sie auf Ihre Komponente
- In der oberen Leiste wechseln Sie zu **Debugger** und starten dann in der Suchleiste eine Suche nach dem in der Manifestdatei beschriebenen Komponentennamen. Geben Sie z. B. Ihren Komponentennamen als `Hello World component` ein.

     > [!div class="mx-imgBorder"]
     > ![debug-component](media/debug-control.png "Komponente debuggen")

> [!NOTE]
> Es ist immer eine gute Praxis, Haltepunkte in Lebenszyklusmethoden der Komponente festzulegen, z. B. `init` und `updateView`

Sie können mit der Komponente auch lokal in Echtzeit interagieren und Elemente in DOM beobachten, indem Sie wie folgt einen Haltepunkt in der Registerkarte "Quellen" festlegen:

> [!div class="mx-imgBorder"]
> ![local-host](media/local-host.png "lokaler Host")

> [!div class="mx-imgBorder"]
> ![debug-component](media/debug-control-1.png "Komponente 1 debuggen")


 > [!NOTE]
 > Sie können auch folgende Schritte durchführen, um äußeres Schleifendebugging mit Fiddler durchzuführen.
 >    1. Installieren Sie [Fiddler](https://www.telerik.com/download/fiddler)
 >    2. Führen Sie die Schritte aus, um [AutoResponder](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder) zu konfigurieren

## <a name="deploying-your-powerapps-component-framework-components"></a>Bereitstellen Ihrer PowerApps-Komponentenframework-Komponenten

Sobald Sie das Debugging und die Entwicklung abgeschlossen ist, bleibt noch ein Schritt übrig - die Bereitstellung Ihrer neuen Komponente.  

Führen Sie die folgenden Schritte aus um eine [Lösungs](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/solutions-overview)-Datei zu erstellen und zu importieren.

1. Erstellen Sie ein neues Verzeichnis und wechseln Sie dorthin 'cd <new directory name>'
2. Erstellen Sie ein neues Lösungsprojekt im Verzeichnis Ihrer Wahl, indem Sie den Befehl `pac solution init --publisherName <enter your publisher name> --customizationPrefix <enter your publisher name>` nach `cd <your new folder>` verwenden.

   > [!NOTE]
   > Die Werte für [publisherName](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/reference/entities/publisher) und [cutomizationPrefix](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/change-solution-publisher-prefix) müssen in Ihrer Umgebung eindeutig sein.
 
3. Sobald das neue Lösungsprojekt erstellt ist, müssen Sie den Speicherort verweisen, an dem sich die erstellte Komponente befindet. Sie können den Verweis mit dem Befehl `pac solution add-reference --path <path or relative path of your PowerApps component framework project on disk>` hinzufügen.
4. Um eine Zip-Datei aus Ihrem Lösungsprojekt zu erstellen, müssen Sie mit `cd` in das Verzeichnis Ihres Lösungsprojekts wechseln und das Projekt mit dem Befehl `msbuild /t:restore` dann `msbuild` erstellen.

    > [!NOTE]
    > Wenn msbuild 15 nicht der Pfad ist, öffnen Sie die Entwicklereingabeaufforderung für VS 2017, um den Befehl `msbuild` auszuführen.

    > [!NOTE]
    > Das Erstellen der Lösung in der Debugging-Konfiguration generiert ein nicht verwaltetes Lösungspaket. Ein verwaltetes Lösungspaket wird erstellt, indem Sie die Lösung in der Versionskonfiguration erstellen. Diese Einstellungen können außer Kraft gesetzt werden, indem die SolutionPackageType-Eigenschaft in der `cdsproj`-Datei angegeben wird.
    
    > [!NOTE]
    > Wenn Ihr Projekt-Build eine verwaltete Lösung ergeben soll, oder sowohl eine verwaltete als auch eine nicht verwaltete, öffnen Sie den Ordner, in dem Sie Ihr Lösungsprojekt erstellt haben, bearbeiten Sie die `cdsproj`-Datei und löschen Sie die Kommentierung der folgenden Eigenschaftengruppe:
      ```XML
         <PropertyGroup>
          <SolutionPackageType>Managed</SolutionPackageType>
           </PropertyGroup>
      ```

    > [!NOTE]
    > Sie können auch zusätzliche [Funktionen](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/compress-extract-solution-file-solutionpackager) für die Lösungsverpackung aktivieren, indem Sie beliebige der folgenden Eigenschaftsgruppenelemente hinzufügen:

     ```XML
       <PropertyGroup>
         <SolutionPackageErrorLevel />
         <SolutionPackageEnableLocalization />
        <SolutionPackagerWorkingDirectory />
        <SolutionPackageLogFilePath />
        <SolutionPackageZipFilePath />
        <SolutionPackageMapFilePath />
       </PropertyGroup>
     ```

5. Die erstelle Lösungs-Zip-Datei befindet sich in `\bin\debug\`.
6. Sie sollten mit dem Webportal einen manuellen [Import der Lösung](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-export-solutions) durchführen, sobald die Zip-Datei bereit ist.

## <a name="adding-custom-controls-to-entity-or-a-field"></a>Hinzufügen benutzerdefinierter Steuerelemente zu einer Entität oder einem Feld

Um eine benutzerdefinierte Komponente wie die Daten-Satz-Komponente oder eine einfach Tabellenkomponente zu einem Raster oder einer Ansicht hinzuzufügen, führen Sie die im Thema [Hinzufügen von Steuerelemente zu Feldern und Entitäten](add-custom-controls-to-a-field-or-entity.md)erwähnten Schritte aus. 

## <a name="telemetry"></a>Telemetrie

Das Funktionsteam aggregiert anonymisierte Telemetrie, um zu verstehen, welche Funktionen im PowerApps-CLI am häufigsten von den Entwicklern verwendet werden. Die aggregierten Daten ermöglichen es uns, dem Kunden die beste Erfahrung zu bieten, indem wir uns auf das wirklich Wichtige konzentrieren.

> [!NOTE]
> Um die Telemetrie zu deaktivieren, führe Sie den Befehl `pac telemetry --enable false` aus. Um die Telemetrie wieder einzuschalten, verwenden Sie den Befehl `pac telemetry --enable true`.

## <a name="how-to-uninstall-microsoft-powerapps-cli"></a>So deinstallieren Sie Microsoft PowerApps-CLI

Um das CLI-Tool zu deinstallieren, führen Sie MSI von [hier](http://download.microsoft.com/download/D/B/E/DBE69906-B4DA-471C-8960-092AB955C681/powerapps-cli-0.1.51.msi) aus. Wenn Sie ein privater Vorschauteilnehmer sind und eine ältere Version der CLI haben, führen Sie die folgenden Schritte manuell aus:

1. Um zu finden, wo PowerApps-CLI installiert ist, öffnen Sie eine Eingabeaufforderung und geben `where pac` ein
1. Löschen Sie den PowerAppsCLI-Ordner.
1. Öffnen Sie das Tool Environment Variables, indem Sie den Befehl `rundll32 sysdm.cpl,EditEnvironmentVariables` in der Eingabeaufforderung ausführen.
1. Klicken Sie zweimal im Abschnitt `User variable for...` auf `Path`.
1. Wählen Sie die Zeile mit dem PowerAppsCLI-Pfad aus, und klicken Sie rechts auf die Schaltfläche "Löschen".
1. Klicken Sie zwei Mal auf "OK".

## <a name="known-configuration-issues-and-workarounds"></a>Bekannte Konfigurationsprobleme und Behebungen

**Msbuild-Fehler MSB4036:**

1. Der Name der Aufgabe in der Projektdatei gleicht dem Namen der Aufgabenklasse.
2. Die Aufgabenklasse ist öffentlich und implementiert die Microsoft.Build.Framework.ITask-Schnittstelle.
3. Die Aufgabe ist mit <UsingTask> korrekt in der Projektdatei in den *.tasks-Dateien im Verzeichnis <path> deklariert.

**Lösung:**

1. Öffnen Sie das Visual Studio-Installationsprogramm 
1. Für VS 2017 klicken Sie auf ändern. 
1. Klicken Sie auf "Einzelne Komponenten"
1. Überprüfen Sie unter Code-Tools die Option **NuGet-Ziele und Build-Aufgaben**

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten in TypeScript](implementing-controls-using-typescript.md)<br/>
[Aktualisieren vorhandener Komponenten in ein neues Tools-Format](updating-existing-controls.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
