---
title: Eingeschränkte Entitäten, die Dynamics 365-Lizenzen erfordern | Microsoft-Dokumentation
description: Hier finden Sie eine Liste der eingeschränkten Entitäten in Common Data Service (CDS) für Apps, die Dynamics 365-Lizenzen erfordern.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 05/01/2018
ms.author: clwesene
ms.openlocfilehash: 79b6e386154b15ae6c625afbebbed18a8a86c420
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
---
# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>Eingeschränkte Entitäten, die Dynamics 365-Lizenzen erfordern
App-Ersteller können die meisten in Common Data Service (CDS) für Apps verfügbaren Entitäten verwenden, um Apps und Flows für Benutzer zu erstellen, die über eine PowerApps Plan 1-Lizenz verfügen. Es gibt jedoch einige Entitäten, die komplexe Unternehmenslogik enthalten, die erfordern, dass Benutzer über eine Lizenz von PowerApps Plan 2 oder Microsoft Flow Plan 2 verfügen (weitere Informationen erhalten Sie in den [Lizenzanforderungen für Entitäten](data-platform-entity-licenses.md)). Einige wenige Entitäten, die mit Dynamics 365-Produkten verknüpft sind, erfordern, dass Benutzer von Canvas- und modellgesteuerten Apps über eine Lizenz für das entsprechende Dynamics 365-Produkt verfügen, wenn sie Datensätze in den Entitäten erstellen, aktualisieren oder löschen müssen. Aus diesem Grund spricht man von *eingeschränkten* Entitäten.

Wenn Entitäten auf eine Dynamics 365-Lizenz eingeschränkt sind, kann das folgende Gründe haben:

* Die Entität wird verwendet, um produktspezifische Konfigurationsdaten zu speichern und zu verwalten, die normalerweise nicht außerhalb der Anwendung verwendet werden.
* Die Entität enthält komplexe Logik, die Daten auf bestimmte Weise erstellt und verwaltet, wenn sie in einem Dynamics 365-Produkt verwendet wird.

Wenn eine App oder ein Flow nur Informationen in einer Entität liest, ist keine Dynamics 365-Lizenz erforderlich sondern nur eine entsprechende PowerApps- oder Microsoft Flow-Lizenz. 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>Eingeschränkte Entitäten zum Erstellen, Aktualisieren und Löschen
In der folgenden Tabelle werden die eingeschränkten Entitäten und die entsprechend erforderlichen Dynamics 365-Lizenzen für PowerApps- und Microsoft Flow-App-Benutzer aufgelistet, die in den Entitäten gespeicherte Daten erstellen, aktualisieren und löschen. 

|Einrichtung  |Logischer Name  |Erforderliche Lizenz  |
|---------|---------|---------|
Actual |msdyn_actual |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Agreement Business Process |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Booking journal | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Booking Setup Metadata | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Booking timestamp | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Case to Work Order Business Process |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Konfiguration |msdyn_configuration |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Entitlement | entitlement | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Estimate Line|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Estimate|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Fact|msdyn_fact |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Field service setting |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Field Service System Job |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Goal | goal | Dynamics 365 for Sales Professional, <br>**oder** Dynamics 365 for Sales, Enterprise Edition, <br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Incident | incident | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Inventory Journal |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Invoice Process |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Journey | journey | Dynamics 365 for Marketing <br> **oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Knowledge article | knowledgearticle | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Organizational Unit |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Product Inventory |msdyn_productinventory |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Project Parameter|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Project Stages| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Project Task Dependency|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Project Task|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Project Team Member|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Purchase Order Business Process | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Resource Assignment Detail (Deprecated)|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Resource Assignment|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Resource Restriction (Deprecated) |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Routing rule set | routingrule | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Schedule Board Setting |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Scheduling Parameter |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
SLA| sla | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
System User Scheduler Setting |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Transaction Connection|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Transaction Origin|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Transaction Type|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Unique Number|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Work Order Business Process |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan
Work Order Details Generation Queue (Veraltet)|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**oder** der Dynamics 365 Customer Engagement Plan <br> **oder**  der Dynamics 365 Plan

## <a name="licensing"></a>Lizenzierung
Weitere Informationen zu PowerApps- und Dynamics 365-Lizenzen finden Sie unter [Licensing overview (Übersicht über die Lizenzierung)](../../administrator/pricing-billing-skus.md).

