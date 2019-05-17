---
title: Debuggen von benutzerdefinierten Komponenten | MicrosoftDocs
description: So debuggen Sie ein benutzerdefinierte Steuerelement mithilfe von Fiddler und Native-Debugging
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
---
# <a name="debugging-csutom-components"></a>Debuggen von benutzerdefinierten Komponenten

Nachdem Sie mit der Implementierung Ihres benutzerdefinierten Steuerelements fertig sind, führen Sie den folgenden Befehl aus, um den Debugging-Prozess zu starten: `npm start`

> [!NOTE]
> Heute können Sie Ihr Feldsteuerelement nur darstellen, aber Dataset-Unterstützung ist in Kürze verfügbar.

> [!div class="mx-imgBorder"]
> ![local-host](media/local-host.png "lokaler Host")

Wie in der obigen Abbildung dargestellt wird das Browserfenster mit 3 Abschnitten geöffnet. Das Steuerelement wird im linken Bereich gerendert, wohingegen der rechte Bereich aus den Abschnitten **Eingaben** und **Ausgaben** besteht.

  - Der **Eingabe**-Bereich ist eine interaktive Benutzeroberfläche, in der alle Eigenschaften und ihre im Manifest definierten Typen/Typ-Gruppen angezeigt werden. Damit können Sie Pseudodaten für jede Eigenschaft eingeben. 
  - Der Abschnitt **Ausgaben** rendert die Ausgabe, wenn eine `getOutputs`-Methode des Steuerelements aufgerufen wird.  
 
> [!NOTE]
> Wenn Sie `manifest.xml` ändern oder weitere Eigenschaften erstellen möchten, müssen Sie den Debugging-Prozess erneut starten, bevor sie im Eingabebereich angezeigt werden.

Da Sie Scheindaten eingeben, können Sie die Debugging-Funktionen des Browsers verwenden, um das Verhalten des Steuerelements zu beobachten. Jeder Browser bietet ein Debugging-Tool, das Ihnen hilft, Ihren Code systemeigen im Browser zu debuggen. In der Regel können Sie das Debugging in Ihrem Browser aktivieren, indem Sie die Taste **F12** drücken, um das systemeigene Entwicklungstool anzuzeigen,d as für das Debugging verwendet wird.

Beispiel: Bei **Microsoft Edge**

- Drücken Sie **F12**, um den Inspector zu öffnen.
- Klicken Sie auf das Steuerelement
- Wechseln Sie auf der oberen Leiste auf **Debugger** und starten Sie die Suche nach dem Namen des Steuerelements, der in der Manifestdatei in der Suchenleiste beschrieben wird. Geben Sie z. B. den Namen Ihres Steuerelements ein, z. B. `Hello World Control`.

     > [!div class="mx-imgBorder"]
     > ![debug-control](media/debug-control.png "Debugging-Steuerelement")

> [!NOTE]
> Es ist immer gut, Haltepunkte in den Lebenszyklusmethoden des Steuerelements festzulegen, z. B: `init` und `updateView`

Sie können auch lokal mit dem Steuerelement in Echtzeit interagieren und Elemente im DOM beobachten, indem Sie wie folgt den folgenden Haltepunkt in der Quellen-Registerkarte festlegen

> [!div class="mx-imgBorder"]
> ![local-host](media/local-host.png "lokaler Host")

> [!div class="mx-imgBorder"]
> ![debug-control](media/debug-control-1.png "Debugging-Steuerelement 1")

## <a name="fiddler-autoresponder"></a>Fiddler-AutoResponder

Verwenden Sie den Fiddler AutoResponder, um die benutzerdefinierten Komponenten schnellen zu debuggen. Installieren Sie [Fiddler](https://www.telerik.com/download/fiddler) aus und folgen Sie den Schritten zum Konfigurieren von [AutoResponder](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)

### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)