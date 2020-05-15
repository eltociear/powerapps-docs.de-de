---
title: Exportieren in ein dynamisches Excel-Arbeitsblatts aus einer modellgesteuerten Power Apps-App | Microsoft-Dokumentation
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
ms.openlocfilehash: 99aa4fb38311d51237abba2c56d69e9845ea280f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302861"
---
# <a name="export-to-an-excel-dynamic-worksheet"></a>In eine dynamische Excel-Tabelle exportieren

Exportieren Sie Ihre App-Daten in ein Office Excel-Arbeitsblatt, damit alle Benutzer auf die aktuellen Informationen zugreifen können. Stellen Sie sich vor, der CEO Ihres Unternehmens könnte an wichtige Informationen gelangen, ohne in einer App navigieren zu müssen, sondern indem dieser einfach eine Excel-Verknüpfung auf dem Desktop öffnet. Sie können bis zu 100.000 Datensätze gleichzeitig exportieren.    
  
## <a name="export-data-to-an-excel-dynamic-worksheet"></a>Exportieren von Daten in ein dynamisches Excel-Arbeitsblatt  

Sie können Daten nicht für alle Datensatztypen in ein dynamisches Arbeitsblatt in Excel exportieren. Wenn die Option nicht angezeigt wird, ist sie für den betreffenden Datensatz nicht verfügbar.  
  
1. Öffnen Sie eine Datensatzliste in der App, und klicken Sie auf den Pfeil rechts neben **In Excel exportieren**. 
  
2. Wählen Sie **Dynamisches Arbeitsblatt** aus.  
  
3. Wählen Sie im Dialogfeld **Spalten für dynamisches Excel auswählen** die Spalteneinstellungen, und klicken Sie auf **Exportieren**.  
  
4. Wählen Sie **Speichern** aus, und speichern Sie die XLSX-Datei. Notieren Sie den Speicherort, an dem Sie die Datei gespeichert haben.  
  
   > [!NOTE]
   > Wenn Sie die Datendatei später bearbeiten möchten, empfiehlt es sich, die Datei zu speichern, bevor Sie sie öffnen. Andernfalls erhalten Sie möglicherweise die Fehlermeldung: **Excel kann keine weiteren Dokumente mehr öffnen, da nicht genügend Speicherplatz vorhanden ist.**  
   > 
   > So beheben Sie das Problem:  
   > 
   >    1. Öffnen Sie Excel, und navigieren Sie zu **Datei** > **Optionen** > **Trust Center** >**Center-Einstellungen** > **Geschützte Ansicht**.  
   >    2. Deaktivieren Sie unter **Geschützte Ansicht** alle drei Optionen.  
   >    3. Klicken Sie auf **OK** > **OK**.  
   >     
   >    Es wird jedoch dringend empfohlen, die Datendatei zu speichern und dann zu öffnen, anstatt die geschützte Ansicht zu deaktivieren und Ihren Computer so Risiken auszusetzen.  
  
5. Öffnen Sie Excel und dann die XLSX-Datei, die Sie im vorherigen Schritt gespeichert haben.  
  
6. Wenn die Sicherheitswarnung **Externe Datenverbindungen wurden deaktiviert** angezeigt wird, wählen Sie **Inhalt aktivieren** aus.  
  
7. Wählen Sie zum Aktualisieren der Daten in der Datei unter der Registerkarte **Daten** die Option **Aus Power Apps aktualisieren** aus.  
  
   > [!NOTE]
   > Wenn Ihre Telefonnummer mit **+** oder **–** beginnt (z. B. +1-123-456-7890), wird diese im Feld „Telefonnummer“ nicht richtig angezeigt, wenn Sie das dynamische Arbeitsblatt aktualisieren.   
   >
   > Dieses Problem können Sie vermeiden, indem Sie ein Leerzeichen oder Klammern **()** verwenden: +1 123-456-7890 oder +1 (123)-456-7890.  
  
## <a name="tips"></a>Tipps  
  
- Sie können eine dynamische Excel-Datei per E-Mail versenden oder diese als freigegebene Datei speichern, wenn die Empfänger sich in derselben Domäne befinden. Wenn Empfänger die dynamische Datei öffnen, werden ihnen die Daten angezeigt, für die sie in der App die Berechtigung besitzen. Es ist also möglich, dass diesen andere Daten angezeigt werden als Ihnen.  
  
- Einige Ansichten, z. B. "Firmen: Keine Kampagnenaktivitäten in den letzten 3 Mon.", können nur in eine statische Excel-Tabelle exportiert werden.  
  
- In Power Apps werden Geldbeträge als Zahlen nach Excel exportiert. Weitere Informationen zum Formatieren von Daten als Währung nach dem Export finden Sie im Excel-Hilfeartikel „Anzeigen von Zahlen als Währung“.

- Die Datums- und Uhrzeitwerte, die in der App angezeigt werden, werden nur als Datum angezeigt, wenn Sie die Datei nach Excel exportieren, aber die Zelle zeigt das Datum und die Uhrzeit an.  
  
- Wenn Sie Änderungen vornehmen und die Datendatei wieder in die App importierten, sind geschützte, berechnete und zusammengesetzte Felder (z. B. „Vollständiger Name“) schreibgeschützt und können nicht in die App importiert werden. Sie können diese Felder in Excel bearbeiten, aber wenn Sie die Daten zurück in die App importieren, werden diese Felder nicht aktualisiert. Wenn Sie diese Felder aktualisieren möchten, z. B. den Namen eines Kontakts, empfiehlt es sich, die Daten über diese Ansicht zu exportieren, sie in Excel zu aktualisieren und wieder in die App zu importieren, um Änderungen vorzunehmen.  
 

