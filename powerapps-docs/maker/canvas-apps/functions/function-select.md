---
title: Funktion „Select“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktion „Select“ in Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/08/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 12e0f7e33487d5a274dea8bf666ed7d539284e92
ms.sourcegitcommit: db62bf0f8210b5ba2d1d5fc2c7d362ab23ec8c63
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2020
ms.locfileid: "76315421"
ms.PowerAppsDecimalTransform: true
---
# <a name="select-function-in-power-apps"></a>Funktion „Select“ in Power Apps
Simuliert eine Auswahlaktion für ein Steuerelement, sodass die Formel **OnSelect** ausgewertet wird.

## <a name="description"></a>Beschreibung
Die Funktion **Select** simuliert eine Auswahlaktion für ein Steuerelement, so als ob der Benutzer auf das Steuerelement geklickt oder getippt hätte. Dadurch wird die Formel **OnSelect** für das Zielsteuerelement ausgewertet.

Verwenden Sie **Select**, um eine Auswahlaktion an ein übergeordnetes Steuerelement weiterzugeben. Dieser Typ von Weitergabe ist das Standardverhalten z.B. in Galerien. Standardmäßig ist die Eigenschaft **OnSelect** eines Steuerelements in einem **[Katalogsteuerelement](../controls/control-gallery.md)** auf **Select( Parent )** festgelegt. Auf diese Weise können Sie den Wert der Eigenschaft **OnSelect** des Katalogsteuerelements selbst festlegen, und die Formel wird unabhängig davon ausgewertet, wo im Katalog ein Benutzer möglicherweise klickt oder tippt.

Wenn ein oder mehrere Steuerelemente im Katalog andere Aktionen als der Katalog selbst ausführen sollen, legen Sie die Eigenschaft **OnSelect** für diese Steuerelemente auf einen anderen Wert als den Standardwert fest. Sie können die Standardwerte für die Eigenschaft **OnSelect** der meisten Steuerelemente im Katalog unverändert lassen, wenn sie die gleiche Aktion wie der Katalog selbst ausführen sollen.

Mit **Select** wird das Ziel-**OnSelect** zur späteren Verarbeitung in die Warteschlange aufgenommen. Die Verarbeitung könnte erfolgen, nachdem die aktuelle Formel ausgewertet wurde. **Select** führt nicht dazu, dass das Ziel-**OnSelect** sofort ausgewertet wird, und **Select** wartet auch nicht den Abschluss der **OnSelect**-Auswertung ab.

Sie können **Select** nicht über mehrere Bildschirme verwenden.

Sie können **Select** nur für Steuerelemente nutzen, die eine **OnSelect**-Eigenschaft aufweisen.

Verwenden Sie **Select** nur in [Verhaltensformeln](../working-with-formulas-in-depth.md).

**Select** kann nicht direkt oder indirekt über andere Steuerelemente für ein Steuerelement selbst verwendet werden.

Die Funktion „Select“ kann auch mit einem Katalog verwendet werden. Beispielsweise kann sie verwendet werden, um die Zeile oder Spalte, die in einem Katalog ausgewählt werden soll, und das Steuerelement, das in dieser Zeile oder Spalte des Katalogs ausgewählt werden soll, anzugeben. Wenn Sie eine Zeile oder Spalte auswählen, ändert sich die Katalogauswahl, und die Formel **OnSelect** im Katalogsteuerelement wird ausgewertet. Wenn ein Steuerelement innerhalb der Zeile oder Spalte bereitgestellt wird, wird die **OnSelect**-Formel für das untergeordnete Steuerelement ausgewertet. 

## <a name="syntax"></a>Syntax
**Select**(*Steuerelement*)

* *Steuerelement* – Erforderlich.  Das Steuerelement, das für den Benutzer ausgewählt werden soll.

**Select** (*Steuerelement, Zeile oder Spalte, untergeordnetes Steuerelement*)

- *Steuerelement* – Erforderlich. Das Steuerelement, das für den Benutzer ausgewählt werden soll.
- *Zeile oder Spalte* – Nicht erforderlich. Die Anzahl der Zeilen oder Spalten (beginnend mit 1) in einer Katalogsteuerung, die für den Benutzer ausgewählt werden sollen.
- *Untergeordnetes Steuerelement* – Nicht erforderlich. Das untergeordnete Element des Steuerelements, das im Parameter „Steuerelement“ identifiziert wird und ausgewählt werden soll. 

## <a name="examples"></a>Beispiele

- *Schaltfläche*

    ```Select(button1)```

- *Katalog* 

    ```Select(Gallery1; 1)```

    Simuliert einen Benutzer, der Zeile 1 oder Spalte 1 in Gallery1 auswählt. 

- *Katalog* 

    ```Select(Gallery1; 1; ChildControl1)```

    Simuliert einen Benutzer, der ChildConttrol1 in Zeile 1 oder Spalte 1 von Gallery1 auswählt.

#### <a name="basic-usage"></a>Grundlegende Nutzung

1. Fügen Sie ein **[Schaltflächen](../controls/control-button.md)**-Steuerelement hinzu, und benennen Sie es in **Button1** um, wenn es nicht bereits so heißt.

1. Legen Sie die Eigenschaft **OnSelect** von **Button1** auf die folgende Formel fest:

    **Notify( "Hello World" )**

1. Fügen Sie auf dem gleichen Bildschirm ein zweites **Schaltflächen**-Steuerelement hinzu, und legen Sie dessen Eigenschaft **OnSelect** auf diese Formel fest:

    **Select( Button1 )**

1. Halten Sie die ALT-TASTE gedrückt, und wählen Sie die zweite Schaltfläche aus.

    Eine Benachrichtigung wird oben in der App angezeigt. Die Eigenschaft **OnSelect** von **Button1** hat diese Benachrichtigung generiert.

    ![Eine Animation, in der die Eigenschafteneinstellungen von „OnSelect“ für die zwei Schaltflächen und die Benachrichtigung angezeigt werden, wenn auf die zweite Schaltfläche geklickt wird](media/function-select/basic-select.gif)

#### <a name="gallery-control"></a>Katalogsteuerelement

1. Fügen Sie ein Steuerelement für einen vertikalen **[Katalog](../controls/control-gallery.md)** hinzu, der weitere Steuerelemente enthält.

    ![Einen vertikalen Katalog auswählen, der Steuerelemente enthält](media/function-select/select-gallery.png)

2. Legen Sie die Eigenschaft **OnSelect** des Katalogs auf die folgende Formel fest:
 
    **Notify( "Gallery Selected" )**

3. Während Sie die ALT-TASTE gedrückt halten, klicken oder tippen Sie auf den Hintergrund des Katalogs oder auf ein Steuerelement im Katalog.

    Bei allen Aktionen wird die Benachrichtigung **Gallery Selected** oben in der App angezeigt.

    Verwenden Sie die Eigenschaft **OnSelect** des Katalogs, um die Standardaktion anzugeben, die ausgeführt wird, wenn der Benutzer auf ein Element im Katalog klickt oder tippt.

5. Legen Sie die Eigenschaft **OnSelect** des Bildsteuerelements auf die folgende Formel fest:

    **Notify( "Image Selected"; Success )**

6. Während Sie die ALT-TASTE gedrückt halten, klicken oder tippen Sie auf die verschiedenen Elemente des Katalogs.

    Beim Klicken oder Tippen auf alle Steuerelemente im Katalog mit Ausnahme des Bilds wird wie zuvor **Gallery Selected** angezeigt. Wenn Sie auf das Bild klicken oder tippen, wird **Image Selected** angezeigt.
 
    Verwenden Sie einzelne Steuerelemente im Katalog, um Aktionen auszuführen, die sich von der Standardaktion des Katalogs unterscheiden.

    ![Eine Animation, die den Standardwert der Eigenschaft „OnSelect“ für ein Katalogsteuerelement sowie ein Steuerelement darstellt, das eine andere Aktion ausführt](media/function-select/gallery-select.gif)

7. Fügen Sie auf dem gleichen Bildschirm ein **Schaltflächen**-Steuerelement hinzu, und legen Sie dessen Eigenschaft **OnSelect** auf diese Formel fest:

    **Select( Gallery1;2;Image1 )**

8. Halten Sie die ALT-TASTE gedrückt, und wählen Sie die Schaltfläche aus.
   
     Eine Benachrichtigung **Image Selected** (Bild ausgewählt) wird oben in der App angezeigt. Durch Klicken auf die Schaltfläche haben Sie das Bild in Zeile 2 des Katalogs ausgewählt.  

