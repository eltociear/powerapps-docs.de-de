---
title: Funktionen „Back“ und „Navigate“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Back“ und „Navigate“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0033d0a2d7473e6aaeac1e8533f62873e0d2f49a
ms.sourcegitcommit: c52c1869510a9a37d9f7b127e06f07583529588b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670921"
ms.PowerAppsDecimalTransform: true
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Funktionen „Back“ und „Navigate“ in PowerApps
Ändern, welcher Bildschirm angezeigt wird

## <a name="overview"></a>Übersicht
Die meisten Apps umfassen mehrere Bildschirme.  Verwenden Sie die Funktionen **Back** und **Navigate**, um zu ändern, welcher Bildschirm angezeigt wird. Legen Sie z.B. die **[OnSelect](../controls/properties-core.md)**-Eigenschaft einer Schaltfläche auf eine Formel fest, die eine **Navigate**-Funktion enthält, wenn Sie einen anderen Bildschirm anzeigen möchten, wenn ein Benutzer diese Schaltfläche auswählt. In dieser Formel können Sie einen visuellen Übergang, wie z.B. **Fade** angeben, um zu steuern, wie ein Bildschirm zu einem anderen Bildschirm wechselt.  

Die Funktionen **Back** und **Navigate** ändern nur, welcher Bildschirm angezeigt wird. Bildschirme, die momentan nicht angezeigt werden, werden weiterhin im Hintergrund ausgeführt. Sie können Formeln erstellen, die sich auf Eigenschaften von Steuerelementen auf einem anderen Bildschirm beziehen. Beispielsweise kann ein Benutzer den Wert des Schiebereglers auf einem Bildschirm ändern, zu einem anderen Bildschirm navigieren, der diesen Wert in einer Formel verwendet, und sehen, wie sich dies darauf auswirkt, was auf dem neuen Bildschirm geschieht.  Der Benutzer kann dann wieder zum ursprünglichen Bildschirm zurück navigieren und sehen, dass der Wert des Schiebereglers beibehalten wurde.

[Kontextvariablen](../working-with-variables.md#use-a-context-variable) werden ebenfalls beibehalten, wenn ein Benutzer zwischen Bildschirmen navigiert. Sie können **Navigate** verwenden, um eine oder mehrere Kontextvariablen für den Bildschirm festzulegen, den die Formel anzeigen wird. Dies ist die einzige Möglichkeit, von außerhalb des Bildschirms eine Kontextvariable festzulegen. Sie können diesen Ansatz verwenden, um Parameter an einen Bildschirm zu übergeben. Wenn Sie ein anderes Programmiertool verwendet haben, ähnelt diese Vorgehensweise der Übergabe von Parametern an Prozeduren.

## <a name="description"></a>Beschreibung
### <a name="back"></a>Back
Die Funktion **Back** zeigt den Bildschirm an, der zuletzt angezeigt wurde. Sie geben keine Argumente für diese Funktion an.

### <a name="navigate"></a>Navigate
Geben Sie im ersten Argument den Namen des Bildschirms an, der angezeigt werden soll.  

 Geben Sie im zweiten Argument an, wie der alte Bildschirm auf den neuen Bildschirm wechselt:

| „Transition“-Argument | Beschreibung | Demo |
| --- | --- | --- |
| **ScreenTransition.Cover** |Der neue Bildschirm gleitet in die Ansicht, Verschieben von rechts nach links, um den aktuellen Bildschirm abdeckt. | ![Bildschirm Cover übergangsanimation](media/function-navigate/cover.gif) |
| **ScreenTransition.CoverRight** |Der neue Bildschirm Folien in der Ansicht, die Verschieben von links nach rechts, um den aktuellen Bildschirm abdeckt. | ![Bildschirm Cover rechten übergangsanimation](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |Der aktuelle Bildschirm wird ausgeblendet entfernt, um den neuen Bildschirm anzuzeigen. | ![Animation zum Ausblenden von Bildschirm Übergang](media/function-navigate/fade.gif) |
| **ScreenTransition.None** (Standard) |Der neue Bildschirm wird schnell im aktuellen Fenster ersetzt. | ![Bildschirm Übergang keine Animation](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | Der aktuelle Bildschirm wird ausgeblendet, Verschieben von rechts nach links, um den neuen Bildschirm zu gewinnen. | ![Bildschirmübergang aufdecken animation](media/function-navigate/uncover.gif) |
| **ScreenTransition.UnCoverRight** | Die aktuellen Bildschirm Folien aus der Sicht, die Verschieben von links nach rechts, um den neuen Bildschirm zu gewinnen. | ![Bildschirmübergang nach rechts Animation aufdecken.](media/function-navigate/uncoverright.gif) |

Sie können **Navigate** verwenden, um Kontextvariablen des neuen Bildschirms zu erstellen oder zu aktualisieren. Als optionales drittes Argument übergeben Sie einen [Datensatz](../working-with-tables.md#records), der den Kontextvariablennamen als [Spaltennamen](../working-with-tables.md#columns) sowie den neuen Wert für die Kontextvariable enthält.  Dieser Datensatz ist identisch mit dem Datensatz, den Sie mit der **[UpdateContext](function-updatecontext.md)**-Funktion verwenden.

Legen Sie die **[OnHidden](../controls/control-screen.md)**-Eigenschaft des alten Bildschirms, die **[OnVisible](../controls/control-screen.md)**-Eigenschaft des neuen Bildschirms oder beide fest, um während des Übergangs zusätzliche Änderungen vorzunehmen. Die **App.ActiveScreen**-Eigenschaft wird aktualisiert, um die Änderung zu übernehmen.

**Back** gibt in der Regel **TRUE** zurück, gibt jedoch **FALSE** zurück, wenn sich der Benutzer auf dem ersten angezeigten Bildschirm befindet und es keinen vorherigen Bildschirm gibt.  **Navigate** gibt in der Regel **TRUE** zurück, gibt jedoch **FALSE** zurück, wenn ein Problem mit einem der Argumente vorliegt.

Sie können diese Funktionen nur in einer [Verhaltensformel](../working-with-formulas-in-depth.md) verwenden.

## <a name="syntax"></a>Syntax
**Back**()

**Navigieren Sie**( *Bildschirm* [; *Übergang* [; *kontextaktualisierungs-Datensatz* ]])

* *Bildschirm*: Erforderlich. Der anzuzeigende Bildschirm.
* *Übergang* : Optional.  Der visuelle Übergang, der zwischen dem aktuellen Bildschirm und dem nächsten Bildschirm verwendet werden soll. Weitere Informationen finden Sie in der Liste der gültigen Werte für dieses Argument weiter oben in diesem Thema. Der Standardwert ist **keine**.
* *Kontextaktualisierungs-Datensatz*: Optional.  Ein Datensatz, der den Namen mindestens einer Spalte und einen Wert für jede Spalte enthält. Dieser Datensatz aktualisiert die Kontextvariablen des neuen Bildschirms wie bei der Übergabe an die **[UpdateContext](function-updatecontext.md)**-Funktion.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Navigate( Details )** |Zeigt den **Detailbildschirm** ohne Übergang oder Änderung des Werts einer Kontextvariablen an. |Der **Detailbildschirm** erscheint schnell. |
| **Navigate( Details; ScreenTransition.Fade )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an.  Kein Wert einer Kontextvariablen wird geändert. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. |
| **Navigate( Details; ScreenTransition.Fade; {&nbsp;ID:&nbsp;12&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an und aktualisiert den Wert der Kontextvariable **ID** auf **12**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen, und die Kontextvariable **ID** auf diesem Bildschirm wird auf **12** festgelegt. |
| **Navigate( Details; ScreenTransition.Fade; {&nbsp;ID:&nbsp;12&nbsp;;&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an. Aktualisiert den Wert der Kontextvariable **ID** auf **12** und aktualisiert den Wert der Kontextvariable **Shade** auf **Color.Red**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. Die Kontextvariable **ID** auf dem **Detailbildschirm** wird auf **12** festgelegt, und die Kontextvariable **Shade** wird auf **Color.Red** festgelegt. Wenn Sie die **Fill**-Eigenschaft eines Steuerelements auf dem **Detailbildschirm** auf **Shade** festlegen, würde dieses Steuerelement rot angezeigt werden. |

### <a name="step-by-step"></a>Schritt für Schritt
1. Benennen Sie den Standardbildschirm **DefaultScreen**, fügen Sie eine Bezeichnung zu ihm hinzu, und legen Sie die **[Text](../controls/properties-core.md)**-Eigenschaft dieser Bezeichnung so fest, dass diese **Default** anzeigt.
2. Fügen Sie einen Bildschirm hinzu, und nennen Sie diesen **AddlScreen**.
3. Fügen Sie eine Bezeichnung zu **AddlScreen** hinzu, und legen Sie die **[Text](../controls/properties-core.md)**-Eigenschaft der Bezeichnung so fest, dass diese **Addl** anzeigt.
4. Fügen Sie eine Schaltfläche zu **AddlScreen** hinzu, und legen Sie ihre **[OnSelect](../controls/properties-core.md)**-Eigenschaft auf diese Formel fest:<br>**Navigate(DefaultScreen; ScreenTransition.Fade)**
5. Drücken Sie von **AddlScreen** aus auf F5, und wählen Sie anschließend die Schaltfläche aus.<br>**DefaultScreen** über einem ausblendübergang angezeigt wird.

[Ein weiteres Beispiel](../add-screen-context-variables.md)

