---
title: Festlegen von Eigenschaften für ein modellgesteuertes App-Diagramm oder eine Liste in einem Dashboard in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Eigenschaften für ein Diagramm oder eine Liste festlegen, das bzw. die in einem Dashboard enthalten ist.
ms.custom: ''
ms.date: 06/06/2018
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
ms.assetid: 50fb2ab0-5c1a-4a5e-8ebc-5603fecc4da0
caps.latest.revision: 26
ms.author: matp
manager: kvivek
ms.openlocfilehash: c88fef0412060516ef448c89f5ddfdc9cad00e20
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39687681"
---
# <a name="set-properties-for-a-model-driven-app-chart-or-list-included-in-a-dashboard"></a>Festlegen von Eigenschaften für ein modellgesteuertes App-Diagramm oder eine Liste in einem Dashboard

Um eine Diagramm- oder Listenkomponente mit dem Dashboard-Designer zu bearbeiten, wählen Sie das gewünschte Diagramm oder die Liste und dann auf der Symbolleiste des Dashboard-Designers „Komponente bearbeiten“ aus.   

  ![„Komponente bearbeiten“ für ein Diagramm im Dashboard-Designer](media/dashboard-chart-select.png)

Daraufhin wird das Dialogfeld **Eigenschaften festlegen** geöffnet.

  ![„Eigenschaften festlegen“ für ein Diagramm](media/set-properties-chart.png)  
 
Sie können die folgenden Diagrammeigenschaften im Dialogfeld **Eigenschaften festlegen** festlegen:  
  
- **Name**. Eindeutiger Name für das Diagramm. Das System schlägt einen Wert vor, aber Sie können ihn ändern.  
  
- **Beschriftung**. Die Beschriftung, die oben im Diagramm angezeigt wird.  
  
- **Beschriftung auf dem Dashboard anzeigen**. Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die Diagrammbeschriftung ein- oder auszublenden.  
  
- **Entität**. Wählen Sie die Entität (Datensatztyp) als Grundlage für das Diagramm aus. Diese Einstellung bestimmt die verfügbaren Werte für die Eigenschaften „Standardansicht“ und „Standarddiagramm“.  
  
- **Standardansicht**. Wählen Sie die Ansicht aus, die zum Abrufen der Daten für das Diagramm verwendet wird.  
  
- **Standarddiagramm**. Wählen Sie das Standarddiagramm aus, das angezeigt werden soll, wenn das Dashboard zum ersten Mal geöffnet wird. Die verfügbaren Werte werden durch den Wert bestimmt, der für die Eigenschaft „Entität“ festgelegt wurde. Diese Eigenschaft wird zusammen mit der Eigenschaft „Diagrammauswahl anzeigen“ verwendet. Ein Benutzer kann den Typ des Diagramms ändern, wenn die Option **Diagrammauswahl anzeigen** aktiviert ist. Wenn das Dashboard das nächste Mal geöffnet wird, wird das Diagramm jedoch auf das Standarddiagramm zurückgesetzt.  
  
- **Nur Diagramm anzeigen**. Aktivieren Sie dieses Kontrollkästchen, wenn Sie nur das Diagramm anzeigen möchten. Deaktivieren Sie dieses Kontrollkästchen, wenn Sie das Diagramm und die zugehörigen Daten anzeigen möchten.  
  
- **Diagrammauswahl anzeigen**. Aktivieren Sie dieses Kontrollkästchen, damit Benutzer den Typ des Diagramms (Säule, Balken, Kreis usw.) ändern können, wenn sie das Dashboard verwenden. Wenn der Benutzer den Typ des Diagramms ändert, werden die Einstellungen nicht gespeichert. Der Diagrammtyp wird auf die Einstellung für „Standarddiagramm“ zurückgesetzt, wenn das Dashboard geschlossen wird.  
  
Sie können die folgenden Listeneigenschaften im Dialogfeld **Eigenschaften festlegen** festlegen:  
  
- **Name**. Eindeutiger Name für die Liste. Das System schlägt einen Wert vor, aber Sie können ihn ändern.  
  
- **Beschriftung**. Die Beschriftung, die oben in der Liste angezeigt wird.  
  
- **Beschriftung auf dem Dashboard anzeigen**. Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die Listenbeschriftung ein- oder auszublenden.  
  
- **Entität**. Wählen Sie die Entität (Datensatztyp) als Grundlage für die Liste aus. Diese Einstellung bestimmt die verfügbaren Werte für die Eigenschaft „Standardansicht“.  
  
- **Standardansicht**. Wählen Sie die Ansicht aus, die zum Abrufen der Daten in der Liste verwendet wird. Ein Benutzer kann die Ansicht ändern, aber wenn das Dashboard das nächste Mal geöffnet wird, wird die Liste auf die Standardansicht zurückgesetzt.  
  
- **Suchfeld anzeigen**. Aktivieren Sie dieses Kontrollkästchen, wenn oben in der Liste ein Suchfeld angezeigt werden soll. Wenn das Suchfeld enthalten ist, können Sie oder andere Benutzer zur Laufzeit nach Datensätzen in der Liste suchen.  
  
- **Index anzeigen**. Aktivieren Sie dieses Kontrollkästchen, wenn unten in der Liste A-bis-Z-Filter angezeigt werden sollen. Wenn die A-bis-Z-Filter angezeigt werden, können Sie oder andere Benutzer einen Buchstaben auswählen, um zu Datensätzen zu springen, die mit diesem Buchstaben beginnen.  
  
- **Ansichtsauswahl**. Wählen Sie einen der folgenden Werte aus:  
  
    - **Aus**. Die Ansichtsauswahl wird nicht angezeigt. Sie oder andere Benutzer können Ansichten zur Laufzeit nicht ändern.  
  
    - **Alle Ansichten anzeigen**. Stellen Sie eine vollständige Liste der Ansichten bereit, die mit dem in der Eigenschaft „Entität“ festgelegten Wert verknüpft sind.  
  
    - **Ausgewählte Ansichten anzeigen**. Wählen Sie diese Einstellung aus, um die Liste der Ansichten zu beschränken, die zur Laufzeit verfügbar sind. Um die jeweiligen anzuzeigenden Ansichten auszuwählen, halten Sie die STRG-Taste gedrückt, und tippen Sie auf die gewünschten Ansichten, oder wählen Sie sie aus.  
 
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen oder Anpassen von Dashboards](create-edit-dashboards.md)
