---
title: Webformular-Eigenschaften für ein Portal konfigurieren | MicrosoftDocs
description: Anweisungen, Webformular-Eigenschaften für ein Portal und zu konfigurieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 31e7dd819ba274a70a4c07bf7a21721a7cfa1f76
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980215"
---
# <a name="define-web-form-properties-for-portals"></a>Definieren von Webformulareigenschaften für Portale

Das Webformular enthält Beziehungen zu Webseiten und einen Startschritt, um die Initialisierung des Formulars im Portal zu steuern. Die Beziehung der Webseite ermöglicht ein dynamisches Abrufen der Formulardefinition für einen bestimmten Seitenknoten innerhalb der Website.  

Die anderen Optionen des Webformulardatensatzes selbst steuern die Einstellungen der obersten Ebene für den Prozess aus mehreren Schritten als Ganzes (beispielsweise, ob Sie eine Statusanzeige anzeigen möchten).

Um vorhandene Webformulare anzuzeigen oder neue Webformulare zu erstellen, öffnen Sie die [Portalverwaltungs-App](configure-portal.md) und gehen Sie zu **Portale** > **Webformulare**.

> [!Note]
> Ein **Webformular** muss einer Webseite für eine bestimmte Website für das Formular zugeordnet sein, um auf der Website angezeigt werden zu können.  

Wenn Sie eine Webseite über die [Portalverwaltungs-App](configure-portal.md) erstellen oder bearbeiten, kann ein **Webformular** im Suchfeld auf dem Formular **Neue Webseite** angegeben werden.

## <a name="web-form-attributes"></a>Webformularattribute

Die folgenden Attribute und Beziehungen bestimmen die Funktionalität des Webformulars.


|                Name                 |                                                                                                                                                                                        Beschreibung                                                                                                                                                                                         |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                Name                 |                                                                                                                                                                          Ein Titel des Formulars als Referenz.                                                                                                                                                                           |
|             Schritt starten              |                                                                                Der erste Schritt des Formulars. Ein Webformulare besteht aus mindestens einem Schritt. Weitere Details zu Schritten finden Sie im Abschnitt "Webformularschritte" weiter unten. Der erste Schritt kann nicht vom Typ „Bedingung” sein.                                                                                |
|       Authentifizierung erforderlich       |                                                                              Wenn aktiviert, wir ein nicht angemeldeter Benutzer auf die Anmeldeseite umgeleitet. Nach der Anmeldung wird der Benutzer wieder zur Seite mit dem Formular umgeleitet.                                                                               |
|      Neue Sitzung beim Laden starten      |              **Ja** legt fest, dass Formular beim Öffnen des Formulars in einem neuen Browser oder einer neuen Registerkarte eine komplett neue Sitzung startet und mit dem ersten Schritt beginnt. Andernfalls bleibt die Sitzung erhalten und der Benutzer kann den Browser oder die Seite schließen und später fortsetzen. Standard: **Nein**.               |
| Es sind mehrere Datensätze pro Benutzer zulässig |                                                                                                  **Ja** gibt an, dass ein Benutzer über die Berechtigung verfügt, mehrere Sendungen zu erstellen. Dies erleichtert dem Formular die Bestimmung von erneuten Besuchen durch einen Benutzer. Standard: **Ja**.                                                                                                   |
|       Statuscode "Bearbeitung abgelaufen"       |                                                                                                                    Der ganzzahlige Statuscode der Zielentität, die mit dem Statuscode kombiniert wird, legt fest, wann ein bestehender Datensatz nicht mehr bearbeitet werden kann.                                                                                                                     |
|     Statusgrund "Bearbeitung abgelaufen"      |                                                                       Der ganzzahlige Statuscode der Zielentität, die mit dem Statusgcode kombiniert wird, legt fest, wann ein bestehender Datensatz nicht mehr bearbeitet werden kann&mdash;z. B., wenn ein Datensatz auf "Abgeschlossen" aktualisiert wird.                                                                       |
|        Meldung "Bearbeitung abgelaufen"         | Die Meldung wird angezeigt, wenn der vorhandene Statusgrund und Statuscode den angegebenen Werten entsprechen. Für jedes installierte und für das Unternehmen aktivierte Sprachpaket steht ein Feld zur Verfügung, in dem Sie die Nachricht in der zugehörigen Sprache eingeben können. Standardmeldung: Sie haben bereits eine Übermittlung abgeschlossen. Vielen Dank! |
|                                     |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="progress-indicator-settings"></a>Einstellungen für die Statusanzeige

| Name                              | Beschreibung                                                                                          |
|-----------------------------------|------------------------------------------------------------------------------------------------------|
| Aktiviert                           | Aktivieren, um die Statusanzeige anzuzeigen. Standard: **Deaktiviert**.                                      |
| Typ                              | Einer der Folgenden: Titel, numerisch (Schritt x von n) und Statusanzeige. Standardwert ist **Titel**                                                                                    |
| Position                          | Eine der Folgenden: „Oben”, „Unten”, „Links”, „Rechts”. Die Position ist relativ zum Formular. Standard: **Oben**                                                   |
| Schrittnummer dem Schritttitel voranstellen | Aktivieren, um der Nummer des Schritts am Anfang des Titels des Schritts hinzuzufügen. Der Standardwert ist deaktiviert. |
||

Beispiel der verschiedenen Statusanzeigetypen:

**Titel**

![Status anhand eines Titels nachverfolgen](../media/track-progress-title.png "Status anhand eines Titels nachverfolgen")  

**Titel mit vorangestellter Schrittnummer**

![Status anhand von Schrittnummer nachverfolgen](../media/track-progress-step-number.png "Status anhand von Schrittnummer nachverfolgen")  

**Numerisch**

![Status anhand eines Nummernzeichens nachverfolgen](../media/track-progress-numeral.png "Status anhand eines Nummernzeichens nachverfolgen")  

**Statusanzeige**

![Status anhand einer Anzeige nachverfolgen](../media/track-progress-bar.png "Status anhand einer Anzeige nachverfolgen")  

## <a name="save-changes-warning"></a>Warnung „Änderungen Speichern” 

|                 Name                  |                                                                                                                                Beschreibung                                                                                                                                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Warnung "Änderungen Speichern" beim Schließen anzeigen |                         Aktivieren, um eine Warnmeldung anzuzeigen, wenn der Benutzer Änderungen an Feld(ern) vorgenommen hat und versucht, die Seite neu zu laden, den Browser schließt, auf die Schaltfläche „Zurück” des Browsers klickt, oder in einem Mehrschrittformular auf die Schaltfläche „Zurück” klickt.                         |
|     Warnmeldung \"Änderungen Speichern\"      | Für jedes installierte und für das Unternehmen aktivierte Sprachpaket steht ein Feld zur Verfügung, in dem Sie die Nachricht in der zugehörigen Sprache eingeben können. Wenn keine Meldung angeben wird, wird die standardmäßige des Browsers verwendet. |
|                                       |                                                                                                                                                                                                                                                                           |

Beispiel:

![Warnung „Änderungen Speichern”](../media/save-changes-warning.png "Warnung "Änderungen Speichern"")  

>[!Note]
> Firefox bietet keine Möglichkeit eine benutzerdefinierten Nachricht anzugeben.

## <a name="geolocation-configuration-for-web-form"></a>Geolocation-Konfiguration für Webformular

Ein verwaltetes Formular kann so konfiguriert werden, dass es ein Kartensteuerelement anzeigt, das entweder einen vorhandenen Standort als Stecknadel auf einer Karte anzeigt oder dem Benutzer die Möglichkeit bereitstellt, einen Standort anzugeben. Siehe [Hinzufügen einer Geolocation](add-geolocation.md).

Das Kartensteuerelement des Formulars erfordert eine zusätzliche Konfiguration, um die IDs der verschiedenen Standortfelder anzugeben, damit diesen Werte zugewiesen bzw. Werte von diesen abgerufen werden können. Der Webformularschritt-Datensatz besitzt einen Abschnitt, der die Feldzuordnungen definiert, denen Sie einen Wert zuweisen müssen. Die Feldnamen sind von dem von Ihnen erstellten Schema abhängig.

![Geolocation-Daten in Webformular](../media/geolocation-managed-form.png "Geolocation-Daten in Webformular")

> [!Note]
> Der Geolocation-Abschnitt wird in der deutschen Sovereign Cloud-Umgebung nicht angezeigt. Wenn ein Benutzer Geolocation mithilfe eines anderen Formulars aktiviert hat, wird es während des Renderings im Portal nicht angezeigt.

### <a name="see-also"></a>Siehe auch

[Ein Portal konfigurieren](configure-portal.md)  
[Entitätsformulare definieren](entity-forms.md)  
[Webformularschritte für Portale](web-form-steps.md)  
[Web-Formulare-Metadaten für Portale](configure-web-form-metadata.md)  
[Webformular-Unterrasterkonfiguration für Portale](configure-web-form-subgrid.md)  
[Notizkonfiguration für Webformular für Portale](../configure-notes.md)  
