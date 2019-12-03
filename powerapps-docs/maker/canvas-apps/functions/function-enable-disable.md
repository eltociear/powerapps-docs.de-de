---
title: Funktionen „Enable“ und „Disable“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "aktivieren" und "deaktivieren" in powerapps
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
ms.openlocfilehash: af1522934bcfee13c00950a3686583393699d0ad
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731103"
---
# <a name="enable-and-disable-functions-in-power-apps"></a>Aktivieren und Deaktivieren von Funktionen in Power apps
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

