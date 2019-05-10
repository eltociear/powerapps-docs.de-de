---
title: Arbeiten mit Lösungen in PowerApps | Microsoft-Dokumentation
description: Informationen zum Verteilen von Lösungen
ms.custom: ''
ms.date: 01/28/2019
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
ms.openlocfilehash: da6b44c4755fa42d6e946cfe5955bba0e78b91c2
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "65038603"
---
# <a name="solutions-overview"></a>Übersicht über Lösungen  

  In PowerApps dienen Lösungen dazu, Apps und Komponenten von einer Umgebung in eine andere zu transportieren oder eine Reihe von Anpassungen auf vorhandene Apps anzuwenden. Eine Lösung kann eine oder mehrere Apps sowie weitere Komponenten wie Entitäten, Optionssätze usw. enthalten.  Sie können eine Lösung aus [AppSource](https://appsource.microsoft.com/) oder von einem unabhängigen Softwareanbieter (Independent Software Vendor, ISV) beziehen.
  
Weitere Informationen finden Sie unter: [Whitepaper: Solution Lifecycle Management](https://www.microsoft.com/en-us/download/details.aspx?id=57777)  
  
> [!NOTE]
>  Wenn Sie als ISV eine App erstellen, die Sie verteilen möchten, müssen Sie Lösungen verwenden. Weitere Informationen zum Verwenden von Lösungen finden Sie im [Entwicklerleitfaden: Einführung in Lösungen](/powerapps/developer/common-data-service/introduction-solutions).  
  
 Wenn Sie PowerApps-Apps zur Verwendung in der Organisation erstellen oder Dynamics 365 für Kundenbindungs-Apps anpassen möchten, müssen Sie über Lösungen Folgendes wissen:  
  
-   Das Erstellen von Lösungen ist optional. Sie können Apps in Ihrer PowerApps-Umgebung erstellen oder anpassen, ohne eine Lösung zu erstellen.  
  
-   Wenn Sie die PowerApps-Umgebung ohne Erstellen einer Lösung direkt anpassen, arbeiten Sie mit einer speziellen Lösung, die als **Common Data Services-Standardlösung** bezeichnet wird. Diese Lösung enthält alle Anpassungen, die Sie in Ihrer PowerApps-Umgebung vornehmen.  
  
-   Es gibt eine weitere spezielle Lösung mit dem Namen **Standardlösung**. Diese Lösung enthält alle Komponenten in Ihrem System, unabhängig davon, ob diese von Ihnen oder jemand anderem erstellt wurden. Sie können die **Standardlösung** exportieren, um eine Sicherung der in Ihrer Organisation definierten Anpassungen zu erstellen. Es empfiehlt sich, Änderungen zu sichern, um sie notfalls rückgängig machen oder wiederherstellen zu können.  
  
<a name="BKMK_SolutionComponents"></a>   
### <a name="components"></a>Komponenten  
 Eine Komponente stellt ein Element dar, das Sie möglicherweise anpassen können. Jedes Element, das Bestandteil einer Lösung sein kann, ist eine Komponente. Die folgende Liste enthält Komponenten, die Sie in einer Lösung anzeigen können:  
  
-   Anwendungsmenüband  
  
-   Artikelvorlage  
  
-   Geschäftsregel  

-   Canvas-App 
  
-   Diagramm  
  
-   Verbindungsrolle  
  
-   Vertragsvorlage  
 
-   Benutzerdefiniertes Steuerelement
  
-   Dashboard  
  
-   E-Mail-Vorlage  
  
-   Einrichtung  
  
-   Entitätsbeziehung  
  
-   Feld  
  
-   Feldsicherheitsprofil  

-   Flow
  
-   Formular  
  
-   Seriendruckvorlage  
  
-   Nachricht  

-   Modellgesteuerte App
  
-   Optionssatz  
  
-   Plug-In-Assembly  
  
-   Prozess  
  
-   Schritt zur Verarbeitung der SDK-Nachricht  
  
-   Sicherheitsrolle  
  
-   Dienstendpunkt  
  
-   Siteübersicht  

-   Datenanbieter für virtuelle Entität

-   Datenquelle für virtuelle Entität
  
-   Webressource  
  
 Einige Komponenten sind in anderen Komponenten geschachtelt. So enthält eine Entität beispielsweise Formulare, Ansichten, Diagramme, Felder, Entitätsbeziehungen, Nachrichten und Geschäftsregeln. Für jede dieser Komponenten muss eine Entität vorhanden sein. Ein Feld kann außerhalb einer Entität nicht existieren. Wir sprechen davon, dass das Feld von der Entität abhängt. Eigentlich gibt es doppelt so viele Arten von Komponenten wie in der oben stehenden Liste angegeben. Die meisten davon sind jedoch in anderen Komponenten geschachtelt und in der Anwendung nicht sichtbar.  
  
 Der Zweck von Komponenten besteht darin, alle Einschränkungen hinsichtlich der Anpassbarkeit mit verwalteten Eigenschaften sowie alle Abhängigkeiten nachzuverfolgen, sodass sie exportiert, importiert und (in verwalteten Lösungen) restlos gelöscht werden können.  
  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
### <a name="managed-and-unmanaged-solutions"></a>Nicht verwaltete und verwaltete Lösungen  
 Es gibt **verwaltete** und **nicht verwaltete** Lösungen. Eine **verwaltete** Lösung kann nicht geändert, aber nach dem Import deinstalliert werden. Durch die Deinstallation der Lösung werden alle Komponenten dieser Lösung entfernt.  
  
 Beim Importieren einer **nicht verwalteten** Lösung werden Ihrer Umgebung alle Komponenten dieser Lösung hinzugefügt. Die Komponenten können nicht durch Deinstallieren der Lösung entfernt werden.  
  
 Wenn Sie eine **nicht verwaltete** Lösung importieren, die bereits von Ihnen angepasste Komponenten enthält, werden Ihre Anpassungen durch die Anpassungen in der importierten nicht verwalteten Lösung überschrieben. Dieser Vorgang kann nicht rückgängig gemacht werden.  
  
> [!IMPORTANT]
>  Installieren Sie eine nicht verwaltete Lösung nur, wenn Sie alle Komponenten zu Ihrer Umgebung hinzufügen und alle vorhandenen Anpassungen überschreiben möchten.  
  
 Selbst wenn Sie Ihre Apps und Anpassungen nicht verteilen möchten, empfiehlt es sich möglicherweise, eine nicht verwaltete Lösung zu erstellen und zu verwenden, um über eine separate Ansicht nur der von Ihnen angepassten Teile der Anwendung zu verfügen. Wenn Sie irgend etwas anpassen, fügen Sie es einfach der nicht verwalteten Lösung hinzu, die Sie erstellt haben.  
  
 Sie können Ihre **Standardlösung** nur als nicht verwaltete Lösung exportieren.  
  
 Zum Erstellen einer **verwalteten** Lösung wählen Sie beim Exportieren der Lösung die Option **Verwaltet** aus. Wenn Sie eine verwaltete Lösung erstellen, können Sie diese nicht wieder in die Umgebung importieren, die Sie für die Erstellung verwendet haben. Sie können sie nur in eine andere Umgebung importieren.  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### <a name="how-solutions-are-applied"></a>Anwenden von Lösungen  
 Alle Lösungen werden als Ebenen ausgewertet, um zu bestimmen, was Ihre App tatsächlich tun wird. Das folgende Diagramm zeigt, wie verwaltete und nicht verwaltete Lösungen ausgewertet und Änderungen an den Lösungen in Ihrer Umgebung angezeigt werden.  
  
 ![Lösungsebenen](media/solution-layering.png "lösungsebenen")  
  
 Von unten nach oben:  
  
 **Systemlösung**  
 Bei der Systemlösung handelt es sich um eine verwaltete Lösung, über die jede Umgebung verfügt. Die Systemlösung ist die Definition aller sofort einsetzbaren Komponenten im System.  
  
 **Verwaltete Lösungen**  
 Mit verwalteten Lösungen können die Systemlösungskomponenten geändert und neue Komponenten hinzugefügt werden. Wenn mehrere verwaltete Lösungen installiert werden, wird die erste unter den später installierten verwalteten Lösungen installiert. Das bedeutet, dass die erste installierte Lösung durch die zweite installiert Lösung geändert werden kann. Wenn die Definitionen zweier verwalteter Lösungen in Konflikt stehen, gilt als allgemeine Regel, dass die letzte den Vorrang hat. Wenn Sie eine verwaltete Lösung deinstallieren, wird die verwaltete Lösung darunter wirksam. Wenn Sie alle verwalteten Lösungen deinstallieren, wird das innerhalb der Systemlösung definierte Standardverhalten angewendet.  
  
 **Nicht verwaltete Anpassungen**  
 Nicht verwaltete Anpassungen sind alle Änderungen, die Sie durch eine nicht verwaltete Lösung an Ihrer Umgebung vornehmen. Durch die Systemlösung wird definiert, was Sie mit verwalteten Eigenschaften anpassen können. Herausgeber von verwalteten Lösungen können Ihre Möglichkeiten bei der Anpassung von Lösungskomponenten begrenzen, die sie in ihrer Lösung hinzufügen. Sie können alle Lösungskomponenten anpassen, die keine verwalteten Eigenschaften aufweisen, mit denen Sie an deren Anpassung gehindert werden.  
  
 **Anwendungsverhalten**  
 Das ist das Ergebnis, das Sie in Ihrer Umgebung tatsächlich zu sehen bekommen: die Standardsystemlösung, alle verwalteten Lösungen sowie alle nicht verwalteten Anpassungen, die Sie angewendet haben.  
  
<a name="BKMK_ManagedProperties"></a>   
### <a name="managed-properties"></a>Verwaltete Eigenschaften  
 Einige Komponenten können nicht angepasst werden. Diese Komponenten in der Systemlösung enthalten Metadaten, mit denen Sie an der Anpassung gehindert werden. Sie werden als **verwaltete Eigenschaften** bezeichnet. Der Herausgeber einer verwalteten Lösung kann die verwalteten Eigenschaften so festlegen, dass Sie daran gehindert werden, seine Lösung auf eine von ihm nicht gewünschte Weise anzupassen.  
  
<a name="BKMK_Dependencies"></a>   
### <a name="solution-dependencies"></a>Lösungsabhängigkeiten  
 Aufgrund der Anordnung verwalteter Lösungen in Ebenen können einige verwaltete Lösungen von Lösungskomponenten in anderen verwalteten Lösungen abhängen. Diesen Umstand nutzen einige Lösungsherausgeber und erstellen modulare Lösungen. Möglicherweise müssen Sie zunächst eine verwaltete „Basislösung“ installieren und können erst danach eine zweite verwaltete Lösung installieren, mit der die Komponenten in der verwalteten Basislösung weiter angepasst werden. Die zweite verwaltete Lösung hängt von den Lösungskomponenten ab, die Teil ersten Lösung sind.  
  
 Diese Abhängigkeiten zwischen Lösungen werden vom System verfolgt. Eine Lösung, für die eine Basislösung erforderlich ist, die nicht installiert ist, kann nicht installiert werden. Sie erhalten eine Meldung, dass für die Lösung zuerst eine andere Lösung installiert werden muss. Entsprechend kann die Basislösung aufgrund der Abhängigkeiten nicht deinstalliert werden, solange noch eine von ihr abhängige Lösung installiert ist. Die abhängige Lösung muss vor der Basislösung deinstalliert werden.  
  
  
## <a name="next-steps"></a>Nächste Schritte  
[Import, update, and export solutions (Importieren, Aktualisieren und Exportieren von Lösungen)](import-update-export-solutions.md) <br/>
[Navigieren zu einer bestimmten Lösung](navigate-specific-solution.md)
 
