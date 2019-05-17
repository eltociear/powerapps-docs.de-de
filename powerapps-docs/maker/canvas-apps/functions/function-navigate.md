---
title: Funktionen „Back“ und „Navigate“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Back“ und „Navigate“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/16/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e57cc541c753ff3f24f66a78c6e30d6e5683b41a
ms.sourcegitcommit: 57dfad065318263e162e949e26b5c2684ba0dccb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828178"
---
# <a name="back-and-navigate-functions-in-powerapps"></a>Funktionen „Back“ und „Navigate“ in PowerApps

Ändern, welcher Bildschirm angezeigt wird

## <a name="overview"></a>Übersicht

Die meisten Apps umfassen mehrere Bildschirme.  Verwenden Sie die Funktionen **Back** und **Navigate**, um zu ändern, welcher Bildschirm angezeigt wird. Legen Sie z.B. die **[OnSelect](../controls/properties-core.md)**-Eigenschaft einer Schaltfläche auf eine Formel fest, die eine **Navigate**-Funktion enthält, wenn Sie einen anderen Bildschirm anzeigen möchten, wenn ein Benutzer diese Schaltfläche auswählt. In dieser Formel können Sie einen visuellen Übergang, wie z.B. **Fade** angeben, um zu steuern, wie ein Bildschirm zu einem anderen Bildschirm wechselt.  

Die Funktionen **Back** und **Navigate** ändern nur, welcher Bildschirm angezeigt wird. Bildschirme, die momentan nicht angezeigt werden, werden weiterhin im Hintergrund ausgeführt. Sie können Formeln erstellen, die auf Eigenschaften von Steuerelementen auf anderen Bildschirmen verweisen. Beispielsweise kann ein Benutzer ändern Sie den Wert eines Schiebereglers auf einem Bildschirm, navigieren Sie zu einem anderen Bildschirm, der diesen Wert in einer Formel verwendet und ermitteln, wie sie beeinflusst, was auf dem neuen Bildschirm geschieht. Der Benutzer kann dann wieder zum ursprünglichen Bildschirm zurück navigieren und bestätigen Sie, dass der Wert der des Schiebereglers beibehalten wurde.

[Kontextvariablen](../working-with-variables.md#use-a-context-variable) werden ebenfalls beibehalten, wenn ein Benutzer zwischen Bildschirmen navigiert. Sie können **Navigate** verwenden, um eine oder mehrere Kontextvariablen für den Bildschirm festzulegen, den die Formel anzeigen wird. Dies ist die einzige Möglichkeit, von außerhalb des Bildschirms eine Kontextvariable festzulegen. Sie können diesen Ansatz verwenden, um Parameter an einen Bildschirm zu übergeben. Wenn Sie ein anderes Programmiertool verwendet haben, ähnelt diese Vorgehensweise der Übergabe von Parametern an Prozeduren.

Sie können entweder die Funktion nur innerhalb einer [verhaltensformel](../working-with-formulas-in-depth.md).

## <a name="navigate"></a>Navigate

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

**Navigieren Sie** normalerweise zurück **"true"** jedoch zurück **"false"** , wenn ein Fehler aufgetreten ist.

## <a name="back"></a>Back

Die **wieder** Funktionsergebnis ist auf dem Bildschirm, der die zuletzt angezeigt wurde.

Für jede **Navigate** Aufrufe die app verfolgt, den Bildschirm, der angezeigt wurde und den Übergang. Können Sie aufeinander folgende **wieder** Aufrufe zurück bis hin zu dem Bildschirm, die beim angezeigt wurden den Benutzer gestartet, die app.

Wenn die **wieder** -Funktion ausgeführt wird, den umgekehrten Übergang wird standardmäßig verwendet. Beispielsweise wenn ein Bildschirm angezeigt wurde, über die **CoverRight** Übergang **wieder** verwendet **aufdecken** (Dies ist auf der linken Seite) zurückgegeben.  **Fade** und **keine** sind ihre eigenen Gegenstücke. Übergeben Sie ein optionales Argument für **wieder** einen spezifischen Übergang zu erzwingen.

**Wieder** normalerweise zurück **"true"** gibt jedoch **"false"** , wenn der Benutzer zu einem anderen Bildschirm navigiert noch nicht, seit dem Start der app.

## <a name="syntax"></a>Syntax

**Wieder**([ *Übergang* ])

* *Übergang* : Optional. Der visuelle Übergang, der zwischen dem aktuellen Bildschirm und dem vorherigen Bildschirm verwendet werden soll. Finden Sie in der Liste der gültigen Werte für dieses Argument weiter oben in diesem Thema. Standardmäßig ist die Umstellung, die über die ein Bildschirm gibt die Umkehrung des Übergangs durch die es angezeigt.

**Navigieren Sie**( *Bildschirm* [, *Übergang* [, *kontextaktualisierungs-Datensatz* ]])

* *Bildschirm*: Erforderlich. Der anzuzeigende Bildschirm.
* *Übergang* : Optional.  Der visuelle Übergang, der zwischen dem aktuellen Bildschirm und dem nächsten Bildschirm verwendet werden soll. Weitere Informationen finden Sie in der Liste der gültigen Werte für dieses Argument weiter oben in diesem Thema. Der Standardwert ist **keine**.
* *Kontextaktualisierungs-Datensatz*: Optional.  Ein Datensatz, der den Namen mindestens einer Spalte und einen Wert für jede Spalte enthält. Dieser Datensatz aktualisiert die Kontextvariablen des neuen Bildschirms wie bei der Übergabe an die **[UpdateContext](function-updatecontext.md)**-Funktion.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Navigate( Details )** |Zeigt den **Detailbildschirm** ohne Übergang oder Änderung des Werts einer Kontextvariablen an. |Der **Detailbildschirm** erscheint schnell. |
| **Navigate( Details, ScreenTransition.Fade )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an.  Kein Wert einer Kontextvariablen wird geändert. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an und aktualisiert den Wert der Kontextvariable **ID** auf **12**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen, und die Kontextvariable **ID** auf diesem Bildschirm wird auf **12** festgelegt. |
| **Navigate( Details, ScreenTransition.Fade, {&nbsp;ID:&nbsp;12&nbsp;,&nbsp;Shade:&nbsp;Color.Red&nbsp;} )** |Zeigt den **Detailbildschirm** mit einem **Fade**-Übergang an. Aktualisiert den Wert der Kontextvariable **ID** auf **12** und aktualisiert den Wert der Kontextvariable **Shade** auf **Color.Red**. |Der aktuelle Bildschirm wird ausgeblendet, um den **Detailbildschirm** anzuzeigen. Die Kontextvariable **ID** auf dem **Detailbildschirm** wird auf **12** festgelegt, und die Kontextvariable **Shade** wird auf **Color.Red** festgelegt. Wenn Sie die **Fill**-Eigenschaft eines Steuerelements auf dem **Detailbildschirm** auf **Shade** festlegen, würde dieses Steuerelement rot angezeigt werden. |
| **Back()** | Zeigt dem vorherigen Bildschirm mit dem Standard-zurück-Übergang. | Zeigt die vorherige Ansicht der umgekehrten Umstellung des Übergangs über die vom aktuelle Bildschirm angezeigt wurde. |
| **Back( ScreenTransition.Cover )** |  Zeigt den vorherigen Bildschirm mit der **behandelt** Übergang. | Zeigt den vorherigen Bildschirm über das **behandelt** Übergang, unabhängig von den Übergang, der über die vom aktuelle Bildschirm angezeigt wurde. |

### <a name="step-by-step"></a>Schritt für Schritt

1. Erstellen Sie eine leere app.

1. Fügen Sie einen zweiten Bildschirm hinzu.

    Die app enthält zwei leere Bildschirme: **Screen1** und **Screen2**.

1. Legen Sie die **füllen** Eigenschaft **Screen2** auf den Wert `Gray`.

1. Auf **Screen2**, fügen Sie eine Schaltfläche hinzu, und legen dessen **[OnSelect](../controls/properties-core.md)** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    Navigate( Screen1, ScreenTransition.Cover )
    ```

1. Halten Sie die **Alt** Schlüssel, klicken Sie auf die Schaltfläche.

    **Screen1** angezeigt, die mit einem weißen Hintergrund durch einen Übergang, der auf der linken Seite behandelt wird.

1. Auf **Screen1**, fügen Sie eine Schaltfläche hinzu, und legen dessen **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    Back()
    ```

1. Halten Sie die **Alt** Schlüssel, klicken Sie auf die Schaltfläche.

    Der zweite Bildschirm angezeigt wird, mit einem grauen Hintergrund durch einen Übergang, der auf der rechten Seite ereignisverarbeitungsmodul (die Umkehrung der **behandelt**).

1. Wählen Sie die Schaltfläche auf den einzelnen Bildschirmen wiederholt, um hin und her zu springen.

[Ein weiteres Beispiel](../add-screen-context-variables.md)
