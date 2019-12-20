---
title: Tooling-Abruf für das Power Apps component framework | Microsoft Docs
description: Holen Sie sich die Microsoft Power Apps CLI, um Codekomponenten mit dem Power Apps component framework zu erstellen, zu debuggen und bereitzustellen.
keywords: Power Apps Component Framework, Code-Komponenten, Komponentenframework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 4bc237027dab1459c3a9f83c6ff18310f35ff614
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2019
ms.locfileid: "2895012"
---
# <a name="get-tooling-for-power-apps-component-framework"></a>Tooling-Abruf für das Power Apps component framework

Verwenden Sie **Microsoft Power Apps CLI** (Befehlszeilenschnittstelle), um Codekomponenten mit dem Power Apps component framework zu erstellen, zu debuggen und bereitzustellen. Mit der Power Apps CLI können Entwickler Codekomponenten schnell erstellen. Künftig wird es erweitert, um Unterstützung für die weitere Entwicklung und Application Lifecycle Management (ALM)-Umgebungen einzuschließen. 

## <a name="what-is-microsoft-power-apps-cli"></a>Was ist Microsoft Power Apps CLI? 

Die Microsoft Power Apps CLI ist eine einfache, einheitliche Befehlszeilenschnittstelle für Entwickler, mit der Entwickler und App-Ersteller Codekomponenten erstellen können. Die Power Apps CLI-Tools sind der erste Schritt in Richtung einer umfassenden ALM-Story, in der Unternehmensentwickler und ISVs ihre Erweiterungen sowie Anpassungen schnell und effizient erstellen, debuggen und veröffentlichen können.  

## <a name="install-microsoft-power-apps-cli"></a>Installieren der Microsoft Power Apps CLI

Um die Microsoft Power Apps CLI zu erhalten, gehen Sie wie folgt vor:

1. Installieren Sie [Npm](https://www.npmjs.com/get-npm) (wird mit Node.js geliefert) oder [Node.js](https://nodejs.org/en/) (wird mit npm geliefert). Wir empfehlen LTS (Long Term Support) Version 10.15.3 oder höher.

1. Installieren Sie das [.NET Framework 4.6.2-Entwicklerpaket](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Wenn Sie Visual Studio 2017 oder später noch nicht haben, folgen Sie einer der folgenden Optionen:
   - Option 1: Installieren Sie [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) oder später.
   - Option 2: Installieren Sie das [.NET Core 2.2-SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) und dann [Visual Studio Code](https://code.visualstudio.com/Download).

1. Installieren Sie die [Microsoft Power Apps CLI](https://aka.ms/PowerAppsCLI).
1. Um alle aktuellen Funktionen nutzen zu können, aktualisieren Sie die Power Apps CLI-Tools auf die neuste Version mit Hilfe dieses Befehls:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Um Ihre Codekomponente über die CLI Power Apps bereitzustellen, benötigen Sie eine Umgebung Common Data Service mit Systemadministrator- oder System-Customizer-Rechten.
> - Derzeit wird Power Apps CLI nur unter Windows 10 unterstützt.

## <a name="common-commands"></a>Allgemeine Befehle

In dieser Tabelle sind einige allgemeine Befehle aufgeführt, die in der CLI verwendet werden

|Befehl|Beschreibung|Beispiele|
|------|-----------|--------|
|**PCF**|Befehle zum Arbeiten mit Power Apps Component Framework Verfügt über die folgenden Parameter: <br/> - **init**: Initialisiert das Codekomponentenprojekt. <br/> - **namespace**: Namespace der Codekomponente. <br/> - **name**: Name der Codekomponente. <br/> - **template**: Feld oder DataSet <br/> - **push** : Verschiebt die Codekomponente mit den neuesten Änderungen auf die Common Data Service-Instanz.| `pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>` <br/> <br/> `pac pcf push --publisher-prefix <your publisher prefix>`|
|**Lösung**|Befehle zum Arbeiten mit Common Data Service-Projekten. Verfügt über die folgenden Parameter: <br/> - **init**: Initialisiert das Lösungsprojekt.<br/> - **publisher-name**: Name des Herausgebers der Organisation. <br/> - **publisher-prefix**: Präfix des Herausgebers der Organisation. <br/> - **add-reference**: Legt den Referenzpfad zum Komponentenprojektordner fest, indem der `path`-Parameter übergeben wird.<br/> - **Klonen**: Erstellt ein Lösungsprojekt auf der Grundlage des vorhandenen Lösungsprojekts, indem die Parameter `name`, `version` und `include` übergeben werden|`pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>` <br/><br/> `pac solution add-reference --path <path to your Power Apps component framework project>`<br/><br/> `pac solution clone –name<name of the solution to be exported> --version <version of your solution> --include <settings that should be included>`|
|**auth**|Befehle zur Authentifizierung in Common Data Service. Verfügt über die folgenden Parameter: <br/> - **Erstellen**: Erstellt das Authentifizierungsprofil für Ihre Organisation durch Übergeben des `url`-Parameters. Sie müssen die Organisations-URL für den `url`-Parameter bereitstellen. <br/> - **Liste**: Bietet die Liste der Authentifizierungsprofile. <br/> - **Auswählen**: Bietet eine Möglichkeit zum Wechseln zwischen zuvor erstellten Authentifizierungsprofilen durch Übergeben des `index`-Parameters.|`pac auth create --url <your Common Data Service org’s url>` <br/> <br/> `pac auth list` <br/><br/> `Pac auth select --index <index of the active profile>`|
|**Telemetrie**|Telemetrieeinstellungen verwalten. Es hat die folgenden Parameter: aktivieren und deaktivieren.|`pac telemetry enable` <br/><br/> `pac telemetry disable`|
|**org**|Befehl zum Arbeiten mit Common Data Service.|`pac org who`|
|**Plug-In**|Erstellt ein Plug-In-Projekt|`pac plugin init`|

## <a name="uninstall-microsoft-power-apps-cli"></a>Deinstallieren der Microsoft Power Apps CLI

Um das Power Apps CLI-Tooling zu deinstallieren, führen Sie das MSI von [hier](https://aka.ms/PowerAppsCLI) aus. 

Wenn Sie ein Teilnehmer der Privaten Vorschau sind und eine ältere Version der CLI haben, führen Sie diese Schritte aus:

1. Um zu finden, wo Power Apps-CLI installiert ist, öffnen Sie eine Eingabeaufforderung und geben `where pac` ein
1. Löschen Sie den PowerAppsCLI-Ordner.
1. Öffnen Sie das Tool Environment Variables, indem Sie den Befehl `rundll32 sysdm.cpl,EditEnvironmentVariables` in der Eingabeaufforderung ausführen.
1. Klicken Sie zweimal im Abschnitt `User variable for...` auf `Path`.
1. Wählen Sie die Zeile mit dem PowerAppsCLI-Pfad aus, und wählen Sie rechts die Schaltfläche **Löschen** aus.
1. Wählen Sie zweimal **OK** aus.

### <a name="see-also"></a>Siehe auch

[Erstellen Sie Ihre erste Codekomponente](implementing-controls-using-typescript.md)<br/>
