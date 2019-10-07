---
title: Funktionen „Back“ und „Navigate“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Back“ und „Navigate“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/16/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8f63321b128214d14cd2f4e521d7cc1b85c7b98f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984483"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Funktionen „Back“ und „Navigate“ in PowerApps

Ändern, welcher Bildschirm angezeigt wird

## <a name="overview"></a>Übersicht

Die meisten Apps umfassen mehrere Bildschirme.  Verwenden Sie die Funktionen **Back** und **Navigate**, um zu ändern, welcher Bildschirm angezeigt wird. Legen Sie z.B. die **[OnSelect](../controls/properties-core.md)** -Eigenschaft einer Schaltfläche auf eine Formel fest, die eine **Navigate**-Funktion enthält, wenn Sie einen anderen Bildschirm anzeigen möchten, wenn ein Benutzer diese Schaltfläche auswählt. In dieser Formel können Sie einen visuellen Übergang, wie z.B. **Fade** angeben, um zu steuern, wie ein Bildschirm zu einem anderen Bildschirm wechselt.  

Die Funktionen **Back** und **Navigate** ändern nur, welcher Bildschirm angezeigt wird. Bildschirme, die momentan nicht angezeigt werden, werden weiterhin im Hintergrund ausgeführt. Sie können Formeln erstellen, die auf Eigenschaften von Steuerelementen auf anderen Bildschirmen verweisen. Beispielsweise kann ein Benutzer den Wert eines Schiebereglers auf einem Bildschirm ändern, zu einem anderen Bildschirm navigieren, der diesen Wert in einer Formel verwendet, und die Auswirkungen auf das Verhalten im neuen Bildschirm ermitteln. Der Benutzer kann dann zurück zum ursprünglichen Bildschirm navigieren und sich vergewissern, dass der Schieberegler seinen Wert beibehalten hat.

[Kontextvariablen](../working-with-variables.md#use-a-context-variable) werden ebenfalls beibehalten, wenn ein Benutzer zwischen Bildschirmen navigiert. Sie können **Navigate** verwenden, um eine oder mehrere Kontextvariablen für den Bildschirm festzulegen, den die Formel anzeigen wird. Dies ist die einzige Möglichkeit, von außerhalb des Bildschirms eine Kontextvariable festzulegen. Sie können diesen Ansatz verwenden, um Parameter an einen Bildschirm zu übergeben. Wenn Sie ein anderes Programmiertool verwendet haben, ähnelt diese Vorgehensweise der Übergabe von Parametern an Prozeduren.

Sie können eine der beiden Funktionen nur innerhalb einer [Verhaltens Formel](../working-with-formulas-in-depth.md)verwenden.

## <a name="navigate"></a>Navigate

Geben Sie im ersten Argument den Namen des Bildschirms an, der angezeigt werden soll.  

 Geben Sie im zweiten Argument an, wie der alte Bildschirm auf den neuen Bildschirm wechselt:

| „Transition“-Argument | Beschreibung | Tions |
| --- | --- | --- |
| **ScreenTransition.Cover** |Der neue Bildschirm wird in die Ansicht verschoben, von rechts nach links, um den aktuellen Bildschirm abzudecken. | ![Animation des Bildschirm Übergangs abdecken](media/function-navigate/cover.gif) |
| **Screentransition. coverright** |Der neue Bildschirm wird in die Ansicht verschoben, von links nach rechts, um den aktuellen Bildschirm abzudecken. | ![Bildschirm Übergangs Abdeckung für die richtige Animation](media/function-navigate/coverright.gif) |
| **ScreenTransition.Fade** |Der aktuelle Bildschirm wird ausgeblendet, um den neuen Bildschirm anzuzeigen. | ![Animation für Bildschirm Übergänge ausblenden](media/function-navigate/fade.gif) |
| **Screentransition. None** (Standard) |Der neue Bildschirm ersetzt schnell den aktuellen Bildschirm. | ![Bildschirm Übergang keine Animation](media/function-navigate/none.gif) |
| **ScreenTransition.UnCover** | Der aktuelle Bildschirm wird von rechts nach links verschoben, um den neuen Bildschirm anzuzeigen. | ![Bildschirm Übergang zum Entdecken der Animation](media/function-navigate/uncover.gif) |
| **Screentransition. uncoverright** | Der aktuelle Bildschirm wird von links nach rechts verschoben, um den neuen Bildschirm anzuzeigen. | ![Bildschirm Übergang mit rechter Animation](media/function-navigate/uncoverright.gif) |

Sie können **Navigate** verwenden, um Kontextvariablen des neuen Bildschirms zu erstellen oder zu aktualisieren. Als optionales drittes Argument übergeben Sie einen [Datensatz](../working-with-tables.md#records), der den Kontextvariablennamen als [Spaltennamen](../working-with-tables.md#columns) sowie den neuen Wert für die Kontextvariable enthält.  Dieser Datensatz ist identisch mit dem Datensatz, den Sie mit der **[UpdateContext](function-updatecontext.md)** -Funktion verwenden.

Legen Sie die **[OnHidden](../controls/control-screen.md)** -Eigenschaft des alten Bildschirms, die **[OnVisible](../controls/control-screen.md)** -Eigenschaft des neuen Bildschirms oder beide fest, um während des Übergangs zusätzliche Änderungen vorzunehmen. Die **App.ActiveScreen**-Eigenschaft wird aktualisiert, um die Änderung zu übernehmen.

**Navigate** gibt normalerweise **true** zurück, gibt jedoch **false** zurück, wenn ein Fehler aufgetreten ist.

## <a name="back"></a>Back

Die **Back** -Funktion kehrt zum Bildschirm zurück, der zuletzt angezeigt wurde.

Für jeden **Navigate** -Befehl verfolgt die APP den angezeigten Bildschirm und den Übergang. Sie können nachfolgende **Back** -Aufrufe verwenden, um den Bildschirm zurückzugeben, der beim Starten der app durch den Benutzer aufgetreten ist.

Wenn die **Back** -Funktion ausgeführt wird, wird standardmäßig der umgekehrte Übergang verwendet. Wenn z. b. ein Bildschirm durch den Übergang " **coverright** " angezeigt wird **, verwendet** Back die Rückgabe von " **zurück** " (auf der linken Seite).  **Fade** und **None** sind Ihre eigenen inversen. Übergeben Sie ein optionales Argument an **zurück** , um einen bestimmten Übergang zu erzwingen.

**Back** gibt normalerweise **true** zurück, gibt jedoch **false** zurück, wenn der Benutzer seit dem Starten der APP nicht zu einem anderen Bildschirm navigiert hat

## <a name="syntax"></a>Syntax

**Zurück**([ *Übergang* ])

* *Übergang* : optional. Der visuelle Übergang, der zwischen dem aktuellen Bildschirm und dem vorherigen Bildschirm verwendet werden soll. Eine Liste der gültigen Werte für dieses Argument finden Sie weiter oben in diesem Thema. Standardmäßig ist der Übergang, durch den ein Bildschirm zurückgegeben wird, der Umkehrung des Übergangs, durch den es auftrat.

**Navigate**( *Bildschirm* [, *Übergang* [, *updatecontextrecord* ]])

* *Bildschirm*: Erforderlich. Der anzuzeigende Bildschirm.
* *Übergang* : optional.  Der visuelle Übergang, der zwischen dem aktuellen Bildschirm und dem nächsten Bildschirm verwendet werden soll. Weitere Informationen finden Sie in der Liste der gültigen Werte für dieses Argument weiter oben in diesem Thema. Der Standardwert ist " **None**".
* *Kontextaktualisierungs-Datensatz*: Optional.  Ein Datensatz, der den Namen mindestens einer Spalte und einen Wert für jede Spalte enthält. Dieser Datensatz aktualisiert die Kontextvariablen des neuen Bildschirms wie bei der Übergabe an die **[UpdateContext](function-updatecontext.md)** -Funktion.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Navigation (Details)** |Zeigt den **Detailbildschirm** ohne Übergang oder Änderung des Werts einer Kontextvariablen an. |Der **Detailbildschirm** erscheint schnell. |
| **Navigate( Details, ScreenTransition.Fade )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an.  Kein Wert einer Kontextvariablen wird geändert. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an und aktualisiert den Wert der Kontextvariable **ID** auf **12**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen, und die Kontextvariable **ID** auf diesem Bildschirm wird auf **12** festgelegt. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an. Aktualisiert den Wert der Kontextvariable **ID** auf **12** und aktualisiert den Wert der Kontextvariable **Shade** auf **Color.Red**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. Die Kontextvariable **ID** auf dem **Detailbildschirm** wird auf **12** festgelegt, und die Kontextvariable **Shade** wird auf **Color.Red** festgelegt. Wenn Sie die **Fill**-Eigenschaft eines Steuerelements auf dem **Detailbildschirm** auf **Shade** festlegen, würde dieses Steuerelement rot angezeigt werden. |
| **Back()** | Zeigt den vorherigen Bildschirm mit dem standardmäßigen Rückgabe Übergang an. | Zeigt den vorherigen Bildschirm durch den umgekehrten Übergang des Übergangs an, durch den der aktuelle Bildschirm angezeigt wurde. |
| **Zurück (screentransition. Cover)** |  Zeigt den vorherigen Bildschirm mit dem **Deck** Übergang an. | Zeigt den vorherigen Bildschirm über den **Umschlag** Übergang an, unabhängig von der Umstellung, in der der aktuelle Bildschirm angezeigt wird. |

### <a name="step-by-step"></a>Schritt für Schritt

1. Erstellen Sie eine leere app.

1. Fügen Sie einen zweiten Bildschirm hinzu.

    Die app enthält zwei leere Bildschirme: **Screen1** und **Screen2**.

1. Legen **Sie die Fill** -Eigenschaft von **Screen2** auf den Wert `Gray` fest.

1. Fügen Sie auf **Screen2**eine Schaltfläche hinzu, und legen Sie die **[onselect](../controls/properties-core.md)** -Eigenschaft auf diese Formel fest:

    ```powerapps-dot
    Navigate( Screen1, ScreenTransition.Cover )
    ```

1. Wenn Sie die **alt** -Taste gedrückt halten, wählen Sie die Schaltfläche aus.

    **Screen1** wird mit einem weißen Hintergrund durch einen Übergang angezeigt, der sich auf der linken Seite befindet.

1. Fügen Sie auf **Screen1**eine Schaltfläche hinzu, und legen Sie die **onselect** -Eigenschaft auf diese Formel fest:

    ```powerapps-dot
    Back()
    ```

1. Wenn Sie die **alt** -Taste gedrückt halten, wählen Sie die Schaltfläche aus.

    Der zweite Bildschirm wird mit einem grauen Hintergrund durch einen Übergang angezeigt, der auf der rechten Seite (umgekehrter **Abdeckung**) steht.

1. Wählen Sie die Schaltfläche auf jedem Bildschirm wiederholt aus, um hin und her zu springen

[Ein weiteres Beispiel](../add-screen-context-variables.md)
