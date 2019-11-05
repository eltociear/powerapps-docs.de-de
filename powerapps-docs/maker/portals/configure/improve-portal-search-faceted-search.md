---
title: Verwenden der Facetten Suche zur Verbesserung der Portal Suche | MicrosoftDocs
description: Anweisungen zum Aktivieren oder Deaktivieren der Facetten Suche.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552334"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>Verwenden der Facetten Suche zur Verbesserung der Portal Suche

Der Portal Inhalt kann mithilfe von Filtern durchsucht werden, die auf den Merkmalen des Inhalts basieren. Die durch die Suche im Facetten Portal implementierten Filter ermöglichen es Kunden, den gewünschten Inhalt schneller zu finden als eine herkömmliche Suche.

## <a name="enable-or-disable-faceted-search"></a>Aktivieren oder Deaktivieren der Facetten Suche

Die Standard basierte Facetten Suche ist in Ihren Portalen aktiviert. Führen Sie die folgenden Schritte aus, um Sie zu steuern oder zu aktivieren:

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md) , und navigieren Sie zu **Portale** &gt; **Website** &gt; **Website Einstellungen**.
2. Wählen Sie die Site Einstellung **Search/facetedview** aus. 
3. Ändern Sie den **Wert** in **true** , um "enable" oder " **false** " zu aktivieren.

So deaktivieren Sie einen einzelnen Teil der Facetten Ansicht:

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md) , und navigieren Sie zu **Portale** &gt; **Webvorlagen**.
2. Wählen Sie die zu deaktivierende Ansicht (d. h. Wissensverwaltung – Artikel mit der höchsten Bewertung)
3. Klicken Sie oben auf der Seite auf **Deaktivieren** .

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>Gruppieren von Entitäten als Teil eines Daten Satz Typs für die Facetten Ansicht

Mit der Site setting **Search/recordtypefaketsentities** können Sie ähnliche Entitäten gruppieren, sodass Benutzer logische Methoden zum Filtern von Suchergebnissen haben. Wenn Sie z. b. keine separaten Optionen für Foren, Forumsbeiträge und Forenthreads haben, werden diese Entitäten unter dem Daten Satz des Forums Typs gruppiert.

Wechseln Sie zu **Portale** &gt; **Websites** &gt; **Website Einstellungen** , und öffnen Sie die Website Einstellung **Search/recordtypefaketsentities** . 

Beachten Sie, dass die verschiedenen Entitäten den Word-Foren vorangestellt sind **:** . Dies liegt daran, dass der erste Wert der Name ist, mit dem Sie gruppiert sind. Dieses Wort wird basierend auf der Sprache übersetzt, die im Portal verwendet wird.

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>Verwenden der Facetten Suche zur Verbesserung der Wissens Suchergebnisse

Die Facetten Suche ermöglicht es Portalen, Suchfilter auf der linken Seite zu haben, die es Ihnen ermöglichen, zwischen Elementen wie Foren, Blogs und Wissens Daten Bank Artikeln auszuwählen. Für bestimmte Suchtypen werden weitere Filter hinzugefügt. Wissens Daten Bank Artikel können z. b. nach Daten Aufgabentyp, Änderungsdatum,-Bewertung und-Produkten gefiltert werden, um Kunden bei der Suche nach benötigten Inhalten zu unterstützen. Die Rechte Seite verfügt auch über ein Dropdown-Feld, das die Ergebnisse sortiert, basierend auf der Auswahl der Relevanz oder der Ansichts Anzahl (spezifisch für Wissens Daten Bank Artikel). Im folgenden finden Sie eine Bildschirmaufnahme mit einem Beispiel für einige der verfügbaren Filter.

![Verwenden von Filtern zum Verbessern von Suchergebnissen](../media/faceted-search-filter.png "Verwenden von Filtern zum Verbessern von Suchergebnissen")
