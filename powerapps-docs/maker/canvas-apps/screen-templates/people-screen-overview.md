---
title: Personen-Bildschirm Vorlage | Microsoft-Dokumentation
description: Erfahren Sie, wie die Vorlage "Benutzer Bildschirm" für Canvas-apps funktioniert und wie Sie den Bildschirm für Ihre eigenen Anwendungsfälle erweitern können.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4f54a2f6d3bfa7c843b7b095f999050602e063b0
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675016"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>Übersicht über die Vorlage "Personen Bildschirm" für Canvas-apps

Fügen Sie in einer Canvas-APP einen People-Bildschirm hinzu, mit dem Benutzer innerhalb ihrer Organisationen nach Personen suchen können. Benutzer können einer Sammlung nach Personen suchen, Sie auswählen und diese hinzufügen. Sie können ändern, welche Datentypen in der Suchergebnis Galerie angezeigt werden, wie Sie die Auswahl ihrer Personen zum Senden einer e-Mail verwenden und andere Anpassungen vornehmen.

Sie können auch andere vorlagenbasierte Bildschirme hinzufügen, die unterschiedliche Daten aus Office 365 anzeigen, z. b. [e-Mail](email-screen-overview.md), [Kalender](calendar-screen-overview.md)eines Benutzers und [Verfügbarkeit](meeting-screen-overview.md) von Benutzern, die möglicherweise zu einer Besprechung einladen möchten.

Diese Übersicht vermittelt Ihnen Folgendes:
> [!div class="checklist"]
> * Verwendung des Bildschirms "Standardbenutzer"
> * Vorgehensweise beim Ändern des Bildschirms.
> * So integrieren Sie den Bildschirm in apps.

Einen tieferen Einblick in die Standardfunktionalität dieses Bildschirms finden Sie in der [People-Screen-Referenz](people-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen [beim Erstellen einer APP in powerapps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionalität

So fügen Sie einen People-Bildschirm aus der Vorlage hinzu:

1. [Melden](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an, und erstellen Sie eine APP, oder öffnen Sie eine vorhandene app in powerapps Studio.

    In diesem Thema wird eine Phone-App gezeigt, aber die gleichen Konzepte gelten auch für eine Tablet-app.

1. Wählen Sie auf der Registerkarte **Start** des Menübands die Option **New Screen** > **People**aus.

    Standardmäßig sieht der Bildschirm in etwa wie folgt aus:

    ![Bildschirm Zustand der anfänglichen Personen](media/people-screen/people-screen-empty.png)

1. Um mit der Suche nach Benutzern zu beginnen, wählen Sie oben das Texteingabefeld aus, und beginnen Sie mit der Eingabe des Namens eines Kollegen. Die Suchergebnisse werden unterhalb des Texteingabe Felds angezeigt:

    ![Benutzer Bildschirm-Such Zustand](media/people-screen/people-browse-gall-full.png)

1. Wenn Sie die einzelnen Benutzer aus den Suchergebnissen auswählen, werden Sie der **mypeople** -Sammlung hinzugefügt. Der Eingabe Wert für die Suchleiste wird zurückgesetzt und zeigt die Sammlung der von Ihnen ausgewählten Personen an:

    ![Ergebnisse der Benutzer-Bildschirm Sammlung](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>Bildschirm ändern

Sie können die Standardfunktionalität dieses Bildschirms ändern, indem Sie [unterschiedliche Daten für Personen anzeigen](people-screen-overview.md#show-different-data-for-people).

Wenn Sie den Bildschirm weiter ändern möchten, verwenden Sie die Benutzer [Bildschirm Referenz](./people-screen-reference.md) als Leitfaden.

### <a name="show-different-data-for-people"></a>Andere Daten für Personen anzeigen

In diesem Bildschirm wird der [Office365Users. searchuser](https://docs.microsoft.com/connectors/office365users/#searchuser) -Vorgang verwendet, um nach Benutzern in Ihrer Organisation zu suchen. Es werden zusätzliche Felder für jedes Ereignis bereitstellt, das über die im **userbrowsegallery** -Steuerelement angezeigten Ereignisse hinausgeht. Das Hinzufügen oder Ändern von Feldern im Katalog ist ein einfacher Vorgang:

1. Wählen Sie in **userbrowsegallery**eine zu ändernde Bezeichnung aus (oder fügen Sie Sie hinzu, und lassen Sie Sie ausgewählt).

1. Ersetzen Sie bei ausgewählter Text-Eigenschaft in der **Bearbeitungs** Leiste den Inhalt durch `ThisItem.`

    IntelliSense zeigt eine Liste von Feldern an, die Sie auswählen können.

1. Wählen Sie das gewünschte Feld aus.

    Die **Text** -Eigenschaft sollte auf `ThisItem.{FieldSelection}`aktualisiert werden.

## <a name="integrate-the-screen-into-an-app"></a>Integrieren des Bildschirms in eine APP

Der Bildschirm People ist ein leistungsfähiges Bündel von Steuerelementen, das in der Regel am besten als Teil einer größeren, vielseitigen APP funktioniert. Sie können diesen Bildschirm auf verschiedene Arten in eine größere App integrieren, einschließlich [der Verwendung der zwischengespeicherten Liste von Personen](people-screen-overview.md#use-your-cached-list-of-people).

### <a name="use-your-cached-list-of-people"></a>Verwenden der zwischengespeicherten Liste von Personen

Der Bildschirm Personen speichert Ihre Personen Auswahl in der **mypeople** -Auflistung zwischen. Wenn ihr Geschäftsszenario für eine Person-Suche aufgerufen werden soll, müssen Sie wissen, wie Sie diese Sammlung verwenden können. Hier erfahren Sie, wie Sie diesen Bildschirm mit einem rudimentären e-Mail-Bildschirm verbinden und e-Mails an Benutzer in der **mypeople** -Sammlung senden. Außerdem erhalten Sie Einblicke in die Funktionsweise des [e-Mail-Bildschirms](./email-screen-overview.md) .

1. Fügen Sie die Outlook-Datenquelle von Office 365 zu Ihrer APP hinzu, indem Sie die Registerkarte **Ansicht** auswählen, **Datenquellen** > **Datenquelle hinzufügen**auswählen und nach dem Office 365 Outlook-Connector suchen. Möglicherweise müssen Sie **neue Verbindung** auswählen, um Sie zu finden.
1. Fügen Sie nach dem Einfügen des Bildschirms "People" einen neuen leeren Bildschirm ein. Fügen Sie in diesem Bildschirm ein rückwärts Pfeilsymbol, zwei Texteingabefelder und ein Sende Symbol hinzu.
1. Benennen Sie den Bildschirm in **emailscreen**, das Symbol für den rückwärts Pfeil in " **backicon**", ein Texteingabefeld in " **subjetline**", das andere in " **MessageBody**" und das Sende Symbol an " **senargumenton**" um.
1. Legen **Sie die onselect** -Eigenschaft von **backicon** auf `Back()`fest.
1. Legen **Sie die onselect** -Eigenschaft von **sendion** auf diese Formel fest:

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    Hier verwenden Sie den Outlook-Connector, um eine e-Mail zu senden. Sie übergeben ihn `Concat(MyPeople, UserPrincipalName & ";")` als Empfängerliste. Diese Formel verkettet alle e-Mail-Adressen in der **mypeople** -Sammlung mit einer einzelnen Zeichenfolge, wobei Sie durch Semikolons getrennt werden. Dies unterscheidet sich nicht vom Schreiben einer Zeichenfolge von e-Mail-Adressen, die durch Semikolons in der "an"-Zeile Ihres bevorzugten e-Mail-Clients getrennt sind.
    * Sie übergeben `SubjectLine.Text` als Betreff der Nachricht und `MessageBody.Text` als Text der Nachricht.
1. Fügen Sie auf dem Bildschirm Personen in der oberen rechten Ecke das Symbol " **Mail** " ein.
   Ändern Sie die Farbe des Symbols in den gewünschten Wert.
1. Legen **Sie die onselect** -Eigenschaft der **sendische auf** `Navigate( EmailScreen, None )`fest.

    Sie verfügen jetzt über eine APP mit zwei Bildschirmen, in der Sie Benutzer auswählen, eine e-Mail-Nachricht verfassen und dann senden können. Sie können es gerne testen, aber seien Sie vorsichtig, da die APP e-Mails an jeden sendet, den Sie der **mypeople** -Sammlung hinzufügen.

## <a name="next-steps"></a>Nächste Schritte

* [Sehen Sie sich die Referenz Dokumentation für diesen Bildschirm an](./people-screen-reference.md).
* [Erfahren Sie mehr über den Outlook-Connector von Office 365](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über den Connector für Office 365-Benutzer](../connections/connection-office365-users.md).
