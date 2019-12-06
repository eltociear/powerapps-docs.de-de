---
title: Exportieren von Daten nach Excel in powerapps | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680625"
---
# <a name="export-data-to-excel"></a>Exportieren von Daten nach Excel

Müssen Sie die Daten analysieren und diese Daten in umsetzbare Elemente konvertieren, die Ihnen helfen, mehr Umsätze zu fördern? Dies ist jetzt möglich, wenn Sie Ihre Daten in Excel oder Excel Online exportieren. Außerdem ist das Analysieren großer Datasets kein Problem, da Sie bis zu 100.000 Daten Zeilen exportieren können.
  
Sie können statische Arbeitsblätter oder dynamische Arbeitsblätter exportieren, die Sie wieder in die App importieren können. Wenn Sie erweiterte Funktionen benötigen, können Sie eine dynamische Pivotfunktion exportieren. dadurch ist es sehr einfach, Daten zu organisieren und zusammenzufassen.  
  
Sie können Daten in eine standardmäßige Excel-Datei exportieren, die Sie auf jedem Gerät wie z. b. auf Ihrem Smartphone, Tablet oder Desktop Computer verwenden können. Die Daten werden in dem Format exportiert, das in der App angezeigt wird. Text bleibt Text, Zahlen werden Zahlen, und Datumsangaben verbleiben Datumsangaben. Wenn Sie jedoch Daten aus der app in Excel exportieren, können sich einige Zell Formate ändern. In der folgenden Tabelle wird zusammengefasst, wie die Daten in-apps angezeigt werden und wie sich das Zellen Format ändert, wenn Sie die Daten nach Excel exportieren.  
  
## <a name="cell-format-when-data-is-exported-from-model-driven-apps"></a>Zellformat beim Exportieren von Daten aus Modell gesteuerten apps
  
| Datenformat in Modell gesteuerten apps |                                            Zellformat in Excel                                             |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Text, ticksymbol, Telefon, Options Satz und suchen            |                                                       Wird als Text angezeigt, und der Options Satz wird zu einer Dropdown Liste.                                                       |
|                                 E-Mail, URL                                 |                                                                        Wird als allgemein angezeigt.                                                                         |
|                                   Number                                   |                                                             Zeigt als Zahl ohne Gruppen Trennzeichen an.                                                             |
|                                  Währung                                  |                                                         Zeigt als Zahl an und enthält kein Dollarzeichen ($).                                                         |
|                          Nur Datum, Datum und Uhrzeit                          |                                                                       Nur als Datum anzeigen                                                                        |
|                       Berechnete Felder und rollupfelder                        | In Excel bearbeitbar, kann aber nicht zurück in Power apps importiert werden |
|                               Gesicherte Felder                               | In Excel bearbeitbar, kann aber nicht zurück in Power apps importiert werden |
  
## <a name="see-which-type-of-export-works-best-for-you"></a>Sehen Sie, welche Art von Export für Sie am besten geeignet ist.  
  
|                                                                                                               Task                                                                                                                |                                              Weitere Informationen                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
|   Durchführen einer *Ad-hoc-* oder *Was-wäre-wenn* -Analyse ohne Änderung der APP Oder Sie können eine schnelle Massenbearbeitung in mehrere Datensätze durcharbeiten.   | [Online in Excel exportieren](export-to-excel-online.md) |
|                                                                   Erstellen Sie eine Momentaufnahme der Daten mit den aktuellen Daten und der aktuellen Uhrzeit, oder möchten Sie Sie für andere Benutzer freigeben.                                                                    |           [Exportieren in ein statisches Excel-Arbeitsblatt](export-excel-static-worksheet.md)           |
| Hier finden Sie die aktuellsten Informationen, die Sie in Excel aktualisieren können, und Sie können die Inhalte, die Sie in der app sehen, zu einem beliebigen Zeitpunkt abgleichen. |          [Exportieren in ein dynamisches Excel-Arbeitsblatt](export-excel-dynamic-worksheet.md)          |
|                                                                      Anzeigen von App-Daten in einer Pivottabelle.                                                                      |                 [Exportieren in eine Excel-PivotTables](export-excel-pivottable.md)                 |



Wenn Sie Daten in Excel (XLSX-Format) exportieren und dann Spalten hinzufügen oder ändern, können Sie die Daten nicht wieder in Dynamics 365 importieren. Dies wird für das xlsx-Dateiformat nicht unterstützt.  
  
Wenn Sie Excel 2010 verwenden, erhalten Sie möglicherweise diese Fehlermeldung, wenn Sie Daten aus dem Bereich Konten exportieren: 
 
`The file is corrupt and cannot be opened.`  
  
Die Fehlermeldung tritt aufgrund einer Einstellung in Excel auf. Um das Problem zu beheben, gehen Sie wie folgt vor:  
  
1. Öffnen Sie Excel 2010.  
  
2. Wechseln Sie zu **Datei** > **Optionen**.  
  
3. Wechseln Sie zu **Trust Center** > Einstellungen für das **Trust Center**.  
  
4. Wählen Sie **geschützte Ansicht** aus, und deaktivieren Sie dann die Kontrollkästchen für die ersten beiden Optionen.  
  
5. Wählen Sie **OK** aus, und schließen Sie dann das Dialogfeld **Optionen** .  
  

