---
title: Generieren einer Canvas-App aus Common Data Service für Apps | Microsoft-Dokumentation
description: Automatisches Generieren einer Canvas-App in PowerApps zum Verwalten von Daten in Common Data Service für Apps
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1393d6dcdd9b88f4bca9e536a776b8601ae4c1c1
ms.sourcegitcommit: 452d4ead948591d16aff144006ad84c957eba837
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "57801777"
---
# <a name="generate-a-canvas-app-from-common-data-service-for-apps-in-powerapps"></a>Generieren einer Canvas-App aus Common Data Service für Apps in PowerApps

Generieren Sie automatisch eine Canvas-App in PowerApps, die auf einer Liste von Beispielkonten in [Common Data Service (CDS) für Apps](../common-data-service/data-platform-intro.md) basiert. In dieser App können Sie alle Konten durchsuchen, Details zu einem einzelnen Konto anzeigen und ein Konto erstellen, aktualisieren oder löschen.

Wenn Sie noch nicht bei PowerApps registriert sind, [registrieren Sie sich zuerst kostenlos](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="prerequisites"></a>Voraussetzungen

Um diesem Schnellstart folgen zu können, müssen Sie zum zugewiesen werden die [Umgebungsersteller](https://docs.microsoft.com/power-platform/admin/database-security.md#predefined-security-roles) Sicherheitsrolle, und Sie müssen [zu einer Umgebung wechseln](working-with-environments.md) bei dem eine Datenbank in CDS für Apps erstellt wurde, enthält Daten, und lässt Updates zu. Wenn keine Umgebung dieser Art vorhanden ist, und Sie über Administratorrechte verfügen, können Sie [eine Umgebung erstellen](https://docs.microsoft.com/power-platform/admin/environments-administration.md#create-an-environment), die diese Anforderungen erfüllt.

## <a name="generate-an-app"></a>Eine App generieren

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wechseln Sie gegebenenfalls die Umgebung, wie weiter oben in diesem Thema erläutert.

1. Zeigen Sie unter **Eigene App erstellen** auf **Mit Daten beginnen**, und wählen Sie dann **Diese App erstellen** aus.

    ![Option zum Erstellen einer App](./media/data-platform-create-app/start-from-data.png)

1. Wählen Sie auf der Kachel **Common Data Service** die Option **Telefonlayout** aus.

    ![Verbindungskachel](./media/data-platform-create-app/connection-tile.png)

1. Wählen Sie unter **Tabelle auswählen** die Option **Konten** und dann **Verbinden** aus.

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** angezeigt wird, klicken Sie auf **Überspringen**.

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
In diesem Schnellstart haben Sie eine App für das Verwalten von Beispieldaten zu Konten in CDS für Apps erstellt. Passen Sie im nächsten Schritt den Katalog und andere Elemente des Standardbildschirms zum Durchsuchen Ihren Bedürfnissen an.

> [!div class="nextstepaction"]
> [Katalog anpassen](customize-layout-sharepoint.md)
