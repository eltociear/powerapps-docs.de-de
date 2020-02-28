---
title: Verhaltens Formeln für Komponenten | Microsoft-Dokumentation
description: Führen Sie eine oder mehrere Tasks in der Canvas-App aus, wenn eine komponentenbasierte Aktion auftritt.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 28ea432e5d09684029f104d69f593e24dcc4cc14
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77910977"
---
# <a name="behavior-formulas-for-components"></a>Verhaltens Formeln für Komponenten

> [!IMPORTANT]
> Dieses Feature befindet sich noch in der öffentlichen Vorschau Phase. Weitere Informationen finden Sie unter [Experimentelle Features und Previewfunktionen](working-with-experimental.md).

Geben Sie mindestens eine [Verhaltens Formel](working-with-formulas-in-depth.md) an, die ausgeführt wird, wenn ein Ereignis eine Änderung in Komponenten Instanzen auslöst. 

Wenn Sie z. b. die **onreset** -Eigenschaft einer Komponente auf eine oder mehrere Formeln festlegen, die die Initialisierung durchführen, löschen Sie die Eingabe. Und setzen Werte zurück, wenn die **Reset** -Funktion auf den Komponenten Instanzen ausgeführt wird.

## <a name="onreset"></a>OnReset

Wählen Sie bei ausgewähltem Komponenten Master in der Dropdown Liste mit den Eigenschaften (auf der linken Seite der Bearbeitungs Leiste) die Option **onreset** aus, und geben Sie dann eine oder mehrere Formeln ein.

> [!div class="mx-imgBorder"]
> ![onreset-Beispiel](./media/component-behavior/example-onreset.png)

Zum Testen von **onreset**konfigurieren Sie ein-Steuerelement, um die Komponente zurückzusetzen. Legen Sie z. b. die **onselect** -Eigenschaft einer Schaltfläche auf diese Formel fest: **Reset**(*componentname*).

### <a name="example---reset-timer"></a>Beispiel: Zurücksetzen des Timers

> [!div class="mx-imgBorder"]
> ![onreset-Beispiel](./media/component-behavior/Resettimer.gif)

In dieser Zeitauswahl Komponente werden zwei Variablen zum Anzeigen der Zeit _selectedHour und _selectedMinute verwendet. Wenn die Auswahl zurückgesetzt wird, sollten diese Variablen auf einen Standardwert zurückgesetzt werden, beispielsweise 12:12.  Die onreset-Eigenschaft für die Komponente weist die folgende Formel auf: **Set (_selectedHour, 12); Set (_selectedMinute, 12)**

Wechseln Sie zum Zurücksetzen des zurück Setzens zu einem Bildschirm, und fügen Sie eine Instanz der Komponente ein. Fügen Sie eine Schaltfläche hinzu, und konfigurieren Sie onselect der Schaltfläche, um **Reset (TimerComponent_instance)** aufzurufen und onreset aufzurufen.

> [!div class="mx-imgBorder"]
> Schaltfläche zum Zurücksetzen ![](./media/component-behavior/reset-button.png)

## <a name="update-onreset-using-custom-property"></a>Aktualisieren von onreset mithilfe der benutzerdefinierten Eigenschaft

Neben dem Zurücksetzen einer Komponenteninstanz von außerhalb der Komponente gibt es eine andere Methode, um die onreset-Methode aus dem Inneren zu initiieren. "**Onreset bei Wertänderungen erhöhen**" ist eine Option beim Erstellen einer benutzerdefinierten Eingabe Eigenschaft. Außerdem ermöglicht es den Wertänderungen dieser Eigenschaft, das onreset der Komponente zu initiieren. Diese Methode ist so konzipiert, dass Sie den Standardwert problemlos festlegen und zurücksetzen kann. 

> ![Onreset-Beispiel](./media/component-behavior/property-trigger.png)

### <a name="example"></a>Beispiel

> [!div class="mx-imgBorder"]
> ![onreset-Beispiel](./media/component-behavior/updateordernumber2.gif)

Das obige Beispiel zeigt das Überprüfen von Bestellnummern und das Aktualisieren der Zahlen. Die numerische Komponente "nach oben" und "nach unten" wird verwendet, um die Anzahl der Bestellungen zu erhöhen Wenn Sie den Katalog auf der linken Seite auswählen, wird die Standard Anzahl der numerischen und Downstreamkomponenten zurückgesetzt, um die Bestellnummer des ausgewählten Tools anzuzeigen. "**Onreset bei Wertänderungen**zurücksetzen" ermöglicht es, den Standardwert zurückzusetzen, wenn die Eingabe geändert wird. 

Aktivieren Sie zu diesem Zweck die Option "**onreset bei Wertänderungen zurücksetzen**" der Standardeingabe Eigenschaft. Das **onreset** der Komponente ist auf Set festgelegt **(_numericValue, ' numeric up '. DefaultValue)** . _numericValue ist die Variable zum Speichern des Werts des aktuellen Auftragswerts. Und legen Sie die **Standardeinstellung** des Texteingabe-Steuer Elements auf **if (isblank (_numericValue), ' numeric on Down ' fest. DefaultValue, _numericValue)** . 

### <a name="see-also"></a>Siehe auch

- [Übersicht über Canvas-App-Komponenten](create-component.md)
- [Bibliothek der Canvas-App-Komponenten](component-library.md)
