---
title: Debug-Codekomponenten | MicrosoftDocs
description: Wie man eine Codekomponente mit Fiddler und Native Debugging debuggt.
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
---
# <a name="debug-code-components"></a>Debuggen von Codekomponenten

Sobald Sie mit der Implementierung der Codekomponentenlogik fertig sind, beginnen Sie mit dem Testen und Debuggen der Codekomponente mit dem Befehl `npm start`. Dadurch wird die Codekomponente erstellt und im lokalen Testbereich geöffnet.

> [!div class="mx-imgBorder"]
> ![Testumgebung 1](media/test-harness-1.png "Testumgebung 1")

Wie in der obigen Abbildung dargestellt wird das Browserfenster mit 4 Abschnitten geöffnet. Die Codekomponente wird im linken Bereich gerendert, während der rechte Bereich **Context inputs**, **Data inputs** und **Outputs** Abschnitte hat.

- **Context inputs** bietet eine Möglichkeit, den Formfaktor zu spezifizieren und die Codekomponente mit jedem Formfaktor (Web, Tablett, Telefon) zu testen. Dies ist hilfreich, wenn die Codekomponente von einer bestimmten Formfaktorfähigkeit abhängig ist. In der kommenden Version Haben Sie die Möglichkeit, die Höhe und Breite anzugeben.
- **Data inputs** ist eine interaktive Benutzeroberfläche, die alle Eigenschaften und deren [Typen](manifest-schema-reference/types.md) oder [Typgruppen](manifest-schema-reference/type-group.md) anzeigt, die in der Datei [manifest](manifest-schema-reference/manifest.md) definiert sind. Damit können Sie Pseudodaten für jede Eigenschaft eingeben. 
- **Outputs** rendert die Ausgabe, wenn die Methode [getOutputs](reference/control/getoutputs.md) einer Komponente aufgerufen wird.  

     > [!div class="mx-imgBorder"]
     > ![Testumgebung 2](media/test-harness-2.png "Testumgebung 2")

> [!NOTE]
> Wenn Sie die Datei `ControlManifest.Input.xml` ändern oder weitere Eigenschaften erstellen möchten, müssen Sie den Debugging-Prozess erneut starten, bevor sie im Eingabebereich angezeigt werden.

## <a name="test-code-components-with-mock-data"></a>Testcodekomponenten mit Mockdaten

- Für *Feld* Typkomponenten können Sie Wert und Typ für jede Eigenschaft eingeben, die in Ihrer **ControlManifest.Input.xml** definiert ist, wie unten gezeigt:

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 2.5](media/test-harness-2.5.png "Testumgebung 2.5")

- Für *Datensatz* Typkomponenten können Sie eine CSV-Datei mit Testdaten laden. Sie erstellen oder exportieren manuell im .csv-Format direkt aus Ihrer Umgebung. Nachdem eine gültige CSV-Datei verfügbar ist, kann sie wie unten gezeigt geladen werden:

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 3](media/test-harness-3.png "Testumgebung 3")

- Binden Sie nach dem Laden einer CSV-Datei jede in der Datei **ControlManifest.Input.xml** definierte Eigenschaft an eine Spalte in der CSV-Datei. Dies geschieht, indem Sie die Spalte für jede Eigenschaft auswählen (siehe unten):

    > [!div class="mx-imgBorder"]
    > ![Testumgebung 4](media/test-harness-4.png "Testumgebung 4")

- Wenn Sie keine Eigenschaften in der Datei **ControlManifest.Input.xml** definiert haben, werden alle Spalten automatisch in den Testbereich geladen.

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 5](media/test-harness-5.png "Testumgebung 5")


## <a name="watch-mode-in-test-harness"></a>Watch-Modus im Testbereich

Der Testbereich unterstützt den `watch`-Modus, den Sie für PowerApps component framework Projekte nutzen können. Um den `watch`-Modus zu aktivieren, starten Sie den Testbereich mit dem Befehl `npm start watch`. Im Modus `watch` werden die Änderungen, die an einer der folgenden Komponenten vorgenommen wurden, automatisch in den Testbereich übernommen, ohne es neu starten zu müssen:

1.  `index.ts`-Datei enthalten sind.
2.  `ControlManifest.Input.xml`-Datei enthalten sind.
3.  Importierte Bibliotheken in `index.ts`.
4.  Alle Ressourcen, die in der Manifestdatei aufgeführt sind.

## <a name="debug-code-components-using-native-browsers"></a>Debuggen von Codekomponenten mit nativen Browsern

Sie können die Debugging-Funktionen Ihres Browsers verwenden, um das Komponentenverhalten zu beobachten. Jeder Browser bietet ein Debugging-Tool, das Ihnen hilft, Ihren Code systemeigen im Browser zu debuggen. In der Regel können Sie das Debugging in Ihrem Browser aktivieren, indem Sie die Taste **F12** drücken, um das systemeigene Entwicklungstool anzuzeigen,d as für das Debugging verwendet wird.

Zum Beispiel in **Microsoft Edge**,

- Drücken Sie **F12**, um den Inspector zu öffnen.
- Klicken Sie auf Ihre Komponente
- In der oberen Leiste wechseln Sie zu **Debugger** und starten dann in der Suchleiste eine Suche nach dem in der Manifestdatei beschriebenen Komponentennamen. Geben Sie z. B. Ihren Komponentennamen als `Hello World component` ein.

     > [!div class="mx-imgBorder"]
     > ![debug-component](media/debug-control.png "Komponente debuggen")

> [!NOTE]
> Es ist immer eine gute Praxis, Haltepunkte für die Lebenszyklusmethoden der Komponente wie [init](reference/control/init.md) und [updateView](reference/control/updateview.md) zu setzen.

Sie können mit der Komponente auch lokal in Echtzeit interagieren und Elemente in DOM beobachten, indem Sie wie folgt einen Haltepunkt in der Registerkarte „Quellen“ festlegen:

> [!div class="mx-imgBorder"]
> ![debug-component](media/debug-control-1.png "Komponente 1 debuggen")

## <a name="fiddler-autoresponder"></a>Fiddler-AutoResponder

Verwenden Sie den Fiddler AutoResponder, um Ihre Codekomponenten schnell zu debuggen. Installieren Sie [Fiddler](https://www.telerik.com/download/fiddler) aus und folgen Sie den Schritten zum Konfigurieren von [AutoResponder](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)

### <a name="related-topics"></a>Verwandte Themen

[PowerApps component framework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps component framework](overview.md)
