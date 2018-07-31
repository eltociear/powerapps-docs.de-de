---
title: Komplexe Entitäten, die PowerApps Plan 2-Lizenzen erfordern | Microsoft-Dokumentation
description: Hier finden Sie eine Liste der komplexen Entitäten in Common Data Service (CDS) für Apps, die eine PowerApps 2-Lizenzen erfordern.
author: clwesene
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 07/17/2018
ms.author: clwesene
ms.openlocfilehash: 76c101f35e236ac6bf037d2b5b748ca1b943d61d
ms.sourcegitcommit: efea7ed5ad8e80c87ba423fb094fa94b4e864d75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39266259"
---
# <a name="complex-entities-and-licensing"></a>Komplexe Entitäten und Lizenzierung
Entitäten, die folgende komplexe serverseitige Logik enthalten, erfordern, dass die Benutzer einer App oder eines Flows, die diese Entitäten verwenden, über eine Lizenz für PowerApps-Plan 2 oder Microsoft Flow-Tarif 2 verfügen:

* Code-Plug-ins. Weitere Informationen: [Plug-in-Entwicklung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development)
* Echtzeitworkflows. Weitere Informationen: [Workflowprozesse](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)

    > [!IMPORTANT]
    >  Nur Workflows, die in einen Echtzeitworkflow konvertiert werden, werden als synchron und in Echtzeit ausgeführt betrachtet. Workflows, die im Hintergrund ausgeführt werden, können vom entsprechenden PowerApps-Plan weiterhin verwendet werden und erfordern keine zusätzlichen Lizenzen.

Überprüfen Sie die Liste der Plug-in-Assemblys und Workflows, die in Ihrer Umgebung konfiguriert sind, um zu ermitteln, ob Sie komplexe Geschäftslogiken zu Ihren Entitäten hinzugefügt haben.

## <a name="complex-entities-installed-with-dynamics-365"></a>Komplexe Entitäten, die mit Dynamics 365 installiert sind
Die folgende Tabelle listet Entitäten auf, die komplexe serverseitige Logik als Teil einer Dynamics 365-Anwendungsinstallation enthalten. Diese Liste dient als Leitfaden. Je nachdem, welche Dynamics 365-Anwendungen und -Versionen in Ihrer Umgebung installiert sind, kann die Liste der komplexen Entitäten variieren.

> [!NOTE]
>  Wenn Sie den Common Data Service verwenden und keine Dynamics 365-Anwendung oder Lösung eines Drittanbieters installiert haben, verfügt Ihre Umgebung nicht über Entitäten mit komplexer serverseitiger Logik.

* Konto
* Vereinbarung
* Agreement Booking Date
* Agreement Booking Incident
* Agreement Booking Product
* Agreement Booking Service
* Agreement Booking Service Task
* Agreement Booking Setup
* Agreement Invoice Date
* Agreement Invoice Product
* Agreement Invoice Setup
* Agreement Sub-Status
* Bookable Resource
* Bookable Resource Booking
* Bookable Resource Booking Header
* Bookable Resource Category
* Bookable Resource Category Assn
* Bookable Resource Characteristic
* Bookable Resource Group
* Booking Alert
* Booking Alert Status
* Booking Status
* Case
* Characteristic
* Competency Requirement (Deprecated)
* Competitor
* Kontakt
* Customer Asset
* Delegierung
* Expense
* Field Computation
* Field Service Price List Item
* Filter
* Follow
* Incident Type
* Incident Type Product
* Incident Type Service
* Incident Type Service Task
* Integration Job
* Integration Job Detail
* Inventory Adjustment
* Inventory Adjustment Product
* Inventory Transfer
* Invoice
* Invoice Frequency
* Invoice Line
* Invoice Line Detail
* Journal
* Journal Line
* Lead
* Note
* OData v4 Data Source
* Opportunity
* Opportunity Line
* Opportunity Line Detail
* Order
* Order Invoicing Product
* Order Invoicing Setup
* Order Line
* Payment
* Payment Detail
* Post Configuration
* Post Rule Configuration
* Postal Code
* Price List
* Price List Item
* Product
* Project
* Project Approval
* Project Contract Line Detail
* Project Contract Line Milestone
* Project Contract Line Resource Category
* Project Contract Line Transaction Category
* Project Parameter
* Project Stages
* Project Task Status User
* Project Team Member Sign-Up
* Purchase Order
* Purchase Order Bill
* Purchase Order Product
* Purchase Order Receipt
* Purchase Order Receipt Product
* Purchase Order Sub Status
* Queue Item
* Quote
* Quote Booking Incident
* Quote Booking Product
* Quote Booking Service
* Quote Booking Service Task
* Quote Booking Setup
* Quote Invoicing Product
* Quote Invoicing Setup
* Quote Line
* Quote Line Detail
* Quote Line Milestone
* Quote Line Resource Category
* Quote Line Transaction Category
* Quote Project Price List
* Rating Model
* Rating Value
* Requirement Characteristic
* Requirement Resource Category
* Requirement Resource Preference
* Requirement Status
* Resource Request
* Resource Requirement
* Resource Requirement Detail
* RMA
* RMA Product
* RMA Receipt
* RMA Receipt Product
* RMA Sub-Status
* Role competency requirement
* Role Price
* RTV
* RTV Product
* RTV Sub-Status
* Tax Code
* Tax Code Detail
* Time Entry
* Time Group
* Time Group Detail
* Time Off Request
* Transaction Category Price
* User
* Anzeigen
* Wall View
* Warehouse
* Work Order
* Work Order Incident
* Work Order Product
* Work Order Service
* Work Order Service Task
* Work Order Sub-Status
* Work template


## <a name="licensing"></a>Lizenzierung
Weitere Informationen zu PowerApps- und Dynamics 365-Lizenzen finden Sie auf der Seite [Übersicht über die Lizenzierung](../../administrator/pricing-billing-skus.md).

