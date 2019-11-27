---
title: BusinessUnit-Entität (Common Data Service) | Microsoft-Dokumentation
description: Eine Organisation in Common Data Service, wie eine Beteiligungsgesellschaft oder eine Gesellschaft, besteht aus Unternehmenseinheiten.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 82ee0de5cf08c36d19afd5e9e7527390107367fc
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748436"
---
# <a name="businessunit-entity"></a>BusinessUnit-Entität

Eine Organisation in Common Data Service, wie eine Beteiligungsgesellschaft oder eine Gesellschaft, besteht aus Unternehmenseinheiten. Eine *Unternehmenseinheit* ist eine Einheit der Organisation auf oberster Ebene. Unternehmenseinheiten können übergeordnete Elemente anderer Unternehmenseinheiten (untergeordneter Unternehmenseinheiten) sein. Die erste für eine Organisation erstellte Unternehmenseinheit ist die Stammunternehmenseinheit. Unternehmenseinheiten können gelöscht werden, jedoch die Stammunternehmenseinheit kann nicht gelöscht werden.  
  
- Eine *übergeordnete Geschäftseinheit* ist eine Unternehmenseinheit mit einer oder mehreren untergeordneten Unternehmenseinheiten.  
  
- Eine *untergeordnete Unternehmenseinheit* ist eine Unternehmenseinheit, die sich direkt unter einer anderen Unternehmenseinheit in der Unternehmenshierarchie einer Organisation befindet.  
  
 Eine Unternehmenseinheit kann Datensätze besitzen, wie sie im Besitztyp in der Metadatendefinition für eine Entität festgelegt sind. 
  
 Sicherheitsrollen sind Unternehmenseinheiten zugeordnet. Sie können die <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest>-Nachricht abrufen, um die Unternehmenseinheit für den Benutzer, der derzeit angemeldet ist oder dessen Identität angenommen wurde, herauszufinden.

### <a name="see-also"></a>Siehe auch

[BusinessUnit-Entitätsreferenz](reference/entities/businessunit.md)
[Sicherheitsentitäten](security-model.md)