---
title: Definieren Sie in PowerAppss berechnete Felder | MicrosoftDocs
description: 'Hier erfahren Sie, wie Sie berechnete Felder definieren'
ms.custom: ''
ms.date: 05/25/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 6d58a297-2ddf-4236-be3a-47249b49d5fa
caps.latest.revision: 67
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-calculated-fields-to-automate-manual-calculations"></a>Definition berechneter Felder für das Automatisieren von manuellen Berechnungen

Verwenden Sie berechnete Felder, um manuelle Berechnungen zu automatisieren, die in Ihren Geschäftsprozessen verwendet werden. 

Beispielsweise möchte ein Vertriebsmitarbeiter möglicherweise den gewichteten Umsatzes für eine Verkaufschance kennen, die auf dem geschätzten Umsatz einer Verkaufschance multipliziert mit der Wahrscheinlichkeit basiert. Oder er möchte automatisch einen Rabatt anwenden, wenn der Auftrag größer als $500 ist. Ein berechnetes Feld kann Werte enthalten, die sich aus einfachen Berechnungen ergeben, z. B. bedingte Operationen, wie größer als oder If-Else und viele andere. Sie können all dies erzielen, indem Sie PowerApps verwenden. Es ist nicht erforderlich, Code zu schreiben.  
  
## <a name="capabilities"></a>Funktionen
  
- Berechnete Felder verwenden die Felder aus der aktuellen Entität oder verknüpften übergeordneten Entitäten.  
- Der Ausdruckssupport ist in der aktuellen Entität und den Feldern der verwandten übergeordneten Entität in den Abschnitten **Bedingung** und **Aktion** verfügbar. Die integrierten Funktionen enthalten:  
 **ADDHOURS**, **ADDDAYS**, **ADDWEEKS**, **ADDMONTHS**, **ADDYEARS**, **SUBTRACTHOURS**, **SUBTRACTDAYS**, **SUBTRACTWEEKS**, **SUBTRACTMONTHS**, **SUBTRACTYEARS**, **DIFFINDAYS**, **DIFFINHOURS**, **DIFFINMINUTES**, **DIFFINMONTHS**, **DIFFINWEEKS**, **DIFFINYEARS**, **CONCAT**, **TRIMLEFT** und **TRIMRIGHT**.  
- Eine umfangreiche bedingte Unterstützung bietet Verzweigung und mehrere Bedingungen. Die logischen Operationen uimfassen **UND** und **ODER**-Operatoren.  
- Die Sichtbearbeitungsfunktionen enthalten moderne Benutzerschnittstelle und Intellisense im Abschnitt **AKTION**. 
- Eine nahtlose Integration der berechneten Felder mit Formularen, Ansichten, Diagrammen und Berichten in Echtzeit ist verfügbar.  
- Sie können berechnete Felder konfigurieren, um benutzerdefinierte Steuerelemente zu verwenden.  
  
  
## <a name="scenarios"></a>Szenarios
  
- **Gewichteter Umsatz**: Geschätzter Umsatz multipliziert mit Wahrscheinlichkeit  
- **Nettowert**: Aktivposten, vermindert um die Verbindlichkeiten für ein bestimmtes Konto  
- **Arbeitslohn**: Basisrate bis zu 40 Stunden, plus zusätzliche Überstunden  
- **Kontaktnummer**: Telefonnummer für eine Verkaufschance basierend auf Firma oder Kontakt  
- **Lead-Ergebnis**: Einzelnes Feld, das Einblicke zur Qualität eines gegebenen Leads eines Qualität bereitstellt  
- **Nachverfolgung bis**: Nachverfolgen einer Aktivität bis auf eine angegebene Anzahl von Tagen nach Priorität  
  
> [!IMPORTANT]
>  Um ein berechnetes Feld zu erstellen, müssen Sie über Schreibberechtigung auf der [Feldsicherheitsprofil](/powerapps/developer/common-data-service/reference/entities/fieldsecurityprofile)-Entität verfügen. Wenn das berechnete Feld die gesicherten Felder in einer Berechnung verwendet, sollten Sie erwägen, das berechnete Feld zu sichern, um Benutzer am Zugriff auf Daten zu hindern, für die sie nicht über ausreichende Zugriffsberechtigungen verfügen. Der Editor für berechnete Felder gibt eine Warnung aus, wenn Sie ein berechnetes Feld erstellen, das gesichterte Felder in einer berechnung verwendet, und es schlägt vor, das berechnete Feld zu sichern. Weitere Informationen:  [Feldsicherheit, um den Zugriff zu steuern](/dynamics365/customer-engagement/admin/field-level-security).  

## <a name="create-a-calculated-field"></a>Erstellen eines berechneten Felds

Verwenden Sie den Feldeditor, um ein berechnetes Feld anzugeben. In diesem Beispiel verwenden wir [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), aber die Schritte ähneln den zur Verwendung des Projektmappen-Explorers. Weitere Informationen: [Erstellen und Bearbeiten von Feldern](create-edit-fields.md)
  
1. Öffnen Sie [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
1. Erweitern Sie **Daten** > **Entitäten**.  
1. Wählen Sie die gewünschte Entität und wählen Sie **Felder** aus. Wählen Sie **Feld hinzufügen** aus.  
1. Geben die für das Feld erforderlichen Informationen an, einschließlich **Anzeigename**, **Name** und **Datentyp**. 
1. Wenn der Datentyp eines der Typen ist, die berechnete Felder unterstützen, können Sie das Feld zu einem berechneten Feld machen, indem Sie **Hinzufügen** > **Berechnung** auswählen.

    ![Feld zu einem berechneten Feld machen](media/make-field-calculated-maker.png)

    Dies sind die Feldtypen, die Berechnungen unterstützen:
    - Text
    - Optionssatz  
    - Zwei Optionen  
    - Ganze Zahl  
    - Dezimalzahl  
    - Währung  
    - Datum/Uhrzeit

1. Die Auswahl von **Berechnung** erfordert, dass Sie die Änderungen an der Entität speichern. Klicken Sie auf im Dialog **Ausstehende Änderungen** auf **Speichern** , um fortzusetzen.
1. Damit wird der Definitionseditor für berechnete Felder geöffnet, in dem das neue berechnete Feld erstellt wurde, jedoch keine Formel festgelegt wurde. Die Definition von berechneten Feldern besteht aus zwei Abschnitten: **BEDINGUNG** und **AKTION**.  
  ![Formular für neue Feldberechnung](media/empty-field-calculation.png)
- Im Abschnitt **Bedingung** können Sie ein Feld, eine Entität, einen Operator, Typ und Wert angeben. im Dropdownfeld für die **Entität** können Sie eine aktuelle Entität oder eine verknüpfte Entität auswählen. Im Dropdownfeld **Feld** haben Sie eine Auswahl aller verfügbaren Felder für die Entität. Je nach dem Operator, den Sie ausgewählt haben, müssen Sie ggf. Typ und Wert bereitstellen. Sie können mehrere Bedingungen mithilfe Operatoren `AND` oder `OR` angeben.  
- Im Abschnitt **Aktion** können Sie die Formel für das berechnete Feld bereitstellen.  
  
> [!NOTE]
>  Sie können Daten aus Suchdatensätzen innerhalb einer Aktion verwenden. Sie müssen zuerst das Suchfeld auswählen und dann einen Zeitraum eingeben. Danach können Sie eines der Felder auswählen, die für die verknüpfte Entität verfügbar sind. In Fall von *`<LookupFieldName>.<RelatedFieldName>`* können Sie beispielsweise `ParentAccountId.AccountNumber` auswählen.  
>   
>  Beachten Sie, dass die Sicherheit auf Feldebene für die verknüpfte Entität ignoriert wird, sodass im Falle vertraulicher Daten im Zugriffs-Feld empfohlen wird, auch das berechnete Feld zu sichern.  


<a name="BusinessScenarios"></a> 
  
## <a name="examples"></a>Beispiele  

Es folgt eine ausführlichere Betrachtung der Beispiele der berechneten Felder. 
  
### <a name="weighted-revenue-of-opportunity"></a>Gewichteter Umsatz für Verkaufschance

In diesem Beispiel verwenden wir die Felder der Verkaufschancenentität, um den gewichteten Umsatz nach der Wahrscheinlichkeit der Verkaufschance zu berechnen. Im Feldeditor für eine Verkaufschancenentität erstellen wir ein Feld namens **Gewichteter Umsatz**, und geben an den Feldtyp als **Berechnet** an, und der Datentyp ist **Währung**.

In Definitionseditor des berechneten Felds im Abschnitt **Bedingung**, geben wir die Verkaufschance mit dem Status = Offen an. In der **AKTION** berechnet die Formel den gewichteten Umsatz anhand des geschätzten Umsatzes der Verkaufschance, multipliziert mit der Wahrscheinlichkeit der Verkaufschance.  Die folgendenScreenshots zeigen Schritt für Schritt, wie das Feld **Gewichteter Umsatz** definiert wird.  
  
#### <a name="set-the-condition-on-the-opportunities"></a>Legen Sie die Bedingung in den Verkaufschancen fest:
  
![Festlegen des gewichteten Umsatzes in Dynamics 365](media/calc-field-open-opportunity.png)  
  
#### <a name="provide-the-formula-for-the-weighted-revenue"></a>Stellen Sie die Formel für den gewichteten Umsatz zur Verfügung: 
  
![Festlegen des geschätzten Werts für den gewichteten Umsatz in Dynamics 365](media/calc-field-open-opportunities-3.png)  
  
#### <a name="altogether"></a>Vollständig:
  
![Gewichteter Umsatz zu gesch. Umsatz in Dynamics 365](media/calculated-field-open-opportunity.png)  
  
### <a name="follow-up-date-of-opportunity"></a>Nachverfolgungsdatum der Verkaufschance 
 
In diesem Beispiel verwenden wir die Felder des Leads, der die Verkaufschance ausgelöst hat, um das betreffende Datum zu berechnen, bis zu dem die Verkaufschance nachverfolgt wird. 

Im Feldeditor für eine Verkaufschancenentität erstellen wir ein Feld namens **Nachverfolgungsdatum**, und geben an den Feldtyp als **Berechnet** an, und der Datentyp ist **Datum und Uhrzeit**.  

In Definitionseditor des berechneten Felds im Abschnitt **Bedingung**, geben wir zwei Bedingungen an: Zeitrahmen des Kaufs und den geschätzten Wert des Leads. 

In **AKTION** können Sie zwei Formeln eingeben:
 - So führen Sie bei der unmittelbaren Verkaufschance in einer Woche eine Nachverfolgung durch
 - So führen Sie eine Nachverfolgung in einem Monat durch, wenn die Verkaufschance wahrscheinlich nicht sofort passiert. 

Die folgenden Screenshots zeigen Schritt für Schritt, wie das berechnete Feld **Nachverfolgungsdatum** definiert wird.  
  
#### <a name="set-the-two-conditions-on-the-originating-lead"></a>Legen Sie die Bedingungen für den Ursprungslead fest:
  
![Nachverfolgungsdatum für eine Verkaufschance in Dynamics 365](media/calc-field-follow-update-2.PNG)  
  
![Nachverfolgungsdatum für eine Verkaufschance in Dynamics 365](media/calc-field-follow-update-3.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-week"></a>Stellen Sie die Formel zur Nachverfolgung in einer Woche zur Verfügung:
  
![Nachverfolgungsdatum für eine Verkaufschance in Dynamics 365](media/calc-field-follow-update-4.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-month"></a>Stellen Sie die Formel zur Nachverfolgung in einem Monat zur Verfügung:
  
![Nachverfolgungsdatum in Dynamics 365 festlegen](media/calc-field-follow-update-5.PNG)  
  
#### <a name="altogether"></a>Vollständig:
  
 ![Nachverfolgungsdatum Wenn-Dann und Sonst in Dynamics 365 festlegen](media/calc-field-follow-update-6.PNG)  
  
### <a name="days-from-a-record-creation"></a>Tage ab einer Datensatzerstellung 
 
In diesem Beispiel wird die Funktion **DIFFINDAYS** verwendet, um die Differenz in Tagen vom Zeitpunkt der Erstellung eines Datensatzes bis zum aktuellen Datum zu berechnen. 

Erstellen Sie ein neues Ganzzahlfeld namens **Berechnete Differenz in Tagen**.
  
#### <a name="provide-the-formula-for-computing-the-difference-in-days"></a>Stellen Sie die Formel zum Berechnen der Differenz in Tagen zur Verfügung
  
![Berechnetes Feld, DIFFINDAYS-Funktion](media/custom-calc-field-diff-days.png)  
  
#### <a name="altogether"></a>Vollständig:
  
![Unterschied in Tagen seit Datensatzerstellung](media/calc-field-diff-days-complete.png)  
  
<a name="Syntax"></a> 
  
## <a name="functions-syntax"></a>Funktionssyntax  

Die folgende Tabelle enthält Informationen zur Syntax für die Funktionen, die im Abschnitt **AKTION** des berechneten Felds bereitgestellt werden.  
  
> [!TIP]
>  Die Funktionsnamen werden in Großbuchstaben angegeben.  
  
|Funktionssyntax|Beschreibung|Rückgabetyp|  
|---------------------|-----------------|-----------------|  
|**ADDDAYS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, plus die angegebenen Anzahl von Tagen.|Datum und Uhrzeit|  
|**ADDHOURS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, plus die angegebenen Anzahl von Stunden.|Datum und Uhrzeit|  
|**ADDMONTHS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, plus die angegebenen Anzahl von Monaten.|Datum und Uhrzeit|  
|**ADDWEEKS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, plus die angegebenen Anzahl von Wochen.|Datum und Uhrzeit|  
|**ADDYEARS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, plus die angegebenen Anzahl von Jahren.|Datum und Uhrzeit|  
|**SUBTRACTDAYS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, minus der angegebenen Anzahl von Tagen.|Datum und Uhrzeit|  
|**SUBTRACTHOURS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, minus die angegebenen Anzahl von Stunden.|Datum und Uhrzeit|  
|**SUBTRACTMONTHS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, minus die angegebenen Anzahl von Monaten.|Datum und Uhrzeit|  
|**SUBTRACTWEEKS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, minus die angegebenen Anzahl von Wochen.|Datum und Uhrzeit|  
|**SUBTRACTYEARS** (ganze Zahl, Datum und Uhrzeit)|Gibt ein neues Datum und Uhrzeit zurück, die dem gegebenen Datum und der Uhrzeit gleich sind, minus die angegebenen Anzahl von Jahren.|Datum und Uhrzeit|  
|**DIFFINDAYS** (Datum und Uhrzeit, Datum und Uhrzeit)|Gibt die Differenz in Tagen zwischen zwei **Datum und Uhrzeit**-Feldern zurück. Wenn die Datums- und Uhrzeitenangaben auf den gleichen Tag fallen, beträgt die Differenz "Null".|Ganze Zahl|  
|**DIFFINHOURS** (Datum und Uhrzeit, Datum und Uhrzeit)|Gibt die Differenz in Stunden zwischen zwei **Datum und Uhrzeit**-Feldern zurück.|Ganze Zahl|  
|**DIFFINMINUTES** (Datum und Uhrzeit, Datum und Uhrzeit)|Gibt die Differenz in Minuten zwischen zwei **Datum und Uhrzeit**-Feldern zurück.|Ganze Zahl|  
|**DIFFINMONTHS** (Datum und Uhrzeit, Datum und Uhrzeit)|Gibt die Differenz in Monaten zwischen zwei **Datum und Uhrzeit**-Feldern zurück. Wenn die Datums- und Uhrzeitenangaben auf den gleichen Monat fallen, beträgt die Differenz "Null".|Ganze Zahl|  
|**DIFFINWEEKS** (Datum und Uhrzeit, Datum und Uhrzeit)|Gibt die Differenz in Wochen zwischen zwei **Datum und Uhrzeit**-Feldern zurück. Wenn die Datums- und Uhrzeitenangaben auf die gleiche Woche fallen, beträgt die Differenz "Null".|Ganze Zahl|  
|**DIFFINYEARS** (Datum und Uhrzeit, Datum und Uhrzeit)|Gibt die Differenz in Jahren zwischen zwei **Datum und Uhrzeit**-Feldern zurück. Wenn die Datums- und Uhrzeitenangaben auf das gleiche Jahr fallen, beträgt die Differenz "Null".|Ganze Zahl|  
|**CONCAT** (einzelne Textzeile, einzelne Textzeile, ...) einzelne Textzeile)|Gibt eine Zeichenfolge zurück, die das Ergebnis einer Verkettung von zwei oder mehr Zeichenfolgen ist.|Zeichenfolge|  
|**TRIMLEFT** (einzelne Textzeile, ganze Zahl)|Gibt eine Zeichenfolge zurück, die eine Kopie einer angegebenen Zeichenfolge ohne die ersten N-Zeichen enthält.|Zeichenfolge|  
|**TRIMRIGHT** (einzelne Textzeile, ganze Zahl)|Gibt eine Zeichenfolge zurück, die eine Kopie einer angegebenen Zeichenfolge ohne die letzten N-Zeichen enthält.|Zeichenfolge|  
  
> [!NOTE]
>  Alle DIFF-Funktionen erfordern, dass das erste **Datum und Uhrzeit**-Feld und das zweite **Datum und Uhrzeit**-Feld das gleiche Verhalten aufweisen: **Ortszeit Benutzer**, **Nur Datum** oder **zeitzonenunabhängig**. Wenn das Verhalten des zweiten Felds nicht mit dem Verhalten des ersten Felds übereinstimmt, wird die Fehlermeldung angezeigt, die angibt, dass das zweite Feld nicht in der aktuellen Funktion verwendet werden kann. Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)  
  
> [!NOTE]
>  Sie können ein Datum wie 01/01/2015 nicht als der Datumswert in einem berechneten Feld eingeben. Datum und DateTime-Werte können nur mithilfe von anderen DateTime-Feldern festgelegt oder verglichen werden.  
  
In der Funktion **CONCAT** können Sie Literalzeichenfolgen als einzelne Textzeilen, Entitätsfelder, die eine einzelne Textzeile enthalten, oder eine Kombination aus beiden verwenden. Beispiel: **CONCAT** (FirstName, LastName, “ist ein Manager.”). Wenn eine Literalzeichenfolge Anführungszeichen enthält, stellen Sie jeder Marke das Escapezeichen (\\) voran, wie folgt: `This string contains the \"quotation marks.\"`. Dies stellt sicher, dass die Anführungszeichen innerhalb der Zeichenfolge nicht als Sonderzeichen behandelt werden, die die Zeichenfolgen trennen.  
  
Die folgenden Beispiele veranschaulichen, wie die **TRIMLEFT**- und **TRIMRIGHT**-Funktionen verwendet werden. Sie enthalten die ersten Zeichenfolgen und die resultierenden Zeichenfolgen, die von den Funktionen **TRIMLEFT** und **TRIMRIGHT** zurückgegeben werden:  
  
**TRIMLEFT** (“RXX10-3456789”, 3) gibt die Zeichenfolge `10-3456789`  zurück  
**TRIMRIGHT** (“20-3456789RXX”, 3) gibt die Zeichenfolge `20-3456789` zurück 
  
<a name="Considerations"></a> 
  
## <a name="considerations"></a>Überlegungen 
 
Sie sollten bestimmte Bedingungen und Beschränkungen berücksichtigen, wenn Sie mit den berechneten Feldern arbeiten:  
  
- Gespeicherte Abfragen, Diagramme und Visualisierungen können über maximal 10 eindeutige berechnete Felder verfügen.  
- Die Werte von berechneten Feldern werden nicht im Outlook Client Offline-Modus in den Kachelansichten oder auf Entitätshauptformularen angezeigt.  
- Eine Maximalanzahl verketteter berechneter Felder ist 5.  
- Ein berechnetes Feld kann nicht auf sich selbst verweisen oder zyklische Ketten haben.  
- Wenn Sie einen der Bedingungsoperatoren in einer mehrfachen Bedingungsklausel ändern, werden alle Bedingungsoperatoren auf diese Bedingung aktualisiert. Wenn Sie beispielsweise in der Klausel `IF (x > 50) OR (y ==10) OR (z < 5)` den `OR`-Operator zu dem `AND`-Operator ändern, werden alle `OR`-Operatoren in der Klausel zu `AND` -Operatoren.  
- Sie können auf übergeordnete Felder über das Suchfeld zur übergeordneten Entität zugreifen, z. B. *`<LookupFieldName>.<FieldName>`*. Dies ist nicht möglich mit Multi-Entitäts-Suchfeldern wie Kunde, die Firma oder Kontakt sein können. Allerdings haben manche Entitäten einzelne Suchfelder für eine bestimmte Entität, beispielsweise `ParentAccountid.`*`<FieldName>`* oder `ParentContactid.`*`<FieldName>`*.  
- Sortierung ist deaktiviert für:  
  - Ein berechnetes Feld, das ein Feld aus einem übergeordneten Datensatz enthält.  
  - Ein berechnetes Feld, das ein logische Feld enthält (z. B. ein Adressfeld).
  - Ein berechnetes Feld, das ein anderes berechnetes Feld enthält.  
- Berechnete Felder können nur zwei Entitäten umfassen.  
  - Ein berechnetes Feld kann ein Feld aus einer anderen Entität enthalten (zwei Entitäten umfassend - Aktuelle Entität und übergeordneten Datensatz).  
  - Ein berechnetes Feld kann kein berechnetes Feld aus einer anderen Entität enthalten, das ebenfalls ein anderes Feld aus einer anderen Entität enthält (drei Entitäten umfassend):   
    (Aktuelle Entität) berechnetes Feld &larr; (übergeordneter Datensatz) berechnetes Feld 1 &larr; (übergeordneter Datensatz) berechnetes Feld 2.  
- Sie können keine Workflows oder Plug-Ins in berechneten Feldern auslösen.  
- Sie können ein vorhandenes einfaches Feld nicht in ein berechnetes Feld ändern. Wenn Ihre aktuelle Anwendung JavaScript oder Plug-Ins verwendet, um ein Feld zu berechnen, können Sie die Funktion Berechnete Felder nicht verwenden, ohne ein neues Feld zu erstellen.  
- Duplikaterkennungsregeln werden für berechnete Felder nicht ausgelöst.  
- Ein Rollup kann nicht auf ein berechnetes Feld verweisen, das ein anderes berechnetes Feld nutze. Dies gilt auch dann, wenn das andere berechnete Feld der aktuellen Entität angehört.  
  
### <a name="see-also"></a>Siehe auch
 
[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Definition von Rollupfeldern, die Werte aggregieren](define-rollup-fields.md)<br />
[Video: Rollup und berechnete Felder](http://go.microsoft.com/fwlink/p/?LinkId=517727)
