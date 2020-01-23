---
title: 'Beispiel: Duplikaterkennung aktivieren und Duplikate abrufen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie die Duplikaterkennung aktivieren und doppelte Datensätze abrufen.
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
ms.openlocfilehash: c43c9a25b4b662a00f2886c23cb05be1bb105f7d
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934306"
---
# <a name="sample-enable-duplicate-detection-and-retrieve-duplicates"></a>Beispiel: Duplikaterkennung aktivieren und Duplikate abrufen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-enable-duplicate-detection-and-retrieve-duplicates -->

Dieses Beispiel zeigt, wie Sie die Duplikaterkennung aktivieren und doppelte Datensätze abrufen. Sie können das Beispiel herunterladen von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/EnableDuplicateDetection).

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IsDuplicateDetectionEnabled`-Eigenschaft wird in einem Szenario verwendet werden, um eine Duplikaterkennungsregel für Organisation sowie für eine Entität zu aktivieren.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Account`-Methode erstellt mehrere Datensätze, um Duplikate abzurufen.
1. Die `RetrieveDuplicateRequest` Methode ruft die doppelten Datensätze ab. 
1. Die `EnableDuplicateDetectionForOrg` Klasse aktiviert die Duplikaterkennung für eine Organisation. 
1. So aktivieren Sie die Duplikaterkennung: `IsDuplicateDetectionEnabled = true`.
1. Die `RetrieveEntityRequest` Methode ruft die Entitätsmetadaten ab. 
1. Die `IsDuplicateDetectionEnabled = true`, um den Duplikaterkennungshinweis zu aktualisieren.
1. Die `UpdateEntityRequest` aktualisiert die Entität mit der Duplikaterkennung, die auf `true` festgelegt ist.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
