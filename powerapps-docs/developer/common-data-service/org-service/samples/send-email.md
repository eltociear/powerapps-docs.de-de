---
title: 'Beispiel: Senden einer E-Mail (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie eine E-Mail gesendet wird.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-send-an-email"></a>Beispiel: Senden einer E-Mail

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-send-email -->

In diesem Beispiel wird gezeigt, wie eine E-Mail mit einer [SendEmailRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.sendemailrequest?view=dynamics-general-ce-9)-Nachricht gesendet wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SenEmail) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `SendEmailRequest`-Message ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie Daten enthält, die zum Senden einer E-Mail-Nachricht benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die Methode `Contact` erstellt einen Kontakt zum Senden einer E-Mail an `(To: field)`.
1. Die Methode `WhoAmIRequest` ruft die aktuellen Benutzerinformationen zum Senden der E-Mail `(From: field)` ab.
1. Die Methode `ActivityParty` erstellt die Aktivitätspartei `To` und `From` für die E-Mail.
1. Die Methode `Email` erstellt eine E-Mail-Nachricht.

### <a name="demonstrate"></a>Demonstrieren

1. Die Methode `SendEmailRequest` sendet eine E-Mail-Nachricht, die in der [Setup](#setup) erstellt wird.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
