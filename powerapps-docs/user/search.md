---
title: Suchoptionen in Common Data Service | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/27/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 440241571f716fa1931b5c11935c70de5c85e7ee
ms.sourcegitcommit: 5bfd0448f1d5ca3d938e3bd928d1dd3d4042afff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2020
ms.locfileid: "3303022"
---
# <a name="compare-search-options-in-common-data-service"></a>Vergleichen von Suchoptionen in Common Data Service

Dazu gibt es drei Möglichkeiten zum Suchen von Datensätzen in Common Data Service:

-   Relevanzsuche   
  
-   Schnellsuche (einzelne Entität oder mehrere Entitäten)  

-   Erweiterte Suche

> [!NOTE]
> Die Schnellsuche mit mehreren Entitäten wird auch als Suche nach Kategorien bezeichnet. 
  
Die folgende Tabelle enthält eine kurze Gegenüberstellung der drei Optionen:

|Funktionalität|[Relevanzsuche](relevance-search.md)|[Schnellsuche](quick-find.md)|[Erweiterte Suche](advanced-find.md)|  
|-------------------|---------------------------|----------------|-------------------|  
|Standardmäßig aktiviert?|Nr. Muss von einem Administrator manuell aktiviert werden.|Ja|Ja|  
|Suchbereich: einzelne Entität|Nicht verfügbar in einem Entitätsraster. Sie können die Suchergebnisse nach einer Entität auf der Ergebnisseite filtern.|Verfügbar in einem Entitätsraster.|Verfügbar in einem Entitätsraster.|  
|Suchbereich für mehrere Entitäten|Es gibt keine Höchstgrenze für die Anzahl der Entitäten, die Sie suchen können. **Hinweis:** Wenn keine Höchstgrenze auf der Anzahl Entitäten vorhanden ist, kann die Suche ausgeführt werden. Der Datensatzfilter zeigt nur 10 Entitäten an.|Durchsucht bis zu zehn Entitäten (gruppiert durch eine Entität).|Keine Suche mit mehreren Entitäten verfügbar.|  
|Suchverhalten|Sucht nach Übereinstimmungen für jedes Wort im Suchbegriff in jedem Entitätsfeld.|Sucht in einem einzelnen Feld einer Entität nach Übereinstimmungen für alle Wörter im Suchbegriff ohne Berücksichtigung der Wortreihenfolge im Feld.|Abfrage-Generator zum Definieren von Suchkriterien für den ausgewählten Datensatztyp. Kann außerdem verwendet werden, um Daten für den Export nach Office Excel vorzubereiten, sodass Sie Daten analysieren, zusammenfassen oder aggregieren können, oder PivotTables erstellen, um die Daten in verschiedenen Perspektiven anzuzeigen.|  
|Suchbare Felder|Textfelder wie einzelne Textzeilen, mehrere Textzeilen, Suchen und Optionssätze. Die Suche in numerischen Feldern oder Datumsfeldern wird nicht unterstützt.|Alle durchsuchbaren Felder.|Alle durchsuchbaren Felder.|  
|Suchergebnisse|Gibt die Suchergebnisse nach Relevanz zurück, in einer einzelnen Liste.|Gibt die Suchergebnisse für eine einzelne Entität in einem Entitätsraster zurück. Gibt die Suchergebnisse für mehrere Entitäten nach Kategorien gruppiert zurück, beispielsweise nach Firmen, Kontakten oder Leads.|Gibt Suchergebnisse des ausgewählten Datensatztyps mit den Spalten, die Sie angegeben haben, in der Sortierreihenfolge, die Sie konfiguriert haben, zurück.|
|Platzhalter (*)|Nachfolgender Platzhalter wird für die Wortvervollständigung unterstützt.|Vorangestellter Platzhalter wird unterstützt. Nachgestellter Platzhalter wird standardmäßig hinzugefügt.|Nicht unterstützt.|  
