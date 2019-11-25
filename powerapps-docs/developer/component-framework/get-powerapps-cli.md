---
title: Tooling-Abruf für das PowerApps component framework | Microsoft Docs
description: Holen Sie sich die Microsoft PowerApps CLI, um Codekomponenten mit dem PowerApps component framework zu erstellen, zu debuggen und bereitzustellen.
keywords: PowerApps Component Framework, Code-Komponenten, Komponentenframework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 496b7d443775da075dd8da52ac4b0a754121bf28
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748483"
---
# <a name="get-tooling-for-powerapps-component-framework"></a>Tooling-Abruf für das PowerApps component framework

Verwenden Sie **Microsoft PowerApps CLI** (Befehlszeilenschnittstelle), um Codekomponenten mit dem PowerApps component framework zu erstellen, zu debuggen und bereitzustellen. Mit der PowerApps CLI können Entwickler Codekomponenten schnell erstellen. Künftig wird es erweitert, um Unterstützung für die weitere Entwicklung und Application Lifecycle Management (ALM)-Umgebungen einzuschließen. 

## <a name="what-is-microsoft-powerapps-cli"></a>Was ist Microsoft PowerApps CLI? 

Die Microsoft PowerApps CLI ist eine einfache, einheitliche Befehlszeilenschnittstelle für Entwickler, mit der Entwickler und App-Ersteller Codekomponenten erstellen können. Die PowerApps CLI-Tools sind der erste Schritt in Richtung einer umfassenden ALM-Story, in der Unternehmensentwickler und ISVs ihre Erweiterungen sowie Anpassungen schnell und effizient erstellen, debuggen und veröffentlichen können.  

## <a name="install-microsoft-powerapps-cli"></a>Installieren der Microsoft PowerApps CLI

Um die Microsoft PowerApps CLI zu erhalten, gehen Sie wie folgt vor:

1. Installieren Sie [Npm](https://www.npmjs.com/get-npm) (wird mit Node.js geliefert) oder [Node.js](https://nodejs.org/en/) (wird mit npm geliefert). Wir empfehlen LTS (Long Term Support) Version 10.15.3 LTS, da es am stabilsten zu sein scheint.

1. Installieren Sie das [.NET Framework 4.6.2-Entwicklerpaket](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Wenn Sie Visual Studio 2017 oder später noch nicht haben, folgen Sie einer der folgenden Optionen:
   - Option 1: Installieren Sie [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) oder später.
   - Option 2: Installieren Sie das [.NET Core 2.2-SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) und dann [Visual Studio Code](https://code.visualstudio.com/Download).

1. Installieren Sie die [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI).
1. Um alle aktuellen Funktionen nutzen zu können, aktualisieren Sie die PowerApps CLI-Tools auf die neuste Version mit Hilfe dieses Befehls:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Um Ihre Codekomponente über die CLI PowerApps bereitzustellen, benötigen Sie eine Umgebung Common Data Service mit Systemadministrator- oder System-Customizer-Rechten.
> - Derzeit wird PowerApps CLI nur unter Windows 10 unterstützt.

## <a name="microsoft-powerapps-cli-telemetry"></a>Microsoft PowerApps CLI-Telemetrie

Das Funktionsteam sammelt die Telemetrie, um zu verstehen, welche Funktionen oder Fähigkeiten Entwickler am häufigsten im CLI-Tool PowerApps verwenden. Die aggregierten Daten ermöglichen die Bereitstellung des besten Erlebnisses für die Kunden, indem Sie sich darauf konzentrieren können, was wirklich ist wichtig ist.

> [!NOTE]
> Um die Telemetrie zu deaktivieren, führe Sie den Befehl `pac telemetry disable` aus. Um die Telemetrie wieder einzuschalten, verwenden Sie den Befehl `pac telemetry enable`.


## <a name="uninstall-microsoft-powerapps-cli"></a>Deinstallieren der Microsoft PowerApps CLI

Um das PowerApps CLI-Tooling zu deinstallieren, führen Sie das MSI von [hier](https://aka.ms/PowerAppsCLI) aus. 

Wenn Sie ein Teilnehmer der Privaten Vorschau sind und eine ältere Version der CLI haben, führen Sie diese Schritte aus:

1. Um herauszufinden, wo PowerApps CLI installiert ist, öffnen Sie eine Eingabeaufforderung und geben Sie `where pac` ein.
1. Löschen Sie den PowerAppsCLI-Ordner.
1. Öffnen Sie das Tool Environment Variables, indem Sie den Befehl `rundll32 sysdm.cpl,EditEnvironmentVariables` in der Eingabeaufforderung ausführen.
1. Klicken Sie zweimal im Abschnitt `User variable for...` auf `Path`.
1. Wählen Sie die Zeile mit dem PowerAppsCLI-Pfad aus, und wählen Sie rechts die Schaltfläche **Löschen** aus.
1. Wählen Sie zweimal **OK** aus.

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten mithilfe von TypeScript](implementing-controls-using-typescript.md)<br/>
