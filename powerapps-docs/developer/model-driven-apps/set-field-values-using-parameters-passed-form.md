---
title: 'Festlegen von Feldwerten mithilfe von Parametern, die an ein Formular übergeben werden (modelgestützte Apps) | Microsoft Docs'
description: 'Sie können Standardwerte für benutzererstellte neue Datensätze festlegen, indem Sie Attributwerte in der URL angeben, die verwendet wird, um das Formular zu öffnen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-field-values-using-parameters-passed-to-a-form"></a>Festlegen von Feldwerten mithilfe von Parametern, die an ein Formular übergeben werden

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/set-field-values-using-parameters-passed-form -->

Sie können Standardwerte für benutzererstellte neue Datensätze festlegen, indem Sie Attributwerte in der URL angeben, die verwendet wird, um das Formular zu öffnen. Standardmäßig werden diese Werte im Formular festgelegt, können jedoch von Benutzern geändert werden, bevor sie den Datensatz speichern.  
  
<a name="BKMK_PassingParameters"></a>   
## <a name="pass-parameters-to-set-field-record-values"></a>Parametern zum Festlegen von Feldwerten übergeben  
  
> [!NOTE]
>  Sie können Parameterwerte an das Formular übergeben, um mithilfe der Funktion `Xrm.Navigation.`[openForm](clientapi/reference/Xrm-Navigation/openForm.md) Feldwerte festzulegen. Wenn ein Beispiel finden Sie unter [Beispiel: Verwendung von Xrm.Navigation.openForm, um ein neues Fenster zu öffnen](set-field-values-using-parameters-passed-form.md#BKMK_ExampleXrmNavigationOpentForm).  
  
 Wenn Sie ein neues Formular öffnen, indem Sie die URL-Adresse verwenden, können Sie Argumente in den Parameter `extraqs` einfügen, um Feldwerte festzulegen. Die folgenden Anforderungen müssen erfüllt sein:  
  
- Sie müssen den Parameter codieren, der im Parameter `extraqs` übergeben wird. Um die Parameter zu codieren, verwenden Sie [encodeURIComponent](https://msdn.microsoft.com/library/aeh9cef7\(VS.85\).aspx).  
  
- Die Namen der Abfragezeichenfolgenargumente müssen mit den Namen der Attribute für die Entität übereinstimmen oder diese enthalten.  
  
- Die übergebenen Werte müssen gültig sein.  
  
- Der Wert kann kein Skript sein.  
  
  Jeder Versuch, einen ungültigen Parameter oder Wert zu übergeben, ergibt einen Fehler.  
  
- Verwenden Sie für boolesche Felder entweder einen Ganzzahlwert von `0` bzw. `1` oder einen Textwert von `true` bzw. `false`, um den Wert festzulegen.  
  
- Für Datum-Zeit-Felder verwenden Sie den Textwert des Datums.  
  
<a name="BKMK_ExampleSetValueStringFields"></a>   

## <a name="example-set-the-value-for-string-fields"></a>Beispiel: Festlegen des Werts für Zeichenfolgenfelder  
 Im folgenden Beispiel wird der Wert für das Feld **Name** eines neuen Firmendatensatzes als "Neue Firma" festgelegt.  
  
 Der uncodierte Wert für den Parameter `extraqs` ist “name=Neue Firma".  
  
```  
/main.aspx?etn=account&extraqs=name%3DNew%20Account&pagetype=entityrecord  
```  
  
<a name="BKMK_SetLookupFieldValues"></a>   

## <a name="set-values-for-lookup-fields"></a>Werte für Suchfelder festlegen  
 Die folgende Tabelle beschreibt fünf Typen von Suchfeldern. Weitere Beispiele zum Verwenden von Suchfeldern finden Sie unter [Beispiel: Den Wert für Suchfelder festlegen](set-field-values-using-parameters-passed-form.md#BKMK_setValueLookupfields) und [Beispiel: Verwenden von Xrm.Navigation.openForm, um ein neues Fenster zu öffnen](set-field-values-using-parameters-passed-form.md#BKMK_ExampleXrmNavigationOpentForm).  
  
|Suchtyp|Beschreibung|  
|-----------------|-----------------|  
|einfache Suche|Erlaubt einen einzelnen Verweis auf einen Entitätstyp.|  
|Kundensuche|Erlaubt eine einzelne Referenz zu einem Konto- oder einem Kontaktdatensatz.|  
|Besitzersuche|Erlaubt einen einzelnen Verweis auf einen Team- oder einen Systembenutzerdatensatz.|  
|Partylist-Suche|Erlaubt mehrere Referenzen zu mehreren Entitäten.|  
|Bezug-Suche|Erlaubt eine einzelne Referenz zu mehreren Entitäten.|  
  
 Die folgenden Richtlinien treffen zu, wenn der Wert einer Suche in einem Formular mithilfe eines Abfragezeichenfolgenarguments festgelegt wird:  
  
-   Bei einfachen Suchen müssen Sie den Wert und den Text festlegen, der in der Suche angezeigt werden soll. Verwenden Sie das Suffix "Name" mit dem Namen des Attributs, um den Wert für den Text festzulegen.  
  
     Verwenden Sie keine anderen Argumente.  
  
-   Bei Kunden- und Besitzersuchen müssen Sie den Wert und den Namen auf die gleiche Weise festlegen wie bei einfachen Suchen. Des Weiteren müssen Sie das Suffix "Typ" verwenden, um den Typ der Entität anzugeben. Zulässige Werte lauten Firma, Kontakt, Benutzer und Teams.  
  
-   Sie können die Werte für Partylist oder für Bezug-Suchen nicht festlegen.  
  
<a name="BKMK_setValueLookupfields"></a>   

## <a name="example-set-the-value-for-lookup-fields"></a>Beispiel: Festlegen des Werts für Suchfelder  
 Um Werte für Suchfelder festzulegen, verwenden Sie den Datenwert, den Namenswert, und geben Sie nur bei Kunden- oder Besitzersuchen den Typwert für das jeweilige Feld an. Im folgenden Beispiel wird das Besitzerfeld auf einen Benutzer mit dem Namen "Mark Folkerts" festgelegt.  
  
 Der uncodierte Wert für den `extraqs` Parameter lautet "**ownerid**={B8C6E040-656E-DF11-B414-00155DB1891A}&**owneridname** = Mark Folkerts&**owneridtype**=systemuser”.  
  
```  
/main.aspx?etn=lead&pagetype=entityrecord&extraqs=ownerid%3D%7bB8C6E040-656E-DF11-B414-00155DB1891A%7d%26owneridname%3DMark%20Folkerts%26owneridtype%3Dsystemuser  
```  
  
 Im folgenden Beispiel wird das Feld für den primären Kontakt auf “Yvonne McKay (Beispiel)” festgelegt. Der nicht-kodierte Wert für den `extraqs` Parameter ist “**primarycontactid**={43b58571-eefa-e311-80c1-00155d2a68c4}&**primarycontactidname**=Yvonne McKay (sample)”.  
  
```  
/main.aspx?etn=account&pagetype=entityrecord&extraqs=primarycontactid%3D%7B43b58571-eefa-e311-80c1-00155d2a68c4%7D%26primarycontactidname%3DYvonne%20McKay%20(sample)  
```  
  
> [!NOTE]
>  Für eine einfache Suche wie diese müssen Sie keinen Typwert festlegen.  
  
<a name="BKMK_SetValueDateFields"></a>   

## <a name="example-set-the-value-for-date-fields"></a>Beispiel: Festlegen des Werts für Datumsfelder  
 Im folgenden Beispiel wird für das Feld **Vorauss. Abschlussdatum** für eine neue Verkaufschance auf den 31. Januar 2011 festgelegt. Der unkodierte Wert für den `extraqs`-Parameter ist “estimatedclosedate=01/31/11”.  
  
```  
/main.aspx?etn=opportunity&extraqs=estimatedclosedate%3D01%2F31%2F11&pagetype=entityrecord  
```  
  
<a name="BKMK_SampleSEtValueOptionSetFields"></a>   

## <a name="example-set-the-value-for-option-set-fields"></a>Beispiel: Festlegen des Werts für Optionssatzfelder  
 Um den Wert für ein Feld **Optionssatz** festzulegen, legen Sie den Ganzzahlwert für die Option fest. Im folgenden Beispiel wird der Feldwert **Rolle** in einem neuen Kontaktdatensatz auf "Entscheidungsträger" festgelegt.  
  
 Der uncodierte Wert für den Parameter `extraqs` lautet “accountrolecode=1”.  
  
```  
/main.aspx?etn=contact&extraqs=accountrolecode%3D1&pagetype=entityrecord  
``` 

<a name="BKMK_SampleSEtValueMultiSelectOptionSetFields"></a> 
  
## <a name="example-set-the-value-for-multi-select-option-set-fields"></a>Beispiel: Legen Sie den Wert von MultiSelect-Optionssatzfeldern fest

Um den Wert von **MultiSelect-Optionssatzfeldern** festzulegen, geben Sie für die Optionen in der URL zum Öffnen des Formulars ganzzahlige Werte an. Um beispielsweise die Optionen für das Feld **Hobbys** festzulegen, ist der unkodierte Wert für den Parameter "extraqs" “hobbies=[1,3,4]”.   

```  
/main.aspx?etn=contact&extraqs=hobbies%3D%5B1%2C3%2C4%5D&pagetype=entityrecord   
``` 
  
<a name="BKMK_ExampleXrmNavigationOpentForm"></a>   

## <a name="example-use-xrmnavigationopenform-to-open-a-new-window"></a>Beispiel: Verwendung von Xrm.Navigation.openForm, um ein neues Fenster zu öffnen.  
 Das folgende Beispiel legt Standardwerte für verschiedene Felder fest und veranschaulicht, wie die `Xrm.Navigation`.[openForm](clientapi/reference/Xrm-Navigation/openForm.md)-Funktion verwendet wird. Es entspricht dem früheren Beispiel, das die Methode `window.open` verwendet hat.  
  
```Javascript  
function OpenNewContact() {  
 var parameters = {};  
 //Set the Parent Customer field value to “Contoso”.  
 parameters["parentcustomerid"] = "2878282E-94D6-E111-9B1D-00155D9D700B";  
 parameters["parentcustomeridname"] = "Contoso";  
 parameters["parentcustomeridtype"] = "account";  
 //Set the Address Type to “Primary”.  
 parameters["address1_addresstypecode"] = "3";  
 //Set text in the Description field.  
 parameters["description"] = "Default values for this record were set programmatically.";  
 //Set Do not allow E-mails to "Do Not Allow".  
 parameters["donotemail"] = "1";  
  
 // Define the entity name to open the form  
 var entityFormOptions = {};
 entityFormOptions["entityName"] = "contact";

// Open the form
 Xrm.Navigation.openForm(entityFormOptions, parameters).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });  
}  
```  
  
<a name="BKMK_ExampleWindowOpen"></a>   

## <a name="example-use-windowopen-to-open-a-new-window"></a>Beispiel: Verwenden von window.open zum Öffnen eines neuen Fensters  
 Das folgende Beispiel legt Standardwerte für verschiedene Felder fest und veranschaulicht, wie [encodeURIComponent](https://msdn.microsoft.com/library/aeh9cef7\(VS.85\).aspx) verwendet wird, um den Wert des Parameters `extraqs` zu codieren. Wenn Sie die Methode [window.open](https://msdn.microsoft.com/library/ms536651\(VS.85\).aspx) verwenden, können Sie die Funktionen des Fensters steuern, das geöffnet wird.  
  
```Javascript  
function OpenNewContact() {  
    //Set the Parent Customer field value to “Contoso”.  
    var extraqs = "parentcustomerid={F01F3F6D-896E-DF11-B414-00155DB1891A}";  
    extraqs += "&parentcustomeridname=Contoso";  
    extraqs += "&parentcustomeridtype=account";  
    //Set the Address Type to “Primary”.  
    extraqs += "&address1_addresstypecode=3";  
    //Set text in the Description field.  
    extraqs += "&description=Default values for this record were set programatically.";  
    //Set Do not allow E-mails to "Do Not Allow".  
    extraqs += "&donotemail=1";  
    //Set features for how the window will appear.  
    var features = "location=no,menubar=no,status=no,toolbar=no";  
    // Open the window.  
    window.open("/main.aspx?etn=contact&pagetype=entityrecord&extraqs=" +  
     encodeURIComponent(extraqs), "_blank", features, false);  
}  
```  
  
### <a name="see-also"></a>Siehe auch  

 [Öffnen von Formularen und Ansichten mit einer URL](open-forms-views-dialogs-reports-url.md)   
 [openForm](clientapi/reference/Xrm-Navigation/openForm.md)  
 [Ein Formular konfigurieren, um benutzerdefinierte Abfragezeichenfolgenparameter zu akzeptieren.](configure-form-accept-custom-querystring-parameters.md)
