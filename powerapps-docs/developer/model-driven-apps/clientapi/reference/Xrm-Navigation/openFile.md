---
title: openFile (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6a2497fe-08ad-4953-b3ff-44c72bc25082
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openfile-client-api-reference"></a>openFile (Client-API-Referenz)



[!INCLUDE[./includes/openFile-description.md](./includes/openFile-description.md)]

## <a name="syntax"></a>Syntax

`Xrm.Navigation.openFile(file,openFileOptions)`

## <a name="parameters"></a>Parameter

| Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|Datei |Objekt | Ja|Ein Objekt, das die Datei beschreibt, die geöffnet werden soll. Das Objekt hat die folgenden Attribute:<br/>- **fileContent**: Zeichenfolge. Inhalt der Datei.  <br/>- **fileName**: Zeichenfolge. Name der Datei.<br/>- **fileSize**: Zahl. Größe der Dateigröße in KB.<br/>- **mimeType**: Zeichenfolge. MIME-Typ der Datei.|
|openFileOptions |Zahl | No|Geben Sie an, ob die Datei geöffnet bzw. gespeichert wird:<br/> `1:Open`<br/> `2:Save`<br/>Wird dieser Parameter nicht angegeben, wird **1** (öffnen) als Standardwert übergeben.|

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Navigation](../xrm-navigation.md)
