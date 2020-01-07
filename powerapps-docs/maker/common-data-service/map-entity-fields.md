---
title: Entitätsfelder zuordnen in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Entitätsfelder zugeordnet werden
ms.custom: ''
ms.date: 05/29/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a5da8b9ecfb2bbba2a4e03fbc0d28301c41e2a7c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860893"
---
# <a name="map-entity-fields"></a>Entitätsfelder zuordnen
 
Sie können Attributen zwischen Entitäten zuordnen, die eine Entitätsbeziehung haben. Hiermit können Sie Standardwerte für einen Datensatz festlegen, der im Kontext eines anderen Datensatzes erstellt wird. 

## <a name="easier-way-to-create-new-records-in-model-driven-apps"></a>Einfacheres Erstellen neuer Datensätze in modellgesteuerten Anwendungen

Angenommen, man möchte einen neuen Kontaktdatensatz für eine Person hinzufügen, die Mitarbeiter einer bestimmten Firma ist. Dies kann auf zweierlei Weise erfolgen:  
  
### <a name="the-hard-way"></a>Auf die umständliche Art

Indem man in der App navigiert, um einen neuen Kontaktdatensatz von Grund auf neu zu erstellen. Dann müssen Sie jedoch die übergeordnete Firma festlegen und verschiedene Informationen (wie etwa Adresse und Telefonnummer) eingeben, die möglicherweise denen der übergeordneten Firma entsprechen. Dies ist oft zeitraubend und fehleranfällig.  
  
### <a name="the-easier-way"></a>Die einfache Möglichkeit

Es ist einfacher, mit der Firmenentität zu beginnen und mittels des Unterrasters **Kontakte** auf dem Formular einfach **+** auszuwählen, um einen Kontakt hinzuzufügen. Sie werden zuerst angeleitet, nach eventuell vorhandenen Kontakten zu suchen, damit Sie nicht versehentlich doppelte Datensätze anlegen. Wenn kein vorhandener Datensatz zu finden ist, wählen Sie **Neu** aus und erstellen einen neuen Kontaktdatensatz. 

Das neue Kontaktformular enthält alle zugeordneten Attributwerte aus der Firma (z.B. Adresse und Telefoninformationen) als Standardwerte. Benutzer können diese Werte bearbeiten, bevor der Datensatz gespeichert wird.

## <a name="how-this-works"></a>So funktioniert's

Wenn Sie Entitätsfelder für eine 1:N-Entitätsbeziehung zuordnen, werden bestimmte Daten aus dem primären Entitätsdatensatz in das neue Entitätsformular kopiert, um Standardwerte festzulegen, die vor dem Speichern bearbeitet werden können.
 
  
> [!NOTE]
> Diese Zuordnungen legen lediglich Standardwerte für einen Datensatz fest, bevor er gespeichert wird. Benutzer können die Werte vor dem Speichern bearbeiten. Die Daten, die übertragen werden, sind die Daten zu dem jeweiligen Zeitpunkt. Es wird nicht synchronisiert, wenn sich die Quelldaten später ändern.
>   
> Diese Zuordnungen werden nicht auf die verknüpften Datensätze angewendet, die mit einem - oder Dialogfeldprozess erstellt wurden. Sie werden nicht automatisch auf neue Datensätze angewendet, die mit Code erstellt wurden, obwohl Entwickler eine spezielle Mitteilung namens `InitializeFrom` ([InitializeFrom Function](/dynamics365/customer-engagement/web-api/initializefrom?view=dynamics-ce-odata-9) oder [InitializeFromRequest Class](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9)) verwenden können, um einen neuen Datensatz mit verfügbaren Zuordnungen zu erstellen.  

## <a name="open-solution-explorer"></a>Öffnen Sie den Lösungs-Explorer

Die einzige Möglichkeit, Entitätsfelder zuzuordnen, ist die Verwendung des Lösungs-Explorers.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
Die Zuordnung von Feldern erfolgt im Kontext einer 1:N oder N:1 Entitätsbeziehung, daher müssen Sie zuerst [1:N oder N:1 Entitätsbeziehungen anzeigen](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships).

## <a name="view-mappable-fields"></a>Zum Zuordnen geeignete Felder anzeigen

Feldzuordnungen werden nicht tatsächlich innerhalb der Entitätsbeziehungen definiert, sondern in der Benutzeroberfläche der Beziehung angezeigt. Nicht jede 1: N-Entitätsbeziehung verfügt über diese. Wenn Sie eine Liste mit 1:n (oder n:1)-Entitätsbeziehungen für eine Entität anzeigen, können Sie die angezeigten Beziehungen nach Typ filtern. Sie können entweder **Alle**, **Benutzerdefiniert**, **Anpassbar** oder **Zum Zuordnen geeignet** auswählen. Zum Zuordnen geeignete Entitätsbeziehungen ermöglichen den Zugriff auf das Zuordnung von Entitätsfeldern. 

![Zum Zuordnen geeignete Entitätsbeziehungen anzeigen](media/mappable-entity-relationships.png) 

Wenn Sie eine zum Zuordnen geeignete Entitätsbeziehung öffnen, wählen Sie **Zuordnungen** in der linken Navigation.

![Zuordnungen für die Entitätsbeziehungen auswählen](media/map-entity-fields-ui-solution-explorer.png)

## <a name="delete-mappings"></a>Zuordnungen löschen

Wenn es Zuordnungen gibt, die Sie nicht anwenden möchten, können Sie diese auswählen und klicken auf die Schaltfläche ![Symbol löschen](media/delete.gif) -Symbol.

## <a name="add-new-mappings"></a>Neue Zuordnungen hinzufügen

Klicken Sie zum Erstellen einer neuen Zuordnung auf **Neu** in der Symbolleiste. Dadurch wird das Dialogfeld **Feldzuordnung erstellen** geöffnet.

![Feldzuordnungsdialog erstellen](media/create-field-mapping-dialog.png)

Wählen Sie ein Quellentitätsfeld und ein Zielentitätsfeld mit Werten ,die Sie zuordnen möchten. 

![Feldzuordnung konfigurieren](media/configure-field-mapping.png)

Klicken Sie auf **OK**, um das Dialogfeld zu schließen.

Die folgenden Regeln zeigen, welche Arten von Daten zugeordnet werden können.  
  
- Beide Felder müssen den gleichen Typ und das gleiche Format aufweisen.  
- Das Zielfeld muss mindestens so lang sein wie das Quellfeld.  
- Das Zielfeld kann nicht einem anderen Feld zugeordnet sein.  
- Das Quellfeld muss im Formular sichtbar sein.  
- Beim Zielfeld muss es sich um ein Feld handeln, in das der Benutzer Daten eingeben kann.  
- Adresskennungswerte können nicht zugeordnet werden.
- Die Zuordnung zu oder von einem Feld, das nicht in einem Formular angezeigt wird, ist nicht möglich. Das Feld muss dem Formular erst hinzugefügt werden.
- Falls es sich bei den Feldern um Optionssätze handelt, müssen die ganzzahligen Werte für jede Option identisch sein.  
  
> [!NOTE]
>  Wenn Sie Optionssatzfelder zuordnen müssen, wird empfohlen, beide Felder für die Verwendung desselben globalen Optionssatzes zu konfigurieren. Andernfalls kann es schwierig sein, zwei verschiedene Sätze von Optionen manuell synchronisiert zu halten. Wenn die ganzzahligen Werte für jede Option nicht richtig zugeordnet sind, können Sie Probleme in Ihren Daten bekommen. Weitere Informationen: [Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service (Auswahllisten)](create-edit-global-option-sets.md)  
  
## <a name="automatically-generate-field-mappings"></a>Automatisches Generieren von Feldzuordnungen  

Sie können Zuordnungen auch automatisch erzeugen, indem Sie **Zuordnungen erzeugen** aus dem Menü **Weitere Aktionen** wählen.

Bei der Verwendung von Systementitäten sollten Sie vorsichtig sein. Verwenden Sie dies, wenn Sie benutzerdefinierte Entitäten erstellen und die Zuordnung verwenden möchten. 

> [!WARNING]
> Dadurch werden alle vorhandenen Zuordnungen entfernt und durch vorgeschlagene Zuordnungen ersetzt, die nur auf den Feldern basieren, die ähnliche Namen und Datentypen haben. Wenn Sie dies für eine Systementität verwenden, können einige erwartete Zuordnungen verloren gehen. Für benutzerdefinierte Entitäten spart dies Zeit, da Sie einfacher Zuordnungen löschen können, die Sie nicht benötigen, und andere hinzufügen können, die die automatische Zuordnungsgenerierung nicht erstellt hat.  


## <a name="publish-customizations"></a>Veröffentlichen von Anpassungen 

Da Feldzuordnungen keine Metadaten sind, müssen Sie sie veröffentlichen, bevor Änderungen wirksam werden. 
<!-- TODO Need a general topic about publishing to link to in situations like this -->

### <a name="see-also"></a>Siehe auch
[Erstellen oder Bearbeiten von 1: N (1: n- oder n: n) Entitätsbeziehungen 1 mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)<br />
[Dokumentation für Entwickler: Anpassen von Entitäten und Attributzuordnungen](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)<br />
[: Dokumentation für Entwickler: Web API Erstellen einer neuen Entität aus einer anderen Entität](/dynamics365/customer-engagement/developer/webapi/create-entity-web-api#create-a-new-entity-from-another-entity)
