---
title: Bereitstellen eines Portals mit dem früheren Portal-Add-On | Microsoft-Dokumentation
description: Anleitungen zum Bereitstellen eines Portals mit dem früheren Portal-Add-On.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6572a92a46fa308eab6cb46b813a572605327197
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760436"
---
# <a name="provision-a-portal-using-the-older-portal-add-on"></a>Bereitstellen eines Portals mit dem früheren Portal-Add-On

Wenn Sie ein früheres Portal-Add-On erworben haben und ein Portal mit dem Add-On bereitstellen möchten, müssen Sie zur **Dynamics 365 Admin Center**-Seite zurückkehren und das Portal bereitstellen.

> [!NOTE]
> Um ein Portal bereitzustellen, muss Ihnen entweder die Rolle Systemadministrator oder System Anpasser der für das Portal ausgewählten Common Data Service-Umgebung zugewiesen werden. Außerdem müssen Sie über die [erforderlichen Berechtigungen](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions) verfügen, um eine Anwendung in Azure AD zu erstellen und zu registrieren. Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, wenden Sie sich an den globalen Administrator, um Ihre Berechtigungen zu aktualisieren, oder bitten Sie den globalen Administrator, das Portal bereitzustellen.

So stellen Sie ein Portal bereit:

1.  Wechseln Sie zur Seite **Dynamics 365 Administration Center**, und klicken Sie auf die Registerkarte **Anwendungen**.

2.  Wählen Sie die Anwendungszeile mit dem Titel **Portal Add-On** aus und klicken Sie dann auf **Verwalten.**

3.  Im Abschnitt **Allgemeine Einstellungen** geben Sie einen **Name** für Ihr Portal ein. Der **Name** unterstützt Sie dabei, das Portal zu identifizieren, und er kann später geändert werden.

4.  Das Feld **Typ** stellt den Typ des Portalabonnements dar (Testversion oder Produktion). Das ist ein Systemfeld. Deshalb kann es nicht durch den Benutzer geändert werden. Der Wert ändert sich abhängig davon, ob es ein Testabonnement oder ein bezahltes Abonnement ist.

5. Optional in der Dropdownliste **Portalentwicklungsstand**, wählen Sie eine der folgenden Entwicklungsstände für das Portal aus:

    - Prototyp
    - Entwicklung
    - Testen
    - UAT
    - Live

    > [!NOTE]
    > - Bei vorhandenen bereitgestellten Portalen ist diese Dropdownliste auf der Registerkarte **Portaldetails** verfügbar und kein Status ist standardmäßig ausgewählt.
    > - Diese wird nur für die Dropdownliste Portale des Typs Produktion verfügbar.
    > - Das Feld wird von Microsoft verwendet, um ein Verwendungsmuster des Portals zu verstehen und hat keinen Einfluss auf die  Funktionen. Falls Sie unterschiedliche Namen für Entwicklungslebenszyklus verwenden, wählen Sie jenen aus, der besser zum Zweck passt. Dies kann zu einem späteren Zeitpunkt geändert werden, sobald es angegeben wird.

5.  Im Feld **Portal-URL** geben Sie den Namen der Unterdomäne ein, den Sie für das Portal möchten. Sie können nur alphanumerische Zeichen oder Bindestriche (-) verwenden; andere Zeichen sind nicht zulässig.

    > [!NOTE]
    > - Um die URL des Portals ändern nachdem Sie bereitgestellt ist, gehen Sie zu [URL für Portal ändern](admin/change-base-url.md).
    > - Um Ihr Portal mit einer benutzerdefinierten Domäne zu verknüpfen, siehe [Verknüpfen Sie Ihr Portal mit einer benutzerdefinierten Domäne](admin/add-custom-domain.md).

6.  Wählen Sie in der Dropdown-Liste **Dynamics 365 Instanz** die Instanz aus, mit der Sie das Portal verlinken möchten. Dazu ist es erforderlich, dass der Systemadministrator oder die Rolle System Anpasser in der von Ihnen ausgewählten Instanz verwendet wird.

7.  Wählen Sie die standardmäßige Sprache für Ihr Portal aus der Dropdownliste **Portalsprache wählen** aus. Die verfügbaren Sprachen hängen von den Sprachen ab, die in Ihrer Instanz installiert sind. 

    > [!NOTE]
    > Beispieldaten werden nur in einer Sprache bereitgestellt. Die Auswahl einer Standardsprache entscheidet somit auch, wie die Beispieldaten übersetzt werden. Arabisch und Hebräisch werden nicht unterstützt und werden in der Liste nicht angezeigt.

8. Wählen Sie in der Dropdown-Liste **Portaladministrator auswählen** den Benutzer aus, der das Portal konfigurieren, anpassen und pflegen soll. Alle Benutzer, die in der Organisation die Rolle Systemadministrator haben, werden als Optionen angezeigt. 

9. Wählen Sie im Abschnitt **Portalzielgruppe** den Typ der Zielgruppe aus, der das neue Portal besuchen wird.l Hiermit wird bestimmt, welche Optionen von Portalen Ihnen zugewiesen werden. Sie können aus folgenden Optionen auswählen:

    -   Partner    
        -   Kunden-Self-Service-Portal
        -   Benutzerdefiniertes Portal
        -   Partnerportal
        -   Partner Project Service (optional, erfordert installierte Lösungen)
        -   Partner Field Service (optional, erfordert installierte Lösungen)
        -   Community-Portal

    -   Kundin/Kunde
        -   Kunden-Self-Service-Portal
        -   Benutzerdefiniertes Portal
        -   Community-Portal

    -   Mitarbeiter
        -   Mitarbeiter-Self-Service-Portal

10. Wählen Sie im Abschnitt **Bereitgestelltes Portal auswählen** die Art des Portals aus, die Sie erstellen möchten. Die Optionen, die angezeigt werden, basieren auf der Zielgruppe, die Sie ausgewählt haben.

    > [!div class="mx-imgBorder"]
    > ![Einstellungen für Ihr Portal konfigurieren](media/configure-settings-portal.png "Einstellungen für Ihr Portal konfigurieren")  

11. Klicken Sie auf **Übermitteln** und akzeptieren Sie die Servicebedingungen.
    > [!div class="mx-imgBorder"]
    > ![Vertragsbedingungen](media/terms-of-service.png "Vertragsbedingungen")  

Nachdem Sie die Vertragsbedingungen akzeptiert haben, wird das Portal bereitgestellt. Die Bereitstellung dauert in der Regel 30 Minuten, kann jedoch auch einige Stunden dauern, je nach Systemauslastung. Der *Name* des Portals in der Registerkarte "Anwendung" ändert sich zu "*Name*-Konfigurierung" während der Bereitstellung. Navigieren Sie zur Portalverwaltungsseite zurück, um zu überprüfen, ob die Bereitstellung erfolgreich war.

Nachdem das Portal bereitgestellt wurde, wird die Seite **Portaldetails** mit den erforderlichen Details angezeigt.

> [!div class="mx-imgBorder"]
> ![Portal-Details](media/portal-details-prov.png "Portal-Details") 


> [!Note]
> Wenn sich ein Portalbenutzer zum ersten Mal mit Azure AD-Anmeldeinformationen beim Portal anmeldet, wird allen Benutzern eine Zustimmungsseite angezeigt, unabhängig vom Typ des Benutzers oder Portals.

Die Tabelle unten fasst die Funktionen zusammen, die jeder Portaloption zugeordnet sind:

| Funktion                                | Kunden-Self-Service-Portal | Partnerportal | Employee Self-Service-Portal | Community-Portal | Benutzerdefiniertes Portal |
|----------------------------------------|------------------------------|----------------|------------------------------|------------------|---------------|
| Bereit für die Welt                            | •                            | •              | •                            | •                | •             |
| Mehrsprachunterstützung                 | •                            | •              | •                            | •                | •             |
| Portalverwaltung                  | •                            | •              | •                            | •                | •             |
| Anpassung und Erweiterbarkeit        | •                            | •              | •                            | •                | •             |
| Designverwendung                                | •                            | •              | •                            | •                | •             |
| Content Management                     | •                            |                | •                            | •                |               |
| Wissensmanagement                   | •                            | •              | •                            | •                |               |
| Support/Case Management                | •                            |                | •                            | •                |               |
| Foren                                 | •                            |                | •                            | •                |               |
| Facettierte Suche                         | •                            |                | •                            |                  |               |
| Profilverwaltung                     | •                            |                | •                            |                  |               |
| Forenthread abonnieren              | •                            |                | •                            |                  |               |
| Kommentare                               | •                            |                | •                            | •                |               |
| [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)]-AD-Authentifizierung                |                              |                | •                            |                  |               |
| Ideen                                  |                              |                |                              | •                |               |
| Blogs                                  |                              |                |                              | •                |               |
| Integration von Project Service Automation |                              | •              |                              |                  |               |
| Integration von Field Service              |                              | •              |                              |                  |               |
| Partner-Onboarding                     |                              | •              |                              |                  |               |
| -Portalbasis                            |  •                           | •              |  •                           | •                | •             |
| Portalworkflows                       |  •                           | •              |  •                           | •                | •             |
| Webbenachrichtigungen                      |  •                           | •              |  •                           | •                | •             |
| [!INCLUDE[cc-microsoft](../../includes/cc-microsoft.md)]-Identität                     |     •                         |  •              |     •                         |   •               | •             |
| Identitätsworkflows                     | •                            |  •             |     •                         |   •               | •             |
| Webformulare                              |  •                            | •               |    •                          | •                 | •             |
| Feedback                               |   •                           |  •              |  •                            | •                 | •             |
||

## <a name="troubleshoot-provisioning"></a>Problembehebung bei Bereitstellung

Gelegentlich fällt der die Paketinstallationsvorgang oder der URL-Erstellungsprozess durch Fehler aus. In solchen Fällen können die Prozesse neu gestartet werden.

Wenn sich "*Name*-Konfigurierung" ändert zu "*Name*-Bereitstellung fehlgeschlagen", müssen Sie den Bereitstellungsprozess neu starten.

1. Wechseln Sie zur Seite **Anwendungen**, und wählen Sie das Portal aus.
2. Wählen Sie die blaue Zeichenstiftschaltfläche mit der Bezeichnung **Verwalten** aus.
3. Wählen Sie eine der folgenden Optionen:

   - **Bereitstellung neu starten**: Startet den Installationsprozess erneut mit der Konfiguration, die bereits vorher definiert wurde.

   - **Werte ändern und Bereitstellung neu starten**: Ermöglicht es Ihnen, einige der Werte zu ändern, bevor der Bereitstellungsprozess neu gestartet wird.

Wenn die Paketinstallation fehlgeschlagen ist, lässt sich die Portaladministratorseite ohne Probleme öffnen, aber beim Navigieren zur tatsächlichen Portal-URL wird die Meldung "Wird eingerichtet" angezeigt. Um dies zu bestätigen:

1. Wechseln Sie zur Seite „Lösungsverwaltung“ der **Dynamics 365 Admin Center**-Seite und überprüfen Sie, ob der Paketstatus **Installation fehlgeschlagen** lautet. 

2. Wenn der Paketstatus **Installation fehlgeshlagen** ist, versuchen Sie die Installation von der Lösungsseite aus erneut. Stellen Sie außerdem sicher, dass ein Systemadministrator die Lösung mit der Standardsprache Common Data Service installiert, die auf die Sprache eingestellt ist, in der das Portal installiert werden soll.

> [!NOTE]
> Einige Lösungen besitzen Voraussetzungen für die Installation. Eine Installation wird daher fehlschlagen, wenn die Voraussetzungen nicht erfüllt sind. Wenn Sie beispielsweise den Partner Field Service für ein Partnerportal installieren, müssen die Partnerportal- und Field Service-Lösungen bereits installiert sein. Wenn Sie versuchen, den Partner Field Service zuerst zu installieren, wird die Installation fehlschlagen, und Sie erhalten eine Fehlermeldung.
