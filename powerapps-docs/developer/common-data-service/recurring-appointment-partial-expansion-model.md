---
title: Teilerweiterungsmodell für Serientermine (Common Data Service) | Microsoft Docs
description: 'Das Teilerweiterungsmodell ist ein asynchroner Auftrag in , der in vorab festgelegten Intervallen ausgeführt wird und auf der Organisationsebene definiert und zum Erstellen wiederkehrender Termininstanzen verwendet wird.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="recurring-appointment-partial-expansion-model"></a>Teilerweiterungsmodell für Serientermine

Common Data Service implementiert ein Teilerweiterungsmodell, um Serientermininstanzen in der Datenbank zu erstellen. Die Serieninformationen, die beim Erstellen eines `RecurringAppointmentMaster`-Datensatzes angegeben wurden, werden verwendet, um einzelne Instanzen schrittweise zu erstellen oder zu synchronisieren. Dies steuert die Erstellung einer großen Anzahl von Termindatensätzen in Common Data Service aufgrund der Erstellung oder Synchronisierung von Serienterminen, die einen großen oder unbegrenzten (kein Enddatum) Serienbereich haben.  

 Das Teilerweiterungsmodell ist ein asynchroner Auftrag in Common Data Service, der in vorab festgelegten Intervallen ausgeführt wird und auf der Organisationsebene mithilfe des Attributs `Organization.RecurrenceExpansionJobBatchInterval` definiert wird. Darüber hinaus hängt das Instanzerweiterungsmodell von einem Parameter auf Organisationsebene ab, wie beispielsweise "n", wobei "n" für die maximale Anzahl von Instanzen steht, die synchron erstellt werden können. Sie können einen geeigneten Wert für diese Variable mithilfe des Attributs `Organization.RecurrenceExpansionSynchCreateMax` angeben. Diese Eigenschaften werden detailliert im Abschnitt [Parameter für den eingeschränkten Erweiterungsauftrag](#Parameter) behandelt.  

<a name="Scenario1"></a>   
## <a name="when-the-recurring-appointment-instances-are-less-than-or-equal-to-n"></a>Wenn die Serientermininstanzen kleiner oder gleich "n" sind  
 Wenn die Anzahl der zu generierenden Instanzen aufgrund der Serieninformationen kleiner oder gleich "n" ist, wird die tatsächliche Anzahl von Instanzen ab dem effektiven Startdatum des Termins synchron erstellt. Jede Instanz wird als Termindatensatz in Common Data Service gespeichert.  

<a name="Scenario2"></a>   

## <a name="when-the-recurring-appointment-instances-are-more-than-n"></a>Wenn die Serientermininstanzen größer oder gleich "n" sind  
 Für jeden Serientermin, der in Common Data Service erstellt wird, wird ein asynchroner Erweiterungsauftrag erstellt. Die Instanzen des Serientermins werden in den folgenden Phasen erweitert:  

1. **Synchrone Erweiterung**: Die ersten "n" Instanzen des Serientermins werden ab dem effektiven Startdatum synchron erstellt. Jede Instanz wird als Termindatensatz gespeichert, wobei das Attribut `Appointment.InstanceTypeCode` auf "2 " (Wiederkehrende Instanz) festgelegt ist. Die Erweiterung der restlichen Instanzen wird an einen asynchronen Auftrag übergeben. Das effektive Startdatum ist das Datum, ab dem die Serienterminserie erweitert werden muss.  

2. **Asynchrone Erweiterung**: Asynchrone Aufträge verarbeiten den restlichen Erweiterungsauftrag und erweitern die Instanzen periodisch in Übereinstimmung mit den Serieninformationen. Die asynchrone Dateierweiterung tritt nur bis zum Fenster für Erweiterung (zukünftig) auf (`Organization.FutureExpansionWindow`). Danach wird ein neuer asynchroner Auftrag erstellt, der die Erweiterung bis zum nächsten Fenster für Erweiterung (zukünftig) verarbeitet. Der asynchrone Dienst erweitert in regelmäßigen Abständen die Instanzen und speichert sie als Termindatensätze im System.  

<a name="Parameter"></a>   
## <a name="parameters-for-the-partial-expansion-job"></a>Parameter für den Teilerweiterungsauftrag  
 Sie müssen geeignete Werte für diese Attribute auf Organisationsebene im `Organization`-Datensatz festlegen, damit das Erweiterungsmodell gemäß Ihren Anforderungen funktioniert. Hierzu müssen Sie über die Rolle "Systemadministrator" oder eine entsprechende Berechtigung verfügen. Die folgende Tabelle enthält Informationen zu diesen Eigenschaften.  


|                    Attribut                     |                                                                                                                                                                                                                    Beschreibung                                                                                                                                                                                                                    |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Organization.RecurrenceExpansionSynchCreateMax  |                                                                                             Dies ist der maximale Anzahl von Termininstanzen, die zum Zeitpunkt der Erstellung oder Synchronisierung eines Serientermins erstellt wird. Sie müssen einen Ganzzahlwert angeben, der der Anzahl von Instanzen entspricht. Dieser Wert entspricht "n".                                                                                              |
|         Organization.PastExpansionWindow         |    Dies ist der maximale gültige Zeitraum in der Vergangenheit, bis zu welchem Serientermine mit Dynamics 365 for Outlook erweitert oder synchronisiert werden können. Sie müssen einen Ganzzahlwert angeben, der der Anzahl von Monaten entspricht.<br /><br /> Der Wert dieses Attributs bestimmt das Vergangenheitsinstanz-Stichdatum zum Erweitern oder Synchronisieren der Serientermininstanzen.    |
|        Organization.FutureExpansionWindow        | Dies ist der maximale gültige Zeitraum in der Zukunft, bis zu welchem Serientermine mit Dynamics 365 for Outlook erweitert oder synchronisiert werden können. Sie müssen einen Ganzzahlwert angeben, der der Anzahl von Monaten entspricht.<br /><br /> Der Wert dieses Attributs bestimmt das Zukunftsinstanz-Stichdatum zum Erweitern oder Synchronisieren der Serientermininstanzen. |
| Organization.RecurrenceExpansionJobBatchInterval |                                                                                                                                                                               Dies ist die Häufigkeit in Sekunden, nach der der Teilerweiterungsauftrag ausgelöst wird.                                                                                                                                                                                |
|   Organization.RecurrenceExpansionJobBatchSize   |                                                                                                                                                                                  Dies ist die Anzahl der Instanzen, die bei jeder Ausführung des asynchronen Auftrags erweitert werden.                                                                                                                                                                                   |

### <a name="see-also"></a>Siehe auch  
 [Serientermin-Entitäten](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [Erstellen einer Terminserie, Instanz oder Ausnahme](create-recurring-appointment-series-instance-exception.md)   
 [Terminserie oder Terminserieninstanz löschen oder beenden](/dynamics365/customer-engagement/developer/delete-or-end-a-recurring-appointment-series-or-instance)   
 [Einen wiederkehrenden Termin aktualisieren](update-recurring-appointment.md)
