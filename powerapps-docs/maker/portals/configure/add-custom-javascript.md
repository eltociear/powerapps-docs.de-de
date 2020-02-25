---
title: Verwenden von benutzedefiniertem JavaScript für ein Portal | Microsoft-Dokumentation
description: Anweisungen, benutzerdefiniertes JavaScript einem Formular in einem Portal hinzuzufügen
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: fca222555a4a19b511e3b2a140586d20a668ec85
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979379"
---
# <a name="add-custom-javascript"></a>Benutzerdefiniertes JavaScript hinzufügen

Der Webformularschritt-Eintrag enthält ein Feld namens **Benutzerdefiniertes JavaScript**, das zum Speichern von JavaScript-Codes verwendet werden kann und Ihnen die Möglichkeit gibt, die visuelle Anzeige oder die Funktion des Formulars zu erweitern oder zu ändern.

Der benutzerdefinierte JavaScript-Satz wird unten an der Seite hinzugefügt, direkt vor dem abschließenden Form-Tag-Elements.

## <a name="form-fields"></a>Formularfelder

Die HTML-Eingabe-ID eines Entitätsfelds wird auf den logischen Namen des Attributs festgelegt. Dadurch wird das Auswählen von Feldern, Einstellungswerten oder anderen clientseitigen Änderungen mit [jQuery](https://jquery.com/) erleichtert.  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>Zusätzliche clientseitige Feldvalidierung
Manchmal müssen Sie die Validierung der Felder auf dem Formular anpassen. Im folgenden Beispiel wird gezeigt, wie ein benutzerdefinierter Validator hinzugefügt wird. Dieses Beispiel zwingt den Benutzer, nur eine E-Mail-Adresse zu definieren, wenn das andere Feld für die bevorzugte Kontaktmethode auf E-Mail festgelegt ist.

> [!NOTE]
> Die clientseitige Feldüberprüfung wird in einem Unterraster nicht unterstützt.

```JavaScript
if (window.jQuery) {
   (function ($) {
      $(document).ready(function () {
         if (typeof (Page_Validators) == 'undefined') return;
         // Create new validator
         var newValidator = document.createElement('span');
         newValidator.style.display = "none";
         newValidator.id = "emailaddress1Validator";
         newValidator.controltovalidate = "emailaddress1";
         newValidator.errormessage = "<a href='#emailaddress1_label'>Email is a required field.</a>";
         newValidator.validationGroup = ""; // Set this if you have set ValidationGroup on the form
         newValidator.initialvalue = "";
         newValidator.evaluationfunction = function () {
            var contactMethod = $("#preferredcontactmethodcode").val();
            if (contactMethod != 2) return true; // check if contact method is not 'Email'.
            // only require email address if preferred contact method is email.
            var value = $("#emailaddress1").val();
            if (value == null || value == "") {
            return false;
            } else {
               return true;
            }
         };
 
         // Add the new validator to the page validators array:
         Page_Validators.push(newValidator);
 
         // Wire-up the click event handler of the validation summary link
         $("a[href='#emailaddress1_label']").on("click", function () { scrollToAndFocus('emailaddress1_label','emailaddress1'); });
      });
   }(window.jQuery));
}
```

## <a name="general-validation"></a>Allgemeine Überprüfung

Klicken Sie auf die Schaltfläche **Weiter**/**Übermitteln**, um eine Funktion namens **webFormClientValidate** auszuführen. Sie können diese Methode erweitern, um benutzerdefinierte Validierungslogik hinzuzufügen.

```JavaScript
if (window.jQuery) {
   (function ($) {
      if (typeof (webFormClientValidate) != 'undefined') {
         var originalValidationFunction = webFormClientValidate;
         if (originalValidationFunction && typeof (originalValidationFunction) == "function") {
            webFormClientValidate = function() {
               originalValidationFunction.apply(this, arguments);
               // do your custom validation here
               // return false; // to prevent the form submit you need to return false
               // end custom validation.
               return true;
            };
         }
      }
   }(window.jQuery));
}
```
### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Entitätsformulare definieren](entity-forms.md)  
[Webformularschritte für Portale](web-form-steps.md)  
[Schritttyp zum Laden von Formularen/Registerkarten](load-form-step.md)  
[Umleitungsschritttyp](add-redirect-step.md)  
[Bedingter Schritttyp](add-conditional-step.md)
