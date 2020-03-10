---
title: Ändern der Bildschirmgröße und -ausrichtung einer Canvas-App | Microsoft-Dokumentation
description: Schritt-für-Schritt-Anleitungen zum Ändern von Einstellungen, z. b. Bildschirmgröße und Ausrichtung einer Canvas-app in Power apps
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b6ec2006266a15b7552d1a83b2d7d67c14560470
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404331"
ms.PowerAppsDecimalTransform: true
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-power-apps"></a>Ändern der Bildschirmgröße und der Ausrichtung einer Canvas-app in Power apps
Passen Sie eine Canvas-App an, indem Sie Bildschirmgröße und -ausrichtung ändern.

## <a name="prerequisites"></a>Erforderliche Komponenten

Erstellen Sie eine APP, oder öffnen Sie eine APP zum Bearbeiten, und wählen Sie dann im Menü **Datei** die Option **App-Einstellungen** aus.

## <a name="change-screen-size-and-orientation"></a>Bildschirmgröße und -ausrichtung ändern
1. Wählen Sie unter **App settings**  (App-Einstellungen) die Option **Screen size + orientation**  (Bildschirmgröße und -ausrichtung) aus.

    ![Option zum Ändern der Bildschirmgröße und -ausrichtung einer App](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. **Wählen Sie** in der Liste **Ausrichtung** die Option Hochformat oder **quer**Format aus.

1. (Nur Tablet-Apps) Führen Sie unter **Seitenverhältnis**einen der folgenden Schritte aus:

    - Wählen Sie das Verhältnis aus, das dem Zielgerät für diese APP entspricht.
    - Wählen Sie **Benutzer** definiert aus, um Ihre eigene Größe festzulegen, und geben Sie dann eine Breite zwischen 50 und 3840 und eine Höhe zwischen 50 und 2160 an.

    ![Ändern des Seitenverhältnisses einer Tablet-App](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. Geben **Sie unter Skalieren für anpassen**entweder ein oder **aus** **an** .

    Diese Einstellung ist standardmäßig aktiviert, sodass die Größe der APP-Bildschirme an den verfügbaren Speicherplatz auf dem Gerät angepasst wird. Wenn diese Einstellung auf ON festgelegt ist, stimmt die **Width** -Eigenschaft der APP mit der **Design Width**-Eigenschaft überein, und die **Höhe** der APP entspricht Ihrer **Design Height**.

    Wenn Sie diese Einstellung deaktivieren, wird die APP an das Seitenverhältnis des Geräts angepasst, auf dem es ausgeführt wird, und es wird der gesamte verfügbare Speicherplatz belegt. Die APP wird nicht skaliert, und daher können Bildschirme Weitere Informationen anzeigen.

    Wenn diese Einstellung deaktiviert ist, wird das **Seitenverhältnis für Sperren** automatisch deaktiviert und deaktiviert. Außerdem ist die **Width** -Eigenschaft aller Bildschirme auf `Max(App.Width; App.DesignWidth)`festgelegt, und Ihre **height** -Eigenschaft wird auf `Max(App.Height; App.DesignHeight)` festgelegt, sodass die Dimensionen des Fensters, in dem die app ausgeführt wird, nachverfolgt werden. Mit dieser Änderung können Sie Apps erstellen, die auf verschiedene Geräte und Fenster Dimensionen reagieren. Weitere Informationen: [Erstellen eines reaktionsfähigen Layouts](create-responsive-layout.md)

1. Geben Sie unter **Seitenverhältnis sperren** entweder **Ein** oder **Aus** an.

    Wenn diese Einstellung auf ON festgelegt ist, behält die APP die Bildschirm Ausrichtung und das Seitenverhältnis bei, die Sie in den Schritten 2 und 3, unabhängig vom Gerät, angegeben haben. Beispielsweise behält eine Phone-APP, die in einem Webbrowser ausgeführt wird, das Verhältnis für ein Telefon bei und zeigt eine dunkle Leiste auf jeder Seite an, anstatt das Fenster zu füllen.

    Wenn diese Einstellung auf OFF festgelegt ist, wird die APP an das Seitenverhältnis des Geräts angepasst, auf dem es ausgeführt wird (und die Benutzeroberfläche bei Bedarf verzerrt).

1. Geben Sie unter **Bildschirmausrichtung sperren** entweder **Ein** oder **Aus** an.

    Wenn Sie die Ausrichtung der App Sperren, behält die APP die von Ihnen angegebene Ausrichtung bei. Wenn die APP auf einem Gerät ausgeführt wird, für das sich der Bildschirm in einer anderen Ausrichtung befindet, wird die APP falsch angezeigt, und es werden möglicherweise unerwünschte Ergebnisse angezeigt. Wenn Sie die Ausrichtung der APP entsperren, wird Sie an die Bildschirm Ausrichtung des Geräts angepasst, auf dem es ausgeführt wird.

    Sie können auch die Ausrichtung der App ändern, indem Sie die Option App-Einbettung der Benutzerumgebung in **erweiterten Einstellungen** **aktivieren aktivieren** . Diese Funktion oben links richtet die APP an, wenn Sie eingebettet ist, und ändert die Hintergrundfarbe des Hostens in weiß.

1. Klicken Sie auf **Anwenden**, um Ihre Änderungen zu speichern.

## <a name="next-step"></a>Nächster Schritt
Wählen Sie im Menü **Datei** die Option **Speichern** aus, um Ihre App mit den neuen Einstellungen erneut zu veröffentlichen.