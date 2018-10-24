---
title: Erstellen einer Lösung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Lösung erstellen.
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 26ecc9b2f83375ba10e6b32dfc12d6cc37342cf4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689177"
---
# <a name="create-a-solution"></a>Erstellen einer Lösung

Da die Standardlösung alle Lösungskomponenten enthält, ist es ggf. einfacher, beim Erstellen einer separaten Lösung nur die angepassten Lösungskomponenten zu berücksichtigen, und Anpassungen an diesen vorzunehmen. Dadurch ist es auch einfach, eine Sicherung Ihrer Lösung als kleinere Datei zu exportieren. Achten Sie jedoch stets darauf, dieser Lösung eine von Ihnen bearbeitete Lösungskomponente hinzuzufügen. Wenn Sie neue Lösungskomponenten erstellen, tun Sie das immer im Kontext dieser Lösung. Dadurch wird das Anpassungspräfix des Lösungsherausgebers einheitlich angewendet. Nachdem Sie in Ihrer Lösung Lösungskomponenten erstellt oder dieser Lösung vorhandene Lösungskomponenten hinzugefügt haben, können Sie sie bei Bedarf auch in der Standardlösung bearbeiten.  
  
 Weitere Informationen zu Lösungskonzepten finden Sie unter [Arbeiten mit Lösungen](solutions-overview.md).  
  
1.  Navigieren Sie zu **[Einstellungen](../model-driven-apps/advanced-navigation.md#settings)** > **Lösungen**. 
  
2.  Wählen Sie **Neu** aus, und bearbeiten Sie die erforderlichen Felder für die Lösung.  
  
    |Feld|Beschreibung|  
    |-----------|-----------------|  
    |**Anzeigename**|Der Name, der in der Liste der Lösungen angezeigt wird. Sie können ihn später ändern.|  
    |**Name**|Der eindeutige Name der Lösung. Dieser wird anhand des Werts erzeugt, den Sie in das Feld „Anzeigename“ eingeben. Sie können den Namen bearbeiten, bevor Sie die Lösung speichern – danach können Sie keine Änderungen mehr vornehmen.|  
    |**Herausgeber**|Sie können den Standardherausgeber auswählen oder einen neuen Herausgeber erstellen. Wenn Sie Ihre Lösung nicht verteilen möchten, wird empfohlen, den Standardherausgeber für Ihre Organisation zu verwenden.|  
    |**Version**|Geben Sie die Versionsnummer Ihrer Lösung ein. Dies ist nur wichtig, wenn Sie Ihre Lösung exportieren. Die Versionsnummer wird beim Exportieren der Lösung im Dateinamen angegeben.|  
  
3.  Wählen Sie **Speichern** aus.  
  
 Nachdem Sie die Lösung gespeichert haben, möchten Sie ggf. Informationen über die Pflichtfelder hinaus hinzufügen. Das ist optional. Verwenden Sie das Feld **Beschreibung**, um die Lösung zu beschreiben, und wählen Sie eine HTML-Webressource als **Konfigurationsseite** für die Lösung aus. Die Konfigurationsseite nutzen i.d.R. unabhängiger Softwarehersteller (ISV), die Lösungen verteilen. Wenn dies festgelegt ist, erscheint unter dem Knoten **Informationen** ein neuer Knoten **Konfiguration**, um diese Webressource anzuzeigen. Entwickler verwenden diese Seite, um Anweisungen oder Steuerelemente zu integrieren, mit denen Sie Konfigurationsdaten festlegen oder ihre Lösung starten können.  
  
<a name="BKMK_AddSolutionComponents"></a>   

## <a name="add-solution-components"></a>Hinzufügen von Lösungskomponenten  
 Nachdem Sie Ihre Lösung erstellt haben, enthält sie keine Lösungskomponenten mehr. Sie können neue Lösungskomponenten erstellen oder im Listenmenü über die Schaltfläche **Vorhandenes Element hinzufügen** alle Lösungskomponenten aus der Standardlösung hinzufügen.  
  
 In diesem Fall wird ggf. das Dialogfeld **Fehlende erforderliche Komponenten** angezeigt.  
   
 ![Dialogfeld „Erforderliche Komponenten hinzufügen“](media/crm-itpro-cust-addrequiredcomponents.PNG "Dialogfeld „Erforderliche Komponenten hinzufügen“")  
  
 Dieses Dialogfeld weist Sie darauf hin, dass die Lösungskomponente Abhängigkeiten zu anderen Lösungskomponenten aufweist. Wenn Sie **Nein, erforderliche Komponenten nicht einschließen.** auswählen, tritt möglicherweise ein Fehler für die Lösung auf, falls Sie sie in eine andere Organisation importieren, in der alle diese erforderlichen Komponenten nicht vorhanden sind. Wenn der Lösungsimport erfolgreich ist, kann das Verhalten in der anderen Lösung nicht identisch mit dem der ursprünglichen Organisation sein, da die Komponenten anders konfiguriert sind als in der Quelllösung.  
  
 Im Allgemeinen ist es sicherer, die erforderlichen Komponenten einzuschließen, wenn Sie die Lösung in eine andere Organisation exportieren. Wenn Sie diese Komponenten nicht beim Hinzufügen einer einzelnen Lösungskomponente hinzufügen, können Sie das auch später tun. Wählen Sie dazu die hinzugefügte Lösungskomponente und im Menü **Erforderliche Komponenten hinzufügen** aus.  
  
 Wenn Sie die Lösung gar nicht exportieren oder nur als nicht verwaltete Lösung exportieren und dann wieder in dieselbe Organisation importieren möchten, müssen Sie keine erforderlichen Komponenten einschließen. Wenn Sie die Lösung jemals exportieren, werden Sie darauf hingewiesen, dass einige erforderliche Komponenten fehlen. Wenn Sie diese Lösung nur wieder in dieselbe Organisation importieren möchten, können Sie diesen Hinweis ignorieren. Im Rahmen der Schritte zum Bearbeiten der Anwendungsnavigation oder des Menübands ohne Drittanbieter-Bearbeitungstool wird davon ausgegangen, dass Sie die Lösung wieder in dieselbe Organisation exportieren.  

> [!IMPORTANT]
>  Wenn Sie Lösungen Termine hinzufügen möchten, wird dringend empfohlen, nur einen Termintyp – d.h. nur Termine oder nur Terminserien – pro Lösung zu integrieren. Wenn Sie separate Lösungen mit unterschiedlichen Termintypen installieren und deinstallieren, tritt ein SQL Server-Fehler auf, und Sie müssen die Termine neu erstellen. 
