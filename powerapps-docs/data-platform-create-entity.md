---
title: "Erstellen einer benutzerdefinierten Entität | Microsoft-Dokumentation"
description: "Erstellen Sie eine benutzerdefinierte Entität basierend auf einer anderen Entität oder von Grund auf neu."
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
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 5d927e84144da8e3b011bb4e4a7ac107aedac74f
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-custom-entity"></a>Eine benutzerdefinierte Entität erstellen
Sie können eine benutzerdefinierte Entität zum Speichern von Daten erstellen, die spezifisch für Ihre Organisation sind. Sie können die Daten dann anzeigen, indem Sie eine App entwickeln, die auf die Entität verweist.

Es gibt zwei Möglichkeiten zum Erstellen einer Entität:

* Sie erstellen die Entität von Grund auf neu. Standardmäßig enthält die Entität nur [vier Systemfelder und ein Datensatztitelfeld](data-platform-create-entity.md#system-and-record-title-fields).
* Sie erstellen eine Entität auf Grundlage einer anderen Entität, indem Sie die Felder und die Einstellungen der Entität, nicht jedoch die Daten kopieren.

In beiden Fällen speichert Microsoft PowerApps Daten automatisch und trägt zum Schutz dieser bei. Nachdem Sie eine Entität erstellt haben, können Sie [eines oder mehrere ihrer Felder erstellen oder bearbeiten](data-platform-manage-fields.md) und [Beziehungen zwischen Entitäten erstellen](data-platform-entity-lookup.md).

**Hinweis:** Bevor Sie eine Entität erstellen, schauen Sie unter der [Liste der Standardentitäten](data-platform-intro.md#standard-entities) nach. Diese Entitäten beschreiben typische Szenarios, wie z.B. Konten und Kontakte. Wenn eine dieser Entitäten Ihre Anforderungen sofort oder nach nur geringfügigen Änderungen erfüllt, können Sie Zeit sparen, indem Sie mit diesen Entität beginnen.

## <a name="create-an-entity"></a>Erstellen einer Entität
1. 1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entities** (Entitäten).
2. Wenn Sie noch keine Datenbank erstellt haben, müssen Sie eine erstellen. Weitere Informationen finden Sie unter [Erstellen einer Common Data Service-Datenbank](create-database.md).
3. Klicken oder tippen Sie in der Nähe der oberen rechten Ecke auf **New entity** (Neue Entität).
4. Geben Sie im Feld **Entity name** (Entitätsname) einen Namen für die Entität ein. Vergewissern Sie sich, dass der Entitätsname klar und aussagekräftig ist, da Sie diesen nicht mehr ändern können, nachdem Sie die Entität erstellt haben. Sie verweisen mit diesem Namen in einer Formel auf die Entität, wenn Sie eine App entwickeln.
5. Geben Sie einen Anzeigenamen und optional eine Beschreibung für die Entität ein, und klicken oder tippen Sie anschließend auf **Next**.
6. Optional: Ändern Sie den Wert des Felds **Title** in eine für Ihre Daten aussagekräftigere Benennung um.
7. Klicken oder tippen Sie auf **Erstellen**, um die Entität zu erstellen.

Ihre Entität wird in der Liste der Entitäten in Ihrer Datenbank angezeigt. Klicken oder tippen Sie am Anfang der Liste auf die Spaltenüberschrift **Type** (Typ), um Ihre Entität oben in der Liste anzuzeigen. Die Entitäten werden nach Typ sortiert und alle benutzerdefinierten Entitäten werden über allen Standardentitäten angezeigt werden.

## <a name="system-fields-and-the-record-title-field"></a>Systemfelder und das Datensatztitelfeld
Alle Entitäten enthalten fünf Systemfelder. Diese Felder sind schreibgeschützt. Daher können Sie sie nicht ändern oder löschen, und ihnen keine Werte zuweisen.

| Anzeigename | Systemfeldname | Datentyp | Beschreibung |
| --- | --- | --- | --- |
| Id |Systemfeldname |Big Integer |Der eindeutige Bezeichner für den Datensatz |
| Created By |CreatedByUser |Text |Der Benutzer, der einen Datensatz erstellt hat |
| Created Record Date |CreatedOnDateTime |DateTime |Das Datum und die Uhrzeit der Erstellung eines Datensatzes |
| Last modified By |LastModifiedByUser |Text |Der Benutzer, der den Datensatz zuletzt geändert hat |
| Modified Record Date |LastModifiedDateTime |DateTime |Das Datum und die Uhrzeit der letzten Änderung eines Datensatzes |

Wenn Sie eine Entität von Grund auf neu erstellen, enthält sie auch ein benutzerdefiniertes Feld mit dem Namen **Title** (Titel). Dieses Feld wird festgelegt, wie das Feld des Datensatzes **Title**. Der Wert des Feldes **Title** ist der benutzerfreundliche Bezeichner eines Datensatzes bei der Verwendung in einer App. Sie können ändern, welches Feld das **Title**-Feld ist, jede Entität muss jedoch über ein **Title**-Feld verfügen.

## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md)
* [Definieren von Beziehungen zwischen Entitäten](data-platform-entity-lookup.md)
* [Generate an app by using a Common Data Service database (Generieren einer App mithilfe einer Common Data Service-Datenbank)](data-platform-create-app.md)
* [Create an app from scratch using a Common Data Service database (Erstellen einer App von Grund auf neu mithilfe einer Common Data Service-Datenbank)](data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

