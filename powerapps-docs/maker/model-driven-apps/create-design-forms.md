---
title: Erstellen und Entwerfen von Formularen in modellgesteuerten Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2018
ms.reviewer: ''
ms.service: crm-online
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
tags:
- Links to topic not migrated
ms.openlocfilehash: ed51d04919c6316c827b0286eefaaccdf539c6ef
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689561"
---
# <a name="create-and-design-model-driven-app-forms"></a>Erstellen und Entwerfen von Formularen in modellgesteuerten Apps 

PowerApps stellt Benutzern mit Formularen eine Benutzeroberfläche für die Interaktion mit den Daten zur Verfügung, die sie für ihre Arbeit benötigen. Es ist wichtig, dass die von den Benutzern verwendeten Formulare so gestaltet sind, dass sie die benötigten Informationen effizient suchen und eingeben können. 

In der Standardlösung oder einer nicht verwalteten Lösung können Sie neue Formulare erstellen oder vorhandene Formulare für alle Entitäten bearbeiten, die eine Anpassung des Formulars ermöglichen. In einer nicht verwalteten Lösung können Sie die verwalteten Eigenschaften für eine nicht verwaltete benutzerdefinierte Entität bearbeiten, die für die Lösung erstellt wurde.
Beim Anzeigen einer verwalteten Lösung können Sie keine neuen Formulare erstellen oder vorhandene Formulare für Entitäten bearbeiten. Wenn jedoch die verwalteten Eigenschaften für eine Entität in der verwalteten Lösung so festgelegt sind, dass sie eine Anpassung ermöglichen, können Sie Formulare dieser Entität hinzufügen oder bearbeiten. 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>Formulartypen
Es gibt verschiedene Typen von Formularen, und für jeden Typ gibt es eine bestimmte Funktion oder Verwendung. Weitere Informationen finden Sie unter [Formulartypen in PowerApps](types-forms.md).  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>Vergleich zwischen aktualisierten und klassischen Entitäten  
PowerApps bietet viele Optionen zum Entwerfen von Formularen. Mit der einheitlichen Oberfläche wurden die meisten Entitäten aktualisiert, damit sie sich besser für die dynamische Oberfläche eignen. Aktualisierte Entitäten und Ihre eigenen benutzerdefinierten Entitäten unterstützen Clients für Dynamics 365 für Tablets, Geschäftsprozessflüsse und Geschäftsregeln. Wenn Sie diese Entitäten verwenden, können Sie einen einzigen Entwurf erstellen und diesen für alle Clients bereitstellen.  
  
Es gibt noch eine Reihe von Entitäten, die hier als „klassische“ Entitäten bezeichnet werden, die das Aussehen und die Funktionalität früherer Versionen erhalten. Diese Entitäten werden seltener verwendet. Es handelt sich um:  
  
||||||  
|-|-|-|-|-|  
|Adresse|Artikel|Kommentar zu Artikel|Massenlöschungsvorgang|Verbindung|  
|Rabatt|Rabattliste|Dokumentspeicherort|E-Mail-Anlage|Follow|  
|Goal|Zielmetrik|Importquelldatei|Rechnung (Produkt)|Auftrag (Produkt)|  
|Price List|Queue Item|Angebot (Produkt)|Rollupfeld|Rollupabfrage|  
|Gespeicherte Ansicht|Dienst|Serviceaktivität|SharePoint-Website|Website|  
|Territory|Einheit|Einheitengruppe|||  
  
### <a name="related-topics"></a>Verwandte Themen  
    
[Zuweisen der Formularreihenfolge](assign-form-order.md) <br />
[Steuern des Zugriffs auf Formulare](control-access-forms.md) <br />
[Wie Hauptformulare in verschiedenen Clients angezeigt werden](main-form-presentations.md) <br />
