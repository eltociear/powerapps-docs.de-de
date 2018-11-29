---
title: Erstellen von barrierefreien Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: 'Das Thema enthält allgemeine Anleitungen und Links zu weiteren Ressourcen, die Ihnen dabei helfen, Benutzeroberflächenelemente für Webressourcen zu entwerfen, die für Personen mit Behinderung barrierefrei sind.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 307269ac-674c-5b8a-fee7-767f060af15f
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

# <a name="create-accessible-web-resources"></a>Erstellen von barrierefreien Webressourcen

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/create-accessible-web-resources -->


Wenn Sie Webressourcen einschließen, die Benutzeroberflächenelemente in der Lösung bereitstellen, müssen Sie sicherstellen, dass Sie Voraussetzungen einschließen, die es Personen mit Behinderung ermöglichen, die Webressourcen zu verwenden.  
  
 Die Elemente der Anwendungs-Benutzeroberfläche folgen Standards und bewährten Methoden, die eine gleichwertige Funktionalität für alle Benutzer ermöglichen. Personen mit Behinderung sind möglicherweise auf die Verwendung von assistiver Technologie (AT), wie beispielsweise Screenreader oder eine Reihe von alternativen Eingabegeräten, angewiesen, um mit Anwendungen interagieren zu können.  
  
 Dieses Thema enthält allgemeine Anleitungen und Links zu weiteren Ressourcen, die Ihnen dabei helfen, Benutzeroberflächenelemente für Webressourcen zu entwerfen, die für Personen mit Behinderung barrierefrei sind.  
  
<a name="BKMK_AT"></a>   
## <a name="assistive-technology"></a>Assistive Technologie  
 Es gibt eine Vielzahl von assistiven Anwendungen, wie beispielsweise Screenreader, Blindenschrift-Terminals und Spracherkennungssoftware. Diese Anwendungen fungieren als Bindeglied zu Ihren Benutzeroberflächenelementen, sodass Benutzer, die die AT-Anwendung verwenden, Ihr Programm nutzen können.  
  
 Bei Windows-Anwendungen bieten die Microsoft Benutzeroberflächenautomatisierungs-Klassen (UIA-Klassen) programmgesteuerten Zugriff auf Benutzeroberflächenelemente. Diese Klassen unterstützen automatisierte Tests und Assistive Technologie (AT). AT-Anwendungen können die Eigenschaften und Elemente verwenden, die vom Entwickler definiert und durch UIA verfügbar gemacht werden. Windows-Anwendungsentwickler besitzen ein hohes Maß an Kontrolle darüber, wie die Benutzeroberflächenelemente mithilfe von UIA verfügbar gemacht werden.  
  
 Für Webanwendungen werden bestimmte HTML-Elemente durch das Dokumentobjektmodell (DOM) verfügbar gemacht. Der Browser konvertiert DOM-Elemente in UIA-Objekte mit Eigenschaften und Ereignissen, die von der AT genutzt werden können, um dem Benutzer die Verwendung der Webanwendung zu ermöglichen. Der Entwickler hat nur beschränkte Kontrolle darüber, wie die Benutzeroberflächenelemente von dem Browser, der UIA verwendet, verfügbar gemacht werden.  
  
<a name="BKMK_HTMLWebResources"></a>   
## <a name="accessible-html-web-resources"></a>Barrierefreie HTML-Webressourcen  
 Das HTML in Ihren Webressourcen wird vom Browser verarbeitet und für AT-Anwendungen verfügbar gemacht.  
  
 Als erstes muss sichergestellt werden, dass das HTML erwarteten Verwendungsmustern folgt. Sie können beispielsweise ein `div`-HTML-Element mit einem Klickereignis definieren, sodass es genau wie ein `button`-HTML-Element funktioniert. Der Browser erwartet jedoch nicht, dass ein `div`-Element als Schaltfläche verwendet wird und macht nicht die gleichen Eigenschaften und Ereignisse für eine AT-Anwendung verfügbar.  
  
 Es ist wichtig, dass Sie die richtigen HTML-Elemente für die Typen von Interaktionen verwenden, die Benutzer mit Ihren Webressourcen tätigen. Dies wird als [semantisches HTML](https://docs.microsoft.com/en-us/microsoft-edge/accessibility) bezeichnet.  
  
 Allerdings sind dem semantischen HTML Grenzen gesetzt. Moderne Webanwendungen enthalten in der Regel benutzerdefinierte Steuerelemente, die aus vielen HTML-Elementen bestehen, die zusammenarbeiten. Seiteninhalt, der häufig mithilfe von asynchronem JavaScript dynamisch aktualisiert wird, ist für AT-Anwendungen, die nur auf semantischem HTML basieren, verwirrend. [ARIA (Accessible Rich Internet Application)](https://docs.microsoft.com/en-us/microsoft-edge/accessibility) Technologie bietet eine Lösung durch die Erweiterung von HTML mit zusätzlichen Attributen, die benutzerdefinierte Semantik übermitteln.  
  
 ARIA bietet einen Standardsatz von erweiterten Attributen, die auf HTML-Elemente angewandt werden können, die in einem Steuerelement oder einem "Widget" verwendet werden. Diese Attribute beschreiben die Rolle, die das HTML-Element im Steuerelement spielt. ARIA bietet auch Funktionen, um die Navigationserfahrung zu verbessern und den Benutzer auf Elemente aufmerksam zu machen, die dynamisch aktualisiert werden können. Das empfohlene Verfahren besteht darin, semantisches HTML mit ARIA zu überlagern.  
  
 Zusätzlich zum Einschließen von Unterstützung für AT müssen noch weitere Anforderungen berücksichtigt werden. Wie passt sich beispielsweise die Benutzeroberfläche an, wenn der Benutzer die Textgröße vergrößert? Muss der Benutzer auf der Benutzeroberfläche Farben unterscheiden können, um Aufgaben auszuführen? Können alle Aktionen ausgeführt werden, indem eine Tastatur verwendet wird? Weitere Informationen finden Sie unter [Einführung in Web-Barrierefreiheit](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh452681(v=win.10)).
  
<a name="BKMK_SilverlightWebResources"></a>   
## <a name="accessible-silverlight-web-resources"></a>Barrierefreie Silverlight-Webressourcen  
 Silverlight-Webressourcen werden in einem Formular oder einer HTML-Webressource gehostet und die Benutzeroberfläche wird vom Silverlight-Browser-Plug-in gerendert. Silverlight ist eine Teilmenge von Windows Presentation Frameworks (WPF) und daher werden der programmgesteuerter Zugriff und AT über UIA verfügbar gemacht, dass WPF-Windows-Anwendungen ähnelt. Weitere Informationen finden Sie unter [Silverlight-Barrierefreiheit für Entwickler](https://docs.microsoft.com/en-us/previous-versions/windows/).  
  
<a name="BKMK_AccessiblityTestingTools"></a>   
## <a name="accessibility-testing-tools"></a>Tools zum Testen der Barrierefreiheit  
 Die folgende Liste enthält einige öffentlich verfügbare Tools zum Testen der Barrierefreiheit:  
  
 [Visual Studio-Barrierefreiheitsprüfung](https://msdn.microsoft.com/library/ms228004)  <!--TODO No relevant microsoft docs link--> Wenn Sie Visual Studio verwenden, um Ihre HTML-Webressourcendateien zu bearbeiten, werden Sie feststellen, dass integrierte Tools vorhanden sind, mit denen nach Barrierefreiheitproblemen gesucht werden kann. Wählen Sie im Menü **Extras** die Option **Barrierefreiheit überprüfen**, um einen Bericht anzuzeigen, der Anleitungen im Hinblick auf Barrierefreiheitprobleme bietet.  
  
 [Benutzeroberflächen-Barrierefreiheitsprüfung](http://acccheck.codeplex.com/)  
 Benutzeroberflächen-Barrierefreiheitsprüfung (oder AccChecker) aktiviert Prüfvorrichtungen, um auf einfache Weise Barrierefreiheitsprobleme mit Microsoft Active Accessibility (MSAA) und anderen Benutzeroberflächenimplementierungen für Windows zu finden. AccChecker entstammt der Erkenntnis, dass vorhandene Windows Automatisierungs-API-Tools, wie beispielsweise Inspect, zwar detaillierte Details über die Implementierung bereitstellen, jedoch keine Informationen im Hinblick darauf, ob eine Implementierung korrekt ist oder nicht.  
  
 [Inspect (Inspect.exe)](https://docs.microsoft.com/en-us/windows/desktop/WinAuto/inspect-objects)  
 Inspect (Inspect.exe) ist ein Windows-basiertes Tool, mit dem Sie ein beliebiges Benutzeroberflächenelement auswählen und die Barrierefreiheitsdaten des Elements anzeigen können. Sie können Eigenschaften und Steuerelementmuster der Microsoft-Benutzeroberflächenautomatisierung zusätzlich zu Microsoft Active Accessibility-Eigenschaften anzeigen. Mithilfe von Inspect können Sie außerdem die Navigationsstruktur der Automatisierungselemente in der Benutzeroberflächenautomatisierungs-Struktur sowie die barrierefreien Objekte in der Microsoft Active Accessibility-Hierarchie testen.  
  
 [Accessible Event Watcher (AccEvent.exe)](https://docs.microsoft.com/en-us/windows/desktop/WinAuto/accessible-event-watcher)  
 Mit dem Accessible Event Watcher (AccEvent) können Entwickler und Tester überprüfen, ob die Benutzeroberflächenelemente einer Anwendung entsprechende Microsoft-Benutzeroberflächenautomatisierungs- und Microsoft Active Accessibility-Ereignisse aktivieren, wenn Änderungen der Benutzeroberfläche eintreten. Änderungen der Benutzeroberfläche können eintreten, wenn sich der Fokus ändert oder wenn ein Benutzeroberflächenelement aufgerufen oder ausgewählt wird bzw. eine Status- oder Eigenschaftenänderung aufweist.
  
<a name="BKMK_AdditionalResources"></a>   
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
 Die folgenden Ressourcen bieten einen Ausgangspunkt zum Definieren von Anforderungen zum Erreichen von Barrierefreiheit für Ihre Webressourcen:  
  
-   [CRM, Barrierefreiheit und 508](http://blogs.msdn.com/b/devkeydet/archive/2013/01/29/crm-accessibility-and-508.aspx)  
  
-   [Einführung in Web-Barrierefreiheit](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh452681(v=win.10))  
  
-   [Barrierefreiheit in Visual Studio und der ASP.NET](https://msdn.microsoft.com/library/ms228004) <!--TODO No relevant microsoft docs link-->
  
-   [Silverlight-Barrierefreiheit für Entwickler](https://docs.microsoft.com/en-us/previous-versions/windows/)  
  
-   [Barrierefreiheit – Übersicht](https://developer.microsoft.com/en-us/windows/accessible-apps)  
  
-   [Barrierefreiheit – W3C](http://www.w3.org/standards/webdesign/accessibility)  
  
-   [Richtlinien für barrierefreie Webinhalte (WCAG) 2.0](http://www.w3.org/TR/WCAG20/)  
  
### <a name="see-also"></a>Siehe auch  
 [Webseite (HTML)-Webressourcen](webpage-html-web-resources.md)   
 [Silverlight (XAP)-Webressourcen](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)<br/>   <!--TODO No relevant topic in powerapps repo--> [Webressourcen](web-resources.md)
