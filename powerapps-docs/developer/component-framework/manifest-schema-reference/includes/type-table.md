---
title: Tabelle eingeben | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 41ea27ac-65b6-45a4-ae03-5f8d02dfc67b
ms.openlocfilehash: 058580b8f39417ccc5e77e7ac96a51bfc95939a1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338756"
---
|Value|Beschreibung|
|--|--|
|`Currency`|In diesem Feld können monetäre Werte zwischen-922.337.203.685.477 und 922.337.203.685.477 sein. Sie können einen Genauigkeits Grad festlegen oder festlegen, dass die Genauigkeit auf eine bestimmte Währung oder eine einzelne von der Organisation verwendete Standardgenauigkeit basieren soll.|
|`DateAndTime.DateAndTime`|Zeigt das Datum und die Uhrzeit an.|
|`DateAndTime.DateOnly`|Zeigt nur das Datum an.|
|`Decimal`|Es können bis zu 10 Dezimalstellen für Werte zwischen-100 Milliarden und-100 Milliarden in diesem Feld verwendet werden. Sie können den Genauigkeits Grad und die maximalen und minimalen Werte angeben.|
|`Enum`|Enumerierter Datentyp.|
|`FP`|Bis zu 5 Dezimalstellen der Genauigkeit können für Werte zwischen-100 Milliarden und-100 Milliarden in diesem Feld verwendet werden. Sie können den Genauigkeits Grad und die maximalen und minimalen Werte angeben. |
|`Multiple`|Dieses Feld kann bis zu 1.048.576 Textzeichen enthalten. Sie können die maximale Länge auf einen niedrigeren Wert festlegen. Wenn Sie dieses Feld zu einem Formular hinzufügen, können Sie die Größe des Felds angeben.|
|`OptionSet`|Dieses Feld stellt eine Reihe von Optionen bereit. Jede Option verfügt über einen Zahlenwert und eine Bezeichnung. Wenn Sie zu einem Formular hinzugefügt wird, wird in diesem Feld ein Steuerelement angezeigt, in dem Benutzer nur eine Option auswählen können. |
|`SingleLine.Email`|Der Text stellt einen mailto-Link bereit, um die e-Mail-Anwendung des Benutzers zu öffnen.|
|`SingleLine.Phone`|In der-Webanwendung werden Felder Click-aktiviert, um Anrufe mithilfe von Skype oder lync zu initiieren, wenn ein Client für entweder auf Ihrem Computer installiert ist. Die Auswahl des telefonieanbieters erfolgt unten auf der Registerkarte "Allgemein" unter "System Einstellungen". für Dynamics 365 für Tablets ist Skype der einzige verfügbare Telefonieanbieter.|
|`SingleLine.Text`|Mit dieser Option wird lediglich Text angezeigt.|
|`SingleLine.TextArea`|Diese Format Option kann verwendet werden, um mehrere Textzeilen anzuzeigen. Mit einer Beschränkung von 4000 Zeichen sind jedoch mehrere Zeilen des Textfelds besser geeignet, wenn eine große Menge an Text erwartet wird.|
|`SingleLine.Ticker`|In den meisten Sprachen wird der Text als Link zum Öffnen der MSN Money-Website aktiviert, um Details zu dem durch das Ticker-Symbol dargestellten Aktienpreis anzuzeigen. Für bestimmte ostasiatische Sprachen öffnet das Fenster die Ergebnisse der Suchergebnisse für das Ticker-Symbol.|
|`SingleLine.URL`|Der Text enthält einen Link zum Öffnen der angegebenen Seite. Jedem Text, der nicht mit einem gültigen Protokoll beginnt, wird "http://" vorangestellt. In diesem Feld sind nur http-, HTTPS-, FTP-, FTPS-, OneNote-und Tel-Protokolle zulässig.|
|`TwoOptions`|Dieses Feld bietet zwei Optionen. Jede Option hat einen Zahlenwert von 0 oder 1, der dem Wert false oder true entspricht. Jede Option verfügt auch über eine Bezeichnung, sodass true-oder false-Werte als "yes" und "No", "Hot" und "Cold", "on" und "Off" oder ein beliebiges paar von Bezeichnungen dargestellt werden können, die Sie anzeigen möchten.|
|`Whole.None`|Mit dieser Option wird einfach eine Zahl angezeigt.|

## <a name="value-elements-that-are-not-supported"></a>Wert Elemente, die nicht unterstützt werden

Die folgenden `of-type` Attributwerte werden zurzeit nicht unterstützt:

|Value|Beschreibung|
|-----|------|
|`Whole.Duration`|Diese Format Option kann verwendet werden, um eine Liste der Optionen für die Dauer anzuzeigen. Die in der Datenbank gespeicherten Daten sind jedoch immer eine Anzahl von Minuten. Das Feld sieht wie eine Dropdown Liste aus und bietet Empfohlene Optionen wie 1 Minute, 15 Minuten, bis zu 3 Tage bis zu 30 Minuten. Personen können diese Optionen auswählen. Personen können jedoch auch nur eine Anzahl von Minuten eingeben, die in diesen Zeitraum aufgelöst werden.|
|`Whole.Timezone`|Mit dieser Option wird eine Auswahlliste von Zeitzonen angezeigt, z. b. (GMT-12:00) Internationale Datumsgrenze West und (GMT-08:00) Pacific Time (USA & Kanada). Jede dieser Zonen wird als Zahl gespeichert. Beispielsweise ist für die Zeitzone (GMT-08:00) Pacific Time (USA & Kanada) der timezonecode 4. Weitere Informationen: [timezonecode-Klasse (SDK-Assembly)](https://docs.microsoft.com/en-us/previous-versions/dynamics-crm4/developers-guide/bb959779(v=msdn.10))|
|`Whole.Language`|Mit dieser Option wird eine Liste der Sprachen angezeigt, die für Ihre Organisation bereitgestellt wurden. Die Werte werden als Dropdown Liste mit Sprachnamen angezeigt, aber die Daten werden mithilfe von LCID-Codes als Zahl gespeichert. Sprachcodes sind vier- oder fünfstellige Gebietsschema-IDs. Gültige Gebietsschema-ID-Werte finden Sie im [Gebietsschema-ID (LCID)-Diagramm)](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms912047(v=winembedded.10)).|
|`Lookup.Simple`|Ermöglicht einen einzelnen Verweis auf eine bestimmte Entität. Alle benutzerdefinierten suchen sind dieser Typ.|
|`Lookup.Customer`|Ermöglicht einen einzelnen Verweis auf ein Konto oder einen Kontaktdaten Satz. Diese Suchvorgänge sind für die Entitäten "Verkaufschance", "Fall", "Angebot", "Bestellung" und "Rechnung" Diese Entitäten verfügen auch über separate Konto-und Kontakt Suchvorgänge, die Sie verwenden können, wenn Ihre Kunden immer ein Typ sind. Oder Sie können beides einschließen, anstatt die Kundensuche zu verwenden.|
|`Lookup.Owner`|Ermöglicht einen einzelnen Verweis auf ein Team oder einen Benutzerdaten Satz. Alle Team-oder benutzereigenen Entitäten haben eines dieser Elemente.|
|`Lookup.PartyList`|Ermöglicht mehrere Verweise auf mehrere Entitäten. Diese Suchvorgänge finden Sie in der e-Mail-Entität **in** den Feldern und **CC** . Sie werden auch in den Telefon-und Termin Entitäten verwendet.|
|`Lookup.Regarding`|Ermöglicht einen einzelnen Verweis auf mehrere Entitäten. Diese Suchvorgänge finden Sie im Feld bezüglich der Aktivitäten, das in Aktivitäten verwendet wird.|
|`MultiSelectOptionSet`|Sie können Formulare (Haupt-, schneller Fassung-und Schnellansicht) und e-Mail-Vorlagen anpassen, indem Sie Mehrfachauswahl Felder hinzufügen. Wenn Sie ein Optionsfeld für die Mehrfachauswahl hinzufügen, können Sie mehrere Werte angeben, die für die Benutzer verfügbar sein werden. Wenn Benutzer das Formular ausfüllen, kann ein, mehrere oder alle Werte ausgewählt werden, die in einer Dropdown Liste angezeigt werden.|
