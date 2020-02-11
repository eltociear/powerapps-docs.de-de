---
title: With-Funktion | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax, für die with-Funktion in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0d1105577459cc447fbd2a14a946ce5651d4d236
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "77089717"
ms.PowerAppsDecimalTransform: true
---
# <a name="with-function-in-power-apps"></a>With-Funktion in powerapps
Berechnet Werte und führt Aktionen für einen einzelnen [Datensatz](../working-with-tables.md#records)aus, einschließlich Inline Datensätze benannter Werte.

## <a name="description"></a>Beschreibung

Die **with** -Funktion wertet eine Formel für einen einzelnen Datensatz aus.  Die Formel kann einen Wert berechnen und/oder Aktionen wie das Ändern von Daten oder das Arbeiten mit einer Verbindung ausführen.  Verwenden Sie die [ **ForAll** -Funktion](function-forall.md) , um eine Formel für alle Datensätze in einer Tabelle mit Datensätzen auszuwerten.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Verwenden Sie **mit** , um die Lesbarkeit komplexer Formeln zu verbessern, indem Sie Sie in kleinere benannte unter Formeln aufteilen.  Diese benannten Werte agieren wie einfache lokale Variablen, die auf den Bereich der **mit**beschränkt sind.  Dieselbe Inline Daten Satz Syntax, die mit der [ **updatecontext** -Funktion](function-updatecontext.md) verwendet wird, kann mit **with**verwendet werden.  Die Verwendung **von mit** wird über Kontext-oder globale Variablen bevorzugt, da Sie eigenständig und leicht verständlich ist und in jedem deklarativen Formel Kontext verwendet werden kann.  

Verwenden Sie **mit** , um auf die Felder des Datensatzes zuzugreifen, die von Funktionen wie z. b. [**Patch**](function-patch.md) oder [**Match**](function-ismatch.md)zurückgegeben werden.  **Mit** enthält den Wert dieser Funktionen lang genug, um in weiteren Berechnungen oder Aktionen verwendet zu werden.  

Wenn das *Datensatz* -Argument für **mit** ein Fehler ist, wird dieser Fehler von der-Funktion zurückgegeben, und die *Formel* wird nicht ausgewertet.

## <a name="syntax"></a>Syntax
**With**( *Datensatz*; *Formel* )

* *Datensatz* – erforderlich. Der Datensatz, auf den die Aktion durchgeführt werden soll.  Verwenden Sie für Namen Werte die Inline Syntax `{ name1: value1; name2: value2; ... }`
* *Formel* – erforderlich.  Die für den *Datensatz*auszuwertende Formel.  Die Formel kann direkt als Daten Satz Bereich auf eines der Felder des *Datensatzes* verweisen.

## <a name="examples"></a>Beispiele

### <a name="simple-named-values"></a>Einfache benannte Werte

```powerapps-comma
With( { radius: 10; 
        height: 15 };
    Pi() * (radius*radius) * height
)
// Result: 4712,38898038 (as shown in a label control)
```

In diesem Beispiel wird ein Datensatz benannter Werte verwendet, um das Volume eines Zylinders zu berechnen.  **Mit** wird verwendet, um alle Eingabewerte zu erfassen, sodass Sie leicht von der Berechnung selbst getrennt werden.  

### <a name="nested-with"></a>Mit

![Interessen Rechner mit with-Funktion](media/function-with/interest-calculator.gif)

```powerapps-comma
With( { AnnualRate: RateSlider/8/100;        // slider moves in 1/8th increments and convert to decimal
        Amount: AmountSlider*10000;          // slider moves by 10;000 increment
        Years: YearsSlider;                  // slider moves in single year increments; no adjustment required
        AnnualPayments: 12 };                // number of payments per year
      With( { r: AnnualRate/AnnualPayments;  // interest rate
              P: Amount;                     // loan amount
              n: Years*AnnualPayments };     // number of payments
            r*P / (1 - (1+r)^-n)             // standard interest calculation
      )
)  
```

In diesem Beispiel wird mit Functions geschachtelt, um eine Berechnung **mit** zwei Ebenen für [monatliche Hypothekenzahlungen](https://en.wikipedia.org/wiki/Mortgage_calculator#Monthly_payment_formula)zu erstellen.  Solange kein Konflikt vorliegt, sind alle äußeren **mit** benannten Werten im inneren **mit**verfügbar.

Da die Schieberegler-Steuerelemente nur in Schritten von 1 verschoben werden können, werden die Schieberegler aufgeteilt oder multipliziert, um ein benutzerdefiniertes Inkrement effektiv zu erstellen.  Im Fall des Zinssatzes ist die **Max** -Eigenschaft des **ratesliders** auf **48**festgelegt, dividiert durch 8 für einen 1/8 Prozentsatz Punkt Inkrement und dividiert durch 100, um von einem Prozentsatz in einen Dezimalwert zu konvertieren, der den Bereich von 0,125% bis 6% abdeckt.  Im Fall des Darlehensbetrags ist die **Max** -Eigenschaft von "" für "" auf **60** und mit 10.000 multipliziert, **wobei der Bereich** 10.000 bis 600.000 abgedeckt wird.

Der **mit** wird automatisch neu berechnet, wenn die Schieberegler verschoben werden und die neue Kreditzahlung angezeigt wird.  Es werden keine Variablen verwendet, und es ist nicht erforderlich, die **OnChange** -Eigenschaft der Schieberegler-Steuerelemente zu verwenden.

Im folgenden finden Sie ausführliche Anweisungen zum Erstellen dieser APP:
1. Erstellen Sie eine neue APP.
2. Fügen Sie ein [ **Schieberegler** -Steuer](../controls/control-slider.md) Element hinzu, und nennen Sie es **rateslider**  Legen Sie die **Max** -Eigenschaft auf 48 fest.
3. Fügen Sie der linken Seite des Schieberegler-Steuer Elements ein [ **Label** -Steuer](../controls/control-text-box.md) Element hinzu.  Legen Sie die **Text** -Eigenschaft auf **"Zinssatz:** " fest.
3. Fügen Sie ein **Label** -Steuerelement rechts neben dem Schieberegler-Steuerelement hinzu.  Legen Sie die **Text** -Eigenschaft auf die Formel **rateslider/8 & "&nbsp;%"** fest.
3. Fügen Sie ein weiteres **Schieberegler** -Steuerelement hinzu, und **nennen Sie es**"".  Legen Sie die **Max** -Eigenschaft auf 60 fest.
3. Fügen Sie links neben diesem Schieberegler-Steuerelement ein **Label** -Steuerelement hinzu.  Legen Sie die **Text** -Eigenschaft auf **"Loan amount:"** fest. 
3. Fügen Sie rechts neben diesem Schieberegler-Steuerelement ein **Label** -Steuerelement hinzu.  Legen Sie die **Text** -Eigenschaft auf die Formel "- **/8 * 10000**" fest.
4. Fügen Sie ein weiteres **Slider** -Steuerelement hinzu, und nennen Sie es **yearsslider**  Legen Sie die **Max** -Eigenschaft auf 40 fest.
3. Fügen Sie links neben diesem Schieberegler-Steuerelement ein **Label** -Steuerelement hinzu.  Legen Sie die **Text** -Eigenschaft auf **"Anzahl von Jahren:"** fest. 
3. Fügen Sie rechts neben diesem Schieberegler-Steuerelement ein **Label** -Steuerelement hinzu.  Legen Sie die **Text** -Eigenschaft auf die Formel **yearsslider**fest.
5. Fügen Sie ein **Label** -Steuerelement hinzu, und legen Sie dessen Eigenschaft **Text** auf die oben gezeigte Formel fest.
3. Fügen Sie links neben dem letzten Label-Steuerelement ein **Label** -Steuerelement hinzu.  Legen Sie die **Text** -Eigenschaft auf **"wiederkehrende monatliche Zahlung:"** fest.  

### <a name="primary-key-returned-from-patch"></a>Vom Patch zurückgegebener Primärschlüssel

```powerapps-comma
With( Patch( Orders; Defaults( Orders ); { OrderStatus: "New" } );
      ForAll( NewOrderDetails; 
              Patch( OrderDetails; Defaults( OrderDetails ); 
                     { Order: OrderID;          // from With's first argument; primary key of Patch result
                       Quantity: Quantity;      // from ForAll's NewOrderDetails table
                       ProductID: ProductID }   // from ForAll's NewOrderDetails table
              )
      )
)
```

In diesem Beispiel wird der **Order** -Tabelle in SQL Server ein Datensatz hinzugefügt.  Anschließend wird der zurückgegebene Primärschlüssel für die Bestellung verwendet, die von der **Patch** -Funktion im **OrderID** -Feld zurückgegeben wird, um verknüpfte Datensätze in der **Order Details** -Tabelle zu erstellen.  

### <a name="extracted-values-with-a-regular-expression"></a>Extrahierte Werte mit regulärem Ausdruck

```powerapps-comma
With( 
    Match( "PT2H1M39S"; "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" );
    Time( Value( hours ); Value( minutes ); Value( seconds ) )
)
// Result: 2:01 AM (as shown in a label control; use the Text function to see the seconds)
```

In diesem Beispiel werden die Stunden, Minuten und Sekunden aus dem Duration-Wert von ISO 8601 extrahiert und dann mithilfe dieser Teil Übereinstimmungen ein Datums-/Uhrzeitwert erstellt. 

Beachten Sie, dass die Teil Übereinstimmungen Zahlen enthalten, die Sie noch in einer Text Zeichenfolge enthalten.  Verwenden Sie die [**value**](function-value.md) -Funktion, um in eine Zahl zu konvertieren, bevor Sie mathematische Operationen ausführen.  

