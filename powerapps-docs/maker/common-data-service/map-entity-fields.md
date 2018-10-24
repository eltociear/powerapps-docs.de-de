---
title: Zuordnen von Entitätsfeldern in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Entitätsfelder zuordnen.
ms.custom: ''
ms.date: 05/29/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 7c5aa1c3-bde9-43f1-a369-fdcdbf14dec0
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 7e84e10a824ea218063cb2dccdc15ed7ae2340da
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688672"
---
# <a name="map-entity-fields"></a>Zuordnen von Entitätsfeldern
 
Sie können Attribute zwischen Entitäten zuordnen, die eine Entitätsbeziehung aufweisen. Dadurch können Sie Standardwerte für einen Datensatz festlegen, der im Kontext eines anderen Datensatzes erstellt wird. 

## <a name="easier-way-to-create-new-records-in-model-driven-apps"></a>Einfacher Ansatz zum Erstellen neuer Datensätze in modellgesteuerten Apps

Nehmen wir an, ein Benutzer möchte einen neuen Kontaktdatensatz für eine Person hinzufügen, die Mitarbeiter eines bestimmten Kontos ist. Er hat zwei Möglichkeiten:  
  
### <a name="the-hard-way"></a>Komplizierter Ansatz

Benutzer können einfach in der App navigieren, um einen neuen Kontaktdatensatz von Grund auf neu zu erstellen. Aber dann müssen sie das übergeordnete Konto festlegen und mehrere Informationen wie Adresse und Telefonnummer eingeben, die ggf. mit dem übergeordneten Konto übereinstimmen. Dieser Schritt kann zeitaufwändig sein und potenzielle Fehlerquellen beinhalten.  
  
### <a name="the-easier-way"></a>Einfacher Ansatz

Einfacher ist es, mit der Kontoentität zu beginnen. Wählen Sie im Formular im Unterraster **Kontakte** **+** aus, um einen Kontakt hinzuzufügen. Zunächst werden Sie aufgefordert, vorhandene verwandte Kontakte zu prüfen, um nicht versehentlich einen doppelten Datensatz zu erstellen. Wenn Sie keinen vorhandenen Datensatz finden, wählen Sie **Neu** aus, und erstellen Sie einen neuen Kontaktdatensatz. 

Das neue Kontaktdatensatzformular enthält alle zugeordneten Attributwerte aus dem Konto wie Adresse und Telefonnummer als Standardwerte. Sie können diese Werte bearbeiten, bevor Sie den Datensatz speichern.

## <a name="how-this-works"></a>Funktionsweise

Wenn Sie Entitätsfelder für eine 1:n-Entitätsbeziehung zuordnen, werden bestimmte Elemente aus dem Datensatz der primären Entität in das neue verknüpfte Entitätsformular kopiert, um Standardwerte festzulegen, die sich vor dem Speichern bearbeiten lassen.
 
  
> [!NOTE]
> Diese Zuordnungen legen nur Standardwerte für einen Datensatz fest, bevor er gespeichert wird. Diese Werte lassen sich vor dem Speichern bearbeiten. Die übertragenen Daten entsprechen den Daten zu einem bestimmten Zeitpunkt. Sie werden nicht synchronisiert, wenn sich die Quelldaten später ändern.
>   
> Diese Zuordnungen werden nicht für verknüpfte Datensätze übernommen, die mit einem Workflow- oder Dialogprozess erstellt wurden. Sie werden nicht automatisch auf neue Datensätze angewendet, die mit Code erstellt wurden, obwohl Entwickler die spezielle Nachricht `InitializeFrom` verwenden können ([InitializeFrom-Funktion](/dynamics365/customer-engagement/web-api/initializefrom?view=dynamics-ce-odata-9) oder [InitializeFromRequest-Klasse](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9)), um einen neuen Datensatz mit verfügbaren Zuordnungen zu erstellen.  

## <a name="open-solution-explorer"></a>Öffnen des Projektmappen-Explorers

Entitätsfelder lassen sich nur über den Projektmappen-Explorer zuordnen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
Felder werden im Rahmen einer 1:n- oder einer n:1-Entitätsbeziehung zugeordnet. Machen Sie sich daher zunächst mit [1:n- und n:1-Entitätsbeziehungen](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships) vertraut.

## <a name="view-mappable-fields"></a>Anzeigen zum Zuordnen geeigneter Felder

Feldzuordnungen werden nicht innerhalb der Entitätsbeziehungen definiert, doch sie sind in der Benutzeroberfläche sichtbar, die die Beziehungen anzeigt. Nicht jede 1: n-Entitätsbeziehung verfügt darüber. In einer Liste von 1:n- oder n:1-Entitätsbeziehungen lassen sich die Beziehungen nach Typ filtern. Sie haben die Wahl zwischen **Alle**, **Benutzerdefiniert**, **Anpassbar** und **Zum Zuordnen geeignet**. Zum Zuordnen geeignete Entitätsbeziehungen ermöglichen den Zugriff zum Zuordnen von Entitätsfeldern. 

![Anzeigen von zum Zuordnen geeigneter Entitätsbeziehungen](media/mappable-entity-relationships.png) 

Wenn Sie eine zum Zuordnen geeignete Entitätsbeziehung öffnen, wählen Sie in der linken Navigation **Zuordnungen** aus.

![Auswählen von Zuordnungen für die Entitätsbeziehung](media/map-entity-fields-ui-solution-explorer.png)

## <a name="delete-mappings"></a>Löschen von Zuordnungen

Wenn es Zuordnungen gibt, die Sie nicht übernehmen möchten, können Sie diese auswählen und auf die Schaltfläche ![Symbol „Löschen“](media/delete.gif) klicken.

## <a name="add-new-mappings"></a>Hinzufügen neuer Zuordnungen

Um eine neue Zuordnung zu erstellen, klicken Sie in der Symbolleiste auf **Neu**. Daraufhin wird das Dialogfeld **Feldzuordnung erstellen** geöffnet.

![Dialogfeld „Feldzuordnung erstellen“](media/create-field-mapping-dialog.png)

Wählen Sie ein Quellentitätsfeld und ein Zielentitätsfeld mit den Werten aus, die Sie zuordnen möchten. 

![Konfigurieren der Feldzuordnung](media/configure-field-mapping.png)

Wählen Sie dann **OK** aus, um das Dialogfeld zu schließen.

Die folgenden Regeln zeigen, welche Arten von Daten zugeordnet werden können.  
  
- Beide Felder müssen dem gleichen Typ entsprechen und das gleiche Format haben.  
- Die Länge des Zielfelds muss gleich oder größer als die Länge des Quellfelds sein.  
- Das Zielfeld darf nicht bereits einem anderen Feld zugeordnet werden.  
- Das Quellfeld muss im Formular sichtbar sein.  
- Das Zielfeld muss ein Feld sein, in das Daten eingegeben werden können.  
- Adress-ID-Werte können nicht zugeordnet werden.
- Wenn Sie eine Zuordnung für ein Feld vornehmen, das in keinem Formular angezeigt wird, findet die Zuordnung erst dann statt, wenn das Feld einem Formular hinzugefügt wird.
- Wenn die Felder Optionssätze sind, müssen die ganzzahligen Werte für jede Option identisch sein.  
  
> [!NOTE]
>  Wenn Sie Felder für Optionssätze zuordnen, wird empfohlen, beide Felder so zu konfigurieren, dass sie denselben globalen Optionssatz verwenden. Andernfalls kann es schwierig sein, zwei verschiedene Optionssätze manuell zu synchronisieren. Wenn die ganzzahligen Werte für jede Option nicht korrekt zugeordnet werden, können Probleme mit Ihren Daten entstehen. Weitere Informationen finden Sie unter [Erstellen und Bearbeiten globaler Optionssätze für Common Data Service für Apps (Auswahllisten)](create-edit-global-option-sets.md).  
  
## <a name="automatically-generate-field-mappings"></a>Automatisches Generieren von Feldzuordnungen  

Sie können Zuordnungen auch automatisch generieren, indem Sie im Menü **Weitere Aktionen** **Zuordng. generieren** auswählen.

Beim automatischen Generieren von Feldzuordnungen für Systementitäten ist Vorsicht geboten. Nutzen Sie diese Option, wenn Sie benutzerdefinierte Entitäten erstellen und diese zuordnen möchten. 

> [!WARNING]
> Dadurch werden alle vorhandenen Zuordnungen entfernt und durch vorgeschlagene Zuordnungen ersetzt, die nur auf Feldern mit ähnlichen Namen und Datentypen basieren. Wenn Sie diese Vorgehensweise auf eine Systementität anwenden, gehen ggf. einige erwartete Zuordnungen verloren. Im Fall von benutzerdefinierten Entitäten können Sie allerdings Zeit sparen, da Sie einfacher alle nicht gewünschten Zuordnungen löschen und andere hinzufügen können, die die Aktion „Zuordng. generieren“ nicht erstellt hat.  


## <a name="publish-customizations"></a>Veröffentlichen von Anpassungen 

Da Feldzuordnungen keine Metadaten sind, müssen Sie sie veröffentlichen, bevor Änderungen wirksam werden. 
<!-- TODO Need a general topic about publishing to link to in situations like this -->

### <a name="see-also"></a>Siehe auch
[Erstellen und Bearbeiten von 1:n- oder n:1-Entitätsbeziehungen mit dem Projektmappen-Explorer](create-edit-1n-relationships-solution-explorer.md)<br />
[Dokumentation für Entwickler: Anpassen von Entitäts- und Attributzuordnungen](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)<br />
[Dokumentation für Entwickler: Erstellen einer neuen Entität aus einer anderen Entität mit der Web-API](/dynamics365/customer-engagement/developer/webapi/create-entity-web-api#create-a-new-entity-from-another-entity)
