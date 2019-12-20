---
title: Optimistische Parallelität (Common Data Service) | Microsoft-Dokumentation
description: Mit der optimistischen Parallelität können die Anwendungen feststellen, ob ein Entitätsdatensatz auf dem Server zwischen dem Abrufen des Datensatzes durch die Anwendung und dem Versuch der Anwendung, den Datensatz zu aktualisieren oder zu löschen, geändert wurde.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: c21caa604e025250805d26d0b31a2e88d1a7ad64
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2859995"
---
# <a name="optimistic-concurrency"></a>Optimistische Parallelität

In einem Multithread- und Mehrbenutzersystem wie Power Apps werden Vorgänge und Datenänderungen häufig parallel ausgeführt. Ein Problem entsteht, wenn zwei oder mehr Update- oder Löschvorgänge für dieselben Daten gleichzeitig ausgeführt werden. Dieser Fall kann möglicherweise zu Datenverlusten führen. Mit der optimistischen Parallelität können die Anwendungen feststellen, ob ein Entitätsdatensatz auf dem Server zwischen dem Abrufen des Datensatzes durch die Anwendung und dem Versuch der Anwendung, den Datensatz zu aktualisieren oder zu löschen, geändert wurde.  
  
 Optimistische Parallelität wird für alle vordefinierten Entitäten, die für die Offlinesynchronisierung aktiviert sind, und für alle benutzerdefinierten Entitäten unterstützt. Sie können feststellen, ob eine Entität die optimistische Parallelität unterstützt, indem Sie die Metadaten der Entität durch Code abrufen oder die Metadaten mit dem [Metadatenbrowser](browse-your-metadata.md) anzeigen und prüfen, ob das Attribut **IsOptimisticConcurrencyEnabled** auf `true` gesetzt ist. Bei benutzerdefinierten Entitäten wird diese Eigenschaft standardmäßig auf `true` festgelegt.  
  
<a name="bkmk_enable"></a>   
## <a name="enable-optimistic-concurrency"></a>Aktivieren der optimistischen Parallelität  
 Sie können das Prüfverhalten der optimistischen Parallelität aktivieren, wenn Sie  <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> ausführen, indem Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest.ConcurrencyBehavior> der Anforderung auf <xref:Microsoft.Xrm.Sdk.ConcurrencyBehavior.IfRowVersionMatches> setzen. Entsprechend legen Sie für <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> die Eigenschaft <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest.ConcurrencyBehavior> fest.  
  
 Wennn Sie den Organisationsdienstkontext für Datenänderungen verwenden, legen Sie <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.ConcurrencyBehavior> für das Objekt <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> fest. Dieser Wert wird an alle **UpdateRequest**- und **DeleteRequest**-Nachrichten weitergegeben, die von **OrganizationServiceContext** verwendet werden, wenn <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> aufgerufen wird.  
  
 Das Verhalten der optimistischen Parallelität kann nur durch einen SDK-Aufruf festgelegt werden. Es gibt momentan keine Einstellung dafür in Formularen der Webanwendung.  
  
## <a name="apply-optimistic-concurrency-using-web-api"></a>Anwendung der optimistischen Parallelität mit der Web-API

Informationen zur Nutzung der Web-API, um die optimistische Parallelität anzuwenden, finden Sie unter [Optimistische Parallelität anwenden](webapi/perform-conditional-operations-using-web-api.md##apply-optimistic-concurrency)


## <a name="apply-optimistic-concurrency-using-organization-service"></a>Anwenden der optimistischen Parallelität mit dem Organisationsservice

Informationen zur Nutzung des Organisationsservice, um die optimistische Parallelität anzuwenden, finden Sie unter [Verhalten der optimistischen Parallelität](org-service/entity-operations-update-delete.md##optimistic-concurrency-behavior)
  
<a name="bkmk_handle"></a>   
## <a name="handle-exceptions"></a>Verarbeiten von Ausnahmen  
 Es gibt mehrere Fehlerzustände, die in einer [FaultException](https://msdn.microsoft.com/library/ms576199\(v=vs.110\).aspx)\<<xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>> aus dem Webdienstaufruf zurückgegeben werden können, wenn die optimistische Parallelität verwendet wird.  
  
- **ConcurrencyVersionMismatch** (code=-2147088254)  
  
     Wenn eine Zeilenversion bereitgestellt wurde und das **IfVersionMatches**-Verhalten angegeben wird, falls die Version des vorhandenen Datensatzes nicht mit der in der Anforderung bereitgestellten Zeilenversion übereinstimmt, wird ein Fehler zurückgegeben.  
  
- **ConcurrencyVersionNotProvided** (code= -2147088253)  
  
     Wenn das **IfVersionMatches**-Verhalten angegeben ist und kein Wert für die Zeilenversion bereitgestellt wurde, wird ein Fehler zurückgegeben.  
  
- **OptimisticConcurrencyNotEnabled** (code=-2147088243)  
  
     Wenn das **IfVersionMatches**-Verhalten für ein Update einer Entität angegeben wird und die optimistische Parallelität nicht aktiviert ist, wird ein Fehler zurückgegeben.  
  
  Sie können die [Code](https://msdn.microsoft.com/library/system.servicemodel.faultexception.code\(v=vs.110\).aspx)-Eigenschaft des zurückgegebenen Fehlers prüfen, um zu ermitteln, ob der Fehler mit der optimistischen Parallelität zusammenhängt. Die Codes für die oben Fehlerzustände werden oben angezeigt und stammen aus dem ErrorCodes.cs-Hilfscode.  
  
