# <a name="dataset"></a>DataSet

<!-- IDataSetExposedParameter  -->

[!INCLUDE [dataset-description](includes/dataset-description.md)]

## <a name="addcolumn"></a>addColumn

Die Funktion, um eine Spalte dem Dataset hinzuzufügen

**Typ**: `function`<br />
**Optional**

### <a name="remarks"></a>Anmerkungen

Diese Funktion muss zwei Parameter akzeptieren.

|Name|Typ|Erforderlich|Beschreibung|
|-|-|-|-|
|Name|Zeichenfolge|Ja|Der dem Dataset hinzuzufügende Spaltenname,|
|entityalias|Zeichenfolge|Nein| Alias, für den der Spaltenname hinzugefügt werden muss|

## <a name="columns"></a>columns

Der Satz von Spalten, die in diesem Dataset verfügbar sind.

**Typ**: [Spalte](column.md)[]

## <a name="error"></a>Fehler

Ob ein Fehler im Datenabruf aufgetreten ist.

**Typ**: `boolean`

## <a name="errormessage"></a>errorMessage

Die Fehlermeldung im Zusammenhang mit dem letzten aufgetretenen Fehler.

**Typ**: `string`

## <a name="filtering"></a>Filterung

Platzhalterbeschreibung: IDataSetExposedParameter.name
<!-- 
QUESTION: This description doesn't seem right
'The column sorting for the current query.' 
-->

**Typ**: [Filterung](filtering.md)

## <a name="linking"></a>Verknüpfung

Platzhalterbeschreibung: IDataSetExposedParameter.name

**Typ**: [Verknüpfung](linking.md)

## <a name="loading"></a>Laden

Ob der Datensatz geladen wird.

**Typ**: `boolean`

## <a name="paging"></a>Auslagern

Status vom Blättern und von Aktionen.

**Typ**: [Blättern](paging.md)

## <a name="records"></a>Datensätze

Zuordnen der IDs zum gesamten Datensatzobjekt

**Typ**: `object`

## <a name="sortedrecordids"></a>sortedRecordIds

IDs der Datensätze im Dataset, in Reihenfolge.

**Typ**: `string[]`

## <a name="sorting"></a>Sortierung

Die Spaltensortierung für die aktuelle Abfrage.

**Typ**: [Sortieren](sortstatus.md)

## <a name="methods"></a>Methoden

|Methode | Beschreibung | 
| ------------- |-------------|
|[clearSelectedRecordIds](dataset/clearselectedrecordids.md)|[!INCLUDE [clearselectedrecordids-description](dataset/includes/clearselectedrecordids-description.md)]| 
|[getSelectedRecordIds](dataset/getselectedrecordids.md)|[!INCLUDE [getselectedrecordids-description](dataset/includes/getselectedrecordids-description.md)]| 
|[getTargetEntityType](dataset/gettargetentitytype.md)|[!INCLUDE [gettargetentitytype-description](dataset/includes/gettargetentitytype-description.md)]| 
|[getTitle](dataset/gettitle.md)|[!INCLUDE [gettitle-description](dataset/includes/gettitle-description.md)]| 
|[getViewId](dataset/getviewid.md)|[!INCLUDE [getviewid-description](dataset/includes/getviewid-description.md)]| 
|[openDatasetItem](dataset/opendatasetitem.md)|[!INCLUDE [opendatasetitem-description](dataset/includes/opendatasetitem-description.md)]| 
|[Aktualisieren](dataset/refresh.md)|[!INCLUDE [refresh-description](dataset/includes/refresh-description.md)]| 
|[setSelectedRecordIds](dataset/setselectedrecordids.md)|[!INCLUDE [setselectedrecordids-description](dataset/includes/setselectedrecordids-description.md)]| 


### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)