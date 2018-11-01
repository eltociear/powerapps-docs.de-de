---
title: Konfigurieren einer Entität für Feedback mit PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Feedback für eine Entität aktiviert wird'
ms.custom: ''
ms.date: 05/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 5b25cf09-d43b-4165-9eaa-7549f4855e7c
caps.latest.revision: 13
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-an-entity-for-feedbackratings"></a>Konfigurieren einer Entität für Feedback/Bewertungen

Ermöglichen Sie Kunden oder Mitarbeitern, Feedback für einen beliebigen Entitätsdatensatz zu schreiben oder Entitätsdatensätze innerhalb eines definierten Bewertungsbereichs zu bewerten, indem Sie Entitäten für Feedback aktivieren.  

Diese Funktion ist in ein System, das Daten von Kunden über das Portal oder Umfrage erfasst. Daten zur Service oder Produkt-Zufriedenheit können von Entitäten angewendet werden, die die Art von Daten darstellt.

Feedback kann der Mitarbeiter auch verwenden, um Feedback in einer erforderlichen Zusammenarbeit bereitzustellen.

> [!NOTE]
> Stellen Sie sicher, dass Sie über die Sicherheitsrolle „Systemadministrator“ oder „Systemanpasser“ bzw. entsprechende Berechtigungen verfügen, um diese Aufgabe auszuführen.
  
## <a name="enable-feedback"></a>Feedback aktivieren  
  
Bearbeiten Sie die Entität, um **Feedback** zu aktivieren. Weitere Informationen: [Bearbeiten einer Entität](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>Hinzufügen eines Unterrasters für Feedback auf dem Entitätsformular  

Standardmäßig müssen Benutzer zur Liste der verknüpften Datensätze des Datensatzes wechseln, für den Sie Feedback hinzufügen möchten. Damit Benutzer Feedback einfacher hinzufügen können, können Sie ein Feedback-Unterraster zum Formular der Entität hinzufügen, für die Sie Feedback ermöglichen möchten.  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. --> Weitere Informationen: [Unterrastereigenschaftenübersicht](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>Hinzufügen eines Rollupfelds zum Entitätsformular, um die Bewertungen anzuzeigen  

Abhängig davon, wie Sie die Bewertung für die Entität berechnen möchten, können Sie ein Rollupfeld erstellen, das die Bewertung berechnet und dieses dann zum Formular der Entität hinzufügen, für die Sie Feedback ermöglichen. Weitere Informationen: [Definieren der Rollupfelder für die Gesamtwerte](define-rollup-fields.md)
  
### <a name="see-also"></a>Siehe auch  
 [Feedback oder für Bewertungen für Dynamics 365-Datensätze senden](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
