---
title: Definieren und Abfragen von hierarchischen Daten Common Data Service | MicrosoftDocs
description: 'Erfahren Sie, wie Sie hierarchiebezogene Daten festlegen und abfragen'
ms.custom: ''
ms.date: 06/02/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-and-query-hierarchically-related-data"></a>Hierarchiebezogene Daten festlegen und abfragen

Sie können wertvolle Unternehmenseinblicke erhalten, indem Sie hierarchisch verknüpften Daten festlegen und Abfragen. Die hierarchischen Modellierungs- und Visualisierungsfähigkeiten bieten Ihnen eine Reihe von Vorteilen:  
  
- Anzeigen und Durchsuchen komplexer hierarchischer Informationen.  
- Anzeigen von Key Performance Indicators (KPIs) in der Kontextansicht einer Hierarchie.  
- Visuelles Analysieren wichtiger Informationen über das Internet und die Tablets hinweg.  
  
Einige Standardobjekte haben bereits Hierarchien definiert. Andere Entitäten, einschließlich benutzerdefinierter Entitäten, können für eine Hierarchie aktiviert werden, und Sie können die Visualisierungen für diese erstellen. 

## <a name="define-hierarchical-data"></a>Definieren Sie hierarchische Daten

Mit Common Data Service werden hierarchische Datenstrukturen durch auf *sich selbst verweisende* Eins-zu-Viele (1: n)-Beziehungen der verknüpften Datensätze unterstützt. 

> [!NOTE]
> *Auf sich selbst verweisen* bedeutet, dass die Entität mit sich selbst verknüpft ist. Beispielsweise enthält die Firmenentität ein Suchfeld, um sie einem anderen Firmenentitätsdatensatz zuzuweisen.

Wenn in der Beziehungsdefinition eine auf sich selbst verweisende eins zu viele (1:N)-Beziehung vorhanden ist, kann die Option **Hierarchisch** auf **Ja** festgelegt werden.

![Hierarchische Einstellung in der Beziehungsdefinition](media/self-referential-relationship-car-solution-explorer.png)

Um die Daten als Hierarchie abzufragen, müssen Sie die auf sich selbst verweisenden Eins-zu-Viele (1:N)-Beziehungen als hierarchisch festlegen. Dies ist nur mit dem Projektmappen-Explorer möglich.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

So aktivieren Sie die Hierarchie  
  
1. Während dem [Anzeigen von 1:N-Beziehungen](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships) wählen Sie die sich selbst verweisende Beziehung aus, die Sie bearbeiten möchten.
2. In **Beziehungsdefinition** legen Sie **Hierarchisch** auf **Ja** fest.  
  
> [!NOTE]
> - Einige der standardmäßigen (1:N)-Beziehungen können nicht angepasst werden. Dieses hindert Sie, diese Beziehungen als hierarchisch festzulegen.  
> - Sie können eine hierarchische Beziehung für die auf sich selbst verweisenden Beziehungen des Systems festlegen. Hierzu zählen die auf sich selbst verweisenden 1:n-Beziehungen vom Systemtyp, beispielsweise die "contact_master_contact"-Beziehung.  

> [!IMPORTANT]
> Sie können mehrere auf sich selbst verweisende Beziehungen haben, aber nur eine Beziehung pro Entität kann als hierarchische Beziehung definiert werden. Wenn Sie versuchen, die Einstellung nach der Übernahme zu ändern, erhalten Sie eine Warnung:
>
> - **Bei Deaktivierung:** Falls Sie die Hierarchieeinstellung für diese Beziehung deaktivieren, funktionieren keine Rollupdefinitionen, Prozesse und Ansichten, die diese Hierarchie verwenden. Möchten Sie fortfahren? 
> - **Bei Aktivierung:** Falls Sie die Hierarchieeinstellung für diese Beziehung aktivieren, werden alle Rollupdefinitionen ungültig, die die vorhandene Hierarchie verwenden. Möchten Sie fortfahren?
>
> Sofern Sie nicht sicher sind, dass es keine weiteren Abhängigkeiten auf der vorhandenen Hierarchie gibt, sollten Sie in einer beliebigen Dokumentation zur Bereitstellung nachschlagen oder sich an die Systemanpasser wenden, um nachvollziehen zu können, wie die vorhandene hierarchische Beziehung verwendet wird, bevor Sie fortfahren.

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>Abfragen von hierarchischen Daten  

Ohne eine definierte Hierarchie müssen hierarchische Daten die verknüpften Datensätze iterativ abfragen, um abgerufen zu werden. Bei einer definierten Hierarchie können Sie verknüpfte Daten in einem Schritt als Hierarchie abfragen. Sie können nach Entitätsdatensätzen abfragen, indem Sie die **Unter** und **Nicht Unter**-Logik verwenden. Die hierarchischen Operatoren **Unter** und **Nicht unter** werden in der erweiterten Suche und im Workfloweditor verfügbar gemacht. Weitere Informationen zum Verwenden dieser Operatoren finden Sie unter [Konfigurieren von Workflowschritten](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions). Weitere Information zur erweiterten Suche finden Sie unter [Erstellen, Bearbeiten oder Speichern einer erweiterten Suche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  

> [!NOTE]
> Entwickler können diese Operatoren auch im Code verwenden. Weitere Informationen: [Entwicklerdokumentation: Hierarchische Daten abfragen](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data).
  
Die folgenden Beispiele illustrieren Szenarien für das Abfragen von Hierarchien:  
  
### <a name="query-account-hierarchy"></a>Firmenhierarchie abfragen  
  
![Firmen in der Firmenhierarchie abfragen](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>Firmenhierarchie abfragen, einschließlich verwandter Aktitvitäten  
  
![Zugehörige Aktivitäten der Firma abfragen](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>Firmenhierarchie abfragen, einschließlich verwandter Geschäftschancen  
  
![Zugehörige Verkaufschancen der Firma abfragen](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>Siehe auch 
[Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](create-edit-1n-relationships.md)<br />
[Erstellen oder Bearbeiten von 1: N (1: n- oder n: n) Entitätsbeziehungen 1 mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)<br />
[Visualisierung hierarchischer Daten mit modellgesteuerten Apps](visualize-hierarchical-data.md)<br />
[Video: Hierarchische Sicherheitsmodellierung](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)<br />
[Video: Hierarchievisualisierung in](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
