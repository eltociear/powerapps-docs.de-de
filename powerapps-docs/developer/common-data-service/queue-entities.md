---
title: Warteschlangenentitäten (Common Data Service) | Microsoft-Dokumentation
description: Warteschlangen in PowerApps sind wichtig, um den Fortschritt Ihrer Arbeit organisieren, priorisieren und überwachen zu können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6452dd50cb54e1c7c3aa5a57b9d7751ba9f13af7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748661"
---
# <a name="queue-entities"></a>Warteschlangenentitäten

Mithilfe von *Warteschlangen* können Sie den Fortschritt Ihrer Arbeit organisieren, priorisieren und überwachen. Als zentraler Ort für die Arbeitsverwaltung unterstützen Warteschlangen Sie dabei, Anfragen zu bearbeiten, Serviceanrufe zu beantworten oder Produktinformationen an zukünftige Kunden zu senden. Eine Warteschlange ist eine programmgesteuerte Sammlung von Warteschlangenelementen. Ein Warteschlangenelement dient als Container für einen Datensatz, wie eine Aufgabe, eine E-Mail oder eine Anfrage, die bearbeitet werden muss. Siehe [Warteschlangenentität](reference/entities/queue.md)

> [!NOTE]
> Informationen zum Arbeiten mit Warteschlangen mit der Benutzeroberfläche finden Sie unter [Übersicht zu Warteschlangen](/dynamics365/customer-engagement/customer-service/set-up-queues-manage-activities-cases).  
  
Für Warteschlangen gelten die folgenden Informationen:  
  
-   Alle anpassbaren Entitäten können für eine Warteschlangen aktiviert werden.  
  
-   Warteschlangen können öffentlich oder privat sein. Elemente der privaten Warteschlange können nur von Mitgliedern der Warteschlage angezeigt werden.  
  
-   Eine private Warteschlange wird automatisch für alle neuen Benutzer oder Teams erstellt.  
  
-   Eine Warteschlange kann mehrere Entitätstypen, wie Aufgaben, E-Mail-Nachrichten oder Anfragen, enthalten.  
  
-   Eine Warteschlange enthält Informationen über den Benutzer, der mit einem bestimmten Warteschlangenelement arbeitet. Dies hilft Ihnen dabei, Ressourcen effizienter zu verwalten und Überlappung bei der Arbeit zu vermeiden.  
  
-   Warteschlangen können für Workflows und die Überwachung aktiviert werden. Dies trägt zur Verbesserung der Produktivität bei und hilft beim Nachverfolgen der Entitäts- und Attributdatenänderungen für zukünftige Analyse- und Berichterstellungszwecke.  
  
<a name="BKMK_MemberCapabilities"></a>   
## <a name="members-capabilities"></a>Mitgliederfunktionen  
 Warteschlangen werden in *öffentliche* oder *private* Warteschlange unterteilt. Private Warteschlangen haben einzelne Benutzer als Mitglieder, um die Steuerung des Zugriffs auf Warteschlangen zu vereinfachen. Wenn Sie ein Team zu einer privaten Warteschlange hinzufügen, werden alle Mitglieder dieses Teams zu Mitgliedern der privaten Warteschlange.  
  
<a name="BKMK_publicAndPrivateQueues"></a>   
## <a name="public-and-private-queues"></a>Öffentliche und private Warteschlangen  
 Das neue [QueueViewType](reference/entities/queue.md#BKMK_QueueViewType)-Attribut ist eine Auswahlliste, die definiert, ob eine Warteschlange öffentlich oder privat ist.  
  
-   Alle Benutzerwarteschlangen sind private Warteschlangen für den Benutzer: Nur der Benutzer kann die Warteschlangenelemente in der privaten Warteschlange anzeigen.  
  
-   Teamwarteschlangen sind als private Warteschlange mit Mitgliedern gekennzeichnet: Der Besitzer des Teams und alle Teammitglieder können die Warteschlange in der Anwendung anzeigen.  
  
-   Alle anderen Warteschlangen sind öffentlich. Jeder Benutzer mit Leserechten für die Warteschlangenentität kann diese Warteschlangen anzeigen.  
  
<a name="BKMK_QueueAttributes"></a>   
## <a name="attributes-used-to-manage-queues"></a>Attribute zum Verwalten von Warteschlangen  
 Verwenden Sie die folgenden Attribute, um Warteschlangen zu verwalten.  
  
|SchemaName|DisplayName|Typ|Beschreibung|  
|----------------|-----------------|----------|-----------------|  
|NumberOfItems|Warteschlangenelemente|Ganze Zahl|Gibt die Anzahl von Warteschlangenelementen an, die der Warteschlange zugeordnet sind.|  
|NumberOfMembers|Nr. von Mitgliedern|Ganze Zahl|Gibt die Anzahl von Mitgliedern an, die der Warteschlange zugeordnet sind.|  
|QueueViewType|Typ|Bei Auswahllistenattributen ist keine Texteingabe möglich.|Wählen Sie aus, ob die Warteschlange öffentlich oder privat ist. Eine öffentliche Warteschlange kann von allen Benutzern angezeigt werden. Eine private Warteschlange kann nur von den Mitgliedern angezeigt werden, die der Warteschlange hinzugefügt werden.|  
  
<a name="BKMK_deletingQueues"></a>   
## <a name="restrictions-on-deleting-queues"></a>Einschränkungen beim Löschen von Warteschlangen  
 Eine Warteschlange kann nicht gelöscht werden, wenn Folgendes zutrifft:  
  
-   Wenn die Warteschlange über Warteschlangenelemente verfügt.  
  
-   Wenn die Warteschlange von einer Routingregel verwendet wird.  
  
<a name="BKMK_Enabling"></a>   
## <a name="enable-entities-for-queues"></a>Aktivieren von Entitäten für Warteschlangen  
 Um eine anpassbare Entität (`EntityMetadata.IsCustomizable = true`) für Warteschlangen zu aktivieren, verwenden Sie die Meldung <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, um das Attribut <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsValidForQueue> auf `true` festzulegen. Die Warteschlangenentität und die Warteschlangenelemententität sind anpassbare Entitäten, trotzdem können sie für Warteschlangen nicht aktiviert werden.  
  
 Die folgende Liste enthält standardmäßige für die Verwendung in Warteschlangen aktivierte Entitäten in Common Data Service:  
  
-   Termin  
  
-   Campaignactivity  
  
-   CampaignResponse  
  
-   Per E-Mail senden  
  
-   Faxnummer  
  
-   Vorfall  
  
-   Brief  
  
-   PhoneCall  
  
-   RecurringAppointmentMaster  
  
-   ServiceAppointment  
  
-   Social Media-Aktivitäten  
  
-   Aufgabe  
  
<a name="BKMK_Inheriting"></a>   
## <a name="inherit-privileges-and-provide-limited-access-to-a-queue"></a>Erben von Rechten und Bereitstellen von eingeschränktem Zugriff auf eine Warteschlange  
 Eine Warteschlange und ein Warteschlangenelement haben eine übergeordnete Beziehung, in der Vorgänge für den übergeordneten Warteschlangendatensatz an die untergeordneten Warteschlangenelementdatensätze weitergegeben werden.  
  
> [!NOTE]
>  In dieser speziellen übergeordneten Beziehung wird nur der Löschvorgang von der übergeordneten Warteschlangenentität zur untergeordneten Warteschlangenelemententität kaskadiert. Andere Aktionen, wie Zuweisen, Zusammenführen oder Freigeben, werden nicht kaskadiert.  
  
 Die Rechte für ein Warteschlangenelement werden von den Rechten für eine Warteschlange geerbt.  
  
- Wenn Sie das `prvReadQueue`-Recht besitzen, verfügen Sie auch über ein Leserecht für eine Warteschlangenelemententität.  
  
- Wenn Sie das `prvAppendToQueue`-Recht besitzen, verfügen Sie auch über Erstellungs-, Aktualisierungs- und Löschrechte für eine Warteschlangenelemententität.  
  
  Häufig muss der Zugriff auf die Warteschlange eingeschränkt werden, wenn Zugriff auf Warteschlangenelemente gewährt wird. Warteschlangenbesitzern mit Vollzugriff auf die Warteschlange wird empfohlen, eine Warteschlange für ein Team freizugeben, das nur eingeschränkten Zugriff auf die Warteschlange erhält. Angenommen, einem Supportteam werden Lese- und Anfügerechte für eine Warteschlange erteilt, dann können die Teammitglieder keine Änderungen an der Warteschlange, zum Beispiel eine Änderung des Warteschlangennamens oder des Warteschlangenbesitzers, vornehmen. Sie können jedoch Warteschlangenelemente erstellen, abrufen, aktualisieren und löschen.  
  
<a name="BKMK_Actions"></a>   
## <a name="actions-on-queues-and-queue-items"></a>Aktionen für Warteschlangen und Warteschlangenelemente  
 Sie können eine Reihe von Aktionen für Warteschlangen und Warteschlangenelemente ausführen, wenn Sie über die entsprechenden Rechte für die Warteschlangenentität und die Warteschlangenelemententität verfügen.  
  
### <a name="actions-on-queues"></a>Aktionen für Warteschlangen  
 Führen Sie die folgenden Aktionen für Warteschlangen aus:  
  
-   Passen Sie Warteschlangen und Warteschlangenelemente an, indem Sie benutzerdefinierte Attribute hinzufügen.  
  
-   Fügen Sie einen Entitätsdatensatz zu einer Warteschlange hinzu.  
  
    > [!NOTE]
    >  Ein Entitätsdatensatz kann nicht in mehreren Warteschlangen hinzugefügt werden. Eine Ausnahme ist ein E-Mail-Entitätsdatensatz mit dem Status "Empfangen".  
  
-   Fügen Sie Entitätsdatensätze unterschiedlichen Typs in derselben Warteschlange hinzu.  
  
-   Ändern Sie den Besitzer einer Warteschlange, indem Sie diese einem anderen Benutzer oder Team zuweisen.  
  
-   Fügen Sie Prizipale einer privaten Warteschlange mithilfe von <xref:Microsoft.Crm.Sdk.Messages.AddPrincipalToQueueRequest> hinzu.  
  
-   Löschen Sie den Verlauf für eine Warteschlange, indem Sie inaktive Warteschlangenelemente in der Warteschlange, wie z. B. abgeschlossene oder abgebrochene Telefonanrufe, löschen.  
  
-   Rufen Sie alle Warteschlangen ab, auf die ein Benutzer Zugriff hat, indem Sie <xref:Microsoft.Crm.Sdk.Messages.RetrieveUserQueuesRequest> verwenden.  
  
-   Legen Sie eine Warteschlange als standardmäßige Warteschlange für einen Benutzer fest, indem Sie das Attribut `SystemUser.QueueId` auf die ID der Warteschlage festlegen. Dieselbe Warteschlange kann als Standardwarteschlange für verschiedene Benutzer angegeben werden.  
  
-   Erstellen Sie einen Workflow, der für alle privaten Warteschlangen verwendet wird. Wenn ein Benutzer beispielsweise eine Aufgabe erstellt, fügt der Workflow die Aufgabe stets in der Standardwarteschlange des Benutzers hinzu. Sie können außerdem einen Workflow erstellen, der nur für eine bestimmte Warteschlange verwendet wird.  
  
-   Konfigurieren Sie eine E-Mail für eingehende Nachrichten, wenn eingehende E-Mail-Nachrichten an eine Warteschlange übermittelt werden sollen.  
  
### <a name="actions-on-queue-items"></a>Aktionen für Warteschlangenelemente  
 Führen Sie die folgenden Aktionen für Warteschlangenelemente aus:  
  
- Weisen Sie ein Warteschlangenelement einem Benutzer mithilfe von <xref:Microsoft.Crm.Sdk.Messages.PickFromQueueRequest> zu.  
  
- Verschieben Sie ein Warteschlangenelement aus einer Quellwarteschlange in eine Zielwarteschlange, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest>-Meldung verwenden. Ein Warteschlangenelement kann von einer Warteschlange in eine andere verschoben werden, bis es mithilfe der <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest>-Meldung deaktiviert wird.  
  
  > [!NOTE]
  >  Ein Warteschlangenelement wird automatisch deaktiviert, wenn der Status des Datensatzes im Warteschlangenelement von "Aktiv" in "Inaktiv" geändert wird. Dies betrifft für die Verwendung in Warteschlangen aktivierte Entitäten mit den Status "Aktiv" und "Inaktiv". Um festzustellen, ob eine Entität für die Verwendung in Warteschlangen aktiviert ist und ob ein Entitätsdatensatz den Status "Aktiv" oder "Inaktiv" aufweisen kann, lesen Sie die Informationen zu Entitätsmetadaten.  
  
- Verwenden Sie <xref:Microsoft.Crm.Sdk.Messages.ReleaseToQueueRequest>, um ein Warteschlangenelement wieder für die Warteschlange freizugeben.  
  
- Löschen Sie ein Warteschlangenelement aus einer Warteschlange, indem Sie die <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest>-Meldung verwenden. Wenn Sie ein Warteschlangenelement löschen, wird ein referenzierter Entitätsdatensatz nicht gelöscht. Wenn Sie einen Entitätsdatensatz löschen, werden jedoch sämtliche Warteschlangenelemente, die auf diesen Entitätsdatensatz verweisen, gelöscht.  
  
### <a name="see-also"></a>Siehe auch  
 <!--[Configure EMail for Incoming Messages](configure-email-incoming-messages.md)-->  
 
[Warteschlangenentität](reference/entities/queue.md)   
[QueueItem-Entität](reference/entities/queueitem.md)   
<xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest>   
 