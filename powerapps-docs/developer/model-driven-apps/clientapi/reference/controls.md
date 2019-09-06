---
title: Steuerelemente in modellgesteuerten Apps für Dynamics 365 | MicrosoftDocs
ms.date: 08/12/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="controls-client-api-reference"></a>Steuerelemente (Client-API-Referenz)



Ein Steuerelement stellt ein HTML-Element dar, das im Formular vorhanden ist. Einige Steuerelemente sind an ein spezifisches Attribut gebunden, während andere ungebundene Steuerelemente darstellen können, z. B. einen IFRAME, eine Webressource oder ein Unterraster, der/die/das für das Formular hinzugefügt wurde. 

Das **Steuerelement**-Objekt bietet Methoden, um die Darstellung und das Verhalten eines Steuerelements zu ändern und das entsprechende Attribut zu identifizieren. Der Zugriff auf Steuerelemente erfolgt mit einer folgenden Sammlungen: 
- **formContext.ui.controls**
- **formContext.ui Section.controls**
- **formContext.data.entity** **Attribute.controls**

Die **formContext**.[getControl](controls/getControl.md)-Methode ist eine Verknüpfung für den Zugriff auf **formContext.ui.controls.get**. 

Steuerelemente werden nach Typ kategorisiert. Sie können den Typ eines Steuerelements feststellen, indem Sie die [getControlType](controls/getControlType.md)-Methode verwenden. Bestimmte Steuerungsmethoden sind nur für spezifische Steuerelementtypen verfügbar.

Dieses Thema enthält Informationen zu den Methoden, die pro Steuerelementtyp verfügbar sind. 

## <a name="standard-control-type"></a>Standardsteuerelementtyp

Das sind die Methoden, die für ein Standardsteuerelement verfügbar sind.

<table>
<tr>
<td>
<ul>
<li><a href="controls/addNotification.md" data-raw-source="[addNotification](controls/addNotification.md)">addNotification</a></li>
<li><a href="controls/clearNotification.md" data-raw-source="[clearNotification](controls/clearNotification.md)">clearNotification</a></li>
<li><a href="controls/getAttribute.md" data-raw-source="[getAttribute](controls/getAttribute.md)">getAttribute</a></a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setNotification.md" data-raw-source="[setNotification](controls/setNotification.md)">setNotification</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

Die folgenden Methoden für das Standardsteuerelement sind [veraltet](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) in dieser Version: addOnKeyPress, fireOnKeyPress und removeOnKeyPress.

## <a name="iframe-control-type"></a>IFRAME-Steuerelementtyp

Das sind die Methoden, die für ein IFRAME-Steuerelement verfügbar sind.

<table>
<tr>
<td>
<ul>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getInitialUrl.md" data-raw-source="[getInitialUrl](controls/getInitialUrl.md)">getInitialUrl</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getObject.md" data-raw-source="[getObject](controls/getObject.md)">getObject</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getSrc.md" data-raw-source="[getSrc](controls/getSrc.md)">getSrc</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setSrc.md" data-raw-source="[setSrc](controls/setSrc.md)">setSrc</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

## <a name="kbsearch-knowledge-base-search-control-type"></a>kbsearch (Knowledge base search)-Steuerelementtyp

Das sind die Methoden, die für das Wissendatenbank-Suchsteuerelement verfügbar sind.

<table>
<tr>
<td>
<ul>
<li><a href="controls/addOnPostSearch.md" data-raw-source="[addOnPostSearch](controls/addOnPostSearch.md)">addOnPostSearch</a></li>
<li><a href="controls/addOnResultOpened.md" data-raw-source="[addOnResultOpened](controls/addOnResultOpened.md)">addOnResultOpened</a></li>
<li><a href="controls/addOnSelection.md" data-raw-source="[addOnSelection](controls/addOnSelection.md)">addOnSelection</a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getSearchQuery.md" data-raw-source="[getSearchQuery](controls/getSearchQuery.md)">getSearchQuery</a></li>
<li><a href="controls/getSelectedResults.md" data-raw-source="[getSelectedResults](controls/getSelectedResults.md)">getSelectedResults</a></li>
<li><a href="controls/getTotalResultCount.md" data-raw-source="[getTotalResultCount](controls/getTotalResultCount.md)">getTotalResultCount</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/openSearchResult.md" data-raw-source="[openSearchResult](controls/openSearchResult.md)">openSearchResult</a></li>
<li><a href="controls/removeOnPostSearch.md" data-raw-source="[removeOnPostSearch](controls/removeOnPostSearch.md)">removeOnPostSearch</a></li>

</ul>
</td>
<td>
<ul>
<li><a href="controls/removeOnResultOpened.md" data-raw-source="[removeOnResultOpened](controls/removeOnResultOpened.md)">removeOnResultOpened</a></li>
<li><a href="controls/removeOnSelection.md" data-raw-source="[removeOnSelection](controls/removeOnSelection.md)">removeOnSelection</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setSearchQuery.md" data-raw-source="[setSearchQuery](controls/setSearchQuery.md)">setSearchQuery</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

>[!NOTE]
>Wenn das Wissensdatenbank-Suchsteuerelement dem sozialen Bereich hinzugefügt wird, ist der Name des Steuerelements „searchwidgetcontrol_notescontrol”. Dieser Name kann nicht geändert werden. 

## <a name="lookup-control-type"></a>lookup-Steuerelementtyp

Das sind die Methoden, die für ein Lookup-Steuerelement verfügbar sind.

<table>
<tr>
<td>
<ul>
<li><a href="controls/addCustomFilter.md" data-raw-source="[addCustomFilter](controls/addCustomFilter.md)">addCustomFilter</a></li>
<li><a href="controls/addCustomView.md" data-raw-source="[addCustomView](controls/addCustomView.md)">addCustomView</a></li>
<li><a href="controls/addNotification.md" data-raw-source="[addNotification](controls/addNotification.md)">addNotification</a></li>
<li><a href="controls/addPreSearch.md" data-raw-source="[addPreSearch](controls/addPreSearch.md)">addPreSearch</a></li>
<li><a href="controls/clearNotification.md" data-raw-source="[clearNotification](controls/clearNotification.md)">clearNotification</a></li>
<li><a href="controls/getAttribute.md" data-raw-source="[getAttribute](controls/getAttribute.md)">getAttribute</a></a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDefaultView.md" data-raw-source="[getDefaultView](controls/getDefaultView.md)">getDefaultView</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getEntityTypes.md" data-raw-source="[getEntityTypes](controls/getEntityTypes.md)">getEntityTypes</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/removePreSearch.md" data-raw-source="[removePreSearch](controls/removePreSearch.md)">removePreSearch</a></li>
<li><a href="controls/setDefaultView.md" data-raw-source="[setDefaultView](controls/setDefaultView.md)">setDefaultView</a></li>

</ul>
</td>
<td>
<ul>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
<li><a href="controls/setEntityTypes.md" data-raw-source="[setEntityTypes](controls/setEntityTypes.md)">setEntityTypes</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setNotification.md" data-raw-source="[setNotification](controls/setNotification.md)">setNotification</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

## <a name="multiselectoptionset-and-optionset-control-types"></a>MultiSelectOptionSet- und OptionSet-Steuerelementtypen

Sowohl Mehrfachauswahloptionssatz- als auch Optionssatz-Steuerelemente haben denselben Satz der verfügbaren Methoden.

<table>
<tr>
<td>
<ul>
<li><a href="controls/addNotification.md" data-raw-source="[addNotification](controls/addNotification.md)">addNotification</a></li>
<li><a href="controls/addOption.md" data-raw-source="[addOption](controls/addOption.md)">addOption</a></li>
<li><a href="controls/clearNotification.md" data-raw-source="[clearNotification](controls/clearNotification.md)">clearNotification</a></li>
<li><a href="controls/clearOptions.md" data-raw-source="[clearOptions](controls/clearOptions.md)">clearOptions</a></li>
<li><a href="controls/getAttribute.md" data-raw-source="[getAttribute](controls/getAttribute.md)">getAttribute</a></a></li>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
<li><a href="controls/getOptions.md" data-raw-source="[getOptions](controls/getOptions.md)">getOptions</a></li>
<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>

</ul>
</td>
<td>
<ul>
<li><a href="controls/removeoption.md" data-raw-source="[removeOption](controls/removeoption.md)">removeOption</a></li>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setNotification.md" data-raw-source="[setNotification](controls/setNotification.md)">setNotification</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>

</ul>
</td>
</tr>
</table>

## <a name="quickform-control-type"></a>Schnellformular-Steuerelementtype

Informationen zu Methoden, die für diesen Steuerelementtyp unterstützt werden, finden Sie unter [formContext.ui.quickForms](formcontext-ui-quickforms.md).

## <a name="subgrid-control-type"></a>Unterraster-Steuerelementtyp

Informationen zu Methoden, die für diesen Steuerelementtyp unterstützt werden, finden Sie unter [Raster und Unterraster](grids.md).

## <a name="timelinewall-control-type"></a>Zeitplan-Steuerelementtyp

Das Zeitplansteuerelement ist ein neuer Steuerelementtyp, der in Dynamics 365 for Customer Engagement-Apps, Version 9.0, eingeführt wurde, wobei die Nachrichten, die Aktivitäten und Anmerkungen in einer einheitlichen Ansicht dargestellt werden. Das sind die Methoden, die für diesen Steuerelementtyp verfügbar sind.

<table>
<tr>
<td>
<ul>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>

<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/refresh.md" data-raw-source="[refresh](controls/refresh.md)">Aktualisieren</a></li>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

## <a name="timer-control-type"></a>Zeitgeber-Steuerelementtyp

Das sind die Methoden, die für den Zeitgeber-Steuerelementtyp verfügbar sind.

<table>
<tr>
<td>
<ul>
<li><a href="controls/getControlType.md" data-raw-source="[getControlType](controls/getControlType.md)">getControlType</a></li>
<li><a href="controls/getDisabled.md" data-raw-source="[getDisabled](controls/getDisabled.md)">getDisabled</a></li>
<li><a href="controls/getLabel.md" data-raw-source="[getLabel](controls/getLabel.md)">getLabel</a></li>
<li><a href="controls/getName.md" data-raw-source="[getName](controls/getName.md)">getName</a></li>
</ul>
</td>
<td>
<ul>

<li><a href="controls/getParent.md" data-raw-source="[getParent](controls/getParent.md)">getParent</a></li>
<li><a href="controls/getState.md" data-raw-source="[getState](controls/getState.md)">getState</a></li>
<li><a href="controls/getVisible.md" data-raw-source="[getVisible](controls/getVisible.md)">getVisible</a></li>
<li><a href="controls/refresh.md" data-raw-source="[refresh](controls/refresh.md)">Aktualisieren</a></li>

</ul>
</td>
<td>
<ul>
<li><a href="controls/setDisabled.md" data-raw-source="[setDisabled](controls/setDisabled.md)">setDisabled</a></li>
<li><a href="controls/setFocus.md" data-raw-source="[setFocus](controls/setFocus.md)">setFocus</a></li>
<li><a href="controls/setLabel.md" data-raw-source="[setLabel](controls/setLabel.md)">setLabel</a></li>
<li><a href="controls/setVisible.md" data-raw-source="[setVisible](controls/setVisible.md)">setVisible</a></li>
</ul>
</td>
</tr>
</table>

## <a name="webresource-control-type"></a>Webressourcen-Steuerelementtyp

Ein Webressourcesteuerelement hat denselben Satz von Methoden wie das Iframesteuerelement. Siehe [IFRAME-Steuerelementtyp](#iframe-control-type)


### <a name="related-topics"></a>Verwandte Themen

[Attribute](attributes.md)
