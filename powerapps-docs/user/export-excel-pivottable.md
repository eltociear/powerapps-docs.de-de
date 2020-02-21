---
title: Exportieren in eine Excel-PivotTable aus einer modellgesteuerten Power Apps-App | Microsoft-Dokumentation
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
ms.openlocfilehash: b14e24e7048e4f91de13f582914ffb621d3c7899
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725791"
---
# <a name="export-to-an-excel-pivottable"></a>Exportieren in eine Excel-PivotTable


Sie können App-Daten in eine Office Excel-PivotTable exportieren, um Muster und Trends in Daten zu erkennen. Eine Excel-PivotTable ist eine hervorragende Möglichkeit, Ihre Daten aus der App zusammenzufassen, zu analysieren, zu untersuchen und darzustellen. Sie können bis zu 100.000 Datensätze gleichzeitig exportieren.  
  

## <a name="export-data-to-an-excel-pivottable"></a>Exportieren von Daten in eine Excel-PivotTable  
Die Option zum Exportieren von Daten in eine Excel-PivotTable steht nicht für alle Datensatztypen zur Verfügung. Wenn die Option nicht angezeigt wird, ist sie für den betreffenden Datensatz nicht verfügbar.  
  
1. Öffnen Sie eine Liste mit Datensätzen in der App, wählen Sie den Pfeil rechts neben **Nach Excel exportieren** aus, und wählen Sie dann **Dynamische PivotTable** aus.  
  
2. Wählen Sie im Dialogfeld **Spalten für Navigationssteuerung in Excel auswählen** die Spalteneinstellungen, und klicken Sie auf **Exportieren**.  
  
   Standardmäßig enthält die **PivotTable-Feldliste** nur Felder, die in der Liste **Spalten für Navigationssteuerung in Excel auswählen** angezeigt werden.  
  
3. Wählen Sie **Speichern** aus, und speichern Sie die Datei im XLSX-Format. Notieren Sie sich den Speicherort der Datei.  
  
   > [!NOTE]
   > Wenn Sie die Datendatei später bearbeiten möchten, empfiehlt es sich, die Datei zu speichern, bevor Sie sie öffnen. Andernfalls wird möglicherweise diese Fehlermeldung angezeigt: **Excel kann keine weiteren Dateien öffnen oder speichern, da nicht genügend Arbeitsspeicher oder Festplattenspeicherplatz vorhanden ist.**  
   > 
   > So beheben Sie das Problem:  
   > 
   > 1. Öffnen Sie Excel, und wechseln Sie zu **Datei** > **Optionen** > **Trust Center**.  
   > 2. Wählen Sie **Einstellungen für das Trust Center** und dann **Geschützte Ansicht** aus.  
   > 3. Deaktivieren Sie unter **Geschützte Ansicht** die Kontrollkästchen für alle drei Elemente.  
   > 4. Klicken Sie auf **OK** > **OK**.  
   > 
   > Es wird jedoch dringend empfohlen, die Datendatei zu speichern und dann zu öffnen, anstatt die geschützte Ansicht zu deaktivieren und Ihren Computer so Risiken auszusetzen.  
  
4. Öffnen Sie Excel und dann die XLSX-Datei, die Sie im vorherigen Schritt gespeichert haben.  
  
5. Wenn die Sicherheitswarnung **Externe Datenverbindungen wurden deaktiviert.** angezeigt wird, klicken Sie auf **Inhalt aktivieren**.  
  
6. Klicken Sie auf der Registerkarte **Daten** auf **Refresh from Power Apps** (Über Power Apps aktualisieren), um die Daten in der Datei zu aktualisieren.  
  
7. Ziehen Sie die Felder aus der PivotTable-Feldliste auf die PivotTable. Weitere Informationen finden Sie in der Excel-Hilfe.  
  
## <a name="tips"></a>Tipps  
  
- In Power Apps werden Währungswerte als Zahlen nach Excel exportiert. Lesen Sie nach dem Abschluss des Exports das Excel-Hilfethema „Anzeigen von Zahlen als Währung“, um die Daten als Währung zu formatieren.
  
- Die Datums- und Uhrzeitwerte, die in der App angezeigt werden, werden nur als Datum angezeigt, wenn Sie die Datei nach Excel exportieren, aber die Zelle zeigt das Datum und die Uhrzeit an.  
  
- Wenn Sie Änderungen vornehmen und die Datendatei wieder in die App importierten, sind geschützte, berechnete und zusammengesetzte Felder (z. B. „Vollständiger Name“) schreibgeschützt und können nicht in die App importiert werden. Sie können diese Felder in Excel bearbeiten, aber wenn Sie die Daten zurück in die App importieren, werden diese Felder nicht aktualisiert. Wenn Sie diese Felder aktualisieren möchten, z. B. den Namen eines Kontakts, empfiehlt es sich, die Daten über diese Ansicht zu exportieren, sie in Excel zu aktualisieren und wieder in die App zu importieren, um Änderungen vorzunehmen.  
  
 
