---
title: Fügen Sie in Common Data Service Daten einer Entität hinzu, indem Sie Power Query verwenden | Microsoft Docs
description: Schrittweise Anweisungen für die Verwendung von Power Query, um Daten einer neuen oder vorhandenen Entität aus einer anderen Datenquelle in Common Data Service hinzuzufügen.
author: mllopis
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 03/21/2018
ms.author: millopis
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 923797d7781ef64da4193d0114d50a3bda6b0b66
ms.sourcegitcommit: 86c81c9efb105d11f4def49eef823af6c69059a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2020
ms.locfileid: "3027353"
---
# <a name="add-data-to-an-entity-in-common-data-service-by-using-power-query"></a>Daten mithilfe von Power Query zu einer Entität in Common Data Service hinzufügen
In dieser Vorgehensweise erstellen Sie eine Entität in [Common Data Service](data-platform-intro.md) und befüllen diese Entität mit Daten aus einem OData-Feed, indem Sie Power Query verwenden. Sie können dieselben Techniken verwenden, um Daten aus diesen Online- und lokalen Quellen zu integrieren, unter anderem:

* SQL Server
* Salesforce
* IBM DB2
* Zugriff
* Excel
* Web-APIs
* OData-Feeds
* Textfelder

Sie können Daten auch filtern, transformieren und kombinieren, bevor Sie sie in eine neue oder vorhandene Entität laden.

Sofern Sie keine Lizenz für Power Apps haben, können Sie sich hier [kostenlos anmelden](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Voraussetzungen
Bevor Sie beginnen, diesem Thema zu folgen:
- Wechseln Sie zu einer [Umgebung](../canvas-apps/working-with-environments.md), in der Sie Entitäten erstellen können.
- Sie müssen eine Power Apps pro Benutzerplan oder Power Apps pro App Plan haben.

## <a name="specify-the-source-data"></a>Angeben der Quelldaten

1. Melden Sie sich in [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und klicken oder tippen Sie auf den Abwärtspfeil für **Daten** neben dem linken Rand.

    ![Power Apps Homepage](./media/data-platform-cds-newentity-pq/sign-in.png)

1. Klicken oder tippen Sie in der Liste, die angezeigt wird, auf **Datenintegration** und klicken oder tippen Sie auf **Neues Projekt** neben der oberen rechten Ecke des Fensters.

1. Klicken oder tippen Sie in der Datenquellenliste auf **OData**.

    ![Auswählen eines OAuth-Konnektors](./media/data-platform-cds-newentity-pq/choose-odata.png)

1. Geben Sie unter **Verbindungseinstellungen** diese URL ein oder fügen Sie sie ein, und wählen Sie dann **Weiter** aus:<br>
`https://services.odata.org/V4/Northwind/Northwind.svc/`

1. In der Tabellenliste aktivieren Sie das Kontrollkästchen **Kunden** aus, und klicken oder tippen Sie dann auf **Weiter**.

    ![Auswählen der Kundentabelle](./media/data-platform-cds-newentity-pq/select-table.png)

1. (Optional) Ändern Sie das Schema passend für Ihre Anforderungen, indem Sie die einzuschließenden Spalten auswählen und so die Tabelle auf eine oder mehrere Arten zu transformieren, einen Index oder eine bedingte Spalte hinzufügen, oder andere Änderungen vorzunehmen.

1. Klicken oder tippen Sie in der unteren rechten Ecke auf **Weiter**.

## <a name="specify-the-target-entity"></a>Angeben der Zielentität
1. Wählen Sie unter **Einstellungen laden** auf **Zur neuen Entität laden** aus.

    ![Angeben des Namens der neuen Entität](./media/data-platform-cds-newentity-pq/new-entity-name.png)

    Sie können der neuen Entität einen anderen Namen oder Anzeigenamen geben, die Standardwerte jedoch belassen, um diesem Lernprogramm genau zu folgen.

1. In der Liste **Primäres Namensfeld** klicken oder tippen Sie auf **ContactName** und dann auf **Weiter** in der rechten unteren Ecke.

    Sie können ein anderes Primär-Namenfeld angeben, eine andere Spalte in der Quelltabelle für jedes Feld in der Entität zuordnen, die Sie erstellen, oder beides. Sie können auch angeben, ob Textspalten in der Abfrageausgabe als mehrzeiliger Text oder einzeiliger Text im Common Data Service erstellt werden sollen. Um diesem Lernprogramm genau zu folgen, belassen Sie die Standardspaltenzuordnung.

1. Wenn der **Ladestatus** **Abgeschlossen** ist, wählen Sie **Fertig** in der rechten unteren Ecke aus.

1. Unter **Daten** (neben dem linken Rand) wählen Sie **Entitäten** aus, um die Liste der Entitäten in der Datenbank anzuzeigen.

    Die **Kunden**-Entität, die Sie in einem OData-Feed erstellt haben, wird als benutzerdefinierte Entität angezeigt.

    ![Liste des Standard- sowie der angepassten Entitäten](./media/data-platform-cds-newentity-pq/entity-list.png)

> [!WARNING]
> Wenn Sie Power Query verwenden, um Daten einer vorhandenen Entität hinzuzufügen, werden alle Daten in dieser Entität überschrieben.

Wenn Sie **In vorhandene Entität laden** auswählen, können Sie eine Entität angeben, der die Daten aus der Tabelle **Kunden** hinzugefügt werden. Sie können die Daten beispielsweise der Entität **Firma** hinzufügen, mit der Common Data Service bereitgestellt wird. In der **Quellspalte** können Sie genauer angeben, dass die Daten in der Spalte **ContactName** aus der Tabelle **Kunden** der Spalte **Name** in der **Firmen**-Entität hinzugefügt werden sollen.

![Angeben des Namens der neuen Entität](./media/data-platform-cds-newentity-pq/existing-entity.png)

Wir freuen über diese Funktion und sehen Ihrem Feedback entgegen. Bitte [senden Sie uns Ihre Vorschläge und Ihr Feedback](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) zu dieser Funktion!

Bei einer [Fehlermeldung zu Berechtigungen](data-platform-cds-newentity-troubleshooting-mashup.md) wenden Sie sich an Ihren Administrator.

> [!WARNING]
> Es gibt ein Limit von 500.000 Zeilen pro Ausführung und pro Projekt, die mithilfe dieses Features geladen werden können.
