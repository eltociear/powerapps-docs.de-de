---
title: Verwaltete Eigenschaften in Common Data Service-Metadaten festlegen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie verwaltete Eigenschaften für Metadatenelemente in einer Lösung festlegen können.
ms.custom: ''
ms.date: 03/03/2020
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
ms.openlocfilehash: 0f75c9c38b3fbd74f330de5e80a2c0f7df8d6e13
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "3124955"
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>Verwaltete Eigenschaften in Common Data Service-Metadaten festlegen 
Sie können steuern, welche der von Ihnen verwalteten Lösungskomponenten mithilfe von verwalteten Eigenschaften anpassbar sind. ISVs sollten die Anpassung von Lösungskomponenten ermöglichen, wenn dies sinnvoll ist. Damit können Organisationen Ihre Lösung entsprechend ihren eindeutigen Anforderungen anpassen. Schränken Sie Anpassung von kritischen Lösungskomponenten, die die Kernfunktionen Ihrer Lösung sicherstellen ein oder lassen Sie diese nicht zu, sodass Sie diese vorhersagbar unterstützen und verwalten können. Für die meisten Nicht-ISV-Entwicklungsumgebungen empfehlen wir, dass Sie keine Anpassung für Ihre verwaltete Lösung-Komponenten zulassen. 

Verwaltete Eigenschaften dienen dazu, Ihre Lösung vor Änderungen zu schützen, die möglicherweise die Funktion unterbrechen. Verwaltete Eigenschaften bieten keine digitale Rechteverwaltung (DRM) oder Möglichkeiten, Ihre Lösung oder Steuerung, die Sie installieren, zu lizenzieren.

Sie wenden verwaltete Eigenschaften an, wenn die Lösung in der nicht verwalteten Ebene Ihrer Entwicklungsumgebung nicht verwaltet wird. Die verwalteten Eigenschaften werden erst nach dem Packen und der Installation der verwalteten Lösung in einer anderen Umgebung wirksam. Nachdem die verwaltete Lösung importiert ist, können verwaltete Eigenschaften nicht mehr aktualisiert werden, außer durch eine Aktualisierung durch den ursprünglichen Herausgeber. 

Die meisten Lösungskomponenten verfügen über ein Menü **Verwaltete Eigenschaften**, wenn eine Liste der Lösungskomponenten angezeigt wird. Wenn Sie die verwaltete Lösung importieren, die die Komponenten enthält, können Sie deren verwaltete Eigenschaften anzeigen, aber nicht ändern.

## <a name="view-and-edit-entity-managed-properties"></a>Bearbeiten und anzeigen von verwalteten Eigenschaften
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und wählen Sie **Lösungen** aus der linken Navigation aus. 
2.  Öffnen Sie die gewünschte Lösung. 
3.  Wählen Sie aus der Liste der Komponenten die Lösung und wählen Sie **...** Klicken Sie neben der Entität, für die Sie die verwalteten Eigenschaften anzeigen möchten und wählen dann **Verwaltete Eigenschaften**. 

    > [!div class="mx-imgBorder"] 
    > ![Von der Entität verwaltete Befehlseigenschaft](media/entity-managed-properties.png "Von der Entität verwaltete Befehlseigenschaft")

    Die Seite mit den verwalteten Eigenschaften wird angezeigt. 

    > [!div class="mx-imgBorder"] 
    > <img src="media/managed-properties-dialog.png" alt="Managed properties pane" height="572" width="300">

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

## <a name="view-and-edit-field-managed-properties"></a>Bearbeiten und anzeigen von verwalteten Feldeigenschaften
Neben einem benutzerdefinierten Feld in einer Lösung wählen Sie **...** Und dann wählen Sie **Verwaltete Eigenschaften**.

Der Bereich für **Verwaltete Eigenschaften** öffnet sich.
> [!div class="mx-imgBorder"] 
> <img src="media/field-managed-prop.png" alt="Field managed properties" height="525" width="295">

Die Option **Anpassungen zulassen** steuert alle anderen Optionen. Wenn diese Option deaktiviert ist, gelten keine der anderen Einstellungen. Wenn sie aktviiert ist, können Sie die anderen Anpassungsoptionen angeben.  
  
Wenn das Entität Feld angepasst werden kann, können Sie die folgenden Optionen aktivieren.  
  
- **Anzeigename kann geändert werden**
- **Kann zusätzliche Eigenschaften ändern**: Diese Eigenschaft steuert alle anderen Anpassungen, die keine bestimmte verwaltete Eigenschaft haben. 
- **Neue Formulare können erstellt werden** 
- **Neue Diagramme können erstellt werden** 
- **Neue Ansichten können erstellt werden** 
- **Hierarchische Beziehung kann geändert werden** 
- **Kann die Änderungsnachverfolgung aktiviert werden** 
- **Kann Synchronisierung mit externem Suchindex aktivieren**

Das Deaktivieren aller einzelnen Optionen entspricht dem Deaktivieren **Anpassungen zulassen**.  

Wenden Sie Ihre Auswahl an und wählen Sie **Erledigt**, um das Fenster zu schließen.

> [!NOTE]
> Wenn dieses Feld ein **Datum und Uhrzeit**-Feld ist, steht eine zusätzliche Eigenschaft **Kann das Datums- und Uhrzeitverhalten ändern** zur Verfügung. Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md) 

Weitere Informationen zum Bearbeiten von Feldern finden Sie unter [Erstellen und Bearbeiten von Feldern für Common Data Service mit Power Apps-Lösungs-Explorer](create-edit-field-solution-explorer.md).

## <a name="view-and-edit-other-component-managed-properties"></a>Bearbeiten und anzeigen von anderen verwalteten Komponenteneigenschaften
Sie können verwaltete Eigenschaften für viele andere Lösungskomponenten anzeigen und bearbeiten, z. B. eine Webressource, einen Prozess, ein Diagramm oder ein Dashboard. Neben der Komponente in einer Lösung wählen Sie **...** Und dann wählen Sie **Verwaltete Eigenschaften**. 

## <a name="view-and-edit-relationship-managed-properties"></a>Bearbeiten und anzeigen von verwalteten Beziehungseigenschaften
Wählen Sie beim Anzeigen von Entitätsbeziehungen in einem [Lösungs-Explorer](../model-driven-apps/advanced-navigation.md#solution-explorer) eine Beziehung aus einer nicht verwalteten Lösung aus, und wählen Sie dann **Weitere Aktionen** > **Verwaltete Eigenschaften** in der Menüleiste.
  
Bei Beziehungen ist die einzige verwaltete Eigenschaft **Kann angepasst werden**. Diese Einstellung steuert alle Änderungen, die an der Entitätsbeziehung vorgenommen werden können. 

### <a name="see-also"></a>Siehe auch

[Exportieren von Lösungen](export-solutions.md) <br />
[Überblick über Lösungen](solutions-overview.md)

