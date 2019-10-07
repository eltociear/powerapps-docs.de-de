---
title: Funktionen „EncodeUrl“ und „PlainText“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „EncodeUrl“ und „PlainText“ in PowerApps
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
ms.openlocfilehash: c21cae9e39e3a9a1461ac3fafe576f40b70c0818
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985018"
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>Die Funktionen „EncodeUrl“ und „PlainText“ in PowerApps
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