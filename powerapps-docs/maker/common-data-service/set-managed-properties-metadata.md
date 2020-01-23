---
title: Verwaltete Eigenschaften in Common Data Service-Metadaten festlegen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie verwaltete Eigenschaften für Metadatenelemente in einer Lösung festlegen können.
ms.custom: ''
ms.date: 12/19/2019
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
ms.assetid: edaa7d4a-a95f-4d66-a9d9-2ad6051332f7
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4e0c0432626896acdabf89133c86510b651e3859
ms.sourcegitcommit: 366f0d1b8309ab1fd533ebd7e1b41a69a99fd25a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2917911"
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>Verwaltete Eigenschaften in Common Data Service-Metadaten festlegen 

Verwaltete Eigenschaften gelten nur, wenn Sie Metadaten in einer verwalteten Lösung hinzufügen und in eine andere Umgebung importieren. Diese Einstellungen ermöglichen einem Lösungsentwickler, die Anpassungsmöglichkeiten zu steuern, die Benutzer, die ihre verwaltete Lösung installieren, haben sollen. 

Bei nicht verwalteten Komponenten können Sie die verwalteten Eigenschaften anzeigen und ändern. Bei verwalteten Komponenten können Sie die verwalteten Eigenschaften nicht anzeigen und ändern. 

> [!TIP]
> Im Allgemeinen ist es eine gute Idee, die Metadaten in Ihrer Lösung, die mit Geschäftsdaten arbeitet, zu erweitern. Dies ermöglicht es ihnen, Ihre Lösung genau so auf ihre Bedürfnisse zuzuschneiden, wie sie es für Standardentitäten können.
>
>Für Metadaten, die Funktionen zur Unterstützung Ihrer Lösung bieten, aber keine Geschäftsdaten enthalten, ist es eine gute Idee, die zulässigen Anpassungen einzuschränken.


## <a name="entity-managed-properties"></a>Verwaltete Eigenschaften der Entität
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und wählen Sie **Lösungen** aus der linken Navigation aus. 
2.  Öffnen Sie die gewünschte Lösung. 
3.  Wählen Sie aus der Liste der Komponenten die Lösung und wählen Sie **...** Klicken Sie neben der nicht verwalteten Entität, die Sie anzeigen oder bearbeiten möchten und wählen Sie dann **Verwaltete Eigenschaften**. 

    > [!div class="mx-imgBorder"] 
    > ![Von der Entität verwaltete Befehlseigenschaft](media/entity-managed-properties.png "Von der Entität verwaltete Befehlseigenschaft")

    Die Seite mit den verwalteten Eigenschaften wird angezeigt. 

    > [!div class="mx-imgBorder"] 
    > <img src="media/managed-properties-dialog.png" alt="Managed properties pane" height="572" width="300">

<!-- [Managed properties pane](media/managed-properties-dialog.png "Managed properties pane") -->
  
Entitäten haben mehr verwaltete Eigenschaften als andere Arten von Lösungskomponenten. Wenn die Entität angepasst werden kann, können Sie die folgenden Optionen einstellen:  

|Option|Beschreibung|
|--|--|
|**Anpassungen zulassen** |Steuert alle anderen Optionen. Wenn diese Option `False` ist, gelten keine der anderen Einstellungen. Wenn sie `True` ist, können Sie die anderen Anpassungsoptionen angeben. Bei `False` ist es gleichbedeutend mit dem Setzen aller anderen Optionen auf false.|
|**Anzeigename kann geändert werden**|Ob der Name der Entitätsanzeige geändert werden kann.|
|**Ändern zusätzlicher Eigenschaften möglich** |Gilt für alles, was nicht durch andere Optionen abgedeckt ist.|
|**Neue Formulare können erstellt werden**|Ob neue Formulare für die Entität erstellt werden können.|
|**Neue Diagramme können erstellt werden**|Ob neue Diagramme für die Entität erstellt werden können.|
|**Neue Ansichten können erstellt werden** |Ob neue Ansichten für die Entität erstellt werden können.|
|**Hierarchische Beziehung kann geändert werden**|Ob die Einstellungen für hierarchische Beziehungen geändert werden können. Weitere Informationen: [Definieren und Abfragen von hierarchisch verknüpften Daten](define-query-hierarchical-data.md)|
|**Kann die Änderungsnachverfolgung aktiviert werden?** |Ob die Entitätseigenschaft **Änderungsnachverfolgung** geändert werden kann.|
|**Kann Synchronisierung mit externem Suchindex aktivieren** |Ob die Entität zur Aktivierung der Relevanzsuche konfiguriert werden kann. Weitere Informationen: [Konfigurieren Sie die Relevanzsuche, um und die Suchergebnisse und Leistung zu verbessern](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="field-managed-properties"></a>Feld Verwaltete Eigenschaften

Weitere Informationen zum Bearbeiten von Feldern finden Sie unter [Erstellen und Bearbeiten von Feldern für Common Data Service mit Power Apps-Lösungs-Explorer](create-edit-field-solution-explorer.md).

Wählen Sie beim [Anzeigen von Feldern](create-edit-field-solution-explorer.md#view-fields) ein benutzerdefiniertes Feld aus einer nicht verwalteten Lösung aus, und wählen Sie dann **Weitere Aktionen** >  **Verwaltete Eigenschaften** in der Menüleiste.

![Feld Verwaltete Eigenschaften anzeigen](media/view-field-managed-properties-solution-explorer.png)  
  
Dadurch wird das Dialogfeld **Verwaltete Eigenschaften festlegen** geöffnet.

![Feld Verwaltete Eigenschaften festlegen](media/set-field-managed-property.png)

Die Option **Kann angepasst werden** steuert alle anderen Optionen. Wenn diese Option **False** ist, gelten keine der anderen Einstellungen. Wenn sie **True** ist, können Sie die anderen Anpassungsoptionen angeben.  
  
Wenn das Feld anpassbar ist, setzen Sie die folgenden Optionen auf **True** oder **False**.  
  
- **Anzeigename kann geändert werden**
- **Kann Erforderlichkeitsstufe ändern** 
- **Kann zusätzliche Eigenschaften ändern** : Diese Eigenschaft steuert alle anderen Anpassungen, die keine bestimmte verwaltete Eigenschaft haben.

Die Einstellung aller einzelnen Optionen auf **False** ist gleichbedeutend mit der Einstellung **Kann angepasst werden** auf **False**.  

Übernehmen Sie Ihre Auswahl und klicken Sie auf **Festlegen**, um das Dialogfeld zu schließen.

> [!NOTE]
> Wenn dieses Feld ein **Datum und Uhrzeit**-Feld ist, steht eine zusätzliche Eigenschaft **Kann das Datums- und Uhrzeitverhalten ändern** zur Verfügung. Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)

## <a name="relationship-managed-properties"></a>Beziehungsverwaltete Eigenschaften

Wählen Sie beim Anzeigen von Entitätsbeziehungen eine Beziehung aus einer nicht verwalteten Lösung aus, und wählen Sie dann **Weitere Aktionen** > **Verwaltete Eigenschaften** in der Menüleiste.
  
Bei Beziehungen ist die einzige verwaltete Eigenschaft **Kann angepasst werden**. Diese Einstellung steuert alle Änderungen, die an der Entitätsbeziehung vorgenommen werden können. 


### <a name="see-also"></a>Siehe auch

[Verwaltete Eigenschaften](solutions-overview.md#managed-properties)<br />
[Erstellen und Bearbeiten von Entitäten mithilfe des Lösungsexplorer](create-edit-entities-solution-explorer.md)<br />
[Erstellen und Bearbeiten von Feldern für Common Data Service mithilfe des Power Apps-Projektmappen-Explorers](create-edit-field-solution-explorer.md)<br />
[Erstellen oder Bearbeiten von 1: N (1: n- oder n: n) Entitätsbeziehungen 1 mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)<br />
[Erstellen von n:n-Entitätsbeziehungen in Common Data Service mithilfe des Projektmappen-Explorers](create-edit-nn-relationships-solution-explorer.md)
