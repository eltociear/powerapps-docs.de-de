---
title: Erstellen oder Bearbeiten von Filtern in modellgesteuerten App-Ansichten | MicrosoftDocs
description: Lernen Sie, wie Sie Filter oder Ansichten für Ihre Anwendung erstellen und bearbeiten können
keywords: Ausdrucks-Builder
ms.date: 2/04/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
author: iangpgh
ms.author: v-iapr
manager: matp
ms.reviewer: srihas
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 25
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a36cf57710da4e6306c7de48e19d4af6c722f10
ms.sourcegitcommit: abdc8c609a7a221ce4ca6b051a84b7083bdbe1ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "3225582"
---
# <a name="create-or-edit-filters-in-model-driven-app-views"></a>Erstellen oder Bearbeiten von Filtern in modellgesteuerten Anwendungsansichten

<a name="BKMK_CreateOrEditViewFilters"></a>   

Die Filter in einer Power Apps-Ansicht sind wichtig für den von der Ansicht gelieferten Wert. Die Filter, die Sie anwenden, bestimmen, welche Datensätze standardmäßig in der Liste erscheinen. Sie können einen Filter für die Spalten, die Sie in eine Ansicht aufnehmen, hinzufügen oder bearbeiten, indem Sie die Spalte auswählen und **Filter nach** wählen. Sie können auch den Ausdruck-Builder im Ansichts-Designer verwenden. Verwenden Sie den Ausdrucks-Builder, um Filter für beliebige Felder der Entität in der aktuellen Ansicht oder für beliebige Felder in einer verknüpften Entität hinzuzufügen oder zu bearbeiten. 

In diesem Thema erstellen oder bearbeiten Sie Filter, indem Sie die folgenden Aufgaben ausführen:

-   [Bearbeiten oder Entfernen einer Filterbedingung](create-edit-view-filters.md#edit-or-remove-a-filter-condition)

-   [Öffnen Sie den Ausdrucks-Builder](create-edit-view-filters.md#open-the-expression-builder)

-   [Bedingungen zu einem Filter hinzufügen](create-edit-view-filters.md#add-conditions-to-a-filter)

-   [Eine Gruppenbedingung zu einem Filter hinzufügen](create-edit-view-filters.md#add-a-group-condition-to-a-filter)

-   [Eine verwandte Entität zu einer Bedingung hinzufügen](create-edit-view-filters.md#add-a-related-entity-to-a-condition)

-   [Gruppenbedingungen eines Filters](create-edit-view-filters.md#group-conditions-of-a-filter)

## <a name="edit-or-remove-a-filter-condition"></a>Bearbeiten oder Entfernen einer Filterbedingung

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2. Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Anzeigen**.

3. Wählen Sie eine Ansicht aus, um sie zu öffnen. Im Ansichtseigenschaften-Panel werden vorhandene Filter aufgelistet.

    > [!div class="mx-imgBorder"] 
    > ![Ansicht-Panel-Filter](media/views-panel-filters.png "Ansichts-Panel-Filter")

4. Wählen Sie im Ansichtseigenschaften-Panel eine Filterbedingung aus.

    > [!div class="mx-imgBorder"] 
    > ![Filter bearbeiten](media/edit-filter-viewpanel.png "Filter bearbeiten")

5. Wählen Sie den Bedingungsoperator, den Sie verwenden möchten.

6. Geben Sie den Vergleichswert für die Bedingung ein oder wählen Sie ihn aus.

7. Wählen Sie **Übernehmen** aus.

8. Um eine Bedingung zu entfernen, wählen Sie **Schließen**. Die Bedingung wird ohne Bestätigung entfernt.

### <a name="open-the-expression-builder"></a>Öffnen Sie den Ausdrucks-Builder

- Wählen Sie im Eigenschaften-Panel der Ansicht **Filter bearbeiten**.

    > [!div class="mx-imgBorder"] 
    > ![Ausdruck-Builder](media/edit-create-filters.png "Ausdrucks-Builder")

### <a name="add-conditions-to-a-filter"></a>Bedingungen zu einem Filter hinzufügen

1. Wählen Sie im Ausdrucks-Builder **Hinzufügen** > **Zeile hinzufügen**.

2. Wählen Sie ein Feld für die Bedingung aus.

3. Wählen Sie einen Bedingungsoperator.

4. Wählen Sie einen Vergleichswert.  

    Für einige Filterbedingungen ist kein Vergleichswert für die Bedingung erforderlich. Beispielsweise erfordert der Operator **Enthält Daten** keinen Vergleichswert. Bei anderen Filterbedingungen wählen Sie den Vergleichswert aus einem Optionssatz. Das Feld **Status** hat z.B. einen Optionssatz, der die Werte **Aktiv** und **Inaktiv** enthält.

    > [!div class="mx-imgBorder"] 
    > ![Filterbedingung](media/add-condition-filter.png "Filter-Bedingung")

5. Wählen Sie **OK** aus.

### <a name="add-a-group-condition-to-a-filter"></a>Hinzufügen einer Gruppenbedingung zu einem Filter

1. Wählen Sie im Ausdrucksbildner **Hinzufügen** > **Gruppe hinzufügen**.

2. Wählen Sie den Vergleichsoperator **Oder** für die Gruppe. **Und** ist der Standard-Vergleichsoperator.

3. Geben Sie den ersten Abschnitt der gruppierten Bedingung an. Wählen Sie das Feld, den Bedingungsoperator und den Vergleichswert.

4. Wählen Sie **Hinzufügen** > **Gruppe hinzufügen**

5. Geben Sie den zweiten Abschnitt der gruppierten Bedingung an.

    > [!div class="mx-imgBorder"] 
    > ![Gruppenbedingungsfilter](media/add-group-filter.png "Gruppenbedingungsfilter")

    Sie können **Zusammenklappen** wählen, um die Gruppe als bedingten Ausdruck anzuzeigen.

### <a name="add-a-related-entity-to-a-condition"></a>Eine verwandte Entität zu einer Bedingung hinzufügen

1. Wählen Sie im Ausdrucks-Builder **Hinzufügen** > **Verwandte Einheit hinzufügen**.

2. Wählen Sie ein Feld aus der aktuellen Entität, das mit einer anderen Entität verknüpft ist. Die mit dem Feld verknüpfte Entität wird in Klammern angezeigt. Sie können Felder auswählen, die eine Eins-zu-eins-, Eins-zu-viele- oder Eins-zu-viele-Beziehung mit der verknüpften Entität haben.

3. Wählen Sie ein Feld der verknüpften Entität für die Bedingung aus.

4. Wählen Sie einen Bedingungsoperator.

5. Wählen Sie einen Vergleichswert aus oder geben Sie ihn ein.

    > [!div class="mx-imgBorder"] 
    > ![Verwandte Entitätsfilter](media/add-relatedentity-filter.png "Filter für verwandte Entitäten")

### <a name="group-conditions-of-a-filter"></a>Gruppenbedingungen eines Filters

1. Aktivieren Sie im Ausdruck-Builder das Kontrollkästchen für die Bedingungen, die Sie gruppieren möchten.

2. Wählen Sie **Weitere Befehle** (...) für eine der Bedingungen, und wählen Sie dann **Gruppe erstellen**.

3. Um die Gruppierung einer Gruppe aufzuheben, wählen Sie **Weitere Befehle** (...) für die Gruppe und wählen Sie dann **Gruppe auflösen**

    > [!div class="mx-imgBorder"] 
    > ![Gruppierter Bedingungsfilter](media/group-conditions-filter.png "Gruppierter Bedingungsfilter")

### <a name="see-also"></a>Siehe auch
[Bearbeiten oder Erstellen von persönlichen Ansichten mithilfe erweiterter Rasterfilter](../../user/grid-filters-advanced.md)
[Auswählen und Konfigurieren von Spalten](choose-and-configure-columns.md)  
[Filterkriterien bearbeiten](edit-filter-criteria.md)  
[1:N (1: n) oder N:1-Beziehungen erstellen](../common-data-service/create-edit-1n-relationships.md)
