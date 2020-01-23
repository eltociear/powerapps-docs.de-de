---
title: 'Beispiel: Prüfen eines Termins (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie ein Termin überprüft wird
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
ms.openlocfilehash: d49ad9ed6440076d20e771b099227b35dbf7ae36
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934158"
---
# <a name="sample-validate-an-appointment"></a>Beispiel: Prüfen eines Termins

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-validate-appointment -->

Dieses Beispiel veranschaulicht, wie Sie mithilfe der Meldung [ValidateRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.validaterequest?view=dynamics-general-ce-9) einen Termin überprüfen. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateAppointment) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `ValidateRequest` ist dafür bestimmt, im Szenario verwendet zu werden, in dem sie Daten enthält, die dazu benötigt werden, zu überprüfen, dass ein Termin oder Servicetermin(Serviceaktivität) in angemessener Weise über die verfügbaren Ressourcen für die Aktivität, die Dauer und den Standort verfügt.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt Beispielkontakt- und -Aktivitätsparteidatensätze.
3. Erstellt Beispieltermin.

### <a name="demonstrate"></a>Demonstrieren

1. Ruft den zu überprüfenden Termin ab. 
2. Die `ValidateRequest`-Nachricht überprüft den im Setup(#setup) erstellten Termin.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
