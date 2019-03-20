---
title: Meeting-Bildschirmvorlage | Microsoft-Dokumentation
description: Verstehen, wie die Besprechung Bildschirmvorlage für Canvas-apps funktioniert, und erweitern Sie den Bildschirm für Ihre eigenen Anwendungsfälle
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 24f04ff9ce95f603f5f7d4dc7d217146b9eebef8
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459402"
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>Übersicht über die Besprechung Bildschirmvorlage für Canvas-apps

Fügen Sie in einer Canvas-app einen Besprechung-Bildschirm, mit dem Benutzer erstellen und senden Besprechungsanfragen ihres Office 365 Outlook-Kontos ein. Benutzer können die Teilnehmer in ihrer Organisation suchen und externe e-Mail-Adressen hinzufügen. Wenn es sich bei Ihrem Mandanten Besprechungsräume in Outlook integriert ist, können Benutzer auch einen Speicherort auswählen.

Sie können auch andere Template-basierten Bildschirme, die zeigen, wie z. B. verschiedene Daten aus Office 365 hinzufügen [-e-Mail](email-screen-overview.md), [Personen](people-screen-overview.md) in einer Organisation und eines Benutzers [Kalender](calendar-screen-overview.md).

In dieser Übersicht erfahren Sie, über die allgemeine Funktionalität des Bildschirms.

Tiefer in die Standardfunktionalität des Bildschirms, finden Sie unter den [Meeting-bildschirmreferenz](meeting-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und Steuerelementen wie [Erstellen einer app in PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionen

So fügen Sie einen Bildschirm für die Besprechung aus der Vorlage hinzu:

1. [Melden Sie sich bei](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) powerapps an, und klicken Sie dann erstellen Sie eine app oder eine vorhandene app in PowerApps Studio öffnen.

    In diesem Thema wird gezeigt, eine Phone-app, die gleichen Konzepte gelten jedoch für eine Tablet-app.

1. Auf der **Startseite** Menüband auf der Registerkarte **neuer Bildschirm** > **Besprechung**.

  Wenn die beiden Registerkarten für die Besprechung Bildschirm ausfüllen ähnelt dieser:

  ![Bildschirm "Besprechung" beiden Registerkarten](media/meeting-screen/meeting-screen-full-both.png)

Einige hilfreiche Hinweise:

* Der Bildschirm für die Besprechung kann app-Benutzer zu eine Besprechung in Outlook erstellt werden.
  Benutzer können Suchen und Teilnehmer hinzufügen, und, optional ein besprechungsraums hinzufügen, zu der Besprechung.
* Um für einen Benutzer in Ihrer Organisation zu suchen, starten Sie ihren Namen im Feld "Texteingabe" unter "Teilnehmer" eingeben.
* Wenn Sie nach Personen suchen, werden nur die ersten 15 Ergebnisse zurückgegeben.
* Um die e-Mail-Adressen für Teilnehmer außerhalb Ihrer Organisation hinzufügen möchten, geben Sie die vollständige, gültige e-Mail-Adresse, und wählen Sie das "+"-Symbol, das rechts neben der e-Mail-Adresse angezeigt wird.
* Um eine Besprechung zu erstellen, Sie müssen mindestens einer Person als Teilnehmer hinzufügen, geben Sie einen Betreff, und wählen einen Zeitpunkt in der **Zeitplan** Registerkarte.
* Nachdem Sie die Anfrage zu senden, wird alle zugehörigen Informationen gelöscht.
* Die **OnSelect** -Anweisung von Symbol "Senden" (in der oberen rechten Ecke), enthält diese Formel:
    ```powerapps-dot
    Set( _myCalendarName, 
        LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name 
    );
    ```
* "Kalender" ist der standardmäßige Anzeigename für die meisten Office Kalender des Benutzers Ihrer Organisation kann sich unterscheiden. Wenn dies der Fall ist, können Sie "Kalender" auf den entsprechenden Begriff für Ihre Organisation bieten ändern.
* Sie erhalten eine Fehlermeldung, wenn Sie versuchen, eine Besprechung zu planen, die in der Vergangenheit liegt oder Hinzufügen von mehr als 20 Mitarbeitern zu einer Besprechung.

## <a name="next-steps"></a>Nächste Schritte

* [Die Referenzdokumentation für diesen Bildschirm](./meeting-screen-reference.md).
* [Erfahren Sie mehr über das Office 365 Outlook-Connector](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über das Office 365-Benutzer-Connector](../connections/connection-office365-users.md).
