---
title: Wie verwaltete Lösungen zusammengeführt werden (Common Data Service) | Microsoft Docs
description: Um zu vermeiden, dass mehrere installierte Lösungen sich stören, befolgen Sie beim Erstellen einer Lösung die bewährten Methoden
ms.custom: ''
ms.date: 02/27/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- maker
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7b6a5d741179c26799badfd6c7427e06941f5851
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "3124911"
---
# <a name="understand-how-managed-solutions-are-merged"></a>Verstehen, wie verwaltete Lösungen zusammengeführt werden

Wenn Sie die Installation Ihrer verwalteten Lösung vorbereiten, denken Sie daran, dass in einer Umgebung möglicherweise mehrere Lösungen installiert sind oder dass in Zukunft weitere Lösungen installiert werden können. Erstellen Sie eine Lösung, die erfolgreich bewährten Praktiken folgt, so dass Ihre Lösung nicht andere Lösungen behindert.  
  
Die Prozesse, die von Common Data Service verwendet werden, um Anpassungen zusammenzuführen, legt den Fokus auf die Aufrechterhaltung der Funktionalität der Lösung. Während alle Anstrengungen unternommen werden, um die Darstellung zu wahren, können Inkompatibilitäten zwischen Anpassungen es erforderlich machen, dass die gesteuerte Endpunktauflösung gewisse Darstellungsdetails zugunsten der Anpassungsfunktionalität ändert.  
  
<a name="BKMK_MergingFormCustomizations"></a>   

## <a name="merge-form-customizations"></a>Formularanpassungen zusammenführen  
 Die einzigen Formularanpassungen, die zusammengeführt werden müssen, sind diejenigen, die an allen Entitätsformularen durchgeführt werden, die sich bereits in der Umgebung befinden. Dies bedeutet in der Regel, dass nur Formularanpassungen zusammengeführt werden müssen, wenn Ihre Lösung Formulare anpasst, die für Entitäten eingeschlossen waren und erstellt wurden als Common Data Service installiert wurde. Eine Möglichkeit, das Formularzusammenführen zu vermeiden ist es, neue Formulare für beliebige Entitäten Common Data Service bereitzustellen. Formulare für benutzerdefinierte Entitäten benötigen keine Zusammenführung, es sei denn, Sie erstellen eine Lösung, die bestehende verwaltete Lösungen aktualisiert oder modifiziert, die von den benutzerdefinierten Entitäten und Formularen erstellt wurden.  
  
 Wenn einer Lösung als verwaltete Lösung verpackt wird, werden die Formulardefinitionen, die im XML-Formular gespeichert sind, Datei Formular mit dem ursprünglichen XML-Formular verglichen und es werden nur die Unterschieden in der verwalteten Lösung hinzugefügt. Wenn die verwaltete Lösung in einer neuen Umgebung installiert wird, werden die Unterschiede bei der Formularanpassung dann mit dem FormXML für das vorhandene Formular zusammengeführt, um eine neue Formulardefinition zu erstellen. Diese neue Formulardefinition ist, was der Benutzer sieht und was ein Systemanpasser ändern kann. Wenn die verwaltete Lösung deinstalliert wurde, werden nur jene Formularelementen entfernt, die in der verwalteten Lösung gefunden werden.  
  
 Wenn Sie neue Elemente in ein Formular hinzufügen, das zusammengeführt werden soll, empfehlen wir, dass Sie Ihre neuen Elemente innerhalb des Containerelemente integrieren (Registerkarten oder Abschnitte) Ergänzungen in einem Container werden an das Ende des Containers angefügt. Beispielsweise sind die Felder, die in einem Abschnitt hinzugefügt werden, am Ende des Abschnitts zu finden. Es wird erwartet, dass ein Anpasser, der eine Lösung installiert, das Formular dann so ändert, dass die Elemente nach der Installation neu angeordnet werden.  
  
 Verwaltete Lösungen, die Formulare nutzen, die neue Sicherheitsrollen abhängig von diesen Rollen enthalten. Sie sollten diese Sicherheitsrollen in Ihren verwalteten Lösung integrieren. Wenn einem Formular Sicherheitsrollen zugeordnet sind, die sich nicht in der Umgebung befinden, in der die verwaltete Lösung installiert wird, schlägt die Installation nicht fehl, aber die Formulare sind möglicherweise keinen Sicherheitsrollen zugeordnet. Wenn die verwaltete Lösung deinstalliert wird, werden alle dazugehörenden Sicherheitsrollen entfernt. Alle Formulare außerhalb der verwalteten Lösung können nicht mehr diesen Sicherheitsrollen zugeordnet werden.  
  
> [!NOTE]
>  Wenn eine Entität der verwalteten Lösung mehrere Formulare enthält und das Formular der Umgebungsentität ebenfalls mehrere Formulare enthält, werden die neuen Formulare nicht an das Ende der Liste der verfügbaren Formulare angehängt - sie werden mit den ursprünglichen Entitätsformularen verschachtelt.  
  
<a name="BKMK_MergingNavigationCustomizations"></a>   
## <a name="merge-navigation-sitemap-customizations"></a>Zusammenführungsnavigation-Anpassungen (SiteMap)  
 Wenn eine Lösung als verwaltet gepackt ist, wird die SMX-Siteübersicht mit der ursprünglichen XML-Siteübersicht verglichen und alle anderen Anpassungen erfolgen auf der SiteMap. Es werden nur die Unterschiede in der verwalteten Lösung integriert. Diese Unterschiede umfassen Elemente, die geändert, verschoben, hinzugefügt oder entfernt werden. Wenn die verwaltete Lösung in einer neuen Umgebung installiert wird, werden die SiteMap-Änderungen mit dem SiteMap-XML zusammengeführt, das für die Umgebung gefunden wurde, in der die verwaltete Lösung installiert wird. Die Benutzer sehen eine neue Siteübersichtsdefinition.  
  
 Zu diesem Zeitpunkt kann ein Anpasser die Siteübersicht auf eine nicht verwaltete Lösung exportieren und diese Siteübersichtsdefinition wird dann alle Elemente der aktiven Siteübersicht enthalten. Ein Anpasser kann dann die SiteMap modifizieren und als nicht verwaltete Anpassung wieder importieren.  Wenn die verwaltete Lösung später deinstalliert wird, wird die XML-Siteübersicht, die mit der verwalteten Lösung importiert wurde, referenziert, um die Änderungen zu entfernen, die mit der verwalteten Lösung übernommen wurden. Es wird eine aktive neue Siteübersicht berechnet.  
  
 Wenn ein neues sichtbares Element zur SiteMap hinzugefügt wird, wird es am unteren Rand des dazugehörigen Containers angezeigt. Beispielsweise wird ein neuer Bereich unten im Navigationsbereich angezeigt. Um die Elemente zu positionieren, die hinzugefügt wurden, müssen Sie die Siteübersicht exportieren und bearbeiten um die genaue Position festzulegen und sie dann als nicht verwaltete Lösung erneut importieren.  
  
> [!NOTE]
>  Eine Siteüersichtanpassung kann zwischen der Veröffentlichung erfolgen. Alle nicht veröffentlichten Siteübersichtsanpassungen gehen verloren, wenn eine neue Siteübersichtsdefinition importiert wird.  
  
<a name="BKMK_MergingOptionSetOptions"></a>   
## <a name="merge-option-set-options"></a>Optionssatz-Optionen zusammenführen  
 Bei jeder neuen Optionssatzoption wird ein ganzzahliger Wert zugeteilt,, der einen Optionswertpräfix enthält. Der Optionswertpräfix ist ein Satz von fünf Ziffern, die dem Optionswert vorangestellt werden. Ein Optionswertpräfix wird basierend auf dem Lösungsherausgeberanpassungspräfix erstellt, kann aber auf einen beliebigen Wert festgelegt werden. Der Optionswertpräfix hilft, neue Optionssatzoptionen zu differenzieren, die im Kontext eines bestimmten Lösungsherausgebers erstellt wurden und verringert die Möglichkeit zur Kollision mit Optionswerten. Die Verwendung des Optionswertpräfixes ist empfohlen, aber nicht erforderlich.  
  
 Eine verwaltete Lösung aktualisiert oder fügt in der Regel Optionen für Optionssätze hinzu, die sich bereits in der Umgebung befinden, z.B. die Optionssätze für Kontokategorie oder Branche. Wenn eine verwaltete Lösung die in einem Optionssatz verfügbaren Optionen modifiziert, sind alle in der verwalteten Lösung definierten Optionen in der Umgebung verfügbar. Wenn die verwaltete Lösung deinstalliert wurde, werden die Optionssatzoptionen ihrem ursprünglichen Status zurückgegeben.  
  
### <a name="see-also"></a>Siehe auch  

[Überblick über Lösungen](solutions-overview.md)  <br />
[Exportieren von Lösungen](export-solutions.md) <br />
[Mit dem Sitemap-Designer eine modellgesteuerte App-Sitemap erstellen](../model-driven-apps/create-site-map-app.md)