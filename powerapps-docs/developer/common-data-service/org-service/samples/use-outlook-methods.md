---
title: " Verwenden Sie Outlook-Methoden (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie man die Outlook-Methoden verwendet.
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
ms.openlocfilehash: 128f988bb9ae16ac477e62e7c67829545b811af8
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155518"
---
# <a name="sample-use-dynamics-365-for-outlook-methods"></a>Beispiel: Verwendung von Dynamics 365 for Outlook Methoden

Dieses Beispiel zeigt, wie die in der Baugruppe [Microsoft.Crm.Outlook.Sdk.dll](https://docs.microsoft.com/dotnet/api/microsoft.crm.outlook.sdk?view=dynamics-outlookclient-ce-9) verfügbaren Methoden verwendet werden. Sie können das Beispiel von [hier]() herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Baugruppe `Microsoft.Crm.Outlook.sdk` wird in einem Szenario verwendet, in dem sie Typen enthält, die eine programmatische Interaktion mit Microsoft Dynamics 365 for Outlook und Microsoft Dynamics 365 for Microsoft Office Outlook mit Offline-Zugriff ermöglichen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das oben beschriebene Beispiel zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `CrmOutlookService`-Methode legt den Dienst fest.
2. Die `CrmOutlookService.IsCrmClientOffline`-Methode prüft, ob der Kunde offline ist.
3. Die `CrmOutlookService.GoOnline()`-Methode bringt den Kunden zum Online-Betrieb. Diese Methode wird automatisch mit der Datenbank synchronisiert, es besteht keine Notwendigkeit, die `Sync()`-Methode aufzurufen.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.