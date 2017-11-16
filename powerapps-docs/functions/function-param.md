---
title: "Funktionen „Download“, „Launch“ und „Param“ | Microsoft-Dokumentation"
description: "Referenzinformationen, einschließlich Syntax und Beispiele, für die Download-, Launch- und Param-Funktionen in PowerApps"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 4ed646431263e96a079483bc514c8154b6d9b653
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="download-launch-and-param-functions-in-powerapps"></a>Download-, Launch- und Param-Funktionen in PowerApps
Lädt eine Webseite herunter oder startet eine Webseite oder eine App mit Parametern.  

## <a name="description"></a>Beschreibung
Die **Download**-Funktion lädt eine Datei aus dem Web auf das lokale Gerät herunter.  Der Benutzer wird aufgefordert, einen Speicherort zum Speichern der Datei anzugeben.  **Download** gibt den Speicherort zurück, wo die Datei lokal als Zeichenfolge gespeichert wurde.  

Die **Launch**-Funktion startet eine Webseite oder eine App.  Diese Funktion kann optional Parameter an die App übergeben.  

Die **Param**-Funktion ruft einen an die App übergebenen Parameter ab, wenn sie gestartet wurde.  Wenn der benannte Parameter nicht übergeben wurde, gibt **Param** *leer* zurück.

## <a name="syntax"></a>Syntax
**Download**( *Address* )

* *Address*: Erforderlich.  Die Adresse einer Webressource, die heruntergeladen werden soll.

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address*: Erforderlich.  Die Adresse einer Webseite oder die ID einer App, die gestartet werden soll.
* *ParameterName(s)*: Optional.  Parametername
* *ParameterValue(s)*: Optional.  Entsprechende Parameterwerte, die an die App oder Webseite übergeben werden sollen.

**Param**( *ParameterName* )

* *ParameterName*: Erforderlich.  Der Name des Parameters, der an die App übergeben wurde.

