---
title: Anpassen einer Karte in einer Canvas-app | Microsoft-Dokumentation
description: Ändern des Standardsteuerelements, das in einer Karte in einem Details-angezeigt wird oder Edit-Formular in einer Canvas-app
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ddc1c677ed95caf10d8cd6e0e7e12e6aaf88a0f5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61559801"
---
# <a name="customize-a-card-in-a-canvas-app"></a>Anpassen einer Karte in einer Canvas-app

Führen Sie eine grundlegende Anpassung (ohne Entsperren einer Karte) durch, indem Sie beispielsweise das Steuerelement ändern. Erweiterte Anpassung (mit Aufheben der Sperre einer Karte), indem Sie z.B. ein Steuerelement hinzufügen, das für diese Karte standardmäßig nicht verfügbar ist.

Eine Übersicht finden Sie unter [Grundlegendes zu Datenkarten](working-with-cards.md).

## <a name="prerequisites"></a>Voraussetzungen

- Grundlegende Informationen zum [Hinzufügen und Konfigurieren von Steuerelementen](add-configure-controls.md).
- Sie können in diesem Thema zur allgemeinen Information verwenden oder folgen sie Schritt für Schritt Durcharbeiten der Verfahren in den folgenden Themen:

    1. [Generate an app (Generieren einer App)](data-platform-create-app.md)
    1. [Customize its gallery (Anpassen des Katalogs)](customize-layout-sharepoint.md)
    1. [Customize its forms (Anpassen der Formulare)](customize-forms-sharepoint.md)

## <a name="customize-a-locked-card"></a>Anpassen einer gesperrten Karte

Ersetzen Sie in diesem Verfahren eine **[Texteingabe-](controls/control-text-input.md)** steuern Sie mit einem **[Schieberegler] (Steuerelemente/Steuerelement-slider.md** Steuerelement ohne die Karte zu entsperren.

1. Wählen Sie in der app, die Sie generiert und angepasst, **EditForm1** im linken Navigationsbereich, und klicken Sie anschließend **Bearbeitungsfelder** auf die **Eigenschaften** Registerkarte im rechten Bereich.

1. Wählen Sie in der Liste der Felder, die den Pfeil nach unten **Number of Employees**, und öffnen Sie dann die Liste unter **Steuerelementtyp**.

    > [!div class="mx-imgBorder"]
    > ![Dropdown-Liste von Optionen für eine zahlenkarte](./media/customize-card/card-selector.png)

1. Wählen Sie **Schieberegler bearbeiten**.

    Der Bildschirm spiegelt die vorgenommene Änderung wider.

    > [!div class="mx-imgBorder"]
    > ![EditForm1 mit Schieberegler-Steuerelement](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>Entsperren und Anpassen einer Karte

In diesem Verfahren entsperren Sie eine Karte und aktualisieren Sie die **Max** Eigenschaft der **Schieberegler** -Steuerelement, das Sie gerade hinzugefügt haben.

1. In **EditForm1**, wählen die **Schieberegler** steuern, der **Number of Employees** Karte.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie den Schieberegler](./media/customize-card/select-slider.png)

1. Auf der **erweitert** Registerkarte im rechten Bereich, wählen Sie das Schlosssymbol, um die Karte zu entsperren.

    > [!div class="mx-imgBorder"]
    > ![Karte zu entsperren](./media/customize-card/lock-icon.png)

1. Legen Sie die **Max** Eigenschaft der **Schieberegler** Steuerelement auf 10.000.

    > [!div class="mx-imgBorder"]
    > ![Max-Eigenschaft auf der Registerkarte "Erweitert"](./media/customize-card/max-property.png)

    Die **Schieberegler** Steuerelement zeigt einen genaueren Wert.

    > [!div class="mx-imgBorder"]
    > ![Schieberegler liegen im Bereich: 0-10,000](./media/customize-card/final-slider.png)

## <a name="next-steps"></a>Nächste Schritte

Da Sie jetzt einen grundlegenden Überblick darüber haben, wie Sie eine App generieren und einen Katalog, ein Formular und eine Karte anpassen können, sollten Sie Ihre [App von Grund auf neu erstellen können](data-platform-create-app-scratch.md).