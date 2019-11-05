---
title: Konfigurieren von Web Form-Eigenschaften für ein Portal | MicrosoftDocs
description: Anweisungen zum Konfigurieren von Web Form-Eigenschaften für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 904734c2143eae8e687be339b1bc5b30b47cff46
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551207"
---
# <a name="define-web-form-properties-for-portals"></a>Definieren von Web Form-Eigenschaften für Portale

Das Webformular enthält Beziehungen zu Webseiten und einen Start Schritt, um die Initialisierung des Formulars im Portal zu steuern. Die Beziehung zur Webseite ermöglicht das dynamische Abrufen der Formular Definition für einen bestimmten Seiten Knoten innerhalb der Website.  

Die anderen Optionen im Webformular zeichnen sich selbst durch die Einstellungen der obersten Ebene für den Prozess mit mehreren Schritten als Ganzes auf, z. b. ob Sie eine Statusanzeige anzeigen möchten.

Um vorhandene Web Forms anzuzeigen oder neue Web Forms zu erstellen, öffnen Sie die [Portal Verwaltungs-App](configure-portal.md) , und navigieren Sie zu **Portale** > **Web Forms**.

> [!Note]
> Ein **Webformular** muss einer Webseite für eine bestimmte Website zugeordnet sein, damit das Formular innerhalb der Site angezeigt werden kann.  

Beim Erstellen oder Bearbeiten einer Webseite aus der [Portal Verwaltungs-App](configure-portal.md)kann ein **Webformular** im Suchfeld angegeben werden, das im Formular für die **neue Webseite** bereitgestellt wird.

## <a name="web-form-attributes"></a>Web Form-Attribute

Die folgenden Attribute und Beziehungen bestimmen die Funktionalität des Webformulars.


|                Name                 |                                                                                                                                                                                        Beschreibung                                                                                                                                                                                         |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                Name                 |                                                                                                                                                                          Ein Titel des Formulars, das für den Verweis verwendet wird.                                                                                                                                                                           |
|             Start Schritt              |                                                                                Der erste Schritt im Formular. Ein Webformular besteht aus einem oder mehreren Schritten. Weitere Informationen zu diesen Schritten finden Sie im Abschnitt "Web Form Step" (weiter unten). Der erste Schritt kann nicht den Typ "Condition" aufweisen.                                                                                |
|       Authentifizierung erforderlich       |                                                                              Wenn dieses Kontrollkästchen aktiviert ist und ein Benutzer, der nicht angemeldet ist, die Seite besucht, die das Formular enthält, wird er zur Anmeldeseite umgeleitet. Nach erfolgreicher Anmeldung wird der Benutzer zurück an die Seite umgeleitet, die das Formular enthält.                                                                               |
|      Neue Sitzung beim Laden starten      |              Wenn der Benutzer das Formular in einem neuen Browser oder einer neuen Registerkarte öffnet oder den Browser oder die Seite schließt und **zurückgibt,** startet das Formular eine vollständig neue Sitzung und beginnt dann mit dem ersten Schritt. Andernfalls wird die Sitzung persistent gespeichert, und der Benutzer kann den Browser oder die Seite schließen und später genau dort fortsetzen, wo Sie aufgehört haben. Standardwert: **Nein**.               |
| Mehrere Datensätze pro Benutzer zulässig |                                                                                                  Durch Auswahl von **Ja** wird angegeben, dass ein Benutzer mehr als eine Übermittlung erstellen darf. Dies unterstützt das Formular, um zu bestimmen, was zu tun ist, wenn ein Benutzer ein Formular erneut besucht. Standardwert: **Ja**.                                                                                                   |
|       Abgelaufenen Zustands Code bearbeiten       |                                                                                                                    Der ganzzahlige Wert des Zustands Codes der Ziel Entität, der in Kombination mit dem Status Grund angibt, wann ein vorhandener Datensatz nicht mehr bearbeitet werden kann.                                                                                                                     |
|     Grund für den abgelaufenen Status bearbeiten      |                                                                       Der ganzzahlige Wert des Statuscodes der Ziel Entität, der in Kombination mit dem Statuscode angibt, dass der Datensatz nicht mehr bearbeitet werden soll, wenn ein vorhandener Datensatz diese Werte besitzt&mdash;z. b., wenn ein Datensatz als "Fertig" aktualisiert wird.                                                                       |
|        Abgelaufene Nachricht bearbeiten         | Die Meldung, die angezeigt wird, wenn der Statuscode und der Status des vorhandenen Datensatzes den angegebenen Werten entsprechen. Für jedes Sprachpaket, das für die Organisation installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann. Standardmeldung; Sie haben bereits eine Übermittlung abgeschlossen. Danke! |
|                                     |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="progress-indicator-settings"></a>Status Indikator Einstellungen

| Name                              | Beschreibung                                                                                          |
|-----------------------------------|------------------------------------------------------------------------------------------------------|
| Wodurch                           | Aktivieren Sie diese Option, um die Statusanzeige anzuzeigen. Standard: **deaktiviert**.                                      |
| Typ                              | Einer der folgenden Werte: Title, numerisch (Schritt x von n) und Statusanzeige. Standard: **Titel**                                                                                    |
| Position                          | Eines der folgenden: oben, unten, Links, rechts. Die Position ist relativ zum Formular. Standard: **oben**.                                                   |
| Schritt-für-Schritt-Titel voransetzen | Aktivieren Sie diese Option, um die Nummer des Schritts am Anfang des Titels des Schritts hinzuzufügen. Der Standardwert ist deaktiviert. |
||

Beispiel für die verschiedenen Status Indikator Typen:

**Title**

![Nachverfolgen des Fortschritts mithilfe eines Titels](../media/track-progress-title.png "Nachverfolgen des Fortschritts mithilfe eines Titels")  

**Titel mit vorangemittelten Schritt Nummer**

![Nachverfolgen des Fortschritts mithilfe einer Schritt Nummer](../media/track-progress-step-number.png "Nachverfolgen des Fortschritts mithilfe einer Schritt Nummer")  

**Isch**

![Nachverfolgen des Fortschritts mithilfe einer Ziffer](../media/track-progress-numeral.png "Nachverfolgen des Fortschritts mithilfe einer Ziffer")  

**Statusanzeige**

![Verfolgen des Fortschritts mithilfe eines Balkens](../media/track-progress-bar.png "Nachverfolgen des Fortschritts mithilfe eines Balkens")  

## <a name="save-changes-warning"></a>Warnung "Änderungen speichern" 

|                 Name                  |                                                                                                                                Beschreibung                                                                                                                                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Warnung zum Speichern von Änderungen beim Schließen anzeigen |                         Wählen Sie diese Option aus, um eine Warnmeldung anzuzeigen, wenn der Benutzer Änderungen an den Feldern vorgenommen hat und versucht, die Seite erneut zu laden, den Browser zu schließen, die Schaltfläche "zurück" des Browsers auszuwählen oder die Schaltfläche "zurück" in einem mehrstufigen Formular auszuwählen.                         |
|     Warnmeldung "Änderungen speichern"      | Für jedes Sprachpaket, das für die Organisation installiert und aktiviert ist, steht ein Feld zur Verfügung, in dem die Nachricht in der zugeordneten Sprache eingegeben werden kann. Wenn keine Meldung angegeben ist, wird der Browser Standard verwendet. |
|                                       |                                                                                                                                                                                                                                                                           |

Beispiel:

![Warnung "Änderungen speichern"](../media/save-changes-warning.png "Warnung "Änderungen speichern"")  

>[!Note]
> Firefox bietet keine Möglichkeit, eine benutzerdefinierte Meldung anzugeben.

## <a name="geolocation-configuration-for-web-form"></a>Geolozierungkonfiguration für Web Form

Ein verwaltetes Formular kann so konfiguriert werden, dass ein Karten Steuerelement angezeigt wird, um entweder einen vorhandenen Speicherort als PIN auf einer Karte anzuzeigen oder den Benutzer zum Angeben eines Speicher Orts zu sorgen. Siehe [Hinzufügen von Geolokation](add-geolocation.md).

Das Karten Steuerelement des Formulars erfordert eine zusätzliche Konfiguration, um ihm mitzuteilen, was die IDs der verschiedenen Speicherort Felder sind, um Ihnen Werte zuzuweisen oder um Werte abzurufen. Der Datensatz für den Webformular Schritt enthält einen Abschnitt, in dem diese Feld Zuordnungen definiert sind, für die Sie Werte zuweisen müssen. Die Feldnamen variieren je nach Schema, das Sie erstellt haben.

![Geolozierungdaten in Web Form](../media/geolocation-managed-form.png "Geolozierungdaten in Web Form")

> [!Note]
> Der Abschnitt "Geolokation" ist in der deutschen unabhängigen cloudumgebung nicht sichtbar. Wenn ein Benutzer die geolozierung mit einer anderen Form aktiviert hat, wird er während des Renderings im Portal nicht angezeigt.

### <a name="see-also"></a>Siehe auch

[Konfigurieren eines Portals](configure-portal.md)  
[Definieren von Entitäts Formularen](entity-forms.md)  
[Webformular Schritte für Portale](web-form-steps.md)  
[Web Forms von Metadaten für Portale](configure-web-form-metadata.md)  
[Webformular-unter Raster Konfiguration für Portale](configure-web-form-subgrid.md)  
[Hinweise zur Konfiguration für Web Forms für Portale](../configure-notes.md)  
