---
title: Barrierefreiheits Eigenschaften für Canvas-apps | Microsoft-Dokumentation
description: Referenzinformationen zu Eigenschaften, z. b. TabIndex und ToolTip
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/26/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e1baf96ab96dc6fe783fccdf243c0ae4ba6d0c1d
ms.sourcegitcommit: b4df7d781cda50dfe2f6609f1cc4d2b531428b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70161255"
---
# <a name="accessibility-properties-for-canvas-apps"></a>Barrierefreiheits Eigenschaften für Canvas-apps

Hier geht es um die Konfiguration von Eigenschaften, die für Benutzer mit Sehschwäche als Hilfe für alternative Interaktionsmöglichkeiten mit Steuerelementen dienen.

## <a name="properties"></a>Eigenschaften

**AccessibleLabel**: Bezeichnung für Sprachausgaben. Durch einen leeren Wert für Bild-, Symbol- und Formsteuerelemente werden diese für die Bildschirmsprachausgabe unsichtbar und als Dekoration behandelt.

**Live** – gibt an, wie Sprachausgaben Änderungen an Inhalten ankündigen sollen. Nur im **[Label](control-text-box.md)** -Steuerelement verfügbar.

* Wenn diese Einstellung auf OFF festgelegt ist, werden keine Änderungen **von**der Bildschirmausgabe angekündigt.
* Wenn diese Einstellung auf " **höflich**" festgelegt ist, wird die Sprachausgabe beendet, bevor alle Änderungen angekündigt werden, die während der Sprachausgabe aufgetreten sind.
* Wenn diese Einstellung auf " **Durchsetzungs**fähig" festgelegt ist, unterbricht der sprach Leser alle Änderungen, die während der Sprachausgabe aufgetreten sind.

Erfahren Sie, wie Sie [dynamische Änderungen mit Live-Regionen ankündigen](../accessible-apps-live-regions.md).

**TabIndex** – bestimmt, ob das Steuerelement an der Tastaturnavigation teilnimmt.

Die Tastaturnavigation ist ein wichtiger Aspekt jeder app.  Für viele Geräte ist die Tastatur effizienter als die Verwendung von toucheingaben oder Maus Eingaben, und die Bildschirm Sprachausgabe ist für die visuelle Beeinträchtigung aktiviert.  Die Navigations Reihenfolge sollte:
- Spiegelung der visuellen Darstellung.
- Es ist nur ein Tabstopp bei interaktiven Steuerelementen vorhanden.
- Befolgen Sie entweder eine intuitive und dann die "Z"-Reihenfolge oder ein-nach-unten und dann über die "umgekehrte N"-Reihenfolge.

Die oben aufgeführten Anforderungen werden mit den Standardwerten für **TabIndex** erfüllt, und es wird empfohlen, Sie nicht zu ändern.  Der Standardwert ist, was die meisten Benutzer visuell erwarten, und funktioniert gut mit einer Bildschirm Sprachausgabe.  Es kann jedoch vorkommen, dass Sie die Standardeinstellung überschreiben möchten.  Verwenden Sie die **TabIndex** -Eigenschaft und das [ **Erweiterte Gruppen** Steuer](https://powerapps.microsoft.com/en-us/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/) Element (experimentell), um Anpassungen an der Navigations Reihenfolge vorzunehmen.  

Die **TabIndex** -Eigenschaft verfügt über zwei Empfohlene Werte:

| TabIndex-Wert | Verhalten | Standardwert für |
|----------------|----------|-------------|
| 0 | Das Steuerelement ist Teil der Tastaturnavigation. | [**Schaltfläche**](control-button.md), [**Text Eingabe**](control-text-input.md), Kombinations [**Feld**](control-combo-box.md)und andere in der Regel interaktive Steuerelemente. |
| &minus;1 | Das Steuerelement ist nicht Teil der Tastaturnavigation. | [**Bezeichnung**](control-text-box.md), [**Bild**](control-image.md), [**Symbol**](control-shapes-icons.md)und andere in der Regel nicht interaktive Steuerelemente. |

Die Navigations Reihenfolge erfolgt in der Regel von links nach rechts und von oben nach unten in einem "Z"-Muster. Die Reihenfolge basiert auf den **X** -und **Y** -Eigenschafts Werten der Steuerelemente. Wenn Steuerelemente dynamisch auf dem Bildschirm verschoben werden, z. b. Wenn eine Formel für **X** oder **Y** auf Grundlage eines Timers oder eines anderen Steuer Elements vorhanden ist, wird die Navigations Reihenfolge ebenfalls dynamisch geändert.

Verwenden Sie das [ **Erweiterte Gruppen** Steuer](https://powerapps.microsoft.com/en-us/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/) Element (experimentell), um Steuerelemente zu bündeln, die zusammengeführt werden sollen, oder um Spalten in einem "umgekehrten N"-Muster zu erstellen.  Oben im folgenden Beispiel sind die namens Felder in einem erweiterten Gruppen Steuerelement enthalten, das bewirkt, dass die Navigation vor dem Verschieben fortgesetzt wird.  Am unteren Rand des Beispiels werden keine Gruppen Steuerelemente verwendet, und die Navigation verläuft über und dann wie gewohnt, was bei den Steuerelement Gruppierungen nicht intuitiv ist. 

![Animation, die ein erweitertes Gruppen Steuerelement anzeigt, wodurch die Navigation innerhalb einer Gruppe vor dem Verschieben fortgesetzt wird](media/properties-accessibility/enhanced-group.gif)

Auf ähnliche Weise wird beim Durchlaufen von Containern wie [**Form**](control-form-detail.md)- und [**Gallery**](control-gallery.md)-Steuerelementen mit der TAB-Taste durch alle Elemente des Containers navigiert, bevor mit dem nächsten Steuerelement außerhalb des Containers fortgefahren wird.  

Steuerelemente, die den **Visible** -Eigenschafts Wert *false* oder den **DisplayMode** -Eigenschafts Wert **deaktiviert** haben, sind nicht in der Navigation enthalten.  

Wenn Sie einen Browser verwenden, wechselt die Navigation vom letzten Steuerelement auf dem Bildschirm zu den integrierten Steuerelementen des Browsers (z. b. die URL-Adresse).  

> [!WARNING]
> Vermeiden Sie **TabIndex** -Werte, die größer als 0 sind. Letztendlich werden Steuerelemente in HTML gerendert, wobei auch das [W3C gewarnt hat](https://www.w3.org/TR/wai-aria-practices/#kbd_general_between) : "Autoren werden dringend darauf hingewiesen, dass diese Werte nicht verwendet werden." Viele HTML-Tools warnen bei Werten, die größer als 0 (null) sind, ebenso wie die [App](../accessibility-checker.md) -Prüfung, wenn Sie die Reihenfolge der Bildschirmelemente überprüft.  Alles aus gutem Grund: die Verwendung von **TabIndex** auf diese Weise kann sehr schwierig sein, und es kann Hilfstechnologien wie Bildschirm Sprachausgaben unbrauchbar machen.
> 
> Wenn Steuerelemente mit **TabIndex** größer als 0 (null) vorhanden sind, navigieren Benutzer zu Steuerelementen mit steigenden **TabIndex** -Werten (1, dann 2 usw.). Wenn Benutzer alle Steuerelemente mit positiven **TabIndex** -Werten navigiert haben, navigieren Sie schließlich zu den Steuerelementen mit dem **TabIndex** 0, einschließlich der integrierten Steuerelemente des Browsers. Wenn mehrere Steuerelemente mit dem gleichen **TabIndex**vorhanden sind, bestimmt die **X** -und **Y** -Position ihre relative Reihenfolge.





