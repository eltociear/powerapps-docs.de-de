---
title: Exportieren in ein statisches Excel-Arbeitsblatt in einer Modell gesteuerten App | MicrosoftDocs
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
ms.openlocfilehash: 82d14f70bbdcd9faddc467636db255f0b512830e
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544819"
---
# <a name="export-to-an-excel-static-worksheet"></a>Exportieren in ein statisches Excel-Arbeitsblatt

Wenn Sie Informationen zu den Daten in Ihrer APP für eine Person darstellen möchten, die keinen Zugriff auf die APP hat, oder wenn Sie über Daten verfügen, die sich nicht häufig ändern, sollten Sie die APP-Daten in ein statisches Office Excel-Arbeitsblatt exportieren.

Sie können bis zu 100.000 Datensätze gleichzeitig exportieren. Standardmäßig listet eine Modell gesteuerte app bis zu 50 Datensätze pro Seite auf. Wählen Sie die **Seiten Pfeile am** unteren Rand der Liste aus, um weitere Seiten anzuzeigen.  
  
## <a name="export-data-to-an-excel-static-worksheet"></a>Exportieren von Daten in ein statisches Excel-Arbeitsblatt  
Möglicherweise haben Sie die Möglichkeit, Daten in ein statisches Excel-Arbeitsblatt in alle Daten Satz Typen zu exportieren. In manchen Fällen ist das Format jedoch möglicherweise veraltet, oder die Daten werden möglicherweise nicht nach dem Inhalt gefiltert, der in der App angezeigt wird.  
  
1. Öffnen Sie eine Liste der Datensätze in der APP, klicken Sie auf den Pfeil rechts neben in **Excel exportieren**, und wählen Sie dann **statisches Arbeitsblatt (nur Seite)** aus.  
  
2. Standardmäßig enthält ein exportiertes Arbeitsblatt die Felder, die in der Liste angezeigt werden, und verwendet dabei die gleiche Feld Reihenfolge, Sortierung und Feldbreite. Wenn Sie Änderungen an den Spalten in einer erweiterten Such Ansicht vornehmen möchten, klicken Sie auf **Spalten bearbeiten**. 
  
3. Wählen Sie **Speichern** aus, und speichern Sie die XLSX-Datei. Notieren Sie sich den Speicherort, an dem Sie die Datei gespeichert haben.  
  
   > [!NOTE]
   > Wenn Sie die Datendatei später bearbeiten möchten, empfiehlt es sich, die Datei zu speichern, bevor Sie Sie öffnen. Andernfalls erhalten Sie möglicherweise die folgende Fehlermeldung: **Excel kann keine weiteren Dokumente öffnen oder speichern, da nicht genügend Arbeitsspeicher oder Speicherplatz verfügbar ist.**  
   > 
   > Gehen Sie wie folgt vor, um das Problem zu beheben:  
   > 
   > 1. Öffnen Sie Excel, und wechseln Sie zu **Datei** > **Optionen** > **Trust Center** > **Einstellungen Center Einstellungen** > **geschützte Ansicht**.  
   > 2.  Löschen Sie in der **geschützten Ansicht**alle drei Elemente.  
   > 3.  Wählen Sie **OK** > **aus.**  
   > 
   > Es wird weiterhin dringend empfohlen, die Datendatei zu speichern und dann zu öffnen, anstatt die geschützte Ansicht zu deaktivieren, was möglicherweise zu einem Risiko für Ihren Computer wird.  


4. Öffnen Sie Excel, und öffnen Sie dann die XLSX-Datei, die Sie im vorherigen Schritt gespeichert haben.  
  
   Standardmäßig enthält ein exportiertes Arbeitsblatt die Felder, die in der Liste angezeigt werden, und verwendet dabei die gleiche Feld Reihenfolge, Sortierung und Feldbreite.  
  
## <a name="tips"></a>Tipps  
  
- Sie können ein statisches exportiertes Arbeitsblatt an beliebige Personen per e-Mail senden oder in einer freigegebenen Datei speichern. Jeder Benutzer, der die Datei öffnet, erhält alle Daten in der Datei.
  
- Die Spalten für eine Systemsicht können nicht geändert werden, z. b. **alle aktiven Konten**. Sie müssen entweder die Ansicht anpassen, die die Sicherheitsrolle "System Administrator" oder "Systembenutzer Name" erfordert, oder die erweiterte Suche verwenden, um eine eigene Ansicht basierend auf der aktuellen Ansicht zu erstellen.  
    
- In Modell gesteuerten apps werden Währungswerte als Zahlen nach Excel exportiert. Wenn Sie den Export abgeschlossen haben, sehen Sie sich das Excel-Hilfethema "Anzeigen von Zahlen als Währung" an, um die Daten als Währung zu formatieren.
  
- Die Datums-und Uhrzeitwerte, die in der App angezeigt werden, werden nur als Datum angezeigt, wenn Sie die Datei nach Excel exportieren, aber die Zelle zeigt das Datum und die Uhrzeit an.  
  
- Wenn Sie Änderungen vornehmen und die Datendatei wieder in die App importieren möchten, sollten Sie daran denken, dass gesicherte, berechnete und zusammengesetzte Felder (z. b. vollständiger Name) schreibgeschützt sind und nicht in die app importiert werden können. Sie können diese Felder in Excel bearbeiten, aber wenn Sie die Daten zurück in die App importieren, werden diese Felder nicht aktualisiert. Wenn Sie diese Felder aktualisieren möchten, z. b. den Namen eines Kontakts, empfiehlt es sich, diese Ansicht zu verwenden, um die Daten zu exportieren, Sie in Excel zu aktualisieren und für Änderungen wieder in die APP zu importieren.  
  

