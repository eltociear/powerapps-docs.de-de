---
title: Hinzufügen eines Diagramms zu einem Portal | MicrosoftDocs
description: Anweisungen, ein Diagramm, das in einer modellgesteuerten App erstellt wurde, zu einer Webseite im Portal hinzuzufügen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/29/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3d9a2ec3ef4e2589c51717629213dfe73d3418eb
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012573"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>Ein Diagramm, das in einer modellgesteuerten App erstellt wurde, zu einer Webseite im Portal hinzufügen

Sie fügen ein Diagramm zu einer Webseite hinzu, indem Sie ein Liquid-Tag namens [Diagramm](../liquid/portals-entity-tags.md#chart) verwenden. Sie könne das Diagramm-Liquid-Tag im Feld **Kopie** auf einer Webseite oder im Feld **Quelle** auf einer [Webvorlage](../liquid/store-content-web-templates.md) hinzufügen.
 
Zum Beispiel {% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}

![Beispieldiagramm](../media/dynamics365-chart-example.png "Beispieldiagramm")

Sie können auch die ID einer Ansicht angeben (gespeicherte Anfrage), um die Abfrage zu filtern. Beispiel:

<!—Leads by Source – Open Leads -->

{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}

## <a name="get-the-id-of-a-chart"></a>Abrufen der ID eines Diagramms

1.  Gehen Sie zur Zielentität, beispielsweise **Vertrieb** > **Leads**
2.  Vergrößern Sie den Bereich **Diagramme**.
3.  Wählen Sie das Diagramm aus, die angezeigt werden sollen.
4.  Wählen Sie **Weitere Befehle** und dann **Diagramm exportieren** aus.

    ![Exportieren eines Diagramms](../media/export-dynamics365-chart.png "Exportieren eines Diagramms")

5. Öffnen Sie die XML-Datei des exportierten Diagramms in einem Text-Editor.
6. Kopieren Sie den Wert des \<visualizationid\>-Tags.

    ![Abrufen der Diagramm-ID für ein Diagramm](../media/dynamics365-chart-chartid.png "Abrufen der Diagramm-ID für ein Diagramm")

7. Fügen Sie den Visualisierungswert in die Liquid-Tag-Diagrammdeklaration für den Diagramm-ID-Parameter ein, beispielsweise ein:

    {% chart id:EE3C733D-5693-DE11-97D4-00155DA3B01E %}.

## <a name="get-the-id-of-a-view"></a>Abrufen der ID einer Ansicht

Sie müssen den Ansichtseditor öffnen, um die Ansichts-ID abzurufen, die mit dem Liquid-Tag zu verwenden ist.
 
1. Gehen Sie zu make.powerapps.com und wählen Sie die entsprechende Umgebung aus.
1. Wählen Sie in der linken Navigationsleiste die Option Daten > Entitäten.
1. Wählen Sie die entsprechende Entität aus und wechseln Sie zur Registerkarte Ansichten.
1. Sie können die Liste der Ansichten sehen. Gehen Sie zu den Optionen (...) und wählen Sie Ansicht bearbeiten.
1. Kopieren Sie den ID-Wertaus der Adressleiste des Ansichtsfensters.

    ![Anzeigen ID des Formulars](../media/dynamics365-chart-viewid.png)

1. Fügen Sie diese ID in die Liquid-Tag-Diagrammdeklaration für den Ansichts-ID-Parameter ein, beispielsweise:

    ```
    <!—Leads by Source – Open Leads -->
    {% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001004" %}
    ```

## <a name="entity-permission-requirement"></a>Entitätsberechtigung-Anforderung

Leseberechtigung wird für die Zielentität bestätigt, die im Diagramm abgefragt wird. Damit anonyme oder authentifizierte Benutzer dazu in der Lage sind, das Diagramm anzuzeigen, müssen Sie sicherstellen, dass die entsprechenden [Entitätsberechtigung](assign-entity-permissions.md)-Datensätze erstellt und den entsprechenden [Webrollen](create-web-roles.md) zugewiesen werden. 
 
Wenn keine Berechtigung erteilt ist, wird dem Benutzer die Meldung "Zugriff verweigert" angezeigt.

## <a name="unsupported-charts-and-chart-types"></a>Nicht unterstützte Diagrammtypen und Diagramme

Die folgenden Diagrammtypen werden derzeit nicht in Portalen unterstützt:
- Ring
- Tag

Die folgende Tabelle listet die Diagrammtypen auf, die derzeit nicht in Portalen unterstützt werden.

| Diagrammname                              | Diagramm-ID                             | Entitätstyp      |
|-----------------------------------------|--------------------------------------|------------------|
| Firmen nach Besitzer – Tag-Diagramm           | be178262-6142-4b41-85b7-4ccedc62cfd9 | account          |
| Aktivitäten nach Besitzer – Tag-Diagramm         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| Aktivitäten nach Priorität – Ringdiagramm | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| Kontakte nach Firma                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | contact          |
| Kontakte nach Land                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | contact          |
| Kontakte nach bevorzugter Kontaktmethode    | 751b7456-308e-4568-a3a9-47135aae833a | contact          |
| Zielstatus (Anzahl)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | goal             |
| Zielstatus (Geld)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | goal             |
| Ziel nach heutigem Stand im Vergleich zu Istwerten (Anzahl)      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| Ziel nach heutigem Stand im Vergleich zu Istwerten (Zahlung)      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| Anfragen nach Firma                        | 38872e4f-ac99-e511-80da-00155dc1b253 | incident         |
| Anfragen nach Priorität                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | incident         |
| Anfragen nach Produkt                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | incident         |
| Artikel, die in diesem Monat ablaufen, nach Besitzer   | 47d696ad-7c3b-e511-80d1-00155db10d2b | knowledgearticle |
| Nach Besitzer                                | 330068fd-833b-e511-80d1-00155db10d2b | knowledgearticle |
| Nach Betreff                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | knowledgearticle | 
| | |
