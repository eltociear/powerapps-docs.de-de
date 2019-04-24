---
title: Eigenschaften von Bedienungshilfen für canvas-apps | Microsoft-Dokumentation
description: Referenzinformationen zu Eigenschaften wie z. B. TabIndex und QuickInfo
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/26/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5fa8b6fecdf690114cbf6a0945f2dfec66b067c3
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560413"
---
# <a name="accessibility-properties-for-canvas-apps"></a>Eigenschaften von Bedienungshilfen für Canvas-apps

Hier geht es um die Konfiguration von Eigenschaften, die für Benutzer mit Sehschwäche als Hilfe für alternative Interaktionsmöglichkeiten mit Steuerelementen dienen.

## <a name="properties"></a>Eigenschaften

**AccessibleLabel**: Bezeichnung für Sprachausgaben. Durch einen leeren Wert für Bild-, Symbol- und Formsteuerelemente werden diese für die Bildschirmsprachausgabe unsichtbar und als Dekoration behandelt.

**Live** : wie Änderungen an Inhalten die Sprachausgabe sollten. Verfügbar nur in der **[Bezeichnung](control-text-box.md)** Steuerelement.

* Bei Festlegung auf **aus**, die Sprachausgabe keine Änderungen bekanntgeben zu können.
* Bei Festlegung auf **Polite**, die Sprachausgabe abgeschlossen ist, das halten öffentlicher Vorträge Ankündigung: Änderungen, die beim Ausführen die Sprachausgabe gesprochen habe.
* Bei Festlegung auf **Assertive**, die Sprachausgabe von Hardwareinterrupts benötigt hat sich alle Änderungen, die aufgetreten sind, während die Sprachausgabe gesprochen habe, ankündigen zu können.

Erfahren Sie, wie Sie [dynamische Änderungen mit live-Regionen ankündigen](../accessible-apps-live-regions.md).

**TabIndex**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

Mit dem Standardwert 0 wird die Standardaktivierreihenfolge basierend auf der XY-Koordinate des Steuerelements angegeben.  Wenn Sie einen höheren Wert als 0 wählen, wird die Aktivierreihenfolge für alle Steuerelemente mit den Standardwerten entsprechend verschoben.  Ein Steuerelement mit einem TabIndex-Wert von 2 hat in der Aktivierreihenfolge Vorrang vor einem Steuerelement mit dem TabIndex-Wert 3 oder höher.

Beachten Sie, dass bei Containern, z.B. Formular- und Katalog-Steuerelementen, immer erst alle Elemente des Containers durchlaufen werden, bevor die Steuerelemente außerhalb des Containers an die Reihe kommen.  Die Aktivierreihenfolge des Containers entspricht der Reihenfolge des niedrigsten TabIndex-Werts eines untergeordneten Steuerelements.

Durch Festlegen von TabIndex auf den Wert -1 wird der Registerkartenzugriff auf das Steuerelement deaktiviert; im Fall von Bildern, Symbolen und Formen werden diese zu nicht interaktiven Elementen.
