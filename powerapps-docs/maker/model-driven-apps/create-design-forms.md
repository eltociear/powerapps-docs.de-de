---
title: Erstellen und entwerfen von Modell-angetriebenen App-Formularen | MicrosoftDocs
ms.custom: ''
ms.date: 12/06/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 33
ms.author: matp
manager: kvivek
author: Mattp123
tags:
- Links to topic not migrated
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e3a3e8bd5527f9707849bf1b54247605d447469
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2704565"
---
# <a name="create-and-design-model-driven-app-forms"></a>Erstellen und entwerfen von Modell-angetriebenen App-Formularen 

Mit PowerApps bieten Formulare die Benutzeroberfläche, mit der Benutzer mit den Daten interagieren, die sie für Ihre Arbeit benötigen. Es ist wichtig, dass die Formulare, die die Benutzer verwenden, so konzipiert sind, dass benötigte Informationen effektiv gefunden oder eingegeben werden können. 

In der Standardlösung oder einer nicht verwalteten Lösung können Sie für alle Entitäten, die eine Anpassung erlauben, neue Formulare erstellen oder vorhandene Formulare bearbeiten. In einer nicht verwalteten Lösung können Sie die verwalteten Eigenschaften für eine nicht verwaltete benutzerdefinierte Entität bearbeiten, die für die Lösung erstellt wurde.
Wenn Sie eine verwaltete Lösung anzeigen, können Sie keine neuen Formulare für Entitäten erstellen oder vorhandene Formulare bearbeiten. Wenn jedoch die verwalteten Eigenschaften für eine Entität in der verwalteten Lösung eine Anpassung erlauben, können Sie für diese Entität Formulare hinzufügen oder vorhandene Formulare bearbeiten. 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>Typ der Formulare
Es gibt mehrere unterschiedliche Arten von Formularen und jeder Typ verfügt über eine Funktion oder Verwendung. Weitere Informationen: [Typen von Formularen in PowerApps](types-forms.md).  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>Aktualisierte versus klassische Entitäten  
PowerApps bietet zahlreiche Optionen zum Entwerfen von Formularen. Mit der einheitlichen Oberfläche wurden die meisten Entitäten aktualisiert, damit sie sich für die dynamische Benutzeroberfläche eignen. Aktualisierte Entitäten und Ihre eigenen benutzerdefinierten Entitäten bieten Unterstützung für den Dynamics 365 for tablets Client, Geschäftsprozessflüsse und Geschäftsregeln. Wenn Sie diese Entitäten verwenden, können Sie einmal entwerfen und für alle Clients bereitstellen.  
  
Es gibt immer noch mehrere Entitäten (klassische Entitäten), die die Darstellung und Funktionen aus früheren Versionen verwenden. Diesen Entitäten werden weniger häufig verwendet. Sie sind hier aufgelistet:  
  
||||||  
|-|-|-|-|-|  
|Adresse|Artikel|Kommentar zu Artikel|Massenlöschungsvorgang|Verbindung|  
|Rabatt|Rabattliste|Dokumentort|E-Mail-Anlage|Folgen|  
|Ziel|Zielmetrik|Importquelldatei|Rechnung (Produkt)|Auftrag (Produkt)|  
|Preisliste|Warteschlangenelement|Angebot (Produkt)|Rollupfeld|Rollupabfrage|  
|Gespeicherte Ansicht|Service|Serviceaktivität|SharePoint-Website|Standort|  
|Gebiet|Einheit|Einheitengruppe|||  
  
## <a name="form-display-faq"></a>Formularanzeige FAQ

### <a name="why-is-my-form-not-visible-in-the-form-selector-drop-down-in-my-app"></a>Warum ist mein Formular in der Dropdown-Formularauswahlliste meiner App nicht sichtbar?
Ein Formular ist möglicherweise nicht verfügbar, weil es nicht zur App hinzugefügt wurde.
1. Öffnen Sie eine App im App-Designer.
2. Wählen Sie im Bereich **Entitätsansicht** **Formulare** neben der Entität aus.
3. Überprüfen Sie auf der Registerkarte **Komponenten** die Hauptformulare, die für die App enthalten sind. Überprüfen Sie, ob das Formular, das Sie anzeigen möchten, aktiviert ist. Falls nicht, wählen Sie es aus und dann speichern und veröffentlichen Sie die App.

   > [!div class="mx-imgBorder"] 
   > ![](media/forms-included-in-app.png "Forms included with app")
   
### <a name="why-isnt-my-form-displayed-as-the-default-form-in-the-app"></a>Warum wird mein Formular in der App nicht als Standardformular angezeigt?
Ein Formular kann über die Konfiguration der Formularreihenfolge oder wenn ein Benutzer das Standardformular als Personalisierungseinstellung festlegt, als Standardformular festgelegt werden.
1. Öffnen Sie den Projektmappen-Explorer. Erweitern Sie die Entität, die die Formulare beinhaltet, die Sie bestellen möchten, und wählen Sie dann **Formulare**.
2. Wählen Sie in der Symbolleiste **Formularreihenfolge** > **Hauptformularsatz** aus. 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-toolbar.png "Form Order toolbar command")
   
3. Die Formularreihenfolge wird angezeigt. Wählen Sie das Formular aus und bewegen Sie es mit den Pfeiltasten nach oben und unten innerhalb der Formularreihenfolge. Das Formular oben in der Liste ist das Standardformular. 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-dialog.png "Form order dialog")
   
4. Wählen Sie **OK**, um die Änderungen der Formularreihenfolge zu speichern.
5. Wählen Sie in der Symbolleiste des Formulardesigners **Veröffentlichen**, um die Formularreihenfolge in Apps verfügbar zu machen.
 
#### <a name="form-order-user-personalization-setting"></a>Einstellung zur Personalisierung der Benutzer der Formularreihenfolge
Beachten Sie, dass, wenn ein App-Benutzer die Formularauswahl im Dropdown-Menü einer App ändert, dieses Formular zum Standardformular für den Benutzer wird. Diese Personalisierung überschreibt das Standardformular, das für die Entität in der App angegeben ist.

   > [!div class="mx-imgBorder"] 
   > ![](media/change-form-user-setting.png "User setting to change default form")
   
### <a name="related-topics"></a>Verwandte Themen  
    
[Zuweisen der Formularreihenfolge](assign-form-order.md) <br />
[Zugriff auf Formulare steuern](control-access-forms.md) <br />
[Wie Hauptformulare in verschiedenen Clients erscheinen](main-form-presentations.md) <br />
