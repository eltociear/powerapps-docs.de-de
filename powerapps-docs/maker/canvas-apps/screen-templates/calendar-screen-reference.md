---
title: Referenz für die Calendar-Bildschirmvorlage für Canvas-apps | Microsoft-Dokumentation
description: Verstehen Sie die Details der Funktionsweise der Kalender-Screen-Vorlage für Canvas-apps in PowerApps.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e3d5f40a604d2cbfa074ed5973d599c40a6c5c05
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539008"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>Referenzinformationen zu den Kalender-Bildschirmvorlage für Canvas-apps

Für Canvas-apps in PowerApps zu verstehen, wie jede bedeutende Kontrolle in der Calendar-Screen-Vorlage, die standardmäßige Gesamtfunktionalität des Bildschirms beiträgt. Tieferer Einblick in diese stellt die verhaltensformeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine allgemeine Diskussion über die Standardfunktionalität des Bildschirms, finden Sie unter den [Kalender-Übersicht über](calendar-screen-overview.md).

In diesem Thema werden einige wichtige steuermöglichkeiten und erläutert die Ausdrücke oder Formeln, die die verschiedenen Eigenschaften (z. B. **Elemente** und **OnSelect**) dieser Steuerelemente festgelegt werden:

- [Kalender (DropdownCalendarSelection)](#calendar-drop-down)
- [Symbol "Kalender" (IconCalendar)](#calendar-icon)
- [Previous-month chevron (iconPrevMonth)](#previous-month-chevron)
- [Nächsten Monat Chevron (IconNextMonth)](#next-month-chevron)
- [Kalender-Katalog (MonthDayGallery) (+ untergeordnete Steuerelemente)](#calendar-gallery)
- [Ereignisse-Katalog (CalendarEventsGallery)](#events-gallery)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="calendar-drop-down"></a>Kalender Dropdown-Liste

![DropdownCalendarSelection-Steuerelement](media/calendar-screen/calendar-dropdown.png)

- Eigenschaft: **Elemente**<br>
    Wert: `Office365.CalendarGetTables().value`

    Dieser Wert ist ein Connector-Vorgang, der app-Benutzer Outlook-Kalender abgerufen. Sehen Sie [Wert](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table]) , die durch diesen Vorgang abgerufen.

- Eigenschaft: **OnChange**<br>Wert: `Select(dropdownCalendarSelection)`

    Wenn der Benutzer eine Option auswählt, in der Liste die Funktion in des Steuerelements **OnSelect** Eigenschaft ausgeführt wird.

- Eigenschaft: **OnSelect**<br>
    Wert: Ein **Wenn** -Funktion, die in den folgenden Codeblock angezeigt wird, und einige zusätzliche Funktionen, die in den Codeblock nach, die angezeigt werden.

   Dieser Teil der Formel nur beim ersten Mal, dass der Benutzer eine Option in der Dropdownliste auswählt, nach dem Öffnen der app-Ausführungen:

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

    Der vorhergehende Code definiert die folgenden Variablen:
    
  - **\_userDomain**: Der app-Benutzer-Unternehmensdomäne, wie die e-Mail-Adresse des Benutzers dargestellt.
  - **\_dateSelected**: Aktuelles Datum (standardmäßig). Die Kalender-Galerie highlights dieses Datum und der Ereignis-Katalog zeigt die Ereignisse, die für dieses Datum geplant ist.
  - **\_firstDayOfMonth**: Der erste Tag des aktuellen Monats. Da `(Today + (1 - Today)) = Today - Today + 1 = 1`wird in diesem **DateAdd** Funktion gibt immer den ersten Tag des Monats zurück.
  - **\_firstDayInView**: Der erste Tag, die der Kalender-Katalog anzeigen können. Dieser Wert ist identisch mit den ersten Tag des Monats nicht, es sei denn, ein Sonntag des Monats beginnt. Um zu verhindern, zeigt eine ganze Woche des vorherigen Monats, um den Wert der  **\_FirstDayInView** ist `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1`.
  - **\_lastDayOfMonth**: Der letzte Tag des aktuellen Monats, der den ersten Tag des nächsten Monats, abzüglich eines Tages entspricht.

   Die Funktionen nach der **Wenn** Funktion ausgeführt wird, wenn der Benutzer wählt eine Option in der Dropdown-Liste der Kalender (nicht nur beim ersten die app den Benutzer öffnen):

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

    Der vorhergehende Code definiert diese Variablen und einer Auflistung:

    - **\_calendarVisible**: Legen Sie auf **"false"** so, dass der Kalender nicht angezeigt wird, während die neue Auswahl geladen wird.
    - **\_showLoading**: Legen Sie auf **"true"** , damit beim Laden von Indikatoren angezeigt werden, während die neue Auswahl geladen wird.
    - **\_myCalendar**: Legen Sie auf den aktuellen Wert des der **Dropdown-Kalender** Steuerelement, sodass Ereignisse aus dem richtigen Kalender abgerufen werden.
    - **\_minDate**: Legen Sie auf den gleichen Wert wie  **\_FirstDayInView**. Diese Variable wird bestimmt, welche Ereignisse bereits vom Outlook abgerufen und in der app zwischengespeichert wurden.
    - **\_maxDate**: Legen Sie auf der letzten sichtbaren Tag im Kalender. Die Formel lautet `_firstDayInView + 40`. Der Kalender zeigt maximal 41 Tage, sodass die  **\_MaxDate** Variable immer gibt den letzten Tag des angezeigt werden kann, und bestimmt, welche Ereignisse bereits vom Outlook abgerufen und in der app zwischengespeichert wurden.
    - **MyCalendarEvents**: Legen Sie auf eine Auflistung von Ereignissen für den Benutzer aus dem ausgewählten Kalender, die im Bereich von  **\_MinDate** zu  **\_MaxDate**.
    - **\_showLoading**: Legen Sie auf **"false"**;  **\_CalendarVisible** nastaven NA hodnotu **"true"** nachdem alles geladen wurde.

## <a name="calendar-icon"></a>Symbol "Kalender"

![IconCalendar-Steuerelement](media/calendar-screen/calendar-today-icon.png)

- Eigenschaft: **OnSelect**<br>
    Wert: Vier **festgelegt** Funktionen, die den Kalender-Katalog auf das aktuelle Datum zurücksetzen:

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    Der vorangehende Code setzt alle Datenvariablen, die für die Anzeige der richtigen Kalenderansicht erforderlich sind:

    - **\_DateSelected** zu heute zurückgesetzt.
    - **\_FirstDayOfMonth** wird auf den ersten Tag des des aktuellen Monats zurückgesetzt.
    - **\_FirstDayInView** wird zurückgesetzt, auf den ersten Tag angezeigt werden Wenn des aktuellen Monats aktiviert ist.
    - **\_LastDayOfMonth** wird bis zum letzten Tag des des aktuellen Monats zurückgesetzt.

    Die [ **Dropdown-Kalender** ](#calendar-drop-down) Abschnitt dieses Themas wird dieser Variablen im Detail erläutert.

## <a name="previous-month-chevron"></a>Vorheriger Monat chevron

![IconPrevMonth-Steuerelement](media/calendar-screen/calendar-back.png)

- Eigenschaft: **OnSelect**<br>Wert: Vier **festgelegt** Funktionen und ein **Wenn** -Funktion, die den vorhergehenden Monat im Katalog Kalender angezeigt:

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
    > Definitionen für  **\_FirstDayOfMonth**,  **\_FirstDayInView**, und  **\_LastDayOfMonth** sind nahezu identisch, mit denen in der [Dropdown-Kalender](#calendar-drop-down) Abschnitt dieses Themas.

    Die ersten drei Zeilen des vorangehenden Codes ausgeführt, wenn der Benutzer auf das Chevron vorherigen Monat auswählt. Der Code legt die Variablen, die erforderlich sind, um die richtige Kalenderansicht angezeigt. Der restliche Code wird nur dann, wenn der Benutzer diesen Monat für den ausgewählten Kalender zuvor ausgewählt wurde nicht ausgeführt.

    Wenn dies der Fall ist,  **\_MinDate** ist der erste Tag, die angezeigt wird, wenn es sich bei der vorherige Monat angezeigt wird. Bevor der Benutzer das Symbol auswählt  **\_MinDate** verfügt über eine minimale Wert von dem 23. des aktuellen Monats. (Wenn an einem Samstag, 1. März fällt  **\_FirstDayInView** für März Februar 23 ist.) Das heißt, wenn ein Benutzer in diesem Monat noch ausgewählt noch nicht  **\_MinDate** ist größer als die neue  **\_FirstDayOfMonth**, und die **Wenn** Funktion gibt **"true"**. Der Code ausgeführt wird, und eine Sammlung und einer Variablen werden aktualisiert:

    - **MyCalendarEvents** ruft Ereignisse ab, aus dem ausgewählten Kalender mit dem [Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) Vorgang. Der Datumsbereich liegt zwischen dem  **\_FirstDayInView** Datum und  **\_MinDate** - 1. Da **MyCalendarEvents** bereits Ereignisse enthält, auf die  **\_MinDate** Datum 1 ab diesem Datum für den maximalen Wert in diesem Bereich neue Datum subtrahiert wird.

    - **\_MinDate** festgelegt ist, mit dem aktuellen  **\_FirstDayInView** da dies das erste Datum ist für die Ereignisse abgerufen wurden. Wenn ein Benutzer zu diesem Datum zurück, wählen Sie die vorherigen Monat Chevron-Schaltfläche, die **Wenn** -Funktion zurückgegeben **"false"**; der Code nicht ausgeführt werden, da Ereignisse für diese Ansicht in bereits zwischengespeichert werden  **MyCalendarEvents**.

## <a name="next-month-chevron"></a>Nächsten Monat chevron

![IconNextMonth-Steuerelement](media/calendar-screen/calendar-forward.png)

- Eigenschaft: **OnSelect**<br>
    Wert: Vier **festgelegt** Funktionen und ein **Wenn** -Funktion, die im nächsten Monat im Katalog Kalender angezeigt:

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
    > Definitionen für  **\_FirstDayOfMonth**,  **\_FirstDayInView**, und  **\_LastDayOfMonth** sind nahezu identisch, mit denen in der [Dropdown-Kalender](#calendar-drop-down) Abschnitt dieses Themas.

    Die ersten drei Zeilen des vorherigen Codes, der ausgeführt wird, wenn der Benutzer die nächsten Monate Chevron-Schaltfläche auswählt, legen Sie die Variablen, die erforderlich sind, um die richtige Kalenderansicht angezeigt. Der restliche Code wird nur dann, wenn der Benutzer diesen Monat für den ausgewählten Kalender zuvor ausgewählt wurde nicht ausgeführt.

    In diesem Fall  **\_MaxDate** ist der letzte Tag, die angezeigt wird, wenn es sich bei der vorherige Monat angezeigt wird. Bevor der Benutzer auf das Chevron nächsten Monat auswählt  **\_MaxDate** hat einen maximalen möglichen Wert der vom 13. bis des nächsten Monats. (Wenn der 1. Februar auf eine kein Schaltjahr Sonntag, fällt  **\_MaxDate** ist 13. März handelt es sich  **\_FirstDayInView** + 40 Tagen.) Das heißt, wenn ein Benutzer in diesem Monat noch ausgewählt noch nicht  **\_MaxDate** ist größer als die neue  **\_LastDayOfMonth**, und die **Wenn** Funktion Gibt **"true"**. Der Code ausgeführt wird, und eine Sammlung und einer Variablen werden aktualisiert:

    - **MyCalendarEvents** ruft Ereignisse ab, aus dem ausgewählten Kalender mit dem [Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) Vorgang. Der Datumsbereich liegt zwischen  **\_MaxDate** + 1 Tag und  **\_FirstDayInView** + 40 Tagen. Da **MyCalendarEvents** bereits Ereignisse enthält, auf die  **\_MinDate** Datum 1 wird hinzugefügt, dem Datum für den minimalen Wert in diesem Bereich des neuen Datums. **\_FirstDayInView** + 40 wird die Formel für  **\_MaxDate**, deshalb ist das zweite Datum im Bereich der neuen  **\_MaxDate**.

    - **\_MaxDate** nastaven NA hodnotu  **\_FirstDayInView** + 40 Tagen, da dies der letzte Tag ist für das Ereignisse abgerufen wurden. Wenn ein Benutzer zu diesem Datum zurück, wählen Sie die nächsten Monate Chevron-Schaltfläche, die **Wenn** -Funktion zurückgegeben **"false"**; der Code nicht ausgeführt werden, da Ereignisse für diese Ansicht in bereits zwischengespeichert werden  **MyCalendarEvents**.

## <a name="calendar-gallery"></a>Kalender-Katalog

![MonthDayGallery-Steuerelement](media/calendar-screen/calendar-month-gall.png)

- Eigenschaft: **Elemente**<br>
    Wert: `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  Der Satz von 0 bis 41 für die Elemente im Katalog Kalender verwendet, da, im Falle des ungünstigsten Szenarios die Kalenderansicht 42 vollständige Tage anzeigen muss. Dies tritt auf, wenn es sich bei den ersten Tag des Monats am Samstag und die letzten des Monats erfolgt an einem Sonntag. In diesem Fall zeigt der Kalender, sechs Tage des vorherigen Monats in der Zeile mit dem ersten Tag des Monats und sechs Tage aus dem folgenden Monat in der Zeile mit dem letzten des Monats. Dies ist 42 eindeutige Werte, die als 30 Jahre für den ausgewählten Monat sind.

- Eigenschaft: **WrapCount**<br>
    Wert: `7`

  Dieser Wert gibt die sieben Tage pro Woche wieder.

### <a name="title-control-in-the-calendar-gallery"></a>Titel des Steuerelements in der Calendar-Galerie

![MonthDayGallery Titel des Steuerelements](media/calendar-screen/calendar-month-text.png)

- Eigenschaft: **Text**<br>
    Wert: `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    Zur Erinnerung:  **\_FirstDayInView** als definiert ist (**\_FirstDayOfMonth** – den Wochentagwert) + 1. Hier erfahren Sie, die  **\_FirstDayInView** ist immer ein Sonntag und  **\_FirstDayOfMonth** befindet sich immer in der ersten Zeile der **MonthDayGallery**. Aufgrund dieser zwei Fakten  **\_FirstDayInView** ist immer in der ersten Zelle des **MonthDayGallery**. **ThisItem.Value** ist die Anzahl für diese Zelle in der **MonthDayGallery** item (Eigenschaft). Daher dauert  **\_FirstDayInView** als Ausgangspunkt, jede Zelle zeigt den inkrementellen Wert von  **\_FirstDayInView** und der Zellenwert für die jeweilige.

- Eigenschaft: **Füllung**<br>
    Wert: Eine **Wenn** Funktion:

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

  Wie in der Beschreibung des erläutert die **Text** Eigenschaft `DateAdd(_firstDayInView, ThisItem.Value)` stellt den Tag dar, in der Zelle angezeigt. Berücksichtigung dieser, führt der obige Code diese Vergleiche:
  1. Wenn der Wert der Zelle wird das aktuelle Datum und diese Zelle ist äquivalent zu  **\_DateSelected**, geben Sie einen Fill-Wert nicht.
  1. Wenn der Wert der Zelle des heutigen Datums ist, aber nicht äquivalent  **\_DateSelected**, geben Sie die **ColorFade** füllen.
  1. Die letzte Vergleich nicht so klar. Es ist ein Vergleich zwischen den eigentlichen Text-Wert in der Zelle und dem Wert des Elements Zelle (die Anzahl auf Anzeige) und die Artikelnummer.<br>

      Um besser verstehen, betrachten September 2018, einem Monat, die an einem Samstag beginnt und endet am Sonntag. Der Kalender zeigt in diesem Fall den 26. bis 31. August und dem 1. September an, in der ersten Zeile und `Abs(Title.Text - ThisItem.Value) = 26` bis zum 1. September. Klicken Sie dann `Abs(Title.Text - ThisItem.Value) = 5`. Es wird auf 5 die letzte Zeile im Kalender, bleiben, bis der 30. September und dem 1. Oktober bis 6. angezeigt. Insofern `Abs(Title.Text - ThisItem.Value)` werden 5 für den 30. September, jedoch werden für die Oktober-Datumsangaben 35.<br>

      Dies ist das Muster: Für Tage, angezeigt wird, aus dem vorherigen Monat `Abs(Title.Text - ThisItem.Value)` ist immer gleich der `Title.Text` Wert des ersten Tages auf Anzeige. Für Tage, die in den nächsten Monat angezeigt wird `Abs(Title.Text - ThisItem.Value)` ist immer gleich der **MonthDayGallery** Element der Wert der ersten Zelle des Monats (in diesem Fall dem 1. Oktober) minus 1. Und vor allem für Tage, die im aktuell ausgewählten Monat angezeigt `Abs(Title.Text - ThisItem.Value)` entspricht immer den Wert des ersten Elements des betreffenden Monats minus 1 und 5, wie im vorherigen Beispiel gezeigt wird nie übersteigen. Daher ist es absolut gültige zum Schreiben der Formel als `Abs(Title.Text - ThisItem.Value) > 5`.

      Diese Anweisung überprüft, ob es sich bei der Date-Wert außerhalb der aktuell ausgewählten Monat liegt. Wenn es sich handelt, **füllen** ist eine teilweise nicht transparente grau.

    > [!NOTE]
    > Sehen Sie die Gültigkeit des diesem letzten Vergleich für sich selbst durch Einfügen einer **Bezeichnung** Steuerelement in den Katalog und die Einstellung der **Text** -Eigenschaft auf diesen Wert:<br>`Abs(Title.Text - ThisItem.Value)`.

- Eigenschaft: **Visible**<br>
    Wert:

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    Die vorhergehende Anweisung überprüft, ob die Zelle in einer Zeile, in denen keine Tage des Monats aktuell ausgewählten auftreten. Denken Sie daran, dass den Weekday-Wert, der einem beliebigen Tag in der Date-Wert subtrahiert und Hinzufügen von 1 wird immer, dass das erste Element in der Zeile befindet sich dieses Tag zurückgegeben in. Damit diese Anweisung überprüft, ob der erste Tag in der Zeile nach dem letzten Tag des Monats angezeigt werden kann. Wenn es sich handelt, wird nicht es angezeigt, da die gesamte Zeile Tage des nächsten Monats enthält.

- Eigenschaft: **OnSelect**<br>
    Wert: Ein **festgelegt** Funktion, setzt der  **\_DateSelected** Variable auf das Datum der ausgewählten Zelle:

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>Kreis-Steuerelement in der Calendar-Galerie

![MonthDayGallery Kreis-Steuerelement](media/calendar-screen/calendar-month-event.png)

- Eigenschaft: **Visible**<br>
    Wert: Eine Formel, die bestimmt, ob alle Ereignisse für das ausgewählte Datum geplant sind, und ob die **Subcircle** und **Titel** Steuerelemente sichtbar sind:

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    Die **Kreis** -Steuerelement sichtbar ist wenn die **starten** Feld für jedes Ereignis, für das Datum dieser Zelle entspricht, wenn die **Titel** Steuerelement sichtbar ist, und, wenn die  **Subcircle** Steuerelement nicht sichtbar ist. Das heißt, wird das Steuerelement angezeigt, wenn mindestens ein Ereignis tritt auf, an diesem Tag ein, und diesem Tag nicht aktiviert ist. Wenn es aktiviert ist, werden die Ereignisse für diesen Tag angezeigt, der **CalendarEventsGallery** Steuerelement.

### <a name="subcircle-control-in-the-calendar-gallery"></a>Subcircle-Steuerelement in der Calendar-Galerie

![MonthDayGallery Subcircle-Steuerelement](media/calendar-screen/calendar-month-selected.png)

- Eigenschaft: **Visible**<br>
    Wert:

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  Die **Subcircle** Steuerelement ist sichtbar, wenn  **\_DateSelected** ist gleichbedeutend mit dem Datum der Zelle, und die **Titel** -Steuerelement sichtbar ist. Das heißt, wird dieses Steuerelement angezeigt, wenn die Zelle, die derzeit ausgewählte Datum ist.

## <a name="events-gallery"></a>Ereignisse-Katalog

![CalendarEventsGallery-Steuerelement](media/calendar-screen/calendar-events-gall.png)

- Eigenschaft: **Elemente**<br>
    Wert: Eine Formel, die Sortierungen und Filter im Katalog Ereignisse:

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   Die **MyCalendarEvents** Auflistung enthält alle Ereignisse zwischen  **\_MinDate** und  **\_MaxDate**. Um die Ereignisse für das ausgewählte Datum anzuzeigen, ein Filter angewendet wird, auf **MyCalendarEvents** um Ereignisse anzuzeigen, die ein Startdatum entspricht **\ _dateSelected**. Die Elemente werden dann durch die Startdaten Einsatzort in sequenzieller Reihenfolge sortiert.

## <a name="next-steps"></a>Nächste Schritte

- [Weitere Informationen zu diesem Bildschirm](./calendar-screen-overview.md)
- [Erfahren Sie mehr über das Office 365 Outlook-Connector in PowerApps](../connections/connection-office365-outlook.md)
- [Erfahren Sie mehr über das Office 365-Benutzer-Connector in PowerApps](../connections/connection-office365-users.md)
