---
title: getValue (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: acc78a1e-212a-4eef-88c5-8272f9ba3009
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getvalue-client-api-reference"></a>getValue (Client-API-Referenz)

Ruft den Datenwert für ein Attribut ab.

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getValue()`

## <a name="return-value"></a>Rückgabewert

**Typ**: Abhängig vom Typ des Attributs. 

| Attributtyp | Rückgabetyp| 
|----|-----|
| Boolescher Wert | [Boolesch](https://msdn.microsoft.com/library/t7bkhaz6.aspx) |
| datetime| [Datum](https://msdn.microsoft.com/library/cd9w2te4.aspx)<br/> Um die Zeichenfolgenversion eines Datums unter Verwendung des bevorzugten PowerApps-Gebietsschemas des Benutzers abzurufen, verwenden Sie die [format](https://msdn.microsoft.com/library/bb384009.aspx)- und [localeFormat](https://msdn.microsoft.com/library/bb383816.aspx)-Methoden. Andere Methoden formatieren Datumsangaben mithilfe des Betriebssystemgebietsschemas anstelle des bevorzugten PowerApps-Gebietsschemas des Benutzers. | 
| Dezimalzahl| [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)| 
| Doppelt | [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)| 
| integer | [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| Suche | [Array](https://msdn.microsoft.com/library/k4h76zbx.aspx) <br/>Ein Array von Suchobjekten.<br/><br/>HINWEIS: Bestimmte Suchen ermöglichen das Zuordnen mehrerer Datensätze in einer Suche, z. B. das „An:“-Feld für einen E-Mail-Entitätsdatensatz. Daher verwenden alle Suchdatenwerte ein Suchobjekt-Array, auch wenn das Suchattribut nicht mehr als einen hinzugefügten Datensatzverweis unterstützt. <br/><br/>Jede Suche bietet folgende Eigenschaften:<br/>- *entityType*: Zeichenfolge. Der Name der Entität, der in der Suche angezeigt wird.<br/>- *id*: Zeichenfolge: die Zeichenfolgendarstellung des GUID-Werts für den Datensatz, der in der Suche angezeigt wird.<br/>- *name*Zeichenfolge: Der Text, der den in der Suche anzuzeigenden Datensatz darstellt.|
| memo  | [Zeichenfolge](https://msdn.microsoft.com/library/ecczf11c.aspx)  |
| Zahlung| [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| optionset | [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| Zeichenfolge | [Zeichenfolge](https://msdn.microsoft.com/library/ecczf11c.aspx) |


### <a name="related-topic"></a>Verwandtes Thema
[setValue (Client-API-Referenz)](setValue.md)
