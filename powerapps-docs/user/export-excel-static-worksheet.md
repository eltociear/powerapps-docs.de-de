---
title: Exportieren in ein statisches Excel-Arbeitsblatt in einer modellgesteuerten App | Microsoft-Dokumentation
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544819"
---
# <a name="export-to-an-excel-static-worksheet"></a>Exportieren in ein statisches Excel-Arbeitsblatt

Wenn Sie einer Einzelperson, die keinen Zugriff auf Ihre App hat, Informationen über die Daten in Ihrer App präsentieren möchten oder sich Ihre Daten nur selten ändern, erwägen Sie, die Daten in ein statisches Excel-Arbeitsblatt zu exportieren.

Sie können bis zu 100.000 Datensätze gleichzeitig exportieren. Standardmäßig listet eine modellgesteuerte App bis zu 50 Datensätze pro Seite auf. Wählen Sie die Pfeile **Seite** unten in der Liste aus, um zusätzliche Seiten anzuzeigen.  
  
## <a name="export-data-to-an-excel-static-worksheet"></a>Exportieren von Daten in ein statisches Excel-Arbeitsblatt  
Möglicherweise haben Sie die Option, Daten in allen Datensatztypen in ein statisches Excel-Arbeitsblatt zu exportieren. In manchen Fällen kann es sich jedoch um ein Legacyformat handeln, oder die Daten sind nicht so gefiltert, wie sie in der App dargestellt werden.  
  
1. Öffnen Sie eine Liste mit Datensätzen in der App, wählen Sie den Pfeil rechts neben **Nach Excel exportieren** aus, und wählen Sie dann **Statisches Arbeitsblatt (nur Seite)** aus.  
  
2. Standardmäßig enthält ein exportiertes Arbeitsblatt die Felder, die in der Liste angezeigt werden, und verwendet die gleiche Feldreihenfolge, Sortierung und Feldbreite. Um Änderungen an den Spalten in einer Ansicht für die erweiterte Suche vorzunehmen, wählen Sie **Spalten bearbeiten** aus. 
  
3. Wählen Sie **Speichern** aus, und speichern Sie dann die XLSX-Datei. Notieren Sie sich den Speicherort der Datei.  
  
   > [!NOTE]
   > Wenn Sie die Datendatei später bearbeiten möchten, empfiehlt es sich, die Datei zu speichern, bevor Sie sie öffnen. Andernfalls wird möglicherweise diese Fehlermeldung angezeigt: **Excel kann keine weiteren Dateien öffnen oder speichern, da nicht genügend Arbeitsspeicher oder Festplattenspeicherplatz vorhanden ist.**  
   > 
   > So beheben Sie das Problem:  
   > 
   > 1. Öffnen Sie Excel, und navigieren Sie zu **Datei** > **Optionen** > **Trust Center** > **Trust Center-Einstellungen** > **Geschützte Ansicht**.  
   > 2.  Deaktivieren Sie unter **Geschützte Ansicht** alle drei Optionen.  
   > 3.  Klicken Sie auf **OK** > **OK**.  
   > 
   > Es wird jedoch dringend empfohlen, die Datendatei zu speichern und dann zu öffnen, anstatt die geschützte Ansicht zu deaktivieren und Ihren Computer so Risiken auszusetzen.  


4. Öffnen Sie Excel und dann die XLSX-Datei, die Sie im vorherigen Schritt gespeichert haben.  
  
   Standardmäßig enthält ein exportiertes Arbeitsblatt die Felder, die in der Liste angezeigt werden, und verwendet die gleiche Feldreihenfolge, Sortierung und Feldbreite.  
  
## <a name="tips"></a>Tipps  
  
- Sie können ein exportiertes statisches Arbeitsblatt an alle senden oder es in einer freigegebenen Datei speichern. Jede Person, die die Datei öffnet, sieht sämtliche in der Datei enthaltenen Daten.
  
- Die Spalten für die Systemansicht, wie etwa **Alle aktiven Konten**, können nicht geändert werden. Sie müssen entweder die Ansicht anpassen, wofür die Sicherheitsrolle Systemadministrator oder Systemanpasser erforderlich ist, oder die erweiterte Suche verwenden, um Ihre eigene Ansicht auf der Grundlage der aktuellen Ansicht zu erstellen.  
    
- In modellgesteuerten Apps werden Währungswerte als Zahlen nach Excel exportiert. Lesen Sie nach dem Abschluss des Exports das Excel-Hilfethema „Anzeigen von Zahlen als Währung“, um die Daten als Währung zu formatieren.
  
- Die Datums- und Uhrzeitwerte, die in der App angezeigt werden, werden nur als Datum angezeigt, wenn Sie die Datei nach Excel exportieren, aber die Zelle zeigt das Datum und die Uhrzeit an.  
  
- Wenn Sie Änderungen vornehmen und die Datendatei wieder in die App importierten, sind geschützte, berechnete und zusammengesetzte Felder (z. B. „Vollständiger Name“) schreibgeschützt und können nicht in die App importiert werden. Sie können diese Felder in Excel bearbeiten, aber wenn Sie die Daten zurück in die App importieren, werden diese Felder nicht aktualisiert. Wenn Sie diese Felder aktualisieren möchten, z. B. den Namen eines Kontakts, empfiehlt es sich, die Daten über diese Ansicht zu exportieren, sie in Excel zu aktualisieren und wieder in die App zu importieren, um Änderungen vorzunehmen.  
  

