---
title: Tools für das powerapps-Komponenten Framework Microsoft-Dokumentation
description: Rufen Sie die Microsoft PowerApps CLI zum Erstellen, Debuggen und Bereitstellen von Code Komponenten mit dem powerapps-Komponenten Framework ab.
keywords: Powerapps-Komponenten Framework, Code Komponenten, Komponenten Framework
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
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2019
ms.locfileid: "72340021"
---
# <a name="get-tooling-for-powerapps-component-framework"></a>Tools für das powerapps-Komponenten Framework

Verwenden Sie **Microsoft PowerApps CLI** (Befehlszeilenschnittstelle) zum Erstellen, Debuggen und Bereitstellen von Code Komponenten mithilfe des powerapps-Komponenten-Frameworks. Powerapps CLI ermöglicht Entwicklern das schnelle Erstellen von Code Komponenten. In der Zukunft wird Sie erweitert, um Unterstützung für zusätzliche Entwicklungs-und Application Lifecycle Management (ALM)-Umgebungen zu bieten. 

## <a name="what-is-microsoft-powerapps-cli"></a>Was ist die Microsoft PowerApps CLI 

Microsoft PowerApps CLI ist eine einfache Befehlszeilenschnittstelle für Entwickler mit einmaligem Ende, die Entwicklern und App-Entwicklern das Erstellen von Code Komponenten ermöglicht. Powerapps-CLI-Tools sind der erste Schritt in Richtung einer umfassenden Alm-Story, in der Entwickler und ISVs von Unternehmen ihre Erweiterungen und Anpassungen schnell und effizient erstellen, erstellen, Debuggen und veröffentlichen können.  

## <a name="install-microsoft-powerapps-cli"></a>Installieren von Microsoft PowerApps CLI

Gehen Sie folgendermaßen vor, um Microsoft PowerApps CLI zu erhalten:

1. Installieren Sie [NPM](https://www.npmjs.com/get-npm) (mit Node. js) oder [node. js](https://nodejs.org/en/) (enthält NPM). Wir empfehlen LTS (langfristige Unterstützung) Version 10.15.3 LTS, da Sie anscheinend die stabilste ist.

1. Installieren Sie [.NET Framework 4.6.2 Developer Pack](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Wenn Sie noch nicht über Visual Studio 2017 oder höher verfügen, verwenden Sie eine der folgenden Optionen:
   - Option 1: Installieren Sie [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) oder höher.
   - Option 2: Installieren Sie das [.net Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) , und installieren Sie dann [Visual Studio Code](https://code.visualstudio.com/Download).

1. Installieren Sie [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI).
1. Um die neuesten Funktionen nutzen zu können, aktualisieren Sie die powerapps-CLI-Tools auf die neueste Version, indem Sie den folgenden Befehl verwenden:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Um die Code Komponente mithilfe der powerapps-Befehlszeilenschnittstelle bereitzustellen, müssen Sie über eine Common Data Service Umgebung mit Systemadministrator-oder systemanpassungsberechtigungen verfügen.
> - Derzeit wird die powerapps-CLI nur unter Windows 10 unterstützt.

## <a name="microsoft-powerapps-cli-telemetry"></a>Microsoft PowerApps CLI-Telemetrie

Das Featureteam aggregierte die Telemetriedaten, um zu verstehen, welche Features oder Funktionen Entwickler am häufigsten im powerapps-CLI-Tool verwenden. Mithilfe der aggregierten Daten können wir den Kunden die bestmögliche Leistung bereitstellen, indem wir uns auf das Wesentliche konzentrieren.

> [!NOTE]
> Führen Sie den Befehl `pac telemetry disable` aus, um die telemetriesammlung zu deaktivieren. Um die Telemetrie wieder zu aktivieren, verwenden Sie den Befehl `pac telemetry enable`.


## <a name="uninstall-microsoft-powerapps-cli"></a>Deinstallieren Microsoft PowerApps CLI

Um die powerapps-CLI-Tools zu deinstallieren, führen Sie die MSI von [hier](https://aka.ms/PowerAppsCLI)aus. 

Wenn Sie ein privater Vorschau Teilnehmer sind und über eine ältere Version der CLI verfügen, führen Sie die folgenden Schritte aus:

1. Um herauszufinden, wo die powerapps-CLI installiert ist, öffnen Sie eine Eingabeaufforderung, und geben Sie `where pac` ein.
1. Löschen Sie den Ordner powerappscli.
1. Öffnen Sie das Tool Umgebungsvariablen, indem Sie den Befehl `rundll32 sysdm.cpl,EditEnvironmentVariables` an der Eingabeaufforderung ausführen.
1. Doppelklicken Sie im Abschnitt `User variable for...` auf `Path`.
1. Wählen Sie die Zeile mit dem powerappscli-Pfad aus, und klicken Sie auf der rechten Seite auf die Schaltfläche **Löschen** .
1. Wählen Sie zweimal **OK** aus.

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten mithilfe von typescript](implementing-controls-using-typescript.md)<br/>
