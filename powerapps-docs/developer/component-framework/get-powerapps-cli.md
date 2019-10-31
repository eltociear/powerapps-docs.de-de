---
title: Tooling-Abruf für das PowerApps component framework | Microsoft Docs
description: 'Holen Sie sich die Microsoft PowerApps CLI, um Codekomponenten mit dem PowerApps component framework zu erstellen, zu debuggen und bereitzustellen.'
keywords: 'PowerApps Component Framework, Code-Komponenten, Komponentenframework'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
---

# <a name="get-tooling-for-powerapps-component-framework"></a>Tooling-Abruf für das PowerApps component framework

Verwenden Sie **Microsoft PowerApps CLI** (Befehlszeilenschnittstelle), um Codekomponenten mit dem PowerApps component framework zu erstellen, zu debuggen und bereitzustellen. PowerApps CLI ermöglicht es Entwicklern, Codekomponenten schnell zu erstellen und wird in Zukunft um die Unterstützung zusätzlicher Entwicklungs- und Application Lifecycle Management (ALM) Erfahrungen erweitert. 

## <a name="what-is-microsoft-powerapps-cli"></a>Was ist Microsoft PowerApps CLI? 

Microsoft PowerApps CLI ist eine einfache, zentrale Entwickler-Befehlszeilenschnittstelle, die es den Entwicklern und App-Herstellern ermöglicht, Codekomponenten zu erstellen. PowerApps CLI-Tooling ist der erste Schritt zu einer umfassenden ALM-Story, in der Unternehmensentwickler und ISVs ihre Erweiterungen und Anpassungen schnell und effizient erstellen, bauen, debuggen und veröffentlichen können.  

## <a name="install-microsoft-powerapps-cli"></a>Installieren der Microsoft PowerApps CLI

Um die Microsoft PowerApps CLI zu erhalten, gehen Sie wie folgt vor:

1. Installieren Sie [Npm](https://www.npmjs.com/get-npm)(wird mit Node.js geliefert) oder installieren Sie [Node.js](https://nodejs.org/en/) (wird mit npm geliefert). Wir empfehlen LTS (Long Term Support) Version 10.15.3 LTS, da es am stabilsten zu sein scheint.

1. Installieren Sie das [.NET Framework 4.6.2-Entwicklerpaket](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Wenn Sie Visual Studio 2017 oder später noch nicht haben, folgen Sie einer der folgenden Optionen:
   - Option 1: Installieren Sie [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) oder später.
   - Option 2: Installieren Sie das [.NET Core 2.2-SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) und dann [Visual Studio Code](https://code.visualstudio.com/Download).

1. Installieren Sie die [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI).
1. Um die Vorteile der neuesten Funktionen zu nutzen, aktualisieren Sie das CLI-Tooling PowerApps mit dem Befehl auf die neueste Version.

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Um Ihre Codekomponente über die CLI PowerApps bereitzustellen, benötigen Sie eine Umgebung Common Data Service mit Systemadministrator- oder System-Customizer-Rechten.
> - Derzeit wird PowerApps CLI nur unter Windows 10 unterstützt.

## <a name="microsoft-powerapps-cli-telemetry"></a>Microsoft PowerApps CLI-Telemetrie

Das Funktionsteam sammelt die Telemetrie, um zu verstehen, welche Funktionen oder Fähigkeiten Entwickler am häufigsten im CLI-Tool PowerApps verwenden. Die aggregierten Daten ermöglichen es uns, den Kunden das beste Erlebnis zu bieten, indem wir uns auf das konzentrieren, was wirklich wichtig ist.

> [!NOTE]
> Um die Telemetrie zu deaktivieren, führe Sie den Befehl `pac telemetry disable` aus. Um die Telemetrie wieder einzuschalten, verwenden Sie den Befehl `pac telemetry enable`.

## <a name="uninstall-microsoft-powerapps-cli"></a>Deinstallieren der Microsoft PowerApps CLI

Um das PowerApps CLI-Tooling zu deinstallieren, führen Sie das MSI von [hier](https://aka.ms/PowerAppsCLI) aus. 

Wenn Sie ein privater Vorschauteilnehmer sind und eine ältere Version der CLI haben, führen Sie diese Schritte aus:

1. Um herauszufinden, wo PowerApps CLI installiert ist, öffnen Sie eine Eingabeaufforderung und geben Sie `where pac` ein.
1. Löschen Sie den PowerAppsCLI-Ordner.
1. Öffnen Sie das Tool Environment Variables, indem Sie den Befehl `rundll32 sysdm.cpl,EditEnvironmentVariables` in der Eingabeaufforderung ausführen.
1. Klicken Sie zweimal im Abschnitt `User variable for...` auf `Path`.
1. Wählen Sie die Zeile mit dem PowerAppsCLI-Pfad aus und klicken Sie auf die Schaltfläche Delete auf der rechten Seite.
1. Klicken Sie zwei Mal auf **OK**.

### <a name="see-also"></a>Siehe auch

[Implementieren von Komponenten in TypeScript](implementing-controls-using-typescript.md)<br/>
