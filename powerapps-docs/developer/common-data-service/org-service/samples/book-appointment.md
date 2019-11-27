---
title: 'Beispiel: Buchen eines Termins (Common Data Service) | Microsoft-Dokumentation'
description: 'Dieses Beispiel zeigt, wie Sie einen Termin buchen oder planen '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 651e10d5a57d644f7330e26ba3889d7fde1992bb
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748386"
---
# <a name="sample-book-an-appointment"></a>Beispiel: Buchen eines Termins

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-book-appointment -->

Dieses Beispiel veranschaulicht, wie Sie mithilfe der Meldung [BookRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.bookrequest?view=dynamics-general-ce-9) einen Termin buchen oder planen. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/BookAppointment) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `BookRequest` ist für die Verwendung in einem Szenario zur Buchung oder Planung eines Termins vorgesehen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft die aktuelle Version der Organisation.
1. Ruft die aktuellen Benutzerinformationen ab und erstellt die ActivityParty-Instanz.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt die Termininstanz mithilfe der Nachricht [BookRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.bookrequest?view=dynamics-general-ce-9) und überprüft, ob der Termin geplant ist oder nicht.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
