---
title: Funktionen „Enable“ und „Disable“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktionen „Enable“ und „Disable“ in PowerApps
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 3b9801e804284cb52d389aa0c57d1247a008dd0d
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
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
