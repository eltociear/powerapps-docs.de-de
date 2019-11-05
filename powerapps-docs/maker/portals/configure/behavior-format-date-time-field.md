---
title: Verhalten und Format des Felds "Datum und Uhrzeit" in Common Data Service | MicrosoftDocs
description: Das Verhalten und das Format der Datums-und Uhrzeit Felder, die in einem Portal verwendet werden.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553323"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Verhalten und Format des Felds "Datum und Uhrzeit"

In Common Data Service wird der Datums-und Uhrzeit Datentyp in vielen System Entitäts Feldern verwendet. Beispielsweise können Sie anzeigen, wann ein Konto zuletzt in einer Marketingkampagne verwendet wurde, oder das Datum und die Uhrzeit anzeigen, zu denen ein Fall eskaliert wurde. Sie können auch benutzerdefinierte Entitäten erstellen, die die Datums-und Uhrzeit Felder enthalten. Je nachdem, was das Feld darstellt, können Sie eines der folgenden Feld Verhalten für Portal Formulare und Raster auswählen: 
- **Lokaler Benutzer**: die Feldwerte werden in der lokalen Zeit des Benutzers angezeigt und gemäß der aktuellen Portal Sprache/dem aktuellen Gebiets Schema formatiert. Die Werte werden im UTC-Zeit Zonen Format in Common Data Service gespeichert. Wenn ein Benutzer in Common Data Service (oder einem anderen Portalbenutzer) in einer anderen Zeitzone den Wert anzeigt, wird dieser in seine eigene Zeitzone konvertiert.
- **Nur Datum**: die Feldwerte enthalten nur das Datum und werden ohne Zeit Zonen Konvertierung angezeigt. Der Uhrzeit Teil des Werts ist immer 12:00 Uhr. Der von einem Benutzer eingegebene Wert wird von anderen Benutzern in unterschiedlichen Zeitzonen (z. b. Geburtsdaten) gleich angezeigt.
  
  > [!Note]
  > Das Verhalten dieses Felds kann nicht geändert werden, nachdem es gespeichert wurde.
  
- **Zeit Zonen unabhängig**: die Feldwerte enthalten Datum und Uhrzeit und werden ohne Zeit Zonen Konvertierung angezeigt. Der von einem Benutzer eingegebene Wert wird von anderen Benutzern in unterschiedlichen Zeitzonen gleich angezeigt.
  
  > [!Note]
  > Das Verhalten dieses Felds kann nicht geändert werden, nachdem es gespeichert wurde.

Sie können das standardmäßige Datums-/Uhrzeitformat für Portale auch überschreiben, indem Sie die folgenden Site Einstellungen erstellen:
- DateTime/DATEFORMAT: das Datumsformat, das im Portal verwendet wird. 
- DateTime/TimeFormat: das Zeitformat, das im Portal verwendet wird. 
- DateTime/DateTimeFormat: das Format für das vollständige Datum und die Uhrzeit, das im Portal verwendet wird.

Standardmäßig verwendet das Portal das Standardformat für Datums-/Uhrzeitformate, das in den Einstellungen der Website Sprache festgelegt ist.
Die zulässigen Datums-/Uhrzeitformate werden [hier](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)angegeben.
