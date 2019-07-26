---
ms.openlocfilehash: 29226cfe8ab5c0ad01b785cfdaeec2e12a230dd7
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225340"
---
Durch Aktivieren der Social Engagement-Verbindung mit [Azure Event Hubs](https://azure.microsoft.com/documentation/articles/event-hubs-overview/) können Social Media-Daten mithilfe von Automatisierungsregeln an Event Hubs gestreamt werden. Event Hubs speichert die von Social Engagement gestreamten Social Media-Daten für einen [vorkonfigurierten Zeitraum](https://azure.microsoft.com/documentation/articles/event-hubs-availability-and-support-faq/), und alle Anwendungen, die den Event Hub verfolgen können, haben die Möglichkeit zum Abrufen, Speichern und/oder Verarbeiten dieser Daten.  
  
 Beachten Sie, dass die von Social Engagement gesendeten Daten für das soziale Netzwerk Informationen zum Beitrag im sozialen Netzwerk (Autor und Text) sowie zusätzliche Informationen wie Sprache, Standort, Stimmung, Tags usw. enthalten. Informationen zum Inhalt eines Beitrags im sozialen Netzwerk, die an Event Hubs gesendet werden, finden Sie in der [JSON-Schemadefinition](http://go.microsoft.com/fwlink/p/?LinkId=786643).