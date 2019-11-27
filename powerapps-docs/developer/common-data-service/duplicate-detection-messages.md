---
title: Duplikaterkennungsmeldungen (Common Data Service) | Microsoft-Dokumentation
description: Verwenden Sie die Messages BulkDetectDuplicatesRequest oder RetrieveDuplicatesRequest, um Duplikate zu erkennen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ed2d9180bfb148c59efb679f6a44d8d184a9c2d7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748223"
---
# <a name="duplicate-detection-messages"></a>Duplikaterkennungsmeldungen

Mithilfe der Nachrichten, die in der folgenden Tabelle aufgeführt sind, können Sie in Common Data Service Duplikate erkennen.  


|                                                                                                                                                                                                                   Meldung                                                                                                                                                                                                                   |                                      Web-API-Vorgang                                       |                         SDK-Assembly                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| Erkennt Duplikate für einen angegebenen Entitätstyp anhand vonAbfragekriterien, und speichert sie als Instanzen doppelter Datensatzentitätstypen in der Common Data Service-Datenbank.<br /><br /> Der Abfrageausdruck, der die Datensätze beschreibt, auf denen der Duplikaterkennungsauftrag ausgeführt werden soll, ist in der Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest.Query> dieser Anfrage angegeben. | <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates Action" /> | <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest> |
|                                                                                                         Erkennt und ruft Duplikate für einen bestimmten Datensatz ab.<br /><br /> Die entsprechende Entitätstyp ist in der Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest.MatchingEntityName> dieser Anfrage angegeben.                                                                                                          |  <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />  |  <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest>  |

### <a name="see-also"></a>Siehe auch  
 [Aktivieren und Deaktivieren der Duplikaterkennung](enable-disable-duplicate-detection.md)  
 [Ausführen der Duplikaterkennung](run-duplicate-detection.md)   
 [Duplikatregelentitäten](duplicaterule-entities.md)<br />
