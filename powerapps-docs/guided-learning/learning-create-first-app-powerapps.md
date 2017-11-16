---
title: Erstellen einer ersten App | Microsoft-Dokumentation
description: Generieren einer App aus SharePoint
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: ixRpT48Z6IQ
courseduration: 5m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 34cf3ccd871be00efa3e06c8dbf3717051ab0f13
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="create-your-first-app-in-powerapps"></a>Erstellen einer ersten App in PowerApps
Nachdem Sie nun die Komponenten von PowerApps und die Optionen zum Erstellen von Apps kennen, wird es Zeit, eine eigene App zu erstellen. In diesem Thema erstellen wir eine Smartphone-App anhand einer SharePoint Online-Liste. Sie können aber auch Daten aus vielen anderen Quellen verwenden, z.B. aus Excel, Clouddiensten wie Salesforce und lokalen Quellen wie SQL Server.

## <a name="connect-to-a-data-source"></a>Mit einer Datenquelle verbinden
Der erste Schritt beim Generieren einer App aus Daten ist das Auswählen der PowerApps Studio-Version und das Herstellen einer Verbindung mit Ihrer Datenquelle. Klicken oder tippen Sie auf web.powerapps.com auf **Neue App**, und wählen Sie dann aus, ob Sie PowerApps Studio für Windows oder PowerApps Studio für das Web verwenden möchten.

![Erste Schritte mit web.powerapps.com](./media/learning-create-first-app-powerapps/generate-choose-studio.png)

In PowerApps Studio können Sie mit Daten, mit einer Vorlage oder völlig neu beginnen. Wir erstellen eine Smartphone-App für eine SharePoint-Liste, klicken oder tippen Sie daher unter **SharePoint** auf **Telefonlayout**.

![Smartphone-App aus SharePoint-Liste](./media/learning-create-first-app-powerapps/generate-sharepoint-phone.png)

Generierte Apps basieren immer auf einer einzelnen Liste oder Tabelle (Sie können der App später weitere Daten hinzufügen). Die nächsten drei Bildschirme führen Sie durch das Herstellen einer Verbindung mit der Liste **Flooring Estimates** in SharePoint Online.

![Mit einer SharePoint Online-Liste verbinden](./media/learning-create-first-app-powerapps/generate-connect-list.png)

Nachdem Sie auf **Verbinden** geklickt haben, wird die App von PowerApps generiert. PowerApps zieht eine Vielzahl von Rückschlüssen aus Ihren Daten, um eine sinnvolle App als Ausgangspunkt zu generieren.

## <a name="explore-the-generated-app"></a>Komponenten der generierten App
Herzlichen Glückwunsch! Ihre neue App mit drei Bildschirmen wird in PowerApps Studio geöffnet. Alle Apps, die aus Daten generiert wurden, weisen die gleichen Bildschirme auf:

* Der **Bildschirm zum Durchsuchen**: Hier können Sie die aus der Liste abgerufenen Daten durchsuchen, sortieren, filtern und aktualisieren und Elemente hinzufügen, indem Sie auf das Pluszeichen (+) klicken.
* Der **Detailbildschirm**: Hier werden weitere Informationen zu einem Element angezeigt, und Sie können das Element löschen oder bearbeiten.
* Der **Bildschirm zum Bearbeiten/Erstellen**: Hier können Sie vorhandene Elemente bearbeiten oder neue Elemente erstellen.

Klicken oder tippen Sie auf der linken Navigationsleiste rechts unten auf ein Symbol, um zur Miniaturansicht zu wechseln. 

![Umschalten der Ansichten](./media/learning-create-first-app-powerapps/toggle-view.png)

Klicken oder tippen Sie auf jede Miniaturansicht, um die Steuerelemente auf diesem Bildschirm anzuzeigen.

![Die generierte App](./media/learning-create-first-app-powerapps/generate-finished-app.png)

Klicken oder tippen Sie auf ![Pfeil zum Starten der App-Vorschau](./media/learning-create-first-app-powerapps/f5-arrow-sm.png) oben rechts, um die App auszuführen. Wenn Sie durch die App navigieren, sehen Sie, dass sie alle Daten aus der Liste enthält und in der Standardversion bereits gut zu bedienen ist.

Wow, das war wirklich einfach! In wenigen Minuten haben Sie gelernt, wie Sie eine Verbindung mit einer Datenquelle herstellen und eine App generieren, und Sie haben PowerApps Studio und die drei App-Bildschirme kennengelernt. In den folgenden Abschnitten erfahren Sie, wie die generierten Apps angepasst werden. Im nächsten Thema wird dieser Teil des Kurses noch einmal wiederholt, und wir bereiten uns auf künftige Lektionen vor.

