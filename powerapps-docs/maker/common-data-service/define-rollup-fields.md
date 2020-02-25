---
title: Rollupfelder definieren mit Power Apps | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Rollup-Felder definieren
ms.custom: ''
ms.date: 01/23/2020
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
ms.assetid: ff0504a1-01bd-4f9b-b884-7f84911d86c3
caps.latest.revision: 58
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ee3e6b75202e901e72af7bc353770add253f2038
ms.sourcegitcommit: 2fd8b682e2d4c1e6a45c851b56f37f842ef18224
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2020
ms.locfileid: "2982455"
---
# <a name="define-rollup-fields-that-aggregate-values"></a>Definition von Rollupfeldern, die Werte aggregieren

Rollupfelder helfen Benutzern, Einblicke in die Daten zu erhalten, indem Sie Schlüsselunternehmensmetriken überwachen. Ein Rollupfeld enthält einen Gesamtwert, der über die Datensätze berechnet wird, die mit einem bestimmten Datensatz verknüpft sind. Dies umfasst reguläre Entitäten und Aktivitätsentitäten wie E-Mails und Termine.

In den komplexeren Szenarien können Sie Daten über die Hierarchie von Datensätzen aggregieren. Wenn Sie Administrator oder Anpasser sind, können Sie Rollupfelder mithilfe der Anpassungstools in Power Apps definieren, ohne dass hierfür Code geschrieben werden muss.  
  
<a name="BKMK_benefitsandcapabilities"></a> 
 
## <a name="rollup-fields-benefits-and-capabilities"></a>Vorzüge und Funktionen der Rollupfelder  

Die Vorzüge und Fähigkeiten von Rollupfeldern sind Folgende:  
  
- Sichtbearbeitung ist einfach. Sie können die Rollupfelder erstellen, indem Sie den Feld-Editor verwenden, genauso wie wenn Sie ein normales Feld erstellen.  
- Breite Auswahl von Aggregatfunktionen. Sie können Daten aggregieren, indem Sie die folgenden Funktionen nutzen: `SUM`, `COUNT`, `MIN`, `MAX` und `AVG`.  
- Vollständiger Filtersupport für Aggregation. Sie können verschiedene Filter für die Quellentität oder verknüpfte Entität beim Festlegen mehrerer Bedingungen festlegen.  
- Nahtlose Integration mit der Benutzeroberfläche. Sie können die Rollupfelder in Formulare, Ansichten, Diagramme und Berichte einschließen.  
- Rollupfelder sind Lösungskomponenten. Sie können die Rollupfelder einfach als Komponenten zwischen Umgebungen transportieren und sie in Lösungen verteilen.  
- Rollupfelder und die berechneten Felder sind gegenseitig komplementär. Sie können ein Rollpfeld im Rahmen einesberechneten Felds verwenden und umgekehrt.  
- Sie können Sie Rollup-Felder konfigurieren, um benutzerdefinierte Steuerelemente zu verwenden.  
  
 Einige Beispiele von Rollupfeldern sind:  
  
- Gesamter geschätzter Umsatz der offenen Verkaufschancen eines Kontos  
- Gesamter geschätzter Umsatz aus offenen Verkaufschancen in allen Konten in einer Hierarchie  
- Gesamter geschätzter Umsatz einer Verkaufschance einschließlich untergeordneter Verkaufschancen  
- Gesamter geschätzter Wert der qualifizierten Leads, die durch eine Kampagne generiert wurden  
- Anzahl der offenen Anfragen mit hoher Priorität für alle Konten in einer Hierarchie  
- Früheste erstellte Zeit aller offenen Anfragen mit hoher Priorität für ein Konto  
  
Jedes Rollupfeld erstellt zwei zusätzliche Felder mit dem Suffixmuster *&lt;fieldname&gt;*`_date` und *&lt;fieldname&gt;*`_state`. Das `_date`-Feld enthält Datum-Zeit-Daten und das `_state` Feld enthält Ganzzahldaten. Das Feld `_state` hat folgende Werte:  
  
|Value|Status|Beschreibung|  
|-|-|-|  
|0|NotCalculated|Der Feldwert muss noch berechnet werden.|  
|1|Calculated|Der Feldwert wurde anhand der letzten Aktualisierungszeit im Feld _date Gebiet berechnet.|  
|2|OverflowError|Die Feldwertberechnung ergab einen Überlauffehler.|  
|3|OtherError|Fehler bei der Berechnung des Feldwerts aufgrund eines internen Fehlers. Bei der folgenden Ausführung des Berechnungsauftrags wird er wahrscheinlich behoben.|  
|4|RetryLimitExceeded|Die Feldwertberechnung schlug fehl, weil die maximale Anzahl von Wiederholungsversuchen, den Wert zu berechnen aufgrund der großen Anzahl von Parallelitäts- und Sperrkonflikte überschritten wurde.|  
|5|HierarchicalRecursionLimitReached|Die Feldwertberechnung schlug fehl, da die maximale Hierarchientiefengrenze für die Berechnung erreicht wurde.|  
|6|LoopDetected|Die Feldwertberechnung schlug fehl, da eine Schleife in der Hierarchie des Datensatzes erkannt wurde.|  
  
<a name="BKMK_calculations"></a>  
 
## <a name="rollup-calculations"></a>Rollupberechnungen  

Die Rollups werden nach geplanten Systemaufträgen berechnet, die asynchron im Hintergrund ausgeführt werden. Sie müssen ein Administrator sein, um die Rollupaufträge, anzeigen und verwalten zu können. 

### <a name="view-rollup-jobs"></a>Rollup-Aufträge anzeigen

So zeigen Sie Rollup-Aufträge an:

1. Beim Anzeigen der **Common Data Service-Standardlösung** bearbeiten Sie die URL und entfernen alles nach `dynamics.com` und aktualisieren die Seite.
2. Wählen Sie im Bereich **Einstellungen** und **System** > **Systemaufträge**.<br />![Navigieren zu Systemaufträgen](media/navigate-system-jobs.png)
1. In der Ansichtsauswahl wählen Sie **Seriensystemaufträge** aus.
2. Um einen relevanten Vorgang schnell zu finden, können Sie nach dem Systemauftragstyp filtern: **Rollupfeld Massenberechnung** oder **Rollupfeld Neuberechnung**.
 
### <a name="mass-calculate-rollup-field"></a>Massenberechnung des Rollupfelds

**Rollupfeld-Massenberechnung** sind ein iterativer Vorgang, der pro Rollupfeld erstellt wird. Er wird einmal ausgeführt, wenn Sie ein Rollupfeld erstellt oder aktualisiert haben. Der Vorgang berechnet den angegebenen Rollupfeldwert in allen vorhandenen Datensätzen neu, die dieses Feld enthalten. Standardmäßig wird der Vorgang 12 Stunden, nachdem Sie ein Feld erstellt oder aktualisiert haben, ausgeführt. Wenn der Vorgang abgeschlossen ist, wird automatisch geplant, ihn in der ferneren in der Zukunft, in 10 Jahren, auszuführen. Wenn das Feld geändert wird, wird der Vorgang zurückgesetzt, um 12 Stunden nach dem Update erneut ausgeführt zu werden. Die 12-stündige Verzögerung ist erforderlich, um zu gewährleisten, dass das **Massenberechnungs-Rollupfeld** nicht in den Betriebsstunden der Umgebung ausgeführt wird. Es wird empfohlen, dass ein Administrator die Startzeit des **Massenberechnungs-Rollupfeld**-Auftrags anpasst, nachdem das Rollupfeld erstellt oder geändert wurde, sodass er in Nicht-Betriebsstunden ausgeführt wird. Beispielsweise ist Mitternacht eine gute Zeit, um den Auftrag zu aktivieren, um eine effizienten Verarbeitung der Rollupfelder zu gewährleisten.  

### <a name="calculate-rollup-field"></a>Rollupfeld berechnen 

**Rollupfelder berechnen** ist ein iterativer Auftrag, der inkrementelle Berechnungen aller Rollupfelder in den vorhandenen Datensätzen für eine bestimmte Entität ausführt. Es gibt nur einen Auftrag **Rollupfeldfeld berechnen** pro Entität. Die inkrementellen Berechnungen bedeuten, dass der **Rollupfeld berechnen**-Auftrag die Datensätze verarbeitet, die nach der letzten abgeschlossenen Ausführung des **Massenberechnungs-Rollupfeldes** erstellt, aktualisiert oder gelöscht wurden. Die standardmäßige maximale Wiederholungseinstellung ist auf eine Stunde festgelegt. Der Auftrags wird automatisch erstellt, wenn das erste Rollupfeld für eine Entität erstellen und gelöscht wird, wenn die letzte Rollupfeld gelöscht wird.  

## <a name="online-recalculation-option"></a>Online-Neuberechnungsoption
Das Rollup-Feld im Formular zeigt ein Taschenrechnerbild, einen Rollup-Wert und den Zeitpunkt der letzten Berechnung an. Wählen Sie zum erneuten Berechnen das Taschenrechnerbild die Schaltfläche **Neuberechnen**, die angezeigt wird. 

> [!div class="mx-imgBorder"] 
> ![Rollupfeld auf dem Firmenformular](media/rollup-field-on-account-form.png)
  

Es gibt einige Gesichtspunkte, an die Sie denken sollten, wenn Sie die Online-Neuberechnungsoption verwenden (das Formular manuell aktualisieren):  
  
- Sie müssen Schreibrechte für die Entität und Schreibzugriffsrechte im Quelldatensatz haben, für den Sie die Aktualisierung anfordern. Wenn Sie z. B. den geschätzten Umsatz aus den offenen Verkaufschancen eines Kontos berechnen, müssen Sie nicht die Schreibrechte für die Verkaufschancenentität haben, nur für die Kontoentität.  
- Diese Option ist nur im Onlinemodus verfügbar. Sie können diese nicht im Offlinemodus verwenden.  
- Die maximale Anzahl von Datensätzen während der Rollupaktualisierung ist auf 50.000 Datensätze beschränkt. Im Falle eines hierarchischen Rollups gilt dies für die verknüpften Datensätze in der gesamten Hierarchie. Wenn der Grenzwert überschritten wird, wird eine Fehlermeldung angezeigt: *Es können keine Onlineberechnungen durchgeführt werden, da das Berechnungslimit von 50.000 verknüpften Datensätzen erreicht wurde.* Dieses Limit gilt nicht, wenn der Rollup automatisch durch die Systemaufträge neu berechnet wird.  
- Die maximale Hierarchientiefe ist auf 10 für den Quelldatensatz beschränkt. Wenn der Grenzwert überschritten wird, wird eine Fehlermeldung angezeigt: *Es können keine Onlineberechnungen durchgeführt werden, da das Hierarchietiefenlimit von 10 für den Quelldatensatz erreicht wurde.* Dieses Limit gilt nicht, wenn der Rollup automatisch durch die Systemaufträge neu berechnet wird.  

## <a name="modify-rollup-job-recurrence"></a>Ändern der Rollupauftragswiederholung

Als Systemadministrator können Sie das Rollupauftragsserienmuster ändern und den Rollupauftrag zurückstellen, anhalten oder fortsetzen. Allerdings können Sie einen Rollupauftrag nicht stornieren oder löschen. 

Um ein Serienmuster zu unterbrechen, zu verschieben, wiederaufnehmen oder zu ändern, müssen Sie die Systemaufträge anzeigen. Weitere Informationen [Anzeigen von Rollupaufträgen](#view-rollup-jobs) 

Klicken oder tippen Sie auf der Navigationsleiste auf **Aktionen** und wählen Sie die Aktion aus, die angezeigt werden sollen. 

Für den Auftrag **Rollupfeld-Massenberechnung** sind die verfügbaren Optionen: **Wiederaufnehmen**, **Zurückstellen** und **Anhalten**. 

Für den Auftrag **Rollupfeld Massenberechnung** sind die verfügbaren Optionen: **Wiederholung ändern**, **Wiederaufnehmen**, **Zurückstellen**, und **Anhalten**.  
  
<a name="BKMK_businessscenarios"></a>  
 
## <a name="examples"></a>Beispiele 

Betrachten wir einige Beispiele für Rollupfeler. Wir aggregieren Daten für einen Datensatz aus den verknüpften Datensätzen, mit und ohne Hierarchie. Wir aggregieren auch Daten für einen Datensatz aus zugehörigen Aktivitäten und Aktivitäten mit indirektem Bezug auf einen Datensatz über die ActivityParty-Entität. In jedem Beispiel definieren wir das Rollupfeld, indem wir den Feld-Editor verwenden. Wenn Sie den Feld-Editor öffnen, öffnen Sie den Projektmappen-Explorer und erweitern Sie **Komponenten** > .**Entitäten** Wählen Sie die gewünschte Entität und wählen Sie **Felder** aus. Klicken Sie auf **Neu**. Geben Sie im Editor die für das Feld erforderlichen Informationen an, einschließlich **Feldtyp** und **Datentyp**. In **Feldtyp** wählen Sie die Option **Rollup** aus, nachdem Sie den Datentyp ausgewählt haben. Die Datentypen enthalten Dezimalzahlen oder ganze Zahlen, Währung oder Datum/Uhrzeit. Klicken Sie auf die Schaltfläche **Bearbeiten** neben **Feldtyp**. Dadurch gelangen Sie zum Rollupfelddefinitionseditor. Die Rollupfelddefinition besteht aus drei Abschnitten: **Quellentität**, **Verknüpfte Entität** und **Aggregation**.  
  
-   Geben Sie im Abschnitt **Quellentität** die Entität an, für die das Rollup definiert ist, und ob Sie über eine Hierarchie aggregieren. Sie können Filter mit mehreren Bedingungen hinzufügen, um die Datensätze in der Hierarchie anzugeben, die Sie für das Rollup verwenden möchten.  
  
-   Geben Sie im Abschnitt **Verknüpfte Entität** der Entität an, über die Sie aggregieren. Dieser Abschnitt ist optional, wenn Sie auswählen, den Rollup über der Hierarchie auf der Quellentität auszuführen. Sie können Filter mit mehreren Bedingungen hinzufügen, um anzugeben, welche verknüpften Datensätze Sie in der Berechnung verwenden möchten. Beispielsweise schließen Sie den Umsatz aus den offenen Verkaufschancen mit einem Jahresumsatz von mehr als $1000 ein.  
  
-   Geben Sie im Abschnitt **Aggregieren** die Metrik an, die Sie berechnen möchten. Sie können verfügbare Aggregatfunktionen, wie SUMME, ANZAHL, MIN, MAX oder DURCHSCHNITT auswählen.  
  
### <a name="aggregate-data-for-a-record-from-related-records"></a>Daten für einen Datensatz aus verknüpften Datensätzen aggregieren  

In diesem Beispiel wird eine Hierarchie nicht verwendet. Der gesamte geschätzte Umsatz wird für ein Konto aus den verknüpften offenen Verkaufschancen berechnet.  

![Geschätzten Umsatz für ein Konto aggregieren](media/rollup-field-no-hierarchy.png)
  
### <a name="aggregate-data-for-a-record-from-the-child-records-over-the-hierarchy"></a>Aggregieren von Daten für einen Datensatzes aus den untergeordneten Datensätzen, über die Hierarchie 
 
In diesem Beispiel berechnen wir den gesamten geschätzten Umsatz einer Verkaufschance, einschließlich der untergeordneten Verkaufschancen, über die Hierarchie.  
  
![Geschätzten Umsatz, Verkaufschancenhierarchie aggregieren](media/rollup-field-hierarchy-self.png)
  
### <a name="aggregate-data-for-a-record-from-the-related-records-over-the-hierarchy"></a>Aggregieren von Daten für einen Datensatzes aus den verknüpften Datensätzen, über die Hierarchie

In diesem Beispiel berechnen wir den gesamten geschätzten Umsatz offener Verkaufschancen über alle Konten hinweg, über die Hierarchie.  
  
![Geschätzten Umsatz über Firmenhierarchie aggregieren](media/rollup-field-hierarchy.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities"></a>Daten für einen Datensatz aus allen verknüpften Aktivitäten aggregieren
  
In diesem Beispiel berechnen wir die gesamte benötigte und fakturierte Zeit aus allen Aktivitäten in Bezug auf eine Firma. Hierzu zählen ggf. Zeit am Telefon, bei Terminen oder benutzerdefinierten Aktivitäten.  
  
In älteren Versionen konnten Sie ein Rollupfeld für eine einzelne Aktivität definieren, z. B. einen Telefonanruf, ein Fax oder einen Termin. Um aber das Ergebnis des nachfolgenden Beispiels sicherzustellen, mussten Sie die Daten mithilfe der berechneten Felder summieren. Nun können Sie alles in einem Schritt ausführen, indem Sie ein Rollupfeld für die Aktivitätsentität definieren.  
  
![Rollup aller Aktivitäten für eine Firma](media/rollup-enhancements-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities-and-activities-indirectly-related-via-the-activity-party-entity"></a>Aggregieren von Daten für einen Datensatz aus allen zugehörigen Aktivitäten und Aktivitäten mit indirektem Bezug über die Aktivitätsparteientität  

In diesem Beispiel wird die Gesamtanzahl der E-Mails gezählt, die an eine Firma gesendet werden, wobei die Firma in der "Empfänger (An:)"- oder "Empfänger (Cc)"-Zeile der E-Mail aufgeführt wird. Dies erfolgt durch Angabe von **Teilnahmetyp** in **FILTER** für die Aktivitätsparteientität in der Rollupfelddefinition. Sollen Sie keine Filter verwenden, werden alle verfügbaren Teilnahmetypen für eine Aktivität in der Berechnung verwendet. 
 
Weitere Informationen zu Aktivitätsparteientität und Teilnahmetypen, die für eine bestimmte Aktivität verfügbar sind, finden Sie unter [Aktivitätsparteientität](/dynamics365/customer-engagement/developer/activityparty-entity).

  
![Mit dem Rollup verknüpfte Aktivitäten und Aktivitätspartei](media/rollup-enhancements-indirect-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-related-records-using-the-avg-operator"></a>Daten für einen Datensatz aus verknüpften Datensätzen mit AVG-Operator aggregieren

In diesem Beispiel wird ein durchschnittlicher geschätzter Umsatz aus allen Verkaufschancen, die mit einer Firma verknüpft sind, berechnet.  
  
![Durchschnittlicher geschätzter Umsatz in Dynamics 365](media/rollup-enhancements-average.PNG)  
  
Im folgenden Beispiel wird veranschaulicht, wie Sie einen durchschnittlichen geschätzten Umsatz aus verknüpften Verkaufschancen über eine Firmenhierarchie berechnen. Ein durchschnittlicher geschätzter Umsatz kann auf jeder Ebene in der Hierarchie angezeigt werden.  
  
![Durchschnittlicher geschätzter Umsatz in Dynamics 365](media/cust-rollup-enhancements-avg-over-hierarchy.png)  
  
<a name="BKMK_considerations"></a> 

## <a name="rollup-field-considerations"></a>Rollupfeld - Gesichtspunkte 

Sie sollten bestimmte Bedingungen und Beschränkungen berücksichtigen, wenn Sie mit den Rollupfeldern arbeiten:  
  
- Sie können maximal 100 Rollupfelder für die Organisation und für bis zu 10 Rollupfelder pro Entität definieren.  
- Ein Workflow kann nicht durch das Rollupfeldupdates gestartet werden.  
- Eine Workflow-Wartebedingung kann ein Rollupfeld kann nicht verwenden.  
- Ein Rollup über das Rollupfeld wird nicht unterstützt.  
- Ein Rollup kann nicht auf ein berechnetes Feld verweisen, das ein anderes berechnetes Feld nutze. Dies gilt auch dann, wenn das andere berechnete Feld der aktuellen Entität angehört.  
- Das Rollup kann nur Filter auf die Quellentität oder verknüpfte Entitäten, einfache Felder oder nicht-komplexe berechnete Felder angewendet werden.  
- Ein Rollup kann nur über verknüpften Entitäten mit eine 1:N-Beziehung ausgeführt werden. Ein Rollup kann nicht zu N:N-Beziehungen ausgeführt werden.  
- Ein Rollup kann nicht zur 1:N-Beziehung für die Aktivitätsentität oder die Aktivitätsparteientität ausgeführt werden.  
- Die Unternehmensregeln, Workflows oder berechneten Felder verwenden immer den letzten berechneten Wert des Rollupfelds.  
- Ein Rollupfeld wird unter dem Systembenutzerkontext aggregiert. Alle Benutzer können denselben Rollupfeldwert anzeigen. Sie können die Rollupfeldsichtbarkeit mit der Sicherheit auf Feldebene (FLS) steuern, indem Sie einschränken, wer auf das Rollupfeld zugreifen kann. Weitere Informationen:  [Feldsicherheit, um den Zugriff zu steuern](/dynamics365/customer-engagement/admin/field-level-security). 

### <a name="precision-rounding"></a>Genaues Runden
 
Wenn die Genauigkeit aggregierten Felds größer ist als die Anzahl der Stellen des Rollupfelds, wird die Genauigkeit des aggregierten Felds auf die Anzahl der Stellen des Rollupfelds abgerundet, bevor die Aggregation ausgeführt wird. Um dieses Verhalten vorzuführen, sehen wir uns ein bestimmtes Beispiel an. Angenommen,das Rollupfeld auf der Firmaenentität für die Berechnung des geschätzten Gesamtumsatzes der verknüpften Verkaufschancen hat eine Genauigkeit von zwei Dezimalstellen. Das Feld „Gesch. Umsatz“ für die Verkaufschancenentität ist das aggregierte Feld mit der Genauigkeit von vier Dezimalstellen. In unserem Beispiel hat das Konto zwei verknüpfte Verkaufschancen. Die aggregierte Summe des geschätzten Umsatzes wird berechnet wie folgt:  
  
1. Gesch. Umsatz für die erste Verkaufschance: 1.000,0041 USD  
1. Gesch. Umsatz für die zweite Verkaufschance: 2.000,0044 USD  
1. Aggregierte Summe Gesch. Umsatzerlös: 1000,00 USD + 2000,00 USD = 3000,00 USD

Wie Sie sehen, wird die Genauigkeitsrundung auf zwei Dezimalstellen auf dem aggregierten Feld durchgeführt, bevor die Aggregierung ausgeführt wird.  
  
### <a name="different-behavior-from-associated-grids"></a>Unterschiedliches Verhalten der zugeordneten Raster
 
Bestimmte Entitätsformulare, wie Konto oder Kontakt, enthalten standardmäßig die zugeordneten Raster. Beispielsweise enthält ein Kontaktformular Kontakte, Verkaufschancen, Anfragen und andere Raster. Einige der Datensätze, die in den Kontoformularrastern angezeigt werden, sind direkt mit dem Kontodatensatz verknüpft; andere indirekt über Beziehungen mit anderen Datensätzen. Im Vergleich dazu verwendet die Rollupfeldaggregation nur direkte Beziehungen, die in der Rollupfelddefinition explizit definiert werden. Es werden keine anderen Beziehungen berücksichtigt. Um den Unterschied bezüglich des Verhaltens vorzuführen, sehen ir uns das folgende Beispiel an.  
  
1. Das Konto A1 hat einen primären Kontakt, P1. Die Anfrage C1 ist dem Konto A1 (C1.Customer-Feld = A1) zugeordnet, und die Anfrage C2 ist dem Kontakt P1 zugeordnet (C2.Customer-Feld = P1).  
1. Das Raster **Anfragen** im Formular **Konto** für den A1-Datensatz zeigt zwei Anfragen, C1 und C2.  
1. Das Rollupfeld namens Gesamtzahl der Anfragen in der Kontoentität wird verwendet, um die Anfragen zu zählen, die dem Konto zugeordnet sind.  
1. In der Konto-Rollupfelddefinition geben wir die Anfragen an, die die Kundenbeziehung mit dem Konto haben. Nach der Aggregation ist die Gesamtzahl der Anfrage gleich 1 (Anfrage C1). Die Anfrage C2 ist in der der Summe nicht enthalten, da sie direkt dem Kontakt, nicht dem Konto zugeordnet ist und nicht in der Konti-Rollupfelddefinition explizit definiert werden kann. Deshalb entspricht die Gesamtzahl der Anfragen, die vom Rollupvorgang zurückgegeben werden, nicht der Anzahl der Anfragen, die im Raster **Anfragen** angezeigt werden.  
  
### <a name="see-also"></a>Siehe auch  

[Erstellen und Bearbeiten von Feldern](create-edit-fields.md)<br />
[Definieren berechneter Felder](define-calculated-fields.md)<br />
[Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)<br />
[Hierarchiebezogene Daten festlegen und abfragen](define-query-hierarchical-data.md)<br />
[Video: Rollup und berechnete Felder](https://www.youtube.com/watch?v=RoahCH1p3T8&list=PLC3591A8FE4ADBE07&index=8)<br />
[Video: Verwenden von Power BI](https://www.youtube.com/watch?v=PkQe4BFlBS8&list=PLC3591A8FE4ADBE07&index=3)
