---
title: Funktion „SetProperty“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax zur Funktion „SetProperty“ in Power Apps Test Studio
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dac65ed25a9e286b056cf3c1408554ca79ea3e11
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541150"
ms.PowerAppsDecimalTransform: true
---
# <a name="setproperty-function-in-power-apps-test-studio"></a>Funktion „SetProperty“ in Power Apps Test Studio

Die Funktion „SetProperty“ simuliert Interaktionen mit Eingabesteuerelementen, bei denen der Benutzer einen Wert für das Steuerelement eingibt oder festlegt. Diese Funktion ist nur verfügbar, wenn Sie Tests in Power Apps Test Studio schreiben. Die folgenden Eigenschaften können mit der Funktion „SetProperty“ festgelegt werden.

## <a name="syntax"></a>Syntax

*SetProperty(Steuerelementeigenschaft, Wert)*

- *Steuerelementeigenschaft:* erforderlich. Dies ist die Steuerelementeigenschaft, die für den Benutzer festgelegt werden soll.
- *Wert*: Erforderlich. Dies ist der Wert der Eigenschaft, die für den Benutzer festgelegt werden soll. 

## <a name="examples"></a>Beispiele

| Steuerung   | Eigenschaft  | Beispielausdruck
| :- | :- | :-
| TextInput | Text  | ```SetProperty(TextInput1.Text; "Sample text")```
| RichTextEditor    | HtmlText  | ```SetProperty(RichTextEditor1.HtmlText; "<p>Sample text</p>")```
| Umschalten    | Wert | ```SetProperty(Toggle1.Value; false)```
| Checkbox  | Wert | ```SetProperty(Checkbox1.Value; false)```
| Schieberegler    | Wert | ```SetProperty(Slider1.Value; 10)```
| Rating    | Wert | ```SetProperty(Rating1.Value; 5)```
| DatePicker    | SelectedDate  | ```SetProperty(DatePicker1.SelectedDate; Date(2020;3;10))```
| Radio | Ausgewählt  | ```SetProperty(Radio1.Selected; "Yes")```
| Radio | SelectedText | ```SetProperty(Radio1.SelectedText; "Yes")```
| Dropdown | Ausgewählt | ```SetProperty(Dropdown1.Selected; {Value:"Sample value"})```
| Dropdown | SelectedText | ```SetProperty(Dropdown1.SelectedText; {Value:"Sample value"})```
| Combobox | Ausgewählt | ```SetProperty(Dropdown1.Selected; {Value:"Sample value"})```
| Combobox | SelectedItems | ```SetProperty(ComboBox1.SelectedItems; Table({Value:"Sample value"};({Value:"Sample value"}))```
| Listenfeld | Ausgewählt | ```SetProperty(Listbox1.Selected; {'Value':"Sample value"})```
| Listenfeld | SelectedItems | ```SetProperty(Listbox1.SelectedItems; Table({Value:"Sample value"};({Value:"Sample value"}))```

### <a name="see-also"></a>Siehe auch

[Test Studio: Übersicht](../test-studio.md) <br>
[Arbeiten mit Test Studio](../working-with-test-studio.md)