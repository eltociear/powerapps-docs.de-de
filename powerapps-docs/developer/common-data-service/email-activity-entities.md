---
title: E-Mail-Entitäten (Common Data Service) | Microsoft Docs
description: Mithilfe der E-Mail-Aktivität in Dynamics 365 können Sie die E-Mail-Kommunikation mit Kunden nachverfolgen und verwalten.
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
# <a name="email-activity-entities"></a>E-Mail-Aktivitätsentitäten

Mithilfe der E-Mail-Aktivität können Sie die E-Mail-Kommunikation mit Kunden nachverfolgen und verwalten. Common Data Service enthält die E-Mail-Router-Software, die die Weiterleitung von E-Mails zu oder von Common Data Service verwaltet. Die E-Mail-Aktivität, die unter Verwendung von E-Mail-Protokollen übermittelt wird. E-Mail-Router unterstützt die folgenden E-Mail-Protokolle: Exchange-Webdienste, POP3 und SMTP. Zusätzlich zur E-Mail-Router-Software kann die E-Mail-Aktivität auch mithilfe von Dynamics 365 for Outlook. übermittelt werden.  
  
<a name="Actions"></a>   

## <a name="actions-on-an-email-activity"></a>Aktionen für eine E-Mail-Aktivität  
 Mithilfe der Dynamics 365 Customer Engagement-Webdienste können Sie folgende Aktionen für eine E-Mail Aktivität ausführen.  
  
- Erstellen, Abrufen, Aktualisieren und Löschen der E-Mail-Aktivität.  
  
- Senden von E-Mail-Nachrichten, oder Senden von E-Mail-Nachrichten mithilfe von E-Mail-Vorlagen (`Template`). Weitere Informationen zu E-Mail-Vorlagen finden Sie unter [Vorlagen-Entität](/reference/entities/template.md).  
  
- Anfügen von Dateien als Anlagen mithilfe des (`ActivityMimeAttachment`) Attributs in der E-Mail-Nachricht.  
  
- Senden von Massen-E-Mail-Nachrichten.  
  
- Konfigurieren von eingehenden E-Mail-Nachrichten, sodass sie vom Microsoft Exchange Server  an einen Benutzer oder die Warteschlange übermittelt werden, oder ausgehende Nachrichten von einem beliebigen Benutzer oder einer Warteschlange an Microsoft Exchange Server. gesendet werden können. Informationen dazu, wie eingehende E-Mails für Warteschlangen konfiguriert werden, siehe [Konfigurieren der E-Mail für eingehende Nachrichten](/dynamics365/customer-engagement/developer/configure-email-incoming-messages).  
  
   Wenn die Organisationsattribute `Organization.RequireApprovalForuserEmail` und `Organization.RequireApprovalForQueueEmail` (E-Mails nur für genehmigte Benutzer/Warteschlangen verarbeiten) auf **true** (1) festgelegt werden, tritt Folgendes auf: E-Mail-Nachrichten werden von einem Benutzer oder einer Warteschlange nur dann übermittelt oder gesendet, wenn die primäre E-Mail-Adresse des Benutzers oder der Warteschlange genehmigt wurde. Die Attribute `SystemUser.EmailRouterAccessApproval` und `Queue.EmailRouterAccessApproval` geben den Status der primären E-Mail-Adresse des Benutzers bzw. der Warteschlange an, und der Wert muss auf 1 festgelegt werden. Andernfalls werden die eingehenden und ausgehenden Nachrichten blockiert. Sie können den Benutzer- oder Warteschlangendatensatz aktualisieren, um den Attributwert zu ändern, falls er noch nicht genehmigt wurde, vorausgesetzt Ihr Benutzerkonto verfügt über die Berechtigung **prvApproveRejectEmailAddress**.
  
> [!NOTE]
>  Im Common Data Service kann das `Email.StatusCode`-Attribut nicht **NULL** sein.  
  
<a name="BulkE-Mail"></a>   

## <a name="bulk-email"></a>Massen-E-Mail  
 Common Data Service unterstützt das Senden von E-Mails an eine Vielzahl von Empfängern durch eine Massen-E-Mail-Anforderung. Wenn eine Massen-E-Mail-Anforderung an Common Data Service gesendet wird, wird in der Warteschlange "Asynchroner Dienst", welche die E-Mail-Messages mithilfe eines Hintergrundprozesses sendet, ein asynchroner Vorgang erstellt. Dadurch wird eine verbesserte Systemleistung erreicht.  
  
 Die Meldungen <xref:Microsoft.Crm.Sdk.Messages.SendBulkMailRequest> und <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> werden für das Senden von Massen-E-Mail-Nachrichten verwendet. Im Folgenden wird die Sequenz zum Senden von Massen-E-Mails aufgeführt:  
  
1. Führen Sie `SendBulkMail`-Anforderung aus. Diese Anforderung enthält eine Abfrage, die die Ziel-E-Mail-Empfänger und eine E-Mail-Vorlage zum Verfassen jeder E-Mail auswählt.  
  
2. Der asynchrone Dienst erstellt die E-Mail-Aktivitäten für jeden Empfänger.  
  
3. Der asynchrone Dienst versendet jede E-Mail-Nachricht. Die E-Mail-Nachrichten haben den Sendestatus "Ausstehend".  
  
4. Der E-Mail-Router, Dynamics 365 for Outlook oder eine Drittanbieterkomponente zum Senden von E-Mails fragt Common Data Service nach ausstehenden E-Mail-Messages ab, und wenn eine gefunden wird, lädt sie mithilfe der `BackgroundSendEmail`-Anforderung herunter.  
  
5. Die `BackgroundSendEmail`-Anforderung führt die folgenden Vorgänge aus: Überprüft, ob ausstehende E-Mailnachrichten vorhanden sind, lädt die E-Mail an den Aufrufer der Meldung <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> herunter und synchronisiert die Downloads, wenn mehrere Aufrufer vorhanden sind.  
  
6. Der Aufrufer der Meldung <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> empfängt die heruntergeladene E-Mail-Nachricht und versendet und sie.  
  
<a name="E-MailAttachments"></a>   
## <a name="email-attachments"></a>E-Mail-Anlagen  
 E-Mail-Anlagen sind Dateien, die an E-Mail-Nachrichten oder E-Mail-Vorlagen angefügt werden können. Eine angefügte Datei kann jedes beliebige Standardcomputerdateiformat haben, wie beispielsweise Office Outlook-Dokumente, Office Excel-Arbeitsblätter, CAD-Dateien und PDF-Dateien. Sie können mehrere Dateien als E-Mail-Anlagen an eine E-Mail oder eine E-Mail-Vorlage anfügen. Die maximale Größe für Dateien, die hochgeladen werden können, wird durch die **Organization.MaxUploadFileSize**-Eigenschaft bestimmt. Diese Eigenschaft wird in der Dynamics 365-Anwendung auf der Registerkarte **E-Mail** in den **Systemeinstellungen** festgelegt. Mit dieser Einstellung wird die Größe von Dateien begrenzt, die an E-Mail-Nachrichten, Notizen und Webressourcen angefügt werden können. Die Standardeinstellung ist 5 MB. 
  
 Zum Anfügen einer E-Mail-Anlage an eine E-Mail-Nachricht oder -Vorlage verwenden Sie die Attribute `ActivityMimeAttachment.ObjectId` und `ActivityMimeAttachment.ObjectTypeCode`, während Sie einen Aktivitäts-MIME-Anlagendatensatz erstellen oder aktualisieren.  
  
 Das folgende Codebeispiel zeigt, wie eine E-Mail-Anlage an eine E-Mail angefügt wird:  
  
```csharp  
ActivityMimeAttachment _sampleAttachment = new ActivityMimeAttachment{  
    ObjectId = new EntityReference(Email.EntityLogicalName, _emailId),  
    ObjectTypeCode = Email.EntityLogicalName,  
    Subject = "Sample Attachment”,  
    Body = System.Convert.ToBase64String(new ASCIIEncoding().GetBytes("Example Attachment")),  
    FileName = "ExampleAttachment.txt"};  
```  
  
 Um die E-Mail-Anlage an eine Vorlage anstatt an eine E-Mail anzufügen, ersetzen Sie die Werte der Attribute `ActivityMimeAttachment.ObjectId` und `ActivityMimeAttachment.ObjectTypeCode` wie folgt im obigen Code:  
  
```csharp  
ObjectId = new EntityReference(Template.EntityLogicalName, _templateId), ObjectTypeCode = Template.EntityLogicalName,  
```  
  
 Ein vollständiges Codebeispiel, inwieweit von E-Mail-Anlagen erstellt werden, finden Sie unter [Beispiel: Erstellen, Abrufen, Aktualisieren und Löschen eines E-Mail-Anhangs](/dynamics365/customer-engagement/developer/sample-create-retrieve-update-delete-email-attachment).  
  
### <a name="reusing-email-attachments"></a>Wiederverwenden von E-Mail-Anlagen  
 Wenn Sie einen E-Mail-Anlagendatensatz erstellen, wird die angehängte Datei als BLOB-Datei gespeichert. Das Attribut `ActivityMimeAttachment.AttachmentId` des E-Mail-Anlagendatensatzes kennzeichnet eindeutig die BLOB-Datei. Dies erleichtert die erneute Verwendung der Dateianlagen mit anderen E-Mail- und E-Mail-Vorlagendatensätzen, ohne dass mehrere Kopien derselben Datei in der Datenbank erstellt und gespeichert werden müssen.  
  
 So verwenden Sie eine vorhandene Dateianlage erneut:  
  
1.  Rufen Sie den `ActivityMimeAttachment`-Datensatz ab, der die Anlagendatei enthält, die Sie erneut verwenden möchten, wie im folgenden Codebeispiel gezeigt:  
  
    ```csharp  
    ActivityMimeAttachment retrievedAttachment = (ActivityMimeAttachment)_serviceProxy.Retrieve(ActivityMimeAttachment.EntityLogicalName, _emailAttachmentId, new ColumnSet(true));  
    ```  
  
2.  Erstellen Sie einen neuen E-Mail-Anlagendatensatz, ordnen Sie ihn dem erforderlichen E-Mail- oder E-Mail-Vorlagendatensatz zu und verweisen Sie ihn auf die Datei des abgerufenen `ActivityMimeAttachment`-Datensatzes, wie im folgenden Codebeispiel gezeigt:  
  
    ```csharp  
    ActivityMimeAttachment _reuseAttachment = new ActivityMimeAttachment{  
        ObjectId = new EntityReference(Email.EntityLogicalName, _emailId),  
        ObjectTypeCode = Email.EntityLogicalName,  
        Subject = "Sample Attachment”,  
        AttachmentId = retrievedAttachment.AttachmentId};  
    ```  
  
     Da Sie eine bestehende Anlagendatei wiederverwenden, müssen Sie die Attributwerte `ActivityMimeAttachment.Body` und `ActivityMimeAttachment.FileName` nicht festlegen, während Sie E-Mail-Anlagendatensätze zu E-Mail-Nachrichten oder E-Mail-Vorlagen erstellen und zuordnen.  
  
### <a name="see-also"></a>Siehe auch  
 [Aktivitätsentitäten](activity-entities.md)   
 [Beispielcode für Aktivitätsentitäten](/dynamics365/customer-engagement/developer/sample-code-activity-entities)   
 [E-Mail-Entität](/reference/entities/email.md)   
 [ActivityMimeAttachment-Entität](/reference/entities/activitymimeattachment.md)
