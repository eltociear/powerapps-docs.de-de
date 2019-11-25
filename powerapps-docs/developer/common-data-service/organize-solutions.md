---
title: Organisieren der Lösungen (Common Data Service) | Microsoft-Dokumentation
description: Dieses Dokument enthält einige Strategien, um Ihre Lösungen zu organisieren
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: cc6414a1d846b5bd601ce2c6f37164014f089631
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748678"
---
# <a name="organize-your-solutions"></a>Organisieren der Lösungen

Bevor Sie Lösungen erstellen, nehmen Sie sich etwas Zeit, um im Voraus zu planen. Überlegen Sie beispielsweise, wie viele Lösungen Sie freigeben möchten und ob die Lösungen Komponenten gemeinsam nutzen sollen.  
  
 Außerdem muss ermittelt werden, wie viele Common Data Service-Organisationen Sie benötigen, um Ihre Linie von Lösungen zu entwickeln. Sie können eine einzelne Organisation für die meisten Strategien verwenden, die in diesem Thema beschrieben werden. Wenn Sie sich jedoch für nur eine Organisation entscheiden und später realisieren, dass Sie mehr benötigen, kann es schwierig sein, die Lösungen zu ändern, falls Benutzer sie bereits installiert haben. Die Verwendung von mehreren Organisationen, obwohl mit mehr Komplexität verbunden, kann bessere Flexibilität bieten.  
  
<a name="BKMK_OptionsToModularize"></a>   
## <a name="strategies-to-organize-your-solutions"></a>Strategien zum Organisieren von Lösungen  
 Nachfolgend sind einige Strategien zum Erstellen von Lösungen angegeben, die in der Reihenfolge von der einfachsten bis zur komplexesten aufgeführt werden:  
  
-   [Keine benutzerdefinierten Lösungen](organize-solutions.md#BKMK_NoCustomSolution)  
  
-   [Eine einzelne Lösung](organize-solutions.md#BKMK_SingleSolution)  
  
-   [Mehrere Lösungen](organize-solutions.md#BKMK_MultipleSolutions)  
  
-   [Mehrere Lösungen mit gemeinsam genutzten Komponenten](organize-solutions.md#BKMK_MultipleSolutionsSharedComponents)  
  
-   [Lösungsbibliotheken](organize-solutions.md#BKMK_SolutionLibraries)  
  
<a name="BKMK_NoCustomSolution"></a> 
  
### <a name="no-custom-solutions"></a>Keine benutzerdefinierten Lösungen  
 Sie müssen keine Lösungen erstellen. Sie können Common Data Service direkt anpassen, indem Sie die Standardlösung verwenden.  
  
 Sie können die Standardlösung noch als nicht verwaltete Lösung exportieren, um sie zwischen Organisationen zu übertragen.  
  
> [!TIP]
>  Wenn Sie das Anpassungspräfix für den Standardherausgeber auf einem Wert ändern, der mit einem Herausgeber übereinstimmt, den Sie in der Zukunft erstellen möchten, enthalten alle neuen Anpassungen, die Sie erstellen, dieses Anpassungspräfix im Namen. Auf diese Weise können Sie, wenn Sie Lösungen verwenden möchten, die Anpassungen, die Sie in der Standardlösung erstellt haben, zu einer nicht verwalteten Lösung hinzufügen, sodass diese einheitliche Namen besitzen können.  
  
<a name="BKMK_SingleSolution"></a>   
### <a name="single-solution"></a>Eine einzelne Lösung  
 Indem Sie eine Lösung erstellen, legen Sie einen Arbeitssatz von Anpassungen fest. Dadurch ist es einfacher, Elemente zu suchen, die Sie angepasst haben.  
  
 Diese Methode wird empfohlen, wenn Sie nur eine einzelne verwaltete Lösung erstellen möchten. Wenn Sie der Meinung sind, dass Sie die Lösung in der Zukunft aufspalten müssen, sollten Sie die Verwendung mehrerer Lösungen in Betracht ziehen.  
  
<a name="BKMK_MultipleSolutions"></a>   
### <a name="multiple-solutions"></a>Mehrere Lösungen  
 Bei zwei nicht verknüpften Lösungen, die keine Komponenten gemeinsam nutzen, besteht die direkteste Methode darin, zwei nicht verwaltete Lösungen zu erstellen.  
  
> [!NOTE]
>  Es ist sehr verbreitet, in Lösungen die Anwendungsmenübänder oder die Siteübersicht zu ändern. Ändern Sie in Ihren beiden Lösungen diese Lösungskomponenten, es sind gemeinsam genutzte Komponenten. Der folgende Abschnitt enthält Informationen über das Arbeiten mit gemeinsam genutzten Komponenten.  
  
<a name="BKMK_MultipleSolutionsSharedComponents"></a>   
### <a name="multiple-solutions-with-shared-components"></a>Mehrere Lösungen mit gemeinsam genutzten Komponenten  
 Möglicherweise haben Sie mehrere Lösungen, die Komponenten gemeinsam verwenden. Es gibt möglicherweise einen bestimmten Satz von gemeinsamen Funktionen innerhalb von mehreren Lösungen, und diese gemeinsamen Funktionen sind mit allen anderen Funktionen kompatibel, die in jeder Lösung individuell vorhanden sind. Sie verfügen beispielsweise über eine Reihe von Dienst-Plug-Ins, die von jeder Lösung verwendet werden, aber keine der separaten Lösungen nutzt weitere Komponenten gemeinsam.  
  
 In diesem Fall kann jede Lösung in einer einzelnen Organisation entwickelt werden. Einige Komponenten können mehr als einer Lösung hinzugefügt werden, solange Änderungen, die an ihnen vorgenommen werden, mit allen anderen Lösungen, die sie verwenden, kompatibel sind. Es ist wichtig, dass alle diese Lösungen denselben Lösungsherausgeber gemeinsam nutzen. Wenn der Lösungsherausgeber nicht identisch ist, können Organisationen nicht mehr als eine Ihrer Lösungen installieren.  
  
<a name="BKMK_SolutionLibraries"></a> 
  
### <a name="solution-libraries"></a>Lösungsbibliotheken  
 Bei einem ISV mit mehreren Lösungen oder einer großen Unternehmensbereitstellung müssen wahrscheinlich viele Lösungskomponenten gemeinsam genutzt werden. Die besten Möglichkeiten für Lösungen zur gemeinsamen Nutzung von Komponenten bieten Lösungsbibliotheken. Erstellen Sie eine Lösungsbibliothek, indem Sie eine nicht verwaltete Lösung in einer separaten Organisation erstellen und dann diese Komponenten in eine verwaltete Lösung packen. Installieren Sie die verwaltete Lösung in einer anderen Organisation und veranlassen Sie Entwickler, auf diese gemeinsam genutzten Komponenten zu verweisen.  
  
 Das Common Data Service Solutions Framework ermöglicht es Ihnen, Schichten von Lösungen zu erstellen, die voneinander abhängen. In der Regel können Sie eine Lösungsbibliothek erstellen, die eine" Basislösung" darstellt. Weitere Lösungen können aufbauend auf dieser Basislösung erstellt werden. Dies ermöglicht eine klarere Trennung von Komponenten. Entwicklerteams, die an Lösungsbibliotheken arbeiten, und diejenigen, die an den abhängigen Lösungen arbeiten, können mit unterschiedlichem Tempo arbeiten. Die abhängigen Lösungen müssen erstellt werden, nachdem die Lösungsbibliotheken installiert wurden.  
  
 Dies erfordert, dass Sie eine Voraussetzungslösung erstellen, die Kunden installieren müssen, bevor sie eine abhängige Lösung installieren können. Entwickler, die an den Lösungsbibliotheken arbeiten, können die Arbeit fortsetzen und Aktualisierungen durchführen, solange sie keine abhängigen Lösungen unterbrechen, die sie benötigen.  
  
### <a name="see-also"></a>Siehe auch  
 [Organisieren des Teams zum Entwickeln von Lösungen](organize-team-develop-solutions.md)   
 [Planen für Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)
