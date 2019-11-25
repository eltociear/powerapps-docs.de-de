---
title: Konfigurieren von Bing Maps in einer modellgesteuerten App mit PowerApps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: f9729664-561c-4758-86ce-7216d68075d9
caps.latest.revision: 63
ms.author: matp
author: Mattp123
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ff7f5c01e913da60409bb60c637b37ebd4bfa096
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756474"
---
# <a name="configure-a-map-on-a-form"></a>Konfigurieren einer Karte in einem Formular
Standardmäßig wird das Bing Maps-Steuerelement auf dem Hauptformular für das Konto und die Kontaktentitäten konfiguriert, womit die Möglichkeit gegeben ist, eine Karte auf Entitätsdatensätzen anzuzeigen. Obwohl nicht standardmäßig so konfiguriert, kann das Bing Maps-Steuerelement zur Systembenutzerentität hinzugefügt werden. Das Bing Maps-Steuerelement kann auch mit einigen Entitäten verwendet werden, einschließlich modellgesteuerter Apps in Dynamics 365, wie Dynamics 365 Sales und Dynamics 365 Customer Service. Dazu gehören beispielsweise der Lead, das Angebot, der Auftrag, die Rechnung und die Mitbewerber-Entitäten. Das Bing Maps-Seuerelement kann nicht für benutzerdefinierte Entitäten verwendet werden.  

Wenn diese aktiviert, zeigt die Karte den Standort an, der in den zusammengesetzten Felder der Adresse für den betreffenden Datensatz angegeben ist. 

> [!div class="mx-imgBorder"] 
> ![Bing Maps-Steuerelement in einer App](media/bing-map-example.png "Bing Maps-Steuerelement in einer App")

> [!IMPORTANT]
> Um Karten zu verwenden muss die Systemeinstellung Bing Maps auf Formularen anzeigen aktiviert werden. Weitere Informationen: [Karten für Ihre Umgebung aktivieren](#enable-maps-for-your-environment)

Sie können den Kartenbereich aus dem Formulareditor mit der Schaltfläche **Bing Maps** auf der Registerkarte **Einfügen** des klassischen Formulareditors entfernen oder wieder einsetzen.

## <a name="enable-maps-for-your-environment"></a>Aktivieren Sie Karten für Ihre Umgebung
1. Öffnen Sie eine modellgesteuerte App und wählen Sie **Einstellungen** > **Erweiterte Einstellungen** aus. 
2. Wählen Sie **Einstellungen** > **Verwaltung** > **Systemeinstellungen** aus. 
3. Wählen Sie auf der Registerkarte **Allgemein** die Option **Bing Maps auf Formularen anzeigen** und anschließend **OK** aus. 
 
    ![Karten auf Formularen aktivieren](media/enable-maps.png)

## <a name="configure-a-map"></a>Konfigurieren einer Karte 
1. Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Gehen Sie zu **Daten** > ,**Entitäten** und wählen Sie dann die Entität aus, für die Sie eine Karte auf dem Hauptformular konfigurieren möchten. 
3. Wählen Sie die Registerkarte **Formulare**, und dann das Hauptformular aus. Wählen Sie dann auf der Befehlsleiste **In klassischen Modus wechseln** aus. 
4. Doppelklicken Sie im klassischen Formular-Designer auf das **Kartenansicht**-Steuerelement, um die Eigenschaften anzuzeigen und zu bearbeiten. Weitere Informationen: [Anzeigen und Bearbeiten von Karteneigenschaften](#view-and-edit-map-properties)

    ![Kartenansichtssteuerung](media/map-view-control.png)

Um das Kartensteuerelement aus dem Formular zu entfernen, wählen Sie **Kartenansicht**-Steuerung und drücken Sie dann die ENTF-Taste.

## <a name="view-and-edit-map-properties"></a>Karteneigenschaften anzeigen und bearbeiten

|      Registerkarte       |                        Eigenschaft                         |                                                                                                  Beschreibung                                                                                                   |
|----------------|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Allgemein**   |                        **Beschriftung**                        |                                                                              **Erforderlich**: Eine für die Bing Maps anzuzeigende Beschriftung.                                                                               |
|                |              **Beschriftung im Formular anzeigen**              |                                                                                     Ob die Beschriftung angezeigt werden soll.                                                                                     |
|                | **Wählen Sie eine Adresse, die mit dem Bing Maps-Steuerelement verwendet werden soll.** |                                                                        Wählen Sie aus, welche Adresse verwendet werden soll, um Daten für die Map zur Verfügung zu stellen.                                                                        |
|                |                 **Standardmäßig sichtbar**                  | Die Anzeige der Bing Maps ist optional und kann durch Geschäftsregeln oder Skripts gesteuert werden. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md) |
| **Formatierung** |  **Wählen Sie die Anzahl der Spalten, die vom Steuerelement belegt werden**  |                              Wenn der Abschnitt, der die Bing Maps enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält.                              |
|                |   **Wählen Sie die Anzahl der Zeilen für das Steuerelement aus**    |                                                                  Sie können die Höhe der Bing Maps steuern, indem Sie eine Anzahl von Zeilen angeben.                                                                   |
|                |     **Automatisch erweitern, um verfügbaren Bereich auszufüllen**     |                                                                        Sie können zulassen, dass die Höhe der Bing Maps sich bis zum verfügbaren Raum ausdehnt.                                                                        |

### <a name="see-also"></a>Siehe auch
[Erstellen und entwerfen von Modell-angetriebenen App-Formularen](create-design-forms.md) 
