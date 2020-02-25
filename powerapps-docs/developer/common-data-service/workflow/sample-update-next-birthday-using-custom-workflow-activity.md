---
title: 'Beispiel: Aktualisieren des nächsten Geburtstags mithilfe einer benutzerdefinierten Workflowaktivität (Common Data Service) | Microsoft-Dokumentation'
description: 'Die folgende Beispielworkflowaktivität gibt den nächsten Geburtstag zurück. Verwenden Sie das Beispiel in einem Workflow, der einen Geburtstagsgruß an einen Kunden sendet. '
ms.custom: ''
ms.date: 1/28/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
ms.assetid: 1cff83b0-1f7b-4ddb-a2af-b85f9f785529
caps.latest.revision: 21
author: JimDaly
ms.author: jdaly
manager: KumarVivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2bc01c06ca6f40e8bd521fa481519f6490f13d43
ms.sourcegitcommit: 4d858e628c89d245317d6192801d136f3591ea52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "2994596"
---
# <a name="sample-update-next-birthday-using-a-custom-workflow-activity"></a>Beispiel: Aktualisieren des nächsten Geburtstags mithilfe einer benutzerdefinierten Workflowaktivität

Laden Sie hier das vollständige Beispiel herunter: [WorkflowActivities](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkflowActivities).

## <a name="prerequisites"></a>Voraussetzungen

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Anforderungen 
 
Das folgende benutzerdefinierte Feld muss vorhanden sein, damit diese benutzerdefinierte Workflowaktivität funktioniert:  
  
-   `Contact`.`new_nextbirthday`  
  
## <a name="demonstrates"></a>Demonstriert  
 Die folgende Beispielworkflowaktivität gibt den nächsten Geburtstag zurück. Verwenden Sie das Beispiel in einem Workflow, der einen Geburtstagsgruß an einen Kunden sendet.  
  
## <a name="example"></a>Beispiel  

[NextBirthday.cs](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/orgsvc/C%23/WorkflowActivities/WorkflowActivities/NextBirthday.cs)
  
### <a name="see-also"></a>Siehe auch

[Workflowerweiterungen](workflow-extensions.md)<br />
[Lernprogramm: Erstellen einer Workflow-Erweiterung](tutorial-create-workflow-extension.md)<br />
[Beispiel: Eine benutzerdefinierte Workflowaktivität erstellen](sample-create-custom-workflow-activity.md)<br />
[Beispiel: Berechnen Sie mit einer benutzerdefinierten Workflowaktivität einen Kreditscore](sample-calculate-credit-score-custom-workflow-activity.md)
