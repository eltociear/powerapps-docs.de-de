---
title: Deaktivierte Anpassungen entfernen | MicrosoftDocs
description: 'Deaktivierte oder deaktivierte Anpassungen sollten aus einer Lösung entfernt werden, um das Lösungsmanagement zu verbessern und das Risiko der Verwendung oder Verwaltung einer veralteten Komponente zu verringern.'
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="remove-deactivated-or-disabled-customizations"></a>Deaktivierte Anpassungen entfernen

**Kategorie**: Wartbarkeit, Supportfähigkeit

**Wirkungspotential**: Niedrig

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Deaktivierte oder deaktivierte Anpassungen sollten aus einer Lösung entfernt werden, um das Lösungsmanagement zu verbessern und das Risiko der Verwendung oder Verwaltung einer veralteten Komponente zu verringern.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Stellen Sie sicher, dass jede Lösungskomponente, die deaktiviert oder deaktiviert ist, absichtlich deaktiviert wurde.  Wenn dies der Fall ist und nicht mehr verwendet wird, ziehen Sie in Betracht, es aus der Lösung zu entfernen, um Verwechslungen für Benutzer und System-Customizer zu vermeiden. Zu diesen Komponenten gehören:

- SDK-Nachrichtenverarbeitungsschritte
- Prozesse
- Regeln für Datensatzerstellung und -aktualisierung
- SLAs

Entitätskomponenten wie:

- Formulare
- Ansichten
- Geschäftsregeln

![Deaktivierte Prozesse](../media/deactivated-processes.png)

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Wenden Sie angepasste Geschäftslogik mit Geschäftsregeln und Flüssen in Modell-angetriebene Apps an](/powerapps/maker/model-driven-apps/guide-staff-through-common-tasks-processes)<br />
[Ereignisse in Formularen und in Rastern in Modell-angetriebenen Apps](/powerapps/developer/model-driven-apps/clientapi/events-forms-grids)<br/>