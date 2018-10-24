---
title: Arbeiten mit Lösungen in PowerApps | Microsoft-Dokumentation
description: Informationen zum Verteilen von Lösungen
ms.custom: ''
ms.date: 06/21/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 47fb64e650da2f3e1a9e0cf523060cf7d9f5a03b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683498"
---
<a name="BKMK_Solutions"></a>   
# <a name="solutions-overview"></a>Übersicht über Lösungen  

 Lösungen sind dazu da, dass modellgesteuerte Apps gekauft, freigegeben oder anderweitig von einer Organisation an eine andere weitergegeben werden können. Lösungen erhalten Sie von [AppSource](https://appsource.microsoft.com/) oder von einem unabhängigen Softwareanbieter (ISV, Independent Software Vendor). Bei einer Lösung handelt es sich um eine Datei, die Sie als App in eine Umgebung importieren können oder die Sie zum Anwenden von Anpassungen an eine vorhandene App importieren können.  
  
Weitere Informationen: [Whitepaper: Patterns and Principles for Solution Builders (Muster und Prinzipien für Lösungsentwickler)](http://go.microsoft.com/fwlink/p/?LinkID=533946)  
  
> [!NOTE]
>  Wenn Sie als ISV eine App erstellen, die Sie verteilen möchten, müssen Sie Lösungen verwenden. Weitere Informationen zur Verwendung von Lösungen finden Sie unter [Packen und Verteilen von Erweiterungen mithilfe von Lösungen](https://msdn.microsoft.com/library/gg334530.aspx).  
  
 Wenn Sie nur PowerApps-Apps zur Verwendung in der Organisation erstellen oder Dynamics 365 anpassen möchten, müssen Sie über Lösungen Folgendes wissen:  
  
-   Das Erstellen von Lösungen ist optional. Sie können Apps in Ihrer PowerApps-Umgebung erstellen oder anpassen, ohne eine Lösung zu erstellen.  
  
-   Wenn Sie die PowerApps-Umgebung direkt anpassen, arbeiten Sie mit einer speziellen Lösung, die als **Common Data Services-Standardlösung** bezeichnet wird. Diese Lösung enthält alle Komponenten in Ihrem System.  
  
-   Sie können Ihre Standardlösung exportieren, um eine Sicherung der in Ihrer Organisation definierten Anpassungen zu erstellen. Eine Sicherung empfiehlt sich für den Notfall.  
  
<a name="BKMK_SolutionComponents"></a>   
### <a name="solution-components"></a>Lösungskomponenten  
 Eine Lösungskomponente stellt ein Element dar, das Sie potenziell anpassen können. Alles, was Bestandteil einer Lösung sein kann, ist eine Lösungskomponente. Die folgende Liste enthält Lösungskomponenten, die Sie in einer Lösung anzeigen können:  
  
-   Anwendungsmenüband  

-   App 
  
-   Artikelvorlage  
  
-   Geschäftsregel  
  
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
  
-   Formular  
  
-   Seriendruckvorlage  
  
-   Nachricht  
  
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
  
 Die meisten Lösungskomponenten sind in andere Lösungskomponenten geschachtelt. So enthält eine Entität beispielsweise Formulare, Ansichten, Diagramme, Felder, Entitätsbeziehungen, Nachrichten und Geschäftsregeln. Für jede dieser Lösungskomponenten muss eine Entität vorhanden sein. Ein Feld kann außerhalb einer Entität nicht existieren. Wir sprechen davon, dass das Feld von der Entität abhängt. Genau genommen, gibt es doppelt so viele Arten von Lösungskomponenten wie in der vorherigen Liste angegeben. Die meisten davon sind in der Anwendung jedoch nicht sichtbar.  
  
 Der Zweck von Lösungskomponenten besteht darin, alle Einschränkungen hinsichtlich der Anpassbarkeit mit verwalteten Eigenschaften sowie alle Lösungsabhängigkeiten nachzuverfolgen, sodass sie exportiert, importiert und (in verwalteten Lösungen) restlos gelöscht werden können.  
  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
### <a name="managed-and-unmanaged-solutions"></a>Nicht verwaltete und verwaltete Lösungen  
 Eine **verwaltete** Lösung kann nach dem Import deinstalliert werden. Durch die Deinstallation der Lösung werden alle Komponenten dieser Lösung entfernt.  
  
 Beim Importieren einer **nicht verwalteten** Lösung werden dagegen Ihrer Standardlösung alle Komponenten dieser Lösung hinzugefügt. Die Komponenten können nicht durch Deinstallieren der Lösung entfernt werden.  
  
 Wenn Sie eine **nicht verwaltete** Lösung importieren, die bereits von Ihnen angepasste Lösungskomponenten enthält, werden Ihre Anpassungen von den Anpassungen in der nicht verwalteten Lösung überschrieben. Dieser Vorgang kann nicht rückgängig gemacht werden.  
  
> [!IMPORTANT]
>  Installieren Sie eine nicht verwaltete Lösung nur, wenn Sie alle Komponenten Ihrer Standardlösung hinzufügen wollen und alle vorhandenen Anpassungen überschrieben werden sollen.  
  
 Selbst wenn Sie Ihre Lösung nicht verteilen möchten, sollten Sie eine nicht verwaltete Lösung so erstellen und verwenden, dass sie über eine separate Ansicht verfügt, die nur die Teile der Anwendung enthält, die Sie angepasst haben. Wenn Sie irgend etwas anpassen, fügen Sie es einfach der nicht verwalteten Lösung hinzu, die Sie erstellt haben.  
  
 Sie können Ihre Standardlösung nur als nicht verwaltete Lösung exportieren.  
  
 Zur Erstellung einer **verwalteten** Lösung wählen Sie beim Exportieren der Lösung die Option „Verwaltete Lösung“. Wenn Sie eine verwaltete Lösung erstellen, können Sie sie nicht wieder in die Organisation importieren, die Sie für die Erstellung verwendet haben. Sie können sie nur in eine andere Organisation importieren.  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### <a name="how-solutions-are-applied"></a>Anwenden von Lösungen  
 Alle Lösungen werden als Ebenen ausgewertet, um zu bestimmen, was Ihre App tatsächlich tun wird. Im folgenden Diagramm ist dargestellt, wie verwaltete und nicht verwaltete Lösungen ausgewertet werden und wie Änderungen an den Lösungen in Ihrer Organisation angezeigt werden.  
  
 ![Lösungsebenen](media/solution-layering.png "lösungsebenen")  
  
 Von unten nach oben:  
  
 **Systemlösung**  
 Bei der Systemlösung handelt es sich um eine verwaltete Lösung, über die jede Organisation verfügt. Die Systemlösung ist die Definition aller sofort einsetzbaren Komponenten im System.  
  
 **Verwaltete Lösungen**  
 Mit verwalteten Lösungen können die Systemlösungskomponenten geändert und neue Komponenten hinzugefügt werden. Wenn mehrere verwaltete Lösungen installiert werden, wird die erste unter den später installierten verwalteten Lösungen installiert. Das bedeutet, dass die erste installierte Lösung durch die zweite installiert Lösung geändert werden kann. Wenn die Definitionen zweier verwalteter Lösungen in Konflikt stehen, gilt als allgemeine Regel, dass die letzte den Vorrang hat. Wenn Sie eine verwaltete Lösung deinstallieren, wird die verwaltete Lösung darunter wirksam. Wenn Sie alle verwalteten Lösungen deinstallieren, wird das innerhalb der Systemlösung definierte Standardverhalten angewendet.  
  
 **Nicht verwaltete Anpassungen**  
 Nicht verwaltete Anpassungen sind alle Änderungen, die Sie an Ihrer Organisation durch eine nicht verwaltete Lösung vornehmen. Durch die Systemlösung wird definiert, was Sie mit verwalteten Eigenschaften anpassen können. Herausgeber von verwalteten Lösungen können Ihre Möglichkeiten bei der Anpassung von Lösungskomponenten begrenzen, die sie in ihrer Lösung hinzufügen. Sie können alle Lösungskomponenten anpassen, die keine verwalteten Eigenschaften aufweisen, mit denen Sie an deren Anpassung gehindert werden.  
  
 **Anwendungsverhalten**  
 Das ist das Ergebnis, das Sie in Ihrer Organisation tatsächlich zu sehen bekommen: die Standardsystemlösung, alle verwalteten Lösungen sowie alle nicht verwalteten Anpassungen, die Sie angewendet haben.  
  
<a name="BKMK_ManagedProperties"></a>   
### <a name="managed-properties"></a>Verwaltete Eigenschaften  
 Einige Komponenten können nicht angepasst werden. Diese Komponenten in der Systemlösung enthalten Metadaten, mit denen Sie an der Anpassung gehindert werden. Sie werden als **verwaltete Eigenschaften** bezeichnet. Der Herausgeber einer verwalteten Lösung kann die verwalteten Eigenschaften so festlegen, dass Sie daran gehindert werden, seine Lösung auf eine von ihm nicht gewünschte Weise anzupassen.  
  
<a name="BKMK_Dependencies"></a>   
### <a name="solution-dependencies"></a>Lösungsabhängigkeiten  
 Aufgrund der Anordnung verwalteter Lösungen in Ebenen können einige verwaltete Lösungen von Lösungskomponenten in anderen verwalteten Lösungen abhängen. Diesen Umstand nutzen einige Lösungsherausgeber, und erstellen Lösungen entsprechend modular. Möglicherweise müssen Sie zunächst eine verwaltete „Basislösung“ installieren und können erst danach eine zweite verwaltete Lösung installieren, mit der die Komponenten in der verwalteten Basislösung weiter angepasst werden. Die zweite verwaltete Lösung hängt von den Lösungskomponenten ab, die Teil ersten Lösung sind.  
  
 Diese Abhängigkeiten zwischen Lösungen werden vom System verfolgt. Eine Lösung, für die eine Basislösung erforderlich ist, die nicht installiert ist, kann nicht installiert werden. Sie erhalten eine Meldung, dass für die Lösung zuerst eine andere Lösung installiert werden muss. Entsprechend kann die Basislösung aufgrund der Abhängigkeiten nicht deinstalliert werden, solange noch eine von ihr abhängige Lösung installiert ist. Die abhängige Lösung muss vor der Basislösung deinstalliert werden.  
  
  
## <a name="next-steps"></a>Nächste Schritte  
[Import, update, and export solutions (Importieren, Aktualisieren und Exportieren von Lösungen)](import-update-export-solutions.md) <br/>
[Navigieren zu einer bestimmten Lösung](navigate-specific-solution.md)
 
