---
title: Erstellen und Erstellen einer Code Komponente | Microsoft-Dokumentation
description: Beginnen Sie mit dem Erstellen einer Komponente mithilfe der Tools von powerapps Component Framework.
keywords: Powerapps-Komponenten Framework, Code Komponenten, Komponenten Framework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 286458da2ed7b7b94f92b86355bf8785161ef778
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347013"
---
# <a name="create-and-build-a-code-component"></a>Erstellen und Erstellen einer Code Komponente

In diesem Thema wird erläutert, wie Code Komponenten mithilfe der powerapps-CLI erstellt und bereitgestellt werden. Stellen Sie sicher, dass Sie [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI)installiert haben.

## <a name="create-a-new-component"></a>Neue Komponente erstellen

Öffnen Sie zunächst **Developer-Eingabeaufforderung für vs 2017** nach der Installation der powerapps-CLI.

1. Erstellen Sie im Developer-Eingabeaufforderung für Visual Studio 2017 einen neuen Ordner auf dem lokalen Computer – z. b. *c:\Users\YOUR name\Documents\My_PCF_Component* . verwenden Sie dazu den Befehl `mkdir <Specify the folder name>`.
2. Wechseln Sie mithilfe des Befehls `cd <specify your new folder path>` zum neu erstellten Ordner.
3. Führen Sie den folgenden Befehl aus, um ein neues Komponenten Projekt zu erstellen, indem Sie einige grundlegende Parameter übergeben:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Die powerapps-CLI unterstützt derzeit zwei Arten von Komponenten: **Feld** und **DataSet**.  Für Canvas-apps wird nur der **Feldtyp** für diese experimentelle Vorschau unterstützt.

4. Um alle erforderlichen Projekt Abhängigkeiten abzurufen, führen Sie den Befehl `npm install` aus.
5. Öffnen Sie Ihren Projektordner `C:\Users\<your name>\Documents\<My_PCF_Component>` in einer beliebigen Entwicklerumgebung Ihrer Wahl, und beginnen Sie mit der Entwicklung von Code Komponenten. Die schnellste Methode für den Einstieg besteht darin, dass Sie `code .` über die Eingabeaufforderung ausführen, sobald Sie sich im `C:\Users\<your name>\Documents\<My_PCF_Component>` Verzeichnis befinden. Dieser Befehl öffnet das Komponenten Projekt in Visual Studio Code.

## <a name="build-your-component"></a>Erstellen der Komponente

Um das Komponenten Projekt zu erstellen, öffnen Sie den Projektordner, der `package.json` in Visual Studio Code enthält, und verwenden Sie den Befehl (STRG + UMSCHALT + B), und wählen Sie dann die Buildoptionen aus. Alternativ können Sie die Komponente mithilfe des Befehls `npm run build` im Fenster Developer-Eingabeaufforderung für Visual Studio 2017 schnell erstellen.

> [!TIP]
> Informationen zum Debuggen der Komponente während oder nach dem Buildvorgang finden Sie unter [Debuggen einer Code Komponente](debugging-custom-controls.md).

Nachdem Sie die Komponenten Logik in typescript implementiert haben, müssen Sie alle Code Komponenten Elemente in einer Projektmappendatei bündeln, damit Sie die Lösung in Common Data Service importieren können. Weitere Informationen: [Verpacken einer Code Komponente](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>Bekannte Konfigurationsprobleme und Problem Umgehungen

**MSBuild-Fehler MSB4036:**

1. Der Name der Aufgabe in der Projektdatei ist mit dem Namen der Aufgaben Klasse identisch.
2. Die Task-Klasse ist öffentlich und implementiert die Microsoft. Build. Framework. ITask-Schnittstelle.
3. Der Task wurde mit *\<UsingTask >* in der Projektdatei oder in den *. Tasks-Dateien, die sich im Pfad Verzeichnis befinden, ordnungsgemäß deklariert.

**Lösungs**

1. Öffnen Sie Visual Studio-Installer. 
1. Wählen Sie für Visual Studio 2017 die Option **ändern**aus. 
1. Wählen Sie **einzelne Komponenten**aus.
1. Aktivieren Sie unter Code Tools die Option **nuget-Ziele & Buildaufgaben**.

**Verleger Präfix**

Wenn eine Komponente mit einer powerapps-CLI-ToolsVersion kleiner als 0.4.3 erstellt wird, tritt ein Fehler auf, wenn Sie versuchen, die Projektmappendatei erneut in Common Data Service zu importieren. Der Fehler wird ausgelöst, weil der neu importierte Komponenten Name nun mit dem Herausgeber Präfix versehen wird, um seine Eindeutigkeit sicherzustellen und Konflikte zu vermeiden.

Problem **Umgehung**:

- Löschen Sie die Projekt Mappe mit der relevanten Komponente aus Common Data Service. Wenn die Komponente bereits in einem Formular oder Raster konfiguriert ist, muss Sie zuerst entfernt werden, da die Komponenten Lösung eine Abhängigkeit von der Konfiguration aufweist.  
- Importieren Sie die neue Projekt Mappe mit Updates für die-Komponente, die mit der neuesten CLI-Version erstellt wurde.
- Neu importierte Komponenten können jetzt in Formularen oder Raster konfiguriert werden.  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>Siehe auch

[Code Komponenten Debuggen](debugging-custom-controls.md)<br/>
[Packen einer Code Komponente](import-custom-controls.md)<br/>
[Hinzufügen von Code Komponenten zu einem Feld oder einer Entität](add-custom-controls-to-a-field-or-entity.md)<br/>
[Aktualisieren vorhandener Code Komponenten](updating-existing-controls.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](overview.md)
