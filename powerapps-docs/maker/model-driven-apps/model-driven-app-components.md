---
title: Grundlegendes zu Komponenten modellgestützter Apps in Power Apps | Microsoft-Dokumentation
description: Verschiedene Komponenten einer modellgesteuerten Anwendung wie Daten, Benutzeroberfläche, Logik und Visualisierung verstehen.
Keywords: Felder, Attribute, modellgestützte App
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 10/17/2019
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4f1c05ca41e6873a0072e8ea6720343e468e38bb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2863058"
---
# <a name="understand-model-driven-app-components"></a>Grundlegendes zu Komponenten modellgestützter Apps
Eine gut gestaltete modellgesteuerte Anwendung besteht aus mehreren Komponenten, die Sie mit Hilfe des Designers auswählen, um das Aussehen und die Funktionalität der fertigen App zu gestalten. Die Komponenten und Komponenteneigenschaften, aus denen Designer eine App zusammensetzen, werden zu Metadaten. 

Um zu verstehen, wie sich jede dieser Komponenten auf das App-Design bezieht, werden sie hier in die Kategorien *Daten*, *UI*, *Logik* und *Visualisierung* unterteilt. 

## <a name="data"></a>Daten
Diese Komponenten bestimmen, auf welchen Daten die App basiert und welcher Designer verwendet wird, um die Komponente zu erstellen oder zu bearbeiten.


|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|Entität     |Ein Element mit Eigenschaften, die Sie nachverfolgen, wie z. B. Kontakte oder Firma. Viele Standard-Entitäten sind verfügbar. Sie können eine Nicht-System-Standard-Entität (Produktions-Entität) anpassen oder eine benutzerdefinierte Entität von Grund auf neu erstellen.     | [!INCLUDE [powerapps](../../includes/powerapps.md)] Entitäts-Designer        |
|Beziehung     | Entitätsbeziehungen legen fest, wie Entitäten miteinander verknüpft werden können. Es gibt 1:N (eins-zu-viele), N:1 (viele-zu-eins) und N:N (viele-zu-viele) Arten von Beziehungen. Wenn Sie beispielsweise ein Suchfeld zu einer Entität hinzufügen, wird eine neue 1:N-Beziehung zwischen den beiden Entitäten erstellt und Sie können dieses Suchfeld in ein Formular einfügen.   | [!INCLUDE [powerapps](../../includes/powerapps.md)] Entitäts-Designer        |
|Feld     | Eine Eigenschaft, die einer Entität zugeordnet ist. Ein Feld wird durch einen Datentyp definiert, der die Art der Daten bestimmt, die eingegeben oder ausgewählt werden können. Dazu zählen Text, Nummer, Datum und Uhrzeit, Währung oder Suchen (erstellt eine Beziehung zu einer anderen Entität.) Felder werden typischerweise in Formularen, Ansichten und Suchen verwendet.        | [!INCLUDE [powerapps](../../includes/powerapps.md)] Entitäts-Designer   |
|Optionssatzfeld     | Dies ist ein spezieller Feldtyp, der dem Benutzer eine Reihe von vordefinierten Optionen bietet. Jede Option hat einen Zahlenwert und eine Beschriftung. Bei Hinzufügung zu einem Formular enthält dieses Feld ein Steuerelement für Benutzer zur Auswahl einer Option.  Es gibt zwei Arten von Optionssätzen: Optionssätze, bei denen der Benutzer nur eine Option auswählen kann, und Multi-Select-Optionssätze, die mehr als eine Auswahl erlauben.  | [!INCLUDE [powerapps](../../includes/powerapps.md)] Optionssatz-Designer     |

Weitere Informationen: [Definieren Sie Daten für die modellgesteuerte App](define-data-model-driven-app.md) 

## <a name="ui"></a>Benutzeroberfläche
Diese Komponenten bestimmen, wie Benutzer mit der App interagieren. 

|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|App     | Bestimmt die Anwendungsgrundlagen wie Komponenten, Eigenschaften, Clienttyp und URL für Ihre Anwendung.      | App-Designer   |
|Siteübersicht     | Gibt die Navigation für Ihre App an.        | Siteübersichts-Designer        |
|Formular     | Ein Satz von Dateneingabefeldern für eine bestimmte Entität, die mit den Elementen übereinstimmen, die Ihre Organisation für die Entität verfolgt. Zum Beispiel eine Reihe von Dateneingabefeldern, in denen der Benutzer relevante Informationen eingibt, um die früheren Bestellungen eines Kunden zusammen mit bestimmten gewünschten Nachbestellungsdaten zu verfolgen.        | Formulardesigner        |
|Ansicht     | Ansichten definieren, wie eine Liste von Datensätzen für eine bestimmte Entität in Ihrer Anwendung angezeigt wird. Eine Ansicht definiert die anzuzeigenden Spalten, die Breite jeder Spalte, das Sortierverhalten und die Standardfilter.   |  Ansicht-Designer       |

![App-Designer und Formular-Designer](media/model-driven-app-overview/app-and-form-designers.png)

## <a name="logic"></a>Logik
Bestimmt die Geschäftsprozesse, Regeln und die Automatisierung der Anwendung. [!INCLUDE [powerapps](../../includes/powerapps.md)] Hersteller verwenden einen Designer, der für die Art des Prozesses oder der Regel spezifisch ist. 


|Logiktyp  |Beschreibung  |Designer  |
|---------|---------|---------|
|Geschäftsprozessfluss     | Ein Online-Prozess, der die Benutzer durch einen Standardgeschäftsprozess führt. Verwenden Sie beispielsweise einen Geschäftsprozessfluss, wenn Sie möchten, dass jeder Kundenserviceanfragen auf die gleiche Methode bearbeitet, oder von Mitarbeitern eine Genehmigung für eine Rechnung erforderlich ist, bevor Sie einen Auftrag senden.        | Geschäftsprozessflow-Designer        |
|Workflow     |  Workflows automatisieren Geschäftsprozesse ohne eine Benutzeroberfläche. Designer verwenden Workflows, um eine Automatisierung zu initiieren, die keine Benutzerinteraktion erfordert.       | Workflow-Designer        |
|Aktionen    |  Aktionen sind ein Prozesstyp, mit dem Sie manuell Aktionen, einschließlich benutzerdefinierter Aktionen, direkt aus einem Workflow heraus aufrufen können.       |  Prozess-Gestalter       |
|Geschäftsregel     | Wird verwendet, um eine Regel- oder Empfehlungslogik auf ein Formular anzuwenden, z. B. um Feldanforderungen festzulegen, Felder auszublenden oder Daten zu validieren. App-Designer verwenden eine einfache Schnittstelle, um schnell wechselnde und häufig verwendete Regeln zu implementieren und zu pflegen.         |  Geschäftsregel-Designer       |
|Flow     | Flow ist ein Cloud-basierter Dienst, mit dem Sie automatisierte Workflows zwischen Anwendungen und Diensten erstellen können, um Benachrichtigungen zu erhalten, Dateien zu synchronisieren, Daten zu sammeln und vieles mehr.        | Power Automate        |

![Workflow-, Aktions- und Geschäftsprozessfluss-Designer](media/model-driven-app-overview/designer-mash.png)

Weitere Informationen: [Geschäftslogik in Ihrer modellgesteuerten App anwenden](guide-staff-through-common-tasks-processes.md) 

### <a name="additional-options-for-adding-custom-business-logic"></a>Zusatzoptionen zum Hinzufügen der benutzerdefinierten Geschäftslogik
[Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](../../developer/common-data-service/plug-ins.md) <br />
[Workflowerweiterungen](../../developer/common-data-service/workflow/workflow-extensions.md)

## <a name="visualizations"></a>Visualisierungen
Legt fest, welcher Typ von Datenvisualisierung und Berichten der App zur Verfügung steht.


|Komponente  |Beschreibung  |Designer  |
|---------|---------|---------|
|Diagramm     | Eine einzelne grafische Visualisierung, die innerhalb einer Ansicht, auf einem Formular oder in einem Dashboard angezeigt werden kann.        | Diagramm-Designer        |
|Informationsleiste     | Dient als Auswahl einer oder mehrerer grafischer Visualisierungen, die einen Überblick über verwertbare Geschäftsdaten gibt.        | Dashboard-Designer        |
|Power BI-Einbettung     | Fügen Sie eingebettete Power BI-Kacheln und -Dashboards zu Ihrer App hinzu. Power BI ist ein Cloud-basierter Service, der Einblicke in die Business Intelligence bietet.        |  Kombination aus Diagramm-Designer, Dashboard-Designer und Power BI       |

![Beispiel-Dashboard](media/model-driven-app-overview/dashboard-designer.png)

## <a name="advanced-model-driven-app-making"></a>Erweiterte modellgesteuerte App-Erstellung
Der Lösungs-Explorer ist ein umfassendes Werkzeug zur modellgesteuerten Anwendungsentwicklung. Innerhalb des Lösungs-Explorers können Sie über den Navigationsbereich auf der linken Seite des Tools durch eine Hierarchie navigieren, die aus allen App-Komponenten besteht.

![Lösungs-Explorer](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

Um den Lösungs-Explorer zu öffnen, wählen Sie **Modellgesteuert** im linken Bereich von [!INCLUDE [powerapps](../../includes/powerapps.md)]"2".

  ![Wählen Sie Modellgesteuert aus.](media/model-driven-app-overview/app-type-picker-mod.png)

Wählen Sie dann die Registerkarte **Erweitert**.

Weitere Informationen: [Erweiterte App-Erstellung und -Anpassung](advanced-navigation.md)

## <a name="related-topics"></a>Verwandte Themen

[Validieren und Veröffentlichen Ihrer modellgesteuerten Anwendung](validate-app.md)

[Freigeben Ihrer modellgesteuerten Anwendung](share-model-driven-app.md)
