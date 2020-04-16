---
title: Common Data Service Web API Versionen (Common Data Service)| Microsoft Docs
description: Lesen Sie, wie die Versionierung der Common Data Service Web API funktioniert. Common Data Service Web-API-Versionen unterstützen versionsspezifische Unterschiede in derselben Umgebung, die sich von dem Verhalten in den v8.x-Versionen unterscheiden, in denen neue Funktionen hinzugefügt wurden.
ms.custom: ''
ms.date: 07/25/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: d9bb79a5-2bfa-4ffe-8cb4-60f192359489
caps.latest.revision: 34
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9f400988376ccfe1427df8dd6036fb61b85aa987
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154938"
---
# <a name="common-data-service-web-api-versions"></a>Common Data ServiceWeb-API-Versionen

Ab der (v9.0)-Version von Dynamics 365 unterstützt die Web-API versionsspezifische Unterschiede in derselben Umgebung.  
  
Dies unterscheidet sich vom Verhalten der v8.*x*-Versionen. In früheren Versionen waren neue Funktionen für alle Versionen des Services verfügbar. Dies hing vom Update ab, das auf die Umgebung angewendet wurde.  Nach dem Upgrade auf v8.2 sind die Services v8.0 und v8.1 identisch. Dies war möglich, da alle Änderungen additiv waren. Nichts wurde entfernt oder führte wichtige Änderungen ein. Daher war die bestimmte Version, auf die in der Service-URL für V8.*x* verwiesen wurde, nicht wirklich wichtig.  
  
Darüber hinaus können sich die Funktionen des Service ändern, einschließlich möglicher wichtiger Änderungen wie das Entfernen bestimmter Operationen. Dadurch wird es möglich, Verbesserungen regelmäßig anzuwenden. In diesem Thema werden alle versionsspezifischen Unterschiede und alle Einschränkungen genannt, in denen die Web-API dem Organisationsservice noch nicht gleichwertig ist.  
  
## <a name="web-api-version-specific-differences"></a>Web API - Versionsspezifische Unterschiede

<a name="BKMK_fetchresponse"></a>

### <a name="encoding-for-special-characters-in-fetchxml-query-response"></a>Kodierung für Sonderzeichen in der FetchXML-Abfrageantwort

Für v8.*x* Versionen enthält die Antwort von FetchXML-Abfragen, die Linkeinheiten und deren Attribute enthalten, Unicode-Sonderzeichen, so dass '.' zu '_x002e_' und '@' zu '_x0040_' wird. Diese Kodierung für Sonderzeichen ist bei FetchXML-Abfragen für v9.*x* Release nicht vorhanden.

### <a name="same-name-for-entity-and-attribute"></a>Gleicher Name für Entität und Attribut

Wenn der Name einer Entität und eines ihrer Attribute gleich sind, wird an den Attributnamen in v8.x-Instanzen angehängt. Wenn beispielsweise eine Entität **new_zipcode** ein Attribut mit dem Namen **new_zipcode** hat, ändert sich der Attributname in **new_zipcode1**.

Für v9.*x* Instanzen wird nichts an den Attributnamen angehängt.

## <a name="new-operations-added"></a>Neuer Vorgang hinzugefügt  

Die folgenden Vorgänge sind der Web-API für die Version v9.x hinzugefügt worden.  
  
||||  
|-|-|-|  
|<xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest>|  

## <a name="web-api-limitations"></a>-Web-API-Einschränkungen  

Die Common Data Service-Web API bietet komplette Parität mit den Fähigkeiten des Organisationsservices. Für Common Data Service beschreibt dieses Thema die aus dem Release Common Data Service v8.x übertragenen Einschränkungen. Informationen zu früheren Versionen finden Sie unter [Dynamics CRM 2016 Web-API-Einschränkungen](https://msdn.microsoft.com/library/mt628816\(CRM.8\).aspx),  
 
> [!NOTE] 
> Wenn Sie eine benutzerdefinierte Aktion definiert haben, die einem komplexen und einen einfachen Rückgabewert enthielt, stand in der Web-API keine entsprechende Aktion zur Verfügung, dafür aber im SOAP-Endpunkt 2011. Ein komplexer Rückgabewert ist ein `EntityReference`, `Entity`oder `EntityCollection`. Sie können eine beliebige Kombination von einfachen Rückgabewerten oder einem einzelner komplexen Rückgabewert haben. Weitere Informationen: [Erstellen eigener Aktionen](/dynamics365/customer-engagement/developer/create-own-actions).

### <a name="see-also"></a>Siehe auch  

[Verwenden der Common Data Service-Web-API](overview.md)<br />
[Authentifizieren von Common Data Service mit der Web-API](authenticate-web-api.md)<br />
[Internet API-Typen und -Vorgänge](web-api-types-operations.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)