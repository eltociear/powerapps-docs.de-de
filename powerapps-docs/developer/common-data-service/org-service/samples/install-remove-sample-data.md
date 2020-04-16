---
title: 'Beispiel: Installieren und Entfernen von Beispieldaten (Common Data Service) | Microsoft Docs'
description: In diesem Beispiel wird gezeigt, wie Beispieldaten installiert und entfernt werden.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 0d70537539cf318ab6c70345178cd55863c4ea0b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155742"
---
# <a name="install-or-remove-sample-data"></a>Installieren oder entfernen der Beispieldaten

Dieses Beispiel zeigt, wie die Beispieldaten für eine Organisation mit Hilfe der Meldung [InstallSampleDataRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.installsampledatarequest?view=dynamics-general-ce-9) installiert oder deinstalliert werden können.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `InstallSampleDataRequest`-Nachricht ist für ein Szenario gedacht, in dem sie Daten enthält, die für die Installation der Beispieldaten erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

1. Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Fordert die Benutzer auf, Beispieldaten zu installieren oder zu entfernen.
2. Wenn sich der Benutzer für die Installation von Beispieldaten entscheidet, installiert die `InstallSampleDataRequest`-Meldung die Beispieldaten.
3. Wenn sich der Benutzer für die Deinstallation der Beispieldaten entscheidet, werden die Beispieldaten durch die `UninstallSampleDataRequest`-Meldung entfernt.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.