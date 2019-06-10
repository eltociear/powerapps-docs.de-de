---
title: Übersicht über das Canvas-app für Northwind Traders | Microsoft-Dokumentation
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2f28b07f53646e6fbf5afc0b1510bd37e3262b8
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761049"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Übersicht über das Canvas-app für Northwind Traders

Erfahren Sie mehr über das Canvas-app für die Verwaltung von relationalen Daten in der Northwind Traders-Datenbank, die Sie [in Ihrer Umgebung installierten](northwind-install.md). Befolgen Sie dann die schrittweise Anweisungen in der nachfolgenden Themen zum Erstellen dieser app von Grund auf neu, und gewinnen praktische Erfahrung mit relationalen Daten.

In diesem Thema zu ermitteln:

- Wie app-Benutzer zeigt und relationale Daten in der app verwaltet.
- Welche Arten von Daten der app steuern.
- Wie Beziehungen zwischen diesen Typen von Daten erstellt wurden.

In einem Bildschirm der app-Benutzer anzeigen, aktualisieren, erstellen und Löschen von Aufträgen.

> [!div class="mx-imgBorder"]
> ![Vollständige Canvas-app](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>Untersuchen der Benutzeroberfläche

### <a name="order-gallery"></a>Order-Katalog

Am linken Rand der app zeigt ein Katalog eine Liste der Aufträge, z. B. die Bestellnummer, den Status, den Namen des Kunden und die Gesamtkosten für die Reihenfolge an. Der Benutzer kann einen Bildlauf in der Liste finden eine Bestellung, und klicken Sie dann weitere Informationen dazu anzeigen, die Reihenfolge der Pfeil. Weitere Informationen finden Sie unter: [Erstellen des Katalogs Reihenfolge](northwind-orders-canvas-part1.md).

### <a name="summary-form"></a>Übersichtsformular

In der oberen rechten Ecke sind eine Form die Reihenfolge, in der Benutzer im Katalog Reihenfolge ausgewählt zusammengefasst. Die Zusammenfassung enthält viele der gleichen Informationen wie diesem Katalog verfügt, aber die Zusammenfassung zeigt auch die Datumsangaben, wenn die Bestellung erstellt und bezahlt, sowie den Namen und das Bild des Mitarbeiters, der die Reihenfolge verwaltet wurde. Der Benutzer kann Ändern der Daten in das Formular, diese Änderungen speichern, diese stornieren oder löschen Sie die Bestellung durch ein Symbol neben dem rechten Rand der Titelleiste auswählen. Weitere Informationen finden Sie unter: [Erstellen Sie die Zusammenfassung Formular](northwind-orders-canvas-part2.md).

### <a name="detail-gallery"></a>Detail-Katalog

In der unteren rechten Ecke zeigt einen anderen Katalog Informationen über die Produkte, die die ausgewählte Bestellung enthält und in welchen Mengen. Jedes Element in dieser Katalog wird als ein auftragsdetailbereich bezeichnet. Der app-Benutzer kann hinzufügen und löschen ein Element in diesem Katalog mithilfe der Steuerelemente in und darunter. Weitere Informationen finden Sie unter: [Erstellen des Detail-Katalogs](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definition der Bildschirmbereiche](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>Untersuchen Sie die Datenquellen

Um diese app zu erstellen, zeigen Ihnen, Daten aus fünf Entitäten und eine Option festgelegt werden. In der Tat zeigen die meisten Bereiche des diese app Daten aus mehreren Entitäten. Die Order-Katalog enthält z. B. folgende Informationen:

- Die Bestellnummer ist ein Feld in der **Bestellungen** Entität.
- Der Status ist ein anderes Feld in der **Bestellungen** Entität, die eine Option aus der **Status der Bestellung** Optionssatz.
- Der Namen des Kunden ist ein Feld in der **Kunden** Entität.
- Die Gesamtkosten wird berechnet, basierend auf Daten in die **Bestelldetails** Entität.

Die Zusammenfassung enthält einige der Informationen, wie die Liste der Bestellungen, aber es enthält auch den Namen und das Bild des Mitarbeiters, der die Reihenfolge verwaltet. Dass die Informationen abgerufen werden, aus Feldern in der **Mitarbeiter** Entität. Zeigt die Details-Katalog die Datensätze in der **Order Details** Entität und jedes Produkt in die Details sind in einem Datensatz in die **Bestellprodukte** Entität.

## <a name="explore-the-relationships"></a>Die Beziehungen untersuchen

Sie können Daten aus verschiedenen Quellen (z. B. Entitäten) im selben Katalog oder Formular anzeigen, da die Entitäten, Beziehungen verfügen, die für Sie, in der Datenbank erstellt wurden.

### <a name="many-to-one-relationships"></a>N: 1 Beziehungen

Informationen zu den Kunden und der Mitarbeiter für jeden Auftrag befindet sich z. B. in der **Kunden** und **Mitarbeiter** Entitäten. Aus diesem Grund die **Bestellungen** Entität n: 1 Beziehungen mit diesen Entitäten verfügt, da es viele Bestellungen gibt, von denen jeder durch nur einen Kunden platziert und von nur einem Mitarbeiter verwaltet werden kann.

Jede Reihenfolge verfügt auch über, eine oder mehrere Positionen, die die Produkte darstellen, die den Auftrag enthält sowie deren Anzahl. Jedes Zeilenelement ist ein Datensatz in die **Bestelldetails** -Entität, die Ruft Informationen zu jedem Produkt aus der **Bestellprodukte** Entität. Jede Detail-identifiziert nur ein Produkt, aber jedes Produkt in mehreren Details angezeigt werden kann. Aus diesem Grund die **Bestelldetails** Entität verfügt über eine n: 1 Beziehung mit der **Bestellprodukte** Entität.

### <a name="one-to-many-relationships"></a>1: n Beziehungen

Jeder Auftrag kann mehrere Positionen enthalten, aber jedes Zeilenelement bezieht sich nur eine Bestellung. Aus diesem Grund die **Bestellungen** Entität verfügt über eine 1: n Beziehung mit der **Bestelldetails** Entität.

### <a name="dot-notation-for-relationships"></a>Punktierte Schreibweise für Beziehungen 

Um Daten basierend auf einer Beziehung zwischen Entitäten anzuzeigen, können Sie den Punktselektor-Eigenschaft, die über eine Beziehung von einer Entität zum andern.  Beispielsweise jeder Datensatz in die **Bestellungen** Entität zieht Informationen aus der **Kunden** Entität, damit die Order-Katalog den Namen der Kunden anzeigen kann. In diesem Katalog, konfigurieren Sie dieses Verhalten durch Festlegen der **Text** -Eigenschaft einer Bezeichnung auf den folgenden Ausdruck:<br>`ThisItem.Customer.Company`

**ThisItem** gibt einen Datensatz in die **Bestellungen** Entität und ruft Informationen aus der **Kunden** Entität über den Kunden, die Bestellung aufgegeben hat. In diesem Fall gibt den Ausdruck an, dass der Name des Kunden Unternehmen angezeigt wird. Jedoch der gesamte Datensatz für den Kunden per Pull abgerufen wird, damit Sie ganz einfach anzeigen können, z. B. eine e-Mail-Adresse für diesen Kunden stattdessen.

Ein weiteres Beispiel aus einer Entität in eine andere durchlaufen können Sie angeben, dass ein Katalog Datensätze in einer Entität, die basierend auf einem Datensatz, den der Benutzer, die in einen anderen Katalog ausgewählt und das ist in einer anderen Entität, anzeigen soll. Um die Auftragsdetails anzuzeigen, legen Sie die Details des Katalogs **Elemente** Eigenschaft auf den folgenden Ausdruck:<br>`Gallery1.Selected.'Order Details'`

In diesem Fall **Gallery1.Selected** gibt einen Datensatz in die **Bestellungen** Entität wie **ThisItem** wurde im vorherigen Beispiel. Dieser Ausdruck jedoch abrufen nicht nur einen Datensatz, wie der vorherige Ausdruck. Stattdessen bezieht es eine ganze Tabelle von Datensätzen, die die Namen und pro Einheit Kosten der einzelnen Produkte angezeigt (wie dargestellt in der **Bestellprodukte** Entität) und die Menge (wie dargestellt in der **Bestelldetails** Entität).

## <a name="do-it-yourself"></a>Es selbst tun.

Sie können schrittweise Anleitungen zum Erstellen von Northwind Orders-Canvas-app folgen.  Die Anweisungen sind in drei Teile unterteilt:

1. [Erstellen eines Katalogs Reihenfolge](northwind-orders-canvas-part1.md).
1. [Erstellen Sie eine Zusammenfassung Formular](northwind-orders-canvas-part2.md).
1. [Erstellen Sie einen Katalog Detail](northwind-orders-canvas-part3.md).

Wenn Sie fortfahren möchten, enthält die Projektmappe eine Ausgangspunkt-app für die einzelnen Teile an.  Suchen Sie in der Liste der apps nach **Northwind Orders (Canvas) – Teil 1 beginnen** und so weiter.

> [!div class="nextstepaction"]
> [Fortsetzen Sie, indem Sie den Order-Katalog erstellen](northwind-orders-canvas-part1.md)
