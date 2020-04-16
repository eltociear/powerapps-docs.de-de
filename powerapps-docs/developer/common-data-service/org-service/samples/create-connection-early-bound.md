---
title: 'Beispiel: Erstellen einer Verbindungsrolle (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie eine Verbindungsrolle erstellt wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8e67af447e8d43f14476dcb153798ff3ce7da673
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155894"
---
# <a name="sample-create-a-connection"></a>Beispiel: Erstellen einer Verbindung

Dieses Beispiel zeigt, wie Sie eine Verknüpfung zwischen einer Firma und einer Kontaktentität erstellen, mit übereinstimmenden Verknüpfungsrollen. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConnectionEarlyBound) herunterladen. 
  
## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel zeigt, wie Sie eine Verknüpfung zwischen einer Firma und einem Kontakt erstellen, mit übereinstimmenden Verknüpfungsrollen.  

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt eine Verbindungsrolle für Firmen- und Kontaktentitäten.
3. Erstellt einen der Verbindungsrolle zugehörigen Objekttypcode für Firmen- und Kontaktentität.
4. Verknüpft die Verbindungsrolle mit sich selbst.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt eine Verbindung zwischen Firmen- und Kontaktentitäten. 
2. Weist eine Verbindungsrolle einem Datensatz zu.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
