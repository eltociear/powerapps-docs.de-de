---
title: Verwalten von Weblinks | MicrosoftDocs
description: Anweisungen zum Verwalten von Weblinks.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5d0ead5104765ab71848ffcf8c4aaff801a58a20
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551782"
---
# <a name="manage-web-links"></a>Verwalten von Weblinks

Ein Weblink kann mit einer beliebigen URL verknüpft werden, oder er kann mit einer anderen Webseite auf derselben Website verknüpft werden. Wenn ein Weblink zu einer Webseite gehört, gilt der Sicherheits-und Veröffentlichungsstatus der Webseite auch für den Weblink. Weblinks sind immer Teil einer weblinkmenge. Eine weblinkgruppe ist eine Gruppe von Links, z. b. eine primäre Navigation oder eine Gruppe von footerLinks. Weblinksets lassen intern zu, unabhängig von der Platzierung in der Site Übersicht und externe Links, die gruppiert und sortiert werden.

## <a name="manage-web-links-in-powerapps-portals"></a>Verwalten von Weblinks in powerapps-Portalen

Nachdem die Portal Anpassungen in die Common Data Service Umgebung importiert wurden, können Weblinks über einen weblinksatz verwaltet werden.

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** > **weblinksets**.

3. Wählen Sie **neu**aus, um einen neuen weblinksatz zu erstellen.

4. Um einen vorhandenen weblinksatz zu bearbeiten, wählen Sie den Namen der weblinkgruppe aus.

5. Geben Sie entsprechende Werte in die Felder ein.

6. Wenn Sie einen neuen weblinksatz erstellen, wählen Sie **Speichern** aus, um den Datensatz zu speichern, damit Sie Weblinks hinzufügen können.

7. Wechseln Sie zur Registerkarte " **Links** ".

8. Um einen neuen Weblink zu erstellen, wählen Sie **neuer Weblink**aus.

    ![Weblink hinzufügen](../media/add-web-link.png "Weblink hinzufügen")

9. Wählen Sie den Namen des Weblinks aus, um einen vorhandenen Weblink zu bearbeiten.

9. Geben Sie entsprechende Werte in die Felder ein.

6. Speichern Sie die Änderungen.

## <a name="web-link-set-attributes-and-relationships"></a>Attribute und Beziehungen für weblinksätze

In der folgenden Tabelle werden viele der standardmäßigen weblinkseteigenschaften erläutert, die von Portalen verwendet werden. Es ist wichtig zu beachten, dass die Art und Weise, in der viele der Inhalt/Anzeige-orientierten Eigenschaften gerendert werden, von der verwendeten Seitenvorlage gesteuert wird.

| Name    | Beschreibung                                                                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name    | Der beschreibende Name der weblinkgruppe. Dieser Wert beschreibt in der Regel die Platzierung der Menge in der Seitenvorlage, z. b. die primäre Navigation. Dieses Feld ist erforderlich.                   |
| Website | Die Website, zu der die Entität gehört. Dieses Feld ist erforderlich.                                                                                                                             |
| Title   | Ein optionaler Titel für den weblinksatz. Dieser Wert kann im Portal verwendet werden, wenn er Teil der Seitenvorlage ist. Dies könnte ein Beispiel für unsere Partner sein und in einer Seitenleiste angezeigt werden.    |
| Skopie    | Eine optionale Beschreibung für den weblinksatz. Dieser Wert kann im Portal verwendet werden, wenn er Teil der Seitenvorlage ist. Es könnte eine weitere Beschreibung der Partner in einer Seitenleiste enthalten. |
||

## <a name="web-link-attributes-and-relationships"></a>Weblink Attribute und-Beziehungen

In der folgenden Tabelle werden viele der standardmäßigen Weblink Eigenschaften erläutert, die von Portalen verwendet werden. Es ist wichtig zu beachten, dass die Art und Weise, in der viele der Inhalt/Anzeige-orientierten Eigenschaften gerendert werden, von der verwendeten Seitenvorlage gesteuert wird.


|           Name           |                                                                                                               Beschreibung                                                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Name           |                                                          Der Titel für den Weblink. Dieser Wert wird in den meisten Vorlagen als Weblink Titel verwendet. Dieses Feld ist erforderlich.                                                           |
|       Weblinksatz       |                                                                                  Der weblinksatz, zu dem die Entität gehört. Dieses Feld ist erforderlich.                                                                                  |
|     Übergeordneter Weblink      |                                      Der übergeordnete Weblink der Entität in einer mehrstufigen weblinkmenge. Wenn kein übergeordneter Weblink angegeben ist, wird die Entität auf der obersten/Stamm Ebene der weblinkgruppe angezeigt.                                      |
|           s           |                                                                                          Eine optionale Webseite von derselben Website, mit der eine Verknüpfung hergestellt werden soll.                                                                                          |
|        Externe URL      |                                                                                Eine optionale URL, mit der eine Verknüpfung hergestellt werden soll. Dieser Wert kann eine beliebige ordnungsgemäß formatierte URL sein.                                                                                |
|       Beschreibung        |                                                              Eine optionale Zusammenfassung für den Weblink. Dieser Wert kann im Portal verwendet werden, wenn er Teil der Seitenvorlage ist.                                                              |
|     Veröffentlichungsstatus     | Der aktuelle Veröffentlichungs Workflow Status des Weblinks, der möglicherweise vorgibt, ob der Weblink auf der Site sichtbar ist. Diese Funktion wird am häufigsten verwendet, um das Veröffentlichen/Entwerfen von Inhalten über Inhalte bereitzustellen. Dieses Feld ist erforderlich. |
|    Roboter folgen Link    |                                                           Gibt an, ob Suchindexer dem Inhalt der Verknüpfung folgen und ihn indizieren sollen. Dieses Feld ist erforderlich.                                                            |
|      Anzeigereihenfolge       |                                                  Ein ganzzahliger Wert, der die Reihenfolge angibt, in der der Weblink in Relation zu anderen Weblinks innerhalb derselben weblinkgruppe platziert wird.                                                  |
| Untergeordnete Links der Seite anzeigen |  Generieren Sie in einer Vorlage, die mehrstufige weblinksets unterstützt, untergeordnete Verknüpfungen für diese Entität mit dem Portal Site Übersichts Anbieter. Beachten Sie, dass diese Option nur für Weblinks gültig ist, die auf interne Seiten und nicht auf externe URLs verweisen.  |
|    In neuem Fenster öffnen    |                                                                            Gibt an, ob beim Auswählen des Links der Link in einem neuen Browserfenster geladen wird.                                                                             |
| Deaktivieren der Seiten Validierung  |                                                                       Gibt an, ob die Sicherheit einer verknüpften Webseite auch auf den Weblink angewendet wird.                                                                       |
|        Bild-URL         |                                                   Eine optionale URL zu einem Bild. Das verknüpfte Bild kann im Portal verwendet werden, wenn es Teil der Seitenvorlage ist. beispielsweise als Symbol.                                                   |
|       Bildhöhe       |                                                                                      Eine optionale Höhe für das Bild aus der Bild-URL-Eigenschaft.                                                                                      |
|       Bildbreite        |                                                                                      Eine optionale Breite für das Bild aus der Bild-URL-Eigenschaft.                                                                                       |
|      Bild-alt-Text      |                                                                                   Eine optionale Beschreibung des Bilds aus der Bild-URL-Eigenschaft.                                                                                    |
|    Nur Bild anzeigen    |                                                   Gibt an, dass die Vorlage nur einen Bildlink für diesen Weblink und nicht gleichzeitig den Bild-und Linknamen darstellen soll.                                                    |
|                          |                                                                                                                                                                                                                                         |

> [!Note]
> - Wenn ein Weblink zu einer Webseite gehört, gilt der Sicherheits-und Veröffentlichungsstatus der Webseite auch für den Weblink. Diese Überprüfung kann mit der Option Seiten Überprüfung deaktivieren deaktiviert werden. 
>   - Benutzern mit Inhalts Verwaltungs Berechtigungen kann die Möglichkeit zur Verwendung des Vorschaumodus erteilt werden, der es diesen Benutzern ermöglicht, nicht veröffentlichte Inhalte anzuzeigen (Vorschau).

### <a name="see-also"></a>Siehe auch

[Anpassen von Inhalten mithilfe von Inhalts Ausschnitten](customize-content-snippets.md)
