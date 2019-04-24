---
title: Referenz für die Besprechung Bildschirmvorlage für Canvas-apps | Microsoft-Dokumentation
description: Erläuterungen zu Details der Funktionsweise von der Besprechung Bildschirmvorlage für Canvas-apps in PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a7559f84b43d3c0372dea71d49c35461ba9d4e57
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539520"
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>Referenzinformationen zu der Besprechung Bildschirmvorlage für Canvas-apps

Für Canvas-apps in PowerApps zu verstehen, wie jede bedeutende Kontrolle in der Besprechung-Screen-Vorlage, die standardmäßige Gesamtfunktionalität des Bildschirms beiträgt. Tieferer Einblick in diese stellt die verhaltensformeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine allgemeine Diskussion über die Standardfunktionalität des Bildschirms, finden Sie unter den [Meeting-Übersicht über](meeting-screen-overview.md).

In diesem Thema werden einige wichtige steuermöglichkeiten und erläutert die Ausdrücke oder Formeln, die die verschiedenen Eigenschaften (z. B. **Elemente** und **OnSelect**) dieser Steuerelemente festgelegt werden:

* [Laden Sie die Registerkarte (LblInviteTab)](#invite-tab)
* [Registerkarte "Zeitplan" (LblScheduleTab)](#schedule-tab)
* [Textsuchfeld](#text-search-box)
* [Symbol (AddIcon) "hinzufügen"](#add-icon)
* [Personen durchsuchen den Katalog](#people-browse-gallery) (+ untergeordnete Steuerelemente)
* [Besprechung Personen Katalog](#meeting-people-gallery) (+ untergeordnete Steuerelemente)
* [Besprechung Datumsauswahl (MeetingDateSelect)](#meeting-date-picker)
* [Besprechung Dauer Dropdown-Liste (MeetingDurationSelect)](#meeting-duration-drop-down)
* [Besprechungstermine suchen Katalog](#find-meeting-times-gallery) (+ untergeordnete Steuerelemente)
* [Raum Katalog durchsuchen](#room-browse-gallery) (+ untergeordnete Steuerelemente)
* [Back-Chevron (RoomsBackNav)](#back-chevron) (möglicherweise nicht sichtbar, wenn Mandanten Räume enthält keine)
* [Symbol "Senden"](#send-icon)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="invite-tab"></a>Laden Sie die Registerkarte "

   ![LblInviteTab-Steuerelement](media/meeting-screen/meeting-invite-text.png)

* Eigenschaft: **Farbe**<br>
    Wert: `If( _showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** ist eine Variable verwendet, um zu bestimmen, ob die **LblInviteTab** Steuerelement oder das **LblScheduleTab** Steuerelement ausgewählt ist. Wenn der Wert des **_showDetails** ist **"true"**, **LblScheduleTab** ausgewählt ist, wenn der Wert ist **"false"**, **LblInviteTab**  ausgewählt ist. Das bedeutet, dass bei den Wert der **_showDetails** ist **"true"** (auf dieser Registerkarte *ist nicht* ausgewählte), die Farbe der entspricht **LblRecipientCount**. Andernfalls entspricht es den Fill-Wert, der **RectQuickActionBar**.

* Eigenschaft: **OnSelect**<br> 
    Wert: `Set( _showDetails, false )`

    Legt die **_showDetails** Variable **"false"**, das bedeutet, dass den Inhalt der Registerkarte "einladen" sichtbar sind, und die Inhalte von der **Zeitplan** Registerkarte ausgeblendet werden.

## <a name="schedule-tab"></a>Registerkarte "Zeitplan"

   ![LblInviteTab-Steuerelement](media/meeting-screen/meeting-schedule-text.png)

* Eigenschaft: **Farbe**<br>
    Wert: `If( !_showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** ist eine Variable verwendet, um zu bestimmen, ob die **LblInviteTab** Steuerelement oder das **LblScheduleTab** Steuerelement ausgewählt ist. Ist dies "true" **LblScheduleTab** ausgewählt ist; Wenn "false" **LblInviteTab** ist. Dies bedeutet, dass bei **_showDetails** ist "true" (auf dieser Registerkarte *ist* ausgewählte), die Farbe Registerkarte entspricht dem Füllwert **RectQuickActionBar**. Andernfalls entspricht es den Farbwert der **LblRecipientCount**.

* Eigenschaft: **OnSelect**<br>
    Wert: `Set( _showDetails, true )`

    Legt die **_showDetails** Variable **"true"**, d. h. den Inhalt der Registerkarte "Zeitplan" sichtbar sind und den Inhalt der Registerkarte "einladen" ausgeblendet sind.

## <a name="text-search-box"></a>Textsuchfeld

   ![TextSearchBox-Steuerelement](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

Mehrere andere Steuerelemente auf dem Bildschirm haben eine Abhängigkeit von diesem Dienst:

* Wenn ein Benutzer beginnt, geben einen beliebigen Text ein, **PeopleBrowseGallery** sichtbar wird.
* Wenn ein Benutzer eine gültige e-Mail-Adresse eingibt **AddIcon** sichtbar wird.
* Wenn ein Benutzer eine Person in auswählt **PeopleBrowseGallery** die Search-Inhalte werden zurückgesetzt.

## <a name="add-icon"></a>Symbol „Hinzufügen“

   ![AddIcon-Steuerelement](media/email-screen/email-add-icon.png)

Dieses Steuerelement ermöglicht Benutzer hinzufügen, die nicht in ihrer Organisation zur Teilnehmerliste der Besprechung, die erstellt vorhanden sind.

* Eigenschaft: **Visible**<br>
    Wert: Drei logischen überprüft, dass alle ergeben muss **"true"** für das Steuerelement sichtbar sein:

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  Zeile für Zeile diesen Codeblock wird angegeben, dass die **AddIcon** -Steuerelement sichtbar ist nur möglich, wenn:

  * Die **TextSearchBox** Text enthält.
  * Der Text im **TextSearchBox** ist eine gültige e-Mail-Adresse.
  * Der Text im **TextSearchBox** nicht bereits vorhanden ist, der **MyPeople** Auflistung.

* Eigenschaft: **OnSelect**<br> 
    Wert: Ein **sammeln** Anweisung, um den Benutzer an die Teilnehmer hinzufügen aufzulisten, eine andere verfügbare Termine von Besprechungen und mehrere Variablen schaltet aktualisieren:

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

  Auswählen dieses Steuerelements fügt die gültige e-Mail-Adresse (nur sichtbar, wenn in eine gültige e-Mail-Adresse eingegeben wird **TextSearchBox**) auf die **MyPeople** Auflistung (diese Sammlung ist die Teilnehmerliste) und dann aktualisiert den verfügbaren Besprechungstermine mit den neuen Benutzereintrag an.

  Auf niedriger Ebene, diesen Codeblock:
  1. Erfasst die e-Mail-Adresse in der **MyPeople** -Auflistung, sammeln die e-Mail-Adresse in der **"DisplayName"**, **"userPrincipalName"**, und **-e-Mails**  Felder.
  1. Setzt den Inhalt der **TextSearchBox** Steuerelement.
  1. Legt die **_showMeetingTimes** Variable **"false"**. Diese Variable steuert die Sichtbarkeit der **FindMeetingTimesGallery**, zeigt geöffnete Zeiten für die ausgewählten Teilnehmer zu erfüllen.
  1. Legt die **_loadMeetingTimes** auf **"true"**. Mit dieser Variable wird einen Zustand, laden, der Schaltet die Sichtbarkeit der Zustand der Steuerelemente wie Laden **_LblTimesEmptyState** für den Benutzer an, wenn die Daten geladen wird.
  1. Legt **_selectedMeetingTime** zu **Blank()**. **_selectedMeetingTime** ist der ausgewählte Datensatz aus der **FindMeetingTimesGallery** Steuerelement. Es ist hier ausgeblendet, da das Hinzufügen von einem anderen Teilnehmer, die die vorherige Definition von bedeuten könnten **_selectedMeetingTime** ist nicht für diesen Teilnehmer verfügbar sein.
  1. Legt **_selectedRoom** zu **Blank()**. **_selectedRoom** ist die ausgewählte Platz **RoomBrowseGallery**. Die Verfügbarkeit der Platz hängen vom Wert der **_selectedMeetingTime**. Mit diesem Wert ausgeblendet die **_selectedRoom** Wert ist nicht mehr gültig ist, damit es ausgeblendet werden muss.
  1. Legt **_roomListSelected** zu **"false"**. Diese Zeile möglicherweise nicht für alle Benutzer gilt. In Office, gruppieren Sie Ihre Räume von anderen "Raumlisten." Wenn Sie Raumlisten verfügen, berücksichtigt dieser Bildschirm, sodass Sie Sie zuerst auf Raumliste bevor Sie Sie ein Zimmer aus in dieser Liste auswählen. Der Wert des **_roomListSelected** wird bestimmt, ob ein Benutzer (in einem Mandanten mit nur Raumlisten) werden Räume in Raumliste oder den Satz von Raumlisten angezeigt werden. Es wird festgelegt, um **"false"** Benutzer zwingen, eine neue Raumliste erneut auswählen.
  1. Verwendet die [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) Vorgang, um zu bestimmen, und erfassen die verfügbaren Besprechungstermine für Teilnehmer. Dieser Vorgang wird übergeben:
      * Die **"userPrincipalName"** der einzelnen ausgewählten Benutzer in der *RequiredAttendees* Parameter.
      * **MeetingDurationSelect**. Selected.Minutes in die *MeetingDuration* Parameter.
      * MeetingDateSelect.SelectedDate + 8 Stunden in der *starten* Parameter. Acht Stunden wird hinzugefügt, da standardmäßig die vollständige(s) Datum/Zeit für das Kalender-Steuerelement 12:00 Uhr des ausgewählten Datums ist. Wahrscheinlich möchten Sie Verfügbarkeit innerhalb der normalen Geschäftszeiten abzurufen. Eine Startzeit für die normale Arbeit wäre 8:00 Uhr.
      * **MeetingDateSelect**. "SelectedDate" + 10 Stunden in der *End* Parameter. 17 Stunden wird hinzugefügt, da 12:00 Uhr und 17 = 17:00 Uhr. Eine normale Arbeit Endzeit wäre 17:00 Uhr.
      * *15* in die *MaxCandidates* Parameter. Dies bedeutet, dass der Vorgang nur die ersten 15 verfügbaren Zeiten für das ausgewählte Datum zurückgibt. Dies ist sinnvoll, da nur 16 30-Minuten-Blöcke in einen Arbeitstag von 8 Stunden vorhanden sind und eine 30-minütigen Besprechung ist mindestens eine kann auf diesem Bildschirm festgelegt.
      * *1* in die *MinimumAttendeePercentage* Parameter. Im Wesentlichen wird der Zeitpunkt, wenn keine Teilnehmer verfügbar sind, abgerufen.
      * **"false"** in die *IsOrganizerOptional* Parameter. Der app-Benutzer ist kein optionale Teilnehmer dieser Besprechung.
      * "Work" in der *ActivityDomain* Parameter. Dies bedeutet, dass Sie die Zeiten, die abgerufen werden nur in eine normale Arbeitszeit Zeitraum.
  1. Die **ClearCollect** Funktion fügt außerdem zwei Spalten: "StartTime" und "EndTime". Dies vereinfacht die zurückgegebenen Daten. 
  Das Feld mit den verfügbaren Anfangs- und Endzeiten der **MeetingTimeSlot** Feld. Dieses Feld ist, einen Datensatz mit den Beginn und Ende-Datensätze, die wiederum selbst enthalten die **"DateTime"** und **TimeZone** Werte von ihren jeweiligen Vorschlag. Hinzufügen von nicht versucht wird, um diese Schachtelung von Datensätzen abzurufen, die Spalten "StartTime" und "EndTime" aus, die **MeetingTimes** Auflistung bietet die **starten > "DateTime"** und **End > "DateTime"** Werte auf die Oberfläche des der Auflistung.
  1. Wenn diese Funktionen alle abgeschlossen haben, die **_loadingMeetingTimes** auf festgelegt ist **"false"**, entfernen den Zustand beim Laden und **_showMeetingTimes** nastaven NA hodnotu **"true"** mit **FindMeetingTimesGallery**.

## <a name="people-browse-gallery"></a>Personen durchsuchen den Katalog

   ![PeopleBrowseGallery-Steuerelement](media/meeting-screen/meeting-browse-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: 
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text), top: 15 } )
    )
    ```

Die Elemente dieser Katalog vom Suchergebnisse aus aufgefüllt werden die [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) Vorgang. Der Vorgang nimmt den Text in `Trim(**TextSearchBox**)` als seine Suche Begriff und gibt die ersten 15 Ergebnisse basierend auf, dass die Suche.
  
**TextSearchBox** umschlossen ist eine **Trim** funktionieren, da eine Benutzersuche auf Speicherplätzen ungültig ist. Die `Office365Users.SearchUser` Vorgang innerhalb einer `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` funktionieren, da das Abrufen von Suchergebnissen, bevor ein Benutzer durchsucht hat ein Abfall der Leistung ist.

### <a name="people-browse-gallery-title"></a>Katalog-Titel für Personen durchsuchen

   ![PeopleBrowseGallery Titel des Steuerelements](media/meeting-screen/meeting-browse-gall-title.png)

* Eigenschaft: **Text**<br>
    Wert: `ThisItem.DisplayName`

    Zeigt den Namen der Person Anzeige aus ihrer Office 365-Profil an.

* Eigenschaft: **OnSelect**<br>
    Wert: Ein **sammeln** Anweisung, um den Benutzer an die Teilnehmer hinzufügen aufzulisten, eine andere verfügbare Termine von Besprechungen und mehrere Variablen schaltet aktualisieren:

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

    Auf einer hohen Ebene auswählen dieses Steuerelements die Person sind, fügt die **MyPeople** Sammlung (die app Speicher von der Teilnehmerliste), und aktualisiert den verfügbaren Besprechungstermine basierend auf den neuen Benutzer hinzufügen.

    Auswählen dieses Steuerelements ist sehr ähnlich ist, auf die Auswahl der **AddIcon** Steuerelement, das einzige besteht darin, dass die `Set(_selectedUser, ThisItem)` -Anweisung und die Ausführungsreihenfolge der Vorgänge. Daher nicht hier so tief. Lesen Sie eine umfassendere Erläuterung, über die [AddIcon-Steuerelement](#add-icon) Abschnitt.

    Setzt auswählen dieses Steuerelements **TextSearchBox**. Klicken Sie dann, wenn die Auswahl nicht in der **MyPeople** Auflistung, die das Steuerelement:
    1. Legt die **_loadMeetingTimes** Zustand **"true"** und **_showMeetingTimes** Zustand **"false"**, Leerzeichen die **_ SelectedMeetingTime** und **_selectedRoom** Variablen und aktualisiert die **MeetingTimes** Sammlung mit die neue Erweiterung von der **MyPeople** Auflistung. 
    1. Legt diese fest der **_loadMeetingTimes** Zustand **"false"**, und legt **_showMeetingTimes** zu **"true"**. Wenn die Auswahl bereits in der **MyPeople** Sammlung wird nur der Inhalt des zurückgesetzt **TextSearchBox**.

## <a name="meeting-people-gallery"></a>Meeting-Personen-Katalog

   ![MeetingPeopleGallery-Steuerelement](media/meeting-screen/meeting-people-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: `MyPeople`

    Die **MyPeople** -Auflistung enthält die Leute dazu hinzugefügt oder initialisiert die **PeopleBrowseGallery Titel** Steuerelement.

* Eigenschaft: **Höhe**<br>
    Wert: Die Logik zum Katalog aus, um eine maximale Höhe von 350 erreichen können:

    ```powerapps-dot
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2, 0 ),
        350
    )
    ```

  
   Die Anzahl der Elemente im Katalog auf die maximale Höhe von 350 passt die Höhe der dieser Katalog an. Die Formel akzeptiert 76 als die Höhe einer einzelnen Zeile des **MeetingPeopleGallery**, klicken Sie dann die Anzahl von Zeilen multipliziert. Die **WrapCount** -Eigenschaft ist auf 2 festgelegt, sodass die Anzahl der Zeilen mit "true" ist `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2, 0)`.

* Eigenschaft: **ShowScrollbar**<br>
    Wert: `MeetingPeopleGallery.Height >= 350`

    Wenn die maximale Höhe des Katalogs (350) erreicht wird, ist die Bildlaufleiste sichtbar.

### <a name="meeting-people-gallery-title"></a>Besprechung Personen Katalog Titel

   ![MeetingPeopleGallery Titel des Steuerelements](media/meeting-screen/meeting-people-gall-title.png)

* Eigenschaft: **OnSelect**<br>
    
    Wert: `Set(_selectedUser, ThisItem)`
    
    Legt die **_selectedUser** -Variable auf das Element im ausgewählten **MeetingPeopleGallery**.

### <a name="meeting-people-gallery-iconremove"></a>Besprechung Personen Katalog iconRemove

   ![MeetingPeopleGallery IconRemove-Steuerelement](media/meeting-screen/meeting-people-gall-delete.png)

* Eigenschaft: **OnSelect**<br>
    Wert: Ein **entfernen** Anweisung, um den Benutzer aus der Teilnehmerliste Entfernen einer **sammeln** Anweisung, um die verfügbaren Termine von Besprechungen und mehrere Variablen schaltet aktualisieren:

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

  Im Allgemeinen entfernt die Person, die aus der Teilnehmerliste und aktualisiert den verfügbaren Besprechungstermine basierend auf das Entfernen dieser Person auswählen dieses Steuerelements.

  Nach der ersten Zeile des obigen Codes werden soll, Auswählen dieses Steuerelements ist fast identisch mit wählen die **AddIcon** Steuerelement. Daher wird hier nicht so tief sein. Eine umfassendere Erläuterung, lesen die [AddIcon-Steuerelement Abschnitt](#add-icon).

  In der ersten Zeile des Codes, das ausgewählte Element entfernt wird, aus der **MyPeople** Auflistung. Klicken Sie dann den Code:
  1. Setzt **TextSearchBox**, und klicken Sie dann entfernt die Auswahl aus den **MyPeople** Auflistung. 
  1. Legt die **_loadMeetingTimes** Zustand **"true"** und **_showMeetingTimes** Zustand **"false"**, Leerzeichen die **_ SelectedMeetingTime** und **_selectedRoom** Variablen und aktualisiert die **MeetingTimes** Sammlung mit die neue Erweiterung von der **MyPeople** Auflistung. 
  1. Legt diese fest der **_loadMeetingTimes** Zustand **"false"**, und legt **_showMeetingTimes** zu **"true"**.

## <a name="meeting-date-picker"></a>Besprechung Datumsauswahl

   ![MeetingDateSelect-Steuerelement](media/meeting-screen/meeting-datepicker.png)

* Eigenschaft: **DisplayMode**<br>
    Wert: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    Ein Datum für eine Besprechung kann nicht ausgewählt werden, bis mindestens ein Teilnehmer hinzugefügt wurde die **MyPeople** Auflistung.

* Eigenschaft: **OnChange**<br>
    Wert: `Select( MeetingDateSelect )`

    Ändern das ausgewählte Datum löst den Code in die **OnSelect** -Eigenschaft dieses Steuerelements ausgeführt.

* Eigenschaft: **OnSelect**<br>
    Wert: Ein **sammeln** Anweisung, um die verfügbaren Termine von Besprechungen und mehrere Variablen schaltet aktualisieren:
  
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

  Beim Auswählen dieses Steuerelements auf einer hohen Ebene aktualisiert die verfügbaren Besprechungstermine. Es ist hilfreich, da es sich bei, wenn ein Benutzer das Datum ändert, die verfügbaren Besprechungstermine aktualisiert, sodass die Teilnehmer Verfügbarkeit für diesen Tag entsprechen müssen.

  Mit Ausnahme der ersten **sammeln** -Anweisung, dies ist identisch mit der **OnSelect** Funktionalität der **AddIcon** Steuerelement. Daher wird hier nicht so tief sein. Lesen Sie eine umfassendere Erläuterung, über die [AddIcon-Steuerelement](#add-icon) Abschnitt.

  Setzt auswählen dieses Steuerelements **TextSearchBox**. Klicken Sie dann diese: 
  1. Legt die **_loadMeetingTimes** Zustand **"true"** und **_showMeetingTimes** Zustand **"false"**, Leerzeichen die **_ SelectedMeetingTime** und **_selectedRoom** Variablen und aktualisiert die **MeetingTimes** Auflistung mit der Auswahl des neuen Datums. 
  1. Legt diese fest der **_loadMeetingTimes** Zustand **"false"**, und legt **_showMeetingTimes** zu **"true"**.

## <a name="meeting-duration-drop-down"></a>Besprechungsdauer Dropdown-Liste

   ![MeetingDateSelect-Steuerelement](media/meeting-screen/meeting-timepicker.png)

* Eigenschaft: **DisplayMode**<br>
    Wert: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    Eine Dauer für eine Besprechung kann nicht ausgewählt werden, bis mindestens ein Teilnehmer hinzugefügt wurde die **MyPeople** Auflistung.

* Eigenschaft: **OnChange**<br>
    Wert: `Select(MeetingDateSelect1)`

    Ändern den ausgewählten Zeitraum wird ausgelöst, den Code in die **OnSelect** Eigenschaft der **MeetingDateSelect** Steuerelement ausgeführt.

## <a name="find-meeting-times-gallery"></a>Besprechungstermine suchen Katalog

   ![FindMeetingTimesGallery-Steuerelement](media/meeting-screen/meeting-time-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: `MeetingTimes`

    Die Auflistung von möglichen Besprechungstermine abgerufen wird, aus der [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) Vorgang.

* Eigenschaft: **Visible**<br>
    Wert: `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    Der Katalog sichtbar ist nur, wenn **_showMeetingTimes** nastaven NA hodnotu **"true"**, der Benutzer ausgewählt hat die **LblScheduleTab** -Steuerelement, und es ist mindestens ein Teilnehmer, die hinzugefügt der erreicht.

### <a name="find-meeting-times-gallery-title"></a>Besprechungstermine suchen Katalog Titel

   ![FindMeetingTimesGallery Titel des Steuerelements](media/meeting-screen/meeting-time-gall-title.png)

* Eigenschaft: **Text**<br>
    Wert: Eine Konvertierung der Startzeit, die in Ortszeit des Benutzers angezeigt werden:

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

  Der abgerufene Wert von **"StartTime"** wird im UTC-Format. Um [konvertieren aus UTC in die Ortszeit](../functions/function-dateadd-datediff.md#converting-from-utc), **DateAdd** -Funktion angewendet wird.
  Die [Funktion "Text"](../functions/function-text.md#datetime) einen Datum/Uhrzeit als erstes Argument, und Formate, die sie basierend auf dem zweiten Argument akzeptiert. Sie übergeben die Ortszeit Konvertierung **ThisItem.StartTime**, und zeigen Sie sie als **DateTimeFormat.ShortTime**.

* Eigenschaft: **OnSelect**<br>
    Wert: Mehrere **sammeln** Anweisungen zum Sammeln von Besprechungsräumen und ihre vorgeschlagenen Verfügbarkeit als auch mehrere Variablen schaltet:

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

  Auf einer hohen Ebene diesen Codeblock Überwachungsdaten verfügbaren Räume für Benutzer, die nicht den Räumen Listen, basierend auf dem ausgewählten Datum/Uhrzeit für die Besprechung. Andernfalls ruft einfach die Räume Listen ab.

  Auf niedriger Ebene, diesen Codeblock:
  1. Legt **_selectedMeetingTime** für das ausgewählte Element. Dies wird zum Ermitteln, welche Räume während dieser Zeit verfügbar sind.
  1. Legt das Laden Statusvariable **_loadingRooms** zu **"true"**, Aktivieren der geladenen Status.
  1. Wenn die **RoomsLists** Auflistung ist leer, es den Mandanten des Benutzers Räume werden abgerufen, und speichert sie in der **RoomsLists** Auflistung.
  1. Wenn der Benutzer keine Raumliste oder eine Raumliste verfügt:
      1. Die **NoRoomLists** Variable nastaven NA hodnotu **"true"**, und diese Variable wird verwendet, um zu bestimmen, die in der angezeigten Elemente der **RoomBrowseGallery** Steuerelement.
      1. Die `Office365.GetRooms()` Vorgang wird verwendet, um die ersten 100 Räume in ihrem Mandanten abrufen. Diese befinden sich in der **AllRooms** Auflistung.
      1. Die **_allRoomsConcat** Variable wird festgelegt, um die ersten 20 e-Mail-Adressen der Räume in eine durch Semikolons getrennte Zeichenfolge der **AllRooms** Auflistung. Grund hierfür ist die [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) ist auf der Suche nach den verfügbaren Zeiten von 20 Person-Objekten in einem einzigen Vorgang.
      1. Die **RoomTimeSuggestions** Auflistung verwendet die [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) zum Abrufen der Verfügbarkeit von der ersten 20 Räume in die **AllRooms** anhand für den Time-Werten aus der **_selectedMeetingTime** Variable. Beachten Sie, dass die `& "Z"` wird verwendet, um ordnungsgemäß zu formatieren der **"DateTime"** Wert.
      1. Die **AvailableRooms** Sammlung wird erstellt. Ist dies einfach der **RoomTimeSuggestions** Auflistung der Teilnehmer-Verfügbarkeit mit zwei zusätzliche Spalten hinzugefügt: "Address" und "Name". "Address" ist die e-Mail-Adresse des Raums, und "Name" ist der Name des Raums.
      1. Anschließend wird die **AvailableRoomsOptimal** Sammlung wird erstellt. Dies ist die **AvailableRooms** Auflistung mit den Spalten "Verfügbarkeit" und "Teilnehmer" entfernt. Dies entspricht der Schemas von **AvailableRoomsOptimal** und **AllRooms**. Dies ermöglicht Ihnen die Verwendung der beiden Auflistungen in der **Elemente** Eigenschaft der **RoomBrowseGallery**.
      1. **_roomListSelected** nastaven NA hodnotu **"false"**.
  1. Der Ladezustand **_loadingRooms**, nastaven NA hodnotu **"false"** sobald alles beendet wurde.

## <a name="room-browse-gallery"></a>Raum durchsuchbaren Katalog

   ![RoomBrowseGallery-Steuerelement](media/meeting-screen/meeting-rooms-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: Legen Sie logisch identische Schemas, je nachdem, ob der Benutzer Raumliste ausgewählt hat oder Räume Listen in ihrem Mandanten hat zwei internen Auflistungen:

    ```powerapps-dot
    Search(
        If( _roomListSelected || _noRoomLists, AvailableRoomsOptimal, RoomsLists ),
        Trim(TextMeetingLocation1.Text), 
        "Name", 
        "Address"
    )
    ```

  Dieser Katalog zeigt die **AvailableRoomsOptimal** Auflistung Wenn **_roomListSelected** oder **_noRoomLists** ist **"true"**. Andernfalls zeigt er die **RoomsLists** Auflistung. Dies kann erfolgen, da das Schema dieser Auflistungen sind identisch.

* Eigenschaft: **Visible**<br>
    Wert: ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    Der Katalog ist nur sichtbar, wenn die drei vorherigen Anweisungen ausgewertet **"true"**.

### <a name="roombrowsegallery-title"></a>RoomBrowseGallery Titel

   ![RoomBrowseGallery Titel des Steuerelements](media/meeting-screen/meeting-rooms-gall-title.png)

* Eigenschaft: **OnSelect**<br>
    Wert: Eine Reihe von logisch gebundenen **sammeln** und **festgelegt** Anweisungen, die möglicherweise oder nicht ausgelöst werden können, je nachdem, ob der Benutzer Raumlisten oder Teamräume angezeigt wird:

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

  Die Aktionen, die auftreten, wenn dieses Steuerelement ausgewählt ist, hängen davon ab, ob ein Benutzer eine Gruppe von Raumlisten oder einen Satz von Räumen derzeit angezeigt wird. Ruft ab der Räume, die zum ausgewählten Zeitpunkt in der Liste ausgewählten Platz verfügbar sind, ist dies die ehemalige, wählen Sie dann auf dieses Steuerelement. Wenn sie die zweite ist, legt auswählen dieses Steuerelements die **_selectedRoom** Variable für das ausgewählte Element. Die vorhergehende Anweisung ähnelt stark der **wählen** -Anweisung für [ **FindMeetingTimesGallery Titel**](#find-meeting-times-gallery).

  Auf niedriger Ebene, der zuvor angeführten Codeblock:
  1. Aktiviert die geladenen Status für den Räumen durch Festlegen von **_loadingRooms** zu **"true"**.
  1. Überprüft, um zu ermitteln, ob eine Raumliste ausgewählt wurde und wenn der Mandant besitzt aufgeführt. Wenn dies der Fall ist:
      1. Legt fest **_roomListSelected** zu **"true"** und legt **_selectedRoomList** für das ausgewählte Element.
      1. Die **_allRoomsConcat** Variable wird festgelegt, um die ersten 20 e-Mail-Adressen der Räume in eine durch Semikolons getrennte Zeichenfolge der **AllRooms** Auflistung. Grund hierfür ist die [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) Vorgang bis zur Suche nach den verfügbaren Zeiten von 20 Person-Objekten in einem einzigen Vorgang beschränkt ist.
      1. Die **RoomTimeSuggestions** Auflistung verwendet die [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) Vorgang zum Abrufen von der Verfügbarkeit von der ersten 20 Räume in die **AllRooms** Sammlung basierend auf den Time-Werten aus der **_selectedMeetingTime** Variable. Beachten Sie, dass `& "Z"` wird verwendet, um ordnungsgemäß zu formatieren der **"DateTime"** Wert.
      1. Die **AvailableRooms** Sammlung wird erstellt. Ist dies einfach der **RoomTimeSuggestions** Auflistung der Teilnehmer-Verfügbarkeit mit zwei zusätzliche Spalten hinzugefügt: "Address" und "Name". "Address" ist die e-Mail-Adresse des Raums, und "Name" ist der Name des Raums.
      1. Anschließend wird die **AvailableRoomsOptimal** Sammlung wird erstellt. Dies ist die **AvailableRooms** Auflistung mit den Spalten "Verfügbarkeit" und "Teilnehmer" entfernt. Dies entspricht der Schemas von **AvailableRoomsOptimal** und **AllRooms**. Dies ermöglicht Ihnen die Verwendung der beiden Auflistungen in der **Elemente** Eigenschaft **RoomBrowseGallery**.
      1. **_roomListSelected** nastaven NA hodnotu **"false"**.
  1. Der Ladezustand **_loadingRooms**, nastaven NA hodnotu **"false"** sobald alles beendet wurde.

## <a name="back-chevron"></a>Chevron sichern

   ![RoomsBackNav-Steuerelement](media/meeting-screen/meeting-back.png)

* Eigenschaft: **Visible**<br>
    Wert: `_roomListSelected && _showDetails`

    Dieses Steuerelement ist nur sichtbar, wenn beide Raumliste ausgewählt wurde und die **Zeitplan** Registerkarte ausgewählt ist.

* Eigenschaft: **OnSelect**<br>
    Wert: `Set( _roomListSelected, false )`

    Wenn **_roomListSelected** nastaven NA hodnotu **"false"**, ändert der **RoomBrowseGallery** Steuerelement zum Anzeigen von Elementen aus der **RoomsLists** Auflistung.

## <a name="send-icon"></a>Symbol "Senden"

   ![IconSendItem-Steuerelement](media/meeting-screen/meeting-send-icon.png)

* Eigenschaft: **DisplayMode**<br>
    Wert: Die Logik zum erzwingen, dass Benutzer bestimmte Meeting-Details eingeben, bevor Sie das Symbol bearbeitet werden kann.
    
    ```powerapps-dot
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime ),
        DisplayMode.Edit, DisplayMode.Disabled
    )
    ```
  Das Symbol ist auswählbar, nur dann, wenn dem Thema der Besprechung ausgefüllt wird, mindestens ein Teilnehmer der Besprechung ist und Zeitpunkt ausgewählt wurde. Andernfalls wird es deaktiviert.

* Eigenschaft: **OnSelect**<br>

    Wert: Wenn Sie die Besprechung-Einladung an Ihre ausgewählten Teilnehmer senden, und löschen alle Eingabefelder Code:

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
  
  Auf niedriger Ebene, diesen Codeblock:
  1. Legt **_myCalendarName** auf den Kalender in der [Office365.CalendarGetTables()](https://docs.microsoft.com/connectors/office365/#get-calendars) Vorgang mit einem **"DisplayName"** von "Kalender".
  1. Zeitpläne die Besprechung mit der Eingabe Werte aus der Auswahl der verschiedenen Benutzer vorgenommen werden, während der Bildschirm mit der [Office365.V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-) Vorgang.
  1. Setzt alle Felder und Variablen, die zum Erstellen der Besprechung verwendet.

> [!NOTE]
> Je nach Region die von Ihnen gewünschten Kalender Anzeigenamen "Kalender". möglicherweise nicht Wechseln Sie zu Outlook finden Sie unter der Titel des Kalenders, und nehmen Sie die entsprechende Änderung in der app.

## <a name="next-steps"></a>Nächste Schritte

* [Weitere Informationen zu diesem Bildschirm](./meeting-screen-overview.md)
* [Erfahren Sie mehr über das Office 365 Outlook-Connector in PowerApps](../connections/connection-office365-outlook.md)
* [Erfahren Sie mehr über das Office 365-Benutzer-Connector in PowerApps](../connections/connection-office365-users.md)
