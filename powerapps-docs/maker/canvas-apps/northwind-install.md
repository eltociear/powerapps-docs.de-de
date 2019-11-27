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
ms.openlocfilehash: dca5d5189129e7c9dfe32d27fb4c1190b830c039
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541334"
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

Diese [](../../developer/common-data-service/introduction-solutions.md) Projektmappendatei (ZIP-Datei) enthält die Definitionen von Entitäten, Options Sätzen und Geschäftsprozessen. der Canvas und Modell gesteuerte apps und alle anderen Elemente, die zusammen verwendet werden.

## <a name="install-the-solution"></a>Installieren der Lösung

1. Melden Sie sich bei [powerapps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)an, und stellen Sie sicher, dass Sie in einer Umgebung arbeiten, die eine Common Data Service-Datenbank enthält.

1. Klicken Sie im linken Navigationsbereich auf Projektmappen **, und wählen Sie dann**in der Symbolleiste oben auf dem Bildschirm **importieren** aus:

    > [!div class="mx-imgBorder"]
    > ![Lösungs Ansicht und Import-Solution-Einstiegspunkt](media/northwind-install/solution-import.png)

1. Wählen Sie auf der Seite **Lösungspaket auswählen** die Option **Durchsuchen**aus.

    > [!div class="mx-imgBorder"]
    > ![Seite Projektmappenpaket auswählen, bevor Paket ausgewählt wird](media/northwind-install/select-solution2.png)

1. Suchen Sie die heruntergeladene Datei, und wählen Sie dann **Öffnen**aus.

    Die Datei befindet sich in Ihrem Downloadordner, es sei denn, Sie haben einen anderen Speicherort ausgewählt.

1. Wenn Sie über die richtige Datei verfügen (die Versionsnummer kann variieren), klicken Sie auf **weiter**:

    > [!div class="mx-imgBorder"]
    > ![Seite Projektmappenpaket auswählen, nachdem Paket ausgewählt wurde](media/northwind-install/confirm-solution2.png)

1. Wählen Sie auf der Seite projektmappeninformationen die Option **weiter** aus, wenn der Name der Projekt Mappe und der Verleger korrekt sind.

    > [!div class="mx-imgBorder"]
    > ![Seite "Lösungs Informationen"](media/northwind-install/confirm-publisher.png)

1. Wählen Sie auf der Seite **Importoptionen die Option** **importieren** aus, um die für das Beispiel erforderliche SDK-Nachrichtenverarbeitung zu bestätigen:

    > [!div class="mx-imgBorder"]
    > ![Seite "Import Optionen"](media/northwind-install/confirm-sdk.png)

    Eine andere Seite wird angezeigt und zeigt den Fortschritt bei der Installation der Projekt Mappe in den nächsten Minuten:

    > [!div class="mx-imgBorder"]
    > ![Statusanzeige](media/northwind-install/solution-progress.png)

    Wenn die Installation abgeschlossen ist, wird auf der ursprünglichen Seite das Ergebnis angezeigt:

    > [!div class="mx-imgBorder"]
    > ![Projekt Mappe wird importiert](media/northwind-install/solution-success.png)

1. Klicken Sie auf **Schließen**.

## <a name="load-the-sample-data"></a>Laden der Beispiel Daten

1. Wählen Sie **apps**aus, und wählen Sie dann **Northwind-Beispiel Daten**aus.

    Warten Sie einige Minuten, wenn die Northwind-apps nicht unmittelbar nach der Installation der Lösung angezeigt werden:

    > [!div class="mx-imgBorder"]
    > ![Northwind-Datenbank in der Liste der apps](media/northwind-install/sample-data-app.png)

1. Wenn die APP die Berechtigung zum interagieren mit Common Data Service anfordert, wählen Sie **zulassen**:

    > [!div class="mx-imgBorder"]
    > Dialogfeld "![Zustimmung" für Common Data Service](media/northwind-install/sample-data-permission.png)

1. Nachdem die App geladen und angezeigt wird, dass die Beispiel Entitäten keine Datensätze enthalten, wählen Sie **Daten laden** , um die Entitäten aufzufüllen:

    > [!div class="mx-imgBorder"]
    > ![Schaltfläche "Daten laden" in Beispiel Data Manager](media/northwind-install/sample-data-load.png)

    Wenn die APP die Daten lädt, werden die Punkte über den oberen Rand der APP und die Anzahl der Datensätze vergrößert.

    Entitäten werden in einer bestimmten Reihenfolge geladen, damit Beziehungen zwischen Datensätzen hergestellt werden können. Beispielsweise verfügt die Entität **Order Details** über eine n:1-Beziehung zu den Entitäten **Orders** und **Order Products** , die zuerst geladen werden.

    Sie können den Prozess jederzeit abbrechen, indem Sie " **Abbrechen**" auswählen, und Sie können die Daten jederzeit entfernen, indem Sie **Daten entfernen**auswählen:

    > [!div class="mx-imgBorder"]
    > ![Beispiel Data Manager beim Laden von Daten](media/northwind-install/sample-data-progress.png)

    Wenn das Laden der Daten abgeschlossen ist, wird die letzte Zeile (m:n-Beziehungen) als **abgeschlossen**angezeigt, und die Schaltflächen **Daten laden** und **Daten entfernen** werden erneut aktiviert:

    > [!div class="mx-imgBorder"]
    > ![Beispiel Data Manager nach dem Laden der Daten](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>Beispiel-Apps

Die Northwind-Lösung umfasst diese apps für die Interaktion mit diesen Daten:

- Northwind-Bestellungen (Canvas)
- Northwind-Bestellungen (Modell gesteuert)

Sie öffnen diese apps auf die gleiche Weise, wie Sie die app in der vorherigen Prozedur geöffnet haben.

### <a name="canvas"></a>Zeichenbereich

Diese Einzel Bildschirm-App bietet eine einfache Master-Detail-Ansicht der **Orders** -Entität, in der Sie eine Zusammenfassung der Reihenfolge und der einzelnen Zeilen Elemente für eine Bestellung anzeigen und bearbeiten können. Eine Liste der Bestellungen wird am linken Rand angezeigt, und Sie können einen Pfeil in der Liste auswählen, um eine Zusammenfassung und die Details dieser Bestellung anzuzeigen. Weitere Informationen finden Sie unter: [Übersicht über die Canvas-App für Northwind Traders](northwind-orders-canvas-overview.md).

> [!div class="mx-imgBorder"]
> ![Liste der Bestellungen und Details in der Northwind Canvas-App](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>Modellgesteuert

Diese APP arbeitet mit denselben Daten (in der Entität **Orders** ) als Canvas-app. Zeigen Sie in der Liste der Bestellungen Weitere Informationen zu einem Auftrag an, indem Sie die zugehörige Nummer auswählen:

> [!div class="mx-imgBorder"]
> ![Liste der Bestellungen in der Modell gesteuerten App Northwind](media/northwind-install/orders-model.png)

Eine Zusammenfassung der Reihenfolge wird in einer separaten Form angezeigt:

> [!div class="mx-imgBorder"]
> ![Bestelldetails in Modell gesteuerte App](media/northwind-install/orders-model-2.png)

Wenn Sie einen Bildlauf nach unten durchführen, werden die gleichen Zeilen Elemente wie in der Canvas-App angezeigt:

> [!div class="mx-imgBorder"]
> ![weitere Bestelldetails in Modell gesteuerte App](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>Selbst ausführen

Eine Schritt-für-Schritt-Anleitung zum Erstellen der Canvas-APP, die weiter oben in diesem Thema gezeigt wird, finden Sie unter.  Die Anweisungen sind in drei Teile unterteilt:

1. [Erstellen Sie eine Order Gallery](northwind-orders-canvas-part1.md).
1. [Erstellen Sie ein Zusammenfassungs Formular](northwind-orders-canvas-part2.md).
1. [Erstellen Sie eine Detail Galerie](northwind-orders-canvas-part3.md).

Wenn Sie fortfahren möchten, enthält die Lösung eine Startpunkt-App für jeden Teil.  Suchen Sie in der Liste der apps nach **Northwind Orders (Canvas)-BEGIN Part 1** usw.

[In dieser Übersicht über die APP](northwind-orders-canvas-overview.md) werden die Benutzeroberfläche, Datenquellen und die Verwendung von Beziehungen erläutert.

> [!div class="nextstepaction"]
> [Beginnen Sie mit dem Lesen der Übersicht.](northwind-orders-canvas-overview.md)
