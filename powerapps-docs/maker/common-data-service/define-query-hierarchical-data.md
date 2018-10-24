---
title: Definieren und Abfragen hierarchischer Daten mit Common Data Service für Apps | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie hierarchiebezogene Daten definiert und abgefragt werden können.
ms.custom: ''
ms.date: 06/02/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
ms.openlocfilehash: 4dad7da635156350d104d68108ac4acfbb991862
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682633"
---
# <a name="define-and-query-hierarchically-related-data"></a>Definieren und Abfragen von hierarchiebezogenen Daten

Sie können wertvolle Geschäftsinformationen gewinnen, indem Sie hierarchiebezogene Daten definieren und abfragen. Die hierarchischen Modellierungs- und Visualisierungsfunktionen bieten Ihnen eine Reihe von Vorteilen:  
  
- Anzeigen und Untersuchen von komplexen hierarchischen Informationen  
- Anzeigen von Key Performance Indicators (KPIs) in der kontextbezogenen Ansicht einer Hierarchie  
- Visuelles Analysieren von wichtigen Informationen über das Web und die Tablets  
  
Für einige Standardentitäten sind bereits Hierarchien definiert. Andere Entitäten, einschließlich benutzerdefinierter Entitäten, können für eine Hierarchie aktiviert werden, und Sie können Visualisierungen für diese erstellen. 

## <a name="define-hierarchical-data"></a>Definieren von hierarchischen Daten

Bei Common Data Service für Apps werden hierarchische Datenstrukturen durch *auf sich selbst verweisende* 1:n-Beziehungen der verknüpften Datensätze unterstützt. 

> [!NOTE]
> *Auf sich selbst verweisend* bedeutet, dass die Entität mit sich selbst verknüpft ist. Die Firmenentität beispielsweise enthält ein Suchfeld, um es einem anderen Entitätsfirmendatensatz zuzuordnen.

Bei einer auf sich selbst verweisenden 1:n-Beziehung ist die Option **Hierarchisch** in der Beziehungsdefinition verfügbar, die auf **Ja** festgelegt werden kann.

![Hierarchische Einstellung in der Beziehungsdefinition](media/self-referential-relationship-car-solution-explorer.png)

Um die Daten als Hierarchie abzufragen, müssen Sie auf sich selbst verweisende 1:n-Beziehungen der Entität als hierarchisch festlegen. Dies kann nur über den Lösungs-Explorer erfolgen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Gehen Sie zum Aktivieren der Hierarchie wie folgt vor:  
  
1. Wählen Sie beim [Anzeigen von 1:n-Beziehungen](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships) die auf sich selbst verweisende Beziehung aus, die Sie bearbeiten möchten.
2. Legen Sie in der **Beziehungsdefinition** für **Hierarchisch** die Einstellung **Ja** fest.  
  
> [!NOTE]
> - Einige integrierte 1:n-Beziehungen sind nicht anpassbar. Dadurch wird verhindert, dass diese Beziehungen als hierarchisch festgelegt werden.  
> - Sie können eine hierarchische Beziehung für die Systembeziehungen angeben, die auf sich selbst verweisen. Hierzu zählen die auf sich selbst verweisenden 1:n-Beziehungen des Systemtyps, wie etwa die Beziehung „contact_master_contact“.  

> [!IMPORTANT]
> Sie können über mehrere auf sich selbst verweisende Beziehungen verfügen, jedoch kann nur eine Beziehung pro Entität als hierarchische Beziehung definiert werden. Wenn Sie versuchen, die einmal angewendete Einstellung zu ändern, wird folgende Warnung angezeigt:
>
> - **Bei Deaktivierung**: Wenn Sie die Hierarchieeinstellung für diese Beziehung deaktivieren, funktionieren die Rollupdefinitionen, Prozesse und Ansichten, die diese Hierarchie verwenden, nicht. Möchten Sie fortfahren? 
> - **Bei Aktivierung**: Wenn Sie die Hierarchieeinstellung für diese Beziehung aktivieren, werden alle Rollupdefinitionen, Prozesse und Ansichten, die die vorhandene Hierarchie verwenden, ungültig. Möchten Sie fortfahren?
>
> Wenn Sie sicher sind, dass keine anderen Abhängigkeiten zu der vorhandenen Hierarchie bestehen, sollten Sie die Dokumentation zur Bereitstellung lesen oder sich mit anderen Anpassern besprechen, um in Erfahrung zu bringen, wie die vorhandene hierarchische Beziehung verwendet wird, bevor Sie fortfahren.

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>Abfragen von hierarchischen Daten  

Ohne eine definierte Hierarchie müssen Sie zum Abrufen von hierarchischen Daten iterativ die verknüpften Datensätze abfragen. Mit einer definierten Hierarchie können Sie die verknüpften Daten als Hierarchie in einem Schritt abfragen. Mit der Logik **Unter** und **Nicht unter** können Sie Datensätze abfragen. Die hierarchischen Operatoren **Unter** und **Nicht unter** werden in der erweiterten Suche und im Workflow-Editor verfügbar gemacht. Weitere Informationen zur Verwendung dieser Operatoren finden Sie unter [Konfigurieren von Workflowphasen und -schritten](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions). Weitere Informationen zur erweiterten Suche finden Sie unter [Erstellen, Bearbeiten oder Speichern einer erweiterten Suche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  

> [!NOTE]
> Entwickler können diese Operatoren ebenfalls im Code verwenden. Weitere Informationen finden Sie unter [Abfragen von hierarchischen Daten](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data).
  
Die folgenden Beispiele veranschaulichen Szenarien zum Abfragen von Hierarchien:  
  
### <a name="query-account-hierarchy"></a>Abfragen der Firmenhierarchie  
  
![Abfragen von Firmen in der Firmenhierarchie](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>Abfragen der Firmenhierarchie, einschließlich der damit verbundenen Aktivitäten  
  
![Abfragen von verknüpften Aktivitäten der Firma](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>Abfragen der Firmenhierarchie, einschließlich der damit verbundenen Verkaufschancen  
  
![Abfragen von verknüpften Verkaufschancen der Firma](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>Siehe auch 
[Erstellen von 1:n- oder n:1-Entitätsbeziehungen – Übersicht](create-edit-1n-relationships.md)<br />
[Erstellen und Bearbeiten von 1:n- oder n:1-Entitätsbeziehungen mit dem Lösungs-Explorer](create-edit-1n-relationships-solution-explorer.md)<br />
[Visualisieren hierarchischer Daten mit modellgesteuerten Apps](visualize-hierarchical-data.md)<br />
[Video: Modellierung hierarchischer Sicherheitsmodelle](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07) (in englischer Sprache)<br />
[Video: Visualisierung von Hierarchien](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07) (in englischer Sprache)
