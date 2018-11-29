---
title: 'Beispiel: Senden einer E-Mail mithilfe einer Vorlage (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie eine E-Mail-Nachricht mittels einer Vorlage gesendet wird.'
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
# <a name="sample-send-an-email-using-a-template"></a>Beispiel: Senden einer E-Mail mithilfe einer Vorlage

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-send-email-template -->

Dieses Beispiel zeigt, wie eine E-Mail-Nachricht mittels einer Vorlage unter Verwendung der Message [SendEmailFromTemplateRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.sendemailfromtemplaterequest?view=dynamics-general-ce-9) gesendet wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SendEmailUsingTemp) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `SendEmailFromTemplateRequest` ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die zum Senden einer E-Mail-Nachricht über eine Vorlage erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt einen Kontaktdatensatz zum Senden einer E-Mail an (Feld "An:").

### <a name="demonstrate"></a>Demonstrieren

1. `ActivityParty` erstellt die Aktivitätspartei `From:` und `To:` für die E-Mail.
2. Erstellt eine E-Mail-Nachricht.
3. `QueryExpression` fragt ab, um eine E-Mail-Vorlage vom Typ `Contact` zu erhalten.
4. `SendEmailFromTemplateRequest` sendet eine E-Mail-Nachricht mithilfe einer Vorlage.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
