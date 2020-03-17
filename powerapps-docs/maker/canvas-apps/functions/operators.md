---
title: Operatoren und Bezeichner | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Operatoren und Bezeichner in Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/29/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c7f982f4d2eca1b097a312f74aff70063bf3396
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212674"
ms.PowerAppsDecimalTransform: true
---
# <a name="operators-and-identifiers-in-power-apps"></a>Operatoren und Bezeichner in powerapps

Einige dieser Operatoren sind von der Sprache des Erstellers abhängig.  Weitere Informationen finden Sie unter den Informationen zu [globalen Apps](../global-apps.md).


|                               Symbol                                |                        Typ                         |                                                                                    Syntax                                                                                    |                                                                                                                           Beschreibung                                                                                                                            |
|---------------------------------------------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                **.**                                |                  Eigenschaftsauswahl                  |                                                               **Slider1.Value<br>Color.Red<br>Acceleration.X**                                                               |                                               Extrahiert eine Eigenschaft aus einer [Tabelle](../working-with-tables.md), einem Steuerelement, einem [Signal](signals.md) oder einer Enumeration.  Um die Abwärtskompatibilität sicherzustellen, kann auch **!** verwendet werden.                                                |
| **,**<br>[[sprachabhängig](../global-apps.md)]  |                  Dezimaltrennzeichen                  |                                                             **1.23**                                                           |                                                                              Trennzeichen zwischen dem ganzen Teil und dem Bruchteil einer Zahl. Das Zeichen hängt von der Sprache ab.                                                                              |
|                               **( )**                               |                     Klammern                     |                                                               **Filter(T; A &lt; 10)**<br><br>**(1 + 2) \* 3**                                                               |                                                                                           Erzwingt die Rangfolge und gruppiert Unterausdrücke eines längeren Ausdrucks.                                                                                           |
|                                **+**                                |                Arithmetische operatoren                 |                                                                                  **1+2**                                                                                   |                                                                                                                             Addition                                                                                                                             |
|                                **-**                                |                       &nbsp;                        |                                                                                  **2-1**                                                                                   |                                                                                                                       Subtraktion und Vorzeichen                                                                                                                       |
|                              *                               |                       &nbsp;                        |                                                                                  **2 \* 3**                                                                                  |                                                                                                                          Multiplikation                                                                                                                          |
|                                **/**                                |                       &nbsp;                        |                                                                                  **2/3**                                                                                   |                                                                                                   Division (siehe auch Funktion **[Mod](function-mod.md)**)                                                                                                    |
|                                **^**                                |                       &nbsp;                        |                                                                                  **2^3**                                                                                   |                                                                                          Potenzierung, entspricht der Funktion **[Power](function-numericals.md)**                                                                                          |
|                                **%**                                |                       &nbsp;                        |                                                                                   **20 %**                                                                                    |                                                                                                         Prozentsatz (entspricht &quot;\* 1/100&quot;)                                                                                                          |
|                                **=**                                |                Vergleichsoperatoren                 |                                                                               **Price = 100**                                                                                |                                                                                                                             Gleich                                                                                                                             |
|                              **&gt;**                               |                       &nbsp;                        |                                                                              **Price &gt; 100**                                                                              |                                                                                                                           Größer als                                                                                                                           |
|                              **&gt;=**                              |                       &nbsp;                        |                                                                             **Price &gt;= 100**                                                                              |                                                                                                                     Größer als oder gleich                                                                                                                     |
|                              **&lt;**                               |                       &nbsp;                        |                                                                              **Price &lt; 100**                                                                              |                                                                                                                            Kleiner als                                                                                                                             |
|                              **&lt;=**                              |                       &nbsp;                        |                                                                             **Price &lt;= 100**                                                                              |                                                                                                                      Kleiner als oder gleich                                                                                                                       |
|                            **&lt;&gt;**                             |                       &nbsp;                        |                                                                            **Price &lt;&gt; 100**                                                                            |                                                                                                                           Ungleich                                                                                                                           |
|                              **&amp;**                              |            Operator für Zeichenfolgenverkettung            |                                                      **&quot;Hello&quot; &amp; &quot; &quot; &amp; &quot;Welt&quot;**                                                       |                                                                                                             Verkettet mehrere Zeichenfolgen.                                                                                                             |
|                      **&amp;&amp;** oder **And**                      |                  Logische Operatoren                  |                                       **Price &lt; 100 &amp;&amp; Slider1.Value = 20**<br>oder **Price &lt; 100 And Slider1.Value = 20**                                       |                                                                                         Logische Konjunktion, entspricht der Funktion **[And](function-logicals.md)**                                                                                          |
|                     **&#124;&#124;** oder **Or**                      |                       &nbsp;                        |                                        **Price &lt; 100 &#124;&#124; Slider1.Value = 20** oder **Price &lt; 100 Or Slider1.Value = 20**                                        |                                                                                          Logische Disjunktion, entspricht der Funktion **[Or](function-logicals.md)**                                                                                          |
|                          **!** oder **Not**                           |                       &nbsp;                        |                                                              **!(Price &lt; 100)** oder **Not (Price &lt; 100)**                                                               |                                                                                           Logische Negation, entspricht der Funktion **[Not](function-logicals.md)**                                                                                           |
|                             **exactin**                             |  [Mitgliedschaftsoperatoren](#in-and-exactin-operators)  |                                                                   **Gallery1.Selected exactin SavedItems**                                                                   |                                                                                       Gehört zu einer [Sammlung](../working-with-data-sources.md#collections) oder einer Tabelle.                                                                                        |
|                             **exactin**                             |                       &nbsp;                        |                                           **&quot;Windows&quot; exactin “To display windows in the Windows operating system...”**                                            |                                                                                                                 Teilzeichenfolgentest (Groß-/Kleinschreibung wird berücksichtigt)                                                                                                                  |
|                               **in**                                |                       &nbsp;                        |                                                                     **Gallery1.Selected in SavedItems**                                                                      |                                                                                                               Gehört zu einer Sammlung oder einer Tabelle.                                                                                                               |
|                               **in**                                |                       &nbsp;                        |                                                      **&quot;The&quot; in &quot;The keyboard and the monitor...&quot;**                                                      |                                                                                                                Teilzeichenfolgentest (Groß-/Kleinschreibung wird nicht berücksichtigt)                                                                                                                 |
|                                **@**                                | [Operator zur Mehrdeutigkeitsvermeidung](#disambiguation-operator) |                                                                           **MyTable[@fieldname]**                                                                            |                                                                                                                       Mehrdeutigkeitsvermeidung für Felder                                                                                                                       |
|                                **@**                                |                       &nbsp;                        |                                                                              **[@MyVariable]**                                                                               |                                                                                                                      Globale Mehrdeutigkeitsvermeidung                                                                                                                       |
| **;**<br>[[sprachabhängig](../global-apps.md)]  |                   Listentrennzeichen                    | **If( X < 10; "Low"; "Good" )**<br>**{ X: 12; Y: 32 }**<br>**[ 1; 2; 3 ]** | Trennt Folgendes: <ul><li>Argumente in Funktionsaufrufen</li><li>Felder in einem [Datensatz](../working-with-tables.md#elements-of-a-table)</li><li>Datensätze in einer [Tabelle](../working-with-tables.md#inline-value-tables)</li></ul> Dieses Zeichen hängt von der Sprache ab. |
| **;;**<br>[[sprachabhängig](../global-apps.md)] |                  Formelverkettung                   |                                     **Collect(T; A);; Navigate(S1; &quot;&quot;)**                                     |                                                                          Separate Aufrufe von Funktionen in Verhaltenseigenschaften. Der Verkettungs Operator hängt von der Sprache ab.                                                                          |
|                             **Parent**                              |         [Parent-Operator](#parent-operator)         |                                                                               **Parent.Fill**                                                                                |                                                                                                           Zugriff auf Eigenschaften eines Steuerelementcontainers                                                                                                            |
|                            **ThisItem**                             |       [ThisItem-Operator](#thisitem-operator)       |                                                                            **ThisItem.FirstName**                                                                            |                                                                                                          Zugriff auf Felder eines Katalogs oder Form-Steuerelements                                                                                                           |

## <a name="in-and-exactin-operators"></a>Operatoren „in“ und „exactin“
Sie können die Operatoren **[in](operators.md#in-and-exactin-operators)** und **[exactin](operators.md#in-and-exactin-operators)** verwenden, um in einer [Datenquelle](../working-with-data-sources.md) nach einer Zeichenfolge zu suchen, z.B. einer Sammlung oder importierten Tabelle. Mit dem Operator **[in](operators.md#in-and-exactin-operators)** werden Übereinstimmungen unabhängig von der Groß- und Kleinschreibung identifiziert, und mit dem Operator **[exactin](operators.md#in-and-exactin-operators)** ergeben sich nur dann Übereinstimmungen, wenn sie exakt die gleiche Schreibweise haben. Im Folgenden ein Beispiel:

1. Erstellen oder importieren Sie eine Sammlung mit dem Namen **Inventory**, und zeigen Sie sie in einem Katalog an. Dies wird im ersten Verfahren unter [Show images and text in a gallery](../show-images-text-gallery-sort-filter.md) (Anzeigen von Bildern und Text in einem Katalog) beschrieben.
2. Legen Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs auf diese Formel fest:
   <br>**Filter(Inventory; "E" in ProductName)**

    Im Katalog werden alle Produkte mit Ausnahme von „Callisto“ angezeigt, weil der Name dieses Produkts der einzige Name ist, der den von Ihnen angegebenen Buchstaben nicht enthält.
3. Ändern Sie die **[Items](../controls/properties-core.md)**-Eigenschaft des Katalogs in diese Formel:
   <br>**Filter(Inventory; "E" exactin ProductName)**

    Im Katalog wird nur „Europa“ angezeigt, weil nur dieser Name den von Ihnen angegebenen Großbuchstaben enthält.

## <a name="thisitem-operator"></a>ThisItem-Operator
Sie können Daten in den Steuerelementen **[Katalog](../controls/control-gallery.md)**, **[Formular bearbeiten](../controls/control-form-detail.md)** oder **[Formular anzeigen](../controls/control-form-detail.md)** anzeigen, indem Sie sie an eine Tabelle oder Sammlung binden.  Diese Steuerelemente stellen einen Container für andere Karten und Steuerelemente dar.  Jede Karte bzw. jedes Steuerelement im Container kann über den Operator **[ThisItem](operators.md#thisitem-operator)** auf die angebundenen Daten zugreifen.   

Verwenden Sie den **[thisitem](operators.md#thisitem-operator)** -Operator, um die [Spalte](../working-with-tables.md#columns) der Daten anzugeben, die in den einzelnen Karten oder Steuerelementen innerhalb des äußeren Steuer Elements angezeigt werden sollen. Mit dem Operator im Produktkatalog für [Show images and text in a gallery](../show-images-text-gallery-sort-filter.md) (Anzeigen von Bildern und Text in einem Katalog) wurde beispielsweise angegeben, dass für das Bildsteuerelement das Produktdesign, für die obere Bezeichnung der Produktname und für die untere Bezeichnung die Anzahl von auf Lager befindlichen Einheiten angezeigt werden soll.

Für geschachtelte Kataloge bezieht sich **[ThisItem](operators.md#thisitem-operator)** auf die Elemente des innersten Katalogs. Wenn für die Zeilenfelder in den inneren und äußeren Katalogen kein Konflikt besteht, können Sie die nicht qualifizierten Feldnamen (Spaltennamen) auch direkt verwenden. Mit diesem Ansatz ist es möglich, dass sich Regeln eines inneren Katalogs auf die Elemente eines äußeren Katalogs beziehen.

## <a name="parent-operator"></a>Parent-Operator
Einige Steuerelemente hosten andere Steuerelemente. Bei den Steuerelementen vom Typ **[Bildschirm](../controls/control-screen.md)**, **[Katalog](../controls/control-gallery.md)**, **[Karte](../controls/control-card.md)**, **[Formular bearbeiten](../controls/control-form-detail.md)** und **[Formular anzeigen](../controls/control-form-detail.md)** handelt es sich beispielsweise jeweils um Container für Steuerelemente. Wir bezeichnen das hostende Steuerelement als übergeordnetes Steuerelement (Parent) der darin enthaltenen Steuerelemente.

Alle Steuerelemente in Power Apps können von überall in der APP anhand ihres Namens referenziert werden. **Screen1** kann beispielsweise der Name eines Bildschirms in Ihrer App sein. Zum Abrufen der Hintergrundfarbe dieses Bildschirms können Sie **Screen1.Fill** verwenden.

Steuerelemente auf diesem Bildschirm verfügen über eine weitere Option. Sie können einen relativen Verweis nutzen: **Parent.Fill**. Der **[Parent](operators.md#parent-operator)**-Operator bezieht sich auf das Steuerelement, mit dem dieses Steuerelement gehostet wird, und macht alle zugehörigen Eigenschaften verfügbar. Die Verwendung von **[Parent](operators.md#parent-operator)** ist hilfreich, weil dafür keine Abhängigkeit vom Namen des Steuerelements besteht. Sie können ein Containersteuerelement kopieren und einfügen, ohne dass Sie Verweise im Container anpassen müssen. Mit diesem Operator wird außerdem die Beziehung zwischen dem untergeordneten und übergeordneten Steuerelement beim Lesen von Formeln besser verdeutlicht.

## <a name="identifier-names"></a>Bezeichnernamen

Die Namen von Variablen, Datenquellen, Spalten und anderen Objekten können beliebige [Unicode](https://en.wikipedia.org/wiki/Unicode)enthalten.

Verwenden Sie einfache Anführungszeichen um einen Namen, der ein Leerzeichen oder ein anderes Sonderzeichen enthält.  Verwenden Sie zwei einfache Anführungszeichen, um ein einzelnes Anführungszeichen im Namen darzustellen.  Namen, die keine Sonderzeichen enthalten, erfordern keine einfachen Anführungszeichen.

Im folgenden finden Sie einige Beispiel Spaltennamen, die in einer Tabelle vorkommen können, und wie Sie in einer Formel dargestellt werden:

| Spaltenname in einer Datenbank   | Spalten Verweis in einer Formel |
|-----------------------------|-------------------------------|
| SimpleName                  | ```SimpleName``` |
| NameWith123Numbers          | ```NameWith123Numbers``` |
| Name mit Leerzeichen            | ```'Name with spaces'``` |
| Name mit "doppelten" Anführungszeichen   | ```'Name with "double" quotes'``` |
| Name mit "einfache" Anführungszeichen   | ```'Name with ''single'' quotes'``` |
| Name mit @ at-Zeichen      | ```'Name with an @ at sign'``` |

Doppelte Anführungszeichen werden verwendet, um [Text](data-types.md#embedded-text)Zeichenfolgen festzulegen.  

## <a name="display-names-and-logical-names"></a>Anzeigen Amen und logische Namen
Einige Datenquellen, z. b. SharePoint und Common Data Service, haben zwei verschiedene Namen, um auf dieselbe Tabelle oder Spalte mit Daten zu verweisen:

* **Logischer Name** : ein eindeutiger Name, der garantiert eindeutig ist, nicht geändert wird, nachdem er erstellt wurde, lässt normalerweise keine Leerzeichen oder andere Sonderzeichen zu und ist nicht in verschiedenen Sprachen lokalisiert.  Daher kann der Name etwas kryptisch sein.  Diese Namen werden von professionellen Entwicklern verwendet.  Beispielsweise **cra3a_customfield**.  Dieser Name kann auch als **Schema Name** oder einfach als **Name**bezeichnet werden.

* **Anzeige Name** : ein Name, der benutzerfreundlich ist und von Endbenutzern angezeigt werden soll.  Dieser Name ist möglicherweise nicht eindeutig, kann sich im Laufe der Zeit ändern, kann Leerzeichen und beliebige Unicode-Zeichen enthalten und kann in verschiedenen Sprachen lokalisiert werden.  Entsprechend dem obigen Beispiel kann der Anzeige Name ein **benutzerdefiniertes Feld** mit einem Leerzeichen sein, das zwischen den Wörtern liegt.
 
Da Anzeige Namen leichter zu verstehen sind, werden Sie von Canvas-Apps als Optionen vorgeschlagen, und es werden keine logischen Namen vorgeschlagen.  Obwohl logische Namen nicht vorgeschlagen werden, können Sie immer noch verwendet werden, wenn Sie direkt eingegeben werden.

Stellen Sie sich beispielsweise vor, dass Sie einer Entität in Common Data Service ein **benutzerdefiniertes Feld** hinzugefügt haben.  Ein logischer Name wird vom System zugewiesen, das Sie nur ändern können, wenn das Feld erstellt wird.  Das Ergebnis sieht in etwa wie folgt aus:

> [!div class="mx-imgBorder"]  
> ![Konten Entität mit hinzugefügter benutzerdefiniertem Feld, das den anzeigen Amen "benutzerdefiniertes Feld" und den logischen Namen "cr5e3_customfield" anzeigt](media/operators/customfield_portal.png)

Beim Erstellen eines Verweises auf ein Konto Feld wird der Vorschlag zur Verwendung von **"benutzerdefiniertem Feld"** erstellt, da dies der Anzeige Name ist.  Beachten Sie, dass die einfachen Anführungszeichen verwendet werden müssen, da dieser Name ein Leerzeichen enthält:

> [!div class="mx-imgBorder"]  
> in ![Studio-Bearbeitungs Leiste werden Vorschläge für Feldnamen von Konten angezeigt, deren Anzeige Name "benutzerdefiniertes Feld" hervorgehoben ist](media/operators/customfield_suggest_display.png)

Nachdem Sie den Vorschlag ausgewählt haben, wird in der Bearbeitungs Leiste "benutzerdefiniertes Feld" angezeigt, und die Daten werden abgerufen: 

> [!div class="mx-imgBorder"]  
> ![Studio-Bearbeitungs Leiste, die die Verwendung des anzeigen Amens "benutzerdefiniertes Feld" für das Feld anzeigt](media/operators/customfield_display.png)

Obwohl dies nicht empfohlen wird, können wir auch den logischen Namen für dieses Feld verwenden.  Dies führt dazu, dass die gleichen Daten abgerufen werden.  Beachten Sie, dass keine einfachen Anführungszeichen erforderlich sind, da dieser Name keine Leerzeichen oder Sonderzeichen enthält:

> [!div class="mx-imgBorder"]  
> ![Studio-Bearbeitungs Leiste, die die Verwendung des logischen namens cr5e3_customfield für das Feld anzeigt](media/operators/customfield_logical.png)

Im Hintergrund wird eine Zuordnung zwischen den anzeigen Amen, die in Formeln angezeigt werden, und den zugrunde liegenden logischen Namen beibehalten.  Da logische Namen für die Interaktion mit der Datenquelle verwendet werden müssen, wird diese Zuordnung zum automatischen Konvertieren des aktuellen anzeigen Amens in den logischen Namen verwendet, was im Netzwerk Datenverkehr zu sehen ist.  Diese Zuordnung wird auch für die Konvertierung in logische Namen verwendet, um zu neuen anzeigen Amen zu wechseln, z. b. wenn sich ein Anzeige Name ändert oder ein Ersteller in einer anderen Sprache die APP bearbeitet.

> [!NOTE] 
> Logische Namen werden nicht übersetzt, wenn eine APP zwischen Umgebungen verschoben wird.  Bei Common Data Service System Entitäts-und Feldnamen sollte dies kein Problem darstellen, da logische Namen in Umgebungen einheitlich sind.  Alle benutzerdefinierten Felder, wie z. b. **cra3a_customfield** in diesem Beispiel oben, haben möglicherweise ein anderes Umgebungs Präfix (in diesem Fall**cra3a** ).  Anzeigen Amen werden bevorzugt, da Sie mit anzeigen Amen in der neuen Umgebung abgeglichen werden können. 

## <a name="name-disambiguation"></a>Namens Eindeutigkeit
Da Anzeige Namen nicht eindeutig sind, kann derselbe Anzeige Name mehrmals in derselben Entität angezeigt werden.  Wenn dies der Fall ist, wird der logische Name am Ende des anzeigen Amens in Klammern für einen oder mehrere der in Konflikt stehenden Namen eingefügt.  Wenn im obigen Beispiel ein zweites Feld mit dem gleichen anzeigen amen des **benutzerdefinierten Felds** mit dem logischen Namen **cra3a_customfieldalt** vorhanden wäre, werden die Vorschläge Folgendes angezeigt:

> [!div class="mx-imgBorder"]  
> ![Studio-Bearbeitungs Leiste, die die Verwendung des logischen Namens anzeigt, cr5e3_customfieldalt, die zwei Versionen von "benutzerdefiniertem Feld" eindeutig zu machen](media/operators/customfield_suggest_alt.png)

Namens mehrdeutigkeits Zeichenfolgen werden in anderen Fällen hinzugefügt, in denen Namenskonflikte auftreten, z. b. die Namen von Entitäten, Options Sätzen und andere Common Data Service Elemente. 

## <a name="disambiguation-operator"></a>Operator zur Mehrdeutigkeitsvermeidung
Für einige Funktionen werden [Datensatzbereiche](../working-with-tables.md#record-scope) zum Zugreifen auf die Felder der Tabelle erstellt, während die einzelnen Datensätze verarbeitet werden, z.B. **Filter**, **AddColumns** und **Sum**.  Feldnamen, die mit auf Datensatzebene hinzugefügt wurden, haben Vorrang vor denselben Namen von woanders in der App.  Wenn dies passiert, können Sie mit dem **@**-Operator zur Mehrdeutigkeitsvermeidung trotzdem auf Werte außerhalb des Datensatzbereichs zugreifen:

* Verwenden Sie zum Zugreifen auf Werte aus geschachtelten Datensatzbereichen den **@**-Operator mit dem Namen der jeweiligen Tabelle, indem Sie das folgende Muster verwenden:<br>_Tabelle_**[@**_Feldname_**]**
* Verwenden Sie zum Zugreifen auf globale Werte, z.B. Datenquellen, Sammlungen und Kontextvariablen, das Muster **[@**_Objektname_**]** (ohne Tabellenbezeichnung).

Weitere Informationen und Beispiele finden Sie unter [Datensatzbereiche](../working-with-tables.md#record-scope).

