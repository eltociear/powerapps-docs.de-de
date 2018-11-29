---
title: Steuerelemente in modellgesteuerten Apps für Dynamics 365 | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
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
<li>[addNotification](controls/addNotification.md)</li>
<li>[clearNotification](controls/clearNotification.md)</li>
<li>[getAttribute](controls/getAttribute.md)</a></li>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[setDisabled](controls/setDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setNotification](controls/setNotification.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
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
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getInitialUrl](controls/getInitialUrl.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getObject](controls/getObject.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getSrc](controls/getSrc.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[setDisabled](controls/setDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setSrc](controls/setSrc.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
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
<li>[addOnPostSearch](controls/addOnPostSearch.md)</li>
<li>[addOnResultOpened](controls/addOnResultOpened.md)</li>
<li>[addOnSelection](controls/addOnSelection.md)</li>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getParent](controls/getParent.md)</li>
<li>[getSearchQuery](controls/getSearchQuery.md)</li>
<li>[getSelectedResults](controls/getSelectedResults.md)</li>
<li>[getTotalResultCount](controls/getTotalResultCount.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[openSearchResult](controls/openSearchResult.md)</li>
<li>[removeOnPostSearch](controls/removeOnPostSearch.md)</li>

</ul>
</td>
<td>
<ul>
<li>[removeOnResultOpened](controls/removeOnResultOpened.md)</li>
<li>[removeOnSelection](controls/removeOnSelection.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setSearchQuery](controls/setSearchQuery.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
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
<li>[addCustomFilter](controls/addCustomFilter.md)</li>
<li>[addCustomView](controls/addCustomView.md)</li>
<li>[addNotification](controls/addNotification.md)</li>
<li>[addPreSearch](controls/addPreSearch.md)</li>
<li>[clearNotification](controls/clearNotification.md)</li>
<li>[getAttribute](controls/getAttribute.md)</a></li>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDefaultView](controls/getDefaultView.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getEntityTypes](controls/getEntityTypes.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[removePreSearch](controls/removePreSearch.md)</li>
<li>[setDefaultView](controls/setDefaultView.md)</li>

</ul>
</td>
<td>
<ul>
<li>[setDisabled](controls/setDisabled.md)</li>
<li>[setEntityTypes](controls/setEntityTypes.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setNotification](controls/setNotification.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
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
<li>[addNotification](controls/addNotification.md)</li>
<li>[addOption](controls/addOption.md)</li>
<li>[clearNotification](controls/clearNotification.md)</li>
<li>[clearOptions](controls/clearOptions.md)</li>
<li>[getAttribute](controls/getAttribute.md)</a></li>
<li>[getControlType](controls/getControlType.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[removeOption](controls/removeoption.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setDisabled](controls/setDisabled.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setNotification](controls/setNotification.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="quickform-control-type"></a>Schnellformular-Steuerelementtype

Informationen zu Methoden, die für diesen Steuerelementtyp unterstützt werden, finden Sie unter [formContext.ui.quickForms](formcontext-ui-quickforms.md).

## <a name="subgrid-control-type"></a>Unterraster-Steuerelementtyp

Informationen zu Methoden, die für diesen Steuerelementtyp unterstützt werden, finden Sie unter [Raster und Unterraster](grids.md).

## <a name="timelinewall-control-type"></a>Zeitplan-Steuerelementtyp

Das Zeitplansteuerelement ist ein neuer Steuerelementtyp, der in modellgesteuerten Apps (online), Version 9.0 eingeführt wurde, wobei die Nachrichten, die Aktivitäten und Anmerkungen in einer einheitlichen Ansicht dargestellt werden. Das sind die Methoden, die für diesen Steuerelementtyp verfügbar sind.

<table>
<tr>
<td>
<ul>
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>

<li>[getParent](controls/getParent.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[Aktualisieren](controls/refresh.md)</li>
<li>[setDisabled](controls/setDisabled.md)</li>
</ul>
</td>
<td>
<ul>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
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
<li>[getControlType](controls/getControlType.md)</li>
<li>[getDisabled](controls/getDisabled.md)</li>
<li>[getLabel](controls/getLabel.md)</li>
<li>[getName](controls/getName.md)</li>
</ul>
</td>
<td>
<ul>

<li>[getParent](controls/getParent.md)</li>
<li>[getState](controls/getState.md)</li>
<li>[getVisible](controls/getVisible.md)</li>
<li>[Aktualisieren](controls/refresh.md)</li>

</ul>
</td>
<td>
<ul>
<li>[setDisabled](controls/setDisabled.md)</li>
<li>[setFocus](controls/setFocus.md)</li>
<li>[setLabel](controls/setLabel.md)</li>
<li>[setVisible](controls/setVisible.md)</li>
</ul>
</td>
</tr>
</table>

## <a name="webresource-control-type"></a>Webressourcen-Steuerelementtyp

Ein Webressourcesteuerelement hat denselben Satz von Methoden wie das Iframesteuerelement. Siehe [IFRAME-Steuerelementtyp](#iframe-control-type)

### <a name="related-topics"></a>Verwandte Themen

[Attribute](attributes.md)