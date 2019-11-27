---
title: Verwenden einer Facettensuche, um die Portalsuche zu verbessern | MicrosoftDocs
description: Anleitungen zum Aktivieren oder Deaktivieren der facettierten Suche.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6b605acf1d11ecbc98760810f390f63c9a27a0a6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760448"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>Verwenden einer facettierten Suche, um die Portalsuche zu verbessern

Portalinhalt wird mithilfe von Filtern basierend auf den Eigenschaften des Inhalts gesucht. Durch die von der facettierten Portalsuche implementierten Filter können Kunden gewünschte Inhalte schneller als mit der traditionellen Suche finden.

## <a name="enable-or-disable-faceted-search"></a>Aktivieren oder Deaktivieren der facettierten Suche

Die standardmäßige facettierte Suche ist in Ihren Portalen aktiviert. Führen Sie die folgenden Schritte aus, um diese zu steuern und/oder zu aktivieren:

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md) und navigieren Sie zu **Portale** &gt; **Website** &gt; **Website-Einstellungen**.
2. Wählen Sie die Standortseinstellung **Suchen/FacetedView** aus. 
3. Ändern Sie für die Aktivierung den **Wert** in **True** und in **False** für die Deaktivierung der facettierten Suche.

So deaktivieren Sie ein Einzelstück für die facettierte Ansicht:

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md) und navigieren Sie zu **Portale** &gt; **Webvorlagen**.
2. Ansicht zum Deaktivieren auswählen (d. h. Wissensmanagement – Am besten bewertete Artikel)
3. Klicken Sie oben auf der Seite auf **Deaktivieren**.

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>Gruppieren von Entitäten im Rahmen eines Datensatztyps für die facettierte Ansicht

Die Websiteeinstellung **Suche/RecordTypeFacetsEntities** ermöglicht Ihnen, ähnliche Entitäten zusammen zu gruppieren, sodass Benutzer logische Möglichkeiten zum Filtern von Suchergebnissen haben. Beispiel: Anstelle separater Optionen für Foren, Forumsnachrichten und Forumthreads werden diese Entitäten unter dem Forumsdatensatztyp zusammengefasst.

Navigieren Sie zu **Portale** &gt; **Websites** &gt; **Website-Einstellungen** und öffnen Sie die Website-Einstellung **Suche/RecordTypeFacetsEntities**. 

Beachten Sie, dass den verschiedenen Entitäten das Wort **Foren** vorangestellt ist. Dies ist darauf zurückzuführen, dass der erste Wert der Name ist unter dem sie gruppiert sind. Dieses Wort wird entsprechend der im Portal verwendeten Sprache übersetzt.

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>Verwenden einer facettierten Suche, um die Wissen-Sucherergebnisse zu verbessern

Die facettierte Suche aktiviert Portale, um Suchfilter links zur Verfügung zu stellen, sodass Sie zwischen Elementen wie Foren, Blogs und Wissensartikel wählen können. Mehr Filter werden für bestimmte Suchtypen hinzugefügt. So können beispielsweise Wissensartikel nach Datensatztyp, Änderungsdatum, Bewertung und Produkte gefiltert werden, damit Kunden gewünschte Inhalte finden. Die rechte Seite bietet auch ein Dropdownfeld, das Ergebnisse basierend auf der Auswahl des Kunden von Relevanz oder Anzahl der Ansichten (bestimmte Wissensartikel) sortiert. Unten finden Sie einen Snapshot mit einem Beispiel verfügbarer Filter.

![Verwenden von Filtern zur Verbesserung der Suchergebnisse](../media/faceted-search-filter.png "Verwenden von Filtern zur Verbesserung der Suchergebnisse")
