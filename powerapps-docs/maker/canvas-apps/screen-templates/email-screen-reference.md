---
title: Referenz für die e-Mail-Bildschirmvorlage für Canvas-apps | Microsoft-Dokumentation
description: Verstehen Sie die Details der Funktionsweise der der e-Mail-Bildschirmvorlage für Canvas-apps in PowerApps
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
ms.openlocfilehash: 8f77fe1194ace2f8cb5abeb3f9657cc76aab263a
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61538734"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>Referenzinformationen zu den e-Mail-Bildschirmvorlage für Canvas-apps

Für Canvas-apps in PowerApps zu verstehen, wie jede bedeutende Kontrolle in der Vorlage für e-Mail-Bildschirm auf die standardmäßige Gesamtfunktionalität des Bildschirms beiträgt. Tieferer Einblick in diese stellt die verhaltensformeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine allgemeine Diskussion über die Standardfunktionalität des Bildschirms, finden Sie unter den [-e-Mail-Übersicht über](email-screen-overview.md).

In diesem Thema werden einige wichtige steuermöglichkeiten und erläutert die Ausdrücke oder Formeln, die die verschiedenen Eigenschaften (z. B. **Elemente** und **OnSelect**) dieser Steuerelemente festgelegt werden:

* [Textsuchfeld](#text-search-box)
* [Symbol "hinzufügen"](#add-icon)
* [Personen durchsuchen den Katalog](#people-browse-gallery)
* [Benutzer-e-Mail-Katalog](#email-people-gallery) (+ untergeordnete Steuerelemente)
* [Symbol "Mail"](#mail-icon)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Textsuchfeld

   ![TextSearchBox-Steuerelement](media/email-screen/email-search-box.png)

Mehrere andere Steuerelemente auf dem Bildschirm über eine Abhängigkeit verfügen, auf die **Textsuchfeld** Steuerelement:

* Wenn ein Benutzer beginnt, geben einen beliebigen Text ein, **PeopleBrowseGallery** angezeigt wird.
* Wenn ein Benutzer, eine gültige e-Mail-Adresse eingibt **AddIcon** angezeigt wird.
* Wenn ein Benutzer eine Person in auswählt **PeopleBrowseGallery**, den Inhalt der Suche werden zurückgesetzt.

## <a name="add-icon"></a>Symbol „Hinzufügen“

   ![AddIcon-Steuerelement](media/email-screen/email-add-icon.png)

Die **Symbol zum Hinzufügen von** Steuerelement ermöglicht app-Benutzer, Benutzer hinzufügen, die nicht in ihrer Organisation an die Empfängerliste, der die e-Mail-Adresse, die erstellt vorhanden sind.

* Eigenschaft: **Visible**<br>
    Wert: Die Logik des Steuerelements angezeigt wird, nur, wenn ein Benutzer eine gültige e-Mail-Adresse in das Suchfeld eingibt:

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  Zeile für Zeile, die zuvor angeführten Codeblock wird angegeben, dass die **Symbol zum Hinzufügen von** Steuerelement sichtbar sein wird nur dann, wenn:

    * **TextSearchBox** Text enthält.
    * Der Text im **TextSearchBox** ist eine gültige e-Mail-Adresse.
    * Der Text im **TextSearchBox** nicht bereits vorhanden ist, der **MyPeople** Auflistung.

* Eigenschaft: **OnSelect**<br>
    Wert: Durch Auswahl dieser fügt die gültige e-Mail-Adresse der **MyPeople** Auflistung. Diese Auflistung wird durch den Bildschirm wie der Empfängerliste verwendet:

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Reset( TextSearchBox )
    ```
  
  Dieser Codeblock Fügt eine Zeile in der **MyPeople** Auflistung und füllt drei Felder mit dem Text im **TextSearchBox**. Diese drei Felder sind **"DisplayName"**, **"userPrincipalName"**, und **-e-Mails**. Klicken Sie dann den Inhalt des zurückgesetzt **TextSearchBox**.

## <a name="people-browse-gallery"></a>Personen durchsuchen den Katalog

   ![PeopleBrowseGallery-Steuerelement](media/email-screen/email-browse-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: Die ersten 15 Suchergebnisse des Suchtexts handeln, die in der **TextSearchBox** Steuerelement:
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  Die Elemente dieser Katalog vom Suchergebnisse aus aufgefüllt werden die [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) Vorgang. Der Vorgang nimmt den Text in `Trim(TextSearchBox)` als seine Suche Begriff und gibt die ersten 15 Ergebnisse basierend auf, dass die Suche.
  
  **TextSearchBox** umschlossen ist eine `Trim()` funktionieren, weil eine Benutzersuche auf Speicherplätzen ungültig ist. Die `Office365Users.SearchUser` Vorgang innerhalb einer `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` -Funktion, die bedeutet, dass der Vorgang ausgeführt wird, nur, wenn das Suchfeld eingegebenen Text enthält. Dies verbessert die Leistung. 

### <a name="people-browse-gallery-title-control"></a>Personen durchsuchen Titel bildkatalog-Steuerelement

   ![PeopleBrowseGallery Titel des Steuerelements](media/email-screen/email-browse-gall-title.png)

* Eigenschaft: **Text**<br>
    Wert: `ThisItem.DisplayName`

  Zeigt den Namen der Person Anzeige aus ihrer Office 365-Profil an.

* Eigenschaft: **OnSelect**<br>
    Wert: Code, um den Benutzer zu einer Sammlung auf app-Ebene hinzuzufügen, und wählen Sie dann den Benutzer:

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
Dieses Steuerelement auswählen, führt drei Aufgaben gleichzeitig:

   * Legt die **_selectedUser** -Variable auf das ausgewählte Element.
   * Setzt den gesuchten Begriff in **TextSearchBox**.
   * Fügt das ausgewählte Element auf der **MyPeople** -Auflistung, die eine Auflistung aller ausgewählten Benutzer, die der Bildschirm für die e-Mail-Adresse als eine Gruppe von Empfängern verwendet.

## <a name="email-people-gallery"></a>Benutzer-e-Mail-Katalog

   ![EmailPeopleGallery-Steuerelement](media/email-screen/email-people-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: `MyPeople`

  Dies ist die Sammlung von Personen, die dazu hinzugefügt oder initialisiert die **PeopleBrowseGallery Titel** Steuerelement.

* Eigenschaft: **Höhe**<br>
    Wert: Die Logik für die Höhe, basierend auf der Anzahl der Elemente in der Galerie festgelegt:

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  Die Anzahl der Elemente im Katalog mit einer maximalen Höhe 304 passt die Höhe der dieser Katalog an.
  
  Es dauert `TemplateHeight + TemplatePadding * 2` als die Gesamthöhe des eine einzelne Zeile mit **EmailPeopleGallery**, klicken Sie dann die Anzahl von Zeilen multipliziert. Da `WrapCount = 2`, ist die Anzahl der Zeilen mit "true" `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0)`.

* Eigenschaft: **ShowScrollbar**<br>
    Wert: `EmailPeopleGallery.Height >= 304`
  
  Wenn die Höhe des Katalogs 304 erreicht, ist die Bildlaufleiste sichtbar.

### <a name="email-people-gallery-title-control"></a>E-Mail-Personen-Katalog Titel des Steuerelements

   ![EmailPeopleGallery Titel des Steuerelements](media/email-screen/email-people-gall-text.png)

* Eigenschaft: **OnSelect**<br>
    Wert: `Set(_selectedUser, ThisItem)`

  Legt die **_selectedUser** -Variable auf das Element im ausgewählten **EmailPeopleGallery**.

### <a name="email-people-gallery-iconremove-control"></a>E-Mail-Personen IconRemove Katalogsteuerelement

   ![MonthDayGallery Titel des Steuerelements](media/email-screen/email-people-gall-delete.png)

* Eigenschaft: **OnSelect**<br>
    Wert: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  Sucht nach den Datensatz in der **MyPeople** Sammlung, in denen **"userPrincipalName"** entspricht der **"userPrincipalName"** ausgewählte Element ein, und entfernt, die von Aufzeichnen der Auflistung.

## <a name="mail-icon"></a>Symbol "Mail"

* Eigenschaft: **OnSelect**<br>
    Wert: Die Logik zum Senden von e-Mail des Benutzers:

    ```powerapps-dot
    Set( _emailRecipientString, Concat( MyPeople, Mail & ";" ) );
    'Office365'.SendEmail( _emailRecipientString, 
        TextEmailSubject.Text,  
        TextEmailMessage.Text, 
        { Importance:"Normal" }
    );
    Reset( TextEmailSubject );
    Reset( TextEmailMessage );
    Clear( MyPeople )
    ```

  Senden einer e-Mail-Nachricht ist eine durch Semikolons getrennte Zeichenfolge von e-Mail-Adressen erforderlich. Im vorangehenden Code:
  1. Dauert die erste Zeile des Codes der **-e-Mails** Feld aus allen Zeilen in der **MyPeople** Auflistung verkettet sie in eine einzelne Zeichenfolge von e-Mail-Adressen durch Semikolons getrennt, und legt sie fest der **_ EmailRecipientString** Variablen in dieser Zeichenfolge.

  1. Anschließend wird mithilfe der [Office365.SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) Vorgang, der die e-Mail-Adresse an den Empfänger zu senden.
    Der Vorgang hat drei erforderliche Parameter, **zu**, **Betreff**, und **Text**, und einen optionalen Parameter--**Wichtigkeit**. Im vorangehenden Code werden diese **_emailRecipientString**, **TextEmailSubject**. Text, **TextEmailMessage**. Text, und **Normal**bzw.
  1. Schließlich setzt es die **TextEmailSubject** und **TextEmailMessage** steuert und löscht die **MyPeople** Auflistung.

* Eigenschaft: **DisplayMode**<br>
    Wert: `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )` Für eine e-Mail gesendet werden, die e-Mail-Betreffzeile müssen Text und der Empfänger (**MyPeople**) Auflistung darf nicht leer sein.

## <a name="next-steps"></a>Nächste Schritte

* [Weitere Informationen zu diesem Bildschirm](./email-screen-overview.md)
* [Erfahren Sie mehr über das Office 365 Outlook-Connector in PowerApps](../connections/connection-office365-outlook.md)
* [Erfahren Sie mehr über das Office 365-Benutzer-Connector in PowerApps](../connections/connection-office365-users.md)
