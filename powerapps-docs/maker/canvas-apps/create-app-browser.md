---
title: Erstellen und Bearbeiten von Apps in einem Webbrowser | Microsoft-Dokumentation
description: Erstellen oder bearbeiten Sie Apps mithilfe von PowerApps Studio für Web in einem Browser.
services: powerapps
suite: powerapps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/08/2018
ms.author: sharik
ms.openlocfilehash: 5d120cd0a754b2aa6ad45c5cc81435810e382c61
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="create-or-edit-apps-in-powerapps-studio-for-web"></a>Erstellen und Bearbeiten von Apps in PowerApps Studio für Web
Erstellen und Bearbeiten Sie Apps in PowerApps Studio für Web, das unter Windows oder anderen Plattformen in einem Browserfenster geöffnet wird.

## <a name="prerequisites"></a>Voraussetzungen
* [Registrieren Sie sich](../signup-for-powerapps.md) bei PowerApps.
* Stellen Sie sicher, dass Sie einen [unterstützten Browser](limits-and-config.md#supported-browsers-for-powerapps-studio-for-web) verwenden.

## <a name="open-powerapps-studio-for-web"></a>Öffnen von PowerApps Studio für Web
1. Melden Sie sich bei [powerapps.com](http://go.microsoft.com/fwlink/p/?LinkId=708209) an.
2. Klicken oder tippen Sie in der unteren linken Ecke auf **New App**.

    ![„Neue App“ in der linken Navigationsleiste](./media/create-app-browser/left-nav.png)

PowerApps Studio für Web wird in einer neuen Registerkarte in Ihrem Browser geöffnet, in dem Sie Apps auf die gleiche Weise wie in PowerApps Studio für Windows erstellen und bearbeiten können.

## <a name="known-limitations"></a>Bekannte Einschränkungen
1. **Erstellen einer Verbindung**

    Zum [Erstellen einer Verbindung](add-manage-connections.md) mit einer Datenquelle, die eine Service-Authentifizierung erfordert, verwenden Sie [powerapps.com](https://web.powerapps.com) und [fügen Sie die Verbindung](add-data-connection.md) zu einer App in PowerApps Studio für Web hinzu.
2. **Lokales Bearbeiten und Speichern einer App**

    Verwenden Sie für optimale Ergebnisse PowerApps Studio für Windows, um Apps lokal zu bearbeiten und zu speichern. In einem Webbrowser können Sie keine Änderungen an einer lokalen App speichern, oder Sie müssen eine neue Datei speichern, anstatt die Datei, die Sie geöffnet haben, zu ersetzen.
3. **Verwenden von Signalfunktionen**

    Die Funktionen **[Acceleration und Compass](functions/signals.md)** geben genaue Werte in einer veröffentlichten App zurück, aber diese Funktionen geben 0-Werte zurück, da Sie eine App in einem Browser erstellen oder ändern.
4. **Exportieren und Importieren von Daten**

    Sie können das [Exportieren und Importieren von Daten](controls/control-export-import.md) in einer veröffentlichten App vornehmen, jedoch nicht während Sie eine App in einem Browser erstellen oder ändern.
5. **Sitzungsübergreifendes Kopieren eines Steuerelements**

    Sie können Steuerelemente nicht aus einer Sitzung von PowerApps Studio für Web in eine andere Sitzung von PowerApps Studio für Web kopieren.

## <a name="next-steps"></a>Nächste Schritte
* Generieren Sie automatisch eine App aus Ihren Daten, z.B. in [Excel](get-started-create-from-data.md) oder [SharePoint](app-from-sharepoint.md).
* Erfahren Sie, wie Sie [ein Steuerelement hinzufügen und seine Eigenschaften festlegen](add-configure-controls.md), die bestimmen, wie Ihre App angezeigt wird und sich verhält.
* Lassen Sie Ihrer Kreativität freien Lauf, indem Sie [eine Anwendung von Grund auf Neu erstellen](get-started-create-from-blank.md).