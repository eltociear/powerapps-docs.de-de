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
ms.locfileid: "3302585"
---
# <a name="use-a-screen-reader"></a>Verwenden einer Sprachausgabe 


Über die Sprachausgabe können sehbehinderte Personen oder Personen, die in bestimmten Szenarios zusätzliche Unterstützung (z. B. bei Asthenopie) benötigen, modellgesteuerte Apps selbstständig nutzen. Allgemein verwendete Sprachausgabe wie Narrator, JAWS und NVDA werden unterstützt. 

- [Weitere Informationen zum Arbeiten mit der Microsoft-Sprachausgabe](https://support.microsoft.com/help/22798)
- [Weitere Informationen zum Arbeiten mit JAWS](https://www.freedomscientific.com/Products/Blindness/JawsDocumentation)


- [Weitere Informationen zum Arbeiten mit NVDA](https://www.nvaccess.org/get-help/)


## <a name="basic-tasks-using-a-screen-reader"></a>Grundlegende Aufgaben mit der Sprachausgabe 

### <a name="open-an-app"></a>Öffnen einer App

1.  Verwenden Sie auf der Navigationsleiste die **TAB-TASTE**, um zum Dropdownsteuerelement der App zu wechseln, und drücken Sie die **EINGABETASTE**, um die Siteübersicht zu öffnen.
2.  Drücken Sie die **TAB-TASTE**, bis Sie den Namen der Anwendung hören, die Sie öffnen möchten (z. B. „Sales“). Zum Öffnen der App die **Eingabetaste** drücken.

### <a name="use-scan-mode-in-narrator"></a>Verwenden des Scanmodus in der Sprachausgabe
Sie können den Scanmodus verwenden, um schnell mithilfe der Pfeiltasten und gängiger Tastenkombinationen zu navigieren. In diesem Modus können Sie schnell zu Überschriften, Links, Landmarks, Formularfeldern, Steuerelementen und Tabellen springen. Schalten Sie den Scanmodus ein und aus, indem Sie die **FESTSTELLTASTE+LEERTASTE** drücken. Weitere Informationen: [Verwenden des Scanmodus](https://support.microsoft.com/help/22809/windows-10-narrator-using-scan-mode)

### <a name="find-your-way-around-the-app"></a>Orientierung in der App

#### <a name="navigation-bar"></a>Navigationsleiste
Wenn Sie eine App öffnen, wird auf der linken Seite ein vertikaler Strich mit Unterbereichsymbolen angezeigt. Sie können entweder die **TAB-TASTE** drücken, um durch diese Symbole zu navigieren, bis Sie den Namen des gewünschten Unterbereichs (z. B. „Konten“) hören, oder das Steuerelement für die Siteübersicht nutzen. Drücken Sie beispielsweise die **TAB-TASTE**, bis Sie "Firmen" hören, und drücken Sie dann die **EINGABETASTE**, um die Firmenansicht zu öffnen.

#### <a name="grids"></a>Raster
Sprachausgaben navigieren Raster zuverlässiger und kontinuierlicher und kündigen Zeilen- und Spaltenüberschriften sowie die Positionierung innerhalb des Rasters an. Wenn Sie zuerst ein Raster öffnen, ist die Ansichtsauswahl der Standardtabstopp. 

Wenn Sie von außerhalb des Rasters in eine Zelle innerhalb des Raster klicken, kündigt die Sprachausgabe den Namen der Tabelle die Zeilen-, der und Spaltenanzahlen und die Position des Cursors in der Tabelle an.

Wenn sich der Cursor innerhalb der Tabellenüberschrift befindet, navigieren Sie schnell zwischen Kopfzeilen, indem Sie die **TAB**-Taste oder **UMSCHALT+TAB** verwenden. Die Sprachausgabe kündigt den Namen jeder Kopfzeile an, wenn Sie auf die Kopfzeilenzelle klicken. Es wird auch der Zelltyp (z. B. „Spaltenheader“), die Position der Spalte (z. B. „Spalte 1 von 6“) und eine Angabe, ob die Spalte sortiert oder ausgewählt ist, ausgegeben. Wenn Sie in einem Tabellenheader die **EINGABETASTE** drücken, wird die Tabelle nach dieser Spalte sortiert. Die Sprachausgabe kündigt die Sortierreihenfolge an und Sie können wieder die **EINGABETASTE** drücken, um die Reihenfolge zu ändern.

Wenn Sie die letzte Spalte der Tabelle verlassen, wird der Cursor in die zweite Zeile des Rasters verschoben und ab diesem Punkt müssen Sie die NACH-UNTEN- und NACH-OBEN-TASTEN verwenden, um zwischen den Zellen zu navigieren, die keine Kopfzeilen sind. Wenn Sie stattdessen die **TAB-TASTE** erneut drücken, wird Ihr Cursor auf das folgende interaktive Element verschoben, in der Regel die Tabellenfilterliste. Beim Wechsel zwischen Nicht-Kopfzeilenzeilenzellen kündigt die Sprachausgabe den Spaltennamen, die Position der Spalte und den Text in der Zelle an.

#### <a name="forms"></a>Formulare
Mehrere Navigationsmodi sind zum Navigieren eines Formulars mithilfe der Sprachausgabe verfügbar. Die häufigsten Modi sind Marksteine, Überschriften und Formulare. Wenn Sie den Navigationsmodus ändern möchten, drücken Sie die **FESTSTELLTASTE+NACH-OBEN**. Halten Sie die FESTSTELLTASTE gedrückt, wenn Sie die NACH-OBEN-TASTE drücken, um durch die Modi zu wechseln, bis Sie den Modus hören, den Sie verwenden möchten. Verwenden Sie dann die FESTSTELLTASTE + NACH-LINKS/-RECHTS-TASTEN, um die verschiedenen Elemente zu navigieren. Wenn Sie beispielsweise zum Feld „Nachname“ im Abschnitt „Kontaktinformationen“ eines Kontakts springen möchten, müssen Sie folgendermaßen vorgehen:

1.  Drücken und halten Sie die **FESTSTELLTASTE** und drücken Sie die **NACH-OBEN**-TASTE, bis Sie das Wort "Sehenswürdigkeiten" hören.
2.  Drücken und halten Sie die **FESTSTELLTASTE** und drücken Sie die **NACH-RECHTS**-TASTE, bis Sie das Wort "Kontaktinformationen" hören.
3.  Ändern Sie den Modus, indem Sie die **FESTSTELLTASTE** drücken halten und die **NACH-OBEN**-TASTE drücken, bis Sie das Wort "Formularfelder" hören.
4.  Navigieren Sie zum Nachnamefeld, indem Sie die FESTSTELLTASTE + die NACH-LINKS/-RECHTS-TASTEN drücken, bis Sie das Wort "Nachname" hören. Die Sprachausgabe kündigt auch den Steuerelementtyp, den Wert, den Status und alle speziellen Anweisungen für das Feld an.

Sie können mithilfe der TAB-TASTE auch schnell zu den interaktiven Elementen im Formular navigieren. Einige Formularfelder haben ein Symbol, das die Standardaktion ausführt, wenn Sie STRG+EINGABE drücken. Beispielsweise kann ein E-Mail-Formularfeld ein Umschlagssymbol haben, das einen E-Mail-Editor öffnet. 

#### <a name="dashboardscharts"></a>Dashboards/Diagramme
Sie können mithilfe der TAB-TASTEN und der FESTSTELLTASTE + den PFEILTASTEN zu den Dashboard-Diagrammen navigieren. Drücken Sie die **TAB**-TASTE, um schnell zu den interaktiven Elementen zu wechseln und verwenden SIE die FESTSTELLTASTE + die PFEILTASTEN, um nicht-interaktive Elemente, wie Überschriften, Marksteine und Elemente zu navigieren.


> [!NOTE]
> Das neueste [Windows 10](https://www.microsoft.com/enable/products/windows10/default.aspx)-Update muss installiert sein, um alle Eingabehilfefunktionen für Diagramme nutzen zu können.

#### <a name="interactive-dashboard-streams"></a>Interaktive Dashboardstreams
Sie können die **TAB**-TASTE oder die **UMSCHALT+TAB**-TASTEN verwenden, um zwischen interaktiven Dashboard-Streams, wie im Firmendashboard, zu navigieren oder einfach den Navigationsmodus ändern, bis Sie "Überschriften" hören und dann die **TAB**-TASTE verwenden, um schnell zwischen Dashboard-Streams zu wechseln.

Um zu jedem Element eines Dashboard-Streams zu wechseln, verwenden Sie die NACH-OBEN/-UNTEN-TASTEN. Die Sprachausgabe liest den Typ des Steuerelements und den Titel des Steuerelements vor.

#### <a name="business-process-flows"></a>Geschäftsprozessflüsse
Sie können einen Geschäftsprozessfluss, wie z. B. die im Leadformulars, navigieren, indem Sie die **TAB**-TASTE drücken, um vorwärts zu navigieren, und mit den **UMSCHALT+TAB**-TASTEN rückwärts zu zwichen den Entitäten zu navigieren. Verwenden Sie den **EINGABETASTE** auf der Schaltfläche **Nach links verschieben** oder **Nach rechts verschieben**, um zusätzliche Entitäten im Prozessfluss anzuzeigen. Die Sprachausgabe gibt den Entitätstyp, die Phase, den Status, den Titel, die Anzahl der Elemente im Vergleich zur Gesamtanzahl und eine Angabe aus, ob das Element aktuell ausgewählt ist.

#### <a name="dialog-boxes"></a>Dialogfelder

Wenn ein Dialogfeld geöffnet wird, gibt die Sprachausgabe den Titel aus. Bei Dialogfeldern mit Eingabefeldern ist standardmäßig die Schaltfläche **Schließen** ausgewählt. Dadurch können Sie das Dialogfeld über die **EINGABETASTE** schließen. Bei Dialogfeldern, die eine Benutzeraktion fordern, ist die primäre Aktionsschaltfläche ausgewählt, z. B. **Löschen** oder **OK**.

Sie können mit der **TAB**-TASTE die Steuerelemente navigieren. Der Cursor springt durch die Elemente des Dialogfelds, und Sie können **ESC** drücken, um dieses zu schließen.


