---
title: Bearbeiten einer Entität in PowerApps | Microsoft-Dokumentation
description: Informationen zu den verschiedenen Arten, wie eine Entität bearbeitet werden kann
ms.custom: ''
ms.date: 05/15/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 8b00780c-74f0-4e3a-b570-b9289d0d5383
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3ec64583e2146703711b88456ff7bc91ece3e921
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757442"
---
# <a name="edit-an-entity"></a>Bearbeiten einer Entität

Sie können jede benutzerdefinierte Entität bearbeiten, die Sie erstellen. Standardentitäten oder verwaltete benutzerdefinierte Entitäten verfügen möglicherweise über Beschränkungen hinsichtlich der Änderungen, die Sie vornehmen können.  
  
> [!NOTE]
> **Standard**-Entitäten sind allgemeine Entitäten, die in Ihrer Umgebung enthalten sind und nicht **System**- oder **Benutzerdefiniert**- Entitäten sind. *Verwaltete benutzerdefinierte Entitäten* sind Entitäten, die dem System hinzugefügt wurden, indem eine verwaltete Lösung importiert wurde. Die Möglichkeiten zur Bearbeitung dieser Entitäten werden von den für jede Entität eingestellten verwalteten Eigenschaften festgelegt. Alle Eigenschaften, die nicht bearbeitet werden können, werden deaktiviert. 

Es gibt zwei Möglichkeiten, eine Entität mithilfe eines Designers zu bearbeiten:

|Designer|Beschreibung|
|--|--|
|[PowerApps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.|
|Lösungs-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen.|

Sowohl im PowerApps-Portal als auch im Lösungs-Explorer können Sie Folgendes durchführen:

- **Bearbeiten der Entitätsfelder**. Weitere Informationen: [Erstellen und Bearbeiten von Feldern für Common Data Service](create-edit-fields.md)
  
- **Bearbeiten der Entitätsbeziehungen**. Weitere Informationen:  [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)

- **Schlüssel** [Definieren von Alternativschlüsseln für den Verweis auf Datensätze](define-alternate-keys-reference-records.md)
  
Sie können auch Änderungen an Datensätzen vornehmen, die die Entität unterstützen:  

- **Geschäftsregeln**. Weitere Informationen: [Erstellen von Geschäftsregeln und Empfehlungen zur Anwendung einer Logik in einem Formular](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

- **Ansichten**. Weitere Informationen:  [Erstellen oder Bearbeiten einer Ansicht](../model-driven-apps/create-edit-views.md)
  
- **Formulare**. Weitere Informationen:  [Erstellen und Entwerfen von Formularen](../model-driven-apps/create-design-forms.md)

- **Dashboards**: Weitere Informationen: [Erstellen oder Bearbeiten von Dashboards](../model-driven-apps/create-edit-dashboards.md)

- **Diagramme**. [Systemdiagramme erstellen oder bearbeiten](../model-driven-apps/create-edit-system-chart.md)

## <a name="edit-using-powerapps-portal-designer"></a>Bearbeiten mithilfe des PowerApps-Portaldesigners

Im PowerApps-Portaldesigner gibt es nur drei Entitätseigenschaften, die Sie bearbeiten können:
 - Anzeigename
 - Plural-Anzeigename
 - Beschreibung

Wählen Sie im Designer die Entität aus, die Sie bearbeiten möchten, und klicken Sie darauf, um den Entitäts-Designer zu öffnen. Um die Entitätseigenschaften zu ändern, klicken Sie auf den Befehl **Einstellungen**, um das Formular **Entität bearbeiten** wie unten gezeigt anzuzeigen:

![Entitätseigenschaften bearbeiten](media/edit-entity-properties-powerapps-portal-designer.png)

> [!NOTE]
>  Der Name vieler Standardentitäten kann jedoch auch in anderem Text in der Anwendung verwendet werden. Um Text zu finden und zu ändern, in dem der Name verwendet wurde, lesen Sie [Standardentitätsnachrichten bearbeiten](edit-system-entity-messages.md).

Für alle anderen Änderungen an den Entitätsoptionen, müssen Sie die Entität mithilfe des Lösungs-Explorers bearbeiten.

## <a name="edit-using-solution-explorer"></a>Lösungs-Explorer zum Bearbeiten verwenden

Wenn Sie eine Entität mithilfe des Lösungs-Explorers bearbeiten, müssen Sie die nicht verwaltete Lösung suchen, die hinzugefügt werden soll.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
<a name="BKMK_ChangeEntityName"></a> 
  
## <a name="change-the-name-of-an-entity"></a>Ändern des Entitätsnamens  

Verwenden Sie die Eigenschaften **Anzeigename** und **Pluralname**, um den Namen der Entität in der Anwendung zu ändern. 

> [!NOTE]
>  Der Name vieler Standardentitäten kann jedoch auch in anderem Text in der Anwendung verwendet werden. Um Text zu finden und zu ändern, in dem der Name verwendet wurde, lesen Sie [Standardentitätsnachrichten bearbeiten](edit-system-entity-messages.md).
  
<a name="BKMK_ChangeEntityIcon"></a>   

###  <a name="change-the-icons-used-for-custom-entities"></a>Ändern der für benutzerdefinierte Entitäten verwendeten Symbole  

Standardmäßig haben alle benutzerdefinierten Entitäten in der Webanwendung dieselben Symbole. Sie können die Symbole für Bildwebressourcen erstellen, die Sie für die benutzerdefinierten Entitäten möchten. Weitere Informationen: [Symbole für benutzerdefinierte Entitäten ändern](../model-driven-apps/change-custom-entity-icons.md).  
  
<a name="BKMK_EnableOptions"></a>  
 
###  <a name="entity-options-that-can-only-be-enabled"></a>Entitätsoptionen, die nur aktiviert werden können  

In der folgenden Tabelle werden die Optionen aufgeführt, die Sie für eine Entität aktivieren können; nach der Aktivierung können sie jedoch nicht mehr deaktiviert werden:  

[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)] 
  
<a name="BKMK_EnableDisableOptions"></a>  
 
###  <a name="enable-or-disable-entity-options"></a>Aktivieren oder deaktivieren von Entitätsoptionen  

Die folgende Tabelle enthält die Entitätsoptionen, die Sie jederzeit aktivieren oder deaktivieren können.  

[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)] 

### <a name="see-also"></a>Siehe auch

[Erstellen einer Entität](create-edit-entities.md)<br />
[Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)
