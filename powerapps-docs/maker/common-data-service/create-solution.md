---
title: Erstellen einer Lösung | MicrosoftDocs
description: Erfahren Sie, wie eine Lösung erstellt wird
ms.custom: ''
ms.date: 10/30/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e21a4876-08b4-417a-a644-c577a27c5cf1
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9e57aa7395b6c8fdbcfe35c944f625d9790f592a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757662"
---
# <a name="create-a-solution"></a>Erstellen einer Lösung

Da die Standardlösung alle Lösungskomponenten enthält, ist es wahrscheinlich einfacher für Sie, nur die Lösungskomponenten zu suchen, die Sie angepasst haben, wenn Sie eine separate Lösung erstellen, und alle Anpassungen dort vornehmen. Dies erleichtert auch den Export eines Backups Ihrer Lösung als kleinere Datei. Wenn Sie sich dafür entscheiden, müssen Sie stets daran denken, alle von Ihnen bearbeiteten Lösungskomponenten dieser Lösung hinzuzufügen. Wenn Sie neue Lösungskomponenten erstellen, sollten Sie sie immer im Kontext dieser Lösung erstellen. Dadurch wird das Lösungsherausgeberanpassungspräfix einheitlich verwendet. Nachdem Sie Lösungskomponenten in Ihrer Lösung erstellt oder bestehende Lösungskomponenten zu dieser Lösung hinzugefügt haben, können Sie sie jetzt nach Wunsch in der Standardlösung bearbeiten.  
  
 Weitere Informationen zu Lösungskonzepte, siehe [Arbeiten mit Lösungen](solutions-overview.md).  
  
1.  Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und wählen Sie **Lösungen** aus der linken Navigation. 
  
2.  Klicken Sie auf **Neue Lösung**, und füllen Sie die erforderlichen Felder für die Lösung aus.
  
    |Feld|Beschreibung|  
    |-----------|-----------------|  
    |**Anzeigename**|Der in der Liste der Lösungen angezeigte Name. Sie können ihn später ändern.|  
    |**Name**|Der eindeutige Name der Lösung. Dieser wird anhand des Werts generiert, den Sie im Feld Anzeigename eingegeben haben. Sie können diesen bearbeiten, bevor Sie die Lösung speichern, nach dem Speichern der Lösung ist jedoch keine Änderung mehr möglich.|  
    |**Herausgeber**|Sie können den Standardherausgeber auswählen oder einen neuen Herausgeber erstellen. Sofern Sie nicht planen, Ihre Lösung zu verteilen, sollten Sie den Standardherausgeber für Ihre Organisation verwenden.|  
    |**Version**|Geben Sie eine Nummer für die Version Ihrer Lösung an. Dies ist nur erforderlich, wenn Sie die Lösung exportieren. Die Versionsnummer wird im Dateinamen enthalten sein, wenn Sie die Lösung exportieren.|  
  
3.  Wählen Sie **Speichern** aus.  
  
 Nachdem Sie die Lösung gespeichert haben, sollten Sie möglicherweise Informationen zu Feldern hinzufügen, die nicht erforderlich sind. Diese Schritte sind optional. Verwenden Sie das Feld **Beschreibung**, um die Lösung zu beschreiben und eine HTML-Webressource als **Konfigurationsseite** für die Lösung auszuwählen. Die Konfigurationsseite wird in der Regel von ISVs verwendet, die Lösungen verteilen. Wenn dies festgelegt ist, wird ein neuer **Konfiguration**-Knoten unter dem Knoten **Informationen** angezeigt, der diese Webressource anzeigt. Entwickler verwenden diese Seite für Anweisungen oder Steuerelemente, damit Sie Konfigurationsdaten einrichten oder ihre Lösung starten können.  
  
<a name="BKMK_AddSolutionComponents"></a>   

## <a name="add-solution-components"></a>Hinzufügen von Lösungskomponenten  
 Nachdem Sie Ihre Lösung erstellt haben, enthält sie keine Lösungskomponenten. Sie können neue Lösungskomponenten erstellen oder die Schaltfläche **Vorhandenes Element hinzufügen** im Listenmenü verwenden, um Lösungskomponenten aus der Standardlösung hinzuzufügen.  
  
 Daraufhin sehen Sie möglicherweise ein Dialogfeld **Fehlende erforderliche Komponenten**.  
   
 ![Dialog "Erforderliche Komponenten hinzufügen"](media/crm-itpro-cust-addrequiredcomponents.PNG "Dialog "Erforderliche Komponenten hinzufügen"")  
  
 Dieses Dialogfeld informiert Sie, dass die Lösungskomponente von anderen Lösungskomponenten abhängt. Wenn Sie **Nein, erforderliche Komponenten nicht einschließen** auswählen, kann die Lösung fehlschlagen, wenn Sie sie in eine andere Organisation importieren, in der alle diese erforderlichen Komponenten nicht vorhanden sind. Wenn der Lösungsimport erfolgreich ist, kann es sein, dass das Verhalten in der anderen Lösung nicht dem der ursprünglichen Lösung entspricht, da die Komponenten anders als die in der Quelllösung konfiguriert sind.  
  
 Im Allgemeinen ist es sicherer, die erforderlichen Komponenten hinzufügen, wenn Sie die Lösung in eine andere Organisation exportieren wollen. Wenn Sie diese Komponenten nicht hinzufügen, wenn Sie eine einzelne Lösungskomponente hinzufügen, können Sie später zu diesem Punkt zurückkehren, die hinzugefügte Lösungskomponente auswählen und aus dem Menü **Erforderliche Komponenten hinzufügen** auswählen.  
  
 Wenn Sie die Lösung nicht exportieren möchten, oder wenn Sie sie nur als nicht verwaltete Lösung exportieren und dann wieder in dieselbe Organisation importieren möchten, ist es nicht nötig, erforderliche Komponenten hinzufügen. Wenn Sie jemals die Lösung exportieren, sehen Sie eine weitere Warnung, die besagt, dass einige erforderliche Komponenten fehlen. Wenn Sie diese Lösung nur wieder in dieselbe Organisation importieren, können diese Warnung missachten. Bei diesen Schritten zur Bearbeitung der Anwendungsnavigation oder des Menübands ohne ein Bearbeitungstool eines Drittanbieters zu verwenden, wird erwartet, dass Sie die Lösung wieder in dieselbe Organisation exportieren.  

> [!IMPORTANT]
>  Wenn Sie Termine in Lösungen aufnehmen möchten, sollten Sie nicht nur Termine und nur Terminserien in separate Lösungen einschließen. Beim Installieren und Deinstallieren separater Lösungen mit verschiedenen Termintypen tritt ein SQL Server-Fehler auf, und die Termine müssen erneut erstellt werden. 

## <a name="see-also"></a>Siehe auch
 [Verwenden von Lösungen](use-solution-explorer.md)
