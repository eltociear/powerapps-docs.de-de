---
title: addCustomView (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 482b8cd4-e643-48ea-8a54-d8601271ec81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addcustomview-client-api-reference"></a>addCustomView (Client-API-Referenz)



Fügt eine neue Ansicht für das Suchdialogfeld hinzu. 

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Suche

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).addCustomView(viewId, entityName, viewDisplayName, fetchXml, layoutXml, isDefault)`

## <a name="parameters"></a>Parameter

- **viewId**: Zeichenfolge. Die Zeichenfolgendarstellung eines GUID (EAAL) für eine Ansicht.
    > [!NOTE]
    > Dieser Wert wird nie gespeichert und muss nur unter den anderen verfügbaren Ansichten für die Suche eindeutig sein. Eine Zeichenfolge für eine nicht-gültige GUID funktioniert, beispielsweise „00000000-0000-0000-0000-000000000001“. Es wird empfohlen, dass Sie ein spezielles Tool (beispielsweise **guidgen.exe**) verwenden, um eine gültige GUID zu generieren.  

- **entityName**: Zeichenfolge. Der Name der Entität.
- **viewDisplayName**: Zeichenfolge. Der Name der Ansicht.
- **fetchXml**: Zeichenfolge. Die fetchXml-Abfrage für die Ansicht.
- **layoutXml**: Zeichenfolge. Das XML, das das Layout der Ansicht definiert.
- **isDefault**: Boolesch: Bestimmt, ob die Ansicht die Standardansicht sein soll.

## <a name="remarks"></a>Anmerkungen

Diese Methode funktioniert nicht mit **Besitzer**-Suchen. Besitzer-Suchen werden verwendet, um Datensätze im Besitz des Benutzers zuzuweisen.
