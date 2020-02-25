---
title: Platzieren von Unterknoten mithilfe von Verknüpfungen für ein Portal | MicrosoftDocs
description: Anweisungen für das Platzieren von untergeordneten Knoten mithilfe von Verknüpfungen für Portale
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e438803fa817d1b02a303a6a6e4873f2ba1e295f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980567"
---
# <a name="place-child-nodes-by-using-shortcuts-for-portals"></a>Platzieren von untergeordneten Knoten mithilfe von Verknüpfungen für Portale
Verknüpfungen ermöglichen es, untergeordnete Knoten über die Siteübersicht im Portal zu platzieren, die dann einfach an anderen Knoten in der Siteübersicht oder auf externe URLs verweisen. Das bedeutet, Webseiten, Webdateien, Ereignisse und Foren können als feste Knoten für die Siteübersicht des Portals betrachtet werden. Sie werden zur Siteübersicht hinzugefügt, wenn Sie zu diesen navigieren; der tatsächliche Inhalt dieser Knoten wird direkt angezeigt. Verknüpfungen dagegen können als immaterielle Knoten betrachtet werden: Sie werden ebenfalls der Siteübersicht hinzugefügt (außer Weblinks, diese nicht), aber wenn Sie zu diesen navigieren, sehen sie den Inhalt für den festen Knoten, auf den die Verknüpfung verweist, wobei dieser Inhalt von der Seitenvorlage für jenen Knoten gerendert wird.

## <a name="manage-shortcuts"></a>Verwalten von Tastenkombinationen

Das Erstellen, Bearbeiten und Löschen von Verknüpfungen kann in Power Apps-Portalen erfolgen.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Navigieren Sie zu **Portale** &gt; **Verknüpfungen**. 

3. Wenn Sie eine neue Verknüpfung erstellen möchten, wählen Sie **Neu** aus. 

4. Um eine vorhandene Verknüpfung zu bearbeiten, wählen Sie die vorhandene Verknüpfung im Raster aus. 

5. Geben Sie Werte in die Felder ein. 

6. Klicken Sie auf **Speichern und schließen**.

### <a name="attributes-and-relationships"></a>Attribute und Beziehungen

| Name                               | Beschreibung                                                                                                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                               | Ein beschreibender Name für die Verknüpfung Nur zur internen Verwendung.                                                                                                                                  |
| Website                            | Die Webseite, auf die die Verknüpfung verweist.                                                                                                                                                    |
| Übergeordnete Seite                        | Die übergeordnete Webseite der Verknüpfungs-Entität in der Siteübersicht. Die Verknüpfung wird der Siteübersicht als dieser Seite untergeordnet hinzugefügt.                                                                 |
| Externe URL                       | Ziel der Verknüpfung mit einer URL für eine Ressource außerhalb der Organisation.                                                                                                                  |
| Webseite                           | Ziel der Verknüpfung mit einer internen Webseite.                                                                                                                                               |
| Webdatei                           | Zwecks der Verknüpfung mit einer Internet-Datei.                                                                                                                                                        |
| Veranstaltung                              | Zwecks der Verknüpfung mit einem Ereignis.                                                                                                                                                          |
| Forum                              | Zwecks der Verknüpfung mit einem Forum.                                                                                                                                                           |
| Titel                              | Der Titel für die Verknüpfung. Dies ist der Name, der in den Siteübersicht und der untergeordneten Navigationsansicht angezeigt wird. Wenn Sie keinen Wert (oder Namen) angeben, wird die Zielentität stattdessen angezeigt werden. |
| Beschreibung                        | Eine Beschreibung für die untergeordneten Navigationsansicht. (Optional).                                                                                                                                        |
| Anzeigereihenfolge                      | Die vorderseitige bearbeitbare Bestellung, auf der Die Verknüpfung auf der Siteübersicht und in der untergeordneten Übersicht erscheint im Verhältnis zu andern Knoten in der Siteübersicht.                                                      |
| Verknüpfungszielüberprüfung deaktivieren | Falls deaktiviert basiert die Sicherheit der Verknüpfung auf dem Ziel. Sonst basiert Sie auf dem übergeordneten Element. Weitere Informationen finden Sie unten im Abschnitt "Sicherheit".                                   |
||

> [!Note]
> Eine Verknüpfung braucht nur **einen** den "Ziel"felder (Externe URL, Webseite, Umfrage, Webdatei, Ereignis, Forum) zugewiesenen Wert und eine Verknüpfung nur ein Ziel. Beispielsweise zeigt eine Verknüpfung nicht gleichzeitig auf eine Webseite und eine Umfrage oder eine externe URL und eine Internet-Datei. Wenn mehr als ein Zielattribut für eine Verknüpfung besteht, nimmt die Verknüpfung einfach das erste und ignoriert die anderen. Die Reihenfolge der Prioritäten, für die das Ziel ausgewählt wird, ist auf der Hauptabkürzungsform angegeben. So wird zunächst überprüft, ob eine externe URL für die Verknüpfung vorhanden ist und wenn ja, wird das Ziel der Verknüpfung dann die externe URL sein und alle anderen Zielattribute ignoriert werden. Falls es kein externe URL gibt, wird die Verknüpfung die Webseite überprüfen, dann die Umfrage, die Internetdatei, das Ereignis und schließlich das Forum. 

## <a name="secure-shortcuts"></a>Verknüpfungen sichern

Sicherheit für Verknüpfungen basieren entweder auf der übergeordneten Seite der Verknüpfung oder dem Ziel der Verknüpfung. Dies bestimmt, ob die Verknüpfung in der Siteübersicht angezeigt wird oder nicht. Wenn die Sicherheit auf dem übergeordneten Element basiert, dann kann der Schreibzugriff des Ziels der Verknüpfung immer noch bestimmen, ob die Bearbeitung auf der Vorderseite funktioniert, nachdem die Verknüpfung verwendet wurde, um zum Ziel der Verknüpfung zu navigieren. Deshalb hat die Verknüpfungssicherheit lediglich einen Einfluss auf die Navigation sowie die Bearbeitungsrechte für die vorderseitige Bearbeitung von Verknüpfungen. Die Sicherheitsmethode, die verwendet wird, ist für die Verknüpfung spezifisch. Wenn Sie den booleschen Wert **Verknüpfungszielüberprüfung deaktivieren** nicht auswählen, basiert die Sicherheit der Verknüpfung auf dem Ziel, ansonsten auf der Übergeordneten.

## <a name="navigate-with-shortcuts"></a>Navigieren mit Verknüpfungen

Sobald die Verknüpfungsentität erstellt wurde, wird sie in Ihrer Website angezeigt. Im Beispiel oben enthält die Grundseite zwei weitere Seiten, Seite Eins und Seite Zwei. Seite Zwei ist eine untergeordnete Seite, die ein untergeordnetes Element der Startseite ist. Darüber hinaus gibt es eine Verknüpfung, die der Startseite untergeordnet ist und auf Seite Zwei verweist. 
