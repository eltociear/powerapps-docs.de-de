---
title: 'Power BI-Kachel-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich von Eigenschaften und Beispiele, über das Power BI-Kachel-Steuerelement
author: fikaradz
manager: kfile
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 07/07/2016
ms.author: fikaradz
ms.openlocfilehash: 9df201f5d2fd4017debe47626aedaaa2c735682f
ms.sourcegitcommit: 16a2eeaa4ad9218682143411b609cb961dbcfa91
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886376"
---
# <a name="power-bi-tile-control-in-powerapps"></a>Power BI-Kachel-Steuerelement in PowerApps

Ein Steuerelement, das eine [Power BI](https://powerbi.microsoft.com)-Kachel in einer App anzeigt.

Sie verfügen nicht über Power BI? [Registrieren Sie sich](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi).

## <a name="description"></a>Beschreibung

Profitieren Sie von Ihrer vorhandenen Datenanalyse und -berichterstellung, indem Sie Ihre **[Power BI-Kacheln](https://docs.microsoft.com/power-bi/service-dashboard-tiles)** in Ihren Apps anzeigen. Geben Sie die anzuzeigende Kachel an, indem Sie ihre Eigenschaften **Workspace**, **Dashboard** und **Tile** auf der Registerkarte **Daten** im Optionsbereich festlegen.

## <a name="sharing-and-security"></a>Freigabe und Sicherheit

Wenn Sie eine App freigeben, die Power BI-Inhalt enthält, müssen Sie nicht nur die App selbst sondern auch das [Dashboard](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports) freigeben, aus dem die Kachel stammt. Andernfalls wird der Power BI-Inhalt auch nicht für Benutzer, die die App öffnen, angezeigt. Apps, die Power BI-Inhalt enthalten, berücksichtigen die Berechtigungen für diesen Inhalt.

## <a name="performance"></a>Leistung

Es wird nicht empfohlen, mehr als drei Power BI-Kacheln zur gleichen Zeit in einer App zu laden. Sie können den Ladungsvorgang von Kacheln und auch das Entladen steuern, indem Sie die Eigenschaft **LoadPowerBIContent** festlegen.

## <a name="key-properties"></a>Haupteigenschaften

**Workspace**: Der Power BI-Arbeitsbereich, aus dem die Kachel stammt.

**Dashboard**: Das Power BI-Dashboard, aus dem die Kachel stammt.

**Tile**: Der Name der Power BI-Kachel, die angezeigt werden soll.

**LoadPowerBIContent**: Wenn „TRUE“ gilt, wird der Power BI-Inhalt geladen und angezeigt. Wenn diese Einstellung auf FALSE festgelegt ist, wird der Power BI-Inhalt entladen, wodurch der Arbeitsspeicher freigeben und die Leistung optimiert wird.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt. Standardmäßig wird der Power BI-Bericht geöffnet, der der Kachel zugeordnet ist.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel

1. Öffnen Sie auf der Registerkarte **Einfügen** das Menü **Steuerelemente**, und fügen Sie dann das Steuerelement **Power BI-Kachel** hinzu.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

2. Klicken oder tippen Sie auf der Registerkarte **Daten** im Optionsbereich für die Einstellung **Arbeitsbereich** auf **Mein Arbeitsbereich**.

3. Wählen Sie in der Liste der Dashboards ein Dashboard aus, und wählen Sie eine Kacheln in der Liste der Kacheln aus.

    Das Steuerelement rendert die Power BI-Kachel.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

Bei der **Power BI-Kachel** handelt es sich bloß um einen Container für Power BI-Inhalt. Weitere Informationen zu Inhalt, auf den zugegriffen werden kann, finden Sie unter [Barrierefreiheit in Power BI Desktop-Berichten](https://docs.microsoft.com/power-bi/desktop-accessibility).

Wenn der Power BI-Inhalt über keinen Titel verfügt, fügen Sie ggf. mithilfe des Steuerelements **[Bezeichnung](control-text-box.md)** einen Titel hinzu, damit Sprachausgaben unterstützt werden. Sie können die Bezeichnung unmittelbar vor der Power BI-Kachel platzieren.
