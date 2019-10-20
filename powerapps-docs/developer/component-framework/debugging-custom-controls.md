---
title: Debugcode-Komponenten | MicrosoftDocs
description: Debuggen einer Code Komponente mithilfe von "fddler" und nativem Debuggen
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 088792a32f401ddaf7d3a3cd4fd4d5aa9fa472ff
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346921"
---
# <a name="debug-code-components"></a>Code Komponenten Debuggen

Sobald Sie mit der Implementierung der Code Komponenten Logik fertig sind, können Sie mit dem Befehl "`npm start`" mit dem Testen und Debuggen der Code Komponente beginnen. Dadurch wird die Code Komponente erstellt und in der lokalen Testumgebung geöffnet.

> [!div class="mx-imgBorder"]
> ![Testumgebung 1](media/test-harness-1.png "Testumgebung 1")

Wie die Abbildung oben zeigt, wird das Browserfenster mit vier Abschnitten geöffnet. Die Code Komponente wird im linken Bereich gerendert, während im rechten Bereich die Abschnitte **Kontext Eingaben**, **Dateneingaben**und **Ausgaben** angezeigt werden.

- **Kontext Eingaben** bieten eine Möglichkeit, den Formular Faktor anzugeben und die Code Komponente mit jedem Formfaktor (Web, Tablet, Phone) zu testen. Dies ist hilfreich, wenn die Code Komponente von einer bestimmten Formfaktor Funktion abhängig ist.
- **Dateneingaben** sind eine interaktive Benutzeroberfläche, auf der alle Eigenschaften und deren [Typen](manifest-schema-reference/types.md) oder [Typgruppen](manifest-schema-reference/type-group.md) angezeigt werden, die in der [Manifest](manifest-schema-reference/manifest.md) -Datei definiert sind. Sie ermöglicht es Ihnen, in den mockdaten für jede Eigenschaft zu Schlüsseln. 
- **Ausgaben** rendert die Ausgabe, wenn die [getoutputs](reference/control/getoutputs.md) -Methode einer Komponente aufgerufen wird.  

     > [!div class="mx-imgBorder"]
     > ![Testumgebung 2](media/test-harness-2.png "Testumgebung 2")

> [!NOTE]
> Wenn Sie die `ControlManifest.Input.xml` Datei ändern oder zusätzliche Eigenschaften erstellen möchten, müssen Sie den Debugprozess neu starten, bevor Sie im Abschnitt Eingaben angezeigt werden.

## <a name="test-code-components-with-mock-data"></a>Testen von Code Komponenten mit Mock-Daten

- Für *Feldtyp* Komponenten können Sie den Wert und den Typ für jede Eigenschaft eingeben, die in der Datei " **controlmanifest. Input. XML** " definiert ist, wie hier gezeigt:

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 2,5](media/test-harness-2.5.png "Testumgebung 2,5")

- Für *DataSet* -typkomponenten können Sie eine CSV-Datei mit Testdaten laden. Sie erstellen oder exportieren Sie manuell im CSV-Format direkt aus Ihrer Umgebung. Sobald eine gültige CSV-Datei verfügbar ist, kann Sie wie hier gezeigt geladen werden:

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 3](media/test-harness-3.png "Testumgebung 3")

- Binden Sie nach dem Laden einer CSV-Datei jede in der Datei " **controlmanifest. Input. XML** " definierte Eigenschaft an eine Spalte in der CSV-Datei. Dies erfolgt durch Auswählen der Spalte für jede Eigenschaft, wie hier gezeigt:

    > [!div class="mx-imgBorder"]
    > Testumgebung ![4](media/test-harness-4.png "Testumgebung 4")

- Wenn Sie keine Eigenschaften in der Datei " **controlmanifest. Input. XML** " definiert haben, werden alle Spalten automatisch in die Testumgebung geladen.

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 5](media/test-harness-5.png "Testumgebung 5")


## <a name="watch-mode-in-test-harness"></a>Überwachungsmodus in Testumgebung

Die Testumgebung unterstützt den `watch` Modus, den Sie für powerapps-Komponenten Framework-Projekte nutzen können. Um den `watch` Modus zu aktivieren, starten Sie die Testumgebung mit dem Befehl `npm start watch`. Im `watch` Modus werden die Änderungen an den folgenden Komponenten Objekten automatisch in der Testumgebung wiedergegeben, ohne dass ein Neustart erforderlich ist:

1.  `index.ts` Datei.
2.  `ControlManifest.Input.xml` Datei.
3.  Importierte Bibliotheken in `index.ts`.
4.  Alle Ressourcen, die in der Manifest-Datei aufgelistet sind.

## <a name="debug-code-components-using-native-browsers"></a>Debuggen von Code Komponenten mithilfe nativer Browser

Sie können die Debuggingfunktionen des Browsers verwenden, um das Verhalten der Komponente zu beobachten. Jeder Browser stellt ein Debugtool bereit, mit dem Sie Ihren Code im Browser nativ Debuggen können. In der Regel können Sie das Debuggen in Ihrem Browser aktivieren, indem Sie die Taste **F12** drücken, um das Native Entwickler Tool für das Debuggen anzuzeigen.

Beispielsweise auf **Microsoft Edge**:

- Drücken Sie **F12** , um den Inspektor zu öffnen.
- Wählen Sie die Komponente aus.
- Wechseln Sie in der oberen Leiste zum **Debugger** , und suchen Sie nach dem Komponentennamen, der in der Manifest-Datei in der Suchleiste beschrieben wird. Geben Sie z. b. den Namen der Komponente wie `Hello World component` ein.

     > [!div class="mx-imgBorder"]
     > Komponente(media/debug-control.png "Debugkomponente") ![Debuggen]

> [!NOTE]
> Es ist immer eine bewährte Methode, Haltepunkte für die Lebenszyklus Methoden der Komponente wie [Init](reference/control/init.md) und [Update View](reference/control/updateview.md)festzulegen.

Sie können auch lokal in Echtzeit mit der Komponente interagieren und die Elemente im Dom beobachten, indem Sie auf der Registerkarte *Quellen* einen Haltepunkt festlegen, wie hier gezeigt:

> [!div class="mx-imgBorder"]
> ![Debugkomponente]Debuggen Komponente(media/debug-control-1.png "1")

## <a name="fiddler-autoresponder"></a>Autor von "fddler"

Verwenden Sie den Autor von "fddler", um Ihre Code Komponenten schnell zu debuggen. Installieren Sie " [fddler](https://www.telerik.com/download/fiddler) ", und befolgen Sie die Schritte zum Konfigurieren von [Autoresponder](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder).

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](overview.md)
