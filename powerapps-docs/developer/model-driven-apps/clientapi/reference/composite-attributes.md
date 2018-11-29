---
title: Zusammengesetzte Attribute in modellgesteuerten Apps | MicrosoftDocs
description: 'Erfahren Sie über das Attribut addOnchange-Methode, um eine Funktion zum Aufruf festzulegen, wenn der Attributwert geändert wird.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9f3b2fed-fde5-46e4-8c59-43aa51aa82df
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="composite-attributes"></a>Zusammengesetzte Attribute 



Einige Felder, die in einem Formular hinzugefügt werden, können mehrere Elemente von Daten darstellen. Diese *zusammengesetzten Attribute* verhalten sich anders als andere Attribute, wenn sie in der Webanwendung angezeigt werden, und Sie müssen Skripts anders schreiben, um sie korrekt zu verwenden.

In der folgenden Tabelle sind die zusammengesetzten Attribute, die in modellgesteuerten Apps verfügbar sind, aufgeführt:

<table>
    <tbody>
        <tr>
            <th scope="col">
                <p>
Entität </p>
            </th>
            <th scope="col">
                <p>
Anzeigename </p>
            </th>
            <th scope="col">
                <p>
Logischer Name </p>
            </th>
        </tr>
        <tr>
            <td rowspan="2">
                <p>
Firma </p>
            </td>
            <td>
                <p>
                    <strong>Adresse 1</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Adresse 2</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="3">
                <p>
Kontakt </p>
            </td>
            <td>
                <p>
                    <strong>Vollständiger Name</strong>
                </p>
            </td>
            <td>
                <p>
fullname </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Adresse 1</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Adresse 2</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="3">
                <p>
Lead </p>
            </td>
            <td>
                <p>
                    <strong>Vollständiger Name</strong>
                </p>
            </td>
            <td>
                <p>
fullname </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Adresse 1</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Adresse 2</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="3">
                <p>
Benutzer </p>
            </td>
            <td>
                <p>
                    <strong>Vollständiger Name</strong>
                </p>
            </td>
            <td>
                <p>
fullname </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Adresse</strong>
                </p>
            </td>
            <td>
                <p>
address1_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Weitere Adresse</strong>
                </p>
            </td>
            <td>
                <p>
address2_composite </p>
            </td>
        </tr>        
        <tr>
            <td rowspan="2">
                <p>
Angebot </p>
            </td>
            <td>
                <p>
                    <strong>Rechnungsadresse</strong>
                </p>
            </td>
            <td>
                <p>
billto_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Lieferadresse</strong>
                </p>
            </td>
            <td>
                <p>
shipto_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="2">
                <p>
Reihenfolge </p>
            </td>
            <td>
                <p>
                    <strong>Rechnungsadresse</strong>
                </p>
            </td>
            <td>
                <p>
billto_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Lieferadresse</strong>
                </p>
            </td>
            <td>
                <p>
shipto_composite </p>
            </td>
        </tr>
        <tr>
            <td rowspan="2">
                <p>
Rechnung </p>
            </td>
            <td>
                <p>
                    <strong>Rechnungsadresse</strong>
                </p>
            </td>
            <td>
                <p>
billto_composite </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
                    <strong>Lieferadresse</strong>
                </p>
            </td>
            <td>
                <p>
shipto_composite </p>
            </td>
        </tr>
    </tbody>
</table>

## <a name="composite-attributes-in-the-web-application"></a>Zusammengesetzte Attribute in der Webanwendung

Wenn Felder für zusammengesetzte Attribute einem Hauptformular hinzugefügt werden, wird in der Webanwendung nur das zusammengesetzte Attribut angezeigt. Wenn ein Benutzer das Feld bearbeitet, wird ein Flyout mit den einzelnen Attributen angezeigt, aus denen das Attribut besteht. 

Beispielsweise ist das Feld **Adresse** in einem Kontaktformular ein zusammengesetztes Attribut. Durch Klicken auf das Feld **Adresse** wird ein Flyout mit einzelnen Attributen angezeigt, die das zusammengesetzte Attribut ausmachen. 

![Ein Beispiel eines zusammengesetzten Attributs](../../media/clientapi_compositeattribute.png)

Obwohl nicht explizit dem Formular im Formular-Editor hinzugefügt, ist jedes der Attribute, die Teil des Attributs sind, für das Formular verfügbar. Obwohl Sie den Wert des zusammengesetzten Werts mithilfe von [getValue](attributes/getValue.md) lesen können, kann [setValue](attributes/setValue.md) nicht verwendet werden, um den Wert des zusammengesetzten Attributs direkt zu ändern. Sie müssen mindestens eines der Attribute festlegen, auf die das zusammengesetzte Attribut verweist.

Sie können auf die einzelnen zugehörigen Steuerelemente zugreifen, die in dem Flyout nach Name angezeigt werden. Diese Steuerelemente verwenden die folgende Namenskonvention: \<**Name des zusammengesetzten Steuerelements**>\_compositionLinkControl_\<**zugehöriger Attributname**>. 

Um nur auf das **address_line1**-Steuerelement im **address1_composite**-Steuerelement zuzugreifen, verwenden Sie: 

`formContext.getControl("address1_composite_compositionLinkControl_address1_line1")`

## <a name="composite-attributes-in-mobile-clients"></a>Zusammengesetzte Attribute in mobilen Clients
Der mobile Client für modellgesteuerte Apps verwendet die gleichen Formulardefinitionen wie für die Entitäten mit zusammengesetzten Attributen, interpretiert sie aber unterschiedlich. Wenn ein zusammengesetztes Attribut in der Formulardefinition gefunden wird, zeigt es alle Attribute an, die Teil des zusammengesetzten Attributs in diesem Abschnitt des Formular sind. Ein Flyout ist nicht erforderlich, weil alle Felder angezeigt werden. Sie können Skripts für das Formular schreiben, die auf jedes der einzelnen Attribute zugreifen, als ob sie dem Formular einzeln hinzugefügt worden seien.
Allerdings ist das eigentliche zusammengesetzte Steuerelement auf der Seite für mobile -Clients in modellgesteuerten Apps nicht vorhanden.

## <a name="mitigate-the-differences"></a>Verringern der Unterschiede

Wenn Sie auf das Feld für den vollständigen Namen für Kontakt-, Lead- oder Benutzerentitäten zugreifen möchten, ist die Verwendung der Methode **formContext.data.entity**.[getPrimaryAttributeValue](formContext-data-entity/getPrimaryAttributeValue.md) eine einfache Möglichkeit, den Wert für dieses Attribut zu erhalten, ohne es direkt zu referenzieren. Diese Methode funktoniert sowohl für die Webanwendung als auch für mobile Clients in modellgesteuerten Apps.

Wenn Sie über Code verfügen, der den Wert einer der Adressen der zusammengesetzten Attribute lesen muss, um mit beiden Clients zu arbeiten, müssen Sie den Code mithilfe der Methode [getClient](Xrm-Utility/getGlobalContext/client.md#getclient) trennen, wie in der folgenden Funktion veranschaulicht, wobei die formatierte Adresse mithilfe der Methode **Xrm.Navigation**[openAlertDialog](Xrm-Navigation/openAlertDialog.md) in der Haupt-Webanwendung oder in der mobilen App-Version des Formulars angezeigt wird.

```JavaScript
function showAddressDialog(executionContext) {
    var address1_compositeValue;
    var formContext = executionContext.getFormContext();
    if (Xrm.Utility.getGlobalContext().client.getClient() != "Mobile") {
        address1_compositeValue = formContext.getAttribute("address1_composite").getValue();
    }
    else {
        var address1_line1 = formContext.getAttribute("address1_line1").getValue();
        var address1_line2 = formContext.getAttribute("address1_line2").getValue();
        var address1_line3 = formContext.getAttribute("address1_line3").getValue();
        var address1_city = formContext.getAttribute("address1_city").getValue();
        var address1_stateorprovince = formContext.getAttribute("address1_stateorprovince").getValue();
        var address1_postalcode = formContext.getAttribute("address1_postalcode").getValue();
        var address1_country = formContext.getAttribute("address1_country").getValue();

        // Achieve equivalent formatting
        //address1_line1
        //address1_line2
        //address1_line3
        //address1_city, address1_stateorprovince address1_postalcode
        //address1_country

        var addressText = "";
        if (address1_line1 != null) {
            addressText += address1_line1 + "\n";
        }
        if (address1_line2 != null) {
            addressText += address1_line2 + "\n";
        }
        if (address1_line3 != null) {
            addressText += address1_line3 + "\n";
        }
        if (address1_city != null) {
            addressText += address1_city + ", ";
        }
        if (address1_stateorprovince != null) {
            addressText += address1_stateorprovince + " ";
        }
        if (address1_postalcode != null) {
            addressText += address1_postalcode + "\n";
        }
        addressText += address1_country;

        address1_compositeValue = addressText;
    }
    Xrm.Navigation.openAlertDialog({ text: address1_compositeValue });
    console.log(address1_compositeValue);
}
```

### <a name="related-topics"></a>Verwandte Themen
[Attribute](attributes.md)





