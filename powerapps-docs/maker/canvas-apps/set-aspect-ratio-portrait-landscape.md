---
title: Ändern der Bildschirmgröße und -ausrichtung einer Canvas-App | Microsoft-Dokumentation
description: Schrittanleitung zum Ändern von Einstellungen, z.B. von Bildschirmgröße und -ausrichtung einer Canvas-App in PowerApps
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c4d9f648a4519ef30887d8d0739d7dc3d940555b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536038"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-powerapps"></a>Ändern der Bildschirmgröße und -ausrichtung einer Canvas-App in PowerApps
Passen Sie eine Canvas-App an, indem Sie Bildschirmgröße und -ausrichtung ändern.

## <a name="prerequisites"></a>Voraussetzungen

Erstellen Sie eine app oder eine für die Bearbeitung, und wählen Sie dann **Anwendungseinstellungen** auf die **Datei** Menü.

## <a name="change-screen-size-and-orientation"></a>Ändern der Bildschirmgröße und -ausrichtung
1. Wählen Sie unter **App settings**  (App-Einstellungen) die Option **Screen size + orientation**  (Bildschirmgröße und -ausrichtung) aus.

    ![Option zum Ändern der Bildschirmgröße und -ausrichtung einer App](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. In der **Ausrichtung** Liste **Hochformat** oder **Querformat**.

1. (Gilt nur für Tablet-apps) Klicken Sie unter **Seitenverhältnis**, führen Sie einen der folgenden Schritte aus:

    - Wählen Sie das Seitenverhältnis, das dem Zielgerät für diese app übereinstimmt.
    - Wählen Sie **benutzerdefinierte** , legen Sie Ihren eigenen Größe, und geben Sie eine Breite zwischen 50-3840 und eine Höhe zwischen 50-2160.

    ![Ändern des Seitenverhältnisses einer Tablet-App](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. Klicken Sie unter **an anpassen**, geben Sie entweder **auf** oder **aus**.

    Diese Einstellung ist standardmäßig so, dass app-Bildschirme Größe auf dem Gerät den verfügbaren Platz angepasst. Wenn diese Einstellung ist für der app **Breite** Eigenschaft entspricht der **DesignWidth**, und der app **Höhe** entspricht der **DesignHeight**.

    Wenn Sie diese Einstellung deaktivieren, wird die app an das Seitenverhältnis des Geräts auf dem es ausgeführt wird, und die gesamte verfügbare Platz angepasst. Die app nicht skaliert werden und daher Bildschirme Weitere Informationen anzeigen können.

    Wenn diese Einstellung deaktiviert ist, **Seitenverhältnis sperren** ist automatisch aktiviert und deaktiviert. Darüber hinaus die **Breite** alle Bildschirme-Eigenschaftensatz auf `Max(App.Width, App.DesignWidth)`, und ihre **Höhe** -Eigenschaftensatz auf `Max(App.Height, App.DesignHeight)` , damit sie die Dimensionen des Fensters verfolgen, in dem die app ausgeführt wird. Mit dieser Änderung können Sie apps erstellen, die auf verschiedenen Geräten und fensterabmessungen reagieren. Weitere Informationen finden Sie unter: [Dynamisches Layout erstellen](create-responsive-layout.md)

1. Geben Sie unter **Seitenverhältnis sperren** entweder **Ein** oder **Aus** an.

    Wenn diese Einstellung aktiviert ist, behält die app die bildschirmausrichtung und das Originalseitenverhältnis beibehalten, die Sie in den Schritten 2 und 3, unabhängig vom Gerät angegeben. Beispielsweise behält eine phoneapp, die in einem Webbrowser ausgeführt wird, das Verhältnis für ein Smartphone, einen dunklen Balken auf jeder Seite statt füllen das Fenster angezeigt.

    Wenn diese Einstellung deaktiviert ist, passt sich die app an das Seitenverhältnis des Geräts auf dem es ausgeführt wird (und die Benutzeroberfläche verzerren, falls erforderlich).

1. Geben Sie unter **Bildschirmausrichtung sperren** entweder **Ein** oder **Aus** an.

    Wenn Sie die Ausrichtung der app sperren, behält die app die Ausrichtung, die Sie angeben. Wenn die app auf einem Gerät ausgeführt wird, für die der Bildschirm in eine andere Ausrichtung ist, wird die app falsch angezeigt, und möglicherweise unerwünschte Ergebnisse angezeigt. Wenn Sie die Ausrichtung der app entsperren, passt es auf die bildschirmausrichtung des Geräts auf dem er ausgeführt wird.

    Sie können auch die Ausrichtung der app ändern, indem Sie aktivieren **aktivieren-app, die Benutzeroberfläche zum Einbetten** in **Erweiterte Einstellungen**. Dieses Feature oben links richtet die app aus, wenn es eingebettet ist, und die Hintergrundfarbe der hostingcanvas auf weiß ändert.

1. Zum Speichern Ihrer Änderungen wählen Sie **Anwenden** aus.

## <a name="next-step"></a>Nächster Schritt
Wählen Sie im Menü **Datei** die Option **Speichern** aus, um Ihre App mit den neuen Einstellungen erneut zu veröffentlichen.