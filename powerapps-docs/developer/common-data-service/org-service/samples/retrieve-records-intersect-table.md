---
title: 'Beispiel: Abrufen von Datensätzen aus einer Überschneidungstabelle (Common Data Service for Apps) | Microsoft Docs'
description: Dieses Beispiel veranschaulicht das Abrufen eines Datensatzes aus einer Überschneidungstabelle.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-retrieve-records-from-an-intersect-table"></a>Beispiel: Abrufen von Datensätzen aus einer Überschneidungstabelle

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-retrieve-records-intersect-table --> Dieses Beispiel veranschaulicht das Abrufen von Datensätzen aus einer Überschneidungstabelle. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveRecordsFromIntersectTable) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `QueryExpression` ist für die Verwendung in einem Szenario vorgesehen, das Abfragen in einer Hierarchie von Ausdrücken enthält.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation. 
1. Die Methode `CreateRequireRecords` erstellt Entitätsdatensätze, die von dem Beispiel verwendet werden.
1. Die Message `QueryExpression` wird zum Abrufen der Standardunternehmenseinheit verwendet, die zum Erstellen des Teams benötigt wird.
1. `WhoAmIRequest` fordert die GUID des aktuellen Benutzers an.
1. Die Methode `Role` instanziiert einen Rollenentitätsdatensatz und legt seine Eigenschaftswerte fest.
1. `AssociateRequest` weist dem Benutzer die Managerrolle zu. 

### <a name="demonstrate"></a>Demonstrieren

1. `QueryExpression` ruft die Datensätze aus einer Überschneidungstabelle ab.
1. `RetrieveMultipleRequest` erstellt die Fetch-Anforderung und erhält die Ergebnisse.
### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.