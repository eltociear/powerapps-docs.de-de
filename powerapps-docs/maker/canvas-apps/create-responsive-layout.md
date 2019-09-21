---
title: Erstellen von reaktionsfähigen Layouts in Canvas-apps | Microsoft-Dokumentation
description: Referenzinformationen zum Konfigurieren von Height-, Width-, X-und Y-Eigenschaften für Steuerelemente in Canvas-apps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm-msft
ms.date: 9/20/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: eee82691b288f21749fe58adbf02ab5ffc3bd8b4
ms.sourcegitcommit: 7016ff837eff2cb0985fc71edab95cbf99335677
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159859"
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>Erstellen von reaktionsfähigen Layouts in Canvas-apps

Bevor Sie eine Canvas-app in powerapps erstellen, geben Sie an, ob die APP für ein Smartphone oder ein Tablet angepasst werden soll. Diese Auswahl bestimmt die Größe und Form der Canvas, auf der Sie Ihre APP erstellen.

Nachdem Sie diese Auswahl getroffen haben, können Sie einige weitere Optionen auswählen, wenn Sie **Datei** > -**App-Einstellungen** > **Bildschirmgröße + Ausrichtung**auswählen. Sie können hoch-oder Querformat und Bildschirmgröße auswählen (nur Tablet). Sie können auch das Seitenverhältnis sperren oder entsperren und die Geräte Rotation unterstützen (oder nicht).

Diese Auswahlmöglichkeiten unterliegen allen anderen Optionen, die Sie beim Entwerfen von Bildschirmlayouts treffen. Wenn Ihre APP auf einem Gerät mit einer anderen Größe oder im Web ausgeführt wird, wird das gesamte Layout entsprechend dem Bildschirm skaliert, auf dem die app ausgeführt wird. Wenn eine für ein Telefon entwickelte app in einem großen Browserfenster ausgeführt wird, wird die APP beispielsweise so skaliert, dass Sie kompensiert wird Die APP kann die zusätzlichen Pixel nicht nutzen, indem Sie mehr Steuerelemente oder mehr Inhalt anzeigt.

Wenn Sie ein reaktionsfähiges Layout erstellen, können die Steuerelemente auf verschiedene Geräte oder Fenstergrößen reagieren, sodass sich die verschiedenen Benutzeroberflächen besser Verhalten. Um das reaktionsfähige Layout zu erreichen, passen Sie einige Einstellungen an und schreiben Ausdrücke in der gesamten app. 

## <a name="disable-scale-to-fit"></a>Deaktivieren der Skalierung

Sie können die einzelnen Bildschirme so konfigurieren, dass sich das Layout an den tatsächlichen Bereich anpasst, in dem die app ausgeführt wird.

Sie aktivieren die Reaktionsfähigkeit, indem Sie die Einstellung **für die Skalierung** der APP ausschalten, die standardmäßig aktiviert ist. Wenn Sie diese Einstellung deaktivieren, deaktivieren Sie auch das **Seitenverhältnis zwischen Sperren** , da Sie nicht mehr für eine bestimmte Bildschirm Form entwerfen. (Sie können weiterhin angeben, ob Ihre APP Geräte Rotation unterstützt.)

![Einstellung für die Skalierung deaktivieren](media/create-responsive-layout/scale-to-fit-off.png)

Damit Ihre APP reaktionsfähig ist, müssen Sie zusätzliche Schritte ausführen, aber diese Änderung ist der erste Schritt, um die Reaktionsfähigkeit zu ermöglichen.

## <a name="understand-app-and-screen-dimensions"></a>Grundlegendes zu app-und Bildschirmdimensionen

Damit die Layouts der APP auf Änderungen in den Bildschirmdimensionen reagieren, schreiben Sie Formeln, die die Eigenschaften " **Width** " und " **height** " auf dem Bildschirm verwenden. Um diese Eigenschaften anzuzeigen, öffnen Sie eine app in PowerApps Studio, und wählen Sie dann einen Bildschirm aus. Die Standardformeln für diese Eigenschaften werden auf der Registerkarte **erweitert** des rechten Bereichs angezeigt.

**Breite** = `Max(App.Width, App.DesignWidth)`

**Flugh** = `Max(App.Height, App.DesignHeight)`

Diese Formeln beziehen sich auf die Eigenschaften " **Width**", " **height**", " **designwidth**" und " **designheight** " der app. Die Eigenschaften " **Width** " und " **height** " der App entsprechen den Dimensionen des Geräts oder Browserfensters, in dem Ihre APP ausgeführt wird. Wenn der Benutzer die Größe des Browserfensters ändert (oder das Gerät rotiert, wenn Sie die **Sperr Ausrichtung**ausgeschaltet haben), werden die Werte dieser Eigenschaften dynamisch geändert. Die Formeln in den Eigenschaften " **Width** " und " **height** " des Bildschirms werden erneut ausgewertet, wenn sich diese Werte ändern.

Die Eigenschaften **Design Width** und **designheight** stammen aus den Dimensionen, die Sie im Bereich **Bildschirmgröße + Ausrichtung** der **App-Einstellungen**angeben. Wenn Sie z. b. das Telefon Layout im Hochformat auswählen, ist **designwidth** 640, und **designheight** ist 1136.

Da Sie in den Formeln für die **Width** -und **height** -Eigenschaften des Bildschirms verwendet werden, können Sie **Design Width** und **designheight** als minimale Dimensionen vorstellen, für die Sie die APP entwerfen. Wenn der tatsächliche Bereich, der für Ihre app verfügbar ist, noch kleiner als diese minimalen Dimensionen ist, stellen die Formeln für die **Width** -und **height** -Eigenschaften des Bildschirms sicher, dass ihre Werte nicht kleiner als Minimums werden. In diesem Fall muss der Benutzer einen Bildlauf durchführen, um den gesamten Inhalt des Bildschirms anzuzeigen.

Nachdem Sie **Design Width** und **designheight**Ihrer APP festgelegt haben, müssen Sie (in den meisten Fällen) Standardformeln für die Eigenschaften " **Width** " und " **height** " für jeden Bildschirm ändern. Später werden in diesem Thema Fälle erläutert, in denen Sie diese Formeln möglicherweise anpassen möchten.

## <a name="use-formulas-for-dynamic-layout"></a>Verwenden von Formeln für dynamisches Layout

Um einen reaktionsfähigen Entwurf zu erstellen, können Sie die einzelnen Steuerelemente mithilfe von Formeln anstelle absoluter (konstanter) Koordinaten Werte suchen und anpassen. Diese Formeln Ausdrücken die Position und Größe jedes Steuer Elements in Bezug auf die gesamte Bildschirmgröße oder relativ zu anderen Steuerelementen auf dem Bildschirm.

> [!IMPORTANT]
> Nachdem Sie Formeln für die Eigenschaften **X**, **Y**, **Width** und **height** eines Steuer Elements geschrieben haben, werden die Formeln mit Konstanten Werten überschrieben, wenn Sie das Steuerelement anschließend in den Canvas-Editor ziehen. Wenn Sie mit der Verwendung von Formeln beginnen, um dynamisches Layout zu erzielen, sollten Sie das Ziehen von Steuerelementen vermeiden.

Im einfachsten Fall füllt ein Steuerelement einen gesamten Bildschirm aus. Legen Sie die Eigenschaften des Steuer Elements auf die folgenden Werte fest, um diesen Effekt zu erstellen:

| Eigenschaft      | Value            |
|--------|---------------|
| **STUBEN**      | `0`             |
| **TEENIE**      | `0`             |
| **Breite**  | `Parent.Width`  |
| **Flugh** | `Parent.Height` |

Diese Formeln verwenden den **Parent** -Operator. Bei einem direkt auf einem Bildschirm platzierten Steuerelement verweist **Parent** auf den Bildschirm. Mit diesen Eigenschafts Werten wird das Steuerelement in der oberen linken Ecke des Bildschirms (0,0) angezeigt und hat dieselbe **Breite** und **Höhe** wie der Bildschirm.

Später in diesem Thema wenden Sie diese Prinzipien (und den über **geordneten** Operator) an, um Steuerelemente in anderen Containern, z. b. Galerien, Gruppen Steuerelementen und Komponenten, zu positionieren.

Als Alternative kann das Steuerelement nur die obere Hälfte des Bildschirms ausfüllen. Legen Sie zum Erstellen dieses Effekts die **height** -Eigenschaft auf **Parent. Height** /2 fest, und lassen Sie die anderen Formeln unverändert.

Wenn Sie ein zweites Steuerelement in der unteren Hälfte des gleichen Bildschirms ausfüllen möchten, können Sie die Formeln mit mindestens zwei weiteren Ansätzen erstellen. Der Einfachheit halber können Sie diesen Ansatz nutzen:

| Steuerelement | Eigenschaft | Formel           |
|-|----------|-------------------|
| **Weite** | **STUBEN**        | `0`                 |
| **Weite** | **TEENIE**        | `0`                 |
| **Weite** | **Breite**    | `Parent.Width`      |
| **Weite** | **Flugh**   | `Parent.Height / 2` |
| **Günstigere** | **STUBEN**        | `0`                 |
| **Günstigere** | **TEENIE**        | `Parent.Height / 2` |
| **Günstigere** | **Breite**    | `Parent.Width`      |
| **Günstigere** | **Flugh**   | `Parent.Height / 2` |

![Obere und untere Steuerung](media/create-responsive-layout/dynamic-layout.png)

Mit dieser Konfiguration können Sie die gewünschte Wirkung erzielen, aber Sie müssen jede Formel bearbeiten, wenn Sie die relative Größe der Steuerelemente geändert haben. Beispielsweise können Sie entscheiden, dass das oberste Steuerelement nur das oberste Drittel des Bildschirms belegen soll, wobei das untere Steuerelement die unteren zwei Drittel füllt. 

Um diesen Effekt zu erstellen, müssen Sie die **height** -Eigenschaft des **oberen** Steuer Elements und die **Y** -und **height** -Eigenschaften des **unteren** Steuer Elements aktualisieren. Schreiben Sie stattdessen die Formeln für das **untere** Steuerelement in Bezug auf das **obere** Steuerelement (und sich selbst), wie in diesem Beispiel:


| Steuerelement | Eigenschaft | Formel           |
|-|----------|-------------------|
| **Weite** | **STUBEN**        | `0`                 |
| **Weite** | **TEENIE**        | `0`                 |
| **Weite** | **Breite**    | `Parent.Width`      |
| **Weite** | **Flugh**   | `Parent.Height / 2` |
| **Günstigere** | **STUBEN**        | `0`                       |
| **Günstigere** | **TEENIE**        | `Upper.Y + Upper.Height`  |
| **Günstigere** | **Breite**    | `Parent.Width`            |
| **Günstigere** | **Flugh**   | `Parent.Height - Lower.Y` |

![Obere und untere Steuerelemente relative Größe](media/create-responsive-layout/dynamic-layout2.png)

Wenn diese Formeln vorhanden sind, müssen Sie nur die **height** -Eigenschaft des **oberen** Steuer Elements ändern, um einen anderen Bruchteil der Höhe des Bildschirms auszudrücken. Das **untere** Steuerelement wird automatisch verschoben und seine Größe geändert, um die Änderung zu berücksichtigen.

Sie können diese Formel Muster verwenden, um allgemeine Layoutbeziehungen zwischen einem Steuerelement mit dem Namen **C**und dem übergeordneten Element oder einem gleich geordneten Steuerelement mit dem Namen **D**auszudrücken.

| Beziehung zwischen C und dem übergeordneten Element | Eigenschaft | Formel | Deutlich |
|--|--|--|--|
| **C** füllt Breite des übergeordneten Elements mit einem Rand von *N* | **STUBEN**| `N` | ![Beispiel für die C-Füllungs Breite des übergeordneten Elements](media/create-responsive-layout/c1.png) |
|  | **Breite** | `Parent.Width - (N * 2)` |  |
| **C** füllt die Höhe des übergeordneten Elements mit einem Rand von *N* | **TEENIE** | `N` | ![Beispiel für die C-Füllungs Höhe eines übergeordneten Elements](media/create-responsive-layout/c2.png) |
|  | **Flugh** | `Parent.Height - (N * 2)` |  |
| **C** am rechten Rand des übergeordneten Elements ausgerichtet, mit Rand von *N* | **STUBEN** | `Parent.Width - (C.Width + N)` | ![Beispiel für C-Ausrichtung mit Rand des übergeordneten Elements](media/create-responsive-layout/c3.png) |
| **C** mit dem unteren Rand des übergeordneten Elements ausgerichtet, mit Rand von *N* | **TEENIE** | `Parent.Height - (C.Height + N)` | ![Beispiel für C-Ausrichtung mit Rand des übergeordneten Elements](media/create-responsive-layout/c4.png) |
| **C** zentriert horizontal auf übergeordnetem Element | **STUBEN** | `(Parent.Width - C.Width) / 2` | ![Beispiel für das horizontale zentrierte C auf dem übergeordneten Element](media/create-responsive-layout/c5.png) |
| **C** vertikal auf dem übergeordneten Element zentriert | **TEENIE** | `(Parent.Height - C.Height) / 2` | ![Beispiel für das vertikale zentrierte C auf dem übergeordneten Element](media/create-responsive-layout/c6.png) |

| Beziehung zwischen C und D | Eigenschaft | Formel | Deutlich |
|--|--|--|--|
| **C** horizontal mit **d** und derselben Breite wie **d** ausgerichtet | **STUBEN** | `D.X` | ![Beispiel für Muster](media/create-responsive-layout/d1.png) |
|  | **Breite**    | `D.Width` |  |
| **C** vertikal an **d** und gleicher Höhe als **d** ausgerichtet  | **TEENIE** | `D.Y` | ![Beispiel für Muster](media/create-responsive-layout/d2.png) |
|  | **Flugh** | `D.Height` |  |
| Rechter Rand von **C** ausgerichtet am rechten Rand von **D** | **STUBEN** | `D.X + D.Width - C.Width` | ![Beispiel für Muster](media/create-responsive-layout/d3.png) |
| Der untere Rand von **C** ist am unteren Rand von **D** ausgerichtet. | **TEENIE** | `D.Y + D.Height - C.Height` | ![Beispiel für Muster](media/create-responsive-layout/d4.png) |
| **C** zentriert horizontal relativ zu **D** zentriert | **STUBEN** | `D.X + (D.Width - C.Width) / 2`  | ![Beispiel für Muster](media/create-responsive-layout/d5.png) |
| **C** in Bezug auf **D** vertikal zentriert | **TEENIE** | `D.Y + (D.Height - C.Height) /2` | ![Beispiel für Muster](media/create-responsive-layout/d6.png) |
| **C** auf der rechten Seite von **D** mit einer Lücke von N positioniert | **STUBEN** | `D.X + D.Width + N` | ![Beispiel für Muster](media/create-responsive-layout/d7.png) |
| **C** unter **D** positioniert und eine Lücke von *N*             | **TEENIE** | `D.Y + D.Height + N` | ![Beispiel für Muster](media/create-responsive-layout/d8.png) |
| **C** füllt den Leerraum zwischen **D** und dem rechten Rand des übergeordneten Elements | **STUBEN** | `D.X + D.Width` | ![Beispiel für Muster](media/create-responsive-layout/d9.png) |
|  | **Breite** | `Parent.Width - C.X` |  |
| **C** füllt den Leerraum zwischen **D** und dem unteren Rand des übergeordneten Elements | Y | `D.Y + D.Height` | ![Beispiel für Muster](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>Hierarchisches Layout

Wenn Sie Bildschirme erstellen, die mehr Steuerelemente enthalten, wird es bequemer (oder sogar notwendig), Steuerelemente relativ zu einem übergeordneten Steuerelement zu positionieren, anstatt relativ zum Bildschirm oder einem gleich geordneten Steuerelement zu werden. Indem Sie Ihre Steuerelemente in einer hierarchischen Struktur organisieren, können Sie die Erstellung und Verwaltung Ihrer Formeln vereinfachen.

### <a name="galleries"></a>Buden

Wenn Sie in Ihrer APP einen Katalog verwenden, müssen Sie die Steuerelemente in der Vorlage des Katalogs anordnen. Sie können diese Steuerelemente positionieren, indem Sie Formeln schreiben, die den über **geordneten** Operator verwenden, der auf die Katalog Vorlage verweist. Verwenden Sie in den Formeln für Steuerelemente in einer Katalog Vorlage die **Parent. templateheight** -Eigenschaft und die **Parent. templatewidth** -Eigenschaft. Verwenden Sie " **Parent. Width** " und " **Parent. Height**" nicht, was sich auf die Gesamtgröße des Katalogs bezieht.

![Vertikaler Katalog mit Vorlagen Breite und-Höhe](media/create-responsive-layout/gallery-vertical.png)

### <a name="container-control"></a>Container-Steuerelement

Sie können eine experimentelle Funktion, das **Container** Steuerelement, als übergeordnetes Steuerelement verwenden. Um diese Funktion zu aktivieren, wählen Sie **Datei** > **App-Einstellungen** > **Erweiterte Einstellungen**aus.

Betrachten Sie das Beispiel eines Headers am oberen Rand eines Bildschirms. Es ist üblich, dass ein Header mit einem Titel und mehreren Symbolen vorhanden ist, mit denen Ihre Benutzer interagieren können. Sie können einen solchen Header mit dem **Container** -Steuerelement erstellen, das ein **Label** -Steuerelement und zwei **Symbol** Steuerelemente enthält:

![Header Beispiel mit einer Gruppe](media/create-responsive-layout/header-group.png)

Legen Sie die Eigenschaften für diese Steuerelemente auf folgende Werte fest:

| Eigenschaft | Header | Stehen | ihrer | Title |
|--|--|--|--|--|
| **STUBEN** | `0`  | `0` | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **TEENIE** | `0` | `0` | `0` | `0` |
| **Breite**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **Flugh** | `64` | `Parent.Height` | `Parent.Height` | `Parent.Height` |

`Parent` Bezieht sich auf den Bildschirm für das **Header** -Steuerelement. Bei den anderen `Parent` bezieht sich auf das **Header** Steuerelement.

Nachdem Sie diese Formeln geschrieben haben, können Sie die Größe oder Position des **Header** Steuer Elements anpassen, indem Sie die Formeln für ihre Eigenschaften ändern. Die Größen und Positionen der untergeordneten Steuerelemente werden automatisch entsprechend angepasst.

### <a name="components"></a>Komponenten

Wenn Sie eine andere experimentelle Funktion namens "Components" verwenden, können Sie Bausteine erstellen und Sie in der gesamten APP wieder verwenden. Wie beim **Container** Steuerelement sollten die Steuerelemente, die Sie in einer Komponente platzieren, ihre Positions-und Größen `Parent.Width` Formeln `Parent.Height`auf und festlegen, die auf die Größe der Komponente verweisen. Weitere Informationen finden Sie unter: [Erstellen Sie eine-Komponente](create-component.md).

## <a name="adapting-layout-for-device-size-and-orientation"></a>Anpassen des Layouts für Gerätegröße und-Ausrichtung

Bisher haben Sie gelernt, wie Sie Formeln verwenden, um die Größe jedes Steuer Elements als Reaktion auf den verfügbaren Platz zu ändern, während Steuerelemente relativ zueinander ausgerichtet bleiben. Vielleicht möchten Sie jedoch auch größere Layoutänderungen als Reaktion auf verschiedene Gerätegrößen und-Ausrichtungen durchführen. Wenn ein Gerät z. b. vom Hochformat in Querformat gedreht wird, können Sie z. b. von einem vertikalen Layout in ein horizontales Layout wechseln. Auf einem größeren Gerät können Sie weitere Inhalte präsentieren oder Sie neu anordnen, um ein ansprechendere Layout zu bieten. Auf einem kleineren Gerät müssen Sie möglicherweise Inhalt auf mehrere Bildschirme aufteilen.

### <a name="device-orientation"></a>Geräte Ausrichtung

Die Standardformeln für die Eigenschaften " **Width** " und " **height** " eines Bildschirms, wie in diesem Thema bereits beschrieben, bieten nicht unbedingt eine gute Benutzerfunktion, wenn ein Benutzer ein Gerät rotiert. Beispielsweise hat eine APP, die für ein Telefon im Hochformat entworfen wurde, eine Entwurfs **Breite** von 640 und eine **designheight** von 1136. Die gleiche APP auf einem Telefon in Querformat weist die folgenden Eigenschaftswerte auf:

- Die **Width** -Eigenschaft des Bildschirms ist `Max(App.Width, App.DesignWidth)`auf festgelegt. Die **Breite** der APP (1136) ist größer als die **designwidth** (640), sodass die Formel als 1136 ausgewertet wird.
- Die **height** -Eigenschaft des Bildschirms ist `Max(App.Height, App.DesignHeight)`auf festgelegt. Die **Höhe** der APP (640) ist kleiner als die **designheight** (1136), sodass die Formel zu 1136 ausgewertet wird.

Bei einer Bildschirm **Höhe** von 1136 und einer Geräte Höhe (in dieser Ausrichtung) von 640 muss der Benutzer den Bildschirm vertikal scrollen, um den gesamten Inhalt anzuzeigen. Dies ist möglicherweise nicht die gewünschte Umgebung.

Wenn Sie die Eigenschaften **Breite** und **Höhe** des Bildschirms an die Geräte Ausrichtung anpassen möchten, können Sie folgende Formeln verwenden:

**Breite** = `Max(App.Width, If(App.Width < App.Height, App.DesignWidth, App.DesignHeight))`

**Flugh** = `Max(App.Height, If(App.Width < App.Height, App.DesignHeight, App.DesignWidth))`

Diese Formeln tauschen die **Design Width** -und **designheight** -Werte der APP aus, je nachdem, ob die Breite des Geräts kleiner ist als seine Höhe (Hochformat Ausrichtung) oder mehr als seine Höhe (Querformat).

Nachdem Sie die Formeln für **Breite** und **Höhe** des Bildschirms angepasst haben, möchten Sie möglicherweise auch die Steuerelemente in Ihrem Bildschirm neu anordnen, um den verfügbaren Platz besser zu nutzen. Wenn beispielsweise jedes der beiden Steuerelemente die Hälfte des Bildschirms einnimmt, können Sie diese vertikal im Hochformat Stapeln, Sie aber nebeneinander im Querformat anordnen.

Mit der Eigenschaft **Ausrichtung** des Bildschirms können Sie feststellen, ob der Bildschirm vertikal oder horizontal ausgerichtet ist.

> [!NOTE]
> Im Querformat werden die **oberen** und **unteren** Steuerelemente als linke und Rechte Steuerelemente angezeigt.

| Steuerelement | Eigenschaft | Formel |
|--|----------|---|
| **Weite** | **STUBEN** | `0` |
| **Weite** | **TEENIE** | `0` |
| **Weite** | **Breite** | `If(Parent.Orientation = Layout.Vertical, Parent.Width, Parent.Width / 2)` |
| **Weite** | **Flugh**   | `If(Parent.Orientation = Layout.Vertical, Parent.Height / 2, Parent.Height)` |
| **Günstigere** | X | `If(Parent.Orientation = Layout.Vertical, 0, Upper.X + Upper.Width)`  |
| **Günstigere** | Y | `If(Parent.Orientation = Layout.Vertical, Upper.Y + Upper.Height, 0)` |
| **Günstigere** | **Breite** | `Parent.Width - Lower.X` |
| **Günstigere** | **Flugh** | `Parent.Height - Lower.Y` |

![Ausdrücke zur Anpassung der Hochformat Ausrichtung](media/create-responsive-layout/portrait.png)

![Ausdrücke zum Anpassen einer Querformat Ausrichtung](media/create-responsive-layout/landscape.png)

### <a name="screen-sizes-and-breakpoints"></a>Bildschirmgrößen und Breakpoints

Sie können das Layout basierend auf der Größe des Geräts anpassen. Die **size** -Eigenschaft des Bildschirms klassifiziert die aktuelle Gerätegröße. Die Größe ist eine positive ganze Zahl. der ScreenSize-Typ stellt benannte Konstanten bereit, um die Lesbarkeit zu unterstützen. In dieser Tabelle sind die Konstanten aufgeführt:

| Bend              | Value | Typischer Gerätetyp (unter Verwendung der standardmäßigen App-Einstellungen) |
|-----------------------|-------|--------------------------------------------------|
| ScreenSize. Small      | 1     | Smartphone                                            |
| ScreenSize. Medium     | 2     | Tablet, vertikal gehalten                          |
| ScreenSize. Large      | 3     | Tablet, horizontal gehalten                        |
| ScreenSize. extralarge | 4     | Desktop Computer                                 |

Verwenden Sie diese Größen, um Entscheidungen über das Layout Ihrer APP zu treffen. Wenn Sie z. b. möchten, dass ein Steuerelement auf einem Gerät mit Telefongerät ausgeblendet, aber andernfalls angezeigt wird, können Sie die **Visible** -Eigenschaft des Steuer Elements auf diese Formel festlegen:

`Parent.Size >= ScreenSize.Medium`

Diese Formel ergibt **true** , wenn die Größe Mittel oder größer ist, und andernfalls **false** .

Wenn Sie möchten, dass ein Steuerelement einen anderen Bruchteil der Bildschirmbreite basierend auf der Bildschirmgröße einnimmt, legen Sie die **Width** -Eigenschaft des Steuer Elements auf diese Formel fest:

```powerapps-dot
Parent.Width *  
    Switch(Parent.Size,  
        ScreenSize.Small, 0.5,  
        ScreenSize.Medium, 0.3,  
        0.25)
```
Mit dieser Formel wird die Breite des Steuer Elements auf einem kleinen Bildschirm auf die Hälfte der Bildschirmbreite festgelegt, die drei Zehntel der Bildschirmbreite auf einem mittleren Bildschirm und ein Quartal der Bildschirmbreite auf allen anderen Bildschirmen.

## <a name="custom-breakpoints"></a>Benutzerdefinierte Breakpoints

Die **size** -Eigenschaft des Bildschirms wird berechnet, indem die **Width** -Eigenschaft des Bildschirms mit den Werten in der **sizebreakpoints** -Eigenschaft der APP verglichen wird. Diese Eigenschaft ist eine einspaltige Tabelle mit Zahlen, die die Breite Haltepunkte angeben, mit denen die benannten Bildschirmgrößen getrennt werden:

In einer APP, die für Tablet oder Web erstellt wurde, ist der Standardwert in der **sizebreakpoints** -Eigenschaft der APP **[600, 900, 1200]** . In einer für Smartphones erstellten App lautet der Wert **[1200, 1800, 2400]** . (Die Werte für Phone-apps werden verdoppelt, da solche apps Koordinaten verwenden, die die in anderen apps verwendeten Koordinaten effektiv verdoppeln.)

![Standardwerte der app. sizebreakpoints-Eigenschaft](media/create-responsive-layout/default-breakpoints.png)

Sie können die Breakpoints Ihrer APP anpassen, indem Sie die Werte in der **sizebreakpoints** -Eigenschaft der App ändern. Wählen Sie in der Strukturansicht **App** aus, wählen Sie in der Liste Eigenschaft die Option **sizebreakpoints** aus, und bearbeiten Sie dann die Werte in der Bearbeitungs Leiste. Sie können so viele Haltepunkte wie Ihre APP erstellen, aber nur die Größen 1 bis 4 entsprechen den benannten Bildschirmgrößen. In Formeln können Sie mit ihren numerischen Werten ("5", "6" usw.) auf Größen hinaus verweisen.

Sie können auch weniger Haltepunkte angeben. Ihre APP benötigt z. b. möglicherweise nur drei Größen (zwei Breakpoints), sodass die möglichen Bildschirmgrößen klein, Mittel und groß sind.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Der Authoring Canvas antwortet nicht auf die erstellten Größen Anpassungs Formeln. Um das Reaktionsverhalten zu testen, speichern und veröffentlichen Sie Ihre APP, und öffnen Sie Sie auf Geräten oder in Browserfenstern verschiedener Größen und Ausrichtungen.

Wenn Sie Ausdrücke oder Formeln in den Eigenschaften **X**, **Y**, **Width**und **height** eines Steuer Elements schreiben, überschreiben Sie diese Ausdrücke oder Formeln, wenn Sie das Steuerelement später an eine andere Position ziehen oder die Größe des Steuer Elements durchziehen der Größe ändern. der Rahmen.
