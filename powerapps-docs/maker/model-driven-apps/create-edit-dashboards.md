---
title: Erstellen oder bearbeiten Modell-angetriebener App-Dashboards  | MicrosoftDocs
ms.custom: ''
ms.date: 05/23/2018
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
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>Erstellen oder bearbeiten von Modell-angetriebene App-Dashboards

Es gibt zwei Arten von Dashboards: Benutzerdashboards und Systemdashboards- Ein App-Benutzer kann ein Dashboard erstellen, das ausschließlich in den App-Bereichen angezeigt wird, in denen sie über Rechte verfügt. Ein Administrator oder Anpasser kann Systemdashboards erstellen oder anpassen. Diese sind bei Veröffentlichung für alle App-Benutzer in der Organisation sichtbar. Ein Benutzer kann festlegen, dass seine Benutzerdashboards als Standarddashboard anzeigt werden und die Systemdashboards überschreiben. Der Schwerpunkt dieses Themas liegt auf Systemdashboards.  
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-dashboard"></a>Neues Dashboard erstellen  
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).   
  
2. Erweitern Sie, **Daten** und wählen Sie **Entitäten**, wählen Sie die Entität aus, die Sie als Grundlage für das Dashboard möchten, wie beispielsweise Entität **Firma** und dann wählen Sie die Registerkarte **Dashboards** aus. 

3. Klicken Sie auf der Symbolleiste auf **Ein Dashboard hinzufügen** und dann auf ein Layout mit 2, 3 oder 4 Spalten aus.  
  
4.  Geben Sie im Dialogfeld **Dashboard: Neu** einen Namen für das Dashboard ein.  
  
5.  Wählen Sie einen der Komponentenbereiche und wählen Sie das Symbol für ein Diagramm oder eine Liste aus.  
  
     Sie können bis zu sechs Komponenten im Dashboard verwenden.  
  
6.  Um beispielsweise ein Diagramm hinzuzufügen, wäehlen Sie im Dialogfeld **Komponente hinzufügen** in die Werte für **Datensatztyp**, **Ansicht** und **Diagramm** aus, und wählen Sie dann **Hinzufügen**, um das Diagramm im Dashboard hinzuzufügen.  
  
7.  Wenn Sie mit dem Hinzufügen fertig sind, wählen Sie **Speichern** und dann **Veröffentlichen** aus.  
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>Bearbeiten eines vorhandenen Dashboards  
  
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).    
  
2. Erweitern Sie, **Daten** und wählen Sie **Entitäten**, wählen Sie die Entität aus, die Sie als Grundlage für das Dashboard möchten, wie beispielsweise Entität **Firma** und dann wählen Sie die Registerkarte **Dashboards** aus.  

3. Öffnen (Doppelklick) Sie ein Dashboard, wählen Sie einen der Komponentenbereiche aus, und wählen Sie dann **Komponente bearbeiten** aus.  
  
4.  Im Dialogfeld **Eigenschaften festlegen** können Sie Änderungen zu Diagrammen oder einer Liste machen wie die Änderungen vornehmen an Entität, Standardansicht, eine Diagrammauswahl hinzufügen oder das Dashboard auf dem mobilen Apps zur Verfügung stellen. Wählen Sie **Festlegen** aus, wenn Sie fertig sind.  
  
     Weitere Informationen zu Einstellungsdashboardkomponenteeigenschaften finden Sie unter [Eigenschaften für ein Diagramm oder eine Liste in einem Dashboard festlegen](set-properties-chart-list-included-dashboard.md)  
  
4.  Wenn Sie Ihre Änderungen abgeschlossen haben, müssen Sie diese Speichern und veröffentlichen.  
  
 Zusätzliche Systemdashboard-Aufgaben sind unter anderem:  
  
    -   Entfernen einer Liste oder eines Diagramms aus einem Dashboard  
  
    -   Hinzufügen einer Liste oder eines Diagramms zu einem Dashboard  
  
    -   Einrichten des Standarddashboards  
  
    -   Verwenden von Sicherheitsrollen, um ein Dashboard nur für bestimmte Rollen sichbar zu machen    
  
## <a name="next-steps"></a>Nächste Schritte  
[Festlegen von Eigenschaften für ein Diagramm oder eine Liste, die in einem Dashboard enthalten sind](set-properties-chart-list-included-dashboard.md)
