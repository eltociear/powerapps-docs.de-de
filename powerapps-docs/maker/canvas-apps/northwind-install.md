---
title: Installieren von Northwind Traders-Datenbank und-Apps | Microsoft-Dokumentation
description: Installieren Sie die Northwind-Datenbank und die apps in einer Umgebung, um die relationalen Konzepte zu erforschen.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3a2c3b468c7ccc09c49221c65113e66b562f5ed1
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71990861"
---
# <a name="install-northwind-traders-database-and-apps"></a>Installieren von Northwind Traders-Datenbank und-Apps

Wenn Sie die Schritte in [dieser Reihe von Themen](northwind-orders-canvas-part1.md)ausführen, können Sie Konzepte von relationalen Daten ermitteln, die in Common Data Service in einer Beispieldatenbank implementiert werden. Sie können auch Beispiel-Business-Apps durchsuchen, sowohl Canvas als auch Modell gesteuert, um die Daten zu verwalten und praktische Funktionen zu erzielen, indem Sie eine solche APP erstellen. In diesem ersten Thema wird erläutert, wie Sie die Datenbank Northwind Traders in ihrer eigenen Umgebung installieren und Zugriff auf die Beispiel-apps erhalten, die Sie für die Bearbeitung öffnen können, um die Art der Erstellung anzuzeigen.

Northwind Traders ist eine fiktive Organisation, die Aufträge, Produkte, Kunden, Lieferanten und viele andere Aspekte eines kleinen Unternehmens verwaltet. Dieses Beispiel wurde mit den ersten Versionen von Microsoft Access angezeigt und ist weiterhin als Zugriffs Vorlage verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

- Eine powerapps-Lizenz, die Common Data Service unterstützt. Sie können [eine kostenlose Testversion](../signup-for-powerapps.md) für 30 Tage verwenden.
- Eine Umgebung mit einer Common Data Service Datenbank. Sie können [eine solche Umgebung erstellen](https://docs.microsoft.com/power-platform/admin/create-environment) , wenn Sie über die entsprechenden Berechtigungen verfügen.

## <a name="download-the-solution"></a>Herunterladen der Lösung

> [!div class="nextstepaction"]
> [Herunterladen der Projektmappen-Datei für Northwind Traders](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

Diese [Projektmappendatei](../../developer/common-data-service/introduction-solutions.md) (ZIP-Datei) enthält die Definitionen von Entitäten, Options Sätzen und Geschäftsprozessen. der Canvas und Modell gesteuerte apps und alle anderen Elemente, die zusammen verwendet werden.

## <a name="install-the-solution"></a>Installieren der Lösung

1. Melden Sie sich bei [powerapps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)an, und stellen Sie sicher, dass Sie in einer Umgebung arbeiten, die eine Common Data Service-Datenbank enthält.

1. Klicken Sie im linken Navigationsbereich auf Projektmappen **, und wählen Sie dann**in der Symbolleiste oben auf dem Bildschirm **importieren** aus:

    > [!div class="mx-imgBorder"]
    > ![projektmappenansicht und Import-Solution Entry Point @ no__t-1

1. Wählen Sie auf der Seite **Lösungspaket auswählen** die Option **Durchsuchen**aus.

    > [!div class="mx-imgBorder"]
    > ![seite Projektmappenpaket auswählen, bevor Package ausgewählt ist @ no__t-1

1. Suchen Sie die heruntergeladene Datei, und wählen Sie dann **Öffnen**aus.

    Die Datei befindet sich in Ihrem Downloadordner, es sei denn, Sie haben einen anderen Speicherort ausgewählt.

1. Wenn Sie über die richtige Datei verfügen (die Versionsnummer kann variieren), klicken Sie auf **weiter**:

    > [!div class="mx-imgBorder"]
    > ![seite Projektmappenpaket auswählen, nachdem das Paket ausgewählt wurde @ no__t-1

1. Wählen Sie auf der Seite projektmappeninformationen die Option **weiter** aus, wenn der Name der Projekt Mappe und der Verleger korrekt sind.

    > [!div class="mx-imgBorder"]
    > Seite "![projektmappeninformationen" @ no__t-1

1. Wählen Sie auf der Seite **Importoptionen die Option** **importieren** aus, um die für das Beispiel erforderliche SDK-Nachrichtenverarbeitung zu bestätigen:

    > [!div class="mx-imgBorder"]
    > Seite "![import Options" @ no__t-1

    Eine andere Seite wird angezeigt und zeigt den Fortschritt bei der Installation der Projekt Mappe in den nächsten Minuten:

    > [!div class="mx-imgBorder"]
    > ![fortschritts Leiste @ no__t-1

    Wenn die Installation abgeschlossen ist, wird auf der ursprünglichen Seite das Ergebnis angezeigt:

    > [!div class="mx-imgBorder"]
    > ![projektmappenseite wird importiert @ no__t-1

1. Klicken Sie auf **Schließen**.

## <a name="load-the-sample-data"></a>Laden der Beispiel Daten

1. Wählen Sie **apps**aus, und wählen Sie dann **Northwind-Beispiel Daten**aus.

    Warten Sie einige Minuten, wenn die Northwind-apps nicht unmittelbar nach der Installation der Lösung angezeigt werden:

    > [!div class="mx-imgBorder"]
    > ![northwind-Datenbank in der Liste der apps @ no__t-1

1. Wenn die APP die Berechtigung zum interagieren mit Common Data Service anfordert, wählen Sie **zulassen**:

    > [!div class="mx-imgBorder"]
    > Dialogfeld "![consent" für Common Data Service @ no__t-1

1. Nachdem die App geladen und angezeigt wird, dass die Beispiel Entitäten keine Datensätze enthalten, wählen Sie **Daten laden** , um die Entitäten aufzufüllen:

    > [!div class="mx-imgBorder"]
    > Schaltfläche "![load Data" in Sample Data Manager @ no__t-1

    Wenn die APP die Daten lädt, werden die Punkte über den oberen Rand der APP und die Anzahl der Datensätze vergrößert.

    Entitäten werden in einer bestimmten Reihenfolge geladen, damit Beziehungen zwischen Datensätzen hergestellt werden können. Beispielsweise verfügt die Entität **Order Details** über eine n:1-Beziehung zu den Entitäten **Orders** und **Order Products** , die zuerst geladen werden.

    Sie können den Prozess jederzeit abbrechen, indem Sie " **Abbrechen**" auswählen, und Sie können die Daten jederzeit entfernen, indem Sie **Daten entfernen**auswählen:

    > [!div class="mx-imgBorder"]
    > ![sample Data Manager beim Laden von Daten @ no__t-1

    Wenn das Laden der Daten abgeschlossen ist, wird die letzte Zeile (m:n-Beziehungen) als **abgeschlossen**angezeigt, und die Schaltflächen **Daten laden** und **Daten entfernen** werden erneut aktiviert:

    > [!div class="mx-imgBorder"]
    > ![sample Data Manager, nachdem die Daten geladen wurden @ no__t-1

## <a name="sample-apps"></a>Beispiel-Apps

Die Northwind-Lösung umfasst diese apps für die Interaktion mit diesen Daten:

- Northwind-Bestellungen (Canvas)
- Northwind-Bestellungen (Modell gesteuert)

Sie öffnen diese apps auf die gleiche Weise, wie Sie die app in der vorherigen Prozedur geöffnet haben.

### <a name="canvas"></a>Zeichenbereich

Diese Einzel Bildschirm-App bietet eine einfache Master-Detail-Ansicht der **Orders** -Entität, in der Sie eine Zusammenfassung der Reihenfolge und der einzelnen Zeilen Elemente für eine Bestellung anzeigen und bearbeiten können. Eine Liste der Bestellungen wird am linken Rand angezeigt, und Sie können einen Pfeil in der Liste auswählen, um eine Zusammenfassung und die Details dieser Bestellung anzuzeigen. Weitere Informationen finden Sie unter: [Übersicht über die Canvas-App für Northwind Traders](northwind-orders-canvas-overview.md).

> [!div class="mx-imgBorder"]
> ![liste der Bestellungen und Details in der Northwind Canvas-App @ no__t-1

### <a name="model-driven"></a>Modellgesteuert

Diese APP arbeitet mit denselben Daten (in der Entität **Orders** ) als Canvas-app. Zeigen Sie in der Liste der Bestellungen Weitere Informationen zu einem Auftrag an, indem Sie die zugehörige Nummer auswählen:

> [!div class="mx-imgBorder"]
> ![liste der Bestellungen in der Modell gesteuerten Northwind-App @ no__t-1

Eine Zusammenfassung der Reihenfolge wird in einer separaten Form angezeigt:

> [!div class="mx-imgBorder"]
> Details zur ![order in der Modell gesteuerten App @ no__t-1

Wenn Sie einen Bildlauf nach unten durchführen, werden die gleichen Zeilen Elemente wie in der Canvas-App angezeigt:

> [!div class="mx-imgBorder"]
> ![weitere Bestelldetails in der Modell gesteuerten App @ no__t-1

## <a name="do-it-yourself"></a>Selbst ausführen

Eine Schritt-für-Schritt-Anleitung zum Erstellen der Canvas-APP, die weiter oben in diesem Thema gezeigt wird, finden Sie unter.  Die Anweisungen sind in drei Teile unterteilt:

1. [Erstellen Sie eine Order Gallery](northwind-orders-canvas-part1.md).
1. [Erstellen Sie ein Zusammenfassungs Formular](northwind-orders-canvas-part2.md).
1. [Erstellen Sie eine Detail Galerie](northwind-orders-canvas-part3.md).

Wenn Sie fortfahren möchten, enthält die Lösung eine Startpunkt-App für jeden Teil.  Suchen Sie in der Liste der apps nach **Northwind Orders (Canvas)-BEGIN Part 1** usw.

[In dieser Übersicht über die APP](northwind-orders-canvas-overview.md) werden die Benutzeroberfläche, Datenquellen und die Verwendung von Beziehungen erläutert.

> [!div class="nextstepaction"]
> [Beginnen Sie mit dem Lesen der Übersicht.](northwind-orders-canvas-overview.md)
