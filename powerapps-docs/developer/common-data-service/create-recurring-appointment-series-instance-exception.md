---
title: Erstellen einer Terminserie, Instanz oder Ausnahme (Common Data Service) | Microsoft-Dokumentation
description: Erstellen Sie programmgesteuert einen Serienterminmaster (Serie), einzelne Serientermininstanzen, Ausnahmen zu diesen Instanzen, oder konvertieren Sie einen Termin in einen Serientermin.
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
ms.openlocfilehash: 57778f4520a305061c8f598ad82e033a89565033
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748569"
---
# <a name="create-a-recurring-appointment-series-instance-or-exception"></a>Erstellen einer Terminserie, Instanz oder Ausnahme

Wenn Sie einen Terminserienmaster (Serie) erstellen, erstellt Common Data Service einzelne Termininstanzen basierend auf den angegebenen Wiederholungsinformationen. Sie können auch einzelne Serientermininstanzen und Ausnahmen für diese Instanzen erstellen, und Sie können einen Termin zu einem Serientermin konvertieren.  
  
<a name="bkmk_createseries"></a>   

## <a name="create-a-recurring-appointment-series"></a>Erstellen einer Terminserie  

 Um eine Terminserie zu erstellen (ein `RecurringAppointmentMaster`-Datensatz), können Sie die <xref:Microsoft.Crm.Sdk.Messages.BookRequest>-Meldung, die <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Meldung oder die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>-Methode verwenden. Methode.  
  
 Beim Erstellen einer Terminserie passiert Folgendes:  
  
1. Ein `RecurringAppointmentMaster`-Datensatz (Terminserie) wird erstellt, der grundlegende Informationen und Wiederholungsinformationen zur Terminserie enthält. Jeder Datensatz kann mit der Eigenschaft `RecurringAppointmentMaster.ActivityId` eindeutig identifiziert werden. Außerdem wird diese Terminserie auch als Aktivitätsdatensatz (`ActivityPointer`) erstellt und gespeichert. Der Aktivitätsdatensatz kann mit der Eigenschaft `ActivityPointer.ActivityId` eindeutig identifiziert werden.  
  
2. Einzelne Serientermininstanzen werden basierend auf den Wiederholungsinformationen erstellt und als `Appointment`-Datensätze gespeichert. Diese Terminobjekte werden der übergeordneten Terminserie mithilfe der Eigenschaft `Appointment.SeriesId` zugeordnet und haben denselben Wert wie die ID der übergeordneten Terminserie (`ActivityPointer.SeriesId`).  
  
    Der Wert der `Appointment.InstanceTypeCode`-Eigenschaft wird für diese Terminobjekte auf **Wiederkehrende Instanz** (Auswahllistenwert 2) festgelegt.  
  
   > [!NOTE]
   >  Terminserieninstanzen werden basierend auf dem Erweiterungsmodell und der Parameter erstellt, die es definieren. Weitere Informationen: [Teilerweiterungsmodell für Serientermine](recurring-appointment-partial-expansion-model.md).  
  
   Für Beispielcode, der zeigt, wie ein Serientermin erstellt wird, siehe [Beispiel: Erstellen Sie einen Serientermin](/dynamics365/customer-engagement/developer/sample-create-retrieve-update-delete-recurring-appointment).  
  
<a name="bkmk_createinstance"></a>   

## <a name="create-a-recurring-appointment-instance"></a>Erstellen einer Terminserieninstanz  
 Um eine Terminserieninstanz (ein `RecurringAppointmentMaster`-Datensatz) zu erstellen, können Sie <xref:Microsoft.Crm.Sdk.Messages.CreateInstanceRequest> verwenden. Diese Meldung verwendet zwei Parameter: die Anzahl der zu erstellenden Instanzen und die Terminserie, für die die Instanzen erstellt werden müssen.  
  
 Die Instanzen werden in der Terminserie nach der letzten Instanz erstellt. Die Instanzen werden nur bis zum zukünftigen Instanzen-Schlussdatum erstellt, unabhängig von der Anzahl der Instanzen, die Sie für die Erstellung angegeben haben.  
  
<a name="bkmk_createexception"></a>   

## <a name="create-a-recurring-appointment-exception"></a>Erstellen einer Terminserienausnahme  
 Eine Ausnahme wird erstellt, wenn Sie entweder eine Instanz der Terminserie aktualisieren oder löschen. Terminserieninstanzen werden wie andere Termine als Termindatensatz gespeichert, und Sie können eine Terminserieninstanz mithilfe des `Appointment.InstanceTypeCode`-Attributs eines Termindatensatzes angegeben, das den Wert **Wiederkehrende Instanz** (Auswahllistenwert 2) besitzt.  
  
 Sie können Ausnahmen wie folgt erstellen:  
  
-   Verwenden Sie die <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>-Klasse in der `Appointment`-Entität, um eine Terminserieninstanz zu aktualisieren, und legen Sie den Wert des Attributs `Appointment.InstanceTypeCode` auf **Wiederkehrende Ausnahme** (Auswahllistenwert 3) fest.  
  
-   Verwenden Sie die <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest>-Klasse in der `Appointment`-Entität, um eine Terminserieninstanz zu löschen. Eine gelöschte Terminserieninstanz wird als Ausnahme gekennzeichnet, indem für das übergeordnete Terminserienobjekt im `RecurringAppointmentMaster.DeletedExceptionsList`-Attribut ein Eintrag für die Instanz erstellt wird.  
  
-   Verwenden Sie die <xref:Microsoft.Crm.Sdk.Messages.CreateExceptionRequest>-Klasse in der `Appointment`-Entität.  
  
<a name="bkmk_convert"></a>   

## <a name="convert-an-appointment-to-a-recurring-appointment"></a>Konvertieren eines Termins in eine Terminserie  
 Eine Terminserie ist ein Termin mit Wiederholungsinformationen. Sie können in Common Data Service einen vorhandenen Termin in eine Terminserie konvertieren, indem Sie <xref:Microsoft.Crm.Sdk.Messages.AddRecurrenceRequest> verwenden. Wenn Sie einen vorhandenen Termin in eine Terminserie konvertieren, werden die Daten von dem vorhandenen Termin in eine neue Terminserienmasterinstanz kopiert und der vorhandene Termin wird gelöscht.  
  
### <a name="see-also"></a>Siehe auch  
 [Serientermin-Entitäten](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [Einen wiederkehrenden Termin aktualisieren](update-recurring-appointment.md)   
 [Beispiel: Erstellen einer Terminserie](/dynamics365/customer-engagement/developer/sample-create-retrieve-update-delete-recurring-appointment)   
 [Beispiel: Konvertieren eines Termins in eine Terminserie](/dynamics365/customer-engagement/developer/sample-convert-appointment-recurring-appointment)
