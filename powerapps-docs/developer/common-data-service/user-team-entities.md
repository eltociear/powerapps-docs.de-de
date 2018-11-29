---
title: Benutzer- und Teamentitäten (Common Data Service für Apps) | Microsoft Docs
description: 'Erfahren Sie mehr über die Benutzer- und Teamverwaltung, mit der Sie die Benutzerkonten und -profile erstellen und verwalten können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
# <a name="user-and-team-entities"></a>Benutzer- und Teamentitäten

Die Benutzer- und Teamverwaltung ist der Bereich von CDS für Apps, in dem Sie die Benutzerkonten und -profile erstellen und verwalten können.  

 Ein *Benutzer* ist eine Person, die in einer Unternehmenseinheit arbeitet, die CDS für Apps verwendet. Jeder Benutzer hat ein Benutzerkonto. Alle Benutzer müssen einer einzigen Unternehmenseinheit zugeordnet sein. Diese Zuordnung steuert, auf welche Kundendaten der Benutzer Zugriff hat. Das Benutzerkonto umfasst Informationen wie die Telefonnummern des Benutzers, die E-Mail-Adresse sowie eine Verknüpfung zum Vorgesetzten des Benutzers. Jeder Benutzer verfügt über die Rechte und Berechtigungen zum Verwalten der eigenen Einstellungen. Jeder Benutzer entspricht einem Benutzer im Azure Active Directory für diese Organisation. Wenn Sie einen Benutzer erstellen, müssen Sie den Benutzer mindestens einer Sicherheitsrolle zuweisen. Selbst wenn der Benutzer Teil eines Teams ist, das über zugewiesene Rollen verfügt, sollte der Benutzer einer Rolle zugewiesen werden. Weitere Informationen zu Rechten und Zugriffsebenen finden Sie unter [Wie rollenbasierte Sicherheit verwendet werden kann, um den Zugriff auf Entitäten in Dynamics 365 zu kontrollieren](/dynamics365/customer-engagement/developer/security-dev/how-role-based-security-control-access-entities).  

 Ein *Team* ist eine Gruppe von Benutzern. Teams ermöglichen es, dass Benutzer organisationsübergreifend zusammenarbeiten und Informationen austauschen können. Weitere Informationen zu Teams siehe [Verwenden von Teams für die Zusammenarbeit und Freigabe von Informationen](use-access-teams-owner-teams-collaborate-share-information.md)  

 Datensätze können sich im Besitz von Benutzern oder Teams befinden. Legen Sie den <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OwnershipType> auf <xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>.`UserOwned` oder <xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>.`TeamOwned` fest, um den Besitz zu aktivieren. Sie können die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsOwnerRequest> oder <xref:Microsoft.Crm.Sdk.Messages.ReassignObjectsSystemUserRequest> verwenden, um eine Massenneuzuweisung aller Datensätze für einen Besitzer auszuführen.  

 Die folgende Abbildung zeigt die Entitätsbeziehungen für Benutzer und Teams.  

 ![Benutzer- und Team-Entitätsbeziehungsdiagramm](media/crm-v5s-em-userteam.gif "Benutzer- und Team-Entitätsbeziehungsdiagramm")  

## <a name="users"></a>Users  
 In CDS für Apps können Benutzer deaktiviert, jedoch nicht gelöscht werden. Um den Benutzer zu suchen, der derzeit angemeldet ist oder dessen Identität angenommenen wurde, rufen Sie die <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest>-Meldung auf.  

 Die folgende Tabelle enthält Details zu wichtigen Attributen für die Systembenutzerentität.  


|   Attributname    |                                                                                                                                                                                                                                                                                                                              Beschreibung                                                                                                                                                                                                                                                                                                                              |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     AccessMode      | Gibt den Zugriffstyp an, den der Benutzer auf CDS für Apps hat. Dies wird auch als Benutzertyp bezeichnet.<br /><br /> -   Administrator – Der Benutzer hat Zugriff auf den Einstellungsbereich, aber keinen Zugriff auf die Vertriebs-, Marketing- und Servicebereiche.<br />-   Nicht interaktiv – Der Benutzer kann auf das System zugreifen, jedoch nur über den Webdienst.<br />-   Lesezugriff – Der Benutzer verfügt über schreibgeschützten Zugriff.<br />-   Lesen-Schreiben – Der Benutzer hat sowohl Lese- als auch Schreibzugriff.<br />-   Supportbenutzer – Der Benutzer wurde vom CDS für Apps-Supportteam erstellt. |
|       CalType       |                                                               Gibt den Typ der Benutzerlizenz an.<br /><br /> -   Administrator – Der Benutzer verfügt über Administratorrechte.<br />-   Gerät voll – Der Benutzer des Geräts, auf dem CDS für Apps ausgeführt wird, hat sowohl Lese- als auch Schreibzugriff.<br />-   Gerät begrenzt – Der Benutzer des Geräts, auf dem CDS für Apps ausgeführt wird, hat nur schreibgeschützten Zugriff.<br />-   Vollzugriff – Der Benutzer hat sowohl Lese- als auch Schreibzugriff.<br />-   Begrenzt – Der Benutzer verfügt nur über schreibgeschützten Zugriff.                                                                |
|     IsDisabled      |                                                                                                                                                                                                                                             Gibt an, ob der Benutzer deaktiviert ist. Nur lizenzierte Benutzer oder Benutzer mit dem Zugriffsmodus Support oder Nicht interaktiv können aktiviert werden. Supportbenutzer können nicht deaktiviert werden.                                                                                                                                                                                                                                              |
|     IsLicensed      |                                                                                                                                                                             Gibt an, ob der Benutzer eine Lizenz besitzt. Dies gilt für Kunden, die über die Microsoft Online Services environment Zugriff auf CDS für Apps haben. Dieses Attribut ist schreibgeschützt und wird vom System aktualisiert.                                                                                                                                                                              |
| IsSyncWithDirectory |                                                                                                                                 Gibt an, ob der Benutzer mit dem Office 365-Verzeichnis synchronisiert ist. Dies gilt für Kunden, die über die Microsoft Online Services environment Zugriff auf CDS für Apps haben. Dieses Attribut kann nur bei der Erstellung festgelegt werden und ist sonst schreibgeschützt.                                                                                                                                 |
|       QueueId       |                                                                                                                                                                                                                                                                                                               Gibt die Standardwarteschlange für den Benutzer an.                                                                                                                                                                                                                                                                                                               |

 Zugriffsprüfungen sind erweiterbar. Sie können auf Entitäten basierend auf den Rollen, die dem Benutzer zugewiesen sind, sowie den Rollen, die dem Team zugewiesen sind, dem der Benutzer angehört, zugreifen. Dadurch kann ein Benutzer über Rechte außerhalb der Unternehmenseinheit verfügen.  

> [!NOTE]
>  Die Rechte eines Benutzers umfassen die Rechte von den Benutzerrollen und die Rechte der Rollen aller Teams, denen der Benutzer angehört.  


 Nicht interaktive Benutzer werden häufig beim Schreiben von Service-zu-Service-Code verwendet, da diese Benutzer die Lizenz nicht erschöpfen. CDS für Apps erlaubt fünf kostenlose nicht interaktive Benutzer. Um einen nicht interaktiven Benutzer zu deaktivieren, aktualisieren Sie den Benutzerdatensatz, und ändern Sie den `accessmode`-Wert in einen anderen Wert. Der Benutzer wird automatisch deaktiviert.

## <a name="community-tools"></a>Community-Tools

**Hilfsprogramm für Benutzereinstellungen** ist ein Tool, das von der XrmToolbox-Community für CDS für Apps entwickelt wurde. Weitere Informationen finden Sie im Thema [Entwicklertools](developer-tools.md) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von CDS for Apps und es wird kein Support für die Communitytools angeboten.
> Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Siehe auch  
 [Verwaltungs- und Sicherheitsentitäten](/dynamics365/customer-engagement/developer/administration-security-entities)   
 [Verwenden von Teams für die Zusammenarbeit und Freigabe von Informationen](use-access-teams-owner-teams-collaborate-share-information.md)   
 [Teamentität](reference/entities/team.md)   
 [Angeben der Zeitzoneneinstellungen für einen Benutzer](specify-time-zone-settings-user.md)   
 [TeamTemplate-Entität](reference/entities/teamtemplate.md)   
 [SystemUser-Entität](reference/entities/systemuser.md)   
 [UserSettings-Entität](reference/entities/usersettings.md)   
 [Beispiel: Deaktivieren eines Benutzers](/dynamics365/customer-engagement/developer/sample-disable-user)   
 [Beispiel: Datensätze mithilfe von GrantAccess, ModifyAccess und RevokeAccess Messages teilen](org-service/samples/share-records-using-grantaccess-modifyaccess-revokeaccess-messages.md)   
 [Beispiel: Freigeben eines Datensatzes mithilfe eines Zugriffsteams](org-service/samples/share-record-using-access-team.md)   
 [Blog: Dienstkonten – Nicht-interaktive Benutzer](http://go.microsoft.com/fwlink/p/?LinkId=234350)   
 [Rechte- und Rollenentitäten](/dynamics365/customer-engagement/developer/privilege-role-entities)
