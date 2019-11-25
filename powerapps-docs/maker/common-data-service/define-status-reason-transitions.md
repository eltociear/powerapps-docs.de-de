---
title: Statusgrundübergänge festlegen mit PowerApps | Microsoft-Dokumentation
description: Statusgrundübergänge definieren
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: dbc4f436-0b23-42f9-8079-b0de482aaebe
caps.latest.revision: 11
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9fb1fc93b5559c47cebeef4fb73ebd095a48f0a5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705577"
---
# <a name="define-status-reason-transitions-for-the-case-or-custom-entities"></a>Festlegen von Statusgrundübergängen für Anfrage- oder benutzerdefinierte Entitäten

Sie können für die (**Case**) Vorfallentität eine benutzerdefinierte Entitäte angeben.

> [!NOTE]
> Obwohl die Entität Vorfall (Anfrage) nicht in einer Standardumgebung von Common Data Service enthalten ist, wird diese von [Dynamics 365 for Customer Service](https://dynamics.microsoft.com/customer-service/) verwendet und im [Common Data Model](https://github.com/Microsoft/CDM/blob/master/schemaDocuments/core/applicationCommon/foundationCommon/crmCommon/service/Incident.cdm.json) definiert.
  
Statusgrundübergänge stellen eine optionale zusätzliche Filterebene dar, um zu definieren, in was der Statusgrundwert für die einzelnen Statusgründe geändert werden kann. Die Definition einer begrenzten Liste von gültigen Optionen kann es für Benutzer einfacher machen, den korrekten nächsten Statusgrund für einen Datensatz auszuwählen, wenn es eine große Zahl von Kombinationen für gültige Statusgrundwerte gibt.  
  
<a name="BKMK_StatusAndStatusReasons"></a>

## <a name="what-is-the-connection-between-status-and-status-reason-fields"></a>Was ist die Verbindung zwischen den Feldern für den Status und den Statusgrund?  

Entitäten, die über verschiedene Statuswerte verfügen können, verfügen über zwei Felder, die diese Daten erfassen:  
  
|Anzeigename|Beschreibung|  
|------------------|-----------------|  
|**Status**|Stellt den Status des Datensatzes dar. In der Regel **Aktiv** oder **Inaktiv**. Sie können keine neuen Statusoptionen hinzufügen.|  
|**Statusgrund**|Stellt einen Grund dar, der mit einem bestimmten Status verknüpft ist. Jeder Status muss mindestens einen möglichen Statusgrund haben. Sie können zusätzliche Statusgrundoptionen hinzufügen.|  
  
Die Metadaten für das Feld definieren, welche Werte für einen bestimmten Status gültig sind. Beispielsweise sind für die Vorfall-Entität (**Anfrage**) die Standardoptionen für Status und Statusgrund:  
  
|Status|Statusgrund|  
|------------|-------------------|  
|**Aktiv**|<li>**In Bearbeitung**</li><li>**Zurückgestellt**</li><li>**Warten auf Details**</li><li>**Recherche**</li>| 
|**Behoben**|<li>**Problem behoben**</li><li>**Bereitgestellte Informationen**</li>|
|**Storniert**|<li>**Storniert**</li><li>**Zusammengeführt**</li>|
  
  
<a name="BKMK_EditStatusReasonTransitions"></a>   

## <a name="edit-status-reason-transitions"></a>Bearbeiten von Statusgrundübergängen
 
Sie können die Optionen für das Statusgrundfeld für die Entität Case (Fall) und angepasste Entitäten modifizieren, um zu definieren, welche weiteren Statusgrundoptionen gewählt werden können. Die einzige Beschränkung besteht darin, dass jede Statusgrundoption für einen aktiven Status mindestens einen Pfad zu einem inaktiven Status zulassen muss. Andernfalls könnten Sie einen Zustand schaffen, in dem der Fall weder gelöst noch abgebrochen werden kann.  

> [!NOTE]
> Die Bearbeitung der Statusgrundübergänge erfordert die Verwendung des Projektmappen-Explorers. Weitere Informationen zum Bearbeiten von Feldern finden Sie unter [Erstellen und Bearbeiten von Feldern für Common Data Service mit PowerApps-Lösungs-Explorer](create-edit-field-solution-explorer.md).
  
 Wenn Sie ein Feld "Statusgrund" bearbeiten, ist die Schaltfläche **Statusgrund-Übergänge bearbeiten** im Menü. 

![Statusgrundübergänge-Befehl bearbeiten](media/status-reason-transitions-command.png)

Wenn Sie auf diese Schaltfläche klicken, stellt das **Statusgrund-Übergange**-Dialogfeld die Option zum Auswählen von **Statusgrund-Übergänge aktivieren** bereit. Wenn diese Option ausgewählt ist, müssen Sie definieren, welche *anderen* Statusgrundwerte für jeden Statusgrund zulässig sind. Um die angewendeten Filter zu entfernen, löschen Sie die Auswahl **Statusgrund-Übergäng eaktivieren**. Die Übegänge, die Sie definiert haben, bleiben gespeichert, werden jedoch nicht angewendet.  
  
Im folgenden Screenshot sehen Sie ein Beispiels, das die folgenden Anforderungen erfüllt: 
 
- Eine Anfrage kann jederzeit zusammengeführt werden. Sie können Anfragen nicht zusammenzuführen, wenn ein Statusgrundübergang dies nicht zulässt.  
- Eine aktive Anfrage kann jederzeit abgebrochen werden.  
- Eine abgeschlossene oder abgebrochene Anfrage kann nicht erneut aktiviert werden.  
- Alle Anfragen nach müssen folgende Phasen durchlaufen: **In Bearbeitung** > **Zurückgestellt** > **Warten auf Details** > **Recherche**, bevor sie aufgelöst werden können. Mit dieser Konfiguration kann eine Anfrage nicht auf einen früheren Status festgelegt werden.  
  > [!NOTE]
  >  Dies ist kein gutes Beispiel für wirkliches Arbeiten, aber es zeigt, wie Phasen von Status durch Statusgrundübergänge erzwungen werden können.  
  
 ![Beispiel für Statusgrundübergängen für Anfrage](media/status-reason-transitions-example.PNG)  
  
### <a name="see-also"></a>Siehe auch  

[Erstellen und Bearbeiten von Feldern für Common Data Service mithilfe des PowerApps-Projektmappen-Explorers](create-edit-field-solution-explorer.md)<br />
[Entitätsmetadaten > Entitätsstatus](/powerapps/developer/common-data-service/entity-metadata#entity-states)<br />
[Definieren von benutzerdefinierten Statusmodellübergängen](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

