---
title: "Entitätsbeziehungen über das Nachschlagefeld | Microsoft-Dokumentation"
description: "Erstellen Sie eine Beziehung zwischen Entitäten durch Verwenden eines Nachschlagefelds."
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: kfend
ms.openlocfilehash: 1aff4df6e314f50a67aff6a08298d3d7aa4a9cfa
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="build-a-relationship-between-entities"></a>Eine Beziehung zwischen Entitäten erstellen
Daten in einer Entität beziehen sich häufig auf Daten in einer anderen Entität. Angenommen, Sie haben eine Entität **Customers** und eine Entität **Orders**, und die Entität **Orders** verfügt möglicherweise über eine Nachschlagebeziehung zu der Entität **Customers**, um anzuzeigen, welcher Kunde den Auftrag erteilt hat. Sie können ein Nachschlagefeld verwenden, Daten aus der **Customers**-Entität für den Kunden anzuzeigen, der den Auftrag erteilt hat. Weitere Informationen finden Sie unter [Entity relationships and lookup fields (Entitätsbeziehungen und Nachschlagefelder)](https://docs.microsoft.com/en-us/common-data-service/entity-reference/relationships).

## <a name="define-a-relationship"></a>Definieren einer Beziehung
Sie können mehrere Typen von Beziehungen zwischen zwei Entitäten (oder innerhalb einer Entität) erstellen. Jede Entität kann eine Beziehung mit mehr als einer Entität haben, und jede Entität kann mehr als eine Beziehung zu einer anderen Entität haben. Einige häufige Beziehungstypen sind folgende:

* **Normal**: Dieser Beziehungstyp besteht zwischen zwei Entitäten.
* **Selbst**: Dieser Beziehungstyp besteht innerhalb einer Entität.
* **1:1**: Bei diesem Beziehungstyp kann jeder Datensatz in Entität A mit nur einem Datensatz in Entität B übereinstimmen und umgekehrt. Das aktuelle Release von Common Data Service unterstützt diesen Beziehungstyp für benutzerdefinierte Entitäten nicht.
* **1:n**: Bei diesem Beziehungstyp kann jeder Datensatz in Entität A mit mehr als einem Datensatz in Entität B übereinstimmen, jedoch kann jeder Datensatz in Entität B mit nur einem Datensatz in Entität A übereinstimmen.
* **m:n**: Bei diesem Beziehungstyp kann jeder Datensatz in Entität A mit mehr als einem Datensatz in Entität B übereinstimmen und umgekehrt. Das aktuelle Release von Common Data Service unterstützt diesen Beziehungstyp nicht.

## <a name="add-a-lookup-relation"></a>Hinzufügen einer Nachschlagebeziehung
Um eine Nachschlagebeziehung zu einer Entität hinzuzufügen, erstellen Sie unter der Registerkarte **Beziehungen** eine Beziehung, und geben Sie die Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entities** (Entitäten).
2. Klicken oder tippen Sie in der Liste der Entitäten auf eine Entität, um deren Felder anzuzeigen. Sie können in der Liste filtern, indem Sie mindestens ein Zeichen in der Suchleiste über der Liste eingeben.
3. Klicken oder tippen Sie im oberen Bereich des Bildschirms auf **Beziehungen**. Auf dieser Registerkarte werden alle Beziehungen der Entität angezeigt. Klicken Sie auf **Neue Beziehung**.
4. Geben Sie auf der Seite **Beziehung erstellen** die entsprechende Entität an, mit der Sie eine Beziehung erstellen möchten, und geben Sie anschließend den Namen und Anzeigenamen der Beziehung an.
5. Klicken oder tippen Sie auf **Speichern**, um die Änderungen zu übernehmen. Ein Nachschlagefeld mit dem gleichen Namen wird automatisch erstellt.

## <a name="use-a-lookup-field-in-an-app"></a>Verwenden eines Nachschlagefelds in einer App
Wenn Sie [eine App automatisch aus einer Entität erstellen](data-platform-create-app.md), die ein Nachschlagefeld enthält, wird dieses als **Dropdown**-Steuerelement angezeigt, das Daten aus dem Feld **Primärschlüssel** der entsprechenden Entität in einem reduzierten Zustand enthält. Um in der Drop-down-Liste zwei Felder anzuzeigen, wenn diese erweitert ist, müssen Sie das Feld „Primär-ID“ sowie ein zweites Feld Ihrer Wahl zur Feldgruppe **Default Lookup** (Standardsuche) der verknüpften Entität der Nachschlagebeziehung hinzufügen.

## <a name="delete-a-record-with-a-lookup-relation"></a>Löschen eines Datensatzes mit einer Nachschlagebeziehung
Angenommen, Entität A verfügt über eine Nachschlagebeziehung zu Entität B:

* Sie können alle Datensätze in Entität A ohne Einschränkung löschen.
* Falls ein Datensatz in Entität B mit mindestens einem Datensatz in Entität A übereinstimmt, müssen Sie zunächst alle übereinstimmenden Datensätze in Entität A löschen, bevor Sie den Datensatz in Entität B löschen können.

**Hinweis**: Falls Entität B eine Standardentität mit einer übergeordneten Beziehung zu Entität A ist und Sie einen Datensatz aus Entität A löschen, werden alle übereinstimmenden Datensätze in Entität B ebenfalls gelöscht.

Informationen dazu, wie Sie ein Feld löschen, finden Sie unter [Verwalten von Feldern](data-platform-manage-fields.md).

## <a name="next-steps"></a>Nächste Schritte
* [Generate an app by using a Common Data Service database (Generieren einer App mithilfe einer Common Data Service-Datenbank)](data-platform-create-app.md)
* [Neuerstellen einer App mithilfe einer Common Data Service-Datenbank](data-platform-create-app-scratch.md)

