---
title: Funktionen „EncodeUrl“ und „PlainText“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „EncodeUrl“ und „PlainText“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 3f7df27ed5b49d60437ba8e5a070fcb676f828e4
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39020697"
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
