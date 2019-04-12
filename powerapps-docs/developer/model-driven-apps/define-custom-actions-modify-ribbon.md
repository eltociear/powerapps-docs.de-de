---
title: Festlegen benutzerdefinierter Aktionen zur Änderung des Menübands (modellgesteuerte Apps) | Microsoft Docs
description: Infos zum Festlegen benutzerdefinierter Aktionen zur Änderung des Menübands
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 72544b02-4eed-4d70-666e-a0d880f526af
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

# <a name="define-custom-actions-to-modify-the-ribbon"></a>Festlegen benutzerdefinierter Aktionen zur Änderung des Menübands

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/define-custom-actions-modify-ribbon -->

Die Standardeinstellung, eine Anwendungsbefehlsleiste oder ein Menüband, wird durch den Common Data Service Metadaten definiert. Die standardmäßigen Daten können nicht geändert werden, aber Sie können Definitionen bestimmter Aktionen einschließen, die das Standardmenüband überschreiben.  
  
## <a name="types-of-custom-actions"></a>Typen benutzerdefinierter Aktionen  
 Es gibt zwei Typen benutzerdefinierte Aktionen für Menübänder:  
  
- `<CustomAction>`: [!INCLUDE[ribbon_element_CustomAction](../../includes/ribbon-element-customaction.md)]  
  
- `<HideCustomAction>` : [!INCLUDE[ribbon_element_HideCustomAction](../../includes/ribbon-element-hidecustomaction.md)]  
  
### <a name="custom-actions"></a>Benutzerdefinierte Aktionen  
 Eine benutzerdefinierte Aktion ist eine Anweisung dafür, wie Sie die standardmäßige Menübanddefinition ändern möchten. Sie wird zur Laufzeit ausgewertet auf das Menüband angewendet. Um den Kontext für eine benutzerdefinierte Aktion festzulegen, müssen Sie die Informationen zu dem Speicherort der Elemente einschließen, die Sie ändern möchten. Verwenden Sie das Attribut `Location`, um anzugeben, wo Ihre Änderung gelten.  
  
 Wenn Sie ein neues Menübandelement hinzufügen, verweisen Sie auf das enthaltende Element, etwa eine vorhandene Registerkarte oder Gruppe. Sie können dann das Suffix `._children` anfügen, um anzugeben, dass diese benutzerdefinierte Aktion einem vorhandenen Element etwas hinzufügt.  
  
 Wenn Sie die Definition eines vorhandenen Elements ändern, entspricht der `Location`-Wert der ID dieses  Elements.  
  
 Sie müssen auch einen eindeutigen Bezeichner für die benutzerdefinierte Aktionen angeben. Verwenden Sie das Attribut **ID**, um diesen Wert festzulegen. Es wird dringend empfohlen, eine Namenskonvention verwenden, die einen eindeutigen Wert garantiert. Aus Gründen der Konsistenz und Lesbarkeit, empfiehlt es sich, einen Punkt verwenden, um konsistente Komponenten voneinander zu trennen. Der erste Element in Ihrer Namenskonvention sollte sich auf den Lösungsherausgeber oder die Lösung beziehen, etwa `Contoso.contact.form.CustomButton.CustomAction`.  
  
> [!TIP]
>  Die konsistente Verwendung Ihrer `Id`-Attributnamenskonventionen erhöht Ihre Produktivität deutlich bei der Bearbeitung von RibbonDiffXml.  
  
 Basierend auf den Standortinformationen, die Sie angeben, bestimmt der `Sequence`-Attributwert die Reihenfolge der Wiedergabe der Elemente. Wenn ein benutzerdefiniertes Steuerelement zwischen zwei vorhandenen Steuerelementen angezeigt werden soll, müssen Sie einen Reihenfolgenwert auswählen, der zwischen den Reihenfolgenwerten der vorhandenen Elemente liegt.  
  
### <a name="hide-custom-actions"></a>Benutzerdefinierte Aktionen ausblenden  
 Ein `<HideCustomAction>` ist eine Anweisung, die Sie verwenden, wenn Sie ein vorhandenes Menübandelement entfernen möchten, damit es nicht gerendert wird. Dieses Menübandelement wird nicht ausgeblendet, es wird zur Laufzeit entfernt, so dass es nicht im Menüband vorhanden ist.  
  
> [!NOTE]
>  Da das `HideCustomAction`-Element einen angegebenen Knoten aus dem Menüband entfernt, ist das Entfernen von Menübandelementen nicht immer die beste Vorgehensweise.  
> 
> - Wenn Sie eine Schaltfläche entfernen möchten, die einem bestimmten Recht zugeordnet ist, sollten Sie die Rechte für die Entität in den Sicherheitsrollen in Ihrer Implementierung einstellen. Dadurch kann das Standardmenüband angezeigt werden, und Regeln können für Benutzer Menüelemente ausblenden oder deaktivieren, die nicht über die entsprechenden Rechte verfügen.  
>   -   Wenn Sie ein vorhandenes Menübandelement durch ein benutzerdefiniertes Menübandelement ersetzen möchten, können Sie dieses Element überschreiben, indem Sie einen `CustomAction.Location`-Wert angeben, der dem vorhandenen Element entspricht.  
  
 Das Element **HideActionId** bietet eine eindeutige ID für die Aktion. Aus Gründen der Konsistenz und Lesbarkeit, sollten Sie derselben Namenskonvention folgen wie für `<CustomAction>` -Elemente. Das Attribut **Ort** muss der ID des Menübandelements entsprechen, das Sie entfernen möchten.  
  
### <a name="see-also"></a>Siehe auch  
 [Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)   
 [Daten von einer Seite als Parameter an Menüband-Aktionen übermitteln](/dynamics365/customer-engagement/developer/customize-dev/pass-dynamics-365-data-page-parameter-ribbon-actions)<br/>   <!-- TODO need to update the relevant PowerApps repo link-->
 [Definieren der Skalierung für Menübandelemente](define-scaling-ribbon-elements.md)
