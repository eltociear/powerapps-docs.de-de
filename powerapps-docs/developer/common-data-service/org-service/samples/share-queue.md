---
title: " Freigeben einer Warteschlange (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie eine Warteschlange gemeinsam genutzt werden kann.
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
ms.openlocfilehash: d2f569de501b89be1a535244864dac8ff6a7578d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155570"
---
# <a name="share-a-queue"></a>Eine Warteschlange freigeben

Dieses Beispiel zeigt, wie einem Benutzer oder Team Zugriff auf eine Warteschlange zugewiesen wird. Die [AddPrincipalToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addprincipaltoqueuerequest?view=dynamics-general-ce-9) fügt den angegebenen Prinzipal der Liste der Warteschlangenmitglieder hinzu. Wenn der angegebene Sicherheitsprinzipal ein Team ist, wird jedes Teammitglied der Warteschlange hinzugefügt.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ShareQueue) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Siehe [Wie man dieses Beispiel ausführt ](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) für Informationen über die Ausführung dieses Beispiels.

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht [AddPrincipalToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addprincipaltoqueuerequest?view=dynamics-general-ce-9) ist für ein Szenario gedacht, in dem sie die Daten zum Hinzufügen des angegebenen Prinzipals zur Liste der Warteschlangenmitglieder enthält. Wenn der Prinzipal ein Team ist, fügen Sie jedes Teammitglied zur Warteschlange hinzu.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

1. Prüft auf aktuelle Version der Organisation. 
1. Erstellt die für dieses Beispiel erforderlichen Daten.

### <a name="demonstrate"></a>Demonstrieren

Die `AddPrincipalToQueueRequest`-Nachricht teilt sich eine Warteschlange mit einem Team.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.