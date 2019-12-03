---
title: Referenz für die e-Mail-Bildschirm Vorlage für Canvas-apps | Microsoft-Dokumentation
description: Details zur Funktionsweise der e-Mail-Bildschirm Vorlage für Canvas-apps in powerapps
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
ms.openlocfilehash: 7226433c5e95537346841f2e2f9474ea68e42dda
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675083"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>Referenzinformationen zur e-Mail-Bildschirm Vorlage für Canvas-apps

Verstehen Sie für Canvas-apps in Power apps, wie die einzelnen wichtigen Steuerelemente in der e-Mail-Bildschirm Vorlage zur gesamten Standardfunktionalität des Bildschirms beitragen. Dieser ausführliche Einblick zeigt die Verhaltens Formeln und die Werte anderer Eigenschaften, die bestimmen, wie die Steuerelemente auf Benutzereingaben reagieren. Eine allgemeine Erörterung der Standardfunktionalität dieses Bildschirms finden Sie in der [Übersicht über den e-Mail-Bildschirm](email-screen-overview.md).

In diesem Thema werden einige bedeutende Steuerelemente hervorgehoben und die Ausdrücke oder Formeln erläutert, mit denen verschiedene Eigenschaften (z. b. **Elemente** und **onselect**) dieser Steuerelemente festgelegt werden:

* [Textsuchfeld](#text-search-box)
* [Symbol hinzufügen](#add-icon)
* [Benutzer durchsuchen Gallery](#people-browse-gallery)
* [E-Mail-](#email-people-gallery) Benutzer (+ untergeordnete Steuerelemente)
* [Symbol "Mail"](#mail-icon)

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen [beim Erstellen einer APP in powerapps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Textsuchfeld

   ![Textsearchbox-Steuerelement](media/email-screen/email-search-box.png)

Mehrere andere Steuerelemente auf dem Bildschirm weisen eine Abhängigkeit vom **Textsuchfeld** auf:

* Wenn ein Benutzer mit der Eingabe von Text beginnt, wird **peoplebrowsegallery** angezeigt.
* Wenn ein Benutzer eine gültige e-Mail-Adresse eingibt, wird **addicon** angezeigt.
* Wenn ein Benutzer eine Person in **peoplebrowsegallery**auswählt, wird der Such Inhalt zurückgesetzt.

## <a name="add-icon"></a>Symbol „Hinzufügen“

   ![Addicon-Steuerelement](media/email-screen/email-add-icon.png)

Mit dem Steuerelement **Add Symbol** können App-Benutzer Personen, die nicht in der Organisation vorhanden sind, der Empfängerliste der erstellten e-Mail hinzufügen.

* Eigenschaft: **sichtbar**<br>
    Wert: Logik, mit der das Steuerelement nur angezeigt wird, wenn ein Benutzer eine gültige e-Mail-Adresse in das Suchfeld eingibt:

    ```powerapps-comma
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text; Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  Zeilenweise bedeutet der vorangehende Codeblock, dass das **Add-Symbol** -Steuerelement nur dann sichtbar ist, wenn Folgendes gilt:

    * **Textsearchbox** enthält Text.
    * Der Text in **textsearchbox** ist eine gültige e-Mail-Adresse.
    * Der Text in **textsearchbox** ist in der **mypeople** -Auflistung nicht bereits vorhanden.

* Eigenschaft: **onselect**<br>
    Wert: bei Auswahl dieser Option wird die gültige e-Mail-Adresse der **mypeople** -Sammlung hinzugefügt. Diese Sammlung wird vom Bildschirm als Empfängerliste verwendet:

    ```powerapps-comma
    Collect( MyPeople;
        { 
            DisplayName: TextSearchBox.Text; 
            UserPrincipalName: TextSearchBox.Text; 
            Mail: TextSearchBox.Text
        }
    );;
    Reset( TextSearchBox )
    ```
  
  Dieser Codeblock fügt der **mypeople** -Auflistung eine Zeile hinzu und füllt drei Felder mit dem Text in **textsearchbox**auf. Diese drei Felder lauten " **Display Name**", " **userPrincipalName**" und " **Mail**". Anschließend wird der Inhalt von **textsearchbox**zurückgesetzt.

## <a name="people-browse-gallery"></a>Benutzer durchsuchen Gallery

   ![People browsegallery-Steuerelement](media/email-screen/email-browse-gall.png)

* Eigenschaft: **Elemente**<br>
    Value: die 15 besten Suchergebnisse des Suchtexts, der in das **textsearchbox** -Steuerelement eingegeben wurde:
    
    ```powerapps-comma
    If( !IsBlank( Trim(TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ); top: 15} )
    )
    ```

  Die Elemente dieser Galerie werden durch Suchergebnisse aus dem Vorgang [Office 365. searchuser](https://docs.microsoft.com/connectors/office365users/#searchuser) aufgefüllt. Der-Vorgang nimmt den Text in `Trim(TextSearchBox)` als Suchbegriff und gibt basierend auf dieser Suche die 15 besten Ergebnisse zurück.
  
  **Textsearchbox** ist in einer `Trim()` Funktion umschließt, weil eine Benutzersuche in Leerzeichen ungültig ist. Der `Office365Users.SearchUser` Vorgang wird in eine `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` Funktion umschließt, was bedeutet, dass der Vorgang nur ausgeführt wird, wenn das Suchfeld einen von Benutzern eingegebenen Text enthält. Dadurch wird die Leistung verbessert. 

### <a name="people-browse-gallery-title-control"></a>Personen durchsuchen Galerie Titel-Steuerelement

   ![People browsegallery-Titel Steuerelement](media/email-screen/email-browse-gall-title.png)

* Eigenschaft: **Text**<br>
    Wert: `ThisItem.DisplayName`

  Zeigt den anzeigen amen der Person aus Ihrem Office 365-Profil an.

* Eigenschaft: **onselect**<br>
    Wert: Code zum Hinzufügen des Benutzers zu einer Sammlung auf App-Ebene, und wählen Sie dann den Benutzer aus:

    ```powerapps-comma
    Concurrent(
        Set( _selectedUser; ThisItem );
        Reset( TextSearchBox );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem )
        )
    )
    ```
Wenn Sie dieses Steuerelement auswählen, werden gleichzeitig drei Dinge

   * Legt die **_selectedUser** Variable auf das ausgewählte Element fest.
   * Setzt den Suchbegriff in **textsearchbox**zurück.
   * Fügt das ausgewählte Element der **mypeople** -Auflistung hinzu, einer Auflistung aller ausgewählten Benutzer, die der e-Mail-Bildschirm als Empfängergruppe verwendet.

## <a name="email-people-gallery"></a>Email People Gallery

   ![Emailpeoplegallery-Steuerelement](media/email-screen/email-people-gall.png)

* Eigenschaft: **Elemente**<br>
    Wert: `MyPeople`

  Dabei handelt es sich um die Auflistung von Personen, die initialisiert oder zu hinzugefügt werden, indem das Steuerelement **People browsegallery Title** ausgewählt wird.

* Property: **height**<br>
    Wert: Logik zum Festlegen der Höhe, basierend auf der Anzahl der gegenwärtig im Katalog enthaltenen Elemente:

    ```powerapps-comma
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2; 0 );
        304
    )
    ```

  Die Höhe dieses Katalogs entspricht der Anzahl der Elemente im Katalog mit einer maximalen Höhe von 304.
  
  Es nimmt `TemplateHeight + TemplatePadding * 2` als Gesamthöhe einer einzelnen Zeile von **emailpeoplegallery**an und multipliziert Sie dann mit der Anzahl der Zeilen. Seit `WrapCount = 2`wird die Anzahl der echten Zeilen `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2; 0)`.

* Property: **ShowScrollbar**<br>
    Wert: `EmailPeopleGallery.Height >= 304`
  
  Wenn die Höhe des Katalogs 304 erreicht, ist die Scrollleiste sichtbar.

### <a name="email-people-gallery-title-control"></a>Titel Steuerelement für e-Mail Personen-Katalog

   ![Emailpeoplegallery-Titel Steuerelement](media/email-screen/email-people-gall-text.png)

* Eigenschaft: **onselect**<br>
    Wert: `Set(_selectedUser; ThisItem)`

  Legt die **_selectedUser** Variable auf das in **emailpeoplegallery**ausgewählte Element fest.

### <a name="email-people-gallery-iconremove-control"></a>Email People Gallery iconremove-Steuerelement

   ![Monthdaygallery-Titel Steuerelement](media/email-screen/email-people-gall-delete.png)

* Eigenschaft: **onselect**<br>
    Wert: `Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) )`

  Sucht den Datensatz in der **mypeople** -Auflistung, wobei " **userPrincipalName** " mit dem " **userPrincipalName** " des ausgewählten Elements übereinstimmt, und entfernt diesen Datensatz aus der Sammlung.

## <a name="mail-icon"></a>Symbol "Mail"

* Eigenschaft: **onselect**<br>
    Wert: Logik zum Senden der e-Mail-Nachricht des Benutzers:

    ```powerapps-comma
    Set( _emailRecipientString; Concat( MyPeople; Mail & ";" ) );;
    'Office365'.SendEmail( _emailRecipientString; 
        TextEmailSubject.Text;  
        TextEmailMessage.Text; 
        { Importance:"Normal" }
    );;
    Reset( TextEmailSubject );;
    Reset( TextEmailMessage );;
    Clear( MyPeople )
    ```

  Zum Senden einer e-Mail ist eine durch Semikolons getrennte Zeichenfolge von e-Mail-Adressen erforderlich. Im vorangehenden Code:
  1. Die erste Codezeile übernimmt das Feld " **Mail** " aus allen Zeilen in der Sammlung " **mypeople** ", verkettet Sie in einer einzelnen, durch Semikolons getrennten Zeichenfolge von e-Mail-Adressen und legt die **_emailRecipientString** Variable auf diesen Zeichen folgen Wert fest.

  1. Anschließend wird der [Office 365. SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) -Vorgang verwendet, um die e-Mail an die Empfänger zu senden.
    Der Vorgang verfügt über drei erforderliche Parameter: **to**, **Subject**und **Body**und einen optionalen Parameter--**Wichtigkeit**. Im vorangehenden Code handelt es sichum _emailRecipientString **textemailsubject**. Text, **textemailmessage**. Text (bzw. **Normal**).
  1. Schließlich setzt es die Steuerelemente **textemailsubject** und **textemailmessage** zurück und löscht die Auflistung **mypeople** .

* Eigenschaft: **Display Mode**<br>
    Wert: `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ); DisplayMode.Edit; DisplayMode.Disabled )` für eine e-Mail, die gesendet werden soll, muss die Betreffzeile der e-Mail über Text verfügen, und die Empfänger Auflistung (**mypeople**) darf nicht leer sein.

## <a name="next-steps"></a>Nächste Schritte

* [Weitere Informationen zu diesem Bildschirm](./email-screen-overview.md)
* [Weitere Informationen zum Office 365 Outlook-Connector in powerapps](../connections/connection-office365-outlook.md)
* [Weitere Informationen zum Office 365-Benutzer-Connector in powerapps](../connections/connection-office365-users.md)
