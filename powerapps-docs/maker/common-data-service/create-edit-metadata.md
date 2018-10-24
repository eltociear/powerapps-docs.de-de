---
title: Entitäten und Metadaten in Common Data Service für Apps | Microsoft-Dokumentation
description: Hier erhalten Sie Informationen zu Entitäten und Metadaten in Common Data Service für Apps.
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 88b18946-474c-4c94-8e4c-27532f930757
caps.latest.revision: 28
ms.author: matp
manager: kvivek
ms.openlocfilehash: ef2f92865205fa7c97ada356edc70ac69a637e0f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689746"
---
# <a name="entities-and-metadata-in-common-data-service-for-apps"></a>Entitäten und Metadaten in Common Data Service für Apps

Mit Common Data Service für Apps (CDS für Apps) können Sie ganz schnell und einfach ein Datenmodell für Ihre Anwendung erstellen. Üblicherweise müssen Sie sich mit den Details der Metadaten nicht beschäftigen, die in diesem Thema vorgestellt werden. Wenn Sie jedoch genauer wissen möchten, wie Apps funktionieren, die CDS für Apps verwenden, oder wenn Sie die damit einhergehenden Möglichkeiten eruieren möchten, sind Kenntnisse der von CDS für Apps verwendeten Metadaten nützlich.

*Metadaten* sind ganz einfach Daten über Daten. CDS für Apps bietet Ihnen eine flexible Plattform, da es relativ einfach ist, die Definitionen der Daten zu bearbeiten, die von der Umgebung verwendet werden. In CDS für Apps sind die Metadaten eine Sammlung von Entitäten. Entitäten beschreiben die Arten der Daten, die in der Datenbank gespeichert sind.  Jede Entität entspricht einer Datenbanktabelle, und jedes Feld (auch als Attribut bezeichnet) innerhalb einer Entität stellt eine Spalte in dieser Tabelle dar. Mit Entitätsmetadaten wird gesteuert, welche Arten von Datensätzen Sie erstellen können und welche Arten von Aktionen mit diesen ausgeführt werden können. Wenn Sie die Anpassungstools verwenden, um Entitäten, Felder und Entitätsbeziehungen zu erstellen oder zu bearbeiten, bearbeiten Sie diese Metadaten. 
  
Die verschiedenen Clients, die von Benutzern für die Interaktion mit den Daten in Ihrer Umgebung verwendet werden, benötigen die Entitätsmetadaten und passen sich an geänderte Metadaten an. Diese Clients benötigen aber auch andere Daten, um zu steuern, welche visuellen Elemente angezeigt werden sollen, welche benutzerdefinierte Logik angewendet werden soll und welche Sicherheitsfunktionen genutzt werden sollen. Diese Systemdaten werden auch in Entitäten gespeichert, die Entitäten selbst können aber nicht angepasst werden.

Weitere Informationen über Entitäten, Attribute und Entitätsbeziehungen, die von CDS für Apps standardmäßig eingeschlossen werden, finden Sie in der [Entitätsreferenz](/powerapps/developer/common-data-service/reference/about-entity-reference).

> [!TIP]
> Die Designer, mit denen Sie Metadaten bearbeiten können, können nicht alle Informationen anzeigen, die in den Metadaten gefunden werden. Sie können eine modellgesteuerte App namens **Metadata Browser** installieren, über die Sie alle Eigenschaften von Entitäten und Metadaten abrufen können, die im System gefunden werden. Weitere Informationen finden Sie unter [Durchsuchen der Metadaten für die Organisation](https://docs.microsoft.com/dynamics365/customer-engagement/developer/browse-your-metadata).
  
<a name="BKMK_CreateNewOrUseExistingMetadata"></a>

## <a name="create-new-metadata-or-use-existing-metadata"></a>Erstellen neuer Metadaten oder Verwenden vorhandener Metadaten?

CDS für Apps enthält eine Reihe von Standardentitäten, die grundlegende Funktionen für Geschäftsanwendungen unterstützen. Daten zu Ihren Kunden oder potenziellen Kunden sollten beispielsweise mithilfe der Entitäten „Account“ oder „Contact“ gespeichert werden.  
  
Jede dieser Entitäten enthält auch eine Reihe von Feldern, die gemeinsame Daten repräsentieren und die vom System möglicherweise für die jeweilige Entität gespeichert werden müssen.  
  
In den meisten Organisationen ist es von Vorteil, die Standardentitäten und -attribute für die Zwecke zu verwenden, für die sie bereitgestellt wurden. 
  
Wenn Sie eine Lösung installieren, können Sie davon ausgehen, dass der Lösungsentwickler die Standardentitäten und -attribute verwendet hat. Die Erstellung einer neuen, benutzerdefinierten Entität, die eine Systementität oder ein Systemattribut ersetzt, bedeutet, dass verfügbare Lösungen möglicherweise für Ihre Organisation nicht funktionieren.  
  
Aus diesen Gründen empfiehlt es sich, die standardmäßigen Entitäten, Felder und Entitätsbeziehungen zu suchen und zu verwenden, wenn sie für Ihre Organisation sinnvoll sind. Wenn sie nicht sinnvoll sind und nicht an Ihre Anforderungen angepasst werden können, sollten Sie überprüfen, ob die Erstellung neuer Entitäten, Felder oder Entitätsbeziehungen erforderlich ist. 

<!--  Can we say this yet? 
    
> [!NOTE]
> The [Common Data Model](/powerapps/common-data-model/overview) will provide a capability to add additional standard entities. 

-->

Denken Sie daran, dass Sie den Anzeigenamen einer Entität ändern können, sodass sie in die Nomenklatur Ihrer Organisation passt. Beispielsweise kommt es sehr häufig vor, dass der Anzeigename der Entität „Account“ zu *Unternehmen* oder der Name der Entität „Contact“ zu *Person* geändert wird. Diese Änderungen können für Entitäten und Attribute durchgeführt werden, ohne dass sich das Verhalten der Entität ändert. Weitere Informationen zum Umbenennen von Entitäten finden Sie unter [Ändern des Namens einer Entität](edit-entities.md#change-the-name-of-an-entity).
  
Sie können standardmäßige Entitäten, Felder oder Entitätsbeziehungen nicht löschen. Diese sind Teil der Systemlösung, und jede Organisation muss über sie verfügen. Wenn Sie eine Standardentität verbergen möchten, ändern Sie die Berechtigungen der Sicherheitsrolle für Ihre Organisation, sodass die Leseberechtigung für diese Entität entfernt wird. Damit wird die Entität aus den meisten Teilen der Anwendung entfernt. Wenn Sie ein Systemfeld nicht benötigen, entfernen Sie es aus dem Formular und allen Ansichten, die dieses verwenden. Ändern Sie den Wert **Searchable** in den Definitionen für Feld und Entitätsbeziehung, sodass diese bei erweiterten Suchvorgängen nicht angezeigt werden. 
  
<a name="BKMK_LimitationsOnMetadata"></a>   

## <a name="limitations-on-creating-metadata-items"></a>Einschränkungen beim Erstellen von Metadatenelementen  

Sie können nur eine begrenzte Anzahl von Entitäten erstellen. Informationen zur maximalen Anzahl finden Sie auf der Seite **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Verwaltung** > **Verwendete Ressourcen**. Wenn Sie weitere benutzerdefinierte Entitäten benötigen, wenden Sie sich an den technischen Support. Die Obergrenze kann angepasst werden.  
  
Innerhalb von Entitäten kann nur eine begrenzte Anzahl von Feldern erstellt werden. Dieser Grenzwert basiert auf den technischen Einschränkungen in Bezug auf die Menge der Daten, die in einer Zeile einer Datenbanktabelle gespeichert werden können. Ein genauer Wert lässt sich nur schwer beziffern, weil jede Art von Feld eine unterschiedliche Menge an Speicherplatz verwenden kann. Die Obergrenze hängt von dem Speicherplatz ab, der insgesamt von allen Feldern für die Entität verwendet wird.  
  
In den meisten Fällen werden nicht so viele benutzerdefinierte Felder erstellt, dass der Grenzwert erreicht wird. Wenn Sie aber planen, einer Entität Hunderte von benutzerdefinierten Feldern hinzuzufügen, sollten Sie überprüfen, ob dies der optimale Entwurf ist. Beschreiben alle Felder, die Sie planen, Eigenschaften für einen Datensatz für diese Entität? Können Sie wirklich davon ausgehen, dass alle Benutzer in Ihrer Organisation in der Lage sein werden, mit einem Formular umzugehen, dass eine so hohe Anzahl von Feldern umfasst? Die Anzahl von Feldern, die Sie einem Formular hinzufügen, erhöht die Menge an Daten, die bei jeder Bearbeitung eines Datensatzes übertragen werden müssen, und wirkt sich auf die Leistung des Systems aus. Berücksichtigen Sie diese Faktoren, wenn Sie einer Entität benutzerdefinierte Felder hinzufügen.  
  
Felder mit Optionssätzen enthalten Optionen, die auf einem Formular in einem Dropdown-Steuerelement oder bei einer erweiterten Suche in einem Auswahllisten-Steuerelement angezeigt werden. Ihre Umgebung kann Tausende von Optionen in einem Optionssatz unterstützen – Sie sollten diese Obergrenze aber nicht ausreizen. Studien zur Benutzerfreundlichkeit belegen, dass Benutzer Probleme haben, ein System zu verwenden, in dem Dropdown-Steuerelemente sehr viele Optionen enthalten. Verwenden Sie Felder für Optionssätze, um Kategorien für Daten zu definieren. Verwenden Sie diese Felder nicht zur Auswahl von Kategorien, die tatsächlich separate Datenelemente repräsentieren. Ein Beispiel: Anstatt ein Optionssatzfeld zu verwenden, das jeweils Hunderte von möglichen Herstellern eines bestimmten Produkts speichert, erstellen Sie lieber eine Entität, die Verweise auf jeden Hersteller speichert, und verwenden ein Nachschlagefeld anstelle eines Optionssatzes.  
  
## <a name="next-steps"></a>Nächste Schritte 

[Erstellen oder Bearbeiten von Entitäten (Datensatztypen)](create-edit-entities.md)<br />
[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)

