---
title: Verwalten von in Weblinks | MicrosoftDocs
description: Anweisungen zum Verwalten von Internetlinks.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: d8e2421545247f72b5b164e08b4ac210466048c1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866837"
---
# <a name="manage-web-links"></a>Verwalten von Weblinks

Ein Weblink kann mit jeder beliebigen URL oder mit einer anderen Webseite innerhalb derselben Website verknüpft sein. Wenn ein Weblink mit einer Webseite verknüpft ist, gelten der Sicherheits- und der Veröffentlichungsstatus der Webseite auch für den Weblink. Weblinks sind immer Teil eines Weblinksatzes. Ein Weblinksatz ist eine Gruppe von Links, wie z.B. eine primäre Navigation oder eine Gruppe Fußzeilenlinks. Weblinksätze lassen die Gruppierung und Sortierung von externen und internen Links unabhängig von der Platzierung in der Sitemap zu.

## <a name="manage-web-links-in-power-apps-portals"></a>Verwalten von Weblinks in Power Apps-Portalen

Sobald die Anpassungen des Portals in die Common Data Service-Umgebung importiert wurden, können Weblinks über einen Weblinksatz verwaltet werden.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Öffnen Sie **Portale** > **Weblinksätze**.

3. Um ein neues Weblinkset zu erstellen, klicken Sie auf **Neu**.

4. Wenn Sie einen vorhandenen Internet-Linksatz bearbeiten, wählen Sie den Namen des Internet- Dialogfeld aus.

5. Hinzufügen der entsprechenden Werte zu den Feldern.

6. Wenn Sie einen neuen Internet-Linksatz erstellen wählen Sie **Speichern**, um den Datensatz speichern sodass Sie Internet-Links hinzufügen können.

7. Wechseln Sie zur Registerkarte **Links**.

8. Um einen neuen Weblink zu erstellen, wählen Sie **Neuer Internetlink**.

    ![Weblink hinzufügen](../media/add-web-link.png "Weblink hinzufügen")

9. Wenn Sie einen vorhandenen Internet-Linksatz bearbeiten, wählen Sie den Namen des Internet- Dialogfeld aus.

9. Hinzufügen der entsprechenden Werte zu den Feldern.

6. Speichern Sie die Änderungen.

## <a name="web-link-set-attributes-and-relationships"></a>Weblinksatz-Attribute und -Beziehungen

Die Tabelle unten erklärt viele der Standardattribute von Weblinksatz-Eigenschaften, die von Portalen verwendet werden. Es ist wichtig, zu beachten, wie einige der Eigenschaften für die Inhalte/die Anzeige gerendert werden, basierend auf der verwendeten Seitenvorlage.

| Name    | Beschreibung                                                                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name    | Der beschreibende Name des Weblinksatzes. Dieser Wert beschreibt in der Regel die Platzierung des Satzes in der Seitenvorlage, beispielsweise „Primäre Navigation“. In diesem Feld ist ein Eintrag erforderlich.                   |
| Website | Die Website, zu der die Entität gehört. In diesem Feld ist ein Eintrag erforderlich.                                                                                                                             |
| Titel   | Ein optionaler Titel für den Weblinksatz. Dieser Wert kann auf dem Portal verwendet werden, wenn er ein Teil der Seitenvorlage ist. Er kann beispielsweise "Unsere Partner" lauten und in der Randleiste angezeigt werden.    |
| Kopieren    | Eine optionaler Beschreibung für den Weblinksatz. Dieser Wert kann auf dem Portal verwendet werden, wenn er ein Teil der Seitenvorlage ist. Sie kann beispielsweise "Unsere Partner" in der Randleiste näher beschreiben. |
||

## <a name="web-link-attributes-and-relationships"></a>Weblink-Attribute und -Beziehungen

Die Tabelle unten erklärt viele der Weblink-Standardeigenschaften, die von Portalen verwendet werden. Es ist wichtig, zu beachten, wie einige der Eigenschaften für die Inhalte/die Anzeige gerendert werden, basierend auf der verwendeten Seitenvorlage.


|           Name           |                                                                                                               Beschreibung                                                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Name           |                                                          Der Titel des Weblinks. Dieser Wert wird als Weblink-Überschrift in den meisten Vorlagen verwendet. In diesem Feld ist ein Eintrag erforderlich.                                                           |
|       Weblinksatz       |                                                                                  Der Weblinksatz, zu der die Entität gehört. In diesem Feld ist ein Eintrag erforderlich.                                                                                  |
|     Übergeordneter Weblink      |                                      Der übergeordnete Weblink der Entität in einem Weblinksatz mit mehreren Ebenen. Wenn kein übergeordneter Weblink angegeben wurde, ist die Entität auf der obersten Ebene oder der Stammebene des Weblinksatzes.                                      |
|           Seite           |                                                                                          Eine optionale Webseite auf derselben Website, auf die verlinkt wurde.                                                                                          |
|        Externe URL      |                                                                                Eine optionale URL auf die verlinkt wird. Dieser Wert kann jede ordnungsgemäß formatierte URL sein.                                                                                |
|       Beschreibung        |                                                              Eine optionale Zusammenfassung für den Weblink. Dieser Wert kann auf dem Portal verwendet werden, wenn er ein Teil der Seitenvorlage ist.                                                              |
|     Veröffentlichungsstatus     | Der aktuelle Veröffentlichungsworkflowstatus des Weblinks, der möglicherweise vorgibt, ob der Weblink auf der Website angezeigt wird oder nicht. Häufig wird diese Funktion verwendet, um Inhalte als veröffentlicht/Entwurf bereitzustellen. In diesem Feld ist ein Eintrag erforderlich. |
|    Roboter folgen Link    |                                                           Gibt an, ob Suchroboter dem Link folgen und den Inhalt des Links indizieren können oder nicht. In diesem Feld ist ein Eintrag erforderlich.                                                            |
|      Anzeigereihenfolge       |                                                  Ein ganzzahliger Wert, der die Reihenfolge angibt, in der der Weblink platziert wird, im Verhältnis zu anderen Weblinks mit dem gleichen übergeordneten Weblinksatz.                                                  |
| Untergeordnete Seitenlinks anzeigen |  In einer Vorlage, die Weblinksätze mit mehreren Ebenen unterstützt, werden untergeordnete Links für diese Entität über den Siteübersichts-Anbieter des Portals erstellt. Beachten Sie, dass diese Option nur für Weblinks gilt, die auf interne Seiten verweisen und nicht auf externe URLs.  |
|    In neuem Fenster öffnen    |                                                                            Gibt an, ob beim Auswählen des Links dieser in einem neuen Browserfenster geöffnet wird.                                                                             |
| Seitenüberprüfung deaktivieren  |                                                                       Gibt an, ob die Sicherheit einer verlinkten Webseite auch auf den Weblink angewendet wird.                                                                       |
|        Bild-URL         |                                                   Eine optionale URL zu einem Bild. Das verknüpfte Bild kann auf dem Portal verwendet werden, wenn es ein Teil der Seitenvorlage ist; beispielsweise als Symbol.                                                   |
|       Bildhöhe       |                                                                                      Eine optionale Höhe des Bilds aus den Bild-URL-Eigenschaften.                                                                                      |
|       Bildbreite        |                                                                                      Eine optionale Breite des Bilds aus den Bild-URL-Eigenschaften.                                                                                       |
|      Alternativer Bildtext      |                                                                                   Eine optionale Beschreibung des Bilds aus den Bild-URL-Eigenschaften.                                                                                    |
|    Nur Bild anzeigen    |                                                   Gibt an, dass die Vorlage nur einen Bildlink dieses Weblinks rendert, nicht Bild und Linknamen gemeinsam.                                                    |
|                          |                                                                                                                                                                                                                                         |

> [!Note]
> - Wenn ein Weblink mit einer Webseite verknüpft ist, gelten der Sicherheits- und der Veröffentlichungsstatus der Webseite auch für den Weblink. Diese Überprüfung mit der Option "Seitenüberprüfung deaktivieren" deaktiviert werden. 
>   - Benutzern mit Berechtigungen für Inhaltsverwaltung kann die Möglichkeit zur Nutzung des „Vorschaumodus” gewährt werden. Dies ermöglicht es diesen Benutzern, nicht veröffentlichten Inhalt anzuzeigen (Vorschau).

### <a name="see-also"></a>Siehe auch

[Anpassen von Inhalt mit Inhaltsausschnitten](customize-content-snippets.md)
