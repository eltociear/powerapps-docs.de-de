---
title: Übersicht über die Canvas-App für Northwind Traders | Microsoft-Dokumentation
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48966659ca12ada12448543492731fff8431fbde
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995816"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Übersicht über die Canvas-App für Northwind Traders

Erfahren Sie mehr über die Canvas-App zum Verwalten von relationalen Daten in der Northwind Traders-Datenbank, die Sie [in Ihrer Umgebung installiert](northwind-install.md)haben. Befolgen Sie dann die Schritt-für-Schritt-Anweisungen in den nachfolgenden Themen, um diese APP von Grund auf neu zu erstellen. Dadurch erhalten Sie praktische Erfahrungen mit relationalen Daten.

In diesem Thema finden Sie Folgendes:

- Gibt an, wie ein App-Benutzer relationale Daten in der APP anzeigt und verwaltet.
- Welche Datentypen die App steuern.
- Gibt an, wie Beziehungen zwischen diesen Datentypen erstellt wurden.

Auf einem einzelnen Bildschirm kann der App-Benutzer Aufträge anzeigen, aktualisieren, erstellen und löschen.

> [!div class="mx-imgBorder"]
> ![complete Canvas-App @ no__t-1

## <a name="explore-the-user-interface"></a>Erkunden Sie die Benutzeroberfläche

### <a name="order-gallery"></a>Order Gallery

Am linken Rand der APP wird in einem Katalog eine Liste der Bestellungen angezeigt, einschließlich der Bestellnummer, des Status, des Namens des Kunden und der Gesamtkosten der Bestellung. Der Benutzer kann einen Bildlauf durch die Liste durchführen, um nach einer Bestellung zu suchen und dann weitere Informationen anzuzeigen, indem er den Pfeil der Bestellung auswählt. Weitere Informationen finden Sie unter: [Erstellen Sie die Order Gallery](northwind-orders-canvas-part1.md).

### <a name="summary-form"></a>Zusammenfassungs Formular

In der oberen rechten Ecke fasst ein Formular die Reihenfolge zusammen, die der Benutzer in der Order Gallery ausgewählt hat. Die Zusammenfassung enthält viele der gleichen Informationen wie der Katalog, aber in der Zusammenfassung werden auch die Datumsangaben, zu denen die Bestellung erstellt und bezahlt wurde, sowie der Name und das Bild des Mitarbeiters angezeigt, der die Bestellung verwaltet hat. Der Benutzer kann die Daten im Formular ändern, diese Änderungen speichern, Abbrechen oder den Auftrag löschen, indem er am rechten Rand der Titelleiste ein Symbol auswählt. Weitere Informationen finden Sie unter: [Erstellen Sie das Zusammenfassungs Formular](northwind-orders-canvas-part2.md).

### <a name="detail-gallery"></a>Detail Galerie

In der unteren rechten Ecke werden in einer anderen Galerie Informationen zu den Produkten, die in der ausgewählten Bestellung enthalten sind, und in den Mengen angezeigt. Jedes Element in diesem Katalog wird als Bestelldetails bezeichnet. Der App-Benutzer kann alle Elemente in diesem Katalog mithilfe von Steuerelementen in und darunter hinzufügen und löschen. Weitere Informationen finden Sie unter: [Erstellen Sie die Detail Galerie](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![definition von Bildschirm Bereichen @ no__t-1

## <a name="explore-the-data-sources"></a>Untersuchen der Datenquellen

Zum Erstellen dieser APP zeigen Sie Daten aus fünf Entitäten und einen Options Satz an. Tatsächlich zeigen die meisten Bereiche dieser APP Daten aus mehreren Entitäten an. Die Bestell Galerie enthält z. b. folgende Informationen:

- Die Bestellnummer ist ein Feld in der Entität **Orders** .
- Der Status ist ein anderes Feld in der Entität " **Orders** ", eine Option aus der Option " **Auftragsstatus** ".
- Der Kunden Name ist ein Feld in der **Customers** -Entität.
- Die Gesamtkosten werden basierend auf den Daten in der Entität **Order Details** berechnet.

Die Zusammenfassung enthält einige der gleichen Informationen wie die Liste der Bestellungen, enthält jedoch auch den Namen und das Bild des Mitarbeiters, der die Bestellung verwaltet hat. Diese Informationen werden aus Feldern **in der Employee** -Entität abgerufen. Die Detail Galerie zeigt Datensätze in der Entität **Order Details** an, und jedes Produkt in diesen Details ist ein Datensatz in der Entität **Order Products** .

## <a name="explore-the-relationships"></a>Untersuchen der Beziehungen

Sie können Daten aus verschiedenen Quellen (z. b. Entitäten) im gleichen Katalog oder Formular anzeigen, da diese Entitäten Beziehungen aufweisen, die für Sie in der Datenbank erstellt wurden.

### <a name="many-to-one-relationships"></a>N:1-Beziehungen

Beispielsweise befinden sich Informationen zum Kunden und zum Mitarbeiter für die einzelnen Bestellungen in den Entitäten **Customers** und **Employees** . Daher verfügt die Entität **Orders** über eine n:1-Beziehung zu diesen Entitäten, da viele Aufträge vorhanden sind, die jeweils nur von einem Kunden platziert und nur von einem Mitarbeiter verwaltet werden können.

Jede Bestellung verfügt auch über ein oder mehrere Zeilen Elemente, die die in der Bestellung enthaltenen Produkte und ihre Mengen darstellen. Jedes Zeilen Element ist ein Datensatz in der Entität " **Order Details** ", der Informationen zu jedem Produkt aus der Entität " **Order Products** " abruft. Jedes Detail identifiziert nur ein Produkt, aber jedes Produkt kann in mehreren Details angezeigt werden. Daher verfügt die Entität **Order Details** über eine n:1-Beziehung zu der Entität **Order Products** .

### <a name="one-to-many-relationships"></a>1: n-Beziehungen

Jede Bestellung kann mehrere Zeilen Elemente enthalten, aber jedes Zeilen Element bezieht sich nur auf eine Bestellung. Daher verfügt die Entität " **Orders** " über eine 1: n-Beziehung mit der Entität " **Order Details** ".

### <a name="dot-notation-for-relationships"></a>Punkt Notation für Beziehungen 

Zum Anzeigen von Daten auf der Grundlage einer Beziehung zwischen Entitäten können Sie mithilfe der Punkt Eigenschaften Auswahl eine Beziehung zwischen einer Entität und einer anderen Entität durchlaufen.  Beispielsweise ruft jeder Datensatz in der **Orders** -Entität Informationen aus der **Customers** -Entität ab, sodass der Order Gallery die Kundennamen anzeigen kann. In diesem Katalog konfigurieren Sie dieses Verhalten, indem Sie die **Text** -Eigenschaft einer Bezeichnung auf diesen Ausdruck festlegen:<br>`ThisItem.Customer.Company`

**Thisitem** gibt einen Datensatz in der **Orders** -Entität an und ruft Informationen von der **Customers** -Entität über den Kunden ab, der die Bestellung aufgegeben hat. In diesem Fall gibt der Ausdruck an, dass der Unternehmens Name des Kunden angezeigt wird. Allerdings wird der gesamte Datensatz für diesen Kunden abgerufen, sodass Sie so einfach eine e-Mail-Adresse für diesen Kunden anzeigen können.

Als weiteres Beispiel für das Durchlaufen von einer Entität zu einem anderen können Sie angeben, dass ein Katalogdaten Sätze in einer Entität basierend auf einem Datensatz anzeigen soll, den der Benutzer in einem anderen Katalog ausgewählt hat und der sich in einer anderen Entität befindet. Um die Bestelldetails anzuzeigen, legen Sie die **Items** -Eigenschaft des Detail Katalogs auf den folgenden Ausdruck fest:<br>`Gallery1.Selected.'Order Details'`

In diesem Fall gibt **Gallery1. Selected** einen Datensatz in der Entität **Orders** an, genau wie **thisitem** im vorherigen Beispiel. Mit diesem Ausdruck wird jedoch nicht nur ein Datensatz abgerufen, wie der vorherige Ausdruck bereits getan hat. Stattdessen wird eine gesamte Tabelle mit Datensätzen abgerufen, um den Namen und die Kosten pro Einheit für jedes Produkt (wie in der Entität **Order Products** ) und die Menge (wie in der **Order Details** -Entität dargestellt) anzuzeigen.

## <a name="do-it-yourself"></a>Selbst ausführen

Befolgen Sie die Schritt-für-Schritt-Anweisungen, um die Canvas-app "Northwind Orders" zu erstellen.  Die Anweisungen sind in drei Teile unterteilt:

1. [Erstellen Sie eine Order Gallery](northwind-orders-canvas-part1.md).
1. [Erstellen Sie ein Zusammenfassungs Formular](northwind-orders-canvas-part2.md).
1. [Erstellen Sie eine Detail Galerie](northwind-orders-canvas-part3.md).

Wenn Sie fortfahren möchten, enthält die Lösung eine Startpunkt-App für jeden Teil.  Suchen Sie in der Liste der apps nach **Northwind Orders (Canvas)-BEGIN Part 1** usw.

> [!div class="nextstepaction"]
> [Fortfahren durch Erstellen der Order Gallery](northwind-orders-canvas-part1.md)
