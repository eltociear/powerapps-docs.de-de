---
title: Erstellen und Entwickeln einer Code-Komponente | Microsoft Docs
description: Starten der Erstellung einer Komponente mit PowerApps Component Framework-Tooling
keywords: 'PowerApps Component Framework, Code-Komponenten, Komponentenframework'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---

# <a name="create-and-build-a-code-component"></a>Erstellen und Entwickeln einer Code-Komponente

Dieses Thema zeigt, wie Sie Code-Komponenten mithilfe von PowerApps CLI erstellen und bereitstellen. Stellen Sie sicher, dass [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI) installiert ist.

## <a name="create-a-new-component"></a>Erstellen einer neuen Komponente

Für den Anfang öffnen Sie eine neue **Entwicklereingabeaufforderung für VS 2017** nach der Installation von PowerApps CLI.

1. In der Entwicklereingabeaufforderung für VS 2017 erstellen Sie einen neuen Ordner auf Ihrem lokalen Computer, z. B. *C:\Benutzer\Ihr Name\Dokumente\Meine_PCF_Komponente*, mithilfe des Befehls `mkdir <Specify the folder name>`.
2. Wechseln Sie mit dem Befehl `cd <specify your new folder path>` zum neu erstellen Ordner.
3. Führen Sie den Befehl unten aus, um ein neues Komponentenprojekt zu erstellen, indem Sie einige Basisparameter übergeben:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Derzeit unterstützt PowerApps CLI zwei Arten von Komponenten: **Feld** und **DataSet**.  Für Canvas-Apps wird nur der Typ **Feld** für diese experimentelle Vorschau unterstützt.

4. Um alle erforderlichen Projektabhängigkeiten abzurufen, führen Sie den Befehl `npm install` aus.
5. Öffnen Sie Ihren Projektordner `C:\Users\<your name>\Documents\<My_PCF_Component>` in einer Entwicklerumgebung Ihrer Wahl und beginnen Sie mit der Entwicklung Ihrer Code-Komponente. Die schnellste Möglichkeit, zu starten, besteht darin, `code .` über die Eingabeaufforderung auszuführen, sobald Sie sich im Verzeichnis `C:\Users\<your name>\Documents\<My_PCF_Component>` befinden. Durch diesen Befehl wird das Komponentenprojekt in Visual Studio Code geöffnet.

## <a name="build-your-component"></a>Entwickeln Ihrer Komponente

Um das Komponentenprojekt zu erstellen, öffnen Sie den Projektordner, der `package.json` in Visual Studio Code enthält, und verwenden Sie den Befehl (Strg-Umschalt-B). Dann wählen Sie Ihre Build-Optionen aus. Alternativ können Sie die Komponente auch schnell mit dem `npm run build`-Befehl in der Entwicklereingabeaufforderung für das VS 2017-Fenster erstellen.

> [!TIP]
> Zum Debuggen der Komponente während oder nach dem Buildvorgang siehe [Debuggen einer Code-Komponente](debugging-custom-controls.md).

Nach dem Implementieren der Komponentenlogik in TypeScript müssen Sie alle Codekomponentenelemente in einer Lösungsdatei bündeln, damit Sie die Lösung in Common Data Service importieren können. Weitere Informationen: [Bündeln einer Code-Komponente](import-custom-controls.md).

## <a name="known-configuration-issues-and-workarounds"></a>Bekannte Konfigurationsprobleme und Behebungen

**Msbuild-Fehler MSB4036:**

1. Der Name der Aufgabe in der Projektdatei gleicht dem Namen der Aufgabenklasse.
2. Die Aufgabenklasse ist öffentlich und implementiert die Microsoft.Build.Framework.ITask-Schnittstelle.
3. Die Aufgabe ist mit *\<UsingTask>* korrekt in der Projektdatei in den *.tasks-Dateien im Pfadverzeichnis deklariert.

**Lösung:**

1. Öffnen Sie das Visual Studio-Installationsprogramm. 
1. Wählen Sie für VS 2017 **Ändern** aus. 
1. Klicken Sie auf „Einzelne Komponenten“.
1. Überprüfen Sie unter „Code-Tools“ die Option **NuGet-Ziele und Build-Aufgaben**.

**Herausgeberpräfix**

Wenn eine Komponente mithilfe der PowerApps CLI-Toolversion unter 0.4.3 erstellt wird, wird Ihnen eine Fehlermeldung angezeigt, wenn Sie versuchen, eine Lösungsdatei wieder in Common Data Service zu importieren. Dieser Fehler wird ausgegeben, weil dem Namen der neu importierten Komponente jetzt das Herausgeberpräfix angehängt wird, um sicherzustellen, dass dieser eindeutig ist, und um Konflikte zu vermeiden.

**Problemumgehung**:

- Löschen Sie die Lösung, die die relevante Komponente aus Common Data Service enthält. Wenn die Komponente bereits in einem Formular oder einem Raster konfiguriert ist, muss sie dort zuerst entfernt werden, da die Komponentenlösung in einer Abhängigkeit zur Konfiguration stand.  
- Importieren Sie die neue Lösung mit Updates an der Komponente, die durch die aktuelle CLI-Version erstellt wurden.
- Neu importierte Komponenten können jetzt in Formularen oder Rastern konfiguriert werden.  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>Siehe auch

[Debuggen von Code-Komponenten](debugging-custom-controls.md)<br/>
[Bündeln einer Code-Komponente](import-custom-controls.md)<br/>
[Hinzufügen von Code-Komponenten zu einem Feld oder einer Entität](add-custom-controls-to-a-field-or-entity.md)<br/>
[Aktualisieren vorhandener Code-Komponenten](updating-existing-controls.md)<br/>
[PowerApps component framework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps component framework](overview.md)
