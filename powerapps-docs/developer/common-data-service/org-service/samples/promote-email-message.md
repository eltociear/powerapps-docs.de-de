---
title: 'Beispiel: Heraufstufen einer E-Mail-Nachricht (Common Data Service) | Microsoft Docs'
description: <Description>
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
# <a name="sample-promote-an-email-message"></a>Beispiel: Heraufstufen einer E-Mail-Nachricht

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-promote-email-message -->

Dieses Beispiel zeigt, wie eine E-Mail-Aktivitätsinstanz aus der angegebenen E-Mail-Nachricht in Common Data Service erstellt wird, indem die Nachricht [DeliverPromoteEmailRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.deliverpromoteemailrequest?view=dynamics-general-ce-9) verwendet wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PromoteEmail) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `DeliverPromoteEmailRequest` ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die benötigt werden, um einen E-Mail-Aktivitätsdatensatz aus der angegebenen E-Mail-Nachricht zu erstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt eines Kontakts zum Senden einer E-Mail an (Feld "An:").
2. `WhoAmIRequest` ruft den Systembenutzer zum Senden der E-Mail (Feld "Von:") ab.
3. Die Mesage `DeliverPromoteEmailRequest` erstellt die Anforderung und führt diese auch aus.
4. Überprüfen Sie den Erfolg, indem Sie anonyme Typen definieren, die mögliche Werte für den E-Mail-Status definieren. 
5. Fragt die zugestellte E-Mail ab und überprüft, ob der Statuscode `sent` ist.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
