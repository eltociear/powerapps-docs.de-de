---
title: Befehlsleisten- oder Menübandpräsentation (modellgesteuerte Apps) | Microsoft Docs
description: 'Daten, die Befehle in Common Data Service for Apps definieren, können abhängig vom Client und von den Unterschieden bezüglich dessen, wie einige Entitäten behandelt werden, auf verschiedene Weisen dargestellt werden. Sie müssen diese Faktoren in Erwägung ziehen, wenn Sie Menüband-Befehle ändern oder neue definieren.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 5b1d7633-ab0d-94ec-166f-f5bc1af2a657
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="command-bar-or-ribbon-presentation"></a>Darstellen von Befehlsleisten und Menübändern

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/command-bar-ribbon-presentation -->

Daten, die Befehle in Common Data Service for Apps definieren, können abhängig vom Client und von den Unterschieden bezüglich dessen, wie einige Entitäten behandelt werden, auf verschiedene Weisen dargestellt werden. Sie müssen diese Faktoren in Erwägung ziehen, wenn Sie Menüband-Befehle ändern oder neue definieren.
  
<a name="BKMK_DifferentPresentations"></a>   
## <a name="different-presentations-of-commands"></a>Verschiedene Darstellungen von Befehlen  
 Es gibt drei unterschiedliche Weisen zum Anzeigen von Befehlsdaten.  
  
### <a name="updated-user-experience"></a>Aktualisierte Benutzerumgebung  
 Dies ist die Darstellung der Befehlsleiste in der Anwendung und für Formulare für Entitäten mit der aktualisierten Benutzerumgebung.  
  
 ![Firmenbefehlsleisten](media/customization-account-grid-command-bar.PNG "Firmenbefehlsleisten in Dynamics 365")
  
 In dieser Umgebung werden nur die ersten sieben Befehle angezeigt. Die restlichen Befehle sind in einem Flyoutmenü verfügbar.  
  
 Das Aktivieren von Regeln blendet Befehle aus, die nicht verwendet werden sollen.  
  
 Unterraster verfügen über eine begrenzte Anzahl von Steuerelementen. Nur Steuerelemente, die das Hinzufügen von Datensätzen, Löschen von Datensätzen oder Öffnen einer Ansicht des Rasters ermöglichen, sind verfügbar. Aber diese Befehle werden weiterhin durch Menübanddaten definiert und können angepasst werden.  
  
 ![Kontaktunterraster](media/customization-contract-subgrid.PNG "Kontaktunterraster in Dynamics 365")  
  
 Wenn Sie weitere Aktionen in der Liste der Datensätze, die in einem Unterraster angezeigt werden, ausführen möchten, muss die Option zum Öffnen einer Ansicht des Rasters ausgewählt werden.  
  
 Weitere Informationen zum Verhalten von Unterrastersteuerelementen und wie sie angepasst werden können finden Sie unter [Unterrastermenübänder](/dynamics365/customer-engagement/developer/customize-dev/ribbons-available-microsoft-dynamics-365#BKMK_SubGridRibbons).  
  
### <a name="classic-user-experience"></a>Klassische Benutzerumgebung  
 Dies ist die Darstellung mithilfe des Menübands. Es wird für Listen im Outlook-Client und für die Formulare von Entitäten verwendet, die nicht die aktualisierte Benutzerumgebung verwenden.  
  
 ![Artikelmenüband](media/customization-article-ribbon.PNG "Artikelmenüband in Dynamics 365")  
  
 In dieser Umgebung sind Registerkarten verfügbar und Gruppen können eine Skalierung definieren, sodass alle verfügbaren Befehle in einer Registerkarte angezeigt werden, wenn die Breite des Bildschirms geändert wird.  
  
 Das Aktivieren von Regeln kann Befehle deaktivieren, die nicht verwendet werden sollen, sodass diese weiterhin angezeigt werden.  
  
 Unterrasterbefehle werden in einer Listentool-Kontextregisterkarte oben auf der Seite angezeigt, wenn das Unterraster ausgewählt ist.  
  
 ![Unterrastermenüband für Artikelkommentare](media/customization-article-comments-subgrid-ribbon.PNG "Unterrastermenüband für Artikelkommentare in Dynamics 365")  
  
<a name="BKMK_CRMForTablets"></a>   
### <a name="dynamics-365-for-tablets"></a>Dynamics 365 for Tablets  
 Dynamics 365 for tablets stellt Befehle in einer für Touch-Umgebungen optimierten Weise dar. Befehle werden in der Befehlsleiste unten rechts im Bildschirm von rechts nach links angezeigt.  
  
 ![Kontoformularbefehle für Dynamics  365 für Tablets](media/customization-nobile-app-account-form-command.PNG "Kontoformularbefehle für Dynamics  365 für Tablets")  
  
> [!NOTE]
>  Symbole, die für Befehle konfiguriert wurden, werden nicht angezeigt und Beschriftungen, die zu lang sind, werden abgeschnitten.  
> 
> Dynamics 365 for tablets unterstützt kein Hinzufügen von dynamischen Elementen zu `<FlyoutAnchor>`- oder `<SplitButton>`-Elementen bei der Laufzeit.  
  
 Unterrasterbefehle werden angezeigt, wenn Benutzer auf das Unterrastersteuerelement tippen und dieses gedrückt halten. Diese Befehle werden unten links im Bildschirm von links nach rechts angezeigt.  
  
 ![Aktivitätsunterrasterbefehle in Dynamics 365 for tablets](media/customization-mobile-app-activity-subgrid.PNG "Aktivitätsunterrasterbefehle in Dynamics 365 for tablets")  
  
<a name="BKMK_CommandData"></a>   
## <a name="command-data"></a>Befehlsdaten  
 Trotz dieser sehr verschiedenen Darstellungen sind die Daten, die die Befehle für Entitäten definieren, einheitlich, unabhängig davon, wie die Befehle dargestellt werden. Sie enthalten Definitionen für Registerkarten und Gruppen mit Skalierung, doch die sichtbaren Bereiche dieser Container für Steuerelemente werden nur in der klassischen Benutzeroberfläche angezeigt.  
  
 Sowohl in der aktualisierten Benutzerumgebung als auch in Dynamics 365 für Tablets fungieren Registerkarten und Gruppen weiterhin als Container für Steuerelemente, aber es gibt keine visuelle Darstellung dieser Container und eine Skalierung wird nicht angewendet.  
  
<a name="BKMK_FilteringCommands"></a>   
## <a name="filtering-commands-based-on-presentation-and-client"></a>Filterungsbefehle basierend auf Darstellung und Client  
  
> [!IMPORTANT]
>  Das Einschließen einer Regel zum Filtern der Anzeige der Befehle ist erforderlich, es sei denn, Sie möchten, dass den Befehl für alle Clients und Darstellungen verfügbar ist.  
  
 Dank dieser Version gibt es ein neues Element, das in der Anzeige verwendet werden und Regeln aktivieren kann, die die Befehle anpassen, die Sie in der Darstellung anzeigen.  
  
 `<CommandClientTypeRule>` `Type` enthält ein Attribut, das auf Basis der Darstellung ausgewertet wird. Die folgenden gültigen Optionen entsprechen der Darstellung:  
  
- `Refresh`: Aktualisierte Benutzerumgebung  
  
- `Legacy` Klassische Benutzerumgebung  
  
- `Modern`: Dynamics 365 für Tablets  
  
  Verwenden Sie dieses Element zum Definieren von Befehlen, um zu steuern, ob sie in den verschiedenen Darstellungen angezeigt werden.  
  
  Außerdem ist bereits ein `<CrmClientTypeRule>`-Element vorhanden, aber das `Type`-Elementattribut kann nur zwischen `Web`- und `Outlook`-Clients unterscheiden. Diese Regel wertet den Dynamics 365 für Tablets-Client als auch den Webclient aus.  
  
### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Verfügbare Menübänder](/dynamics365/customer-engagement/developer/customize-dev/ribbons-available-microsoft-dynamics-365)   
 [Exportieren von Menübanddefinitionen](export-ribbon-definitions.md)   
 [Entwicklerhandbuch zur Anpassung](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)
