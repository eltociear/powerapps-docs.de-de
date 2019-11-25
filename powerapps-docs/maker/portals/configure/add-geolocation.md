---
title: Hinzufügen von Geolocation zu einem verwalteten Formular in einem Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen von Geolocation zu einem verwalteten Formular.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760430"
---
# <a name="add-geolocation"></a>Geolocation hinzufügen

*Geolocation* ist die Identifikation des realen geografischen Standorts eines Objekts. Geolocation ist eng verbunden mit der Verwendung von Positioniersystemen, legt jedoch mehr Wert auf das Bestimmen eines sinnvollen Standorts (z. B. eine Straßenadresse) als lediglich eine Reihe von geografischen Koordinaten. Das Wort Geolocation kann auch die Breiten- und Längengrade eines spezifischen Standorts bedeuten.

Ein verwaltetes Formular kann so konfiguriert werden, dass es ein Kartensteuerelement anzeigt, das entweder einen vorhandenen Standort als Stecknadel auf einer Karte anzeigt oder dem Benutzer die Möglichkeit bereitstellt, einen Standort anzugeben.

![Standortdaten in einem Formular.](../media/location-data-form.png "Standortdaten in einem Formular")

Wenn das Formular oder das Adresszeilenfeld bearbeitbar ist und dieses Feld leer ist, werden Benutzer beim Laden der Seite gefragt, ob sie ihren Standort freigeben möchte. Wenn die Benutzer ihren Standort freigeben möchte, wird die Karte mit dem aktuell ermittelten Standort aktualisiert. Der Benutzer kann den Standort des Stiftes genauer bestimmen, indem er diesen zieht. Wenn die Benutzer ihren Standort nicht freigeben möchten, können sie den Standort manuell im dafür vorgesehen Feld eingeben und es erfolgt eine Abfrage an den Kartendienst, damit dieser den Standort sucht, Breiten- und Längengrade aktualisiert und die Stecknadel auf der Karte entsprechend neu positioniert.

## <a name="add-geolocation"></a>Geolocation hinzufügen
Um die Geolocation-Funktion zu einem verwalteten Formular hinzuzufügen, müssen die folgenden Aufgaben ausgeführt werden.

### <a name="form-customization"></a>Formularanpassung
Bearbeiten Sie das Entitätsformular mithilfe des Formulardesigners und nehmen Sie die folgenden Änderungen vor:

1. Erstellen Sie einen neuen Abschnitt und geben Sie eine geeignete Bezeichnung an, zum Beispiel **Karte**. Dieser Abschnitt enthält die Karte.
2. Legen Sie als Namen für den Abschnitt **Abschnitt\_Karte** fest oder einen Namen, der auf _Abschnitt\_Karte_ endet, z.B. **contoso\_Abschnitt\_Karte**. Dieser Name ist wichtig, da das Formularmodul einen Abschnitt mit diesem Namen sucht, um zu ermitteln, wann eine Karte gerendert werden soll. 
3. Fügen Sie ein neues oder vorhandenes Feld mit der formatierten Adresse hinzu, und fügen Sie dieses zum Abschnitt **Karte** hinzu, der im vorherigen Schritt erstellt wurde.
4. Erstellen Sie einen neuen Abschnitt und geben Sie eine geeignete Bezeichnung an, zum Beispiel **Location**. Dieser Abschnitt enthält die Adressfelder für den ausgewählten Standort.
5. Fügen Sie die erforderlichen Adressfelder zum Abschnitt **Standort** hinzu, der im vorherigen Schritt erstellt wurde: 
    - Adresszeile
    - Ort
    - Verwaltungsbezirk
    - Bundesland/Kanton
    - Land/Region
    - Postleitzahl
    - Breite
    - Länge

Das erstellte Formular sollte in etwa wie folgt aussehen. Sie können verschiedene Anzeigenamen für diese Felder wählen. Sie können diese Abschnitte auch so gestalten, wie Sie wünschen.

![Benutzerdefiniertes Geolokalisierungsformular.](../media/custom-geolocation-form.png "Benutzerdefiniertes Geolokalisierungsformular")

### <a name="site-settings"></a>Website-Einstellungen
Für Geolocation mit Kartenfunktion auf verwalteten Formularen sind Konfigurationseinstellungen erforderlich, um Anfragen mit dem REST-Endpunkt des Kartendiensts abzuschließen. Die folgenden Websiteeinstellungen werden verwendet, um den Standortdienst zu konfigurieren.

|Name|Wert|
|---|---|
|Bingmaps/Anmeldeinformationen|Eindeutiger Schlüssel zum Authentifizieren von Anfragen bei der Bing Maps-API. Besuchen Sie [www.bingmapsportal.com](https://www.bingmapsportal.com), um einen Bing Maps-Account zu erstellen und einen Schlüssel abzurufen. Erforderlich.|
|Bingmaps/restURL|URL zur Bing Maps-REST-API. (Optional). Wenn ein Wert nicht definiert ist, wird der Standardwert https://dev.virtualearth.net/REST/v1/Locations verwendet.|
| |

### <a name="field-configurations"></a>Feldkonfigurationen
Das Kartensteuerelement erfordert eine zusätzliche Konfiguration, um die IDs der verschiedenen Standortfelder anzugeben, damit diesen Werte zugewiesen bzw. Werte von diesen abgerufen werden können. Die Konfiguration hängt vom Typ des verwalteten Formulars ab.

- Informationen zum Entitätsformular finden Sie unter [Geolocation-Konfiguration für Entitätsformulare](entity-forms.md#geolocation-configuration-for-entity-forms).

- Informationen zum Webformular finden Sie unter [Geolocation-Konfiguration für Webformulare](web-form-properties.md#geolocation-configuration-for-web-form).
