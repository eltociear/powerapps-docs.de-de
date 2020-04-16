---
title: " Aktualisieren einer Verbindungsrolle (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie man eine Verbindungsrolle aktualisiert
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: e858b2722a2af2a24bf2ef65bb2a9ba53caf058e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155546"
---
# <a name="update-a-connection-role-early-bound"></a>Aktualisieren einer Verbindungsrolle (frühe Bindung)

Dieses Beispiel veranschaulicht, wie die Eigenschaften der gesammelten Verbindungsrolle wie Rollenname, Beschreibung und Kategorie veränder werden. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UpdateConnectionRole) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9) ist für ein Szenario gedacht, in dem sie die Daten enthält, die zur Aktualisierung eines bestehenden Datensatzes benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

1. Prüft auf aktuelle Version der Organisation. 
1. Erstellt die für dieses Beispiel erforderlichen Daten.

### <a name="demonstrate"></a>Demonstrieren

Die `Update`-Nachricht aktualisiert die Verbindungsrolle.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.