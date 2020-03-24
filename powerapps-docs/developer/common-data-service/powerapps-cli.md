---
title: Power Apps CLI installieren | Microsoft Docs
description: Holen Sie sich die Microsoft Power Apps CLI, um Codekomponenten mit dem Power Apps component framework zu erstellen, zu debuggen und bereitzustellen.
keywords: Power Apps CLI, Code-Komponenten, component framework, CLI
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 01/28/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 0c42aa69edfea9ac9c5382e6569896f51889e6d0
ms.sourcegitcommit: 4728372a4a467f65bab9ae17e91738f420e17374
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "3029989"
---
# <a name="what-is-microsoft-power-apps-cli"></a>Was ist die Microsoft Power Apps CLI? 

Die Microsoft Power Apps CLI ist eine einfache Befehlszeilenschnittstelle für Entwickler, die es Entwicklern und Anwendungsherstellern ermöglicht, Codekomponenten zu erstellen. 

Power Apps CLI-Tooling ist der erste Schritt zu einem umfassenden Application Life Cycle Management (ALM), bei dem Unternehmensentwickler und ISVs ihre Erweiterungen und Anpassungen schnell und effizient erstellen, bauen, debuggen und veröffentlichen können.  

## <a name="install-power-apps-cli"></a>Installieren der Power Apps CLI

Um die Power Apps CLI zu erhalten, gehen Sie wie folgt vor:

1. Installieren Sie [Npm](https://www.npmjs.com/get-npm) (wird mit Node.js geliefert) oder [Node.js](https://nodejs.org/en/) (wird mit npm geliefert). Wir empfehlen LTS (Long Term Support) Version 10.15.3 oder höher.

1. Installieren Sie das [.NET Framework 4.6.2-Entwicklerpaket](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Wenn Sie Visual Studio 2017 oder später noch nicht haben, folgen Sie einer der folgenden Optionen:
   - Option 1: Installieren Sie [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) oder später.
   - Option 2: Installieren Sie das [.NET Core 3.1-SDK](https://dotnet.microsoft.com/download/dotnet-core/current) und dann [Visual Studio Code](https://code.visualstudio.com/Download).

1. Installieren Sie die [Power Apps CLI](https://aka.ms/PowerAppsCLI).

1. Um alle aktuellen Funktionen nutzen zu können, aktualisieren Sie die Power Apps CLI-Tools auf die neuste Version mit Hilfe dieses Befehls:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> Derzeit wird Power Apps CLI nur unter Windows 10 unterstützt.

## <a name="common-commands"></a>Allgemeine Befehle

Diese Tabelle listet einige häufig verwendete Befehle auf, die in der CLI verwendet werden:

|Befehl|Beschreibung|Beispiele|
|------|-----------|--------|
|**PCF**|Befehle für die Arbeit mit [Power Apps component framework](/powerapps/developer/component-framework/overview). Verfügt über die folgenden Parameter: <br/> - **init**: Initialisiert das Codekomponentenprojekt. Es hat die folgenden Parameter <br/> - *namespace*: Namespace der Codekomponente. <br/> - *name*: Name der Codekomponente. <br/> - *template*: Feld oder DataSet <br/> - **push** : Verschiebt die Codekomponente mit den neuesten Änderungen auf die Common Data Service-Instanz. Es hat die folgenden Parameter: <br/> - *publisher-prefix*: Präfix des Herausgebers der Organisation.| `pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>` <br/> <br/> `pac pcf push --publisher-prefix <your publisher prefix>`|
|**Lösung**|Befehle für die Arbeit mit [Common Data Service Lösungsprojekten](/powerapps/maker/common-data-service/solutions-overview). Verfügt über die folgenden Parameter: <br/> - **init**: Initialisiert das Lösungsprojekt. Verfügt über die folgenden Parameter:<br/>  - *publisher-name*: Name des Herausgebers der Organisation. <br/>  - *publisher-prefix*: Präfix des Herausgebers der Organisation. <br/> - **add-reference**: Legt den Referenzpfad zum Komponentenprojektordner fest, indem der `path`-Parameter übergeben wird.<br/> - **clone**: Erstellt ein Lösungsprojekt auf der Grundlage des vorhandenen Lösungsprojekts, indem die folgenden Parameter `name`, `version` und `include` übergeben werden|`pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>` <br/><br/> `pac solution add-reference --path <path to your Power Apps component framework project>`<br/><br/> `pac solution clone –name<name of the solution to be exported> --version <version of your solution> --include <settings that should be included>`|
|**auth**|Befehle zur [Authentifizierung in Common Data Service](/powerapps/developer/component-framework/import-custom-controls#connecting-to-your-environment). Verfügt über die folgenden Parameter: <br/> - **Erstellen**: Erstellt das Authentifizierungsprofil für Ihre Organisation durch Übergeben des `url`-Parameters. Sie müssen die Organisations-URL für den `url`-Parameter übergeben. <br/> - **Liste**: Bietet die Liste der Authentifizierungsprofile. <br/> - **Auswählen**: Bietet eine Möglichkeit zum Wechseln zwischen zuvor erstellten Authentifizierungsprofilen durch Übergeben des `index`-Parameters.<br/>**Löschen**: Löscht das durch die Übergabe des Parameters `index` erstellte Authentifizierungsprofil.|`pac auth create --url <your Common Data Service org’s url>` <br/> <br/> `pac auth list` <br/><br/> `Pac auth select --index <index of the active profile>`|
|**Telemetrie**|Telemetrieeinstellungen verwalten. Verfügt über die folgenden Parameter: <br/>- *enable*: Aktiviert die Telemetrieoption.<br/> - *deaktivieren*: Deaktiviert die Telemetrie-Option.<br/> - *status*: Gibt zurück, ob die Telemetrie aktiviert oder deaktiviert ist.|`pac telemetry enable` <br/><br/> `pac telemetry disable`|
|**org**|Befehl zum Arbeiten mit Common Data Service.|`pac org who`|
|**Plug-In**|Verwaltet die Erstellung eines [Plug-in](/powerapps/developer/common-data-service/plug-ins) Projekts|`pac plugin init`|

## <a name="uninstall-power-apps-cli"></a>Deinstallieren der Power Apps CLI

Um das Power Apps CLI-Tooling zu deinstallieren, führen Sie das MSI von [hier](https://aka.ms/PowerAppsCLI) aus.

Wenn Sie einen Teilnehmer der **Privaten Vorschau** sind und eine ältere Version der CLI haben, führen Sie diese Schritte aus:

1. Um zu finden, wo Power Apps-CLI installiert ist, öffnen Sie eine Eingabeaufforderung und geben `where pac` ein

1. Löschen Sie den PowerAppsCLI-Ordner.

1. Öffnen Sie das Tool Environment Variables, indem Sie den Befehl `rundll32 sysdm.cpl,EditEnvironmentVariables` in der Eingabeaufforderung ausführen.

1. Klicken Sie zweimal im Abschnitt `User variable for...` auf `Path`.

1. Wählen Sie die Zeile mit dem PowerAppsCLI-Pfad aus, und wählen Sie rechts die Schaltfläche **Löschen** aus.

1. Wählen Sie zweimal **OK** aus.


## <a name="see-also"></a>Siehe auch

[Power Apps component framework](../component-framework/overview.md)