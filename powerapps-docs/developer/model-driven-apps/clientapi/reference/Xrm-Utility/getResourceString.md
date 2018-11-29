---
title: getReesourceString (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d5e51eac-ce0a-4f4a-b7b6-495433e3f8c1
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getresourcestring-client-api-reference"></a>getResourceString (Client-API-Referenz)



[!INCLUDE[./includes/getResourceString-description.md](./includes/getResourceString-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Utility.getResourceString(webResourceName,key)` 

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|webResourceName|String|Ja|Der Name der Webressource.|
|Schlüssel|String|Ja|Der Schlüssel für die lokalisierte Zeichenfolge.|

## <a name="return-value"></a>Rückgabewert

Eine lokalisierte Zeichenfolge.

## <a name="remarks"></a>Anmerkungen

<!-- 
Content adapted from /developer/resx-web-resources 
If you change this, make sure that topic is in sync.
-->

Wenn Sie RESX-Webressourcen erstellen, müssen Sie den Sprachenwert explizit festlegen sowie den Gebietsschemabezeichner (LCID) für die entsprechende Sprache im Namen der Webressource einschließen. Beispielsweise `new_/strings/MyAppResources.1033.resx` würde Ressourcen für englische Sprache enthalten. Siehe [Microsoft-Gebietsschema-ID-Werte](https://msdn.microsoft.com/library/ms912047(WinEmbedded.10).aspx) für eine Liste der LCID-Werte.

Beispielsweise gibt `Xrm.Utility.getResourceString("new_/strings/MyAppResources","hello")` den lokalisierten Zeichenfolgenwert für den Ressourcenschlüssel `hello` innerhalb der `new_/strings/MyAppResources.1033.resx` Webressource  zurück, wenn die bevorzugte Sprache des Benutzers Englisch ist. Beachten Sie, dass die Funktion sich nicht auf eine bestimmte Sprache oder vollständigen Namen der RESX-Webressource bezieht. Die Funktionalität ist von der RESX-Webressource abhängig, die mit der aufrufenden JavaScript-Webressource als Abhängigkeit verknüpft ist. Weitere Informationen: [Webressourcenabhängigkeiten](../../../web-resource-dependencies.md).

Der entsprechende Zeichenfolgenwert ist festgelegt durch die Spracheinstellung und die deaktivierten Sprachen einzelner Benutzer, die in der Organisation verfügbar sind. Wenn eine isolierte Zeichenfolge nicht gefunden wird, die Spracheinstellung des Benutzers entspricht, wird automatisch die lokalisierte Zeichenfolge auf die Ausgangssprache für die Organisation zurückgesetzt. Wenn keine entsprechende Zeichenfolge für die Organisationsausgangssprache gefunden wird, wird ein NULL-Wert zurückgegeben.

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility](../xrm-utility.md)<br />
[Zeichenfolge (RESX) Webressourcen](../../../resx-web-resources.md)<br />
[Abhängigkeiten von Webressourcen](../../../web-resource-dependencies.md)



