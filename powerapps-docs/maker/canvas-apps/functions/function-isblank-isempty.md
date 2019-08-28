---
title: Funktionen „Blank“, „Coalesce“, „IsBlank“ und „IsEmpty“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich von Syntax und Beispielen, für die Funktionen „Blank“, „Coalesce“, „IsBlank“ und „IsEmpty“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.component: canvas
ms.date: 08/27/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fec70eae81568cf2360c3413d878301b3c0dcf0b
ms.sourcegitcommit: 06612108755d386b9df41bd6f45157e94e929511
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70064875"
---
# <a name="blank-coalesce-isblank-and-isempty-functions-in-powerapps"></a>Die Funktionen „Blank“, „Coalesce“, „IsBlank“ und „IsEmpty“ in PowerApps
Prüft, ob ein Wert leer ist oder eine [Tabelle](../working-with-tables.md) keine [Datensätze](../working-with-tables.md#records) enthält, und stellt ein Verfahren zum Erstellen von *leeren* Werten zur Verfügung.

## <a name="overview"></a>Übersicht
*Blank* ist ein Platzhalter für "no value" (kein Wert) oder "unknown value" (unbekannter Wert).  Beispielsweise ist die **ausgewählte** Eigenschaft eines Kombinations **[Feld](../controls/control-combo-box.md)** -Steuer Elements *leer* , wenn der Benutzer keine Auswahl getroffen hat. Viele Datenquellen können NULL-Werte speichern und zurückgeben, die in powerapps als *leer*dargestellt werden.

Jede Eigenschaft oder der berechnete Wert in powerapps kann *leer*sein.  Ein boolescher Wert weist normalerweise einen von zwei Werten auf: **TRUE** oder **FALSE**.  Zusätzlich zu diesen beiden kann Sie auch *leer* sein, um anzugeben, dass der Status nicht bekannt ist.  Dies ist vergleichbar mit Microsoft Excel, bei dem eine Arbeitsblatt Zelle leer ist, ohne Inhalte, aber die Werte **true** oder **false** (u.a.) enthalten kann. Der Inhalt der Zelle kann jederzeit gelöscht und in einen *leeren* Zustand zurückversetzt werden.

Eine *leere Zeichenfolge* verweist auf eine Zeichenfolge, die keine Zeichen enthält.  Die [ **len** -Funktion](function-len.md) gibt 0 (null) für eine solche Zeichenfolge zurück, und Sie kann in Formeln als zwei doppelte Anführungs `""`Zeichen geschrieben werden, wobei nichts dazwischen liegt.  Einige Steuerelemente und Datenquellen verwenden eine leere Zeichenfolge, um die Bedingung "kein Wert" anzugeben.  Um die Erstellung von apps zu vereinfachen, testen die Funktionen " **isblank** " und " **COALESCE** " sowohl *leere* als auch leere Zeichen folgen.    

Im Kontext der **IsEmpty** -Funktion ist *empty* spezifisch für Tabellen, die keine Datensätze enthalten. Die Tabellenstruktur ist möglicherweise mit [Spaltennamen](../working-with-tables.md#columns) intakt, enthält jedoch keine Werte. Eine Tabelle kann zunächst leer sein, Datensätzen aufnehmen und dann nicht mehr leer sein, und dann erneut leer sein, wenn die Datensätze entfernt werden.

> [!NOTE]
> Wir befinden uns in einem Übergangszeitraum.  Bis jetzt wurde *blank* auch zum Melden von Fehlern verwendet, sodass kein gültiger "No Value" von einem Fehler unterschieden werden kann.  Aus diesem Grund wird das Speichern von *leeren* Werten nur für lokale Sammlungen unterstützt.  Sie können *leere* Werte in anderen Datenquellen speichern, wenn Sie die experimentelle Funktion "Fehler Verwaltung auf Formel Ebene" im Menü "Datei", "App-Einstellungen", "Erweiterte Einstellungen" und "experimentelle Features" aktivieren.  Wir arbeiten aktiv daran, diese Funktion abzuschließen und die ordnungsgemäße Trennung von *leeren* Werten von Fehlern abzuschließen.

## <a name="description"></a>Beschreibung
Die Funktion **Blank** gibt einen *leeren* Wert zurück. Sie können sie verwenden, um einen NULL-Wert in einer Datenquelle zu speichern, die diese Werte unterstützt, wodurch effektiv jeder Wert aus dem Feld entfernt wird.

Die **isblank** -Funktion testet auf einen *leeren* Wert oder eine leere Zeichenfolge.  Der Test enthält leere Zeichen folgen, um die APP-Erstellung zu vereinfachen, da einige Datenquellen und Steuerelemente eine leere Zeichenfolge verwenden, wenn kein Wert vorhanden ist.  Verwenden`if( Value = Blank(), ...` Sie anstelle von **isblank**, um speziell auf einen *leeren* Wert zu testen.

Die **COALESCE** -Funktion wertet ihre Argumente in der richtigen Reihenfolge aus und gibt den ersten Wert zurück, der nicht *leer* oder eine leere Zeichenfolge ist.  Verwenden Sie diese Funktion, um einen *leeren* Wert oder eine leere Zeichenfolge durch einen anderen Wert zu ersetzen, aber nicht*leere* und nicht leere Zeichen folgen Werte unverändert zu lassen.  Wenn alle Argumente *leer* oder leere Zeichen folgen sind, gibt die Funktion *blank*zurück, sodass **COALESCE** eine gute Möglichkeit zum Konvertieren leerer Zeichen folgen in *leere* Werte ist.  Alle Argumente von **Coalesce** müssen vom selben Typ sein; es können nicht Zahlen und Textzeichenfolgen gleichzeitig angegeben werden.  

`Coalesce( value1, value2 )`ist die präzisere Entsprechung `If( Not IsBlank( value1 ), value1, Not IsBlank( value2 ), value2 )` von und erfordert nicht, dass **value1** und **value2** zweimal ausgewertet werden.  Die [ **if** -Funktion](function-if.md) gibt " *blank* " zurück, wenn keine else-Formel vorhanden ist, wie es hier der Fall ist.

Die **IsEmpty**-Funktion prüft, ob eine Tabelle keine Datensätze enthält. Dies entspricht dem Einsatz der **[CountRows](function-table-counts.md)** -Funktion und dem Prüfen auf 0. Sie können nach Fehlern in Datenquellen suchen, indem Sie **IsEmpty** mit der **[Errors](function-errors.md)** -Funktion kombinieren.

Der Rückgabewert für die beiden Funktionen **IsBlank** und **IsEmpty** ist ein Boolescher Wert **WAHR** oder **FALSCH**.

## <a name="syntax"></a>Syntax
**Blank**()

**Coalesce**( *Wert1* [, *Wert2*, ... ] )

* *Wert(e)* – Erforderlich. Die zu testenden Werte.  Jeder Wert wird in der Reihenfolge ausgewertet, bis ein Wert, der nicht *leer* ist, und keine leere Zeichenfolge gefunden wird.  Werte nach diesem Punkt werden nicht ausgewertet.  

**IsBlank**( *Value* )

* *Wert*: Erforderlich. Wert, der auf einen *leeren* Wert oder eine leere Zeichenfolge getestet werden soll.

**IsEmpty**( *Table* )

* *Tabelle* (erforderlich): Tabelle, die auf Datensätze geprüft werden soll

## <a name="examples"></a>Beispiele
### <a name="blank"></a>Blank
> [!NOTE]
> Aktuell funktioniert das folgende Beispiel nur mit lokalen Sammlungen.  Sie können *leere* Werte in anderen Datenquellen speichern, wenn Sie die experimentelle Funktion "Fehler Verwaltung auf Formel Ebene" im Menü "Datei", "App-Einstellungen", "Erweiterte Einstellungen" und "experimentelle Features" aktivieren.  Wir arbeiten aktiv daran, diese Funktion abzuschließen und die Trennung *leerer* Werte von Fehlern abzuschließen.

1. Erstellen Sie eine Anwendung von Grund auf, und fügen Sie ein **Schaltfläche**-Steuerelement hinzu.
2. Legen Sie die **[OnSelect](../controls/properties-core.md)** -Eigenschaft auf die folgende Formel fest:

    ```powerapps-dot
    ClearCollect( Cities, { Name: "Seattle", Weather: "Rainy" } )
    ```
3. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die hinzugefügte Schaltfläche, und schließen Sie dann die Vorschau.  
4. Klicken oder tippen Sie im Menü **Datei** auf **Sammlungen**.

     Die Sammlung **Cities** wird angezeigt und enthält einen Datensatz mit „Seattle“ und „Rainy“:

    ![Sammlung, die Seattle bei Regen zeigt](./media/function-isblank-isempty/seattle-rainy.png)
5. Klicken oder tippen Sie auf den Rückwärtspfeil, um zum Standardarbeitsbereich zurückzukehren.
6. Fügen Sie ein **Label**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **Text**-Eigenschaft auf diese Formel fest:

    ```powerapps-dot
    IsBlank( First( Cities ).Weather )
    ```

    Die Bezeichnung zeigt **FALSCH** an, da das Feld **Weather** einen Wert („Rainy“) enthält.
7. Fügen Sie eine zweite Schaltfläche hinzu, und legen Sie ihre **OnSelect**-Eigenschaft auf diese Formel fest:

    ```powerapps-dot
    Patch( Cities, First( Cities ), { Weather: Blank() } )
    ```
8. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die hinzugefügte Schaltfläche, und schließen Sie dann die Vorschau.  

    Das Feld **Weather** des ersten Datensatzes in **Cities** wird durch ein *leeres* Element ersetzt, wodurch der vorherige Wert „Rainy“ entfernt wird.

    ![Sammlung, die Seattle mit einem leeren Feld „Weather“ enthält](./media/function-isblank-isempty/seattle-blank.png)

    Die Bezeichnung zeigt **WAHR** an, da das Feld **Weather** keinen Wert mehr enthält.

### <a name="coalesce"></a>Coalesce

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **COALESCE (&nbsp;Blank (),&nbsp;1&nbsp;)** |Prüft den Rückgabewert der Funktion **Blank**, die immer einen *leeren* Wert zurückgibt. Da das erste Argument *leer*ist, wird die Auswertung mit dem nächsten Argument fortgesetzt, bis ein nicht leerer Wert und eine nicht leere Zeichenfolge gefunden wird. |**1** |
| **COALESCE ("", 2)** |Testet das erste Argument, das eine leere Zeichenfolge ist. Da das erste Argument eine leere Zeichenfolge ist, wird die Auswertung mit dem nächsten Argument fortgesetzt , bis ein nicht leerer Wert und eine nicht leere Zeichenfolge gefunden werden. |**2** |
| **COALESCE (Blank (), "", Blank (), "", 3, 4)** |**COALESCE** beginnt am Anfang der Argumentliste und wertet jedes Argument nacheinander aus, bis ein nicht leerer Wert und eine nicht leere Zeichenfolge gefunden werden.  In diesem Fall geben die ersten vier Argumente " *blank* " oder eine leere Zeichenfolge zurück, sodass die Auswertung mit dem fünften Argument fortgesetzt wird. Das fünfte Argument ist nicht*leer* und keine leere Zeichenfolge. die Auswertung wird daher hier angehalten. Der Wert des fünften Arguments wird zurückgegeben, und das sechste Argument wird nicht ausgewertet. |**3** |
| **COALESCE ("")** | Testet das erste Argument, das eine leere Zeichenfolge ist. Da das erste Argument eine leere Zeichenfolge ist und keine weiteren Argumente vorhanden sind, gibt die Funktion *blank*zurück.   |*blank* |

### <a name="isblank"></a>IsBlank
1. Erstellen Sie eine App von Grund auf, fügen Sie ein Texteingabe-Steuerelement hinzu, und benennen Sie es **FirstName**.
2. Fügen Sie eine Bezeichnung hinzu, und legen Sie deren Eigenschaft **[Text](../controls/properties-core.md)** auf diese Funktion fest:

    ```powerapps-dot
    If( IsBlank( FirstName.Text ), "First Name is a required field." )
    ```

    Standardmäßig ist die Eigenschaft **[Text](../controls/properties-core.md)** eines Texteingabe-Steuerelements auf **„Texteingabe“** festgelegt. Da die Eigenschaft einen Wert enthält, ist sie nicht leer, und die Bezeichnung zeigt keinerlei Nachricht an.
3. Entfernen Sie alle Zeichen aus dem Texteingabe-Steuerelement, einschließlich Leerzeichen.

    Da die **[Text](../controls/properties-core.md)** -Eigenschaft keine Zeichen mehr enthält, handelt es sich um eine leere Zeichenfolge, und **isblank (FirstName. Text)** ist **true**. Die Meldung für ein erforderliches Feld wird angezeigt.

Informationen für die Validierung mithilfe anderer Tools finden Sie bei der Funktion **[Validate](function-validate.md)** und unter [Arbeiten mit Datenquellen](../working-with-data-sources.md).  

Weitere Beispiele:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Isblank (&nbsp;leer ()&nbsp;)** |Prüft den Rückgabewert der Funktion **Blank**, die immer einen *leeren* Wert zurückgibt. |**TRUE** |
| **IsBlank( "" )** |Eine Zeichenfolge, die keine Zeichen enthält |**TRUE** |
| **IsBlank ("Hello")** |Eine Zeichenfolge, die ein oder mehrere Zeichen enthält |**FALSE** |
| **IsBlank ( *AnyCollection* )** |Da die [Sammlung](../working-with-data-sources.md#collections) vorhanden ist, ist sie nicht leer, auch wenn sie keine Datensätze enthält. Verwenden Sie stattdessen zum Überprüfen auf eine leeren Sammlung **IsEmpty**. |**FALSE** |
| **IsBlank( Mid( "Hello", 17, 2 ) )** |Das Anfangszeichen für **[Mid](function-left-mid-right.md)** befindet sich hinter dem Ende der Zeichenfolge.  Das Ergebnis ist eine leere Zeichenfolge. |**TRUE** |
| **IsBlank( If( false, false ) )** |Eine **[If](function-if.md)** -Funktion ohne *ElseResult*.  Da die Bedingung immer **FALSE** ist, gibt diese **[If](function-if.md)** -Funktion immer *blank* zurück. |**TRUE** |

### <a name="isempty"></a>IsEmpty
1. Erstellen Sie eine Anwendung von Grund auf, und fügen Sie ein **Schaltfläche**-Steuerelement hinzu.
2. Legen Sie die **[OnSelect](../controls/properties-core.md)** -Eigenschaft auf die folgende Formel fest:

    **Collect (icecream, {Flavor: "Erdbeer", Menge: 300}, {Flavor: "Chocolate", Menge: 100})**
3. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die hinzugefügte Schaltfläche, und schließen Sie dann die Vorschau.  

    Eine Sammlung mit dem Namen **IceCream** wird erstellt und enthält diese Daten:

    ![](media/function-isblank-isempty/icecream-strawberry-chocolate.png)

    Diese Sammlung verfügt über zwei Datensätze und ist nicht leer. **IsEmpty( IceCream )** gibt **FALSE** zurück, und **CountRows( IceCream )** gibt **2** zurück.
4. Fügen Sie eine zweite Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](../controls/properties-core.md)** auf diese Formel fest:

    **Clear( IceCream )**
5. Führen Sie eine Vorschau Ihrer App aus, klicken oder tippen Sie auf die zweite Schaltfläche, und schließen Sie dann die Vorschau.  

    Die Sammlung ist jetzt leer:

    ![](media/function-isblank-isempty/icecream-clear.png)

    Die **[Clear](function-clear-collect-clearcollect.md)** -Funktion entfernt alle Datensätze aus einer Sammlung, woraus sich eine leere Sammlung ergibt. **IsEmpty( IceCream )** gibt **TRUE** und **CountRows( IceCream )** gibt **0** zurück.

Sie können auch **IsEmpty** verwenden, um zu prüfen, ob eine berechnete Tabelle leer ist, wie diese Beispiele zeigen:

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **IsEmpty( [&nbsp;1,&nbsp;2,&nbsp;3 ] )** |Die einspaltige Tabelle enthält drei Datensätze und ist daher nicht leer. |**FALSE** |
| **IsEmpty( [&nbsp;] )** |Die einspaltige Tabelle enthält keine Datensätze und ist leer. |**TRUE** |
| **IsEmpty( Filter( [&nbsp;1,&nbsp;2,&nbsp;3&nbsp;], Value > 5 ) )** |Die einspaltige Tabelle enthält keine Werte, die größer als 5 sind.  Das Ergebnis des Filters enthält keine Datensätze und ist leer. |**TRUE** |

