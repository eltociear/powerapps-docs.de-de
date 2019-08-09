---
title: Attribute in modellgesteuerten Apps | MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden von Attributen in modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="attributes-client-api-reference"></a>Attribute (Client-API-Referenz)



Attribute enthalten Daten im modellgesteuerte Apps-Formular oder den -Rastern. Verwenden Sie die `formContext.data.entity.attributes`-Sammlung oder die `formContext.getAttribute`-Verknüpfungsmethode, um auf eine Sammlung von Attributen zuzugreifen. Weitere Informationen über die Sammlungen finden Sie unter [Sammlungen (Client-API-Referenz)](collections.md). 

Wenn Sie auf ein Attribut in der Sammlung zuzugreifen, verabschieden Sie entweder den Namen (die Zeichenfolge) oder den Indexwert (die Zahl) des Attributs als ein Argument an die Methode. Beispiel: '`formContext.getAttribute(arg)`'

Attribute werden nach Typ kategorisiert. Sie können den Typ eines Attributs feststellen, indem Sie die [getAttributeType](attributes/getAttributeType.md)-Methode verwenden. Bestimmte Attributmethoden sind nur für spezifische Attributtypen verfügbar.

Dieses Thema enthält Informationen zu den Methoden, die pro Attributtyp verfügbar sind. 

## <a name="all-attribute-types"></a>Alle Attributtypen

<table>
<tr>
<td>
<ul>
<li><a href="attributes/controls-collection.md" data-raw-source="[controls](attributes/controls-collection.md)">Steuerelemente</a></li>
<li><a href="attributes/addOnChange.md" data-raw-source="[addOnChange](attributes/addOnChange.md)">addOnChange</a></li>
<li><a href="attributes/fireOnChange.md" data-raw-source="[fireOnChange](attributes/fireOnChange.md)">fireOnChange</a></a></li>
<li><a href="attributes/getAttributeType.md" data-raw-source="[getAttributeType](attributes/getAttributeType.md)">getAttributeType</a></li>
<li><a href="attributes/getFormat.md" data-raw-source="[getFormat](attributes/getFormat.md)">getFormat</a></li>
<li><a href="attributes/getIsDirty.md" data-raw-source="[getIsDirty](attributes/getIsDirty.md)">getIsDirty</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="attributes/getName.md" data-raw-source="[getName](attributes/getName.md)">getName</a></li>
<li><a href="attributes/getParent.md" data-raw-source="[getParent](attributes/getParent.md)">getParent</a></li>
<li><a href="attributes/getRequiredLevel.md" data-raw-source="[getRequiredLevel](attributes/getRequiredLevel.md)">getRequiredLevel</a></li>
<li><a href="attributes/getSubmitMode.md" data-raw-source="[getSubmitMode](attributes/getSubmitMode.md)">getSubmitMode</a></li>
<li><a href="attributes/getUserPrivilege.md" data-raw-source="[getUserPrivilege](attributes/getUserPrivilege.md)">getUserPrivilege</a></li>
<li><a href="attributes/getValue.md" data-raw-source="[getValue](attributes/getValue.md)">getValue</a></li>
</ul>
</td>
<td>
<ul>

<li><a href="attributes/isValid.md" data-raw-source="[isValid](attributes/isValid.md)">isValid</a></li>
<li><a href="attributes/removeOnChange.md" data-raw-source="[removeOnChange](attributes/removeOnChange.md)">removeOnChange</a></li>
<li><a href="attributes/setRequiredLevel.md" data-raw-source="[setRequiredLevel](attributes/setRequiredLevel.md)">setRequiredLevel</a></li>
<li><a href="attributes/setSubmitMode.md" data-raw-source="[setSubmitMode](attributes/setSubmitMode.md)">setSubmitMode</a></li>
<li><a href="attributes/setValue.md" data-raw-source="[setValue](attributes/setValue.md)">setValue</a></li>
</ul>
</td>
</tr>
</table>


## <a name="boolean-attribute-type"></a>Boolescher Attributtyp
Zusätzlich zu den Methoden, die für alle Attributtypen verfügbar sind, wie früher erklärte wurde, ist die folgende Methode nur für das **boolean** Attribut verfügbar:

- [getInitialValue](attributes/getInitialValue.md)

## <a name="lookup-attribute-type"></a>Suchattributtyp
Zusätzlich zu den Methoden, die für alle Attributtypen verfügbar sind, wie früher erklärte wurde, ist die folgende Methode nur für das **lookup**-Attribut verfügbar:

- [getIsPartyList](attributes/getIsPartyList.md)

## <a name="multiselectoptionset-and-optionset-attribute-types"></a>MultiSelectOptionSet und OptionSet-Attributtypen

Zusätzlich zu den Methoden, die für alle Attributtypen verfügbar sind, wie früher erklärte wurde, sind die folgenden Methoden nur für **multiselectoption**- und **optionset**-Attribute verfügbar:

<table>
<tr>
<td>
<ul>
<li><a href="attributes/getInitialValue.md" data-raw-source="[getInitialValue](attributes/getInitialValue.md)">getInitialValue</a></li>
<li><a href="attributes/getOption.md" data-raw-source="[getOption](attributes/getOption.md)">getOption</a></li>
<li><a href="attributes/getOptions.md" data-raw-source="[getOptions](attributes/getOptions.md)">getOptions</a></a></li>
<li><a href="attributes/getSelectedOption.md" data-raw-source="[getSelectedOption](attributes/getSelectedOption.md)">getSelectedOption</a></li>
<li><a href="attributes/getText.md" data-raw-source="[getText](attributes/getText.md)">getText</a></li>
</ul>
</td>
</tr>
</table>

## <a name="number-attribute-type-decimal-double-integer-money"></a>Zahlattributtyp: (decimal, double, integer, money)
Die folgenden Methoden sind nur für die **decimal**-, **double**- und **integer**-Attribute verfügbar:

<table>
<tr>
<td>
<ul>
<li><a href="attributes/getMax.md" data-raw-source="[getMax](attributes/getMax.md)">getMax</a></li>
<li><a href="attributes/getMin.md" data-raw-source="[getMin](attributes/getMin.md)">getMin</a></li>
<li><a href="attributes/getPrecision.md" data-raw-source="[getPrecision](attributes/getPrecision.md)">getPrecision</a></a></li>
<li><a href="attributes/setPrecision.md" data-raw-source="[setPrecision](attributes/setPrecision.md)">setPrecision</a></li>
<li><a href="attributes/getText.md" data-raw-source="[getText](attributes/getText.md)">getText</a></li>
</ul>
</td>
</tr>
</table>

## <a name="string-attribute-type"></a>Zeichenfolgenattributtyp
Zusätzlich zu den Methoden, die für alle Attributtypen verfügbar sind, wie früher erklärte wurde, ist die folgende Methode nur für das **string**-Attribut verfügbar:

- [getMaxLength](attributes/getMaxLength.md)


### <a name="related-topics"></a>Verwandte Themen

[Zusammengesetzte Attribute](composite-attributes.md)

[Verständnis des Xrm-Objektmodells](../understand-clientapi-object-model.md)

[Steuerelemente (Client-API-Referenz)](controls.md)




