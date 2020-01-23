---
title: " Entitätsinstanzen serialisieren und deserialisieren (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie Sie eine per Entitätsinstanz serialisieren und deserialisieren.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: 6bc85049df107821dd8cdaba0a33b1ec0f15a979
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934555"
---
# <a name="serialize-and-deserialize-an-entity-instance"></a>Eine Entitätsinstanz serialisieren und deserialisieren 

Dieses Beispiel veranschaulicht, wie die früh und spät gebunden Entitätsinstanzen in ein serialisiertes XML-Format umgewandelt werden und wie die gebundenen XML-Formate einer früh gebundenen Entitätsinstanz deserialisiert werden.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SerializeDeserializeEntity) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Weitere Informationen unter [Wie man Beispiele lässt](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) zum Ausführen dieses Beispiels.

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `DataContractSerializer` Nachricht soll in einem Szenario verwendet werden, in dem eine Instanz eines Typs mithilfe eines bereitgestellten Datenvertrags in einen XML-Stream oder ein Dokument serialisiert und deserialisiert wird. Diese Klasse kann nicht vererbt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `CreateRequiredRecords` Methode erzeugt das für die Beispieldaten erforderliche Beispiel.

### <a name="demonstrate"></a>Demonstrieren

1. Die `DataContractSerializer` Methode serialisiert die Kontaktdatensätze in XML und schreibt sie auf die Festplatte. 
1. Die `earlyBoundSerializer` Methode deserialisiert die Entitätinstanz.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

