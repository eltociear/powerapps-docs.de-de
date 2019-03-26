---
title: openFile (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 01/25/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 6a2497fe-08ad-4953-b3ff-44c72bc25082
author: KumarVivek
ms.author: kvivek
manager: annbe
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
|openFileOptions |Objekt | Nein|Ein Objekt, das beschreibt, ob die Datei geöffnet oder gespeichert werden soll. Das Objekt hat das folgende Attribut:<br/>- **openMode**: Geben Sie `1` zum Öffnen und `2` zum Speichern an. <br/>Wird dieser Parameter nicht angegeben, wird `1` (öffnen) als Standardwert übergeben.<br/>Dieser Parameter wird nur im Einheitliche Oberfläche unterstützt.|

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Navigation](../xrm-navigation.md)
