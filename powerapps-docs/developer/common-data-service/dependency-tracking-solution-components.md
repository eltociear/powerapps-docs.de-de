---
title: Abhängigkeitsnachverfolgung für Lösungskomponenten (Common Data Service) | Microsoft-Dokumentation
description: Mithilfe der Komponentenabhängigkeiten kann sichergestellt werden, dass Sie beim Verwenden von Lösungen über eine zuverlässige Umgebung verfügen. Diese können in der Anwendung angezeigt werden, indem Sie auf "Abhängigkeiten anzeigen" klicken
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 538c26f0f0a0dfbd1347137e0086945783dec441
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156254"
---
# <a name="dependency-tracking-for-solution-components"></a>Abhängigkeitsnachverfolgung für Lösungskomponenten

Lösungen bestehen aus Lösungskomponenten. Sie können den Bereich **Lösungen** in Common Data Service verwenden, um Lösungskomponenten zu erstellen oder hinzuzufügen. Sie können diese Aktionen programmgesteuert ausführen, indem Sie die Meldung <xref:Microsoft.Crm.Sdk.Messages.AddSolutionComponentRequest> verwenden, oder eine beliebige Meldung, die Lösungskomponenten erstellt oder aktualisiert, die einen `SolutionUniqueName`-Parameter enthalten.  
  
 Lösungskomponenten sind oft von anderen Lösungskomponenten abhängig. Sie können keine Lösungskomponente löschen, von der andere Lösungskomponenten abhängig sind. Beispielsweise benötigt ein benutzerdefiniertes Menüband normalerweise Bild- oder Skript-Webressourcen, um Symbole anzuzeigen und Aktionen mithilfe von Skripts auszuführen. Solange das benutzerdefinierte Menüband Bestandteil der Lösung ist, werden verwendeten die Webressourcen benötigt. Bevor Sie die Webressourcen löschen können, müssen Sie diese Referenzen im benutzerdefinierten Menüband entfernen. Diese Abhängigkeiten der Lösungskomponenten können in der Anwendung angezeigt werden, indem Sie auf **Abhängigkeiten anzeigen** klicken.  
  
 Dieses Thema beschreibt die Typen von Lösungskomponenten, die Sie in Ihre Lösungen integrieren können, und wie diese voneinander abhängig sind.  
  
<a name="bkmk_SolutionComponents"></a>   

## <a name="all-solution-components"></a>Alle Lösungskomponenten  
 Die vollständige Liste aller verfügbaren Lösungskomponententypen ist im globalen Optionssatz `componenttype` des Systems zu finden. Der unterstützte Wertebereich für diese Eigenschaft wird verfügbar, indem Sie die Datei `OptionSets.cs` oder `OptionSets.vb` in Ihr Projekt integrieren. Viele der hier aufgeführten Lösungskomponententypen sind jedoch nur für den internen Gebrauch bestimmt, und die Liste enthält keine Informationen zu den Beziehungen zwischen Lösungskomponenten.  
  
<a name="BKMK_SolutionComponentDependencies"></a>   

## <a name="solution-component-dependencies"></a>Lösungskomponentenabhängigkeiten  
 Mithilfe der Komponentenabhängigkeiten kann sichergestellt werden, dass Sie beim Verwenden von Lösungen über eine zuverlässige Umgebung verfügen. So wird verhindert, das mit üblicherweise ausgeführten Aktionen versehentlich Anpassungen beschädigt werden, die in einer Lösung definiert sind. Durch die Abhängigkeiten wird ermöglicht, dass eine verwaltete Lösung durch das einfache Importieren oder Löschen einer neuen Lösung installiert und deinstalliert wird.  
  
 Durch das Solutions Framework werden Abhängigkeiten für Lösungskomponenten automatisch überwacht. Jeder Vorgang über eine Lösungskomponente berechnet automatisch alle Abhängigkeiten zu anderen Komponenten im System. Die Abhängigkeitsinformationen werden verwendet, um die Integrität des Systems beizubehalten und Vorgänge zu verhindern, die zu einem inkonsistenten Zustand führen können.  
  
 Die Abhängigkeitsüberwachung erzwingt die folgenden Verhaltensweisen:  
  
- Das Löschen einer Komponente wird verhindert, wenn eine andere Komponente im System von ihr abhängig ist.  
  
- Beim Exportieren einer Lösung wird der Benutzer gewarnt, falls eine Komponente fehlen sollte und der Import der Daten in ein anderes System dadurch fehlschlagen kann.  
  
   Warnungen können während des Exports ignoriert werden, wenn der Lösungsentwickler beabsichtigt, die Lösung in nur einer Organisation zu installieren, in der die abhängigen Komponenten vorhanden sind. Ein Beispiel wäre, dass Sie eine Lösung erstellen, die dafür konzipiert wurde, über eine vorinstallierten "Basis"-Lösung installiert zu werden.  
  
- Das Importieren einer Lösung ist nicht erfolgreich, falls nicht alle erforderlichen Komponenten in der Lösung enthalten sind und auch nicht in dem Zielsystem vorhanden sind.  
  
  -   Wenn Sie außerdem eine verwaltete Lösung importieren, müssen alle erforderlichen Komponenten mit dem Pakettyp der Lösung übereinstimmen. Eine Komponente in einer verwalteten Lösung kann nur von einer anderen verwalteten Komponente abhängig sein.  
  
  Es gibt drei Arten von Lösungskomponentenabhängigkeiten:  
  
  **Lösungsintern**  
  Interne Abhängigkeiten werden von Common Data Service verwaltet. Diese sind dann vorhanden, wenn eine bestimmte Lösungskomponente nicht ohne eine andere Lösungskomponente verwendet werden kann.  
  
  **Veröffentlicht**  
  Veröffentlichte Abhängigkeiten werden erstellt, wenn zwei Lösungskomponenten miteinander verknüpft sind und dann veröffentlicht werden. Um diese Art von Abhängigkeit zu entfernen, müssen Sie die Zuordnung entfernen und anschließend die Entitäten erneut veröffentlichen.  
  
  **Unveröffentlicht**  
  Unveröffentlichte Abhängigkeiten gelten für die unveröffentlichte Version einer veröffentlichbaren Lösungskomponente, die gerade aktualisiert wird. Nachdem die Lösungskomponente veröffentlicht wurde, wird sie zu einer veröffentlichten Abhängigkeit.  
  
  Lösungsinterne Abhängigkeiten sind Abhängigkeiten, bei denen für die Aktion mit einer Lösungskomponente die Aktion einer anderen Lösungskomponente erforderlich ist. Wenn Sie z. B. eine Entität löschen, erwarten Sie, dass mit dem Löschen alle Attribute der Entität ebenfalls gelöscht werden. Alle Entitätsbeziehungen zu anderen Entitäten werden auch gelöscht.  
  
  Es ist jedoch möglich, dass eine interne Abhängigkeit mit einer veröffentlichten Abhängigkeit verknüpft ist und daher weiterhin eine manuelle Bearbeitung erfordert. Wenn Sie beispielsweise ein Suchfeld in ein Entitätsformular integriert haben und die primäre Entität in der Beziehung löschen, können Sie den Löschvorgang solange nicht abschließen, bis Sie das Suchfeld aus dem verknüpften Entitätsformular entfernen und das Formular erneut veröffentlichen.  
  
  Wenn Sie programmgesteuerte Aktionen ausführen, können Sie Nachrichten verwenden, die mit der Entität `Dependency` zusammenhängen. Weitere Informationen zu Nachrichten, die Sie verwenden können, um vorhandene Abhängigkeiten zu ermitteln, bevor Sie eine Komponente löschen oder eine Lösung deinstallieren, finden Sie unter [Abhängigkeitsentität](/reference/entities/dependency.md).  
  
<a name="BKMK_CheckForSolutionComponentDependencies"></a>   
## <a name="check-for-solution-component-dependencies"></a>Überprüfen der Abhängigkeiten von Komponentenlösungen  
 Wenn Sie Lösungen bearbeiten, kommt es möglicherweise vor, dass Sie eine Lösungskomponente nicht löschen können, da sie in einer veröffentlichten Abhängigkeit zu einer anderen Lösungskomponente steht. Oder Sie können unter Umständen eine verwaltete Lösung nicht deinstallieren, da eine der Komponenten in der verwalteten Lösung für eine Anpassung in einer anderen unverwalteten Lösung verwendet wurde.  
  
 In der folgenden Tabelle sind die Meldungen aufgeführt, die Sie verwenden können, um Daten über Lösungskomponentenabhängigkeiten abzurufen.  
  
|Meldung|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDependentComponentsRequest>|Gibt eine Liste der Abhängigkeiten für Lösungskomponenten zurück, die direkt von einer Lösungskomponente abhängen.<br /><br /> Wenn Sie z. B. diese Nachricht für eine globale Optionssatzlösungskomponente verwenden, werden die Abhängigkeitsdatensätze für Lösungskomponenten zurückgegeben, die Optionssatzattribute darstellen, die auf die Optionssatzlösungskomponente verweisen.<br /><br /> Wenn Sie diese Meldung für den Lösungskomponentendatensatz der Firmenentität verwenden, werden die Abhängigkeitsdatensätze für alle Lösungskomponenten zurückgegeben, die Attribute, Ansichten und Formularen darstellen, die für diese Entität verwendet werden.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveRequiredComponentsRequest>|Gibt eine Liste der Abhängigkeiten für Lösungskomponenten zurück, von denen eine andere Lösungskomponente direkt abhängig ist. Diese Meldung gibt das Gegenteil der `RetrieveDependentComponentsRequest`-Meldung aus.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDependenciesForDeleteRequest>|Gibt eine Liste aller Abhängigkeiten für Lösungskomponenten zurück, die das Löschen einer Lösungskomponente verhindern könnten.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveDependenciesForUninstallRequest>|Gibt eine Liste aller Abhängigkeiten für Lösungskomponenten zurück, die die Deinstallation einer verwalteten Lösungskomponente verhindern könnten.|  
  
<a name="BKMK_RootSolutionComponents"></a>   
## <a name="common-solution-components"></a>Allgemeine Lösungskomponenten  
 Dies sind die Lösungskomponenten, die in der Anwendung und in den Komponenten angezeigt werden, mit denen Sie direkt arbeiten werden, wenn Sie mithilfe der Lösungsseite Lösungskomponenten hinzufügen oder entfernen. Jeder der anderen Typen von Lösungskomponenten ist von mindestens einer dieser Lösungskomponenten anhängig.  
  
||||  
|-|-|-|  
|[Anwendungsmenübänder (RibbonCustomization)](dependency-tracking-solution-components.md#BKMK_RibbonCustomization)|[Entität (Entity)](dependency-tracking-solution-components.md#BKMK_Entity)|[Bericht (Report)](dependency-tracking-solution-components.md#BKMK_Report)|  
|[Artikelvorlage (KBArticleTemplate)](dependency-tracking-solution-components.md#BKMK_KBArticleTemplate)|[Feldsicherheitsprofil (FieldSecurityProfile)](dependency-tracking-solution-components.md#BKMK_FieldSecurityProfile)|[SDK-Nachrichtenverarbeitungsschritt (SDKMessageProcessingStep)](dependency-tracking-solution-components.md#BKMK_SDKMessageProcessingStep)|  
|[Verbindungsrolle (ConnectionRole)](dependency-tracking-solution-components.md#BKMK_ConnectionRole)|[Seriendruckvorlage (MailMergeTemplate)](dependency-tracking-solution-components.md#BKMK_MailMergeTemplate)|[Sicherheitsrolle (Role)](dependency-tracking-solution-components.md#BKMK_Role)|  
|[Vertragsvorlage (ContractTemplate)](dependency-tracking-solution-components.md#BKMK_ContractTemplate)|[Optionssatz (OptionSet)](dependency-tracking-solution-components.md#BKMK_OptionSet)|[Dienstendpunkt (ServiceEndpoint)](dependency-tracking-solution-components.md#BKMK_ServiceEndpoint)|  
|[Dashboard oder Entitätsformular (SystemForm)](dependency-tracking-solution-components.md#BKMK_SystemForm)|[Plug-In-Assembly (PluginAssembly)](dependency-tracking-solution-components.md#BKMK_PluginAssembly)|[Siteübersicht (SiteMap)](dependency-tracking-solution-components.md#BKMK_SiteMap)|  
|[E-Mail-Vorlage (EmailTemplate)](dependency-tracking-solution-components.md#BKMK_EmailTemplate)|[Prozess (Workflow)](dependency-tracking-solution-components.md#BKMK_Workflow)|[Webressource (WebResource)](dependency-tracking-solution-components.md#BKMK_WebResource)|  
  
<a name="BKMK_RibbonCustomization"></a>   
### <a name="application-ribbons-ribboncustomization"></a>Anwendungsmenübänder (RibbonCustomization)  
 Menübandanpassungen für die Anwendungs- und Entitätsmenübandvorlagen. Anwendungsmenübänder schließen keine Definitionen von Menübändern auf Entitäts- oder Formularebene ein.  
  
 Benutzerdefinierte Anwendungsmenübänder weisen häufig eine veröffentlichte Abhängigkeit von Webressourcen auf. Webressourcen werden verwendet, um Menübandschaltflächensymbole und JavaScript-Funktionen zu definieren und so zu steuern, wann Menübandelemente angezeigt werden oder welche Aktionen ausgeführt werden, wenn ein bestimmtes Menübandsteuerelement verwendet wird. Abhängigkeiten werden erstellt nur, wenn die Menübanddefinitionen die `$webresource:`-Direktive verwenden, um die Webressource mit dem Menüband zu verknüpfen. Weitere Informationen: [$webresource-Direktive](/dynamics365/customer-engagement/developer/web-resources#BKMK_WebResourceDirective).  
  
<a name="BKMK_KBArticleTemplate"></a>   
### <a name="article-template-kbarticletemplate"></a>Artikelvorlage (KBArticleTemplate)  
 Vorlage, die die Standardattribute eines Artikels enthält. Es besteht immer eine interne Abhängigkeit zwischen der Artikelvorlage und der KbArticle-Entität.  
  
<a name="BKMK_ConnectionRole"></a>   
### <a name="connection-role-connectionrole"></a>Verbindungsrolle (ConnectionRole)  
 Rolle, die die Beziehung zwischen zwei Datensätzen beschreibt. Jede Verbindungsrolle definiert, welche Typen von Entitätsdatensätzen mithilfe der Verbindungsrolle verknüpft werden können. Dadurch wird eine veröffentlichte Abhängigkeit zwischen der Verbindungsrolle und der Entität erstellt.  
  
<a name="BKMK_ContractTemplate"></a>   
### <a name="contract-template-contracttemplate"></a>Vertragsvorlage (ContractTemplate)  
 Vorlage, die die Standardattribute eines Vertrags enthält. Es besteht immer eine interne Abhängigkeit zwischen der Vertragsvorlagen und der Vetragsentität.  
  
<a name="BKMK_SystemForm"></a>   
### <a name="dashboard-or-entity-form-systemform"></a>Dashboard oder Entitätsformular (SystemForm)  
 Systemformularentitätsdatensätze werden verwendet, um Dashboards und Entitätsformulare zu definieren. Wenn ein SystemForm als ein Entitätsformular verwendet wird, besteht eine interne Abhängigkeit von der Entität. Wenn ein SystemForm als Dashboard verwendet wird, treten keine internen Abhängigkeiten auf. Entitätsformulare und Dashboards weisen normalerweise auf ihrem Inhalt basierende veröffentlichte Abhängigkeiten auf. Bei einem Entitätsformular können Suchfelder vorkommen, die von einer Entitätsbeziehung abhängen. Dashboards und Entitätsformulare enthalten möglicherweise Diagramme oder Unterraster, die eine veröffentlichte Abhängigkeit von einer Ansicht erstellen, die dann eine interne Abhängigkeit von eine Entität aufweist. Eine veröffentlichte Abhängigkeit von Webressourcen kann aufgrund des Inhalt erstellt werden, der im Dashboard oder im Formular angezeigt wird, oder wenn ein Formular JavaScript-Bibliotheken enthält. Entitätsformulare weisen eine veröffentlichte Abhängigkeiten von allen Attributen auf, die als Felder im Formular angezeigt werden.  
  
<a name="BKMK_EmailTemplate"></a>   

### <a name="email-template-emailtemplate"></a>E-Mail-Vorlage (EmailTemplate)  
 Vorlage, in der die Standardattribute einer E-Mail-Nachricht enthalten sind. Eine E-Mail-Vorlage enthält in der Regel Felder, die Daten aus angegebenen Entitätsattributen einfügen. Eine E-Mail-Vorlage kann bei ihrer Erstellung mit einer bestimmten Entität verknüpft werden, sodass eine interne Abhängigkeit von der Entität möglich wird. Eine globale E-Mail-Vorlage wird nicht mit einer bestimmten Entität verknüpft, aber sie weist möglicherweise veröffentlichte Abhängigkeiten von Entitätsattributen auf, die verwendet werden, um Daten bereitzustellen. Ein Prozess (Workflow) wird häufig so konfiguriert, dass eine E-Mail gesendet werden kann, die auf einer E-Mail-Vorlage basiert, wodurch eine veröffentlichte Abhängigkeit mit dem Workflow erstellt wird.  
  
<a name="BKMK_Entity"></a>   

### <a name="entity-entity"></a>Entität (Entity)  
 Die primäre Struktur, die verwendet wird, um Daten in Common Data Service zu modellieren und zu verwalten. Diagramme, Formulare, Entitätsbeziehungen, Ansichten und Attribute, die einer Entität zugeordnet sind, werden automatisch gelöscht, wenn die Entität aufgrund der internen Abhängigkeiten zwischen ihnen gelöscht wird. Entitäten weisen oft veröffentlichte Abhängigkeiten von Prozessen, Dashboards und E-Mail-Vorlagen auf.  
  
<a name="BKMK_FieldSecurityProfile"></a>   
### <a name="field-security-profile-fieldsecurityprofile"></a>Feldsicherheitsprofil (FieldSecurityProfile)  
 Profil, das die Zugriffsebene für gesicherte Attribute definiert.  
  
<a name="BKMK_MailMergeTemplate"></a>   
### <a name="mail-merge-template-mailmergetemplate"></a>Seriendruckvorlage (MailMergeTemplate)  
 Vorlage, die die Standardattribute eines Seriendruckdokuments enthält. Eine Seriendruckvorlage weist eine veröffentlichte Abhängigkeit von der Entität auf, mit der sie verknüpft ist.  
  
<a name="BKMK_OptionSet"></a>   
### <a name="option-set-optionset"></a>Optionssatz (OptionSet)  
 Ein Optionssatz definiert einen Satz von Optionen. Ein Auswahllistenattribut verwendet einen Optionssatz, um die bereitgestellten Optionen zu definieren. Einige Auswahllistenattribute verwenden möglicherweise einen globalen Optionssatz, sodass die Optionen, die sie bereitstellen, immer dieselben sind und an einem Ort verwaltet werden können. Eine veröffentlichte Abhängigkeit tritt auf, wenn ein Auswahllistenattribut auf einen globalen Optionssatz verweist. Sie können einen globalen Optionssatz nicht löschen, der durch ein Auswahllistenattribut verwendet wird.  
  
<a name="BKMK_PluginAssembly"></a>   
### <a name="plug-in-assembly-pluginassembly"></a>Plug-In-Assembly (PluginAssembly)  
 Assembly, die mindestens einen Plug-In-Typ enthält. Plug-Ins werden für Ereignisse registriert, die einer Entität typischerweise zugeordnet sind. Dadurch wird eine veröffentlichte Abhängigkeit erstellt.  
  
<a name="BKMK_Workflow"></a>   
### <a name="process-workflow"></a>Prozess (Workflow)  
 Satz an logischen Regeln, die die erforderlichen Schritte zum Automatisieren eines bestimmten Geschäftsprozesses, einer bestimmten unternehmerischen Aufgabe oder einer Gruppe von auszuführenden Aktionen definieren. Prozesse stellen ein großes Angebot an Aktionen bereit, die veröffentlichte Abhängigkeiten von jeder anderen Lösungskomponente erstellen, auf die durch den Prozess verwiesen wird. Jeder Prozess weist auch eine veröffentlichte Abhängigkeit von der Entität auf, mit der er verknüpft ist.  
  
<a name="BKMK_Report"></a>   
### <a name="report-report"></a>Bericht (Report)  
 Datenzusammenfassung in einem leicht lesbaren Layout. Ein Bericht weist veröffentlichte Abhängigkeiten von allen Entitäts- oder Attributdaten auf, die im Bericht enthalten sind. Jeder Bericht muss auch einer Berichtskategorie zugeordnet werden, die eine interne Abhängigkeit zu einer Lösungskomponente erstellt, die als berichtsbezogene Kategorie (ReportCategory) bezeichnet wird. Berichte können so konfiguriert werden,dass sie Unterberichte darstellen, die eine veröffentlichte Abhängigkeit von dem übergeordneten Bericht erstellen.  
  
<a name="BKMK_SDKMessageProcessingStep"></a>   
### <a name="sdk-message-processing-step-sdkmessageprocessingstep"></a>Nachrichtenverarbeitungsschritt (SDKMessageProcessingStep)  
 Phase in der Ausführungspipeline, die als Plug-In ausgeführt werden soll.  
  
<a name="BKMK_Role"></a>   
### <a name="security-role-role"></a>Sicherheitsrolle (Role)  
 Gruppieren von Sicherheitsrechten. Benutzern werden Rollen zugewiesen, die ihren Zugriff auf das Common Data Service-System autorisieren. Entitätsformulare können bestimmten Sicherheitsrollen zugeordnet werden, um zu steuern, wer das Formular anzeigen kann. Dadurch wird eine veröffentlichte Abhängigkeit zwischen der Sicherheitsrolle und dem Formular erstellt.  
  
> [!NOTE]
>  Nur Sicherheitsrollen aus der Unternehmenseinheit der Organisation können einer Lösung hinzugefügt werden. Nur Benutzer mit Lesezugriff auf diese Sicherheitsrollen können sie einer Lösung hinzufügen.  
  
<a name="BKMK_ServiceEndpoint"></a>   
### <a name="service-endpoint-serviceendpoint"></a>Dienstendpunkt (ServiceEndpoint)  
 Dienstendpunkt, der kontaktiert werden kann.  
  
<a name="BKMK_SiteMap"></a>   
### <a name="site-map-sitemap"></a>Siteübersicht (SiteMap)  
 XML-Daten zum Steuern des Navigationsbereichs der Anwendung. Die Siteübersicht ist möglicher weise so verlinkt, dass eine HTML-Webressource angezeigt wird, oder ein Symbol in der Siteübersicht verwendet möglicherweise eine Bild-Webressource. Wenn die `$webresource:`-Direktive verwendet wird, um diese Zuordnungen festzulegen, wird eine veröffentlichte Abhängigkeit erstellt. Weitere Informationen: [$webresource-Direktive](/dynamics365/customer-engagement/developer/web-resources#BKMK_WebResourceDirective).  
  
<a name="BKMK_WebResource"></a>   
### <a name="web-resource-webresource"></a>Webressource (WebResource)  
 Datenentsprechung zu Dateien, die in der Webentwicklung verwendet werden. Webressourcen bieten clientseitige Komponenten, die verwendet werden, um benutzerdefinierte Benutzeroberflächenelemente bereitzustellen. Webressourcen weisen möglicherweise veröffentlichte Abhängigkeiten von Entitätsformularen, Menübändern und SiteMap auf. Wenn die `$webresource:`-Direktive verwendet wird, um diese Zuordnungen in einem Menüband oder SiteMap festzulegen, wird eine veröffentlichte Abhängigkeit erstellt. Weitere Informationen finden Sie unter [$webresource-Direktive](/dynamics365/customer-engagement/developer/web-resources#BKMK_WebResourceDirective).  
  
> [!NOTE]
>  Webressourcen sind möglicherweise von anderen Webressourcen abhängig, je nach den vorhandenen relativen Links. Z. B. verwendet eine HTML-Webressource möglicherweise eine CSS oder Skript-Webressource. Eine Silverlight-Webressource, die außerhalb eines Entitätsformulars oder Diagramms angezeigt wird, muss über eine HTML-Webressource verfügen muss, auf der sie gehostet ist. Diese Abhängigkeiten werden nicht als Lösungsabhängigkeiten überwacht.  
  
### <a name="see-also"></a>Siehe auch  
 [Packen und Verteilen von Erweiterungen mithilfe von Dynamics 365-Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Einführung zu Lösungen](introduction-solutions.md)   
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Erstellen, Exportieren oder Importieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Deinstallieren oder Löschen einer Lösung](uninstall-delete-solution.md)   
 [Lösungsentitäten](/dynamics365/customer-engagement/developer/solution-entities)