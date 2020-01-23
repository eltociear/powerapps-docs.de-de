---
title: " Lizenzinformationen abrufen (Common Data Service) | Microsoft Docs"
description: 'Dieses Beispiel zeigt, wie Lizenzinformationen abgerufen werden '
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
ms.openlocfilehash: 1ed007c4536a359b0e3a6a4c072f02cebd7c3311
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934206"
---
# <a name="retrieve-license-information"></a>Lizenzinformationen abrufen

In diesem Beispiel wird gezeigt, wie die [IDeploymentService.RetrieveDeploymentLicenseTypeRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievedeploymentlicensetyperequest?view=dynamics-general-ce-9) Nachricht und die [IOrganizationService.RetrieveLicenseInfoRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievelicenseinforequest?view=dynamics-general-ce-9) Nachricht verwendet werden, um Informationen zu Lizenzen abzurufen.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveLicenseInformation) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die [IDeploymentService.RetrieveDeploymentLicenseTypeRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievedeploymentlicensetyperequest?view=dynamics-general-ce-9) Meldung soll in einem Szenario verwendet werden, in dem es Daten enthält, die zum Abrufen des Lizenztyps für eine Bereitstellung von erforderlich sind Common Data Service.

Die [IDeploymentService.RetrieveDeploymentLicenseTypeRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievelicenseinforequest?view=dynamics-general-ce-9) Meldung soll in einem Szenario verwendet werden, in dem es Daten enthält, die zum Abrufen des Lizenztyps für eine Bereitstellung von erforderlich sind Common Data Service.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `deploymentTypeRequest` Methode erstellt eine Anforderung zum Abrufen der Bereitstellungslizenztypen.
2. Die `licenseInfoRequest` Meldung erstellt Anforderung zum Abrufen der lizenzierten Informationsanforderung.

### <a name="clean-up"></a>Bereinigung

Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich