---
title: Übersicht über die Erstellung einer modellgesteuerten App mit PowerApps | Microsoft-Dokumentation
description: Ausführliche Anleitungen zum Erstellen und Konfigurieren einer Entität zur Verwendung mit einer PowerApps-App
documentationcenter: na
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: 1b9ee344192d84933d25a3208d2feb0873a298c1
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-building-a-model-driven-app"></a>Übersicht über die Erstellung einer modellgesteuerten App

Das Design einer modellgesteuerten App ist ein auf Komponenten bezogener Ansatz zum Entwickeln von Apps. Das Design modellgesteuerter Apps erfordert keinen Code, und die Apps, die Sie erstellen, können so einfach oder sehr komplex sein.  Im Gegensatz zur Entwicklung einer Canvas-App, bei der der Designer über die vollständige Kontrolle über das Layout der App verfügt, wird bei modellgesteuerten Apps beinahe das gesamte Layout für Sie bestimmt und von den von Ihnen zur App hinzugefügten Komponenten größtenteils festgelegt. 

![Beispiel für eine modellgesteuerte App](media/model-driven-app-overview/model-app-sample.png)

> [!IMPORTANT]
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

Das Design modellgesteuerter Apps bietet folgende Vorteile:
- Umfangreiche Entwurfsumgebungen, die sich auf Komponenten statt Code konzentrieren 
- Erstellen von komplexen dynamischen Apps mit einer ähnlichen Benutzeroberfläche auf unterschiedlichen Geräten, egal ob es sich dabei um Desktopgeräte oder Mobilgeräte handelt
- Entwerfen von Funktionen, die den auf der Dynamics 365 Customer Engagement-Plattform verfügbaren Funktionen ähnlich sind 
- Ihre App kann als eine Lösung verteilt werden
 
## <a name="the-approach-to-model-driven-app-making"></a>Ansatz für die Erstellung modellgesteuerter Apps
Die Erstellung modellgesteuerter Apps besteht grundsätzlich aus drei Schwerpunktbereichen.

- Modellieren von Geschäftsdaten 
- Definieren von Geschäftsprozessen 
- Entwerfen der App

### <a name="modeling-business-data"></a>Modellieren von Geschäftsdaten
Um Geschäftsdaten zu modellieren, bestimmen Sie, welche Daten Ihre App benötigt und wie diese Daten mit anderen Daten in Zusammenhang stehen. Der modellgesteuerte Entwurf nutzt eine durch Metadaten gesteuerte Architektur, damit Designer die Anwendung anpassen können, ohne Code schreiben zu müssen. Metadaten sind im Grunde genommen „Daten über Daten“ und definieren die Struktur der im System gespeicherten Daten. [Tutorial: Erstellen benutzerdefinierter Entitäten mit Komponenten in PowerApps](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>Definieren von Geschäftsprozessen
Das Definieren und Erzwingen konsistenter Geschäftsprozesse ist ein wichtiger Aspekt beim Entwurf modellgesteuerter Apps. Konsistente Prozesse können Benutzer dabei unterstützen, sich auf ihre Arbeit zu konzentrieren, da sie nicht manuell mehrere verschiedene Schritte ausführen müssen. Prozesse können einfach oder komplex sein und sich über die Jahre oft ändern. Wählen Sie zum Erstellen eines Prozesses **Erweitert** aus, um den [Projektmappen-Explorer](#advanced-model-driven-app-making) zu öffnen. Wählen Sie anschließend im linken Bereich im Projektmappen-Explorer **Prozesse** und dann **Neu** aus. Weitere Informationen finden Sie unter [Arbeiten mit Geschäftslogik](#working-with-business-logic).  

### <a name="composing-the-model-driven-app"></a>Erstellen der modellgesteuerten App
Nachdem Sie die Daten modelliert und Prozesse definiert haben, erstellen Sie Ihre App, indem Sie mithilfe des App-Designers die erforderlichen Komponenten auswählen und konfigurieren.

![App-Designer](media/model-driven-app-overview/app-designer.png)

## <a name="model-driven-app-components-and-designers"></a>Komponenten und Designer der modellgesteuerten App
Eine wohlgeformte modellgesteuerte App besteht aus mehreren Komponenten, die vom Designer ausgewählt werden, um die Darstellung und Funktion der fertigen App zu erstellen. Die Komponenten und Komponenteigenschaften, die Designer zum Erstellen einer App verwenden, werden zu Metadaten. Zum einfacheren Verständnis des Zusammenhangs zwischen Komponenten und App-Entwurf werden sie hier in die Kategorien *Daten*, *Benutzeroberfläche*, *Logik* und *Visualisierung* unterteilt. 

### <a name="data"></a>Daten
Diese Komponenten bestimmen, auf welchen Daten die App basiert.


|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|Einrichtung     |Ein Element mit Eigenschaften, das Sie nachverfolgen, z.B. ein Kontakt oder Konto. Es stehen viele Standardentitäten zur Verfügung. Sie können eine nicht zum System gehörige Standardentität (Produktionsentität) anpassen oder eine benutzerdefinierte Entität von Grund auf neu erstellen.     | [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entitäts-Designer        |
|Feld     | Eine Eigenschaft, die einer Entität zugeordnet ist. Ein Feld, das durch einen Datentyp definiert ist, der den Typ der Daten bestimmt, der eingegeben oder ausgewählt werden kann. Beispiele sind unter anderem Text, Zahl, Datum und Uhrzeit, Währung oder Nachschlagen (führt zu einer Beziehung mit einer anderen Entität). Felder werden in der Regel mit Formularen, Ansichten und Suchvorgängen verwendet.        | [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entitäts-Designer   |
|Beziehung     | Entitätsbeziehungen definieren, wie Entitäten miteinander verknüpft werden können. Es gibt die Beziehungstypen 1:n (One-to-Many), n:1 (Many-to-One) und m:n (Many-to-Many). Durch das Hinzufügen eines Nachschlagefelds zu einer Entität wird z.B. eine neue 1:n-Beziehung zwischen den beiden Entitäten erstellt, und Sie können dieses Nachschlagefeld in ein Formular einfügen.   | [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entitäts-Designer        |
|Feld „Optionssatz“     | Dies ist ein besonderes Feld, das dem Benutzer eine Reihe vorbestimmter Optionen bereitstellt. Jede Option verfügt über einen Zahlenwert und eine Bezeichnung. Wenn dieses Feld zu einem Formular hinzugefügt wird, wird ein Steuerelement angezeigt, damit der Benutzer eine Option auswählen kann.  Es gibt zwei Arten von Optionen: Optionen, bei denen der Benutzer nur eine Option auswählen kann und Optionen mit mehreren Auswahlmöglichkeiten.  | Optionen-Designer von [!INCLUDE [powerapps](../../includes/powerapps.md)]     |

### <a name="ui"></a>UI
Diese Komponenten ermitteln, wie Benutzer mit der App interagieren. 

|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|App     | Bestimmt die grundlegenden Bestandteile einer Anwendung, z.B. Komponenten, Eigenschaften, Clienttyp und URL für Ihre App.      | App-Designer   |
|Siteübersicht     | Gibt die Navigation für Ihre App an.        | Designer für die Siteübersicht        |
|Formular     | Eine Reihe von Dateneingabefeldern für eine angegebene Entität, die mit den Elementen übereinstimmt, die Ihre Organisation für die Entität nachverfolgt. Beispielsweise mehrere Dateneingabefelder, in denen Benutzer relevante Informationen eingeben, um die vorherigen Bestellungen eines Kunden zusammen mit Datumsangaben angeforderter Nachbestellungen nachzuverfolgen.        | Formular-Designer        |
|Anzeigen     | Ansichten definieren, wie eine Liste von Datensätzen für eine bestimmte Entität in Ihrer Anwendung angezeigt wird. Eine Ansicht definiert die anzuzeigenden Spalten, die Breite jeder Spalte, das Sortierverhalten und die Standardfilter.   |  Ansicht-Designer       |

![App-Designer und Formular-Designer](media/model-driven-app-overview/app-and-form-designers.png)

### <a name="logic"></a>Logik
Bestimmt die Geschäftsprozesse, Regeln und die Automatisierung, über die die App verfügt. [!INCLUDE [powerapps](../../includes/powerapps.md)]-Entwickler verwenden einen Designer, der für den Prozesstyp oder die Regel spezifisch ist. 


|Logiktyp  |Beschreibung  |Designer  |
|---------|---------|---------|
|Geschäftsprozess     | Ein Onlineprozess, der Benutzer durch einen Standardgeschäftsprozess führt. Verwenden Sie z.B. einen Geschäftsprozess, wenn Sie möchten, dass Kundenserviceanfragen immer gleich behandelt werden oder dass Mitarbeiter die Rechnungsfreigabe vor der Aufgabe einer Bestellung erhalten.        | Geschäftsprozess-Designer        |
|Workflow     |  Workflows automatisieren Geschäftsprozesse ohne eine Benutzeroberfläche. Designer verwenden Workflows, um die Automatisierung, die keine Benutzerinteraktion erfordert, zu initiieren.       | Workflow-Designer        |
|Aktionen    |  Aktionen sind Prozesstypen, mit denen Sie Aktionen, einschließlich benutzerdefinierter Aktionen, direkt aus einem Workflow manuell aufrufen können.       |  Prozess-Designer       |
|Geschäftsregel     | Wird verwendet, um auf ein Formular eine Regel- oder Empfehlungslogik anzuwenden, um beispielsweise Feldanforderungen festzulegen, Felder auszublenden oder Daten zu validieren. App-Designer verwenden eine einfache Schnittstelle, um sich schnell ändernde und häufig verwendete Regeln zu implementieren und zu verwalten.         |  Geschäftsregel-Designer       |
|Flow     | Flow ist ein cloudbasierter Dienst, mit dem Sie automatisierte Workflows zwischen Apps und Diensten erstellen können, um Benachrichtigungen zu erhalten, Dateien zu synchronisieren, Daten zu erfassen und viele weitere Aufgaben auszuführen.        | Microsoft Flow        |

![Designer für Workflows, Aktionen und Geschäftsprozesse](media/model-driven-app-overview/designer-mash.png)

### <a name="visualizations"></a>Visualisierungen
Bestimmt, welche Art Datenvisualisierungen und Berichterstattung für die App verfügbar ist.


|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|Diagramm     | Eine einzelne Visualisierung in Diagrammform, die innerhalb einer Ansicht oder in einem Formular angezeigt oder einem Dashboard hinzugefügt werden kann.        | Diagramm-Designer        |
|Dashboard     | Funktionen als Palette für mindestens eine grafische Visualisierung, die eine Übersicht über handlungsrelevante Geschäftsdaten bietet.        | Dashboard-Designer        |
|Power BI Embedded     | Hinzufügen von Kacheln und Dashboards von Power BI Embedded zu Ihrer App. Power BI ist ein cloudbasierter Dienst, der Einblicke in Business Intelligence bietet.        |  Kombination von Diagramm-Designer, Dashboard-Designer und Power BI       |

![Beispieldashboard](media/model-driven-app-overview/dashboard-designer.png)

### <a name="advanced-model-driven-app-making"></a>Erstellung modellgesteuerter Apps im erweiterten Modus
Der Projektmappen-Explorer ist ein umfassendes Tool für die Erstellung erweiterter modellgesteuerter Apps. Sie können innerhalb des Projektmappen-Explorers mithilfe des Navigationsbereichs auf der linken Seite des Tools durch eine Hierarchie navigieren, die aus allen App-Komponenten besteht.

![Projektmappen-Explorer](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

Wählen Sie zum Öffnen des Projektmappen-Explorers links von [!INCLUDE [powerapps](../../includes/powerapps.md)] die Option **Modellgesteuert** aus.

  ![Auswahl von „Modellgesteuert“](media/model-driven-app-overview/app-type-picker-mod.png)

Wählen Sie anschließend die Registerkarte **Erweitert** aus. 

## <a name="model-driven-app-development-resources"></a>Ressourcen für die Entwicklung modellgesteuerter Apps
Weitere Informationen zur Entwicklung modellgesteuerter Apps finden Sie in folgenden Artikeln.
### <a name="modeling-your-data"></a>Modellieren Ihrer Daten
- [Entwurf benutzerdefinierter Unternehmens-Apps mit dem App-Designer](https://docs.microsoft.com/dynamics365/customer-engagement/customize/design-custom-business-apps-using-app-designer)
- [Erstellen und Entwerfen von Formularen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [Erstellen oder Bearbeiten von Ansichten](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)  

### <a name="modeling-and-composing-your-app"></a>Modellieren und Erstellen Ihrer App
- [Erstellen oder Bearbeiten von Entitäten](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-entities)
- [Erstellen und Bearbeiten von Beziehungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-entity-relationships) 
- [Erstellen und Bearbeiten von Feldern](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-fields)
- [Erstellen und Bearbeiten globaler Optionssätze (Auswahllisten)](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-global-option-sets)

### <a name="working-with-business-logic"></a>Arbeiten mit Geschäftslogik
- [Übersicht: Geschäftsprozessfluss](https://docs.microsoft.com/dynamics365/customer-engagement/customize/business-process-flows-overview)
- [Verwendung von Workflowprozessen für die Automatisierung von Prozessen, für die keine Benutzerinteraktion erforderlich ist](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)
- [Übersicht: Aktionen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/actions)
- [Erstellen von Geschäftsregeln und Empfehlungen zur Anwendung einer Logik in einem Formular](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

### <a name="using-visualizations-in-your-app"></a>Verwenden von Visualisierungen in Ihrer App
- [Erstellen oder Bearbeiten eines Systemdiagramms](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [Erstellen oder Bearbeiten von Dashboards](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)


### <a name="distributing-your-app"></a>Verteilen Ihrer App
[Erstellen einer Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-solution)

## <a name="next-steps"></a>Nächste Schritte
[Schnellstart: Erstellen einer benutzerdefinierten Entität](../common-data-service/data-platform-create-entity.md)

[Tutorial: Erstellen benutzerdefinierter Entitäten mit Komponenten in PowerApps](../common-data-service/create-custom-entity.md)

