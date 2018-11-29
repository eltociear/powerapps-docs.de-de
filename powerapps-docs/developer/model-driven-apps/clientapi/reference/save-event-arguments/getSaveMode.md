---
title: getSaveMode (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 03e970ee-7ed3-4df2-9670-222d76a479fd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getsavemode-client-api-reference"></a>getSaveMode (Client-API-Referenz)



[!INCLUDE[./includes/getSaveMode-description.md](./includes/getSaveMode-description.md)]

## <a name="syntax"></a>Syntax

`executionContext.getEventArgs().getSaveMode()`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Die folgende Tabelle beschreibt die unterstützten Werte, die zurückgegeben werden, um unterschiedliche Arten zu ermitteln, die vom Benutzer gespeichert werden können.

|Value |Speichermodus |Entity|
|---|---|---|
|1|Speichern|Alle|
|2|Speichern und schließen|Alle|
|5|Deaktivieren|Alle|
|6|Erneut aktivieren|Alle|
|7|Senden|Per E-Mail senden|
|15|Qualifizierung aufheben|Lead|
|16|Qualifizieren|Lead|
|47|Zuweisen|Entitäten im Besitz von Benutzern oder Teams.|
|58|Als abgeschlossen speichern|Aktivitäten|
|59|Speichern und neu|Alle|
|70|Automatisches Speichern|Alle|

## <a name="remarks"></a>Anmerkungen

Diese Methode ist wichtig, wenn Sie automatische Speicherung für die meisten Formulare aktivieren möchten, sie jedoch für bestimmte für Formulare deaktivieren möchten.  

## <a name="example"></a>Beispiel

Der folgende Code, der für das Ereignis **OnSave** mit dem übergebenen Ausführungskontext registriert ist, verhindert Speicherungen, die durch eine automatische Speicherung initiiert werden, lässt jedoch andere zu. Wenn automatische Speicherung aktiviert ist, ist das Wegnavigieren gleichbedeutend mit **Speichern und Schließen**. Dieser Code verhindert, dass Speicherungen durch den 30 Sekunden-Timer initiiert werden, oder wenn die Mitarbeiter von einem Formular nicht mit nichtgespeicherten Daten wegnavigieren.

```JavaScript
function preventAutoSave(executionContext) {
    var eventArgs = executionContext.getEventArgs();
    if (eventArgs.getSaveMode() == 70 || eventArgs.getSaveMode() == 2) {
        eventArgs.preventDefault();
    }
}
```

Um einen Datensatz zu speichern, muss der Benutzer auf das Symbol **Speichern** unten im Formular klicken oder ein benutzerdefinierter **Speichern**-Befehl muss der Befehlsleiste hinzugefügt werden.

### <a name="related-topics"></a>Verwandte Themen

[isDefaultPrevented](isDefaultPrevented.md)

[preventDefault](preventDefault.md)

