---
title: Personen-Screen-vorlagenreferenz | Microsoft-Dokumentation
description: Erläuterungen zu Details der Funktionsweise von den Personen Bildschirmvorlage für Canvas-apps in PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 09b92a1e2bc87ac6f4e2ec651aa67a845e0f07b1
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540689"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Referenzinformationen zu den Personen Bildschirmvorlage für Canvas-apps

Für Canvas-apps in PowerApps zu verstehen, wie jede bedeutende Kontrolle in der Vorlage Personen-Bildschirm auf die standardmäßige Gesamtfunktionalität des Bildschirms beiträgt. Tieferer Einblick in diese enthält die verhaltensformeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine allgemeine Diskussion über die Standardfunktionalität des Bildschirms, finden Sie unter den [Personen-Übersicht über](people-screen-overview.md).

In diesem Thema werden einige wichtige steuermöglichkeiten und erläutert die Ausdrücke oder Formeln, die die verschiedenen Eigenschaften (z. B. **Elemente** und **OnSelect**) dieser Steuerelemente festgelegt werden:

* [Textsuchfeld](#text-search-box)
* [Benutzer-durchsuchbaren Katalog](#user-browse-gallery) (+ untergeordnete Steuerelemente)
* [Personen hinzugefügt Katalog](#people-added-gallery) (+ untergeordnete Steuerelemente)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Textsuchfeld

![TextSearchBox-Steuerelement](media/people-screen/people-search-box.png)

Einige andere Steuerelemente interagieren oder eine Abhängigkeit für das Textfeld für die Suche:

* Wenn ein Benutzer beginnt, geben einen beliebigen Text ein, **UserBrowseGallery** sichtbar wird.
* Wenn ein Benutzer eine Person in auswählt **UserBrowseGallery**, den Inhalt der Suche werden zurückgesetzt.

## <a name="user-browse-gallery"></a>Katalog durchsuchen-Benutzer

![UserBrowseGallery-Steuerelement](media/people-screen/people-browse-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: Die Logik, um Benutzer zu suchen, wenn der Benutzer mit der Eingabe beginnt:
    
    ```powerapps-comma
    If( !IsBlank( Trim( TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ); 
                top: 15
            }
        )
    )
    ```
    
Die Elemente dieser Katalog vom Suchergebnisse aus aufgefüllt werden die [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) Vorgang. Der Vorgang nimmt den Text in `Trim(TextSearchBox)` als seine Suche Begriff und gibt die ersten 15 Ergebnisse basierend auf, dass die Suche. **TextSearchBox** umschlossen ist eine `Trim()` funktionieren, weil eine Benutzersuche auf Speicherplätzen ungültig ist.

Die `Office365Users.SearchUser` Vorgang innerhalb einer `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` funktionieren, da Sie nur müssen, um den Vorgang aufzurufen, wenn das Suchfeld eingegebenen Text enthält. Dies verbessert die Leistung.

### <a name="userbrowsegallery-title-control"></a>UserBrowseGallery Titel des Steuerelements

![UserBrowseGallery Titel des Steuerelements](media/people-screen/people-browse-gall-title.png)

* Eigenschaft: **Text**<br>Wert: `ThisItem.DisplayName`

  Zeigt den Namen der Person Anzeige aus ihrer Office 365-Profil an.

* Eigenschaft: **OnSelect**<br>
    Wert: Code, um den Benutzer zu einer Sammlung auf app-Ebene hinzuzufügen, und wählen Sie dann den Benutzer:

    ```powerapps-comma
    Concurrent(
        Set( _selectedUser; ThisItem );
        Reset( TextSearchBox );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem )
        )
    )
    ```
Dieses Steuerelement auswählen, führt drei Aufgaben gleichzeitig:

   * Legt die  **\_SelectedUser** -Variable auf das ausgewählte Element.
   * Setzt den gesuchten Begriff in **TextSearchBox**.
   * Fügt das ausgewählte Element auf der **MyPeople** -Auflistung, die eine Auflistung aller Personen der app-Benutzer wurde ausgewählt.

### <a name="userbrowsegallery-profileimage-control"></a>UserBrowseGallery ProfileImage-Steuerelement

![UserBrowseGallery ProfileImage-Steuerelement](media/people-screen/people-browse-gall-image.png)

* Eigenschaft: **Bild**<br>
    Wert: Die Logik zum Abrufen eines Benutzers das Profilfoto.

    ```powerapps-comma
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto;
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

Die **Image** Steuerelement abruft Bild des Benutzers mit der [Office365Users.UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) Vorgang. Allerdings wird geprüft, ob zuvor zwei Dinge:
  
   * Gibt an, ob das ID-Feld leer oder nicht leer ist. Dies verhindert, dass die **Image** Steuerelement versucht, ein benutzerfoto abgerufen werden soll, bis die Galerie mit Suchergebnissen aufgefüllt wurde.
   * Gibt an, ob der Benutzer ein Foto hat (mit der [Office365Users.UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) Vorgang). Dies verhindert, dass die `Office365Users.UserPhoto` Datensuche in eine Ausnahme zurückgegeben, wenn der Benutzer nicht über ein Profilbild verfügt.

Beachten Sie, dass, wenn ein Bild abgerufen wird nicht die **Image** -Steuerelement leer ist und die **IconUser** -Steuerelement sichtbar ist, stattdessen ist.

## <a name="people-added-gallery"></a>Katalog Personen hinzugefügt

![PeopleAddedGallery-Steuerelement](media/people-screen/people-people-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: `MyPeople`

Dies ist die Sammlung von Personen, die dazu hinzugefügt oder initialisiert die **UserBrowseGallery Titel** Steuerelement.

### <a name="peopleaddedgallery-title-control"></a>PeopleAddedGallery Titel des Steuerelements

![PeopleAddedGallery Titel des Steuerelements](media/people-screen/people-people-gall-title.png)

* Eigenschaft: **OnSelect**<br>
    Wert: `Set( _selectedUser; ThisItem )`

Legt die **_selectedUser** -Variable auf das Element im ausgewählten **EmailPeopleGallery**.

### <a name="peopleaddedgallery-iconremove-control"></a>PeopleAddedGallery IconRemove-Steuerelement

![PeopleAddedGallery IconRemove-Steuerelement](media/people-screen/people-people-gall-delete.png)

* Eigenschaft: **OnSelect**<br>
    Wert: `Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) )`

Sucht nach den Datensatz in die **MyPeople** Sammlung, in denen **"userPrincipalName"** entspricht der **"userPrincipalName"** ausgewählte Element, und klicken Sie dann entfernt, die von Aufzeichnen der Auflistung.

## <a name="next-steps"></a>Nächste Schritte

* [Weitere Informationen zu diesem Bildschirm](./people-screen-overview.md).
* [Erfahren Sie mehr über das Office 365 Outlook-Connector](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über das Office 365-Benutzer-Connector](../connections/connection-office365-users.md).
