---
title: Funktionen „Download“, „Launch“ und „Param“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispiele, für die Download-, Launch- und Param-Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: f2af4fef413aa5502c57e7158d9efdddd36757c9
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39021870"
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

