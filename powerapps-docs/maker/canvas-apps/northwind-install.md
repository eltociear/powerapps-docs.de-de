---
title: Installieren von Northwind Trader-Datenbank und apps | Microsoft-Dokumentation
description: Installieren Sie die Northwind-Datenbank und die apps in einer Umgebung mit relationale Konzepten vertraut zu machen.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 351f9fd4fe369b3073a9edfb0158883140f50693
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761026"
---
# <a name="install-northwind-traders-database-and-apps"></a>Installieren von Northwind Trader-Datenbank und apps

Anhand der Schritte in [dieser Reihe von Themen](northwind-orders-canvas-part1.md), Konzepte zu relationalen Daten können Sie ermitteln, wie Sie in einer Beispieldatenbank in Common Data Service implementiert. Sie können auch untersuchen, Business-Beispiel-apps, beide canvas und modellgesteuerte, für die Verwaltung von Daten und Sammeln Sie praktische Erfahrungen, indem Sie eine solche Anwendung zu erstellen. Dieser erste Thema wird erläutert, wie die Datenbank Northwind Traders in Ihrer Umgebung installieren, und erhalten Zugriff auf die Beispiel-apps, die Sie öffnen können, für die Bearbeitung, um anzuzeigen, wie diese erstellt wurden.

Northwind Traders ist eine fiktive Organisation, die Bestellungen, Produkte, Kunden, Lieferanten und viele andere Aspekte von einem kleinen Unternehmen verwaltet. Dieses Beispiel mit den ersten Versionen von Microsoft Access angezeigt und ist weiterhin verfügbar, wie eine Vorlage für den Zugriff.

## <a name="prerequisites"></a>Voraussetzungen

- Eine PowerApps-Lizenz, die von Common Data Service unterstützt. Sie können [verwenden Sie eine kostenlose Testversion](../signup-for-powerapps.md) für 30 Tage.
- Eine Umgebung mit einer Common Data Service-Datenbank. Sie können [Erstellen einer solchen Umgebung](https://docs.microsoft.com/power-platform/admin/create-environment) Wenn Sie die entsprechenden Berechtigungen verfügen.

## <a name="download-the-solution"></a>Laden Sie die Lösung

> [!div class="nextstepaction"]
> [Laden Sie die Projektmappendatei für Northwind Traders](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

Dies [Lösung](../../developer/common-data-service/introduction-solutions.md) -Datei (.zip) enthält die Definitionen von Entitäten, Optionssätze und Geschäftsprozesse, im Zeichenbereich und modellgesteuerten apps; und alle anderen Elemente, die zusammen verwendet werden.

## <a name="install-the-solution"></a>Installieren Sie die Projektmappe

1. Melden Sie sich beim [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), und stellen Sie sicher, dass Sie in einer Umgebung arbeiten, die eine Common Data Service-Datenbank enthält.

1. Wählen Sie im linken Navigationsbereich **Lösungen**, und wählen Sie dann **Import** auf der Symbolleiste am oberen Rand des Bildschirms:

    > [!div class="mx-imgBorder"]
    > ![Lösungen anzeigen und Importieren einer Projektmappe Einstiegspunkt](media/northwind-install/solution-import.png)

1. In der **Lösungspaket wählen** Seite **Durchsuchen**.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie Lösungspaket-Seite aus, bevor das Paket ausgewählt ist](media/northwind-install/select-solution2.png)

1. Suchen Sie die Datei, die Sie heruntergeladen haben, und wählen Sie dann **öffnen**.

    Wenn Sie einen anderen Speicherort ausgewählt haben, wird die Datei im Ordner "Downloads" sein.

1. Wenn Sie die richtige Datei haben (die Versionsnummer kann davon abweichen), wählen Sie **Weiter**:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie Seite für Pakete für Projektmappe aus, nach dem Paket ausgewählt ist](media/northwind-install/confirm-solution2.png)

1. In der **Lösungsinformationen** Seite **Weiter** Wenn der Name der Projektmappe und dem Verleger richtig sind.

    > [!div class="mx-imgBorder"]
    > ![Seite "Lösung Informationen"](media/northwind-install/confirm-publisher.png)

1. In der **Importoptionen** Seite **Import** auf SDK-Nachrichtenverarbeitung, vergewissern Sie sich die für dieses Beispiel müssen:

    > [!div class="mx-imgBorder"]
    > ![Importieren Sie die Seite "Optionen"](media/northwind-install/confirm-sdk.png)

    Eine andere Seite wird angezeigt, und es wird der Fortschritt während der Installation der Lösung für den nächsten Minuten:

    > [!div class="mx-imgBorder"]
    > ![Statusanzeige](media/northwind-install/solution-progress.png)

    Wenn die Installation abgeschlossen ist, zeigt die ursprüngliche Seite das Ergebnis an:

    > [!div class="mx-imgBorder"]
    > ![Importieren die Seite "Lösung"](media/northwind-install/solution-success.png)

1. Klicken Sie auf **Schließen**.

## <a name="load-the-sample-data"></a>Laden der Beispieldaten

1. Wählen Sie **Apps**, und wählen Sie dann **Northwind Beispieldaten**.

    Warten Sie einige Minuten, wenn die Northwind-apps nicht angezeigt werden unmittelbar nach der Installation der Lösung:

    > [!div class="mx-imgBorder"]
    > ![Northwind-Datenbank in der Liste der apps](media/northwind-install/sample-data-app.png)

1. Wenn die app die Berechtigung für die Interaktion mit Common Data Service verlangt wird, wählen Sie **zulassen**:

    > [!div class="mx-imgBorder"]
    > ![Stimmen Sie im Dialogfeld für Common Data Service](media/northwind-install/sample-data-permission.png)

1. Wählen Sie nach die app geladen und zeigt an, dass die Beispiel-Entitäten keine Datensätze enthalten, **Laden von Daten** um Entitäten aufzufüllen:

    > [!div class="mx-imgBorder"]
    > ![Laden Sie die Schaltfläche "Daten" im Sample Data Manager](media/northwind-install/sample-data-load.png)

    Wie die app die Daten lädt, März Punkte auf dem oberen Rand der app, und die Anzahl der Datensätze erhöht.

    Entitäten in einer bestimmten Reihenfolge geladen, sodass die Beziehungen zwischen den Datensätzen hergestellt werden können. Z. B. die **Bestelldetails** Entität verfügt über eine n: 1 Beziehung mit der **Bestellungen** und **Bestellprodukte** Entitäten, die zuerst geladen werden.

    Sie können den Prozess jederzeit abbrechen, indem Sie die Auswahl **Abbrechen**, und Sie können die Daten zu einem beliebigen Zeitpunkt entfernen, indem Sie die Auswahl **entfernen Daten**:

    > [!div class="mx-imgBorder"]
    > ![Sample Data Manager, wie die Daten geladen werden](media/northwind-install/sample-data-progress.png)

    Wenn die Daten vollständig geladen ist, die letzte Zeile (**viele-zu-viele-Beziehungen**) zeigt **Fertig**, und die **Laden von Daten** und **entfernen Daten** Schaltflächen werden erneut aktiviert werden:

    > [!div class="mx-imgBorder"]
    > ![Beispiel-Daten-Manager nach dem Laden von Daten](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>Beispiel-Apps

Die Northwind-Lösung umfasst diese apps für die Interaktion mit diesen Daten:

- Northwind Orders (Canvas)
- Northwind Orders (modellgesteuerte)

Sie öffnen diese apps auf die gleiche Weise, dass Sie die app im vorherigen Verfahren geöffnet.

### <a name="canvas"></a>Zeichenbereich

Dieser Bildschirm app bietet eine einfache Master / Detail-Ansicht der **Bestellungen** Entität können Sie anzeigen und bearbeiten eine Übersicht über die Reihenfolge und jedes Zeilenelement für eine Bestellung. Eine Liste der Aufträge, die am linken Rand angezeigt wird, und Sie können einen Pfeil auswählen, in der Liste aus, um eine Zusammenfassung und die zugehörigen Detailinformationen anzuzeigen. Weitere Informationen finden Sie unter: [Übersicht über das Canvas-app für Northwind Traders](northwind-orders-canvas-overview.md).

> [!div class="mx-imgBorder"]
> ![Liste der Bestellungen und Details in Northwind canvas-app](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>Modellgesteuert

Diese app greift auf dieselben Daten (in der **Bestellungen** Entität) wie die Canvas-app. Zeigen Sie in der Liste der Bestellungen Weitere Informationen zu einer Bestellung durch Auswählen der Anzahl:

> [!div class="mx-imgBorder"]
> ![Liste der Bestellungen in Northwind modellgesteuerten app](media/northwind-install/orders-model.png)

Auf einem separaten Formular wird eine Zusammenfassung des Auftrags angezeigt:

> [!div class="mx-imgBorder"]
> ![die Auftragsdetails in modellgesteuerten app](media/northwind-install/orders-model-2.png)

Wenn Sie im Formular nach unten scrollen, wird die gleiche Zeile Elemente wie die Canvas-app:

> [!div class="mx-imgBorder"]
> ![Weitere Auftragsdetails im modellgesteuerten app](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>Es selbst tun.

Sie können schrittweise Anleitungen zum Erstellen von Canvas-app, die weiter oben in diesem Thema folgen.  Die Anweisungen sind in drei Teile unterteilt:

1. [Erstellen eines Katalogs Reihenfolge](northwind-orders-canvas-part1.md).
1. [Erstellen Sie eine Zusammenfassung Formular](northwind-orders-canvas-part2.md).
1. [Erstellen Sie einen Katalog Detail](northwind-orders-canvas-part3.md).

Wenn Sie fortfahren möchten, enthält die Projektmappe eine Ausgangspunkt-app für die einzelnen Teile an.  Suchen Sie in der Liste der apps nach **Northwind Orders (Canvas) – Teil 1 beginnen** und so weiter.

Dies [Überblick über die app](northwind-orders-canvas-overview.md) wird erläutert, die Benutzer-Schnittstelle, Datenquellen und wie Beziehungen verwendet werden.

> [!div class="nextstepaction"]
> [Lesen Sie die Übersicht](northwind-orders-canvas-overview.md)
