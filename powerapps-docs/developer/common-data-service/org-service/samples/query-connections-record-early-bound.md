---
title: 'Beispiel: Abfragen von Verbindungen nach Datensatz (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie ein bestimmter Datensatz in Verbindungen abgefragt wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c38b1709e34ea85f7de84b0c9eaea0a2c9256c2d
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934254"
---
# <a name="sample-query-connections-by-a-record"></a>Beispiel: Abfragen von Verbindungen nach Datensatz 

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-connections-record-early-bound -->

Dieses Beispiel zeigt, wie ein bestimmter Datensatz in Verbindungen abgefragt wird. Dabei werden Verbindungen zwischen einem Kontakt und zwei Konten erstellt und dann die Verbindungen des Kontakts gesucht. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryByRecord) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

In diesem Beispiel werden Account-  und Kontaktdatensätze Verbindungsrollen zwischen ihnen erstellt. `QueryExpression` ruft die Verbindungen für einen bestimmten Datensatz ab.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Definiert einige anonyme Typen, um den Bereich der möglichen Werte für die Verbindungseigenschaften festzulegen.
3. `ConnectionRole` erstellt eine Verbindungsrolle.
4. `ConnectionRoleObjectType` erstellt eine Verbindungsrollen-Objekttypcode-Datensatz für die Account-Entität. 
5. Erstellt wenige Account- und Kontaktdatensätze für die Verwendung in der Verbindung.

### <a name="demonstrate"></a>Demonstrieren

`QueryExpression` ruft alle Verbindungen ab, die dem Kontakt zugeordnet sind, der im Beispiel erstellt wird.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
