---
title: Exportieren in ein dynamisches Excel-Arbeitsblatt in Modell gesteuerten powerapps | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733245"
---
# <a name="export-to-an-excel-dynamic-worksheet"></a>Exportieren in ein dynamisches Excel-Arbeitsblatt

Exportieren Sie Ihre APP-Daten in ein Office Excel-Arbeitsblatt, damit Benutzer die neuesten Informationen erhalten können. Stellen Sie sich vor, dass der CEO Ihres Unternehmens wichtige Informationen erhält, die Sie benötigen, ohne in einer APP navigieren zu müssen, sondern lediglich den Excel-Link auf dem Desktop öffnen. Sie können bis zu 100.000 Datensätze gleichzeitig exportieren.    
  
## <a name="export-data-to-an-excel-dynamic-worksheet"></a>Exportieren von Daten in ein dynamisches Excel-Arbeitsblatt  

Sie können Daten nicht für alle Daten Satz Typen in ein dynamisches Arbeitsblatt in Excel exportieren. Wenn die Option nicht angezeigt wird, ist Sie für diesen Datensatz nicht verfügbar.  
  
1. Öffnen Sie eine Liste der Datensätze in der APP, und wählen Sie den Pfeil rechts neben **Export in Excel**aus. 
  
2. Wählen Sie **dynamisches Arbeitsblatt**aus.  
  
3. Wählen Sie im Dialogfeld **Spalten für dynamisches Excel auswählen** die Spalten Einstellungen aus, und wählen Sie dann **exportieren**aus.  
  
4. Wählen Sie **Speichern** aus, und speichern Sie die XLSX-Datei. Notieren Sie sich den Speicherort, an dem Sie die Datei gespeichert haben.  
  
   > [!NOTE]
   > Wenn Sie die Datendatei später bearbeiten möchten, empfiehlt es sich, die Datei zu speichern, bevor Sie Sie öffnen. Andernfalls erhalten Sie möglicherweise die folgende Fehlermeldung: **Excel kann keine weiteren Dokumente öffnen oder speichern, da nicht genügend Arbeitsspeicher oder Speicherplatz verfügbar ist.**  
   > 
   > So beheben Sie das Problem:  
   > 
   >    1. Öffnen Sie Excel, und wechseln Sie zu **Datei** > **Optionen** > **Trust Center** **Einstellungen Center Einstellungen** > **geschützte Ansicht**.  
   >    2. Löschen Sie in der **geschützten Ansicht**alle drei Elemente.  
   >    3. Klicken Sie auf **OK** > **OK**.  
   >     
   >    Es wird weiterhin dringend empfohlen, die Datendatei zu speichern und dann zu öffnen, anstatt die geschützte Ansicht zu deaktivieren, was möglicherweise zu einem Risiko für Ihren Computer wird.  
  
5. Öffnen Sie Excel, und öffnen Sie dann die XLSX-Datei, die Sie im vorherigen Schritt gespeichert haben.  
  
6. Wenn die Sicherheitswarnung **externe Datenverbindungen deaktiviert**angezeigt wird, wählen Sie **Inhalt aktivieren**aus.  
  
7. Wählen Sie zum Aktualisieren der Daten in der Datei auf der Registerkarte **Daten** in **powerapps die Option aktualisieren aus**.  
  
   > [!NOTE]
   > Wenn Sie eine Telefonnummer haben, die mit **+** oder **–** beginnt (z. b. + 1-123-456-7890), wird das Feld für die Telefonnummer beim Aktualisieren des dynamischen Arbeitsblatts nicht ordnungsgemäß angezeigt.   
   >
   > Um das Problem zu vermeiden, verwenden Sie ein Leerzeichen oder Klammern **()** wie folgt: + 1 123-456-7890 oder + 1 (123)-456-7890.  
  
## <a name="tips"></a>Tipps  
  
- Sie können eine dynamische Excel-Datei per e-Mail senden oder als freigegebene Datei speichern, wenn sich die Empfänger in derselben Domäne befinden. Wenn Empfänger die dynamische Datei öffnen, sehen Sie, dass Sie über die Berechtigung zum Anzeigen von Daten in der App verfügen, sodass sich die Daten, die Sie sehen, möglicherweise von der Anzeige unterscheiden.  
  
- Einige System Sichten, wie z. b. Konten: keine Kampagnenaktivitäten in den letzten drei Monaten, können nur in ein statisches Excel-Arbeitsblatt exportiert werden.  
  
- In powerapps werden Währungswerte als Zahlen nach Excel exportiert. Wenn Sie die Daten nach Abschluss des Exports als Währung formatieren möchten, lesen Sie das Excel-Hilfethema "Anzeigen von Zahlen als Währung".

- Die Datums-und Uhrzeitwerte, die in der App angezeigt werden, werden nur als Datum angezeigt, wenn Sie die Datei nach Excel exportieren, aber die Zelle zeigt das Datum und die Uhrzeit an.  
  
- Wenn Sie Änderungen vornehmen und die Datendatei wieder in die App importieren möchten, sollten Sie daran denken, dass gesicherte, berechnete und zusammengesetzte Felder (z. b. vollständiger Name) schreibgeschützt sind und nicht in die app importiert werden können. Sie können diese Felder in Excel bearbeiten, aber wenn Sie die Daten zurück in die App importieren, werden diese Felder nicht aktualisiert. Wenn Sie diese Felder aktualisieren möchten, z. b. den Namen eines Kontakts, empfiehlt es sich, diese Ansicht zu verwenden, um die Daten zu exportieren, Sie in Excel zu aktualisieren und für Änderungen wieder in die APP zu importieren.  
 

