---
title: setActiveStage (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9c40a770-f4cb-4230-8893-0527f8472825
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setactivestage-client-api-reference"></a>setActiveStage (Client-API-Referenz)



[!INCLUDE[./includes/setActiveStage-description.md](./includes/setActiveStage-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.setActiveStage(stageId, callbackFunction);`

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>stageId</td>
<td>String</td>
<td>Ja</td>
<td>Die ID der abgeschlossenen Phase für die Entität, die zur aktiven Phase gemacht werden soll. </td>
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
<td>Ungültig</td>
<td>Es gibt drei Gründe, weshalb dieser Wert zurückgegeben werden kann:
<ul>
<li>Die *stageId* ist ein nicht-bestehender Phasen-ID-Wert.</li>
<li>Die aktive Phase ist nicht die ausgewählte Phase.</li>
<li>Der Datensatz ist noch nicht gespeichert.</li>
</ul>
</td>
</tr>
<tr>
<td>Nicht erreichbar</td>
<td>Die Phase befindet sich in einem anderen Pfad.</td>
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
>Diese Methode kann nur verwendet werden, wenn die ausgewählte Phase und die aktive Phase identisch sind. Wenn Ihr Code vom [OnStageChange](../../events/onstagechange.md)-Ereignis initiiert wird, wird die aktuelle Phase ausgewählt. Wenn Ihr Code vom [OnStageSelected](../../events/onstageselected.md)-Ereignis initiiert wird, sollten Sie die[getActiveStage](getActiveStage.md)-Methode verwenden, um zu überprüfen, ob die ausgewählten Phase auch die aktive Phase ist. Für ein anderes Formularereignis ist es nicht möglich, zu ermitteln, welche Phase derzeit ausgewählt ist. Zur Erzielung optimaler Ergebnisse sollte diese Methode nur in Code verwendet werden, der in Funktionen verwendet wird, die von den [OnStageChange](../../events/onstagechange.md) und [OnStageSelected](../../events/onstageselected.md)-Ereignissen initiiert werden.

### <a name="related-topics"></a>Verwandte Themen

[getActiveStage](getActiveStage.md)

[formContext.data.process](../../formContext-data-process.md)
 


