---
title: Vorlage für Kalender Bildschirm | Microsoft-Dokumentation
description: Erfahren Sie, wie die Vorlage für Canvas-apps funktioniert, ändern Sie den Bildschirm, und erweitern Sie ihn als Teil einer App.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 945a4fd3c017363a8c43171c8e891e0c32c84a0f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675222"
ms.PowerAppsDecimalTransform: true
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>Übersicht über die Vorlage "Kalender Bildschirm" für Canvas-apps

Fügen Sie in einer Canvas-APP einen Kalender Bildschirm hinzu, der den Benutzern anstehende Ereignisse aus Ihren Office 365 Outlook-Konten anzeigt. Benutzer können ein Datum aus einem Kalender auswählen und durch eine Liste der Ereignisse dieses Tages scrollen. Sie können ändern, welche Details in der Liste angezeigt werden, einen zweiten Bildschirm hinzufügen, der weitere Details zu jedem Ereignis anzeigt, eine Liste der Teilnehmer für jedes Ereignis anzeigen und andere Anpassungen vornehmen.

Sie können auch andere vorlagenbasierte Bildschirme hinzufügen, die unterschiedliche Daten aus Office 365 anzeigen, z. b. [e-Mail](email-screen-overview.md), [Personen](people-screen-overview.md) in einer Organisation und [Verfügbarkeit](meeting-screen-overview.md) von Benutzern, die möglicherweise zu einer Besprechung einladen möchten.

Diese Übersicht vermittelt Ihnen Folgendes:
> [!div class="checklist"]
> * Verwenden des standardmäßigen Kalender Bildschirms.
> * Vorgehensweise beim Ändern der Datei.
> * Integration in eine APP

Einen tieferen Einblick in die Standardfunktionalität dieses Bildschirms finden Sie in der [Calendar-Screen-Referenz](calendar-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen [beim Erstellen einer APP in powerapps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionalität

So fügen Sie einen Kalender Bildschirm aus der Vorlage hinzu:

1. [Melden](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an, und erstellen Sie eine APP, oder öffnen Sie eine vorhandene app in powerapps Studio.

    In diesem Thema wird eine Phone-App gezeigt, aber die gleichen Konzepte gelten auch für eine Tablet-app.

1. Wählen Sie auf der Registerkarte **Start** des Menübands die Option **neuer Bildschirm** > **Kalender**aus.

    Standardmäßig sieht der Bildschirm in etwa wie folgt aus:

    ![Kalender Bildschirm](media/calendar-screen/calendar-initial.png)

1. Wählen Sie zum Anzeigen von Daten eine Option in der Dropdown Liste am oberen Rand des Bildschirms aus.

    ![Kalender Bildschirm nach Abschluss des Ladevorgangs](./media/calendar-screen/calendar-screen.png)

Einige hilfreiche Hinweise:

* Das heutige Datum ist standardmäßig ausgewählt, und Sie können einfach dorthin zurückkehren, indem Sie das Kalendersymbol in der oberen rechten Ecke auswählen.
* Wenn Sie ein anderes Datum auswählen, umgibt es ein Kreis und ein hell farbiges Rechteck (blau, wenn das Standarddesign angewendet wird) umgibt das heutige Datum.
* Wenn mindestens ein Ereignis für ein bestimmtes Datum geplant ist, wird ein kleiner farbiger Kreis unter diesem Datum im Kalender angezeigt.
* Wenn Sie ein Datum auswählen, für das mindestens ein Ereignis geplant ist, werden die Ereignisse in einer Liste unter dem Kalender angezeigt.

## <a name="modify-the-screen"></a>Bildschirm ändern

Sie können die Standardfunktionalität dieses Bildschirms auf einige gängige Weise ändern:

* [Geben Sie den Kalender](calendar-screen-overview.md#specify-the-calendar)an.
* [Anzeigen verschiedener Details zu einem Ereignis](calendar-screen-overview.md#show-different-details-about-an-event).
* [Nicht blockierende Ereignisse ausblenden](calendar-screen-overview.md#hide-nonblocking-events).

Wenn Sie den Bildschirm weiter ändern möchten, verwenden Sie den [Kalender Bildschirm Verweis](./calendar-screen-reference.md) als Leitfaden.

### <a name="specify-the-calendar"></a>Kalender angeben

Wenn Sie bereits wissen, welcher Kalender Ihre Benutzer anzeigen sollen, können Sie den Bildschirm vereinfachen, indem Sie diesen Kalender vor dem Veröffentlichen der APP angeben. Durch diese Änderung entfällt die Notwendigkeit der Dropdown Liste der Kalender, sodass Sie Sie entfernen können.

1. Legen Sie die **[OnStart](../controls/control-screen.md)** -Eigenschaft des Standard Bildschirms in der APP auf diese Formel fest:

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
    > Diese Formel wird vom Standardwert der **onselect** -Eigenschaft der Dropdown Liste für die Auswahl eines Kalenders leicht bearbeitet. Weitere Informationen zu diesem Steuerelement finden Sie im Abschnitt des [Calendar-Screen-Verweises](./calendar-screen-reference.md#calendar-drop-down).

1. Ersetzen Sie `{YourCalendarNameHere}`, einschließlich der geschweiften Klammern, durch den Namen des Kalenders, den Sie anzeigen möchten (z. b. **Calendar**).

    > [!IMPORTANT]
    > Bei den folgenden Schritten wird davon ausgegangen, dass der app nur ein Kalender Bildschirm hinzugefügt wurde. Wenn Sie mehr als ein Element hinzugefügt haben, enden Steuerelement Namen (z. b. **iconCalendar1**) mit einer anderen Zahl, und Sie müssen die Formeln entsprechend anpassen.

1. Legen Sie die **Y** -Eigenschaft des **iconCalendar1** -Steuer Elements auf diesen Ausdruck fest:

    `RectQuickActionBar1.Height + 20`

1. Legen Sie die **Y** -Eigenschaft des **LblMonthSelected1** -Steuer Elements auf diesen Ausdruck fest:

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. Legen Sie die **Text** -Eigenschaft des **LblNoEvents1** -Steuer Elements auf diesen Wert fest:

    `"No events scheduled"`

1. Legen Sie die **Visible** -Eigenschaft von **LblNoEvents1** auf diese Formel fest:

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. Löschen Sie diese Steuerelemente:

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. Wenn der Kalender Bildschirm nicht der Standard Bildschirm ist, fügen Sie eine Schaltfläche hinzu, die vom Standard Bildschirm zum Kalender Bildschirm navigiert, sodass Sie die APP testen können.

    Fügen Sie z. b. auf **Screen1** eine Schaltfläche hinzu, die zu **Screen2** navigiert, wenn Sie einer APP, die Sie aus leer erstellt haben, einen Kalender Bildschirm hinzugefügt haben.

1. Speichern Sie die APP, und testen Sie Sie in einem Browser oder auf einem mobilen Gerät.

### <a name="show-different-details-about-an-event"></a>Andere Details zu einem Ereignis anzeigen

Standardmäßig zeigt der Katalog unter dem Kalender namens **calendareventsgallery**die Startzeit, die Dauer, den Betreff und den Speicherort der einzelnen Ereignisse an. Sie können den Katalog so konfigurieren, dass alle Felder (z. b. der Planer) angezeigt werden, die der [Office 365-Connector](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) unterstützt.

1. Legen Sie in **calendareventsgallery**die **Text** -Eigenschaft einer neuen oder vorhandenen Bezeichnung auf `ThisItem` gefolgt von einem Zeitraum fest.

    IntelliSense listet die Felder auf, die Sie auswählen können.

1. Wählen Sie das gewünschte Feld aus.

    Die Bezeichnung zeigt den Typ der Informationen, die Sie angegeben haben.

### <a name="hide-nonblocking-events"></a>Nicht blockierende Ereignisse ausblenden

In vielen Büros senden Teammitglieder Besprechungs Anfragen, um sich gegenseitig zu benachrichtigen, wenn Sie nicht im Büro sind. Um zu vermeiden, dass alle Zeitpläne blockiert werden, legt die Person, die die Anforderung sendet, die Verfügbarkeit auf **Free**fest Sie können diese Ereignisse aus dem Kalender und dem Katalog ausblenden, indem Sie einige Eigenschaften aktualisieren.

1. Legen Sie die **Items** -Eigenschaft von **calendareventsgallery** auf diese Formel fest:

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

    In dieser Formel verbirgt die **Filter** -Funktion nicht nur die Ereignisse, die für ein anderes Datum als das ausgewählte Datum geplant sind, sondern auch Ereignisse, deren Verfügbarkeit auf **Free**festgelegt ist.

1. Legen Sie die **Visible** -Eigenschaft des **Kreis** -Steuer Elements im Kalender auf diese Formel fest:

    ```powerapps-comma
    CountRows(
        Filter(
            MyCalendarEvents;
            DateValue( Text(Start) ) = DateAdd( _firstDayInView; ThisItem.Value; Days );
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    Diese Formel enthält dieselben Filter wie die vorherige Formel. Daher wird der Ereignis Indikator Kreis nur dann unter einem Datum angezeigt, wenn er mindestens ein Ereignis enthält, das am ausgewählten Datum liegt und für das die Verfügbarkeit nicht auf **Free**festgelegt ist.

## <a name="integrate-the-screen-into-an-app"></a>Integrieren des Bildschirms in eine APP

Der Kalender Bildschirm ist eine leistungsstarke Gruppe von Steuerelementen, die sich in der Regel am besten als Teil einer größeren, vielseitigen App eignet. Sie können diesen Bildschirm auf verschiedene Arten in eine größere App integrieren, einschließlich der folgenden Optionen:

* [Anzeigen von Ereignis Details](calendar-screen-overview.md#view-event-details).
* [Ereignis Teilnehmer anzeigen](calendar-screen-overview.md#show-event-attendees).

### <a name="view-event-details"></a>Anzeigen von Ereignis Details

Wenn Benutzer ein Ereignis in **calendareventsgallery**auswählen, können Sie einen weiteren Bildschirm öffnen, auf dem weitere Informationen zu diesem Ereignis angezeigt werden.

> [!NOTE]
> Diese Prozedur zeigt Ereignis Details in einem Katalog mit dynamischem Inhalt an, aber Sie können ähnliche Ergebnisse erzielen, indem Sie andere Ansätze nutzen. Beispielsweise können Sie mit einer Reihe von Bezeichnungen mehr Entwurfs Steuerelemente erhalten.

1. Fügen Sie einen leeren Bildschirm mit dem Namen **eventdetailsscreen**hinzu, der einen leeren Katalog mit flexibler Höhe und eine Schaltfläche enthält, die zurück zum Kalender Bildschirm navigiert.

1. Fügen Sie im Katalog der flexiblen Höhe ein **Label** -Steuerelement und ein **HTML-Text** -Steuerelement hinzu, und legen Sie die **AutoHeight** -Eigenschaft von both auf **true**fest.

    > [!NOTE]
    > Power apps Ruft den Nachrichtentext jedes Ereignisses als HTML-Text ab, sodass Sie diesen Inhalt in einem **HTML-Text** Steuerelement anzeigen müssen.

1. Legen Sie die **Y** -Eigenschaft des **HTML-Text** -Steuer Elements auf diesen Ausdruck fest:

    `Label1.Y + Label1.Height + 20`

1. Passen Sie zusätzliche Eigenschaften nach Bedarf an Ihre Anforderungen an.

    Beispielsweise können Sie unter dem **HTML-Text** Steuerelement eine Trennlinie hinzufügen.

1. Legen Sie die **Items** -Eigenschaft des Katalogs für die flexible Höhe auf diese Formel fest:

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

    Mit dieser Formel wird ein Katalog dynamischer Daten erstellt, der auf die Feldwerte **_selectedCalendarEvent**festgelegt wird, die jedes Mal festgelegt wird, wenn der Benutzer ein Ereignis im **calendareventsgallery** -Steuerelement auswählt. Sie können diese Galerie erweitern, um weitere Felder einzuschließen, indem Sie weitere Bezeichnungen hinzufügen, aber dieser Satz bietet einen guten Ausgangspunkt.

1. Wenn die Galerie Elemente vorhanden sind, legen Sie die **Text** -Eigenschaft des **Label** -Steuer Elements auf `ThisItem.Title`und die **htmlText** -Eigenschaft des **HTML-Text** -Steuer Elements auf `ThisItem.Value`fest.

1. Legen Sie in **calendareventsgallery**die **onselect** -Eigenschaft des **Title** -Steuer Elements auf diese Formel fest:

    ```powerapps-comma
    Set( _selectedCalendarEvent; ThisItem );;
    Navigate( EventDetailsScreen; None )
    ```

    > [!Note]
    > Anstatt die **_selectedCalendarEvent** Variable zu verwenden, können Sie stattdessen **calendareventsgallery**verwenden. Gewählte.

### <a name="show-event-attendees"></a>Ereignis Teilnehmer anzeigen

Der `Office365.GetEventsCalendarViewV2`-Vorgang ruft eine Vielzahl von Feldern für jedes Ereignis ab, einschließlich eines durch Semikolons getrennten Satzes von erforderlichen und optionalen Teilnehmern. In diesem Verfahren analysieren Sie jede Gruppe von Teilnehmern, legen fest, welche Teilnehmer in Ihrer Organisation sind, und rufen die Office 365-Profile eines beliebigen Benutzers ab.

1. Wenn Ihre APP den Office 365-Benutzer-Connector nicht enthält, [fügen Sie Sie hinzu](../add-data-connection.md).

1. Um die Office 365-Profile der Besprechungs Teilnehmer abzurufen, legen Sie die **onselect** -Eigenschaft des **Title** -Steuer Elements im **calendareventsgallery** auf diese Formel fest:

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

In dieser Liste wird erläutert, was jeder **clearcollect** -Vorgang bewirkt:

- Clearcollect (attende eemailstemp)
    ```powerapps-comma
    ClearCollect( AttendeeEmailsTemp;
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees; ";" ); 
            !IsBlank( Result)
        )
    );;
    ```

    Diese Formel verkettet die erforderlichen und optionalen Teilnehmer zu einer einzelnen Zeichenfolge und teilt diese Zeichenfolge dann bei jedem Semikolon in einzelne Adressen auf. Die Formel filtert dann leere Werte aus diesem Satz heraus und fügt die anderen Werte einer Auflistung mit dem Namen **attende eemailstemp**hinzu.

- Clearcollect (attenabeemails)
    ```powerapps-comma
    ClearCollect( AttendeeEmails;
        AddColumns( AttendeeEmailsTemp; 
            "InOrg";
            Upper( _userDomain ) = Upper( Right( Result; Len(Result) - Find("@"; Result) ) )
        )
    );;
    ```
    Diese Formel bestimmt grob, ob ein Teilnehmer in Ihrer Organisation ist. Die Definition von **_userDomain** ist einfach die Domänen-URL in der e-Mail-Adresse der Person, die die app ausgeführt hat. Diese Zeile erstellt eine zusätzliche true/false-Spalte mit dem Namen **Inorg**in der **attende eemailstemp** -Auflistung. Diese Spalte enthält **true** , wenn **UserDomain** der Domänen-URL der e-Mail-Adresse in der jeweiligen Zeile von **attendeeemailstemp**entspricht.

    Diese Vorgehensweise ist nicht immer genau, aber Sie wird ziemlich nah. Bestimmte Teilnehmer in Ihrer Organisation können z. b. eine e-Mail-Adresse wie Jane@OnContoso.comhaben, während **_userDomain** contoso.com ist. Der App-Benutzer und Jane können im selben Unternehmen arbeiten, haben aber leichte Abweichungen in Ihren e-Mail-Adressen. In diesen Fällen können Sie die folgende Formel verwenden:

    `Upper(_userDomain) in Upper(Right(Result; Len(Result) - Find("@"; Result)))`

    Diese Formel stimmt jedoch mit e-Mail-Adressen wie Jane@NotTheContosoCompany.com mit einem **_userDomain** wie contoso.com überein, und diese Personen arbeiten nicht in demselben Unternehmen.

- Clearcollect (mypeople)

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
    Zum Abrufen von Office 365-Profilen müssen Sie den [Office365Users. USERPROFILE](https://docs.microsoft.com/connectors/office365users/#userprofile) -oder [Office365Users. UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) -Vorgang verwenden. Diese Vorgänge sammeln zuerst alle Office 365-Profile für Teilnehmer, die sich in der Organisation des Benutzers befinden. Dann fügen die Vorgänge einige Felder für Teilnehmer von außerhalb der Organisation hinzu. Sie haben diese beiden Elemente in verschiedene Vorgänge aufgeteilt, da die **ForAll** -Schleife die Reihenfolge nicht garantiert. Daher kann **ForAll** einen Teilnehmer von außerhalb der Organisation zuerst erfassen. In diesem Fall enthält das Schema für " **mypeople** " nur " **Display Name**", " **ID**", " **JobTitle**" und " **userPrincipalName**". Die USERPROFILE-Vorgänge rufen jedoch weitaus umfangreichere Daten ab. Daher erzwingen Sie, dass die **mypeople** -Sammlung Office 365-profile vor den anderen Profilen hinzufügt.

    > [!NOTE]
    > Sie können dasselbe Ergebnis mit nur einer **clearcollect** -Funktion erzielen:

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

So beenden Sie diese Übung:

1. Fügen Sie einen Bildschirm hinzu, der einen Katalog enthält, für den die **Items** -Eigenschaft auf **mypeople**festgelegt ist.

1. Fügen Sie in der **onselect** -Eigenschaft des **Title** -Steuer Elements im **calendareventsgallery**dem Bildschirm, den Sie im vorherigen Schritt erstellt haben, eine **Navigate** -Funktion hinzu.

## <a name="next-steps"></a>Nächste Schritte

* [Sehen Sie sich die Referenz Dokumentation für diesen Bildschirm an](calendar-screen-reference.md).
* [Erfahren Sie mehr über den Outlook-Connector von Office 365](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über den Connector für Office 365-Benutzer](../connections/connection-office365-users.md).
