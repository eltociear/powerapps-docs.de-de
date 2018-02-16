---
title: 'Power BI-Kachel-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich von Eigenschaften und Beispiele, über das Power BI-Kachel-Steuerelement"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/07/2016
ms.author: fikaradz
ms.openlocfilehash: 1f351877e3c05b83b4bd9cfa104a7eb22cef5028
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="power-bi-tile-control-in-powerapps"></a>Power BI-Kachel-Steuerelement in PowerApps
Ein Steuerelement, das eine [Power BI](https://powerbi.microsoft.com)-Kachel in einer App anzeigt.

## <a name="description"></a>Beschreibung
Profitieren Sie von Ihrer vorhandenen Datenanalyse und -berichterstellung, indem Sie Ihre **[Power BI-Kacheln](https://docs.microsoft.com/power-bi/service-dashboard-tiles)** in Ihren Apps anzeigen.  Wählen Sie die anzuzeigende Kachel aus, indem Sie ihre Eigenschaften **Workspace**, **Dashboard** und **Tile** auf der Registerkarte **Daten** im Optionsbereich festlegen.

## <a name="sharing-and-security"></a>Freigabe und Sicherheit
Nach der Freigabe ist die PowerApp für alle Benutzer zugänglich, die über Zugriffsberechtigungen für die App verfügen.  Um jedoch den Power BI-Inhalt für diese Benutzer sichtbar zu machen, muss das Dashboard, aus dem die Kachel stammt, für den Benutzer in Power BI [freigegeben](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports) werden.  Dadurch wird sichergestellt, dass Power BI-Freigabeberechtigungen berücksichtigt werden, wenn in einer App auf Power BI-Inhalt zugegriffen wird.

## <a name="key-properties"></a>Haupteigenschaften
**Workspace**: Der Power BI-Arbeitsbereich, aus dem die Kachel stammt.

**Dashboard**: Das Power BI-Dashboard, aus dem die Kachel stammt.

**Tile**: Der Name der Power BI-Kachel, die angezeigt werden soll.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt. In der Standardeinstellung gelangt der Benutzer zum Power BI-Bericht, der zur Kachel gehört.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel
1. Fügen Sie ein **Power BI-Kachel**-Steuerelement von der Registerkarte **Einfügen**, Menü **Steuerelemente** ein.  
2. Wählen Sie auf der Registerkarte **Daten** im Optionsbereich für die Einstellung **Arbeitsbereich** „Mein Arbeitsbereich“ aus.  Wählen Sie ein Dashboard aus der Liste der Dashboards und eine Kachel aus der Liste der Kacheln aus.
   
    Das Steuerelement rendert die Power BI-Kachel.
   
    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?
   
   Sie verfügen nicht über Power BI? [Registrieren Sie sich](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi).

