---
title: 'Schnellstart: Generieren einer App in PowerApps über SharePoint | Microsoft-Dokumentation'
description: Automatisches Generieren einer App in PowerApps, um Daten in einer SharePoint-Liste zu verwalten
services: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/12/2018
ms.author: anneta
ms.openlocfilehash: 86e255f6c3fbb77b60820108c4a21dd8c0cba532
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-for-generating-an-app-in-powerapps-from-sharepoint"></a>Schnellstart: Generieren einer App in PowerApps über SharePoint

In diesem Schnellstart verwenden Sie PowerApps, um Ihre erste App basierend auf einer Liste von Beispielkonten in SharePoint automatisch zu generieren. In dieser App können Sie alle Elemente der Liste durchsuchen, Details zu einem einzelnen Element anzeigen und ein Element erstellen, aktualisieren oder löschen.

Sie lernen in diesem Schnellstart Konzepte und Techniken kennen, die Sie verwenden können, wenn Sie über eine Liste in SharePoint verfügen. Wenn Sie diesen Schnellstart genau befolgen möchten, erstellen Sie zunächst auf einer SharePoint Online-Website eine Liste mit dem Namen **SimpleApp**, die eine Spalte mit dem Namen **Titel** enthält. Erstellen Sie in der Liste Einträge für **Beispiel1**, **Beispiel2** und **Beispiel3**.

Sie können auch eine viel komplexere Liste mit mehreren Spalten und verschiedenen Typen (z.B. Text, Datumsangaben, Zahlen und Währungen) erstellen. Die Vorgehensweise beim Generieren von Apps ändert sich dabei nicht. Sie können auch App aus einer Liste auf einer lokalen SharePoint-Website generieren, wenn Sie über ein Datengateway [eine Verbindung mit der Website herstellen](connect-to-sharepoint.md).

Wenn Sie nicht über eine Lizenz für PowerApps verfügen, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="generate-an-app"></a>Eine App generieren
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an.

    ![PowerApps-Startseite](./media/app-from-sharepoint/sign-in.png)

1. Zeigen Sie unter **Apps wie diese erstellen** auf **Mit Daten beginnen**, und klicken Sie dann auf **Diese App erstellen**.

    ![Option zum Erstellen einer App](./media/app-from-sharepoint/make-this-app.png)

1. Klicken Sie auf der SharePoint-Kachel auf **Smartphonelayout**.

    ![Option zum Erstellen einer App](./media/app-from-sharepoint/sharepoint-tile.png)

1. Wenn Sie die Option **Direkt verbinden** aktiviert haben, können Sie auf **Erstellen** klicken.

    ![Erstellen der Verbindung](./media/app-from-sharepoint/create-connection.png)

1. Geben Sie unter **Verbindung mit einer SharePoint-Website herstellen** die URL ihrer SharePoint Online-Website ein, und klicken Sie anschließend auf **Gehe zu**.

    Geben Sie wie im folgenden Beispiel nur die Website-URL und nicht den Namen der Liste ein:<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. Klicken Sie unter **Liste auswählen** erst auf **SimpleApp** und dann auf **Verbinden**.

Nach wenigen Minuten wird Ihre App auf dem Bildschirm zum Durchsuchen geöffnet, auf dem eine Liste der Elemente anzeigt wird, die Sie in Ihrer Liste erstellt haben. Wenn Ihre Liste auch Daten in anderen Spalten als nur der Spalte **Titel** enthält, zeigt die App diese Daten an. Im oberen Bereich des Bildschirms werden in einer Titelleiste Symbole zum Aktualisieren und Sortieren der Liste sowie zum Erstellen eines Elements in einer Liste angezeigt. Unterhalb der Titelleiste können Sie über ein Suchfeld die Liste basierend auf dem Text filtern, den Sie darin eingeben bzw. einfügen. 

![Bildschirm zum Durchsuchen](./media/app-from-sharepoint/browse-screen.png)

Sie sollten möglicherweise Änderungen vornehmen, bevor Sie diese App verwenden oder für andere freigeben. Es wird empfohlen, dass Sie Ihre bisherige Arbeit speichern, bevor Sie fortfahren, indem Sie STRG+S drücken. Geben Sie Ihrer App einen Namen, und klicken Sie dann auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte
Sie haben in diesem Schnellstart erfahren, wie Sie eine App erstellen können, um Daten in einer SharePoint-Liste zu verwalten. Generieren Sie als Nächstes eine App über eine komplexere Liste, und passen Sie diese App anschließend angefangen bei dem Bildschirm zum Durchsuchen an Ihre Bedürfnisse an.

> [!div class="nextstepaction"]
> [Anpassen des Standardbildschirms zum Durchsuchen](customize-layout-sharepoint.md)