---
title: 'Beispiel: Berechnen Sie mit einer benutzerdefinierten Workflowaktivität einen Kreditscore (Common Data Service) | Microsoft-Dokumentation'
description: Die folgende Beispielworkflowaktivität berechnet den Kreditscore anhand der Sozialversicherungsnummer (SSN) und des Namens.
ms.custom: ''
ms.date: 1/28/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
ms.assetid: 9cb7eb41-1a73-44a8-ae58-14120e84243f
caps.latest.revision: 19
author: JimDaly
ms.author: jdaly
manager: KumarVivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5d007765af7f8c22d027a65f2a1c8818e1890410
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154902"
---
# <a name="sample-calculate-a-credit-score-with-a-custom-workflow-activity"></a>Beispiel: Berechnen Sie mit einer benutzerdefinierten Workflowaktivität einen Kreditscore

Dieser Beispielcode ist für Common Data Service. Laden Sie hier das vollständige Beispiel herunter: [WorkflowActivities](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkflowActivities).

## <a name="prerequisites"></a>Voraussetzungen

[!INCLUDE [sdk-prerequisite](../../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Anforderungen

Die folgenden Anpassungen müssen vorhanden sein, damit diese benutzerdefinierte Workflowaktivität funktioniert:  

-   Entitätsschemaname: `new_loanapplication`  
-   Attribut: `new_loanapplicationid` als Primärschlüssel  
-   Attribut: `new_creditscore` vom Typ `int` mit mindestens 0 und maximal 1000 (falls aktualisiert werden soll)  
-   Attribut: `new_loanamount` des Geld-Typs mit Standard-Minimum und Maximum.  
-   Anpassen des Formulars, um das Attribut `new_loanapplicantid` einzuschließen  
  
Die Kontaktentität muss über die folgenden Anpassungen verfügen:  
  
-   Attribut: `new_ssn` als **Einzelne Textzeile** mit einer maximalen Länge von 15  
-   1:n-Beziehung mit diesen Eigenschaften:  
    -   Schemaname der Beziehungsdefinition: `new_loanapplicant`  
    -   Anzeigename der mit der Beziehungsdefinition verknüpften Entität: Kreditwendung  
    -   Schemaname des Beziehungsnamens: `new_loanapplicantid`  
    -   Beziehungsverhaltenstyp: Referenziell  
  
## <a name="demonstrates"></a>Demonstriert

Die folgende Beispielworkflowaktivität berechnet den Kreditscore anhand der Sozialversicherungsnummer (SSN) und des Namens.  
  
## <a name="example"></a>Beispiel  

[RetrieveCreditScore.cs](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/orgsvc/C%23/WorkflowActivities/WorkflowActivities/RetrieveCreditScore.cs)

### <a name="see-also"></a>Siehe auch

[Workflowerweiterungen](workflow-extensions.md)<br />
[Lernprogramm: Erstellen einer Workflow-Erweiterung](tutorial-create-workflow-extension.md)<br />
[Beispiel: Eine benutzerdefinierte Workflowaktivität erstellen](sample-create-custom-workflow-activity.md)<br />
[Beispiel: Aktualisieren des nächsten Geburtstags mithilfe einer benutzerdefinierten Workflowaktivität](sample-update-next-birthday-using-custom-workflow-activity.md)
