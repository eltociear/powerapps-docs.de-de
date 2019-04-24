---
title: Personen-Bildschirmvorlage | Microsoft-Dokumentation
description: Verstehen Sie, wie die Benutzer-Bildschirmvorlage für Canvas-apps funktioniert und wie Sie den Bildschirm für Ihre eigenen Anwendungsfälle zu erweitern
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 85da6f5414cc25d1145f0fa8910e8c78bfb74533
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536109"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>Übersicht über die Benutzer-Bildschirmvorlage für Canvas-apps

Fügen Sie in einer Canvas-app einen Bildschirm von Personen, mit dem Benutzer, die für Personen innerhalb ihrer Organisationen suchen kann. Benutzer können suchen, auswählen und Hinzufügen von Personen zu einer Sammlung. Sie können ändern, welche Arten von Daten in die Gallery durchsuchen Ergebnis angezeigt werden, verwenden die Auswahl der Benutzer zum Senden einer e-Mail und andere Anpassungen vornehmen.

Sie können auch andere Template-basierten Bildschirme, die zeigen, wie z. B. verschiedene Daten aus Office 365 hinzufügen [-e-Mail](email-screen-overview.md), eines Benutzers [Kalender](calendar-screen-overview.md), und [Verfügbarkeit](meeting-screen-overview.md) Personen möglicherweise Benutzer Möchten Sie zu einer Besprechung eingeladen.

In dieser Übersicht erfahren Sie:
> [!div class="checklist"]
> * So verwenden Sie den Standardbildschirm von Personen.
> * Vorgehensweise: Ändern Sie den Bildschirm.
> * Wie Sie den Bildschirm in apps zu integrieren.

Tiefer in die Standardfunktionalität des Bildschirms, finden Sie unter den [Personen-bildschirmreferenz](people-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionen

So fügen Sie einen Bildschirm für Personen aus der Vorlage hinzu:

1. [Melden Sie sich bei](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) powerapps an, und klicken Sie dann erstellen Sie eine app oder eine vorhandene app in PowerApps Studio öffnen.

    In diesem Thema wird gezeigt, eine Phone-app, die gleichen Konzepte gelten jedoch für eine Tablet-app.

1. Auf der **Startseite** Menüband auf der Registerkarte **neuer Bildschirm** > **Personen**.

    Standardmäßig sieht der Bildschirm wie folgt aus:

    ![Status der anfänglichen Personen-Bildschirm](media/people-screen/people-screen-empty.png)

1. Um die Suche nach Benutzern zu starten, wählen Sie das Texteingabefeld oben und ein Kollege hat den Namen eingeben. Die Ergebnisse der Suche werden nachfolgend das Texteingabefeld angezeigt:

    ![Personen Bildschirm Search-Status](media/people-screen/people-browse-gall-full.png)

1. Wenn Sie Personen in den Suchergebnissen auswählen, werden diese hinzugefügt die **MyPeople** Auflistung. Suchleiste eingegebenen Wert wird zurückgesetzt, Offenlegung durch die Auflistung von Personen, für die Sie ausgewählt haben:

    ![Personen Bildschirm Auflistungsergebnisse](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>Ändern Sie den Bildschirm

Sie können die Standardfunktionen dieses Bildschirms durch [mit Personen andere Daten](people-screen-overview.md#show-different-data-for-people).

Wenn Sie den Bildschirm weiter ändern möchten, verwenden Sie die [Personen-bildschirmreferenz](./people-screen-reference.md) als Leitfaden.

### <a name="show-different-data-for-people"></a>Verschiedene Daten für Benutzer anzeigen

Dieser Bildschirm wird die [Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) Vorgang, der Benutzer in Ihrer org. Suchen Es bietet zusätzliche Felder für jedes Ereignis, hinausgehen wird die **UserBrowseGallery** Steuerelement. Hinzufügen oder Ändern von Feldern im Katalog ist ein einfacher Prozess:

1. In der **UserBrowseGallery**, wählen Sie eine Bezeichnung zu ändern (oder fügen Sie einen hinzu, und bewahren Sie sie ausgewählt haben).

1. Mit der **Text** Eigenschaft ausgewählt ist, in der Bearbeitungsleiste, ersetzen Sie den Inhalt mit `ThisItem.`

    IntelliSense zeigt eine Liste der Felder, die Sie auswählen können.

1. Wählen Sie das gewünschte Feld.

    Die **Text** Eigenschaft sollten ein update auf `ThisItem.{FieldSelection}`.

## <a name="integrate-the-screen-into-an-app"></a>Integrieren Sie den Bildschirm in eine app

Der Benutzer-Bildschirm ist eine leistungsfähige Zusammenstellung von Steuerelementen auf seine eigene, aber es am besten in der Regel als Teil einer größeren, stärker ausbauen app führt. Sie können diesen Bildschirm in eine größere app in eine Reihe von Möglichkeiten, einschließlich integrieren [mithilfe der zwischengespeicherten Liste mit den Personen](people-screen-overview.md#use-your-cached-list-of-people).

### <a name="use-your-cached-list-of-people"></a>Verwenden der zwischengespeicherte Liste mit den Personen

Der Bildschirm für Personen speichert Ihre Auswahl der Personen in der **MyPeople** Auflistung. Ihr Geschäftsszenario für eine Person Suche aufrufen soll, müssen Sie wissen, wie Sie diese Sammlung verwenden. Hier führe Sie durch das Herstellen einer Verbindung eine rudimentäre-e-Mail-Bildschirm mit diesem Bildschirm und Senden von e-Mails an Benutzer in der **MyPeople** Auflistung. Sie erhalten auch einen Einblick in die [-e-Mail-Bildschirm](./email-screen-overview.md) funktioniert.

1. Hinzufügen die Office 365 Outlook-Datenquelle zu Ihrer app durch Auswählen der **Ansicht** Registerkarte auswählen **Datenquellen** > **Datenquelle hinzufügen**, und suchen Sie für Office 365 Outlook-Connector. Möglicherweise müssen Sie wählen **neue Verbindung** zu finden.
1. Fügen Sie nach dem Einfügen des Personen-Bildschirms, einen neuen leeren Bildschirm ein. In diesem Bildschirm können fügen Sie ein Rückwärtspfeil-Symbol, zwei Texteingabefelder und ein Symbol "Senden hinzu".
1. Benennen Sie den Bildschirm zu **EmailScreen**, den zurück-Pfeil **BackIcon**, in einer Texteingabe-Box **SubjectLine**, die andere zum **MessageBody**, und das Symbol "Senden", um **SendIcon**.
1. Legen Sie die **OnSelect** Eigenschaft **BackIcon** zu `Back()`.
1. Legen Sie die **OnSelect** Eigenschaft **SendIcon** auf diese Formel:

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    Hier verwenden Sie den Outlook-Connector, um eine e-Mail senden. Sie übergeben `Concat(MyPeople, UserPrincipalName & ";")` als die Liste der Empfänger. Diese Formel verkettet alle e-Mail-Adressen in der **MyPeople** Auflistung in einer einzelnen Zeichenfolge durch ein Semikolon voneinander getrennt sind. Dies unterscheidet sich von schreibt eine Zeichenfolge mit e-Mail-Adressen getrennt durch ein Semikolon in der Zeile "To" Ihre bevorzugte e-Mail-Clients.
    * Übergeben Sie `SubjectLine.Text` als Betreff der Nachricht und `MessageBody.Text` als Text der Nachricht.
1. Fügen Sie auf dem Bildschirm Personen in der oberen rechten Ecke der **-e-Mails** Symbol.
   Ändern Sie die Farbe des Symbols, was auch immer Sie geeignet ist.
1. Legen Sie die **OnSelect** Eigenschaft der **SendIcon** zu `Navigate( EmailScreen, None )`.

    Sie haben nun eine app mit zwei Bildschirmen, in der Benutzer auswählen, erstellen sie eine e-Mail-Nachricht und senden Sie sie. Probieren Sie es aus, aber Achten Sie darauf, da die app sendet eine e-Mail an alle Benutzer Sie ruhig Hinzufügen der **MyPeople** Auflistung.

## <a name="next-steps"></a>Nächste Schritte

* [Die Referenzdokumentation für diesen Bildschirm](./people-screen-reference.md).
* [Erfahren Sie mehr über das Office 365 Outlook-Connector](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über das Office 365-Benutzer-Connector](../connections/connection-office365-users.md).
