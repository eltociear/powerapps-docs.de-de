---
title: Grundlegendes zu Komponenten von modellgesteuerten Apps in PowerApps | Microsoft-Dokumentation
description: Hier finden Sie Informationen zu verschiedenen Komponenten einer modellgesteuerten App wie Daten, Benutzeroberfläche, Logik und Visualisierung.
Keywords: fields, attributes, model-driven app
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.openlocfilehash: 249f0d35ce9eb466303ef16658aa01198632875e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682834"
---
# <a name="understand-model-driven-app-components"></a>Grundlegendes zu Komponenten von modellgesteuerten Apps
Eine wohlgeformte modellgesteuerte App besteht aus mehreren Komponenten, die Sie mit dem Designer auswählen, um die Darstellung und Funktion der fertigen App zu erstellen. Die Komponenten und Komponenteigenschaften, die Designer zum Erstellen einer App verwenden, werden zu Metadaten. 

Zum einfacheren Verständnis des Zusammenhangs zwischen Komponenten und App-Entwurf werden sie hier in die Kategorien *Daten*, *Benutzeroberfläche*, *Logik* und *Visualisierung* unterteilt. 

## <a name="data"></a>Daten
Diese Komponenten bestimmen, auf welchen Daten die App basiert.


|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|Einrichtung     |Ein Element mit Eigenschaften, das Sie nachverfolgen, z.B. ein Kontakt oder Konto. Es stehen viele Standardentitäten zur Verfügung. Sie können eine nicht zum System gehörige Standardentität (Produktionsentität) anpassen oder eine benutzerdefinierte Entität von Grund auf neu erstellen.     | [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entitäts-Designer        |
|Feld     | Eine Eigenschaft, die einer Entität zugeordnet ist. Ein Feld, das durch einen Datentyp definiert ist, der den Typ der Daten bestimmt, der eingegeben oder ausgewählt werden kann. Beispiele sind unter anderem Text, Zahl, Datum und Uhrzeit, Währung oder Nachschlagen (führt zu einer Beziehung mit einer anderen Entität). Felder werden in der Regel mit Formularen, Ansichten und Suchvorgängen verwendet.        | [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entitäts-Designer   |
|Beziehung     | Entitätsbeziehungen definieren, wie Entitäten miteinander verknüpft werden können. Es gibt die Beziehungstypen 1:n (One-to-Many), n:1 (Many-to-One) und m:n (Many-to-Many). Durch das Hinzufügen eines Nachschlagefelds zu einer Entität wird z.B. eine neue 1:n-Beziehung zwischen den beiden Entitäten erstellt, und Sie können dieses Nachschlagefeld in ein Formular einfügen.   | [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entitäts-Designer        |
|Feld „Optionssatz“     | Dies ist ein besonderes Feld, das dem Benutzer eine Reihe vorbestimmter Optionen bereitstellt. Jede Option verfügt über einen Zahlenwert und eine Bezeichnung. Wenn dieses Feld zu einem Formular hinzugefügt wird, wird ein Steuerelement angezeigt, damit der Benutzer eine Option auswählen kann.  Es gibt zwei Arten von Optionen: Optionen, bei denen der Benutzer nur eine Option auswählen kann und Optionen mit mehreren Auswahlmöglichkeiten.  | Optionen-Designer von [!INCLUDE [powerapps](../../includes/powerapps.md)]     |

Weitere Informationen: [Define data for your model-driven app (Definieren von Daten in Ihrer modellgesteuerten App)](define-data-model-driven-app.md) 

## <a name="ui"></a>UI
Diese Komponenten ermitteln, wie Benutzer mit der App interagieren. 

|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|App     | Bestimmt die grundlegenden Bestandteile einer Anwendung, z.B. Komponenten, Eigenschaften, Clienttyp und URL für Ihre App.      | App-Designer   |
|Siteübersicht     | Gibt die Navigation für Ihre App an.        | Designer für die Siteübersicht        |
|Formular     | Eine Reihe von Dateneingabefeldern für eine angegebene Entität, die mit den Elementen übereinstimmt, die Ihre Organisation für die Entität nachverfolgt. Beispielsweise mehrere Dateneingabefelder, in denen Benutzer relevante Informationen eingeben, um die vorherigen Bestellungen eines Kunden zusammen mit Datumsangaben angeforderter Nachbestellungen nachzuverfolgen.        | Formular-Designer        |
|Anzeigen     | Ansichten definieren, wie eine Liste von Datensätzen für eine bestimmte Entität in Ihrer Anwendung angezeigt wird. Eine Ansicht definiert die anzuzeigenden Spalten, die Breite jeder Spalte, das Sortierverhalten und die Standardfilter.   |  Ansicht-Designer       |

![App-Designer und Formular-Designer](media/model-driven-app-overview/app-and-form-designers.png)

## <a name="logic"></a>Logik
Bestimmt die Geschäftsprozesse, Regeln und die Automatisierung, über die die App verfügt. [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entwickler verwenden einen Designer, der für den Prozesstyp oder die Regel spezifisch ist. 


|Logiktyp  |Beschreibung  |Designer  |
|---------|---------|---------|
|Geschäftsprozess     | Ein Onlineprozess, der Benutzer durch einen Standardgeschäftsprozess führt. Verwenden Sie z.B. einen Geschäftsprozess, wenn Sie möchten, dass Kundenserviceanfragen immer gleich behandelt werden oder dass Mitarbeiter die Rechnungsfreigabe vor der Aufgabe einer Bestellung erhalten.        | Geschäftsprozess-Designer        |
|Workflow     |  Workflows automatisieren Geschäftsprozesse ohne eine Benutzeroberfläche. Designer verwenden Workflows, um die Automatisierung, die keine Benutzerinteraktion erfordert, zu initiieren.       | Workflow-Designer        |
|Aktionen    |  Aktionen sind Prozesstypen, mit denen Sie Aktionen, einschließlich benutzerdefinierter Aktionen, direkt aus einem Workflow manuell aufrufen können.       |  Prozess-Designer       |
|Geschäftsregel     | Wird verwendet, um auf ein Formular eine Regel- oder Empfehlungslogik anzuwenden, um beispielsweise Feldanforderungen festzulegen, Felder auszublenden oder Daten zu validieren. App-Designer verwenden eine einfache Schnittstelle, um sich schnell ändernde und häufig verwendete Regeln zu implementieren und zu verwalten.         |  Geschäftsregel-Designer       |
|Flow     | Flow ist ein cloudbasierter Dienst, mit dem Sie automatisierte Workflows zwischen Apps und Diensten erstellen können, um Benachrichtigungen zu erhalten, Dateien zu synchronisieren, Daten zu erfassen und viele weitere Aufgaben auszuführen.        | Microsoft Flow        |

![Designer für Workflows, Aktionen und Geschäftsprozesse](media/model-driven-app-overview/designer-mash.png)

Weitere Informationen: [Apply business logic in your model-driven app (Anwenden von Geschäftslogik in Ihrer modellgesteuerten App)](guide-staff-through-common-tasks-processes.md)

## <a name="visualizations"></a>Visualisierungen
Bestimmt, welche Art Datenvisualisierungen und Berichterstattung für die App verfügbar ist.


|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|Diagramm     | Eine einzelne Visualisierung in Diagrammform, die innerhalb einer Ansicht oder in einem Formular angezeigt oder einem Dashboard hinzugefügt werden kann.        | Diagramm-Designer        |
|Dashboard     | Funktionen als Palette für mindestens eine grafische Visualisierung, die eine Übersicht über handlungsrelevante Geschäftsdaten bietet.        | Dashboard-Designer        |
|Power BI Embedded     | Hinzufügen von Kacheln und Dashboards von Power BI Embedded zu Ihrer App. Power BI ist ein cloudbasierter Dienst, der Einblicke in Business Intelligence bietet.        |  Kombination von Diagramm-Designer, Dashboard-Designer und Power BI       |

![Beispieldashboard](media/model-driven-app-overview/dashboard-designer.png)

## <a name="advanced-model-driven-app-making"></a>Erstellung modellgesteuerter Apps im erweiterten Modus
Der Projektmappen-Explorer ist ein umfassendes Tool für die Erstellung erweiterter modellgesteuerter Apps. Sie können innerhalb des Projektmappen-Explorers mithilfe des Navigationsbereichs auf der linken Seite des Tools durch eine Hierarchie navigieren, die aus allen App-Komponenten besteht.

![Projektmappen-Explorer](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

Wählen Sie zum Öffnen des Projektmappen-Explorers links von [!INCLUDE [powerapps](../../includes/powerapps.md)] die Option **Modellgesteuert** aus.

  ![Auswahl von „Modellgesteuert“](media/model-driven-app-overview/app-type-picker-mod.png)

Wählen Sie anschließend die Registerkarte **Erweitert** aus.

Weitere Informationen: [Advanced app making and customization (Erweiterte App-Erstellung und -Anpassung)](advanced-navigation.md)

## <a name="related-topics"></a>Verwandte Themen

[Validate and publish your model-driven app (Überprüfen und Veröffentlichen Ihrer modellgesteuerten App)](validate-app.md)

[Freigeben einer modellgesteuerten App](share-model-driven-app.md)