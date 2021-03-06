---
title: " Warteschlangen löschen (Common Data Service) | Microsoft-Dokumentation"
description: Dieses Beispiel zeigt, wie eine Warteschlange gelöscht wird
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
ms.openlocfilehash: b663296a3f99624b1aee8996f79f04cbf9a245ae
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155842"
---
# <a name="delete-a-queue-early-bound"></a>Löschen einer Warteschlange (mit früher Bindung)

In diesem Beispiel wird gezeigt, wie Sie eine einfache Warteschlange mithilfe der Nachricht [IOrganizationService.Delete](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9) löschen.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DeleteQueue) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService`-Methoden soll in einem Szenario verwendet werden, das Daten enthält, die programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die `CreateRequiredRecords`-Methode erstellt Entitätsdatensätze, die für das Beispiel erforderlich sind.

### <a name="demonstrate"></a>Demonstrieren

Die `newQueue`-Methode erstellt eine Warteschlangeninstanz und legt deren Eigenschaftswerte fest. 

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

