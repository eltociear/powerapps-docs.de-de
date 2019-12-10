---
title: Erstellen einer Canvas-App aus einer SharePoint-Liste | Microsoft-Dokumentation
description: Erstellen Sie in powerapps automatisch eine Canvas-APP, um Daten in einer SharePoint-Liste zu verwalten.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 346bb27911549715b6c4fdc40f64552c524527be
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959447"
---
# <a name="create-a-canvas-app-in-power-apps-from-a-sharepoint-list"></a>Erstellen einer Canvas-app in powerapps aus einer SharePoint-Liste

In diesem Thema verwenden Sie powerapps, um eine Canvas-App auf der Grundlage von Elementen in einer SharePoint-Liste zu erstellen. Sie können die app in powerapps oder SharePoint Online erstellen. In powerapps können Sie die App basierend auf einer Liste auf einer lokalen SharePoint-Website erstellen, wenn Sie über ein Daten Gateway eine [Verbindung damit herstellen](connections/connection-sharepoint-online.md#create-a-connection) .

Die von Ihnen erstellte app enthält drei Bildschirme:

- Im Bildschirm zum Durchsuchen können Sie durch alle Elemente der Liste scrollen.
- Im Bildschirm mit den Details können Sie alle Informationen zu einem einzelnen Element der Liste anzeigen.
- Im Bildschirm zum Bearbeiten können Sie ein Element erstellen oder Informationen zu einem vorhandenen Element aktualisieren.

Sie können die Konzepte und Techniken in diesem Thema auf jede Liste in SharePoint anwenden. Um die Schritte genau befolgen zu können, bereiten Sie Folgendes vor:

1. Erstellen Sie auf einer SharePoint Online-Website eine Liste namens **SimpleApp**.
2. Erstellen Sie in einer Spalte namens **Title** Einträge für **Vanilla**, **Chocolate** und **Strawberry**.

Das Grundprinzip beim Erstellen einer App ändert sich nicht, auch wenn Sie eine viel komplexere Liste mit mehreren Spalten und verschiedenen Typen (z.B. Text, Datumsangaben, Zahlen und Währungen) erstellen.

> [!IMPORTANT]
> Power Apps unterstützt nicht alle Typen von SharePoint-Daten. Weitere Informationen finden Sie unter [Known issues (Bekannte Probleme)](connections/connection-sharepoint-online.md#known-issues).

## <a name="create-an-app-from-within-power-apps"></a>Erstellen einer APP innerhalb von powerapps

1. Melden Sie sich bei [powerapps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)an.

1. Zeigen Sie unter **Eigene App erstellen** auf **Mit Daten beginnen**, und wählen Sie dann **Diese App erstellen** aus.

    ![Option zum Erstellen einer App](./media/app-from-sharepoint/start-from-data.png)

1. Klicken Sie auf der SharePoint-Kachel auf **Smartphonelayout**.

    ![Option zum Erstellen einer App](./media/app-from-sharepoint/sharepoint-tile.png)

1. Wenn Sie die Option **Direkt verbinden** aktiviert haben, können Sie auf **Erstellen** klicken.

    ![Erstellen der Verbindung](./media/app-from-sharepoint/create-connection.png)

1. Geben Sie unter **Verbindung mit einer SharePoint-Website herstellen** die URL ihrer SharePoint Online-Website ein, und klicken Sie anschließend auf **Gehe zu**.

    Geben Sie wie im folgenden Beispiel nur die Website-URL und nicht den Namen der Liste ein:<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. Klicken Sie unter **Liste auswählen** erst auf **SimpleApp** und dann auf **Verbinden**.

    Nach wenigen Minuten wird Ihre App auf dem Bildschirm zum Durchsuchen geöffnet, auf dem eine Liste der Elemente anzeigt wird, die Sie in Ihrer Liste erstellt haben. Wenn Ihre Liste auch Daten in anderen Spalten als nur der Spalte **Titel** enthält, zeigt die App diese Daten an. Im oberen Bereich des Bildschirms werden in einer Titelleiste Symbole zum Aktualisieren und Sortieren der Liste sowie zum Erstellen eines Elements in einer Liste angezeigt. Unter der Titelleiste ermöglicht ein Suchfeld das Filtern der Liste basierend auf dem Text, den Sie in das Suchfeld eingeben bzw. einfügen. 

    ![Bildschirm zum Durchsuchen](./media/app-from-sharepoint/browse-screen.png)

    Sie sollten möglicherweise Änderungen vornehmen, bevor Sie diese App verwenden oder für andere freigeben. Es wird empfohlen, dass Sie Ihre bisherige Arbeit speichern, bevor Sie fortfahren, indem Sie STRG+S drücken. Geben Sie Ihrer App einen Namen, und klicken Sie dann auf **Speichern**.

## <a name="create-an-app-from-within-sharepoint-online"></a>Erstellen einer App aus SharePoint Online

Wenn Sie eine App über die SharePoint Online-Befehlszeile aus einer benutzerdefinierten Liste erstellen, ist die App eine Ansicht dieser Liste. Sie können die App außer im Webbrowser auch auf einem iOS- oder Android-Gerät ausführen.

1. Öffnen Sie in SharePoint Online eine benutzerdefinierte Liste, klicken Sie in der Befehlsleiste auf **PowerApps**, und klicken Sie anschließend auf **App erstellen**.

    ![Erstellen einer App](./media/app-from-sharepoint/generate-new-app.png)

2. Geben Sie im angezeigten Bereich einen Namen für Ihre App ein, und klicken Sie auf **Erstellen**.

    ![Benennen der App](./media/app-from-sharepoint/app-name.png)

    Im Webbrowser wird eine neue Registerkarte angezeigt, auf der die App angezeigt wird, die Sie basierend auf Ihrer SharePoint-Liste erstellt haben. Die APP wird in powerapps Studio angezeigt, wo Sie Sie anpassen können.

    ![Standard-App](./media/app-from-sharepoint/default-app.png)

3. (Optional) Aktualisieren Sie die Browserregisterkarte für Ihre SharePoint-Liste (indem Sie die Registerkarte auswählen und F5 drücken), und führen Sie dann die folgenden Schritte aus, um Ihre App auszuführen oder zu verwalten:

    - Um die App auszuführen (in einer separaten Browserregisterkarte), wählen Sie **Öffnen** aus.
    - Um anderen Personen in Ihrer Organisation die Ausführung der App zu ermöglichen, wählen Sie **Diese Ansicht öffentlich machen** aus.

        Um anderen Personen die Bearbeitung Ihrer App zu ermöglichen, [geben Sie sie frei](share-app.md), und legen Sie die Berechtigung **Kann bearbeiten** fest.

    - Um die Ansicht aus SharePoint zu entfernen, klicken Sie auf **Diese Ansicht entfernen**.

        [Löschen Sie die APP](delete-app.md), um die APP aus powerapps zu entfernen.

> [!NOTE]
> Apps, die aus der SharePoint-Liste erstellt wurden, werden zurzeit nicht in den mobilen Power apps angezeigt.

## <a name="next-steps"></a>Nächste Schritte
In diesem Thema haben Sie eine App erstellt, mit der Daten in einer SharePoint-Liste verwaltet werden können. Erstellen Sie im nächsten Schritt eine APP aus einer komplexeren Liste, und passen Sie die APP (beginnend mit dem Bildschirm zum Durchsuchen) an, damit Sie Ihren Anforderungen besser entspricht.

> [!div class="nextstepaction"]
> [Anpassen des Standardbildschirms zum Durchsuchen](customize-layout-sharepoint.md)
