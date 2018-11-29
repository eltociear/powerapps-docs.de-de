---
title: setSubmitMode (Client API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d0728377-4365-4571-97af-9b99b2a39b65
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setsubmitmode-client-api-reference"></a>setSubmitMode (Client-API-Referenz)



Legt fest, ob Daten vom Attribut gesendet werden, wenn der Datensatz gespeichert wird. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).setSubmitMode(mode)`

## <a name="parameters"></a>Parameter

**Typ:**: Zeichenfolge. 

**Beschreibung**: Legt einen der folgenden Werte fest:
- **immer**: Die Daten werden immer beim Speichern gesendet.
- **nie**: Die Daten werden niemals beim Speichern gesendet. Wenn diese Option festgelegt ist, können Felder im Formular für dieses Attribut nicht bearbeitet werden.
- **dirty**: Standardverhalten. Die Daten werden beim Speichern gesendet, wenn sie geändert wurden.
 
## <a name="remarks"></a>Anmerkungen
Sie können mit dieser Methode steuern, wann Daten für ein Attribut gesendet werden, wenn ein Datensatz erstellt oder gespeichert wird. Beispielsweise verfügen Sie über ein Feld im Formular, das nur zum Steuern der Logik im Formular vorgesehen ist. Sie sind nicht interessiert, die Daten darin zu erfassen. Sie legen es so fest, dass die Daten nicht gespeichert werden. Oder sie haben ein Plug-In, das davon abhängt, dass der Wert immer enthalten ist. Sie möchten das Attribut so festlegen, dass es immer enthalten ist. 

Attribute, die nicht aktualisiert werden nach dem ersten Speichern des Datensatzes, wie z. B. **createdby**, werden so festgelegt, dass diese beim Speichern nicht gesendet werden. Um zu erzwingen, dass ein Attributwert gesendet wird, egal ob er geändert wurde oder nicht, verwenden Sie diese Methode mit der *mode*-Funktion mit dem auf „immer“ festgelegten Modusparameter.

### <a name="related-topic"></a>Verwandtes Thema
[getSubmitMode (Client-API-Referenz)](getSubmitMode.md)

