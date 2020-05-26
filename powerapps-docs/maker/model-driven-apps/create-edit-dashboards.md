---
title: Erstellen oder bearbeiten Modell-angetriebener App-Dashboards  | MicrosoftDocs
ms.custom: ''
ms.date: 04/08/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 641885d2-4a08-41b8-b914-d9a244e4d5b1
caps.latest.revision: 10
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9a9e49a14268c3ee82a8c5fb541473903bbf5f11
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285801"
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>Erstellen oder bearbeiten von Modell-angetriebene App-Dashboards

Es gibt zwei Arten von Dashboards: Benutzerdashboards und Systemdashboards- Ein App-Benutzer kann ein Dashboard erstellen, das ausschließlich in den App-Bereichen angezeigt wird, in denen sie über Rechte verfügt. Ein Administrator oder Anpasser kann Systemdashboards erstellen oder anpassen. Diese sind bei Veröffentlichung für alle App-Benutzer in der Organisation sichtbar. Ein Benutzer kann festlegen, dass seine Benutzerdashboards als Standarddashboard anzeigt werden und die Systemdashboards überschreiben.   

Dashboards können Standard oder interaktiv sein. Standard-Dashboards unterstützen das Hinzufügen einer oder mehrerer nicht zusammenhängender Komponenten wie Diagramme oder Listen. Interaktive Dashboards bieten Benutzern die Möglichkeit, direkt vom Dashboard aus auf einen bestimmten Datensatz zu reagieren. Der Schwerpunkt dieses Themas liegt auf standardmäßigen Systemdashboards. Informationen zu interaktivem Dashboards finden Sie unter [Konfigurieren von modellgesteuerten Dashboards für interaktive Funktionen](configure-interactive-experience-dashboards.md).
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-standard-dashboard"></a>Ein neues Standard-Dashboard erstellen  
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
  
2. Wählen Sie **Lösungen** aus und öffnen Sie dann die gewünschte Lösung.

3. Klicken Sie auf der Symbolleiste auf **Neu**, wählen Sie **Dashboard** und dann auf ein Layout mit 2, 3 oder 4 Spalten aus.  
  
4.  Geben Sie auf der Seite **Dashboard: Neu** einen Namen für das Dashboard ein.  
  
5.  Wählen Sie einen der Komponentenbereiche und wählen Sie das Symbol für ein Diagramm oder eine Liste aus.  
  
     Sie können bis zu sechs Komponenten im Dashboard verwenden.  
  
6.  Um beispielsweise ein Diagramm hinzuzufügen, wählen Sie das Diagrammsymbol auf der Kachel des Dashboard-Bereichs aus, auf der das Diagramm angezeigt werden soll. Wählen Sie dann im Dialogfeld **Komponente hinzufügen** in die Werte für **Datensatztyp**, **Ansicht** und **Diagramm** aus, und wählen Sie dann **Hinzufügen**, um das Diagramm im Dashboard hinzuzufügen. Weitere Informationen zum Erstellen eines Diagramms finden Sie unter [Erstellen eines Systemdiagramms für modellgesteuerte Apps](create-edit-system-chart.md).
  
7.  Wenn Sie mit dem Hinzufügen fertig sind, wählen Sie **Speichern** und dann **Schließen** aus.  

8. Wählen Sie auf der Symbolleiste der Lösung **Veröffentlichen** aus. 
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>Bearbeiten eines vorhandenen Dashboards  
  
1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2. Wählen Sie **Lösungen** aus und öffnen Sie dann die gewünschte Lösung.  

3. Öffnen Sie in der Liste der Lösungskomponenten das Dashboard, wählen Sie einen der Komponentenbereiche aus, und wählen Sie dann **Komponente bearbeiten** aus.  
  
4.  Im Dialogfeld **Eigenschaften festlegen** können Sie Änderungen zu Diagrammen oder einer Liste machen wie die Änderungen vornehmen an Entität, Standardansicht, eine Diagrammauswahl hinzufügen oder das Dashboard auf dem mobilen Apps zur Verfügung stellen. Wählen Sie **OK**, wenn Sie fertig sind.  
  
     Weitere Informationen zu Einstellungsdashboardkomponenteeigenschaften finden Sie unter [Eigenschaften für ein Diagramm oder eine Liste in einem Dashboard festlegen](set-properties-chart-list-included-dashboard.md)  
  
5.  Wenn Sie Ihre Änderungen in der Symbolleiste abgeschlossen haben, wählen Sie **Speichern**und dann **Schließen** aus. 

6. Wählen Sie auf der Symbolleiste der Lösung **Veröffentlichen** aus.  
  
Zusätzliche Systemdashboard-Aufgaben sind unter anderem:  
  
-   Entfernen einer Liste oder eines Diagramms aus einem Dashboard  

-   Hinzufügen einer Liste oder eines Diagramms zu einem Dashboard  

-   Einrichten des Standarddashboards  

-   Verwenden von Sicherheitsrollen, um ein Dashboard nur für bestimmte Rollen sichbar zu machen    

## <a name="next-steps"></a>Nächste Schritte  
[Festlegen von Eigenschaften für ein Diagramm oder eine Liste, die in einem Dashboard enthalten sind](set-properties-chart-list-included-dashboard.md)
