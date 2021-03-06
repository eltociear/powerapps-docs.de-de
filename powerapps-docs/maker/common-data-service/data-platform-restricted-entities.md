---
title: Eingeschränkte Entitäten, die Dynamics 365-Lizenzen benötigen | Microsoft Docs
description: Eine Liste der eingeschränkten Entitäten in Common Data Service, die Dynamics 365-Lizenzen benötigen.
author: KumarVivek
ms.service: powerapps
ms.topic: reference
ms.date: 04/15/2020
ms.author: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9656f9db1a00fe82a2788b20513014bc49a09d4f
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "3264926"
---
# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>Eingeschränkte Entitäten, die Dynamics 365-Lizenzen benötigen

> [!IMPORTANT]
> Dieses Thema ist veraltet und wird in Kürze aktualisiert, um die neuesten Lizenzierungsänderungen zu berücksichtigen, die ab dem 1. Oktober 2019 gelten. Aktuelle Informationen zu den Lizenzbestimmungen für Unternehmen finden Sie im [Power Apps Lizenzhandbuch](https://go.microsoft.com/fwlink/p/?linkid=2085130).

App-Ersteller können die meisten der in Common Data Service verfügbaren Entitäten verwenden, um Apps und Abläufe für Benutzer zu erstellen, die nur eine Power Apps Plan 1-Lizenz haben. Einige Entitäten enthalten jedoch eine komplexe Geschäftslogik, die erfordert, dass App-Benutzer eine Power Apps Plan 2 oder Power Automate Plan 2 Lizenz haben (für weitere Informationen siehe [Entitäts-Lizenzanforderungen](data-platform-entity-licenses.md)). Ein noch kleinere Gruppe von Entitäten, die zu Dynamics 365-Produkten gehören, erfordern von Canvas und modellgesteuerte App-Benutzern, dass sie eine Lizenz für das jeweilige Dynamics 365-Produkt haben, wenn sie Datensätzen in Entitäten erstellen, aktualisieren oder löschen. Diese Elemente werden als *eingeschränkte* Entitäten bezeichnet.

Entitäten werden möglicherweise durch eine Dynamics 365-Lizenz aus folgenden Gründen beschränkt:

* Die Entität wird verwendet, um produktspezifische Konfigurationsdaten zu speichern und zu verwalten, die in der Regel nicht außerhalb der Anwendung verwendet wird.
* Die Entität wird von erweiterter Logik begleitet, die Daten auf eine bestimmte Art erstellt und verwaltet, wenn sie in einem Dynamics 365-Produkt verwendet wird.

Wenn eine App oder ein Flow nur Informationen von einer Entität liest, ist eine Dynamics 365-Lizenz nicht erforderlich und eine entsprechende Power Apps oder Power Automate Lizenz ist alles, was erforderlich ist. 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>Eingeschränkte Entitäten für Erstellen-, Aktualisieren- und Löschvorgänge
Die folgende Tabelle listet die eingeschränkten Entitäten und die damit verbundenen Dynamics 365-Lizenzanforderungen für Power Apps und Power Automate App-Benutzer auf, die innerhalb der Entitäten gespeicherte Daten erstellen, aktualisieren oder löschen. 

|Entität  |Logischer Name  |Lizenz erforderlich  |
|---------|---------|---------|
Tatsächlich |msdyn_actual |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Vereinbarungsgeschäftsprozess |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Buchungsjournal | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Buchungssetupmetadaten | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Buchungszeitstempel | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Anfrage | incident | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Anfrage an Arbeitsauftrags-Geschäftsprozess |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Konfiguration |msdyn_configuration |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Berechtigung | Anspruch | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Vorkalkulationsposition|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Schätzung|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Fakt|msdyn_fact |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Field Service-Einstellung |Msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Field Service-Systemauftrag |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Ziel | goal | Dynamics 365 for Sales Professional, <br>**oder** Dynamics 365 for Sales, Enterprise Edition, <br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Bestandsjournal |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Rechnungsprozess |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Kontaktverlauf | Kontaktverlauf | Dynamics 365 for Marketing <br> **oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Wissensartikel | knowledgearticle | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Organisationseinheit |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Produktbestand |msdyn_productinventory |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Projektparameter|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Projektphasen| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Abhängigkeit der Projektaufgaben|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Projektaufgabe|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Projektteammitglied|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Bestellungsgeschäftsprozess | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Ressourcenzuweisungsdetail (veraltet)|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Ressourcenzuweisung|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Ressourcenbeschränkung (veraltet) |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Routingregelsatz | routingrule | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Zeitplanübersichtseinstellung |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Planungsparameter |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
SLA| sla | Dynamics 365 for Customer Service, Enterprise Edition <br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Systembenutzerplanereinstellung |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **oder** Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Transaktionsverbindung|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Transaktionsursprung|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Transaktionstyp|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Eindeutige Nummer|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Arbeitsauftrags-Geschäftsprozess |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan
Warteschlange für Arbeitsauftrags-Detailgenerierung (Veraltet)|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**oder** Dynamics 365 Customer Engagement Plan <br> **oder** Dynamics 365-Plan

## <a name="licensing"></a>Lizenzierung
Weitere Informationen zu Power Apps und Dynamics 365 Lizenzen finden Sie auf der Seite [Lizenzübersicht](../../administrator/pricing-billing-skus.md).

