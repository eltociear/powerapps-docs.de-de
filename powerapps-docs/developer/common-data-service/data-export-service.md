---
title: Datenenexportservice (Common Data Service) | Microsoft Docs
description: Funktionen, Voraussetzungen, API und Programmierung des Datenexport-Service.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sabinn-msft
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a00d4e751452be55c824727af238900e964a649f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752994"
---
# <a name="data-export-service"></a>Datenexportservice

Der Datenexport ist ein Add-On-Service, der von der Common Data Service-Lösung bereitgestellt wird und der die Möglichkeit gibt, Common Data Service-Daten auf einen Microsoft Azure SQL-Datenbankspeicher in einem kundeneigenen Microsoft Azure-Abonnement zu replizieren. Die unterstützten Ziele sind Microsoft Azure SQL-Datenbank und Microsoft Azure SQL Server auf virtuellen Microsoft Azure-Computern. Datenexport synchronisiert intelligent das gesamte Dynamics 365-Schema und die Daten und synchronisiert danach auf fortlaufender Basis, wenn Änderungen im Dynamics 365 (online)-System eintreten (Delta-Änderungen).  
  
 Der Datenexportservice bietet eine Schnittstelle zum Verwalten der Konfiguration und der laufenden Verwaltung dieses Service auf Common Data Service.  Weitere Informationen finden Sie unter [Datenexport](https://technet.microsoft.com/library/a70feedc-12b9-4a2d-baf0-f489cdcc177d). In diesem Thema werden die entsprechenden programmgesteuerte Benutzeroberfläche und die Probleme für diesen Service behandelt.  
  
## <a name="prerequisites-for-using-the-data-export-service"></a>Voraussetzungen für die Verwendung des Datenexport-Service  
 Da dieser Service einen externen Zugriff auf die Microsoft Azure SQL-Datenbank vom Common Data Service erfordert, müssen einige Voraussetzungen erfüllt sein, bevor Sie erfolgreich auf den Service zugreifen können. Die folgenden Voraussetzungen werden im Detail aus Sicht eines Administrators erläutert im Abschnitt [Voraussetzungen für die Verwendung des Datenexport-Service-](https://technet.microsoft.com/library/mt744592.aspx).  
  
 Der Common Data Service - Dienst muss konfiguriert werden, damit:  
  
- Die Entitäten, die exportiert wurden, werden mit Änderungsnachverfolgung aktiviert. Weitere Informationen finden Sie unter [Verwenden von Änderungsnachverfolgung zum Synchronisieren von Daten mit externen Systemen](use-change-tracking-synchronize-data-external-systems.md).  
  
- Code wird im Rahmen eines Benutzers mit der Systemadministrator-Sicherheitsrolle ausgeführt.  
  
> [!NOTE]
>  Beachten Sie, dass programmgesteuerter Zugriff für diesen Service *nicht* die Installation der zugeordneten verwalteten Datenexportlösung erfordert.  
  
 Die SQL Azure Ziel Datenbank muss konfiguriert werden, damit:  
  
- Das Abonnement muss die Menge der Daten, die von Ihrer Common Data Service-Instanz synchronisiert werden unterstützen.  
  
- Firewalleinstellungen muss den Zugriff von der IP-Adresse des Datenexportservice erlauben. Weitere Informationen: [Eine Azure SQL Datenbankserverstufen-Firewallregel mithilfe von Azure Portal konfigurieren](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/).  
  
- Es wird empfohlen, die Option "Zugriff an Azure Services" aktiviert zu lassen.  
  
- Der Datenbankbenutzer, der in der Datenexportverbindungszeichenfolge definiert ist, muss die richtigen Berechtigungen verfügen, um auf der Zieldatenbank zu erstellen und zu ändern.  Als Minimum schließen diese ein: `CRTB`, `CRTY`, `CRVW`, `CRPR`und `ALUS`. Weitere Informationen finden Sie unter [Berechtigungen (Database Engine)](https://msdn.microsoft.com/library/ms191291.aspx).  
  
- Mindestens ein Benutzer muss Berechtigungen für das Schema haben. Im folgenden Skript wird ein neuer Benutzer erstellt.  
  
```sql  
  
USE MASTER;  
CREATE LOGIN NewUser WITH PASSWORD='newpassword';  
  
USE DESTINATIONDATABASE;  
CREATE USER NewUser FOR LOGIN NewUser  
GRANT CREATE TABLE, CREATE TYPE, CREATE VIEW, CREATE PROCEDURE, ALTER ANY USER to NewUser  
GRANT ALTER, REFERENCES, INSERT, DELETE, UPDATE, SELECT, EXECUTE ON SCHEMA::dbo TO NewUser  
  
```  
  
Für online Lösungen und Services stellt Azure einen [Key Vault](https://azure.microsoft.com/services/key-vault/)-Service bereit, um kryptografische Schlüssel, Kennwörter und andere Geheimnisse zu schützen.  Um Vault Azure zu verwenden, muss dieser kundeneigene Service konfiguriert sein, damit die Berechtigung für "Dynamics 365-Datenexport-Service" gewährt wird, das verwendet wird, um die SQL Azure-Verbindungszeichenfolge sicher zu speichern. Um diese Konfiguration mit einem PowerShell-Skript ausführen, siehe [Einrichten von Azure Key Vault](https://technet.microsoft.com/library/mt744592.aspx). Alternativ kann dieser Service über die REST-API verwaltet werden; sehen Sie dazu [Key Vault-Verwaltung](https://msdn.microsoft.com/library/azure/mt620024.aspx).  
  
Es ist ratsam, dass die Domäne https://discovery.crmreplication.azure.net/ der Liste der vertrauenswürdigen Websites in Ihrem Browser hinzugefügt und Popups für diesen Ort aktiviert werden.  
  
## <a name="programming-for-the-data-export-service"></a>Programmierung für den Datenexport-Service  
 Der Datenexport-Service trifft auf eine Rest-basierte API, die in zwei Gruppen unterteilt werden: eine Gruppe von `Metadata` Vorgänge, um Common Data Service Organisationsstrukturen, Beziehungen und Verbindungsinformationen zu erkunden und eine Gruppe für `Profiles` Vorgänge zum Konfigurieren und Verwalten der Datenenreplikation.  Die API ist in den folgenden Swagger URLs definiert und dokumentiert: [Swaggern von](https://swagger.io/) URLs:  
  
|Swagger-Endpunkt|Beschreibung|  
|----------------------|-----------------|  
|[https://discovery.crmreplication.azure.net/swagger/docs/2016-01-01](https://discovery.crmreplication.azure.net/swagger/docs/2016-01-01)|JSON-Definition der Datenexport-Service API zur Verwendung mit Entwicklertools und dynamische Prozesse|  
|[https://discovery.crmreplication.azure.net/swagger/ui/index#](https://discovery.crmreplication.azure.net/swagger/ui/index)|Die benutzerfreundliche Version dieser API als Entwicklerreferenz|  
  
<a name="bk_ApiQuickReference"></a>   
### <a name="api-quick-reference"></a>API  Kurzübersicht  
 Diese Schnittstellen werden für den Benutzer in den folgenden Tabellen zusammengefasst.  
  
 **Metadaten-Vorgänge** (`https://discovery.crmreplication.azure.net/crm/exporter/metadata/`)  
  
|Ressource|Methoden|Beschreibung|  
|--------------|-------------|-----------------|  
|Organisationen|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetOrganizations)|Ruft Organisationsdetails für alle Organisationen ab, zu denen der aktuelle Benutzer gehört|  
|Entdecken|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetOrgDetails)|Abrufen von Organisationsdetails für die angegebene Organisation|  
|Connector|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetConnectorDetails)|Abrufen von Verbindungsdetails für die angegebene Organisation|  
|Entitäten|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetEntities)|Rufen Sie alle exportfähigen öffentlichen Stellen für die angegebene Organisation ab|  
|Beziehungen|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetRelationships)|Rufen Sie alle exportfähigen Beziehungen für die angegebene Organisation ab|  
|hasorgacceptedprivacyterms|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_HasOrgAcceptedPrivacyTerms)|Überprüfen Sie, ob die zugeordnete Organisation die Datenschutzbedingungen akzeptiert hat|  
|acceptprivacyterms|[NACHRICHT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_AcceptOrgPrivacyTerms)|Nehmen Sie die angegebene Organisation für den Datenzugriff an|  
  
 **Profilvorgänge** (`[Organization-URI]/crm/exporter/`)  
  
|Ressource|Methoden|Beschreibung|  
|--------------|-------------|-----------------|  
|Profile|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetProfilesByOrganizationId), [POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_CreateProfile)|Rufen Sie die Profile für die angegebene Organisation ab, erstellen Sie ein neues Exportprofil|  
|Profile/{id}|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetProfileById), [PUT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_UpdateProfile), [DELETE](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_DeleteProfileById)|Bestimmtes Profil abrufen, aktualisieren oder Löschen|  
|Profile/{id}/aktivieren|[NACHRICHT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_Activate)|Aktivieren Sie ein Profil, das die Replikation beider zugeordneten Metadaten und Daten startet|  
|Profile/{id}/Metadaten aktivieren|[NACHRICHT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_ActivateMetadata)|Aktivieren Sie nur Profile für Metadatenreplikation|  
|Profile/{id}/Daten aktivieren|[NACHRICHT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_ActivateData)|Aktivieren Sie nur Profile für Datenreplikation|  
|Profile/{id}/deaktivieren|[NACHRICHT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_Deactivate)|Ein Profil deaktivieren|  
|Profile/{id}/Test|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetTestResultById)|Führen Sie auf einem vorhandenen Profil Testvorgänge aus|  
|Profile/überprüfen|[NACHRICHT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_ValidateBeforeProfileCreation)|Führen Sie Testvorgänge auf einer Profilbeschreibung aus, bevor Sie es erstellen|  
|Profile/{id}/Fehler|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetProfileFailuresInfoById)|Hier finden Sie die Verbindungszeichenfolge für einen Blob, der Fehlerdetails für ein gegebenes Profil enthält|  
  
### <a name="gain-access"></a>Zugriff erhalten  
Da nur Common Data Service-Systemadministratoren die Autorisierung besitzen, um Datenexportvorgänge auszuführen, erzwingen diese APIs die Aufruferautorisierung durch die Nutzung von Azure Active Directory ([AAD](https://azure.microsoft.com/services/active-directory/)) [Sicherheitstokens](https://azure.microsoft.com/documentation/articles/active-directory-token-and-claims/). Der folgende Codeausschnitt wird zeigt das Generieren eines Tokens für eine Webanwendung, indem er der Name und das Kennwort des Administrators verwendet.   Sie müssen `AppId`, `crmAdminUser` und `crmAdminPassword` durch die Werte ersetzen, die Ihrem Dienst entsprechen. Diese Methode kann für die Entwicklung und Tests verwendet werden, aber für die Produktion sollten sicherere Methoden wie Azure Key Vault genutzt werden.  
  
```csharp  
  
//Reference Azure AD authentication Library (ADAL)    
using Microsoft.IdentityModel.Clients.ActiveDirectory;  
   . . .  
    string yourAppClientID = "[app-associated-GUID]";   //Your AAD-registered AppId   
    string crmAdminUser = "admin1@contoso.com";  //Your CRM administrator user name  
    string crmAdminPassword = "Admin1Password";  //Your CRM administrator password;   
    //For interactive applications, there are overloads of AcquireTokenAsync() which prompt for password.   
    var authParam = AuthenticationParameters.CreateFromResourceUrlAsync(new   
        Uri("https://discovery.crmreplication.azure.net/crm/exporter/aad/challenge")).Result;  
    AuthenticationContext authContext = new AuthenticationContext(authParam.Authority, false);  
    string token = authContext.AcquireTokenAsync(authParam.Resource, yourAppClientID,   
        new UserCredential(crmAdminUser, crmAdminPassword)).Result.AccessToken;  
  
```  
  
Anweisungen, wie Sie eine `AppId` erhalten, finden Sie unter [Autorisieren des Zugriffs auf Webanwendungen mithilfe von OAuth 2.0 und Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-protocols-oauth-code/). Weitere Informationen über die Azure-Benutzersicherheit finden Sie unter [Authentifizierungsszenarien für Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/).  
  
### <a name="error-handling-and-failure-processing"></a>Fehlerbehandlung und Fehlerverarbeitung  
 Sobald ein Profil korrekt konfiguriert ist, ist die Synchronisierung normalerweise sehr zuverlässig. Wenn ein Datensatz nicht synchronisiert, gilt die folgende Fehlerverarbeitung:  
  
1. Nach dem konfigurierten Wiederholungsintervall wird ein weiterer Versuch den Datensatz zu synchronisieren gemacht. Dies wird für die konfigurierte maximale Anzahl von Wiederholungen versucht.  
  
2. Der Datensatz wird als verarbeitet gekennzeichnet.  
  
3. Ein entsprechender Fehlereintrag wird das Fehlerprotokoll geschrieben.  
  
4. Der nächste Datensatz wird verarbeitet.  
  
Da der Datensatz als verarbeitet markiert ist, wird kein zukünftiger Versuch gemacht, den Datensatz zu synchronisieren bis der Wert oder das Schema geändert wird. (Beachten Sie, dass auch das Schreiben von identischen Werten in eine Entitätsinstanz als Änderung gilt.)  
  
Die Einträge im Fehlerprotokoll sind schreibgeschützt. Zukünftige Erfolge oder Fehler während der Synchronisierung im gleichen Datensatz bedeuten führen nicht zur Ändern von alten Einträgen für diesen Datensatz. Beispielsweise bleibt ein Fehlereintrag im Fehlerprotokoll, selbst wenn der Datensatz erfolgreich während eines späteren Synchronisierungszyklus synchronisiert wurde.  
  
> [!CAUTION]
>  Diese Fehlerablauflogik kann sich in zukünftigen Versionen des Dienstes ändern.  
  
Diese Fehlereinträge können über die Anforderung [Rufen Sie die für gegebenes Fehlerdetails ein Profil ab](https://discovery.crmreplication.azure.net/swagger/ui/index) abgerufen werden. Die Antwort gibt eine URI für einen Azure-Blob zurück, der Fehlerinformationen enthält.  Jede Zeile umfasst die folgenden Felder durch Kommas getrennten Felder (Zeilenumbrüche aus Gründen der Übersichtlichkeit hinzugefügt):  
  
```  
  
Entity: <entity-name>,   
RecordId: <”N/A” | guid>,   
NotificationTime: <datetime>,   
ChangeType: <sync-type>,  
FailureReason: <description>  
  
```  
  
Beispiel:  
  
```  
  
Entity: lead,   
RecordId: N/A, NotificationTime: , ChangeType: Trigger Initial Export, FailureReason: There is already an object named 'hatest201_lead' in the database.  
Entity: account, RecordId: b2a19cdd-88df-e311-b8e5-6c3be5a8b200, NotificationTime: 8/31/2016 6:50:38 PM, ChangeType: New, FailureReason: Invalid object name 'dbo.hatest201_account'.  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Ihre Daten in Dynamics 365 verwalten](/dynamics365/customer-engagement/developer/manage-data)   
 [Importieren von Daten](import-data.md)
