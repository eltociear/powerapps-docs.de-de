---
title: Entität ActivityPointer (Aktivität) (Common Data Service) | Microsoft-Dokumentation
description: Die Aktivitätszeiger (Aktivität)-Entität stellt eine Aktivität oder Aufgabe dar, die von einem Benutzer ausgeführt wird, oder ausgeführt werden soll. Eine Aktivität ist eine beliebige Aktion, für die ein Eintrag in einem Kalender vorgenommen werden kann.
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
ms.openlocfilehash: f979296356ba5cce562272ae1291a4aa39189a33
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748264"
---
# <a name="activitypointer-activity-entity"></a>ActivityPointer (Aktivität) Entität

Die Aktivitätszeiger (Aktivität)-Entität stellt eine Aktivität oder Aufgabe dar, die von einem Benutzer ausgeführt wird, oder ausgeführt werden soll. Eine Aktivität ist jede Aktion, für die ein Eintrag in einem Kalender vorgenommen werden kann.  
  
 Wenn Sie einen Aktivitätsdatensatz in Common Data Service erstellen, wird ein entsprechender Aktivitätszeigerdatensatz erstellt. Dies bedeutet, dass der Aktivitätsdatensatz und der entsprechende Aktivitätszeigerdatensatz denselben Wert für das `ActivityId`-Attribut haben. Wenn Sie z. B. einen `Email`-Datensatz erstellen, sind die Attributwerte von `Email.ActivityId` und des entsprechenden `ActivityPointer.ActivityId` identisch.  
  
 Das `ActivityPointer.ActivityTypeCode`-Attribut definiert den Typ der Aktivität. Die möglichen Werte für dieses Attribut sind im globalen Optionssatz `activitypointer_activitytypecode` definiert.  
  
<a name="bkmk_sortdate"></a>   

## <a name="control-how-activities-are-sorted-by-date"></a>Steuern, wie Aktivitäten nach Datum sortiert werden  
  
 Immer wenn Sie eine Liste von Entitäten anzeigen und sie nach Datum ordnen, können Sie nur die allgemeinen Datumsattribute verwenden, die in der activitypointer-Entität definiert wurden. Sie möchten jedoch manchmal auch ein anderes Sortierverhalten je nach Aktivitätstyp erhalten. Beispielsweise möchten Sie mit der E-Mail-Entität nach dem senton-Attributwert sortieren, anstelle des modifiedon-Attributwerts.  
  
 Verwenden Sie das sortdate-Attribut, um zu steuern, wie Aktivitäten nach Datum sortiert werden. Der Standardwert des sortdate-Attributs ist null. Sie müssen Geschäftslogik aufnehmen, um den Datumswert auszufüllen, der für dieses Attribut festgelegt wird, und dann das sortdate-Attribut in der Abfrage verwenden, die für die Ansicht definiert ist. Sie können den sortdate-Attributwert mithilfe eines Workflows oder Plug-Ins festlegen. Für einheitliche Ergebnisse sollte dieser Wert für jeden Aktivitätstyp und alle vorhandenen Aktivitätsdaten im System festgelegt werden.  
  
### <a name="see-also"></a>Siehe auch  
 [Aktivitätsentitäten](activity-entities.md)   
 [ActivityPointer-Entität](reference/entities/activitypointer.md)