---
title: Betrachten einer generierten App (SharePoint-Liste) | Microsoft-Dokumentation
description: Untersuchen von Bildschirmen und Steuerelementen in einer App
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: OJ8a9VINeKU
courseduration: 5m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: b6a6597970845aa16e75d83468a987992692c561
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="explore-the-generated-app-sharepoint-list"></a>Betrachten der generierten App (SharePoint-Liste)
In diesem Thema wird die generierte App genauer betrachtet, indem wir die Bildschirme und Steuerelemente durchgehen, die das Verhalten der App steuern. Dabei wird nicht auf alle Details eingegangen, die Einblicke in die Funktionsweise dieser App werden Ihnen aber beim Erstellen Ihrer eigenen Apps nützlich sein. In einem der folgenden Themen betrachten wir die Formeln, die mit Bildschirmen und Steuerelementen verwendet werden.

## <a name="understanding-controls-in-powerapps"></a>Grundlegendes zu Steuerelementen in PowerApps
Ein Steuerelement ist einfach ein Benutzeroberflächenelement, dem ein bestimmtes Verhalten zugeordnet wird. Viele Steuerelemente in PowerApps sind identisch mit Steuerelementen, die Sie bereits in anderen Apps verwendet haben: Bezeichnungen, Texteingabefelder, Dropdownlisten, Navigationselemente usw. In PowerApps gibt es aber auch spezialisiertere Steuerelemente wie **Galerien** (zum Anzeigen von Zusammenfassungsdaten) und **Formulare** (für Detaildaten und zum Erstellen und Bearbeiten von Elementen). Außerdem gibt es einige andere praktische Steuerelemente wie **Bild**, **Kamera** und **Barcode**. Klicken oder tippen Sie zum Anzeigen der verfügbaren Optionen im Menüband auf **Einfügen** und dann auf die verschiedenen Optionen wie **Text** oder **Symbole**.

![Registerkarte „Steuerelemente“ im PowerApps Studio-Menüband](./media/learning-spo-app-explore-controls/ribbon-controls.png)

## <a name="explore-the-browse-screen"></a>Elemente des Bildschirms zum Durchsuchen
Jeder der drei App-Bildschirme verfügt über ein Hauptsteuerelement sowie einige zusätzliche Steuerelemente. Der erste Bildschirm in der App ist der Bildschirm zum Durchsuchen, dem standardmäßig der Name **BrowseScreen1** zugewiesen ist. Das Hauptsteuerelement auf diesem Bildschirm ist eine Galerie mit dem Namen **BrowseGallery1**. **BrowseGallery1** enthält andere Steuerelemente wie z.B. **NextArrow1** (ein Symbolsteuerelement – durch Klicken oder Tippen wird der Detailbildschirm aufgerufen). Es gibt auch separate Steuerelemente auf dem Bildschirm z.B. **IconNewItem1** (ein Symbolsteuerelement – durch Klicken oder Tippen wird ein Element auf dem Bildschirm zum Bearbeiten/Erstellen erstellt).

![Bildschirm zum Durchsuchen mit Steuerelementen](./media/learning-spo-app-explore-controls/browse-screen.png)

PowerApps enthält eine Reihe von Galerietypen, sodass Sie die Galerie auswählen können, die dem gewünschten Layout für Ihre App am besten entspricht. Weiter unten in diesem Abschnitt werden weitere Möglichkeiten zum Steuern des Layouts vorgestellt.

![Optionen für PowerApps-Galerien](./media/learning-spo-app-explore-controls/galleries.png)

## <a name="explore-the-details-screen"></a>Elemente des Detailbildschirms
Als Nächstes wird der Detailbildschirm mit dem Standardnamen **DetailScreen1** betrachtet. Das Hauptsteuerelement auf diesem Bildschirm ist ein Anzeigeformular mit dem Namen **DetailForm1**. **DetailForm1** enthält andere Steuerelemente, z.B. **DataCard1** (ein Kartensteuerelement, das in diesem Fall die Kategorie für Bodenbeläge anzeigt). Es gibt auch separate Steuerelemente auf dem Bildschirm, z.B. **IconEdit1** (ein Symbolsteuerelement – durch Klicken oder Tippen wird das aktuelle Element auf dem Bildschirm zum Bearbeiten/Erstellen bearbeitet).

![Detailbildschirm mit Steuerelementen](./media/learning-spo-app-explore-controls/details-screen.png)

Es gibt eine Vielzahl von Galerieoptionen, Formulare sind allerdings ganz einfach – es handelt sich immer entweder um ein Formular zum Bearbeiten oder ein Formular zum Anzeigen.

![PowerApps-Formularoptionen](./media/learning-spo-app-explore-controls/forms.png)

## <a name="explore-the-editcreate-screen"></a>Elemente des Bildschirms zum Bearbeiten/Erstellen
Der dritte Bildschirm in der App ist der Bildschirm zum Bearbeiten/Erstellen mit dem Standardnamen **EditScreen1**. Das Hauptsteuerelement auf diesem Bildschirm ist ein Bearbeitungsformular mit dem Namen **EditForm1**. **EditForm1** enthält andere Steuerelemente, z.B. **DataCard8** (ein Kartensteuerelement, mit dem in diesem Fall die Kategorie für Bodenbeläge bearbeitet werden kann). Es gibt auch separate Steuerelemente auf dem Bildschirm, z.B. **IconAccept1** (ein Symbolsteuerelement – durch Klicken oder Tippen werden die Änderungen auf dem Bildschirm zum Bearbeiten/Erstellen gespeichert).

![Bearbeitungsbildschirm mit Steuerelementen](./media/learning-spo-app-explore-controls/edit-screen.png)

Nachdem Sie nun gesehen haben, aus welchen Bildschirmen und Steuerelementen die App besteht, wird im nächsten Thema das Anpassen der App beschrieben.

