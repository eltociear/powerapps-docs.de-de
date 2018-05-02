---
title: Eigenschaften von Bedienungshilfen | Microsoft-Dokumentation
description: Enthält Referenzinformationen zu Eigenschaften, z.B. TabIndex, QuickInfo.
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 01/26/2017
ms.author: fikaradz
ms.openlocfilehash: 94d15ff14ccd57ccc392eae47b6c10d6cec50bb1
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="accessibility-properties-in-powerapps"></a>Eigenschaften von Bedienungshilfen in PowerApps
Hier geht es um die Konfiguration von Eigenschaften, die für Benutzer mit Sehschwäche als Hilfe für alternative Interaktionsmöglichkeiten mit Steuerelementen dienen.

### <a name="properties"></a>Eigenschaften
**AccessibleLabel**: Bezeichnung für Sprachausgaben. Durch einen leeren Wert für Bild-, Symbol- und Formsteuerelemente werden diese für die Bildschirmsprachausgabe unsichtbar und als Dekoration behandelt.

**TabIndex**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

Mit dem Standardwert 0 wird die Standardaktivierreihenfolge basierend auf der XY-Koordinate des Steuerelements angegeben.  Wenn Sie einen höheren Wert als 0 wählen, wird die Aktivierreihenfolge für alle Steuerelemente mit den Standardwerten entsprechend verschoben.  Ein Steuerelement mit einem TabIndex-Wert von 2 hat in der Aktivierreihenfolge Vorrang vor einem Steuerelement mit dem TabIndex-Wert 3 oder höher.

Beachten Sie, dass bei Containern, z.B. Formular- und Katalog-Steuerelementen, immer erst alle Elemente des Containers durchlaufen werden, bevor die Steuerelemente außerhalb des Containers an die Reihe kommen.  Die Aktivierreihenfolge des Containers entspricht der Reihenfolge des niedrigsten TabIndex-Werts eines untergeordneten Steuerelements.

Durch Festlegen von TabIndex auf den Wert -1 wird der Registerkartenzugriff auf das Steuerelement deaktiviert; im Fall von Bildern, Symbolen und Formen werden diese zu nicht interaktiven Elementen.
