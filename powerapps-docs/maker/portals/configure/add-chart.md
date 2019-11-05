---
title: Hinzufügen eines Diagramms zu einer Webseite in einem Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen eines in einer Modell gesteuerten App erstellten Diagramms zu einer Webseite im Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cc2e390b988689e9a21317d80aa7d94d2ea9e6d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553875"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>Hinzufügen eines in einer Modell gesteuerten App erstellten Diagramms zu einer Webseite im Portal

Sie fügen ein Diagramm zu einer Webseite hinzu, indem Sie ein Liquid-Tag mit dem Namen [Diagramm](../liquid/portals-entity-tags.md#chart)verwenden. Sie können das Tag "Diagramm Liquid" im Feld " **Kopieren** " auf einer Webseite oder im **Quellfeld** einer [Webvorlage](../liquid/store-content-web-templates.md)hinzufügen.
 
Beispiel: {% Chart ID: EE3C733D-5693-DE11-97d4-00155da3b01e%}

![Diagramm Beispiel](../media/dynamics365-chart-example.png "Diagramm Beispiel")

Sie können auch die ID einer Ansicht (gespeicherte Abfrage) angeben, um die Abfrage zu filtern. Beispiel:

<!—Leads by Source – Open Leads -->

{% Chart ID: "EE3C733D-5693-DE11-97d4-00155da3b01e" viewId: "00000000-0000-0000-00AA-000010001006"%}

## <a name="get-the-id-of-a-chart"></a>ID eines Diagramms erhalten

1.  Wechseln Sie zur Ziel Entität, z. b. **Sales** > **Leads**.
2.  Erweitern Sie den Bereich **Diagramme** .
3.  Wählen Sie das gewünschte Diagramm aus.
4.  Wählen Sie **Weitere Befehle**aus, und wählen Sie dann **Diagramm exportieren**aus.

    ![Exportieren eines Diagramms](../media/export-dynamics365-chart.png "Exportieren eines Diagramms")

5. Öffnen Sie die XML-Datei des exportierten Diagramms in einem Text-Editor.
6. Kopieren Sie den Wert der \<visualizationid\>-Tags.

    ![Chartid für ein Diagramm](../media/dynamics365-chart-chartid.png "Diagramm-ID für ein Diagramm")

7. Fügen Sie den Wert von visualizationid in die Kennung des Liquid-Diagramm Tags für den Diagramm-ID-Parameter ein. Beispiel:

    {% Chart ID: EE3C733D-5693-DE11-97d4-00155da3b01e%}.

## <a name="get-the-id-of-a-view"></a>Anzeigen der ID einer Ansicht

Sie müssen den Ansicht-Editor öffnen, um die Ansichts-ID zu erhalten, die mit dem Liquid-diagrammtag verwendet wird.
 
1.  Wechseln Sie zur Ziel Entität, z. b. **Sales** > **Leads**.
2.  Wählen Sie die gewünschte Ansicht aus der Dropdown Kopfzeile Ansicht aus.
3.  Wählen Sie in der Symbolleiste **Ansicht** aus. Das Ansichts Fenster wird geöffnet.

    ![Anzeigen der Leads im Ansichts-Editor](../media/dynamics365-chart-view.png "Anzeigen der Leads im Ansichts-Editor")

4. Kopieren Sie den **ID** -Wert aus der URL des Ansichts Fensters.

    ![Anzeigen der ID aus dem Ansichts-Editor](../media/dynamics365-chart-viewid.png "Anzeigen der Ansichts-ID aus dem Ansichts-Editor")

5. Fügen Sie diese ID in die Kennung des Liquid-Diagramm Tags für den viewId-Parameter ein, z. b.:

    <!—Leads by Source – Open Leads -->

    {% Chart ID: "EE3C733D-5693-DE11-97d4-00155da3b01e" viewId: "00000000-0000-0000-00AA-000010001006"%}

## <a name="entity-permission-requirement"></a>Anforderung für Entitäts Berechtigungen

Die Leseberechtigung wird für die Ziel Entität bestätigt, die im Diagramm abgefragt wird. Damit anonyme oder authentifizierte Benutzer das Diagramm anzeigen können, müssen Sie sicherstellen, dass die entsprechenden [Entitäts Berechtigungs](assign-entity-permissions.md) Einträge erstellt und den entsprechenden [Webrollen](create-web-roles.md)zugewiesen werden. 
 
Wenn die Berechtigung nicht erteilt wird, wird dem Benutzer die Meldung "Zugriff verweigert" angezeigt.

## <a name="unsupported-charts-and-chart-types"></a>Nicht unterstützte Diagramme und Diagrammtypen

Die folgenden Diagrammtypen werden zurzeit nicht in Portalen unterstützt:
- Ring
- Tag

In der folgenden Tabelle werden die Diagramme aufgelistet, die derzeit nicht in Portalen unterstützt werden.

| Diagramm Name                              | Diagramm-ID                             | Entitätstyp      |
|-----------------------------------------|--------------------------------------|------------------|
| Konten nach Besitzer-tagdiagramm           | be178262-6142-4b41-85b7-4ccedc62cfd9 | Ziehen          |
| Aktivitäten nach Besitzer-tagdiagramm         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| Aktivitäten nach Priorität-Ring Diagramm | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| Kontakte nach Konto                     | 2ff3ebea-6310-4dde-B3a1-e1144ea42b7b | Sie          |
| Kontakte nach Land                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | Sie          |
| Kontakte nach bevorzugter Kontaktmethode    | 751b7456-308e-4568-a3a9-47135aae833a | Sie          |
| Ziel Fortschritt (Anzahl)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | goal             |
| Ziel Fortschritt (Money)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | goal             |
| Heutige Ziele im Vergleich zu den aktuellen Zielen (Anzahl)      | 1b697c8e-9a6l-DF11-986c-00155d2e3002 | goal             |
| Das heutige Ziel und die aktuellen Ziele (Money)      | 1e697c8e-9a6l-DF11-986c-00155d2e3002 | goal             |
| Fälle nach Konto                        | 38872e4f-ac99-E511-80da-00155dc1b253 | incident         |
| Fälle nach Priorität                       | 0F 0b995-9d6l-453c-b26d-8l443e42e676 | incident         |
| Fälle nach Produkt                        | 17c3f 166-5b22-4476-819b-b05da2e8d24f | incident         |
| Artikel zum Ablauf dieses Monats nach Besitzer   | 47d696ad-7c3b-E511-80d1-00155db10d2b | knowledgearticle |
| Nach Besitzer                                | 330068sd-833b-E511-80d1-00155db10d2b | knowledgearticle |
| Nach Betreff                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | knowledgearticle | 
| | |
