---
title: Debuggen Sie Ihren JavaScript-Code für modellgetriebene Anwendungen | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: 3edad039-4397-4984-a29b-9307a7a2aaee
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0441d5a96a3e35eb28f77c726591a6634be9704
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115670"
---
# <a name="debug-your-javascript-code-for-model-driven-apps"></a>Debuggen Sie Ihren JavaScript-Code für modellgetriebene Anwendungen



Jeder Browser bietet eine Art von Debuggingerweiterung. Microsoft Edge und Internet Explorer bieten F12-Entwicklertools, die Sie verwenden können, um Ihre Skripts in modellgesteuerten Apps zu debuggen. Die F12-Entwicklertools können durch Drücken von F12 geöffnet werden, wenn eine Seite mit Microsoft Edge oder Internet Explorer angezeigt wird. Weitere Informationen finden Sie unter Verwenden von [F12-Entwicklertools Handbuch](https://docs.microsoft.com/microsoft-edge/f12-devtools-guide).

Drücken Sie in Google Chrome auf F12, um die Entwicklertools zu öffnen. Firebug ist eine beliebte Browsererweiterung zur Webentwicklung, die Mozilla Firefox verwendet. In Apple Safari müssen Sie zuerst das Menü **Erweitert** auf der Menüleiste in **Erweiterte Voreinstellungen** auswählen. Dann können Sie aus dem Menü **Entwickler** die Option **Web Inspector anzeigen** auswählen.

Wenn Sie JavaScript-Bibliotheken in modellegsteuerten Apps verwenden, werden die Bibliotheken mit der Webseite geladen. Es kann manchmal schwierig sein, eine bestimmte Bibliothek in der Debugumgebung zu isolieren. Wenn Sie Debuggen-Tools in Microsoft Edge verwenden, erweitern Sie die verfügbaren Skripts auf der Registerkarte **Debugger**, klicken auf das Ordnersymbol oben links, und suchen Sie das Skript mit dem Namen, der dem Namen Ihrer JavaScript-Webressource entspricht, wie die unten gezeigte **new_myCustomJavaScript.js**-Webressource. Sie können auch nach Ihrer JavaScript-Bibliothek suchen, indem Sie den Namen im Suchfeld eingeben.

![JavaScript-Debugging](../media/form-script-debugging.png)

Debugtools unterschiedlicher Browser haben ähnliche Funktionen. Nachdem Sie die Bibliothek gefunden haben, können Sie einen Haltepunkt festlegen und das Ereignis neu erstellen, das die Ausführung Ihres Codes auslösen sollte.

Sehen Sie sich auch den folgenden Beitrag in unserem Teamblog an, um weitere Ideen zum Debugging des JavaScript-Codes zu finden: [Blog: Debugging benutzerdefinierten JavaScript-Codes in CRM mithilfe der Browser-Entwicklertools](https://blogs.msdn.microsoft.com/crm/2015/11/29/debugging-custom-javascript-code-in-crm-using-browser-developer-tools/).

## <a name="select-appropriate-frame-to-debug-your-code"></a>Wählen Sie die entsprechenden Frame aus, um Ihren Code zu debuggen.

modellgesteuerte Apps-Formulare bestehen aus mehreren Frames. Damit der Code in der **Konsole** der Browserentwicklertools funktioniert, müssen den entsprechenden Frame auswählen. 
- Wählen Sie für die Webclientformulare den Frame namens **ClientApiWrapper** aus. 
- Für die neuen Einheitliche Oberfläche-Formulare wählen Sie den Frame aus, der die Bezeichnung **ClientApiFrame_[n]** hat, wobei n die interne Seiten- ID ist. Sie sollten den Frame mit dem Höchstwert für [n] auswählen.

## <a name="write-messages-to-the-console"></a>Schreiben von Nachrichten an die Konsole

Die Verwendung der [window.alert](https://msdn.microsoft.com/library/ms535933(v=vs.85).aspx)-Methode zum Debuggen JavaScript ist immer noch eine gängige Methode, um Fehler im Anwendungscode zu beheben. Da inzwischen alle modernen Browser einen einfachen Zugriff auf Debugtools bieten, ist dies nicht sinnvoll, insbesondere, wenn andere Personen die Anwendung, die Sie debuggen, verwenden könnten.

Sie sollten stattdessen Ihre Nachrichten an die Konsole schreiben. Im Folgenden finden Sie eine kleine Funktion, die Sie Ihren Bibliotheken hinzufügen können, sodass Sie Nachrichten senden können, die Sie bei geöffneter Konsole anzeigen möchten.

```JavaScript
function writeToConsole(message)
{
 if (typeof console != 'undefined') {
  console.log(message);
 }
}
```

Wenn Sie vergessen, Code zu entfernen, der diese Funktion verwendet, sehen Benutzer der Anwendung im Gegensatz zur alert-Methode Ihre Nachrichten nicht.
