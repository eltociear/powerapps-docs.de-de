---
title: Schnellansichts-Steuerlementeigenschaften für Hauptformulare in modellgesteuerten Apps in PowerApps | MicrosoftDocs
description: Grundlegendes zu Schnellansichts-Steuerlementeigenschaften für Hauptformulare
Keywords: Quick view control properties; Dynamics 365; Main forms
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 68f68d5b-6c71-4b95-bb46-d48c59d9008e
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="model-driven-app-quick-view-control-properties"></a>Eigenschaften des Schnellansichtssteuerelements in modellgesteuerten Apps

Ein Steuerelement für die Schnellansicht auf einem modellgesteuerten App-Formular zeigt Daten aus einem Datensatz an, der bei einer Suche im Formular ausgewählt wurde. Die Daten, die im Steuerelement angezeigt werden, werden mithilfe eines Schnellansichtsformulars definiert. Die Daten, die angezeigt werden, können nicht bearbeitet werden; wenn jedoch das primäre Feld im Schnellansichtsformular Feld enthalten ist, wird es zu einem Link, mit dem der verknüpfte Datensatz geöffnet werden kann. Weitere Informationen: [Erstellen und Bearbeiten von Schnellansichtsformularen](create-edit-quick-view-forms.md)  

> [!div class="mx-imgBorder"] 
> ![Kontaktschnellansichtsformular im Firmenformular](media/quick-view-form-contact.png "Kontaktschnellansichtsformular im Firmenformular")  

Sie können auf **Eigenschaften des Steuerelements für die Schnellansicht** über die PowerApps-Webseite zugreifen. 
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  


2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3. Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**. Wählen Sie dann auf der Registerkarte **Einfügen** das **Schnellansichtsformular**, um die Eigenschaften des Steuerelements für die Schnellansicht anzuzeigen.

    ![Steuerelement für die Schnellansicht](media/quick-view-control.png)
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Name**|**Erforderlich**: Der eindeutige Name für das Schnellansichtsformular, der verwendet wird, wenn auf es in Skripts verwiesen wird.|  
|**Bezeichnung**|**Erforderlich**: Eine für das Schnellansichtsformular anzuzeigende Beschriftung.|  
|**Beschriftung im Formular anzeigen**|Zeigt die Beschriftung im Formular an.|  
|**Suchfeld**|Wählen Sie eines der Suchfelder, die im Formular enthalten sind.|  
|**Verknüpfte Entität**|Dieser Wert hängt vom **Nachschlagefeld** ab, das Sie auswählen. Dies ist normalerweise die primäre Entität für die 1: N-Entitätsbeziehung für die Suche.<br /><br /> Wenn die Suche eine Entität **Potenz. Kunde** umfasst, die entweder eine Firma oder einen Kontakt annehmen kann, können Sie im Feld **Schnellansichtsformular** ein Schnellansichtsformular für Firma und Kontakt auswählen, indem Sie diesen Wert ändern und dann ein anderes Schnellansichtsformular auswählen.|  
|**Schnellansichtsformular**|Wenn die **Verknüpfte Entität** ein Schnellansichtsformular hat, können Sie dies hier auswählen. Wählen Sie andernfalls **Neu** aus, um eines zu erstellen.<br /><br /> Wählen Sie **Bearbeiten** aus, um das ausgewählte Schnellansichtsformular zu ändern.|  
|**Zusätzliche Eigenschaften**|Sie können den Standardrenderingstil angeben, indem Sie das Kontrollkästchen aktivieren.|

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
 
