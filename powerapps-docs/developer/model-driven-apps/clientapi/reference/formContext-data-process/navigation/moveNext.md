---
title: moveNext (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 97640c6a-816b-4d18-9b0b-e79411787c1a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="movenext-client-api-reference"></a>moveNext (Client-API-Referenz)



[!INCLUDE[./includes/moveNext-description.md](./includes/moveNext-description.md)]

Sie können auch zu einer nächsten Phase in einer anderen Entität wechseln. 

## <a name="syntax"></a>Syntax

`formContext.data.process.moveNext(callbackFunction);`

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>callbackFunction</td>
<td>Funktion</td>
<td>No</td>
<td>Eine Funktion, die aufgerufen wird, wenn der Vorgang abgeschlossen ist. Dieser Rückruffunktion wird einer der folgenden Zeichenfolgenwerte übergeben, um den Status eines Vorgangs anzuzeigen:
<table>
<tr>
<th>Value</th>
<th>Grund</th>
</tr>
<tr>
<td>Erfolg</td>
<td>Der Vorgang war erfolgreich.</td>
</tr>
<tr>
<td>crossEntity</td>
<td>Die nächste Phase ist für eine andere Entität.</td>
</tr>
<tr>
<td>Ende</td>
<td>Die aktive Phase ist die letzte Phase des aktiven Pfads.</td>
</tr>
<tr>
<td>Ungültig</td>
<td>Der Vorgang ist fehlgeschlagen, da die ausgewählte Phase nicht dieselbe ist wie die aktive Phase.</td>
</tr>
<tr>
<td>dirtyForm</td>
<td>Dieser Wert wird zurückgegeben, wenn die Daten auf der Seite nicht gespeichert werden.</td>
</tr>
</table>
</td>
</tr>
</table>

>[!IMPORTANT]
>Diese Methode kann nur verwendet werden, wenn die ausgewählte Phase und die aktive Phase identisch sind. Wenn Ihr Code vom [OnStageChange](../../events/onstagechange.md)-Ereignis initiiert wird, wird die aktuelle Phase ausgewählt. Wenn Ihr Code vom [OnStageSelected](../../events/onstageselected.md)-Ereignis initiiert wird, sollten Sie die [getActiveStage](../activestage/getActiveStage.md)-Methode verwenden, um zu überprüfen, ob die ausgewählten Phase auch die aktive Phase ist. Für ein anderes Formularereignis ist es nicht möglich, zu ermitteln, welche Phase derzeit ausgewählt ist. Zur Erzielung optimaler Ergebnisse sollte diese Methode nur in Code verwendet werden, der in Funktionen verwendet wird, die von den [OnStageChange](../../events/onstagechange.md) und [OnStageSelected](../../events/onstageselected.md)-Ereignissen initiiert werden.

## <a name="remarks"></a>Anmerkungen

Diese Methoden verursachen ein [OnStageChange](../../events/onstagechange.md)-Ereignis.

### <a name="related-topics"></a>Verwandte Themen

[movePrevious](movePrevious.md)

[formContext.data.process](../../formContext-data-process.md)
 


