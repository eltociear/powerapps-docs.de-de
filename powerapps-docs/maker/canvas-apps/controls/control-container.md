---
title: 'Container-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Container Steuerelement
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 9/20/2019
ms.author: emcoope
ms.reviewer: tapanm-msft
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e22800dc929c32f0a605137b6dc94820b984459c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727336"
---
# <a name="container-control-in-power-apps-experimental"></a>Container-Steuerelement in powerapps (experimentell)
Bietet die Möglichkeit, Hierarchie zu erstellen.

> [!IMPORTANT]
> Dies ist ein experimentelles Feature. Experimentelle Features können sich noch deutlich verändern oder im Laufe der Zeit wieder vollständig verschwinden.
> Weitere Informationen finden Sie Untergrund Legendes zu [experimentellen Features und Vorschau Features in Power apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview).

## <a name="description"></a>Beschreibung
 Der Container kann eine Reihe von Steuerelementen enthalten und über eigene Eigenschaften verfügen. 

Sie können beginnen, indem Sie einen leeren Container einfügen, ihn anpassen, indem Sie ihm Steuerelemente hinzufügen, seine Größe ändern, ihn verschieben, ausblenden und andere Änderungen vornehmen. Sie können auch mit einer Reihe von Steuerelementen beginnen, diese auswählen und Sie einem Container über das Kontextmenü in der Strukturansicht hinzufügen oder mit der rechten Maustaste auf den Zeichenbereich klicken. 

## <a name="properties"></a>Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist). 

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist). 


## <a name="known-limitations"></a>Bekannte Einschränkungen

Container funktionieren nicht mit Canvas-Komponenten oder innerhalb von Formularen. 

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Worin besteht der Unterschied zwischen einem Container und einer Gruppe?**
Bei der Erstellungs Gruppe handelt es sich um ein schlankes Konzept zum Verschieben von Steuerelementen und zum Massen bearbeiten ähnlicher Eigenschaften von Steuerelementen in der Gruppe. Die Erstellungs Gruppe wirkt sich nicht auf das Layout der APP aus. 

Das Container Steuerelement, das zuvor im experimentellen als Ersatz für die Erstellungs Gruppe ausgeliefert wurde, wurde als erweiterte Gruppe umbenannt. Es wurde in das Container-Steuerelement umbenannt, da es einen Wert sowohl in einer Lightweight-Erstellungs Gruppe als auch in einem Strukturen-Container Steuerelement mit zusätzlichen Eigenschaften gibt. 

