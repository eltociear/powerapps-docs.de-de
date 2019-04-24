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
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9956332c35b4df2773b2634cb7f66d2ea96469e4
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551052"
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>Die Funktionen „EncodeUrl“ und „PlainText“ in PowerApps
Codiert und decodiert Zeichenfolgen

## <a name="description"></a>Beschreibung
Die **EncodeUrl** Funktion codiert eine URL-Zeichenfolge, die bestimmte nicht-alphanumerischen Zeichen mit dem % und eine hexadezimale Zahl ersetzt.  

Die **nur-Text** -Funktion entfernt HTML- und XML-Tags, konvertieren bestimmte Tags wie diese in ein entsprechendes Symbol:

* **&amp;nbsp;**
* **&amp;quot;**

Der Rückgabewert dieser Funktionen ist die codierte oder decodierte Zeichenfolge. Diese Funktion entfernt nicht alle HTML- und XML-Tags. 

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
