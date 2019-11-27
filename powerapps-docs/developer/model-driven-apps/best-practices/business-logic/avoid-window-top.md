---
title: Vermeiden der Verwendung von window.top | MicrosoftDocs
description: Beschreibt, wie Sie Skriptfehler und falsches Anwendungsverhalten im Zusammenhang mit der Verwendung von window.top in JavaScript-Anpassungen vermeiden können.
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
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: daa8e5a4a8aaff4b2aecb0942783a84eed328dfb
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748305"
---
# <a name="avoid-using-windowtop"></a>Vermeiden Sie die Verwendung von window.top

**Kategorie**: Supportfähigkeit, Upgrade-Bereitschaft, Online-Migration

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

- Der folgende Skriptfehler wird den Benutzern angezeigt oder in Ihre Fehlerprotokolle aufgenommen: `Error: Blocked a frame with origin "https://<yourinstance>.dynamics.com" from accessing a cross-origin frame.`
- Anpassungen verhalten sich möglicherweise nicht korrekt im Kontext von Dynamics 365 App for Outlook, Dynamics 365 für Smartphones und Tablets, oder einer externen Anwendung, die den Common Data Service innerhalb eines Iframe hostet.

  > [!NOTE]
  > Es kann einige Szenarien geben, in denen die Fehlerbehandlung den Fehler maskiert und die Skriptverarbeitung fortsetzt, was zu unerwartetem Verhalten führt.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Vermeiden Sie die Verwendung von `window.top` in Skripten, die im Rahmen von Dynamics 365 App for Outlook, Dynamics 365 für Smartphones und Tablets, oder einer externen Anwendung laufen, die den Common Data Service innerhalb eines Iframe hostet. Auch wenn diese Szenarien derzeit nicht für Ihr Unternehmen gelten, sollten Sie die Verwendung von `window.top` vermeiden oder sich vor diesem Problem schützen.

 > [!IMPORTANT]
 > Die Verwendung von `window.parent` oder Variationen der übergeordneten Hierarchie (z. B. `window.parent.parent`) können die gleichen Symptome verursachen.

Im Folgenden werden die empfohlenen Ansätze aufgeführt:

- Vermeiden Sie die Verwendung des Objekts `window.top` ganz.

- Wenn die Verwendung von `window.top` die einzige verfügbare Option ist, testen Sie zunächst, ob `window.top` mit dem untenstehenden Skript zugänglich ist. Wenn es nicht verfügbar ist, bieten Sie alternative Logik oder eine Fallback-Benutzerfreundlichkeit.

  > [!NOTE]
  > Obwohl wir empfehlen, die Verwendung von `window.top` zu vermeiden, ist dieses Skript für diejenigen Edge-Fälle enthalten, in denen es die einzige verfügbare Option sein könnte.

    ```javascript
    function isTopAccessible() {
        try {
                window.top.location;
                return true;
            }
            catch (err) {
                return false;
            }
        }
    }

    var canAccess = isTopAccessible();
    alert(canAccess);
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Die Verwendung von `window.top` sollte nach Möglichkeit vermieden werden. Im Folgenden finden Sie Beispiele für häufig vorkommende Muster.

> [!WARNING]
> Diese Szenarien sollten vermieden werden.

```javascript
// Getting or setting variables at the top level
var myValue = window.top.myGlobalVariable;

// Attempting to access the Xrm namespace at the top level
myValue = window.top.Xrm.Page.getAttribute("field1");
```

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

In den genannten Szenarien bezieht sich `window.top` auf das Fenster, das einem Anwendungskontext außerhalb von Dynamics 365 gehört. Aufgrund der unterschiedlichen Herkunft stellt der Browser dem Benutzer einen herkunftsübergreifenden Sicherheitsfehler dar.

### <a name="see-also"></a>Siehe auch
[Anwenden von Geschäftslogik mit Client-Skripting in modellgesteuerten Anwendungen mit JavaScript](/powerapps/developer/model-driven-apps/client-scripting)<br/>
[Ereignisse in Formularen und in Rastern in Modell-angetriebenen Apps](/powerapps/developer/model-driven-apps/clientapi/events-forms-grids)<br/>