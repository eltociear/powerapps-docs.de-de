---
title: Hinzufügen von Transformationszuordnungen für den Import (Common Data Service) | Microsoft-Dokumentation
description: Transformationszuordnung aktiviert optionale Änderung von Quelldaten vor dem Import.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2ec4a7ec143559fc3c64987764ee996b6e3d5cc4
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748263"
---
# <a name="add-transformation-mappings-for-import"></a>Hinzufügen von Transformationszuordnungen für den Import

Verwenden Sie Transformationszuordnungen, um Daten zu ändern, bevor Sie sie Importieren. Teilen Sie beispielsweise einen vollständigen Namen, der in der Quelldatei enthalten ist, in einen Vornamen und einen Nachnamen ein, um die Zielattribute für eine Entität anzupassen.  
  
 Verwenden Sie zum Implementieren von Transformationszuordnung die Entität Transformationszuordnung (`TransformationMapping`) und die Entität Transformationsparameterzuordnung (`TransformationParameterMapping`).  
  
 Die transformierten Daten müssen mit den Common Data Service-Entitätsattributtypen kompatibel sein.  
  
 Der Transformationstyp wird von der `TransformationMapping.TransformationTypeName`-Eigenschaft beschrieben. Die gültigen Werte für diese Eigenschaft werden in der folgenden Tabelle aufgeführt:  
  
|Feld|Wert|  
|-----------|-----------|  
|AddToCurrentDate|"Microsoft.Crm.Transformations.AddToCurrentDate"|  
|AddToDate|"Microsoft.Crm.Transformations.AddToDate"|  
|AdvancedAddToCurrentDate|"Microsoft.Crm.Transformations.AdvancedAddToCurrentDate"|  
|AssignValue|"Microsoft.Crm.Transformations.AssignValue"|  
|Verketten|"Microsoft.Crm.Transformations.Concatenate"|  
|Ersetzen|"Microsoft.Crm.Transformations.Replace"|  
|Teilen|"Microsoft.Crm.Transformations.Split"|  
|Teilzeichenfolge|"Microsoft.Crm.Transformations.Substring"|  
  
 In den folgenden Abschnitten werden die verfügbaren Transformationen beschrieben.  
  
<a name="BKMK_Concatenation"></a>   
## <a name="concatenation"></a>Verkettung  
 Verkettet Zeichenfolgen und trennt sie mit einem Trennzeichen.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Präfix|Zeichenfolge, die als Präfix in der verketteten Zeichenfolge verwendet wird.|  
|Suffix|Zeichenfolge, die als Suffix in der verketteten Zeichenfolge verwendet wird.|  
|Trennzeichen|Ein Zeichen oder eine Kombination von Zeichen, die Teilzeichenfolgen innerhalb der verketteten Zeichenfolge trennen. Das Trennzeichen wird nicht zwischen dem Präfix und der Teilzeichenfolge oder Suffix und der Teilzeichenfolge verwendet. Verwenden Sie nicht die Zeichen für zurück (\b), neue Zeile (\n) und Zeilenumbruch (\r) als ein Trennzeichen.|  
|\<Variable>|Array variabler Länge, das Teilzeichenfolgen enthält.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Zeichenfolge|Verkettete Zeichenfolge.|  
  
<a name="BKMK_Split"></a>   
## <a name="split"></a>Teilen  
 Trennt eine Zeichenfolge, die ein Trennzeichen in Teilzeichenfolgen enthält. Es kann bis zu zehn Teilzeichenfolgen geben.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Eingabezeichenfolge|Zeichenfolge, die mindestens eine Teilzeichenfolge enthält, die mit Trennzeichen getrennt wird.|  
|Trennzeichen|Ein Zeichen oder eine Kombination von Zeichen, die Teilzeichenfolgen innerhalb der Zeichenfolge trennen. Verwenden Sie nicht die Zeichen für zurück (\b), neue Zeile (\n) und Zeilenumbruch (\r) oder leere Zeichenfolgen als ein Trennzeichen.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Variable|Teilzeichenfolgen 1 durch Maximum von 10.|  
  
 Angenommen die Eingabezeichenfolge enthält elf , Teilzeichenfolgen, die Ausgabe enthält zehn Teilzeichenfolgen, wie im folgenden Beispiel gezeigt:  
  
 Eingabezeichenfolge: a;b;c;d;e;f;g;h;i;j;k  
  
 Ausgabe:  
  
 a  
  
 b  
  
 c  
  
 d  
  
 e  
  
 f  
  
 g  
  
 h  
  
 i  
  
 j;k  
  
<a name="BKMK_Substring"></a>   
## <a name="substring"></a>Teilzeichenfolge  
 Gibt eine Teilzeichenfolge einer bestimmten Länge zurück, beginnend an einem bestimmten Punkt der Zeichenfolge.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Eingabezeichenfolge|Zeichenfolge, die eine Teilzeichenfolge enthält.|  
|Startindex|Anfangsposition der Teilzeichenfolge.|  
|Länge|Länge der Teilzeichenfolge. Wenn die Länge **NULL** ist, wird vom Startindex eine vollständige Zeichenfolge zurückgegeben.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Teilzeichenfolge|Zurückgegebene Teilzeichenfolge.|  
  
<a name="BKMK_Replace"></a>   
## <a name="replace"></a>Ersetzen  
 Ersetzt alle Vorkommen einer angegebenen Zeichenfolge durch eine andere angegebene Zeichenfolge.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Eingabezeichenfolge|Zeichenfolge, die eine Suchzeichenfolge enthält.|  
|Suchzeichenfolge|Suchzeichenfolge Verwenden Sie nicht die Zeichen für zurück (\b), neue Zeile (\n) und Zeilenumbruch (\r) als eine Suchzeichenfolge.|  
|Zeichenfolge ersetzen|Die Ersetzungszeichenfolge. Verwenden Sie eine leere Zeichenfolge, um eine Suchzeichenfolge zu entfernen. Verwenden Sie nicht die Zeichen für zurück (\b), neue Zeile (\n) und Zeilenumbruch (\r) als eine Ersatzzeichenfolge.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Wert|Ersatzwert (gleich dem zugewiesenen Wert)|  
  
<a name="BKMK_AssignValue"></a>   
## <a name="assign-value"></a>Wert zuweisen  
 Ersetzt alle Werte durch einen angegebenen Wert.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Wert|Wert, den Sie zuweisen möchten.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Wert|Ersatzwert (gleich dem zugewiesenen Wert)|  
  
> [!NOTE]
>  Datumstransformationen können nur für ordnungsgemäß formatierte Datumswerte verwendet werden. Informationen zum Formatieren von Daten finden Sie in der Hilfe zu Common Data Service.  
  
<a name="BKMK_AddToDate"></a>   
## <a name="add-to-date"></a>Hinzufügen zum Datum  
 Fügt einem Datum eine bestimmte Anzahl von Tagen, Monaten und Jahren hinzu.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Datum|Datumszeichenfolge, die geändert werden soll.|  
|Offset für das Jahr|Positiver oder negativer Wert, der einer Jahreskomponente eines Eingabedatums hinzugefügt wird.|  
|Offset für den Monat|Positiver oder negativer Wert, der einer Monatskomponente eines Eingabedatums hinzugefügt wird.|  
|Offset für den Tag.|Positiver oder negativer Wert, der einer Tagkomponente eines Eingabedatums hinzugefügt wird.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Neues Datum|Neue Datenzeichenfolge, die Tag, Monat, und Jahr in dieser Reihenfolge hinzugefügt enthält.|  
  
<a name="BKMK_AdjustCurrentDate"></a>   
## <a name="adjust-current-date-and-set-time"></a>Anpassen des aktuellen Datums und Festlegen der Zeit  
 Fügt dem aktuellen Datum eine angegebene Anzahl von Tagen, Monaten und Jahren hinzu und legt die angegebene Uhrzeit fest. Die Offsets können nur ganze Zahlen sein.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Offset für das Jahr.|Positiver oder negativer Wert, der einer Jahreskomponente eines aktuellen Datums hinzugefügt wird.|  
|Offset für den Monat|Positiver oder negativer Wert, der einer Monatskomponente eines aktuellen Datums hinzugefügt wird.|  
|Offset für den Tag|Positiver oder negativer Wert, der einer Tageskomponente eines aktuellen Datums hinzugefügt wird.|  
|Stunden|Wert, der verwendet wird, um die Stundenkomponente des aktuellen Datums festzulegen.|  
|Minuten|Wert, der verwendet wird, um die Minutenkomponente des aktuellen Datums festzulegen.|  
|Sekunden|Wert, der verwendet wird, um die Sekundenkomponente des aktuellen Datums festzulegen.|  
|Wochentag|Wochentag, der Montag, Dienstag, Mittwoch, Donnerstag, Freitag, Samstag oder Sonntag sein kann. Die Wochentage werden von ganzen Zahlen, beginnend mit der Dezimalstellen 1 für Montag, dargestellt. Die Werte für Wochentage sind in der `DayOfWeek`-Enumeration enthalten. Weitere Informationen über diese Enumeration finden Sie im MSDN-Thema [DayOfWeekEnumeration](https://msdn.microsoft.com/library/system.dayofweek.aspx). <br />Wenn das berechnete aktuelle Datum nicht dem angegebene Wochentag entspricht, wird es auf das nächst frühere Datum angepasst, das auf den angegebenen Wochentag fällt. Das aktuelle Datum wird stets auf ein Datum in der Vergangenheit angepasst. <br />Wenn Sie z. B. Mittwoch als ein Wochentag angeben, und das neu berechnete Datum fällt auf Dienstag, den 9. März, wird das Datum auf Mittwoch, den 3. März angepasst.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Neues Datum|Neue Datenzeichenfolge, die Tag, Monat, und Jahr in dieser Reihenfolge hinzugefügt enthält.|  
  
<a name="BKMK_AdvancedAdd"></a>   
## <a name="advanced-add-to-current-date"></a>Erweitertes Hinzufügen zum aktuellen Datum  
 Fügt dem aktuellen Datum eine angegebene Anzahl von Tagen, Monaten und Jahren hinzu. Sie können angeben, ob Offsets relativ zum aktuellen Datum oder zu absoluten Werten sind. Die Offsets können nur ganze Zahlen sein.  
  
 Wenn Sie beispielsweise den absoluten Wert 3 für einen Monatsoffset verwenden, ist neu berechnete Monat März Wenn Sie ein relatives zu aktuellem Datumsmonatsoffset auf 3 festlegen und der aktuelle Monat April ist, ist der neu berechnete Monat Juli.  
  
|Eingabeparameter|Beschreibung|  
|----------------------|-----------------|  
|Offset für das Jahr|Positiver oder negativer Wert, der einer Jahreskomponente eines aktuellen Datums oder absoluten Jahres hinzugefügt wird.|  
|Offsetmodus für das Jahr.|Legen Sie fest, ob der Offset relativ zum aktuellen Datum oder ein absoluter Wert ist, indem Sie das Attribut `TransformationParameterMapping.Data` verwenden. Bei Nutzung von Typen mit früher Bindung, können Sie die `TransformationOffsetMode`-Enumeration verwenden, um relativen oder absoluten Offset anzugeben. Eine Liste der DataTypeCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität. Zum Anzeigen der Entitätsmetadaten für Ihre Organisation installieren Sie die Metadatenbrowserlösung, die in [Durchsuchen der Metadaten für Ihre Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata) beschrieben ist. Sie können die Referenzdokumentation für Entitäten auch in der [Entitätsreferenz](/dynamics365/customer-engagement/developer/about-entity-reference) durchsuchen.  
|Offset für den Monat|Positiver oder negativer Wert, der einer Monatskomponente eines aktuellen Datums oder absoluten Monats hinzugefügt wird.|  
|Offsetmodus für den Monat.|Legen Sie fest, ob der Offset relativ zum aktuellen Datum oder ein absoluter Wert ist, indem Sie das Attribut `TransformationParameterMapping.Data` verwenden. Bei Nutzung von Typen mit früher Bindung, können Sie die `TransformationOffsetMode`-Enumeration verwenden, um relativen oder absoluten Offset anzugeben. Eine Liste der DataTypeCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität.|  
|Offset für den Tag.|Positiver oder negativer Wert, der einer Tageskomponente eines aktuellen Datums oder absoluten Tages hinzugefügt wird.|  
|Offsetmodus für den Tag.|Legen Sie fest, ob der Offset relativ zum aktuellen Datum oder ein absoluter Wert ist, indem Sie das Attribut `TransformationParameterMapping.Data` verwenden. Bei Nutzung von Typen mit früher Bindung, können Sie die `TransformationOffsetMode`-Enumeration verwenden, um relativen oder absoluten Offset anzugeben. Eine Liste der DataTypeCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität.|  
|Stunden|Wert, der die Stundenkomponente des aktuellen Datums festlegt.|  
|Minuten|Wert, der die Minutenkomponente des aktuellen Datums festlegt.|  
|Sekunden|Wert, der die Sekundenkomponente des aktuellen Datums festlegt.|  
  
|Ausgabeparameter|Beschreibung|  
|-----------------------|-----------------|  
|Neues Datum|Neue Datenzeichenfolge, die Tag, Monat, und Jahr in dieser Reihenfolge hinzugefügt enthält. Zunächst werden die relativen Komponenten hinzugefügt, und anschließend werden die absoluten Werte verwendet, um ein Datum zu bilden.|  

### <a name="see-also"></a>Siehe auch

[Importieren von Daten](import-data.md)<br />
[Vorbereiten einer Quelldatei für den Import](prepare-source-files-import.md)<br />
[Erstellen von Datenzuordnungen für den Import](create-data-maps-for-import.md)<br />
[Konfiguration des Datenimports](configure-data-import.md)<br />
[Ausführen des Datenimports](run-data-import.md)<br />
[Datenimportentitäten](data-import-entities.md)<br />
[Beispiel: Exportieren und Importieren einer Datenzuordnung](org-service/samples/export-import-data-map.md)<br />
[Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](org-service/samples/import-data-complex-data-map.md)<br />