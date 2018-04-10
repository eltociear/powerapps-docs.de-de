---
title: Schnellstart für das Hinzufügen von Daten zu einer Entität in Common Data Service mithilfe von Power Query | Microsoft-Dokumentation
description: Schnellstart mit einer ausführlichen Anleitung zur Verwendung von Power Query zum Hinzufügen von Daten aus einer anderen Datenquelle zu einer neuen oder vorhandenen Entität in Common Data Service für Apps.
services: ''
suite: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: anneta
ms.openlocfilehash: def53153d3db75b0f56d7878324fa1391c8c58a8
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-add-data-to-an-entity-in-the-common-data-service-by-using-power-query"></a>Schnellstart: Hinzufügen von Daten zu einer Entität in Common Data Service mithilfe von Power Query
In diesem Verfahren erstellen Sie eine Entität in [Common Data Service für Apps](data-platform-intro.md) und füllen diese mithilfe von Power Query mit Daten aus einem OData-Feed auf. Sie können die gleichen Techniken verwenden, um Daten unter anderem aus diesen lokalen Quellen und Onlinequellen zu integrieren:

* SQL Server
* Salesforce
* IBM DB2
* Zugang
* Excel
* Web-APIs
* OData-Feeds
* Textdateien

Sie können Daten ebenfalls filtern, transformieren oder kombinieren, bevor Sie diese in eine neue oder vorhandene Entität laden.

Wenn Sie über keine Lizenz für PowerApps verfügen, können Sie sich [kostenlos registrieren](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Voraussetzungen
Sie müssen in eine [Umgebung](../canvas-apps/working-with-environments.md) wechseln, in der Sie Entitäten erstellen können, um diesem Artikel zu folgen.

## <a name="specify-the-source-data"></a>Angeben der Quelldaten

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an, und klicken oder tippen Sie am linken Rand auf den Pfeil nach unten für **Daten**.

    ![PowerApps-Startseite](./media/data-platform-cds-newentity-pq/sign-in.png)

1. Klicken oder tippen Sie in der angezeigten Liste auf **Datenintegration**, und klicken oder tippen Sie dann in der oberen rechten Ecke des Fensters auf **Neues Projekt**.

1. Klicken oder tippen Sie in der Liste der Datenquellen auf **OData**.

    ![Auswählen des OAuth-Connectors](./media/data-platform-cds-newentity-pq/choose-odata.png)

1. Geben oder fügen Sie diese URL unter **Verbindungseinstellungen** ein, und klicken Sie dann auf **Weiter**:<br>
`http://services.odata.org/V4/Northwind/Northwind.svc/`

1. Aktivieren Sie in der Liste der Tabellen das Kontrollkästchen **Kunden**, und klicken oder tippen Sie dann auf **Weiter**.

    ![Auswählen der Customers-Tabelle](./media/data-platform-cds-newentity-pq/select-table.png)

1. Optional: Ändern Sie das Schema entsprechend Ihren Anforderungen, indem Sie auswählen, welche Spalten eingefügt werden sollen, die Tabelle auf verschiedene Arten transformieren, einen Index oder bedingte Spalten hinzufügen oder andere Änderungen vornehmen.

1. Klicken oder tippen Sie in der unteren rechten Ecke auf **Weiter**.

## <a name="specify-the-target-entity"></a>Angeben der Zielentität
1. Klicken Sie unter **Einstellungen laden** auf **Load to new entity** (In neue Entität laden).

    ![Angeben des Namens der neuen Entität](./media/data-platform-cds-newentity-pq/new-entity-name.png)

    Sie können der neuen Entität einen anderen Namen oder Anzeigenamen geben. Behalten Sie jedoch die Standardwerte bei, um dieses Tutorial genau befolgen zu können.

1. Klicken oder tippen Sie in der Liste **Primäres Namensfeld** auf **ContactName**, und klicken oder tippen Sie in der unteren rechten Ecke auf **Weiter**.

    Sie können ein anderes primäres Namensfeld angeben, jedem Feld in der von Ihnen erstellten Entität eine andere Spalte in der Quelltabelle zuordnen oder beides tun. Behalten Sie die Standardzuordnung für Spalten bei, um dieses Tutorial genau befolgen zu können.

1. Wenn der **Ladestatus** **Abgeschlossen** anzeigt, klicken Sie in der unteren rechten Ecke auf **Fertig**.

1. Klicken Sie in der Nähe des linken Rands unter **Daten** auf **Entitäten**, um die Liste der Entitäten in Ihrer Datenbank anzuzeigen.

    Die **Customers**-Entität, die Sie aus einem OData-Feed erstellt haben, wird als benutzerdefinierte Entität angezeigt.

    ![Liste der Standardentitäten und benutzerdefinierten Entitäten](./media/data-platform-cds-newentity-pq/entity-list.png)

> [!WARNING]
> Wenn Sie Power Query für das Hinzufügen von Daten zu einer vorhandenen Entität verwenden, werden alle Daten in dieser Entität überschrieben.

Wenn Sie **Load to existing entity** (In vorhandene Entität laden) auswählen, können Sie eine Entität angeben, zu der Sie die Daten der **Customers**-Tabelle hinzufügen möchten. Sie könnten die Daten beispielsweise zur Entität **Account** hinzufügen, die in Common Data Service enthalten ist. Unter **Quellspalte** können Sie zudem angeben, dass die Daten in der Spalte **ContactName** der Tabelle **Customers** zur Spalte **Name** der Entität **Accounts** hinzugefügt werden sollen.

![Angeben des Namens der neuen Entität](./media/data-platform-cds-newentity-pq/existing-entity.png)

Wir halten diese neue Funktionalität für sehr hilfreich und würden uns über Ihr Feedback freuen. Bitte [senden Sie uns Ihre Vorschläge und Ihr Feedback](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) zu dieser Funktion.

