---
title: BusinessUnit-Entität (Common Data Service) | Microsoft-Dokumentation
description: Eine Organisation in Common Data Service, wie eine Beteiligungsgesellschaft oder eine Gesellschaft, besteht aus Unternehmenseinheiten.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 8b10a53a1dde7e0a86d92a9601bcbc01d8577010
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156390"
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