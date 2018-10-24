---
title: App-Erstellungsmethoden von Common Data Service für Apps | Microsoft-Dokumentation
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
- powerapps
ms.assetid: e9810433-224b-4bde-851a-e581cf5fb8a4
caps.latest.revision: 21
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1eda4b591a3296001ffa62b16e185b421a197e75
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865039"
---
# <a name="common-data-service-for-apps-supported-and-unsupported-app-building-practices"></a>Unterstützte und nicht unterstützte App-Erstellungsmethoden für Common Data Service für Apps

<!--
The way your organization works is unique. Some organizations have well-defined business processes that they apply using PowerApps apps. Others aren’t happy with their current business processes and use PowerApps to apply new data and processes to their business. Whatever situation you find yourself in, you’ll find a lot of customization capabilities in PowerApps so that it can work for your organization.  
  
 Of course you’re eager to get started, but please take a few minutes to read the content in this section. This will introduce you to important terms, give you some background about why things are done a certain way, and help you avoid potential problems in the future.  

## What is metadata and why should you care?  
 In the past, you may have customized business applications by editing the source code. This created complications because each organization had unique changes and it was very difficult, or extremely expensive, to upgrade. Then application developers started exposing application programming interfaces (APIs) so that other developers could interact with the application and add their own logic without touching the source code. This was moderately better because it means developers can extend the application without changing it. But it still requires a developer to write code.  -->
  
 Moderne Geschäftsanwendungen verwenden eine von Metadaten gesteuerte Architektur, sodass Benutzer Apps erstellen können, ohne Code zu schreiben. Metadaten sind „Daten über Daten“ und definieren die Struktur der in Common Data Service für Apps gespeicherten Daten. Dank der Metadaten kennt eine Anwendung alle Änderungen der Datenstruktur. Dies ermöglicht der Anwendung die Anpassung, wenn sich die Datenstruktur ändert. Da die Metadaten bekannt sind, können zusätzliche Funktionen eingeschlossen werden, die mit den Metadaten verknüpft sind.  

Das Ändern der Komponenten von Common Data Service für Apps, z.B. Entitäten, Ansichten, Felder, Diagramme und Dashboards, um Apps auf die gewünschte Art und Weise zu erstellen, wird als *Anpassung* bezeichnet.  
 
Wenn Sie Ihre Apps mit den Tools in PowerApps erstellen und anpassen, fügen Sie Metadaten oder Daten hinzu oder aktualisieren diese, die von Features verwendet werden, die von den Metadaten abhängen. Da wir die Arten von Daten kennen, mit denen Apps erstellt werden, können wir diese Daten berücksichtigen und Ihrer Common Data Service für Apps-Umgebung neue Features hinzufügen, ohne Ihre Apps zu beenden. <!-- This way you should always be able to apply an update rollup or upgrade to the latest version and enjoy the best new features.  -->

<!--  
> **Customize or Configure?**   
> Most people say they want to customize the application, so we use the word “customize” to describe changing the system to make it work the way you want. Some people prefer to use the word “configure” because it suggests that no code was required to make changes. Call it whatever you like, we just want to make it clear that you don’t need to be a developer to customize or create PowerApps apps.  -->
  
Sie müssen kein Entwickler sein, um PowerApps-Apps zu erstellen und anzupassen. PowerApps bietet jedoch eine Reihe von Webdiensten und APIs, mit denen Entwickler Code schreiben können. Wenn Code mit unterstützten Methoden geschrieben wird, können Sie davon ausgehen, dass er auch nach einer Aktualisierung der Common Data Service für Apps-Umgebung noch funktioniert.  
  
<a name="BKMK_SupportedCust"></a>   
## <a name="what-kinds-of-customizations-are-supported"></a>Welche Arten von Anpassungen werden unterstützt?  
 Wir gehen davon aus, dass Sie die meisten Erstellungs- und Anpassungsvorgänge mit den verfügbaren PowerApps-Tools durchführen können. Wenn die Anpassungstools nicht Ihren Anforderungen entsprechen, können Sie eine Lösung installieren, die von einem Drittanbieter bereitgestellt wird, oder einen Entwickler zum Codieren der App einstellen. Wenn Sie in eine Lösung investieren müssen, die Code erfordert, sollten Sie sicherstellen, dass der Code nur mit unterstützten APIs geschrieben wird. Dadurch können Sie Ihre Investition in die Apps und etwaige Lösungen schützen.  
  
 Entwickler, die Apps in PowerApps erweitern, müssen den im SDK dokumentierten Regeln und Best Practices folgen: [Best practices for developing with Dynamics 365 Customer Engagement (Best Practices für die Entwicklung mit Dynamics 365 Customer Engagement)](https://docs.microsoft.com/dynamics365/customer-engagement/developer/best-practices-sdk). Das SDK dokumentiert die APIs, die Entwicklern zur Verfügung stehen, und enthält Anleitungen dazu, wie Sie diese am besten verwenden. Microsoft unterstützt nur die APIs und die Methoden, die im SDK dokumentiert sind. Möglicherweise finden Sie im Internet eine Beschreibung einer möglichen Problemlösung, aber wenn diese die im SDK dokumentierten APIs nicht verwendet, wird sie von Microsoft nicht unterstützt. Bevor ein Entwickler eine Änderung anwendet, sollten Sie prüfen, ob diese unterstützte Methoden verwendet.  
  
 Wenn Entwickler die im SDK beschriebenen APIs und Best Practices verwenden, können wir testen, ob eine der von uns an Common Data Service für Apps vorgenommenen Änderungen möglicherweise vorhandene Anpassungen beeinträchtigt. Unser Ziel ist, dass mit unterstützten Methoden geschriebene Codeanpassungen weiterhin auch dann noch einwandfrei funktionieren, wenn neue Versionen oder Aktualisierungen von Common Data Service für Apps veröffentlicht werden. Sie profitieren, da Sie auf neue Versionen mit verbesserten Funktionen aktualisieren können, ohne dass Entwickler jedes Mal ihren Code ändern müssen.  
  
 Wenn festgestellt wird, dass eine Änderung in einer neuen Version von Common Data Service für Apps eine unterstützte Anpassung beeinträchtigt, werden die betroffenen Teile und Änderungen dokumentiert, mit denen der Code korrigiert werden kann.  
  
<a name="BKMK_Unsupported"></a>   
## <a name="what-kinds-of-customizations-arent-supported"></a>Welche Arten von Anpassungen werden nicht unterstützt?  
 Nur weil bestimmte APIs und Programmiermethoden von Microsoft nicht unterstützt werden, bedeutet dies nicht, dass sie nicht funktionieren. <!--  “Unsupported by Microsoft” means exactly what it says: you can’t get support about these APIs or programming practices from Microsoft. We don’t test them and we don’t know if something we change will break them. We can’t predict what will happen if someone changes code in our application.  --> Die Entwickler, die nicht unterstützte APIs und Programmiermethoden verwenden, übernehmen die Verantwortung dafür, dass ihr Code unterstützt wird. Sie müssen ihren Code testen, um sicherzustellen, dass er funktioniert.  
  
 Wenn Sie nicht unterstützte Anpassungen in Ihrer Common Data Service für Apps-Umgebung verwenden möchten, sollten Sie unbedingt die durchgeführten Schritte dokumentieren und eine Strategie zum Entfernen der Anpassungen besitzen, bevor Sie sich an den technischen Support von Microsoft wenden. Wenn Sie bei nicht unterstützten Anpassungen Hilfe benötigen, wenden Sie sich an den Entwickler oder die Organisation, die die Anpassungen vorbereitet haben.  
  
<a name="BKMK_CommonUnsupportedCustomizations"></a>   
### <a name="common-unsupported-customization-practices"></a>Gängige, nicht unterstützte Praktiken im Zusammenhang mit Anpassungen  
 Folgende Liste enthält eine Aufstellung der gängigen, nicht unterstützten Praktiken im Zusammenhang mit Anpassungen. Die Liste ist nicht erschöpfend. Weitere Informationen: [Supported extensions for Dynamics 365: Unsupported customizations (Unterstützte Erweiterungen für Dynamics 365: nicht unterstützte Anpassungen)](https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions#Unsupported). 
 
**Interacting with the web application Document Object Model (DOM) elements using JavaScript (Interagieren mit Document Object Model- (DOM-)Elementen der Webanwendung unter Verwendung von JavaScript)**  
 Alle JavaScript-Bibliotheken, die an einer beliebigen Stelle in der Anwendung verwendet werden, dürfen nur mit den dokumentierten APIs interagieren. Wenn JavaScript-Entwickler mit Anwendungen arbeiten, greifen sie häufig unter Verwendung bestimmter Namen auf DOM-Elemente zu. Da PowerApps-Apps Webanwendungen sind, funktionieren diese Verfahren, werden aber aller Wahrscheinlichkeit nach während einer Aktualisierung beeinträchtigt, da die Namen der Elemente, auf die sie verweisen, jederzeit geändert werden können. Wir behalten uns das Recht vor, alle notwendigen Änderungen in der Anwendung vorzunehmen. Dies bedeutet häufig, dass der Aufbau der Seite geändert muss. Das Hinzufügen von Änderungen, die von der aktuellen Struktur der Seite abhängig sind, bedeutet, dass Sie den benutzerdefinierten Code in diesen Skripts jedes Mal testen und möglicherweise ändern müssen, wenn Sie ein Update auf Ihre Anwendung anwenden.  
  
 jQuery ist eine häufig von JavaScript-Entwicklern verwendete Bibliothek. jQuery erleichtert Entwicklern den Zugriff auf und die Erstellung von DOM-Elementen, was auf den Anwendungsseiten von Common Data Service für Apps nicht unterstützt wird. jQuery wird empfohlen, wenn Entwickler benutzerdefinierte Benutzeroberflächen mit HTML-Webressourcen erstellen, aber die unterstützten APIs in den PowerApps-Anwendungsseiten die Verwendung von jQuery nicht voraussetzen.  
  
 **Verwenden von nicht dokumentierten internen Objekten oder Methoden mithilfe von JavaScript**  
Common Data Service für Apps verwendet viele JavaScript-Objekte in Seiten. JavaScript-Entwickler können diese Objekte ermitteln, indem sie eine Seite debuggen und dann auf die Objekte zugreifen und diese wiederverwenden. Wir behalten uns das Recht vor, alle notwendigen Änderungen an diesen Objekten vorzunehmen. Dazu gehört auch das Entfernen der Methode oder Ändern ihrer Namen. Wenn ein Skript auf diese Objekte verweist und die Objekte nicht gefunden werden, wird das Skript beendet.  <a name="BKMK_Metadata"></a>   
 
<a name="BKMK_CombineCustomizations"></a>   
## <a name="combine-customization-capabilities"></a>Kombinieren von Anpassungsfunktionen  
 In den Themen der folgenden Abschnitte werden die einzelnen Anpassungsfunktionen ausführlich beschrieben. Es ist jedoch wichtig zu beachten, dass die Lösungen, die ihre geschäftlichen Anforderungen erfüllen, häufig eine Funktion mit mindestens einer anderen Funktion verwenden.  
  
<a name="BKMK_ChooseTheRightCustomization"></a>   
### <a name="choose-the-right-customization-capability-for-the-job"></a>Auswählen der richtigen Anpassungsfunktion für den Einzelvorgang  
 Angesichts der vielen unterschiedlichen Anpassungsfunktionen in PowerApps können Sie sich rasch mit einer Funktion vertraut manchen und sie zur Behebung jedes Problems verwenden. Bedenken Sie beim Beurteilen der geschäftlichen Probleme, die Sie lösen möchten, das gewünschte Endergebnis, und bearbeiten Sie das Problem dann vom Ende her.  
 
<a name="BKMK_changesinperformance"></a>   
## <a name="changes-that-affect-common-data-service-for-apps-environment-performance"></a>Änderungen mit Auswirkungen auf die Leistung von Common Data Service für Apps  
 Die Leistung von Common Data Service für Apps kann durch Importieren von Lösungen und Anwenden von Anpassungen beeinträchtigt werden, durch die Metadaten geändert werden. Aktionen, die den normalen Systembetrieb stören können:  
  
-   Hinzufügen, Entfernen oder Ändern von Entitäten, alternativen Schlüsseln, Attributen oder Beziehungen   
-   Importieren von Lösungen
  
-   Veröffentlichen von Anpassungen 
  
Wenn Sie diese Änderungen in einem Produktionssystem anwenden, sollten Sie die Vorgänge für einen Zeitpunkt planen, zu dem deren Durchführung für Benutzer am wenigsten störend ist.   
  
  
## <a name="next-steps"></a>Nächste Schritte  
[What are model-driven apps in PowerApps? (Was sind modellgesteuerte Apps in PowerApps?)](../../maker/model-driven-apps/model-driven-app-overview.md)

