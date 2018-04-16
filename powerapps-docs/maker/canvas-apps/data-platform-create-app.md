---
title: Generieren einer App in PowerApps für Common Data Service für Apps (Schnellstart) | Microsoft-Dokumentation
description: Automatisches Generieren einer App in PowerApps zum Verwalten von Daten in Common Data Service für Apps
services: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/10/2018
ms.author: anneta
ms.openlocfilehash: 78429fc5d0220b5cc9e8dc726583c2e9e543f85a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-for-generating-an-app-in-powerapps-for-the-common-data-service-for-apps"></a>Schnellstart zum Generieren einer App in PowerApps für Common Data Service für Apps

In diesem Schnellstart verwenden Sie PowerApps, um Ihre erste App basierend auf einer Liste von Beispielkonten in [Common Data Service für Apps](../common-data-service/data-platform-intro.md) automatisch zu generieren. In dieser App können Sie alle Konten durchsuchen, Details zu einem einzelnen Konto anzeigen und ein Konto erstellen, aktualisieren oder löschen.

Damit Sie diesem Schnellstart folgen können, müssen Sie zu einer [Umgebung](working-with-environments.md) wechseln, in der eine Datenbank in Common Data Service erstellt wurde, die Daten enthält. Wenn keine Umgebung dieser Art vorhanden ist, und Sie über Administratorrechte verfügen, können Sie [eine Umgebung erstellen](../../administrator/environments-administration.md#create-an-environment), die diese Anforderungen erfüllt.

Wenn Sie nicht eine Lizenz für PowerApps verfügen, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="generate-an-app"></a>Eine App generieren
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an.

    ![PowerApps-Startseite](./media/data-platform-create-app/sign-in.png)

1. Zeigen Sie unter **Apps wie diese erstellen** auf **Mit Daten beginnen**, und klicken Sie dann auf **Diese App erstellen**.

    ![Option zum Erstellen einer App](./media/data-platform-create-app/make-this-app.png)

1. Klicken Sie unter **Von Ihren Daten ausgehen** auf den Pfeil nach rechts.

    ![Pfeilsymbol](./media/data-platform-create-app/right-arrow.png)

1. Wählen Sie unter **Verbindungen** Ihre Verbindung zu Common Data Service aus.

1. Geben Sie am rechten Rand **Konten** in das Suchfeld ein, wählen Sie unter **Tabelle auswählen** **Konten** aus, und klicken Sie dann auf **Verbinden**.

    ![Auswählen einer Entität](./media/data-platform-create-app/select-entity.png)

Nach wenigen Minuten wird Ihre App auf dem Bildschirm zum Durchsuchen geöffnet, auf dem eine Liste der Konten angezeigt wird. Im oberen Bereich des Bildschirms werden auf einer Titelleiste Symbole für das Aktualisieren und Sortieren der Liste sowie das Erstellen eines Kontos angezeigt. Unter der Titelleiste ermöglicht ein Suchfeld das Filtern der Liste basierend auf dem Text, den Sie in das Suchfeld eingeben bzw. einfügen. 

Standardmäßig zeigt die Liste ein Bild, eine E-Mail-Adresse, eine Stadt und eine ID für dieses Konto an. Sie können diese Liste, die als Katalog bezeichnet wird, jedoch anpassen, um andere Arten von Daten anzuzeigen.

![Bildschirm zum Durchsuchen](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>Speichern der App
Sie sollten möglicherweise Änderungen vornehmen, bevor Sie diese App verwenden oder für andere freigeben. Es wird empfohlen, dass Sie Ihre bisherige Arbeit speichern, bevor Sie fortfahren.

1. Klicken oder tippen Sie in der Nähe der oberen linken Ecke auf die Registerkarte **Datei**.

1. Legen Sie auf der Seite **App-Einstellungen** den Namen der App auf **AppGen** fest, ändern Sie die Farbe des Hintergrunds in ein dunkles Rot, und ändern Sie das Symbol in ein Häkchen.

    ![Seite „App-Einstellungen“](./media/data-platform-create-app/app-settings.png)

1. Klicken oder tippen Sie am linken Rand auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte
In diesem Schnellstart haben Sie eine App für das Verwalten von Beispieldaten zu Konten in Common Data Service für Apps erstellt. Passen Sie im nächsten Schritt den Standardbildschirm zum Durchsuchen an Ihre Bedürfnisse an.

> [!div class="nextstepaction"]
> [Anpassen des Standardbildschirms zum Durchsuchen](customize-layout-sharepoint.md)
