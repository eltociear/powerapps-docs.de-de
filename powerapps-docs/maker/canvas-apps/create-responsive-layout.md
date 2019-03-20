---
title: Erstellen von reaktionsfähigen Layouts in Canvas-apps | Microsoft-Dokumentation
description: Referenzinformationen zum Konfigurieren von Höhe, Breite, X und Y-Eigenschaften für Steuerelemente in der Canvas-apps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8a46cb15be6a93988b89d8f85658ae7c9d5a900e
ms.sourcegitcommit: 0dbbf53aea319e53edadc1d3a9efa5728856ebd8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58173241"
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>Erstellen von reaktionsfähigen Layouts in Canvas-apps

Bevor Sie eine Canvas-app in PowerApps erstellen, geben Sie an, ob die app für ein Smartphone oder Tablet anzupassen. Diese Auswahl bestimmt die Größe und Form des Zeichenbereichs auf dem Sie Ihre app erstellen.

Nachdem Sie diese Auswahl vorgenommen haben, können Sie einigen Weitere Optionen vornehmen, bei Auswahl von **Datei** > **Anwendungseinstellungen** > **Bildschirmgröße und-Ausrichtung**. Sie können die hoch- oder Querformat und Größe des Bildschirms (nur für Tablet) auswählen. Sie können auch sperren oder Entsperren das Seitenverhältnis wird beibehalten und geräterotation (oder nicht) zu unterstützen.

Diese Optionen zugrunde liegen, jeder andere von Ihnen gewählten Bildschirmlayouts entwerfen. Wenn Ihre app ausgeführt wird, auf einem Gerät mit einer anderen Größe oder im Web, Ihre gesamte Layout-Skalierung auf den Bildschirm zu passen, in dem die app ausgeführt wird. Wenn eine app für ein Telefon in einem großen Browserfenster ausgeführt wird, z. B. die app skaliert werden kann, um dies auszugleichen und sieht für den Speicher zu große. Die app nutzen nicht die zusätzlichen Pixel zeigen Weitere Steuerelemente oder weitere Inhalte zu.

Wenn Sie ein dynamisches Layout erstellen, können Steuerelemente auf verschiedenen Geräten oder Fenstergrößen, unsere Fans mit verschiedenen Formfaktoren zu Hause fühlen Weitere reagieren. Um reaktionsfähigen Layout zu erzielen, müssen Sie einige Einstellungen anzupassen und Schreiben von Ausdrücken in der gesamten app. 

## <a name="disable-scale-to-fit"></a>Deaktivieren Sie die Skalierung anpassen

Sie können jeden Bildschirm konfigurieren, damit das Layout auf den tatsächlichen Speicherplatz anpasst, in dem die app ausgeführt wird.

Sie aktivieren Reaktionsfähigkeit durch Deaktivieren der app **an anpassen** Einstellung, die standardmäßig aktiviert ist. Wenn Sie aktivieren, diese Einstellung deaktiviert, Sie auch deaktivieren **Seitenverhältnis sperren** , da Sie nicht mehr für eine Form von bestimmten Bildschirm entwerfen. (Sie können immer noch angeben, ob Ihre app geräterotation unterstützt.)

![Deaktivieren Sie die Skalierung Einstellung anpassen.](media/create-responsive-layout/scale-to-fit-off.png)

Um die Reaktionsfähigkeit Ihrer app steigern, müssen Sie zusätzliche Schritte ausführen, aber diese Änderung ist der erste Schritt hin zu einer Reaktionsfähigkeit möglich.

## <a name="understand-app-and-screen-dimensions"></a>Verstehen Sie die Dimensionen "app" und "Bildschirm

Um Ihrer app-Layouts, die Reaktion auf Änderungen in den bildschirmabmessungen machen zu können, Schreiben Sie Formeln, mit denen die **Breite** und **Höhe** Bildschirmeigenschaften. Um diese Eigenschaften anzuzeigen, öffnen Sie eine app in PowerApps Studio, und wählen Sie dann auf einen Bildschirm. Die Standardformel für diese Eigenschaften werden auf die **erweitert** Registerkarte im rechten Bereich.

**Breite** = `Max(App.Width, App.DesignWidth)`

**Höhe** = `Max(App.Height, App.DesignHeight)`

Diese Formeln finden Sie in der **Breite**, **Höhe**, **DesignWidth**, und **DesignHeight** Eigenschaften der app. Der app **Breite** und **Höhe** Eigenschaften entsprechen den Dimensionen im Gerät oder Browser-Fenster, in dem Ihre app ausgeführt wird. Wenn der Benutzer das Browserfenster angepasst wird (oder das Gerät dreht, wenn Sie deaktiviert haben **bildschirmausrichtung Sperren**), die Werte dieser Eigenschaften dynamisch ändern. Die Formeln in des Bildschirms **Breite** und **Höhe** Eigenschaften werden erneut ausgewertet, wenn diese Werte ändern.

Die **DesignWidth** und **DesignHeight** Eigenschaften stammen aus den Dimensionen, die Sie, in angeben der **Bildschirmgröße und-Ausrichtung** Bereich **App-Einstellungen** . Wenn Sie im telefonlayout wählen Sie in das Hochformat-Ausrichtung, z. B. **DesignWidth** ist 640, und **DesignHeight** 1136 ist.

Wie sie in den Formeln für des Bildschirms verwendet werden **Breite** und **Höhe** Eigenschaften, Sie können sich vorstellen **DesignWidth** und **DesignHeight** als die minimalen Abmessungen für die Sie die app entwerfen müssen. Ist der tatsächliche Bereich Ihrer app zur Verfügung sogar noch kleiner als die folgenden Dimensionen, die Formeln für des Screens **Breite** und **Höhe** Eigenschaften stellen Sie sicher, dass ihre Werte groß werden, wird nicht mindestgebühren. In diesem Fall muss der Benutzer scrollen, um alle Inhalte des Bildschirms anzeigen.

Nachdem Sie Ihrer app herstellen **DesignWidth** und **DesignHeight**, Sie (in den meisten Fällen) müssen nicht so ändern Sie die Standardformel für jeden Bildschirm der **Breite** und **Höhe** Eigenschaften. Später wird dieses Thema Fälle, in denen Sie die folgenden Formeln anpassen möchten.

## <a name="use-formulas-for-dynamic-layout"></a>Verwenden von Formeln für dynamisches layout

Um ein reaktionsfähiges Design zu erstellen, suchen und die Größe jedes Steuerelement mithilfe von Formeln anstelle von absoluten (Konstante) Koordinatenwerte. Diese Formeln express-Position und Größe in Bezug auf die Größe des gesamten Bildschirms oder relativ zu anderen Steuerelementen auf dem Bildschirm des Steuerelements.

> [!IMPORTANT]
> Nach dem Erstellen von Formeln für die **X**, **Y**, **Breite** und **Höhe** Eigenschaften eines Steuerelements, die Formeln überschrieben werden mit Konstante Werte, wenn Sie das Steuerelement anschließend in der Canvas-Editor ziehen. Wenn Sie beginnen, Formeln verwenden, um das dynamische Layout zu erzielen, sollten Sie vermeiden, Ziehen von Steuerelementen.

Im einfachsten Fall füllt ein Steuerelement einen ganzen Bildschirm an. Um diesen Effekt zu erstellen, legen Sie die Eigenschaften des Steuerelements auf diese Werte ein:

| Eigenschaft      | Value            |
|--------|---------------|
| **X**      | 0             |
| **Y**      | 0             |
| **Width**  | `Parent.Width`  |
| **Höhe** | `Parent.Height` |

Diese Formeln verwenden Sie den Parent-Operator. Für ein Steuerelement direkt auf einem Bildschirm platziert wird bezieht sich auf dem Bildschirm übergeordnete Element. Mit diesen Eigenschaftswerten des Steuerelements angezeigt wird, in der oberen linken Ecke des Bildschirms (0, 0) und hat die gleiche **Breite** und **Höhe** als Bildschirm.

Weiter unten in diesem Thema werden Sie diese Prinzipien (und den Parent-Operator) zum Positionieren von Steuerelementen innerhalb von anderen Containern, z. B. Galerien, Gruppieren von Steuerelementen und Komponenten anwenden.

Als Alternative kann nur die obere Hälfte des Bildschirms das Steuerelement gefüllt werden. Um diesen Effekt zu erstellen, Ändern der **Höhe** -Formel auf **Parent.Height** / 2, und die andere Formeln, die unverändert lassen.

Wenn Sie ein zweites Steuerelement auf der unteren Hälfte der im gleichen Bildschirm ausfüllen möchten, können Sie über mindestens zwei Ansätzen nutzen, auf die Formeln erstellen. Der Einfachheit halber können Sie diesen Ansatz verwenden:

| Steuerelement | Eigenschaft | Formel           |
|-|----------|-------------------|
| **obere** | **X**        | 0                 |
| **obere** | **Y**        | 0                 |
| **obere** | **Width**    | `Parent.Width`      |
| **obere** | **Höhe**   | `Parent.Height / 2` |
| **niedrigere** | **X**        | 0                 |
| **niedrigere** | **Y**        | `Parent.Height / 2` |
| **niedrigere** | **Width**    | `Parent.Width`      |
| **niedrigere** | **Höhe**   | `Parent.Height / 2` |

![Obere und einer geringeren-Steuerelement](media/create-responsive-layout/dynamic-layout.png)

Diese Konfiguration würde den gewünschten Effekt erzielen, aber Sie müssen jede Formel zu bearbeiten, wenn Sie Ihre Meinung über die relative Größe der Steuerelemente geändert haben. Sie könnten z. B., dass das oberste Steuerelement nur die oberen Drittel des Bildschirms mit dem unteren-Steuerelement, füllen die unteren beiden Drittel einnehmen sollte. Um diesen Effekt zu erstellen, müssen Sie zum Aktualisieren der **Höhe** Eigenschaft der **oberen** Steuerelement und die **Y** und **Höhe** Eigenschaften der **Niedrigere** Steuerelement. Erwägen Sie stattdessen schreiben die Formeln für die **niedrigere** hinsichtlich der steuern die **oberen** -Steuerelement (und selbst), wie im folgenden Beispiel:

| Steuerelement | Eigenschaft | Formel           |
|-|----------|-------------------|
| **obere** | **X**        | 0                 |
| **obere** | **Y**        | 0                 |
| **obere** | **Width**    | `Parent.Width`      |
| **obere** | **Höhe**   | `Parent.Height / 2` |
| **niedrigere** | **X**        | 0                       |
| **niedrigere** | **Y**        | `Upper.Y + Upper.Height`  |
| **niedrigere** | **Width**    | `Parent.Width`            |
| **niedrigere** | **Höhe**   | `Parent.Height - Lower.Y` |

![Obere und untere steuert relativen Größen](media/create-responsive-layout/dynamic-layout2.png)

Diese Formeln vorhanden, benötigen Sie nur ändern der **Höhe** Eigenschaft der **oberen** Steuerelement zum Ausdrücken von eines anderen Bruchteil der Höhe des Bildschirms. Die **niedrigere** -Steuerelement automatisch verschoben wird, und ändert die Größe um die Änderung zu berücksichtigen.

Sie können diese Formel Muster verwenden, zum Ausdrücken von häufig Layout Beziehungen zwischen einem Steuerelement, mit dem Namen **C**, und das übergeordnete Element oder ein gleichgeordnetes Element-Steuerelement, mit dem Namen **D**.

| Beziehung zwischen C und seinem übergeordneten Element | Eigenschaft | Formel | Abbildung |
|--|--|--|--|
| **C** füllt die Breite des übergeordneten Elements, mit einem Rand von *N* | **X**| *N* | ![Beispiel C füllen Breite des übergeordneten Elements](media/create-responsive-layout/c1.png) |
|  | **Width** | `Parent.Width - (N * 2)` |  |
| **C** füllt der Höhe des übergeordneten Elements, mit einem Rand von *N* | **Y** | *N* | ![Beispiel für die C-füllen-Höhe des übergeordneten Elements](media/create-responsive-layout/c2.png) |
|  | **Höhe** | `Parent.Height - (N * 2)` |  |
| **C** rechten Rand des übergeordneten Elements, mit Rand ausgerichtet *N* | **X** | `Parent.Width - (C.Width + N)` | ![Beispiel C mit Kante des übergeordneten Elements](media/create-responsive-layout/c3.png) |
| **C** unteren Rand des übergeordneten Elements, mit Rand ausgerichtet *N* | **Y** | `Parent.Height - (C.Height + N)` | ![Beispiel C mit Kante des übergeordneten Elements](media/create-responsive-layout/c4.png) |
| **C** für übergeordnetes Element horizontal zentriert | **X** | `(Parent.Width - C.Width) / 2` | ![Beispiel C für übergeordnetes Element horizontal zentriert](media/create-responsive-layout/c5.png) |
| **C** auf übergeordnete vertikal zentriert | **Y** | `(Parent.Height - C.Height) / 2` | ![Beispiel C auf übergeordnete vertikal zentriert](media/create-responsive-layout/c6.png) |

| Beziehung zwischen C und D | Eigenschaft | Formel | Abbildung |
|--|--|--|--|
| **C** horizontal ausgerichtet **D** und dieselbe Breite wie **D** | **X** | `D.X` | ![Beispiel für Muster](media/create-responsive-layout/d1.png) |
|  | **Width**    | `D.Width` |  |
| **C** vertikal ausgerichtet **D** und derselben Höhe wie **D**  | **Y** | `D.Y` | ![Beispiel für Muster](media/create-responsive-layout/d2.png) |
|  | **Höhe** | `D.Height` |  |
| Rechte Kante des **C** rechten Rand ausgerichtet **D** | **X** | `D.X + D.Width - C.Width` | ![Beispiel für Muster](media/create-responsive-layout/d3.png) |
| Unteren Rand des **C** unteren Rand ausgerichtet **D** | **Y** | `D.Y + D.Height - C.Height` | ![Beispiel für Muster](media/create-responsive-layout/d4.png) |
| **C** horizontal zentriert, relativ zum **D** | **X** | `D.X + (D.Width - C.Width) / 2`  | ![Beispiel für Muster](media/create-responsive-layout/d5.png) |
| **C** vertikal zentriert, relativ zum **D** | **Y** | `D.Y + (D.Height - C.Height) /2` | ![Beispiel für Muster](media/create-responsive-layout/d6.png) |
| **C** positioniert auf der rechten Seite des **D** Abstand von N | **X** | `D.X + D.Width - N` | ![Beispiel für Muster](media/create-responsive-layout/d7.png) |
| **C** unten positioniert **D** Abstand von *N*             | **Y** | `D.Y + D.Height + N` | ![Beispiel für Muster](media/create-responsive-layout/d8.png) |
| **C** füllt Leerzeichen zwischen **D** und Rechte Kante des übergeordneten Elements | **X** | `D.X + D.Width` | ![Beispiel für Muster](media/create-responsive-layout/d9.png) |
|  | **Width** | `Parent.Width - C.X` |  |
| **C** füllt Leerzeichen zwischen **D** und unteren Rand des übergeordneten Elements | Y | `D.Y + D.Height` | ![Beispiel für Muster](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>Hierarchischer Anordnung

Wie Sie Bildschirme, die weitere Steuerelemente enthalten erstellen, wird es zum bequemer (oder sogar notwendig) so positionieren Sie Steuerelemente relativ zu einem übergeordneten Steuerelement und nicht relativ zum Bildschirm oder ein gleichgeordnetes Element-Steuerelement. Durch die Steuerelemente in einer hierarchischen Struktur organisieren, können Sie, Ihre Formeln einfacher schreiben und verwalten.

### <a name="galleries"></a>Galerien

Wenn Sie einen Katalog in Ihrer app verwenden, müssen Sie das Layout von Steuerelementen innerhalb der Vorlage des Katalogs. Sie können diese Steuerelemente positionieren, durch das Schreiben von Formeln, die den Parent-Operator verwenden, die auf den Katalog: Vorlage verweisen wird. Verwenden Sie in den Formeln für Steuerelemente innerhalb einer Katalogvorlage die Parent.TemplateHeight und Parent.TemplateWidth Eigenschaften ein. Verwenden Sie diese anstelle von Parent.Width und Parent.Height, die sich auf die Gesamtgröße des Katalogs beziehen.

![Vertikalen Katalog mit Vorlagenbreite und Höhe](media/create-responsive-layout/gallery-vertical.png)

### <a name="enhanced-group-control"></a>Erweiterte Group-Steuerelement

Können Sie eine experimentelle Funktion, die verbesserten **Gruppe** Steuerelement als übergeordnetes Steuerelement. Um dieses Feature zu aktivieren, wählen Sie **Datei** > **Anwendungseinstellungen** > **Erweiterte Einstellungen**.

Betrachten Sie das Beispiel einen Header am oberen Rand eines Bildschirms. Es ist üblich, die kein Header mit einem Titel und einige Symbole, mit denen Ihre Benutzer interagieren können. Sie können solche einen Header, die mithilfe der erweiterten erstellen **Gruppe** zu steuern, mit einer **Bezeichnung** -Steuerelements und zweier **Symbol** Steuerelemente:

![Headerbeispiel mithilfe einer Gruppe](media/create-responsive-layout/header-group.png)

Legen Sie die Eigenschaften für diese Steuerelemente, um diese Werte:

| Eigenschaft | Header | Menü " | Schließen | Title |
|--|--|--|--|--|
| **X** | 0  | 0 | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **Y** | 0 | 0 | 0 | 0 |
| **Width**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **Höhe** | 64 | `Parent.Height` | `Parent.Height` | `Parent.Height` |

Für die **Header** Steuerelement `Parent` bezieht sich auf dem Bildschirm. Für die anderen `Parent` bezieht sich auf die **Header** Steuerelement.

Diese Formeln schreiben, können Sie die Größe oder Position der Anpassen der **Header** durch Ändern von Formeln für die zugehörigen Eigenschaften. Die Größen und Positionen der untergeordneten Steuerelemente werden automatisch entsprechend angepasst.

### <a name="components"></a>Komponenten

Bei Verwendung einer anderen experimentelles Feature, benannte Komponenten sind können Bausteine erstellen und sie in der gesamten app wiederverwenden. Wie bei der **Gruppe** -Steuerelement die Steuerelemente, die Sie innerhalb einer Komponente platzieren sollten als Grundlage für ihre Position und Größe Formeln `Parent.Width` und `Parent.Height`, beziehen sich auf die Größe der Komponente. Weitere Informationen finden Sie unter: [Erstellen einer Komponente](create-component.md)

## <a name="adapting-layout-for-device-size-and-orientation"></a>Layout für das GeräteGröße und Ausrichtung anpassen

Bisher haben Sie gelernt, wie Sie Formeln verwenden, Ändern des Steuerelements Größe als Reaktion auf den verfügbaren Platz, halten die Steuerelemente im Verhältnis zueinander ausgerichtet werden sollen. Aber Sie möchten oder müssen Sie erhebliche Änderungen am Layout als Reaktion auf verschiedene gerätegrößen und -Ausrichtungen. Wenn ein Gerät vom Hochformat zum Querformat gedreht wird, sollten Sie z. B. in eine horizontale aus einem vertikalen Layout wechseln. Auf ein größeres Gerät können Sie weitere Inhalte zu präsentieren oder neu anordnen, um ein attraktiver Layout zu bieten. Auf einem kleineren Gerät müssen Sie Inhalte auf mehrere Bildschirme aufzuteilen.

### <a name="device-orientation"></a>Geräteausrichtung

Die Standardformel für eines Bildschirms des **Breite** und **Höhe** Eigenschaften, wie in diesem Artikel, die zuvor beschriebenen wird nicht unbedingt bieten eine gute Erfahrung, wenn ein Benutzer ein Gerät dreht. Eine app für ein Telefon im Hochformat verfügt beispielsweise über eine **DesignWidth** von 640 und ein **DesignHeight** von 1136. Die gleiche app auf einem Smartphone im Querformat verfügen diese Eigenschaftswerte:

- Des Bildschirms **Breite** -Eigenschaftensatz auf `Max(App.Width, App.DesignWidth)`. Der app **Breite** (1136) ist größer als die **DesignWidth** (640), sodass die Formel 1136 ausgewertet wird.
- Des Bildschirms **Höhe** -Eigenschaftensatz auf `Max(App.Height, App.DesignHeight)`. Der app **Höhe** (640) ist kleiner als die **DesignHeight** (1136), sodass die Formel 1136 ausgewertet wird.

Mit einem Bildschirm **Höhe** von 1136 und eine Geräte-Höhe (in diesem Ausrichtung) von 640, muss der Benutzer den Bildschirm vertikal aus, damit alle seinen Inhalt angezeigt, die die Umgebung möglicherweise nicht die gewünschten scrollen.

Anpassen des Bildschirms **Breite** und **Höhe** Eigenschaften, die Ausrichtung, können Sie diese Formeln:

**Breite** = `Max(App.Width, If(App.Width < App.Height, App.DesignWidth, App.DesignHeight))`

**Höhe** = `Max(App.Height, If(App.Width < App.Height, App.DesignHeight, App.DesignWidth))`

Diese Formeln Tauschen der app **DesignWidth** und **DesignHeight** Werte, je nachdem, ob das Gerät die Breite kleiner als die Höhe (Hochformat) oder größer als die Höhe (Querformat) ist .

Nach dem Anpassen des Bildschirms **Breite** und **Höhe** Formeln die, Sie möglicherweise auch Steuerelemente in dem Bildschirm, um den verfügbaren Platz besser einzusetzen neu anordnen möchten. Wenn jeder von zwei Steuerelementen Hälfte des Bildschirms einnimmt, können Sie z. B. vertikal gestapelt, im Hochformat jedoch ordnen Sie sie nebeneinander im Querformat.

> [!NOTE]
> Im Querformat die **oberen** und **niedrigere** Steuerelemente, die als linken und rechten Steuerelemente angezeigt werden.

| Steuerelement | Eigenschaft | Formel |
|--|----------|---|
| **obere** | **X** | 0 |
| **obere** | **Y** | 0 |
| **obere** | **Width** | `If(Parent.Width < Parent.Height, Parent.Width, Parent.Width / 2)` |
| **obere** | **Höhe**   | `If(Parent.Width < Parent.Height, Parent.Height / 2, Parent.Height)` |
| **niedrigere** | X | `If(Parent.Width < Parent.Height, 0, Upper.X + Upper.Width)`  |
| **niedrigere** | Y | `If(Parent.Width < Parent.Height, Upper.Y + Upper.Height, 0)` |
| **niedrigere** | **Width** | `Parent.Width - Lower.X` |
| **niedrigere** | **Höhe** | `Parent.Height - Lower.Y` |

![Ausdrücke Hochformat anpassen.](media/create-responsive-layout/portrait.png)

![Ausdrücke, die ein Querformat anpassen](media/create-responsive-layout/landscape.png)

### <a name="known-limitations"></a>Bekannte Einschränkungen

Im erstellungsbereich Zeichenbereich reagiert nicht auf die größenanpassung-Formeln erstellt. Um reaktionsfähige Verhalten zu testen, speichern Sie und veröffentlichen Sie Ihre app, und öffnen Sie sie auf Geräten oder im Browserfenster verschiedener Größe und Ausrichtung.

Wenn Sie Ausdrücke oder Formeln im Schreiben der **X**, **Y**, **Breite**, und **Höhe** Eigenschaften eines Steuerelements, müssen Sie diese überschreiben Ausdrücke oder Formeln, wenn Sie später das Steuerelement an eine andere Stelle ziehen oder die Größe des Steuerelements durch Ziehen des Rahmens.
