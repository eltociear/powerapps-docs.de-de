---
title: Tutorial zum Anpassen eines Katalogs | Microsoft-Dokumentation
description: In diesem Tutorial erfahren Sie, wie Sie in einer in PowerApps generierten App den Standbildschirm zum Durchsuchen mitsamt des Katalogs anpassen.
services: ''
suite: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/11/2018
ms.author: anneta
ms.openlocfilehash: 30ec6be11b40e01dddfe09cf0ac8af0ed3a8a437
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>Tutorial: Anpassen eines Katalogs in PowerApps
In diesem Tutorial erfahren Sie, wie Sie in einer in PowerApps generierten App den Standardbildschirm zum Durchsuchen mitsamt des Katalogs anpassen. Sie können zwar mithilfe der Standard-App Daten verwalten, ohne diese anzupassen, es ist jedoch viel einfacher – und Sie erzielen bessere Ergebnisse –, wenn Sie die folgenden Änderungen vornehmen:

> [!div class="checklist"]
> * Ändern des Layouts
> * Ändern der angezeigten Daten
> * Festlegen der Spalten zum Filtern und Sortieren
> * Filtern und Sortieren von Tests
> * Ändern des Titels
> * Anzeigen einer Scrollleiste

In diesem Tutorial wird zwar zunächst eine App verwendet, die über [Common Data Service für Apps](../common-data-service/data-platform-intro.md) generiert wurde, es gelten jedoch für Apps, die über SharePoint, Excel und andere Datenquellen generiert wurden, die gleichen Konzepte. 

Wenn Sie nicht über eine Lizenz für PowerApps verfügen, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Voraussetzungen
Bevor Sie mit diesem Tutorial beginnen, [generieren Sie eine App](data-platform-create-app.md) über Common Data Service für Apps.

## <a name="open-the-generated-app"></a>Öffnen einer generierten App
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an, und klicken oder tippen Sie dann am linken Bildschirmrand auf **Apps**.

    ![PowerApps-Startseite](./media/customize-layout-sharepoint/sign-in.png)

1. Suchen Sie die App, die Sie generiert haben, und klicken oder tippen Sie daneben am linken Bildschirmrand auf die Auslassungszeichen (**...**).

    ![App-Liste](./media/customize-layout-sharepoint/open-for-edit.png)

1. Klicken oder tippen Sie in dem Menü, das angezeigt wird, auf die Option zum Bearbeiten der App. 

## <a name="customize-the-gallery"></a>Anpassen des Katalogs
1. Klicken oder tippen Sie in der Liste der Konten auf dem Bildschirm zum Durchsuchen auf alle Elemente bis auf das erste Element.

    In diesem Schritt wird das Steuerelement **Katalog** ausgewählt, das die Liste der Konten anzeigt.

    ![Ausgewählter Katalog](./media/customize-layout-sharepoint/select-gallery.png)

1. Klicken oder tippen Sie rechts neben der Bezeichnung **Daten** auf **Konten**.

    ![Öffnen Sie den Bereich **Daten**](./media/customize-layout-sharepoint/open-data-pane.png)

1. Klicken oder tippen Sie im Bereich **Daten** auf den Pfeil nach unten, um unter **Layouts** die Liste der Optionen zu öffnen.

    ![Layoutoptionen anzeigen](./media/customize-layout-sharepoint/show-layouts.png)

1. Klicken oder tippen Sie in der Liste der Optionen auf die Option, die nur einen Titel anzeigt.

    ![Layout auswählen, das nur von Titeln ausgeht](./media/customize-layout-sharepoint/choose-layout.png)

1. Klicken oder tippen Sie im Bereich **Daten** auf den Pfeil nach unten, um für den jeweiligen Titel die Liste der Optionen zu öffnen.

    ![Layout auswählen, das nur von Titeln ausgeht](./media/customize-layout-sharepoint/show-title-options.png)

1. Klicken oder tippen Sie in der Liste der Optionen auf **Name**, um die Daten im Steuerelement **Katalog** anzuzeigen.

    ![Endgültiger Katalog](./media/customize-layout-sharepoint/final-gallery.png)


## <a name="set-the-sort-and-search-columns"></a>Sortier- und Suchspalten festlegen
1. Wählen Sie wie im vorherigen Abschnitt beschrieben das Steuerelement **Katalog** aus.

    ![Katalog auswählen](./media/customize-layout-sharepoint/select-gallery-title.png)

2. Stellen Sie sicher, dass die Eigenschaftenliste in der Nähe der oberen linken Ecke **Items** anzeigt.

    ![Items-Eigenschaft](./media/customize-layout-sharepoint/items-property.png)

    Der Wert dieser Eigenschaft in der Bearbeitungsleiste bestimmt nicht nur die Datenquelle des Katalogs, sondern auch die Filter- und Sortierspalten.

1. Ersetzen Sie in der Bearbeitungsleiste beide Instanzen von **emailaddress1** durch **name**, und setzen Sie weiter alle Instanzen in doppelte Anführungszeichen.

    Die Formel sollte dem folgenden Beispiel entsprechen:

    ![Formel für die Items-Eigenschaft](./media/customize-layout-sharepoint/items-value.png)

    Die erste Instanz von **name** gibt an, dass der Benutzer die Liste so filtern kann, dass nur die Einträge angezeigt werden, zu denen der Kontoname Text beinhaltet, den der Benutzer in die Suchleiste eingegeben hat. Die zweite Instanz von **name** gibt an, dass der Benutzer die Liste alphabetisch anhand der Kontonamen sortieren kann. Weitere Informationen zu diesen und anderen Funktionen finden Sie unter [formula reference (Formelreferenz)](formula-reference.md).

## <a name="test-sorting-and-searching"></a>Testen von Sortieren und Suchen
1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Klicken oder Tippen der Schaltfläche „Wiedergabe“ in der Nähe der oberen rechten Ecke).

    ![Öffnen des Vorschaumodus](./media/customize-layout-sharepoint/open-preview.png)

1. Klicken oder tippen Sie In der oberen rechten Ecke des Bildschirms zum Durchsuchen mindestens einmal auf die Schaltfläche „Sortieren“, um die Einträge alphabetisch in aufsteigender oder absteigender Reihenfolge zu sortieren.

    ![Die Schaltfläche „Sortieren“ testen](./media/customize-layout-sharepoint/sort-button.png)

1. Geben Sie im Suchfeld den Buchstaben **k** ein, damit nur die Konten angezeigt werden, deren Namen diesen Buchstaben enthalten.

    ![Testen der Suchleiste](./media/customize-layout-sharepoint/test-filter.png)

1. Löschen Sie den Text aus der Suchleiste. Schließen Sie anschließend den Vorschaumodus durch Drücken der ESC-TASTE (oder durch Klicken oder Tippen auf das Schließen-Symbol *unter* der Titelleiste für PowerApps).

## <a name="change-the-title-of-the-screen"></a>Ändern des Bildschirmtitels
1. Klicken oder tippen Sie auf den Titel des Bildschirms, um ihn auszuwählen.

    ![Auswählen des Bildschirmtitels](./media/customize-layout-sharepoint/select-title.png)

1. Stellen Sie sicher, dass die Eigenschaftenliste **Text** anzeigt, und geben Sie anschließend in der Bearbeitungsleiste den Begriff **Durchsuchen** in Anführungszeichen ein.

    ![Aktualisieren des Bildschirmtitels](./media/customize-layout-sharepoint/change-screen-title.png)

    Der Bildschirm spiegelt die vorgenommene Änderung wider.

    ![Neuer Bildschirmtitel](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scroll-bar"></a>Anzeigen einer Scrollleiste
Wenn es sein kann, dass die Geräte Ihre Benutzer weder über Touchscreens noch über Mausräder verfügen, konfigurieren Sie das Steuerelement **Katalog** so, dass eine Scrollleiste angezeigt wird, wenn der Benutzer mit der Maus darauf zeigt. So können Benutzer sogar alle Konten abrufen, wenn auf dem Bildschirm nicht alle Konten gleichzeitig angezeigt werden können.

1. Wählen Sie wie obenstehend beschrieben das Steuerelement **Katalog** aus.

    ![Katalog auswählen](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. Klicken oder tippen Sie auf der Registerkarte **Katalog** auf **Scrollleiste anzeigen**, und überprüfen Sie, ob der Wert der Eigenschaft sich in **TRUE** geändert hat. 

    ![Scrollleiste anzeigen](./media/customize-layout-sharepoint/show-scrollbar.png)

## <a name="next-steps"></a>Nächste Schritte
Sie haben in diesem Tutorial erfahren, wie Sie das Steuerelement **Katalog** und für eine App den Titel des Standardbildschirms zum Durchsuchen generieren. Sie können außerdem die Standardanzeigen anpassen, damit Details angezeigt sowie Konten erstellt und aktualisiert werden können. Diese Anzeigen enthalten jeweils ein **Formular anzeigen**-Steuerelement und ein **Formular bearbeiten**-Steuerelement. Über diese Steuerelemente können Sie z.B. ändern, welche Datentypen in welcher Reihenfolge angezeigt werden sollen.

> [!div class="nextstepaction"]
> [Customize forms (Formulare anpassen)](customize-forms-sharepoint.md)