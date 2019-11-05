---
title: Verwenden von benutzerdefiniertem JavaScript für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen von benutzerdefiniertem JavaScript zu einem Formular in einem Portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 42e31fc2ecb18d4f26327f8ccbeabe034d7a1700
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553645"
---
# <a name="add-custom-javascript"></a>Hinzufügen benutzerdefinierter JavaScript

Der Datensatz für den Webformular Schritt enthält ein Feld mit dem Namen **benutzerdefiniertes JavaScript** , das zum Speichern von JavaScript-Code verwendet werden kann, damit Sie die visuelle Darstellung oder Funktion des Formulars erweitern oder ändern können.

Der benutzerdefinierte Block von JavaScript wird am Ende der Seite direkt vor dem schließenden Formular-TagElement hinzugefügt.

## <a name="form-fields"></a>Formularfelder

Die HTML-Eingabe-ID eines Entitäts Felds wird auf den logischen Namen des Attributs festgelegt. Dies ermöglicht die Auswahl eines Felds, das Festlegen von Werten oder eine andere Client seitige Bearbeitung mit [jQuery](https://jquery.com/).  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>Zusätzliche Client seitige Feld Validierung
Manchmal müssen Sie möglicherweise die Validierung der Felder im Formular anpassen. Im folgenden Beispiel wird das Hinzufügen eines benutzerdefinierten Validierungs Steuer Elements veranschaulicht. In diesem Beispiel wird der Benutzer gezwungen, eine e-Mail nur anzugeben, wenn das andere Feld für die bevorzugte Kontaktmethode auf e-Mail festgelegt ist.

> [!NOTE]
> Die Client seitige Feld Validierung wird in einem subraster nicht unterstützt.

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

## <a name="general-validation"></a>Allgemeine Validierung

Wenn Sie auf die Schaltfläche " **nächste**/**senden** " klicken, wird eine Funktion mit dem Namen " **webformclientvalidate** " ausgeführt. Sie können diese Methode erweitern, um benutzerdefinierte Validierungs Logik hinzuzufügen.

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

[Konfigurieren eines Portals](configure-portal.md)  
[Definieren von Entitäts Formularen](entity-forms.md)  
[Webformular Schritte für Portale](web-form-steps.md)  
[Auslastungs Formular/Lade Registerkarten-Schritttyp](load-form-step.md)  
[Umleitungs Schritttyp](add-redirect-step.md)  
[Bedingter Schritttyp](add-conditional-step.md)
