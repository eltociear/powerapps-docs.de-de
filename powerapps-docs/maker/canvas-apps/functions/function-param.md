---
title: Funktionen „Download“, „Launch“ und „Param“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen, für die Download-, Launch- und Param-Funktionen in Canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4a53d8c20bd4b7784cb94daa574682c041f104ea
ms.sourcegitcommit: b316e0eee9946ef09e0512577ce2d11cd27aa864
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59508307"
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>Download-, Launch- und Param-Funktionen in Canvas-apps
Lädt eine Webseite herunter oder startet eine Webseite oder eine App mit Parametern.  

## <a name="description"></a>Beschreibung
Die **Download**-Funktion lädt eine Datei aus dem Web auf das lokale Gerät herunter. Der Benutzer wird aufgefordert, einen Speicherort zum Speichern der Datei anzugeben.  **Download** gibt den Speicherort zurück, wo die Datei lokal als Zeichenfolge gespeichert wurde.  

Die **Launch**-Funktion startet eine Webseite oder eine App.  Diese Funktion kann optional Parameter an die App übergeben.

In Internet Explorer und Microsoft Edge der **starten** -Funktion öffnet eine Website oder app nur dann, wenn ihre Sicherheitseinstellungen identisch sind oder höher als die der app, die die Funktion enthält. Wenn Sie z. B. Hinzufügen der **starten** Funktion, um eine app, die ausgeführt wird, in der **vertrauenswürdige Sites** Security zone, stellen Sie sicher, dass die Website oder app, die Sie möchten, dass die Funktion, öffnen Sie in der **vertrauenswürdige Websites** oder **lokales Intranet** Zone (nicht im **eingeschränkte Sites**). Weitere Informationen finden Sie unter: [Ändern der Einstellungen für Sicherheit und Datenschutz für Internet Explorer 11](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings).  

Die **Param**-Funktion ruft einen an die App übergebenen Parameter ab, wenn sie gestartet wurde. Wenn der benannte Parameter nicht übergeben wurde, gibt **Param** *leer* zurück.

## <a name="syntax"></a>Syntax
**Download**( *Address* )

* *Address*: Erforderlich.  Die Adresse einer Webressource, die heruntergeladen werden soll.

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address*: Erforderlich.  Die Adresse einer Webseite oder die ID einer App, die gestartet werden soll.
* *ParameterName(s)*: Optional.  Parametername
* *ParameterValue(s)*: Optional.  Entsprechende Parameterwerte, die an die App oder Webseite übergeben werden sollen.

**Param**( *ParameterName* )

* *ParameterName*: Erforderlich.  Der Name des Parameters, der an die App übergeben wurde.

