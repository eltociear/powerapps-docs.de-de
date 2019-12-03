---
title: Benutzer-Bildschirm Vorlagen Referenz | Microsoft-Dokumentation
description: Details zur Funktionsweise der Vorlage "Personen Bildschirm" für Canvas-apps in powerapps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ab4b7683d4ea550ebe5704cb7e5580ccbae48deb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674974"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Referenzinformationen zur Benutzer Bildschirm Vorlage für Canvas-apps

Verstehen Sie für Canvas-apps in Power apps, wie die einzelnen wichtigen Steuerelemente in der Vorlage für Personen auf dem Bildschirm zur gesamten Standardfunktionalität des Bildschirms beitragen. Dieser ausführliche Einblick zeigt Verhaltens Formeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine ausführliche Erläuterung der Standardfunktionalität dieses Bildschirms finden Sie in der [Übersicht über](people-screen-overview.md)die Benutzer.

In diesem Thema werden einige bedeutende Steuerelemente hervorgehoben und die Ausdrücke oder Formeln erläutert, mit denen verschiedene Eigenschaften (z. b. **Elemente** und **onselect**) dieser Steuerelemente festgelegt werden:

* [Textsuchfeld](#text-search-box)
* Katalog zum [Durchsuchen von Benutzern](#user-browse-gallery) (+ untergeordnete Steuerelemente)
* [Hinzugefügte Galerie](#people-added-gallery) (+ untergeordnete Steuerelemente)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen [beim Erstellen einer APP in powerapps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Textsuchfeld

![Textsearchbox-Steuerelement](media/people-screen/people-search-box.png)

Einige andere Steuerelemente interagieren oder haben eine Abhängigkeit vom Textfeld für die Text Suche:

* Wenn ein Benutzer mit der Eingabe von Text beginnt, wird **userbrowsegallery** sichtbar.
* Wenn ein Benutzer eine Person innerhalb von **userbrowsegallery**auswählt, wird der Such Inhalt zurückgesetzt.

## <a name="user-browse-gallery"></a>Katalog zum Durchsuchen von Benutzern

![Userbrowsegallery-Steuerelement](media/people-screen/people-browse-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: Logik zum Suchen von Benutzern, wenn der Benutzer mit der Eingabe beginnt:
    
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ), 
                top: 15
            }
        )
    )
    ```
    
Die Elemente dieser Galerie werden durch Suchergebnisse aus dem Vorgang [Office 365. searchuser](https://docs.microsoft.com/connectors/office365users/#searchuser) aufgefüllt. Der-Vorgang nimmt den Text in `Trim(TextSearchBox)` als Suchbegriff und gibt basierend auf dieser Suche die 15 besten Ergebnisse zurück. **Textsearchbox** ist in einer `Trim()` Funktion umschließt, weil eine Benutzersuche in Leerzeichen ungültig ist.

Der `Office365Users.SearchUser` Vorgang wird in eine `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` Funktion umschließt, da Sie den Vorgang nur dann aufzurufen müssen, wenn das Suchfeld einen vom Benutzer eingegebenen Text enthält. Dadurch wird die Leistung verbessert.

### <a name="userbrowsegallery-title-control"></a>Userbrowsegallery-Titel Steuerelement

![Userbrowsegallery-Titel Steuerelement](media/people-screen/people-browse-gall-title.png)

* Eigenschaft: **Text**<br>Wert: `ThisItem.DisplayName`

  Zeigt den anzeigen amen der Person aus Ihrem Office 365-Profil an.

* Eigenschaft: **onselect**<br>
    Wert: Code zum Hinzufügen des Benutzers zu einer Sammlung auf App-Ebene, und wählen Sie dann den Benutzer aus:

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
Wenn Sie dieses Steuerelement auswählen, werden gleichzeitig drei Dinge

   * Legt die **\_selecteduser** -Variable auf das ausgewählte Element fest.
   * Setzt den Suchbegriff in **textsearchbox**zurück.
   * Fügt das ausgewählte Element der **mypeople** -Auflistung hinzu, einer Auflistung aller Personen, die der App-Benutzer ausgewählt hat.

### <a name="userbrowsegallery-profileimage-control"></a>Userbrowsegallery ProfileImage-Steuerelement

![Userbrowsegallery ProfileImage-Steuerelement](media/people-screen/people-browse-gall-image.png)

* Eigenschaft: **Bild**<br>
    Wert: Logik zum Abrufen des Profil Fotos eines Benutzers.

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

Das **Image** -Steuerelement ruft das Image des Benutzers mit dem [Office365Users. userphoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) -Vorgang ab. Vor diesem Vorgang werden jedoch zwei Dinge überprüft:
  
   * Gibt an, ob das ID-Feld leer oder nicht leer ist. Dadurch wird verhindert, dass das **Image** -Steuerelement versucht, ein Benutzer Foto abzurufen, bevor der Katalog mit den Suchergebnissen aufgefüllt wurde.
   * Gibt an, ob der Benutzer ein Foto hat (mit dem [Office365Users. userphotometadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) -Vorgang). Dadurch wird verhindert, dass die `Office365Users.UserPhoto` Suche eine Ausnahme zurückgibt, wenn der Benutzer kein Profilbild hat.

Beachten Sie, dass das **Bild** Steuerelement leer ist, wenn ein Bild nicht abgerufen wird, und stattdessen das **iconuser** -Steuerelement sichtbar ist.

## <a name="people-added-gallery"></a>Von Benutzern hinzugefügte Galerie

![People addecodgallery-Steuerelement](media/people-screen/people-people-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: `MyPeople`

Dabei handelt es sich um die Auflistung von Personen, die initialisiert oder hinzugefügt werden, indem das Steuerelement **userbrowsegallery** ausgewählt wird.

### <a name="peopleaddedgallery-title-control"></a>People addecodgallery-Titel Steuerelement

![People addecodgallery-Titel Steuerelement](media/people-screen/people-people-gall-title.png)

* Eigenschaft: **onselect**<br>
    Wert: `Set( _selectedUser, ThisItem )`

Legt die **_selectedUser** Variable auf das in **emailpeoplegallery**ausgewählte Element fest.

### <a name="peopleaddedgallery-iconremove-control"></a>People addecodgallery-iconremove-Steuerelement

![People addecodgallery-iconremove-Steuerelement](media/people-screen/people-people-gall-delete.png)

* Eigenschaft: **onselect**<br>
    Wert: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

Sucht den Datensatz in der **mypeople** -Auflistung, wobei " **userPrincipalName** " mit dem " **userPrincipalName** " des ausgewählten Elements übereinstimmt, und entfernt diesen Datensatz dann aus der Sammlung.

## <a name="next-steps"></a>Nächste Schritte

* [Weitere Informationen zu diesem Bildschirm](./people-screen-overview.md).
* [Erfahren Sie mehr über den Outlook-Connector von Office 365](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über den Connector für Office 365-Benutzer](../connections/connection-office365-users.md).
