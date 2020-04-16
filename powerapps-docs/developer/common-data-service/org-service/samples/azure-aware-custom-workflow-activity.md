---
title: Azure-fähige benutzerdefinierte Workflowaktivität (Common Data Service) | Microsoft-Dokumentation
description: Dieses Beispiel erhält den Datenkontext aus dem aktuellen Common Data Service-Vorgang und veröffentlicht diesen im Azure Service Bus.
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
ms.openlocfilehash: 50bcfa51bb8978fc65b903a5f7e30657d0da6778
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155934"
---
# <a name="sample-azure-aware-custom-workflow-activity"></a>Beispiel: Azure-fähige benutzerdefinierte Workflowaktivität

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity -->

Dieses Beispiel erhält den Datenkontext aus dem aktuellen Prozess und veröffentlicht ihn im Azure Service Bus. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Azurecustomworkflowactivity) herunterladen.

## <a name="requirements"></a>Anforderungen

Sie müssen Common Data Service für die Verbindung mit Azure konfigurieren, bevor Sie sich anmelden und diese benutzerdefinierte Beispiel-Workflowaktivität ausführen. Weitere Informationen: [Konfigurieren der Microsoft Azure-Integration mit Common Data Service](../../configure-azure-integration.md).

Beachten Sie das erforderliche `Input id`-Argument im Code. Wenn Sie diese Aktivität zu einem Workflow hinzufügen, müssen Sie die GUID eines Azure-Dienstendpunkts angeben.

Wenn Sie diese benutzerdefinierte Workflowaktivität bei Common Data Service registrieren, müssen Sie es im Sandkasten (mit teilweiser Vertrauenswürdigkeit) registrieren.

## <a name="how-to-run-samples"></a>Ausführen von Beispielen

1. Um eine lokale Kopie zu erhalten, laden Sie den [Beispielbericht](https://github.com/Microsoft/PowerApps-Samples) herunter, oder klonen Sie ihn.
2. Registrieren einer Workflowaktivität

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel zeigt, wie Sie eine benutzerdefinierte Workflowaktivität schreiben, die den Datenkontext vom aktuellen Common Data Service-Vorgang im Azure Service Bus veröffentlichen kann. Das Veröffentlichen des Datenkontexts wird durch die <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService.Execute(Microsoft.Xrm.Sdk.EntityReference,Microsoft.Xrm.Sdk.IExecutionContext)>-Methode ausgeführt.
