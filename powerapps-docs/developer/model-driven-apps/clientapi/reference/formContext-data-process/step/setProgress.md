---
title: setProgress (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setprogress-client-api-reference"></a>setProgress (Client-API-Referenz)



[!INCLUDE[./includes/setProgress-description.md](./includes/setProgress-description.md)]

## <a name="syntax"></a>Syntax

`stepObj.setProgress(stepProgress,message);`

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>stepProgress</td>
<td>Zahl</td>
<td>Ja</td>
<td>Geben Sie einem der folgenden Werte an, um den Schrittstatus anzugeben:
<ul>
<li>0: Keine</li>
<li>1: Verarbeitung</li>
<li>2 : Abgeschlossen</li>
<li>3: Fehler</li>
<li>4: Ungültig</li>
</ul>
</td>
</tr>
<tr>
<td>Meldung</td>
<td>String</td>
<td>No</td>
<td><p>Eine optionale Meldung, die als alternativer Text auf das Symbol für den Schritt festgelegt ist.</td>
</tr>
</table>


## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge. 

**Beschreibung**: Gibt "ungültig "oder "Erfolg" zurück, davon abhängig, ob der Schrittstatus aktualisiert wurde.

## <a name="remarks"></a>Anmerkungen

Diese Methode wird nur für die Funktionsstufen unterstützt. Funktionsstufen sind Schaltflächen bei den Geschäftsprozessphasen, auf die Benutzer klicken können, um einen bedarfsgesteuerten Workflow oder eine Aktion auszulösen. Funktionsstufe ist eine Vorschaufunktion, die in der Version 9.0 eingeführt wurde. Weitere Informationen: Weitere Informationen finden Sie im Abschnitt **Geschäftsprozessflussautomatisierung mit Funktionsstufe** im Blog [Neue Automatisierungs- und für Visualisierungsfunktionen für Geschäftsprozessflüsse (öffentliche Vorschau)](https://blogs.msdn.microsoft.com/crm/2017/10/25/new-automation-and-visualization-features-for-business-process-flows-public-preview/)

### <a name="related-topics"></a>Verwandte Themen

[getProgress](getprogress.md)
 
[formContext.data.process](../../formContext-data-process.md)

