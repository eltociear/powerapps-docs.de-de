---
title: "Grundlegendes zu Entitäten | Microsoft-Dokumentation"
description: "Einführung in Entitäten, Felder, Beziehungen und Datenbanken."
services: powerapps
documentationcenter: na
author: clwesene
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/20/2017
ms.author: kfend
ms.openlocfilehash: bbc501542e634fab925654734cf709fe87248883
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="understand-entities-in-the-common-data-service"></a>Grundlegendes zu Entitäten in Common Data Service

Mit Common Data Service können Sie Daten sicher innerhalb eines Satzes von Standardentitäten und benutzerdefinierte Entitäten speichern und verwalten. Eine Entität ist eine Gruppe von Feldern, die zum Speichern von Daten ähnlich wie eine Tabelle in einer Datenbank verwendet werden. Nachdem die Daten gespeichert sind, können Sie mit Microsoft PowerApps anspruchsvolle Anwendungen mithilfe Ihrer Daten erstellen:

* Importieren Sie Daten in standardmäßige oder benutzerdefinierte Entitäten.
* Erstellen Sie benutzerdefinierte Entitäten, um Ihr Szenario und Ihre Anwendung zu unterstützen.
* Fügen Sie benutzerdefinierte Felder zu Standardentitäten hinzu, für die zusätzliche Informationen benötigt werden.
* Integrieren Sie Standardentitäten und benutzerdefinierte Entitäten in eine App, die Sie entwickeln, so einfach wie Daten aus anderen Quellen.
* Nutzen Sie Produktivitäts-Add-Ins zum Zugriff auf Ihre Daten von Microsoft Excel und Outlook.
* Sichern Sie Ihre Daten innerhalb Ihrer Organisation mithilfe der rollenbasierten Sicherheit für Standardentitäten und benutzerdefinierte Entitäten.
* Schließen Sie Auswahllisten vordefinierter Daten ein, z.B. Land, Anrede oder Währung.
* Bieten Sie globale Unterstützung für Ihre Daten und Anwendungen, durch die Nutzung der Übersetzung der Entität und Feldnamen.

Jede Entität enthält eine Gruppe von Datensätzen, die Benutzer erstellen, lesen, aktualisieren und löschen können. Sie können Beziehungen zwischen Entitäten erstellen, damit Sie in einer Entität anhand eines Datensatz einer anderen Entität nach Informationen suchen können. Sie können beispielsweise eine benutzerdefinierte Entität erstellen, um nachzuverfolgen, an welchen Veranstaltungen ein Benutzer teilgenommen hat. Indem Sie den Kunden als Nachschlagefeld zu Ihrer benutzerdefinierten Entität hinzufügen, bilden Sie eine Beziehung zwischen den zwei Entitäten, was in Ihrer App und in der Berichterstellung genutzt werden kann.

Informationen zum Erwerb eines Plans für die Verwendung von Common Data Service finden Sie unter [Pricing Info (Preise)](pricing-billing-skus.md).

## <a name="why-use-entities"></a>Gründe für die Verwendung von Entitäten
Entitäten (Standard und benutzerdefiniert) in Common Data Service bieten eine sichere und cloudbasierte Speicheroption für Ihre Daten. Mit Entitäten können Sie eine auf Ihr Unternehmen fokussierte Definition Ihrer Daten für die Verwendung in Ihren Apps erstellen. Wenn Sie nicht sicher sind, ob Entitäten die beste Option sind, sollten Sie diese Vorteile bedenken:

* **Einfach zu verwalten**: Sowohl die Metadaten als auch die Daten werden in der Cloud gespeichert. Sie müssen sich nicht um die Details kümmern, wie diese gespeichert werden.
* **Einfache Freigabe**: Sie können Daten problemlos für Ihre Kollegen freigeben, da die Berechtigungen von PowerApps verwaltet werden.
* **Bequem zu sichern**: Daten werden sicher gespeichert, damit Benutzer sie nur dann sehen können, wenn Sie ihnen Zugriff gewähren. Durch die rollenbasierte Sicherheit können Sie den Zugriff auf Entitäten für verschiedene Benutzer innerhalb Ihrer Organisation steuern.
* **Umfassende Metadaten**: Datentypen und Beziehungen werden direkt in PowerApps genutzt. Wenn Sie z.B. den Feldtyp als URL definieren, werden die Daten innerhalb Ihrer App als Hyperlink angezeigt.
* **Produktivitätstools**: Entitäten sind in den Add-Ins für Microsoft Excel und Outlook verfügbar, um die Produktivität zu steigern und die Verfügbarkeit Ihrer Daten sicherzustellen.
* **Auswahllisten**: Sie können aus einer Vielzahl von Standardauswahllisten wählen, um schnell Dropdownlisten in Entitäten und Apps bereitzustellen.

## <a name="standard-and-custom-entities"></a>Standardentitäten und benutzerdefinierte Entitäten
Wenn Sie eine App entwickeln, können Sie Standardentitäten, benutzerdefinierte Entitäten oder beides verwenden. Wenn eine Standardentität einem bestimmten Zweck in Ihrer App dienen kann, sollten Sie sie verwenden, anstatt eine benutzerdefinierte Entität zu entwickeln, die die gleiche Aufgabe erfüllt. Wenn eine Standardentität mit einigen Änderungen passend wäre, können Sie Felder entsprechend Ihren Anforderungen hinzufügen.

* Common Data Service stellt standardmäßig Standardentitäten bereit. Diese sind in Übereinstimmung mit bewährten Methoden entwickelt und dienen zum Erfassen der am häufigsten verwendeten Konzepte für ein Unternehmen, z.B. Kontakte, Konten und Produkte. Eine vollständige Liste der Entitäten finden Sie unter [Standard entities (Standardentitäten)](data-platform-intro.md#standard-entities).
* Sie können die Funktionalität der Standardentitäten erweitern, indem Sie eine oder mehrere benutzerdefinierte Entitäten zum Speichern von Informationen erstellen, die für Ihr Unternehmen einzigartig sind. Weitere Informationen finden Sie unter [Create a custom entity in the Common Data Model (Erstellen einer benutzerdefinierten Entität im Common Data Model)](data-platform-create-entity.md).

> [!NOTE]
> Verwenden Sie, wenn möglich, Standardentitäten (mit benutzerdefinierten Feldern, die bei Bedarf hinzugefügt werden). Dadurch wird sichergestellt, dass Sie von neuen Features oder Apps profitieren können, die diese Entitäten in der Zukunft zu nutzen.


## <a name="fields"></a>Felder
Jedes Feld hat einen Namen, einen Anzeigenamen, einen Datentyp und einfache Überprüfungen. Zu den Datentypen zählen **text**, **date** oder **number**. Die Überprüfung stellt sicher, dass erforderliche Felder Daten enthalten und Datensätze eindeutig sind, wenn die Entität dies fordert. Jedes Feld gehört zu einer von drei Kategorien: Systemfelder, Standardfelder oder benutzerdefinierte Felder.

### <a name="system-fields"></a>Systemfelder
Alle Standardentitäten oder benutzerdefinierten Entitäten werden mit einem Satz von schreibgeschützten Feldern erstellt, die Sie nicht ändern, löschen oder auf einen Wert festlegen können. Weitere Informationen finden Sie unter [System- und Datensatz-Titelfelder](data-platform-create-entity.md#system-fields-and-the-record-title-field). Dies sind die wichtigsten Systemfelder:

* **Datum der Datensatzerstellung**: Das Datum und die Uhrzeit der Erstellung eines Datensatzes
* **Erstellt von**: Der Benutzer, der den Datensatz erstellt hat
* **Datum der Datensatzänderung**: Das Datum und die Uhrzeit der letzten Änderung eines Datensatzes
* **Zuletzt geändert von**: Der Benutzer, der den Datensatz zuletzt geändert hat

### <a name="standard-fields"></a>Standardfelder
Jede Standardentität enthält eine Reihe von Standardfeldern, die Sie nicht ändern oder löschen können. Eine Liste der Entitäten und ihrer Felder sowie eine Liste der Auswahllisten finden Sie unter [Standardentitäten](https://docs.microsoft.com/common-data-service/entity-reference/standard-entities).

### <a name="custom-fields"></a>Benutzerdefinierte Felder
Sie können benutzerdefinierte Felder in einer Standardentität oder in einer benutzerdefinierten Entität erstellen. Sie müssen den Namen, den Anzeigenamen und den Datentyp der einzelnen benutzerdefinierten Felder angeben. Eine vollständige Liste der unterstützten Typen finden Sie unter [Entity field data types (Datentypen des Entitätsfelds)](https://docs.microsoft.com/en-us/common-data-service/entity-reference/field-data-types).

## <a name="lookup-relationships"></a>Nachschlagebeziehungen
Sie können zwischen Datensätzen in Entitäten navigieren, wenn sie zueinander in einer Beziehung stehen, die als Feld des **Lookup**-Datentyps definiert ist. Um eine Nachschlagebeziehung zu erstellen, fügen Sie ein Feld vom Datentyp **Lookup** einer Entität hinzu, und zeigen Sie auf die Entität, in der Sie nach Informationen suchen möchten. Weitere Informationen finden Sie unter [Entitätsbeziehungen über Nachschlagefeld](data-platform-entity-lookup.md).

## <a name="standard-entities"></a>Standardentitäten
Eine Liste der Entitäten und deren Felder sowie eine Liste der Enumerationen finden Sie in der [Standardentitäten](https://docs.microsoft.com/common-data-service/entity-reference/standard-entities).

| Funktionsgruppe | Beschreibung |
| --- | --- |
| Customer Service |Customer Service-Entitäten verwalten Probleme Ihrer Kunden, einschließlich der Überwachung, Eskalation und Dokumentation. |
| Foundation |Die Foundation-Entitäten enthalten Informationen, die für fast jede andere Entitätsgruppe relevant sind. Diese Gruppe enthält Entitäten wie Address und Currency. |
| People, Organizations und Groups |Diese Entitäten umfassen eine Vielzahl von Personen und Organisationen, mit denen Sie interagieren, einschließlich Mitarbeiter, Auftragnehmer, Spender, Freiwillige, Fans, Alumni und Familien. |
| Purchasing |Mit den Purchasing-Entitäten können Sie Einkauflösungen erstellen. |
| Vertrieb |Mit den Sales-Entitäten können Sie End-to-End-Vertriebslösungen erstellen, angefangen bei der Verfolgung von Leads und Verkaufschancen über das Nachfassen bei Kontakten, Akzeptieren und Übermitteln von Aufträgen bis zum Senden von Rechnungen. |

## <a name="get-started"></a>Erste Schritte
Probieren Sie es aus, indem Sie eine App mithilfe einer Standardentität erstellen, oder [erstellen Sie eine benutzerdefinierte Entität](data-platform-create-entity.md). Erstellen Sie anschließend [eine App, die diese Entität verwendet](data-platform-create-app.md).

<!--TODO - Add Link for Standard entity app - Template? -->

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

