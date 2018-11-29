---
title: getFormat (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e5f97552-4a48-4bf9-b460-6105442e2e6b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getformat-client-api-reference"></a>getFormat (Client-API-Referenz) | MicrosoftDocs



Gibt einen Zeichenfolgenwert zurück, die die Formatierungsoptionen des Attributs darstellt. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getFormat()`

## <a name="return-value"></a>Rückgabewert

Diese Methode gibt einen der folgenden **Zeichenfolge** -Werte oder "null" zurück:

- Datum
- datetime
- Dauer
- E-Mail
- language
- keine
- -Smartphone
- Text
- textarea
- tickersymbol
- timezone
- URL

> [!NOTE]
> Diese Formatinformationen stellen im Allgemeinen die Formatoptionen des Anwendungsfelds dar. Formatoptionen für Boolesche Felder werden nicht zur Verfügung gestellt.

Die folgende Tabelle enthält die Formatzeichenfolgenwerte, die für jeden Typ des Attributschematyps und der Formatoption zu erwarten sind.

| Anwendungsfeldtyp | Format-Option | Attributtyp | Formatwert|
|----------------------------|-------------------|--------------------|------------------|
| Datum und Uhrzeit              | Nur Datum         | datetime           | Datum             |
| Datum und Uhrzeit              | Datum und Uhrzeit     | datetime           | datetime         |
| Ganze Zahl               | Dauer          | integer            | Dauer         |
| Einzelne Textzeile        | E-Mail            | Zeichenfolge             | E-Mail            |
| Ganze Zahl               | Sprache          | optionset          | language         |
| Ganze Zahl               | keine              | integer            | keine             |
| Einzelne Textzeile        | Textbereich         | Zeichenfolge             | textarea         |
| Einzelne Textzeile        | Text              | Zeichenfolge             | Text             |
| Einzelne Textzeile        | Tickersymbol     | Zeichenfolge             | tickersymbol     |
| Einzelne Textzeile        | Telefon             | Zeichenfolge             | -Smartphone            |
| Ganze Zahl               | Zeitzone         | optionset          | timezone         |
| Einzelne Textzeile        | URL               | Zeichenfolge             | URL 
