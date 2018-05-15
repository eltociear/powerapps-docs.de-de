---
title: Reagieren auf DSR-Anforderungen (Data Subject Rights) zum Exportieren von PowerApps-Kundendaten | Microsoft-Dokumentation
description: Exemplarische Vorgehensweise zum Reagieren auf DSR-Anforderungen (Data Subject Rights) zum Exportieren von PowerApps-Kundendaten
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: 97f5a6a970e07f9908c02074ef97234b58a52894
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-to-export-powerapps-customer-data"></a>Reagieren auf DSR-Anforderungen (Data Subject Rights) zum Exportieren von PowerApps-Kundendaten
Das „Recht auf Datenübertragbarkeit“ ermöglicht einer betroffenen Person die Anforderung einer Kopie ihrer personenbezogenen Daten in elektronischem Format (d.h. in einem „strukturierten, häufig verwendeten, maschinenlesbaren und interoperablen Format“), die an einen anderen Verantwortlichen übertragen werden kann:

* Websitezugriff: [PowerApps](https://web.powerapps.com), [PowerApps Admin Center](https://admin.powerapps.com/) und [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/)

* PowerShell-Zugriff: PowerApps-Cmdlets [Cmdlets für Ersteller](https://go.microsoft.com/fwlink/?linkid=871448), [Cmdlets für Administratoren](https://go.microsoft.com/fwlink/?linkid=871804) und [Cmdlets für lokale Gateways](https://go.microsoft.com/fwlink/?linkid=872238)

Es folgt eine Zusammenfassung der Arten von personenbezogenen Daten, die für einen bestimmten Benutzer in PowerApps gespeichert werden können, sowie über die Möglichkeiten zum Suchen und Exportieren dieser Daten.

Ressourcen mit personenbezogenen Daten | Websitezugriff |   PowerShell-Zugriff
--- | --- | --
Umgebung | PowerApps Admin Center |  PowerApps-Cmdlets
Umgebungsberechtigungen**   | PowerApps Admin Center    | PowerApps-Cmdlets
Canvas-App  | PowerApps Admin Center <br> PowerApps-Portal für Ersteller |  PowerApps-Cmdlets
Canvas App-Berechtigungen  | PowerApps Admin Center <br> PowerApps-Portal für Ersteller    | PowerApps-Cmdlets
Gateway | PowerApps-Portal für Ersteller*** | Cmdlets für lokale Gateways
Gatewayberechtigungen | PowerApps-Portal für Ersteller*** |
Benutzerdefinierter Connector | |    Ersteller: Verfügbar <br> Administrator: in der Entwicklung
Berechtigungen für benutzerdefinierte Connectors | |    Ersteller: Verfügbar <br> Administrator: in der Entwicklung
Verbindung | | Ersteller: Verfügbar <br> Administrator: in der Entwicklung
Verbindungsberechtigungen  | | Ersteller: Verfügbar <br> Administrator: in der Entwicklung
PowerApps-Benutzereinstellungen, Benutzeranwendungseinstellungen und Benachrichtigungen | | Ersteller: Verfügbar <br> Administrator: in der Entwicklung

> ** Mit der Einführung von Common Data Service (CDS) für Apps werden bei der Erstellung einer Datenbank innerhalb der Umgebung Umgebungsberechtigungen und modellgesteuerte App-Berechtigungen in der Datenbankinstanz von CDS für Apps als Datensätze gespeichert. Anweisungen zum Reagieren auf DSR-Anforderungen für Benutzer, die CDS für Apps verwenden, finden Sie unter [Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps](common-data-service-gdpr-dsr-guide.md).

> *** Ein Administrator kann nur dann über [PowerApps](https://web.powerapps.com) auf diese Ressourcen zugreifen, wenn der Besitzer der Ressource ihm explizit Zugriff erteilt hat. Wenn der Zugriff nicht vom Administrator gewährt wurde, müssen die [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) verwendet werden.

## <a name="prerequisites"></a>Voraussetzungen

### <a name="for-users"></a>Für Benutzer
Alle Benutzer, die über eine gültige PowerApps-Lizenz verfügen, können die in diesem Dokument beschriebenen Vorgänge mit [PowerApps](https://web.powerapps.com) oder [Cmdlets für Ersteller](https://go.microsoft.com/fwlink/?linkid=871448) durchführen.

### <a name="for-admins"></a>Für Administratoren
Für die Durchführung der in diesem Dokument beschriebenen Verwaltungsvorgänge über das PowerApps Admin Center, das Microsoft Flow Admin Center oder die [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) benötigen Sie das Folgende:

* eine kostenpflichtige PowerApps Plan 2-Lizenz oder eine PowerApps Plan 2-Testlizenz. Sie können sich unter [http://web.powerapps.com/trial](http://web.powerapps.com/trial) für eine 30-tägige Testlizenz registrieren. Testlizenzen können verlängert werden, wenn sie abgelaufen sind.

* Die Berechtigungen [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), wenn Sie die Ressourcen eines anderen Benutzers durchsuchen müssen. (Beachten Sie, das Umgebungsadministratoren nur Zugriff auf die Umgebungen und Umgebungsressourcen haben, für die sie über die Berechtigungen verfügen.)

## <a name="step-1-export-personal-data-contained-within-environments-created-by-the-user"></a>Schritt 1: Exportieren persönlicher Daten, die in vom Benutzer erstellten Umgebungen enthalten sind

### <a name="powerapps-admin-center"></a>PowerApps Admin Center
Administratoren können alle Umgebungen exportieren, die über das [PowerApps Admin Center](https://admin.powerapps.com/) von einem bestimmten Benutzer erstellt wurden, indem sie die folgenden Schritte ausführen:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Wenn der Benutzer die Umgebung über die DSR-Anforderung erstellt hat, wechseln Sie zur Seite **Details**, kopieren Sie die Details, und fügen Sie diese anschließend in einen Dokument-Editor wie z.B. Microsoft Word ein.

    ![Umgebungsdetails](./media/powerapps-gdpr-export-dsr/environment-details.png)

### <a name="powerapps-maker-powershell-cmdlets"></a>PowerShell-Cmdlets für Ersteller in PowerApps
Benutzer können mit der Funktion **Get-PowerAppsEnvironment** in den [PowerShell-Cmdlets für Ersteller in PowerApps](https://go.microsoft.com/fwlink/?linkid=871448) die Umgebungen exportieren, auf die sie in PowerApps Zugriff haben:

~~~~
Add-PowerAppsAccount
Get-PowerAppsEnvironment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Administratoren können über die Funktion **Get-AdminEnvironment** in den [PowerShell-Cmdlets für Ersteller in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) sämtliche von einem Benutzer erstellte Umgebungen exportieren:

~~~~
Add-PowerAppsAccount
$userId = "7557f390-5f70-4c93-8bc4-8c2faabd2ca0"
Get-AdminEnvironment -CreatedBy $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~
 
## <a name="step-2-export-the-users-environment-permissions"></a>Schritt 2: Exportieren der Umgebungsberechtigungen des Benutzers
Benutzern können in einer Umgebung Berechtigungen zugewiesen werden (z.B. Umgebungsadministrator, Umgebungsersteller), die in PowerApps als *Rollenzuweisung* gespeichert werden. Mit der Einführung von CDS für Apps werden die Rollenzuweisungen bei der Erstellung einer Datenbank innerhalb der Umgebung als Datensätze in der Datenbankinstanz von CDS für Apps gespeichert. Weitere Informationen finden Sie unter [Verwalten von Umgebungen in PowerApps ](environments-administration.md).

### <a name="for-environments-without-a-cds-for-apps-database"></a>Bei Umgebungen ohne CDS für Apps-Datenbank

#### <a name="powerapps-admin-center"></a>PowerApps Admin Center
Administratoren können die Berechtigungen für eine Benutzerumgebung über das [PowerApps Admin Center](https://admin.powerapps.com/) exportieren, indem sie die folgenden Schritte ausführen:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus. Sie müssen ein [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder ein [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) sein, um alle in Ihrer Organisation erstellten Umgebungen überprüfen zu können.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Wählen Sie **Sicherheit** aus.

    Wenn in Ihrer Umgebung keine CDS für Apps-Datenbank vorhanden ist, wird Ihnen der Abschnitt **Umgebungsrollen** angezeigt.

3. Wählen Sie **Umgebungsadministrator** und **Umgebungsersteller** separat aus, und suchen Sie anschließend über die Suchleiste nach dem Namen des Benutzers.

    ![Seite „Umgebungsrollen“](./media/powerapps-gdpr-export-dsr/admin-environment-role-share-page.png)

4. Wenn der Benutzer auf beide Rollen Zugriff hat, wechseln Sie zur Seite **Benutzer**, kopieren Sie die Details, und fügen Sie diese anschließend in einen Dokument-Editor wie z.B. Microsoft Word ein.

#### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Administratoren können über die Funktion **Get-AdminEnvironmentRoleAssignment** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) alle Rollenzuweisungen zu Umgebungen für einen Benutzer über sämtliche Umgebungen ohne CDS für Apps-Datenbank exportieren:

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminEnvironmentRoleAssignment -UserId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

> [!IMPORTANT]
>  Diese Funktion kann nur in Umgebungen ausgeführt werden, die nicht über eine CDS für Apps-Datenbankinstanz verfügen.
>
>

### <a name="for-environments-with-a-cds-for-apps-database"></a>Bei Umgebungen mit einer CDS für Apps-Datenbank
Mit der Einführung von CDS für Apps werden Rollenzuweisungen bei Erstellung einer Datenbank innerhalb der Umgebung als Datensätze in der Datenbankinstanz von CDS für Apps gespeichert. Informationen zum Entfernen von personenbezogenen Daten aus einer Datenbankinstanz von CDS für Apps finden Sie unter [Entfernen persönlicher Benutzerdaten aus Common Data Service](https://go.microsoft.com/fwlink/?linkid=871886).
 
## <a name="step-3-export-personal-data-contained-within-canvas-apps-created-by-the-user"></a>Schritt 3: Exportieren personenbezogener Daten, die in dem vom Benutzer erstellten Zeichenbereich enthalten sind

### <a name="powerapps-maker-portal"></a>PowerApps-Portal für Ersteller
Ein Benutzer kann eine App über [PowerApps](https://web.powerapps.com) exportieren. Ausführliche Anweisungen zum Exportieren einer App finden Sie unter [Exportieren einer App](environment-and-tenant-migration.md#exporting-an-app).

### <a name="powerapps-admin-center"></a>PowerApps Admin Center
Administratoren können über das [PowerApps Admin Center](https://admin.powerapps.com/) von einem Benutzer erstellte Apps exportieren, indem sie die folgenden Schritte ausführen:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus. Sie müssen ein [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder ein [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) sein, um alle in Ihrer Organisation erstellten Umgebungen überprüfen zu können.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Wählen Sie **Ressourcen** und anschließend **Apps** aus.

3. Suchen Sie über die Suchleiste nach dem Namen des Benutzers. Dabei werden sämtliche Apps angezeigt, die der Benutzer in dieser Umgebung erstellt hat:

    ![Apps suchen](./media/powerapps-gdpr-export-dsr/search-apps.png)

4. Wählen Sie bei jeder App, die der Benutzer erstellt hat, die Option **Freigabe** aus, und erteilen Sie sich Zugriff für die **Bearbeitung** der App:

    ![App-Freigabe auswählen](./media/powerapps-gdpr-export-dsr/select-share.png)

    ![Benutzer Zugriff erteilen](./media/powerapps-gdpr-export-dsr/grant-access.png)

5. Sobald Sie auf die einzelnen Apps des Benutzers Zugriff haben, können Sie über [PowerApps](https://web.powerapps.com) eine App exportieren. Ausführliche Anweisungen zum Exportieren einer App finden Sie unter [Exportieren einer App](environment-and-tenant-migration.md#exporting-an-app).

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Administratoren können über die Funktion **Get-AdminApp** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) von einem Benutzer erstellte Apps exportieren:

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminApp -Owner $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-4-export-the-users-permissions-to-canvas-apps"></a>Schritt 4: Exportieren der Benutzerberechtigungen für Canvas-Apps
Sobald eine App für einen Benutzer freigegeben wird, speichert PowerApps einen Datensatz mit dem Namen *Rollenzuweisung*, der die Benutzerberechtigungen („CanEdit“ oder „CanUser“) für die Anwendung beschreibt. Weitere Informationen finden Sie unter [Freigeben von Apps](../maker/canvas-apps/share-app.md#share-an-app).

### <a name="powerapps-maker-powershell-cmdlets"></a>PowerShell-Cmdlets für Ersteller in PowerApps
Benutzer können über die Funktion **Get-RoleAssignment** in den [PowerShell-Cmdlets für Ersteller in PowerApps](https://go.microsoft.com/fwlink/?linkid=871448) die Rollenzuweisungen zu Apps für alle Apps exportieren, auf die sie Zugriff haben:

~~~~
Add-PowerAppsAccount
Get-AppRoleAssignment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-center"></a>PowerApps Admin Center
Administratoren können Rollenzuweisungen zu Apps für einen Benutzer über das [PowerApps Admin Center](https://admin.powerapps.com/) exportieren, indem sie die folgenden Schritte ausführen:

1. Wählen Sie über das [PowerApps Admin Center](https://admin.powerapps.com/) die einzelnen Umgebungen in Ihrer Organisation aus. Sie müssen ein [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder ein [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) sein, um alle in Ihrer Organisation erstellten Umgebungen überprüfen zu können.

    ![Landing Page des Admin Center](./media/powerapps-gdpr-export-dsr/admin-center-landing.png)

2. Wählen Sie bei jeder Umgebung **Ressourcen** und anschließend **Apps** aus.

3. Wählen Sie bei jeder App in der Umgebung **Freigabe** aus.

    ![App-Freigabe auswählen](./media/powerapps-gdpr-export-dsr/select-admin-share-nofilter.png)

4. Wenn der Benutzer auf die App Zugriff hat, wechseln Sie zur Seite **Freigabe** der App, kopieren Sie die Details, und fügen Sie diese anschließend in einen Dokument-Editor wie z.B. Microsoft Word ein.

    ![Verwaltungsseite „App-Freigabe“](./media/powerapps-gdpr-export-dsr/admin-share-page.png)

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Administratoren können über die Funktion **Get-AdminAppRoleAssignment** in den [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) alle Rollenzuweisungen zu Apps für einen Benutzer über sämtliche Apps in ihrem Mandanten exportieren:

~~~~
Add-PowerAppsAccount
$userId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
Get-AdminAppRoleAssignment -UserId $userId | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

## <a name="step-5-export-personal-data-contained-within-connections-created-by-the-user"></a>Schritt 5: Exportieren personenbezogener Daten, die in den vom Benutzer erstellten Verbindungen enthalten sind
Verbindungen werden zusammen mit Connectors verwendet, wenn eine Verbindung mit anderen APIs und SaaS-Systemen hergestellt wird. Verbindungen umfassen Verweise auf den Benutzer, der diese Verbindungen erstellt hat. Sie können gelöscht werden, um sämtliche Verweise auf den Benutzer zu entfernen.

### <a name="powerapps-maker-powershell-cmdlets"></a>PowerShell-Cmdlets für Ersteller in PowerApps
Benutzer können mit der Funktion **Get-Connection** in den [PowerShell-Cmdlets für Ersteller in PowerApps](https://go.microsoft.com/fwlink/?linkid=871448) sämtliche Verbindungen exportieren, auf die sie Zugriff haben:

~~~~
Add-PowerAppsAccount
Get-Connection | ConvertTo-Json | out-file -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Die Funktion für einen Administrator zum Exportieren von Verbindungen, die ein Benutzer mithilfe der [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) erstellt hat, befindet sich in der Entwicklung.
 
## <a name="step-6-export-the-users-permissions-to-shared-connections"></a>Schritt 6: Exportieren der Benutzerberechtigungen für freigegebene Verbindungen

### <a name="powerapps-maker-powershell-cmdlets"></a>PowerShell-Cmdlets für Ersteller in PowerApps
Benutzer können über die Funktion **Get-ConnectionRoleAssignment** in den [PowerShell-Cmdlets für Ersteller in PowerApps](https://go.microsoft.com/fwlink/?linkid=871448) die Rollenzuweisungen zu Verbindungen für alle Verbindungen exportieren, auf die sie Zugriff haben:

~~~~
Add-PowerAppsAccount
Get-ConnectionRoleAssignment | ConvertTo-Json | out-file -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Die Funktion für einen Administrator zum Exportieren von Rollenzuweisungen zu Verbindungen für einen Benutzer mithilfe der [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) befindet sich in der Entwicklung.

## <a name="step-7-export-personal-data-contained-within-custom-connectors-created-by-the-user"></a>Schritt 7: Exportieren personenbezogener Daten, die in den vom Benutzer erstellten benutzerdefinierten Connectors enthalten sind
Benutzerdefinierte Connectors ergänzen die vorhandenen Out-of-Box-Connectors und ermöglichen das Herstellen einer Verbindung mit anderen APIs, SaaS-Systemen und benutzerentwickelten Systemen.

### <a name="powerapps-maker-powershell-cmdlets"></a>PowerShell-Cmdlets für Ersteller in PowerApps
Benutzer können über die Funktion **Get-Connector** in den [PowerShell-Cmdlets für Ersteller in PowerApps](https://go.microsoft.com/fwlink/?linkid=871448) sämtliche benutzerdefinierte Connectors exportieren:

~~~~
Add-PowerAppsAccount  
Get-Connector -FilterNonCustomConnectors | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Die Funktion für einen Administrator zum Exportieren benutzerdefinierter Connectors, die ein Benutzer mithilfe der [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) erstellt hat, befindet sich in der Entwicklung.

## <a name="step-8-export-the-users-permissions-to-custom-connectors"></a>Schritt 8: Exportieren der Benutzerberechtigungen für benutzerdefinierte Connectors

### <a name="powerapps-maker-powershell-cmdlets"></a>PowerShell-Cmdlets für Ersteller in PowerApps
Benutzer können über die Funktion **Get-ConnectorRoleAssignment** in den [PowerShell-Cmdlets für Ersteller in PowerApps](https://go.microsoft.com/fwlink/?linkid=871448) sämtliche Rollenzuweisungen zu Connectors für die benutzerdefinierten Connectors exportieren, auf die sie Zugriff haben:

~~~~
Add-PowerAppsAccount  
Get-ConnectorRoleAssignment | ConvertTo-Json | Out-File -FilePath "UserDetails.json"
~~~~

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Die Funktion für einen Administrator zum Exportieren von Rollenzuweisungen zu benutzerdefinierten Connectors für einen Benutzer mithilfe der [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) befindet sich in der Entwicklung.
 
## <a name="step-9-export-powerapps-notifications-user-settings-and-user-app-settings"></a>Schritt 9: Exportieren von PowerApps-Benachrichtigungen, -Benutzereinstellungen und -Benutzeranwendungseinstellungen
PowerApps sendet verschiedene Arten von Benachrichtigungen an Benutzer, z.B. wenn eine App für sie freigegeben wurde oder ein CDS für Apps-Export abgeschlossen wurde. Der Benachrichtigungsverlauf eines Benutzers ist für die Benutzer in [PowerApps](https://web.powerapps.com) sichtbar.

PowerApps speichert zudem verschiedene persönliche Optionen und Einstellungen zur Bereitstellung der PowerApps-Laufzeit und Portalerfahrungen, die beispielsweise beinhalten, wann ein Benutzer eine Anwendung zuletzt geöffnet oder fixiert hat.

### <a name="powerapps-maker-powershell-cmdlets"></a>PowerShell-Cmdlets für Ersteller in PowerApps
Die Funktion zum Exportieren der PowerApps-Benachrichtigungen, -Benutzereinstellungen und -Benutzeranwendungseinstellungen eines Benutzers mithilfe der [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) befindet sich in der Entwicklung.

### <a name="powerapps-admin-powershell-cmdlets"></a>PowerShell-Cmdlets für Administratoren in PowerApps
Die Funktion für einen Administrator zum Exportieren der PowerApps-Benachrichtigungen, -Benutzereinstellungen und -Benutzeranwendungseinstellungen eines Benutzers mithilfe der [PowerShell-Cmdlets für Administratoren in PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) befindet sich in der Entwicklung.

## <a name="step-10-export-personal-data-contained-for-a-user-stored-gateway-or-in-the-users-gateway-permissions"></a>Schritt 10: Exportieren von personenbezogenen Daten, die auf einem vom Benutzer gespeicherten Gateway oder in den Gatewayberechtigungen des Benutzers enthalten sind

### <a name="powerapps-maker-portal"></a>PowerApps-Portal für Ersteller
Benutzer können die personenbezogenen Daten exportieren, die über [PowerApps](https://web.powerapps.com) im Gatewaydienst gespeichert wurden, indem sie die folgenden Schritte ausführen:

1. Wählen Sie in [PowerApps](https://web.powerapps.com) in der Standardumgebung Ihres Mandanten den Eintrag **Gateways** und anschließend **Details** aus, um sämtliche Gateways anzuzeigen, auf die Sie Zugriff haben.

    ![Landing Page des Gateways](./media/powerapps-gdpr-export-dsr/gateway-select-details.png)

2. Wenn die Gatewaydetails personenbezogene Daten enthalten, kopieren Sie diese auf der Seite **Details**, und fügen Sie diese anschließend in einen Dokument-Editor wie z.B. Microsoft Word ein.

    ![Gatewaydetails](./media/powerapps-gdpr-export-dsr/gateway-details-drillin.png)

3. Wählen Sie **Freigabe** aus, kopieren Sie den Inhalt der Seite, und fügen Sie diesen anschließend in einen Dokument-Editor wie z.B. Microsoft Word ein.

    ![Gatewaydetails](./media/powerapps-gdpr-export-dsr/gateway-details-share.png)

### <a name="gateway-powershell-cmdlets"></a>PowerShell-Cmdlets für das Gateway
Es gibt auch PowerShell-Cmdlets, mit denen Sie Ihre persönlichen Gateways abrufen, verwalten und löschen können. Weitere Informationen finden Sie unter [Cmdlets für lokale Gateways](https://go.microsoft.com/fwlink/?linkid=872238).

## <a name="step-11-export-the-users-personal-data-in-microsoft-flow"></a>Schritt 11: Exportieren der personenbezogenen Benutzerdaten in Microsoft Flow
In PowerApps-Lizenzen sind immer Microsoft Flow-Funktionen enthalten. Microsoft Flow ist nicht nur in PowerApps-Lizenzen enthalten, sondern auch als eigenständiger Dienst. Weitere Informationen zum Reagieren auf DSR-Anforderungen für Benutzer, die den Microsoft Flow-Dienst verwenden, finden Sie unter [Responding to GDPR Data Subject Requests for Microsoft Flow (Reagieren auf DSGVO-Anforderungen betroffener Personen für Microsoft Flow)](https://go.microsoft.com/fwlink/?linkid=872250).

> [!IMPORTANT] 
>  Es wird empfohlen, dass Administratoren diese Schritte für PowerApps-Benutzer ausführen.
>
>

## <a name="step-12-export-the-users-personal-data-in-cds-for-apps-instances"></a>Schritt 12: Exportieren der personenbezogenen Benutzerdaten in CDS für Apps-Instanzen
Mit bestimmten PowerApps-Lizenzen können Benutzer innerhalb Ihrer Organisation CDS für Apps-Instanzen erstellen und damit Apps wie den PowerApps-Communityplan entwickeln. Dabei handelt es sich um eine kostenlose Lizenz, mit der Benutzer CDS für Apps in einer individuellen Umgebung austesten können. Informationen darüber, welche Funktionen von CDS für Apps in den einzelnen PowerApps-Lizenzen inbegriffen sind, finden Sie auf der [Seite mit den PowerApps-Preisen](https://powerapps.microsoft.com/pricing).

Anweisungen zum Reagieren auf DSR-Anforderungen für Benutzer, die CDS für Apps verwenden, finden Sie unter [Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps](common-data-service-gdpr-dsr-guide.md).

> [!IMPORTANT]
>  Es wird empfohlen, dass Administratoren diese Schritte für PowerApps-Benutzer ausführen.
>
>