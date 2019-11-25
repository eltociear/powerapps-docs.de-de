---
title: Common Data Service App-Erstellungspraktiken | MicrosoftDocs
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: e2dd81bca0ab5805d88f5db0aff9a1f83c8d87ac
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748421"
---
# <a name="common-data-service-supported-and-unsupported-app-building-practices"></a>Common Data Service unterstützte und nicht unterstützte App-Erstellungspraktiken

<!--
The way your organization works is unique. Some organizations have well-defined business processes that they apply using PowerApps apps. Others aren’t happy with their current business processes and use PowerApps to apply new data and processes to their business. Whatever situation you find yourself in, you’ll find a lot of customization capabilities in PowerApps so that it can work for your organization.  
  
 Of course you’re eager to get started, but please take a few minutes to read the content in this section. This will introduce you to important terms, give you some background about why things are done a certain way, and help you avoid potential problems in the future.  

## What is metadata and why should you care?  
 In the past, you may have customized business applications by editing the source code. This created complications because each organization had unique changes and it was very difficult, or extremely expensive, to upgrade. Then application developers started exposing application programming interfaces (APIs) so that other developers could interact with the application and add their own logic without touching the source code. This was moderately better because it means developers can extend the application without changing it. But it still requires a developer to write code.  -->
  
 Moderne Geschäftsanwendungen verwenden eine metadatengesteuerte Architektur, damit Benutzer Apps erstellen können, ohne Code schreiben zu müssen. Metadaten bedeuten "Daten über Daten" und definieren die Struktur der in Common Data Service gespeicherten Daten. Mit diesen Metadaten weiß eine Anwendung über sämtliche Änderungen an der Datenstruktur bescheid und kann sich so anpassen, wenn sich die Datenstruktur ändert. Da die Metadaten bekannt sind, können zusätzliche Funktionen enthalten sein, die mit den Metadaten verbunden sind.  

Das Ändern der Common Data Service-Komponenten, wie Entitäten, Ansichten, Felder, Diagramme und Dashboards, um Anwendungen zu erstellen, die so funktionieren, wie Sie es wünschen, wird als *Anpassung* bezeichnet.  
 
Wenn Sie Ihre Anwendungen mit den Tools unter PowerApps erstellen und anpassen, fügen Sie die Metadaten oder Daten hinzu oder aktualisieren, die von Funktionen verwendet werden, die von den Metadaten abhängen. Da wir die Art der Daten kennen, die zur Erstellung von Apps verwendet werden, können wir diese Daten berücksichtigen und neue Funktionen in Ihre Common Data Service-Umgebung integrieren, ohne Ihre Apps zu beeinträchtigen. <!-- This way you should always be able to apply an update rollup or upgrade to the latest version and enjoy the best new features.  -->

<!--  
> **Customize or Configure?**   
> Most people say they want to customize the application, so we use the word “customize” to describe changing the system to make it work the way you want. Some people prefer to use the word “configure” because it suggests that no code was required to make changes. Call it whatever you like, we just want to make it clear that you don’t need to be a developer to customize or create PowerApps apps.  -->
  
Sie müssen kein Entwickler sein, um PowerApps-Anwendungen zu erstellen und anzupassen. PowerApps bietet jedoch eine Reihe von Webservices und APIs, mit denen Entwickler Code schreiben können. Wenn Code mit unterstützten Methoden geschrieben wird, können Sie erwarten, dass er weiterhin funktioniert, wenn Ihre Common Data Service-Umgebung aktualisiert wird.  
  
<a name="BKMK_SupportedCust"></a>   
## <a name="what-kinds-of-customizations-are-supported"></a>Welche Arten von Anpassungen werden unterstützt?  
 Wir erwarten, dass Sie die meisten Apps mit den verfügbaren PowerApps-Tools erstellen und anpassen können. Wenn die Anpassungstools nicht Ihren Anforderungen entsprechen, können Sie eine Lösung eines Drittanbieters installieren oder einen Entwickler mit der Programmierung Ihrer App beauftragen. Wenn Sie in eine Lösung investieren müssen, für die Code erforderlich ist, sollten Sie sicherstellen, dass der Code nur mithilfe unterstützter APIs geschrieben wird. Dies hilft Ihnen dabei, Ihre Investition in die Apps und alle anderen Lösungen zu schützen.  
  
 Entwickler, die PowerApps-Anwendungen erweitern, haben die Verantwortung, Regeln und Best Practices zu befolgen, die [hier](/powerapps/developer/common-data-service/best-practices/) dokumentiert sind. Microsoft unterstützt nur die APIs und Methoden, die im SDK dokumentiert sind. Möglicherweise finden Sie im Internet etwas, das beschreibt, wie Sie ein Problem lösen können, aber wenn es keine im SDK dokumentierten APIs nutzt, wird es von Microsoft nicht unterstützt. Bevor Sie einen Entwickler eine Änderung durchführen lassen, sollten Sie sich vergewissern, dass unterstützte Methoden verwendet werden.  
  
 Wenn Entwickler die APIs und bewährten Methoden verwenden, die im SDK beschrieben sind, können wir sicher sein, dass wir testen können, um unsere Änderungen an Common Data Service bestehende Anpassungen beschädigen können. Unser Ziel ist es, dass Codeanpassungen, die mit unterstützten Methoden geschrieben wurden, weiterhin funktionieren, wenn neue Versionen oder Updates auf Common Data Service veröffentlicht werden. Sie profitieren davon, da Sie auf neue Versionen mit verbesserten Funktionen aktualisieren können, ohne dass Entwickler jedes Mal ihren Code ändern müssen.  
  
 Wenn wir feststellen, dass eine Änderung in einer neuen Version von Common Data Service zum Fehlschlag einer unterstützten Anpassung führt, dokumentieren wir, was betroffen ist und wie der Code geändert werden kann, um dies zu beheben.  
  
<a name="BKMK_Unsupported"></a>   
## <a name="what-kinds-of-customizations-arent-supported"></a>Welche Arten von Anpassungen werden nicht unterstützt?  
 Nur weil bestimmte APIs und Programmierpraktiken von Microsoft nicht unterstützt werden, bedeutet das nicht, dass sie nicht funktionieren. <!--  “Unsupported by Microsoft” means exactly what it says: you can’t get support about these APIs or programming practices from Microsoft. We don’t test them and we don’t know if something we change will break them. We can’t predict what will happen if someone changes code in our application.  -->    Der Entwickler, der nicht unterstützte APIs und Programmierpraktiken verwendet, übernimmt die Verantwortung für die Unterstützung seines Codes. Er muss den Code testen, um sicherzustellen, dass er funktioniert.  
  
 Wenn Sie sich für die Verwendung nicht unterstützter Anpassungen in Ihrer Common Data Service-Umgebung entscheiden, sollten Sie sicherstellen, dass Sie dokumentieren, was getan wurde, und eine Strategie zum Entfernen dieser Anpassungen haben, bevor Sie sich an den Microsoft Technical Support wenden. Wenn Sie Hilfe bei nicht unterstützten Anpassungen benötigen, wenden Sie sich an den Entwickler oder die Organisation, die die Anpassungen vorgenommen haben.  
  
<a name="BKMK_CommonUnsupportedCustomizations"></a>   
### <a name="common-unsupported-customization-practices"></a>Allgemeine nicht unterstützte Anpassungspraktiken  
 Nachfolgend finden Sie eine Liste verbreiteter Anpassungspraktiken, die nicht unterstützt werden. Dies ist keine vollständige Liste. Weitere Informationen: [Unterstützte Erweiterungen für Dynamics 365: Nicht unterstützte Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions#Unsupported). 
 
**Interagieren mit Elementen der Webanwendung Document Object Model (DOM) mit JavaScript**  
 Alle JavaScript-Bibliotheken, die irgendwo in der Anwendung verwendet werden, dürfen nur mit der dokumentierten API interagieren. Wenn JavaScript-Entwickler mit Anwendungen arbeiten, greifen sie oft auf DOM-Elemente mithilfe bestimmter Namen zu. Da PowerApps-Anwendungen Webanwendungen sind, funktionieren diese Techniken, aber sie werden wahrscheinlich während eines Updates kaputt gehen, da die Namen der Elemente, auf die sie verweisen, jederzeit geändert werden können. Wir behalten uns das Recht vor, alle erforderlichen Änderungen in der Anwendung vorzunehmen, und dies bedeutet häufig, dass die Konstruktionsweise der Seite geändert wird. Das Hinzufügen von Änderungen, die von der aktuellen Struktur der Seite abhängen, bedeutet, dass Sie Tests durchführen und möglicherweise den benutzerdefinierten Code in diesen Skripts immer dann ändern müssen, wenn ein Update für Ihre Anwendung stattfindet.  
  
 jQuery ist eine sehr verbreitete Bibliothek, die von JavaScript-Entwicklern verwendet wird. Der meiste Nutzens bei der Verwendung von jQuery ist, dass es einem Entwickler vereinfacht, DOM-Elemente zu erstellen und darauf zuzugreifen. Genau das unterstützen wir auf den Common Data Service-Anwendungsseiten nicht. jQuery wird empfohlen, wenn Entwickler benutzerdefinierte Benutzerschnittstellen mit HTML-Webressourcen erstellen, aber innerhalb der PowerApps-Anwendungsseiten benötigen die unterstützen APIs keine Verwendung von jQuery.  
  
 **Verwenden nicht dokumentierter interner Objekte oder Methode mit JavaScript**  
Die Common Data Service verwendet viele JavaScript-Objekte innerhalb von Seiten. Ein JavaScript-Entwickler kann diese Objekte erkennen, indem er eine Seite debuggt und dann auf diese Objekte zugreift und sie wieder verwendet. Wir behalten uns das Recht vor, an diesen Objekten alle erforderlichen Änderungen vorzunehmen, einschließlich sie zu entfernen oder die Namen der Methoden zu ändern. Wenn ein Skript auf diese Objekte verweist, schlägt es fehl, wenn sie nicht gefunden werden.  <a name="BKMK_Metadata"></a>   
 
<a name="BKMK_CombineCustomizations"></a>   
## <a name="combine-customization-capabilities"></a>Anpassungsmöglichkeiten kombinieren  
 Die in diesen Abschnitten enthaltenen Themen beschreiben die individuellen Anpassungsmöglichkeiten in erheblichem Umfang. Aber es muss darauf geachtet werden, dass die Lösungen für Ihre geschäftlichen Anforderungen häufig eine der Funktionen zusammen mit einer oder mehreren anderen Funktionen verwenden.  
  
<a name="BKMK_ChooseTheRightCustomization"></a>   
### <a name="choose-the-right-customization-capability-for-the-job"></a>Wahl der richtigen Anpassungsfunktion  
 Mit allen den verschiedenen verfügbaren Anpassungsmöglichkeiten in PowerApps, werden Sie schnell mit einem davon vertraut und versuchen möglicherweise jedes Problem damit zu lösen. Wenn Sie die Probleme prüfen, die Sie lösen müssen, denken Sie an das Endergebnis, das Sie erzielen wollen, und arbeiten Sie sich dann von dort rückwärts zu den Lösungsmöglichkeiten vor.  
 
<a name="BKMK_changesinperformance"></a>   
## <a name="changes-that-affect-common-data-service-environment-performance"></a>Änderungen, die sich auf die Leistung der Common Data Service-Umgebung auswirken.  
 Der Import von Lösungen und die Anwendung von Anpassungen, die Metadaten ändern, können die Leistung der Common Data Service-Umgebung beeinträchtigen. Aktionen, die den normalen Systembetrieb stören können, sind z. B.:  
  
-   Hinzufügen, Entfernen oder Ändern von Entitäten, Alternativschlüsseln, Attributen oder Beziehungen.   
-   Lösung importieren
  
-   Veröffentlichen von Anpassungen 
  
Wenn Sie diese Änderungen an einem Produktionssystem anwenden, empfehlen wir, Sie planen diese Vorgänge, wenn es für die Benutzer am wenigsten Unterbrechung bedeutet.   
  
  
## <a name="next-steps"></a>Nächste Schritte  
[Was sind modellgetriebene Apps in PowerApps?](../../maker/model-driven-apps/model-driven-app-overview.md)

