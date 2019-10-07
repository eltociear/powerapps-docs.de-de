---
title: Erstellen einer Canvas-App aus Common Data Service | Microsoft-Dokumentation
description: In powerapps generieren Sie automatisch eine Canvas-App zum Verwalten von Daten in Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f9dedc515ee130a950c1dc12793751d43aa3804f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993080"
---
# <a name="generate-a-canvas-app-from-common-data-service-in-powerapps"></a>Generieren einer Canvas-App aus Common Data Service in powerapps

In powerapps generieren Sie automatisch eine Canvas-App basierend auf einer Liste von Beispiel Konten in [Common Data Service](../common-data-service/data-platform-intro.md). In dieser App können Sie alle Konten durchsuchen, Details zu einem einzelnen Konto anzeigen und ein Konto erstellen, aktualisieren oder löschen.

Wenn Sie noch nicht bei PowerApps registriert sind, [registrieren Sie sich zuerst kostenlos](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="prerequisites"></a>Voraussetzungen

Um diesen Schnellstart folgen zu können, müssen Sie der Sicherheitsrolle [Umgebungs Ersteller](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles) zugewiesen sein, und Sie müssen [zu einer Umgebung wechseln](working-with-environments.md) , in der eine Datenbank in Common Data Service erstellt wurde, Daten enthält und Updates zulässt. Wenn keine Umgebung dieser Art vorhanden ist, und Sie über Administratorrechte verfügen, können Sie [eine Umgebung erstellen](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment), die diese Anforderungen erfüllt.

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
In dieser Schnellstartanleitung haben Sie eine APP zum Verwalten von Beispiel Daten zu Konten in Common Data Service erstellt. Passen Sie im nächsten Schritt den Katalog und andere Elemente des Standardbildschirms zum Durchsuchen Ihren Bedürfnissen an.

> [!div class="nextstepaction"]
> [Katalog anpassen](customize-layout-sharepoint.md)
