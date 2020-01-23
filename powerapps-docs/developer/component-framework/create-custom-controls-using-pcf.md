---
title: Erstellen und Entwickeln einer Code-Komponente | Microsoft Docs
description: Starten der Erstellung einer Komponente mit Power Apps Component Framework-Tooling
keywords: Power Apps Component Framework, Code-Komponenten, Komponentenframework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 70532cfb3cc5cfad0f274f123857eedc5d54cae2
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909280"
---
# <a name="create-and-build-a-code-component"></a>Erstellen und Entwickeln einer Code-Komponente

Dieses Thema zeigt, wie Sie Code-Komponenten mithilfe von Power Apps CLI erstellen und bereitstellen. Stellen Sie sicher, dass [Microsoft Power Apps CLI](https://aka.ms/PowerAppsCLI) installiert ist.

## <a name="create-a-new-component"></a>Erstellen einer neuen Komponente

Zum Starten öffnen Sie **Entwickler-Eingabeaufforderung für VS 2017** nach dem Sie CLI Power Apps installiert haben.

1. In der Entwicklereingabeaufforderung für VS 2017 erstellen Sie einen neuen Ordner auf Ihrem lokalen Computer, z. B. *C:\Benutzer\Ihr Name\Dokumente\\Meine_Codekomponente* mit dem Befehl `mkdir <Specify the folder name>`.
2. Wechseln Sie mit dem Befehl `cd <specify your new folder path>` zum neu erstellen Ordner.
3. Führen Sie den Befehl aus, um ein neues Komponentenprojekt zu erstellen, indem Sie Basisparameter übergeben:

    ```CLI
    pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>
    ```
 
   > [!NOTE]
   > Derzeit Power Apps unterstützt CLI zwei Typen von Komponenten: **Feld** und **Dataset** für modellgesteuerte Apps.  Für Canvas-Apps wird nur der Typ **Feld** für diese experimentelle Vorschau unterstützt.

4. Um alle erforderlichen Projektabhängigkeiten abzurufen, führen Sie den Befehl `npm install` aus.
5. Öffnen Sie Ihren Projektordner `C:\Users\<your name>\Documents\<My_code_Component>` in einer Entwicklerumgebung Ihrer Wahl und beginnen Sie mit der Entwicklung Ihrer Code-Komponente. Die schnellste Möglichkeit, zu starten, besteht darin, `code .` über die Eingabeaufforderung auszuführen, sobald Sie sich im Verzeichnis `C:\Users\<your name>\Documents\<My_code_Component>` befinden. Durch diesen Befehl wird das Komponentenprojekt in Visual Studio Code geöffnet.
6. Implementieren Sie die erforderlichen Artefakte für die Komponente wie Manifest, Komponentenlogik und Formatierung und erstellen Sie dann das Komponentenprojekt. Mehr Informationen: [Erstellen Sie Ihre erste Codekomponente](implementing-controls-using-typescript.md)

## <a name="build-your-component"></a>Entwickeln Ihrer Komponente

Um das Komponentenprojekt zu erstellen, öffnen Sie den Projektordner, der `package.json` in Visual Studio Code enthält, und verwenden Sie den Befehl (Strg-Umschalt-B). Dann wählen Sie Ihre Build-Optionen aus. Alternativ können Sie Ihre Komponente schnell mit dem `npm run build`-Befehl in Ihrem Entwicklereingabeaufforderung für VS 2017-Fenster erstellen.

> [!TIP]
> Zum Debuggen der Komponente während oder nach dem Buildvorgang siehe [Debuggen einer Code-Komponente](debugging-custom-controls.md).

Wenn Sie schließlich mit der Implementierung der Komponentenlogik in TypeScript fertig sind, müssen Sie alle Codekomponentenelemente in einer Lösungsdatei bündeln, damit Sie die Lösung in Common Data Service importieren können. Weitere Informationen: [Bündeln einer Code-Komponente](import-custom-controls.md).

### <a name="see-also"></a>Siehe auch

[Debuggen von Code-Komponenten](debugging-custom-controls.md)<br/>
[Bündeln einer Code-Komponente](import-custom-controls.md)<br/>
[Hinzufügen von Code-Komponenten zu einem Feld oder einer Entität](add-custom-controls-to-a-field-or-entity.md)<br/>
[Aktualisieren vorhandener Code-Komponenten](updating-existing-controls.md)<br/>
[Power Apps component framework-API-Referenz](reference/index.md)<br/>
[Power Apps component framework Übersicht](overview.md)
