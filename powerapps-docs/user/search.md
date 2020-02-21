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
ms.locfileid: "76828590"
---
# <a name="compare-search-options-in-common-data-service"></a>Vergleich der Suchoptionen in Common Data Service

Datensätze in Common Data Service können auf drei Arten durchsucht werden:

-   Relevanzsuche   
  
-   Schnellsuche (einzelne Entität oder mehrere Entitäten)  

-   Erweiterte Suche

> [!NOTE]
> Die Schnellsuche mit mehreren Entitäten wird auch als Suche nach Kategorien bezeichnet. 
  
Die folgende Tabelle enthält eine kurze Gegenüberstellung der drei Optionen:

|Funktionalität|[Relevanzsuche](relevance-search.md)|[Schnellsuche](quick-find.md)|[Erweiterte Suche](advanced-find.md)|  
|-------------------|---------------------------|----------------|-------------------|  
|Standardmäßig aktiviert?|Nein. Muss von einem Administrator manuell aktiviert werden.|Ja|Ja|  
|Suchbereich: einzelne Entität|Nicht in einem Entitätsraster verfügbar. Die Suchergebnisse können auf der Ergebnisseite nach einer Entität gefiltert werden.|In einem Entitätsraster verfügbar.|In einem Entitätsraster verfügbar.|  
|Suchbereich: mehrere Entitäten|Sie können beliebig viele Entitäten durchsuchen. **Hinweis**:  Sie können zwar beliebig viele Entitäten durchsuchen, vom Filter für den Datensatztyp werden jedoch nur Daten für zehn Entitäten angezeigt.|Durchsucht bis zu zehn Entitäten (gruppiert durch eine Entität).|Keine Suche mit mehreren Entitäten verfügbar.|  
|Suchverhalten|Sucht in sämtlichen Feldern der Entität nach Übereinstimmungen für ein beliebiges Wort aus dem Suchbegriff.|Sucht in einem einzelnen Feld einer Entität nach Übereinstimmungen für alle Wörter im Suchbegriff ohne Berücksichtigung der Wortreihenfolge im Feld.|Abfrage-Generator zum Definieren von Suchkriterien für den ausgewählten Datensatztyp. Kann auch verwendet werden, um Daten für den Export in Office Excel vorzubereiten, damit Sie sie dort analysieren, zusammenfassen oder aggregieren können. Eine weitere Möglichkeit ist die Erstellung von PivotTables, um Ihre Daten aus verschiedenen Blickwinkeln zu betrachten.|  
|Durchsuchbare Felder|Textfelder wie einzelne Textzeilen, mehrere Textzeilen, Nachschlagefelder und Optionssätze. Die Suche in numerischen Feldern oder Datumsfeldern wird nicht unterstützt.|Alle durchsuchbaren Felder.|Alle durchsuchbaren Felder.|  
|Suchergebnisse|Gibt die Suchergebnisse in einer einzelnen, nach Relevanz sortierten Liste zurück.|Bei einer einzelnen Entität werden die Suchergebnisse in einem Entitätsraster zurückgegeben. Bei mehreren Entitäten werden die zurückgegebenen Suchergebnisse nach Kategorien gruppiert (beispielsweise nach Konten, Kontakten oder Leads).|Gibt die Suchergebnisse des ausgewählten Datensatztyps mit den von Ihnen angegebenen Spalten in der von Ihnen konfigurierten Sortierreihenfolge zurück.|
|Platzhalter (*)|Nachgestellter Platzhalter für Wortvervollständigung wird unterstützt.|Vorangestellter Platzhalter wird unterstützt. Nachgestellter Platzhalter wird standardmäßig hinzugefügt.|Wird nicht unterstützt.|  
