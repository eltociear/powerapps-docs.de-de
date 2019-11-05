---
title: Erstellen einer Canvas-App aus der Azure SQL-Datenbank | Microsoft-Dokumentation
description: Beschreibt, wie Sie eine Canvas-App aus Ihren Daten in Azure SQL-Datenbank erstellen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/29/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 652c8d5c67a9f7245ed40be23cc827354d9b1e42
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540874"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>Vorschau: Erstellen einer Canvas-App aus einer Azure SQL-Datenbank

[Dieses Thema ist Teil der Vorabdokumentation und unterliegt Änderungen.]

In diesem Thema verwenden Sie Daten in ihrer Azure SQL-Datenbank, um innerhalb weniger Minuten eine APP mit powerapps zu erstellen. Sie verfügen über eine voll funktionsfähige App mit Ihren Daten, die Sie anpassen können, um Ihre geschäftlichen Anforderungen zu erfüllen und auf jedem Gerät zu teilen.

> [!IMPORTANT]
> - Dies ist ein Vorschau Feature.
> - Ein Vorschau Feature weist möglicherweise eingeschränkte Verfügbarkeit und eingeschränkte Funktionen auf. Vor einer offiziellen Version ist ein Vorschau Feature verfügbar, damit Kunden frühzeitig Zugriff erhalten und Feedback geben können.

## <a name="prerequisites"></a>Voraussetzungen

- Für Ihren Browser müssen Popups aktiviert sein.
- Sie benötigen ein Azure-Abonnement. </br>Wenn Sie über kein Azure-Abonnement verfügen, [Erstellen Sie ein kostenloses Konto](https://azure.microsoft.com/free/).
- Sie benötigen Zugriff auf eine vorhandene SQL-Datenbank. </br> Wenn Sie nicht über eine vorhandene SQL-Datenbank verfügen, [Erstellen Sie eine neue Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal).
- Sie müssen in den Firewalleinstellungen powerapps [-Regions-IP-Adressen oder Azure-Dienste](#app-access-to-sql-database) Zugriff auf SQL-Datenbank gewähren.
- Die SQL-Datenbanktabelle muss mindestens eine Spalte mit dem Text-Datentyp aufweisen.
- Sie benötigen eine gültige powerapps-Lizenz, oder registrieren Sie sich für eine [30-tägige Testlizenz](../signup-for-powerapps.md).

## <a name="create-an-app"></a>Erstellen einer App

1. Anmelden beim [Azure-Portal](https://portal.azure.com).
2. Navigieren Sie zu Ihrer SQL-Datenbank.
3. Wählen Sie powerapps aus.

    
    ![Powerapps-Option in den SQL-Daten Bankoptionen](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "Powerapps-Option in der SQL-Datenbank")

    > [!NOTE]
    > Wenn Sie nicht über eine powerapps-Lizenz verfügen, wird eine blaue Informationsleiste mit einem Link zum Starten einer Testversion angezeigt. Wenn Sie eine Testversion starten, gelangen Sie zu einer neuen Registerkarte, auf der Sie sich für eine Lizenz registrieren. Wechseln Sie nach Abschluss des Vorgangs zurück zum Azure-Portal, und aktualisieren Sie das Blatt, um den Vorgang fortzusetzen.

4. Geben Sie einen Namen für die APP ein, z. b. "Website Überprüfung", "Spenden" oder "Budget Protokollierung".

5. Geben Sie ein SQL-Authentifizierungs Kennwort ein, und ändern Sie ggf. den Benutzernamen
6. Wählen Sie eine Tabelle aus der Dropdown Liste aus, die Sie zum Erstellen der App verwenden möchten.

7. Wählen Sie die Option **Erstellen**.


    ![Geben Sie die Informationen für Ihre APP an.](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "Geben Sie die Informationen für Ihre APP an.")

    Der [PowerApps Studio](https://create.powerapps.com/studio/) wird auf einer neuen Registerkarte geöffnet. Wenn das Popup blockiert ist, aktualisieren Sie den Browser, um Popups zuzulassen, und versuchen Sie es noch mal. Nach der Erstellung verfügen Sie über eine dreiseitige App mit Daten aus der SQL-Datenbank.

## <a name="accessing-your-app"></a>Zugreifen auf Ihre APP

Wenn Sie erneut auf die erstellte App zugreifen möchten, wechseln Sie zu [make.powerapps.com](https://make.powerapps.com).

## <a name="app-environment-and-region"></a>App-Umgebung und-Region

Die APP, die Sie mit dieser Methode erstellen, verwendet die [Standardumgebung](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment) für den Mandanten und wird in der Region dieser Umgebung bereitgestellt. Sie können den Bereich einer bereitgestellten APP oder der Standardumgebung Ihres Mandanten über das [Admin Center](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed)ermitteln. Wenn Sie alle apps in einer bestimmten Umgebung überprüfen möchten, wechseln Sie zu [make.powerapps.com](https://make.powerapps.com), wählen Sie im Menüband die **Umgebung** aus, und klicken Sie dann auf der linken Seite auf **apps** .

## <a name="app-access-to-sql-database"></a>App-Zugriff auf SQL-Datenbank

Sie können powerapps so konfigurieren, dass eine Verbindung mit SQL-Datenbank mithilfe von IP-Adressen oder als Azure-Dienst hergestellt wird.

### <a name="app-access-using-ip-address"></a>App-Zugriff mithilfe der IP-Adresse

[Powerapps-Systemanforderungen](limits-and-config.md#ip-addresses) listet die IP-Adressen auf, die von powerapps abhängig von der Region der APP verwendet werden.

Sie können entweder eine gespeicherte Transact-SQL-Prozedur oder die-Azure-Portal verwenden, um diesen Zugriff zu konfigurieren:

- Gespeicherte Prozedur [sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current) für SQL-Datenbank oder SQL Server Firewallregeln
- [Azure-Portal](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure) für SQL Server Firewallregeln

### <a name="app-access-as-an-azure-service"></a>App-Zugriff als Azure-Dienst

Powerapps kann mithilfe der Azure-Portal eine Verbindung mit der SQL-Datenbank ermöglichen, den **Zugriff auf die Azure-Dienste zu ermöglichen** . Um diesen Zugriff zu konfigurieren, melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und navigieren Sie im Portal zu **SQL Server**. Wählen Sie **Firewalls und virtuelle Netzwerke** **aus**, und legen Sie das Steuerelement die Option **Azure-Dienste und-Ressourcen für den Zugriff auf diesen Server erlauben** Wählen Sie **Speichern** , um Änderungen zu übermitteln.

> [!IMPORTANT]
> Wenn Sie das Steuerelement auf ON festgelegt lassen, akzeptiert der Azure SQL-Datenbankserver die Kommunikation von jedem Subnetz innerhalb der Azure-Grenze, das von einer der IP-Adressen stammt, die als solche innerhalb der für Azure-Rechenzentren definierten Bereiche erkannt werden. Wenn das Steuerelement auf ON festgelegt ist, kann der Zugriff auf die Sicherheitsperspektive übermäßig hoch sein.

## <a name="limitations"></a>Einschränken

- Der App-Name darf nur Buchstaben, Ziffern, Bindestriche, Klammern oder Unterstriche enthalten.
- Powerapps erfordert die SQL-Authentifizierung, um eine Verbindung mit SQL-Datenbank herzustellen
- Beim Erstellen einer Canvas-App aus der Azure-Portal können Sie nur eine Tabelle auswählen. Passen Sie die APP nach der Erstellung der APP an, wenn Sie weitere Tabellen und andere Datenquellen hinzufügen möchten, indem Sie weitere Datenverbindungen hinzufügen.
- Powerapps kann keine Verbindung mit der SQL-Datenbank mithilfe von vnet-Dienst Endpunkten herstellen. Weitere Informationen finden Sie unter [Zulassen des Zugriffs über vnet-Dienst Endpunkte](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview).

## <a name="other-considerations"></a>Weitere Überlegungen

- Der Zugriff der APP auf die SQL-Datenbank wird implizit für alle Benutzer freigegeben, für die Sie [diese APP freigeben](share-app.md) . Stellen Sie sicher, dass die Anmelde Informationen für die SQL-Authentifizierung den entsprechenden Zugriff zum Lesen und schreiben </br> Beispielsweise können Sie eine separate app erstellen, die eine Verbindung mit derselben SQL-Datenbank mit verschiedenen Anmelde Informationen für die SQL-Authentifizierung herstellt, um Lese-und Lese-/Schreibzugriff zu trennen.
- Überprüfen Sie Drosselungs Limits, delegatbare Funktionen und Vorgänge, bekannte Probleme und Einschränkungen des [SQL-Datenbankverbindungs](https://docs.microsoft.com/connectors/sql/) -Connector, der von dieser Funktion zur Leistungsüberprüfung verwendet wird.
- Erstellen Sie eine APP aus [make.powerapps.com](https://make.powerapps.com) , wenn Sie eine APP für eine nicht standardmäßige Umgebung und eine andere Region für den Mandanten mit Daten aus der SQL-Datenbank erstellen müssen.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung haben Sie mithilfe der Azure-Portal eine App mithilfe von Daten aus der SQL-Datenbank erstellt. Im nächsten Schritt passen Sie die APP mit Steuerelementen, Bildern und Logik an, um Ihre geschäftlichen Anforderungen besser zu erfüllen.

> [!div class="nextstepaction"]
> [Entwerfen der Canvas-App-Schnittstelle in powerapps](add-configure-controls.md)

## <a name="see-also"></a>Siehe auch

- [Freigeben einer Canvas-app in powerapps](share-app.md) </br>
- [Hinzufügen einer Datenverbindung zu einer Canvas-app in powerapps](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: Anpassen einer Canvas-app in powerapps](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
