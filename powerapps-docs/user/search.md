---
title: Suchoptionen in Common Data Service | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2020
ms.locfileid: "76828590"
---
# <a name="compare-search-options-in-common-data-service"></a>Vergleichen von Suchoptionen in Common Data Service

Es gibt drei Möglichkeiten, Datensätze in Common Data Service zu durchsuchen:

-   Relevanzsuche   
  
-   Schnellsuche (einzelne Entität oder mehrere Entitäten)  

-   Erweiterte Suche

> [!NOTE]
> Die Schnellsuche mit mehreren Entitäten wird auch als kategorisierte Suche bezeichnet. 
  
In der folgenden Tabelle finden Sie einen kurzen Vergleich der drei Optionen.

|Funktion|[Relevanzsuche](relevance-search.md)|[Schnellsuche](quick-find.md)|[Erweiterte Suche](advanced-find.md)|  
|-------------------|---------------------------|----------------|-------------------|  
|Standardmäßig aktiviert?|Nein. Ein Administrator muss ihn manuell aktivieren.|Ja|Ja|  
|Suchbereich für einzelne Entitäten|Nicht in einem Entitäts Raster verfügbar. Sie können die Suchergebnisse nach einer Entität auf der Seite Ergebnisse filtern.|Verfügbar in einem Entitäts Raster.|Verfügbar in einem Entitäts Raster.|  
|Suchbereich für mehrere Entitäten|Es gibt keine maximale Beschränkung für die Anzahl der Entitäten, die Sie durchsuchen können. **Hinweis:**  Es gibt zwar keine maximale Beschränkung für die Anzahl der Entitäten, die Sie durchsuchen können, aber der Daten Satz-Typfilter zeigt nur Daten für 10 Entitäten an.|Sucht bis zu 10 Entitäten, gruppiert nach einer Entität.|Die Suche in mehreren Entitäten ist nicht verfügbar.|  
|Suchverhalten|Findet Übereinstimmungen mit einem beliebigen Wort im Suchbegriff in einem beliebigen Feld in der Entität.|Findet Übereinstimmungen für alle Wörter im Suchbegriff in einem Feld in einer Entität. die Wörter können jedoch in beliebiger Reihenfolge im Feld abgeglichen werden.|Der Abfrage-Generator, in dem Sie Suchkriterien für den ausgewählten Daten Satz Typ definieren können. Kann auch zum Vorbereiten von Daten für den Export in Office Excel verwendet werden, um Daten zu analysieren, zusammenzufassen oder zu aggregieren oder um PivotTables zu erstellen, um Ihre Daten aus verschiedenen Perspektiven anzuzeigen.|  
|Durchsuchbare Felder|Textfelder wie eine Textzeile, mehrere Textzeilen, Lookups und Optionssätze. Unterstützt nicht das Suchen in Feldern vom Typ "numeric" oder "Date".|Alle durchsuchbaren Felder.|Alle durchsuchbaren Felder.|  
|Suchergebnisse|Gibt die Suchergebnisse in der Reihenfolge ihrer Relevanz in einer einzigen Liste zurück.|Gibt bei einer einzelnen Entität die Suchergebnisse in einem Entitäts Raster zurück. Gibt für mehrere Entitäten die Suchergebnisse nach Kategorien gruppiert zurück, z. b. Konten, Kontakte oder Leads.|Gibt die Suchergebnisse des ausgewählten Daten Satz Typs mit den von Ihnen angegebenen Spalten in der von Ihnen konfigurierten Sortierreihenfolge zurück.|
|Platzhalter (*)|Nach gestellte Platzhalter für Wortvervollständigung wird unterstützt.|Führender Platzhalter unterstützt. Der nachfolgende Platzhalter ist standardmäßig hinzugefügt|Nicht unterstützt.|  
