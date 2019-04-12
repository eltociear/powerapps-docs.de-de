---
title: Anmerkungs- (Notiz)-Entität (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie über die Anmerkungsentität, um einem Datensatz in der Datenbank zusätzliche Informationen anzufügen. Die Anmerkungsentität stellt eine Anmerkung dar und enthält den Anmerkungstext mit Daten darüber, wer die Anmerkung erstellt und geändert hat, und ob eine Anmerkung zur Datei angefügt ist.'
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
# <a name="annotation-note-entity"></a>Die Entität Anmerkung (Hinweis)

Die *Anmerkungen (Notizen)* bieten einfache Möglichkeiten, einem Datensatz in der Common Data Service-Datenbank zusätzliche Informationen anzufügen. Eine Anmerkung (Notiz) ist eine Texteingabe, die jeder beliebigen Entität in Common Data Service zugeordnet werden kann. Sie können Anmerkungen jedoch nur den benutzerdefinierten Entitäten zuordnen, die mit der <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasNotes>-Eigenschaft, für die `true` in der Klasse <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest> festgelegt ist, erstellt werden. Sie können eine benutzerdefinierte Entität, die nicht für Anmerkungen aktiviert ist, so aktualisieren, dass ihr Anmerkungen zugeordnet werden können, indem Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> auf <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasNotes> festlegen. `true` Eigenschaft.  

Mithilfe der Web-API legen Sie die Eigenschaft `HasNotes` von EntityType <xref:Microsoft.Dynamics.CRM.EntityMetadata>, der diese kontrolliert, fest.
  
 Die Entität `Annotation` stellt eine Anmerkung (Notiz) dar und umfasst die folgenden Informationen:  
  
-   Anmerkungstext (Notizentext)  
  
-   Wer die Anmerkung (Notiz) erstellt und geändert hat  
  
-   Ob der Anmerkung (Notiz) eine Datei angefügt wird  
  
 Eine angefügte Datei kann jedes beliebige Standardcomputerdateiformat haben, wie beispielsweise Office Word-Dokumente, Office Excel-Arbeitsblätter, CAD-Dateien und PDF-Dateien. Eine Anlage kann jedem beliebigen Objekt außer einer Anmerkung (Notiz) in Common Data Service zugeordnet werden.  
  
 Um eine Anlage hochzuladen oder zu entfernen, verwenden Sie <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>. <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>-Methode oder -Nachricht, Festlegen von `Annotation.Filename` und `Annotation.MimeType`-Eigenschaften. Dadurch wird eine in ein Base64-Zeichenfolgenformat decodierte Anlage hochgeladen. Die Methode [System.Convert.ToBase64String](https://msdn.microsoft.com/library/system.convert.tobase64string.aspx) kann verwendet werden, um den Inhalt einer Datendatei in eine Base64-formatierte Zeichenfolge zu konvertieren. Die maximale Größe für Dateien, die hochgeladen werden können, wird durch die **Organization.MaxUploadFileSize**-Eigenschaft bestimmt. Diese Eigenschaft wird in der Dynamics 365-Anwendung auf der Registerkarte **E-Mail** in den **Systemeinstellungen** festgelegt. Mit dieser Einstellung wird die Größe von Dateien begrenzt, die an E-Mail-Nachrichten, Notizen und Webressourcen angefügt werden können. Die Standardeinstellung ist 5 MB.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Beispiel: Hochladen, Abrufen und Herunterladen einer Anlage](/dynamics365/customer-engagement/developer/sample-upload-retrieve-download-attachment)  
  
### <a name="see-also"></a>Siehe auch 
 [Anmerkungsentität](reference/entities/annotation.md)   
 [Modellieren Sie Ihre Geschäftsdaten](/dynamics365/customer-engagement/developer/model-business-data)   
 [UserQuery (gespeicherte Ansicht)-Entität](/dynamics365/customer-engagement/developer/userquery-saved-view-entity)