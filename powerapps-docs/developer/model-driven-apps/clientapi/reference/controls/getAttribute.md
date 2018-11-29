---
title: getAttribute (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5ba037da-59f3-4e10-80f8-4e46d5410f81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getattribute-client-api-reference"></a>getAttribute (Client-API-Referenz)



Gibt das Attribut zurück, an das das Steuerelement gebunden ist.

Steuerelemente, die nicht an ein Attribut gebunden sind (Unterraster, Webressourcen und IFRAME) verwenden diese Methode nicht. Ein Fehler wird ausgelöst, wenn Sie versuchen, diese Methode für eines dieser Steuerelemente zu verwenden. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Standard, Suche, OptionSet

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getAttribute();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Objekt.

**Beschreibung**: Ein Attribut

## <a name="remarks"></a>Anmerkungen

Die zugehörigen Steuerelemente in einem [Schnellansicht-Steuerelement](../formContext-ui-quickForms.md) sind in der Steuerelement-Sammlung enthalten und diese Steuerelemente verwenden die **getAttribute**-Methode. Allerdings ist das Attribut nicht Teil der Attributsammlung für die Entität. Während Sie den Wert für das Attribut mithilfe von [getValue](../attributes/getValue.md) abrufen können und sogar mithilfe von [setValue](../attributes/setValue.md) den Wert ändern können, werden Änderungen, die Sie vornehmen, nicht in der Entität gespeichert.
 
Der folgende Code zeigt die Verwendung des Werts des **mobilephone**-Kontaktattributs beim Anzeigen in einem Firmenentitätsformular mithilfe eines Schnellansicht-Steuerelements namens **contactQuickForm**. Dieser Code verbirgt das Steuerelement, wenn der Wert des Attributs **null** ist.

```JavaScript
var quickViewMobilePhoneControl = formContext.getControl("contactQuickForm_contactQuickForm_contact_mobilephone");
if (quickViewMobilePhoneControl.getAttribute().getValue() == null) {
    quickViewMobilePhoneControl.setVisible(false);
}
```


[Steuerelement für die Schnellansicht](../formContext-ui-quickForms.md)

[Attribute](../attributes.md)


