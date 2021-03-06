---
title: Importieren von Daten in modellgesteuerten Apps | Microsoft-Dokumentation
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
ms.openlocfilehash: 8f1105fc88fe87aabceaa10160b96e2d7299cbe0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302884"
---
# <a name="import-data"></a>Daten importieren

Ob Ihre Daten in einem Tabellenblatt, auf Ihrem Telefon oder in einem E-Mail-Programm gespeichert sind, hier erfahren Sie, wie Sie die Daten in Ihre App importieren. Beispielsweise können Sie die Kontaktliste Ihrer Kunden aus einem Excel-Arbeitsblatt in die App importieren, damit Sie alle Ihre Kundeninformationen an einem zentralen Ort nachverfolgen können.
  
## <a name="step-1-get-your-import-file-ready"></a>Schritt 1: Bereiten Sie Ihre Importdatei vor  
Zunächst exportieren Sie Ihre Daten in eine Excel-Datei. Folgende Dateiformate werden unterstützt:
 - Excel-Arbeitsmappe (.xlsx)
 - Durch Trennzeichen getrennte Werte (.csv)
  
Die maximal zulässige Größe für ZIP-Dateien beträgt 32 MB. Für die anderen Dateiformate beträgt die maximal zulässige Dateigröße 8 MB.  
  
### <a name="export-data-from-an-email-program"></a>Exportieren von Daten aus einem E-Mail-Programm  
  
1.  Exportieren Sie Ihre Daten in eine Datei mit durch Trennzeichen getrennten Werten (CSV).  
  
     Spezifische Anweisungsschritte zum Exportieren von Kontakten aus Ihrem E-Mail-Programm finden Sie, indem Sie die Hilfe des Programms öffnen und nach „Export“ suchen. Suchen Sie nach Themen, die im Titel „Kontakte exportieren“ oder „Exportieren Ihres Adressbuchs“ oder „Export-Assistent“ aufweisen.  
  
2.  Speichern Sie die Datei an einem Ort, wo Sie sie später leicht wiederfinden.  
  
### <a name="export-data-from-a-spreadsheet"></a>Exportieren von Daten aus einem Tabellenblatt  
  
1.  Öffnen Sie die Tabelle.  
  
2.  Bearbeiten Sie ggf. alle Spaltennamen im Tabellenblatt, damit sie genau mit den hier angezeigten entsprechenden Namen übereinstimmen.  
  
    > [!WARNING]
    > Wenn das Tabellenblatt nicht alle aufgeführten Spaltennamen enthält, ist das in Ordnung. Wenn jedoch ein Spaltenname vorhanden ist, muss dieser exakt mit dem entsprechenden Namen in der Liste übereinstimmen, weil der Import sonst nicht funktioniert. Leerzeichen sind erforderlich. Beachten Sie, dass das Wort "E-Mail" einen Bindestrich enthält.  

    |**Spaltenname in Spreadsheet (muss exakt entsprechen)**|
    |---------|
    |Vorname|  
    |Weitere Vornamen|  
    |Nachname|  
    |Telefon (geschäftlich)|  
    |Mobiltelefon|  
    |Position|  
    |Straße geschäftlich|  
    |Ort geschäftlich|  
    |Region geschäftlich|  
    |Postleitzahl geschäftlich|  
    |Land/Region geschäftlich|  
    |E-Mail-Adresse|  
  
3.  Speichern Sie die Datei.  
  
### <a name="export-data-from-your-phone"></a>Exportieren von Daten von Ihrem Mobiltelefon  

Verwenden Sie ein USB-Kabel oder eine App, um Ihre Daten wie Kontakte von Ihrem Mobiltelefon auf Ihren Computer zu exportieren.
  
Spezifische Anweisungsschritte zum Exportieren von Kontakten für die Marke Ihres Telefons finden Sie, indem Sie in Ihrer bevorzugten Suchmaschine (z. B. Bing) nach „Kontakte von meinem Telefon exportieren“ suchen.  
  
Um eine App zu finden, durchsuchen Sie den Online Store Ihres Telefons.  
  
## <a name="step-2-import-the-file"></a>Schritt 2: Importieren Sie die Datei. 
  
1. Wählen Sie auf der Befehlsleiste **Aus Excel importieren** oder **Aus CSV importieren** aus.

   > [!div class="mx-imgBorder"]
   > ![Hauptmenü in Power Apps](media/import.png "Hauptmenü in Power Apps")
  
2. Navigieren Sie zu dem Ordner, in dem Sie die Datei gespeichert haben, die den Export Ihrer Kontakte enthält. Wählen Sie die Datei aus, wählen Sie **Öffnen** aus, und wählen Sie dann **Weiter** aus.  
  
   > [!TIP]
   > Sie können immer nur eine Datei gleichzeitig importieren. Um weitere Dateien zu importieren, führen Sie den Assistenten später noch mal aus.
   
3. Überprüfen Sie den Dateinamen, und stellen Sie sicher, dass die Feld- und Datentrennzeichen richtig sind, indem Sie die Option **Zuordnung überprüfen** verwenden. Wenn alles gut aussieht, wählen Sie **Import fertig stellen** aus.  
 
## <a name="step-3-check-that-the-import-is-successful"></a>Schritt 3: Überprüfen, ob der Import erfolgreich war

Nach Fertigstellung des Assistenten überprüfen Sie Ihre Daten (z. B. die Liste der Kontakte), um sicherzustellen, dass sie richtig importiert wurden.  
  
1. Wechseln Sie aus dem Hauptmenü zu **Kontakte**.
  
2. Scrollen Sie durch die Kontaktliste. Überprüfen Sie, ob jede Person aufgeführt wird, und überprüfen Sie den Inhalt der Felder auf Genauigkeit.

## <a name="import-double-byte-characters"></a>Importieren von Doppelbyte-Zeichen 

Wenn Sie Daten importieren, die Doublebyte-Zeichen für ostasiatische Sprachen enthalten, stellen Sie sicher, dass die Datei als UTF-8-BOM codiert ist. Einfaches UTF-8 ist möglicherweise nicht ausreichend.

1. Öffnen Sie die CSV-Datei mit Visual Studio Code.
2. Klicken Sie unten in der Leiste auf die Bezeichnung **UTF-8-** (Popupfenster wird geöffnet). 
3. Wählen Sie **Mit Codierung speichern** aus. 

Sie können jetzt die UTF-8-BOM-Codierung für diese Datei auswählen.

