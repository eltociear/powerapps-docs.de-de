---
title: Bereitstellen eines Portals mit dem älteren Portal-Add-on | MicrosoftDocs
description: Anweisungen zum Bereitstellen eines Portals mit dem älteren Portal-Add-on.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73550977"
---
# <a name="provision-a-portal-using-the-older-portal-add-on"></a>Bereitstellen eines Portals mit dem älteren Portal-Add-on

Wenn Sie ein älteres Portal-Add-on erworben haben und ein Portal mithilfe des Add-Ins bereitstellen möchten, müssen Sie auf der Seite **Dynamics 365 Administration Center (Dynamics Administration Center** ) das Portal bereitstellen.

> [!NOTE]
> Zum Bereitstellen eines Portals müssen Sie entweder System Administrator oder systemanpassungsrolle der Common Data Service Umgebung, die für das Portal ausgewählt ist, zugewiesen sein. Sie müssen auch über die [erforderlichen Berechtigungen](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions) verfügen, um eine Anwendung in Azure AD zu erstellen und zu registrieren. Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, wenden Sie sich an den globalen Administrator, um Ihre Berechtigungen zu aktualisieren, oder bitten Sie den globalen Administrator, das Portal bereitzustellen.

So stellen Sie ein Portal bereit:

1.  Wechseln Sie zur Seite **Dynamics 365-Verwaltungs Center** , und wählen Sie dann die Registerkarte **Anwendungen** aus.

2.  Wählen Sie die Anwendungs Zeile **Portal Add-on aus**, und wählen Sie dann **Verwalten aus.**

3.  Geben Sie im Abschnitt **Allgemeine Einstellungen** einen **Namen** für das Portal ein. Der **Name** hilft bei der Identifizierung des Portals und kann später geändert werden.

4.  Das **typanfeld** stellt den Typ des Portal Abonnements (Test-oder Produktionsumgebung) dar. Dabei handelt es sich um ein System Feld, das vom Benutzer nicht geändert werden kann. Der Wert ändert sich abhängig davon, ob es sich um ein Testabonnement oder kostenpflichtiges Abonnement handelt

5. Wählen Sie optional in der Dropdown Liste **Portal Entwicklungsstatus** einen der folgenden Entwicklungsstatus für Ihr Portal aus:

    - Status
    - Entwickelt
    - Test
    - UAT
    - Führen

    > [!NOTE]
    > - Für vorhandene bereitgestellte Portale ist diese Dropdown Liste auf der Registerkarte " **Portal Details** " verfügbar, und standardmäßig ist kein Status ausgewählt.
    > - Diese Dropdown Liste ist nur für die Portale des Typs Produktion verfügbar.
    > - Dieses Feld wird von Microsoft verwendet, um das Verwendungs Muster dieses Portals zu verstehen, und wirkt sich nicht auf die Funktionalität aus. Wenn Sie unterschiedliche Namen für den Entwicklungs Lebenszyklus verwenden, wählen Sie die Option aus, die sich in diesem Fall genauer eignet. Dies kann zu einem späteren Zeitpunkt geändert werden, nachdem das Portal bereitgestellt wurde.

5.  Geben Sie im Feld **Portal-URL** den Unterdomänennamen ein, den Sie für Ihr Portal wünschen. Sie können nur alphanumerische Zeichen oder Bindestriche (-) verwenden. andere Zeichen sind nicht zulässig.

    > [!NOTE]
    > - Informationen zum Ändern der URL eines Portals nach der Bereitstellung finden Sie unter [Ändern der Basis-URL eines Portals](admin/change-base-url.md).
    > - Informationen zum Verknüpfen Ihres Portals mit einer benutzerdefinierten Domäne finden Sie unter [Verknüpfen Ihres Portals mit einer benutzerdefinierten](admin/add-custom-domain.md)Domäne.

6.  Wählen Sie in der Dropdown Liste **Dynamics 365-Instanz** die Instanz aus, mit der Sie das Portal verknüpfen möchten. Dies erfordert System Administrator-oder systemanpassungsrolle in der-Instanz, die Sie auswählen, um Sie auszuwählen.

7.  Wählen Sie in der Dropdown Liste **Portal Sprache auswählen** die Standardsprache für Ihr Portal aus. Welche Sprachen verfügbar sind, hängt von den Sprachen ab, die in der-Instanz installiert sind. 

    > [!NOTE]
    > Beispiel Daten werden nur in einer Sprache bereitgestellt. Wenn Sie also eine Standardsprache auswählen, entscheiden Sie auch, wie die Beispiel Daten übersetzt werden. Arabisch und Hebräisch werden nicht unterstützt und werden nicht in der Liste angezeigt.

8. Wählen Sie in der Dropdown Liste **Portal Administrator auswählen** den Benutzer aus, der das Portal konfigurieren, anpassen und warten soll. Alle Benutzer, die über die System Administrator Rolle in der Organisation verfügen, werden als Optionen angezeigt. 

9. Wählen Sie im Abschnitt " **Portal Audience** " den Typ der Zielgruppe aus, der das neue Portal besuchen soll. Dadurch wird festgelegt, welche Optionen für Portale angegeben werden. Sie können Folgendes auswählen:

    -   Partner    
        -   Self-Service-Portal für Kunden
        -   Benutzerdefiniertes Portal
        -   Partner Portal
        -   Partner Projekt Dienst (optional, erfordert installierte Lösungen)
        -   Partner Felddienst (optional, erfordert installierte Lösungen)
        -   Communityportal

    -   Customer
        -   Self-Service-Portal für Kunden
        -   Benutzerdefiniertes Portal
        -   Communityportal

    -   Employee
        -   Personal Self-Service-Portal

10. Wählen Sie im Abschnitt **zu verwendende Portal auswählen** den Typ des Portals aus, das Sie erstellen möchten. Die Optionen, die Sie sehen, basieren auf der Zielgruppe, die Sie ausgewählt haben.

    > [!div class="mx-imgBorder"]
    > ![Konfigurieren von Einstellungen für Ihr Portal](media/configure-settings-portal.png "Konfigurieren von Einstellungen für Ihr Portal")  

11. Wählen Sie über **Mitteln**aus, und akzeptieren Sie die Nutzungsbedingungen.
    > [!div class="mx-imgBorder"]
    > ![Vertragsbedingungen](media/terms-of-service.png "Vertragsbedingungen")  

Nachdem Sie die Vertragsbedingungen akzeptiert haben, wird die Bereitstellung des Portals gestartet. Die Bereitstellung dauert in der Regel 30 Minuten, kann aber je nach System Auslastung einige Stunden dauern. Der *Name* des Portals auf der Registerkarte Anwendung wird bei der Bereitstellung zu *Name*-Konfiguration geändert. Navigieren Sie zurück zur Portal Verwaltungsseite, um zu überprüfen, ob die Bereitstellung erfolgreich war.

Nachdem das Portal bereitgestellt wurde, wird die Seite **Portal Details** mit den erforderlichen Informationen angezeigt.

> [!div class="mx-imgBorder"]
> ![Details zum Portal](media/portal-details-prov.png "Informationen zu einem Portal") 


> [!Note]
> Wenn ein Portalbenutzer sich zum ersten Mal beim Portal anmeldet, indem er eine Azure AD Anmelde Informationen verwendet, wird allen Benutzern eine Zustimmungs Seite angezeigt, unabhängig vom Benutzer-oder portentyp.

In der folgenden Tabelle sind die Funktionen der einzelnen Portal Optionen zusammengefasst:

| Befinden                                | Kunden Self-Service-Portal | Partner Portal | Mitarbeiter Self-Service-Portal | Communityportal | Benutzerdefiniertes Portal |
|----------------------------------------|------------------------------|----------------|------------------------------|------------------|---------------|
| Weltweit bereit                            | •                            | •              | •                            | •                | •             |
| Unterstützung für mehrere Sprachen                 | •                            | •              | •                            | •                | •             |
| Portal Verwaltung                  | •                            | •              | •                            | •                | •             |
| Anpassung und Erweiterbarkeit        | •                            | •              | •                            | •                | •             |
| Design                                | •                            | •              | •                            | •                | •             |
| Inhalts Verwaltung                     | •                            |                | •                            | •                |               |
| Wissensverwaltung                   | •                            | •              | •                            | •                |               |
| Unterstützung/Fall Verwaltung                | •                            |                | •                            | •                |               |
| Fan                                 | •                            |                | •                            | •                |               |
| Facetten Suche                         | •                            |                | •                            |                  |               |
| Profilverwaltung                     | •                            |                | •                            |                  |               |
| Forenthread abonnieren              | •                            |                | •                            |                  |               |
| Iny                               | •                            |                | •                            | •                |               |
| [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD-Authentifizierung                |                              |                | •                            |                  |               |
| Ideen                                  |                              |                |                              | •                |               |
| gt                                  |                              |                |                              | •                |               |
| Integration von Project Service-Automatisierung |                              | •              |                              |                  |               |
| Felddienst Integration              |                              | •              |                              |                  |               |
| Onboarding von Partnern                     |                              | •              |                              |                  |               |
| Portal Basis                            |  •                           | •              |  •                           | •                | •             |
| Portal Workflows                       |  •                           | •              |  •                           | •                | •             |
| Webbenachrichtigungen                      |  •                           | •              |  •                           | •                | •             |
| [!INCLUDE[cc-microsoft](../../includes/cc-microsoft.md)] Identität                     |     •                         |  •              |     •                         |   •               | •             |
| Identitäts Workflows                     | •                            |  •             |     •                         |   •               | •             |
| Web Forms                              |  •                            | •               |    •                          | •                 | •             |
| Backs                               |   •                           |  •              |  •                            | •                 | •             |
||

## <a name="troubleshoot-provisioning"></a>Problembehandlung bei der Bereitstellung

Manchmal kann der Paketinstallations-oder URL-Erstellungs Prozessfehler Haft sein. In diesen Fällen können die Prozesse neu gestartet werden.

Wenn die *namens*Konfiguration von Änderungen an der *namens*Bereitstellung fehlgeschlagen ist, müssen Sie den Bereitstellungs Prozess neu starten.

1. Wechseln Sie zur Seite **Anwendungen** , und wählen Sie das Portal aus.
2. Wählen Sie die blaue Stift Schaltfläche **Verwalten**aus.
3. Wählen Sie eine der folgenden Optionen aus:

   - **Neustart neu starten**: der Installationsvorgang wird mit der zuvor definierten Konfiguration neu gestartet.

   - **Werte ändern und Bereitstellung neu starten**: Hiermit können Sie einige der Werte ändern, bevor Sie den Bereitstellungs Vorgang neu starten.

Wenn bei der Paketinstallation ein Fehler aufgetreten ist, wird die Portaladministrator Seite ohne Probleme geöffnet, bei der Navigation zur tatsächlichen Portal-URL wird jedoch die Einrichtung einer Nachricht angezeigt. So bestätigen Sie Folgendes:

1. Wechseln Sie zur Seite projektmappenverwaltung der Seite **Dynamics 365-Verwaltungs Center** , und überprüfen Sie, ob der Paketstatus Fehler bei **Installation**lautet. 

2. Wenn der Paketstatus Fehler bei der **Installation lautet,** versuchen Sie, die Installation auf der Lösungsseite erneut auszuführen. Vergewissern Sie sich außerdem, dass ein Systemadministrator die Lösung mit der Standardsprache in Common Data Service auf die Sprache, in der das Portal installiert werden soll, installiert.

> [!NOTE]
> Einige Lösungen verfügen über erforderliche Komponenten für Ihre Installation, sodass eine Installation fehlschlägt, wenn die Voraussetzungen nicht erfüllt sind. Um z. b. den Partner Felddienst für ein Partnerportal zu installieren, müssen die Partnerportal-und Felddienst Lösungen bereits installiert sein. Wenn Sie zuerst versuchen, den Partner Felddienst zu installieren, tritt bei der Installation ein Fehler auf, und Sie erhalten eine Fehlermeldung.
