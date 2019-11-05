---
title: Erstellen und Verwalten von Seitenvorlagen in powerapps-Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie Seitenvorlagen in powerapps-Portalen erstellen und verwalten.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ef4f61e7b9165d8d2c4abbc70c0bce65957665ab
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551690"
---
# <a name="create-and-manage-page-templates"></a>Erstellen und Verwalten von Seitenvorlagen

Obwohl Webseiten Knoten in der Sitemap Ihres Portals sind, die Inhalte darstellen, die für Portalbenutzer zugänglich sind, stellen Seitenvorlagen die eigentlichen ASPX-Seiten dar, die eine Möglichkeit bieten, ein konsistentes Erscheinungsbild auf der gesamten Website zu gewährleisten. Seitenvorlagen werden mithilfe von ASP.NET Seiten, Masterseiten, Cascading Stylesheets (CSS), Benutzer Steuerelementen und Server Steuerelementen erstellt.

Wenn Sie eine neue Webseite für die Website erstellen, unabhängig davon, ob Sie sich über die übergeordnete Veröffentlichung oder über die Portal Schnittstelle befinden, müssen Sie eine Seitenvorlage auswählen, die den Inhalt der Seite für Benutzer des Portals angezeigt wird.

Der Unterschied zwischen Webseiten und Seitenvorlagen wird vielleicht am besten als der Unterschied zwischen einer exakten URL und einer echten ASPX-Seite verstanden, die als Blaupause zum Anzeigen von Inhalten fungiert. Jede Webseite repräsentiert eine bestimmte URL in Ihrer Website, zu der Benutzer navigieren können. Wenn ein Benutzer zu einer URL navigiert, wird der Inhalt angezeigt, der dieser URL zugeordnet ist. Eine Webseite enthält jedoch keine Informationen darüber, wie dieser Inhalt angezeigt wird.  Dies wird durch die Seitenvorlage bestimmt, bei der es sich um die tatsächliche ASPX-Seite handelt, die den vom Benutzer angezeigten HTML-Code generiert.

Wenn Sie eine neue Webseite erstellen, müssen Sie eine Seitenvorlage aus einer Liste vorhandener Vorlagen auswählen. In jedem der Start Portale sind mehrere Seitenvorlagen enthalten. Wenn Sie diese Portale als Basis für Ihre eigene Website verwenden, sind diese Vorlagen praktisch, um die Funktionalität des Portals zu demonstrieren. Allerdings muss ein Portal Entwickler das Layout dieser Seiten erheblich ändern. In den meisten Fällen handelt es sich bei der Seitenvorlage "page" um die zu verwendende Seitenvorlage: bei einer Webseite, die diese Vorlage verwendet, wird der Inhalt angezeigt, sowie eine Liste der untergeordneten Seiten, die als Navigationselemente dargestellt werden.

## <a name="manage-page-templates"></a>Verwalten von Seitenvorlagen

Das Erstellen einer neuen Seitenvorlage ist nur erforderlich, wenn Sie eine neue. aspx-Seite erstellen, um Inhalte auf Ihrer Website, die Aufgabe eines Portal Entwicklers, anzuzeigen. Tatsächlich kann ein Portal Entwickler für das einfache Anpassen des Layouts Ihrer Site größtenteils nur vorhandene ASPX-Seiten ändern.

1. Pen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** > **Seitenvorlagen**.

3. Wählen Sie **neu**aus, um eine neue Seitenvorlage zu erstellen.

4. Wählen Sie den Namen der Seitenvorlage aus, um eine vorhandene Seitenvorlage zu bearbeiten.

5. Geben Sie entsprechende Werte in die Felder ein.

6. Wählen Sie **Speichern und Schließen** aus.

### <a name="page-template-attributes"></a>Seitenvorlagen Attribute

|Name |Beschreibung |
|-----|--------|
|Name    |Der Name der Vorlage, die für den Verweis verwendet wird.   |
|Website   |Die zugehörige Website.   |
|Typ   |Der Typ der Vorlage, mit der gesteuert wird, wie die Vorlage bestimmt, was dargestellt werden soll.<ul><li>**Rewrite**: verwendet das Feld zum Umschreiben von URLs, um eine gegebene ASP.net-Vorlage zu erzeugen.</li><li>**Webvorlage**: verwendet das Webvorlagen Feld, um eine bestimmte Webvorlage zu erzeugen.</li></ul>   |
|URL umschreiben   |Der Pfad der physischen ASP.net. aspx-Seite (oder einer anderen Ressource, wie z. b. ashx), die den Inhalt rendert.<br> Dieses Feld wird nur angezeigt, wenn in der Liste **Typ** die Option **URL umschreiben** ausgewählt ist. |
|Webvorlage   |Ein Verweis auf eine Webvorlage, die zum Rendering dieser Vorlage verwendet wird.<br>Dieses Feld wird nur angezeigt, wenn eine **Webvorlage** in der Liste **Typ** ausgewählt ist.  |
|Ist Standard   |Wenn "Ja", ist die Vorlage der Standardwert, der der Dropdown Liste in den Tools zur Client seitigen Bearbeitung zugewiesen wird.   |
|Entitäts Name   |Der Seiten Entitätstyp, den diese Vorlage zum Rendering erwartet. Dies wird vom System der systemeigenen Bearbeitung verwendet, um Inhaltsautoren nur geeignete Vorlagen Optionen zur Verfügung zu stellen.<br>Normalerweise handelt es sich hierbei um eine Webseite (adx_webpage), aber es kann sich um eine andere Portal Entität handeln, z. b. Forum, Forums Thread, Blog oder Blogbeitrag.   |
|Beschreibung  |Eine Beschreibung dieser Vorlage, um die Benutzer zu nutzen, die sich auf die Benutzer der Vorderseite-Bearbeitung stützen. |
|||

