---
title: setValue (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1324b465-6012-47d4-bf35-837df82014cb
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setvalue-client-api-reference"></a>setValue (Client-API-Referenz)

Legt den Datenwert für ein Attribut fest. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).setValue(value)`

# <a name="parameters"></a>Parameter
Abhängig vom Typ des Attributs.

<!-- TODO: 

Change type links from msdn to docs, i.e. https://msdn.microsoft.com/library/dwab3ed2.aspx to /scripting/javascript/reference/number-object-javascript 

or MDN https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number
-->

| Attributtyp|Parametertyp|
-------|------|
| Boolescher Wert| [Boolesch](https://msdn.microsoft.com/library/t7bkhaz6.aspx) |
| datetime|[Datum](https://msdn.microsoft.com/library/cd9w2te4.aspx)|
| Dezimalzahl| [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| double| [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx) |
| Integer|[Anzahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| Suche  | [Array](https://msdn.microsoft.com/library/k4h76zbx.aspx) Ein Array von Suchobjekten. <br/><br/>Bestimmte Suchen, sogenannte PartyList-Suchen, ermöglichen das Zuordnen mehrerer Datensätze in einer Suche, z. B. das **An:**-Feld für einen E-Mail-Entitätsdatensatz. Daher verwenden alle Suchdatenwerte ein Suchobjekt-Array, auch wenn das Suchattribut nicht mehr als einen hinzugefügten Datensatzverweis unterstützt.<br/><br/>Jede Suche bietet folgende Eigenschaften:<br/>- *entityType*: Zeichenfolge. Der Name der Entität, der in der Suche angezeigt wird.<br/>- *id*: Zeichenfolge: die Zeichenfolgendarstellung des GUID-Werts für den Datensatz, der in der Suche angezeigt wird. Der Wert muss folgendem Format entsprechen: {XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}<br/>- *name*Zeichenfolge: Der Text, der den in der Suche anzuzeigenden Datensatz darstellt.|
| memo  | [Zeichenfolge](https://msdn.microsoft.com/library/ecczf11c.aspx)  |
| Zahlung| [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| optionset | [Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| Zeichenfolge | [Zeichenfolge](https://msdn.microsoft.com/library/ecczf11c.aspx)|
| memo | [Zeichenfolge](https://msdn.microsoft.com/library/ecczf11c.aspx)|
| Zahlung|[Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| optionset, multiselectoptionset|[Zahl](https://msdn.microsoft.com/library/dwab3ed2.aspx)<br/><br/>Die [getOptions](getOptions.md)-Methode gibt Optionswerte als Zeichenfolgen zurück. Sie müssen [parseInt](https://msdn.microsoft.com/library/x53yedee.aspx) verwenden, um sie in Zahlen zu konvertieren, bevor Sie diese Werte verwenden können, um den Wert eines optionset-Attributs festzulegen. Gültige statuscode (Statusgrund)-Optionen hängen vom aktuellen Zustandscode des Datensatzes ab. Das statecode (Status)-Feld kann nicht in den Formularskripten festgelegt werden. Um zu wissen, welche statecode-Werte gültig sind, lesen Sie die Metadaten für die Attribute. <!-- See [Default status and status reason values](../../../customize/default-status-and-status-reason-values.md) for a list of default values for system entities. --> Für benutzerdefinierte Entitäten verwenden Sie den Entitäts-Metadatenbrowser. Anschließend sollten Sie auch benutzerdefinierte Statusübergänge, die auf das Feld angewendet wurden, berücksichtigen. Weitere Informationen: [Definieren Sie Statusgrundübergänge](/dynamics365/customer-engagement/customize/define-status-reason-transitions).| 
| String| [Zeichenfolge](https://msdn.microsoft.com/library/ecczf11c.aspx) <br/><br/> Ein Zeichenfolgenfeld mit dem E-Mail-Format erfordert, dass die Zeichenfolge eine gültige E-Mail-Adresse darstellt.|


> [!NOTE]
> Die Aktualisierung eines Attributs mithilfe von **setValue** führt nicht dazu, dass **OnChange**-Ereignishandler ausgeführt werden. Wenn die **OnChange**-Ereignishandler ausgeführt werden sollen, müssen Sie [fireOnChange](../attributes/fireOnChange.md) zusätzlich zu **setValue** festlegen. <br/><br/>
Wenn keine modellgesteuerten Microsoft Apps für Tablets mit dem Server verbunden sind, funktioniert **setValue** nicht.<br/><br/>Sie können nicht den Wert von zusammengesetzten Attributen festlegen. Weitere Informationen: [Schreiben von Skripts für zusammengesetzte Attribute](../composite-attributes.md).

### <a name="related-topic"></a>Verwandtes Thema
[getValue (Client-API-Referenz)](getValue.md)
