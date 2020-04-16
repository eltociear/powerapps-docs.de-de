---
title: Verwenden von Zugriffsteams und Besitzerteams, um zusammenzuarbeiten und Informationen zu teilen (Common Data Service) | Microsoft-Dokumentation
description: Lernen Sie mehr über das Verwenden von Zugriffsteams und Besitzersteams, um zusammenzuarbeiten und Informationen zu teilen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 381127cd3c85cdb76e8d8e591943b5fb470a9d19
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155210"
---
# <a name="use-access-teams-and-owner-teams-to-collaborate-and-share-information"></a>Verwenden von Zugriffsteams und Besitzersteams, um zusammenzuarbeiten und Informationen zu teilen

Mit *Besitzersteams* oder *Zugriffsteams* können Sie Geschäftsobjekte leicht freigeben und über Unternehmenseinheiten hinweg mit Benutzern in Common Data Service zusammenarbeiten. Ein Team gehört zu einer Unternehmenseinheit, aber es kann Benutzer von anderen Unternehmenseinheiten enthalten. Ein Benutzer kann mehr als einem Team zugewiesen werden.  
  
 Ein Besitzerteam besitzt Datensätze und ihm sind Sicherheitsrollen zugewiesen. Die Berechtigungen eines Teams werden durch diese Sicherheitsrollen definiert. Zusätzlich zu den Berechtigungen, die das Team bereitgestellt werden, verfügen Teammitglieder über die Berechtigungen, die durch die ihre individuellen Sicherheitsrollen und durch die Rollen aus den anderen Teams, in denen sie Mitglieder sind, bestimmt werden. Ein Team verfügt über vollständige Zugriffsrechte auf die Datensätze, die das Team besitzt.  
  
> [!NOTE]
>  Während Teams Zugang zu einer Benutzergruppe bieten, müssen Sie einzelne Benutzer immer noch mit Sicherheitsrollen verknüpfen, wodurch die Rechte gewährt werden, die sie benötigen, um benutzereigene Datensätze zu erstellen, zu aktualisieren oder zu löschen. Diese Rechte können nicht angewendet werden, indem man Sicherheitsrollen einem Team zuweist und dann den Benutzer diesem Team hinzufügt.  
  
 Ein Zugriffsteam besitzt keine Datensätze und ihm sind keine Sicherheitsrollen zugewiesen. Die Berechtigungen der Teammitglieder werden durch ihre individuellen Sicherheitsrollen und die Rollen der Teams, deren Mitglieder sie sind, bestimmt. Die Datensätze werden für ein Zugriffsteam freigegeben und dem Team werden Zugriffsrechte auf die Datensätze, wie Lesen, Schreiben oder Anfügen gewährt.  
  
 Die Teamfunktionalität wird von der `Team`-Entität und der `TeamTemplate`-Entität unterstützt. Die Entität `Team` wird verwendet, um Besitzerteams und vom Benutzer erstellte Zugriffsteams zu erstellen. Für automatisch erstellte Zugriffsteams wird die Entität `TeamTemplate` und die Entität `Team` verwendet.  
  
<a name="BKMK_OwnerAccess"></a>   
## <a name="owner-team-or-access-team"></a>Besitzerteam oder Zugriffsteam?  
 Die Auswahl des Teamtyps hängt vom den Zielen, der Art des Projekts oder auch von der Größe Ihrer Organisation ab. Es gibt einige Richtlinien, die Sie verwenden können, um den richtigen Teamtyp auszuwählen.  
  
### <a name="when-to-use-owner-teams"></a>Wann Sie Besitzersteams verwenden sollten  
  
- Das Besitzen von Datensätzen durch andere Entitäten als Benutzer wird durch die Richtlinien Ihres Unternehmens erfordert.  
  
- Die Anzahl der Teams ist bekannt, wenn Ihr Common Data Service-System eingerichtet wird.  
  
- Tägliche Berichte zum Fortschritt der Besitzerteams sind erforderlich.  
  
### <a name="when-to-use-access-teams"></a>Wann Sie Zugriffsteams verwenden sollten  
  
- Die Teams werden dynamisch gebildet und aufgelöst. Dies geschieht typischerweise dann, wenn keine klaren Kriterien für die Bildung der Teams existieren, wie etwa ein bestimmtes Territorium, Produkt oder Volumen.  
  
- Die Anzahl der Teams ist nicht bekannt, wenn Ihr Common Data Service-System eingerichtet wird.  
  
- Die Teammitglieder benötigen unterschiedliche Zugriffsrechte zu den Datensätzen. Sie können einen Datensatz für verschiedene Zugriffsteams freigeben, wobei jedes Team unterschiedliche Zugriffsrechte für den Datensatz vergibt. Beispielsweise wird das Lesezugriffsrecht einem Team auf dem Account erteilt und einem anderen Team Lese-, Schreib- und Freigaberechte für den gleichen Account.  
  
- Ein eindeutiger Satz von Benutzern benötigt Zugriff auf einen bestimmten Datensatz, ohne diesen zu besitzen.  
  
> [!NOTE]
>  Eine weitere Art "Zugriffsteam" wird durch die Zugriffsteamvorlagen behandelt, die von der Webanwendung verwendet werden. Dies ist der Typ des Teams, der sich häufig ändert, wie ein bestimmtes Vertriebsteam eines Firmendatensatzes. Wenn ein Benutzer einem Vertriebsteam in einer Firma hinzugefügt wird, erstellt die Webanwendung im Hintergrund ein Team, das für diesen Datensatz spezifisch ist, und fügt den Benutzer zu diesem hinzu.  
>   
>  Diese Art des Zugriffsteams wird im vorliegenden Thema nicht abgedeckt.  
  
<a name="BKMK_SettingUp"></a>   
## <a name="setting-up-teams"></a>Installieren von Teams  
 Zusätzlich zu den Besitzer- und Zugriffsteamtypen werden die Zugriffsteams weiter in vom Benutzer erstellte und automatisch erstellte Teams (System-verwaltete) Teams unterteilt. Die Setupinformationen sind für jeden Teamtyp spezifisch.  
  
### <a name="owner-team"></a>Besitzerteam  
 Ein Besitzerteam kann mehrere Datensätze besitzen. Um ein Besitzerteam zu erstellen, verwenden Sie die `Team`-Entität und legen Sie das Attribut `Team.TeamType` zu `Owner` fest. Eine Liste der `TeamType`-Werte finden Sie in den `Team`-Entitätsmetadaten.  
  
> [!NOTE]
> Zum Anzeigen der Entitätsmetadaten für Ihre Organisation installieren Sie die Metadatenbrowserlösung, die in [Durchsuchen der Metadaten für Ihre Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata) beschrieben ist. Sie können die Referenzdokumentation für Entitäten auch in der [Entitätsreferenz](/dynamics365/customer-engagement/developer/about-entity-reference) durchsuchen. 
  
 Um ein Team zum Besitzer eines Datensatzes zu machen, müssen Sie ihm einen Datensatz zuweisen. Verwenden Sie zum Zuweisen die <xref:Microsoft.Crm.Sdk.Messages.AssignRequest>-Nachricht. Zum Zuweisen von Datensätzen zu einem Besitzersteam in einem Massenvorgang, verwenden Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsOwnerRequest> oder die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsSystemUserRequest>.  
  
 Bei einem Datensatz, bei dem das Team als Besitzer fungiert, muss die <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OwnershipType>-Eigenschaft zu <xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>.`TeamOwned` festgelegt sein.  
  
 Wenn ein Besitzerteam keine Datensätze besitzt und ihm keine Sicherheitsrollen zugewiesen sind, kann es in ein Zugriffsteam umgewandelt werden, indem die <xref:Microsoft.Crm.Sdk.Messages.ConvertOwnerTeamToAccessTeamRequest>-Nachricht verwendet eird. Dies ist eine nicht umkehrbare Umwandlung. Sie können das Zugriffsteam nicht wieder in ein Besitzerteam konvertieren. Während der Konvertierung werden alle mit dem Team verbundenen Warteschlangen und Postfächer gelöscht.  
  
 Zum Hinzufügen oder Entfernen von Teammitgliedern, verwenden Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> und die Nachricht <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest>.  
  
### <a name="user-created-access-team"></a>Vom Benutzer erstelltes Zugriffsteam  
 Sie können mehrere Datensätze für ein benutzererstelltes Zugriffsteam freigeben. Um ein Zugriffsteam zu erstellen, verwenden Sie die Teamentität und legen Sie das `Team.TeamType`-Attribut zu `Access` fest. Eine Liste der `TeamType`-Werte finden Sie in den `Team`-Entitätsmetadaten. Sie finden diese Informationen in den Metadaten für Ihre Organisation. Weitere Informationen finden Sie in den voranstehenden Informationen zum Metadatenbrowser.  
  
 Wenn Sie einem benutzererstellten Team Zugriff auf einen Datensatz gewähren möchten, verwenden Sie die <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>-Nachricht. Für vom Benutzer erstellte Teams ist das `Team.SystemManaged`-Attribut `false`. Eine Liste der `Team.SystemManaged`-Werte finden Sie in den `Team`-Entitätsmetadaten. Sie finden diese Informationen in den Metadaten für Ihre Organisation. Weitere Informationen finden Sie in den voranstehenden Informationen zum Metadatenbrowser.  
  
 Zum Hinzufügen oder Entfernen von Teammitgliedern, verwenden Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> und die Nachricht <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest>.  
  
 Um Teammitgliedern unterschiedliche Zugriffsrechte auf Datensätze zur Verfügung zu stellen, erstellen Sie mehrere Teams und gewähren Sie jedem Team einen anderen Satz von Zugriffsrechten für Datensätze.  
  
### <a name="auto-created-system-managed-access-team"></a>Automatisch erstelltes (System-verwaltetes) Zugriffsteam  
 Ein automatisch erstelltes (systemverwaltetes) Team wird für einen bestimmten Datensatz erstellt, und kann nicht mit anderen andere Datensätzen geteilt werden. Für systemverwaltete Teams müssen Sie eine Teamvorlage zur Verfügung stellen. Wenn Sie eine Vorlage erstellen, können Sie die Teamvorlagenentität verwenden. In derr Vorlage legen Sie den Entitätstyp und die Zugriffsrechte für den Entitätsdatensatz, die den Teammitglidern bei Erstellung des Teams gewährt werden, wie Lesen oder Schreiben, fest. Die Entität, Sie in der Vorlage angeben, muss für automatisch erstellte Zugriffsteams aktiviert werden. Um für die Teammitglieder mit unterschiedlichen Zugriffsrechten für den Datensatz auszustatten, müssen Sie einige Teamvorlagen erstellen. Zum Beispiel stelen Sie für die Firmenentität eine Vorlage mit dem Lesezugriffsrecht für ein Team zur Verfügung, das nur in der Lage sein muss, den Datensatz anzuzeigen. Stellen Sie eine zweite Vorlage mit den Zugriffsrechten für Lesen, Schreiben und Freigeben für ein Team frei, das mehr Zugriff auf den gleichen Datensatz benötigt.  
  
 Um eine Entitä für die automatisch erstellten Zugriffsteams zu aktivieren, legen Sie das <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.AutoCreateAccessTeams>-Attribut zu `true` fest.  
  
 Die maximale Anzahl der Teamvorlagen, die Sie für eine Entität erstellen können, ist in der <xref:Microsoft.Xrm.Sdk.Deployment.TeamSettings.MaxAutoCreatedAccessTeamsPerEntity>-Bereitstellungseinstellung angegeben. Der Standardwert ist 2. Die maximale Anzahl der Entitäten, die Sie für automatisch erstellte Zugriffsteams aktivieren können, ist in der <xref:Microsoft.Xrm.Sdk.Deployment.TeamSettings.MaxEntitiesEnabledForAutoCreatedAccessTeams>-Bereitstellungseinstellung angegeben. Der Standardwert ist 5. Weitere Informationen: [Bereitstellungs-Entitäten und Bereitstellungs-Konfigurationseinstellungen](https://msdn.microsoft.com/library/gg328063.aspx) und [Verwaltung der Bereitstellung mithilfe von Windows PowerShell](https://technet.microsoft.com/library/dn531202.aspx)  
  
 Die Benutzer werden automatisch im systemverwalteten Team hinzugefügt und entfernt, wenn Sie die Benutzer einem bestimmten Datensatz hinzufügen oder sie daraus entfernen, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.AddUserToRecordTeamRequest>-Nachricht und die <xref:Microsoft.Crm.Sdk.Messages.RemoveUserFromRecordTeamRequest>-Nachricht verwenden. Das tatsächliche Team wird erstellt, wenn Sie den ersten Benutzer dem Datensatz hinzufügen und die dem Team-ID in <xref:Microsoft.Crm.Sdk.Messages.AddUserToRecordTeamResponse.AccessTeamId> zurückgegeben wird. Das `Team.SystemManaged`-Attribut für dieses Team wird zu `true` festgelegt. Eine Liste der `Team.SystemManaged`-Werte finden Sie in den `Team`-Entitätsmetadaten. Sie finden diese Informationen in den Metadaten für Ihre Organisation. Weitere Informationen finden Sie in den voranstehenden Informationen zum Metadatenbrowser.  Der Aufrufer der Message muss über das Recht Freigeben auf der Entität und die Zugriffsrechte für den Datensatz verfügen, die mit den Zugriffsrechten übereinstimmen, die in der Tabelle bereitgestellt werden. Wenn z. B. die Vorlage Lesezugriffsrechte angibt, muss der aufrufende Benutzer über Lesezugriffsrechte für den Datensatz verfügen. Um dem Team hinzugefügt werden zu können, muss ein Benutzer mindestens über die Zugriffsebene Basic (User) Read für den in der Vorlage angegebenen Datensatz verfügen.  
  
 Aufgrund der hierarchischen Beziehung zwischen der Teamvorlage und den systemverwalteten Zugriffsteams werden alle mit der Vorlage verknüpften Teams gemäß den kaskadierenden Regeln gelöscht, wenn Sie eine Vorlage löschen.  
  
 Wenn Sie für die Teamvorlage Zugriffsrechte ändern, werden die Änderungen nur auf die neuen automatisch erstellten Zugriffsteams angewendet. Dies wirkt sich nicht auf vorhandene Teams aus.  
  
<a name="BKMK_ShortSummary"></a>   
## <a name="quick-reference-to-teams"></a>Kurzübersicht zu Teams  
 Verwenden Sie die folgenden Informationen als Kurzübersicht zu den verfügbaren Teams.  
  
|Teams|Wann verwenden?|Welche Entitäten verwenden?|Teamvorlage verwenden?|Welche Nachrichten verwenden, um Teammitglieder hinzuzufügen oder zu entfernen?|Besitzt Datensätze?|Wie viele Datensätze besitzt er bzw. auf wie viele hat er Zugriff?|Sind ihm Sicherheitsrollen zugewiesen?|  
|----------|------------------|-------------------------|------------------------|---------------------------------------------------------|-------------------|---------------------------------------------|----------------------------------|  
|Bes.|Datensatzbesitz durch das Team ist erforderlich.<br /><br /> Die Anzahl der Teams ist bekannt, wenn das System eingerichtet wird.|`Team`|Nein|<xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest>.|Ja|Kann mehrere Datensätze besitzen.|Ja|  
|Zugriff, vom Benutzer erstellt|Mehrere Datensätze müssen für das Team freigegeben werden.<br /><br /> Die Anzahl der Teams ist nicht bekannt, wenn das System eingerichtet wird.<br /><br /> Teammitglieder benötigen unterschiedliche Zugriffsrechte zu den Datensätzen.|`Team`|Nein|<xref:Microsoft.Crm.Sdk.Messages.AddMembersTeamRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.RemoveMembersTeamRequest>|Nein|Kann auf mehrere Datensätze zugreifen.|Nr. Stellt Zugriffsrechte für den Datensatz zur Verfügung.|  
|Zugriff, automatisch erstellt (systemverwaltet)|Eindeutiger Satz von Benutzern bearbeitet einen einzelnen Datensatz.<br /><br /> Teammitglieder benötigen unterschiedliche Zugriffsrechte zu den Datensätzen.<br /><br /> Automatisches Erstellen von Teams pro Datensatz ist erwünscht.|`TeamTemplate`<br /><br /> `Team`|Ja|<xref:Microsoft.Crm.Sdk.Messages.AddUserToRecordTeamRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.RemoveUserFromRecordTeamRequest>|Nein|Kann nur auf einen Datensatz zugreifen.|Nr. Stellt Zugriffsrechte für den Datensatz zur Verfügung.|  
  
> [!NOTE]
>  Besitzersteams und Zugriffsteams stellen Zugriffsrechte auf den Datensatz und verknüpfte Datensätze zur Verfügung, z. B. auf eine Firma und alle Verkaufschancen, die mit dieser Firma verknüpft sind. Im Falle einer übergeordneten Beziehung zwischen den Datensätzen werden Kaskadierungsregeln angewendet. Für Benutzerteams können Sie auf Entitäten basierend auf den Rollen, die dem Benutzer zugewiesen sind, sowie den Rollen, die dem Team zugewiesen sind, dem der Benutzer angehört, zugreifen. Dadurch kann ein Benutzer über Rechte außerhalb der Unternehmenseinheit verfügen. Weitere Informationen: [Verhalten von Entitätsbeziehungen](/dynamics365/customer-engagement/developer/entity-relationship-behavior)  
> 
> [!NOTE]
>  Ein Benutzer muss über ausreichende Rechte verfügen, um sich einem Zugriffsteam anzuschließen. Angenommen, das Zugriffsteam verfügt über das Zugriffsrecht "Löschen" für ein Konto, dann muss der Benutzer über das Zugriffsrecht "Löschen" für die Entität "Konto" verfügen, um sich dem Team anzuschließen. Wenn Sie versuchen, einen Benutzer mit unzureichenden Berechtigungen hinzuzufügen, wird diese Fehlermeldung angezeigt: "Sie können den Benutzer dem Zugriffsteam nicht hinzufügen, da der Benutzer keine ausreichenden Berechtigungen für die Entität besitzt".  
  
### <a name="see-also"></a>Siehe auch  
 [Beispiel: Freigeben eines Datensatzes mithilfe eines Zugriffsteams](org-service/samples/share-record-using-access-team.md)   
 [Verwalten von Teams](https://technet.microsoft.com/library/dn531089.aspx)   
 [Whitepaper: Zugriffsteams in Microsoft Dynamics CRM 2013](https://download.microsoft.com/download/E/9/0/E9009308-CA01-4B37-B03C-435B8ACB49B4/Access%20Teams%20with%20Microsoft%20Dynamics%20CRM%202013.pdf)   
 [Whitepaper: Skalierbare Sicherheits-Modellierung mit Microsoft Dynamics CRM](https://go.microsoft.com/fwlink/p/?LinkID=328757)   
 [Benutzer- und Teamentitäten](user-team-entities.md)   
 [Teamentität](reference/entities/team.md)   
 [TeamTemplate-Entität](reference/entities/teamtemplate.md)   
 [Ausführen von Bereitstellungsaufgaben mithilfe von Windows PowerShell](https://technet.microsoft.com/library/dn531202.aspx)   
 [Verwenden von Datensatz-basierter Sicherheit zum Steuern des Zugriffs auf Datensätze](/dynamics365/customer-engagement/developer/security-dev/use-record-based-security-control-access-records)   
 [Wie rollenbasierte Sicherheit verwendet werden kann, um den Zugriff auf Entitäten in Dynamics 365 zu kontrollieren](/dynamics365/customer-engagement/developer/security-dev/how-role-based-security-control-access-entities)   
 [Kaskadierende Verhaltensweise](/dynamics365/customer-engagement/developer/entity-relationship-behavior#BKMK_CascadingBehavior)
