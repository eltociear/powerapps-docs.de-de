---
title: Schnellstart für Entitätsbeziehungen über das Nachschlagefeld | Microsoft-Dokumentation
description: Schnellstart für das Erstellen einer Beziehung zwischen Entitäten durch Verwenden eines Nachschlagefelds
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: a607058d1e26f37a4bffa054d9dc148be8b6b011
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-create-a-relationship"></a>Schnellstart: Erstellen einer Beziehung
Daten in einer Entität beziehen sich häufig auf Daten in einer anderen Entität. Angenommen, Sie haben eine Entität **Teachers** und eine Entität **Class**, und die Entität **Class** verfügt möglicherweise über eine Nachschlagebeziehung zu der Entität **Teachers**, um anzuzeigen, welcher Lehrer den Kurs gibt. Sie können ein Nachschlagefeld verwenden, um Daten aus der Entität **Teachers** anzuzeigen. Dies wird häufig als Nachschlagefeld bezeichnet.

## <a name="define-a-relationship"></a>Definieren einer Beziehung
Sie können mehrere Typen von Beziehungen zwischen zwei Entitäten (oder innerhalb einer Entität) erstellen. Jede Entität kann eine Beziehung mit mehr als einer Entität haben, und jede Entität kann mehr als eine Beziehung zu einer anderen Entität haben. Einige häufige Beziehungstypen sind folgende:


* **n:1**: Bei diesem Beziehungstyp kann jeder Datensatz in Entität B mit mehr als einem Datensatz in Entität A übereinstimmen, jedoch kann jeder Datensatz in Entität A mit nur einem Datensatz in Entität B übereinstimmen. Beispielsweise hat jeder Kurs nur einen einzigen Kursraum. Dabei handelt es sich um die häufigste Art der Beziehung. Diese wird in der Feldliste als **Nachschlagefeld** angezeigt.
* **1:n**: Bei diesem Beziehungstyp kann jeder Datensatz in Entität A mit mehr als einem Datensatz in Entität B übereinstimmen, jedoch kann jeder Datensatz in Entität B mit nur einem Datensatz in Entität A übereinstimmen. Beispielsweise kann ein einzelner Lehrer mehrere Kurse geben.
* **m:n**: Bei diesem Beziehungstyp kann jeder Datensatz in Entität A mit mehr als einem Datensatz in Entität B übereinstimmen und umgekehrt. Schüler können zum Beispiel an mehreren Kursen teilnehmen, und in jedem Kurs sind mehrere Schüler.

## <a name="add-a-lookup-field-many-to-one-relationship"></a>Hinzufügen eines Nachschlagefelds (n:1-Beziehung)

Um eine Nachschlagebeziehung zu einer Entität hinzuzufügen, erstellen Sie unter der Registerkarte **Beziehungen** eine Beziehung, und geben Sie die Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität, oder [erstellen Sie eine neue Entität](data-platform-create-entity.md).

3. Klicken Sie auf **Beziehungen**.

4. Klicken Sie auf **Beziehung hinzufügen**. Dadurch wird ein neuer Bereich geöffnet, in dem Sie die Entität auswählen können, zu der Sie eine Beziehung erstellen möchten. Wählen Sie die Entität aus dem Dropdownmenü **Verknüpfte Entität** aus.

    ![n:1-Beziehung](./media/data-platform-cds-newrelationship/manytoone-1.png "Many to One Relationship")

5. Nach dem Auswählen einer Entität werden die Nachschlagefelder in der primären Entität angezeigt. Diese stimmen standardmäßig mit den Entitätsnamen (in diesem Beispiel „Classroom“) überein, Sie können diese jedoch nach Bedarf ändern.

    ![n:1-Beziehung](./media/data-platform-cds-newrelationship/manytoone-2.png "Many to One Relationship")

6. Klicken Sie auf **Fertig**, um die Beziehung zu Ihrer Entität hinzuzufügen, und klicken Sie dann auf **Entität speichern**.

    ![n:1-Beziehung](./media/data-platform-cds-newrelationship/manytoone-3.png "Many to One Relationship")

## <a name="add-a-one-to-many-relationship"></a>Hinzufügen einer 1:n-Beziehung

Erstellen Sie zum Hinzufügen einer 1:n-Beziehung in der Registerkarte **Beziehungen** eine Beziehung, und geben Sie die Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität, oder [erstellen Sie eine neue Entität](data-platform-create-entity.md).

3. Klicken Sie auf **Beziehungen**.

4. Klicken Sie rechts von **Beziehung hinzufügen** auf den Pfeil nach unten. Dadurch können Sie zwischen den beiden Beziehungen auswählen. Klicken Sie auf **1:n**. Dadurch wird ein neuer Bereich geöffnet, in dem Sie die Entität auswählen können, zu der Sie eine Beziehung erstellen möchten. Wählen Sie die Entität aus dem Dropdownmenü **Verknüpfte Entität** aus.

    ![1:n-Beziehung](./media/data-platform-cds-newrelationship/onetomany-1.png "One to Many Relationship")

5. Nach dem Auswählen einer Entität werden die Nachschlagefelder in der primären Entität angezeigt. Diese stimmen standardmäßig mit den Entitätsnamen (in diesem Beispiel „Class“) überein, Sie können diese jedoch nach Bedarf ändern.

    > [!NOTE]
    > Im Fall einer 1:n-Beziehung wird ein Nachschlagefeld in der verknüpften Entität erstellt, nicht in der Entität, die Sie aktuell ausgewählt haben. Wenn Sie ein Nachschlagefeld in der aktuellen Entität möchten, erstellen Sie eine n:1-Beziehung.

    ![1:n-Beziehung](./media/data-platform-cds-newrelationship/onetomany-2.png "One to Many Relationship")

6. Klicken Sie auf **Fertig**, um die Beziehung zu Ihrer Entität hinzuzufügen, und klicken Sie dann auf **Entität speichern**.

    ![1:n-Beziehung](./media/data-platform-cds-newrelationship/onetomany-3.png "One to Many Relationship")

## <a name="add-a-many-to-many-relationship"></a>Hinzufügen einer m:n-Beziehung

Derzeit ist diese Funktion nur über das Menü „Erweitert“ verfügbar. Klicken Sie im linken Menü der PowerApps-Startseite auf „Erweitert“. Weitere Informationen zum Erstellen der Beziehung finden Sie unter [Create N:N relationships (Erstellen von m:n-Beziehungen)](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships).

## <a name="use-a-lookup-field-in-an-app"></a>Verwenden eines Nachschlagefelds in einer App
Wenn Sie [eine App automatisch aus einer Entität erstellen](../canvas-apps/data-platform-create-app.md), die ein Nachschlagefeld enthält, wird dieses als **Dropdown**-Steuerelement angezeigt, das Daten aus dem Feld **Primärschlüssel** der Entität enthält.

## <a name="next-steps"></a>Nächste Schritte
* [Generieren einer App mithilfe einer Common Data Service-Datenbank](../canvas-apps/data-platform-create-app.md)
* [Neuerstellen einer App mithilfe einer Common Data Service-Datenbank](../canvas-apps/data-platform-create-app-scratch.md)

