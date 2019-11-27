---
title: Sie können NavBar deaktivieren, wenn Sie Entitätsformulare von Ansichten programmgesteuert öffnen | MicrosoftDocs
description: Das Öffnen von Entitätsformularen oder Ansichten mit einer URL kann zu langsamerer Clientleistung auf Latenznetzwerken führen, wenn die Navigationsleiste (NavBar) aktiviert ist.
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
ms.date: 3/04/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 359c505c3df1f2b88268dba2e7da005465f29d84
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748772"
---
# <a name="consider-disabling-navbar-when-programmatically-opening-entity-forms-or-views"></a>Sie können NavBar deaktivieren, wenn Sie Entitätsformulare von Ansichten programmgesteuert öffnen

**Kategorie**: Design, Leistung

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Das Öffnen von Entitätsformularen oder Ansichten mit einer URL kann zu langsamerer Clientleistung auf Latenznetzwerken führen, wenn die Navigationsleiste (NavBar) aktiviert ist.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Ermitteln Sie, ob Ihre Benutzer die vollständige Navigationsleiste benötigen, wenn Sie Anpassungen erstellen, die Entitätsformulare oder Ansichten über eine URL öffnen. In den meisten Fällen klicken Benutzer auf einen Link, um ein Entitätsformular zu öffnen, schnell etwas Arbeit zu erledigen und den Datensatz zu schließen.  Das Deaktivieren der Navigationsleiste senkt die Menge der zu ladenden Ressourcen. Dadurch wird die Anzahl der gestellten Netzwerkanforderungen gesenkt.  

Beim Konstruieren der URLs, um Entitätsformulare oder Ansichten zu öffnen, implementieren Sie `navbar=off` innerhalb des Abfragezeichenfolgeparameters für die `main.aspx`-Seite. Im folgenden Beispiel wird ein Kontoentitätsformular mit der Navigationsleiste deaktiviert.

```JavaScript
function disableNavBar() {
    var globalContext = Xrm.Utility.getGlobalContext();
    return globalContext.getClientUrl() + "/main.aspx?appid=9411ee28-4310-e811-a839-000d3a33a7cb&etc=1&id={00000000-0000-0000-00AA-000010001004}&pagetype=entityrecord&navbar=off";
}
```

> [!IMPORTANT]
> Der navbar=off-Abfragezeichenfolgenparameter ist nur auf der `main.aspx`-Seite verfügbar. 

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

> [!WARNING] 
> Diese Szenarien sollten vermieden werden. 

Das die Navigationsleiste (NavBar) aktiviert bleibt, bedeutet nicht, dass Benutzer Leistungsprobleme bemerken. Allerdings müssen weitere Ressourcen in das Entitätsformular oder für die Ansicht geladen werden. Dafür sind weitere Netzwerkanforderungen erforderlich.  Es wurde beobachtet, dass dies auf hochlatenten Netzwerken geachtet zu einer schlechten Benutzerfreundlichkeit führen kann.

Es folgt ein Beispiel einer konstruierten URL mit aktivierter NavBar

```JavaScript
function enabledNavBar() {
    var globalContext = Xrm.Utility.getGlobalContext();
    // By default, NavBar is set to true if you do not include the parameter in the query string:
    return globalContext.getClientUrl() + "/main.aspx?appid=9411ee28-4310-e811-a839-000d3a33a7cb&etc=1&id={00000000-0000-0000-00AA-000010001004}&pagetype=entityrecord";
}

function enabledNavBarExplicit() {
    var globalContext = Xrm.Utility.getGlobalContext();
    // Explicitly defining that the NavBar will be enabled
    return globalContext.getClientUrl() + "/main.aspx?appid=9411ee28-4310-e811-a839-000d3a33a7cb&etc=1&id={00000000-0000-0000-00AA-000010001004}&pagetype=entityrecord&navbar=on";
}
```

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Wenn Sie weitere Datensätze aus den modellgestützten Apps öffnen, wird die Navigationsleiste mit den Bereichen und Unterbereichen geladen, die innerhalb der Siteübersicht definiert werden.  Darüber hinaus wird das [Office-App-Startprogramm](https://support.office.com/article/Meet-the-Office-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) gerendert, das die Office 365-Apps anzeigt, auf die der Benutzer Zugriff hat.<br/>
![Vergleich der aktivierten und deaktivierten NavBar](../media/navbar_comparison_enabled_disabled.png)

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Öffnen von Formularen, Ansichten, Dialogen und Berichten mit einer URL](../../open-forms-views-dialogs-reports-url.md)
