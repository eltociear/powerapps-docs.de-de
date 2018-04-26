---
title: Funktionen „Download“, „Launch“ und „Param“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Download-, Launch- und Param-Funktionen in PowerApps
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 146372c723df6089890100abd67d1175ba4b4a04
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
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

