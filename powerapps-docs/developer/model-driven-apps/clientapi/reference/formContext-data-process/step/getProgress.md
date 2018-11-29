---
title: getProgEvents (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 56502c8b-af23-40d1-ad97-e780bb757d6d
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getprogress-client-api-reference"></a>getProgress (Client-API-Referenz)



[!INCLUDE[./includes/getProgress-description.md](./includes/getProgress-description.md)]

## <a name="syntax"></a>Syntax

`var stepProgress = stepObj.getProgress();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Zahl. 

**Beschreibung**: Gibt einen der folgenden Werte zurück:

|Value |Beschreibung|
|--|--|
|0|Keiner|
|1|Wird verarbeitet|
|2|Abgeschlossen|
|3|Fehler|
|4|Ungültig|

## <a name="remarks"></a>Anmerkungen

Diese Methode wird nur für die Funktionsstufen, nicht für die Eingabekriterien unterstützt. Funktionsstufen sind Schaltflächen bei den Geschäftsprozessphasen, auf die Benutzer klicken können, um einen bedarfsgesteuerten Workflow oder eine Aktion auszulösen. Funktionsstufe ist eine Vorschaufunktion, die in der Version 9.0 eingeführt wurde. Weitere Informationen: Einzelheiten finden Sie im Abschnitt **Geschäftsprozessflussautomatisierung mit Funktionsstufen** im [Blog: Neue Automatisierungs- und für Visualisierungsfunktionen für Geschäftsprozessflüsse (öffentliche Vorschau)](https://blogs.msdn.microsoft.com/crm/2017/10/25/new-automation-and-visualization-features-for-business-process-flows-public-preview/).

### <a name="related-topics"></a>Verwandte Themen

[setProgress](setprogress.md)

[formContext.data.process](../../formContext-data-process.md)
 


