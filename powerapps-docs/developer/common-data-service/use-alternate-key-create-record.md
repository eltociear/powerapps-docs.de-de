---
title: 'Verwenden Sie einen Alternativschlüssel, um Datensätze zu erstellen (Common Data Service) | Microsoft Docs'
description: 'Sie können Alternativschlüssel zum Erstellen von Instanzen von der Entity- und EntityReference-Klassen verwenden. Dieses Thema erörtert Verwendungsmuster und mögliche Ausnahmen, die möglicherweise beim Verwenden von Alternativschlüsseln ausgelöst werden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-an-alternate-key-to-create-a-record"></a>Verwenden Sie einen Alternativschlüssel, um Datensätze zu erstellen

Sie können jetzt Alternativschlüssel zum Erstellen von Instanzen von <xref:Microsoft.Xrm.Sdk.Entity> und <xref:Microsoft.Xrm.Sdk.EntityReference>-Klassen verwenden. Dieses Thema erörtert Verwendungsmuster und mögliche Ausnahmen, die möglicherweise beim Verwenden von Alternativschlüsseln ausgelöst werden. Um die Definition von Alternativschlüssel für eine Entität zu verstehen, siehe [Definieren von Alternativschlüsseln für eine Entität](define-alternate-keys-entity.md).  
  
<a name="BKMK_entity"></a>   
## <a name="using-alternate-keys-to-create-an-entity"></a>Verwenden der Alternativschlüssel zum Erstellen einer Entität  
 Sie können jetzt eine <xref:Microsoft.Xrm.Sdk.Entity> mit einer primären ID oder einer einzigen `KeyAttribute` in einem einzigen Aufruf mithilfe des neuen Konstruktors erstellen.  
  
```csharp  
public Entity (string logicalName, Guid id) {…}    
public Entity (string logicalName, string keyName, object keyValue) {…}  
public Entity (string logicalName, KeyAttributeCollection keyAttributes) {…}  
  
```  
  
 Eine gültige <xref:Microsoft.Xrm.Sdk.Entity>, die für Updatevorgänge verwendet wird, umfasst einen logischen Entitätsnamen und eines der Folgenden:  
  
-   Einen Wert für ID (primären GUID-Schlüsselwert) (oder)  
  
-   Eine <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> mit einem gültigen Satz von Attributen, die mit einem definierten Schlüssel für die Entität übereinstimmen.  
  
<a name="BKMK_EntityReference"></a>   
## <a name="using-alternate-keys-to-create-an-entityreference"></a>Verwenden der Alternativschlüssel zum Erstellen einer EntityReference  
 Sie können jetzt auch eine <xref:Microsoft.Xrm.Sdk.EntityReference> ohne eine primäre ID und mit einer einzigen `KeyAttribute` in einem einzigen Aufruf mithilfe des neuen Konstruktors erstellen.  
  
```csharp  
public EntityReference(string logicalName, Guid id) {…}    
public EntityReference(string logicalName, string keyName, object keyValue) {…}    
public EntityReference(string logicalName, KeyAttributeCollection keyAttributeCollection) {…}  
  
```  
  
 Eine gültige <xref:Microsoft.Xrm.Sdk.EntityReference> enthält einen logischen Entitätsnamen und eines der Folgenden:  
  
-   Einen Wert für ID (primären GUID-Schlüsselwert) oder  
  
-   Eine <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection>-Sammlung mit einem gültigen Satz von Attributen, die mit einem definierten Schlüssel für die Entität übereinstimmen.  
  
<a name="BKMK_input"></a>   
## <a name="alternative-input-to-messages"></a>Alternative Eingabe für Meldungen  
 Wenn Sie Entitäten an <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> und <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> übergeben, können Werte, die für Suchattribute mithilfe von <xref:Microsoft.Xrm.Sdk.EntityReference> bereitgestellt werden, jetzt <xref:Microsoft.Xrm.Sdk.EntityReference> mit alternativen Schlüsseln verwenden, die in <xref:Microsoft.Xrm.Sdk.EntityReference.KeyAttributes> definiert sind, um einen verknüpften Datensatz anzugeben.  Diese werden aufgelöst und durch die primären ID-basierten Entitätsverweise ersetzt, bevor die Meldungen verarbeitet werden.  
  
<a name="BKMK_Exceptions"></a>   
## <a name="exceptions-when-using-alternate-keys"></a>Ausnahmen beim Verwenden von Alternativschlüsseln  
 Sie müssen die folgenden Bedingungen und möglichen Ausnahmen berücksichtigen, wenn Alternativschlüssel verwendet werden:  
  
-   Die primäre ID wird verwendet, wenn sie bereitgestellt wird. Wenn sie nicht zur Verfügung gestellt wird, wird die <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> untersucht.  Wenn die <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> nicht zur Verfügung gestellt wird, wird ein Fehler ausgelöst.  
  
-   Wenn die bereitgestellte <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> ein Attribut enthält, das der Primärschlüssel der Entität ist und der Wert gültig ist, wird die ID-Eigenschaft der <xref:Microsoft.Xrm.Sdk.Entity> oder <xref:Microsoft.Xrm.Sdk.EntityReference> mit dem zur Verfügung gestellten Wert aufgefüllt.  
  
-   Wenn die Schlüsselattribute bereitgestellt werden, versucht das System, dem Satz von Attributen, die mit den Schlüsseln für die <xref:Microsoft.Xrm.Sdk.Entity> verfügbar gemacht werden, zu entsprechen.  Wenn es keine Übereinstimmung findet, wird ein Fehler ausgelöst.  Wenn es eine Übereinstimmung findet, überprüft es die bereitgestellten Werte für diese Attribute. Im Falle der Gültigkeit ruft es die ID des Datensatzes ab, der mit den bereitgestellten Schlüsselwerten übereinstimmt, und füllt den ID-Wert der <xref:Microsoft.Xrm.Sdk.Entity> oder <xref:Microsoft.Xrm.Sdk.EntityReference> mit diesem Wert auf.  
  
-   Wenn Sie ein festgelegtes Attribut angeben, das nicht als eindeutige Schlüssel definiert ist, wird ein Fehler ausgelöst, der angibt, dass die Verwendung von eindeutigen Schlüsselattributen erforderlich ist.  
  
### <a name="see-also"></a>Siehe auch  
 [Definieren von Alternativschlüsseln für eine Entität](define-alternate-keys-entity.md)   
 [Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung](use-change-tracking-synchronize-data-external-systems.md)   
 [Einen Datensatz mit Upsert einfügen oder aktualisieren](use-upsert-insert-update-record.md)
