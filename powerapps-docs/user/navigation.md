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
ms.openlocfilehash: b05b3220c4e67565a6055a23915cc65f5d434eb2
ms.sourcegitcommit: eda3382ade50efe66611518c8f36e3a2ada7a91d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77282436"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>Einfache Navigation in einer modellgesteuerten App 

In diesem einführenden Artikel wird erläutert, wie Sie eine App suchen und öffnen und allgemeinen Benutzeroberflächenelementen wie Listen, Formularen und Geschäftsprozessen arbeiten.

## <a name="navigating-among-apps-areas-and-entities"></a>Navigieren zwischen Apps, Bereichen und Entitäten

Eine modellgesteuerte App wird aus Anwendungen (Apps), Bereichen und Entitäten erstellt.

- *Apps* bieten Funktionen für bestimmte Aktivitäten, z. B. zum Verwalten von Konten und Kontakten. Über das Menü für die App-Auswahl können Sie zwischen den Apps Ihrer Organisation navigieren.

- Eine *Arbeitsbereichs* ist ein Unterbereich einer App, der für ein bestimmtes Feature vorgesehen ist. In jedem Arbeitsbereich werden gezielt die Entitäten für die Arbeit in diesem Bereich aufgelistet. In einigen Fällen wird dieselbe Entität in mehr als einem Bereich (oder in mehr als einer App) aufgeführt. Die Entitäten „Kontakt“ und „Konto“ erscheinen beispielsweise in vielen Apps und Arbeitsbereichen. Über das Menü „Arbeitsbereich“ können Sie zwischen den Arbeitsbereichen der aktuellen App navigieren.

- *Entitäten* stehen für einen bestimmten Datentyp, z. B. Kontakte und Konten. Entitäten verwenden ein strukturiertes Datenformat, das die für die Entität verfügbaren Felder definiert. Jede Entität besteht aus einzelnen Datensätzen. Bei der Entität „Kontakt“ beschreibt beispielsweise jeder Datensatz eine Einzelperson und enthält Felder wie „Vorname“, „Nachname“ und „E-Mail-Adresse“. Entitäten verfügen normalerweise über zwei Ansichten: eine Listenansicht (in der Regel eine Tabelle mit den verfügbaren Datensätzen) und eine Formularansicht, in der alle verfügbaren Daten und Einstellungen für einen einzelnen Datensatz angezeigt werden. Verwenden Sie den Navigator auf der Seite, um zwischen den Entitäten im aktuellen Arbeitsbereich zu navigieren.

### <a name="move-between-apps"></a>Navigation zwischen Apps

Sie können über das Menü „App-Auswahl“ zwischen Apps wechseln.

![Menü „App-Auswahl“](media/app-selector.png "Menü „App-Auswahl“")

Die in der App-Auswahl aufgeführten Apps hängen davon ab, auf welche Apps Sie Zugriff haben. 

### <a name="move-between-entities-records-and-work-areas"></a>Navigation zwischen Entitäten, Datensätzen und Arbeitsbereichen

Es ist ganz einfach, zwischen Ihren bevorzugten oder am häufigsten verwendeten Datensätzen zu wechseln und zu diesen zurückzukehren. Auf der folgenden Abbildung werden die primären Navigationselemente veranschaulicht:

![Navigationssteuerelemente, erweiterte Ansicht](media/nav-expanded.png "Navigationssteuerelemente, erweiterte Ansicht")

Legende:

1. **App-Auswahl:** Öffnen Sie dieses Menü, um zwischen Apps zu wechseln.
2. **Schaltfläche „Reduzieren/Erweitern“:** Klicken Sie auf diese Schaltfläche, um den Navigator zu reduzieren und mehr Platz für den Hauptteil der Seite zu schaffen. Wenn der Navigator bereits reduziert ist, klicken Sie auf diese Schaltfläche, um ihn wieder zu erweitern.
3. **Zuletzt verwendete Datensätze:** Erweitern Sie diesen Eintrag, um eine Liste der zuletzt verwendeten Datensätze anzuzeigen. Klicken Sie hier auf einen Datensatz, um ihn zu öffnen. Klicken Sie auf das Stecknadelsymbol neben einem aufgelisteten Datensatz, um diesen zu Ihren Favoriten (angeheftete Datensätze) hinzuzufügen.
4. **Bevorzugte Datensätze:** Erweitern Sie diesen Eintrag, um Ihre bevorzugten (angehefteten) Datensätze anzuzeigen und zu öffnen. Über die Liste **Zuletzt verwendete Datensätze** können Sie Datensätze hinzufügen. Klicken Sie erneut auf das Stecknadelsymbol neben einem aufgelisteten Datensatz, um diesen aus der Liste zu entfernen.
5. **Entitätennavigator:** In diesem Bereich werden alle für den aktuellen Arbeitsbereich verfügbaren Entitäten und Dashboards aufgelistet. Wählen Sie einen beliebigen Eintrag aus, um das benannte Dashboard oder die Listenansicht für diese Entität zu öffnen.
6. **Arbeitsbereichauswahl:** Öffnen Sie dieses Menü, um zu einem anderen Arbeitsbereich zu wechseln. Der aktuelle Arbeitsbereich wird hier angezeigt.

## <a name="working-with-list-views"></a>Arbeiten mit Listenansichten

Wenn Sie eine Entität zum ersten Mal öffnen, wird die Listenansicht angezeigt, in der im Tabellenformat eine Liste der Datensätze angezeigt wird, die zu dieser Entität gehören. Wenn Sie z. B. die Entität **Konten** öffnen, wird eine Liste der Konten angezeigt.

![Eine typische Listenansicht](media/list-view.png "Eine typische Listenansicht")

Legende:

1. **Datensätze auswählen:** Wählen Sie einen oder mehrere Datensätze aus, indem Sie in dieser Spalte ein Häkchen setzen. Je nachdem, wo Sie arbeiten, können Sie einen Vorgang auf alle ausgewählten Datensätze anwenden, indem Sie die Schaltflächen auf der Befehlsleiste verwenden.
2. **Einen Datensatz öffnen:** Wählen Sie einen beliebigen Datensatz in der Liste aus, um die zugehörige Ansicht zu öffnen, in der alle Details zum Datensatz angezeigt werden. In der Regel treffen Sie eine Auswahl in der Spalte **Name**, um einen Datensatz aus der aktuellen Entität zu öffnen. Einige Entitäten enthalten Links zu Datensätzen aus verknüpften Entitäten in anderen Spalten (z. B. ein zugehöriger Kontakt).
3. **Listen sortieren oder filtern:** Legen Sie fest, dass eine Spalte nach Werten sortiert wird, oder filtern Sie die Liste nach Werten in der Spalte. Ein Pfeil in der Spaltenüberschrift gibt an, welche Spalte in welche Richtung sortiert wird. 
4. **Befehlsleiste:** Verwenden Sie die Befehle auf der Befehlsleiste, um Datensätze in der Liste zu verarbeiten und ähnliche Aktionen auszuführen. Für einige Befehle (z. B. **Löschen**) ist es erforderlich, dass Sie zuerst einen oder mehrere Zieldatensätze auswählen, indem Sie ein Häkchen in der Spalte ganz links setzen, während andere auf die gesamte Liste angewendet werden. Sie können je nach Datensatz z. B. die Liste in eine Excel-Arbeitsmappe (ggf. anhand einer Vorlage) exportieren oder Diagramme und Dashboards öffnen.
5. **Ansicht durchsuchen:** Geben Sie Text in das Suchfeld oberhalb der Liste ein, um nur die Datensätze in der aktuellen Ansicht anzuzeigen, die diesen Text enthalten.
6. **Filtern und durch Seiten navigieren:** Wählen Sie einen Buchstaben aus, um nur die Datensätze anzuzeigen, deren Namen mit diesem Buchstaben beginnen. Wenn die Liste mehr Datensätze enthält als auf einer Seite angezeigt werden können, verwenden Sie die Pfeile am unteren Rand der Liste, um vorwärts und rückwärts durch die Seiten zu navigieren.

## <a name="working-with-record-views"></a>Arbeiten mit Datensatzansichten

In den Datensatzansichten werden alle Details zu einem Datensatz und ggf. spezielle Features für die Arbeit mit diesem angezeigt. Normalerweise wird eine Datensatzansicht geöffnet, indem Sie einen Datensatz aus einer Listenansicht auswählen. Sie können eine Datensatzansicht jedoch auch öffnen, indem Sie in einem ähnlichen Datensatz auf einen Link klicken.

![Eine typische Datensatzansicht](media/form-view.png "Eine typische Datensatzansicht")

Legende:


1. **Registerkarten**: Die meisten Datensatzansichten sind in Registerkarten unterteilt. Jede Registerkarte enthält ähnliche Felder aus dem Datensatz. Wenn Registerkarten verfügbar sind, werden sie unter dem Datensatznamen aufgelistet. Klicken Sie auf den Namen einer Registerkarte, um zu dieser zu navigieren. Die aktuelle Registerkarte wird unterstrichen.
2. **Ähnlich:** Fast alle Datensatztypen enthalten die Registerkarte **Ähnlich**, nachdem Sie den Datensatz mindestens einmal gespeichert haben. Diese Registerkarte ist eine Dropdownliste, die Sie verwenden können, um andere Datensatztypen zu suchen, die den angezeigten Datensatz verwenden oder auf diesen verweisen. Wenn Sie einen Entitätsnamen aus der Dropdownliste **Ähnlich** auswählen, wird eine neue Registerkarte für diese Entität geöffnet, die alle ähnlichen Datensätze für diesen Typ anzeigt. Die Registerkarte **Ähnlich** ist weiterhin verfügbar, und Sie können diese verwenden, um andere Datensatztypen zu suchen, die auf den aktuellen Datensatz verweisen.
3. **Befehlsleiste:** Verwenden Sie die Befehle in der Befehlsleiste, um im aktuellen Datensatz zu agieren, oder führen Sie eine Aufgabe in Zusammenhang mit dem Datensatz durch. Welche Befehle verfügbar sind, hängt vom Datensatztyp ab. Sie können jedoch in der Regel die Befehlsleiste verwenden, um Änderungen zu speichern, den Datensatz zu löschen, die Seite zu aktualisieren, einen Link zum Datensatz per E-Mail zu senden, den Datensatzbesitzer neu festzulegen oder den Datensatz mithilfe einer Word-Vorlage zu exportieren.
4. **Überschriftenleiste:** Einige Datensatzansichten zeigen gegenüber des Datensatznamens wichtige Felder in der Überschriftenleiste an. Dabei handelt es sich in der Regel um Felder, die für die Arbeit mit Datensätzen des aktuellen Typs essenziell sind (z. B. den Datensatznamen oder -besitzer).
5. **Alle Feldwerte anzeigen und bearbeiten:** Im Hauptteil der Datensatzansicht befinden sich alle Felder, die sich auf die aktuelle Registerkarte, die Formularansicht und den Datensatztyp beziehen. Mit einem roten Sternchen gekennzeichnete Felder sind Pflichtfelder. Sie können den Datensatz nicht speichern, wenn in diesen keine gültigen Werte vorhanden sind. Felder, die mit einem blauen Pluszeichen gekennzeichnet sind, sind besonders wichtig oder werden empfohlen, sind jedoch nicht unbedingt erforderlich. Felder mit einem Sperrsymbol sind schreibgeschützt und können nicht bearbeitet werden.

## <a name="record-set-navigation"></a>Navigation durch die Datensatzgruppe 

Navigieren Sie mit vordefinierten Ansichten und Abfragen durch mehrere Datensätze. Die auf Datensätze ausgerichtete Navigation steigert die Produktivität, indem es Benutzern ermöglicht wird, in der Liste von Datensatz zu Datensatz zu springen und ganz einfach zurück zu navigieren, ohne dabei den Verlust der Liste für die Arbeit zu riskieren.

> [!div class="mx-imgBorder"]
> ![Navigation durch Datensatzgruppen](media/recordset1.png "Navigation durch die Datensatzgruppe")

## <a name="reference-panel"></a>Referenzbereich

Im Referenzbereich können Sie Aufgaben erledigen, ohne die Bildschirmansicht verlassen zu müssen, in der Sie sich gerade befinden. Sie können im Rahmen des angezeigten Datensatzes ähnliche Elemente nachschlagen, z. B. Fälle oder Möglichkeiten für ein Konto, ohne dafür den Bildschirm wechseln zu müssen.

> [!div class="mx-imgBorder"]
> ![Referenzbereich](media/reference-panel1.png "Referenzbereich")

 In diesem Video wird der Referenzbereich näher erläutert:

<div class="embeddedvideo"><iframe src="https://www.microsoft.com/videoplayer/embed/d8224c3f-6e20-4b8e-9d0d-b0f5602c7708" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>Benachrichtigungen 

Es gibt drei Arten von Benachrichtigungen, die auf einem Formular angezeigt werden: Informationen, Warnungen und Fehler. Benachrichtigungen werden immer ganz oben auf dem Formular angezeigt (direkt über der Kopfzeile).

Wenn Sie auf eine Fehlermeldung klicken, gelangen Sie zu dem Feld im Formular, in dem der Fehler aufgetreten ist.

![Beispiel für Benachrichtigungen](media/notifications.png "Beispiel für Benachrichtigungen")

Legende:

1. **Info:** Bei dieser Benachrichtigung handelt es sich um eine Information.
2. **Warnen:** Bei dieser Benachrichtigung handelt es sich um eine Warnung. 
3. **Fehler:** Bei dieser Benachrichtigung handelt es sich um eine Fehlermeldung. 



### <a name="single-notification"></a>Einzelne Benachrichtigung

Wenn nur eine Benachrichtigung vorhanden ist, wird nur eine Zeile angezeigt.

![Beispiel für eine einzelne Benachrichtigung](media/single_notification.png "Beispiel für eine einzelne Benachrichtigung")

### <a name="multiple-notifications"></a>Mehrere Benachrichtigungen

Wenn mehrere Benachrichtigungen vorhanden sind, wird die Anzahl der Benachrichtigungen angezeigt. Klicken Sie auf das Chevron, um die einzelnen Meldung anzuzeigen.

![Beispiel für mehrere Benachrichtigungen](media/multiple_notification.png "Beispiel für mehrere Benachrichtigungen")
