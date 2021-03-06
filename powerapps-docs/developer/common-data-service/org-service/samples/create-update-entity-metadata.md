---
title: 'Beispiel: Erstellen und Aktualisieren von Entitätsmetadaten (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie Entitätsmetadaten erstellen und aktualisieren.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 379df3a1b3f3bfd75b86bf07d82b3f0508d099d1
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155846"
---
# <a name="create-and-update-entity-metadata"></a>Erstellen und Aktualisieren von Entitätsmetadaten

In diesem Thema wird erläutert, wie Sie eine benutzerdefinierte Entität mit der Bezeichnung **Bankkonto** programmgesteuert erstellen und dieser vier verschiedene Arten von Attributen hinzufügen.

Sie können auch unternehmenseigene benutzerdefinierte Entitäten erstellen. Weitere Informationen: [Entitätsbesitz](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/introduction-entities#entity-ownership). Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreateUpdateEntityMetadata) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `CreateEntityRequest` soll in einem Szenario verwendet werden, in dem sie die Daten enthält, die zum Erstellen einer benutzerdefinierten Entität und optional zu deren Hinzufügen zu einer angegebenen nicht verwalteten Lösung erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `createrequest`-Methode erstellt die benutzerdefinierte Entität. 
2. Die `Entity`-Methode wird verwendet, um die Entität zu definieren.
3. Die `StringAttributeMetadata`-Methode definiert das primäre Attribut der Entität.
4. Die `CreateBankNameAttributeRequest`-Methode erstellt ein string-Attribut zur Entität.
5. Die `CreateBalanceAttributeRequest`-Methode erstellt ein money-Attribut zur Entität.
6. Die `CreateCheckedDateRequest`-Methode erstellt ein DateTime-Attribut zur Entität.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
