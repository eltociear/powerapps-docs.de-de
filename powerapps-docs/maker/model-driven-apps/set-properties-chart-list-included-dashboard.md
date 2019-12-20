---
title: Festlegen von Eigenschaften für ein Diagramm oder eine Liste in einer modellgesteuerten App, die in einem Dashboard enthalten sind, in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Eigenschaften für ein Diagramm oder eine Liste, die in einem Dashboard enthalten sind, festgelegt werden
ms.custom: ''
ms.date: 06/06/2018
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
ms.assetid: 50fb2ab0-5c1a-4a5e-8ebc-5603fecc4da0
caps.latest.revision: 26
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 46861b569be4140ca2ac66d016285930c5d9fc31
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862838"
---
# <a name="set-properties-for-a-model-driven-app-chart-or-list-included-in-a-dashboard"></a>Festlegen von Eigenschaften für ein Diagramm oder eine Liste in einer modellgesteuerten App, die in einem Dashboard enthalten sind

Um ein Diagramm oder eine Listenkomponente im Dashboard-Designer zu bearbeiten, wählen Sie das gewünschte Diagramm oder die gewünschte Liste aus und wählen Sie dann Komponente bearbeiten in der Symbolleiste des Dashboard-Designers.   
  > [!div class="mx-imgBorder"] 
  > ![Komponente zum Bearbeiten von Diagrammen im Dashboard-Designer](media/dashboard-chart-select.png)

Das Dialogfeld **Eigenschaften festlegen** wird dadurch geöffnet.

  > [!div class="mx-imgBorder"] 
  > ![Diagrammeigenschaften festlegen](media/set-properties-chart.png)  
 
Sie können die folgenden Diagrammeigenschaften aus dem **Eigenschaften festlegen**-Dialogfeld festlegen:  
  
- **Name** Eindeutiger Name für das Diagramm. Vom System wird ein Wert vorgeschlagen, aber Sie können ihn ändern.  
  
- **Bezeichnung**: Die Bezeichnung, die am oberen Rand des Diagramms angezeigt wird.  
  
- **Beschriftung im Dashboard anzeigen**: Aktivieren oder deaktivieren Sie dieses Kontrollkästchen zum Ein- oder Ausblenden der Diagrammbeschriftung.  
  
- **Entität**: Wählen Sie die Entität (Datensatztyp), auf dem das Diagramm basieren soll. Diese Einstellung bestimmt die verfügbaren Werte für die Eigenschaften "Standardansicht" und "Standarddiagramm".  
  
- **Standardansicht**: Wählen Sie die Ansicht aus, die zum Abrufen der Daten für das Diagramm verwendet wird.  
  
- **Standarddiagramm**. Wählen Sie das Standarddiagramm aus, das Sie anzeigen möchten, wenn das Dashboard zum ersten Mal geöffnet wird. Die verfügbaren Werte werden vom Wert bestimmt, der für die Entity-Eigenschaft festgelegt ist. Diese Eigenschaft arbeitet mit der Eigenschaft "Diagrammauswahl anzeigen" zusammen. Ein Benutzer kann den Typ ändern, wenn die Option **Diagrammauswahl anzeigen** aktiviert ist. Das Diagramm wird allerdings auf das Standarddiagramm zurückgesetzt, wenn das Dashboard das nächste Mal geöffnet wird.  
  
- **Nur Diagramm anzeigen**. Aktivieren Sie dieses Kontrollkästchen, wenn Sie nur das Diagramm anzeigen möchten. Deaktivieren Sie dieses Kontrollkästchen, wenn Sie das Diagramm und die zugehörigen Daten anzeigen möchten.  
  
- **Diagrammauswahl anzeigen**: Aktivieren Sie dieses Kontrollkästchen, damit Benutzer den Typ des Diagramms (Spalte, Leiste, Kreis usw.) ändern können, wenn sie das Dashboard verwenden. Wenn der Benutzer den Typ des Diagramms ändert, werden die Einstellungen nicht gespeichert. Der Diagrammtyp wird auf die Einstellung "Standarddiagramm" zurückgesetzt, wenn das Dashboard geschlossen wird.  
  
Sie können die folgenden Listeneigenschaften aus dem **Eigenschaften festlegen**-Dialogfeld festlegen:  
  
- **Name** Eindeutiger Name für die Liste. Vom System wird ein Wert vorgeschlagen, aber Sie können ihn ändern.  
  
- **Bezeichnung**: Die Bezeichnung, die am oberen Rand der Liste angezeigt wird.  
  
- **Beschriftung im Dashboard anzeigen**: Aktivieren oder deaktivieren Sie dieses Kontrollkästchen zum Ein- oder Ausblenden der Listenbeschriftung.  
  
- **Entität**: Wählen Sie die Entität (Datensatztyp), auf dem die Liste basieren soll. Diese Einstellung bestimmt die verfügbaren Werte für die Eigenschaft "Standardansicht".  
  
- **Standardansicht**: Wählen Sie die Ansicht, die zum Abrufen der Daten in der Liste verwendet wird. Ein Benutzer kann die Ansicht ändern, aber der Liste wird auf Standardansicht zurückgesetzt, wenn das Dashboard das nächste Mal geöffnet wird.  
  
- **Suchfeld anzeigen**: Aktivieren Sie dieses Kontrollkästchen, wenn oben in der Liste ein Suchfeld angezeigt werden soll. Wenn das Suchfeld enthalten ist, können Sie oder andere Benutzer Datensätze in der Liste zur Laufzeit suchen.  
  
- **Index anzeigen**: Aktivieren Sie dieses Kontrollkästchen, wenn unten in der Liste A-Z-Filter angezeigt werden sollen. Wenn die A bis Z-Filter angezeigt werden, können Sie oder andere Benutzer einen Buchstaben auswählen, um zu den Datensätzen zu springen, die mit diesem Buchstaben beginnen.  
  
- **Ansichtsauswahl**. Treffen Sie unter den folgenden Werten eine Auswahl:  
  
    - **Deaktiviert**. Zeigt die Ansichtsauswahl nicht an. Sie oder andere Benutzer werden Ansichten nicht zur Laufzeit ändern können.  
  
    - **Alle Ansichten anzeigen**. Bieten Sie eine vollständige Liste der Ansichten, die dem in der Entity-Eigenschaft festgelegten Wert zugeordnet sind.  
  
    - **Ausgewählte Ansichten anzeigen**. Wählen Sie diese Einstellung, um die Ansichten, die zur Laufzeit zur Verfügung stehen, zu begrenzen. Um die bestimmten Ansichten auszuwählen, die angezeigt werden sollen, halten Sie die STRG-Taste gedrückt, und wählen Sie jede Ansicht aus, die Sie einschließen möchten.  
 
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen oder Bearbeiten eines Dashboards](create-edit-dashboards.md)
