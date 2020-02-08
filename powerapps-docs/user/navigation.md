---
title: Einfache Navigation in einer modellgesteuerten App | Microsoft-Dokumentation
description: Grundlegende Navigation in einer Modell gesteuerten app. In diesem Thema wird erläutert, wie Sie eine APP suchen und öffnen und wie Sie mit ihren allgemeinen Benutzeroberflächen Elementen, einschließlich Listen, Formularen und Geschäftsprozessen, arbeiten.
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
ms.openlocfilehash: 7bf1b81047cc9ebb9e2812d08c84245b7f83c5a9
ms.sourcegitcommit: 4728372a4a467f65bab9ae17e91738f420e17374
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "77067477"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>Einfache Navigation in einer modellgesteuerten App 

In dieser Einführung wird erläutert, wie Sie eine APP suchen und öffnen und wie Sie mit ihren allgemeinen Benutzeroberflächen Elementen, einschließlich Listen, Formularen und Geschäftsprozessen, arbeiten.

## <a name="navigating-among-apps-areas-and-entities"></a>Navigieren zwischen apps, Bereichen und Entitäten

Eine Modell gesteuerte APP wird aus Anwendungen (Apps), Bereichen und Entitäten erstellt.

- *Apps* bieten eine Auflistung von Funktionen zum Erreichen einer bestimmten Aktivitäts Klasse, z. b. zum Verwalten von Konten und Kontakten. Verwenden Sie das Menü App-Selektor, um zwischen den für Ihre Organisation verfügbaren apps zu navigieren.

- Ein *Arbeitsbereich* ist eine Unterteilung einer APP, die für ein bestimmtes Feature reserviert ist. Jeder Arbeitsbereich bietet eine gezielte Auflistung von Entitäten für die Arbeit in diesem Bereich. In einigen Fällen wird dieselbe Entität in mehr als einem Bereich (oder sogar mehr als einer APP) angezeigt. Die Entitäten "Contact" und "Account" werden z. b. in einer Vielzahl von apps und Arbeitsbereichen angezeigt. Verwenden Sie das Menü Arbeitsbereich, um zwischen Arbeitsbereichen für Ihre aktuelle APP zu navigieren.

- *Entitäten* stellen einen bestimmten Datentyp dar, z. b. Kontakte und Konten. Entitäten verwenden ein strukturiertes Datenformat, das die für die Entität verfügbare Auflistung von Feldern definiert. Jede Entität besteht aus einer Sammlung einzelner Datensätze. Für die Entität "Contact" beschreibt jeder Datensatz z. b. eine einzelne Person, und jeder Datensatz enthält eine Auflistung von Feldern, z. b. Vorname, Nachname und e-Mail-Adresse. Entitäten verfügen normalerweise über zwei Ansichten: eine Listenansicht, in der Regel eine Tabelle mit verfügbaren Datensätzen. und eine Formularansicht, in der alle verfügbaren Daten und Einstellungen für einen einzelnen Datensatz angezeigt werden. Verwenden Sie den Seiten Navigator, um zwischen Entitäten im aktuellen Arbeitsbereich zu wechseln.

### <a name="move-between-apps"></a>Wechseln zwischen Apps

Verwenden Sie das Menü App-Selektor, um zwischen apps zu wechseln.

![Das App-Selektor-Menü](media/app-selector.png "Das App-Selektor-Menü")

Die apps, die in Ihrem App-Selektor angezeigt werden, hängen davon ab, auf welche apps Sie zugreifen können. 

### <a name="move-between-entities-records-and-work-areas"></a>Verschieben zwischen Entitäten, Datensätzen und Arbeitsbereichen

Es ist ganz einfach, zu Ihren bevorzugten oder am häufigsten verwendeten Datensätzen zurückzukehren. Die folgende Abbildung zeigt die primären Navigationselemente.

![Navigations Steuerelemente, erweiterte Ansicht](media/nav-expanded.png "Navigations Steuerelemente, erweiterte Ansicht")

Legende:

1. **App-Auswahl**: Öffnen Sie dieses Menü, um zwischen apps zu wechseln.
1. **Schaltfläche "reduzieren/erweitern**": Wählen Sie diese Option aus, um den Navigator zu reduzieren, um mehr Platz für den Hauptteil der Seite zuzulassen. Wenn der Navigator bereits reduziert ist, klicken Sie auf diese Schaltfläche, um Sie erneut zu erweitern.
1. **Letzte Datensätze**: Erweitern Sie diesen Eintrag, um eine Liste der zuletzt verwendeten Datensätze anzuzeigen. Wählen Sie hier einen Datensatz aus, um ihn zu öffnen. Wählen Sie das Push-Pin-Symbol neben einem hier aufgelisteten Datensatz aus, um es Ihren Favoriten (angeheftete Datensätze) hinzuzufügen.
1. **Favoriten Datensätze**: Erweitern Sie diesen Eintrag, um Ihre bevorzugten (fixierten) Datensätze anzuzeigen und zu öffnen. Verwenden Sie die Liste **Letzte Datensätze** , um hier Datensätze hinzuzufügen. Wählen Sie das Symbol Entfernen-Pin neben einem hier aufgelisteten Datensatz aus, um es aus der Liste zu entfernen.
1. **Entitäts Navigator**: in diesem Bereich werden alle für den aktuellen Arbeitsbereich verfügbaren Entitäten und Dashboards aufgelistet. Wählen Sie einen beliebigen Eintrag aus, um das benannte Dashboard oder die Listenansicht für diese Entität zu öffnen.
1. **Arbeitsbereichs Auswahl**: Öffnen Sie dieses Menü, um zu einem anderen Arbeitsbereich zu wechseln. Der aktuelle Arbeitsbereich wird hier benannt.

## <a name="working-with-list-views"></a>Arbeiten mit Listenansichten

Wenn Sie eine Entität zum ersten Mal öffnen, wird die Listenansicht angezeigt, in der eine Liste der Datensätze angezeigt wird, die zu dieser Entität gehören und als Tabelle formatiert sind. Wenn Sie z. b. die Entität **Accounts** öffnen, sehen Sie eine Liste der Konten.

![Eine typische Listenansicht](media/list-view.png "Eine typische Listenansicht")

Legende:

1. **Datensätze auswählen**: Wählen Sie einen oder mehrere Datensätze aus, indem Sie in dieser Spalte ein Häkchen platzieren. Abhängig davon, wo Sie arbeiten, können Sie möglicherweise einen einzelnen Vorgang auf alle ausgewählten Datensätze gleichzeitig anwenden, indem Sie die Schaltflächen in der Befehlsleiste verwenden.
2. **Öffnen eines Datensatzes**: Wählen Sie einen beliebigen Datensatz in der Liste aus, um die Daten Satz Ansicht zu öffnen, in der alle Details zum Datensatz angezeigt werden. Normalerweise wählen Sie aus der Spalte **Name** aus, um einen Datensatz aus der aktuellen Entität zu öffnen. Einige Entitäten stellen Links zu Datensätzen aus verknüpften Entitäten in anderen Spalten bereit (z. b. ein verwandter Kontakt).
3. **Sortieren oder Filtern der Liste**: Wählen Sie diese Option aus, um die Liste nach Werten in dieser Spalte zu sortieren, oder Filtern Sie die Liste nach Werten in dieser Spalte. Ein Pfeil in der Spaltenüberschrift gibt an, welche Spalte sortiert und in welcher Richtung sortiert wird. 
4. **Befehlsleiste**: Verwenden Sie die Befehle in der Befehlsleiste, um Datensätze in der Liste zu verarbeiten und verwandte Aktionen auszuführen. Einige Befehle (z. b. **Delete**) erfordern, dass Sie zuerst einen oder mehrere Ziel Datensätze auswählen, indem Sie ein Häkchen in der Spalte ganz links ablegen, während andere die gesamte Liste verwenden. Abhängig von der Art der Datensätze, mit denen Sie arbeiten, können Sie die Liste in eine Excel-Arbeitsmappe (möglicherweise basierend auf einer Vorlage) exportieren, Diagramme und Dashboards öffnen und vieles mehr.
5. **Durchsuchen der Ansicht**: Geben Sie Text in das Suchfeld oberhalb der Liste ein, um nur die Datensätze in der aktuellen Ansicht anzuzeigen, die Ihren Text enthalten.
6. **Filtern und Paging**: Wählen Sie einen Buchstaben aus, um nur die Datensätze anzuzeigen, deren Namen mit diesem Buchstaben beginnen. Wenn die Liste mehr Datensätze enthält, als auf einer Seite angezeigt werden können, verwenden Sie die Auslagerungs Pfeile am unteren Rand der Liste, um die Seiten vorwärts und rückwärts zu bewegen.

## <a name="working-with-record-views"></a>Arbeiten mit Daten Satz Ansichten

In den Daten Satz Sichten werden alle Details zu einem einzelnen Datensatz angezeigt, und manchmal werden auch besondere Features für die Arbeit mit dem Datensatz angezeigt. Normalerweise wird eine Daten Satz Ansicht geöffnet, indem ein Datensatz ausgewählt wird, der in einer Listenansicht angezeigt wird. Sie können jedoch auch eine Daten Satz Ansicht öffnen, indem Sie einen Link aus einem verknüpften Datensatz befolgen.

![Eine typische Daten Satz Ansicht](media/form-view.png "Eine typische Daten Satz Ansicht")

Legende:


1. **Registerkarten**: die meisten Daten Satz Sichten sind in Registerkarten unterteilt. Jede Registerkarte stellt eine Sammlung verwandter Felder aus dem Datensatz bereit. Wenn Registerkarten verfügbar sind, werden Sie unter dem Daten Satz Namen aufgelistet. Wählen Sie einen beliebigen Tabstopp Namen, um zu dieser Registerkarte zu wechseln Die Registerkarte aktuell wird unterstrichen angezeigt.
2. **Related**: fast alle Arten von Datensätzen zeigen eine **Verwandte** Registerkarte an, nachdem Sie Sie mindestens einmal gespeichert haben. Diese Registerkarte ist eine Dropdown Liste, die Sie verwenden können, um andere Typen von Datensätzen zu suchen, die den angezeigten Datensatz verwenden oder darauf verweisen. Wenn Sie in der Dropdown Liste **Verwandte** Entitäten einen Entitäts Namen auswählen, wird eine neue Registerkarte mit dem Namen für diese Entität geöffnet, auf der eine Liste aller zugehörigen Datensätze dieses Typs angezeigt wird. Die **zugehörige** Registerkarte bleibt verfügbar, und Sie können Sie weiterhin verwenden, um andere Typen von Datensätzen zu finden, die auf die aktuelle Registerkarte verweisen.
3. **Befehlsleiste**: Verwenden Sie die Befehle in der Befehlsleiste, um den aktuellen Datensatz auszuführen, oder führen Sie einen Task aus, der mit dem Datensatz verknüpft ist. Welche Befehle verfügbar sind, hängt vom Typ des Datensatzes ab. Sie können jedoch in der Regel die Befehlsleiste verwenden, um die Änderungen zu speichern, den Datensatz zu löschen, die Seite zu aktualisieren, einen Link zum Datensatz zu senden, den Daten Satz Besitzer neu zuzuweisen oder den Datensatz mithilfe einer Word-Vorlage zu exportieren.
4. Über **Schriften Leiste**: einige Daten Satz Sichten zeigen einige besonders wichtige Felder in der Überschriften Leiste an, die dem Daten Satz Namen entgegen liegen. Dabei handelt es sich in der Regel um Felder, die für die Arbeit mit Datensätzen des aktuellen Typs (z. b. der Daten Satz Name oder Daten Satz Besitzer) von Grund
5. **Alle Feldwerte anzeigen und bearbeiten**: im Hauptteil der Daten Satz Ansicht finden Sie alle Felder, die sich auf die aktuelle Registerkarte, die Formularansicht und den Daten Satz Typ beziehen. Felder, die mit einem roten Sternchen gekennzeichnet sind, sind erforderlich, und Sie können den Datensatz nicht speichern, ohne dass gültige Werte vorhanden sind. Felder, die mit einem blauen Pluszeichen gekennzeichnet sind, sind besonders wichtig oder werden empfohlen, sind jedoch nicht unbedingt erforderlich. Felder mit einem Sperrsymbol sind schreibgeschützt und können nicht bearbeitet werden.

## <a name="record-set-navigation"></a>Navigation durch die Datensatzgruppe 

Navigieren Sie durch mehrere Datensätze, indem Sie vordefinierte Ansichten und Abfragen verwenden. Die auf Datensätze ausgerichtete Navigation steigert die Produktivität, indem es Benutzern ermöglicht wird, in der Liste von Datensatz zu Datensatz zu springen und ganz einfach zurück zu navigieren, ohne dabei den Verlust der Liste für die Arbeit zu riskieren.

> [!div class="mx-imgBorder"]
> ![Navigation in Daten Satz Gruppen](media/recordset1.png "Navigation durch die Datensatzgruppe")

## <a name="reference-panel"></a>Referenzbereich

Der Bezugsbereich eignet sich hervorragend, um die Arbeit zu erledigen, ohne vom Bildschirm zu wechseln, auf dem Sie sich befinden. Sie können andere verwandte Elemente suchen&mdash;z. b. Fälle oder Verkaufschancen für ein Konto&mdash;im Kontext des Einsehens, den Sie anzeigen, ohne zu anderen Bildschirmen navigieren zu müssen.

> [!div class="mx-imgBorder"]
> ![Verweis Bereich](media/reference-panel1.png "Referenzbereich")

 Sehen Sie sich dieses Video an, um mehr über das Referenz Panel zu erfahren:

<div class="embeddedvideo"><iframe src="https://www.microsoft.com/videoplayer/embed/d8224c3f-6e20-4b8e-9d0d-b0f5602c7708" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>Benachrichtigungen 

Es gibt drei Arten von Benachrichtigungen, die auf einem Formular angezeigt werden: Information, Warnung und Fehler. Benachrichtigungen werden immer ganz oben auf dem Formular angezeigt (direkt über der Kopfzeile).

Wenn Sie die Fehler Benachrichtigung auswählen, gelangen Sie zum Feld im Formular, in dem der Fehler aufgetreten ist.

![Beispiel für Benachrichtigungen](media/notifications.png "Beispiele für Benachrichtigungen")

Legende:

1. **Info**: die Benachrichtigung dient nur zu Informationszwecken.
2. **Warnung: die**Benachrichtigung ist eine Warnung. 
3. **Fehler**: die Benachrichtigung ist ein Fehler. 



### <a name="single-notification"></a>Einzelne Benachrichtigung

Wenn nur eine Benachrichtigung vorliegt, wird eine einzelne Zeile angezeigt.

![Beispiel für einzelne Benachrichtigungen](media/single_notification.png "Beispiel für eine einzelne Benachrichtigung")

### <a name="multiple-notifications"></a>Mehrere Benachrichtigungen

Wenn mehrere Benachrichtigungen vorhanden sind, wird die Anzahl der Benachrichtigungen angezeigt. Wählen Sie das Chevron aus, um die einzelnen Nachrichten anzuzeigen.

![Beispiel für mehrere Benachrichtigungen](media/multiple_notification.png "Beispiel für mehrere Benachrichtigungen")
