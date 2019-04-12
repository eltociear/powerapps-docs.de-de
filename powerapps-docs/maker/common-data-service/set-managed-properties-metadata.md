---
title: Verwaltete Eigenschaften in Common Data Service-Metadaten festlegen | MicrosoftDocs
description: 'Erfahren Sie, wie Sie verwaltete Eigenschaften für Metadatenelemente in einer Lösung festlegen können.'
ms.custom: ''
ms.date: 05/30/2018
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
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>Verwaltete Eigenschaften in Common Data Service-Metadaten festlegen 

Verwaltete Eigenschaften gelten nur, wenn Sie Metadaten in einer verwalteten Lösung hinzufügen und in eine andere Umgebung importieren. Diese Einstellungen ermöglichen einem Lösungsentwickler, die Anpassungsmöglichkeiten zu steuern, die Benutzer, die ihre verwaltete Lösung installieren, haben sollen. 

> [!TIP]
> Im Allgemeinen ist es eine gute Idee, die Metadaten in Ihrer Lösung, die mit Geschäftsdaten arbeitet, zu erweitern. Dies ermöglicht es ihnen, Ihre Lösung genau so auf ihre Bedürfnisse zuzuschneiden, wie sie es für Standardentitäten können.
>
>Für Metadaten, die Funktionen zur Unterstützung Ihrer Lösung bieten, aber keine Geschäftsdaten enthalten, ist es eine gute Idee, die zulässigen Anpassungen einzuschränken.

Die Einstellung der verwalteten Eigenschaften muss mit Hilfe des Lösungs-Explorers erfolgen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="entity-managed-properties"></a>Verwaltete Eigenschaften der Entität

Während Sie [Entitäten anzeigen](create-edit-entities-solution-explorer.md#view-entities), wählen Sie die Entität aus und dann **Verwaltete Eigenschaften** in der Menüleiste.  Dadurch wird das Dialogfeld **Verwaltete Eigenschaften festlegen** geöffnet.

![Verwaltete Eigenschaften der Entität festlegen](media/set-managed-properties.png)
  
Entitäten haben mehr verwaltete Eigenschaften als andere Arten von Lösungskomponenten. Wenn die Entität angepasst werden kann, können Sie die folgenden Optionen einstellen:  

|Option|Beschreibung|
|--|--|
|**Kann angepasst werden** |Steuert alle anderen Optionen. Wenn diese Option `False` ist, gelten keine der anderen Einstellungen. Wenn sie `True` ist, können Sie die anderen Anpassungsoptionen angeben. Bei `False` ist es gleichbedeutend mit dem Setzen aller anderen Optionen auf false.|
|**Anzeigename kann geändert werden**|Ob der Name der Entitätsanzeige geändert werden kann.|
|**Ändern zusätzlicher Eigenschaften möglich** |Gilt für alles, was nicht durch andere Optionen abgedeckt ist.|
|**Neue Formulare können erstellt werden**|Ob neue Formulare für die Entität erstellt werden können.|
|**Neue Diagramme können erstellt werden**|Ob neue Diagramme für die Entität erstellt werden können.|
|**Neue Ansichten können erstellt werden** |Ob neue Ansichten für die Entität erstellt werden können.|
|**Hierarchische Beziehung kann geändert werden**|Ob die Einstellungen für hierarchische Beziehungen geändert werden können. Weitere Informationen: [Definieren und Abfragen von hierarchisch verknüpften Daten](define-query-hierarchical-data.md)|
|**Kann die Änderungsnachverfolgung aktiviert werden?** |Ob die Entitätseigenschaft **Änderungsnachverfolgung** geändert werden kann.|
|**Kann Synchronisierung mit externem Suchindex aktivieren** |Ob die Entität zur Aktivierung der Relevanzsuche konfiguriert werden kann. Weitere Informationen: [Konfigurieren Sie die Relevanzsuche, um und die Suchergebnisse und Leistung zu verbessern](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="field-managed-properties"></a>Feld Verwaltete Eigenschaften

Weitere Informationen zum Bearbeiten von Feldern finden Sie unter [Erstellen und Bearbeiten von Feldern für Common Data Service mit PowerApps-Lösungs-Explorer](create-edit-field-solution-explorer.md).

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
[Erstellen und Bearbeiten von Feldern für Common Data Service mit PowerApps-Lösungs-Explorer](create-edit-field-solution-explorer.md)<br />
[Erstellen oder Bearbeiten von 1: N (1: n- oder n: n) Entitätsbeziehungen 1 mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)<br />
[Erstellen von n:n-Entitätsbeziehungen in Common Data Service mithilfe des Lösungs-Explorers](create-edit-nn-relationships-solution-explorer.md)
