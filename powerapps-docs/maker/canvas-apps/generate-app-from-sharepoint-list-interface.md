---
title: Generieren einer App aus einer SharePoint-Liste | Microsoft-Dokumentation
description: Generieren Sie eine App mit drei Bildschirmen, um Daten aus einer SharePoint-Liste zu verwalten, lokal oder in der Cloud.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: 46cf610351cf00d8d947c4006c31a3d5971951d0
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022456"
---
# <a name="generate-an-app-from-within-sharepoint-using-powerapps"></a>Generieren einer App aus SharePoint mit PowerApps

In PowerApps wird eine App automatisch generiert, in der Benutzer Elemente aus einer benutzerdefinierten SharePoint Online-Liste verwalten können. Die App wird drei Bildschirme haben, auf denen Benutzer Folgendes können:

* alle Datensätze in der Liste durchsuchen (**BrowseScreen1**)
* alle Felder eines bestimmten Datensatzes anzeigen (**DetailsScreen1**)
* einen Datensatz erstellen oder bearbeiten (**EditScreen1**)

Wenn Sie eine App über die SharePoint Online-Befehlszeile aus einer benutzerdefinierten Liste erstellen, ist die App eine Ansicht dieser Liste. Sie können die App außer im Webbrowser auch auf einem iOS- oder Android-Gerät ausführen.

> [!IMPORTANT]
> PowerApps unterstützt nicht alle Typen von SharePoint-Daten. Weitere Informationen finden Sie unter [Known issues (Bekannte Probleme)](connections/connection-sharepoint-online.md#known-issues).

## <a name="generate-an-app"></a>Eine App generieren
1. Öffnen Sie eine benutzerdefinierte Liste in SharePoint Online, klicken oder tippen Sie auf **PowerApps** in der Befehlszeile, und klicken oder tippen Sie anschließend auf **App erstellen**.

    ![Erstellen einer App](./media/generate-app-from-sharepoint-list-interface/generate-new-app.png)

2. Geben Sie im angezeigten Bereich einen Namen für Ihre App ein, und klicken oder tippen Sie auf **Erstellen**.

    ![Benennen der App](./media/generate-app-from-sharepoint-list-interface/app-name.png)

    Eine neue Registerkarte wird im Webbrowser angezeigt und zeigt die App, die Sie basierend auf Ihrer SharePoint-Liste automatisch generiert haben. Die App wird in PowerApps Studio angezeigt. Dort können Sie sie anpassen.

    ![Standard-App](./media/generate-app-from-sharepoint-list-interface/default-app.png)  
3. Klicken oder tippen Sie für Ihre SharePoint-Liste auf die Registerkarte des Browsers, und klicken oder tippen Sie anschließend auf **Öffnen**.

> [!NOTE]
> Möglicherweise müssen Sie das Browserfenster aktualisieren (z.B. durch Drücken von F5), bevor die App sich öffnet.

Die App wird in einer separaten Registerkarte des Browsers geöffnet.

## <a name="manage-the-app"></a>Verwalten der App
![Befehlsleiste](./media/generate-app-from-sharepoint-list-interface/command-bar.png)

* Wenn Sie auf **Edit in PowerApps** (In PowerApps bearbeiten) klicken oder tippen, öffnet sich die App auf einer separaten Registerkarte des Browsers, wo Sie die App in PowerApps Studio aktualisieren können.

* Wenn Sie auf **Make this view public** (Veröffentlicht diese Ansicht) klicken oder tippen, können andere Personen in Ihrer Organisation sie anzeigen. Standardmäßig können nur Sie Ansichten anzeigen, die Sie erstellen. Wenn Sie anderen Personen gestatten möchten, diese App zu bearbeiten, müssen Sie sie [für diese freigeben](share-app.md) und die Berechtigungen **Can edit** (Kann bearbeiten) gewähren.

* Wenn Sie auf **Aus Ansicht entfernen** klicken oder tippen, entfernen Sie die Ansicht aus SharePoint, aber die App wird in PowerApps verbleiben, sofern Sie sie nicht [löschen](delete-app.md).

## <a name="next-steps"></a>Nächste Schritte
* Passen Sie die Standardeinstellungen für den [Katalog](customize-layout-sharepoint.md), die [Formulare](customize-forms-sharepoint.md) und die [Karten](customize-card.md) an.
