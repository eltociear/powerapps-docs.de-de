---
title: Attribute in modellgesteuerten Apps | MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden von Attributen in modellgestützten Apps mithilfe von Client-API.
ms.date: 10/31/2018
ms.service: crm-online
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
<li>[Steuerelemente](attributes/controls-collection.md)</li>
<li>[addOnChange](attributes/addOnChange.md)</li>
<li>[fireOnChange](attributes/fireOnChange.md)</a></li>
<li>[getAttributeType](attributes/getAttributeType.md)</li>
<li>[getFormat](attributes/getFormat.md)</li>
<li>[getIsDirty](attributes/getIsDirty.md)</li>
</ul>
</td>
<td>
<ul>
<li>[getName](attributes/getName.md)</li>
<li>[getParent](attributes/getParent.md)</li>
<li>[getRequiredLevel](attributes/getRequiredLevel.md)</li>
<li>[getSubmitMode](attributes/getSubmitMode.md)</li>
<li>[getUserPrivilege](attributes/getUserPrivilege.md)</li>
<li>[getValue](attributes/getValue.md)</li>
</ul>
</td>
<td>
<ul>

<li>[isValid](attributes/isValid.md)</li>
<li>[removeOnChange](attributes/removeOnChange.md)</li>
<li>[setRequiredLevel](attributes/setRequiredLevel.md)</li>
<li>[setSubmitMode](attributes/setSubmitMode.md)</li>
<li>[setValue](attributes/setValue.md)</li>
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
<li>[getInitialValue](attributes/getInitialValue.md)</li>
<li>[getOption](attributes/getOption.md)</li>
<li>[getOptions](attributes/getOptions.md)</a></li>
<li>[getSelectedOption](attributes/getSelectedOption.md)</li>
<li>[getText](attributes/getText.md)</li>
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
<li>[getMax](attributes/getMax.md)</li>
<li>[getMin](attributes/getMin.md)</li>
<li>[getPrecision](attributes/getPrecision.md)</a></li>
<li>[setPrecision](attributes/setPrecision.md)</li>
<li>[getText](attributes/getText.md)</li>
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




