---
title: Organisieren des Teams zur Entwicklung von Lösungen (Common Data Service für Apps) | Microsoft Docs
description: 'Dieses Dokument enthält einige Strategien, die verwendet werden, wenn mehrere Entwickler an derselben Lösung arbeiten'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="organize-your-team-to-develop-solutions"></a>Organisieren des Teams zum Entwickeln von Lösungen

Wenn mehrere Entwickler an derselben Lösung arbeiten müssen, sollten Sie möglicherweise eine Umgebung erstellen, in der jeder Entwickler Anpassungen erstellen kann, die die Arbeit der anderen Entwickler nicht behindern. Möglicherweise müssen Sie die Lösung auch aus der Entwicklungsumgebung in Testumgebungen und zu Umgebungen zum Testen der Benutzerakzeptanz (UAT) verschieben.  
  
<a name="BKMK_StrategiesForTeamDev"></a>   
## <a name="strategies-for-team-development"></a>Strategien für Teamentwicklung  
 Einige der Strategien zur Verwaltung von Teamentwicklung von Lösungen werden im Folgenden aufgeführt:  
  
-   [Einzelne Organisation: Eine Hauptlösung](organize-team-develop-solutions.md#BKMK_SingleOrgMasterSolution)  
  
-   [Einzelne Organisation: Mehrere Entwicklerlösungen + Hauptlösung](organize-team-develop-solutions.md#BKMK_SingleOrgMultipleDeveloper)  
  
-   [Eine Organisation pro Entwickler](organize-team-develop-solutions.md#BKMK_OneOrgPerDev)  
  
<a name="BKMK_SingleOrgMasterSolution"></a>   
### <a name="single-organization-one-master-solution"></a>Einzelne Organisation: Eine Hauptlösung  
 Mehrere Entwickler können bei einer einzelnen Organisation arbeiten; Sie müssen jedoch darauf achten, dass sie an anderen Komponenten arbeiten. Das ist einfacher, wenn zuvor alle erforderlichen verwalteten Lösungen (freigegebene Bibliotheken) installiert werden.  
  
<a name="BKMK_SingleOrgMultipleDeveloper"></a>   
### <a name="single-organization-multiple-developer-solutions--master-solution"></a>Einzelne Organisation: Mehrere Entwicklerlösungen + Hauptlösung  
 In einer einzelnen Organisation können Sie separate nicht verwaltete Lösungen für jeden Entwickler erstellen. Jede Lösung enthält ein Untersatz einer Hauptlösung. Jede Lösungskomponente ist nur in einer nicht verwalteten Lösung vorhanden. Entwickler fügen der nicht verwalteten Lösungen, die ihnen zugewiesen wird, keine vorhandene Lösungskomponente hinzu. Damit wird eine klare Trennung der Komponenten erreicht, die geändert werden. Es müssen keine Änderungen zusammengeführt werden, da jeder Entwicklungslösung einen Verweis auf Komponenten enthält, die in der Hauptlösung enthalten sind.  
  
<a name="BKMK_OneOrgPerDev"></a>   
### <a name="one-organization-per-developer"></a>Eine Organisation pro Entwickler  

 Jeder Entwickler kann an seiner eigenen Organisation arbeiten. Um Änderungen in CDS für Apps zu überprüfen, müssen sie die Lösung als nicht verwaltete Lösung exportieren. Die Lösung jeder Organisation eines Entwicklers wird dann in die Hauptlösung importiert. Verwenden Sie die, Hauptlösung um die verwaltete Lösung zu exportieren.  
  
<a name="BKMK_DeployingSolutionsFromDevThroughToProduction"></a>   
## <a name="deploy-solutions-from-development-through-test-and-production-environments"></a>Stellen Sie Lösungen aus der Entwicklung über Test- und Produktionsumgebungen bereit.  
 In den Entwicklungsorganisationen werden Lösungen in verschiedenen Test- und Bereitstellungsumgebungen zur Analyse bereitgestellt, bevor sie in einer Produktionsumgebung bereitgestellt werden. Das Whitepaper [Bereitstellen von Microsoft Dynamics CRM 2011 und CRM Online-Lösungen, von der Entwicklung bis zu Test- und Produktionsumgebungen](http://go.microsoft.com/fwlink/p/?LinkId=232288) untersucht, wie reale Dynamics 365-Lösungen über Test- und Produktionsumgebungen auf zuverlässige und wiederholbare Weise mithilfe von Automatisierung bereitgestellt werden. Das Whitepaper hebt zudem bestimmte Einschränkungen hervor, die vorhanden sind, wenn Sie Lösungen in CDS für Apps bereitstellen und testen.  
  
### <a name="see-also"></a>Siehe auch  
 [Planen für Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Ihre Lösungen modularisieren](organize-solutions.md)   
 [Whitepaper: Bereitstellen von Microsoft Dynamics 365 Customer Engagement und CRM Online-Lösungen von der Entwicklung bis zu Test- und Produktionsumgebungen](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=27824)