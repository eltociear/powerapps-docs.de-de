---
title: Grundlegendes zum Zusammenführen verwalteter Lösungen (Common Data Service für Apps) | Microsoft Docs
description: 'Um zu vermeiden, dass mehrere installierte Lösungen sich stören, befolgen Sie beim Erstellen einer Lösung die bewährten Methoden'
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
---
# <a name="understand-how-managed-solutions-are-merged"></a>Verstehen, wie verwaltete Lösungen zusammengeführt werden

Wenn Sie die Installation Ihrer verwalteten Lösung vorbereiten, denken Sie daran, dass eine Organisation mehrere Lösungen installiert haben kann oder dass andere Lösungen in der Zukunft installiert werden können. Erstellen Sie eine Lösung, die erfolgreich bewährten Praktiken folgt, so dass Ihre Lösung nicht andere Lösungen behindert.  
  
 Die Prozesse, die von Common Data Service für Apps verwendet werden, um Anpassungen zusammenzuführen, legen den Fokus auf die Aufrechterhaltung der Funktionalität der Lösung. Während alle Anstrengungen unternommen werden, um die Darstellung zu wahren, können Inkompatibilitäten zwischen Anpassungen es erforderlich machen, dass die gesteuerte Endpunktauflösung gewisse Darstellungsdetails zugunsten der Anpassungsfunktionalität ändert.  
  
<a name="BKMK_MergingFormCustomizations"></a>   

## <a name="merge-form-customizations"></a>Formularanpassungen zusammenführen  
 Die einzigen Formularanpassungen, die zusammengeführt werden müssen, sind diejenigen, die bei Entitätsformularen ausgeführt werden, die bereits in der Organisation vorliegen. Dies bedeutet in der Regel, dass nur Formularanpassungen zusammengeführt werden müssen, wenn Ihre Lösung Formulare anpasst, die für Entitäten eingeschlossen waren und erstellt wurden, als CDS für Apps installiert wurde. Eine Möglichkeit, das Formularzusammenführen zu vermeiden, ist es, neue Formulare für beliebige CDS für Apps-Entitäten bereitzustellen. Formulare für benutzerdefinierte Entitäten benötigen keine Zusammenführung, es sei denn, Sie erstellen eine Lösung, die bestehende verwaltete Lösungen aktualisiert oder modifiziert, die von den benutzerdefinierten Entitäten und Formularen erstellt wurden.  
  
 Wenn einer Lösung als verwaltete Lösung verpackt wird, werden die Formulardefinitionen, die im XML-Formular gespeichert sind, Datei Formular mit dem ursprünglichen XML-Formular verglichen und es werden nur die Unterschieden in der verwalteten Lösung hinzugefügt. Wenn die verwaltete Lösung in einer neuen Organisation installiert ist, werden die Formularanpassungsunterschiede mit dem XML-Formular zusammengeführt, damit aus dem bestehenden Formular eine neue Formulardefinition erstellt werden kann. Diese neue Formulardefinition ist, was der Benutzer sieht und was ein Systemanpasser ändern kann. Wenn die verwaltete Lösung deinstalliert wurde, werden nur jene Formularelementen entfernt, die in der verwalteten Lösung gefunden werden.  
  
 Wenn Sie neue Elemente in ein Formular hinzufügen, das zusammengeführt werden soll, empfehlen wir, dass Sie Ihre neuen Elemente innerhalb des Containerelemente integrieren (Registerkarten oder Abschnitte) Ergänzungen in einem Container werden an das Ende des Containers angefügt. Beispielsweise sind die Felder, die in einem Abschnitt hinzugefügt werden, am Ende des Abschnitts zu finden. Es wird erwartet, dass Ein Anpasser, der eine Lösung installiert, dann das Formular anpasst, um die Elemente nach der Installation neu anzuordnen.  
  
 Verwaltete Lösungen, die Formulare nutzen, die neue Sicherheitsrollen abhängig von diesen Rollen enthalten. Sie sollten diese Sicherheitsrollen in Ihren verwalteten Lösung integrieren. Falls es Sicherheitsrollen gibt, die einem Formular zugeordnet sind, die nicht in der Organisation sind, in der die verwaltete Lösung installiert wurde, wird die Installation nicht fehlschlagen, aber die Formulare sind möglicherweise keiner Sicherheitsrolle zugeordnet. Wenn die verwaltete Lösung deinstalliert wird, werden alle dazugehörenden Sicherheitsrollen entfernt. Alle Formulare außerhalb der verwalteten Lösung können nicht mehr diesen Sicherheitsrollen zugeordnet werden.  
  
> [!NOTE]
>  Wenn eine verwaltete Lösungsentität mehrere Formulare enthält und auch das Organisationsentitätsformular mehrere Formulare enthält, werden die neuen Formulare nicht am unteren Rand der Liste der verfügbaren Formulare angefügt. Sie werden mit den ursprünglichen Entitätsformularen verschachtelt.  
  
<a name="BKMK_MergingNavigationCustomizations"></a>   
## <a name="merge-navigation-sitemap-customizations"></a>Zusammenführungsnavigation-Anpassungen (SiteMap)  
 Wenn eine Lösung als verwaltet gepackt ist, wird die SMX-Siteübersicht mit der ursprünglichen XML-Siteübersicht verglichen und alle anderen Anpassungen erfolgen auf der SiteMap. Es werden nur die Unterschiede in der verwalteten Lösung integriert. Diese Unterschiede umfassen Elemente, die geändert, bewegt, hinzugefügt oder entfernt wurden. Wenn die verwaltete Lösung in einer neuen Organisation installiert wird, werden die Siteübersichtsänderungen mit der XML-SiteMap, die für die Organisation gefunden wurde und auf der die verwaltete Lösung installiert wird, zusammengeführt. Die Benutzer sehen eine neue Siteübersichtsdefinition.  
  
 Zu diesem Zeitpunkt kann ein Anpasser die Siteübersicht auf eine nicht verwaltete Lösung exportieren und diese Siteübersichtsdefinition wird dann alle Elemente der aktiven Siteübersicht enthalten. Ein Anpasser kann die Siteübersicht ändern und sie anschließend als nicht verwaltete Anpassung wieder importieren.  Wenn die verwaltete Lösung später deinstalliert wird, wird die XML-Siteübersicht, die mit der verwalteten Lösung importiert wurde, referenziert, um die Änderungen zu entfernen, die mit der verwalteten Lösung übernommen wurden. Es wird eine aktive neue Siteübersicht berechnet.  
  
 Wenn ein neues sichtbares Element zur SiteMap hinzugefügt wird, wird es am unteren Rand des dazugehörigen Containers angezeigt. Beispielsweise wird ein neuer Bereich unten im Navigationsbereich angezeigt. Um die Elemente zu positionieren, die hinzugefügt wurden, müssen Sie die Siteübersicht exportieren und bearbeiten um die genaue Position festzulegen und sie dann als nicht verwaltete Lösung erneut importieren.  
  
> [!NOTE]
>  Eine Siteüersichtanpassung kann zwischen der Veröffentlichung erfolgen. Alle nicht veröffentlichten Siteübersichtsanpassungen gehen verloren, wenn eine neue Siteübersichtsdefinition importiert wird.  
  
<a name="BKMK_MergingOptionSetOptions"></a>   
## <a name="merge-option-set-options"></a>Optionssatz-Optionen zusammenführen  
 Bei jeder neuen Optionssatzoption wird ein ganzzahliger Wert zugeteilt,, der einen Optionswertpräfix enthält. Der Optionswertpräfix ist ein Satz von fünf Ziffern, die dem Optionswert vorangestellt werden. Ein Optionswertpräfix wird basierend auf dem Lösungsherausgeberanpassungspräfix erstellt, kann aber auf einen beliebigen Wert festgelegt werden. Der Optionswertpräfix hilft, neue Optionssatzoptionen zu differenzieren, die im Kontext eines bestimmten Lösungsherausgebers erstellt wurden und verringert die Möglichkeit zur Kollision mit Optionswerten. Die Verwendung des Optionswertpräfixes ist empfohlen, aber nicht erforderlich.  
  
 Eine verwaltete Lösung aktualisiert oder fügt gewöhnlich Optionen für Optionssätze hinzu, die in der Organisation sind, zum Beispiel die Kontengruppe oder die Branchenoptionssätze. Wenn eine verwaltete Lösung, die verfügbaren Optionen in einem Optionssatz verändert, sind alle Optionen, die in der verwalteten Lösung definiert wurden, in der Organisation verfügbar. Wenn die verwaltete Lösung deinstalliert wurde, werden die Optionssatzoptionen ihrem ursprünglichen Status zurückgegeben.  
  
### <a name="see-also"></a>Siehe auch  
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Verwaltete Eigenschaften nutzen](use-managed-properties.md)   
 [Anpassen der Entitätsformulare](/dynamics365/customer-engagement/developer/customize-dev/customize-entity-forms)   
 [Anwendungsnavigation mithilfe von SiteMap ändern](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap)
