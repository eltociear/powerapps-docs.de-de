---
title: Beschreiben einer Beziehung zwischen Entitäten mit Verbindungsrollen (Common Data Service) | Microsoft-Dokumentation
description: Beschreibung einer Beziehung zwischen Entitäten unter Verwendung von Verbindungsrollen und Verbindungsrollenkategorien.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 07bd45625e0947ed7123f891aa9b33aac214869d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748230"
---
# <a name="describe-a-relationship-between-entities-with-connection-roles"></a>Beschreiben einer Beziehung zwischen Entitäten mit Verbindungsrollen

Sie können die Beziehung zwischen Datensätzen durch Rollen die beschreiben, die Sie ihnen zuweisen.  
  
 Es gibt verschiedene Möglichkeiten, um in die Verbindungsrollen in ener Verbindung zu verwenden:  
  
-   Wenden Sie dieselbe Rolle auf den Quelldatensatz und den Zieldatensatz an. Ein "Freund", ein "Team-Mitglied" oder ein "Kollege" sind Beispiele für Rollen, die auf beide Datensätze in der Verbindung angewendet werden können.  
  
-   Wenden Sie eine Rolle auf den Quelldatensatz oder den Zieldatensatz an, aber nicht auf beide. Eine "Vertriebsmitarbeiter"-Rolle in einem Kontakt oder einer Verkaufschance ist ein Beispiel einer solchen Rolle. Die Datensätze, wie Verkaufschance, Rechnung oder Vertriebsauftrag enthalten in der Regel Informationen dazu, was sie repräsentieren und benötigen keine Rolle, die ihnen zugewiesen wird.  
  
-   Zwei entsprechende Rollen anwenden (manchmal als gegenseitige Rollen bezeichnet). Eine Rolle gilt für einen Quelldatensatz, und die andere Rolle gilt für einen Zieldatensatz. Ein "Doktor" ein und "Patient", ein "Eltetn" und ein "Kind" sind Beispiele für entsprechende Rollen.  
  
## <a name="connection-role-categories"></a>Kategorien von Verbindungsrollen  
 Wenn Sie Verbindungsrollen erstellen, können Sie festlegen, zu welcher Kategorie sie gehören. Sie können beispielsweise die folgenden Kategorien verwenden:  
  
- Geschäftlich (Einkäufer, Lieferant, Mitbewerber)  
  
- Familie (Vater, Schwester, Vetter)  
  
- Soziale Beziehungen (Tennispartner, Clubmitglied, Freund)  
  
  Die Kategorienliste ist anpassbar. Sie können die Kategorien hinzufügen, die am besten zu Ihrem Geschäftsmodell passen.  
  
## <a name="create-connection-roles"></a>Verbindungsrollen erstellen  
 Um eine Verbindungsrolle zu erstellen, müssen Sie die folgenden Informationen angeben:  
  
- Verwenden Sie das Attribut `ConnectionRole.Name`, um einen Rollennamen anzugeben.  
  
- Verwenden Sie das Attribut `ConnectionRole.Description`, um eine Rollenbeschreibung hinzuzufügen.  
  
- Verwenden Sie das Attribut `ConnectionRole.Category`, um eine Rollenkategorie anzugeben. Die möglichen Werte für dieses Attribut werden im globalen Optionssatz `connectionrole_category` definiert.  
  
- Wenn Sie eine Verbindungsrolle erstellen, können Sie einen Entitätstyp angeben, auf den die Rolle angewendet wird, beispielsweise Lead, Firma oder Mitbewerber. Wenn Sie keinen bestimmten Entitätstyp angeben, können Sie eine Verbindungsrolle auf alle Common Data Service-Entitäten anwenden. Um den Entitätstyp zu definieren, verwenden Sie das `ConnectionRoleObjectTypeCode.AssociatedObjectTypeCode`-Attribut. Um die Verbindungsrolle mit einem spezifischen Entitätstyp zu verbinden, verwenden Sie das `ConnectionRoleObjectTypeCode.ConnectionRoleId`-Attribut. Auf einen Verbindungsrollen-Datensatz kann von mehreren Verbindungsobjekttypcode-Datensätzen verwiesen werden. Um alle Verweise auf den Verbindungsrollen-Datensatz zu entfernen, können Sie diese Verbindungsrolle auf alle Common Data Service-Entitäten anwenden.  
  
  > [!TIP]
  >  Um die Verbindungsrollen für eine Firmenentität zu suchen, geben Sie in der Abfrage alle Rollen an, die mit der Firmenentität (Entitäts-Typcode = 1) oder mit allen Entitäten (Entitäts-Typcode = 0) verknüpft sind.  
  
## <a name="associate-and-disassociate-connection-roles"></a>Zuordnen und Aufheben der Zuordnung von Verbindungsrollen  
 Um die Rollen in der Verbindung zuzuordnen, können Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*>-Methode verwenden. Um die Zuordnung der Rollen aufzuheben, verwenden Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*>-Methode. Weitere Informationen zur `Associate`-Message und zur `Disassociate`-Message, siehe [Einführung zu Entitäten in Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entities).  
  
### <a name="see-also"></a>Siehe auch  
 [Verbindungsentitäten](connection-entities.md)   
 [Beispiel-Code für Verbindungsentitäten](/dynamics365/customer-engagement/developer/sample-code-connection-entities)   
 [Beispiel: Eine reziproke Verbindungsrolle erstellen (frühe Bindung)](/dynamics365/customer-engagement/developer/sample-create-reciprocal-connection-role-early-bound)   
 [Verbindungsentität](/reference/entities/connection.md)