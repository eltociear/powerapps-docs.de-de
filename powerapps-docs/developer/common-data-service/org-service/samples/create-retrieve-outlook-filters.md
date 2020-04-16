---
title: " Outlook-Filter erstellen und abrufen (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie Filter für Outlook Filter erstellt und abgerufen werden.
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
ms.openlocfilehash: 165dfaaa8fe419257fc552be0f4e9e231fb7c2e8
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155870"
---
# <a name="create-and-retrieve-outlook-filters"></a>Outlook-Filter erstellen und abrufen

Dieses Beispiel veranschaulicht, wie Filter für Outlook abgerufen werden.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreartRetrieveOutlookFilters) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das oben beschriebene Beispiel zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `fetchXml`-Methode erstellt einen Offline-Filter. In Ihrem Outlook-Client erscheint dies in der Registerkarte Systemfilter unter **Datei -> CRM -> Synchronisieren -> Outlook-Filter**.
2. Die `InstantiateFiltersRequest`-Methode aktiviert die ausgewählten Offline-Vorlagen für den aktuellen Benutzer.
3. Die `ResetUserFilterRequest`-Methode setzt die Offline-Vorlagen des aktuellen Benutzers auf die Standardeinstellungen zurück.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

