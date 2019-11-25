---
title: Asynchrones Interagieren mit HTTP- und HTTPS-Ressourcen | MicrosoftDocs
description: Beim Schreiben von JavaScript-Client-Erweiterungen für modellgetriebene Anwendungen sollten Sie asynchron mit HTTP- und HTTPS-Ressourcen interagieren.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/20/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 37f5a91cc70614006a3525a033dac6df2d7e9d98
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753970"
---
# <a name="interact-with-http-and-https-resources-asynchronously"></a>Asynchrones Interagieren mit HTTP- und HTTPS-Ressourcen

**Kategorie**: Leistung

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Synchrone Anfragen blockieren die Ausführung anderer Skripte, was Folgendes bewirken kann:

- Nicht reaktionsfähige modellgetriebene und Canvas-Anwendungen
- Langsame Kundeninteraktionen

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Interagieren Sie nach Möglichkeit asynchron mit HTTP- und HTTPS-Ressourcen. Benutzer sollten Verbesserungen in der tatsächlichen Ladezeit der Seite oder der wahrgenommenen Geschwindigkeit des Seitenaufbaus feststellen. Auch die Reaktionsfähigkeit der Seite sollte zunehmen.

Die folgenden Optionen stehen in modernen Browsern zur Verfügung, um asynchron mit Diensten zu interagieren.

> [!NOTE]
> Das Hinzufügen von asynchronen Interaktionen erfordert einen anderen Designstil als synchrone Interaktionen. Callbacks können in einer nicht deterministischen Reihenfolge ausgeführt werden, d.h. Sie müssen mehr darüber nachdenken, ob der Seitenfluss und die Integrität jederzeit korrekt sind. Beispielsweise müssen Sie oft Maßnahmen ergreifen, um sicherzustellen, dass die Kontrollen erst aktiviert werden, wenn alle abhängigen Serviceaufrufe zurückgegeben wurden. Mit ein paar zusätzlichen Schritten kann ein angenehmeres Benutzererlebnis gewährleistet werden.

- Traditionell wurden Ribbon-Regeln mit synchronen Anforderungen geschrieben, da true/false zurückgegeben werden musste. Einheitliche Oberfläche unterstützt die Rückgabe eines Versprechens anstelle eines Bools, wodurch Ribbon-Regeln asynchrone Netzwerkanforderungen ausgeben können. Weitere Informationen finden Sie unter [Aktivierungsregeln für Multifunktionsleisten definieren](/powerapps/developer/model-driven-apps/define-ribbon-enable-rules#custom-rule).

- [`XMLHttpRequest`](https://developer.mozilla.org/docs/Web/API/XMLHttpRequest), wobei der Async-Parameter weggelassen oder auf true gesetzt wurde.

  ```javascript
  // Missing the async parameter, which is the third parameter. It defaults to true, which is the value you want.
  var requestXhr = new XMLHttpRequest();
  requestXhr.open('GET', '/test/test.txt');

  // Explicitly setting the async parameter.
  requestXhr.open('GET', '/test/test.txt', true);
  ```

- [Fetch](https://developer.mozilla.org/docs/Web/API/Fetch_API) API-Nutzung

  > [!IMPORTANT]
  > Bevor Sie mit dieser Option fortfahren, stellen Sie sicher, dass die Browser, die zur Interaktion mit Ihren Anpassungen verwendet werden, unterstützt werden. Lesen Sie den Abschnitt **Browser-Kompatibilität** der [Fetch](https://developer.mozilla.org/docs/Web/API/Fetch_API)-Dokumentation.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Es gibt mehrere Möglichkeiten, mit dem Server zu interagieren oder Ressourcen anzufordern. Gängige Ansätze, die eine synchrone Kommunikation ermöglichen, sind die folgenden:

> [!WARNING]
> Diese Szenarien sollten vermieden werden.

- Verwendung des in `false` übergebenen Objekts `XMLHttpRequest` für den Wert des Parameters `async` für den Funktionsaufruf `open`.

  ```javascript
  var requestXhr = new XMLHttpRequest();

  // Explicitly setting the async parameter to false or supplying a variable with a value of false will force this as a synchronous call.
  requestXhr.open('GET', '/test/test.txt', false);
  ```

- Verwendung der [`jQuery`](https://www.jquery.com) [Funktion `ajax`](https://api.jquery.com/jquery.ajax/), Übergabe von `false` für den Wert des Parameters `async`.

  ```javascript
  // Explicitly setting the async parameter to false or supplying a variable with a value of false will force this as a synchronous call.
  var requestAjax = $.ajax({ async: false, url: '/test/test.txt' });
  ```

- Speziell für Interaktionen mit den Dynamics 365-Diensten gibt es JavaScript-Bibliotheken, die explizite Operationen für gemeinsame Interaktionen mit dem Produkt bereitstellen. Zu den gängigen Bibliotheken gehören (sind aber nicht beschränkt auf): [`SDK.REST.js`](https://msdn.microsoft.com/library/gg334427(v=crm.7).aspx#BKMK_SDKREST), [`SDK.Soap.js`](https://code.msdn.microsoft.com/sdksoapjs-9b51b99a) und [`XrmServiceToolkit.js`](https://github.com/XrmServiceToolkit/XrmServiceToolkit).
  - Für diese gibt es einige Funktionen, die nur synchrone Operationen unterstützen; andere erfordern die Übergabe einer Callback-Funktion als Parameter, um async auf true zu setzen. Das Standardverhalten für die meisten ist, den zugrunde liegenden Async-Parameter für den offenen Aufruf des Objekts `XMLHttpRequest` auf false zu setzen.

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

### <a name="performance"></a>Leistung

Ein Browser interpretiert Skript auf einem einzelnen Thread. Wenn dieser Thread verwendet wird, um einen Prozess synchron auszuführen, reagiert der Browser nicht mehr auf die Interaktionen des Benutzers ("einfrieren"), während er auf das Ende des Prozesses wartet. Synchrone Aufrufe verhindern auch die Möglichkeit, mehr als eine Interaktion gleichzeitig auszuführen, was dazu führt, dass alle Aufrufe serieller Natur sind. In vielen Fällen führt dies zur Frustration Ihrer Benutzer. Optimieren Sie die Reaktionsfähigkeit der Benutzer durch die Integration asynchroner Service-Aufrufe.

### <a name="browser-support"></a>Browserunterstützung

Die Spezifikation für `XMLHttpRequest` besagt, dass die synchrone Verwendung aus dem Standard entfernt wird, weil sie nun veraltet ist. Derzeit zeigen Browser nur Warnungen an, aber eine `InvalidAccessError`-Ausnahme kann in Zukunft ausgelöst werden, wenn ein Wert von false an den asynchronen Parameter übergeben wird. Moderne Browser haben synchrone Anfragen, die auf dem Hauptthread ausgeführt werden, als veraltet erklärt.

> [!NOTE]
> Es werden moderne APIs eingeführt, die keine Möglichkeit mehr für synchrone Operationen bieten. Weitere Informationen finden Sie in der Dokumentation der [Fetch-API](https://developer.mozilla.org/docs/Web/API/Fetch_API).

### <a name="windowsettimeout"></a>window.setTimeout

Obwohl die Aufnahme von Skriptblöcken als Parameter für die Funktion `window.setTimeout` den normalen synchronen Ablauf der Seitenausführung unterbricht, wird keine Parallelverarbeitung durchgeführt.

```javascript
window.setTimeout(
    function () {
        var oReq = new XMLHttpRequest();
        oReq.open('GET', '/test/action', false);
    }, 0);
```

Der Ansatz in diesem Beispiel verarbeitet noch auf dem Main Browser UI-Thread und sperrt den Browser.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Definieren Sie die Ribbon-Enable-Regeln](/powerapps/developer/model-driven-apps/define-ribbon-enable-rules#custom-rule)
[XMLHttpRequest](https://docs.microsoft.com/microsoft-edge/dev-guide/performance/xmlhttprequest)<br />
[XMLHttpRequest-Spezifikation (mit synchroner Deprecation-Anweisung)](https://xhr.spec.whatwg.org/#the-open()-method)<br />
[Fetch-API-Spezifikation](https://fetch.spec.whatwg.org/#fetch-api)<br />
[Fetch API](https://developer.mozilla.org/docs/Web/API/Fetch_API)
