---
title: Hinzufügen von Geolokation zu einem verwalteten Formular in einem Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen von Geolokation zu einem verwalteten Formular.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a3c583658a5593d8e6c5f6c139a5c967e9581626
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553553"
---
# <a name="add-geolocation"></a>Geolozierung hinzufügen

*Geolokation* ist die Identifizierung des realen geografischen Standorts eines Objekts. Die geolozierung ist eng mit der Verwendung von Positionierungssystemen in Zusammenhang stehen, hat jedoch einen größeren Schwerpunkt auf die Bestimmung eines sinnvollen Orts (z. b. einer Straße) anstatt auf einen Satz geografischer Koordinaten. Das Wort "Geolokation" kann auch die breiten-und Längenkoordinaten eines bestimmten Standorts bedeuten.

Ein verwaltetes Formular kann so konfiguriert werden, dass ein Karten Steuerelement angezeigt wird, um einen vorhandenen Speicherort als PIN auf einer Karte anzuzeigen oder um dem Benutzer die Möglichkeit zu geben, einen Speicherort anzugeben.

![Speicherort Daten in einem Formular.](../media/location-data-form.png "Speicherort Daten in einem Formular")

Wenn das Formular-oder Adresszeilen Feld bearbeitbar ist und dieses Feld leer ist, wird der Benutzer beim Laden der Seite aufgefordert, den Speicherort für die Freigabe anzugeben. Wenn Sie ihren Speicherort freigeben möchten, wird die Zuordnung mit Ihrem aktuell erkannten Speicherort aktualisiert. Der Benutzer kann den Speicherort der PIN verfeinern, indem er ihn zieht. Wenn der Benutzer seinen Speicherort nicht freigeben möchte, kann er den Speicherort in den bereitgestellten Feldern manuell angeben, und der Zuordnungs Dienst wird abgefragt, um den Speicherort zu suchen, den breiten-und Längengrad zu aktualisieren und die PIN auf der Karte entsprechend neu zu positionieren.

## <a name="add-geolocation"></a>Geolozierung hinzufügen
Zum Hinzufügen von geolozierungsfunktionen zu einem verwalteten Formular müssen die folgenden Aufgaben abgeschlossen sein.

### <a name="form-customization"></a>Formular Anpassung
Bearbeiten Sie das Entitäts Formular mithilfe des Formular-Designers, und nehmen Sie die folgenden Änderungen vor:

1. Erstellen Sie einen neuen Abschnitt, und geben Sie eine entsprechende Bezeichnung an, z. b. **map**. Dieser Abschnitt enthält die Karte.
2. Legen Sie den Namen des Abschnitts auf **section\_Map** oder einen Namen fest, der mit _section\_Map_endet, z. b. **\_Abschnitt\_Map**. Dieser Name ist wichtig, da die Formular-Engine nach einem Abschnitt mit diesem Namen sucht, um zu bestimmen, wann eine Karte dargestellt werden soll. 
3. Fügen Sie ein neues oder vorhandenes Feld hinzu, in dem die formatierte Adresse gespeichert wird, und fügen Sie es dem im vorherigen Schritt erstellten **Karten** Abschnitt hinzu.
4. Erstellen Sie einen neuen Abschnitt, und geben Sie eine entsprechende Bezeichnung an, z. b. **Location**. Dieser Abschnitt enthält die Adressfelder für den ausgewählten Speicherort.
5. Fügen Sie die erforderlichen Adressfelder zum **Speicherort** Abschnitt hinzu, den Sie im vorherigen Schritt erstellt haben: 
    - Adresszeile
    - Stadt
    - SSI
    - Bundesland/Kanton
    - Land/Region
    - Zip/Postleitzahl
    - Breiten
    - Längengrad

Das resultierende Formular sollte in etwa wie folgt aussehen. Sie können unterschiedliche anzeigen Amen für diese Felder auswählen. Sie können diese Abschnitte auch beliebig festlegen.

![Benutzerdefiniertes geolozierungformular.](../media/custom-geolocation-form.png "Benutzerdefiniertes geolozierungformular")

### <a name="site-settings"></a>Website Einstellungen
Die geolozierung mit Karten Funktionalität in verwalteten Formularen erfordert Konfigurationseinstellungen, um Anforderungen mit dem Rest-Endpunkt des Zuordnungs Dienstanbieter abzuschließen. Die folgenden Standorteinstellungen werden verwendet, um den Standort Dienst zu konfigurieren.

|Name|Value|
|---|---|
|Bingmaps/Anmelde Informationen|Eindeutiger Schlüssel zum Authentifizieren von Anforderungen an die-API von die-API. Besuchen Sie [www.bingmapsportal.com](https://www.bingmapsportal.com) , um ein Konto zu erstellen und einen Schlüssel zu erhalten. Erforderlich.|
|Bingmaps/resturl|URL zur Rest-API von Rest Maps. Optional. Wenn kein Wert angegeben wird, wird der Standard https://dev.virtualearth.net/REST/v1/Locations verwendet.|
| |

### <a name="field-configurations"></a>Feld Konfigurationen
Das Karten Steuerelement erfordert zusätzliche Konfiguration, um ihm mitzuteilen, was die IDs der verschiedenen Speicherort Felder sind, sodass es Ihnen Werte zuweisen oder Werte daraus abrufen kann. Die Konfiguration hängt vom Typ des verwalteten Formulars ab.

- Informationen zu Entitäts Formularen finden Sie unter [geolozierungkonfiguration für Entitäts Formulare](entity-forms.md#geolocation-configuration-for-entity-forms).

- Informationen zu Web Forms finden Sie unter [geolozierungkonfiguration für Web Forms](web-form-properties.md#geolocation-configuration-for-web-form).
