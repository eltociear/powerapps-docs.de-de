---
title: 'Bewährte Methoden: Clientskripting in modelgesteuerten Apps | MicrosoftDocs'
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 16271bd8-cfa8-4a7f-802a-60fbff7c3722
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d4766cd0bfc48e79a39bb5da7c7048330fbcabfe
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115674"
---
# <a name="best-practices-client-scripting-in-model-driven-apps"></a>Bewährte Methoden: Clientskripting in modelgesteuerten Apps



Nachfolgend sind einige der Tipps aus bewährten Methoden, die Sie betrachten können, während Sie Ihren JavaScript-Code für modellgesteuerte Apps schreiben.

## <a name="define-unique-javascript-function-names"></a>Definieren Sie eindeutige JavaScript-Funktionsnamen.

Wenn Sie Funktionen schreiben, die möglicherweise in JavaScript-Bibliotheken verwendet werden, dann können diese Funktionen mit anderen JavaScript-Bibliotheken in ein Formular geladen werden. Wenn eine andere Bibliothek eine Funktion beinhaltet, die denselben Namen wie die von Ihnen bereitgestellte Funktion enthält, dann wird die zuletzt geladene Funktion für die Seite definiert. Damit Ihre Funktionen nicht in einer anderen Bibliothek von Funktionen überschrieben werden, sollten Sie sich vergewissern, dass Ihre Funktionen eindeutige Namen besitzen. Sie können folgende Strategien verwenden:

- **Eindeutiges Funktionspräfix**: Definieren Sie all Ihre Funktionen unter Verwendung der Standardsyntax mit einem einheitlichen Namen, der eine eindeutige Namenskonvention enthält, wie im folgenden Beispiel zu sehen ist.
    ```JavaScript
    function MyUniqueName_performMyAction()
    {
        // Code to perform your action.
    }
    ```
- **Namespaced-Bibliothekennamen**: Ordnen Sie jede Ihrer Funktionen einem JavaScript-Objekt zu, um eine Art Namespace zum Aufruf Ihrer Funktionen zu erstellen, wie im folgenden Beispiel zu sehen ist.
    ```JavaScript
    //If the MyUniqueName namespace object isn’t defined, create it.
    if (typeof (MyUniqueName) == "undefined")
       { MyUniqueName = {}; }
       // Create Namespace container for functions in this library;
       MyUniqueName.MyFunctions = {
         performMyAction: function(){
         // Code to perform your action.
         //Call another function in your library
         this.anotherAction();
       },
       anotherAction: function(){
         // Code in another function
      }
    };
    ```

    Wenn Sie dann Ihre Funktion verwenden, können Sie den gesamten Namen angeben. Dies wird im folgenden Beispiel verdeutlicht.

    ```JavaScript
    MyUniqueName.MyFunctions.performMyAction();
    ```

    Wenn Sie eine Funktion innerhalb einer anderen Funktion aufrufen, können Sie dieses Schlüsselwort als eine Verknüpfung zu dem Objekt verwenden, das beide Funktionen enthält. Wenn jedoch Ihre Funktion als Ereignishandler verwendet wird, dann verweist dieses Schlüsselwort auf das Objekt, in dem das Ereignis auftritt.

## <a name="avoid-using-unsupported-methods"></a>Verwenden Sie keine nicht unterstützten Methoden.

Im Internet finden Sie zahlreiche Beispiele oder Vorschläge, in denen nicht unterstützte Methoden beschrieben werden. Dazu können auch die Nutzung von nicht dokumentierten internen Funktionen für die Seitensteuerung gehören. Diese Methoden funktionieren möglicherweise, da sie jedoch nicht unterstützt werden, können Sie nicht erwarten, dass sie in zukünftigen Versionen von modellgesteuerten Apps funktionieren.

## <a name="avoid-using-jquery-for-form-scripts"></a>Verwenden Sie jQuery nicht mit Formularskripten

Es empfiehlt sich nicht, jQuery in Formularskripten und Menübandbefehlen zu verwenden. Der Hauptvorteil von jQuery liegt darin, dass es eine einfache browserübergreifende Manipulation des DOMs ermöglicht. Dies wird ausdrücklich nicht in Formularskripts und Menübandbefehlen unterstützt. Beschränken Sie Ihre Skripts, um die Objekte/Methoden, die im [Xrm-Objektmodell](understand-clientapi-object-model.md) verfügbar sind, zu verwenden. 

Wenn Sie sich dafür entscheiden, die verbleibenden Funktionen von jQuery zu verwenden, die zusammen mit modellgesteuerten Apps hilfreich sind, und die Möglichkeit zur Verwendung von **$.ajax** einschließen möchten, sollten Sie Folgendes berücksichtigen:

- Wenn Sie eine optimale Leistung erzielen möchten, laden Sie jQuery nicht auf einer Seite, wenn Sie es nicht benötigen.
- Die Verwendung von **$.ajax** zur Durchführung von Anforderungen für die modellgesteuerten Apps-Webdienste wird unterstützt. Es gibt jedoch Alternativen. Als Alternative zur Verwendung von **$.ajax** kann das **XMLHttpRequest**-Objekt des Browsers direkt verwendet werden. Die **$.ajax**-Methode von jQuery ist lediglich ein Wrapper für dieses Objekt. Wenn Sie das systemeigene **XMLHttpRequest**-Objekt direkt verwenden, müssen Sie jQuery nicht laden.
- Bei jeder Version von jQuery, die auf einer Seite geladen wird, kann es sich um eine andere Version handeln. Verschiedene Versionen von jQuery verhalten sich unterschiedlich. Es können daher Probleme auftreten, wenn mehrere Versionen von jQuery auf derselben Seite geladen werden. Es gibt eine Technik, dies zu verringern, sie hängt aber vom Bearbeiten der jQuery-Bibliothek und sonstigen Bibliotheken ab, die von jQuery abhängen.


## <a name="write-your-code-for-multiple-browsers"></a>Schreiben Sie Ihren Code für mehrere Browser.

Modellgesteuerte Apps unterstützen mehrere Browser. Sie sollten sicherstellen, dass alle Skripte, die Sie verwenden, mit allen unterstützten Browsern funktionieren. Zahlreiche wichtige Unterschiede zwischen Internet Explorer und anderen Browsern beziehen sich auf die HTML- und XML-DOM-Manipulation. Da die HTML-DOM-Manipulation nicht unterstützt wird, wenn die Skriptlogik nur unterstützte Aktionen ausführt und das [Xrm-Objektmodell](understand-clientapi-object-model.md) verwendet, können die zur Unterstützung anderer Browser erforderlichen Änderungen geringfügig sein. 
