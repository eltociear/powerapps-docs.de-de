---
title: save (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a27f8267-9b24-42b7-a075-420a26db6693
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="save-client-api-reference"></a>Speichern (Client-API-Referenz)



[!INCLUDE[./includes/save-description.md](./includes/save-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.entity.save(saveOption);`

## <a name="parameters"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|saveOptions|String|No|Legen Sie Optionen für das Speichern des Datensatzes fest. Wenn keine Parameter in der Methode enthalten sind, wird der Datensatz einfach gespeichert. Dies entspricht der Verwendung des **Speichern**-befehls.<br/>Geben Sie einen der folgenden Werte an:<br/><br/>- **saveandclose**: Dies entspricht der Verwendung des **Speichern und Schließen**-Befehls.<br/><br/>- **saveandnew**: Dies entspricht der Verwendung des **Speichern und Erneuern**-Befehls.|

## <a name="example"></a>Beispiel

Um ein neues Formular nach dem Abschluss des Speichern zu öffnen:

`formContext.data.entity.save("saveandnew");`

### <a name="related-topics"></a>Verwandte Themen

[formContext.data.save](../formContext-data/save.md)

[formContext](../../clientapi-form-context.md)

