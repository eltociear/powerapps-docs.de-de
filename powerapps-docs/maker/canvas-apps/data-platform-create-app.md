---
title: Erstellen einer Canvas-App aus Common Data Service | Microsoft-Dokumentation
description: Erstellen Sie in powerapps automatisch eine Canvas-APP, um Daten in Common Data Service zu verwalten.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c62a690073e591c693d914000511b586dfc97b69
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959378"
---
# <a name="create-a-canvas-app-from-common-data-service-in-power-apps"></a>Erstellen einer Canvas-App aus Common Data Service in Power apps

Erstellen Sie in powerapps eine Canvas-App basierend auf einer Liste von Beispiel Konten in [Common Data Service](../common-data-service/data-platform-intro.md). In dieser App können Sie alle Konten durchsuchen, Details zu einem einzelnen Konto anzeigen und ein Konto erstellen, aktualisieren oder löschen.

Wenn Sie nicht für Power apps registriert sind, [melden Sie sich kostenlos an](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) , bevor Sie beginnen.

## <a name="prerequisites"></a>Voraussetzungen

Um diesen Schnellstart folgen zu können, müssen Sie der Sicherheitsrolle [Umgebungs Ersteller](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles) zugewiesen sein, und Sie müssen [zu einer Umgebung wechseln](working-with-environments.md) , in der eine Datenbank in Common Data Service erstellt wurde, Daten enthält und Updates zulässt. Wenn keine Umgebung dieser Art vorhanden ist, und Sie über Administratorrechte verfügen, können Sie [eine Umgebung erstellen](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment), die diese Anforderungen erfüllt.

## <a name="create-an-app"></a>Erstellen einer App

1. Melden Sie sich bei [powerapps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wechseln Sie ggf. in Umgebungen, wie zuvor in diesem Thema beschrieben.

1. Zeigen Sie unter **Eigene App erstellen** auf **Mit Daten beginnen**, und wählen Sie dann **Diese App erstellen** aus.

    ![Option zum Erstellen einer App](./media/data-platform-create-app/start-from-data.png)

1. Wählen Sie auf der Kachel **Common Data Service** die Option **Telefonlayout** aus.

    ![Verbindungskachel](./media/data-platform-create-app/connection-tile.png)

1. Wählen Sie unter **Tabelle auswählen** die Option **Konten** und dann **Verbinden** aus.

1. Wenn das Dialogfeld **Willkommen bei Power apps Studio** angezeigt wird, wählen Sie über **springen**aus.

Ihre App wird auf dem Bildschirm zum Durchsuchen geöffnet, auf dem eine Liste der Konten im sogenannten Katalog angezeigt wird. Am oberen Rand des Bildschirms wird eine Titelleiste mit Symbolen zum Aktualisieren und alphabetischen Sortieren der Daten im Katalog und Hinzufügen von Daten zum Katalog angezeigt. Unterhalb der Titelleiste können Sie über ein Suchfeld die Daten im Katalog filtern, indem Sie Text eingeben oder einfügen. 

Standardmäßig zeigt der Katalog eine E-Mail-Adresse, eine Stadt und einen Kontonamen an. Sie können den Katalog an Ihre Ansprüche anpassen, sodass die Daten anders angezeigt bzw. andere Daten angezeigt werden (dies wird unter [Nächste Schritte](data-platform-create-app.md#next-steps) erläutert).

![Bildschirm zum Durchsuchen](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>Speichern der App
Sie sollten möglicherweise Änderungen vornehmen, bevor Sie diese App verwenden oder für andere freigeben. Es wird empfohlen, dass Sie Ihre bisherige Arbeit speichern, bevor Sie fortfahren.

1. Wählen Sie in der oberen linken Ecke die Registerkarte **Datei** aus.

1. Legen Sie auf der Seite **App-Einstellungen** den Namen der App auf **AppGen** fest, ändern Sie die Farbe des Hintergrunds in ein dunkles Rot, und ändern Sie das Symbol in ein Häkchen.

    ![Seite „App-Einstellungen“](./media/data-platform-create-app/app-settings.png)

1. Wählen Sie am linken Rand **Speichern** und dann in der unteren linken Ecke **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte
In dieser Schnellstartanleitung haben Sie eine APP zum Verwalten von Beispiel Daten zu Konten in Common Data Service erstellt. Passen Sie im nächsten Schritt den Katalog und andere Elemente des Standardbildschirms zum Durchsuchen Ihren Bedürfnissen an.

> [!div class="nextstepaction"]
> [Katalog anpassen](customize-layout-sharepoint.md)
