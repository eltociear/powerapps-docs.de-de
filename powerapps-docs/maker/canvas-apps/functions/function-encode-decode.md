---
title: Funktionen „EncodeUrl“ und „PlainText“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "EncodeURL" und "Plaintext" in powerapps
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
ms.openlocfilehash: fe02683e0b420a97fe674543a2f0d16bb076f266
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731031"
---
# <a name="encodeurl-and-plaintext-functions-in-power-apps"></a>Funktionen "EncodeURL" und "Plaintext" in powerapps
Codiert und decodiert Zeichenfolgen

## <a name="description"></a>Beschreibung
Die **encode URL** -Funktion codiert eine URL-Zeichenfolge und ersetzt bestimmte nicht-alphanumerische Zeichen durch% und eine hexadezimale Zahl.  

Die **Klartext** -Funktion entfernt HTML-und XML-Tags, wobei bestimmte Tags, z. b. diese, in ein entsprechendes Symbol umgerechnet werden:

* **&amp;nbsp;**
* **&amp;quot;**

Der Rückgabewert dieser Funktionen ist die codierte oder decodierte Zeichenfolge. Diese Funktion entfernt nicht alle HTML-und XML-Tags. 

## <a name="syntax"></a>Syntax
**EncodeUrl**( *String* )

* *Zeichenfolge*: erforderlich.  Die zu codierende URL

**PlainText**( *String* )

* *Zeichenfolge*: erforderlich. Die Zeichenfolge, aus der HTML- und XML-Tags entfernt werden sollen

## <a name="examples"></a>Beispiele
Wenn Sie einen RSS-Feed in einem Textkatalog anzeigen, und Sie anschließend die **[Text](../controls/properties-core.md)** -Eigenschaft einer Bezeichnung in dem Katalog auf **ThisItem.description** festlegen, zeigt die Bezeichnung möglicherweise unformatierten HTML- oder XML-Code wie in folgendem Beispiel:

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>
```

Wenn Sie die **[Text](../controls/properties-core.md)** -Eigenschaft auf **PlainText(ThisItem.description)** festlegen, wird der Text wie in folgendem Beispiel angezeigt:

```
    We have done an unusually "deep" globalization and localization.
```