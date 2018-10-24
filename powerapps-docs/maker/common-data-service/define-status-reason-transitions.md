---
title: Definieren von Statusgrundübergängen mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Statusgrundübergänge definieren
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: dbc4f436-0b23-42f9-8079-b0de482aaebe
caps.latest.revision: 11
ms.author: matp
manager: kvivek
ms.openlocfilehash: e21069a86d2ef21e8209fea6ea4a4b05e604cda4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39686641"
---
# <a name="define-status-reason-transitions-for-the-case-or-custom-entities"></a>Definieren von Statusgrundübergängen für Anfrageentitäten oder benutzerdefinierte Entitäten

Sie können für die Vorfallsentität (**Anfrage**) oder eine benutzerdefinierte Entität Statusgrundübergänge angeben.

> [!NOTE]
> Obwohl die Vorfallsentität (Anfrage) nicht in der Standardumgebung des Common Data Service für Apps enthalten ist, wird diese von [Dynamics 365 für Customer Service](https://dynamics.microsoft.com/customer-service/) verwendet und im [allgemeinen Datenmodell](https://github.com/Microsoft/CDM/blob/master/schemaDocuments/core/applicationCommon/foundationCommon/crmCommon/service/Incident.cdm.json) definiert.
  
Statusgrundübergänge stellen eine optionale zusätzliche Filterebene dar, um zu definieren, in was der Statusgrundwert für die einzelnen Statusgründe geändert werden kann. Die Definition einer begrenzten Liste von gültigen Optionen kann es für Benutzer einfacher machen, den korrekten nächsten Statusgrund für einen Datensatz auszuwählen, wenn es eine große Zahl von Kombinationen für gültige Statusgrundwerte gibt.  
  
<a name="BKMK_StatusAndStatusReasons"></a>

## <a name="what-is-the-connection-between-status-and-status-reason-fields"></a>Was ist die Verbindung zwischen den Feldern für den Status und dem Statusgrund?  

Entitäten, die über verschiedene Statuswerte verfügen können, haben zwei Felder, die diese Daten erfassen:  
  
|Anzeigename|Beschreibung|  
|------------------|-----------------|  
|**Status**|Stellt den Status des Datensatzes dar. In der Regel **Aktiv** oder **Inaktiv**. Sie können keine neuen Statusoptionen hinzufügen.|  
|**Statusgrund**|Stellt einen Grund dar, der mit einem bestimmten Status verknüpft ist. Jeder Status muss mindestens einen möglichen Statusgrund haben. Sie können zusätzliche Statusgrundoptionen hinzufügen.|  
  
Die Metadaten für das Feld definieren, welche Werte für einen bestimmten Status gültig sind. Beispielsweise sind für die Vorfallsentität (**Anfrage**) die Standardoptionen für Status und Statusgrund:  
  
|Status|Statusgrund|  
|------------|-------------------|  
|**Aktiv**|<li>**In Bearbeitung**</li><li>**Zurückgestellt**</li><li>**Warten auf Details**</li><li>**Recherche**</li>| 
|**Behoben**|<li>**Problem behoben**</li><li>**Informationen bereitgestellt**</li>|
|**Storniert**|<li>**Storniert**</li><li>**Zusammengeführt**</li>|
  
  
<a name="BKMK_EditStatusReasonTransitions"></a>   

## <a name="edit-status-reason-transitions"></a>Bearbeiten von Statusgrundübergängen
 
Sie können die Optionen für das Statusgrundfeld für die Anfrageentität und benutzerdefinierte Entitäten modifizieren, um zu definieren, welche weiteren Statusgrundoptionen gewählt werden können. Die einzige Beschränkung besteht darin, dass jede Statusgrundoption für einen aktiven Status mindestens einen Pfad zu einem inaktiven Status zulassen muss. Andernfalls könnten Sie einen Zustand schaffen, in dem die Anfrage weder gelöst noch storniert werden kann.  

> [!NOTE]
> Die Bearbeitung der Statusgrundübergänge erfordert die Verwendung des Projektmappen-Explorers. Weitere Informationen zum Bearbeiten von Feldern finden Sie unter [Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit dem PowerApps-Projektmappen-Explorer](create-edit-field-solution-explorer.md).
  
 Wenn Sie ein Feld „Statusgrund“ bearbeiten, finden Sie die Schaltfläche **Statusgrundübergänge bearbeiten** im Menü. 

![Befehl „Statusgrundübergänge bearbeiten“](media/status-reason-transitions-command.png)

Wenn Sie auf diese Schaltfläche klicken, stellt das **Statusgrundübergange** die Option zum Auswählen von **Statusgrundübergänge aktivieren** bereit. Wenn diese Option ausgewählt ist, müssen Sie definieren, welche *anderen* Statusgrundwerte für jeden Statusgrund zulässig sind. Um die angewendeten Filter zu entfernen, löschen Sie die Auswahl **Statusgrundübergänge aktivieren**. Die Übergänge, die Sie definiert haben, bleiben gespeichert, werden jedoch nicht angewendet.  
  
Im folgenden Screenshot sehen Sie ein Beispiels, das die folgenden Anforderungen erfüllt: 
 
- Eine Anfrage kann jederzeit zusammengeführt werden. Sie können Anfragen nicht zusammenzuführen, wenn ein Statusgrundübergang dies nicht zulässt.  
- Eine aktive Anfrage kann jederzeit storniert werden.  
- Eine abgeschlossene oder storniert Anfrage kann nicht erneut aktiviert werden.  
- Alle Anfragen nach müssen folgende Phasen durchlaufen: **In Bearbeitung** > **Zurückgestellt** > **Warten auf Details** > **Recherche**, bevor sie aufgelöst werden können. Mit dieser Konfiguration kann eine Anfrage nicht auf einen früheren Status festgelegt werden.  
  > [!NOTE]
  >  Dies ist kein gutes Beispiel für wirkliches Arbeiten, aber es zeigt, wie Phasen von Status durch Statusgrundübergänge erzwungen werden können.  
  
 ![Beispiel für Statusgrundübergänge für eine Anfrage](media/status-reason-transitions-example.PNG)  
  
### <a name="see-also"></a>Siehe auch  

[Erstellen und Bearbeiten von Feldern für Common Data Service für Apps mit dem PowerApps-Projektmappen-Explorer](create-edit-field-solution-explorer.md)<br />
[Entitätsmetadaten > Entitätsstatus](/powerapps/developer/common-data-service/entity-metadata#entity-states)<br />
[Definieren von benutzerdefinierten Statusmodellübergängen](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

