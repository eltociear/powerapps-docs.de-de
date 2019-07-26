---
title: Exportieren in eine Excel-PivotTables in einer Modell gesteuerten PowerApp | MicrosoftDocs
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
ms.openlocfilehash: 90cf377f10a99dbcece1e5f556cb50e678099744
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544980"
---
# <a name="export-to-an-excel-pivottable"></a>Exportieren in eine Excel-PivotTable


Sie können APP-Daten in eine Office Excel-Pivottabelle exportieren, um Muster und Trends in den Daten anzuzeigen. Eine Excel-PivotTables ist eine großartige Möglichkeit, Ihre APP-Daten zusammenzufassen, zu analysieren, zu untersuchen und darzustellen. Sie können bis zu 100.000 Datensätze gleichzeitig exportieren.  
  

## <a name="export-data-to-an-excel-pivottable"></a>Exportieren von Daten in eine Excel-PivotTables  
Die Option zum Exportieren von Daten in eine Excel-pivottyp ist nicht in allen Daten Satz Typen verfügbar. Wenn die Option nicht angezeigt wird, ist Sie für diesen Datensatz nicht verfügbar.  
  
1. Öffnen Sie eine Liste der Datensätze in der APP, wählen Sie den Pfeil rechts neben **nach Excel exportieren**aus, und wählen Sie dann **dynamische**pivotberechtigung aus.  
  
2. Wählen Sie im Dialogfeld **Spalten für pivotpivot auswählen** die Spalten Einstellungen aus, und wählen Sie dann **exportieren**aus.  
  
   Standardmäßig enthält die **PivotTables-Feldliste** nur Felder, die in der Liste **Spalten auswählen für** pivotexcel angezeigt werden.  
  
3. Wählen Sie **Speichern** aus, und speichern Sie die XLSX-Datei. Notieren Sie sich den Speicherort, an dem Sie die Datei gespeichert haben.  
  
   > [!NOTE]
   > Wenn Sie die Datendatei später bearbeiten möchten, empfiehlt es sich, die Datei zu speichern, bevor Sie Sie öffnen. Andernfalls erhalten Sie möglicherweise die folgende Fehlermeldung: **Excel kann keine weiteren Dokumente öffnen oder speichern, da nicht genügend Arbeitsspeicher oder Speicherplatz verfügbar ist.**  
   > 
   > So beheben Sie das Problem:  
   > 
   > 1. Öffnen Sie Excel, und wechseln Sie zu **Datei** > **Optionen** > **Trust Center**.  
   > 2. Wählen Sie Einstellungen für das **Trust Center** und dann **geschützte Ansicht**aus.  
   > 3. Deaktivieren Sie unter **geschützte Ansicht**die Kontrollkästchen für alle drei Elemente.  
   > 4. Wählen Sie **OK** > **aus.**  
   > 
   > Es wird weiterhin dringend empfohlen, die Datendatei zu speichern und dann zu öffnen, anstatt die geschützte Ansicht zu deaktivieren, was möglicherweise zu einem Risiko für Ihren Computer wird.  
  
4. Öffnen Sie Excel, und öffnen Sie dann die XLSX-Datei, die Sie im vorherigen Schritt gespeichert haben.  
  
5. Wenn die Sicherheitswarnung **externe Datenverbindungen deaktiviert**angezeigt wird, wählen Sie **Inhalt aktivieren**aus.  
  
6. Wählen Sie zum Aktualisieren der Daten in der Datei auf der Registerkarte **Daten** in **powerapps die Option aktualisieren aus**.  
  
7. Ziehen Sie die Felder aus der PivotTables-Feldliste in die PivotTables. Weitere Informationen finden Sie in der Excel-Hilfe.  
  
## <a name="tips"></a>Tipps  
  
- In powerapps werden Währungswerte als Zahlen nach Excel exportiert. Nachdem Sie den Export durchgeführt haben, lesen Sie das Excel-Hilfethema "Anzeigen von Zahlen als Währung", um die Daten als Währung zu formatieren.
  
- Die Datums-und Uhrzeitwerte, die in der App angezeigt werden, werden nur als Datum angezeigt, wenn Sie die Datei nach Excel exportieren, aber die Zelle zeigt das Datum und die Uhrzeit an.  
  
- Wenn Sie Änderungen vornehmen und die Datendatei wieder in die App importieren möchten, sollten Sie daran denken, dass gesicherte, berechnete und zusammengesetzte Felder (z. b. vollständiger Name) schreibgeschützt sind und nicht in die app importiert werden können. Sie können diese Felder in Excel bearbeiten, aber wenn Sie die Daten zurück in die App importieren, werden diese Felder nicht aktualisiert. Wenn Sie diese Felder aktualisieren möchten, z. b. den Namen eines Kontakts, empfiehlt es sich, diese Ansicht zu verwenden, um die Daten zu exportieren, Sie in Excel zu aktualisieren und für Änderungen wieder in die APP zu importieren.  
  
 
