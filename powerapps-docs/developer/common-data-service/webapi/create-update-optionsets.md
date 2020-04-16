---
title: Erstellen und Aktualisieren von Optionssätzen mit der Web-API (Common Data Service) | Microsoft-Dokumentation
description: Informationen zum Erstellen und Aktualisieren einer Entität Common Data Service, die eine metadatengestützte Architektur verwendet, um die Flexibilität zu bieten, mit der benutzerdefinierte Entitäten und zusätzliche Systementitätsattribute erstellt werden können.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
caps.latest.revision: 15
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f53c92c16a4f586f72d3ff471e285936d4490204
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155098"
---
# <a name="create-and-update-option-sets-using-the-web-api"></a>Erstellen und Aktualisieren von Optionssätzen mit der Web-API

Normalerweise können Sie mithilfe von *globalen* Optionssätzen Felder festlegen, sodass andere Felder denselben Satz von Optionen nutzen können, die an einem Ort verwaltet werden. Anders als *lokale* Optionssätze, die nur für ein bestimmtes Attribut definiert werden, können Sie Globale Optionssätze wiederverwenden. Sie können auch in Anforderungsparametern auf eine ähnliche Weise wie eine Enumeration verwendet werden.  
  
Beim Definieren eines globalen Optionssatzes mithilfe einer POST-Anfrage an *[Organisations-URI]*`/api/data/v9.0/GlobalOptionSetDefinitions` wird empfohlen, das System einen Wert zuweisen zu lassen. Dazu übergeben Sie einen **null** -Wert, wenn Sie die neue `OptionMetadata`-Instanz erstellen. Wenn Sie eine Option definieren, enthält sie ein für den Kontext des Herausgebers spezifisches Optionswertpräfix, festgelegt für die Lösung, in der der Optionssatz erstellt wird. Dieses Präfix hilft, die Möglichkeit der Erstellung von doppelten Optionssätzen für eine verwaltete Lösung zu verringern, sowie in allen Optionssätzen, die in Organisationen definiert werden, in denen die verwaltete Lösung installiert ist. Weitere Informationen finden Sie unter [Zusammenführung von Optionssatz-Optionen](../../../maker/common-data-service/how-managed-solutions-merged.md#merge-option-set-options).

 ## <a name="messages"></a>Nachrichten  
 Die folgende Tabelle enthält die Meldungen, die Sie mit globalen Optionssätzen verwenden können.  
  
|Meldung|Web-API-Vorgang|  
|--|--|
|CreateOptionSet|Verwenden Sie `POST`-Anfragen an *[Organisations-URI]*`/api/data/v9.0/GlobalOptionSetDefinitions`.|
|DeleteOptionSet|Verwenden Sie `DELETE`-Anfragen an *[Organisations-URI]-*`/api/data/v9.0/GlobalOptionSetDefinitions(`*MetadataID*`)`.|
|RetrieveAllOptionSets|Verwenden Sie `GET`-Anfragen an *[Organisations-URI]*`/api/data/v9.0/GlobalOptionSetDefinitions`.| 
|RetrieveOptionSet|Verwenden Sie `GET`-Anfragen an *[Organisations-URI]-*`/api/data/v9.0/GlobalOptionSetDefinitions(`*MetadataID*`)`.|   


Die folgende Tabelle enthält die Meldungen, die Sie mit lokalen und globalen Optionssätzen verwenden können.

|Meldung|Web-API-Vorgang|  
|--|--|
|DeleteOptionValue</br>Löscht einen der Werte in einem globalen Optionssatz.|<xref href="Microsoft.Dynamics.CRM.DeleteOptionValue?text=DeleteOptionValue Action" />  
|InsertOptionValue</br>Fügt eine neue Option in einen globalen Optionssatz ein.|<xref href="Microsoft.Dynamics.CRM.InsertOptionValue?text=InsertOptionValue Action" />| 
|InsertStatusValue</br>Fügt eine neue Option in den globalen Optionssatz ein, der im `Status`-Attribut verwendet wird.|<xref href="Microsoft.Dynamics.CRM.InsertStatusValue?text=InsertStatusValue Action" />|
|OrderOption</br>Ändert die relative Reihenfolge der Optionen in einem Optionssatz.|<xref href="Microsoft.Dynamics.CRM.OrderOption?text=OrderOption Action" />|
|UpdateOptionSet|Verwenden Sie `PUT`-Anfragen mit einer <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> an *[Organisations-URI]*`/api/data/v9.0/GlobalOptionSetDefinitions(`*-MetadataID*`)/Microsoft.Dynamics.CRM.OptionSetMetadata`<br />Für einen lokalen Optionssatz verwenden Sie *[Organisations-URI]*`/api/data/v9.0/EntityDefinitions(`*Metadataid*`)/Attributes(`*Metadataid*`)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet`.|
|UpdateOptionValue</br>Aktualisiert eine Option in einem globalen Optionssatz.|<xref href="Microsoft.Dynamics.CRM.UpdateOptionValue?text=UpdateOptionValue Action" />|
|UpdateStateValue</br>Fügt eine neue Option in den Optionssatz ein, der im `Status`-Attribut verwendet wird.|<xref href="Microsoft.Dynamics.CRM.UpdateStateValue?text=UpdateStateValue Action" />|

### <a name="see-also"></a>Siehe auch

[Optionssätze anpassen](../org-service/metadata-option-sets.md)