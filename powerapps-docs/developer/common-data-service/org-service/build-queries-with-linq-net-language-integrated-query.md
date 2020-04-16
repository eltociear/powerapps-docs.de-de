---
title: Erstellen von Abfragen mit LINQ (.NET language-integrated query) (Common Data Service) | Microsoft Docs
description: Lesen Sie, wie Sie .NET Language-Integrated Query (LINQ) verwenden, um Abfragen in Common Data Service zu schreiben.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e456078b8b49ceb53b28c3aab2165daa8577f440
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156110"
---
# <a name="build-queries-with-linq-net-language-integrated-query"></a>Erstellen von Abfragen mit LINQ (.NET language-integrated query)

Sie können .NET Language-Integrated Query (LINQ) zum Schreiben von Abfragen in Common Data Service verwenden. Sie können die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>-Klasse oder eine Ableitungsklasse verwenden, die mit dem CrmSvcUtil-Tool erstellt wurden, um [LINQ](https://msdn.microsoft.com/library/bb397897.aspx)-Abfragen zu schreiben, die auf den SOAP-Endpunkt (Organization.svc) zugreifen. Die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>-Klasse enthält einen zugrunde liegenden LINQ-Abfragenanbieter, der LINQ-Abfragen aus der Visual C#- oder Visual Basic .NET-Syntax in die von Common Data Service verwendete Abfrage-API übersetzt.  
  
 Wenn Sie Programmierklassen mit früher Bindung verwenden, können Sie eine Klasse generieren, die aus der <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>-Klasse abgeleitet wird,, wenn Sie den Namen der Klasse mithilfe des **servicecontextname**-Parameters angeben, wenn Sie das Codegenerierungs-Tool (CrmSvcUtil.exe) verwenden. Der Einsatz dieser Klasse ermöglicht den Verweis auf einen [IQueryable](https://msdn.microsoft.com/library/system.linq.iqueryable.aspx)-Entitätssatz, der das `<entity schema name>+Set`-Muster verwendet, beispielsweise **AccountSet**, um auf die Sammlung von `Account`-Entitätsdatensätzen zu verweisen. Alle Beispiele in Common Data Service Web Services verwenden **ServiceContext** als Namen für diese Klasse, aber Ihr Code verwendet möglicherweise einen anderen Namen. Weitere Informationen: [Generieren von Klassen mit früher Bindung für den Organisationsservice](generate-early-bound-classes.md).
  
### <a name="see-also"></a>Siehe auch

 [Verwenden von LINQ zum Erstellen einer Abfrage](use-linq-construct-query.md)  
  
 [Verwenden von Entitätsklassen mit später Bindung mit einer LINQ-Abfrage](use-late-bound-entity-class-linq-query.md)  
  
 [Verwenden der Entitäts-Suchattribute mit LINQ](order-results-entity-attributes-linq.md)  

 [LINQ-Abfragebeispiele](linq-query-examples.md)