---
title: Einfache Navigation in einer modellgesteuerten App | Microsoft-Dokumentation
description: Einfache Navigation in einer modellgesteuerten App In diesem Artikel wird erläutert, wie Sie eine App suchen und öffnen und allgemeinen Benutzeroberflächenelementen wie Listen, Formularen und Geschäftsprozessen arbeiten.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 02/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1932699e669b47eba91c4e576416d287d590b5e8
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2020
ms.locfileid: "3303298"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>Einfache Navigation in einer modellgesteuerten App 

In diesem einführenden Artikel wird erläutert, wie Sie eine App suchen und öffnen und allgemeinen Benutzeroberflächenelementen wie Listen, Formularen und Geschäftsprozessen arbeiten.

## <a name="navigating-among-apps-areas-and-entities"></a>Navigieren zwischen Apps, Bereichen und Entitäten

Eine modellgesteuerte App wird aus Anwendungen (Apps), Bereichen und Entitäten erstellt.

- *Apps* bieten Funktionen für bestimmte Aktivitäten, z. B. zum Verwalten von Konten und Kontakten. Über das Menü für die App-Auswahl können Sie zwischen den Apps Ihrer Organisation navigieren.

- Eine *Arbeitsbereichs* ist ein Unterbereich einer App, der für ein bestimmtes Feature vorgesehen ist. In jedem Arbeitsbereich werden gezielt die Entitäten für die Arbeit in diesem Bereich aufgelistet. In einigen Fällen wird dieselbe Entität in mehr als einem Bereich (oder in mehr als einer App) aufgeführt. Die Entitäten „Kontakt“ und „Konto“ erscheinen beispielsweise in vielen Apps und Arbeitsbereichen. Verwenden Sie das Arbeitsbereichsmenü, um zwischen den Arbeitsbereichen für die aktuelle App zu navigieren.

- *Entitäten* stehen für einen bestimmten Datentyp, z. B. Kontakte und Konten. Entitäten verwenden ein strukturiertes Datenformat, das die für die Entität verfügbaren Felder definiert. Jede Entität besteht aus einzelnen Datensätzen. Bei der Entität „Kontakt“ beschreibt beispielsweise jeder Datensatz eine Einzelperson und enthält Felder wie „Vorname“, „Nachname“ und „E-Mail-Adresse“. Entitäten haben normalerweise zwei Ansichten: eine Listenansicht, üblicherweise in Form einer Tabelle mit den verfügbaren Datensätze, sowie eine Formularansicht, in der alle verfügbaren Daten und Einstellungen eines einzelnen Datensatzes angezeigt werden. Mit dem Seitennavigator können Sie sich zwischen Entitäten in Ihrem aktuellen Arbeitsbereich bewegen.

### <a name="move-between-apps"></a>Navigation zwischen Apps

Sie können über das Menü „App-Auswahl“ zwischen Apps wechseln.

![Menü „App-Auswahl“](media/app-selector.png "Menü „App-Auswahl“")

Die in der App-Auswahl aufgeführten Apps hängen davon ab, auf welche Apps Sie Zugriff haben. 

### <a name="move-between-entities-records-and-work-areas"></a>Navigation zwischen Entitäten, Datensätzen und Arbeitsbereichen

Es ist ganz einfach, zwischen Ihren bevorzugten oder am häufigsten verwendeten Datensätzen zu wechseln und zu diesen zurückzukehren. Auf der folgenden Abbildung werden die primären Navigationselemente veranschaulicht:

![Navigationssteuerelemente, erweiterte Ansicht](media/nav-expanded.png "Navigationssteuerelemente, erweiterte Ansicht")

Legende:

1. **App-Auswahl**: Öffnen Sie dieses Menü, um zwischen Apps zu wechseln.
2. **Schaltfläche Minimieren/Erweitern**: Wählen Sie diese Option aus, um den Navigator zu minimieren, damit mehr Platz für den Hauptteil der Seite bleibt. Wenn der Navigator bereits reduziert ist, klicken Sie auf diese Schaltfläche, um ihn wieder zu erweitern.
3. **Aktuelle Datensätze**: Erweitern Sie diesen Eintrag, um eine Liste von Datensätzen anzuzeigen, die Sie vor Kurzem verwendet haben. Klicken Sie hier auf einen Datensatz, um ihn zu öffnen. Klicken Sie auf das Stecknadelsymbol neben einem aufgelisteten Datensatz, um diesen zu Ihren Favoriten (angeheftete Datensätze) hinzuzufügen.
4. **Lieblingsdatensätze**: Erweitern Sie den Eintrag, um Ihre Lieblingsdatensätze (angeheftet) anzuzeigen und zu öffnen. Über die Liste **Zuletzt verwendete Datensätze** können Sie Datensätze hinzufügen. Klicken Sie erneut auf das Stecknadelsymbol neben einem aufgelisteten Datensatz, um diesen aus der Liste zu entfernen.
5. **Entitätsnavigator**: In diesem Bereich wird jede Entität und jedes Dashboard aufgeführt, die bzw. das für den aktuellen Arbeitsbereich verfügbar ist. Wählen Sie einen beliebigen Eintrag aus, um das benannte Dashboard oder die Listenansicht für diese Entität zu öffnen.
6. **Arbeitsbereichsauswahl**: Öffnen Sie dieses Menü, um in einen anderen Arbeitsbereich zu wechseln. Der aktuelle Arbeitsbereich wird hier angezeigt.

## <a name="working-with-list-views"></a>Arbeiten mit Listenansichten

Wenn Sie eine Entität zum ersten Mal öffnen, wird die Listenansicht angezeigt, in der im Tabellenformat eine Liste der Datensätze angezeigt wird, die zu dieser Entität gehören. Wenn Sie z. B. die Entität **Konten** öffnen, wird eine Liste der Konten angezeigt.

![Eine typische Listenansicht](media/list-view.png "Eine typische Listenansicht")

Legende:

1. **Datensätze auswählen**: Wählen Sie einen oder mehrere Datensätze aus, indem Sie in dieser Spalte ein Häkchen setzen. Je nachdem, wo Sie arbeiten, können Sie einen Vorgang auf alle ausgewählten Datensätze anwenden, indem Sie die Schaltflächen auf der Befehlsleiste verwenden.
2. **Einen Datensatz öffnen**: Wählen Sie einen beliebigen Datensatz in der Ansicht aus, um dessen Formularseite zu öffnen. Auf ihr werden alle Details zum Datensatz angezeigt. In der Regel treffen Sie eine Auswahl in der Spalte **Name**, um einen Datensatz aus der aktuellen Entität zu öffnen. Einige Entitäten enthalten Links zu Datensätzen aus verknüpften Entitäten in anderen Spalten (z. B. ein zugehöriger Kontakt).
3. **Listen sortieren oder filtern**: Legen Sie fest, dass eine Spalte nach Werten sortiert wird, oder filtern Sie die Liste nach Werten in der Spalte. Ein Pfeil in der Spaltenüberschrift gibt an, welche Spalte in welche Richtung sortiert wird. 
4. **Befehlsleiste**: Verwenden Sie die Befehle in der Befehlsleiste, um Datensätze in der Liste zu bearbeiten und zugehörige Aktionen auszuführen. Bei einigen Befehlen (wie beispielsweise **Löschen**) muss zuerst mindestens ein Zieldatensatz ausgewählt werden. Dazu setzen Sie in die Spalte ganz links ein Häkchen. Bei anderen Befehlen wird die gesamte Liste bearbeitet. Sie können je nach Datensatz z. B. die Liste in eine Excel-Arbeitsmappe (ggf. anhand einer Vorlage) exportieren oder Diagramme und Dashboards öffnen.
5. **Die Ansicht durchsuchen**: Um nur die Datensätze in der aktuellen Ansicht abzurufen, die einen bestimmten Text enthalten, geben Sie den gewünschten Text in das Suchfeld über der Liste ein.
6. **Filtern und durch Seiten navigieren**: Wählen Sie einen Buchstaben aus, um nur die Datensätze anzuzeigen, deren Namen mit diesem Buchstaben beginnen. Wenn die Liste mehr Datensätze enthält als auf einer Seite angezeigt werden können, verwenden Sie die Pfeile am unteren Rand der Liste, um vorwärts und rückwärts durch die Seiten zu navigieren.

## <a name="working-with-record-views"></a>Arbeiten mit Datensatzansichten

In den Datensatzansichten werden alle Details zu einem Datensatz und ggf. spezielle Features für die Arbeit mit diesem angezeigt. Normalerweise wird eine Datensatzansicht geöffnet, indem Sie einen Datensatz aus einer Listenansicht auswählen. Sie können eine Datensatzansicht jedoch auch öffnen, indem Sie in einem ähnlichen Datensatz auf einen Link klicken.

![Eine typische Datensatzansicht](media/form-view.png "Eine typische Datensatzansicht")

Legende:


1. **Registerkarten**: Die meisten Datensatzansichten sind in Registerkarten unterteilt. Jede Registerkarte enthält ähnliche Felder aus dem Datensatz. Wenn Registerkarten verfügbar sind, werden sie unter dem Datensatznamen aufgelistet. Wählen Sie einen Registerkartennamen aus, um zu dieser Registerkarte zu wechseln. Die aktuelle Registerkarte wird unterstrichen angezeigt.
2. **Verknüpft**: Fast alle Datensatztypen enthalten die Registerkarte **Ähnlich**, nachdem Sie den Datensatz mindestens einmal gespeichert haben. Diese Registerkarte ist eine Dropdownliste, die Sie verwenden können, um andere Datensatztypen zu suchen, die den angezeigten Datensatz verwenden oder auf diesen verweisen. Wenn Sie einen Entitätsnamen aus der Dropdownliste **Ähnlich** auswählen, wird eine neue Registerkarte für diese Entität geöffnet, die alle ähnlichen Datensätze für diesen Typ anzeigt. Die Registerkarte **Ähnlich** ist weiterhin verfügbar, und Sie können diese verwenden, um andere Datensatztypen zu suchen, die auf den aktuellen Datensatz verweisen.
3. **Befehlsleiste**: Mit den Befehlen in der Befehlsleiste bearbeiten Sie den aktuellen Datensatz oder führen eine Aufgabe aus, die sich auf den Datensatz bezieht. Welche Befehle verfügbar sind, hängt vom Datensatztyp ab. Sie können jedoch in der Regel die Befehlsleiste verwenden, um Änderungen zu speichern, den Datensatz zu löschen, die Seite zu aktualisieren, einen Link zum Datensatz per E-Mail zu senden, den Datensatzbesitzer neu festzulegen oder den Datensatz mithilfe einer Word-Vorlage zu exportieren.
4. **Überschriftenleiste**: Einige Datenansichten zeigen einige wenige besonders wichtige Felder in der Überschriftenleiste gegenüber dem Datensatznamen an. Dabei handelt es sich in der Regel um Felder, die für die Arbeit mit Datensätzen des aktuellen Typs essenziell sind (z. B. den Datensatznamen oder -besitzer).
5. **Alle Feldwerte anzeigen und bearbeiten**: Im Hauptteil der Datensatzanzeige finden Sie die Felder, die zur aktuellen Registerkarte, Formularansicht sowie zum aktuellen Datensatztyp gehören. Mit einem roten Sternchen markierte Felder sind Pflichtfelder. Sie können den Datensatz nicht speichern, wenn diese keine gültigen Werte enthalten. Felder, die mit einem blauen Pluszeichen gekennzeichnet sind, sind besonders wichtig oder werden empfohlen, sind jedoch nicht unbedingt erforderlich. Felder mit einem Sperrsymbol sind schreibgeschützt und können nicht bearbeitet werden.

## <a name="record-set-navigation"></a>Navigation durch die Datensatzgruppe 

Navigieren Sie mit vordefinierten Ansichten und Abfragen durch mehrere Datensätze. Die auf Datensätze ausgerichtete Navigation steigert die Produktivität, indem es Benutzern ermöglicht wird, in der Liste von Datensatz zu Datensatz zu springen und ganz einfach zurück zu navigieren, ohne dabei den Verlust der Liste für die Arbeit zu riskieren.

> [!div class="mx-imgBorder"]
> ![Navigation durch Datensatzgruppen](media/recordset1.png "Navigation durch die Datensatzgruppe")

## <a name="reference-panel"></a>Bereich „Verweise“

Im Referenzbereich können Sie Aufgaben erledigen, ohne die Bildschirmansicht verlassen zu müssen, in der Sie sich gerade befinden. Sie können im Rahmen des angezeigten Datensatzes ähnliche Elemente nachschlagen&mdash;z. B. Fälle oder Möglichkeiten für ein Konto&mdash;ohne dafür den Bildschirm wechseln zu müssen.

> [!div class="mx-imgBorder"]
> ![Bereich „Verweise“](media/reference-panel1.png "Bereich „Verweise“")

 In diesem Video wird der Referenzbereich näher erläutert:

<div class="embeddedvideo"><iframe src="https://www.youtube.com/embed/ruAPEKY5vNc" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>Benachrichtigungen 

Es gibt drei Arten von Benachrichtigungen, die auf einem Formular angezeigt werden: Informationen, Warnungen und Fehler. Benachrichtigungen werden immer ganz oben auf dem Formular angezeigt (direkt über der Kopfzeile).

Wenn Sie auf eine Fehlermeldung klicken, gelangen Sie zu dem Feld im Formular, in dem der Fehler aufgetreten ist.

![Beispiel für Benachrichtigungen](media/notifications.png "Beispiel für Benachrichtigungen")

Legende:

1. **Info**: Bei dieser Benachrichtigung handelt es sich um eine Information.
2. **Warnen**: Bei dieser Benachrichtigung handelt es sich um eine Warnung. 
3. **Fehler**: Bei dieser Benachrichtigung handelt es sich um eine Fehlermeldung. 



### <a name="single-notification"></a>Einzelne Benachrichtigung

Wenn nur eine Benachrichtigung vorhanden ist, wird nur eine Zeile angezeigt.

![Beispiel für eine einzelne Benachrichtigung](media/single_notification.png "Beispiel für eine einzelne Benachrichtigung")

### <a name="multiple-notifications"></a>Mehrere Benachrichtigungen

Wenn mehrere Benachrichtigungen vorhanden sind, wird die Anzahl der Benachrichtigungen angezeigt. Klicken Sie auf das Chevron, um die einzelnen Meldung anzuzeigen.

![Beispiel für mehrere Benachrichtigungen](media/multiple_notification.png "Beispiel für mehrere Benachrichtigungen")
