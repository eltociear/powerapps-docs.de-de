---
title: "Funktionen „EncodeUrl“ und „PlainText“ | Microsoft-Dokumentation"
description: "Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „EncodeUrl“ und „PlainText“ in PowerApps"
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
ms.openlocfilehash: a511d731c8dd94c57ec9846d853fec1bef10ab0a
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>Die Funktionen „EncodeUrl“ und „PlainText“ in PowerApps
Codiert und decodiert Zeichenfolgen

## <a name="description"></a>Beschreibung
Die **EncodeUrl**-Funktion codiert eine URL-Zeichenfolge, indem sie nicht alphanumerische Zeichen durch „%“ und eine hexadezimale Zahl ersetzt.  

Die **PlainText**-Funktion entfernt HTML- und XML-Tags und konvertiert Tags wie die folgenden in ein entsprechendes Symbol:

* **&amp;nbsp;**
* **&amp;quot;**

Der Rückgabewert dieser Funktionen ist die codierte oder decodierte Zeichenfolge.   

## <a name="syntax"></a>Syntax
**EncodeUrl**( *String* )

* *Zeichenfolge*: erforderlich.  Die zu codierende URL

**PlainText**( *String* )

* *Zeichenfolge*: erforderlich. Die Zeichenfolge, aus der HTML- und XML-Tags entfernt werden sollen

## <a name="examples"></a>Beispiele
Wenn Sie einen RSS-Feed in einem Textkatalog anzeigen, und Sie anschließend die **[Text](../controls/properties-core.md)**-Eigenschaft einer Bezeichnung in dem Katalog auf **ThisItem.description** festlegen, zeigt die Bezeichnung möglicherweise unformatierten HTML- oder XML-Code wie in folgendem Beispiel:

    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>

Wenn Sie die **[Text](../controls/properties-core.md)**-Eigenschaft auf **PlainText(ThisItem.description)** festlegen, wird der Text wie in folgendem Beispiel angezeigt:

    We have done an unusually "deep" globalization and localization.
