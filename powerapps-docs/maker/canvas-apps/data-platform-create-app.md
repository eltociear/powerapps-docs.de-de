---
title: 'Schnellstart: Erstellen einer App von Common Data Service für Apps aus | Microsoft-Dokumentation'
description: Automatisches Generieren einer App in PowerApps zum Verwalten von Daten in Common Data Service für Apps
author: AFTOwen
ms.service: powerapps
ms.topic: conceptual
ms.component: canvas
ms.date: 03/10/2018
ms.author: anneta
ms.openlocfilehash: a70145ee3db44b4ce5d58be2d7804bffb5a56369
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-generate-an-app-from-common-data-service-for-apps-in-powerapps"></a>Schnellstart: Generieren einer App von Common Data Service für Apps aus in PowerApps

In diesem Schnellstart verwenden Sie Microsoft PowerApps, um eine App basierend auf einer Liste von Beispielkonten in [Common Data Service (CDS) für Apps](../common-data-service/data-platform-intro.md) automatisch zu generieren. In dieser App können Sie alle Konten durchsuchen, Details zu einem einzelnen Konto anzeigen und ein Konto erstellen, aktualisieren oder löschen.

Damit Sie diesem Schnellstart folgen können, müssen Sie [zu einer Umgebung wechseln](working-with-environments.md), in der eine Datenbank in CDS für Apps erstellt wurde, die Daten enthält und Updates zulässt. Wenn keine Umgebung dieser Art vorhanden ist, und Sie über Administratorrechte verfügen, können Sie [eine Umgebung erstellen](../../administrator/environments-administration.md#create-an-environment), die diese Anforderungen erfüllt.

Wenn Sie nicht eine Lizenz für PowerApps verfügen, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="generate-an-app"></a>Eine App generieren
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an, und wechseln Sie gegebenenfalls die Umgebung, wie weiter oben in diesem Thema erläutert.

    ![PowerApps-Startseite](./media/data-platform-create-app/sign-in.png)

1. Zeigen Sie unter **Apps wie diese erstellen** auf **Mit Daten beginnen**, und klicken Sie dann auf **Diese App erstellen**.

    ![Option zum Erstellen einer App](./media/data-platform-create-app/make-this-app.png)

1. Wählen Sie auf der Kachel **Common Data Service** die Option **Telefonlayout** aus.

    ![Verbindungskachel](./media/data-platform-create-app/connection-tile.png)

1. Wählen Sie unter **Tabelle auswählen** die Option **Konten** und dann **Verbinden** aus.

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** angezeigt wird, klicken Sie auf **Überspringen**.

Ihre App wird auf dem Bildschirm zum Durchsuchen geöffnet, auf dem eine Liste der Konten angezeigt wird. Im oberen Bereich des Bildschirms werden auf einer Titelleiste Symbole für das Aktualisieren und Sortieren der Liste sowie das Erstellen eines Kontos angezeigt. Unterhalb der Titelleiste können Sie über ein Suchfeld die Liste basierend auf dem Text filtern, den Sie darin eingeben bzw. einfügen. 

Standardmäßig zeigt die Liste eine E-Mail-Adresse, eine Stadt und eine ID für dieses Konto an. Sie können diese Liste, die als Katalog bezeichnet wird, jedoch anpassen, um andere Arten von Daten anzuzeigen.

![Bildschirm zum Durchsuchen](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>Speichern der App
Sie sollten möglicherweise Änderungen vornehmen, bevor Sie diese App verwenden oder für andere freigeben. Es wird empfohlen, dass Sie Ihre bisherige Arbeit speichern, bevor Sie fortfahren.

1. Wählen Sie in der oberen linken Ecke die Registerkarte **Datei** aus.

1. Legen Sie auf der Seite **App-Einstellungen** den Namen der App auf **AppGen** fest, ändern Sie die Farbe des Hintergrunds in ein dunkles Rot, und ändern Sie das Symbol in ein Häkchen.

    ![Seite „App-Einstellungen“](./media/data-platform-create-app/app-settings.png)

1. Wählen Sie am linken Rand **Speichern** und dann in der unteren linken Ecke **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte
In diesem Schnellstart haben Sie eine App für das Verwalten von Beispieldaten zu Konten in CDS für Apps erstellt. Passen Sie im nächsten Schritt den Katalog und andere Elemente des Standardbildschirms zum Durchsuchen Ihren Bedürfnissen an.

> [!div class="nextstepaction"]
> [Katalog anpassen](customize-layout-sharepoint.md)
