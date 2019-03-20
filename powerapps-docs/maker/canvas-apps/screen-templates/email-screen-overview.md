---
title: E-Mail-Bildschirmvorlage | Microsoft-Dokumentation
description: Verstehen, wie die e-Mail-Bildschirmvorlage für Canvas-apps funktioniert, und erweitern Sie den Bildschirm für Ihre eigenen Anwendungsfälle
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a1aad5ca9e8c7f8b55b1645b04d6c8dc0b9c707b
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459549"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>Übersicht über die e-Mail-Bildschirmvorlage für Canvas-apps

Fügen Sie in einer Canvas-app einen e-Mail-Bildschirm, in dem Benutzer eine e-Mail an ihre Office 365 Outlook-Konto senden kann. Benutzer können Empfänger in ihrer Organisationen suchen und externe e-Mail-Adressen auch hinzufügen. Sie können Image-Attachment-Unterstützung hinzufügen, ändern die Benutzerdaten, die im Katalog suchen angezeigt wird und andere Anpassungen vornehmen.

Sie können auch andere Template-basierten Bildschirme, die unterschiedliche Daten über Office 365, z. B. eines Benutzers anzeigen hinzufügen [Kalender](calendar-screen-overview.md), [Personen](people-screen-overview.md) in einer Organisation und [Verfügbarkeit](meeting-screen-overview.md) von die Benutzer-Benutzer sollten in einer Besprechung eingeladen werden.

In dieser Übersicht erfahren Sie:
> [!div class="checklist"]
> * So verwenden Sie den Standard-e-Mail-Bildschirm.
> * So geändert werden.
> * Wie Sie es in eine app zu integrieren.

Tiefer in die Standardfunktionalität des Bildschirms, finden Sie unter den [-e-Mail-bildschirmreferenz](email-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionen

So fügen Sie einen Bildschirm für die e-Mail-Adresse aus der Vorlage hinzu:

1. [Melden Sie sich bei](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) powerapps an, und klicken Sie dann erstellen Sie eine app oder eine vorhandene app in PowerApps Studio öffnen.

    In diesem Thema wird gezeigt, eine Phone-app, die gleichen Konzepte gelten jedoch für eine Tablet-app.

1. Auf der **Startseite** Menüband auf der Registerkarte **neuer Bildschirm** > **-e-Mail**.

    Standardmäßig sieht der Bildschirm wie folgt aus:

    ![E-Mail-Bildschirm](media/email-screen/email-screen-full.png)

Einige hilfreiche Hinweise:

* Um für Benutzer in Ihrer Organisation zu suchen, starten Sie ihre Namen in das Texteingabefeld unter "To" eingeben.
* Bei der Suche nach Personen werden nur die ersten 15 Ergebnisse zurückgegeben werden.
* Um die e-Mail-Adressen für e-Mail-Empfänger außerhalb Ihrer Organisation hinzufügen möchten, geben Sie die vollständige, gültige e-Mail-Adresse, und wählen Sie das "+"-Symbol, das rechts daneben angezeigt wird.
* Sie fügen Sie als Empfänger mindestens einer Person hinzu, und geben Sie einen Betreff zum Senden einer e-Mail.
* Nachdem Sie die e-Mail-Adresse senden, werden der Inhalt der Betreff und Text als auch die Empfängerliste alle gelöscht.

## <a name="modify-the-screen"></a>Ändern Sie den Bildschirm

Sie können die Standardfunktionen von diesem Bildschirm in eine Reihe gebräuchlicher Verfahren ändern:

* [Hinzufügen von Image-Attachment-Unterstützung](email-screen-overview.md#add-image-attachment-support)
* [Verschiedene Daten für Benutzer anzeigen](email-screen-overview.md#show-different-data-for-people)

Wenn Sie den Bildschirm weiter ändern möchten, verwenden Sie die [-e-Mail-bildschirmreferenz](./email-screen-reference.md) als Leitfaden.

> [!IMPORTANT]
> Die folgenden Schritte wird davon ausgegangen, dass Sie nur eine e-Mail-Bildschirm der App hinzugefügt haben. Wenn Sie mehrere Werte, Steuerelementnamen hinzugefügt haben (z. B. **iconMail1**) endet mit einer unterschiedlichen Anzahl, und Sie müssen die Formeln entsprechend anpassen.

### <a name="add-image-attachment-support"></a>Hinzufügen von Image-Attachment-Unterstützung

Dadurch können Benutzer ein einzelnes Image mit ihrer e-Mail-Adresse als Anlage gesendet.

1. Auf der **einfügen** Registerkarte **Media**, und wählen Sie dann **Bild hinzufügen**.
1. Legen Sie das neuen Steuerelements **Y** Eigenschaft auf den folgenden Ausdruck:

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. Mit der **AddMediaWithImage** Steuerelement eingefügt, legen Sie seine Höhe kleiner als 210 sein.
1. Wählen Sie in der Strukturansicht des Steuerelements **AddMediaWithImage** > **...**   >  **Neu anordnen** > **in den Hintergrund**.
   Dies verhindert, dass das Steuerelement Waren vor der **PeopleBrowseGallery** Steuerelement.
1. Ändern der **Höhe** Eigenschaft **EmailPeopleGallery** auf diese Formel:

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. Legen Sie die **ShowScrollbar** Eigenschaft **EmailPeopleGallery** auf den folgenden Ausdruck:

    ```EmailPeopleGallery1.Height >= 304```
    
    Dadurch wird verhindert, dass die maximale Höhe mithilfe von Push übertragen die **AddMediaWithImage** Steuerelement außerhalb der Seite.
    
1. Ändern der **OnSelect** Eigenschaft der **IconMail** -Steuerelements auf diese Formel:

    ```powerapps-dot
    Set( _emailRecipientString, Concat(MyPeople, Mail & ";") );
    If( IsBlank( UploadedImage1 ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            { Importance: "Normal" }
        ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            {
                Importance: "Normal",
                Attachments: Table(
                    {
                        Name: "Image.jpg", 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );
    Reset( TextEmailSubject1 );
    Reset( TextEmailMessage1 );
    Reset( AddMediaButton1 );
    Clear( MyPeople )
    ```
    
    Diese Formel überprüft, ob eines hochgeladenen Bilds. Wenn keiner vorhanden ist, klicken Sie dann dabei wird derselbe `Office365.SendEmail` Vorgang wie zuvor. Wenn ein Standardimage vorhanden ist, wird sie als Anlage in der Tabelle mit Anlagen hinzugefügt.
    Nach dem Senden der e-Mails, eine zusätzlichen **zurücksetzen** Vorgang erfolgt auf **AddMediaButton** So entfernen Sie das hochgeladene Bild.
> [!NOTE]
> Zum Hinzufügen von mehr als eine Anlage einer e-Mail Datensätze der Tabelle mit Anlagen hinzugefügt.

### <a name="show-different-data-for-people"></a>Verschiedene Daten für Benutzer anzeigen

Dieser Bildschirm wird die [Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) Vorgang, der Benutzer in Ihrer org. Suchen Es bietet zusätzliche Felder für jedes Ereignis, hinausgehen wird die **PeopleBrowseGallery** Steuerelement. Hinzufügen oder Ändern von Feldern in der Galerie ist einfach:

1. In der **PeopleBrowseGallery** steuern, wählen Sie eine Bezeichnung zu ändern (oder fügen Sie einen hinzu, und bewahren Sie sie ausgewählt haben).

1. Mit der **Text** Eigenschaft ausgewählt ist, in der Bearbeitungsleiste, ersetzen Sie den Inhalt mit `ThisItem.`

    IntelliSense zeigt eine Liste der Felder, die Sie auswählen können.

1. Wählen Sie das gewünschte Feld.

    Die **Text** Eigenschaft aktualisiert wird, um `ThisItem.{FieldSelection}`.

## <a name="integrate-the-screen-into-an-app"></a>Integrieren Sie den Bildschirm in eine app

Die e-Mail-Adresse ist eine leistungsfähige Zusammenstellung von Steuerelementen auf seine eigene, aber es am besten in der Regel als Teil einer größeren, stärker ausbauen app führt. Sie können diesen Bildschirm in eine größere app in eine Reihe von Möglichkeiten, einschließlich integrieren [verknüpfen, auf dem Bildschirm Kalender](email-screen-overview.md#linking-to-the-calendar-screen).

### <a name="linking-to-the-calendar-screen"></a>Verknüpfen auf der Kalender-Bildschirm

Befolgen Sie die Schritte im Abschnitt "Ereignis-Teilnehmer anzeigen" der [Kalender der Übersicht über](./calendar-screen-overview.md#show-event-attendees) jedoch im letzten Schritt legen Sie die **navigieren** Funktion, um den e-Mail-Bildschirm zu öffnen. Nachdem Sie diese Schritte ausführen, die **MyPeople** Auflistung aufgefüllt wird, dem Benutzer ermöglicht, eine e-Mail an die Personen senden, die das ausgewählte Ereignis an sind.

> [!NOTE]
> Diese e-Mail senden, wird eine separate e-Mail-Adresse des tatsächlichen Ereignisses in Outlook gesendet.

## <a name="next-steps"></a>Nächste Schritte

* [Die Referenzdokumentation für diesen Bildschirm](./email-screen-reference.md).
* [Erfahren Sie mehr über das Office 365-Benutzer-Connector in PowerApps](../connections/connection-office365-users.md).
* [Finden Sie unter allen verfügbaren Verbindungen in PowerApps](../connections-list.md).