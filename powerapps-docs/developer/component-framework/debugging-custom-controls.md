---
title: Debuggen von benutzerdefinierten Komponenten | MicrosoftDocs
description: So debuggen Sie eine benutzerdefinierte Komponente mithilfe von Fiddler und Native-Debugging
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
---
# <a name="debug-custom-components"></a>Debuggen von benutzerdefinierten Komponenten

Wenn Sie eine benutzerdefinierte Komponentenlogik implementiert haben, testen und debuggen Sie die benutzerdefinierte Komponente mit dem Befehl `npm start`. Dies erstellt die benutzerdefinierte Komponente und öffnet sie in der lokalen Testumgebung.

> [!div class="mx-imgBorder"]
> ![Testumgebung 1](media/test-harness-1.png "Testumgebung 1")

Wie in der obigen Abbildung dargestellt wird das Browserfenster mit 4 Abschnitten geöffnet. Die benutzerdefinierte Komponente wird im linken Bereich gerendert. Der rechte Bereich besteht aus den Abschnitten **Kontexteingaben**, **Dateneingaben** und **Ausgaben**.

- Im Abschnitt **Kontexteingaben** können Sie den Formfaktor angeben und die benutzerdefinierte Komponente für jeden Formfaktor (Web, Tablet, Telefon) testen. Das ist besonders nützlich, wenn die benutzerdefinierte Komponente von einer bestimmten Formfaktorfunktion abhängig ist. In der kommenden Version Haben Sie die Möglichkeit, die Höhe und Breite anzugeben.
- Der Abschnitt **Dateineingabe** ist eine interaktive Benutzeroberfläche, in der alle Eigenschaften und ihre in der Manifestdatei definierten Typen/Typ-Gruppen angezeigt werden. Damit können Sie Pseudodaten für jede Eigenschaft eingeben. 
- Der **Ausgabe**-Bereich rendert die Ausgabe, wenn die `getOutputs`-Methode einer Komponente aufgerufen wird.  

     > [!div class="mx-imgBorder"]
     > ![Testumgebung 2](media/test-harness-2.png "Testumgebung 2")

> [!NOTE]
> Wenn Sie die Datei `manifest.xml` ändern oder weitere Eigenschaften erstellen möchten, müssen Sie den Debugging-Prozess erneut starten, bevor sie im Eingabebereich angezeigt werden.

## <a name="test-custom-components-with-mock-data"></a>Benutzerdefinierte Komponenten mit Pseudodaten testen

- Für Feldkomponenten können Sie den Eingabewert und den Typ für jede Eigenschaft eingeben, die in **ControlManifest.Input.xml** definiert ist (siehe unten)

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 2.5](media/test-harness-2.5.png "Testumgebung 2.5")

- Für Datasets können Sie eine CSV-Datei mit Testdaten laden. Sie kann manuell erstellt oder im CSV-Format direkt in Ihre Umgebung exportiert werden. Nachdem eine gültige CSV-Datei verfügbar ist, kann sie wie unten gezeigt geladen werden:

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 3](media/test-harness-3.png "Testumgebung 3")

- Wenn eine CSV-Datei geladen wurde, binden Sie jede Eigenschaft, die in **ControlManifest.Input.xml** definiert ist, an eine Spalte in der CSV. Dies geschieht, indem Sie die Spalte für jede Eigenschaft auswählen (siehe unten):

    > [!div class="mx-imgBorder"]
    > ![Testumgebung 4](media/test-harness-4.png "Testumgebung 4")

- Sofern keine Eigenschaften in der Datei **ControlManifest.Input.xml** definiert wurden, werden alle Spalten automatisch in die Testumgebung geladen.

   > [!div class="mx-imgBorder"]
   > ![Testumgebung 5](media/test-harness-5.png "Testumgebung 5")

## <a name="debug-custom-components-using-native-browsers"></a>Debuggen von benutzerdefinierten Komponenten mit systemeigenen Browser

Sie können die Debugging-Funktionen Ihres Browsers verwenden, um das Komponentenverhalten zu beobachten. Jeder Browser bietet ein Debugging-Tool, das Ihnen hilft, Ihren Code systemeigen im Browser zu debuggen. In der Regel können Sie das Debugging in Ihrem Browser aktivieren, indem Sie die Taste **F12** drücken, um das systemeigene Entwicklungstool anzuzeigen,d as für das Debugging verwendet wird.

Zum Beispiel in **Microsoft Edge**,

- Drücken Sie **F12**, um den Inspector zu öffnen.
- Klicken Sie auf Ihre Komponente
- In der oberen Leiste wechseln Sie zu **Debugger** und starten dann in der Suchleiste eine Suche nach dem in der Manifestdatei beschriebenen Komponentennamen. Geben Sie z. B. Ihren Komponentennamen als `Hello World component` ein.

     > [!div class="mx-imgBorder"]
     > ![debug-component](media/debug-control.png "Komponente debuggen")

> [!NOTE]
> Es ist immer eine gute Praxis, Haltepunkte in Lebenszyklusmethoden der Komponente festzulegen, z. B. `init` und `updateView`.

Sie können mit der Komponente auch lokal in Echtzeit interagieren und Elemente in DOM beobachten, indem Sie wie folgt einen Haltepunkt in der Registerkarte „Quellen“ festlegen:

> [!div class="mx-imgBorder"]
> ![debug-component](media/debug-control-1.png "Komponente 1 debuggen")

## <a name="fiddler-autoresponder"></a>Fiddler-AutoResponder

Verwenden Sie den Fiddler AutoResponder, um die benutzerdefinierten Komponenten schnell zu debuggen. Installieren Sie [Fiddler](https://www.telerik.com/download/fiddler) aus und folgen Sie den Schritten zum Konfigurieren von [AutoResponder](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)

### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
