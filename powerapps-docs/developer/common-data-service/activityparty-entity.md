---
title: ActivityParty-Entität (Common Data Service) | Microsoft Docs
description: 'Eine Aktivitätspartei stellt eine Person oder Gruppe dar, die einer Aktivität zugeordnet ist. Eine Aktivität kann mehrere Aktivitätsparteien haben.'
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
# <a name="activityparty-entity"></a>ActivityParty-Entität

Eine Aktivitätspartei stellt eine Person oder Gruppe dar, die einer Aktivität zugeordnet ist. Eine Aktivität kann mehrere Aktivitätsparteien haben.  
  
<a name="ActivityPartyTypes"></a>   

## <a name="activity-party-types"></a>Aktivitätsparteitypen  

 Es stehen 11 Aktivitätsparteitypen in Common Data Service zur Verfügung. Der Aktivitätsparteityp ist als ganzzahliger Wert im `ActivityParty.ParticipationTypeMask`-Attribut gespeichert. In der folgenden Tabelle sind die verschiedenen Aktivitätsparteitypen, der entsprechende ganzzahlige Wert für das `ActivityParty.ParticipationTypeMask`-Attribut und die Beschreibung aufgeführt.  
  
|Aktivitätsparteityp|Value|Beschreibung|  
|-------------------------|-----------|-----------------|  
|Absender|1|Gibt den Absender an.|  
|ToRecipient|2|Gibt den Empfänger im Feld "An" an.|  
|CCRecipient|3|Gibt den Empfänger im Feld "Cc" an.|  
|BccRecipient|4|Gibt den Empfänger im Feld "Bcc" an.|  
|RequiredAttendee|5|Gibt einen erforderlichen Teilnehmer an.|  
|OptionalAttendee|6|Gibt einen optionalen Teilnehmer an.|  
|Planung|7|Gibt den Aktivitätsorganisator an.|  
|Bezug|8|Gibt das entsprechende Element an.|  
|Eigentümer|9|Gibt den Aktivitätsbesitzer an.|  
|Ressource|10|Gibt eine Ressource an.|  
|Kundin/Kunde|11|Gibt einen Kunden an.|  
  
<a name="SupportedActivityPartyTypes"></a>   
## <a name="activity-party-types-available-for-each-activity"></a>Aktivitätsparteitypen, die für jede Aktivität verfügbar sind  
 Nicht alle Aktivitätsparteitypen sind für jede Aktivität in Common Data Service verfügbar, mit Ausnahme einer benutzerdefinierten Aktivität. Eine benutzerdefinierte Aktivität unterstützt alle Aktivitätsparteitypen. Sie können einen Aktivitätsparteityp einer Aktivität zuordnen, indem Sie das jeweilige Attribut einer Aktivität verwenden. Möchten Sie also beispielsweise einen `Organizer`-Aktivitätsparteityp einer Terminaktivität zuordnen, müssen Sie einen Wert oder ein Wertarray des `ActivityParty`-Typs im `Appointment.Organizer`-Attribut angeben.  
  
 Um zu steuern, welche E-Mail-Adresse für das Senden von E-Mails an die Aktivitätspartei oder zum Antworten auf E-Mails von der Aktivitätspartei verwendet werden soll, legen Sie das `ActivityParty.AddressUsed`-Attribut-fest.  
  
 Die folgende Tabelle enthält die Aktivitätsparteitypen, die für jede Aktivität unterstützt werden, und die entsprechenden Aktivitätseigenschaften, um diese Aktivitätsparteitypen anzugeben.  
  
|Name der Aktivitätsentität|Unterstützter Aktivitätsparteityp|Aktivitätsattribut|  
|--------------------------|-----------------------------------|------------------------|  
|Termin|OptionalAttendee<br />Planung<br />RequiredAttendee|Appointment.OptionalAttendees<br />Appointment.Organizer<br />Appointment.RequiredAttendees|  
|CampaignActivity|Absender|CampaignActivity.Partners<br />CampaignActivity.From|  
|CampaignResponse|Kundin/Kunde|CampaignResponse.Customer<br />CampaignResponse.Partner<br />CampaignResponse.From|  
|Per E-Mail senden|BccRecipient<br />CcRecipient<br />Absender<br />ToRecipient|Email.Bcc<br />Email.Cc<br />Email.From<br />Email.To|  
|Faxnummer|Absender<br />ToRecipient|Fax.From<br />Fax.To|  
|Brief|BccRecipient<br />Absender<br />ToRecipient|Letter.Bcc<br />Letter.From<br />Letter.To|  
|PhoneCall|Absender<br />ToRecipient|PhoneCall.From<br />PhoneCall.To|  
|RecurringAppointmentMaster|OptionalAttendee<br />Planung<br />RequiredAttendee|RecurringAppointmentMaster.OptionalAttendees<br />RecurringAppointmentMaster.Organizer<br />RecurringAppointmentMaster.RequiredAttendees|  
|ServiceAppointment|Kundin/Kunde<br />Ressource|ServiceAppointment.Customers<br />ServiceAppointment.Resources|  
  
### <a name="see-also"></a>Siehe auch  
 [Aktivitätsentitäten](activity-entities.md)   
 [Aktivitätsentitäten wie Aufgabe, Fax, Telefonanruf und Brief](task-fax-phone-call-letter-activity-entities.md)   
 [ActivityParty-Entität](reference/entities/activityparty.md)   
 [Beispiel: Buchen eines Termins](/dynamics365/customer-engagement/developer/sample-book-appointment)<br>
 [Beispiel: Konvertieren eines Faxes für eine Aufgabe](/dynamics365/customer-engagement/developer/sample-convert-fax-task)   
 [Beispiel: Überschreiben einer Zielgesamtanzahl und Schließen des Ziels](/dynamics365/customer-engagement/developer/sample-override-goal-total-count-close-goal)   
 [Beispiel: Rollup für Zieldaten für eine Buchhaltungsperiode für die Streckungszielanzahl](/dynamics365/customer-engagement/developer/sample-rollup-goal-data-fiscal-period-stretch-target-count)   
 [Beispiel: Senden einer E-Mail mithilfe einer Vorlage](/dynamics365/customer-engagement/developer/sample-send-email-template)   
 [Beispiel: Prüfen eines Termins](/dynamics365/customer-engagement/developer/sample-validate-appointment)
