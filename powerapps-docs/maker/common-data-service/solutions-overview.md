---
title: Arbeiten mit Lösungen in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Lösungen verteilt werden'
ms.custom: ''
ms.date: 05/28/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: ece68f5f-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
   
# <a name="solutions-overview"></a>Überblick über Lösungen  

  In PowerApps werden Lösungen genutzt, um Apps und Komponenten von einer Umgebung in eine andere zu transportieren oder um einen Satz von Anpassungen für vorhandene Apps zu übernehmen. Eine Lösung kann mindestens eine App sowie andere Komponenten, wie Entitäten, Optionssätze usw. enthalten. Sie können eine Lösung aus [AppSource](https://appsource.microsoft.com/) oder durch einen unabhängigen Softwarehersteller (ISV) erhalten.
  
Mehr Informationen: [Whitepaper: Lösungs-Lebenszyklus-Management](https://www.microsoft.com/en-us/download/details.aspx?id=57777)  
  
> [!NOTE]
>  Als ISV, der eine App erstellt, die Sie verteilen werden, müssen Sie Lösungen verwenden. Weitere Informationen zum Verwenden von Lösungen finden Sie unter [Entwicklerhandbuch: Einführung in Lösungen](/powerapps/developer/common-data-service/introduction-solutions).  
  
 Wenn Sie daran interessiert sind, PowerApps-Anwendungen für den organisatorischen Einsatz zu erstellen oder Dynamics 365 for Customer Engagement-Anwendungen anzupassen, erfahren Sie hier, was Sie über Lösungen wissen müssen:  
  
-   Das Erstellen von Lösungen ist optional. Sie können Anwendungen direkt in Ihrer PowerApps-Umgebung erstellen oder anpassen, ohne jemals eine Lösung zu erstellen.  
  
-   Wenn Sie die PowerApps Umgebung direkt anpassen, ohne eine Lösung zu erstellen, arbeiten Sie mit einer speziellen Lösung namens **Standardlösung von Common Data Service**. Diese Lösung enthält alle Anpassungen, die Sie in der PowerApps-Umgebung erstellen.  
  
-   Es gibt eine andere spezielle Lösung, die **Standardlösung** genannt wird. Diese Lösung enthält alle Komponenten in Ihrem System, egal, ob sie von Ihnen oder einem anderen Benutzer erstellt wurde. Sie können die **Standardlösung** exportieren, um ein Backup der Anpassungen, die Sie in Ihrer Organisation definiert haben, zu erstellen. Dies ist eine bewährte Methode, um Ihre Änderungen für den schlimmsten Fall zu sichern.  
  
<a name="BKMK_SolutionComponents"></a>   
### <a name="components"></a>Komponenten  
 Eine Komponente steht für etwas, das Sie anpassen können. Alles, was Bestandteil einer Lösung sein kann, ist eine Komponente. Nachfolgend finden Sie eine Liste von Komponenten, die Sie in einer Lösung anzeigen können:  
  
-   Anwendungsmenüband  
  
-   Artikelvorlage  
  
-   Geschäftsregel  

-   Canvas-App 
  
-   Diagramm  
  
-   Verbindungsrolle  
  
-   Vertragsvorlage  
 
-   Benutzerdefiniertes Steuerelement
  
-   Informationsleiste  
  
-   E-Mail-Vorlage  
  
-   Entität  
  
-   Entitätsbeziehung  
  
-   Feld  
  
-   Feldsicherheitsprofil  

-   Flow
  
-   Formular  
  
-   Seriendruckvorlage  
  
-   Meldung  

-   Modellgesteuerte App
  
-   Optionssatz  
  
-   Plug-In-Assembly  
  
-   Prozess  
  
-   SDK-Nachrichtenverarbeitungsschritt  
  
-   Sicherheitsrolle  
  
-   Dienstendpunkt  
  
-   Siteübersicht  

-   Virtueller Entitätsdatenanbieter

-   Virtuelle Entitätsdatenquelle
  
-   Webressource  
  
 Einige Komponenten werden in anderen Komponenten geschachtelt. Zum Beispiel enthält eine Entität Formulare, Ansichten, Diagramme, Felder, Entitätsbeziehungen, Nachrichten und Geschäftsregeln. Jede dieser Komponenten erfordert eine Entität. Ein Feld kann nicht außerhalb einer Entität existieren. Wir sprechen davon, dass das Feld von der Entität abhängt. Es gibt tatsächlich zweimal so viele Arten von Komponenten wie in der vorherigen Liste angegeben, die meisten davon sind jedoch nicht in anderen Komponenten geschachtelt und sind in der Anwendung nicht sichtbar.  
  
 Der Zweck von Komponenten besteht darin, alle Einschränkungen hinsichtlich der Anpassbarkeit mit verwalteten Eigenschaften, und alle Abhängigkeiten nachzuverfolgen, sodass sie exportiert, importiert und (in verwalteten Lösungen) restlos gelöscht werden können.  
  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
### <a name="managed-and-unmanaged-solutions"></a>Verwaltete und nicht verwaltete Lösungen  
 Es gibt **verwaltete** und **nicht verwaltete** Lösungen. Eine **verwaltete** Lösung kann nicht geändert werden und kann nach dem Import deinstalliert werden. Dadurch werden alle Komponenten der Lösung entfernt.  
  
 Wenn Sie eine **nicht verwaltete** Lösung importieren, fügen Sie alle Komponenten dieser Lösung der Umgebung hinzu. Sie können die Komponenten nicht entfernen, indem Sie die Lösung deinstallieren.  
  
 Wenn Sie eine **nicht verwaltete** Lösung importieren, die bereits von Ihnen angepasste Komponenten enthält, werden Ihre Anpassungen von den Anpassungen in der importierten nicht verwalteten Lösung überschrieben. Sie können dies nicht rückgängig machen.  
  
> [!IMPORTANT]
>  Installieren Sie eine nicht verwaltete Lösung nur, wenn Sie alle Komponenten Ihrer Umgebung hinzufügen wollen und alle vorhandenen Anpassungen überschrieben werden sollen.  
  
 Selbst wenn Sie Ihre Apps oder Anpassungen nicht verteilen wollen, sollten Sie eine nicht verwaltete Lösung so erstellen und verwenden, dass sie über eine separate Ansicht verfügt, die nur die Teile der Anwendung enthält, die Sie angepasst haben. Wenn Sie irgend etwas anpassen, fügen Sie es einfach der nicht verwalteten Lösung hinzu, die Sie erstellt haben.  
  
 Sie können Ihre **Standardlösung** nur als nicht verwaltete Lösung exportieren.  
  
 Zur Erstellung einer **verwalteten** Lösung wählen Sie die Option **Als verwaltet** aus, wenn Sie die Lösung exportieren. Wenn Sie eine verwaltete Lösung erstellen, können Sie sie nicht wieder in die Umgebung importieren, die Sie für die Erstellung verwendet haben. Sie können sie nur in eine andere Umgebung importieren werden.  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### <a name="how-solutions-are-applied"></a>Wie Lösungen angewendet werden  
 Alle Lösungen werden als Ebenen evaluiert, um zu bestimmen, was Ihre App tatsächlich tun wird. Das folgende Diagramm zeigt, wie verwaltete und nicht verwaltete Lösungen evaluiert werden, und wie Änderungen an ihnen in Ihrer Umgebung erscheinen.  
  
 ![Lösungsebenen](media/solution-layering.png "Lösungsebenen")  
  
 Von unten nach oben:  
  
 **Systemlösung**  
 Die ist Systemlösung entspricht einer verwalteten Lösung, die jede Umgebung hat. Die Systemlösung ist die Definition aller direkt einsetzbaren Komponenten in dem System.  
  
 **Verwaltete Lösungen**  
 Verwaltete Lösungen können die Systemlösungskomponenten ändern und neue hinzufügen. Wenn mehrere verwaltete Lösungen installiert sind, wird die erste unter den später installierten verwalteten Lösungen installiert. Dies bedeutet, dass die zweite installierte Lösung die zuvor installierte anpassen kann. Wenn die Definitionen zweier verwalteter Lösungen Konflikte haben, ist die allgemeine Regel, dass die letzte den Vorzug hat. Wenn Sie eine verwaltete Lösung deinstallieren, wird die verwaltete Lösung darunter wirksam. Wenn Sie die verwaltete Lösung deinstallieren, wird das innerhalb der Systemlösung definierte Standardverhalten angewendet.  
  
 **Nicht verwaltete Anpassungen**  
 Nicht verwaltete Anpassungen sind alle Änderungen, die Sie an Ihrer Umgebung durch eine nicht verwaltete Lösung vornehmen. Die Systemlösung definiert, was Sie mit verwalteten Eigenschaften anpassen können und was nicht. Herausgeber von verwalteten Lösungen haben dieselbe Möglichkeit, Ihre Möglichkeiten zu begrenzen, Lösungskomponenten anzupassen, die sie in ihrer Lösung hinzufügen. Sie können alle Lösungskomponenten anpassen, die keine verwalteten Eigenschaften haben, die Sie an ihrer Anpassung hindern.  
  
 **Anwendungsverhalten**  
 Dies ist, was Sie in Ihrer Umgebung sehen. Die Standardsystemlösung plus alle verwalteten und nicht verwalteten Anpassungen, die Sie vorgenommen haben.  
  
<a name="BKMK_ManagedProperties"></a>   
### <a name="managed-properties"></a>Verwaltete Eigenschaften  
 Einige Komponenten können nicht angepasst werden. Diese Komponenten in der Systemlösung verfügen über Metadaten, die Sie an ihrer Anpassung hindern. Diese werden als **Verwaltete Eigenschaften** bezeichnet. Der Herausgeber einer verwalteten Lösung kann die verwalteten Eigenschaften auch so festlegen, dass Sie seine Lösung nicht in einer Weise anpassen können, die er nicht wünscht.  
  
<a name="BKMK_Dependencies"></a>   
### <a name="solution-dependencies"></a>Lösungsabhängigkeiten  
 Aufgrund der Schichtung verwalteter Lösungen können einige verwaltete Lösungen von Lösungskomponenten in anderen verwalteten Lösungen abhängen. Einige Lösungsherausgeber nutzen dies, um modulare Lösungen zu erstellen. Möglicherweise müssen Sie zuerst eine verwaltete "Basis"-Lösung installieren und können dann eine zweite verwaltete Lösung installieren, die die Komponenten in der ersten verwalteten Lösung weiter anpasst. Die zweite verwaltete Lösung hängt von den Lösungskomponenten ab, die Teil ersten Lösung sind.  
  
 Das System verfolgt diese Abhängigkeiten zwischen Lösungen nach. Wenn Sie versuchen, eine Lösung zu installieren, die eine nicht installierte Basislösung erfordert, können Sie dies nicht tun. Sie erhalten eine Meldung angezeigt, die besagt, dass die Lösung eine andere Lösung erfordert, die zuerst installiert werden muss. Ähnlich gilt, dass Sie aufgrund der Abhängigkeiten die Basislösung nicht deinstallieren können, solange eine Lösung, die von ihr abhängt, noch installiert ist. Sie müssen die abhängige Lösung deinstallieren, bevor Sie die Basislösung deinstallieren können.  
  
  
## <a name="next-steps"></a>Nächste Schritte  
[Importieren, aktualisieren und exportieren von Lösungen](import-update-export-solutions.md) <br/>
[Navigieren zu einer bestimmten Lösung](navigate-specific-solution.md)
 
