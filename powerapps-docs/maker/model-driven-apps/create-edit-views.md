---
title: Erstellen oder bearbeiten der Ansicht einer modellgesteuerten App in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Ansicht erstellt oder bearbeitet wird.
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
ms.openlocfilehash: 215f927b68decac864a2f1b667f64a7649827682
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39686650"
---
# <a name="understand-model-driven-app-views"></a>Grundlegendes zu Komponenten von modellgesteuerten Apps

<a name="BKMK_CreatingAndEditingViews"></a>   

Mit PowerApps-Apps können Sie mithilfe von Ansichten definieren, wie eine Liste von Datensätzen für eine bestimmte Entität in Ihrer Anwendung angezeigt wird. Eine Ansicht definiert:

- Die anzuzeigenden Spalten
- Die Breite jeder Spalte
- Wie die Datensatzliste standardmäßig nach Name sortiert werden soll
- Welche Standardfilter angewendet werden sollen, um zu begrenzen, welche Datensätze in der Liste angezeigt werden

Eine Dropdownliste von Ansichten wird häufig in der Anwendung angezeigt, damit Benutzer Optionen für unterschiedliche Ansichten von Entitätsdaten haben.

Die Datensätze, die in einzelnen Ansichten sichtbar sind, werden in einer Liste angezeigt, die manchmal auch als Raster bezeichnet wird, das häufig Optionen bereitstellt, sodass die Benutzer die Standardsortierung, Spaltenbreiten und Filter ändern können, um die für sie wichtigen Daten leichter zu sehen. Ansichten definieren auch die Datenquelle zu Diagrammen, die in der Anwendung verwendet werden.  
  
## <a name="types-of-views"></a>Ansichtstypen  
  
Es gibt drei Arten von Ansichten: *persönlich*, *System* und *öffentlich*.

Dieses Thema beschreibt, wie Systemadministratoren und Systemanpasser mit System- und öffentlichen Ansichten arbeiten. 
  
### <a name="personal-views"></a>Persönliche Ansichten  
  
 Sie und ein jeder Benutzer, der mindestens über Benutzerebenenzugriff auf Aktionen für die gespeicherte Ansichtsentität verfügt, kann persönliche Ansichten erstellen. Als Systemadministrator können Sie die Zugriffsebene für jede Aktion in der Sicherheitsrolle ändern, um die Tiefe zu kontrollieren, bis zu der Benutzer persönliche Ansichten erstellen, lesen, schreiben, löschen, freigeben oder zuweisen können.

Persönliche Ansichten sind im Besitz von Benutzern und sie sind aufgrund ihres standardmäßigen Benutzerebenenzugriffs nur für den Mitarbeiter oder andere Personen, für die er seine persönliche Ansicht freigibt, sichtbar. Sie können persönliche Ansichten erstellen, indem Sie eine Abfrage speichern, die Sie definieren, indem Sie die Optionen „Filter als neue Ansicht speichern“ und „Filter in aktueller Ansicht speichern“ in der Liste der Ansichten verwenden. Diese Ansichten sind gewöhnlich unten in den Listen der System- oder einer öffentlichen Ansichten enthalten, die in der Anwendung zur Verfügung stehen. Beim Erstellen einer neuen persönlichen Ansicht auf der Grundlage einer System- oder einer öffentlichen Ansicht können Sie keine öffentliche Ansicht auf Basis einer persönlichen Ansicht erstellen.
  
### <a name="system-views"></a>Systemsichten
Als Systemadministrator oder Systemanpasser können Sie Systemansichten bearbeiten. Systemansichten sind spezielle Ansichten, von denen die Anwendung abhängig ist, die für Systementitäten existieren oder die automatisch erstellt werden, wenn Sie benutzerdefinierte Entitäten erstellen. Diese Ansichten enthalten spezielle Zwecke und einige zusätzliche Funktionen. 


|Systemansichten  |Beschreibung  |
|---------|---------|
|Schnellsuche     | Die standardmäßige Ansicht wird verwendet, wenn Suchen mit der Schnellsuche ausgeführt werden. Diese Ansicht definiert auch, welche Felder durchsucht werden, wenn Suchfunktionen der Ansichten „Schnellsuche“ und „Suche“ verwendet werden.        |
|Erweiterte Suche     |  Die Standardansicht, in der die Suchergebnisse angezeigt werden, wenn „Erweiterte Suche“ verwendet wird. Diese Ansicht definiert auch Spalten, die standardmäßig verwendet werden, wenn neue benutzerdefinierte öffentliche Ansichten oder persönliche Ansichten erstellt werden, ohne dass eine Ansicht definiert wird, die als Vorlage verwendet wird.       |
|Zugeordnet     |  Die standardmäßige Ansicht, in der verknüpfte Entitäten für einen Datensatz aufgeführt sind.       |
|Suche     | Die Ansicht, die Sie sehen, wenn Sie einen Datensatz auswählen, um ein Suchfeld festzulegen.        |

Diese Ansichten werden in der Ansichtsauswahl nicht angezeigt und Sie können sie nicht in den Unterlisten in einem Formular oder als Liste in einem Dashboard verwenden. Diese Ansichten nicht gelöscht oder deaktiviert werden. Weitere Informationen: [Ansichten entfernen](remove-views.md)

Systemansichten sind im Besitz der Organisation, sodass sie von allen Benutzern angezeigt werden können. Beispielsweise hat jeder einen Organisationsebenenzugriff, um Datensätzen für die Ansichtsentität (savedquery) anzuzeigen. Diese Ansichten sind bestimmten Entitäten zugeordnet und innerhalb des Projektmappen-Explorers sichtbar. Sie können diese Ansichten in Lösungen aufnehmen, da diese der Entität zugeordnet sind.

### <a name="public-views"></a>Öffentliche Ansichten

Öffentliche Ansichten sind universelle Ansichten, die Sie nach Bedarf anpassen können. Diese Ansichten werden in der Ansichtsauswahl angezeigt und Sie können sie nicht in den Unterrastern in einem Formular oder als Liste in einem Dashboard verwenden. Einige öffentliche Ansichten sind Standard für Systementitäten und für benutzerdefinierte Entitäten. Wenn Sie beispielsweise eine neue benutzerdefinierte Entität erstellen, dann enthält sie folgende Kombination der öffentlichen und der Systemansicht.


|Name  |Typ  |
|---------|---------|
|Aktiver *Entitätspluralname*     |  Öffentlich       |
|Inaktiver *Entitätspluralname*    |  Öffentlich       |
|Schnellsuche nach aktivem *Entitätspluralnamen*     | Schnellsuche        |
|*Entitätsname* Erweiterte Suchansicht     | Erweiterte Suche        |
|*Entitätsname* Zugeordnete Ansicht     |  Zugeordnet       |
|*Entitätsname* Suchansicht     | Suche        |

Sie können benutzerdefinierte öffentliche Ansichten erstellen. Sie können alle benutzerdefinierten öffentlichen Ansichten in einer nicht verwalteten Lösung löschen. Sie können keine systemdefinierten öffentlichen Ansichten löschen. Die benutzerdefinierten öffentlichen Ansichten, die hinzugefügt werden, indem eine verwaltete Lösung importiert wurde, enthält möglicherweise verwaltete Eigenschaften, die verhindern, dass sie gelöscht werden können, außer indem die verwaltete Lösung deinstalliert wird.

## <a name="places-where-you-can-access-the-view-editor-to-create-or-edit-views"></a>Orte, an denen Sie auf den Ansichtseditor zugreifen können, um Ansichten zu erstellen oder zu bearbeiten

- PowerApps-Standort: Sie können auf den Ansichtsdesigner im Bereich **Modellgesteuert** > Registerkarten **Daten** > **Entitäten** > **Ansicht** zugreifen. Öffnen Sie eine vorhandene Ansicht oder erstellen Sie eine neue. Weitere Informationen: [Erstellen oder Bearbeiten einer Ansicht](create-and-edit-views.md)
- App-Designer: Wenn Sie in einer App arbeiten, sollten Sie den App-Designer verwenden, der eine einfache und intuitive Benutzeroberfläche mit Drag- and Dropfunktionen für erstellte Ansichten bereitstellt. Weitere Informationen:[Tutorial: Erstellen und Bearbeiten von öffentlichen oder Systemansichten mit dem App-Designer](create-edit-views-app-designer.md)
- Projektmappen-Explorer: Wenn Sie bereits erfahren mit Dynamics 365 sind, sollten Sie den Projektmappen-Explorer verwenden. Weitere Informationen: [Navigieren zur erweiterten Apperstellung und Anpassungsbereichen](advanced-navigation.md#solution-explorer)
 
## <a name="customize-views"></a>Anpassen von Ansichten

Als Systemadministrator können Sie Ansichten von Steuerelementen anpassen, indem Sie Raster (Listen) bearbeitbar und kompatibel mit der einheitlichen Schnittstelle machen. Die folgenden Steuerelemente werden verwendet:

- Bearbeitbare Raster: Damit können Benutzer die umfangreiche Inlinebearbeitung direkt aus Rastern und Unterrastern ausführen, unabhängig davon, ob sie eine Web-App, ein Tablet oder ein Smartphone verwenden. Weitere Informationen: [Raster mithilfe des benutzerdefinierten Steuerelements „Bearbeitbares Raster” bearbeitbar machen](make-grids-lists-editable-custom-control.md)
- Schreibgeschütztes Raster: Bietet eine optimale Anzeige- und Interaktionserfahrung für jede Bildschirmgröße und -ausrichtung von Smartphones und Tablets, da die Prinzipien des dynamischen des Designs angewendet werden. Weitere Informationen: [Angeben von Eigenschaften für Apps der einheitlichen Oberfläche](specify-properties-for-unified-interface-apps.md)

## <a name="next-steps"></a>Nächste Schritte

[Erstellen oder Bearbeiten von Ansichten](create-and-edit-views.md)
