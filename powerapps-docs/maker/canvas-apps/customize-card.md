---
title: Anpassen einer Karte in einer Canvas-App | Microsoft-Dokumentation
description: Ändern des Standard Steuer Elements, das auf einer Karte in einem Detail-oder Bearbeitungs Formular in einer Canvas-App angezeigt wird
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5bcf1515f72bdce0872f91c64b5ac4fe5028ee2c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985915"
---
# <a name="customize-a-card-in-a-canvas-app"></a>Anpassen einer Karte in einer Canvas-App

Führen Sie eine grundlegende Anpassung (ohne Entsperren einer Karte) durch, indem Sie beispielsweise das Steuerelement ändern. Erweiterte Anpassung (mit Aufheben der Sperre einer Karte), indem Sie z.B. ein Steuerelement hinzufügen, das für diese Karte standardmäßig nicht verfügbar ist.

Eine Übersicht finden Sie unter [Grundlegendes zu Datenkarten](working-with-cards.md).

## <a name="prerequisites"></a>Voraussetzungen

- Grundlegende Informationen zum [Hinzufügen und Konfigurieren von Steuerelementen](add-configure-controls.md).
- Sie können dieses Thema nur auf allgemeine Konzepte überprüfen, oder Sie können es Schritt für Schritt befolgen, wenn Sie die Verfahren in den folgenden Themen ausführen:

    1. [Generate an app (Generieren einer App)](data-platform-create-app.md)
    1. [Customize its gallery (Anpassen des Katalogs)](customize-layout-sharepoint.md)
    1. [Customize its forms (Anpassen der Formulare)](customize-forms-sharepoint.md)

## <a name="customize-a-locked-card"></a>Anpassen einer gesperrten Karte

In diesem Verfahren ersetzen Sie ein **[Text Eingabe-](controls/control-text-input.md)** Steuerelement durch einen **[Schieberegler] (Steuerelemente/Steuerelement-Schieberegler. MD-** Steuerelement, ohne die Karte zu entsperren.

1. Wählen Sie in der APP, die Sie generiert und angepasst haben, in der linken Navigationsleiste **EditForm1** aus, und klicken Sie dann auf der Registerkarte **Eigenschaften** des rechten Bereichs auf **Felder bearbeiten** .

1. Wählen Sie in der Liste der Felder den Pfeil nach unten für **Anzahl von Mitarbeitern**aus, und öffnen Sie dann die Liste unter **Steuerungstyp**.

    > [!div class="mx-imgBorder"]
    > ![dropdown Liste mit Optionen für eine zahlenkarte @ no__t-1

1. Wählen Sie **Schieberegler bearbeiten**aus.

    Der Bildschirm spiegelt die vorgenommene Änderung wider.

    > [!div class="mx-imgBorder"]
    > ![editform1 mit Schieberegler-Steuerelement @ no__t-1

## <a name="unlock-and-customize-a-card"></a>Entsperren und Anpassen einer Karte

In diesem Verfahren entsperren Sie eine Karte und aktualisieren die Eigenschaft **Max** des **Schieberegler** -Steuer Elements, das Sie soeben hinzugefügt haben.

1. Wählen Sie in **EditForm1**das **Schieberegler** -Steuerelement auf der Karte **Anzahl von Mitarbeitern** aus.

    > [!div class="mx-imgBorder"]
    > ![wählen Sie den Schieberegler @ no__t-1 aus.

1. Wählen Sie im rechten Bereich auf der Registerkarte **erweitert** das Sperrsymbol aus, um die Karte zu entsperren.

    > [!div class="mx-imgBorder"]
    > ![unlock Karte @ no__t-1

1. Legen Sie die Eigenschaft **Max** des **Schieberegler** -Steuer Elements auf 10.000 fest.

    > [!div class="mx-imgBorder"]
    > ![max-Eigenschaft auf der Registerkarte "Erweitert" @ no__t-1

    Das **Schieberegler** -Steuerelement zeigt einen genaueren Wert an.

    > [!div class="mx-imgBorder"]
    > Bereich für ![slider: 0-10000 @ no__t-0

## <a name="next-steps"></a>Nächste Schritte

Da Sie jetzt einen grundlegenden Überblick darüber haben, wie Sie eine App generieren und einen Katalog, ein Formular und eine Karte anpassen können, sollten Sie Ihre [App von Grund auf neu erstellen können](data-platform-create-app-scratch.md).