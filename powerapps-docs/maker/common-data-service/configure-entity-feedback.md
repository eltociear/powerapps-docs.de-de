---
title: Konfigurieren einer Entität für Feedback mit PowerApps | Microsoft-Dokumentation
description: Informationen zum Aktivieren von Feedback für eine Entität
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
ms.openlocfilehash: efb1cf167353d5928564b42aeb7a49f43cf272d6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39684793"
---
# <a name="configure-an-entity-for-feedbackratings"></a>Konfigurieren einer Entität für Feedback/Bewertungen

Lassen Sie Kunden oder Mitarbeiter Feedback für jeden Entitätsdatensatz schreiben oder Entitätsdatensätze innerhalb eines festgelegten Bewertungsbereichs bewerten, indem Sie Entitäten für Feedback aktivieren.  

Diese Funktion wird gerne bei Systemen verwendet, mit denen Daten von Kunden über ein Portal oder eine Umfrage erfasst werden. Daten über Service- oder Produktzufriedenheit können auf Entitäten angewendet werden, die diese Art von Daten darstellen.

Feedback kann auch von Mitarbeitern zum Bereitstellen von Feedback zu einem gemeinsamen Projekt verwendet werden.

> [!NOTE]
> Zum Durchführen der folgenden Schritte benötigen Sie die Sicherheitsrolle „Systemadministrator“ oder „Systemanpasser“ oder eine gleichwertige Berechtigung.
  
## <a name="enable-feedback"></a>Aktivieren von Feedback  
  
Bearbeiten Sie die Entität, um **Feedback** zu aktivieren. Weitere Informationen: [Bearbeiten einer Entität](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>Hinzufügen eines Unterrasters für Feedback zum Entitätsformular  

Standardmäßig müssen Benutzer zur Liste der verknüpften Datensätze des Datensatzes wechseln, für den sie Feedback hinzufügen möchten. Sie können Benutzern das Hinzufügen von Feedback erleichtern, indem Sie dem Formular der Entität, für die Sie Feedback ermöglichen möchten, ein Feedback-Unterraster hinzufügen.  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. --> Weitere Informationen: [Sub-Grid properties overview (Übersicht über Unterrastereigenschaften)](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>Hinzufügen eines Rollupfelds zum Entitätsformular, um die Bewertungen anzuzeigen  

Je nachdem, wie Sie die Bewertung für die Entität berechnen möchten, können Sie ein Rollupfeld zum Berechnen der Bewertung erstellen und dem Formular der Entität hinzufügen, für die Sie Feedback ermöglichen. Weitere Informationen: [Definieren von Rollupfeldern, die Werte aggregieren](define-rollup-fields.md)
  
### <a name="see-also"></a>Siehe auch  
 [Senden von Feedback oder Bewertungen für Informationen, die im System gespeichert sind](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
