---
title: Entitäten und Metadaten in Common Data Service | Microsoft-Dokumentation
description: Weitere Informationen über Entitäten und Metadaten in Common Data Service
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 88b18946-474c-4c94-8e4c-27532f930757
caps.latest.revision: 28
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3aeb07c29178570ca17426cca46dd7cbc73a2aca
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108282"
---
# <a name="entities-and-metadata-in-common-data-service"></a>Entitäten und Metadaten in Common Data Service

Common Data Service wurde entworfen, damit Sie ein Datenmodell für Ihre Anwendung schnell und einfach erstellen können. Normalerweise sollten Sie sich nicht mit einigen der Informationen zu Metadaten befassen müssen, die in diesem Thema vorstellt werden. Wenn Sie jedoch besser verstehen möchten, wie Apps, die Common Data Service verwenden, funktionieren, oder wenn Sie die Möglichkeiten auswerten möchten, kann das Verständnis der Metadaten, die von Common Data Service verwendet werden, Ihnen entsprechende Erkenntnisse vermitteln.

*Metadaten* bedeutet Daten über Daten. Common Data Service bietet eine flexible Plattform für Sie, da es relativ einfach ist, die Definitionen der Daten zu bearbeiten, die von der Umgebung verwendet werden. In Common Data Service sind die Metadaten eine Sammlung von Entitäten. Entitäten beschreiben die Arten von Daten, die in der Datenbank gespeichert werden.  Jede Entität entspricht einer Datenbanktabelle, und jedes Feld (auch als Attribut bezeichnet) in einer Entität stellt eine Spalte in dieser Tabelle dar. Entitätsmetadaten sind die Daten, die steuern, welche Arten von Datensätzen Sie erstellen und welche Arten von Aktionen dafür durchgeführt werden können. Wenn Sie die Anpassungstools verwenden, um Entitäten, Felder oder Entitätsbeziehungen erstellen oder bearbeiten, bearbeiten Sie diese Metadaten. 
  
Verschiedene Clients, mit denen Benutzer mit den Daten in Ihrer Umgebung interagieren, hängen von den Entitätsmetadaten ab und passen sich an, wenn Sie die Metadaten anpassen. Aber diese Clients hängen auch von anderen Daten ab, um zu steuern, welche visuellen Elemente angezeigt werden, welche benutzerdefinierte Logik angewendet wird und wie die Sicherheit geregelt werden soll. Diese Systemdaten werden auch in Entitäten gespeichert, die Entitäten selbst können jedoch nicht angepasst werden.

Sie können mehr über Standardentitäten, -attribute und Entitätsbeziehungen erfahren, die standardmäßig in Common Data Service enthalten sind, indem Sie die [Entitätsreferenz](/powerapps/developer/common-data-service/reference/about-entity-reference) überprüfen.

> [!TIP]
> Die Designer, die zum Bearbeiten der Metadaten verfügbar sind, können nicht alle Details anzeigen, die in den Metadaten gefunden werden. Sie können eine modellgesteuerte App mit dem Namen **Browser für Metadaten** installieren, die es Ihnen ermöglicht, alle Entitäten- und Metadateneigenschaften anzuzeigen, die im System vorhanden sind. Weitere Informationen: [Durchsuchen der Metadaten für die Umgebung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/browse-your-metadata).
  
<a name="BKMK_CreateNewOrUseExistingMetadata"></a>

## <a name="create-new-metadata-or-use-existing-metadata"></a>Neue Metadaten erstellen oder vorhandene nutzen?

Common Data Service verfügt über einige Standardentitäten, die Kernfähigkeiten von Geschäftsanwendungen unterstützen. So sollen beispielsweise Daten zu Ihren Kunden oder potenziellen Kunden mit den Entitäten Firma oder Kontakt gespeichert werden.  
  
Jede dieser Entitäten enthält auch eine Reihe von Feldern, die allgemeine Daten repräsentieren, die das System möglicherweise für die jeweilige Entität speichern muss.  
  
Für die meisten Organisationen ist es von Vorteil, die zu Standardentitäten und Attribute für die Zwecke zu verwenden, für die diese bereitgestellt wurden. 
  
Wenn Sie eine Lösung installieren, können Sie erwarten, dass der Lösungsentwickler die Standardentitäten und Attribute genutzt hat. Das Erstellen einer neuen benutzerdefinierten Entität, die eine Systementität oder ein Attribut ersetzt, kann bedeuten, dass verfügbare Lösungen nicht mehr für Ihre Organisation funktionieren.  
  
Daher wird empfohlen, die bereitgestellten Standardentitäten und Felder und Entitätsbeziehungen zu suchen und verwenden, wenn diese für Ihre Organisation sinnvoll sind. Wenn dies nicht der Fall ist, und sie nicht an Ihre Anforderungen angepasst werden könnten, sollten Sie prüfen, ob das Erstellen einer neuen Entität, einem neuen Feld oder einer neuen Entitätsbeziehung erforderlich ist. 

<!--  Can we say this yet? 
    
> [!NOTE]
> The [Common Data Model](/powerapps/common-data-model/overview) will provide a capability to add additional standard entities. 

-->

Denken Sie daran, dass Sie den Anzeigenamen einer Entität an die Benennungsstandards Ihrer Organisation anpassen können. Beispielsweise ist es sehr verbreitet, dass Benutzer den Anzeigenamen der Firmenentität zu *Unternehmen* oder den Namen der Kontaktentität zu *Person* ändern. Das kann mit Entitäten oder Attributen ausgeführt werden, ohne dass das Verhalten der Entität geändert wird. Weitere Informationen zum Umbenennen von Entitäten finden Sie unter [Den Namen einer Entität ändern](edit-entities.md#change-the-name-of-an-entity).
  
Sie können Standardentitäten, Felder oder Entitätsbeziehungen nicht löschen. Diese gelten als Teil der Systemlösung ,und jede Organisation muss über sie verfügen. Wenn eine Standardentität ausblenden möchten, ändern Sie die Sicherheitsrollenberechtigungen für Ihre Organisation, um die Leseberechtigung für diese Entität zu entfernen. Dadurch wird die Entität aus den meisten Teilen der Anwendung entfernt. Wenn Sie ein Systemfeld nicht benötigen, entfernen Sie es aus dem Formular und allen Ansichten, die dieses verwenden. Ändern Sie den Wert **Durchsuchbar** in den Feld- und Entitätsbeziehungsdefinition, damit sie nicht in der erweiterten Suche angezeigt werden. 
  
<a name="BKMK_LimitationsOnMetadata"></a>   

## <a name="limitations-on-creating-metadata-items"></a>Einschränkungen beim Erstellen von Metadatenelementen  

Es gibt eine Grenze bei der Anzahl von Entitäten, die Sie erstellen können. Sie finden Informationen über die Höchstzahl auf der Seite **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Administration** > **Verwendete Ressourcen**. Wenn Sie mehr benutzerdefinierte Entitäten benötigen, wenden Sie sich an den technischen Support. Diese Obergrenze kann angepasst werden.  
  
Für jede Entität gibt es eine Obergrenze für die Anzahl von Feldern, die Sie erstellen können. Diese Beschränkung basiert auf den technischen Einschränkungen zum Datenvolumen, das in einer Zeile einer Datenbanktabelle gespeichert werden kann. Eine genaue Zahl lässt sich nicht angeben, da jede Feldart einen bestimmten Platz einnimmt. Die Obergrenze hängt von dem Gesamtplatz ab, den alle Felder für die Entität beanspruchen.  
  
Die meisten Benutzer erreichen diese Obergrenze nicht, wenn Sie jedoch planen, einer Entität Hunderte benutzerdefinierter Felder hinzuzufügen, sollten Sie darüber nachdenken, ob dies die beste Lösung ist. Beschreiben alle geplanten Felder Eigenschaften eines Datensatzes für diese Entität? Erwarten Sie wirklich, dass Personen, die Ihre Organisation verwenden, ein Formular mit einer derart großen Menge von Feldern handhaben können? Die Anzahl von Feldern, die Sie einem Formular hinzufügen, erhöht die Menge der Daten, die bei jeder Bearbeitung des Formulars übertragen wird und wirkt sich so auf die Leistung des Systems aus. Berücksichtigen Sie diese Faktoren, wenn Sie einer Entität benutzerdefinierte hinzufügen.  
  
Optionssatzfelder bieten eine Reihe von Optionen, die in einer Dropdownliste in einem Formular oder bei Verwendung der erweiterten Suche in einer Auswahlliste angezeigt werden. Ihre Umgebung kann in einem Optionssatz Tausende von Optionen unterstützen, Sie sollten dies jedoch nicht als die Obergrenze erwägen. Benutzerfreundlichkeitsstudien haben gezeigt, dass Benutzer Schwierigkeiten mit der Verwendung eines Systems haben, in dem eine Dropdownliste zu viele Optionen anzeigt. Verwenden Sie Optionssatzfelder zur Definition der Kategorien für Daten. Verwenden Sie sie nicht zur Auswahl von Kategorien, die separate Datenelemente repräsentieren. Verwenden Sie beispielsweise nicht ein Optionssatzfeld, das Hunderte möglicher Hersteller eines bestimmten Geräts enthält; erstellen Sie stattdessen eine Entität mit Verweisen zu jedem Hersteller und ein Suchfeld anstelle eines Optionssatzes.  
  
## <a name="next-steps"></a>Nächste Schritte 

[Erstellen oder Bearbeiten von Entitäten (Datensatztypen)](create-edit-entities.md)<br />
[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)

