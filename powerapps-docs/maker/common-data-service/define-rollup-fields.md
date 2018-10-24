---
title: Definieren von Rollupfeldern mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Rollupfelder definiert werden.
ms.custom: ''
ms.date: 05/23/2018
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
ms.assetid: ff0504a1-01bd-4f9b-b884-7f84911d86c3
caps.latest.revision: 58
ms.author: matp
manager: kvivek
ms.openlocfilehash: c76162747ac2bda27c46895290e5943b7f46739f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682522"
---
# <a name="define-rollup-fields-that-aggregate-values"></a>Definieren von Rollupfeldern, die Werte aggregieren

Mithilfe von Rollupfeldern können Benutzer durch die Überwachung wichtiger Geschäftsmetriken Erkenntnisse aus Daten gewinnen. Ein Rollupfeld enthält einen Aggregatwert, der über die Datensätze im Zusammenhang mit einem bestimmten Datensatz berechnet wird. Dies schließt reguläre Entitäten und Aktivitätsentitäten wie E-Mails und Termine ein.

In komplexeren Szenarien können Sie Daten über die Hierarchie der Datensätze aggregieren. Als Administrator oder Anpasser können Sie mithilfe der Anpassungstools Rollupfelder in PowerApps definieren, ohne Code schreiben zu müssen.  
  
<a name="BKMK_benefitsandcapabilities"></a> 
 
## <a name="rollup-fields-benefits-and-capabilities"></a>Vorteile und Möglichkeiten von Rollupfeldern  

Zu den Vorteilen und Möglichkeiten von Rollupfeldern zählt Folgendes:  
  
- Einfache visuelle Bearbeitung. Mithilfe des Feld-Editors können Sie Rollupfelder erstellen, ganz so, als ob Sie ein reguläres Feld erstellen würden.  
- Große Auswahl von Aggregatfunktionen. Mithilfe der folgenden Funktionen können Sie Daten aggregieren: `SUM`, `COUNT`, `MIN`, `MAX` und `AVG`.  
- Umfassende Filterunterstützung für die Aggregation. Sie können beim Festlegen mehrerer Bedingungen verschiedene Filter für die Quellentität oder eine verknüpfte Entität festlegen.  
- Nahtlose Integration in die Benutzeroberfläche. Sie können die Rollupfelder in Formulare, Ansichten, Diagramme und Berichte einfügen.  
- Rollupfelder sind Lösungskomponenten. Sie können Rollupfelder problemlos als Komponenten zwischen Umgebungen verschieben und diese in Lösungen verteilen.  
- Rollupfelder und berechnete Felder ergänzen sich gegenseitig. Sie können ein Rollupfeld als Bestandteil des berechneten Felds verwenden und umgekehrt.  
- Sie können Rollupfelder für die Verwendung von benutzerdefinierten Steuerelementen konfigurieren.  
  
 Zu Rollupfeldern gehören beispielsweise Folgende:  
  
- Geschätzter Gesamtumsatz der offenen Verkaufschancen einer Firma  
- Geschätzter Gesamtumsatz der offenen Verkaufschancen aller Firmen in einer Hierarchie  
- Geschätzter Gesamtumsatz einer Verkaufschance, einschließlich untergeordneter Verkaufschancen  
- Geschätzter Gesamtwert der qualifizierten Leads, die durch eine Kampagne generiert wurden  
- Anzahl der offenen Fällen mit hoher Priorität für alle Firmen in einer Hierarchie  
- Früheste Erstellungszeit aller offenen Fälle mit hoher Priorität für eine Firma  
  
Jedes Rollupfeld erstellt zwei zusätzliche Felder mit dem Suffixmuster *&lt;Feldname&gt;*`_date` und *&lt;Feldname&gt;*`_state`. Das Feld `_date` enthält DateTime-Daten, während das Feld `_state` Integer-Daten enthält. Das Feld `_state` enthält die folgenden Werte:  
  
|Wert|Status|Beschreibung|  
|-|-|-|  
|0|NotCalculated|Der Wert des Felds ist noch nicht berechnet.|  
|1|Berechnet|Der Wert des Felds wurde zum Zeitpunkt der letzten Aktualisierung im Feld „_date“ berechnet.|  
|2|OverflowError|Die Berechnung des Feldwerts hat zu einem Überlauffehler geführt.|  
|3|OtherError|Bei der Berechnung des Feldwerts ist ein interner Fehler aufgetreten. Dieser wird aller Wahrscheinlichkeit nach durch die folgende Ausführung des Berechnungsauftrags behoben.|  
|4|RetryLimitExceeded|Bei der Berechnung des Feldwerts ist ein Fehler aufgetreten, da die maximale Anzahl von Wiederholungsversuchen zur Berechnung des Werts aufgrund einer hohen Anzahl von Parallelität und Sperrkonflikten überschritten wurde.|  
|5|HierarchicalRecursionLimitReached|Bei der Berechnung des Feldwerts ist ein Fehler aufgetreten, da der maximale Hierarchietiefenwert für die Berechnung erreicht wurde.|  
|6|LoopDetected|Bei der Berechnung des Feldwerts ist ein Fehler aufgetreten, da eine rekursive Schleife in der Hierarchie des Datensatzes erkannt wurde.|  
  
<a name="BKMK_calculations"></a>  
 
## <a name="rollup-calculations"></a>Rollupberechnungen  

Die Rollups werden durch geplante Systemaufträge berechnet, die asynchron im Hintergrund ausgeführt werden. Sie müssen ein Administrator sein, um die Rollupaufträge anzeigen und verwalten zu können. 

### <a name="view-rollup-jobs"></a>Anzeigen von Rollupaufträgen

Um Rollupaufträge anzuzeigen, gehen Sie wie folgt vor:

1. Beim Anzeigen der **Common Data Services-Standardlösung** bearbeiten Sie die URL, entfernen alles nach `dynamics.com` und aktualisieren die Seite.
2. Klicken Sie im Bereich **Einstellungen** auf **System** > **Systemaufträge**.<br />![Navigation zu „Systemaufträge“](media/navigate-system-jobs.png)
1. Klicken Sie in der Ansichtsauswahl auf **Seriensystemaufträge**.
2. Um schnell einen relevanten Auftrag zu finden, können Sie nach dem Typ „Systemauftrag“ filtern: **Massenberechnung des Rollupfelds** oder **Rollupfeld berechnen**.
 
### <a name="mass-calculate-rollup-field"></a>Massenberechnung des Rollupfelds

**Massenberechnung des Rollupfelds** ist ein Serienauftrag, der pro Rollupfeld erstellt wird. Er wird einmal ausgeführt, nachdem Sie ein Rollupfeld erstellt oder aktualisiert haben. Der Auftrag berechnet den angegebenen Wert des Rollupfelds in allen bereits vorhandenen Datensätzen neu, die dieses Feld enthalten. Standardmäßig wird der Auftrag 12 Stunden nach der Erstellung oder Aktualisierung eines Felds ausgeführt. Wenn der Auftrag abgeschlossen ist, wird er automatisch für die Ausführung in ferner Zukunft (ungefähr in 10 Jahren) geplant. Wenn das Feld geändert wird, wird der Auftrag für die erneute Ausführung 12 Stunden nach dem Update zurückgesetzt. Die 12-Stunden-Verzögerung ist erforderlich, um sicherzustellen, dass **Massenberechnung des Rollupfelds** außerhalb der Betriebszeit der Umgebung ausgeführt wird. Ein Administrator sollte die Startzeit eines Auftrags vom Typ **Massenberechnung des Rollupfelds** anpassen, nachdem das Rollupfeld erstellt oder geändert wurde, sodass dieser außerhalb der Betriebszeiten ausgeführt wird. Um eine effiziente Verarbeitung der Rollupfelder sicherzustellen, wäre beispielsweise Mitternacht ein guter Zeitpunkt für die Auftragsausführung.  

### <a name="calculate-rollup-field"></a>Rollupfeld berechnen 

**Rollupfeld berechnen** ist ein Serienauftrag, der inkrementelle Berechnungen von allen Rollupfeldern in den vorhandenen Datensätzen für eine bestimmte Entität ausführt. Es gibt nur einen Auftrag vom Typ **Rollupfeld berechnen** pro Entität. Inkrementelle Berechnungen bedeuten, dass der Auftrag vom Typ **Rollupfeld berechnen** die Datensätze verarbeitet, die nach der letzten Ausführung des Auftrags **Massenberechnung des Rollupfelds** erstellt, aktualisiert oder gelöscht wurden. Für die maximale Anzahl von Wiederholungen ist standardmäßig eine Stunde festgelegt. Der Auftrag wird automatisch erstellt, wenn das erste Rollupfeld für eine Entität erstellt und gelöscht und das letzte Rollupfeld gelöscht wird.  

## <a name="online-recalculation-option"></a>Onlineneuberechnungsoption
Wenn Sie mit dem Mauszeiger auf das Rollupfeld im Formular zeigen, können Sie den Zeitpunkt des letzten Rollups sehen und den Rollupwert durch Klicken auf das Aktualisierungssymbol neben dem Feld aktualisieren. Dies wird nachfolgend veranschaulicht:  

![Rollupfeld im Firmenformular](media/rollup-field-on-account-form.png)
  

Es gibt einige Überlegungen, die Sie bei der Verwendung der Onlineneuberechnungsoption (manuelle Aktualisierung des Formulars) bedenken sollten:  
  
- Sie benötigen Schreibberechtigungen für die Entität und Schreibzugriffsrechte für den Quelldatensatz, für den Sie die Aktualisierung anfordern. Wenn Sie z.B. den geschätzten Umsatz aus den offenen Verkaufschancen einer Firma berechnen, müssen Sie keine Schreibberechtigungen für die Entität der Verkaufschance besitzen, sondern nur für die Firmenentität.  
- Diese Option ist nur im Onlinemodus verfügbar. Sie kann nicht im Offlinemodus verwendet werden.  
- Die maximale Anzahl von Datensätzen bei der Aktualisierung des Rollups ist auf 50.000 Datensätze beschränkt. Beim hierarchischen Rollup gilt dies für die verknüpften Datensätze in der gesamten Hierarchie. Wenn das Limit überschritten wird, wird eine Fehlermeldung angezeigt: *Es können keine Onlineberechnungen durchgeführt werden, da das Berechnungslimit für 50.000 verknüpfte Datensätze erreicht wurde.* Dieser Grenzwert gilt nicht, wenn das Rollup von den Systemaufträgen automatisch neu berechnet wird.  
- Die maximale Hierarchietiefe ist auf 10 für den Quelldatensatz beschränkt. Wenn das Limit überschritten wird, wird eine Fehlermeldung angezeigt: *Es können keine Onlineberechnungen durchgeführt werden, da das Hierarchietiefenlimit für 10 Quelldatensätze erreicht wurde.* Dieser Grenzwert gilt nicht, wenn das Rollup von den Systemaufträgen automatisch neu berechnet wird.  

## <a name="modify-rollup-job-recurrence"></a>Ändern der Wiederholungen von Rollupaufträgen

Als Systemadministrator können Sie das Serienmuster für Rollupaufträge ändern, verschieben, anhalten oder den Rollupauftrag fortsetzen. Allerdings können Sie keine Rollupaufträge abbrechen oder löschen. 

Zum Anhalten, Verschieben, Fortsetzen oder Ändern des Wiederholungsmusters müssen Sie die Systemaufträge anzeigen. Weitere Informationen finden Sie unter [Anzeigen von Rollupaufträgen](#view-rollup-jobs). 

Wählen Sie auf der Navigationsleiste **Aktionen** und dann die gewünschte Aktion aus. 

Die verfügbaren Auswahlaktionen für den Auftrag **Massenberechnung des Rollupfelds** lauten: **Fortsetzen**, **Verschieben**, und **Anhalten**. 

Die verfügbaren Auswahlaktionen für den Auftrag **Rollupfeld berechnen** lauten: **Serie ändern**, **Fortsetzen**, **Verschieben** und **Anhalten**.  
  
<a name="BKMK_businessscenarios"></a>  
 
## <a name="examples"></a>Beispiele 

Werfen wir einen Blick auf einige Beispiele für Rollupfelder. Wir aggregieren Daten für einen Datensatz aus den verknüpften Datensätzen mit und ohne Hierarchie. Zudem aggregieren wir Daten für einen Datensatz aus verknüpften Aktivitäten und Aktivitäten, die indirekt mit einem Datensatz über die ActivityParty-Entität verknüpft sind. In jedem Beispiel definieren wir das Rollupfeld mit dem Feld-Editor. Um den Feld-Editor zu öffnen, öffnen Sie den Lösungs-Explorer, und erweitern Sie **Komponenten** > **Entitäten**. Wählen Sie die gewünschte Entität und dann **Felder** aus. Wählen Sie **Neu** aus. Geben Sie im Editor die erforderlichen Informationen für das Feld ein, einschließlich **Feldtyp** und **Datentyp**. Nachdem Sie den Datentyp ausgewählt haben, klicken Sie unter **Feldtyp** auf **Rollup**. Zu den Datentypen zählen „decimal“ oder „integer“, „currency“ und „datetime“. Klicken Sie neben dem **Feldtyp** auf **Bearbeiten**. Dadurch gelangen Sie zum Editor für die Definition von Rollupfeldern. Die Definition von Rollupfeldern besteht aus drei Abschnitten: **Quellentität**, **Verknüpfte Entität** und **Aggregation**.  
  
-   Im Abschnitt **Quellentität** geben Sie die Entität, für die das Rollupfeld definiert ist, und geben außerdem an, ob Sie über eine Hierarchie aggregieren. Sie können Filter mit mehreren Bedingungen hinzufügen, um Datensätze in der Hierarchie, die Sie für das Rollup verwenden möchten, festzulegen.  
  
-   Im Abschnitt **Verknüpfte Entität** geben Sie die Entität an, über die Sie aggregieren. Dieser Abschnitt ist optional, wenn Sie das Rollup über die Hierarchie in der Quellentität ausführen. Sie können Filter mit mehreren Bedingungen hinzufügen, um anzugeben, welche verknüpften Datensätze bei der Berechnung verwendet werden sollen. Beispielsweise können Sie die Umsatzerlöse aus den offenen Verkaufschancen mit einem Jahresumsatz von mehr als 1.000 USD einbeziehen.  
  
-   Im Abschnitt **Aggregieren** geben Sie die Metrik an, die berechnet werden soll. Sie können verfügbare Aggregatfunktionen auswählen, z.B. SUM, COUNT, MIN, MAX oder AVG.  
  
### <a name="aggregate-data-for-a-record-from-related-records"></a>Aggregieren von Daten für einen Datensatz aus verknüpften Datensätzen  

In diesem Beispiel wird keine Hierarchie verwendet. Der geschätzte Gesamtumsatz wird aus den entsprechenden offenen Verkaufschancen für eine Firma berechnet.  

![Aggregieren des geschätzten Umsatzes für eine Firma](media/rollup-field-no-hierarchy.png)
  
### <a name="aggregate-data-for-a-record-from-the-child-records-over-the-hierarchy"></a>Aggregieren von Daten für einen Datensatz aus untergeordneten Datensätzen über die Hierarchie 
 
In diesem Beispiel wird der geschätzte Gesamtumsatz einer Verkaufschance über die Hierarchie berechnet, einschließlich der untergeordneten Verkaufschancen.  
  
![Aggregieren des geschätzten Umsatzes, Hierarchie der Verkaufschancen](media/rollup-field-hierarchy-self.png)
  
### <a name="aggregate-data-for-a-record-from-the-related-records-over-the-hierarchy"></a>Aggregieren von Daten für einen Datensatz aus verknüpften Datensätzen über die Hierarchie

In diesem Beispiel wird der geschätzte Gesamtumsatz der offenen Verkaufschancen in allen Firmen über die Hierarchie berechnet.  
  
![Aggregieren des geschätzten Umsatzes über die Firmenhierarchie](media/rollup-field-hierarchy.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities"></a>Aggregieren von Daten für einen Datensatz aus allen verknüpften Aktivitäten
  
In diesem Beispiel wird die gesamte Zeit berechnet, die für alle Aktivitäten im Zusammenhang mit einer Firma aufgewendet und abgerechnet wird. Dies kann die Zeit beinhalten, die für Telefonate, Termine oder benutzerdefinierte Aktivitäten aufgewendet wird.  
  
In früheren Releases konnten Sie ein Rollupfeld für eine einzelne Aktivität definieren, z.B. einen Telefonanruf, ein Fax oder einen Termin. Um das Ergebnis des unten stehenden Beispiels jedoch zu erreichen, mussten Sie den Gesamtwert der Daten mithilfe der berechneten Felder berechnen. Nun können Sie all dies in einem einzigen Schritt tun, indem Sie ein Rollupfeld für die Aktivitätsentität definieren.  
  
![Rollup aller Aktivitäten für eine Firma](media/rollup-enhancements-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities-and-activities-indirectly-related-via-the-activity-party-entity"></a>Aggregieren von Daten für einen Datensatz aus allen verknüpften Aktivitäten und Aktivitäten, die indirekt über die Aktivitätsparteientität verknüpft sind  

In diesem Beispiel zählen wir die Gesamtanzahl der an eine Firma gesendeten E-Mails, wobei die Firma in der Zeile „An Empfänger“ oder „Empfänger (Cc:)“ der E-Mail aufgeführt wird. Dies erfolgt durch Angabe von **Teilnahmetyp** unter **FILTER** für die Aktivitätsparteientität in der Definition von Rollupfeldern. Wenn Sie die Filterung nicht verwenden, werden alle verfügbaren Teilnahmetypen für eine Aktivität in der Berechnung verwendet. 
 
Weitere Informationen zur Aktivitätsparteientität und zu den für eine bestimmte Aktivität verfügbaren Teilnahmetypen finden Sie unter [ActivityParty-Entität](/dynamics365/customer-engagement/developer/activityparty-entity).

  
![Mit Rollups verknüpfte Aktivitäten und Aktivitätspartei](media/rollup-enhancements-indirect-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-related-records-using-the-avg-operator"></a>Aggregieren von Daten für einen Datensatz aus verknüpften Datensätzen mithilfe des AVG-Operators

In diesem Beispiel wird ein geschätzter durchschnittlicher Umsatz aus allen Verkaufschancen im Zusammenhang mit einer Firma berechnet.  
  
![Durchschnittlicher geschätzter Umsatz in Dynamics 365](media/rollup-enhancements-average.PNG)  
  
Das folgende Beispiel zeigt, wie Sie einen durchschnittlichen geschätzten Umsatz aus verknüpften Verkaufschancen über eine Hierarchie von Firmen berechnen. Der durchschnittlich geschätzte Umsatz kann auf jeder Ebene in der Hierarchie angezeigt werden.  
  
![Durchschnittlicher geschätzter Umsatz in Dynamics 365](media/cust-rollup-enhancements-avg-over-hierarchy.png)  
  
<a name="BKMK_considerations"></a> 

## <a name="rollup-field-considerations"></a>Überlegungen zu Rollupfeldern 

Bei der Arbeit mit Rollupfeldern sollten Ihnen bestimmte Bedingungen und Einschränkungen bewusst sein:  
  
- Sie können maximal 100 Rollupfelder für die Organisation und bis zu 10 Rollupfelder pro Entität definieren.  
- Ein Workflow kann nicht durch Aktualisierungen der Rollupfelder ausgelöst werden.  
- Ein Workflow im Wartezustand kann kein Rollupfeld verwenden.  
- Ein Rollup über das Rollupfeld wird nicht unterstützt.  
- Ein Rollup kann kein berechnetes Feld sein, mit dem ein weiteres berechnetes Feld wird, auch wenn sich alle Felder des berechneten Felds in der aktuellen Entität befinden.  
- Das Rollup kann nur Filter auf die Quellentität oder verknüpfte Entitäten, einfache Felder oder nicht komplexe berechnete Felder anwenden.  
- Ein Rollup kann nur über verknüpfte Entitäten mit der 1:n-Beziehung durchgeführt werden. Ein Rollup kann nicht über m:n-Beziehungen ausgeführt werden.  
- Ein Rollup kann nicht über die 1:n-Beziehung für die Aktivitätsentität oder Aktivitätsparteientität ausgeführt werden.  
- Die Geschäftsregeln, Workflows oder berechneten Felder verwenden immer den letzten berechneten Wert des Rollupfelds.  
- Ein Rollupfeld wird im Benutzerkontext des Systems aggregiert. Alle Benutzer können den gleichen Wert des Rollupfelds sehen. Sie können die Sichtbarkeit des Rollupfelds mit der Sicherheit auf Feldebene (Field Level Security, FLS) steuern, indem Sie einschränken, wer auf das Rollupfeld zugreifen kann. Weitere Informationen [Sicherheit auf Feldebene zum Steuern des Zugriffs](/dynamics365/customer-engagement/admin/field-level-security). 

### <a name="precision-rounding"></a>Runden der Genauigkeit
 
Ist die Genauigkeit des aggregierten Felds größer als die Genauigkeit des Rollupfelds, wird die Genauigkeit des aggregierten Felds auf die Genauigkeit des Rollupfelds abgerundet, bevor die Aggregation durchgeführt wird. Um dieses Verhalten zu veranschaulichen, betrachten wir ein konkretes Beispiel. Nehmen wir an, dass das Rollupfeld für die Firmenentität, das für die Berechnung des gesamten geschätzten Umsatzes der verknüpften Verkaufschancen verwendet wird, eine Genauigkeit von zwei Dezimalstellen aufweist. Das Feld „Gesch. Umsatz“ in der Verkaufschancenentität ist das aggregierte Feld mit einer Genauigkeit von vier Dezimalstellen. In diesem Beispiel verfügt die Firma über zwei verknüpfte Verkaufschancen. Die aggregierte Summe des geschätzten Umsatzes wird wie folgt berechnet:  
  
1. Gesch. Umsatz für die erste Verkaufschance: 1.000,0041 USD  
1. Gesch. Umsatz für die erste Verkaufschance: 2.000,0044 USD  
1. Aggregierte Summe des gesch. Umsatzes: 1.000,00 USD + 2.000,00 USD = 3.000,00 USD

Wie Sie sehen können, erfolgt die Rundung der Genauigkeit auf zwei Dezimalstellen für das Aggregatfeld, bevor die Aggregation durchgeführt wird.  
  
### <a name="different-behavior-from-associated-grids"></a>Anderes Verhalten bei zugeordneten Rastern
 
Bestimmte integrierte Entitätsformulare, z.B. Firma oder Kontakt, enthalten die zugeordneten Raster. Beispielsweise enthält ein Firmenformular Kontakte, Fälle, Verkaufschancen und andere Raster. Einige der Datensätze, die in den Firmenformularrastern dargestellt werden, beziehen sich direkt auf den Firmendatensatz, wohingegen andere Felder indirekt über die Beziehungen mit anderen Datensätzen dargestellt werden. Im Gegensatz dazu verwendet die Aggregation der Rollupfelder nur direkte Beziehungen, die explizit in der Definition der Rollupfelder definiert sind. Es werden keine anderen Beziehungen berücksichtigt. Um das unterschiedliche Verhalten zu veranschaulichen, sehen wir uns das folgende Beispiel an.  
  
1. Die Firma A1 enthält einen primären Kontakt: P1. Der Fall C1 bezieht sich auf die Firma A1 (Feld „C1.Customer“ = A1) und Fall C2 auf Kontakt P1 (Feld „C2.Customer“ = P1).  
1. Das Raster **Fälle** im Formular **Firma** für den A1-Datensatz zeigt zwei Fälle an: C1 und C2.  
1. Über das Rollupfeld für die Firmenentität „Gesamtanzahl der Fälle“ werden die Fälle gezählt, die der Firma zugeordnet sind.  
1. In der Definition der Firmenrollupfelder geben wir die Fälle an, bei denen eine Kundenbeziehung mit der Firma besteht. Nach der Aggregation beträgt die Gesamtanzahl der Fälle 1 (Fall C1). Fall C2 wird nicht im Gesamtwert berücksichtigt, da er sich direkt auf den Kontakt bezieht, nicht auf die Firma. Zudem kann er nicht explizit in der Definition der Firmenrollupfelder definiert werden. Daher entspricht die Gesamtzahl der Fälle, die vom Rollupvorgang zurückgegeben wird, nicht der Anzahl der Fälle, die im Raster **Fälle** gezeigt wird.  
  
### <a name="see-also"></a>Siehe auch  

[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Definieren von berechneten Feldern zur Automatisierung von manuellen Berechnungen](define-calculated-fields.md)<br />
[Verhalten und Format des Felds „Datum und Uhrzeit“](behavior-format-date-time-field.md)<br />
[Definieren und Abfragen von hierarchiebezogenen Daten](define-query-hierarchical-data.md)<br />
[Video: Rollup- und berechnete Felder](http://www.youtube.com/watch?v=RoahCH1p3T8&list=PLC3591A8FE4ADBE07&index=8) (in englischer Sprache)<br />
[Video: Verwendung von Power BI](http://www.youtube.com/watch?v=PkQe4BFlBS8&list=PLC3591A8FE4ADBE07&index=3) (in englischer Sprache)
