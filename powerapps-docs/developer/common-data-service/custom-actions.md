---
title: Erstellen Sie Ihre eigenen Aktionen (Common Data Service for Apps) | Microsoft Docs
description: 'Aktionen sind angepasste Nachrichten, die halfen, Funktionen von Dynamics 365 Customer Engagement zu erweitern. Erfahren Sie, wie Sie Ihrer eigene geschäftlichen Aktionen erstellen'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-your-own-actions"></a>Erstellen Ihrer eigenen Aktionen

Sie können die Funktionalität von Common Data Service for Apps erweitern, indem Sie benutzerdefinierte Nachrichten, sogenannte *Aktionen*, erstellen. Diese Aktionen verfügen über zugewiesene Antwort-/Anforderungsklassen, und eine Web API-Aktion wird generiert. Aktionen werden in der Regel verwendet, um neue domänenspezifische Funktionen zum Organisationswebdienst hinzuzufügen oder um mehrere Webdienstmeldungsanforderungen einer Organisation zu einer einzelnen Anforderung zu kombinieren. Beispielsweise können Sie in einem Supportcallcenter die Meldungen , Erstellen, Zuweisen und Setstate zur einer einzelnen neuen „Eskalieren“-Meldung kombinieren.  
  
 Die Geschäftslogik einer Aktion wird mithilfe eines Workflows implementiert. Wenn Sie eine Aktion erstellen, wird der zugeordnete Echtzeitworkflow automatisch registriert, um in Phase 30 (Kernvorgang) der Ausführungspipeline ausgeführt zu werden. Weitere Informationen zu Echtzeitworkflows finden Sie unter [Workflowtypen](/dynamics365/customer-engagement/developer/process-categories).  
  
 Während Aktionen in beiden CDS für Apps unterstützt werden, wird die Erstellung einer Aktion im Code (mit XAML) nur von lokalen und IFD-Bereitstellungen unterstützt. Onlinekunden müssen Aktionen interaktiv in der Webanwendung erstellen.  
  
<a name="about_actions"></a>   

## <a name="about-action-definitions"></a>Informationen zu Aktionsdefinitionen  

 Eine Aktion wird mithilfe eines `Workflow`-Entitätsdatensatzes definiert, der ähnlich wie ein Echtzeitworkflow ist. Einige wichtige Punkte dazu, was eine Aktion ist und wie sie funktioniert, sind in der folgenden Liste enthalten:  
  
- Kann einer einzelnen Entität oder global (keiner bestimmten Entität) zugeordnet werden.  
  
- Wird in der Kernvorgangsphase 30 der Ereignisausführungspipeline ausgeführt.  
  
- Unterstützt den Aufruf von Plug-Ins, die in den vorgelagerten und nachgelagerten Vorgangsphasen der Ereignisausführungspipeline registriert werden.  
  
- Kann die Plug-Ins in den vorgelagerten und nachgelagerten Vorgangsphasen nur registrieren, wenn der Aktionsstatus aktiviert ist.  
  
- Ist durch die Internet API oder `organization.svc` und `organization.svc/web`-Endpunkte verfügbar.  
  
- Kann über eine JavaScript-Webressource ausgeführt werden. Weitere Informationen: [Ausführen einer Aktion mit einer JavaScript-Webressource](/dynamics365/customer-engagement/developer/create-own-actions#BKMK_JavaScript)  
  
- Wird immer im Sicherheitskontext des aufrufenden Benutzers ausgeführt.  
  
- Datensatz kann nicht gelöscht werden, während Plug-In-Schritte auf der Aktion registriert sind.  
  
- Kann optional, durch eine Konfigurationseinstellung, an der aktuellen Datenbanktransaktion teilnehmen.  
  
- Unterstützt einen Umfang nicht, in dem die Ausführung auf einen Benutzer, eine Unternehmenseinheit oder eine Organisation begrenzt ist. Aktionen werden immer im Organisationsumfang ausgeführt.  
  
- Unterstützt Ein- und Ausgabeargumente.  
  
- Unterstützt die Überwachung von Datenänderungen.  
  
- Wird nicht mit Offline-Clients unterstützt.  
  
- Kann mit einem Webdienstmethodenaufruf aufgerufen werden.  
  
- Kann direkt in einem Workflow aufgerufen werden.  
  
<a name="bkmk_permissions"></a> 
  
## <a name="required-permissions"></a>Erforderliche Berechtigungen
  
 Ein Sicherheitsrecht mit der Bezeichnung Echtzeitprozesse aktivieren (`prvActivateSynchronousWorkflow`) ist erforderlich, um einen Echtzeitworkflow der Aktion zu aktivieren, damit sie ausgeführt werden kann. Dies wird zusätzlich zu beliebigen Rechten benötigt, um einen Workflow erstellen.  

<!-- Removed much content about creating a custom action using code-->
  
<a name="bkmk_package"></a>   

## <a name="package-an-action-for-distribution"></a>Packen einer Aktion zur Verteilung

 Um Ihre Aktion so zu verteilen, dass sie in eine CDS for Apps-Organisation importiert werden kann, fügen Sie Ihre Aktion einer CDS for Apps-Lösung hinzu. Mit der Webanwendung ist das ganz einfach, indem Sie zu **Einstellungen** > **Anpassungen** > **Lösungen** gehen. Sie können auch Code schreiben, um die Lösung zu erstellen. Weitere Informationen zur Verwendung von Lösungen finden Sie unter [Packen und Verteilen von Erweiterungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).  
  
<a name="bkmk_gentypes"></a>

## <a name="generate-early-bound-types-for-an-action"></a>Generieren von Typen mit früher Bindung für eine Aktion

 Mithilfe des CrmSvcUtil-Tools können Sie Anforderungs- und Antwortklassen für Ihre Aktion generieren, um sie in Ihren Anwendungscode aufzunehmen. Bevor Sie jedoch diese Klassen erstellen, müssen Sie die Aktion aktivieren.  
  
Um das CrmSvcUtil.exe herunterzuladen, siehe [Tools von NuGet herunterladen](download-tools-NuGet.md)
  
 Im folgenden Beispiel wird das Format für die Ausführung von Tools in der Befehlszeile für eine lokale Installation von CDS for Apps gezeigt. Sie stellen die Parameterwerte für die Installation bereit.  
  
```ms-dos  
CrmSvcUtil.exe /url:http://<serverName>/<organizationName>/XRMServices/2011/Organization.svc /out:<outputFilename>.cs /username:<username> /password:<password> /domain:<domainName> /namespace:<outputNamespace> /serviceContextName:<serviceContextName> /generateActions  
```  
  
 Im folgenden Beispiel wird das Format für die Ausführung von Tools in der Befehlszeile mit CDS for Apps gezeigt. Sie stellen die geeigneten Parameterwerte für Ihr Konto und Ihren Server bereit.  
  
```ms-dos  
CrmSvcUtil.exe /url:https://<organizationUrlName>.api.crm.dynamics.com/XRMServices/2011/Organization.svc /out:<outputFilename>.cs /username:<username> /password:<password> /namespace:<outputNamespace> /serviceContextName:<serviceContextName> /generateActions  
```  
  
 Beachten Sie die Verwendung des `/generateActions`-Parameters. Weitere Informationen: [Entitätsklassen mit früher Bindung mit dem Codegenerierungstool erstellen (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool).  
  
 Sie können Typen mit früher oder später Bindung mit den erstellen Anforderungs- und Antwortklassen für die Aktion verwenden.  
  
<a name="bkmk_executeWebAPI"></a>

## <a name="execute-an-action-using-the-web-api"></a>Ausführen einer Aktion mithilfe der Web-API

Eine neue Aktion wird im Web-API erstellt, wenn es erstellt wird. Wenn die Aktion im Kontext einer Entität erstellt wird, wird sie an diese Entität gebunden. Andernfalls ist es eine ungebundene Aktion. Weitere Informationen finden Sie unter [Verwenden von Web-API-Aktionen](/dynamics365/customer-engagement/developer/webapi/use-web-api-actions).  
  
<a name="bkmk_execute"></a>

## <a name="execute-an-action-using-the-organization-service"></a>Ausführen einer Aktion mithilfe des Organisationsservice

Damit Sie eine Aktion unter Verwendung des Organisationswebdiensts mithilfe von verwaltetem Code ausführen können, führen Sie die folgenden Schritte aus.  
  
1. Nehmen Sie die früh gebundene Typendatei auf, die Sie mithilfe des CrmSvcUtil-Tools im Projekt Ihrer Anwendung erstellt haben.  
  
2. Instanziieren Sie in Ihrem Anwendungscode die Aktionsanforderung, und füllen Sie die erforderlichen Eigenschaften aus.  
  
3. Rufen Sie <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> auf, und übergeben Sie die Anforderung als Argument.  
  
   Bevor Sie den Anwendungscode ausführen, stellen Sie sicher, dass die Aktion aktiviert ist. Andernfalls erhalten Sie einen Laufzeitfehler.  
  
<a name="BKMK_JavaScript"></a>   

### <a name="execute-an-action-using-a-javascript-web-resource"></a>Ausführen einer Aktion mithilfe einer JavaScript-Webressource

Eine Aktion kann mithilfe des Web-API genauso wie eine beliebige Systemmaßnahme ausgeführt werden. Weitere Informationen finden Sie unter [Verwenden von Web-API-Aktionen](/dynamics365/customer-enagagement/developer/webapi/use-web-api-actions).  

Die [Sdk.Soap.js](http://code.msdn.microsoft.com/SdkSoapjs-9b51b99a)-Beispielbibliothek zeigt, wie Meldungen mit den JavaScript-Webressourcen und dem Organization Service (organization.svc/web) verwendet werden können. Verwenden Sie das Begleitbeispiel [Sdk.Soap.js Action Message Generator](http://code.msdn.microsoft.com/SdkSoapjs-Action-Message-971be943), um JavaScript-Bibliotheken zu generieren, die mit Sdk.Soap.js verwendet werden können, genau wie Sie die Bibliotheken für Systemmeldungen verwenden können, die in diesem Beispiel bereitgestellt werden. Die mit dem `Sdk.Soap.js` Action Message Generator erzeugten Dateien sind separate JavaScript-Bibliotheken für jede Aktion. Jede Bibliothek enthält eine Anforderungs- und Antwortklasse, die den Klassen entspricht, die von CrmSvcUtil generiert wurden.  
  
<a name="bkmk_execute-process"></a>

## <a name="execute-an-action-using-a-process"></a>Ausführen einer Aktion mithilfe eines Prozesses

Sie können eine Aktion aus Workflows, Dialogen oder anderen Prozessaktionen ausführen. Aktivierte benutzerdefinierte Aktionen sind für Prozesse verfügbar, indem Sie das Element **Aktion durchführen** in der Dropdownliste **Schritt hinzufügen** des Webanwendungsprozessformulars auswählen. Nachdem der Schritt dem Prozess hinzugefügt wurde, können Sie die neue benutzerdefinierte Aktion (oder eine andere Aktion) aus der Liste **Aktion** auswählen, die in dem Schritt bereitgestellt wird. Wählen Sie **Eigenschaften festlegen** in dem Schritt, um Eingabeparameter, die für die benutzerdefinierte Aktionen erforderlich sind, anzugeben.  
  
> [!NOTE]
>  Wenn eine benutzerdefinierte Aktion nicht unterstützte Parametertypen aufweist, z. B. "Auswahlliste", "Entität" oder "Entitätssammlung", wird die benutzerdefinierte Aktion nicht in der Liste **Aktion** aufgeführt.  
  
Die vorhandenen <xref:Microsoft.Xrm.Sdk.IExecutionContext.Depth>-Plattformprüfungen stellen sicher, dass keine Endlosschleife auftritt. Weitere Informationen zu diesen Tiefenlimits finden Sie unter <xref:Microsoft.Xrm.Sdk.Deployment.WorkflowSettings.MaxDepth>.  
  
<a name="bkmk_longrunning"></a>

## <a name="watch-out-for-long-running-actions"></a>Achten auf lang laufende Aktionen

Wenn einer der Schritte im Echtzeitworkflow der Aktion eine benutzerdefinierte Workflowaktivität ist, wird diese benutzerdefinierte Workflowaktivität innerhalb der isolierten Laufzeitumgebung des Sandkastens ausgeführt und unterliegt dem zweiminütigen Timeoutlimit, ähnlich wie Plug-Ins in Sandkästen verwaltet werden. Es gibt allerdings keine Einschränkungen für die Gesamtzeit, die die Aktion selbst benötigen kann. Wenn eine Aktion an einer Transaktion teilnimmt, bei der Rollback aktiviert ist, gelten außerdem SQL Server-Timeouts.  

> [!TIP]
>  Eine bewährte Vorgehensweise ist, dass lang laufende Operationen außerhalb von CDS for Apps mit asynchronen oder Hintergrundprozessen von .NET ausgeführt werden sollten.  
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Echtzeitworkflows](/dynamics365/customer-engagement/developer/create-real-time-workflows)   
 [Verwenden von Dialogen für Kundeninteraktionen](/dynamics365/customer-engagement/developer/use-dialogs-guided-processes)   
 [Ereignisausführungspipeline](event-framework.md#event-execution-pipeline)   
 [Erstellen von Workflows zum Automatisieren von Geschäftsprozessen](/dynamics365/customer-engagement/developer/automate-business-processes-customer-engagement)   
 [Anpassen des Systems](https://technet.microsoft.com/library/dn531158.aspx)
