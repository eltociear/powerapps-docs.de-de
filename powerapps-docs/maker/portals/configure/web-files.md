---
title: Erstellen und Verwalten von Webdateien in powerapps-Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie Webdateien in einem Portal erstellen und verwalten.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dc67db92ac502611b0c10b5d387b100e8aa43da7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551253"
---
# <a name="create-and-manage-web-files"></a>Erstellen und Verwalten von Webdateien

Eine Webdatei stellt eine herunterladbare Datei auf einer Portale-Website dar, die zum Speichern von Bildern, Dokumenten und einem beliebigen anderen Dateityp verwendet wird.

Zum Speichern der eigentlichen Inhalte einer bestimmten Datei verwendet Portale das Anlagen Feature der Notizen, die einem Webdatei Daten Satz zugeordnet sind. Die Datei Anlage des neuesten Hinweises, der der Webdatei zugeordnet ist, wird als Dateiinhalt verwendet. Daher wird die Größe des Webanwendungs Inhalts, der von Portalen unterstützt werden kann, von der von der Dynamics 365-Installation unterstützten Anfüge Größe bestimmt.

## <a name="manage-web-files"></a>Verwalten von Webdateien

Webdateien können innerhalb von powerapps-Portalen erstellt, bearbeitet und gelöscht werden.

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** > **Webdateien**.

3. Wählen Sie **neu**aus, um eine neue Webdatei zu erstellen.

4. Um eine vorhandene Webdatei zu bearbeiten, wählen Sie den Namen der Webdatei aus.

5. Geben Sie entsprechende Werte in die Felder ein.

6. Wählen Sie **Speichern und Schließen** aus.

### <a name="web-file-attributes"></a>Webdatei Attribute

In der folgenden Tabelle werden viele der Standard Attribute der Webdatei erläutert, die von Portalen verwendet werden. Es ist wichtig zu beachten, dass die Art und Weise, in der viele der Inhalt/Anzeige-orientierten Attribute gerendert werden, von der verwendeten Seitenvorlage und somit vom Portal Entwickler gesteuert wird.

| Name                | Beschreibung               |
|---------------------|-----------------------|
|Name |Der beschreibende Name der Entität. Dieser Wert wird als Datei Titel in den meisten Vorlagen verwendet (z. b. für Verknüpfungs Titel). Dieses Feld ist erforderlich.   |
|Website   |Die Website, zu der die Entität gehört. Dieses Feld ist erforderlich.   |
|Übergeordnete Seite   |Die übergeordnete Webseite der Entität in der Website-Inhalts Hierarchie. <br>Obwohl eine Datei keine übergeordnete Seite haben muss – in einigen Szenarios kann es beispielsweise vorkommen, dass eine Datei über einen übergeordneten Blogbeitrag verfügt – wenn eine übergeordnete Seite in den meisten Fällen die empfohlene Konfiguration ist.  |
|Partielle URL   |Das URL-Pfad Segment, das verwendet wird, um die Portal-URL dieser Seite zu erstellen. <br>Die Seite "Single root (Home)" Ihrer Website – die einzelne Seite, die keine zugeordnete übergeordnete Seite besitzt – muss einen partiellen URL-Wert von "/" aufweisen.<br>Partielle URL-Werte werden als URL-Pfadsegmente verwendet. Daher sollten Sie keine ungültigen URL-Pfad Zeichen wie?, #,!,% enthalten. Da adxstudio-Portale-URLs generiert werden, indem partielle URL-Werte mit Schrägstrichen (/) miteinander verknüpft werden, sollten Sie in der Regel auch keine Schrägstriche enthalten. Die empfohlene Vorgehensweise besteht darin, partielle URL-Werte auf Buchstaben, Zahlen und Bindestriche oder Unterstriche einzuschränken. Beispiel: Press-Release. PDF, Site_Header. png.  |
|Veröffentlichungsstatus   |Der aktuelle Veröffentlichungs Workflow Status der Datei, mit der festgelegt werden kann, ob die Datei auf der Site sichtbar ist. Diese Funktion wird am häufigsten verwendet, um das Veröffentlichen/Entwerfen von Inhalten über Inhalte bereitzustellen.<br>Benutzern mit Inhalts Verwaltungs Berechtigungen kann die Möglichkeit zur Verwendung des Vorschaumodus erteilt werden, der es diesen Benutzern ermöglicht, nicht veröffentlichte Inhalte anzuzeigen (Vorschau).   |
| Anzeige Datum        | Bei diesem Attribut handelt es sich um einen Datums-/Uhrzeitwert, der von einer Vorlage ausschließlich zu Anzeige Zwecken verwendet werden kann. Dies hat keine funktionalen Implikationen, kann jedoch hilfreich sein, wenn z. b. ein veröffentlichtes Datum in einem Press releasedokument manuell angegeben wird.    |
| Veröffentlichungsdatum        | Steuert einen Zeitpunkt (Datum und Uhrzeit), nach dem die Datei im Portal angezeigt wird. Wenn das aktuelle Datum/die aktuelle Uhrzeit vor diesem Datum liegt, wird diese Datei nicht angezeigt. (Die Ausnahme ist, dass Benutzern mit Inhalts Verwaltungs Berechtigungen möglicherweise die Möglichkeit zur Verwendung des Vorschaumodus erteilt wird, der es diesen Benutzern ermöglicht, nicht veröffentlichte Inhalte anzuzeigen.) Dies ist hilfreich, um die Veröffentlichung Zeit sensibler Inhalte, wie z. b. Nachrichten oder Pressemitteilungen, zu steuern. |
| Ablaufdatum     | Steuert einen Zeitpunkt (Datum und Uhrzeit), zu dem die Datei im Portal angezeigt wird. Wenn das aktuelle Datum/die aktuelle Uhrzeit nach diesem Datum liegt, wird diese Datei nicht angezeigt. (Die Ausnahme ist, dass Benutzern mit Inhalts Verwaltungs Berechtigungen möglicherweise die Möglichkeit zur Verwendung des Vorschaumodus erteilt wird, der es diesen Benutzern ermöglicht, abgelaufene Inhalte anzuzeigen (Vorschau).)                |
| FAS             | Eine kurze Beschreibung für die Datei. dieser Wert wird im Allgemeinen verwendet, um eine Beschreibung der Datei zu den Navigationselementen des Portals hinzuzufügen, die einen Link zur Datei Rendering.      |
| Aus Sitemap ausblenden | Steuert, ob die Datei sichtbar ist, ist Teil der Portal Site Übersicht. Wenn dieser Wert aktiviert ist, ist die Datei auf der Website weiterhin unter der URL verfügbar und kann verknüpft werden, aber standardmäßige Navigationselemente (Menüs usw.) enthalten die Seite nicht.      |
| Anzeigereihenfolge       | Ein ganzzahliger Wert, der die Reihenfolge angibt, in der die Datei platziert wird, relativ zu anderen Entitäten mit derselben übergeordneten Seite. Dies steuert die Reihenfolge von Dateien und anderen Site Übersichts Entitäten, wenn z. b. eine Liste mit Links zu den untergeordneten Entitäten einer bestimmten Seite im Portal gerendert wird.      |
| Cloud-BLOB-Adresse  | Ein Textwert im Format `<container>/<filename>`, der angibt, dass der Inhalt für diese Datei in Azure BLOB Storage gespeichert wird.        |
| Inhalts Disposition | Optionen sind Inline oder Anlage. Wenn Inline angegeben ist, sollte der Browser versuchen, ihn im Browserfenster zu verwenden. wenn dies nicht möglich ist, wird der Benutzer aufgefordert, die Datei herunterzuladen oder zu öffnen. Wenn Anlage angegeben ist, wird der Benutzer sofort aufgefordert, die Datei herunterzuladen oder zu öffnen, und es wird nicht versucht, Sie im Browser zu laden.                                                                                        |
| Überwachung aktivieren     | Wenn diese Option aktiviert ist, wird jede Anforderung für diese Webdatei protokolliert. Ein Webdatei-Protokolldaten Satz wird mit dem Datum & Uhrzeit, der IP-Adresse und dem Kontaktdaten Satz erstellt, wenn der Benutzer authentifiziert ist.      |
|||



