---
ms.openlocfilehash: f1c11fd086a91db6dc0d0629549166bbba547dee
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67226505"
---
## <a name="mapping-functions-for-dynamics-365-customer-engagement-plan"></a>Zuordnungsfunktionen für Dynamics 365 Customer Engagement-Plan 
 Field Service und Project Service Automation bieten Schlüsselfunktionen, die auf dem Standort basieren. Beispiel: Standort von Dienstkonten (durch die definiert wird, wo Dienste oder Aufgaben ausgeführt werden) oder der geografische Start-/Endpunkt für Ressourcen (Personen, die Dienste oder Aufgaben ausführen).  Damit das System diese auf einer Karte anzeigen oder die Entfernung zwischen zwei Punkten berechnen kann, sind Kartendienste erforderlich (in diesem Fall Bing Karten).  
  
 Im Folgenden finden Sie den Workflow zum und vom Bing Karten-Dienst:  
  
|Von Dynamics 365|Bing Karten-Rückgabe|Note|  
|-----------------------|-----------------------|----------|  
|Adresse (Konto oder Ressource)|Breiten- und Längengrad der Adresse (Speicherort)|Dies wird als „Geocode“ einer Adresse bezeichnet.|  
|Gruppe von Standorten (Breiten- und Längengrad)|Abstand zwischen Standorten|Dies kann verwendet werden, um die optimalen Strecken für Ressourcen zu ermitteln oder die Fahrtdauer zu berechnen.|  
|Gruppe von Standorten (Breiten- und Längengrad)|Kartenansicht mit den Standorten in Form von Nadeln auf der Karte|Dies wird häufig verwendet, um die Konten und Ressourcen in einer Kartenansicht anzuzeigen.|  
  
> [!NOTE]
>  Neben den oben erwähnten Daten werden keine weiteren Daten an den Bing Karten-Dienst gesendet.
