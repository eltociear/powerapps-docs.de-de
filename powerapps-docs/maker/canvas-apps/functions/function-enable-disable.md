---
title: Funktionen „Enable“ und „Disable“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktionen „Enable“ und „Disable“ in PowerApps
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
ms.openlocfilehash: b35d819730715917f3092ca803b9a38ea9173edc
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "31825117"
---
# <a name="enable-and-disable-functions-in-powerapps"></a>Enable- und Disable-Funktionen in PowerApps
Schaltet ein [Signal](signals.md) ein oder aus.

## <a name="overview"></a>Übersicht
Einige Signale lassen sich häufig ändern, was eine erneute Berechnung durch die App erfordert.  Schnelle Änderungen über längere Zeit können die Batterie eines Geräts schneller entleeren. Sie können diese Funktionen verwenden, um ein Signal manuell ein- oder auszuschalten.

Wenn ein Signal nicht verwendet wird, wird es automatisch deaktiviert.

## <a name="description"></a>Beschreibung
Die Funktionen **Enable** und **Disable** aktivieren bzw. deaktivieren ein Signal.

Diese Funktionen sind derzeit nur für das Signal **[Location](signals.md)** verfügbar.

Diese Funktionen besitzen keinen Rückgabewert. Verwenden Sie sie nur in [Verhaltensformeln](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Syntax
**Enable**( *Signal* )<br>**Disable**( *Signal* )

* *Signal*: erforderlich.  Das zu aktivierende oder zu deaktivierende Signal.

