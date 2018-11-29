---
title: Abfragen erstellen mit LINQ (.NET language-integrated query) (Common Data Service for Apps) | Microsoft Docs
description: 'Lesen Sie, wie Sie.NET Language-Integrated Query (LINQ) verwenden, um Abfragen in Common Data Service for Apps zu schreiben.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="build-queries-with-linq-net-language-integrated-query"></a>Erstellen von Abfragen mit LINQ (.NET language-integrated query)

Sie können .NET Language-Integrated Query (LINQ) verwenden, um Abfragen in Common Data Service for Apps zu schreiben. Sie können die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>-Klasse oder eine Ableitungsklasse verwenden, die mit dem CrmSvcUtil-Tool erstellt wurden, um [LINQ](https://msdn.microsoft.com/library/bb397897.aspx)-Abfragen zu schreiben, die auf den SOAP-Endpunkt (Organization.svc) zugreifen. Die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>-Klasse enthält einen zugrundeliegenden LINQ-Abfragenanbieter, der LINQ-Abfragen aus dem Visual C#- oder Visual Basic .NET-Syntax in die von CDS for Apps verwendeten Abfrage-API übersetzt.  
  
 Wenn Sie Programmierklassen mit früher Bindung verwenden, können Sie eine Klasse generieren, die aus der <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>-Klasse abgeleitet wird,, wenn Sie den Namen der Klasse mithilfe des **servicecontextname**-Parameters angeben, wenn Sie das Codegenerierungs-Tool (CrmSvcUtil.exe) verwenden. Der Einsatz dieser Klasse ermöglicht den Verweis auf einen [IQueryable](https://msdn.microsoft.com/library/system.linq.iqueryable.aspx)-Entitätssatz, der das `<entity schema name>+Set`-Muster verwendet, beispielsweise **AccountSet**, um auf die Sammlung von `Account`-Entitätsdatensätzen zu verweisen. Alle Beispiele im CDS for Apps-Webdienst verwenden **ServiceContext** als Namen für diese Klasse, aber Ihr Code verwendet möglicherweise einen anderen Namen. Weitere Informationen: [Entitätsklassen mit früher Bindung mit dem Codegenerierungstool erstellen (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool.md). 
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden von LINQ zum Erstellen einer Abfrage](use-linq-construct-query.md)  
  
 [Verwenden von Entitätsklassen mit später Bindung mit einer LINQ-Abfrage](use-late-bound-entity-class-linq-query.md)  
  
 [Verwenden der Entitäts-Suchattribute mit LINQ](order-results-entity-attributes-linq.md)  
  
 [Bestellergebnisse mithilfe von LINQ der Entitätsattributen](/dynamics365/customer-engagement/developer/org-service/order-results-entity-attributes-linq)  
  
 [Auslagern von umfangreichen Ergebnissätzen mit LINQ](/dynamics365/customer-engagement/developer/org-service/page-large-result-sets-linq)  
  
 [LINQ-Abfragebeispiele](/dynamics365/customer-engagement/developer/org-service/linq-query-examples)  
  
 [Beispiel: Erstellen einer LINQ-Abfrage](/dynamics365/customer-engagement/developer/org-service/sample-create-linq-query)  
  
 [Beispiel: LINQ-Abfragenbeispiele](/dynamics365/customer-engagement/developer/org-service/sample-complex-linq-queries)  
  
 [Beispiel: RetrieveMultiple mit Bedingungsoperatoren, die LINQ verwenden](/dynamics365/customer-engagement/developer/org-service/sample-retrieve-multiple-with-condition-operators-using-linq)  
  
 [Beispiel: Weitere LINQ-Abfragenbeispiele](/dynamics365/customer-engagement/developer/org-service/sample-more-linq-query-examples)  
  
 [Beispiel: Verwenden von LINQ mit später Bindung](/dynamics365/customer-engagement/developer/org-service/sample-create-linq-query-late-binding)