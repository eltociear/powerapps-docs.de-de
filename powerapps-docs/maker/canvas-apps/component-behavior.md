---
title: Verhaltens Formeln für Komponenten | Microsoft-Dokumentation
description: Löst eine APP aus, um eine oder mehrere Tasks auszuführen, wenn eine komponentenbasierte Aktion auftritt.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 9/30/2019
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: baf7e74581819b3ea21542f30f96a0a6f517c0d5
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "71705047"
---
# <a name="behavior-formulas-for-components"></a>Verhaltens Formeln für Komponenten

> [!IMPORTANT]
> Diese Funktion ist in der Standardeinstellung immer noch experimentell und deaktiviert. Weitere Informationen finden Sie unter [experimentelle Features und Vorschau Features](working-with-experimental.md).

Geben Sie mindestens eine [Verhaltens Formel](working-with-formulas-in-depth.md) an, die ausgeführt wird, wenn ein Ereignis eine Änderung in Komponenten Instanzen auslöst. Legen Sie z. b. die **onreset** -Eigenschaft einer Komponente auf eine oder mehrere Formeln fest, die die Initialisierung durchführen, die Eingabe löschen und Werte zurücksetzen, wenn die **Reset** -Funktion auf den Komponenten Instanzen ausgeführt wird.

## <a name="onreset"></a>OnReset

Wählen Sie bei ausgewähltem Komponenten Master in der Dropdown Liste mit den Eigenschaften (auf der linken Seite der Bearbeitungs Leiste) die Option **onreset** aus, und geben Sie dann eine oder mehrere Formeln ein.

> [!div class="mx-imgBorder"]
> ![onreset-Beispiel](./media/component-behavior/example-onreset.png)

Zum Testen von **onreset**konfigurieren Sie ein-Steuerelement, um die Komponente zurückzusetzen. Legen Sie z. b. die **onselect** -Eigenschaft einer Schaltfläche auf diese Formel fest: **Reset**(*componentname*).

### <a name="example---reset-timer"></a>Beispiel: Zurücksetzen des Timers

> [!div class="mx-imgBorder"]
> ![onreset-Beispiel](./media/component-behavior/Resettimer.gif)

In dieser Zeitauswahl Komponente werden zwei Variablen verwendet, um die Uhrzeit _selectedHour und _selectedMinute anzuzeigen. Wenn die Auswahl zurückgesetzt wird, sollten diese Variablen auf einen Standardwert zurückgesetzt werden, beispielsweise 12:12.  Die onreset-Eigenschaft für die Komponente weist die folgende Formel auf: **Set (_selectedHour, 12); Set (_selectedMinute, 12)**

Wechseln Sie zum Zurücksetzen des zurück Setzens zu einem Bildschirm, und fügen Sie eine Instanz der Komponente ein. Fügen Sie eine Schaltfläche hinzu, und konfigurieren Sie onselect der Schaltfläche, sodass **Reset (TimerComponent_instance)** aufgerufen wird, um onreset aufzurufen

> [!div class="mx-imgBorder"]
> Schaltfläche zum Zurücksetzen ![](./media/component-behavior/reset-button.png)

## <a name="update-onreset-using-custom-property"></a>Aktualisieren von onreset mithilfe der benutzerdefinierten Eigenschaft

Neben dem Zurücksetzen einer Komponenteninstanz von außerhalb der-Komponente gibt es eine weitere-Methode, um die onreset-Methode von innen aus zu initiieren. Die Option "**onreset bei Wertänderungen zurücksetzen**" ist eine Option beim Erstellen einer benutzerdefinierten Eingabe Eigenschaft und ermöglicht, dass der Wertänderungen dieser Eigenschaft das onreset der Komponente auslöst. Diese Methode ist so konzipiert, dass Sie den Standardwert problemlos festlegen und zurücksetzen kann. 

> ![Onreset-Beispiel](./media/component-behavior/property-trigger.png)

### <a name="example"></a>Beispiel

> [!div class="mx-imgBorder"]
> ![onreset-Beispiel](./media/component-behavior/updateordernumber2.gif)

Dies ist ein Beispiel für das Überprüfen von Bestellnummern und das Aktualisieren der Zahlen. Die numerische Komponente "nach oben" und "nach unten" wird verwendet, um die Anzahl der Bestellungen zu erhöhen Wenn Sie den Katalog auf der linken Seite auswählen, wird die Standard Anzahl der numerischen und Downstreamkomponenten zurückgesetzt, um die Bestellnummer des ausgewählten Tools anzuzeigen. "**Onreset bei Wertänderungen**zurücksetzen" ermöglicht es, den Standardwert zurückzusetzen, wenn die Eingabe geändert wird. 

Aktivieren Sie zu diesem Zweck die Option "**onreset bei Wertänderungen zurücksetzen**" der Standardeingabe Eigenschaft. Das **onreset** der Komponente ist auf **Set (_numericValue, ' numeric on Down ') festgelegt. DefaultValue)** . _numericValue ist die Variable, die den Wert des aktuellen Auftragswerts speichert. Und legen Sie die **Standardeinstellung** des Texteingabe-Steuer Elements auf **if (isblank (_numericValue), ' numeric on Down ' fest. DefaultValue, _numericValue)** . 
