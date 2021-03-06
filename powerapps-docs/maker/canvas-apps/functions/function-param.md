---
title: Funktionen „Download“, „Launch“ und „Param“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "herunterladen", "starten" und "param" in Canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 15bef0fc30c2efe90647d9f190cf8917de11a109
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536937"
ms.PowerAppsDecimalTransform: true
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>Download-, Launch-und param-Funktionen in Canvas-apps
Lädt eine Webseite herunter oder startet eine Webseite oder eine App mit Parametern.  

## <a name="description"></a>Beschreibung
Die **Download**-Funktion lädt eine Datei aus dem Web auf das lokale Gerät herunter. Der Benutzer wird aufgefordert, einen Speicherort zum Speichern der Datei anzugeben.  **Download** gibt den Speicherort zurück, wo die Datei lokal als Zeichenfolge gespeichert wurde.  

Die **Launch**-Funktion startet eine Webseite oder eine App.  Diese Funktion kann optional Parameter an die App übergeben.

In Internet Explorer und Microsoft Edge öffnet die **Launch** -Funktion eine Website oder app nur dann, wenn die Sicherheitseinstellungen identisch oder höher sind als die der APP, die die Funktion enthält. Wenn Sie z. b. die **Start** Funktion einer APP hinzufügen, die in der Sicherheitszone " **Vertrauenswürdige Sites** " ausgeführt wird, stellen Sie sicher, dass sich die Website oder die APP, die Sie öffnen möchten, in der Zone " **Vertrauenswürdige Sites** " oder " **Lokales Intranet** " befindet (nicht in  **Eingeschränkte Sites**). Weitere Informationen finden Sie unter [Ändern der Sicherheits-und Datenschutzeinstellungen für Internet Explorer 11](https://support.microsoft.com/help/17479/windows-internet-explorer-11-change-security-privacy-settings).  

Die **Param**-Funktion ruft einen an die App übergebenen Parameter ab, wenn sie gestartet wurde. Wenn der benannte Parameter nicht übergeben wurde, gibt **Param** *leer* zurück.

## <a name="syntax"></a>Syntax
**Download**( *Address* )

* *Address*: Erforderlich.  Die Adresse einer Webressource, die heruntergeladen werden soll.

**Launch**( *Address* [; *ParameterName1*; *ParameterValue1*; ... ] )

* *Address*: Erforderlich.  Die Adresse einer Webseite oder die ID einer App, die gestartet werden soll.
* *ParameterName(s)* : Optional.  Parametername
* *ParameterValue(s)* : Optional.  Entsprechende Parameterwerte, die an die App oder Webseite übergeben werden sollen.

**Param**( *ParameterName* )

* *ParameterName*: Erforderlich.  Der Name des Parameters, der an die App übergeben wurde.

