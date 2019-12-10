---
title: E-Mail-Bildschirm Vorlage | Microsoft-Dokumentation
description: Erfahren Sie, wie die e-Mail-Bildschirm Vorlage für Canvas-apps funktioniert, und erweitern Sie den Bildschirm für Ihre eigenen Anwendungsfälle.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 861d343e653a78af685a1e0cb82deb5b2ad59591
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732568"
ms.PowerAppsDecimalTransform: true
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>Übersicht über die e-Mail-Bildschirm Vorlage für Canvas-apps

Fügen Sie in einer Canvas-APP einen e-Mail-Bildschirm hinzu, mit dem Benutzer eine e-Mail von Ihrem Office 365 Outlook-Konto senden können Benutzer können in ihren Organisationen nach Empfängern suchen und auch externe e-Mail-Adressen hinzufügen. Sie können Unterstützung für Bild Anlagen hinzufügen, die Benutzerdaten ändern, die in der Such Galerie angezeigt werden, und andere Anpassungen vornehmen.

Sie können auch andere vorlagenbasierte Bildschirme hinzufügen, die unterschiedliche Daten aus Office 365 anzeigen, wie z. b. den [Kalender](calendar-screen-overview.md)eines Benutzers, [Personen](people-screen-overview.md) in einer Organisation und die [Verfügbarkeit](meeting-screen-overview.md) der Personen, die Benutzer möglicherweise zu einer Besprechung einladen möchten.

Diese Übersicht vermittelt Ihnen Folgendes:
> [!div class="checklist"]
> * Verwenden des Standard-e-Mail-Bildschirms
> * Vorgehensweise beim Ändern der Datei.
> * Integration in eine APP

Einen tieferen Einblick in die Standardfunktionalität dieses Bildschirms finden Sie in der [e-Mail-Bildschirm Referenz](email-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Machen Sie sich mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen vertraut, wenn Sie [in Power apps eine APP erstellen](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionalität

So fügen Sie einen e-Mail-Bildschirm aus der Vorlage hinzu

1. [Melden](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an, und erstellen Sie eine APP, oder öffnen Sie eine vorhandene app in powerapps Studio.

    In diesem Thema wird eine Phone-App gezeigt, aber die gleichen Konzepte gelten auch für eine Tablet-app.

1. Wählen Sie auf der Registerkarte **Start** des Menübands die Option **neuer Bildschirm** > **e-Mail**aus.

    Standardmäßig sieht der Bildschirm in etwa wie folgt aus:

    ![Bildschirm für e-Mail](media/email-screen/email-screen-full.png)

Einige hilfreiche Hinweise:

* Um nach Benutzern in Ihrer Organisation zu suchen, geben Sie Ihren Namen in das Texteingabefeld unterhalb von "to" ein.
* Wenn Sie nach Personen suchen, werden nur die ersten 15 Ergebnisse zurückgegeben.
* Wenn Sie e-Mail-Adressen für e-Mail-Empfänger außerhalb Ihrer Organisation hinzufügen möchten, geben Sie die vollständige, gültige e-Mail-Adresse ein, und wählen Sie das Symbol "+", das rechts neben
* Sie müssen mindestens eine Person als Empfänger hinzufügen und einen Betreff zum Senden einer e-Mail bereitstellen.
* Nachdem Sie die e-Mail gesendet haben, werden die Inhalte der Betreffzeile und der Nachrichtentext sowie die Empfängerliste gelöscht.

## <a name="modify-the-screen"></a>Bildschirm ändern

Sie können die Standardfunktionalität dieses Bildschirms auf einige gängige Weise ändern:

* [Unterstützung für das Hinzufügen von Images](email-screen-overview.md#add-image-attachment-support)
* [Andere Daten für Personen anzeigen](email-screen-overview.md#show-different-data-for-people)

Wenn Sie den Bildschirm weiter ändern möchten, verwenden Sie den [e-Mail-Bildschirm Verweis](./email-screen-reference.md) als Leitfaden.

> [!IMPORTANT]
> Bei den folgenden Schritten wird davon ausgegangen, dass der app nur ein e-Mail-Bildschirm hinzugefügt wurde. Wenn Sie mehr als ein Element hinzugefügt haben, enden Steuerelement Namen (z. b. **iconMail1**) mit einer anderen Zahl, und Sie müssen die Formeln entsprechend anpassen.

### <a name="add-image-attachment-support"></a>Unterstützung für das Hinzufügen von Images

Dadurch können Benutzer ein einzelnes Bild mit Ihrer e-Mail als Anlage senden.

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Medien**, und klicken Sie dann auf **Bild hinzufügen**.
1. Legen Sie die **Y** -Eigenschaft des neuen Steuer Elements auf diesen Ausdruck fest:

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. Legen Sie mit dem eingefügten **addmediawithimage** -Steuerelement die Höhe auf weniger als 210 fest.
1. Wählen Sie in der Ansicht Steuerelement Struktur die Option **addmediawithimage** aus, >  **...**  > **neu anordnen** > **an zurücksenden**.
   Dadurch wird verhindert, dass das Steuerelement vor dem **People browsegallery** -Steuerelement liegt.
1. Ändern Sie die **height** -Eigenschaft von **emailpeoplegallery** in diese Formel:

    ```powerapps-comma
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2; 0 ); 
        304
    )
    ```

1. Legen Sie die **ShowScrollbar** -Eigenschaft von **emailpeoplegallery** auf diesen Ausdruck fest:

    ```EmailPeopleGallery1.Height >= 304```
    
    Dadurch wird verhindert, dass die maximale Höhe das **addmediawithimage** -Steuerelement von der Seite überträgt.
    
1. Ändern **Sie die onselect** -Eigenschaft des **iconmail** -Steuer Elements in diese Formel:

    ```powerapps-comma
    Set( _emailRecipientString; Concat(MyPeople; Mail & ";") );;
    If( IsBlank( UploadedImage1 );
        'Office365'.SendEmail( _emailRecipientString; 
            TextEmailSubject1.Text; 
            TextEmailMessage1.Text; 
            { Importance: "Normal" }
        );
        'Office365'.SendEmail( _emailRecipientString; 
            TextEmailSubject1.Text; 
            TextEmailMessage1.Text; 
            {
                Importance: "Normal";
                Attachments: Table(
                    {
                        Name: "Image.jpg"; 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );;
    Reset( TextEmailSubject1 );;
    Reset( TextEmailMessage1 );;
    Reset( AddMediaButton1 );;
    Clear( MyPeople )
    ```
    
    Diese Formel überprüft ein hochgeladenes Bild. Wenn keine vorhanden ist, wird derselbe `Office365.SendEmail` Vorgang wie zuvor verwendet. Wenn ein Bild vorhanden ist, wird es in der Tabelle Anhänge als Anlage hinzugefügt.
    Nach dem Senden der e-Mail wird ein **zusätzlicher** Zurücksetzungs Vorgang für **addmediabutton** durchgeführt, um das hochgeladene Image zu entfernen.
> [!NOTE]
> Wenn Sie einer e-Mail mehr als eine Anlage hinzufügen möchten, fügen Sie der Tabelle Anhänge Datensätze hinzu.

### <a name="show-different-data-for-people"></a>Andere Daten für Personen anzeigen

In diesem Bildschirm wird der [Office365Users. searchuser](https://docs.microsoft.com/connectors/office365users/#searchuser) -Vorgang verwendet, um nach Benutzern in Ihrer Organisation zu suchen. Es werden zusätzliche Felder für jedes Ereignis bereitstellt, die über die im **People browsegallery** -Steuerelement angezeigten Ereignisse hinausgehen. Das Hinzufügen oder Ändern von Feldern im Katalog ist einfach:

1. Wählen Sie im **People browsegallery** -Steuerelement eine zu ändernde Bezeichnung aus (oder fügen Sie Sie ein, und lassen Sie Sie ausgewählt).

1. Ersetzen Sie bei ausgewählter Text-Eigenschaft in der **Bearbeitungs** Leiste den Inhalt durch `ThisItem.`

    IntelliSense zeigt eine Liste von Feldern an, die Sie auswählen können.

1. Wählen Sie das gewünschte Feld aus.

    Die **Text** Eigenschaft wird `ThisItem.{FieldSelection}`aktualisiert.

## <a name="integrate-the-screen-into-an-app"></a>Integrieren des Bildschirms in eine APP

Der e-Mail-Bildschirm ist eine leistungsstarke Gruppe von Steuerelementen, die sich in der Regel am besten als Teil einer größeren, vielseitigen App eignet. Sie können diesen Bildschirm auf verschiedene Arten in eine größere App integrieren, einschließlich [der Verknüpfung mit dem Kalender Bildschirm](email-screen-overview.md#linking-to-the-calendar-screen).

### <a name="linking-to-the-calendar-screen"></a>Verknüpfen mit dem Kalender Bildschirm

Befolgen Sie die Schritte im Abschnitt "Anzeigen von Ereignis Teilnehmer" der [Übersicht über das Kalender Bildschirm](./calendar-screen-overview.md#show-event-attendees) , aber legen Sie im letzten Schritt die **Navigate** -Funktion fest, um den e-Mail-Bildschirm zu öffnen. Nachdem Sie diese Schritte ausgeführt haben, wird die Sammlung **mypeople** aufgefüllt, die es Benutzern ermöglicht, e-Mails an die Personen zu senden, die das ausgewählte Ereignis besuchen.

> [!NOTE]
> Wenn Sie diese e-Mail senden, wird eine separate e-Mail von dem eigentlichen Ereignis in Ihrer Outlook-Nachricht gesendet.

## <a name="next-steps"></a>Nächste Schritte

* [Sehen Sie sich die Referenz Dokumentation für diesen Bildschirm an](./email-screen-reference.md).
* [Erfahren Sie mehr über den Office 365-Benutzer-Connector in Power apps](../connections/connection-office365-users.md).
* Anzeigen [aller verfügbaren Verbindungen in powerapps](../connections-list.md)