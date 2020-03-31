---
title: Erstellen einer Canvas-App aus der Azure SQL-Datenbank | Microsoft-Dokumentation
description: Beschreibt, wie Sie eine Canvas-App aus Ihren Daten in Azure SQL-Datenbank erstellen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/30/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c17fff957091a13e26e4bbbb3bc90f34fa5659f7
ms.sourcegitcommit: 204d73f30be2fd63e13e3c64cbfa62b8d667df33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2020
ms.locfileid: "80406092"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>Vorschau: Erstellen einer Canvas-App aus einer Azure SQL-Datenbank

[Dieser Artikel ist Teil der Vorabversion der Dokumentation. Änderungen sind vorbehalten.]

In diesem Thema verwenden Sie Daten in ihrer Azure SQL-Datenbank, um innerhalb weniger Minuten eine APP mit powerapps zu erstellen. Sie verfügen über eine voll funktionsfähige App mit Ihren Daten, die Sie anpassen können, um Ihre geschäftlichen Anforderungen zu erfüllen und auf jedem Gerät zu teilen.

> [!IMPORTANT]
> - Dies ist ein Vorschaufeature.
> - Eine Previewfunktion kann eine eingeschränkte Verfügbarkeit und Funktionalität aufweisen. Eine Previewfunktion ist vor einem offiziellen Release verfügbar, damit Kunden frühzeitig Zugriff erhalten und Feedback geben können.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Für Ihren Browser müssen Popups aktiviert sein.
- Sie benötigen ein Azure-Abonnement. </br>Wenn Sie über kein Azure-Abonnement verfügen, [Erstellen Sie ein kostenloses Konto](https://azure.microsoft.com/free/).
- Sie benötigen Zugriff auf eine vorhandene SQL-Datenbank. </br> Wenn Sie nicht über eine vorhandene SQL-Datenbank verfügen, [Erstellen Sie eine neue Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal).
- Sie müssen in den Firewalleinstellungen für die [IP-Adressen der Azure-Region oder Azure-Dienste](#app-access-to-sql-database) den Zugriff auf SQL-Datenbank zulassen.
- Die SQL-Datenbanktabelle muss mindestens eine Spalte mit dem Text-Datentyp aufweisen.

## <a name="create-an-app-from-azure-portal"></a>Erstellen einer App aus Azure-Portal

> [!TIP]
> Sie können auch eine APP erstellen, die Azure SQL-Datenbank aus [Power apps](https://make.powerapps.com)verwendet. Weitere Informationen finden Sie unter [SQL Server Connector für Power apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase).

1. Melden Sie sich bei [Azure-Portal](https://portal.azure.com)an.
2. Navigieren Sie zu Ihrer SQL-Datenbank.
3. Wählen Sie powerapps aus.
    
    ![Option "Power Apps" in den SQL-Daten Bankoptionen](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "Option "Power Apps" in der SQL-Datenbank")

4. Geben Sie einen Namen für die APP ein, z. b. "Website Überprüfung", "Spenden" oder "Budget Protokollierung".

5. Geben Sie ein SQL-Authentifizierungs Kennwort ein, und ändern Sie ggf. den Benutzernamen
    
    > [!NOTE]
    > Wenn Sie Azure AD integrierte Authentifizierung anstelle der SQL-Authentifizierung mit Azure SQL-Datenbank verwenden möchten, erstellen Sie stattdessen eine APP aus [Power apps](https://make.powerapps.com) , und verwenden Sie [SQL Server Connector](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase).

6. Wählen Sie eine Tabelle aus der Dropdown Liste aus, die Sie zum Erstellen der App verwenden möchten.

7. Wählen Sie **Erstellen** aus.


    ![Geben Sie die Informationen für Ihre APP an.](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "Geben Sie die Informationen für Ihre APP an.")

    [Powerapps Studio](https://create.powerapps.com/studio/) wird auf einer neuen Registerkarte geöffnet. Wenn das Popup blockiert ist, aktualisieren Sie den Browser, um Popups zuzulassen, und versuchen Sie es noch mal. Nach der Erstellung verfügen Sie über eine dreiseitige App mit Daten aus der SQL-Datenbank.

## <a name="accessing-your-app"></a>Zugreifen auf Ihre APP

Wenn Sie erneut auf die erstellte App zugreifen möchten, wechseln Sie zu [make.powerapps.com](https://make.powerapps.com).

## <a name="app-environment-and-region"></a>App-Umgebung und-Region

Die APP, die Sie mit dieser Methode erstellen, verwendet die [Standardumgebung](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment) für den Mandanten und wird in der Region dieser Umgebung bereitgestellt. Sie können den Bereich einer bereitgestellten APP oder der Standardumgebung Ihres Mandanten über das [Admin Center](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed)ermitteln. Wenn Sie alle apps in einer bestimmten Umgebung überprüfen möchten, wechseln Sie zu [make.powerapps.com](https://make.powerapps.com), wählen Sie im Menüband die **Umgebung** aus, und klicken Sie dann auf der linken Seite auf **apps** .

## <a name="app-access-to-sql-database"></a>App-Zugriff auf SQL-Datenbank

Sie können powerapps so konfigurieren, dass eine Verbindung mit SQL-Datenbank mithilfe von IP-Adressen oder als Azure-Dienst hergestellt wird.

### <a name="app-access-using-ip-address"></a>App-Zugriff mithilfe der IP-Adresse

In den [powerapps-Systemanforderungen](limits-and-config.md#ip-addresses) sind die IP-Adressen aufgeführt, die von Power apps abhängig von der Region der APP verwendet werden.

Sie können entweder eine gespeicherte Transact-SQL-Prozedur oder die-Azure-Portal verwenden, um diesen Zugriff zu konfigurieren:

- [Sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current) gespeicherter Prozeduren für SQL-Datenbank oder SQL Server Firewallregeln
- [Azure-Portal](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure) für SQL Server Firewallregeln

### <a name="app-access-as-an-azure-service"></a>App-Zugriff als Azure-Dienst

Power Apps können mithilfe der Azure-Portal eine Verbindung mit der SQL-Datenbank ermöglichen, den **Zugriff auf die Azure-Dienste zu ermöglichen** . Um diesen Zugriff zu konfigurieren, melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und navigieren Sie im Portal zu **SQL Server**. Wählen Sie **Firewalls und virtuelle Netzwerke** **aus**, und legen Sie das Steuerelement die Option **Azure-Dienste und-Ressourcen für den Zugriff auf diesen Server erlauben** Wählen Sie **Speichern** , um Änderungen zu übermitteln.

> [!IMPORTANT]
> Wenn Sie das Steuerelement auf ON festgelegt lassen, akzeptiert der Azure SQL-Datenbankserver die Kommunikation von jedem Subnetz innerhalb der Azure-Grenze, das von einer der IP-Adressen stammt, die als solche innerhalb der für Azure-Rechenzentren definierten Bereiche erkannt werden. Wenn das Steuerelement auf ON festgelegt ist, kann der Zugriff auf die Sicherheitsperspektive übermäßig hoch sein.

## <a name="limitations"></a>Einschränkungen

- Der App-Name darf nur Buchstaben, Ziffern, Bindestriche, Klammern oder Unterstriche enthalten.
- Zum Erstellen einer App aus Azure-Portal ist die SQL-Authentifizierung erforderlich.
- Beim Erstellen einer Canvas-App aus der Azure-Portal können Sie nur eine Tabelle auswählen. Passen Sie die APP nach der Erstellung der APP an, wenn Sie weitere Tabellen und andere Datenquellen hinzufügen möchten, indem Sie weitere Datenverbindungen hinzufügen.
- Power Apps können keine Verbindung mit der SQL-Datenbank mithilfe von vnet-Dienst Endpunkten herstellen. Weitere Informationen finden Sie unter [Zulassen des Zugriffs über vnet-Dienst Endpunkte](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview).

## <a name="other-considerations"></a>Andere Aspekte

- Der Zugriff der APP auf die SQL-Datenbank wird implizit für alle Benutzer freigegeben, für die Sie [diese APP freigeben](share-app.md) . Stellen Sie sicher, dass die Anmelde Informationen für die SQL-Authentifizierung den entsprechenden Zugriff zum Lesen und schreiben </br> Beispielsweise können Sie eine separate app erstellen, die eine Verbindung mit derselben SQL-Datenbank mit verschiedenen Anmelde Informationen für die SQL-Authentifizierung herstellt, um Lese-und Lese-/Schreibzugriff zu trennen.
- Überprüfen Sie Drosselungs Limits, delegatbare Funktionen und Vorgänge, bekannte Probleme und Einschränkungen des [SQL-Datenbankverbindungs](https://docs.microsoft.com/connectors/sql/) -Connector, der von dieser Funktion zur Leistungsüberprüfung verwendet wird.
- Erstellen Sie eine APP aus [make.powerapps.com](https://make.powerapps.com) , wenn Sie eine APP für eine nicht standardmäßige Umgebung und eine andere Region für den Mandanten mit Daten aus der SQL-Datenbank erstellen müssen.

## <a name="next-steps"></a>Nächste Schritte

Im nächsten Schritt verwenden Sie [powerapps](https://make.powerapps.com) Studio, um die APP anzupassen, indem Sie zusätzliche Steuerelemente, Bilder und Logik hinzufügen, um Ihre geschäftlichen Anforderungen besser zu erfüllen.

> [!div class="nextstepaction"]
> [Entwerfen der Canvas-App-Schnittstelle in Power apps](add-configure-controls.md)

## <a name="see-also"></a>Siehe auch

- [Freigeben einer Canvas-app in Power apps](share-app.md) </br>
- [Hinzufügen einer Datenverbindung zu einer Canvas-app in Power apps](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: Anpassen einer Canvas-app in Power apps](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
