---
title: Daten nach Excel exportieren in Power Apps | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 1f9368a7630e7b2f94e7b624e0d005f89b919a59
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "3302723"
---
# <a name="export-data-to-excel"></a>Daten in Excel exportieren

Müssen Sie Ihre Daten analysieren und sie in umsetzbare Elemente konvertieren, die Sie bei der Umsatzförderung unterstützen? Jetzt können Sie das tun, wenn Sie Ihre Daten nach Excel oder Excel Online exportieren. Außerdem ist das Analysieren großer Datasets kein Problem, da Sie bis zu 100.000 Zeilen Daten exportieren können.
  
Sie können sich für den Export statischer oder dynamischer Arbeitsblätter entscheiden, die Sie wieder zurück in die App importieren können. Wenn Sie höher entwickelte Funktionen benötigen, können Sie eine dynamische PivotTable exportieren, die es sehr einfach macht, Daten zu strukturieren und zusammenzufassen.  
  
Sie können Daten in eine Excel-Standarddatei exportieren, die Sie auf jedem Gerät verwenden können, etwa Ihrem Smartphone, Tablet oder Desktopcomputer. Die Daten werden in dem gleichen Format exportiert, das Sie in der App sehen. Text bleibt Text, Zahlen bleiben Zahlen, und Datumswerte bleiben Datumswerte. Wenn Sie Daten aus der App nach Excel exportieren, ändern sich möglicherweise einige Zellenformate. In der folgenden Tabelle ist zusammengefasst, wie die Daten in Apps angezeigt werden, und wie sich das Zellformat beim Exportieren der Daten nach Excel ändert.  
  
## <a name="cell-format-when-data-is-exported-from-model-driven-apps"></a>Zellformat beim Exportieren von Daten aus modellgesteuerten Apps
  
| Datenformat in modellgesteuerten Apps |                                            Zellformat in Excel                                             |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Text, Tickersymbol, Telefon, Optionsmenge und Nachschlagevorgang            |                                                       Wird als Text angezeigt. Optionssatz wird zu Dropdownliste.                                                       |
|                                 E-Mail, URL                                 |                                                                        Wird als "Allgemein" angezeigt.                                                                         |
|                                   Anzahl                                   |                                                             Wird als Zahl ohne Gruppentrennzeichen angezeigt                                                             |
|                                  Währung                                  |                                                         Wird als Zahl ohne Währungssymbol ($) angezeigt                                                         |
|                          Nur Datum, Datum und Uhrzeit                          |                                                                       Wird nur als Datum angezeigt                                                                        |
|                       Berechnete und Rollupfelder                        | Bearbeitung in Excel möglich, kann jedoch nicht wieder in Power Apps importiert werden |
|                               Geschützte Felder                               | Bearbeitung in Excel möglich, kann jedoch nicht wieder in Power Apps importiert werden |
  
## <a name="see-which-type-of-export-works-best-for-you"></a>Finden Sie heraus, welche Art Export sich für Sie am besten eignet  
  
|                                                                                                               Aufgabe                                                                                                                |                                              Erhalten Sie weitere Informationen                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
|   Nehmen Sie eine *Ad-Hoc*- oder *Was-wäre-wenn*-Analyse vor, ohne App-Daten zu ändern. Oder nehmen Sie schnell eine Massenbearbeitung an mehreren Datensätzen vor.   | [Nach Excel Online exportieren](export-to-excel-online.md) |
|                                                                   Rufen Sie eine Momentaufnahme der Daten zum aktuellen Datum und der aktuellen Uhrzeit ab, oder weil Sie sie mit anderen teilen möchten.                                                                    |           [Exportieren in ein statisches Excel-Arbeitsblatt](export-excel-static-worksheet.md)           |
| Rufen Sie die aktuellsten Informationen ab, die Sie in Excel jederzeit aktualisieren und mit dem abgleichen können, was Sie in der App sehen. |          [In eine dynamische Excel-Tabelle exportieren](export-excel-dynamic-worksheet.md)          |
|                                                                      Zeigen Sie App-Daten in einer PivotTable an.                                                                      |                 [In eine Excel-PivotTable exportieren](export-excel-pivottable.md)                 |



Wenn Sie Daten in Excel (XLSX-Format) exportieren und dann Spalten hinzufügen oder ändern, können Sie die Daten nicht mehr in Dynamics 365 zurück importieren. Dies wird für das XLSX-Dateiformat nicht unterstützt.  
  
Wenn Sie Excel 2010 verwenden, erhalten Sie möglicherweise diese Fehlermeldung, wenn Sie Daten aus dem Kontenbereich exportieren: 
 
`The file is corrupt and cannot be opened.`  
  
Die Fehlermeldung tritt aufgrund einer Einstellung in Excel auf. So beheben Sie das Problem:  
  
1. Öffnen Sie Excel 2010.  
  
2. Gehen Sie zu **Datei** > **Optionen**.  
  
3. Navigieren Sie zu **Trust Center** > **Trust Center-Einstellungen**.  
  
4. Wählen Sie **Geschützte Ansicht** aus, und deaktivieren Sie dann die Kontrollkästchen für die beiden ersten Optionen.  
  
5. Klicken Sie auf **OK**, und schließen Sie dann das Dialogfeld **Optionen**.  
  

