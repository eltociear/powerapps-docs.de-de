---
title: " Verwenden der Sprachausgabe in modellgesteuerten Apps | Microsoft-Dokumentation"
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
ms.openlocfilehash: c8ef71753fd743788b52b4f3578f829f153c0898
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543452"
---
# <a name="use-a-screen-reader"></a>Verwenden einer Sprachausgabe 


Über die Sprachausgabe können sehbehinderte Personen oder Personen, die in bestimmten Szenarios zusätzliche Unterstützung (z. B. bei Asthenopie) benötigen, modellgesteuerte Apps selbstständig nutzen. Häufig verwendete Sprachausgaben wie die Sprachausgabe von Microsoft, JAWS und NVDA werden unterstützt. 

- [Weitere Informationen zum Arbeiten mit der Sprachausgabe von Microsoft](https://support.microsoft.com/help/22798)
- [Weitere Informationen zum Arbeiten mit JAWS](https://www.freedomscientific.com/Products/Blindness/JawsDocumentation)


- [Weitere Informationen zum Arbeiten mit NVDA](https://www.nvaccess.org/get-help/)


## <a name="basic-tasks-using-a-screen-reader"></a>Grundlegende Aufgaben mit der Sprachausgabe 

### <a name="open-an-app"></a>Öffnen einer App

1.  Verwenden Sie auf der Navigationsleiste die **TAB-TASTE**, um zum Dropdownsteuerelement der App zu wechseln, und drücken Sie die **EINGABETASTE**, um die Siteübersicht zu öffnen.
2.  Drücken Sie die **TAB-TASTE**, bis Sie den Namen der Anwendung hören, die Sie öffnen möchten (z. B. „Sales“). Drücken Sie die **EINGABETASTE**, um die App zu öffnen.

### <a name="use-scan-mode-in-narrator"></a>Verwenden des Scanmodus in der Sprachausgabe
Sie können den Scanmodus verwenden, um schnell mithilfe der Pfeiltasten und gängiger Tastenkombinationen zu navigieren. In diesem Modus können Sie schnell zu Überschriften, Links, Landmarks, Formularfeldern, Steuerelementen und Tabellen springen. Aktivieren oder deaktivieren Sie den Scanmodus, indem Sie **FESTSTELLTASTE+LEERTASTE** drücken. Weitere Informationen: [Verwenden des Scanmodus](https://support.microsoft.com/help/22809/windows-10-narrator-using-scan-mode)

### <a name="find-your-way-around-the-app"></a>Orientierung in der App

#### <a name="navigation-bar"></a>Navigationsleiste
Wenn Sie eine App öffnen, wird auf der linken Seite ein vertikaler Strich mit Unterbereichsymbolen angezeigt. Sie können entweder die **TAB-TASTE** drücken, um durch diese Symbole zu navigieren, bis Sie den Namen des gewünschten Unterbereichs (z. B. „Konten“) hören, oder das Steuerelement für die Siteübersicht nutzen. Drücken Sie beispielsweise die **TAB-TASTE**, bis Sie „Konten“ hören, und drücken Sie dann die **EINGABETASTE**, um die Ansicht „Konten“ zu öffnen.

#### <a name="grids"></a>Raster
Mit der Sprachausgabe können Sie zuverlässiger und konsistenter durch Raster navigieren. Dabei werden Zeilen- und Spaltenüberschriften sowie die Position im Raster ausgegeben. Wenn Sie ein Raster zum ersten Mal öffnen, ist standardmäßig die Ansichtsauswahl ausgewählt. 

Wenn Sie eine Zelle innerhalb des Rasters von außerhalb des Rasters auswählen, gibt die Sprachausgabe den Namen der Tabelle, die Zeilen- und Spaltenanzahl und die Position des Cursors innerhalb der Tabelle aus.

Wenn der Cursor sich innerhalb des Tabellenheaders befindet, können Sie über die **TAB-TASTE** oder **UMSCHALT+TAB-TASTE** schnell zwischen Headern navigieren. Die Sprachausgabe gibt den Namen des Headers aus, wenn Sie die Headerzelle auswählen. Es wird auch der Zelltyp (z. B. „Spaltenheader“), die Position der Spalte (z. B. „Spalte 1 von 6“) und eine Angabe, ob die Spalte sortiert oder ausgewählt ist, ausgegeben. Wenn Sie in einem Tabellenheader die **EINGABETASTE** drücken, wird die Tabelle nach dieser Spalte sortiert. Die Sprachausgabe gibt die Sortierreihenfolge aus, und Sie können die **EINGABETASTE** noch mal drücken, um die Reihenfolge zu ändern.

Wenn Sie aus der letzten Spalte in der Tabelle navigieren, springt der Cursor in die zweite Zeile des Rasters. Von diesem Punkt aus müssen Sie mit den Pfeiltasten nach oben und unten navigieren, um zwischen den Zellen zu wechseln, die nicht zum Header zählen. Wenn Sie stattdessen noch mal die **TAB-TASTE** drücken, springt der Cursor zum nächsten interaktiven Element (üblicherweise zur Tabellenfilterliste). Wenn Sie zwischen Zeilenzellen navigieren, die nicht zum Header zählen, gibt die Sprachausgabe den Spaltennamen, die Position der Spalte und den Zellentext aus.

#### <a name="forms"></a>Formulare
Mehrere Navigationsmodi sind verfügbar, wenn Sie über die Sprachausgabe in einem Formular navigieren. Hierbei sind die gängigsten Modi als Landmarks, Überschriften und Formularfelder vermerkt. Sie können den Navigationsmodus ändern, indem Sie **FESTSTELLTASTE+NACH-OBEN-TASTE** drücken. Halten Sie die FESTSTELLTASTE gedrückt, während Sie auf die NACH-OBEN-TASTE drücken, um die Modi zu durchlaufen, bis Sie den Modus hören, den Sie verwenden möchten. Drücken Sie dann die FESTSTELLTASTE und die NACH-LINKS- oder NACH-RECHTS-TASTE, um durch die verschiedenen Elemente zu navigieren. Wenn Sie beispielsweise zum Feld „Nachname“ im Abschnitt „Kontaktinformationen“ eines Kontakts springen möchten, müssen Sie folgendermaßen vorgehen:

1.  Halten Sie die **FESTSTELLTASTE** gedrückt, und drücken Sie die **NACH-OBEN-TASTE**, bis Sie „Landmarks“ hören.
2.  Halten Sie die **FESTSTELLTASTE** gedrückt, und drücken Sie die **NACH-RECHTS-TASTE**, bis Sie „Kontaktinformationen“ hören.
3.  Sie können den Modus ändern, indem Sie die **FESTSTELLTASTE** gedrückt halten und die **NACH-OBEN-TASTE** drücken, bis Sie „Formularfelder“ hören.
4.  Navigieren Sie zum Feld „Nachname“, indem Sie die FESTSTELLTASTE und die NACH-LINKS- oder NACH-RECHTS-TASTE drücken, bis Sie „Nachname“ hören. Die Sprachausgabe gibt auch den Typ des Steuerelements, den Wert, den Status und besondere Anweisungen für das Feld aus.

Sie können auch mit der TAB-TASTE schnell durch interaktive Formularfelder navigieren. Einige Formularfelder weisen ein Symbol auf, über das die Standardaktion ausgeführt wird, wenn Sie STRG+EINGABETASTE drücken. Bei einem Formularfeld in einer E-Mail kann beispielsweise ein Umschlagsymbol vorhanden sein, das einen E-Mail-Editor öffnet. 

#### <a name="dashboardscharts"></a>Dashboards und Diagramme
Sie können durch die Dashboarddiagramme navigieren, indem Sie die TAB-TASTE und die FESTSTELLTASTE+PFEILTASTEN drücken. Drücken Sie die **TAB-TASTE**, um schnell zu interaktiven Elementen zu navigieren. Drücken Sie dann die FESTSTELLTASTE+PFEILTASTEN, um durch nicht-interaktive Elemente wie Überschriften und Landmarks zu navigieren.


> [!NOTE]
> Sie müssen das aktuelle Update für [Windows 10](https://www.microsoft.com/enable/products/windows10/default.aspx) installiert haben, um alle Barrierefreiheitsfeatures für Diagramme zu nutzen.

#### <a name="interactive-dashboard-streams"></a>Interaktive Dashboardstreams
Sie können die **TAB-TASTE** oder **UMSCHALT+TAB-TASTE** drücken, um zwischen interaktiven Dashboardstreams zu wechseln, die es beispielsweise im Dashboard „Konten“ gibt. Sie können aber auch den Navigationsmodus ändern, bis Sie „Überschriften“ hören und dann die **TAB-TASTE** drücken, um schnell zwischen Dashboardstreams zu wechseln.

Sie können mithilfe der NACH-OBEN- oder NACH-UNTEN-TASTE durch die einzelnen Elemente eines Dashboardstreams navigieren. Die Sprachausgabe gibt den Steuerelementtyp und -titel aus.

#### <a name="business-process-flows"></a>Geschäftsprozessflüsse
Sie können durch einen Geschäftsprozessflow navigieren (z. B. im oberen Bereich des Formulars „Lead“), indem Sie die **TAB-TASTE** drücken, um vorwärts zu springen, und **UMSCHALT+TAB-TASTE**, um rückwärts zwischen Entitäten zu springen. Drücken Sie die **EINGABETASTE** auf der Schaltfläche **Nach links verschieben** oder **Nach rechts verschieben**, um zusätzliche Entitäten im Prozessflow anzuzeigen. Die Sprachausgabe gibt den Entitätstyp, die Phase, den Status, den Titel, die Anzahl der Elemente im Vergleich zur Gesamtanzahl und eine Angabe aus, ob das Element aktuell ausgewählt ist.

#### <a name="dialog-boxes"></a>Dialogfelder

Wenn ein Dialogfeld geöffnet wird, gibt die Sprachausgabe den Titel aus. Bei Dialogfeldern mit Eingabefeldern ist standardmäßig die Schaltfläche **Schließen** ausgewählt. Dadurch können Sie das Dialogfeld über die **EINGABETASTE** schließen. Bei Dialogfeldern, die eine Benutzeraktion fordern, ist die primäre Aktionsschaltfläche ausgewählt, z. B. **Löschen** oder **OK**.

Sie können mit der **TAB-TASTE** durch die Steuerelemente navigieren. Der Cursor springt durch die Elemente des Dialogfelds, und Sie können **ESC** drücken, um dieses zu schließen.


