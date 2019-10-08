---
title: Besprechungs Bildschirm Vorlage | Microsoft-Dokumentation
description: Erfahren Sie, wie die Vorlage für den Besprechungs Bildschirm für Canvas-apps funktioniert, und erweitern Sie den Bildschirm für Ihre eigenen Anwendungsfälle.
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
ms.openlocfilehash: c53857acfdcb44faa26b2ec3e04b904e25c09aee
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995651"
ms.PowerAppsDecimalTransform: true
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>Übersicht über die Besprechungs Bildschirm Vorlage für Canvas-apps

Fügen Sie in einer Canvas-APP einen Besprechungs Bildschirm hinzu, mit dem Benutzer Besprechungs Anfragen von Ihren Office 365 Outlook-Konten erstellen und senden können. Benutzer können in Ihrer Organisation nach Teilnehmern suchen und externe e-Mail-Adressen hinzufügen. Wenn Ihr Mandant über Besprechungsräume verfügt, die in Outlook integriert sind, können Benutzer auch einen Speicherort auswählen.

Sie können auch andere vorlagenbasierte Bildschirme hinzufügen, die unterschiedliche Daten aus Office 365 anzeigen, z. b. [e-Mail](email-screen-overview.md), [Personen](people-screen-overview.md) in einer Organisation und den [Kalender](calendar-screen-overview.md)eines Benutzers.

In dieser Übersicht werden die Funktionen auf hoher Ebene für den Bildschirm erläutert.

Einen tieferen Einblick in die Standardfunktionalität dieses Bildschirms finden Sie in der [Referenz zum Besprechungs Bildschirm](meeting-screen-reference.md).

## <a name="prerequisite"></a>Voraussetzung

Vertrautheit mit dem Hinzufügen und Konfigurieren von Bildschirmen und anderen Steuerelementen [beim Erstellen einer APP in powerapps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Standardfunktionalität

So fügen Sie einen Besprechungs Bildschirm aus der Vorlage hinzu:

1. [Melden](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich bei powerapps an, und erstellen Sie eine APP, oder öffnen Sie eine vorhandene app in PowerApps Studio.

    In diesem Thema wird eine Phone-App gezeigt, aber die gleichen Konzepte gelten auch für eine Tablet-app.

1. Wählen Sie auf der Registerkarte **Start** des Menübands die Option **neuer Bildschirm** > **Meeting**aus.

  Wenn Sie ausgefüllt sind, sehen beide Registerkarten des Besprechungs Bildschirms ungefähr wie folgt aus:

  ![Besprechungs Bildschirm, beide Registerkarten](media/meeting-screen/meeting-screen-full-both.png)

Einige hilfreiche Hinweise:

* Der Besprechungs Bildschirm ermöglicht einem App-Benutzer das Erstellen einer Besprechung in Outlook.
  Benutzer können nach Teilnehmern suchen und diese hinzufügen und optional einen Besprechungsraum zur Besprechung hinzufügen.
* Um in Ihrer Organisation nach einem Benutzer zu suchen, beginnen Sie mit der Eingabe des Namens im Texteingabefeld unter "Teilnehmer".
* Wenn Sie nach Personen suchen, werden nur die ersten 15 Ergebnisse zurückgegeben.
* Um e-Mail-Adressen für Teilnehmer außerhalb Ihrer Organisation hinzuzufügen, geben Sie die vollständige, gültige e-Mail-Adresse ein, und wählen Sie das Symbol "+" rechts neben der e-Mail-Adresse aus.
* Zum Erstellen einer Besprechung müssen Sie mindestens eine Person als Teilnehmer hinzufügen, einen Betreff angeben und eine Besprechungszeit auf der Registerkarte **Zeitplan** auswählen.
* Nachdem Sie die Besprechungs Anfrage gesendet haben, werden alle Informationen zu dieser Besprechung gelöscht.
* Die **onselect** -Anweisung des Sende Symbols (obere rechte Ecke) enthält folgende Formel:
    ```powerapps-comma
    Set( _myCalendarName; 
        LookUp( 'Office365'.CalendarGetTables().value; DisplayName = "Calendar" ).Name 
    );;
    ```
* "Calendar" ist der Standard Anzeige Name für die meisten Kalender des Office-Benutzers, Ihre Organisation kann jedoch abweichen. Wenn dies der Fall ist, können Sie "Calendar" in den entsprechenden Begriff für Ihre Organisation ändern.
* Sie erhalten eine Fehlermeldung, wenn Sie versuchen, eine Besprechung in der Vergangenheit zu planen oder einer Besprechung mehr als 20 Personen hinzuzufügen.

## <a name="next-steps"></a>Nächste Schritte

* [Sehen Sie sich die Referenz Dokumentation für diesen Bildschirm an](./meeting-screen-reference.md).
* [Erfahren Sie mehr über den Outlook-Connector von Office 365](../connections/connection-office365-outlook.md).
* [Erfahren Sie mehr über den Connector für Office 365-Benutzer](../connections/connection-office365-users.md).
