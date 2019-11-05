---
title: Platzieren von untergeordneten Knoten mithilfe von Tastenkombinationen für ein Portal | MicrosoftDocs
description: Anweisungen zum Platzieren von untergeordneten Knoten mithilfe von Tastenkombinationen für Portale.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e004b0f4f37a57e37d8f847ad7221e6a50d549ed
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551575"
---
# <a name="place-child-nodes-by-using-shortcuts-for-portals"></a>Untergeordnete Knoten mithilfe von Tastenkombinationen für Portale platzieren
Verwenden Sie Verknüpfungen, um untergeordnete Knoten in der Sitemap Ihres Portals zu platzieren, die einfach auf andere, in Ihrer Sitemap vorhandene Knoten oder auf URLs verweisen, die sich außerhalb Ihres Portals befinden. Anders ausgedrückt: Webseiten, Webdateien, Ereignisse und Foren können als "Solid"-Knoten der Sitemap Ihres Portals angesehen werden: Sie werden zu Ihrer Sitemap hinzugefügt. Wenn Sie zu ihnen navigieren, sehen Sie den eigentlichen Inhalt dieser Knoten direkt. Verknüpfungen hingegen können als "immaterielle" Knoten betrachtet werden: Sie werden auch der Sitemap hinzugefügt (im Gegensatz zu Weblinks, die nicht sind). Wenn Sie zu ihnen navigieren, wird der Inhalt für den Ziel-"Solid"-Knoten angezeigt, auf den die Verknüpfung verweist, und der Inhalt ist wird von der Seitenvorlage für diesen Knoten gerendert.

## <a name="manage-shortcuts"></a>Verknüpfungen verwalten

Verknüpfungen können in powerapps-Portalen erstellt, bearbeitet und gelöscht werden.

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu Portale **&gt;** Verknüpfungen. 

3. Wählen Sie **neu**aus, um eine Verknüpfung zu erstellen. 

4. Um eine vorhandene Verknüpfung zu bearbeiten, wählen Sie die vorhandene Verknüpfung im Raster aus. 

5. Geben Sie Werte für die angegebenen Felder ein. 

6. Wählen Sie **& schließen speichern** aus.

### <a name="attributes-and-relationships"></a>Attribute und Beziehungen

| Name                               | Beschreibung                                                                                                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                               | Ein beschreibender Name für die Verknüpfung. Nur zur internen Verwendung.                                                                                                                                  |
| Website                            | Die Website, zu der die Verknüpfung gehört.                                                                                                                                                    |
| Übergeordnete Seite                        | Die übergeordnete Webseite der Verknüpfungs Entität in der Sitemap. Die Verknüpfung wird der Sitemap als untergeordnetes Element dieser Seite hinzugefügt.                                                                 |
| Externe URL                       | Das Ziel der Verknüpfung zu einer URL einer Ressource außerhalb Ihrer Organisation.                                                                                                                  |
| Webseite                           | Das Ziel der Verknüpfung zu einer internen Webseite.                                                                                                                                               |
| Webdatei                           | Das Ziel der Verknüpfung zu einer Webdatei.                                                                                                                                                        |
| Veranstalter                              | Das Ziel der Verknüpfung zu einem Ereignis.                                                                                                                                                          |
| Forum                              | Das Ziel der Verknüpfung zu einem Forum.                                                                                                                                                           |
| Title                              | Der Titel für die Verknüpfung. Dies ist der Name, der in den Bereichen "Sitemap" und "untergeordneter Navigationsansicht" angezeigt wird. Wenn das Feld leer gelassen wird, wird stattdessen der Titel (oder Name) der Ziel Entität angezeigt. |
| Beschreibung                        | Eine Beschreibung, die in den untergeordneten Navigations Ansichten angezeigt wird. Optional.                                                                                                                                        |
| Anzeigereihenfolge                      | Die auf der Vorderseite bearbeitbare Position, in der die Verknüpfung in den Ansichten "Sitemap" und "untergeordneter Navigationsbereich" angezeigt wird, in Bezug auf andere Knoten in der Site Übersicht                                                      |
| Validierung des Verknüpfungs Ziels deaktivieren | Wenn diese Option deaktiviert ist, wird die Sicherheit der Verknüpfung auf dem Ziel basieren. Andernfalls basiert Sie auf dem übergeordneten Element. Weitere Informationen finden Sie unten unter Sicherheit.                                   |
||

> [!Note]
> Für eine Verknüpfung muss lediglich **eines** der Zielfelder (externe URL, Webseite, Umfrage, Webdatei, Ereignis, Forum) zugewiesen werden, und eine Verknüpfung verfügt nur über ein Ziel. Eine Verknüpfung zeigt z. b. nicht auf eine Webseite und eine Umfrage oder eine externe URL und eine Webdatei. Wenn für eine Verknüpfung mehr als ein Ziel Attribut vorhanden ist, wird für die Verknüpfung nur das erste Ziel Attribut verwendet, wobei alle anderen ignoriert werden. Die Reihenfolge der Priorität, für die das Ziel ausgewählt wird, wird im Haupt Verknüpfungs Formular widergespiegelt. Daher wird zuerst überprüft, ob eine externe URL für die Verknüpfung vorhanden ist. ist dies der Fall, wird das Ziel der Verknüpfung als externe URL verwendet, und alle anderen Ziel Attribute werden ignoriert. Wenn keine externe URL vorhanden ist, prüft die Verknüpfung die Webseite, dann die Umfrage, die Webdatei, das Ereignis und schließlich das Forum. 

## <a name="secure-shortcuts"></a>Sichere Verknüpfungen

Die Sicherheit für Verknüpfungen kann entweder auf der übergeordneten Seite der Verknüpfung oder auf dem Ziel der Verknüpfung basieren. Dadurch wird festgelegt, ob die Verknüpfung in der Sitemap sichtbar ist. Wenn die Sicherheit auf dem übergeordneten Element basiert, bestimmt der Schreibzugriff für das Ziel der Verknüpfung trotzdem, ob die vorherige Bearbeitung funktioniert, nachdem die Verknüpfung verwendet wurde, um zum Ziel der Verknüpfung zu navigieren. Daher wirkt sich die Verknüpfungs Sicherheit nur auf die Navigations-und Bearbeitungs Rechte für die Seiten Bearbeitung von Tastenkombinationen aus. Die verwendete Sicherheitsmethode ist spezifisch für die Verknüpfung. Wenn Sie den booleschen Wert nicht ausgewählt, deaktivieren Sie die Verknüpfung von Verknüpfungs **Ziel deaktivieren** , wird die Sicherheit der Verknüpfung auf dem Ziel basieren. Andernfalls basiert Sie auf dem übergeordneten Element.

## <a name="navigate-with-shortcuts"></a>Navigieren mit Verknüpfungen

Nachdem die Verknüpfungs Entität erstellt wurde, wird Sie in der Website angezeigt. Im obigen Beispiel hat die Basic-Website zwei weitere Seiten, Seite 1 und Seite 2. Seite 2 ist ein untergeordnetes Element von Seite 1, das ein untergeordnetes Element der Startseite ist. Außerdem gibt es eine Verknüpfung, bei der es sich um ein untergeordnetes Element der Startseite handelt, das auf Seite 2 zeigt. 
