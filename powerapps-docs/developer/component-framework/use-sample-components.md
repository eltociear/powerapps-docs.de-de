---
title: Beispielkomponenten verwenden (Power Apps Component Framework) | Microsoft Docs
description: Enthält Informationen zur Verwendung der mit dem Power Apps Component Framework erstellten Beispielkomponenten in Ihren modellgesteuerten und Canvas-Apps
keywords: ''
author: Nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 11/25/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: a674b37fd4616a21fe8d61336f255debafd552dd
ms.sourcegitcommit: 3b68c4e29be4e8f68c0bfb88abdd1bbdf0187c57
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "3080840"
---
# <a name="how-to-use-the-sample-components"></a>Beispielkomponenten verwenden

Alle in diesem Abschnitt aufgeführten Beispielkomponenten können [hier](https://go.microsoft.com/fwlink/?linkid=2088525) heruntergeladen werden, um sie in modellgesteuerten oder Canvas-Apps zu testen.

In den einzelnen Themen zu Beispielkomponenten in diesem Abschnitt erhalten Sie einen Überblick über die Beispielkomponente, ihr visuelles Erscheinungsbild sowie das Manifest, den Code und die Ressourcen für die Beispielkomponente.

## <a name="before-you-can-try-the-sample-components"></a>Bevor Sie die Beispielkomponenten ausführen können
Um die Beispielkomponenten zu testen, müssen Sie zuerst:
- Eine lokale Kopie der Beispielkomponenten [herunterladen](https://go.microsoft.com/fwlink/?linkid=2088525).
- Installieren Sie die [Power Apps CLI](https://aka.ms/PowerAppsCLI).

## <a name="try-the-sample-components"></a>Testen der Beispielkomponenten
Führen Sie die folgenden Schritte aus, um die Beispielkomponenten in Ihre modellgesteuerte oder Canvas-App zu importieren und zu testen:

1. Navigieren Sie zum Ordner auf Ihrem Computer, in den Sie die Beispielkomponenten heruntergeladen haben, und extrahieren Sie die ZIP-Datei.  
1. Öffnen Sie die Entwicklereingabeaufforderung für Visual Studio 2017 und navigieren Sie zum Beispielkomponentenordner im extrahierten Ordner, den Sie zur Laufzeit anzeigen möchten. Navigieren Sie zum Beispiel zum Ordner \<extracted_folder>/TS_IncrementComponent.
1. Um alle erforderlichen Abhängigkeiten abzurufen, führen Sie den folgenden Befehl aus:
    ```CLI
    npm install
    ```
1. Erstellen Sie mit dem Befehl `mkdir <folder name>` einen neuen Ordner innerhalb des Beispielkomponentenordners und navigieren Sie mit dem Befehl `cd <folder name>` zum Ordner. 
1. Erstellen Sie mithilfe des folgenden Befehls ein neues Lösungsprojekt im Ordner:
    ```CLI
    pac solution init --publisher-name <Name of the publisher> --publisher-prefix <Publisher prefix>
    ```
1. Sobald das neue Lösungsprojekt erstellt ist, müssen Sie den Speicherort verweisen, an dem sich die Beispielkomponente befindet. Sie können den Verweis hinzufügen, indem Sie den folgenden Befehl verwenden:
    ```CLI
    pac solution add-reference --path <Path to the root of the sample component>
    ```
1. Um eine ZIP-Datei aus Ihrem Lösungsprojekt zu erstellen, müssen Sie `cd` im Lösungsprojektverzeichnis hinzufügen und das Projekt mit Hilfe des folgenden Befehls erstellen:
    
     ```CLI
     msbuild /t:restore
    ```
1. Führen Sie erneut den Befehl `msbuild` aus.
1. Die generierte Lösungs-Zip-Datei steht im Ordner `Solution\bin\debug` zur Verfügung. [Importieren Sie die Lösung](/powerapps/maker/common-data-service/import-update-export-solutions) manuell in Ihre Common Data Service-Umgebung mithilfe des Webportals, sobald die ZIP-Datei bereit ist. Alternativ können Sie die Lösung auch mit Power Apps-CLI-Befehlen importieren. Weitere Informationen finden Sie unter [Verbindung mit der Umgebung](https://docs.microsoft.com/powerapps/developer/component-framework/import-custom-controls#connecting-to-your-environment) und in den Abschnitten [Entwicklung](https://docs.microsoft.com/powerapps/developer/component-framework/import-custom-controls#deploying-code-components).
1. Informationen zum Hinzufügen von Codekomponenten zu modellgesteuerten Apps und Canvas-Apps finden Sie unter [Hinzufügen von Komponenten zu modellgesteuerten Apps](https://docs.microsoft.com/powerapps/developer/component-framework/add-custom-controls-to-a-field-or-entity) und [Hinzufügen von Komponenten zu Canvas-Apps](https://docs.microsoft.com/powerapps/developer/component-framework/component-framework-for-canvas-apps#add-components-to-a-canvas-app).
