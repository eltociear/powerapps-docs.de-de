---
title: Einen wiederkehrenden Termin aktualisieren (Common Data Service) | Microsoft-Dokumentation
description: Aktualisieren Sie wiederkehrende Terminsehrie mit der IOrganizationService.Entity-Methode oder der UpdateRequest-Nachricht für die RecurringAppointmentMaster-Entität.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 3332258f41aaab4f0222bfc3f46cd795a27cf0ea
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155218"
---
# <a name="update-a-recurring-appointment"></a>Einen wiederkehrenden Termin aktualisieren

Sie können entweder die ganze Reihe aktualisieren oder eine Instanz eines wiederkehrenden Termins aktualisieren.  
  
## <a name="update-a-recurring-appointment-series"></a>Eine Terminserie aktualisieren  
 Sie können einen Serientermin aktualisieren, indem Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService>,<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>- Methode bzw. die <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>-Message für die `RecurringAppointmentMaster`-Entität verwenden. Sie können die *standardmäßigen* Information oder die Information zur *Wiederholung* aktualisieren.  
  
### <a name="update-basic-information"></a>Standardinformationen aktualisieren  
 Wenn Sie die standardmäßigen Informationen einer Terminserie aktualisieren, wie beispielsweise Thema, Ort oder Teilnehmer, werden alle Instanzen in der Reihe wiederkehrender Termine aktualisiert, mit Ausnahme von denen, die Ausnahmen beim selben Attribut haben.  
  
### <a name="update-recurrence-information"></a>Aktualisieren von Wiederholungsinformationen  
 Wenn Sie die wiederkehrenden Informationen einer Terminserie aktualisieren, wie beispielsweise das Muster und der Bereich, ereignet sich Folgendes:  
  
1. Eine neue Reihe mit einer neuen `RecurringAppointmentMaster.ActivityId` wird erstellt, die die gleichen Informationen wie die ursprüngliche Reihe hat, und das Datum im Attribut `RecurringAppointmentMaster.EffectiveEndDate` der neuen Reihe wird auf die zuletzt auftretende vergangene Instanz der ursprünglichen Reihe festgelegt. Alle zukünftigen Instanzen der ursprünglichen Reihe werden gelöscht. Auf diese Weise wird die ursprüngliche Reihe beendet, und der Verlauf der vergangenen Instanzen wird im System erhalten, indem er in einer neuen Reihe gespeichert wird.  
  
2. Die neuen Informationen werden verwendet, um die zukünftigen Instanzen der neuen Reihe ab dem tatsächlichen Startdatum `RecurringAppointmentMaster.EffectiveStartDate`() zu erstellen.  
  
   Außerdem wird das Attribut `RecurringAppointmentMaster.GroupId` sowohl für die ursprüngliche als auch die neue Reihe mit demselben Wert aufgefüllt. Dies bedeutet, dass wenn Sie die Wiederholungsinformationen in einer Terminserie aktualisieren, alle neue Reihen, die erstellt werden, denselben Wert für das Attribut `RecurringAppointmentMaster.GroupId` haben, wie der wiederkehrende Termin, der aktualisiert wird, obwohl jede Reihe eine eindeutige Reihen-ID hat.  
  
> [!NOTE]
>  Wenn Sie die Wiederholungsinformationen einer Terminserie aktualisieren, bei der geplant ist, dass alle Instanzen in der Zukunft ausgeführt werden, werden alle Instanzen gelöscht und neue Wiederholungsinformationen verwendet, um neue Instanzen zu erstellen oder zu erweitern.  
  
 Für Beispielcode, der zeigt, wie eine wiederkehrende Terminserie aktualisiert wird, siehe [Beispiel: Aktualisieren eines wiederkehrenden Termins](org-service/samples/reschedule-cancel-recurring-appointment.md).  
  
## <a name="update-a-recurring-appointment-instance"></a>Eine wiederkehrenden Termininstanz aktualisieren  
 Da die Serientermindatensätze als Terminobjekte gespeichert werden, können Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>.<xref:Microsoft.Xrm.Sdk.IOrganizationService>- Methode für die `Appointment`-Entität verwenden, um eine Serienterminserieninstanz zu aktualisieren. Wenn Sie eine Terminserieninstanz aktualisieren, wird die Instanz als Ausnahme der Terminserie markiert. Weitere Informationen: [Erstellen einer Ausnahme eines wiederkehrenden Termins](create-recurring-appointment-series-instance-exception.md#bkmk_createexception)  
  
 Sie können auch die Klasse <xref:Microsoft.Crm.Sdk.Messages.CreateExceptionRequest> für die Entität `Appointment` verwenden, um eine Instanz wiederholender Termine zu aktualisieren.  
  
> [!TIP]
>  Terminserieninstanzen können mithilfe des vierstelligen `Appointment.InstanceTypeCode` identifiziert werden, in dem der Wert "2 " enthält aber auch periodische Instanz (). Weitere Informationen: [Terminentität](reference/entities/appointment.md)  
  
### <a name="see-also"></a>Siehe auch  
 [Serientermin-Entitäten](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [Terminserie oder Terminserieninstanz löschen oder beenden](/dynamics365/customer-engagement/developer/delete-or-end-a-recurring-appointment-series-or-instance)   
 [Beispiel: Einen wiederkehrenden Termin erstellen, abbrufen, aktualisieren und löschen (CRUD)](org-service/samples/create-retrieve-update-delete-recurring-appointment.md)   
 [Beispiel: Erneutes Planen und Stornieren eines Serientermins](org-service/samples/reschedule-cancel-recurring-appointment.md)
