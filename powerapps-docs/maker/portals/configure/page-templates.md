---
title: Erstellen und Verwalten von Seitenvorlagen in Power Apps-Portalen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Seitenvorlagen in Power Apps-Portalen erstellen und verwalten können.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 26d9799425d561e4fb6a5f9f6c368fa6162ecb6d
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980611"
---
# <a name="create-and-manage-page-templates"></a>Erstellen und verwalten Sie Seitenvorlagen

Während Webseiten Knoten in der SiteMap des Portals sind, die Inhalte darstellen, die den Portalbenutzern möglich ist, können Seitenvorlagen die tatsächlichen ASPX-Seiten darstellen, die die Suche erstellen, um ein konsistentes Erscheinungsbild der gesamten Website zu verwalten. Seitenvorlagen werden mithilfe ASP.NET-Seiten, Masterseiten, Cascading Stylesheete (CSS), Benutzersteuerelemente und Serversteuerelemente erstellt.

Wenn Sie eine neue Webseite für die Website erstellen, sei es durch Front-side Publishing oder über die Portaloberfläche, müssen Sie eine Seitenvorlage auswählen, die den Inhalt der Seite den Benutzern des Portale präsentiert.

Der Unterschied zwischen Webseiten und Seitenvorlagen versteht man wohl am besten als die Differenz  zwischen einer exakten URL und einer aktuellen ASPX-Seite, die verstanden wird als Lichtpause zum Anzeigen des Inhalts. Jede Webseite stellt eine bestimmte URL in Ihrem Standort dar, zu der Benutzer navigieren können. Wenn ein Benutzer zu einer URL navigiert, wird der Inhalt, der dieser URL zugeordnet ist, angezeigt. Eine Webseite enthält keine Informationen dazu, wie dieser Inhalt angezeigt wird.  Dies wird durch die Seitenvorlage bestimmt, die die tatsächliche ASPX-Seite ist, die das HTML generiert,  das der Benutzer angezeigt erhält.

Wenn Sie eine neue Website erstellen, müssen Sie eine Seitenvorlage in der Liste der vorhandenen Vorlagen auswählen. Einige Seitenvorlagen sind für jedes der Anfangsportale enthalten. Beim Verwenden der Portale als Basis für Ihre eigene Website verwenden sind diese Vorlagen Praktisch als Basis zum Aufzeigen der Funktionalität des Portals. Es ist ein Portalentwickler erforderlich, um das Layout der Seiten deutlich zu ändern. In den meisten Fällen ist die "Seiten" Seitenvorlage die Seitenvorlage, die verwendet wird, da sie allgemein ist: Eine Webseite mit dieser Vorlage besitzt den Inhalte, der angezeigt wird, sowie eine Liste von untergeordneten Seiten, die als Navigationselemente dargestellt werden.

## <a name="manage-page-templates"></a>Seitenvorlagen verwenden

Eine neue Seiten-Vorlage erstellen ist nur erforderlich, wenn Sie eine nagelneue ASPX-Seite anzeigen, um den Inhalt der Website anzuziegen, eine Portalentwickler-Aufgabe. Wahrscheinlich für den Zweck der Vereinfachung des Layouts des Standorts kann ein Portalentwickler einfach vorhandene ASPX-Seiten wesentlich ändern.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Gehen Sie zu **Portale** > **Seitenvorlagen**.

3. Um eine neue Seitenvorlage zu erstellen, klicken Sie auf **Neu**.

4. Wenn Sie eine vorhandene Seitenvorlage bearbeiten, wählen Sie den Seitenvorlagennamen aus.

5. Hinzufügen der entsprechenden Werte zu den Feldern.

6. Klicken Sie auf **Speichern und schließen**.

### <a name="page-template-attributes"></a>Seitenvorlagenattribute

|Name |Beschreibung |
|-----|--------|
|Name    |Name der Vorlage, die als Referenz verwendet wird.   |
|Website   |Die zugeordnete Website.   |
|Typ   |Der Typ der Vorlage, der bestimmt, inwiefern die Vorlage das Rendern bestimmt.<ul><li>**Überschreiben**: Verwendet das URL-Feld, um eine bestimmte ASP.NET-Vorlage zu rendern.</li><li>**Webvorlage**: Nutzt das Internet-Vorlagenfeld, um eine bestimmte Internet-Vorlage zu rendern.</li></ul>   |
|URL Überschreiben   |Pfad der physischen ASP.NET-ASPX-Seite (oder anderer Ressource, wie .ashx) die Inhalte rendert.<br> Dieses Feld wird angezeigt, wenn **URL überschreiben** in der Liste **Typ** ausgewählt ist. |
|Webvorlage   |Ein Verweis auf eine Internet-Vorlage wird verwendet, um diese Vorlage zu rendern.<br>Dieses Feld wird angezeigt, wenn **Web-Vorlage** in der Liste **Typ** ausgewählt ist.  |
|Ist-Standard   |Wenn" Ja" und die Vorlage in der Standardeinstellung in den Dropdown-Listenfeldern in den clientseitigen Bearbeitungstools zugewiesen wird.   |
|Entitätsname   |Der Seiten-Entitätstyp, den diese Vorlage zu rendern erwartet. Dies wird nur durch das Vorderseitenbearbeitungssystem verwendet, um nur die entsprechenden Vorlagen-Auswahlen für Inhalt-Autoren anzuzeigen.<br>Normalerweise ist dies die Webseite (adx_webpage), aber kann eine andere Portalentität sein, wie zum Beispiel Forum, Forum-Thread, Blog oder Blogbeitrag.   |
|Beschreibung  |Eine Beschreibung dieser Vorlage zugunsten der Vorderseitenbearbeitungsbenutzer. |
|||

