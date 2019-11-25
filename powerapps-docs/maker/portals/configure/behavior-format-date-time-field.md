---
title: Verhalten und Format des Datums- und Uhrzeitfelds in Common Data Service | MicrosoftDocs
description: Verhalten und Format des Datums- und Uhrzeitfelds, die in einem Portal verwendet werden.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 785b5fa7def4a5b8e4964e888567d64643405708
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760434"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Verhalten und Format des Datums- und Uhrzeitfelds

In Common Data Service wird der Datum und Uhrzeit-Datentyp in vielen Systementitätsfeldern verwendet. Beispielsweise können Sie anzeigen, wann eine Firma zuletzt in einer Marketingkampagne verwendet wurde, oder das Datum und die Uhrzeit der letzten Eskalierung einer Anfrage anzeigen. Sie können auch benutzerdefinierte Entitäten erstellen, die die Datums- und Zeitfelder enthalten. Je nachdem, was das Feld darstellt, können Sie eines der folgenden Feldverhalten für Portalformulare und Raster auswählen: 
- **Ortszeit Benutzer**: Die Feldwerte werden in der Ortszeit des Benutzers angezeigt und gemäß der aktuellen Portalsprache/dem aktuellen Gebietsschema formatiert. Die Werte werden im UTC-Zeitzonenformat in Common Data Service gespeichert. Wenn ein Benutzer in Common Data Service (oder ein anderer Portalbenutzer) in einer anderen Zeitzone diesen Wert anzeigt, wird dieser für sie in ihre eigene Zeitzone konvertiert dargestellt.
- **Nur Datum**: Die Feldwerte enthalten nur das Datum und werden ohne Zeitzonenkonvertierung angezeigt. Der Zeitteil des Werts ist immer 12:00 Uhr. Der Wert, der von einem Benutzer angegeben wird, wird anderen Benutzern in verschiedenen Zeitzonen gleich angezeigt (z.B. Geburtdsdaten).
  
  > [!Note]
  > Das Verhalten dieses Felds kann nicht mehr geändert werden, nachdem es gespeichert wurde.
  
- **Zeitzonenunabhängig**: Die Feldwerte enthalten das Datum und die Uhrzeit und werden ohne Zeitzonenkonvertierung angezeigt. Der Wert, der von einem Benutzer angegeben wird, wird anderen Benutzern in verschiedenen Zeitzonen gleich angezeigt.
  
  > [!Note]
  > Das Verhalten dieses Felds kann nicht mehr geändert werden, nachdem es gespeichert wurde.

Sie können das Standardformat für Datum und Uhrzeit auch überschreiben, um es auf Portalen zu verwenden, indem Sie die folgenden Websiteeinstellungen erstellen:
- DateTime/DateFormat: Das im Portal verwendete Datumsformat. 
- DateTime/TimeFormat: Das im Portal verwendete Uhrzeitformat. 
- DateTime/DateTimeFormat: Das Format für das im Portal verwendete vollständige Datum/die vollständige Uhrzeit.

Standardmäßig verwendet das Portal die Standardformate für Datum und Uhrzeit, die durch die Spracheinstellungen der Website festgelegt werden.
Die akzeptierten Formate für Datum und Uhrzeit sind [hier](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings) festgelegt.
