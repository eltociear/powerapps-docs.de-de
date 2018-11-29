---
title: Definieren der Skalierung für Menübandelemente (modellgesteuerte Apps) | Microsoft Docs
description: Infos zum Definieren der Skalierung für Menübandelemente
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: c2cc39d2-e540-0800-f04f-3fa66df21191
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

# <a name="define-scaling-for-ribbon-elements"></a>Definieren der Skalierung für Menübandelemente

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/define-scaling-ribbon-elements -->

Für Anwendungsmenübänder und aktualisierte Entitätsformular-Menübänder gibt es keine Skalierung. Das Skalieren betrifft nur Formulare für Entitäten, die nicht aktualisiert wurden, sowie Listenmenübänder, die mithilfe von Dynamics 365 for Outlook angezeigt wurden.  
  
 Das Ziel der Multifunktionsleiste ist, die Sichtbarkeit von relevanten Steuerelementen zu erhalten, auch wenn die horizontale Größe des Fensters geändert wird. Um dies sicherzustellen, ermöglicht Ihnen die Benutzeroberflächendefinition festzulegen, wie die Steuerelemente in einer Gruppe ihre Größe als Reaktion auf einen Wechsel der Fenstergröße ändern sollen. Dies wird als *Skalierung* bezeichnet.  
  
## <a name="associate-groups-and-controls-to-layout-templates"></a>Verknüpfen von Gruppen und Steuerelementen mit Layoutvorlagen  
 Jedes `<Group>`-Element im Menüband ist mit einem `<GroupTemplate>` verknüpft. Die `GroupTemplate` legt eine oder mehrere Möglichkeiten fest, mit denen die Steuerelemente in der Gruppe mithilfe von `<Layout>`-Elementen dargestellt werden können. Jedes `Layout` kann eine von zwei Definitionstypen für die Anzeige der Steuerelemente in der Gruppe enthalten.  
  
- Ein `<OverflowSection>` ermöglicht Steuerelementen, die relative Position abhängig vom verfügbaren Bereich zu ändern.  
  
- Ein `<Section>` steuert die Anzahl der anzuzeigenden Zeilen und gibt an, wo jedes Steuerelement angezeigt wird.  
  
  Fast alle `Layout`-Elemente, die in Menübändern eingesetzt werden, verwenden `OverflowSection`-Elemente.  
  
  Jedes `<Tab>`-Element muss ein `<MaxSize>` in `<Scaling>` enthalten. Das `MaxSize`-Element ist erforderlich, da es für die standardmäßige Darstellung jeder `Group` in einem `Tab` sorgt, wenn keine Skalierung angewendet wird. Skalierung tritt auf, wenn ein `Tab` mit einem oder mehreren `<Scale>` verknüpft ist. Jedes `MaxSize`-Element und jedes `Scale`-Element ist über das `Size`-Attribut mit einem der `Layout`-Elemente in `GroupTemplate` verknüpft, die von jeder `Group` in einem `Tab` verwendet wird.  
  
> [!NOTE]
>  Der Wert des `Size`-Attributs eines jeden `MaxSize`- oder `Scale`-Elements muss mit dem `Title` der verfügbaren `Layout`-Elemente übereinstimmen, die in `GroupTemplate` angegeben werden. Diese Werte sind Zeichenfolgen, und XSD enthält keine Möglichkeit zur Prüfung der richtigen Zuordnung. In der XML wird immer die Groß-/Kleinschreibung beachtet.  
  
 Das folgende Diagramm zeigt, wie die Elemente `MaxSize`, `Scale`, `Group`, `Layout` und `OverflowSection` aufeinander verweisen müssen, um Skalierung zu ermöglichen, wenn Sie ein `<OverflowSection>`-Element verwenden.  
  
 ![Elementbeziehungen mit OverflowSection](media/ribbon-ui-definition.png "Elementbeziehungen mit OverflowSection")  
  
 Das folgende Diagramm zeigt, wie die Elemente `MaxSize`, `Scale`, `Group`, `Layout` und `ControlRef` aufeinander verweisen müssen, um Skalierung zu ermöglichen, wenn Sie ein `<Section>`-Element verwenden.  
  
 ![Elementbeziehungen mit Abschnitt](media/ui-definition.png "Elementbeziehungen mit Abschnitt") 
  
### <a name="use-existing-group-templates"></a>Verwenden vorhandener Gruppenvorlagen  
 Wenn Sie eine neue Gruppe erstellen möchten, statt neue Gruppenvorlagen zu definieren, können Sie vorhandene `GroupTemplate`-Elemente verwenden.  
  
 Verknüpfen Sie die neue Gruppe mit dieser Vorlage. Für jedes Steuerelement in der Gruppe verwenden Sie einen `TemplateAlias`-Wert von einem der `<Section>`- oder `<OverflowSection>`-Elemente aus einem der `Layout`-Elemente, die von dieser `GroupTemplate` verwendet werden. Jedes `<OverflowSection>` enthält ein `isv``TemplateAlias`, das nicht verwendet wird. Dieses `TemplateAlias` wird bereitgestellt, um es ISVs zu erlauben, dieser Gruppe Steuerelemente hinzuzufügen.  
  
### <a name="control-how-scaling-is-applied"></a>Steuern der Skalierungsanwendung  
 Jedes `Scaling`-Element im `Scale`-Element für eine bestimmte Registerkarte steht für einen Skalierungsschritt. Jedes `Scale` wird sequenziell entsprechend der Reihenfolge angewendet, in der die `Scale`-Elemente stehen. Bei der Reduzierung des verfügbaren horizontalen Bereichs für das Menüband wird jedes Scale-Element von oben nach unten angewendet. Beim Vergrößern des verfügbaren horizontalen Bereichs ist ab dem kleinsten Bereich das untere Scale-Element wirksam. Jedes der verfügbaren `Scale`-Elemente wird von unten nach oben angewendet, bis alle `MaxSize`-Elemente wirksam sind.  
  
> [!NOTE]
>  Die `Sequence`-Attributwerte der `Scale`-Elemente werden nicht verwendet, um die Reihenfolge zu bestimmen, in der die Skalierung erfolgt. Die Skalierung wird entsprechend der relativen Reihenfolge der `MaxSize` und `Scale`-Element in RibbonDiffXML angewendet wird. Der `Sequence`-Wert ist wichtig sowohl für das `MaxSize`-Element als auch für das `Scale`-Element, weil alle `MaxSize`-Elemente über die `Scale`-Elemente zusammengefasst sein müssen. Wenn Sie neue `MaxSize`- oder `Scale`-Elemente hinzufügen, müssen Sie die `Sequence`-Standardwertbereiche überprüfen, die allen `MaxSize`- und `Scale`-Elementen zugewiesen sind. Ein häufiger Fehler ist die Zuweisung von `Sequence`-Werten, die zur Überschneidung der Bereiche führen können.  
  
### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Festlegen benutzerdefinierter Aktionen zur Änderung des Menübands](define-custom-actions-modify-ribbon.md)   
 [Definieren von Menüband-Registerkartenanzeigeregeln](define-ribbon-tab-display-rules.md)
