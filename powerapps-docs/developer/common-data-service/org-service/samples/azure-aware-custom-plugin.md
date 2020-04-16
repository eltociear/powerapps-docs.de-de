---
title: Benutzerdefiniertes Azure-fähiges Plug-In (Common Data Service) | Microsoft-Dokumentation
description: Dieses Beispiel-Plugin kann den Pipeline-Ausführungskontext auf den Azure Service Bus posten.
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
ms.openlocfilehash: f9dd7300882307bd06941b91ece152bf97002f83
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155922"
---
# <a name="sample-azure-aware-custom-plug-in"></a>Beispiel: Benutzerdefiniertes Azure-fähiges Plug-In

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-azure-aware-custom-plugin -->

Das Plug-In demonstriert, wie der Ausführungskontext und der Nachverfolgungsdienst vom Dienstanbieterparameter der `Execute`-Methode abgerufen werden kann. Das Plug-In veröffentlicht den Kontext dann auf dem Azure Service Bus-Endpunkt und schreibt Informationen in das Ablaufverfolgungsprotokoll, um das Debuggen zu erleichtern. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Azureplugin) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

1. Um eine lokale Kopie zu erhalten, laden Sie den [Beispielbericht](https://github.com/Microsoft/PowerApps-Samples) herunter, oder klonen Sie ihn.
2. Öffnen Sie die Beispiellösung in Visual Studio und signieren Sie die Assembly mit einem Schlüssel.
3. Registrieren Sie das Plugin mit dem **Plug-in-Registrierungstool**.

>[!NOTE]
> Dieses Beispiel erfordert, dass zuerst ein Service-Endpunkt erstellt und seine ID über den unsicheren Konfigurationsparameter an den Plugin-Konstruktor übergeben wird, wenn der Plugin-Schritt registriert wird.


