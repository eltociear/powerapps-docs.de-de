---
title: Speichern von Quellinhalten mithilfe von Webvorlagen auf einem Portal | MicrosoftDocs
description: Anweisungen, Inhalte mithilfe von Internet-Vorlagen auf einem Portal zu speichern.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 76c8e525c5d5b612e055da9c43e14df55cec6e4f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757090"
---
# <a name="store-source-content-by-using-web-templates"></a>Quellinhalt mithilfe von Webvorlagen speichern

Die Webvorlage ist eine PowerApps-Entität (adx\_webtemplate), die in PowerApps-Portalen enthalten ist und zur Speicherung von Vorlagenquellinhalten verwendet wird. Eine Webvorlage enthält im Allgemeinen Liquid-Elemente zum Rendern von dynamischen Inhalten und ist die zentrale Entität für die Integration von Liquid-Vorlagen mit dem Rest des PowerApps-Portalsystems.

Webvorlagen können in andere Inhalte eingeschlossen werden oder über Vorlagentags mit anderen Vorlagen kombiniert werden. Auf sie wird in diesen Tags über ihre Attribute **Name** verwiesen. Sie können außerdem verwendet werden, um ganze benutzerdefinierte Seitenvorlagen oder benutzerdefinierte Kopfzeilen und Fußzeilen für Ihre Portalwebsite zu erstellen.

## <a name="web-template-attributes"></a>Webvorlagenattribute

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Name    |                                                                         Der Name der Vorlage. Wird verwendet, um auf diese Vorlage zu verweisen wenn sie in anderen Inhalten enthalten ist oder durch andere Vorlagen erweitert wird.                                                                         |
|  Quelle   |                                  Der Quellinhalt der Vorlage. In PowerApps steht ein Quellcode-Editor mit Syntax-Hervorhebung und anderen Funktionen zur Codebarbeitungen für dieses Feld bereit.                                  |
| MIME-Typ | Stellt optional einen MIME-Typ für die Inhalte der Vorlage zur Verfügung. Wenn keiner bereitgestellt wird, wird ein Typ von „text/html” angenommen. Dieser Wert wird nur verwendet, wenn die Vorlage einer Seitenvorlage zugeordnet ist und das Rendering aller Inhalte diese Vorlage steuert. |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>Webvorlagen als Seitenvorlagen

Webvorlagen können in Verbindung mit Seitenvorlagen können verwendet werden, um neue Vorlagen für das Content-Management-System des PowerApps-Portals zu erstellen. Dies kann komplett in PowerApps durchgeführt werden, ohne, dass .NET-Code geschrieben oder die Portalanwendung neu bereitstellt werden muss.

Um eine neue Seitenvorlage basierend auf einer Webvorlage zu erstellen, wählen Sie einen **Typ** von Webvorlage aus, wenn ein neuer Seitenvorlagendatensatz erstellt wird. Wählen Sie dann **Webvorlage** aus.

Beachten Sie die Option **Kopf- und Fußzeile der Website verwenden**(standardmäßig aktiviert). Wenn die Option aktiviert ist, steuert Ihre Webvorlage das Rendering aller Seiteninhalte zwischen der Kopf- und Fußzeile der Website. Wenn diese Option deaktiviert ist, ist Ihr Webvorlage für das Rendern des gesamten Antwort verantwortlich. Falls Sie HTML rendern bezieht sich dies auf alles vom doctype bis zu den Stamm-&lt;html&gt;-Tags und auf alle Elemente dazwischen.

Der häufigste Einsatzfall für Webvorlagen ist das Rendern von HTML. Das Rendern der gesamten Antwort (über das Deaktivieren von **Kopf- und Fußzeile der Website verwenden**) bietet Ihnen jedoch auch die Option alle gewünschten textbasierten Formate zu rendern. Hier wird das Attribut **MIME-Typ** der Webvorlage relevant. Wenn eine Seitenvorlage, die die Websitekopfzeile und -fußzeile nicht verwendet, gerendert wird, wird die Inhaltstyp-Kopfzeile der HTTP-Antwort auf den MIME-Typ der zugeordneten Webvorlage festgelegt. (text/html wird verwendet, wenn kein MIME-Typ bereitgestellt ist.) Dies bietet Ihnen eine breite Auswahl von Optionen zum Rendern von Nicht-HTML-Inhalt mithilfe von Liquid. Ein häufiger Anwendungsfall wäre das Rendern eines [RSS](https://en.wikipedia.org/wiki/RSS)-Feeds, indem ein MIME-Typ auf application/rss+xml festgelegt wird.  

## <a name="web-templates-as-website-headers-and-footers"></a>Webvorlagen als Websitekopfzeilen und - fußzeilen

Webvorlagen können auch verwendet werden, um die globalen Kopf- und Fußzeilen außer Kraft zu setzen, die von einem PowerApps-Portal verwendet werden. Legen Sie hierzu das Feld **Kopfzeilenvorlage** oder **Fußzeilenvorlage** der Website auf die gewünschte Webvorlage fest. Beachten Sie, dass wenn Sie **Websitekopfzeile** außer Kraft setzen, Ihre ausgewählte Vorlage für das Rendern der primären Navigation, die Anmelde- und Abmeldelinks, die Suchschnittstelle usw. für Ihre Websiteschnittstellen-Elemente zuständig ist, die normalerweise von der Standard-Kopfzeilenvorlage gehandhabt werden.

## <a name="built-in-web-templates"></a>Integrierte Webvorlagen

Es gibt eine Reihe von vorgefertigten Liquid-Vorlagen in den PowerApps-Portalen. Um sie zu verwenden, müssen Sie sie über den Namen mithilfe der unten folgenden Liste als Referenz einbinden.

| Name                        | Beschreibung                                                                                                                                                                                                                             | Code                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| Anzeige                          | Diese Vorlage rendert eine Anzeige nach Namen oder eine zufällige Anzeige aus einer Anzeigenplatzierung.                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| Blogs                       | Diese Vorlage rendert kürzlich erfolgte Blogbeiträge in einer Listengruppe.                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| Breadcrumbs                 | Diese Vorlage rendert Links aus Vorgängerseiten von der aktuellen Seite zurück auf die Startseite.                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| Listengruppe der untergeordneten Links       | Diese Vorlage rendert Links auf untergeordnete Seiten von der aktuellen Seite in einer Listengruppe.                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| Ereignisse: Anstehend            | Diese Vorlage rendert Links zu Ereignissen, die zwischen dem heutigen Datum und 60 Tagen in der Zukunft auftreten.                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| Foren                      | Diese Vorlage rendert eine Liste der Websiteforen mit entsprechender Anzahl von Threads und Beiträgen.                                                                                                                                 | `{% include 'forums' %}`                                       |
| Layout 1: Spalte             | Diese Vorlage rendert ein Layout mit einer einzelnen Spalte, das Breadcrumbs, Seitentitel und Seitenkopieinhalte enthält.                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| Layout 2: Linke Spalte breit   | Diese Vorlage rendert ein Layout mit zwei Spalten. Die linke Spalte als breiter ist die rechte. Sie enthält Breadcrumbs, Seitentitel oben auf der Seite und die Seiteninhalte in der linken Spalte.                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| Layout 2: Rechte Spalte breit  | Diese Vorlage rendert ein Layout mit zwei Spalten. Die rechte Spalte als breiter ist die linke. Sie enthält Breadcrumbs, Seitentitel oben auf der Seite und die Seiteninhalte in der rechten Spalte.                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| Layout 3: Mittlere Spalte breit | Diese Vorlage rendert ein Layout mit drei Spalten. Die mittlere Spalte als breiter ist die linke und rechte. Das Layout enthält Breadcrumbs und den Seitentitel oben auf der Seite und die Seiteninhalte befinden sich in der mittleren Spalte.   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| Seitenkopie                   | Diese Vorlage rendert bearbeitbare HTML-Seitenkopieinhalte mit Unterstützung für eingebettetes Liquid-Markup.                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| Seitenkopfzeile                 | Diese Vorlage rendert den Seitentitel.                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| Umfrage                        | Diese Vorlage rendert eine Umfrage nach Namen oder eine zufällige Umfrage aus einer Umfrageplatzierung.                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| Suchen                      | Diese Vorlage rendert ein grundlegendes Suchformular mit einem einzelnen Texteingabefeld und einer Suchschaltfläche.                                                                                                                                                   | `{% include 'search' %}`                                                             |
| Seitliche Navigation             | Diese Vorlage rendert eine vertikale Navigation in der Art einer Strukturansicht. Sie umfasst Links zu Vorgängerseiten und zur obersten Ebene (oder einem festgelegten Offset), Links zu Geschwisterseiten der aktuellen Seite sowie Links zu untergeordneten Seiten der aktuellen Seite. | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| Ausschnitt                     | Diese Vorlage rendert einen bearbeitbaren HTML-Inhaltsausschnitt nach Namen.                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| Obere Navigation              | Diese Vorlage rendert eine bearbeitbare Navigationsleiste mit Dropdownmenüs für den primären Navigations-Weblinksatz.                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Weblink-Listengruppe          | Diese Vorlage rendert eine Listengruppe von Links für einen Weblinksatz.                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>Siehe auch

[Lernen Sie Liquid-Operatoren kennen](liquid-operators.md)  
[Liquid-Typen](liquid-types.md)  
[Bedingt](liquid-conditional-operators.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
