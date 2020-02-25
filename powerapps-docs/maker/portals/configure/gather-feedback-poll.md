---
title: Einholung von Feedback mit Umfragen im Portal | MicrosoftDocs
description: Anweisungen zum Erstellen von Abstimmungen und Sammeln von Feedback über deren Verwendung.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 561c67076e981c236f491638cdb6814ec56edcd7
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979969"
---
# <a name="gather-feedback-by-using-polls-on-a-portal"></a>Einholung von Feedback mit Umfragen im Portal

Mit Umfragen haben Ihre Web-Zielgruppen die schnelle und einfache Möglichkeit, ihre Ansicht zu bestimmten Themen zu äußern und das Feedback ihrer Abstimmung anschließend sofort automatisch anzuzeigen.

Verwenden Sie die Umfragefunktion der Portale, um Ihre Zielgruppe über Themen von Interesse zu befragen und Einzelantworten oder Auswahlantworten geben zu lassen. Auf jeden Fall werden ihre Antworten direkt gespeichert und dem entsprechenden Kontaktdatensatz zur sofortigen Überprüfung oder Aggregatsberichterstellung zugeordnet. Sie können Umfragen als einfache Marktforschungstools verwenden, und, wenn Sie die Umfragen dynamisch aktualisieren oder rotieren lassen, wirkt Ihre Website aktuell und relevant.

Umfragen können im Portal über das PollPlacement-Steuerelement platziert werden. Dieses Steuerelement funktioniert auf ähnliche Weise wie das AdPlacement-Steuerelement. Sollten Umfragen der Umfrageplatzierungsentität zugeordnet sein, die durch das PollPlacement-Steuerelement gerendert wird, werden diese Umfragen gerendert. Wenn es mehr als eine Umfrage für eine bestimmte Platzierung gibt, stellt die Platzierung zufällig eine der angegebenen Umfragen dar.

> [!Note]
> Benutzer können anonym wählen. Doppelte Stimmen sind nicht zulässig. Grundlegende Informationen zu Übermittlungen können nachverfolgt werden und die Übermittlungen von Benutzern, die sich bei der Website anmelden, werden mit der Kontaktentität, die diesen Benutzer in Common Data Service nachverfolgt, verknüpft.

## <a name="add-a-poll-to-the-page"></a>Fügen Sie der Seite eine Umfrage hinzu

Inhalts-Manager können [Vorlagen-Tags](../liquid/liquid-overview.md) verwenden, um eine Umfrage zu einem Bereich mit bearbeitbarem Inhalt hinzuzufügen:  

`{% include 'Random Poll' placement:polls.placements[Sidebar] %}`

oder

`{% include 'Poll Template' ad:ads[Wireframe Development] %}`

> [!Note]
> Beispiels-Internet-Vorlagen werden in den Starterwebsites konfiguriert. Möglicherweise verwenden Sie die Vorlage "Zufallsumfrage", um eine zufällige Umfrage von einer bestimmten Umfrage-Platzierung anzuzeigen, oder die Vorlage "Umfrage-Vorlage ", um eine bestimmte Umfrage anzuzeigen. Sie können diese Vorlagen bearbeiten oder dem Beispiel folgen und eigene mithilfe von [Umfragen](../liquid/liquid-objects.md#polls) erstellen. 

## <a name="create-a-poll-placement"></a>Erstellen einer Umfrageplatzierung

So erstellen Sie eine neue Umfrageplatzierungsregion:

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Öffnen Sie **Portale** > **Umfrageplatzierungen**.

3. Wählen Sie **Neu** aus.

4. Wählen Sie die zugeordnete **Website** aus, geben Sie der Platzierung einen Namen und wählen Sie &mdash;optional&mdash; die [Webvorlagen](../liquid/store-content-web-templates.md) aus, die das Rendern steuert.

5. Sobald die Platzierung erstellt wurde, müssen Sie mindestens eine Umfrage dieser Platzierung zuordnen. Klicken Sie in der **Umfrage**-Registerkarte der Umfrage-Platzierung-Entität auf die Schaltfläche **Vorhandene Umfrage hinzufügen**. 

6. In dem resultierenden Suchfeld wählen Sie einen vorhandenen Umfragedatensatz aus oder erstellen Sie eine neue Umfrage durch Klicken auf **Neue Umfrage**.
  

## <a name="polls"></a>Umfragen

Eine Umfrage ist eine einfache "Ja/Nein"- oder Multiple-Choice-Frage, die Sie im Portal über Umfrageplatzierungen anzeigen können. Es gibt viele anpassbare Möglichkeiten für die Anzeige von Umfragen für Entwickler, aber Inhalts-Manager können Umfragen auf Ihrer Website ganz einfach über die Auswahl einer Frage und einer Reihe möglicher Antworten (Umfrageoptionen) hinzufügen. Eine Umfrage muss zugehörige Optionen aufweisen, um zu funktionieren, und einer Umfrage-Platzierung zugeordnet werden, um im Portal gerendert zu werden.

Eine neue Umfrage kann auf zwei Arten erstellt werden: 
- Durch Navigation zum Abschnitt **Umfragen** im Bereich **Portale**.
- Durch Klicken auf die Schaltfläche **Neu** im Fenster **Datensätze nachschlagen** beim Hinzufügen einer Umfrage zu einer Umfragenplatzierung.

## <a name="poll-attributes"></a>Umfrageattribute

| Name                | Beschreibung                                                                                                                                                                                                                                                                                                                                  |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                | Der beschreibende Name der Umfrage.                                                                                                                                                                                                                                                                                                            |
| Website             | Die zugeordnete [Webvorlagen](../liquid/store-content-web-templates.md).                                                                                                                                                                                                                                                                |  
| Webvorlage        | Die zugeordnete [Webvorlage](../liquid/store-content-web-templates.md), die standardmäßig verwendet wird, um die Umfrage zu rendern. Dieses Feld ist optional; wenn es leer ist, wird die Umfrage mit einer Standardvorlage gerendert.                                                                                                                     |  
| Frage            | Dies ist die eigentliche Frage, die in der Umfrage gestellt wird. Die zugeordneten Umfrage-Optionen ist die Auswahl der möglichen Antworten für diese Umfrage.                                                                                                                                                                                             |
| Bezeichnung für Schaltfläche "Absenden" | Der Text, der für die Übermittlungsschaltfläche verwendet werden soll.                                                                                                                                                                                                                                                                                       |
| Veröffentlichungsdatum        | Steuert das Datum und die Uhrzeit, ab der die Umfrage auf dem Portal sichtbar ist. Wenn die Umfrage-Platzierung in mehreren Umfragen rotiert, wird eine unveröffentlichte Umfrage nicht angezeigt. Wenn keine freigegebenen Umfragen einer Umfrage-Platzierung zugeordnet sind, wird nichts angezeigt. Dies ist nützlich zur Steuerung der Veröffentlichungzeit von Inhalten.         |
| Ablaufdatum     | Steuert das Datum/die Uhrzeit, vor der die Umfrage auf dem Portal sichtbar ist.                                                                                                                                                                                                                                                                  |
| Abstimmungsenddatum   | Bis zu diesem Datum können Benutzer, die noch nicht in einer Umfrage abgestimmt haben, in der Umfrage abstimmen.|

> [!Note] 
> - Wenn ein Benutzer in einer Umfrage abgestimmt hat, sieht er eine Zusammenfassung der aktuellen Umfrage-Ergebnisse. Diese Ergebnisse werden außerdem für eine Umfrage angezeigt, die hinter dem Abschlussdatum liegt, für die der Benutzer jedoch noch nicht abgestimmt hat. Dies ermöglicht Ihnen, die Ergebnisse der Umfragen weiter anzuzeigen, auch wenn keine Abstimmung mehr möglich sein soll. 
> - Der Unterschied zwischen dem Abstimmungsabschluss- und dem Ablaufdatum ist, dass die Umfrage nach dem Ablaufdatum nicht mehr in der Umfrageplatzierung angezeigt (rotiert) wird. Das Abstimmungsabschlussdatum bestimmt nur das Datum, nach dem Benutzer nicht mehr in der Umfrage abstimmen können.

Jetzt ist die Umfrage erstellt worden; Sie müssen mindestens eine Umfrageoption dieser Umfrage zuordnen. In der **Optionen**-Registerkarte der Umfrage klicken Sie auf die Option **Neue Umfrageoption**

> [!div class=mx-imgBorder]
> ![Umfrageoptionen hinzufügen](../media/add-poll-options.png "Umfrageoptionen hinzufügen")  

## <a name="poll-options"></a>Umfrageoptionen

Eine Umfrage ist eine Frage, die dem Benutzer angezeigt wird. Eine Umfrage besitzt zwei oder mehr mögliche Antworten, wie vom Inhaltsersteller bestimmt. Diese Antworten werden durch Umfrage-Optionen dargestellt, die der jeweiligen Umfrage zugeordnet werden müssen. Eine neue Umfrage-Option wird beim Hinzufügen von Umfrageoptionen für eine Umfrage über das Fenster **Datensätze nachschlagen** erstellt, wie oben beschrieben.

## <a name="poll-option-attributes"></a>Umfrageoptionsattribute

| Name          | Beschreibung                                                                |
|---------------|----------------------------------------------------------------------------|
| Name          | Der beschreibende Name der Umfrageoption.                                  |
| Umfrage          | Die Umfrage, der die Option zugeordnet ist.                               |
| Antwort        | Der Text, der als verfügbare Umfrageabstimmungsoption angezeigt werden soll.                    |
| Stimmen         | Die Anzahl der Abstimmungen, die die Umfrageoption erhalten hat (schreibgeschützt).              |
| Anzeigereihenfolge | Ein numerischer Wert, der die Anzeigereihenfolge der Umfrageoptionen bestimmt. |

## <a name="poll-submissions"></a>Umfrageübermittlungen

Wenn ein Benutzer die Website besucht, kann er an der Umfrage teilnehmen, die auf der Seite angezeigt wird.

> [!div class=mx-imgBorder]
> ![Umfrage übermitteln](../media/submit-poll.png "Umfrage übermitteln")  

Benutzer können nur einmal abstimmen, danach können sie die Ergebnisse für diese Umfrage, wenn diese angezeigt wird, sehen:

> [!div class=mx-imgBorder]
> ![Umfrageabstimmungen](../media/poll-votes.png "Umfrageabstimmungen")  

Die Details der Umfrageabstimmungsergebnisse werden in Common Data Service als Umfrageübermittlungsdatensätze gespeichert. Die Umfrageübermittlungsentität enthält folgende Informationen:

| Name        | Beschreibung                                                                                   |
|-------------|-----------------------------------------------------------------------------------------------|
| Name        | Zeigt den Namen des Abstimmers an, wenn der Benutzer angemeldet ist; andernfalls wird die anonyme ID erfasst. |
| Umfrage        | Die zugeordnete Umfrage.                                                                          |
| Umfrageoption | Die Umfrage-Option, die vom Benutzer ausgewählt wird.                                                       |
| Kontakt     | Der zugeordnete Kontaktdatensatz des Abstimmers, wenn der Benutzer angemeldet ist                           |
| Besucher-ID  | Die anonyme ID des Abstimmers, wenn der Benutzer anonym ist.                                       |

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Über Entitätslisten](entity-lists.md)  
[Erstellen und Ausführen von Werbung in einem Portal](create-run-advertisement.md)  
[Webseite oder Blogbeitrag im Portal bewerten bzw. darüber abstimmen](rate-webpage.md)  
[Umleiten zu einer neuen URL auf einem Portal](add-redirect-url.md)  

