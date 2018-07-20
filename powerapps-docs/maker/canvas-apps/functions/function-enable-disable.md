---
title: Funktionen „Enable“ und „Disable“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktionen „Enable“ und „Disable“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 1b5395459dd5833d054755dadca37bc9b39785c9
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39019064"
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

