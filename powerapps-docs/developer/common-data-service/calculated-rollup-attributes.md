---
title: Berechnete und Rollupattribute (Common Data Service) | Microsoft-Dokumente
description: Erfahren Sie über die allgemeinen Elemente und Parameter, berechnete Attribute, Rollupattribute, rufen Sie einen berechneten Rollupfeldwert und SourceTypeMasks-Enumeration sofort ab.
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
ms.openlocfilehash: 826e535e823ffa433816c7d97a2e4aded7c51309
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753042"
---
# <a name="calculated-and-rollup-attributes"></a>Berechnete und Rollupattribute

*Berechnete* und *Rollup*-Attribute befreien den Benutzer von manuellen Berechnungen und lassen ihn sich auf die Arbeit konzentrieren. Systemadministratoren können jetzt ein Feld leicht definieren, das den Wert vieler allgemeiner Berechnungen enthält, ohne mit einem Entwickler arbeiten zu müssen. Entwickler können die Plattformfunktionen auch dazu nutzen, diese Berechnungen anzustellen, anstatt dies im eigenen Code zu tun.  
  
 [Video: Rollup und berechnete Felder in Microsoft Dynamics CRM 2015](https://youtu.be/RoahCH1p3T8)  
  
<a name="BKMK_CommonElements"></a>   
## <a name="common-elements-and-characteristics"></a>Gemeinsame Elemente und Eigenschaften  
 Berechnete und Rollupattribute haben einige gemeinsame Elementeund Eigenschaften, z. B.:  
  
- Sie sind schreibgeschützt.  
  
- Sie sind nicht für den Benutzer spezifsich. Die berechnung wird mit einem Systembenutzerkontos ausgeführt, sodass die Werte auf Datensätz basieren können, für die der Benutzer ansonsten nicht über Rechte zum Angezeigen verfügt, wie Attribute, für die die Sicherheit auf Feldebene aktiviert ist.  
  
  Alle Attribute, die von <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> erben, haben eine Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SourceType>, die die Werte enthalten kann, die in der folgenden Tabelle aufgeführt sind.  
  
|                 Value                 |                                    Beschreibung                                     |
|---------------------------------------|------------------------------------------------------------------------------------|
| Null |       Kein gültiger Typ für ein zu berechnendes Attribut, oder Rollupattribut.        |
|                   0                   | Einfaches Attribut. Das Attribut ist nicht als berechnetes oder Rollupattribut definiert. |
|                   1                   |                                Beechnetes Attribut                                |
|                   2                   |                                  Rollup-Attribut                                  |
  
 Berechnete und Rollupattribute basieren auf vorhandenen Attributtypen, die von <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> erben. Die folgenden Typen von Attribute haben neue Eigenschaften:  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.BooleanAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.DecimalAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.IntegerAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata>  
  
  Jeder dieser Typen von Attributen hat die folgenden Eigenschaften, um von Berechnungen und Rollups zu unterstützen.  
  
|      Eigenschaft       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Definition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FormulaDefinition` |                                                                                                                                                                                                                                                                                                                                                                                                                                                                   Enthält die XAML-Definition der Formel, die verwendet wird, um die Berechnung oder den Rollup auszuführen. Die einzige unterstützte Möglichkeit, dies zu ändern, ist durch den Anwendungsformeleditor.<br /><br /> Informationen zum Konfigurieren der Formeln für diese Attribute finden Sie in den folgenden Themen im Anpassungs-Handbuch: [Definieren der Rollupfelder](https://technet.microsoft.com/library/dn832162.aspx) und [Definieren berechneter Felder](https://technet.microsoft.com/library/dn832103.aspx).                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|  `SourceTypeMask`   | Der Bitmaskenwert dieser schreibgeschützten Eigenschaft beschreibt die Typen von Quellen, die in der Formel des berechneten Attributs verwendet wird, wenn die Formel eines berechneten Rollupattributs ungültig ist.<br /><br /> -   0: **Nicht definiert**. Der Standardwert für einfache und Rollupattribute.<br />-   1: **Einfach**. Das berechnete Attribut bezieht sich auf ein Attribut im gleichen Datensatz.<br />-   2: **Verknüpft**. Das berechnete Attribut bezieht sich auf ein Attribut im verknüpften Datensatz.<br />-   4: `Logical`. Das berechnete Attribut bezieht sich auf ein Attribut im gleichen Datensatz, das aktuell in einer anderen Datenbanktabelle gespeichert ist. Weitere Informationen [Logische Attribute](/dynamics365/customer-engagement/developer/introduction-to-entity-attributes#BKMK_LogicalAttributes)<br />-   8: `Calculated`. Das berechnete Attribut bezieht sich auf ein anderes berechnetes Attribut.<br />-   16: `Rollup`. Das berechnete Attribut verweist auf ein Rollupattribut.<br />-   32: `Invalid`. Die berchnete oder Rollupfeld ist ungültig.<br />     In der Regel würde dies auftreten, wenn ein Feld auf ein Attribut verweist, das nicht mehr vorhanden ist. **Anmerkung:** Eine oder mehrere dieser Bedingungen können für ein beliebiges berechnetes oder Rollupfeld zutreffen. Da dies ein Bitmaskenwert ist, finden Sie es möglicherweise hilfreich, [SourceTypeMasks-Enumeration](calculated-rollup-attributes.md#BKMK_SourceTypeMasks) zu verwenden, wenn Sie bitweise Vorgänge ausführen. |
  
<a name="BKMK_Calculated"></a>   
## <a name="calculated-attributes"></a>Beechnete Attribute  
 Berechnete Attribute werden in Echtzeit berechnet , sobald sie abgerufen werden. Berechnete Attribute können mithilfe verschiedener Datentypen verfasst werden. Beispielsweise kann ein ganzzahliges berechnetes Attribut auf Werte von den Dezimalzahl- oder Währungsattributen verweisen. Weitere Informationen: [Definieren berechneter Felder](https://technet.microsoft.com/library/dn832103.aspx)  
  
 Berechnete Attributwerte sind sind in der Plug-in-Abruf-Pipeline verfügbar. Bild des Entitätsdatensatzes aktualisieren oder erstellen enthält oder den berechneten Attributwert in Phase 40. Weitere Informationen: [Ereignisausführungs-Pipeline](event-framework.md#event-execution-pipeline) und [Entitäts-Bilder](understand-the-data-context.md#entity-images)
  
### <a name="limitations"></a>Einschränkungen  
 Sie können die Werte in berechneten Attributen, die auf eine verknüpfte Entität, ein anderes berechnetes Attribut oder einen *logischen Wert* in der gleichen Entität verweisen, nicht verwenden, um die Daten zu sortieren, die durch eine Abfrage zurückgegeben werden. Obwohl der Abfrage angeben kann, dass die Ergebnisse mithilfe eines berechneten Attributes geordnet werden sollen, wird die Sortierreihenfolge ignoriert es wird kein Fehler ausgelöst. Wenn das berechnete Attribut nur auf einfache Werte im gleichen Datensatz verweist, funktioniert die Sortierung normal. Sie können die Quellen bestimmen, die in einem berechneten Feld verwendet werden, indem Sie die Eigenschaft `SourceTypeMask` auf den Attributmetadaten verwenden. Weitere Informationen [Logische Attribute](/dynamics365/customer-engagement/developer/introduction-to-entity-attributes.md#BKMK_LogicalAttributes)  
  
 Nur Attribute von einer unmittelbar übergeordneten Entität können in einem berechneten Attribut verwendet werden.  
  
 Gespeicherte Abfragen, Diagramme und Visualisierungen können über maximal 10 eindeutige berechnete Attribute verfügen.  
  
 Berechnete Attribute können auf andere berechnete Attribute in ihrer Formel verweisen, sie können jedoch nicht auf sich selbst verweisen.  
  
 Berechnete Attribute haben keine Werte, wenn ein Benutzer mit Dynamics 365 for Outlook sich im Offlinemodus befindet.  
  
 `MaxValue` und `MinValue`-Metadateneigenschaften können nicht auf berechnete Attribute festgelegt werden.  
  
<a name="BKMK_Rollup"></a>   
## <a name="rollup-attributes"></a>Rollup-Attribute  
 Da Rollupattribute in der Datenbank weiter bestehen, können sie zum Sortieren oder Filtern genauso wie regulären Attribute verwendet werden. Eine Art von Prozess oderPlug-in verwendet den letzten berechneten Wert des Attributs. Rollupattributwerte werden asynchron durch geplante Systemaufträge berechnet. Administratoren legen fest, wann ein Auftrag ausgeführt wird, oder sie halten den Auftrag an. Standardmäßig wird jedes Attribut stündlich aktualisiert. Weitere Informationen: [Definieren der Rollupfelder](https://technet.microsoft.com/library/dn832103.aspx)  
  
 Wenn ein Rollupattribut erstellt oder aktualisiert wird, wird ein Auftrag **Massenberechnen von Rollupfeldern** geplant, um in 12 Stunden ausgeführt zu werden. Die 12-stündige Verzögerung dient dazu, diesen ressourcenintensiven Vorgang zu einer Zeit auszuführen, in der die Benutzer am wenigsten betroffen sind. Wenn der Vorgang abgeschlossen ist, wird automatisch geplant, ihn in 10 Jahren in der Zukunft auszuführen. Liegt ein Problem mit der Berechnung vor, wird dieses mit dem Systemauftrag gemeldet. Suchen Sie den Systemauftrag in **Einstellungen** > **Systemaufträge**, um irgendwelche Fehler bei Rollupfeldern zu finden.  
  
> [!TIP]
>  Als Entwickler, der eine Lösung in einer Entwicklungsumgebung testet, sollten Sie nicht 12 Stunden warten. Sie können dies beschleunigen. In der Liste **Systemaufträge** verwenden Sie die Ansicht **Seriensystemaufträge**, um die Liste zu feltern und den Auftrag **Massenberechnen von Rollupfeldern** zu suchen. Wenn der Auftrag ausgewählt ist, verwenden Sie **Weitere Aktionen** > **Später durchführen**, und legen Sie die Uhrzeit, die bald kommt, fest.  
>   
>  Wenn Sie die Erstellung eines neuen Auftrag **Massenberechnete Rollupfelder** programmgesteuert auslösen möchten, rufen Sie das Rollupattribut für <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> mit <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest> ab und verwenden Sie <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest>, um das Attribut zu aktualisieren, ohne Änderungen vorzunehmen.  
  
 Der Auftrag **Massenberechnete Rollupfelder** triit auf, sobald eine Lösung, die Rollupattribut enthält, importiert wird. Dabei wird davon ausgegangen, dass Sie eine Lösung in einer Zeit installieren, die sich auf Benutzer nicht nachteilig auswirkt.  
  
 Jedes Rollupattribut für eine Entität enthält auch zwei unterstützende Attribute für das Rollupattribut:  
  
- *\<attribute SchemaName>* `_Date`: DateTime – Wann der Rollup zuletzt berechnet wurde.  
  
- *\<attribute SchemaName>* `_State`: Ganze Zahl – Der Status der Rollupberechnung. Weitere Informationen: [Rollupzustandswerte](calculated-rollup-attributes.md#BKMK_RollupStateValues)  
  
<a name="BKMK_RollupStateValues"></a>   
### <a name="rollup-state-values"></a>Rollupstatuswerte  
 Der Status der Rollupfeldberechnung ist im entsprechenden Attribut *\<attribute SchemaName>*`_State` und in der <xref:Microsoft.Crm.Sdk.Messages.CalculateRollupFieldResponse>.`FieldState`- -Eigenschaft verfügbar. Werte, die den Status angeben, sind in der folgenden Tabelle aufgeführt.  
  
|Statuswert|Beschreibung|  
|-----------------|-----------------|  
|0|`NotCalculated`: Der Attributwert muss noch berechnet werden.|  
|1|`Calculated`: Der Attributwert wurde anhand der letzten Aktualisierungszeit im Attribut *\<attribute SchemaName>*`_Date` berechnet.|  
|2|`OverflowError`: Attributwertberechnung führte zu einem Überlauffehler.|  
|3|`OtherError`: Die Attributwertberechnung schlug aufgrund eines internen Fehlers fehl, die nächste Ausführung des Berechnungsauftrags wird dies wahrscheinlich beheben.|  
|4|`RetryLimitExceeded`: Die Attributwertberechnung schlug fehl, weil die maximale Anzahl von Wiederholungsversuchen, den Wert zu berechnen, wahrscheinlich aufgrund der großen Anzahl von Parallelitäts- und Sperrkonflikten, überschritten wurde.|  
|5|`HierarchicalRecursionLimitReached`: Die Attributwertberechnung schlug fehl, da die maximale Hierarchientiefengrenze für die Berechnung erreicht wurde.|  
|6|`LoopDetected`: Die Attributwertberechnung schlug fehl, da eine Schleife in der Hierarchie des Datensatzes erkannt wurde.|  
  
### <a name="retrieve-a-calculated-rollup-field-value-immediately"></a>Den Wert eines berechneten Rollupfeldwert sofort abrufen  
 Rollupattribute unterstützen eine `CalculateRollupField`-Nachricht, die Entwickler verwenden können, um einen Rollupattributwert bei Bedarf zu berechnen. Die Anforderung und die Antwort, zusammen mit den Mitgliedern, sind in der folgenden Tabelle aufgeführt..  
  
|Anforderung/Antwort|Mitglieder|  
|-----------------------|-------------|  
|<xref:Microsoft.Crm.Sdk.Messages.CalculateRollupFieldRequest>|`Target`: <xref:Microsoft.Xrm.Sdk.EntityReference> für den Datensatz.<br /><br /> `FieldName`: Eine Zeichenfolge, die den logische Name des Attributs darstellt.|  
|<xref:Microsoft.Crm.Sdk.Messages.CalculateRollupFieldResponse>|`Entity`: <xref:Microsoft.Xrm.Sdk.Entity>, die das Rollupattribut und die unterstützenden *\<attribute SchemaName>*`_Date` und *\<attribute SchemaName>*`_State`-Attribute enthält.|  
  
 Diese Nachricht ist ein synchroner Vorgang für genau das Attribut, das in der Anforderung identifiziert wird. Wenn der Wert dieses Datensatzes als Teil anderer Rollupfelder enthalten ist, nehmen die Werte dieser Felder nicht die mögliche Wert,änderung an, die durch das Inbetrachtziehen dieser Methode verursacht wurden, bis die regelmäßig geplanten asynchronen Aufträge, die diese Berechnungen ausführen, auftreten.  
  
### <a name="limitations"></a>Einschränkungen  
 Rollupattribute können nicht als Workflowereignis oder Wartebedingung verwendet werden. Diese Attribute führen nicht zu dem Ereignis, Workflows auszulösen.  
  
 Die Attribute ModifiedBy und ModifiedOn für die Entität werden nicht aktualisiert, wenn das Rollupattribut aktualisiert wird.  
  
 Ein Maximum von 100 Rollupattributen kann innerhalb einer Organisation definiert werden. Jede Entität kann maximal 10 Rollupattribute haben.  
  
 Eine Rollupattributformel kann nicht auf ein anderes Rollupattribut verweisen.  
  
 Eine Rollupattributformel kann nicht auf komplexe berechnete Attribute verweisen. Nur berechnete Attribute, die auf einfache Attribute im gleichen Datensatz verweisen, können für Rollups verwendet werden.  
  
 Eine Rollupattributformel kann keine Datensätze in n:n-Beziehungen enthalten. Es kann nur Datensätze in 1: n-Beziehungen enthalten.  
  
 Rollupattributformeln können keine 1:n-Beziehung mit der Entität `ActivityPointer` oder `ActivityParty` verwenden.  
  
<a name="BKMK_SourceTypeMasks"></a>   
## <a name="sourcetypemasks-enumeration"></a>SourceTypeMasks-Enumeration  
 Die Eigenschaft `SourceTypeMask` für die Attribute, die berechnete und Rollupfelder unterstützen, enthält einen Bitmaskenwert. Um die relevanten Informationen vo dem Wert zu extrahieren, ist es hilfreich, diese Enumeration zu besitzen, wenn Sie bitweise Vorgänge ausführen. Verwenden Sie die folgende `SourceTypeMasks`-Enumeration, wenn Sie den `SourceTypeMask`-Eigenschaftswert vergleichen.  
  
```csharp  
 public enum SourceTypeMasks  
{  
    /// <summary>  
    /// Undefined: 0 - The default value for simple and rollup attributes.  
    /// </summary>  
    Undefined = 0,  
    /// <summary>  
    /// Simple: 1 - The calculated attribute refers to an attribute in the same record.  
    /// </summary>  
    Simple = 1,  
    /// <summary>  
    /// Related: 2 - The calculated attribute refers to an attribute in a related record.  
    /// </summary>  
    Related = 2,  
    /// <summary>  
    /// Logical: 4 - The calculated attribute refers to a logical attribute.  
    /// </summary>  
    Logical = 4,  
    /// <summary>  
    /// Calculated: 8 - The calculated attribute refers to another calculated attribute.  
    /// </summary>  
    Calculated = 8,  
    /// <summary>  
    /// Rollup: 16 - The calculated attribute refers a rollup attribute.   
    /// </summary>  
    Rollup = 16,  
    /// <summary>  
    /// Invalid: 32 - The calculated or rollup attribute is invalid.  
    /// Typically this would be where a field refers to an attribute that no longer exists.   
    /// </summary>  
    Invalid = 32  
}  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Video: Rollup und berechnete Felder in Microsoft Dynamics CRM 2015](https://youtu.be/RoahCH1p3T8)   
 [Einführung in die Entitätsattribute](/dynamics365/customer-engagement/developer/introduction-to-entity-attributes)   
 [Definieren berechneter Felder](https://technet.microsoft.com/library/dn832103.aspx)   
 [Rollupfelder definieren](https://technet.microsoft.com/library/dn832103.aspx)
