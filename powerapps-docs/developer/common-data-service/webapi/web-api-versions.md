---
title: Common Data Service für Apps-Web-API-Versionen (Common Data Service für Apps) | Microsoft Docs
description: 'Lesen Sie wie die Versionsverwaltung der "Common Data Service für Apps"""-Web-API funktioniert. "Common Data Service für Apps"-Web-API-Versionen unterstützen versionsspezifische Unterschiede in derselben Umgebung, die sich vom Verhalten in v8x.-Versionen unterscheiden, in der neue Funktionen additiv waren.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d9bb79a5-2bfa-4ffe-8cb4-60f192359489
caps.latest.revision: 34
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-data-service-for-apps-web-api-versions"></a>"Common Data Service für Apps"-Web-API-Versionen

Ab der (v9.0)-Version von Dynamics 365 unterstützt die Web-API versionsspezifische Unterschiede in derselben Umgebung.  
  
Dies unterscheidet sich vom Verhalten der v8.*x*-Versionen. In früheren Versionen waren neue Funktionen für alle Versionen des Services verfügbar. Dies hing vom Update ab, das auf die Umgebung angewendet wurde.  Nach dem Upgrade auf v8.2 sind die Services v8.0 und v8.1 identisch. Dies war möglich, da alle Änderungen additiv waren. Nichts wurde entfernt oder führte wichtige Änderungen ein. Daher war die bestimmte Version, auf die in der Service-URL für V8.*x* verwiesen wurde, nicht wirklich wichtig.  
  
Darüber hinaus können sich die Funktionen des Service ändern, einschließlich möglicher wichtiger Änderungen wie das Entfernen bestimmter Operationen. Dadurch wird es möglich, Verbesserungen regelmäßig anzuwenden. In diesem Thema werden alle versionsspezifischen Unterschiede und alle Einschränkungen genannt, in denen die Web-API dem Organisationsservice noch nicht gleichwertig ist.  
  
## <a name="web-api-limitations"></a>-Web-API-Einschränkungen  

Die "Common Data Service für Apps"-Web API bietet komplette Parität mit den Fähigkeiten des Organisationsservices. Für Common Data Service für Apps beschreibt dieses Thema die Beschränkungen, die von der Common Data Service für Apps v8.x-Version weitergegeben wurden. Informationen zu früheren Versionen finden Sie unter [Web-API-Einschränkungen in Dynamics CRM 2016](https://msdn.microsoft.com/library/mt628816\(CRM.8\).aspx).  
 
> [!NOTE] 
> Wenn Sie eine benutzerdefinierte Aktion definiert haben, die einem komplexen und einen einfachen Rückgabewert enthielt, stand in der Web-API keine entsprechende Aktion zur Verfügung, dafür aber im SOAP-Endpunkt 2011. Ein komplexer Rückgabewert ist ein `EntityReference`, `Entity`oder `EntityCollection`. Sie können eine beliebige Kombination von einfachen Rückgabewerten oder einem einzelner komplexen Rückgabewert haben. Weitere Informationen: [Erstellen eigener Aktionen](/dynamics365/customer-engagement/developer/create-own-actions).
 
## <a name="new-operations-added"></a>Neuer Vorgang hinzugefügt  
 Die folgenden Vorgänge sind der Web-API für die Version v9.x hinzugefügt worden.  
  
||||  
|-|-|-|  
|<xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest>|  
  
### <a name="see-also"></a>Siehe auch  

[Verwenden der Common Data Service for Apps-Web-API](overview.md)<br />
[Authentifizierung beim Common Data Service für Apps mit der Web API](authenticate-web-api.md)<br />
[Internet API-Typen und -Vorgänge](web-api-types-operations.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)
