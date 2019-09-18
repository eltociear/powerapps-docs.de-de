---
title: Funktion „Distinct“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Distinct-Funktion in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 98fd1b67d4835969ac01b1ce63155bc81ed36630
ms.sourcegitcommit: 5899d37e38ed7111d5a9d9f3561449782702a5e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71038025"
---
# <a name="distinct-function-in-powerapps"></a>Distinct-Funktion in PowerApps
Fasst [Datensätze](../working-with-tables.md#records) aus einer [Tabelle](../working-with-tables.md) zusammen, wobei Duplikate entfernt werden.

## <a name="description"></a>Beschreibung
Die unter **schiedliche** Funktion wertet eine Formel für jeden Datensatz einer Tabelle aus und gibt eine einspaltige Tabelle der Ergebnisse zurück, wobei doppelte Werte entfernt werden.  Der Name der Spalte ist **Result**.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>Syntax
**Distinct**( *Table*, *Formula* )

* *Tabelle* (erforderlich):  Die Tabelle, die übergreifend ausgewertet werden soll.
* *Formel* (erforderlich):  Die für jeden Datensatz auszuwertende Formel.

## <a name="example"></a>Beispiel

1. Fügen Sie ein [**Button**](../controls/control-button.md) -Steuerelement ein, und legen **Sie dessen onselect** -Eigenschaft auf diese Formel fest.

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ```

1. Wählen Sie die Schaltfläche, während Sie die Alt-Taste gedrückt halten.

    Die Formel ist evaluatd, und die Auflistung **citypopulation** wird erstellt, die Sie anzeigen können, indem Sie in der Bearbeitungs Leiste **citypopulation** auswählen:

    > [!div class="mx-imgBorder"]
    > ![In der Ergebnis Ansicht angezeigte citypopulation-Auflistung](media/function-distinct/citypopulations-create.png)

1. Fügen Sie ein [**Datentabellen**](../controls/control-data-table.md) -Steuerelement ein, und legen Sie dessen **Items** -Eigenschaft auf diese Formel fest:

    ```powerapps-dot
    Distinct( CityPopulations, Country )
    ```

    Sie können das Ergebnis dieser Formel in der Bearbeitungs Leiste anzeigen, indem Sie die gesamte Formel auswählen:

    > [!div class="mx-imgBorder"]
    > ![Ausgabe der unterschiedlichen Funktion in der Ergebnis Ansicht](media/function-distinct/citypopulations-distinct.png)

1. Verwenden Sie den Link " **Felder bearbeiten** " im Eigenschaften Bereich der Datentabelle, um die Spalte " **Result** " hinzuzufügen:

    > [!div class="mx-imgBorder"]
    > ![Ausgabe der in der Datentabelle gezeigten eindeutigen Funktion](media/function-distinct/citypopulations-datatable.png)

1. Fügen Sie ein [**Label**](../controls/control-text-box.md) -Steuerelement ein, und legen Sie dessen Eigenschaft **Text** auf die Formel fest:

    ```powerapps-dot
    First( Sort( Distinct( CityPopulations, Country ), Result ) ).Result
    ```

    Diese Formel sortiert die Ergebnisse aus unter **schieden** mit der [**Sort**](function-sort.md) -Funktion, nimmt den ersten Datensatz aus der resultierenden Tabelle mit der [**ersten**](function-first-last.md) Funktion und extrahiert das **Ergebnis** Feld, um nur den Namen des Landes abzurufen.

    > [!div class="mx-imgBorder"]
    > ![Ausgabe von einer unterschiedlichen Funktion mit dem ersten Land nach Name](media/function-distinct/citypopulations-first.png)

     
