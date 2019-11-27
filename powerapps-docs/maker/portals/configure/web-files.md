---
title: Erstellen und Verwalten von Webdateien in PowerApps-Portalen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Webdateien in einem Portal erstellen und verwalten
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760458"
---
# <a name="create-and-manage-web-files"></a>Erstellen und Verwalten von Webdateien

Eine Webdatei ist eine herunterladbare Datei in einer Portalwebsite, die verwendet wird, um Bilder, Dokumente und andere Dateitypen zu speichern.

Um den eigentlichen Inhalt einer Datei zu speichern, verwenden Portale die Anlagenfunktion der Notizen, die einem Webdateidatensatz zugeordnet werden. Die Dateianlage der neuesten Notiz, die der Webdatei zugeordnet ist, wird als Dateiinhalt verwendet. Daher wird die Größe der Webdateiinhalte, die von Portalen unterstützt werden können, durch die Größe der Notizanhänge bestimmt, die von Ihrer Dynamics 365-Installation unterstützt werden.

## <a name="manage-web-files"></a>Verwalten von Webdateien

Webdateien können innerhalb von PowerApps-Portalen erstellt, bearbeitet oder gelöscht werden.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** > **Webdateien**.

3. Um eine neue Webdatei zu erstellen, klicken Sie auf **Neu**.

4. Wenn Sie eine vorhandene Webdatei bearbeiten, wählen Sie den Namen der Webdatei aus.

5. Hinzufügen der entsprechenden Werte zu den Feldern.

6. Klicken Sie auf **Speichern und schließen**.

### <a name="web-file-attributes"></a>Webdateiattribute

Die Tabelle unten erklärt viele der Standardattribute von Webdateien, die von Portalen verwendet werden. Es ist wichtig, zu beachten, wie einige der Attribute für die Inhalte/die Anzeige gerendert werden, basierend auf der vom Portalentwickler erstellten Ansicht.

| Name                | Beschreibung               |
|---------------------|-----------------------|
|Name |Der beschreibende Name der Entität. Dieser Wert wird in den meisten Vorlagen als Dateititel verwendet (z. B. für Link-Titel). In diesem Feld ist ein Eintrag erforderlich.   |
|Website   |Die Website, zu der die Entität gehört. In diesem Feld ist ein Eintrag erforderlich.   |
|Übergeordnete Seite   |Die übergeordnete Webseite der Entität in der Websiteinhaltshierarchie. <br>Obwohl keine Datei erforderlich ist, um eine übergeordnete Seite zu erstellen, verfügt eine Seite in einigen Szenarien stattdessen z. B. über einen übergeordneten Blogbeitrag. Die Bereitstellung einer übergeordneten Seite ist in den meisten Fällen die empfohlene Konfiguration.  |
|Teil-URL   |Das URL-Pfadsegment, das zur Erstellung der Portal-URL dieser Seite verwendet wird.. <br>Die einzelne Stammhomepage Ihrer Website – die einzige Seite, der keine übergeordnete Seite zugewiesen ist – muss den partiellen URL-Wert / haben.<br>Partielle URL-Werte werden als URL-Pfadsegmente verwendet. Daher sollten sie keine ungültigen URL-Pfadzeichen enthalten, wie ?, #, !, %. Da Adxstudio Portals-URLs generiert werden, indem Teil-URL-Werte mit Schrägstrichen (/) verknüpft werden, sollten sie diese Schrägstriche grundsätzlich nicht enthalten. Die empfohlene Vorgehensweise ist, partielle URL-Werte auf Buchstaben, Zahlen und Bindestriche oder Unterstriche zu beschränken. Beispiel: press-release.pdf, Site_Header.png.  |
|Veröffentlichungsstatus   |Der aktuelle Veröffentlichungsworkflowstatus der Datei, der möglicherweise vorgibt, ob die Datei auf der Website angezeigt wird oder nicht. Häufig wird diese Funktion verwendet, um Inhalte als veröffentlicht/Entwurf bereitzustellen.<br>Benutzern mit Berechtigungen für Inhaltsverwaltung kann die Möglichkeit zur Nutzung des „Vorschaumodus” gewährt werden. Dies ermöglicht es diesen Benutzern, nicht veröffentlichten Inhalt anzuzeigen (Vorschau).   |
| Anzeigedatum        | Dieses Attribut ist ein Datums-/Uhrzeitwert, der zur Anzeige von einer Vorlage verwendet werden kann. Es bestehen keine funktionalen Auswirkungen, es kann jedoch hilfreich sein, um beispielsweise ein Veröffentlichungsdatum einer Pressemitteilungsdokument manuell anzugeben.    |
| Veröffentlichungsdatum        | Steuert das Datum/die Uhrzeit, ab der die Datei auf dem Portal sichtbar ist. Wenn das aktuelle Datum/die aktuelle Uhrzeit vor diesem Datum liegt, wird diese Datei nicht angezeigt. (Eine Ausnahme stellt dabei ist, dass Benutzer mit Berechtigungen zur Inhaltsverwaltung Möglichkeit gewährt werden können, den Seitenansichtsmodus zu verwenden, mit dem diese Benutzer unveröffentlichten Inhalt (als Vorschau) anzeigen können.) Dies ist nützlich, um die Veröffentlichung von zeitkritischen Inhalten, beispielsweise Nachrichten oder Pressemitteilungen zu steuern. |
| Ablaufdatum     | Steuert das Datum/die Uhrzeit, ab der die Datei auf dem Portal sichtbar ist. Wenn das aktuelle Datum/die aktuelle Uhrzeit nach diesem Datum liegt, wird diese Datei nicht angezeigt. Ausnahme: Benutzern mit der Berechtigung „Inhaltsverwaltung“ kann die Möglichkeit zur Nutzung des Vorschaumodus eingeräumt werden. Dieser stellt eine Vorschau des abgelaufenen Inhalts bereit.                |
| Zusammenfassung             | Eine Kurzbeschreibung für die Datei. Dieser Wert wird im Allgemeinen verwendet, um eine Beschreibung der Datei zu den Navigationselementen des Portals hinzuzufügen, die einen Link zu der Datei rendern.      |
| In Siteübersicht ausgeblendet | Steuert, ob die Datei als Teil der Portalsiteübersicht angezeigt wird. Wenn dieser Wert ausgewählt wird, ist die Datei auf der Website noch unter ihrer URL verfügbar und es können Verknüpfungen zu ihr erstellt werden, aber die Standardnavigationselemente (Menüs usw.) enthalten die Seite nicht.      |
| Anzeigereihenfolge       | Ein ganzzahliger Wert, der die Reihenfolge angibt, in der die Datei platziert wird, im Verhältnis zu anderen Entitäten mit der gleichen übergeordneten Seite. Hiermit wird die Reihenfolge von Dateien und anderen Siteübersichtsentitäten gesteuert, wenn beispielsweise eine Liste der Links zu untergeordneten Entitäten eine bestimmten Seite im Portal gerendert werden.      |
| Cloud Blob-Adresse  | Ein Textwert im Format `<container>/<filename>` zeigt an, dass der Inhalt für diese Datei in Azure Blob Storage gespeichert ist.        |
| Inhaltsdisposition | Mögliche Optionen sind "Inline" oder "Anlage". Bei "Inline" sollte der Browser versuchen die Inhalte innerhalb des Browserfensters zu rendern. Wenn dies nicht möglich ist, wird der Benutzer aufgefordert die Datei herunterzuladen oder zu öffnen. Wenn "Anlage" angegeben ist, wird der Benutzer sofort aufgefordert die Datei herunterzuladen oder zu öffnen. Sie wird nicht im Browser geladen (egal, ob das möglich ist oder nicht).                                                                                        |
| Nachverfolgung aktivieren     | Sofern aktiviert, wird jede Anforderung dieser Datei protokolliert. Ein Webdateiprotokolldatensatz wird mit dem Datum und der Uhrzeit, der IP-Adresse und dem Kontaktdatensatz erstellt, wenn der Benutzer authentifiziert wird.      |
|||



