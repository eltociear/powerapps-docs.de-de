---
title: Referenz für die Besprechungs Bildschirm Vorlage für Canvas-apps | Microsoft-Dokumentation
description: Details zur Funktionsweise der Besprechungs Bildschirm Vorlage für Canvas-apps in powerapps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c62c3de56534201a81e9f4d453796ebd9b3a0366
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71989572"
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>Referenzinformationen zur Besprechungs Bildschirm Vorlage für Canvas-apps

Für Canvas-apps in powerapps können Sie verstehen, wie die einzelnen wichtigen Steuerelemente in der Vorlage für den Besprechungs Bildschirm zur gesamten Standardfunktionalität des Bildschirms beitragen. Dieser ausführliche Einblick zeigt die Verhaltens Formeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine allgemeine Erörterung der Standardfunktionalität dieses Bildschirms finden Sie in der [Übersicht über den Besprechungs Bildschirm](meeting-screen-overview.md).

In diesem Thema werden einige bedeutende Steuerelemente hervorgehoben und die Ausdrücke oder Formeln erläutert, mit denen verschiedene Eigenschaften (z. b. **Elemente** und **onselect**) dieser Steuerelemente festgelegt werden:

* [Registerkarte "einladen" (lblinvitetab)](#invite-tab)
* [Registerkarte "Zeitplan" (lblscheduletab)](#schedule-tab)
* [Textsuchfeld](#text-search-box)
* [Symbol "hinzufügen" (addicon)](#add-icon)
* Benutzer [Durchsuchen Gallery](#people-browse-gallery) (+ untergeordnete Steuerelemente)
* [Meeting People Gallery](#meeting-people-gallery) (+ untergeordnete Steuerelemente)
* [Besprechungs Datumsauswahl (meetingdateselect)](#meeting-date-picker)
* [Dropdown Liste für Besprechungs Dauer (meetingdurationselect)](#meeting-duration-drop-down)
* [Suche nach Besprechungszeiten Gallery](#find-meeting-times-gallery) (+ untergeordnete Steuerelemente)
* Katalog mit [Raum suchen](#room-browse-gallery) (+ untergeordnete Steuerelemente)
* [Zurück Chevron (roomsbacknav)](#back-chevron) (möglicherweise nicht sichtbar, wenn der Mandant keine Räume Listen hat)
* [Symbol "Senden"](#send-icon)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen [beim Erstellen einer APP in powerapps](../data-platform-create-app-scratch.md).

## <a name="invite-tab"></a>Registerkarte einladen

   ![Lblinvitetab-Steuerelement](media/meeting-screen/meeting-invite-text.png)

* Property **Farbe**<br>
    Wert: `If( _showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** ist eine Variable, mit der bestimmt wird, ob das **lblinvitetab** -Steuerelement oder das **lblscheduletab** -Steuerelement ausgewählt ist. Wenn der Wert von **_showDetails** auf **true**festgelegt ist, wird **lblscheduletab** ausgewählt. Wenn der Wert **false**ist, wird **lblinvitetab** ausgewählt. Dies bedeutet Folgendes: Wenn der Wert von _showDetails **true** ist (diese Registerkarte ist *nicht* ausgewählt), entspricht die Registerkarten Farbe der **lblrecepentcount**. Andernfalls entspricht Sie dem Füllwert von **rectquickaktionbar**.

* Property **OnSelect**<br> 
    Wert: `Set( _showDetails, false )`

    Legt die **_showDetails** -Variable auf " **false**" fest. Dies bedeutet, dass der Inhalt der Registerkarte "einladen" sichtbar ist und der Inhalt der Registerkarte " **Zeitplan** " ausgeblendet ist.

## <a name="schedule-tab"></a>Registerkarte Zeitplan

   ![Lblinvitetab-Steuerelement](media/meeting-screen/meeting-schedule-text.png)

* Property **Farbe**<br>
    Wert: `If( !_showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** ist eine Variable, mit der bestimmt wird, ob das **lblinvitetab** -Steuerelement oder das **lblscheduletab** -Steuerelement ausgewählt ist. Wenn der Wert true ist, wird **lblscheduletab** ausgewählt. false gibt an, dass **lblinvitetab** ist. Dies bedeutet Folgendes: Wenn **_showDetails** true ist (diese Registerkarte *ist* ausgewählt), entspricht die Registerkarten Farbe dem Füllwert von **rectquickaktionbar**. Andernfalls entspricht Sie dem Farbwert **lblrecepentcount**.

* Property **OnSelect**<br>
    Wert: `Set( _showDetails, true )`

    Legt die **_showDetails** -Variable auf **true**fest. Dies bedeutet, dass der Inhalt der Registerkarte "Zeitplan" sichtbar ist und der Inhalt der Registerkarte "einladen" ausgeblendet ist.

## <a name="text-search-box"></a>Textsuchfeld

   ![Textsearchbox-Steuerelement](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

Mehrere andere Steuerelemente auf dem Bildschirm haben eine Abhängigkeit von dieser:

* Wenn ein Benutzer mit der Eingabe von Text beginnt, wird **peoplebrowsegallery** sichtbar.
* Wenn ein Benutzer eine gültige e-Mail-Adresse eingibt, wird **addicon** sichtbar.
* Wenn ein Benutzer eine Person in **peoplebrowsegallery** auswählt, werden die Such Inhalte zurückgesetzt.

## <a name="add-icon"></a>Symbol „Hinzufügen“

   ![Addicon-Steuerelement](media/email-screen/email-add-icon.png)

Dieses Steuerelement ermöglicht Benutzern das Hinzufügen von Personen, die nicht in Ihrer Organisation vorhanden sind, zur Teilnehmer Liste für das zusammengesetzte Meeting.

* Property **Barem**<br>
    Wert Drei logische Überprüfungen, die alle als **true** ausgewertet werden müssen, damit das Steuerelement sichtbar ist:

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  Zeilenweise bedeutet dieser Codeblock, dass das **addicon** -Steuerelement nur dann sichtbar ist, wenn Folgendes gilt:

  * **Textsearchbox** enthält Text.
  * Der Text in **textsearchbox** ist eine gültige e-Mail-Adresse.
  * Der Text in **textsearchbox** ist in der **mypeople** -Auflistung nicht bereits vorhanden.

* Property **OnSelect**<br> 
    Wert Eine **Collect** -Anweisung zum Hinzufügen des Benutzers zur Liste der Teilnehmer, eine weitere zum Aktualisieren verfügbarer Besprechungszeiten und verschiedene Variablen Schalter:

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    { 
                        RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";")
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage:1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  Wenn Sie dieses Steuerelement auswählen, wird die gültige e-Mail-Adresse (nur sichtbar, wenn eine gültige e-Mail-Adresse in **textsearchbox**eingegeben wurde) zur **mypeople** -Sammlung hinzugefügt (diese Sammlung ist die Liste der Teilnehmer) und dann die verfügbaren Besprechungszeiten mit der neuen Benutzereintrag.

  Dieser Codeblock auf niedriger Ebene:
  1. Sammelt die e-Mail-Adresse in der **mypeople** -Auflistung und sammelt die e-Mail-Adresse in den Feldern **Display Name**, **userPrincipalName**und **Mail** .
  1. Setzt den Inhalt des **textsearchbox** -Steuer Elements zurück.
  1. Legt die **_showMeetingTimes** -Variable auf **false**fest. Diese Variable steuert die Sichtbarkeit von **findmeetingtimesgallery**, die Öffnungszeiten anzeigt, die die ausgewählten Teilnehmer erfüllen.
  1. Legt die **_loadMeetingTimes** -Kontext Variable auf **true**fest. Diese Variable legt einen Ladezustand fest, der die Sichtbarkeit des Ladens von Zustands Steuerelementen wie **_LblTimesEmptyState** schaltet, um dem Benutzer mitzuteilen, dass die Daten geladen werden.
  1. Legt **_selectedMeetingTime** auf **blank ()** fest. **_selectedMeetingTime** ist der ausgewählte Datensatz aus dem **findmeetingtimesgallery** -Steuerelement. Diese wird hier angezeigt, da das Hinzufügen eines anderen Teilnehmers möglicherweise bedeutet, dass die vorherige Definition von **_selectedMeetingTime** für diesen Teilnehmer nicht verfügbar ist.
  1. Legt **_selectedRoom** auf **blank ()** fest. **_selectedRoom** ist der ausgewählte Raum Daten Satz aus " **roombrowsegallery**". Die Verfügbarkeit des Raums wird anhand des Werts von **_selectedMeetingTime**bestimmt. Wenn dieser Wert leer ist, ist der **_selectedRoom** -Wert nicht mehr gültig und muss daher leer sein.
  1. Legt **_roomListSelected** auf **false**fest. Diese Zeile gilt möglicherweise nicht für alle. In Office können Sie Ihre Räume nach verschiedenen "Raum Listen" gruppieren. Wenn Sie über Raum Listen verfügen, werden Sie von diesem Bildschirm berücksichtigt, sodass Sie zuerst eine Raum Liste auswählen können, bevor Sie in dieser Liste einen Raum auswählen. Der Wert von **_roomListSelected** bestimmt, ob ein Benutzer (nur in einem Mandanten mit Raum Listen) Räume in einer Raum Liste oder in der Liste der Raum Listen anzeigen wird. Der Wert ist auf " **false** " festgelegt, um Benutzer zu zwingen, eine neue Raum Liste erneut auszuwählen.
  1. Verwendet den [Office 365. findmeetingtimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) -Vorgang, um die verfügbaren Besprechungszeiten für die Teilnehmer zu ermitteln und zu erfassen. Dieser Vorgang übergibt Folgendes:
      * Der **userPrincipalName** der einzelnen ausgewählten Benutzer in den Requirements *dattendees* -Parameter.
      * " **Meetingdurationselect**". Ausgewählt. Minuten in den Parameter " *meetingduration* ".
      * "Meetingdateselect. SelectedDate + 8 Stunden" im *Start* Parameter. Es werden acht Stunden hinzugefügt, da das vollständige Datum/die Uhrzeit für das Kalender Steuerelement standardmäßig 12:00 Uhr des ausgewählten Datums ist. Wahrscheinlich möchten Sie die Verfügbarkeit innerhalb der normalen Arbeitszeit abrufen. Eine normale Startzeit für die Arbeit beträgt 8:00 Uhr.
      * **Meetingdateselect**. SelectedDate + 17 Stunden in den *End* -Parameter. 17 Stunden werden hinzugefügt, da 12:00 Uhr + 17 = 5:00 Uhr. Die Endzeit der normalen Arbeit beträgt 5:00 Uhr.
      * *15* in den *maxcandidate* -Parameter. Dies bedeutet, dass der Vorgang nur die ersten 15 verfügbaren Zeiten für das ausgewählte Datum zurückgibt. Dies ist sinnvoll, da es nur 16 30-minütige Blöcke an einem 8-Stunden-Arbeitstag gibt und ein 30-minütiges Meeting in diesem Bildschirm festgelegt werden kann.
      * *1* in den *minimumattendeeprozent* -Parameter. Im Grunde wird die Besprechungszeit abgerufen, es sei denn, es sind keine Teilnehmer verfügbar.
      * **false** in den *isorganizeroptionalen* -Parameter. Der App-Benutzer ist kein Optionaler Teilnehmer für diese Besprechung.
      * "Arbeiten" im Parameter " *activitydomain* ". Dies bedeutet, dass die abgerufenen Zeiten nur solche innerhalb eines normalen Arbeits Zeitraums sind.
  1. Die **clearcollect** -Funktion fügt auch zwei Spalten hinzu: "StartTime" und "EndTime". Dadurch werden die zurückgegebenen Daten vereinfacht. 
  Das Feld, das die verfügbaren Start-und Endzeiten enthält, ist das Feld " **meetingtimeslot** ". Bei diesem Feld handelt es sich um einen Datensatz, der die Start-und Enddaten Sätze enthält, die den **DateTime** -Wert und den **TimeZone** -Wert des jeweiligen Vorschlags enthalten. Anstatt zu versuchen, diese Schachtelung von Datensätzen abzurufen, werden die Spalten "StartTime" und "EndTime" in der Auflistung " **meetingtimes** " mit den Werten **Start > DateTime** und **End > DateTime** auf der Oberfläche der Auflistung angezeigt.
  1. Sobald diese Funktionen abgeschlossen sind, wird die **_loadingMeetingTimes** -Variable auf **false**festgelegt, und der Ladezustand wird entfernt, und **_showMeetingTimes** wird auf **true**festgelegt, um **findmeetingtimesgallery**anzuzeigen.

## <a name="people-browse-gallery"></a>Benutzer durchsuchen Gallery

   ![People browsegallery-Steuerelement](media/meeting-screen/meeting-browse-gall.png)

* Property **Punkte**<br>
    Wert 
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text), top: 15 } )
    )
    ```

Die Elemente dieser Galerie werden durch Suchergebnisse aus dem Vorgang [Office 365. searchuser](https://docs.microsoft.com/connectors/office365users/#searchuser) aufgefüllt. Der-Vorgang nimmt den Text in `Trim(**TextSearchBox**)` als Suchbegriff und gibt die 15 besten Ergebnisse basierend auf dieser Suche zurück.
  
**Textsearchbox** ist in einer **Trim** -Funktion umschließt, da eine Benutzersuche nach Leerzeichen nicht gültig ist. Der `Office365Users.SearchUser`-Vorgang ist in einer `If(!IsBlank(Trim(TextSearchBox.Text)) ... )`-Funktion umschließt, da das Abrufen von Suchergebnissen vor dem Durchsuchen eines Benutzers eine Leistungs Verschwendung ist.

### <a name="people-browse-gallery-title"></a>Benutzer durchsuchen Galerie Titel

   ![People browsegallery-Titel Steuerelement](media/meeting-screen/meeting-browse-gall-title.png)

* Property **Text**<br>
    Wert: `ThisItem.DisplayName`

    Zeigt den anzeigen amen der Person aus Ihrem Office 365-Profil an.

* Property **OnSelect**<br>
    Wert Eine **Collect** -Anweisung zum Hinzufügen des Benutzers zur Liste der Teilnehmer, eine weitere zum Aktualisieren verfügbarer Besprechungszeiten und verschiedene Variablen Schalter:

    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _selectedUser, ThisItem ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem ); 
            Concurrent(
                Set( _showMeetingTimes, false ),
                UpdateContext( { _loadMeetingTimes: true } ),
                Set( _selectedMeetingTime, Blank() ),
                Set( _selectedRoom, Blank() ),
                Set( _roomListSelected, false ),
                ClearCollect( MeetingTimes, 
                    AddColumns(
                        'Office365'.FindMeetingTimes(
                            {
                                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ),
                                MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                                Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                                End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                                MaxCandidates: 15, 
                                MinimumAttendeePercentage: 1, 
                                IsOrganizerOptional: false, 
                                ActivityDomain: "Work"
                            }
                        ).MeetingTimeSuggestions,
                        "StartTime", MeetingTimeSlot.Start.DateTime, 
                        "EndTime", MeetingTimeSlot.End.DateTime
                    )
                )
            );
            UpdateContext( { _loadingMeetingTimes: false } );
            Set( _showMeetingTimes, true )
        )
    )
    ```

    Auf hoher Ebene wird durch Auswählen dieses Steuer Elements die Person der **mypeople** -Auflistung (der Speicher der APP der Teilnehmer Liste) hinzugefügt, und die verfügbaren Besprechungszeiten werden basierend auf der neuen Benutzer Addition aktualisiert.

    Das Auswählen dieses Steuer Elements ähnelt dem Auswählen des **addicon** -Steuer Elements. der einzige Unterschied besteht darin, dass die `Set(_selectedUser, ThisItem)`-Anweisung und die Ausführungsreihenfolge der Vorgänge. Daher wird diese Erörterung nicht so tief sein. Eine ausführlichere Erläuterung finden Sie im Abschnitt zur [addicon-Steuerung](#add-icon) .

    Wenn Sie dieses Steuerelement auswählen, wird **textsearchbox**zurückgesetzt. Wenn sich die Auswahl nicht in der **mypeople** -Auflistung befindet, gilt Folgendes:
    1. Legt den **_loadMeetingTimes** -Zustand auf **true** und den **_showMeetingTimes** -Status auf **false**fest, gibt die **_selectedMeetingTime** -und **_selectedRoom** -Variablen aus und aktualisiert die **meetingtimes** . Sammlung mit der neuen Addition der **mypeople** -Auflistung. 
    1. Legt den **_loadMeetingTimes** -Zustand auf **false**fest und legt **_showMeetingTimes** auf **true**fest. Wenn die Auswahl bereits in der **mypeople** -Sammlung vorhanden ist, wird nur der Inhalt von **textsearchbox**zurückgesetzt.

## <a name="meeting-people-gallery"></a>Meeting People Gallery

   ![Meetingpeoplegallery-Steuerelement](media/meeting-screen/meeting-people-gall.png)

* Property **Punkte**<br>
    Wert: `MyPeople`

    Die Sammlung " **mypeople** " ist die Auflistung von Personen, die initialisiert oder hinzugefügt werden, indem das Steuerelement " **People browsegallery Title** " ausgewählt wird.

* Property **Flugh**<br>
    Wert Logik, mit der der Katalog auf eine maximale Höhe von 350 vergrößert werden kann:

    ```powerapps-dot
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2, 0 ),
        350
    )
    ```

  
   Die Höhe dieses Katalogs entspricht der Anzahl der Elemente im Katalog und der maximalen Höhe von 350. Die Formel nimmt 76 als Höhe einer einzelnen Zeile von " **meetingpeoplegallery**" an und multipliziert Sie mit der Anzahl der Zeilen. Die **wrapcount** -Eigenschaft ist auf 2 festgelegt, sodass die Anzahl der true-Zeilen `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2, 0)` ist.

* Property **ShowScrollbar**<br>
    Wert: `MeetingPeopleGallery.Height >= 350`

    Wenn die maximale Höhe des Katalogs erreicht wird (350), wird die Scrollleiste angezeigt.

### <a name="meeting-people-gallery-title"></a>Besprechungs Titel für Besprechungs Personen

   ![Meetingpeoplegallery-Titel Steuerelement](media/meeting-screen/meeting-people-gall-title.png)

* Property **OnSelect**<br>
    
    Wert: `Set(_selectedUser, ThisItem)`
    
    Legt die **_selectedUser** -Variable auf das Element fest, das in " **meetingpeoplegallery**" ausgewählt ist.

### <a name="meeting-people-gallery-iconremove"></a>Meeting People Gallery iconremove

   ![Meetingpeoplegallery-iconremove-Steuerelement](media/meeting-screen/meeting-people-gall-delete.png)

* Property **OnSelect**<br>
    Wert Eine **Remove** -Anweisung zum Entfernen des Benutzers aus der Teilnehmerliste, einer **Collect** -Anweisung zum Aktualisieren der verfügbaren Besprechungszeiten und mehrerer variablenschalter:

    ```powerapps-dot
    Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  Auf hoher Ebene entfernt die Auswahl dieses Steuer Elements die Person aus der Liste der Teilnehmer und aktualisiert die verfügbaren Besprechungszeiten basierend auf dem Entfernen dieser Person.

  Nach der ersten Zeile des vorangehenden Codes ist das Auswählen dieses Steuer Elements fast identisch mit der Auswahl des **addicon** -Steuer Elements. Daher wird diese Erörterung nicht so tief sein. Eine ausführlichere Erläuterung finden Sie im [Abschnitt zur addicon-Steuerung](#add-icon).

  In der ersten Codezeile wird das ausgewählte Element aus der **mypeople** -Sammlung entfernt. Der Code dann:
  1. Setzt **textsearchbox**zurück und entfernt dann die Auswahl aus der **mypeople** -Auflistung. 
  1. Legt den **_loadMeetingTimes** -Zustand auf **true** und den **_showMeetingTimes** -Status auf **false**fest, gibt die **_selectedMeetingTime** -und **_selectedRoom** -Variablen aus und aktualisiert die **meetingtimes** . Sammlung mit der neuen Addition der **mypeople** -Auflistung. 
  1. Legt den **_loadMeetingTimes** -Zustand auf **false**fest und legt **_showMeetingTimes** auf **true**fest.

## <a name="meeting-date-picker"></a>Besprechungs Datumsauswahl

   ![Meetingdateselect-Steuerelement](media/meeting-screen/meeting-datepicker.png)

* Property **Display Mode**<br>
    Wert: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    Ein Datum für eine Besprechung kann erst ausgewählt werden, nachdem mindestens ein Teilnehmer zur **mypeople** -Sammlung hinzugefügt wurde.

* Property **OnChange**<br>
    Wert: `Select( MeetingDateSelect )`

    Wenn das ausgewählte Datum geändert wird, wird der Code in der **onselect** -Eigenschaft dieses Steuer Elements ausgeführt.

* Property **OnSelect**<br>
    Wert Eine **Collect** -Anweisung zum Aktualisieren der verfügbaren Besprechungszeiten und mehrerer variablenschalter:
  
    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadingMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  Wenn Sie dieses Steuerelement auswählen, werden die verfügbaren Besprechungszeiten auf hoher Ebene aktualisiert. Dies ist hilfreich, da die verfügbaren Besprechungszeiten, wenn ein Benutzer das Datum ändert, aktualisiert werden müssen, um die Verfügbarkeit der Teilnehmer für diesen Tag widerzuspiegeln.

  Mit Ausnahme der Initial **Collect** -Anweisung ist dies identisch mit der **onselect** -Funktionalität des **addicon** -Steuer Elements. Daher wird diese Erörterung nicht so tief sein. Eine ausführlichere Erläuterung finden Sie im Abschnitt zur [addicon-Steuerung](#add-icon) .

  Wenn Sie dieses Steuerelement auswählen, wird **textsearchbox**zurückgesetzt. Dann: 
  1. Legt den **_loadMeetingTimes** -Zustand auf **true** und den **_showMeetingTimes** -Status auf **false**fest, gibt die **_selectedMeetingTime** -und **_selectedRoom** -Variablen aus und aktualisiert die **meetingtimes** . Sammlung mit der neuen Datumsauswahl. 
  1. Legt den **_loadMeetingTimes** -Zustand auf **false**fest und legt **_showMeetingTimes** auf **true**fest.

## <a name="meeting-duration-drop-down"></a>Dropdown für Besprechungs Dauer

   ![Meetingdateselect-Steuerelement](media/meeting-screen/meeting-timepicker.png)

* Property **Display Mode**<br>
    Wert: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    Eine Dauer für eine Besprechung kann erst ausgewählt werden, nachdem mindestens ein Teilnehmer zur **mypeople** -Sammlung hinzugefügt wurde.

* Property **OnChange**<br>
    Wert: `Select(MeetingDateSelect1)`

    Wenn Sie die ausgewählte Dauer ändern, wird der Code in der **onselect** -Eigenschaft des Steuer Elements " **meetingdateselect** " ausgeführt.

## <a name="find-meeting-times-gallery"></a>Besprechungszeiten-Katalog suchen

   ![Findmeetingtimesgallery-Steuerelement](media/meeting-screen/meeting-time-gall.png)

* Property **Punkte**<br>
    Wert: `MeetingTimes`

    Die Auflistung möglicher Besprechungszeiten, die vom [Office 365. findmeetingtimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) -Vorgang abgerufen werden.

* Property **Barem**<br>
    Wert: `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    Der Katalog ist nur sichtbar, wenn **_showMeetingTimes** auf **true**festgelegt ist, der Benutzer das **lblscheduletab** -Steuerelement ausgewählt hat und mindestens ein Teilnehmer zur Besprechung hinzugefügt wurde.

### <a name="find-meeting-times-gallery-title"></a>Besprechungszeit Galerie Titel suchen

   ![Findmeetingtimesgallery-Titel Steuerelement](media/meeting-screen/meeting-time-gall-title.png)

* Property **Text**<br>
    Wert Eine Konvertierung der Startzeit, die in der Ortszeit des Benutzers angezeigt werden soll:

    ```powerapps-dot
    Text(
        DateAdd(
            DateTimeValue( ThisItem.StartTime ),
            - TimeZoneOffset(), 
            Minutes
        ),
        DateTimeFormat.ShortTime
    )
    ```

  Der abgerufene Wert von **StartTime** liegt im UTC-Format vor. Zum [Konvertieren von UTC in eine lokale Zeit](../functions/function-dateadd-datediff.md#converting-from-utc)wird die **DateAdd** -Funktion angewendet.
  Die [Text-Funktion](../functions/function-text.md#datetime) nimmt ein Datum/eine Uhrzeit als erstes Argument an und formatiert Sie basierend auf dem zweiten Argument. Sie übergeben die lokale Zeit Konvertierung von **thisitem. StartTime**und zeigen Sie als **DateTimeFormat. Shorttime**an.

* Property **OnSelect**<br>
    Wert Mehrere **Collect** -Anweisungen, um Besprechungsräume und deren empfohlene Verfügbarkeit sowie mehrere variablenschalter zu erfassen:

    ```powerapps-dot
    Set( _selectedMeetingTime, ThisItem );
    UpdateContext( { _loadingRooms: true } );
    If( IsEmpty( RoomsLists ),
        ClearCollect( RoomsLists, 'Office365'.GetRoomLists().value) );
    If( CountRows( RoomsLists ) <= 1,
        Set( _noRoomLists, true );
        ClearCollect( AllRooms, 'Office365'.GetRooms().value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                    Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter( 
                        First( RoomTimeSuggestions ).AttendeeAvailability,
                        Availability="Free"
                    ), 
                    "Address", Attendee.EmailAddress.Address
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name 
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" ), 
                "Attendee" 
            )
        ),
        Set( _roomListSelected, false) 
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  Auf hoher Ebene sammelt dieser Codeblock verfügbare Räume für Benutzer, die keine Räume Listen haben, basierend auf dem ausgewählten Datum und der ausgewählten Uhrzeit für die Besprechung. Andernfalls werden einfach die Räume Listen abgerufen.

  Dieser Codeblock auf niedriger Ebene:
  1. Legt **_selectedMeetingTime** auf das ausgewählte Element fest. Hiermit wird festgestellt, welche Räume während dieser Zeit verfügbar sind.
  1. Legt die Ladezustands Variable **_loadingRooms** auf **true**fest und schaltet den Ladezustand ein.
  1. Wenn die **roomslists** -Auflistung leer ist, ruft Sie die Zimmer Listen des Benutzers ab und speichert Sie in der Sammlung " **roomslists** ".
  1. Wenn der Benutzer nicht über eine Raum Liste oder eine Raum Liste verfügt:
      1. Die Variable **noroomlists** ist auf **true**festgelegt, und diese Variable wird verwendet, um die im **roombrowsegallery** -Steuerelement angezeigten Elemente zu bestimmen.
      1. Der `Office365.GetRooms()`-Vorgang wird verwendet, um die ersten 100-Räume in Ihrem Mandanten abzurufen. Diese werden in der **allräume** -Auflistung gespeichert.
      1. Die **_allRoomsConcat** -Variable wird auf eine durch Semikolons getrennte Zeichenfolge der ersten 20 e-Mail-Adressen der Räume in der **allrooms** -Auflistung festgelegt. Dies liegt daran, dass [Office 365. findmeetingtimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) auf die Suche nach den verfügbaren Zeiten von 20 Personen Objekten in einem einzelnen Vorgang beschränkt ist.
      1. Die **roomtimesuggestions** -Auflistung verwendet [Office 365. findmeetingtimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) , um die Verfügbarkeit der ersten 20 Räume in der **allroom** -Auflistung basierend auf den Zeitwerten aus der **_selectedMeetingTime** -Variablen abzurufen. Beachten Sie, dass die `& "Z"` verwendet wird, um den **DateTime** -Wert ordnungsgemäß zu formatieren.
      1. Die **availablerooms** -Sammlung wird erstellt. Dabei handelt es sich einfach um die **roomtimesuggestions** -Auflistung der Teilnehmer-Verfügbarkeit mit zwei zusätzlichen Spalten, die ihr hinzugefügt werden: "Address" und "Name". "Address" ist die e-Mail-Adresse des Raums, und "Name" ist der Name des Raums.
      1. Anschließend wird die **availableroomsoptimal** -Auflistung erstellt. Dies ist nur die **availablerooms** -Sammlung, in der die Spalten "Availability" und "Attendee" entfernt wurden. Dies entspricht den Schemas von **availableroomsoptimal** und **allrooms**. Dies ermöglicht es Ihnen, beide Auflistungen in der **Items** -Eigenschaft von **roombrowsegallery**zu verwenden.
      1. **_roomListSelected** ist auf **false**festgelegt.
  1. Der Ladezustand " **_loadingRooms**" wird auf " **false** " festgelegt, sobald die Ausführung der anderen Person abgeschlossen ist.

## <a name="room-browse-gallery"></a>Katalog mit Raum suchen

   ![Roombrowsegallery-Steuerelement](media/meeting-screen/meeting-rooms-gall.png)

* Property **Punkte**<br>
    Wert Wird logisch auf zwei interne Auflistungen identischer Schemas festgelegt, je nachdem, ob der Benutzer eine Raum Liste ausgewählt hat oder in seinem Mandanten über Räume Listen verfügt:

    ```powerapps-dot
    Search(
        If( _roomListSelected || _noRoomLists, AvailableRoomsOptimal, RoomsLists ),
        Trim(TextMeetingLocation1.Text), 
        "Name", 
        "Address"
    )
    ```

  In dieser Galerie wird die **availableroomsoptimal** -Auflistung angezeigt, wenn **_roomListSelected** oder **_noRoomLists** den Wert **true**aufweist. Andernfalls wird die Sammlung " **roomslists** " angezeigt. Dies ist möglich, da das Schema dieser Auflistungen identisch ist.

* Property **Barem**<br>
    Wert: ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    Der Katalog ist nur sichtbar, wenn die drei vorangehenden Anweisungen als **true**ausgewertet werden.

### <a name="roombrowsegallery-title"></a>Roombrowsegallery-Titel

   ![Roombrowsegallery-Titel Steuerelement](media/meeting-screen/meeting-rooms-gall-title.png)

* Property **OnSelect**<br>
    Wert Ein Satz logisch gebundener **Collect** -und **set** -Anweisungen, die abhängig davon, ob der Benutzerraum Listen oder Räume zeigt, möglicherweise ausgelöst werden.

    ```powerapps-dot
    UpdateContext( { _loadingRooms: true } );
    If( !_roomListSelected && !noRoomLists,
        Set( _roomListSelected, true );
        Set( _selectedRoomList, ThisItem.Name );
        ClearCollect( AllRooms, 'Office365'.GetRoomsInRoomList( ThisItem.Address ).value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter(
                        First( RoomTimeSuggestions ).AttendeeAvailability, 
                        Availability = "Free"
                    ),
                    "Address", Attendee.EmailAddress.Address 
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" )
            ), 
            "Attendee" )
        ),
        Set( _selectedRoom, ThisItem )
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  Welche Aktionen ausgeführt werden, wenn dieses Steuerelement ausgewählt wird, hängt davon ab, ob ein Benutzer gerade einen Satz von Raum Listen oder einen Satz von Räumen anzeigen soll. Wenn es sich um das erste Element handelt, werden bei Auswahl dieses Steuer Elements die Räume, die zum ausgewählten Zeitpunkt verfügbar sind, aus der Liste ausgewählter Räume abgerufen. Wenn das Steuerelement dieses Steuerelement ist, wird die **_selectedRoom** -Variable auf das ausgewählte Element festgelegt. Die vorherige Anweisung ähnelt der **Select** -Anweisung für den [**findmeetingtimesgallery-Titel**](#find-meeting-times-gallery).

  Der vorangehende Codeblock auf niedriger Ebene:
  1. Schaltet den Ladezustand für die Räume ein, indem **_loadingRooms** auf **true**festgelegt wird.
  1. Prüft, ob eine Raum Liste ausgewählt wurde und ob der Mandant über Raum Listen verfügt. Wenn ja:
      1. Legt **_roomListSelected** auf **true** fest und legt **_selectedRoomList** auf das ausgewählte Element fest.
      1. Die **_allRoomsConcat** -Variable wird auf eine durch Semikolons getrennte Zeichenfolge der ersten 20 e-Mail-Adressen der Räume in der **allrooms** -Auflistung festgelegt. Dies liegt daran, dass der [Office 365. findmeetingtimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) -Vorgang auf die Suche nach den verfügbaren Zeiten von 20 Personen Objekten in einem einzelnen Vorgang beschränkt ist.
      1. Die **roomtimesuggestions** -Auflistung verwendet den [Office 365. findmeetingtimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) -Vorgang, um die Verfügbarkeit der ersten 20 Räume in der **allroom** -Auflistung basierend auf den Zeitwerten aus dem **_selectedMeetingTime** -Wert abzurufen. veränder. Beachten Sie, dass `& "Z"` verwendet wird, um den **DateTime** -Wert ordnungsgemäß zu formatieren.
      1. Die **availablerooms** -Sammlung wird erstellt. Dabei handelt es sich einfach um die **roomtimesuggestions** -Auflistung der Teilnehmer-Verfügbarkeit mit zwei zusätzlichen Spalten, die ihr hinzugefügt werden: "Address" und "Name". "Address" ist die e-Mail-Adresse des Raums, und "Name" ist der Name des Raums.
      1. Anschließend wird die **availableroomsoptimal** -Auflistung erstellt. Dies ist nur die **availablerooms** -Sammlung, in der die Spalten "Availability" und "Attendee" entfernt wurden. Dies entspricht den Schemas von **availableroomsoptimal** und **allrooms**. Dies ermöglicht es Ihnen, beide Auflistungen in der **Items** -Eigenschaft von **roombrowsegallery**zu verwenden.
      1. **_roomListSelected** ist auf **false**festgelegt.
  1. Der Ladezustand " **_loadingRooms**" wird auf " **false** " festgelegt, sobald die Ausführung der anderen Person abgeschlossen ist.

## <a name="back-chevron"></a>Zurück Chevron

   ![Roomsbacknav-Steuerelement](media/meeting-screen/meeting-back.png)

* Property **Barem**<br>
    Wert: `_roomListSelected && _showDetails`

    Dieses Steuerelement ist nur sichtbar, wenn eine Raum Liste ausgewählt und die Registerkarte **Zeitplan** ausgewählt ist.

* Property **OnSelect**<br>
    Wert: `Set( _roomListSelected, false )`

    Wenn **_roomListSelected** auf **false**festgelegt ist, wird das Element **roombrowsegallery** geändert, sodass Elemente aus der **Auflistung roomslists** angezeigt werden.

## <a name="send-icon"></a>Symbol "Senden"

   ![Iconsenditem-Steuerelement](media/meeting-screen/meeting-send-icon.png)

* Property **Display Mode**<br>
    Wert Logik zum erzwingen, dass Benutzer bestimmte Besprechungs Details eingeben, bevor das Symbol bearbeitet werden konnte.
    
    ```powerapps-dot
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime ),
        DisplayMode.Edit, DisplayMode.Disabled
    )
    ```
  Das Symbol ist nur wählbar, wenn der Besprechungs Betreff ausgefüllt ist, mindestens ein Teilnehmer für die Besprechung vorhanden und eine Besprechungszeit ausgewählt wurde. Andernfalls ist sie deaktiviert.

* Property **OnSelect**<br>

    Wert Code zum Senden der Besprechungs Einladung an Ihre ausgewählten Teilnehmer und zum Löschen aller Eingabefelder:

    ```powerapps-dot
    Set( _myCalendarName, LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name );
    Set( _myScheduledMeeting, 
        'Office365'.V2CalendarPostItem( _myCalendarName,
            TextMeetingSubject1.Text, 
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.StartTime), -TimeZoneOffset(), Minutes) ),
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.EndTime), -TimeZoneOffset(), Minutes) ),
            {
                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ) & _selectedRoom.Address, 
                Body: TextMeetingMessage1.Text, 
                Location: _selectedRoom.Name, 
                Importance: "Normal", 
                ShowAs: "Busy", 
                ResponseRequested: true
            }
        )
    );
    Concurrent(
        Reset( TextMeetingLocation1 ),
        Reset( TextMeetingSubject1 ),
        Reset( TextMeetingMessage1 ),
        Clear( MyPeople ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoomList, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false )
    )
    ```
  
  Dieser Codeblock auf niedriger Ebene:
  1. Legt **_myCalendarName** auf den Kalender im [Office 365. calendargettables ()](https://docs.microsoft.com/connectors/office365/#get-calendars) -Vorgang mit dem **Display Name** "Calendar" fest.
  1. Plant die Besprechung mit allen Eingabe Werten aus den verschiedenen Auswahlen, die der Benutzer im Bildschirm mithilfe des [Office 365. V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-) -Vorgangs getroffen hat.
  1. Setzt alle Eingabefelder und Variablen zurück, die zum Erstellen der Besprechung verwendet werden.

> [!NOTE]
> Abhängig von Ihrer Region hat der gewünschte Kalender möglicherweise keinen anzeigen Amen "Calendar". Wechseln Sie zu Outlook, um zu sehen, was der Titel Ihres Kalenders ist, und nehmen Sie die entsprechende Änderung in der APP vor.

## <a name="next-steps"></a>Nächste Schritte

* [Weitere Informationen zu diesem Bildschirm](./meeting-screen-overview.md)
* [Weitere Informationen zum Office 365 Outlook-Connector in powerapps](../connections/connection-office365-outlook.md)
* [Weitere Informationen zum Office 365-Benutzer-Connector in powerapps](../connections/connection-office365-users.md)
