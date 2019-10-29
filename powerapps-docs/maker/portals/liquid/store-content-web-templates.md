---
title: Speichern von Quell Inhalten mithilfe von Webvorlagen in einem Portal | MicrosoftDocs
description: Anweisungen zum Speichern von Inhalten mithilfe von Webvorlagen in einem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2abdf23376cfbcc0b591afe2efb1699144fbef8f
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974527"
---
# <a name="store-source-content-by-using-web-templates"></a>Speichern von Quell Inhalten mithilfe von Webvorlagen

Die Webvorlage ist eine powerapps-Entität (ADX\_WebTemplate), die in den powerapps-Portalen enthalten ist, die zum Speichern von Vorlagen Quell Inhalten verwendet wird. Eine Webvorlage enthält im allgemeinen Liquid für dynamisches Rendern von Inhalten und ist die zentrale Entität, die zur Integration von Liquid-Vorlagen in den Rest des powerapps-Portals-Systems verwendet wird.

Webvorlagen können mithilfe von Vorlagen Tags in andere Inhalte eingeschlossen oder mit anderen Vorlagen kombiniert werden, und in diesen Tags wird anhand Ihres **namens** Attributs auf Sie verwiesen. Sie können auch zum Erstellen ganzer benutzerdefinierter Seitenvorlagen verwendet werden, oder Sie können benutzerdefinierte Kopf-und Fußzeilen für Ihre Portal Website erstellen.

## <a name="web-template-attributes"></a>Webvorlagen Attribute

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Name    |                                                                         Der Name der Vorlage. Wird verwendet, um auf diese Vorlage zu verweisen, wenn Sie in anderen Inhalten enthalten ist, oder von anderen Vorlagen erweitert.                                                                         |
|  Ausgangs   |                                  Der Quell Inhalt der Vorlage. In powerapps wird ein Quell Code-Editor mit Syntax Hervorhebung und anderen Code Bearbeitungs Features für dieses Feld bereitgestellt.                                  |
| MIME-Typ | Stellt optional einen MIME-Typ für den Inhalt der Vorlage bereit. Wenn keine Angabe erfolgt, wird ein Typ von Text/HTML angenommen. Dieser Wert wird nur in Fällen verwendet, in denen die Vorlage mit einer Seitenvorlage verknüpft ist, und das Rendering aller Inhalte für diese Vorlage steuert. |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>Webvorlagen als Seitenvorlagen

Webvorlagen können zusammen mit Seitenvorlagen verwendet werden, um neue Vorlagen für das Inhalts Verwaltungssystem von powerapps-Portalen zu erstellen. Dies kann vollständig innerhalb von powerapps erfolgen, ohne dass Sie .NET-Code schreiben oder Ihre Portal Anwendung erneut bereitstellen müssen.

Wenn Sie eine neue Seitenvorlage basierend auf einer Webvorlage erstellen möchten, wählen Sie beim Erstellen eines neuen Seitenvorlagen Datensatzes eine **Art** Webvorlage aus. Wählen Sie dann eine **Webvorlage**aus.

Beachten Sie die Option **Website Kopfzeile und-Fußzeile verwenden** (standardmäßig aktiviert). Wenn diese Option aktiviert ist, steuert die Webvorlage das Rendern aller Seiteninhalte zwischen der globalen Website Kopfzeile und-Fußzeile. Wenn diese Option deaktiviert ist, ist die Webvorlage für das Rendern der gesamten Antwort verantwortlich, wenn Sie HTML-Code rendern. Dies bedeutet, dass alles zwischen DOCTYPE und Root &lt;HTML-&gt; Tags und alles dazwischen liegt.

Die gängigsten Anwendungsfälle für Webvorlagen sind das Rendern von HTML, das Rendern der gesamten Antwort (durch Deaktivieren der **Verwendung von Website Kopf-und-Fußzeilen**) bietet Ihnen die Möglichkeit, ein beliebiges textbasiertes Format zu rendern. An dieser Stelle wird das **MIME-Typattribut** der Webvorlage als relevant fest. Wenn eine Seitenvorlage, die nicht die Kopf-und Fußzeile der Website verwendet, gerendert wird, wird der HTTP-Antwort-Inhaltstyp-Header auf den MIME-Typ der zugeordneten Webvorlage festgelegt. (Text/HTML wird verwendet, wenn kein MIME-Typ bereitgestellt wird.) Dadurch erhalten Sie eine Vielzahl von Optionen zum Rendern von nicht-HTML-Inhalten mithilfe von Liquid. Ein häufiger Anwendungsfall wäre das Rendering eines [RSS](http://en.wikipedia.org/wiki/RSS) -Feeds, indem der MIME-Typ "Application/RSS + XML" festgelegt wird.  

## <a name="web-templates-as-website-headers-and-footers"></a>Webvorlagen als Website Kopfzeilen und-Fußzeilen

Webvorlagen können auch verwendet werden, um die von einem powerapps-Portal verwendete globale Kopfzeile und Fußzeile zu überschreiben. Legen Sie hierzu das Feld **Header Vorlage** oder **Fußzeilen Vorlage** Ihrer Website auf die Webvorlage Ihrer Wahl fest. Beachten Sie Folgendes: Wenn Sie die **Website Kopfzeile**außer Kraft setzen, übernimmt die ausgewählte Vorlage die Verantwortung für das Rendern der primären Navigations-, Anmeldungs-/Abmelde Links, Suchschnittstelle usw. für Ihre Website Schnittstellen Elemente, die normalerweise vom Standard behandelt werden. Header Vorlage.

## <a name="built-in-web-templates"></a>Integrierte Webvorlagen

In powerapps-Portalen ist eine Reihe von vordefinierten Liquid-Vorlagen verfügbar. Wenn Sie diese verwenden möchten, müssen Sie Sie anhand des Namens einschließen. verwenden Sie dazu die nachstehende Liste als Referenz.

| Name                        | Beschreibung                                                                                                                                                                                                                             | Code                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| Christus                          | Mit dieser Vorlage wird eine Werbe Einblendungs-oder Zufalls Werbung aus einer Ad-Platzierung gerendert.                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| gt                       | Mit dieser Vorlage werden aktuelle Blogbeiträge in einer Listen Gruppe gerendert.                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| Breadcrumbs                 | Diese Vorlage rendert Links von Vorgänger Seiten zurück zur Startseite von der aktuellen Seite.                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| Untergeordnete Link Listen Gruppe       | Mit dieser Vorlage werden Links zu allen untergeordneten Seiten der aktuellen Seite in einer Listen Gruppe gerendert.                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| Ereignisse: demnächst            | Diese Vorlage stellt Links zu Ereignissen dar, die zwischen jetzt und 60 Tagen auftreten.                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| Fan                      | Mit dieser Vorlage wird eine Liste der Foren der Website mit ihrer jeweiligen Anzahl von Threads und Beiträgen gerendert.                                                                                                                                 | `{% include 'forums' %}`                                       |
| Spalte Layout 1             | Diese Vorlage rendert ein einzelnes Spalten Layout, das Brotkrümel-, Seitentitel-und Seiten Kopier Inhalte enthält.                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| Layout 2 Spalten weit links   | Mit dieser Vorlage wird ein zwei Spalten Layout gerendert. Die linke Spalte ist breiter als die Rechte Spalte. Sie enthält Brotkrümel, Seitentitel am oberen Rand der Seite, und der Inhalt der Seiten Kopie befindet sich in der linken Spalte.                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| Layout 2 Spalten weit rechts  | Mit dieser Vorlage wird ein zwei Spalten Layout gerendert. Die Rechte Spalte ist breiter als die linke. Sie enthält Brotkrümel, Seitentitel am oberen Rand der Seite, und der Inhalt der Seiten Kopie befindet sich in der rechten Spalte.                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| Layout 3 Spalten weite Mitte | Diese Vorlage rendert ein Layout mit drei Spalten. Die mittlere Spalte ist breiter als die linke und die Rechte. Das Layout enthält Brotkrümel und den Seitentitel am oberen Rand der Seite, und der Inhalt der Seiten Kopie befindet sich in der mittleren Spalte.   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| Seiten Kopie                   | Mit dieser Vorlage wird der bearbeitbare HTML-Inhalt der Seite kopiert und unterstützt eingebettete Liquid-Inhalte.                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| Seiten Kopfzeile                 | Mit dieser Vorlage wird der Seitentitel gerendert.                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| Umfrage                        | Mit dieser Vorlage wird ein Abruf nach Namen oder ein zufälliger Abruf aus einer Abruf Platzierung gerendert.                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| Search                      | Mit dieser Vorlage wird ein einfaches Suchformular mit einer einzelnen Texteingabe und einer Such Schaltfläche gerendert.                                                                                                                                                   | `{% include 'search' %}`                                                             |
| Seiten Navigation             | Mit dieser Vorlage wird eine vertikale Strukturansicht für die Navigation gerendert. Sie enthält Links zu den Vorgänger Seiten zurück zur ersten Ebene (oder zum angegebenen tiefen Offset), Links zu gleich geordneten Seiten der aktuellen Seite und Links zu untergeordneten Elementen der aktuellen Seite. | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| Ausschnitt                     | Mit dieser Vorlage wird ein bearbeitbarer HTML-Inhalts Ausschnitt nach Name gerendert.                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| Obere Navigation              | Mit dieser Vorlage wird eine bearbeitbare Navigationsleiste mit Dropdown Menüs für den primären Navigations-weblinksatz gerendert.                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Weblink-Listen Gruppe          | Mit dieser Vorlage wird eine Listen Gruppe von Links für einen weblinksatz gerendert.                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>Siehe auch

[Grundlegendes zu Liquid](liquid-operators.md)  
[Liquid-Typen](liquid-types.md)  
[Conditional](liquid-conditional-operators.md)  
[Liquid-Objekte](liquid-objects.md)  
[Liquid-Tags](liquid-tags.md)  
[Liquid-Filter](liquid-filters.md)  
