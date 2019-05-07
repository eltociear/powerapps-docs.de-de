---
title: Kalender-Bildschirmvorlage | Microsoft-Dokumentation
description: Verstehen Sie, wie die Kalender-Bildschirmvorlage für Canvas-apps funktioniert, ändern Sie den Bildschirm und erweitern Sie im Rahmen einer app
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 745b4232a43a06c46866e83ca2452f8a55afeddf
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536199"
ms.PowerAppsDecimalTransform: true
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>Übersicht über die Kalender-Bildschirmvorlage für Canvas-apps

Fügen Sie in einer Canvas-app einen Kalender-Bildschirm mit der Benutzer über bevorstehende Ereignisse ihres Office 365 Outlook-Kontos angezeigt. Benutzer können ein Datum aus einem Kalender und scrollen Sie durch eine Liste der diesem Tag die Ereignisse auswählen. Sie können ändern, welche Details in der Liste angezeigt werden, fügen einen zweiten Bildschirm, der weitere Details zu jedem Ereignis anzeigt, zeigt eine Liste der Teilnehmer für jedes Ereignis und andere Anpassungen vornehmen.

Sie können auch andere Template-basierten Bildschirme, die zeigen, wie z. B. verschiedene Daten aus Office 365 hinzufügen [-e-Mail](email-screen-overview.md), [Personen](people-screen-overview.md) in einer Organisation und [Verfügbarkeit](meeting-screen-overview.md) Personen-Benutzer möchten zu einer Besprechung eingeladen.

In dieser Übersicht erfahren Sie:
> [!div class="checklist"]
> * So verwenden Sie den Standardbildschirm des Kalenders.
> * So geändert werden.
> * Wie Sie es in eine app zu integrieren.

Tiefer in die Standardfunktionalität des Bildschirms, finden Sie unter den [Kalender-bildschirmreferenz](calendar-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionen

So fügen Sie einen Bildschirm Kalender aus der Vorlage hinzu:

1. [Melden Sie sich bei](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) powerapps an, und klicken Sie dann erstellen Sie eine app oder eine vorhandene app in PowerApps Studio öffnen.

    In diesem Thema wird gezeigt, eine Phone-app, die gleichen Konzepte gelten jedoch für eine Tablet-app.

1. Auf der **Startseite** Menüband auf der Registerkarte **neuer Bildschirm** > **Kalender**.

    Standardmäßig sieht der Bildschirm wie folgt aus:

    ![Kalender-Bildschirm](media/calendar-screen/calendar-initial.png)

1. Um die Daten anzeigen möchten, wählen Sie eine Option in der Dropdown-Liste im oberen Bereich des Bildschirms.

    ![Kalender-Bildschirm, nachdem das Laden abgeschlossen ist](./media/calendar-screen/calendar-screen.png)

Einige hilfreiche Hinweise:

* Heutige Datum ist standardmäßig aktiviert, und Sie können einfach zu zurückkehren, indem Sie das Symbol "Kalender" in der oberen rechten Ecke auswählen.
* Wenn Sie ein anderes Datum auswählen, ein Kreis umschlossen und ein Rechteck helle Farben (Blau, wenn das Standarddesign angewendet wird) schließt des heutigen Datums.
* Wenn mindestens ein Ereignis für ein bestimmtes Datum geplant ist, wird Sie unter diesem Datum im Kalender ein kleiner Farbiger Kreis angezeigt.
* Wenn Sie ein Datum auswählen, für die ein oder mehrere Ereignisse geplant sind, werden die Ereignisse in einer Liste unter dem Kalender angezeigt.

## <a name="modify-the-screen"></a>Ändern Sie den Bildschirm

Sie können die Standardfunktionen von diesem Bildschirm in eine Reihe gebräuchlicher Verfahren ändern:

* [Geben Sie den Kalender](calendar-screen-overview.md#specify-the-calendar).
* [Anzeigen von verschiedenen Details zum Termin](calendar-screen-overview.md#show-different-details-about-an-event).
* [Nicht blockierende Ereignisse ausblenden](calendar-screen-overview.md#hide-nonblocking-events).

Wenn Sie den Bildschirm weiter ändern möchten, verwenden Sie die [Kalender-bildschirmreferenz](./calendar-screen-reference.md) als Leitfaden.

### <a name="specify-the-calendar"></a>Geben Sie den Kalender

Wenn Sie bereits die Kalender Ihre Benutzer anzeigen soll wissen, können Sie den Bildschirm vereinfachen, durch diesen Kalender angeben, bevor Sie die app veröffentlichen. Diese Änderung besteht keine Notwendigkeit für die Dropdown-Liste von Kalendern, damit Sie es entfernen können.

1. Legen Sie die **[OnStart](../controls/control-screen.md)** Eigenschaft dem Standardbildschirm des in der app auf diese Formel:

    ```powerapps-comma
    Set( _userDomain; Right( User().Email; Len( User().Email ) - Find( "@"; User().Email ) ) );;
    Set( _dateSelected; Today() );;
    Set( _firstDayOfMonth; DateAdd( Today(); 1 - Day( Today() ); Days ) );;
    Set( _firstDayInView; 
        DateAdd( _firstDayOfMonth; -( Weekday( _firstDayOfMonth) - 2 + 1 ); Days )
    );;
    Set( _lastDayOfMonth; DateAdd( DateAdd( _firstDayOfMonth; 1; Months ); -1; Days ) );;
    Set( _calendarVisible; false );;
    Set( _myCalendar; 
        LookUp( Office365.CalendarGetTables().value; DisplayName = "{YourCalendarNameHere}" )
    );;
    Set( _minDate; 
        DateAdd( _firstDayOfMonth; -( Weekday(_firstDayOfMonth) - 2 + 1 ); Days )
    );;
    Set( _maxDate; 
        DateAdd(
            DateAdd( _firstDayOfMonth; -( Weekday(_firstDayOfMonth) - 2 + 1 ); Days );
            40; 
            Days 
        )
    );;
    ClearCollect( MyCalendarEvents; 
        Office365.GetEventsCalendarViewV2( _myCalendar.Name; 
            Text( _minDate; UTC ); 
            Text( _maxDate; UTC ) 
        ).value
    );;
    Set( _calendarVisible; true )
    ```

    > [!NOTE]
    > Diese Formel ist etwas aus dem Standardwert von bearbeitet die **OnSelect** -Eigenschaft der Dropdown-Liste für die Auswahl eines Kalenders. Weitere Informationen zu, die steuern, finden Sie unter einen Abschnitt in der [Kalender-bildschirmreferenz](./calendar-screen-reference.md#calendar-drop-down).

1. Ersetzen Sie dies `{YourCalendarNameHere}`, einschließlich der geschweiften Klammern, durch den Namen des Kalenders, die Sie anzeigen möchten (z. B. **Kalender**).

    > [!IMPORTANT]
    > Die folgenden Schritte wird davon ausgegangen, dass Sie nur einen Kalender Bildschirm der App hinzugefügt haben. Wenn Sie mehrere Werte, Steuerelementnamen hinzugefügt haben (z. B. **iconCalendar1**) endet mit einer unterschiedlichen Anzahl, und Sie müssen die Formeln entsprechend anpassen.

1. Legen Sie die **Y** Eigenschaft der **iconCalendar1** Steuerelement auf den folgenden Ausdruck:

    `RectQuickActionBar1.Height + 20`

1. Legen Sie die **Y** Eigenschaft der **LblMonthSelected1** Steuerelement auf den folgenden Ausdruck:

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. Legen Sie die **Text** Eigenschaft der **LblNoEvents1** -Steuerelements auf diesen Wert:

    `"No events scheduled"`

1. Legen Sie die **Visible** Eigenschaft **LblNoEvents1** auf diese Formel:

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. Löschen Sie diese Steuerelemente ein:

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. Wenn der Kalender-Bildschirm den Standardbildschirm nicht ist, fügen Sie eine Schaltfläche, die aus dem Standardbildschirm des auf der Kalender-Bildschirm navigiert, damit Sie die app testen können.

    Fügen Sie z. B. eine Schaltfläche auf **Screen1** , die navigiert zur **Screen2** Wenn Sie einen Bildschirm Kalender für eine app hinzugefügt haben, die Sie ohne Vorlage neu erstellt.

1. Speichern Sie die app, und klicken Sie dann in einem Browser oder auf einem mobilen Gerät testen.

### <a name="show-different-details-about-an-event"></a>Verschiedene Details zu einem Ereignis anzeigen

Standardmäßig wird der Katalog unter dem Kalender, mit dem Namen **CalendarEventsGallery**, zeigt die Startzeit, Dauer, den Betreff und den Speicherort der einzelnen Ereignisse. Sie können konfigurieren, dass der Katalog aus, um jedes Feld (z. B. der Organisator) anzeigen, die die [Office 365-Connector](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) unterstützt.

1. In **CalendarEventsGallery**legen die **Text** -Eigenschaft eine neue oder eine vorhandene Bezeichnung zu `ThisItem` gefolgt von einem Punkt.

    IntelliSense Listet die Felder, die Sie auswählen können.

1. Wählen Sie das gewünschte Feld.

    Die Bezeichnung zeigt den Typ der Informationen, die Sie angegeben haben.

### <a name="hide-nonblocking-events"></a>Nicht blockierende Ereignisse ausblenden

In vielen Zweigstellen und senden die Teammitglieder Meeting-Abfragen, um miteinander zu benachrichtigen, wenn sie außerhalb des Büros werden. Um zu vermeiden, alle Zeitpläne zu blockieren, wird die Person, die die Anforderung sendet seine Verfügbarkeit auf **Free**. Sie können diese Ereignisse aus dem Kalender und der Katalog ausblenden, indem Sie einige Eigenschaften aktualisieren.

1. Legen Sie die **Elemente** Eigenschaft **CalendarEventsGallery** auf diese Formel:

    ```powerapps-comma
    SortByColumns(
        Filter(
            MyCalendarEvents;
            Text( Start; DateTimeFormat.ShortDate ) = 
                Text( _dateSelected; DateTimeFormat.ShortDate );
            ShowAs <> "Free"
        );
        "Start"
    )
    ```

    In dieser Formel die **Filter** Funktion wird ausgeblendet, nicht nur die Ereignisse, die für ein Datum als dem ausgewählten geplant sind, sondern auch Ereignisse, die für die die Verfügbarkeit, um festgelegt ist **Free**.

1. Legen Sie im Kalender, der **Visible** Eigenschaft der **Kreis** -Steuerelements auf diese Formel:

    ```powerapps-comma
    CountRows(
        Filter(
            MyCalendarEvents;
            DateValue( Text(Start) ) = DateAdd( _firstDayInView; ThisItem.Value; Days );
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    Diese Formel enthält, die denselben Filter wie die vorherige Formel. Aus diesem Grund der Ereignis-Indikator Kreis wird unter ein Datum angezeigt, nur, wenn eine oder mehr Ereignisse, die auf dem ausgewählten Datum und für die die Verfügbarkeit ist nicht festgelegt **Free**.

## <a name="integrate-the-screen-into-an-app"></a>Integrieren Sie den Bildschirm in eine app

Der Kalender-Bildschirm ist eine leistungsfähige Zusammenstellung von Steuerelementen auf seine eigene, aber es am besten in der Regel als Teil einer größeren, stärker ausbauen app führt. Sie können diesen Bildschirm in eine größere app in eine Reihe von Möglichkeiten, dazu gehören das Hinzufügen dieser Optionen integrieren:

* [Anzeigen von Ereignisdetails](calendar-screen-overview.md#view-event-details).
* [Anzeigen von Ereignis-Teilnehmer](calendar-screen-overview.md#show-event-attendees).

### <a name="view-event-details"></a>Anzeigen von Ereignisdetails

Wenn Benutzer auf ein Ereignis in auswählen **CalendarEventsGallery**, können Sie einen anderen Bildschirm Weitere Informationen zu diesem Ereignis zeigt öffnen.

> [!NOTE]
> Diese Prozedur zeigt Ereignisdetails in einem Katalog mit dynamischen Inhalten, aber Sie können ähnliche Ergebnisse erzielen, mit anderen Methoden. Beispielsweise erhalten Sie mehr Kontrolle für Entwurf, stattdessen mithilfe einer Reihe von Bezeichnungen.

1. Fügen Sie einen leeren Bildschirm, mit dem Namen **EventDetailsScreen**, enthält einen leer flexible Höhe-Katalog und eine Schaltfläche, die auf der Kalender-Bildschirm navigiert.

1. Im Katalog mit flexibler Höhe Hinzufügen einer **Bezeichnung** Steuerelement und ein **HTML-Text** steuern, und legen die **AutoHeight** Eigenschaft sowohl zu **"true"** .

    > [!NOTE]
    > PowerApps Ruft den Nachrichtentext der einzelnen Ereignisse als HTML-Text ab, daher Sie zum Anzeigen dieses Inhalts in müssen einem **HTML-Text** Steuerelement.

1. Legen Sie die **Y** Eigenschaft der **HTML-Text** Steuerelement auf den folgenden Ausdruck:

    `Label1.Y + Label1.Height + 20`

1. Passen Sie zusätzliche Eigenschaften bei Bedarf Ihren Stil Anforderungen entsprechend an.

    Angenommen, Sie möglicherweise eine Trennlinie unten hinzufügen möchten die **HTML-Text** Steuerelement.

1. Legen Sie die **Elemente** -Eigenschaft des Katalogs flexible Höhe auf diese Formel:

    ```powerapps-comma
    Table(
        { Title: "Subject"; Value: _selectedCalendarEvent.Subject };
        { 
            Title: "Time"; 
            Value: _selectedCalendarEvent.Start & " - " & _selectedCalendarEvent.End 
        };
        { Title: "Body"; Value: _selectedCalendarEvent.Body }
    )
    ```

    Diese Formel erstellt eine Galerie mit dynamischen Daten, die auf den Feldwerten des festgelegt ist **_selectedCalendarEvent**, festgelegt wird, jedes Mal, wenn ein Ereignis in der Auswahl der **CalendarEventsGallery** Steuerelement. Sie können diesen Katalog aus, um weitere Felder enthalten, indem weitere Bezeichnungen hinzugefügt erweitern, aber dieser Satz stellt einen guten Ausgangspunkt.

1. Legen Sie mit den Elementen der Katalog vorhanden, die **Text** Eigenschaft der **Bezeichnung** die Steuerung an `ThisItem.Title`, und die **HtmlText** Eigenschaft der **HTML-Text**  die Steuerung an `ThisItem.Value`.

1. In **CalendarEventsGallery**legen die **OnSelect** Eigenschaft der **Titel** -Steuerelements auf diese Formel:

    ```powerapps-comma
    Set( _selectedCalendarEvent; ThisItem );;
    Navigate( EventDetailsScreen; None )
    ```

    > [!Note]
    > Anstatt die **_selectedCalendarEvent** Variablen, verwenden Sie stattdessen **CalendarEventsGallery**. Ausgewählt.

### <a name="show-event-attendees"></a>Anzeigen von Ereignis-Teilnehmer

Die `Office365.GetEventsCalendarViewV2` Vorgang ruft eine Vielzahl von Feldern für jedes Ereignis, darunter eine durch Semikolons getrennte Reihe von erforderlichen und optionalen Teilnehmer ab. In diesem Verfahren Sie jede Gruppe von Teilnehmern zu analysieren, bestimmen, welche Teilnehmer in Ihrer Organisation sind, und rufen die Office 365-Profile von alle heißen.

1. Wenn Ihre app den Office 365-Benutzer-Connector nicht enthalten [hinzufügen](../add-data-connection.md).

1. Legen Sie zum Abrufen der Office 365-Profile von Teilnehmern der Besprechung der **OnSelect** Eigenschaft der **Titel** steuern, der **CalendarEventsGallery** auf diese Formel:

    ```powerapps-comma
    Set( _selectedCalendarEvent; ThisItem );;
    ClearCollect( AttendeeEmailsTemp;
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees; ";" );
            !IsBlank( Result )
        )
    );;
    ClearCollect( AttendeeEmails;
        AddColumns( AttendeeEmailsTemp; 
            "InOrg";
            Upper( _userDomain ) = Upper( Right( Result; Len( Result ) - Find( "@"; Result ) ) )
        )
    );;
    ClearCollect( MyPeople;
        ForAll( AttendeeEmails; If( InOrg; Office365Users.UserProfile( Result ) ) ) 
    );;
    Collect( MyPeople;
        ForAll( AttendeeEmails;
            If( !InOrg; 
                { DisplayName: Result; Id: ""; JobTitle: ""; UserPrincipalName: Result }
            )
        )
    )
    ```

Diese Liste wird erläutert, was von den einzelnen **ClearCollect** Vorgang wird ausgeführt:

- ClearCollect(AttendeeEmailsTemp)
    ```powerapps-comma
    ClearCollect( AttendeeEmailsTemp;
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees; ";" ); 
            !IsBlank( Result)
        )
    );;
    ```

    Diese Formel die erforderlichen und optionalen Teilnehmer in einer einzelnen Zeichenfolge verkettet, und klicken Sie dann diese Zeichenfolge in einzelne Adressen auf jedem Semikolon teilt. Die Formel und leere Werte aus diesem Satz filtert und fügt die anderen Werte in einer Auflistung, die mit dem Namen **AttendeeEmailsTemp**.

- ClearCollect(AttendeeEmails)
    ```powerapps-comma
    ClearCollect( AttendeeEmails;
        AddColumns( AttendeeEmailsTemp; 
            "InOrg";
            Upper( _userDomain ) = Upper( Right( Result; Len(Result) - Find("@"; Result) ) )
        )
    );;
    ```
    Diese Formel wird ungefähr bestimmt, ob ein Teilnehmer in Ihrer Organisation ist. Die Definition der **_userDomain** ist einfach die Domänen-URL in die e-Mail-Adresse der Person, die die app ausgeführt wird. Diese Zeile erstellt eine zusätzliche wahr/falsch-Spalte, die mit dem Namen **InOrg**in die **AttendeeEmailsTemp** Auflistung. Diese Spalte enthält **"true"** Wenn **UserDomain** ist gleichbedeutend mit der URL für die e-Mail-Adresse in dieser bestimmten Zeile der **AttendeeEmailsTemp**.

    Dieser Ansatz ist nicht immer genau, zeigt aber ziemlich schließen. Z. B. möglicherweise bestimmte Teilnehmer in Ihrer Organisation eine e-Mail-Adresse wie Jane@OnContoso.comhingegen **_userDomain** %% amp;quot;contoso.com%%amp;quot; lautet. Die app-Benutzer und Jane auf dem gleichen Unternehmen arbeiten, jedoch haben geringfügige Unterschiede bei deren e-Mail-Adressen. Für solche Fälle können Sie diese Formel verwenden möchten:

    `Upper(_userDomain) in Upper(Right(Result; Len(Result) - Find("@"; Result)))`

    Diese Formel entspricht jedoch e-Mail-Adressen wie Jane@NotTheContosoCompany.com mit einem **_userDomain** wie "contoso.com", und diese Personen nicht in demselben Unternehmen arbeiten.

- ClearCollect(MyPeople)

    ```powerapps-comma
    ClearCollect( MyPeople;
        ForAll( AttendeeEmails; 
            If( InOrg; 
                Office365Users.UserProfile( Result )
            )
        )
    );;
    Collect( MyPeople;
        ForAll( AttendeeEmails;
            If( !InOrg; 
                { 
                    DisplayName: Result; 
                    Id: ""; 
                    JobTitle: ""; 
                    UserPrincipalName: Result
                }
            )
        )
    );;
    ```
    Zum Abrufen von Office 365-Profilen, müssen Sie verwenden die [Office365Users.UserProfile](https://docs.microsoft.com/connectors/office365users/#userprofile) oder [Office365Users.UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) Vorgang. Diese Vorgänge sammeln Sie zunächst alle Office 365-Profile für Teilnehmer, die sich der Benutzer org. Anschließend fügen Sie die Vorgänge einige Felder für Teilnehmer von außerhalb der Organisation hinzu. Diese beiden Elemente in verschiedene Operationen, die Sie getrennt, da die **ForAll** Schleife keine Reihenfolge garantiert. Aus diesem Grund **ForAll** Teilnehmer von außerhalb der Organisation kann zunächst erfassen. In diesem Fall ist das Schema für **MyPeople** enthält nur **"DisplayName"**, **Id**, **JobTitle**, und **"userPrincipalName"** . Die UserProfile-Vorgänge wird jedoch viel umfangreicheren Daten als die abrufen. Damit Sie erzwingen, dass die **MyPeople** Auflistung, die Office 365-Profilen vor den anderen Profilen hinzugefügt.

    > [!NOTE]
    > Erreichen Sie das gleiche Ergebnis mit nur einem **ClearCollect** Funktion:

    ```powerapps-comma
    ClearCollect( MyPeople; 
        ForAll(
            AddColumns(
                Filter(
                    Split(
                        ThisItem.RequiredAttendees & ThisItem.OptionalAttendees; 
                        ";"
                    ); 
                    !IsBlank( Result )
                ); 
                "InOrg"; _userDomain = Right( Result; Len( Result ) - Find( "@"; Result ) )
            ); 
            If( InOrg; 
                Office365Users.UserProfile( Result ); 
                { 
                    DisplayName: Result; 
                    Id: ""; 
                    JobTitle: ""; 
                    UserPrincipalName: Result; 
                    Department: ""; 
                    OfficeLocation: ""; 
                    TelephoneNumber: ""
                }
            )
        )
    )
    ```

In dieser Übung abschließen zu können:

1. Fügen Sie einen Bildschirm, die für die einen Katalog enthält die **Elemente** -Eigenschaftensatz auf **MyPeople**.

1. In der **OnSelect** Eigenschaft der **Titel** steuern, der **CalendarEventsGallery**, Hinzufügen einer **navigieren** Funktion auf dem Bildschirm, den Sie im vorherigen Schritt erstellt.

## <a name="next-steps"></a>Nächste Schritte

* [Die Referenzdokumentation für diesen Bildschirm](calendar-screen-reference.md).
* [Erfahren Sie mehr über das Office 365 Outlook-Connector](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über das Office 365-Benutzer-Connector](../connections/connection-office365-users.md).
