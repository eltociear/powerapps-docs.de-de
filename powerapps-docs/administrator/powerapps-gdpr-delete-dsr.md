---
title: Reagieren auf DSR-Anforderungen (Data Subject Rights, Rechte betroffener Personen) zum Löschen von Kundendaten | Microsoft-Dokumentation
description: Hier finden Sie eine exemplarische Vorgehensweise zum Reagieren auf DSR-Anforderungen (Data Subject Rights, Rechte betroffener Personen) zum Löschen von PowerApps-Kundendaten.
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 495d9976b1daa6e7adb20d97c0840b3a1ba90c4b
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34552689"
---
# <a name="responding-to-data-subject-rights-dsr-requests-to-delete-powerapps-customer-data"></a>Reagieren auf DSR-Anforderungen (Data Subject Rights, Rechte betroffener Personen) zum Löschen von PowerApps-Kundendaten

Das „Recht auf Löschung“ von personenbezogenen Daten aus den Kundendaten einer Organisation ist ein Kernpunkt der Schutzbestimmungen der Datenschutz-Grundverordnung (DSGVO) der Europäischen Union (EU). Das Entfernen personenbezogener Daten beinhaltet das Entfernen der vom System generierten Protokolle, jedoch nicht der Informationen aus Überwachungsprotokollen.

Mit PowerApps können Benutzer Branchenanwendungen erstellen, die ein wichtiger Bestandteil des täglichen Betriebs Ihrer Organisation sind. Wenn ein Benutzer Ihre Organisation verlässt, müssen Sie manuell überprüfen und bestimmen, ob bestimmte, vom Benutzer erstellte Daten und Ressourcen gelöscht werden sollen. Andere personenbezogene Daten werden automatisch gelöscht, sobald das Konto des Benutzers aus Azure Active Directory gelöscht wird.

Im Folgenden finden Sie eine Aufteilung der personenbezogenen Daten, die automatisch gelöscht werden, und der Daten, die manuell überprüft und gelöscht werden müssen:

Macht manuelles Überprüfen und Löschen erforderlich |   Wird automatisch gelöscht, wenn der Benutzer aus Azure Active Directory gelöscht wird.
--- | ---
Umgebung\** | Gateway
Umgebungsberechtigungen\*** | Gatewayberechtigungen
Canvas-App\** | PowerApps-Benachrichtigungen
Berechtigungen für die Canvas-App | PowerApps-Benutzereinstellungen
Verbindung\** | PowerApps-Benutzeranwendungseinstellungen
Verbindungsberechtigungen |
Benutzerdefinierter Connector\** |
Berechtigungen für benutzerdefinierte Connectors |  

\** Jede dieser Ressourcen enthält Datensätze des Typs „Erstellt von“ und „Geändert von“, die personenbezogene Daten enthalten. Aus Sicherheitsgründen werden diese Datensätze so lange aufbewahrt, bis die Ressource gelöscht wird.

\*** Bei Umgebungen, die über eine CDS für Apps-Datenbank (CDS = Common Data Service) verfügen, werden Umgebungsberechtigungen (d.h., welchen Benutzern die Rolle „Umgebungsersteller“ und die Rolle „Administrator“ zugewiesen ist) als Datensätze in dieser Datenbank gespeichert. Anweisungen zum Reagieren auf DSR-Anforderungen für Benutzer von CDS für Apps finden Sie unter [Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps](common-data-service-gdpr-dsr-guide.md).

Für die Daten und Ressourcen, die manuell überprüft werden müssen, bietet PowerApps folgende Möglichkeiten für die Neuzuweisung (falls erforderlich) oder Löschung der personenbezogenen Daten eines bestimmen Benutzers:

* Websitezugriff: [PowerApps-Website](https://web.powerapps.com), [PowerApps Admin Center](https://admin.powerapps.com/) und [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/)

* PowerShell-Zugriff: PowerApps-Cmdlets für [App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) und [Administratoren](https://go.microsoft.com/fwlink/?linkid=871804) sowie Cmdlets für [lokale Gateways](https://go.microsoft.com/fwlink/?linkid=872238).

Im Folgenden finden Sie eine Aufteilung der Möglichkeiten, die zum Löschen der einzelnen Ressourcentypen verfügbar sind, die personenbezogene Daten enthalten können:

Ressourcen mit personenbezogenen Daten | Websitezugriff | PowerShell-Zugriff
--- | --- | ---
Umgebung | PowerApps Admin Center |  PowerApps-Cmdlets
Umgebungsberechtigungen**   | PowerApps Admin Center | PowerApps-Cmdlets
Canvas-App  | PowerApps Admin Center <br> PowerApps| PowerApps-Cmdlets
Berechtigungen für Canvas-Apps  | PowerApps Admin Center | PowerApps-Cmdlets
Verbindung | | App-Ersteller: Verfügbar <br> Administrator: Verfügbar
Verbindungsberechtigungen | | App-Ersteller: Verfügbar <br> Administrator: Verfügbar
Benutzerdefinierter Connector | | App-Ersteller: Verfügbar <br> Administrator: Verfügbar
Berechtigungen für benutzerdefinierte Connectors | | App-Ersteller: Verfügbar <br> Administrator: Verfügbar

\** Mit der Einführung des CDS für Apps werden bei Erstellung einer Datenbank innerhalb der Umgebung Umgebungsberechtigungen und modellgesteuerte App-Berechtigungen als Datensätze in dieser Datenbankinstanz gespeichert. Anweisungen zum Reagieren auf DSR-Anforderungen für Benutzer von CDS für Apps finden Sie unter [Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps](common-data-service-gdpr-dsr-guide.md).

## <a name="prerequisites"></a>Voraussetzungen

### <a name="for-users"></a>Für Benutzer
Alle Benutzer, die über eine gültige PowerApps-Lizenz verfügen, können die in diesem Dokument beschriebenen Vorgänge über [PowerApps](https://web.powerapps.com) oder [PowerShell-Cmdlets für App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) durchführen.

#### <a name="unmanaged-tenant"></a>Nicht verwalteter Mandant
Wenn Sie Mitglied eines [nicht verwalteten Mandanten](https://docs.microsoft.com/azure/active-directory/domains-admin-takeover) sind, also Ihr Azure AD-Mandant nicht über globale Administratorberechtigungen verfügt, können Sie trotzdem die in diesem Artikel aufgeführten Schritte ausführen, um Ihre eigenen personenbezogenen Daten zu entfernen.  Da es allerdings keinen globalen Administrator für Ihren Mandanten gibt, müssen Sie die nachfolgend unter [Schritt 11: Löschen des Benutzers aus Azure Active Directory](#step-11-delete-the-user-from-azure-active-directory) beschriebenen Anweisungen ausführen, um Ihr eigenes Konto aus dem Mandanten zu entfernen.

Wenn Sie überprüfen möchten, ob Sie Mitglied eines nicht verwalteten Mandanten sind, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die folgende URL in einem Browser. Fügen Sie dabei Ihre E-Mail-Adresse in die URL ein: https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1

2. Wenn Sie Mitglied eines **nicht verwalteten Mandanten** sind, wird der Wert `"IsViral": true` in der Antwort angezeigt.
```
{
  ...
  "Login": "foobar@unmanagedcontoso.com",
  "DomainName": "unmanagedcontoso.com",
  "IsViral": true,
  ...
}
```

3. Wenn dies nichts der Fall ist, sind Sie Teil eines **verwalteten Mandanten**.

### <a name="for-administrators"></a>Für Administratoren
Für die Durchführung der in diesem Dokument beschriebenen Verwaltungsvorgänge über das [PowerApps Admin Center](https://admin.powerapps.com/), das Microsoft Flow Admin Center oder die [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) benötigen Sie folgendes:

* eine kostenpflichtige PowerApps Plan 2-Lizenz oder eine PowerApps Plan 2-Testlizenz. Sie können sich unter [http://web.powerapps.com/trial](http://web.powerapps.com/trial) für eine 30-tägige Testlizenz registrieren. Testlizenzen können verlängert werden, wenn sie abgelaufen sind.

* Die Berechtigungen [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), wenn Sie die Ressourcen eines anderen Benutzers durchsuchen müssen. (Beachten Sie, das Umgebungsadministratoren nur Zugriff auf die Umgebungen und Umgebungsressourcen haben, für die sie über die Berechtigungen verfügen.)

## <a name="step-1-delete-or-reassign-all-environments-created-by-the-user"></a>Schritt 1: Löschen oder Neuzuweisen sämtlicher vom Benutzer erstellten Umgebungen
Als Administrator müssen Sie bei der Verarbeitung einer DSR-Löschanforderung für die einzelnen vom Benutzer erstellten Umgebungen zwei Entscheidungen treffen:

1. Wenn Sie feststellen, dass die Umgebung von keiner anderen Person Ihrer Organisation verwendet wird, können Sie die Umgebung löschen.

2. Wenn Sie feststellen, dass die Umgebung noch benötigt wird, können Sie entscheiden, die Umgebung nicht zu löschen, und sich selbst (oder einen anderen Benutzer in Ihrer Organisation) als Umgebungsadministrator hinzufügen.

> [!IMPORTANT]
> Durch das Löschen einer Umgebung werden sämtliche Ressourcen innerhalb der Umgebung (einschließlich Apps, Flows, Verbindungen usw.) unwiderruflich gelöscht. Daher sollten Sie die Inhalte einer Umgebung überprüfen, bevor Sie diese löschen.

### <a name="give-access-to-a-users-environments-from-the-powerapps-admin-center"></a>Erteilen von Zugriff auf Benutzerumgebungen über das PowerApps Admin Center
Ein Administrator kann Administratorzugriff auf eine Umgebung erteilen, die über das [PowerApps Admin Center](https://admin.powerapps.com/) von einem Benutzer erstellt wurde, indem er die folgenden Schritte ausführt:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Wenn die Umgebung von dem Benutzer über die DSR-Anforderung erstellt wurde, wählen Sie **Sicherheit** aus, und fahren Sie mit den unter [Administer environments](environments-administration.md) (Umgebungen verwalten) beschriebenen Schritten fort, um sich selbst oder einem Benutzer in Ihrer Organisation Administratorberechtigungen zu erteilen.

    ![Umgebungssicherheit](./media/powerapps-gdpr-delete-dsr/share-environment.png)

### <a name="delete-environments-created-by-a-user-from-the-powerapps-admin-center"></a>Löschen der vom Benutzer erstellten Umgebungen über das PowerApps Admin Center
Ein Administrator kann Umgebungen überprüfen und löschen, die über das [PowerApps Admin Center](https://admin.powerapps.com/) von einem bestimmten Benutzer erstellt wurden, indem er die folgenden Schritte ausführt:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Wenn die Umgebung von dem Benutzer über die DSR-Anforderung erstellt wurde, wählen Sie **Löschen** aus, und fahren Sie mit den Schritten zum Löschen der Umgebung fort:

    ![Löschen der Umgebung](./media/powerapps-gdpr-delete-dsr/delete-environment.png)

### <a name="give-access-to-a-users-environments-using-powershell"></a>Erteilen von Zugriff auf die Umgebungen eines Benutzers mithilfe von PowerShell
Ein Administrator kann sich selbst (oder einem anderen Benutzer in seiner Organisation) Zugriff auf sämtliche Umgebungen erteilen, die ein Benutzer über die Funktion **Set-AdminEnvironmentRoleAssignment** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) erstellt hat:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$myUserId = $global:currentSession.UserId

#Assign yourself as an admin to each environment created by the user
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Set-AdminEnvironmentRoleAssignment -RoleName EnvironmentAdmin -PrincipalType User -PrincipalObjectId $myUserId

#Retrieve the environment role assignments to confirm
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Get-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> Diese Funktion kann nur in Umgebungen ausgeführt werden, die nicht über eine CDS für Apps-Datenbankinstanz verfügen.

### <a name="delete-environments-created-by-a-user-using-powershell"></a>Löschen der von einem Benutzer mithilfe von PowerShell erstellten Umgebungen
 Ein Administrator kann mit der Funktion **Remove-AdminEnvironment** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) sämtliche Umgebungen löschen, die ein Benutzer erstellt hat:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

# Retrieve all environments created by the user and then delete them
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Remove-AdminEnvironment
```

## <a name="step-2-delete-the-users-permissions-to-all-other-environments"></a>Schritt 2: Löschen der Benutzerberechtigungen für sämtliche andere Umgebungen
Benutzern können in einer Umgebung Berechtigungen zugewiesen werden (z.B. Umgebungsadministrator, Umgebungsersteller usw.), die im PowerApps-Dienst als „Rollenzuweisung“ gespeichert werden.
Mit der Einführung des CDS für Apps werden diese „Rollenzuweisungen“ bei Erstellung einer Datenbank innerhalb der Umgebung als Datensätze innerhalb dieser Datenbankinstanz gespeichert.
Weitere Informationen finden Sie unter [Verwalten von Umgebungen](environments-administration.md).

### <a name="for-environments-without-a-cds-for-apps-database"></a>Bei Umgebungen ohne CDS für Apps-Datenbank

#### <a name="powerapps-admin-center"></a>PowerApps Admin Center
Ein Administrator kann die Umgebungsberechtigungen eines Benutzers im [PowerApps Admin Center](https://admin.powerapps.com/) löschen, indem er die folgenden Schritte ausführt:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus.

    Sie müssen ein [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder ein [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) sein, um sämtliche in Ihrer Organisation erstellten Umgebungen überprüfen zu können.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Wählen Sie **Sicherheit** aus.

    Wenn in Ihrer Umgebung keine CDS für Apps-Datenbank vorhanden ist, wird Ihnen der Abschnitt **Umgebungsrollen** angezeigt.

3. Wählen Sie unter **Umgebungsrollen** die Optionen **Umgebungsadministrator** und **Umgebungsersteller** separat aus, und suchen Sie über die Suchleiste nach dem Namen des Benutzers.

    ![Seite „Umgebungsrollen“](./media/powerapps-gdpr-delete-dsr/admin-environment-role-share-page.png)

5.  Wenn der Benutzer auf beide Rollen Zugriff hat, entfernen Sie über die Anzeige **Benutzer** die Berechtigungen, und wählen Sie **Speichern** aus.

#### <a name="powershell"></a>PowerShell
Ein Administrator kann über die Funktion **Remove-AdminEnvironmentRoleAssignment** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) alle Rollenzuweisungen zu Umgebungen für einen Benutzer über sämtliche Umgebungen ohne CDS für Apps-Datenbank löschen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all environment role assignments for the user for environments without a CDS for Apps instance and delete them
Get-AdminEnvironmentRoleAssignment -UserId $deleteDsrUserId | Remove-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> Diese Funktion kann nur in Umgebungen ausgeführt werden, die nicht über eine CDS für Apps-Datenbankinstanz verfügen.

### <a name="for-environments-with-a-cds-for-apps-database"></a>Bei Umgebungen mit CDS für Apps-Datenbank
Mit der Einführung von CDS für Apps werden diese „Rollenzuweisungen“ bei Erstellung einer Datenbank innerhalb der Umgebung als Datensätze innerhalb dieser Datenbankinstanz gespeichert. Informationen zum Entfernen von personenbezogenen Daten aus einer Datenbankinstanz in CDS für Apps finden Sie unter „Entfernen personenbezogener Benutzerdaten in Common Data Service“

## <a name="step-3-delete-or-reassign-all-canvas-apps-owned-by-a-user"></a>Schritt 3: Löschen oder Neuzuweisen sämtlicher Canvas-Apps eines Benutzers

### <a name="reassign-a-users-canvas-apps-using-the-powerapps-admin-powershell-cmdlets"></a>Neuzuweisen der Canvas-Apps eines Benutzers über die PowerShell-Cmdlets für Administratoren in PowerApps
Wenn ein Administrator beschließt, die Canvas-Apps eines Benutzers nicht zu löschen, kann er diese Apps über die Funktion **Set-AdminAppOwner** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) neu zuweisen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$newAppOwnerUserId = "72c272b8-14c3-4f7a-95f7-a76f65c9ccd8"

#find all apps owned by the DSR user and assigns them a new owner
Get-AdminApp -Owner $deleteDsrUserId | Set-AdminAppOwner -AppOwner $newAppOwnerUserId
```

### <a name="delete-a-users-canvas-app-using-the-powerapps-site"></a>Löschen der Canvas-App eines Benutzers über die PowerApps-Website
Ein Benutzer kann eine App über die [PowerApps-Website](https://web.powerapps.com) löschen. Ausführliche Informationen zum Löschen einer App finden Sie unter „Löschen einer App“.

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-center"></a>Löschen der Canvas-App eines Benutzers über das PowerApps Admin Center
Ein Administrator kann über das [PowerApps Admin Center](https://admin.powerapps.com/) von einem Benutzer erstellte Apps löschen, indem er die folgenden Schritte ausführt:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus.

    Sie müssen ein [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder ein [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) sein, um sämtliche in Ihrer Organisation erstellten Umgebungen überprüfen zu können.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Wählen Sie **Ressourcen** > **Apps** aus.

3. Suchen Sie über die Suchleiste nach dem Namen des Benutzers. Dabei werden sämtliche Apps angezeigt, die der Benutzer in dieser Umgebung erstellt hat:

    ![Apps suchen](./media/powerapps-gdpr-delete-dsr/search-apps.png)

4. Wählen Sie bei jeder App des Benutzers die Option **Details** aus:

    ![App-Details auswählen](./media/powerapps-gdpr-delete-dsr/select-app-details.png)

5. Wählen Sie **Löschen** aus, um die einzelnen Apps zu löschen:

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-powershell-cmdlets"></a>Löschen der Canvas-App eines Benutzers über die PowerShell-Cmdlets für Administratoren in PowerApps
Wenn ein Administrator beschließt, sämtliche Canvas-Apps eines Benutzers zu löschen, kann er dies über die Funktion **Remove-AdminApp** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) machen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all apps owned by the DSR user and deletes them
Get-AdminApp -Owner "0ecb1fcc-6782-4e46-a4c4-738c1d3accea" | Remove-AdminApp
```

## <a name="step-4-delete-the-users-permissions-to-canvas-apps"></a>Schritt 4: Löschen der Benutzerberechtigungen für Canvas-Apps
Sobald eine App für einen Benutzer freigegeben wird, speichert PowerApps einen Datensatz mit dem Namen „Rollenzuweisung“, der die Benutzerberechtigungen („CanEdit“ oder „CanUser“) für die Anwendung beschreibt. Weitere Informationen finden Sie im Artikel „Freigeben von Apps“.

> [!NOTE]
> Beim Löschen der App werden die Rollenzuweisungen einer App gelöscht.

> [!NOTE]
> Die Rollenzuweisung des App-Besitzers kann nur gelöscht werden, indem ein neuer Besitzer für die App zugewiesen wird.

### <a name="powerapps-admin-center"></a>PowerApps Admin Center
Ein Administrator kann über das [PowerApps Admin Center](https://admin.powerapps.com/) Rollenzuweisungen zu Apps für einen Benutzer löschen, indem er die folgenden Schritte ausführt:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus.

    Sie müssen ein [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder ein [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) sein, um sämtliche in Ihrer Organisation erstellten Umgebungen überprüfen zu können.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Wählen Sie bei jeder Umgebung **Ressourcen** > **Apps** aus.

3. Wählen Sie bei jeder App in der Umgebung **Freigabe** aus:

    ![App-Freigabe auswählen](./media/powerapps-gdpr-delete-dsr/select-admin-share-nofilter.png)

4. Wenn der Benutzer auf die App Zugriff hat, entfernen Sie über die Anzeige **Freigabe** der App die zugehörigen Berechtigungen, und wählen Sie **Speichern** aus.

    ![Verwaltungsseite „App-Freigabe“](./media/powerapps-gdpr-delete-dsr/admin-share-page.png)

### <a name="powershell-cmdlets-for-admins"></a>PowerShell-Cmdlets für Administratoren
Ein Administrator kann über die Funktion **Remove-AdminAppRoleAssignmnet** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) sämtliche Rollenzuweisungen zu Canvas-Apps eines Benutzers löschen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all app role assignments for the DSR user and deletes them
Get-AdminAppRoleAssignment -UserId $deleteDsrUserId | Remove-AdminAppRoleAssignment
```

## <a name="step-5-delete-connections-created-by-a-user"></a>Schritt 5: Löschen der von einem Benutzer erstellten Verbindungen
Verbindungen werden zusammen mit Connectors verwendet, wenn eine Verbindung mit anderen APIs und SaaS-Systemen hergestellt wird.  Verbindungen umfassen Verweise auf den Benutzer, der diese Verbindungen erstellt hat. Sie können gelöscht werden, um sämtliche Verweise auf den Benutzer zu entfernen.

### <a name="powershell-cmdlets-for-app-creators"></a>PowerShell-Cmdlets für App-Ersteller
Ein Benutzer kann über die Funktion „Remove-Connection“ in den [PowerShell-Cmdlets für App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) sämtliche seiner Verbindungen löschen:

```
Add-PowerAppsAccount

#Retrieves all connections for the calling user and deletes them
Get-Connection | Remove-Connection
```

### <a name="powershell-cmdlets-for-powerapps-administrators"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Ein Administrator kann über die Funktion **Remove-AdminConnection** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) sämtliche Verbindungen eines Benutzers löschen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all connections for the DSR user and deletes them
Get-AdminConnection -CreatedBy $deleteDsrUserId | Remove-AdminConnection
```

## <a name="step-6-delete-the-users-permissions-to-shared-connections"></a>Schritt 6: Löschen der Benutzerberechtigungen für freigegebene Verbindungen

### <a name="powershell-cmdlets-for-app-creators"></a>PowerShell-Cmdlets für App-Ersteller
Ein Benutzer kann über die Funktion „Remove-ConnectionRoleAssignment“ in den [PowerShell-Cmdlets für App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) sämtliche Rollenzuweisungen zu Verbindungen für freigegebene Verbindungen löschen:

```
Add-PowerAppsAccount

#Retrieves all connection role assignments for the calling users and deletes them
Get-ConnectionRoleAssignment | Remove-ConnectionRoleAssignment
```
> [!NOTE]
> Rollenzuweisungen zu Besitzern können nur zusammen mit der Verbindungsressource gelöscht werden.

### <a name="powershell-cmdlets-for-admins"></a>PowerShell-Cmdlets für Administratoren
Ein Administrator kann über die Funktion **Remove-AdminConnectionRoleAssignment** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) alle Rollenzuweisungen eines Benutzers löschen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all connection role assignments for the DSR user and deletes them
Get-AdminConnectionRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectionRoleAssignment
```

## <a name="step-7-delete-custom-connectors-created-by-the-user"></a>Schritt 7: Löschen der benutzerdefinierten, vom Benutzer erstellten Connectors
Benutzerdefinierte Connectors ergänzen die vorhandenen Out-of-Box-Connectors und ermöglichen das Herstellen einer Verbindung mit anderen APIs, SaaS-Systemen und benutzerentwickelten Systemen. Sie sollten den Besitz benutzerdefinierter Connectors an andere Benutzer in der Organisation übertragen oder den benutzerdefinierten Connector löschen.

### <a name="powershell-cmdlets-for-app-creators"></a>PowerShell-Cmdlets für App-Ersteller
Ein Benutzer kann über die Funktion „Remove-Connection“ in den [PowerShell-Cmdlets für App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) sämtliche seiner benutzerdefinierten Connectors löschen:

```
Add-PowerAppsAccount

#Retrieves all custom connectors for the calling user and deletes them
Get-Connector -FilterNonCustomConnectors | Remove-Connector
```

### <a name="powershell-cmdlets-for-admins"></a>PowerShell-Cmdlets für Administratoren
Ein Administrator kann über die Funktion **Remove-AdminConnector** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) alle von einem Benutzer erstellten benutzerdefinierten Connectors löschen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all custom connectors created by the DSR user and deletes them
Get-AdminConnector -CreatedBy $deleteDsrUserId | Remove-AdminConnector
```

## <a name="step-8-delete-the-users-permissions-to-shared-custom-connectors"></a>Schritt 8: Löschen der Benutzerberechtigungen für freigegebene benutzerdefinierte Connectors

### <a name="powershell-cmdlets-for-app-creators"></a>PowerShell-Cmdlets für App-Ersteller
Ein Benutzer kann über die Funktion „Remove-ConnectorRoleAssignment“ in den [PowerShell-Cmdlets für App-Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) sämtliche Rollenzuweisungen zu Connectors für freigegebene benutzerdefinierte Connectors löschen:

```
Add-PowerAppsAccount

#Retrieves all connector role assignments for the calling users and deletes them
Get-ConnectorRoleAssignment | Remove-ConnectorRoleAssignment
```

> [!NOTE]
> Rollenzuweisungen zu Besitzern können nur zusammen mit der Verbindungsressource gelöscht werden.

### <a name="powershell-cmdlets-for-admins"></a>PowerShell-Cmdlets für Administratoren
Ein Administrator kann über die Funktion **Remove-AdminConnectorRoleAssignment** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) alle benutzerdefinierten Rollenzuweisungen von Connectors für einen Benutzer löschen:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#Retrieves all custom connector role assignments for the DSR user and deletes them
Get-AdminConnectorRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectorRoleAssignment
```

## <a name="step-9-delete-the-users-personal-data-in-microsoft-flow"></a>Schritt 9: Löschen der personenbezogenen Benutzerdaten in Microsoft Flow
In PowerApps-Lizenzen sind immer Microsoft Flow-Funktionen enthalten. Microsoft Flow ist nicht nur in PowerApps-Lizenzen enthalten, sondern auch als eigenständiger Dienst. Weitere Informationen zum Reagieren auf DSR-Anforderungen für Benutzer, die den Microsoft Flow-Dienst verwenden, finden Sie unter [Responding to GDPR Data Subject Requests for Microsoft Flow (Reagieren auf DSGVO-Anforderungen betroffener Personen für Microsoft Flow)](https://go.microsoft.com/fwlink/?linkid=872250).

> [!IMPORTANT]
> Es wird empfohlen, dass Administratoren diesen Schritt für PowerApps-Benutzer ausführen.

## <a name="step-10-delete-the-users-personal-data-in-instances-of-cds-for-apps"></a>Schritt 10: Löschen der personenbezogenen Benutzerdaten in CDS für Apps-Instanzen
Über bestimmte PowerApps-Lizenzen, einschließlich des PowerApps-Communityplans, können Benutzer innerhalb Ihrer Organisation CDS-Instanzen für Apps erstellen sowie Apps auf CDS für Apps erstellen und entwickeln. Der PowerApps-Communityplan ist eine kostenlose Lizenz, mit der Benutzer CDS für Apps in einer individuellen Umgebung testen können. Informationen zu den Funktionen der einzelnen PowerApps-Lizenzen finden Sie auf der Seite mit den PowerApps-Preisen.

Anweisungen zum Reagieren auf DSR-Anforderungen für Benutzer von CDS für Apps finden Sie unter [Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps](common-data-service-gdpr-dsr-guide.md).

> [!IMPORTANT]
> Es wird empfohlen, dass Administratoren diesen Schritt für PowerApps-Benutzer ausführen.

## <a name="step-11-delete-the-user-from-azure-active-directory"></a>Schritt 11: Löschen des Benutzers aus Azure Active Directory
Wenn Sie die obenstehend aufgeführten Schritte ausgeführt haben, löschen Sie das Azure Active Directory-Konto für den Benutzer.

### <a name="managed-tenant"></a>Verwalteter Mandant
Als Administrator eines verwalteten Azure AD-Mandanten können Sie das Konto des Benutzers in Azure Active Directory löschen. Führen Sie hierzu die Schritte aus, die im [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRDSR) in der Dokumentation zur DSGVO für Azure-Datensubjektanforderungen erläutert werden.

### <a name="unmanaged-tenant"></a>Nicht verwalteter Mandant
Wenn Sie Mitglied eines nicht verwalteten Mandanten sind, führen Sie die folgenden Schritte aus, um Ihr Konto aus Ihrem Azure AD-Mandanten zu löschen:

> [!NOTE]
> Weitere Informationen zur Vorgehensweise bei der Überprüfung, ob Sie Mitglied eines verwalteten oder eines nicht verwalteten Mandanten sind, finden Sie obenstehend im Abschnitt [Nicht verwalteter Mandant](#unmanaged-tenant).

1. Navigieren Sie zu der Seite [Work and School privacy (Datenschutz für Geschäfts-, Schul- oder Unikonten)](https://go.microsoft.com/fwlink/?linkid=87312), und melden Sie sich mit Ihrem Azure AD-Konto an.

2. Klicken Sie auf **Konto schließen**, und führen Sie die Anweisungen aus, um Ihr Konto aus Ihrem Azure AD-Mandanten zu löschen.

    ![App-Freigabe auswählen](./media/powerapps-gdpr-delete-dsr/close-account.png)
