---
title: Festlegen verwalteter Eigenschaften in Common Data Service für Apps-Metadaten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie verwaltete Eigenschaften für Metadatenelemente in einer Lösung festlegen.
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: edaa7d4a-a95f-4d66-a9d9-2ad6051332f7
caps.latest.revision: 41
ms.author: matp
manager: kvivek
ms.openlocfilehash: 46727f5a46e3fd518da52fac7d08a6e43992c00d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39684562"
---
# <a name="set-managed-properties-in-common-data-service-for-apps-metadata"></a>Festlegen verwalteter Eigenschaften in Common Data Service für Apps-Metadaten 

Verwaltete Eigenschaften gelten nur, wenn Sie einer verwalteten Lösung Metadaten hinzufügen und die Lösung in eine andere Umgebung importieren. Diese Einstellungen ermöglichen einem Lösungsersteller, die Anpassungsmöglichkeiten zu steuern, die Benutzer beim Installieren der verwalteten Lösung haben sollen. 

> [!TIP]
> Es ist im Allgemeinen eine gute Idee, Benutzern zu erlauben, Metadaten in Ihre Lösung zu übernehmen, die mit Geschäftsdaten arbeitet. Damit können sie Ihre Lösung auf die gleiche Weise wie für Standardentitäten ihren Anforderungen anpassen.
>
>Es ist sinnvoll, für Metadaten, die Funktionen zur Unterstützung Ihrer Lösung bereitstellen, aber keine geschäftlichen Daten enthalten, die zulässigen Anpassungen einzuschränken.

Das Festlegen verwalteter Eigenschaften muss mithilfe des Projektmappen-Explorers ausgeführt werden.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="entity-managed-properties"></a>Verwaltete Entitätseigenschaften

Wählen Sie während des **Anzeigens von Entitäten** die Entität und anschließend [Verwaltete Eigenschaften](create-edit-entities-solution-explorer.md#view-entities) in der Menüleiste aus.  Hiermit wird das Dialogfeld **Festlegen von verwalteten Eigenschaften** geöffnet.

![Festlegen verwalteter Entitätseigenschaften](media/set-managed-properties.png)
  
Entitäten weisen im Vergleich zu allen anderen Lösungskomponenten die meisten verwalteten Eigenschaften auf. Wenn die Entität angepasst werden kann, können Sie folgende Optionen festlegen:  

|Option|Beschreibung|
|--|--|
|**Kann angepasst werden** |Steuert alle anderen Optionen. Wenn diese Option `False` ist, gilt keine der anderen Einstellungen. Wenn sie `True` ist, können Sie die anderen Anpassungsoptionen festlegen. Wenn sie `False` ist, entspricht dies der Festlegung aller anderen Optionen auf „False“.|
|**Anzeigename kann geändert werden**|Gibt an, ob der Anzeigename der Entität geändert werden kann.|
|**Ändern zusätzlicher Eigenschaften möglich** |Gilt für alles, was von anderen Optionen nicht behandelt wird.|
|**Neue Formulare können erstellt werden**|Gibt an, ob neue Formulare für die Entität erstellt werden können.|
|**Neue Diagramme können erstellt werden**|Gibt an, ob neue Diagramme für die Entität erstellt werden können.|
|**Neue Ansichten können erstellt werden** |Gibt an, ob neue Ansichten für die Entität erstellt werden können.|
|**Hierarchische Beziehung kann geändert werden**|Gibt an, ob Einstellungen hierarchischer Beziehungen geändert werden können. Weitere Informationen: [Definieren und Abfragen von hierarchiebezogenen Daten](define-query-hierarchical-data.md)|
|**Änderungsnachverfolgung kann aktiviert werden** |Gibt an, ob die Entitätseigenschaft **Änderungsnachverfolgung** geändert werden kann.|
|**Synchronisierung mit externem Suchindex kann aktiviert werden** |Gibt an, ob die Entität für die Relevanzsuche aktiviert werden kann. Weitere Informationen: [Konfigurieren Sie die Relevanzsuche, um Suchergebnisse und Leistung zu verbessern](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="field-managed-properties"></a>Verwaltete Feldeigenschaften

Weitere Informationen zum Bearbeiten von Feldern finden Sie unter [Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit der PowerApps-Projektmappe](create-edit-field-solution-explorer.md).

Wählen Sie während des [Anzeigens von Feldern](create-edit-field-solution-explorer.md#view-fields) ein benutzerdefiniertes Feld aus einer nicht verwalteten Lösung und dann **Weitere Aktionen** >  **Verwaltete Eigenschaften** in der Menüleiste aus.

![Anzeigen verwalteter Feldeigenschaften](media/view-field-managed-properties-solution-explorer.png)  
  
Hiermit wird das Dialogfeld **Festlegen von verwalteten Eigenschaften** geöffnet.

![Festlegen verwalteter Feldeigenschaften](media/set-field-managed-property.png)

Die Option **Kann angepasst werden** steuert alle anderen Optionen. Wenn diese Option **False** ist, gilt keine der anderen Einstellungen. Wenn sie **True** ist, können Sie die anderen Anpassungsoptionen festlegen.  
  
Wenn das Feld angepasst werden kann, legen Sie die folgenden Optionen auf **True** oder **False** fest.  
  
- **Anzeigename kann geändert werden**
- **Kann Erforderlichkeitsstufe ändern** 
- **Ändern zusätzlicher Eigenschaften möglich**: Diese Eigenschaft steuert alle anderen Anpassungen, die sich nicht auf bestimmte verwaltete Eigenschaften beziehen.

Alle einzelnen Optionen auf **False** festzulegen, ist gleichbedeutend damit, **Kann angepasst werden** auf **False** festzulegen.  

Übernehmen Sie Ihre Auswahl, indem Sie zum Schließen des Dialogfelds auf **Festgelegt** klicken.

> [!NOTE]
> Wenn dieses Feld ein **Datum und Uhrzeit**-Feld ist, ist eine zusätzliche Eigenschaft **Datum- und Uhrzeitverhalten kann geändert werden** verfügbar. Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)

## <a name="relationship-managed-properties"></a>Verwaltete Beziehungseigenschaften

Wählen Sie während des Anzeigens von Entitätsbeziehungen eine Beziehung aus einer nicht verwalteten Lösung und dann **Weitere Aktionen** > **Verwaltete Eigenschaften** in der Menüleiste aus.
  
Bei Beziehungen kann nur die verwaltete Eigenschaft **Kann angepasst werden** verwendet werden. Diese Einstellung steuert alle Änderungen, die an der Entitätsbeziehung vorgenommen werden können. 


### <a name="see-also"></a>Siehe auch

[Verwaltete Eigenschaften](solutions-overview.md#managed-properties)<br />
[Erstellen und Bearbeiten von Entitäten mit dem Projektmappen-Explorer](create-edit-entities-solution-explorer.md)<br />
[Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit der PowerApps-Projektmappe](create-edit-field-solution-explorer.md)<br />
[Erstellen und Bearbeiten von 1:n- oder n:1-Entitätsbeziehungen mit dem Projektmappen-Explorer](create-edit-1n-relationships-solution-explorer.md)<br />
[Erstellen von n:n-Entitätsbeziehungen in Common Data Service für Apps über den Projektmappen-Explorer](create-edit-nn-relationships-solution-explorer.md)