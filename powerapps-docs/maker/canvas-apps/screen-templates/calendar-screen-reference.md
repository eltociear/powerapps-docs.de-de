---
title: Referenz für die Vorlage "Kalender Bildschirm" für Canvas-apps | Microsoft-Dokumentation
description: Erfahren Sie, wie die Vorlage für Canvas-apps in powerapps funktioniert.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b9e5425244d819816fa05c4b780a6be092b0d22c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995724"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>Referenzinformationen zur Vorlage "Kalender Bildschirm" für Canvas-apps

Für Canvas-apps in powerapps können Sie verstehen, wie die einzelnen wichtigen Steuerelemente in der Vorlage für Kalender Bildschirme zur gesamten Standardfunktionalität des Bildschirms beitragen. Dieser ausführliche Einblick zeigt die Verhaltens Formeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine allgemeine Erörterung der Standardfunktionalität dieses Bildschirms finden Sie in der [Übersicht über den Kalender Bildschirm](calendar-screen-overview.md).

In diesem Thema werden einige bedeutende Steuerelemente hervorgehoben und die Ausdrücke oder Formeln erläutert, mit denen verschiedene Eigenschaften (z. b. **Elemente** und **onselect**) dieser Steuerelemente festgelegt werden:

- [Dropdown Liste "Kalender" (dropdowncalendarselection)](#calendar-drop-down)
- [Kalendersymbol (iconcalendar)](#calendar-icon)
- [Chevron im vorherigen Monat (iconprevmonth)](#previous-month-chevron)
- [Chevron im nächsten Monat (iconnecxtmonth)](#next-month-chevron)
- [Kalender Galerie (monthdaygallery) (+ untergeordnete Steuerelemente)](#calendar-gallery)
- [Ereignis Katalog (calendareventsgallery)](#events-gallery)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen [beim Erstellen einer APP in powerapps](../data-platform-create-app-scratch.md).

## <a name="calendar-drop-down"></a>Kalender-Dropdown

![dropdowncalendarselection-Steuerelement](media/calendar-screen/calendar-dropdown.png)

- Property **Punkte**<br>
    Wert: `Office365.CalendarGetTables().value`

    Dieser Wert ist ein Connector-Vorgang, mit dem die Outlook-Kalender des App-Benutzers abgerufen werden. [Der Wert, den](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table]) dieser Vorgang abruft, wird angezeigt.

- Property **OnChange**<br>Wert: `Select(dropdownCalendarSelection)`

    Wenn der Benutzer eine Option in der Liste auswählt, wird die-Funktion in der **onselect** -Eigenschaft des Steuer Elements ausgeführt.

- Property **OnSelect**<br>
    Wert Eine **if** -Funktion, die im folgenden Codeblock angezeigt wird, und mehrere zusätzliche Funktionen, die danach im Codeblock angezeigt werden.

   Dieser Teil der Formel wird nur beim ersten Mal ausgeführt, wenn der Benutzer nach dem Öffnen der App eine Option in der Dropdown Liste auswählt:

    ```powerapps-dot
    If( IsBlank( _userDomain ),
        UpdateContext( {_showLoading: true} );
        Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
        Set( _dateSelected, Today() );
        Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );  
        Set( _firstDayInView, DateAdd( _firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 1), Days ) );
        Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )  
    );
    ```

    Der vorangehende Code definiert die folgenden Variablen:
    
  - **\_userdomain**: Die Unternehmens Domäne der App-Benutzer, die sich in der e-Mail-Adresse des Benutzers widerspiegelt.
  - **\_datesgewählt**: Das heutige Datum (Standardeinstellung). In der Kalender Galerie wird dieses Datum hervorgehoben, und die Ereignis Galerie zeigt die Ereignisse an, die für dieses Datum geplant sind.
  - **\_firstdayosmonth**: Der erste Tag des aktuellen Monats. Da `(Today + (1 - Today)) = Today - Today + 1 = 1`, gibt diese **DateAdd** -Funktion immer den ersten Tag des Monats zurück.
  - **\_firstdayinview**: Der erste Tag, an dem der Kalender Katalog angezeigt werden kann. Dieser Wert entspricht nicht dem ersten Tag des Monats, es sei denn, der Monat beginnt am Sonntag. Um zu verhindern, dass eine ganze Woche des vorangegangenen Monats angezeigt wird, ist der Wert von **\_firstdayinview** `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1`.
  - **\_lastdayosmonth**: Der letzte Tag des aktuellen Monats, der dem ersten Tag des nächsten Monats entspricht, minus einem Tag.

   Die Funktionen nach der **if** -Funktion werden immer dann ausgeführt, wenn der Benutzer eine Option in der Kalender-Dropdown Liste auswählt (nicht nur beim ersten Öffnen der app durch den Benutzer):

    ```powerapps-dot
    Set( _calendarVisible, false );
    UpdateContext( {_showLoading: true} );
    Set( _myCalendar, dropdownCalendarSelection2.Selected );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set(_maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ), 
            40, 
            Days
        )
    );
    ClearCollect( MyCalendarEvents, 
        'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC )
        ).value
    );
    UpdateContext( {_showLoading: false} );
    Set( _calendarVisible, true )
    ```

    Der vorangehende Code definiert diese Variablen und eine Sammlung:

    - **\_calendarvisible**: Legen Sie diese Einstellung auf " **false** " fest, damit der Kalender beim Laden der neuen Auswahl nicht angezeigt wird.
    - **\_showload**: Auf " **true** " festgelegt, sodass beim Laden der neuen Auswahl Indikatoren angezeigt werden.
    - **\_mycalendar**: Auf den aktuellen Wert des **Dropdown-** Steuer Elements Kalender festlegen, sodass Ereignisse aus dem richtigen Kalender abgerufen werden.
    - **\_mindate**: Legen Sie auf denselben Wert wie **\_firstdayinview**fest. Diese Variable bestimmt, welche Ereignisse bereits aus Outlook abgerufen und in der APP zwischengespeichert wurden.
    - **\_maxdate**: Legen Sie auf den letzten Ansichts baren Tag im Kalender fest. Die Formel ist `_firstDayInView + 40`. Der Kalender zeigt maximal 41 Tage an, sodass die Variable " **\_maxdate** " immer den letzten sichtbaren Tag widerspiegelt und bestimmt, welche Ereignisse bereits aus Outlook abgerufen und in der APP zwischengespeichert wurden.
    - **Mycalendarevents**: Legen Sie auf eine Auflistung von Ereignissen des Benutzers aus dem ausgewählten Kalender fest, die von **\_mindate** bis **\_maxdate**reichen.
    - **\_showload**: Auf **false**festlegen. **\_calendarvisible** ist auf **true** festgelegt, nachdem alles andere geladen wurde.

## <a name="calendar-icon"></a>Kalendersymbol

![iconcalendar-Steuerelement](media/calendar-screen/calendar-today-icon.png)

- Property **OnSelect**<br>
    Wert Vier **Set** -Funktionen, die den Kalender Katalog auf das heutige Datum zurücksetzen:

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    Der vorangehende Code setzt alle Datums Variablen zurück, die zum Anzeigen der richtigen Kalenderansicht erforderlich sind:

    - **\_datesgewählte** wird auf heute zurückgesetzt.
    - **\_firstdayofmonth** wird auf den ersten Tag des heutigen Monats zurückgesetzt.
    - **\_firstdayinview** wird auf den ersten Tag zurückgesetzt, der angezeigt werden kann, wenn der heutige Monat ausgewählt ist.
    - **\_lastdayofmonth** wird auf den letzten Tag des heutigen Monats zurückgesetzt.

    Im [**Dropdown Abschnitt Kalender**](#calendar-drop-down) dieses Themas werden diese Variablen ausführlicher erläutert.

## <a name="previous-month-chevron"></a>Chevron im vorherigen Monat

![iconprevmonth-Steuerelement](media/calendar-screen/calendar-back.png)

- Property **OnSelect**<br>Wert Vier **Set** -Funktionen und eine **if** -Funktion, die den vorherigen Monat in der Kalender Galerie anzeigt:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, -1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set( _lastDayOfMonth, DateAdd(DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _minDate > _firstDayOfMonth,
        Collect( MyCalendarEvents,
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name,
                Text( _firstDayInView, UTC ), 
                Text( DateAdd( _minDate, -1, Days ), UTC )
            ).value
        );
        Set( _minDate, _firstDayInView )
    )
    ```

    > [!NOTE]
    > Definitionen für " **\_firstdayofmonth**", " **\_firstdayinview**" und " **\_lastdayofmonth** " sind nahezu identisch mit denen im [Dropdown](#calendar-drop-down) Abschnitt "Kalender" in diesem Thema.

    Die ersten drei Zeilen des vorangehenden Codes werden immer dann ausgeführt, wenn der Benutzer den Chevron des vorherigen Monats auswählt. Der Code legt die Variablen fest, die zum Anzeigen der richtigen Kalenderansicht erforderlich sind. Der verbleibende Code wird nur dann ausgeführt, wenn der Benutzer diesen Monat nicht bereits für den ausgewählten Kalender ausgewählt hat.

    Wenn dies der Fall ist, ist **\_mindate** der erste Tag, der angezeigt wird, wenn der vorherige Monat angezeigt wird. Bevor der Benutzer das Symbol **auswählt, hat \_mindate** einen minimal möglichen Wert für den 23. des aktuellen Monats. (Wenn der 1. März an einem Samstag liegt, ist **\_firstdayinview** für März der 23. Februar.) Dies bedeutet Folgendes: Wenn ein Benutzer diesen Monat noch nicht ausgewählt hat, ist **\_mindate** größer als das neue **\_firstdayosmonth**, und die **if** -Funktion gibt **true**zurück. Der Code wird ausgeführt, und eine-Auflistung und eine-Variable werden aktualisiert:

    - **Mycalendarevents** ruft Ereignisse aus dem ausgewählten Kalender mit dem Vorgang [Office 365. GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) ab. Der Datumsbereich liegt zwischen dem **\_firstdayinview** -Datum und **\_mindate** -1. Da **mycalendarevents** bereits Ereignisse am **\_mindate-** Datum enthält, wird 1 von diesem Datum für den maximalen Wert in diesem neuen Datumsbereich subtrahiert.

    - **\_mindate** ist auf die aktuelle **\_firstdayinview** festgelegt, da dies das erste Datum ist, für das Ereignisse abgerufen wurden. Wenn ein Benutzer zu diesem Datum zurückkehrt, indem er den Chevron im vorherigen Monat auswählt, gibt die **if** -Funktion **false**zurück. der Code wird nicht ausgeführt, da Ereignisse für diese Sicht bereits in **mycalendarevents**zwischengespeichert wurden.

## <a name="next-month-chevron"></a>Chevron im nächsten Monat

![iconnecxtmonth-Steuerelement](media/calendar-screen/calendar-forward.png)

- Property **OnSelect**<br>
    Wert Vier **Set** -Funktionen und eine **if** -Funktion, die den nächsten Monat in der Kalender Galerie anzeigen:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, 1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ) );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _maxDate < _lastDayOfMonth,
        Collect( MyCalendarEvents, 
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
                Text( DateAdd( _maxDate, 1, Days ), UTC ), 
                DateAdd( _firstDayInView, 40, Days )
            ).value
        );
        Set( _maxDate, DateAdd( _firstDayInView, 40, Days) )    
    )
    ```

    > [!NOTE]
    > Definitionen für " **\_firstdayofmonth**", " **\_firstdayinview**" und " **\_lastdayofmonth** " sind nahezu identisch mit denen im [Dropdown](#calendar-drop-down) Abschnitt "Kalender" in diesem Thema.

    Die ersten drei Zeilen des vorangehenden Codes, die ausgeführt werden, wenn der Benutzer das nächste Monats-Chevron auswählt, legen die Variablen fest, die zum Anzeigen der richtigen Kalenderansicht erforderlich sind. Der verbleibende Code wird nur dann ausgeführt, wenn der Benutzer diesen Monat nicht bereits für den ausgewählten Kalender ausgewählt hat.

    In diesem Fall ist **\_maxdate** der letzte Tag, der angezeigt wird, wenn der vorherige Monat angezeigt wird. Bevor der Benutzer das Chevron des nächsten Monats auswählt, hat **\_maxdate** einen maximal möglichen Wert von 13. des nächsten Monats. (Wenn der 1. Februar an einem nicht-Schaltjahr Sonntag liegt, ist **\_maxdate** der 13. März ( **\_firstdayinview** + 40 Tage). Dies bedeutet Folgendes: Wenn ein Benutzer diesen Monat noch nicht ausgewählt hat, ist **\_maxdate** größer als der neue **\_lastdayosmonth**, und die **if** -Funktion gibt **true**zurück. Der Code wird ausgeführt, und eine-Auflistung und eine-Variable werden aktualisiert:

    - **Mycalendarevents** ruft Ereignisse aus dem ausgewählten Kalender mit dem Vorgang [Office 365. GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) ab. Der Datumsbereich liegt zwischen **\_maxdate** + 1 Tag und **\_firstdayinview** + 40 Tage. Da **mycalendarevents** bereits Ereignisse am **\_mindate-** Datum enthält, wird diesem Datum 1 für den Minimalwert in diesem neuen Datumsbereich 1 hinzugefügt. **\_firstdayinview** + 40 ist die Formel für **\_maxdate**. das zweite Datum im Bereich ist also nur das neue **\_maxdate**.

    - **\_maxdate** ist auf **\_firstdayinview** + 40 Tage festgelegt, da dies der letzte Tag ist, an dem Ereignisse abgerufen wurden. Wenn ein Benutzer zu diesem Datum zurückkehrt, indem er den nächsten Monat auswählt, gibt die **if** -Funktion **false**zurück. der Code wird nicht ausgeführt, da Ereignisse für diese Sicht bereits in **mycalendarevents**zwischengespeichert wurden.

## <a name="calendar-gallery"></a>Kalender Galerie

![Monthdaygallery-Steuerelement](media/calendar-screen/calendar-month-gall.png)

- Property **Punkte**<br>
    Wert: `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  Der Satz von 0 bis 41 wird für die Elemente im Kalender Katalog verwendet, da in der Kalenderansicht im ungünstigsten Fall 42 vollständige Tage angezeigt werden müssen. Dies tritt auf, wenn der erste des Monats an einem Samstag und der letzte Monat an einem Sonntag auftritt. In diesem Fall zeigt der Kalender sechs Tage ab dem vorhergehenden Monat in der Zeile, die den ersten des Monats enthält, und sechs Tage des folgenden Monats in der Zeile mit dem letzten Monat an. Dies sind 42 eindeutige Werte, von denen 30 für den ausgewählten Monat sind.

- Property **WrapCount**<br>
    Wert: `7`

  Dieser Wert gibt eine siebentägige Woche an.

### <a name="title-control-in-the-calendar-gallery"></a>Title-Steuerelement im Kalender Katalog

![Monthdaygallery-Titel Steuerelement](media/calendar-screen/calendar-month-text.png)

- Property **Text**<br>
    Wert: `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    Beachten Sie, dass **\_firstdayinview** als ( **\_firstdayosmonth** -der Wert des Wochentags) + 1 definiert ist. Dies weist darauf hin, dass **\_firstdayinview** immer ein Sonntag ist, und **\_firstdayosmonth** immer in der ersten Zeile von **monthdaygallery**. Aufgrund dieser beiden Fakten befindet sich **\_firstdayinview** immer in der ersten Zelle von **monthdaygallery**. **Thisitem. Value** ist die Nummer für diese Zelle in der Eigenschaft **monthdaygallery** . Wenn Sie **\_firstdayinview** als Ausgangspunkt nehmen, zeigt jede Zelle das Inkrement von **\_firstdayinview** + den entsprechenden Zellwert an.

- Property **Erfüllen**<br>
    Wert Eine **if** -Funktion:

    ```powerapps-dot
    If( DateAdd( _firstDayInView, ThisItem.Value ) = Today() && 
                DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected, 
            RGBA( 0, 0, 0, 0 ),
        DateAdd( _firstDayInView, ThisItem.Value) = Today(), 
            ColorFade( Subcircle.Fill, 0.67 ),
        Abs( Title.Text - ThisItem.Value) > 10,
            RGBA( 200, 200, 200, 0.3 ),
        RGBA( 0, 0, 0, 0 )
    )
    ```

  Wie in der Beschreibung der **Text** -Eigenschaft erläutert, stellt `DateAdd(_firstDayInView, ThisItem.Value)` den Tag in der sichtbaren Zelle dar. Wenn Sie dies berücksichtigen, führt der vorangehende Code die folgenden Vergleiche aus:
  1. Wenn der Wert der Zelle das heutige Datum ist und diese Zelle **\_datesgewählt**entspricht, geben Sie keinen Füll Wert an.
  1. Wenn der Wert der Zelle das heutige Datum ist, aber nicht äquivalent zu **\_datesgewählt**ist, stellen Sie die **colorfade** -Füllung bereit.
  1. Der letzte Vergleich ist nicht so eindeutig. Dabei handelt es sich um einen Vergleich zwischen dem tatsächlichen Textwert in der Zelle und dem Wert des Zellen Elements (die Zahl bei Anzeige und die Element Nummer).<br>

      Um dies besser zu verstehen, sollten Sie September 2018, einen Monat, der an einem Samstag beginnt und an einem Sonntag endet. In diesem Fall zeigt der Kalender den 26. bis 31. August und den 1. September in der ersten Zeile an, und `Abs(Title.Text - ThisItem.Value) = 26` bis zum 1. September. Dann `Abs(Title.Text - ThisItem.Value) = 5`. Der Wert bleibt 5 bis zur letzten Zeile im Kalender, der am 30. September und am 1. Oktober bis zum 6. Oktober angezeigt wird. In diesem `Abs(Title.Text - ThisItem.Value)` für den 30. September immer noch 5, aber für die Oktober-Daten den Wert 35.<br>

      Dies ist das Muster: Für Tage, die aus dem vorherigen Monat angezeigt werden, entspricht `Abs(Title.Text - ThisItem.Value)` immer dem Wert `Title.Text` des ersten Tags in der Anzeige. Für Tage, die im nächsten Monat angezeigt werden, entspricht `Abs(Title.Text - ThisItem.Value)` immer dem **monthdaygallery** -Elementwert der ersten Zelle dieses Monats (in diesem Fall 1. Oktober) minus 1. Und vor allem für Tage, die im aktuell ausgewählten Monat angezeigt werden, entspricht `Abs(Title.Text - ThisItem.Value)` auch immer dem Wert des ersten Elements des ersten Elements minus 1 und überschreitet niemals 5, wie im vorherigen Beispiel gezeigt. Daher ist es vollkommen gültig, die Formel als `Abs(Title.Text - ThisItem.Value) > 5` zu schreiben.

      Diese Anweisung überprüft, ob der Datumswert außerhalb des aktuell ausgewählten Monats liegt. Wenn dies der Fall ist, ist **Fill** ein teilweise undurchsichtiges grau.

    > [!NOTE]
    > Sie können die Gültigkeit dieses letzten Vergleichs selbst überprüfen, indem Sie ein **Label** -Steuerelement in den Katalog einfügen und dessen **Text** -Eigenschaft auf diesen Wert festlegen:<br>`Abs(Title.Text - ThisItem.Value)`.

- Property **Barem**<br>
    Wert

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    Die vorherige Anweisung überprüft, ob sich die Zelle in einer Zeile befindet, in der keine Tage des aktuell ausgewählten Monats auftreten. Erinnern Sie sich daran, dass die Subtraktion des Wochentag-Werts eines beliebigen Tags von seinem Datumswert und das Hinzufügen von 1 immer das erste Element in der Zeile zurückgibt, in dem sich der Tag befindet Diese Anweisung überprüft also, ob der erste Tag in der Zeile nach dem letzten Tag des sichtbaren Monats liegt. Wenn dies der Fall ist, wird es nicht angezeigt, da die gesamte Zeile Tage des folgenden Monats enthält.

- Property **OnSelect**<br>
    Wert Eine **Set** -Funktion, die die **\_datesselected-** Variable auf das Datum der ausgewählten Zelle festlegt:

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>Kreis-Steuerelement im Kalender Katalog

![Monthdaygallery-Kreis Steuerelement](media/calendar-screen/calendar-month-event.png)

- Property **Barem**<br>
    Wert Eine Formel, die bestimmt, ob Ereignisse für das ausgewählte Datum geplant sind und ob der **unter Kreis** und die **Title** -Steuerelemente sichtbar sind:

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    Das **Kreis** Steuerelement ist sichtbar, wenn das **Startfeld** für ein beliebiges Ereignis mit dem Datum dieser Zelle übereinstimmt, wenn das **Titel** Steuerelement sichtbar ist, und wenn das **unter Kreis** -Steuerelement nicht sichtbar ist. Anders ausgedrückt: dieses Steuerelement ist sichtbar, wenn mindestens ein Ereignis an diesem Tag auftritt, und dieser Tag ist nicht ausgewählt. Wenn diese Option ausgewählt ist, werden die Ereignisse für diesen Tag im **calendareventsgallery** -Steuerelement angezeigt.

### <a name="subcircle-control-in-the-calendar-gallery"></a>Subcircle-Steuerelement im Kalender Katalog

![Subcircle-Steuerelement für monthdaygallery](media/calendar-screen/calendar-month-selected.png)

- Property **Barem**<br>
    Wert

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  Das **subcircle** -Steuerelement ist sichtbar, wenn **\_dateswählte** mit dem Datum der Zelle übereinstimmt und das **Titel** Steuerelement sichtbar ist. Anders ausgedrückt: dieses Steuerelement wird angezeigt, wenn die Zelle das aktuell ausgewählte Datum ist.

## <a name="events-gallery"></a>Ereignis Katalog

![Calendareventsgallery-Steuerelement](media/calendar-screen/calendar-events-gall.png)

- Property **Punkte**<br>
    Wert Eine Formel, die die Ereignis Galerie sortiert und filtert:

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   Die **mycalendarevents** -Auflistung enthält alle Ereignisse zwischen **\_mindate** und **\_maxdate**. Um die Ereignisse nur für das ausgewählte Datum anzuzeigen, wird auf **mycalendarevents** ein Filter angewendet, um die Ereignisse anzuzeigen, deren Startdatum " **\ _dateSelected**" entspricht. Die Elemente werden dann nach Ihren Startdatums Angaben sortiert, um Sie in sequenzieller Reihenfolge zu platzieren.

## <a name="next-steps"></a>Nächste Schritte

- [Weitere Informationen zu diesem Bildschirm](./calendar-screen-overview.md)
- [Weitere Informationen zum Office 365 Outlook-Connector in powerapps](../connections/connection-office365-outlook.md)
- [Weitere Informationen zum Office 365-Benutzer-Connector in powerapps](../connections/connection-office365-users.md)
