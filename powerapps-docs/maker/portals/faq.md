---
title: Häufig gestellte Fragen | Microsoft Docs
description: Häufig gestellte Fragen in Power Apps Portalen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/17/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: bf76d2a8a3e91d9e20de9d70543af0bda4a57040
ms.sourcegitcommit: b250e63e881d9bd10c0b3dea36c7f12e8a9c6ac2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2020
ms.locfileid: "2988077"
---
# <a name="power-apps-portals-faq"></a>Power Apps Portale-FAQs

Damit Sie eine schnelle Übersicht erhalten, haben wir eine Liste mit häufig gestellten Fragen sowie kurze Antworten zusammengestellt, damit Sie schnell Ihre Informationen erhalten können.

## <a name="general"></a>Allgemein

### <a name="what-is-the-difference-between-power-apps-portals-dynamics-365-portals-and-add-on-portals"></a>Was ist der Unterschied zwischen Power Apps Portal, Dynamics 365 Portalen und Add-On Portalen?

Mit dem Start von Power Apps Portalen am 1. Oktober 2019 werden Dynamics 365 Portale als Power Apps Portale bezeichnet. Mit anderen Worten, alle Portale werden als **Power Apps Portale** bezeichnet.

Eine der wichtigsten Änderungen, die nach dem 1. Oktober 2019 in Portalen eingeführt wurden, ist das Lizenzmodell. Früher waren Portale lizenzierte Add-Ons für Dynamics 365-Apps, während bestimmte Dynamics 365-Lizenzen ein Standardportal-Add-On enthielten. Nach dem 1. Oktober 2019 sind Portale [lizenziert basierend auf der Verwendung](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing). Alle vorhandenen Portale sind Teil einer Übergangsfrist auf der Grundlage des aktuellen Kundenvertrags, nach deren Ablauf sie auf ein neues Lizenzmodell umgestellt werden müssen.

Sie können den Typ eines Portals über das [Power Apps Portals Administratorcenter](./admin/admin-overview.md) überprüfen:

![Power Apps Portaltyp](./media/power-apps-portals-type.png)

Für Add-On-Portale wurde dem Portaltyp das Suffix Add-On hinzugefügt. Ein Produktions-Add-On-Portal-Typ wird beispielsweise als Produktion (Add-On) aufgeführt.

Es gibt keinen Unterschied in der Funktionalität zwischen Power Apps Portalen mit kapazitätsbasierten Lizenzen und Add-On-basierten Lizenzen. Die Bereitstellungsmethode für Portale mit kapazitätsbasierten Lizenzen und Add-On-basierten Lizenzen ist jedoch unterschiedlich.

Sie können Power Apps Portale mit kapazitätsbasierter Lizenz mit den in den folgenden Artikeln beschriebenen Schritten erstellen:

- [Erstellen eines Common Data Service Starterportals](create-portal.md)
- [Erstellen Sie ein Portal mit einer Dynamics 365-Umgebung](create-dynamics-portal.md)

Um ein Power Apps Portal mit Add-On-basierter Lizenz zu erstellen, siehe [Bereitstellung eines Portals mit dem Portal-Add-On](provision-portal-add-on.md).

Gehen Sie zu [Power Apps FAQ zur Lizenzierung von Portalen](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#what-is-the-difference-between-power-apps-portals-and-dynamics-365-portals-in-terms-of-licensing) für Lizenzierungsunterschiede zwischen Add-On-basierten Lizenzen und kapazitätsbasierten Lizenzen.

### <a name="when-is-an-add-on-portal-in-suspended-state"></a>Wann befindet sich ein Add-On-Portal im gesperrten Zustand?

Portal [bereitgestellt mithilfe eines Portal-Add-On-Plans](provision-portal-add-on.md), das zuvor erworben wurde, wird nach Ablauf gesperrt. Die Gültigkeitsdauer beträgt 30 Tage für Testportale, während sie für ein Add-On-Portal in der Produktion mit einer erworbenen Lizenz unterschiedlich sein kann. Das gesperrte Testportal wird nach 7 Tagen gelöscht, während die Sperrfrist für das Produktionsportal variieren kann. Weitere Details finden Sie unter [Portal-Lebenszyklus](./admin/portal-lifecycle.md#considerations-for-add-on-portals) für Add-On-Portale.

### <a name="how-do-i-redirect-a-user-to-a-default-page-after-signing-in"></a>Wie kann man einen Benutzer nach der Anmeldung auf eine Standardseite umleiten?

Sie können ein Portal so konfigurieren, dass ein Benutzer nach der Anmeldung auf eine Standardseite umgeleitet wird. Um diese Funktionalität zu erreichen, können Sie einen JavaScript-Code in die Startseiten-Webvorlage einbinden.

Wenn Sie beispielsweise alle Benutzer nach der Anmeldung auf die Seite "Foren" umleiten möchten, können Sie einen JavaScript-Code wie folgt in die Startseiten-Webvorlage einfügen:

```xml
{% if user %}
//if any user logs in
<script>
  window.location.href='./forums/'
</script>
{% else %}
//Home web page code, if you don't want to display the page when the user is being redirected
{% endif %}
//Home web page code, if you want to display the page when the user is being redirected
```

Weitere Informationen zum Arbeiten mit Liquid-Vorlagen finden Sie unter [Arbeiten mit Liquid-Vorlagen](liquid/liquid-overview.md).

### <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Ich erhalte einen Fehler, dass nur ein Portal erstellt werden kann.

Derzeit können Sie in einer Umgebung pro Sprache nur ein Portal pro Typ erstellen. Wenn Sie versuchen, mehr als ein Portal anzulegen, erhalten Sie eine Fehlermeldung wie folgt:

> [!div class=mx-imgBorder]
> ![Maximal erstellter Portalfehler](media/portal-max-error.png "Maximal erstellter Portalfehler")

Um weitere Portale zu erstellen, müssen Sie eine neue Umgebung über den Link **Neue Umgebung erstellen** in der Fehlermeldung erstellen. Weitere Informationen zum Anlegen eines Portale finden Sie unter [Ein Portal anlegen](create-portal.md).

### <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Ich erhalte einen Fehler, dass ich mein Portal nicht löschen kann.

Wenn Sie nicht über ausreichende Berechtigungen zum Löschen eines Portale verfügen, wird ein Fehler wie folgt angezeigt:

> [!div class=mx-imgBorder]
> ![Löschen des Portalfehlers](media/portal-delete-error.png "Löschen des Portalfehlers")

Informationen zum Löschen eines Portale und der erforderlichen Berechtigungen finden Sie unter [Löschen eines Portale](manage-existing-portals.md#delete).

### <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Ich erhalte einen Fehler, dass ich kein Portal erstellen kann.

Wenn Sie nicht über ausreichende Berechtigungen verfügen, um ein Portal in einer Umgebung zu erstellen, wird ein Fehler wie folgt angezeigt:

> [!div class=mx-imgBorder]
> ![Erstellen des Portalfehlers](media/portal-create-error.png "Erstellen des Portalfehlers")

Informationen zum Erstellen eines Portale und zu den erforderlichen Berechtigungen finden Sie unter [Erstellen eines Portale](create-portal.md).

### <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Ich verstehe die Nachricht: "Deine Daten sind nicht ganz fertig".

Manchmal kann die Erstellung der Datenbank einige Zeit in Anspruch nehmen und der richtige Status spiegelt sich möglicherweise nicht auf der Startseite wider. In diesem Fall erhalten Sie die folgende Meldung:

> [!div class=mx-imgBorder]
> ![Daten nicht bereit](media/data-not-ready.png "Daten nicht bereit")

Wenn Sie weiterhin die Eingabeaufforderung für die Erstellung der Datenbank erhalten oder Ihre Daten nicht ganz fertig sind, können Sie versuchen, die Power Apps Startseite zu aktualisieren, bevor Sie die Kachel **Portal aus leerer (Vorlage)** auswählen.

### <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Ich erhalte einen Fehler, dass ich keine erforderlichen Berechtigungen habe, um Azure Active Directory-Anwendungen zu erstellen.

Wenn Sie ein Portal anlegen, wird das Portal als neue Anwendung in der dem Mandant zugeordneten Azure Active Directory registriert. Wenn Sie nicht über ausreichende Berechtigungen verfügen, um einen Antrag bei Ihrem Azure Active Directory-Mandanten zu registrieren, erhalten Sie wie folgt einen Fehler:

> [!div class=mx-imgBorder]
> ![Azure Active Directory Fehler](media/azure-ad-error.png "Azure Active Directory Fehler")

Um Anwendungen in Azure Active Directory zu erstellen und zu registrieren, müssen Sie sich an Ihren Mandantenadministrator wenden, um die Einstellung **App-Registrierungen** für Ihren Mandanten einzuschalten. Weitere Informationen finden Sie unter [Benötigte Berechtigungen](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

### <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Ich erhalte einen Fehler, dass die Portalerstellung in diesem Mandanten durch den globalen Administrator blockiert wird.

Wenn die Portalerstellung in einem Mandanten von Ihrem globalen Administrator blockiert wird, erhalten Sie einen Fehler wie folgt:

> [!div class=mx-imgBorder]
> ![Portalerstellung Fehler gesperrt](media/portal-create-blocked-error.png "Portalerstellung Fehler gesperrt")

Sie müssen Ihren globalen Administrator kontaktieren, um die Erstellung von Portalen auch für Nicht-Administratoren zu ermöglichen.

Wenn Sie ein globaler Administrator sind, müssen Sie die Einstellung `disablePortalsCreationByNonAdminUsers` auf Mandantenebene über PowerShell deaktivieren. Führen Sie den folgenden Befehl in einem PowerShell-Fenster aus (führen Sie PowerShell als Administrator aus).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Mehr Informationen: [Deaktivieren der Portalerstellung in einem Mandanten](create-portal.md#disable-portal-creation-in-a-tenant)

### <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Es wird ein Fehler angezeigt, dass ich nicht die entsprechende Lizenz besitze, auf diese Website zuzugreifen.

Für interne Benutzer einer Organisation, die Portale zum Zugriff auf authentifizierten Seiten verwendet, ist es erforderlich, dass Lizenzen der Umgebung zugewiesen werden, mit der ein Portal verbunden ist. Sie können mehr Informationen über Berechtigungen auf Portale für interne Benutzer [hier](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users) lesen. Wenn keine Lizenzen einer Umgebung zugeordnet sind, erhalten interne Benutzer einen Fehler wie den folgenden:

> [!div class=mx-imgBorder]
> ![Portalanmeldefehler](media/portal-login-error.png "Portalanmeldefehler")

## <a name="licensing-and-provisioning"></a>Lizenzierung und Bereitstellung

### <a name="how-do-i-get-a-portal-subscription"></a>Wie erhalte ich ein Portalabonnement?

[Power Apps-Portale](overview.md) sind jetzt völlig eigenständig innerhalb von Power Apps verfügbar. Sie müssen keine Lizenz mehr erwerben, um ein Portal bereitzustellen. Der Benutzerzugriff zum Portal erfordert eine Lizenz abhängig vom Personatyp. Weitere Informationen finden Sie unter [Power Apps-Portallizenzierung – FAQ](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing).

### <a name="how-do-i-change-the-audience-and-type-of-a-portal-after-it-is-provisioned"></a>Wie kann man die Zielgruppe und den Typ eines Portals ändern, nachdem es bereitgestellt wurde?

Nachdem Sie ein Portal bereitgestellt haben, ist die Option zum Ändern des Portalpublikums deaktiviert.

Sie können jedoch die Zielgruppe und den Typ eines Portals ändern, nachdem es bereitgestellt wurde, indem Sie den Schritten folgen, die im Abschnitt [Ändern der Dynamics 365-Instanz, der Zielgruppe oder des Portaltyps](admin/change-dynamics-instance.md) beschrieben sind.

> [!NOTE]
> - Es wird empfohlen, das Portal zurückzusetzen und erneut bereitzustellen, um Zielgruppe, Portaltyp, Organisation usw. zu ändern. Weitere Informationen: [Ein Portal zurücksetzen](admin/reset-portal.md)
> - Die Änderung der Dynamics 365-Instanz gilt nur für die Portale, die mit den älteren Portal-Add-Ons bereitgestellt wurden.

### <a name="how-do-i-change-the-base-url-of-a-portal-after-it-is-provisioned"></a>Wie kann man die Basis-URL eines Portals nach der Bereitstellung ändern?

Sie können die Basis-URL eines Portals nach der Bereitstellung ändern, indem Sie die unter [Ändern der Basis-URL eines Portals](admin/change-base-url.md) genannten Schritte ausführen.

### <a name="how-do-i-delete-a-portal-completely-after-it-is-provisioned"></a>Wie kann ein Portal vollständig gelöscht werden, nachdem es bereitgestellt wurde?

Portale bestehen aus den folgenden Komponenten:

- **Portalwebsitehost**: Portalwebsitehost ist der Portalcode, der die eigentliche Website formt.

- **Portallösungen**: Lösungen, die in der Common Data Service-Umgebung installiert sind und die Metadatenentitäten für jedes Portal enthalten.

Um ein Portal vollständig zu löschen, müssen Sie den Host der Portal-Website löschen und die Portallösungen aus Ihrer Common Data Service-Umgebung deinstallieren.

Um den Portalhost zurückzusetzen, führen Sie die Schritte unter [Ein Portal zurücksetzen](admin/reset-portal.md) aus. Es ist wichtig zu beachten, dass das Zurücksetzen eines Portalrechners keinen Einfluss auf die Konfiguration in Ihrer Common Data Service-Umgebung hat.

Um Portallösungen zu löschen, müssen Sie Lösungen aus der Benutzeroberfläche des Dynamics 365-Lösungs-Explorers löschen. Die Reihenfolge, in der Portallösungen deinstalliert werden sollten, wird unter [Deinstallieren von Portallösungen](https://community.dynamics.com/365/b/dynamics365portalssupport/archive/2017/02/27/portal-troubleshooting-part-three-uninstalling-portal-solutions) bereitgestellt.

## <a name="common-data-service-environment-lifecycle"></a>Common Data Service Lebenszyklus der Umgebung

### <a name="we-recently-moved-our-common-data-service-environment-from-one-geolocation-or-tenant-to-another-how-do-we-handle-portals-connected-to-our-organization"></a>Vor kurzem haben wir unsere Common Data Service-Umgebung von einer Geolocation oder einem Mandanten in eine andere verlegt. Wie behandeln wir Portale, die mit der Organisation verbunden sind?

Wenn Sie Ihre Common Data Service-Umgebung von einer Geolocation oder einem Mandanten in eine andere verschieben, werden die zugehörigen Portale zu dieser Organisation nicht automatisch verschoben. Weil die Organisation verschoben wurde, funktioniert auch kein Portal, das mit dieser Organisation verbunden ist, und löst beim Start einen Fehler aus.

So ordnen Sie Ihr Portal erneut relevanten Organisationen zu:

1. Setzen Sie Ihren vorhanden Portalhost von der vorhandenen Geolokalisierung oder dem vorhandenen Mandanten zurück, indem Sie den Schritten unter [Ein Portal zurücksetzen](admin/reset-portal.md) folgen. Dadurch werden die zugeordneten Portalressourcen gelöscht und die Portal-URL ist nicht verfügbar, nachdem der Vorgang abgeschlossen wurde.

2. Nachdem Ihr vorhandenes Portal zurücksetzt wurde, wechseln Sie zu dem neuen Mandanten (oder zur neuen Geolokalisierung des vorhandenen Mandanten) und stellen Sie dort ein Portal bereit.

### <a name="after-restoring-a-common-data-service-environment-from-an-old-backup-the-portal-connected-to-the-organization-is-not-working-how-do-we-fix-it"></a>Nach der Wiederherstellung einer Common Data Service-Umgebung aus einem alten Backup funktioniert das mit dem Unternehmen verbundene Portal nicht. Wie kann man das beheben?

Wenn eine Common Data Service-Umgebung aus einem Backup wiederhergestellt wird, werden verschiedene Änderungen in Ihrer Organisation vorgenommen, die die Verbindung Ihres Portale mit der Organisation unterbrechen können. So beheben Sie dieses Problem:

- Wenn die Organisations-ID nach dem Wiederherstellungsvorgang gleich ist und zudem Portallösungen zur Verfügung stehen:

1. Öffnen Sie [Power Apps Portale Administratorcenter](admin/admin-overview.md).
2. Gehen Sie zur Registerkarte **Portaldetails**.
3. Wählen Sie in der Dropdownliste **Portalstatus** die Option **Aus** aus.
4. Wählen Sie **Aktualisieren**. 
5. Nachdem der Aktualisierungsvorgang abgeschlossen wurde, legen Sie die Dropdownliste **Portalstatus** auf **Aktiviert** fest und wählen Sie dann **Aktualisieren** aus.

  Das Portal wird neu gestartet und es wird erneut eine Verbindung mit der Organisation erstellt.

- Wenn die Organisations-ID nach dem Wiederherstellungsvorgang anders ist oder Portallösungen aus Ihrer Organisation gelöscht sind:

  - In diesem Fall ist es besser, das Portal zurückzusetzen, indem die Schritte unter [Ein Portal zurücksetzen](admin/reset-portal.md) ausgeführt werden, und es dann erneut bereitzustellen.

### <a name="we-recently-changed-the-url-of-our-common-data-service-environment-and-our-portal-stopped-working-how-do-we-fix-it"></a>Wir haben kürzlich die URL unserer Common Data Service-Umgebung geändert und unser Portal funktioniert nicht mehr. Wie kann man das beheben?

Wenn Sie die URL Ihrer Common Data Service-Umgebung ändern, funktioniert Ihr Portal nicht mehr, da es die Common Data Service-Umgebungs-URL nicht mehr identifizieren kann. So beheben Sie dieses Problem:

1. Öffnen Sie [Power Apps Portale Administratorcenter](admin/admin-overview.md).
2. Wechseln Sie zu **Portalaktionen** > **Dynamics 365 URL aktualisieren**.
3. Führen Sie die Anweisungen im Assistenten aus.

Das Portal wird neu gestartet und funktioniert wieder.

## <a name="debugging-and-fixing-problems"></a>Debuggen und Beheben von Problemen

### <a name="when-accessing-my-portal-i-see-a-generic-error-page-how-can-i-see-the-actual-error"></a>Wenn ich auf mein Portal zugreife, wird eine allgemeine Fehlerseite angezeigt. Wie kann ich den tatsächlichen Fehler anzeigen?

Immer wenn ein Serverfehler bei dem Rendern eines Portal auftritt, wird eine allgemeine Fehlerseite für Endbenutzer zusammen mit dem Zeitstempel und der Aktivitäts-ID des Fehlers angezeigt. Portaladministratoren können das Portal konfigurieren, um tatsächliche Fehlerdetails zu erhalten, die beim Debuggen und Beheben von Problemen nützlich sind. So zeigen Sie den tatsächlichen Fehler an:

- **Die benutzerdefinierten Fehlerseite auf dem Portal deaktivieren**: Dadurch wird die benutzerdefinierte Fehlerseite deaktiviert und Ihnen ermöglicht, das vollständigen Stapelprotokoll eines jeden Fehlers beim Navigieren zu dieser Seite zu sehen. Sie können den benutzerdefinierten Fehler deaktivieren, indem Sie die Schritte unter [Benutzerdefinierten Fehler deaktivieren](admin/view-portal-error-log.md#disable-custom-error) ausführen.

Es ist ratsam, dies nur zu verwenden, wenn Sie ein Portal entwickeln. Sobald das Portal für Benutzer live ist, sollten Sie benutzerdefinierte Fehler wieder aktivieren. Weitere Informationen: [Portalfehlerprotokolle anzeigen](admin/view-portal-error-log.md)

- **Diagnoseprotokollierung aktivieren**: Dies ermöglicht Ihnen,alle Portalfehler in einem Azure Blob Storage Account anzufordern. Sie können Diagnoseprotokollierung aktivieren, indem Sie die Schritte unter [Auf Portalfehlerprotokolle zugreifen](admin/view-portal-error-log.md#access-portal-error-logs) ausführen.

Wenn Sie Diagnoseprotokollierung aktivieren, können Sie nach bestimmten Fehlern suchen, die Benutzer unter der Aktivitäts-ID auf der allgemeinen Fehlerseite melden. Die Aktivitäts-ID wird zusammen mit Fehlerdetails protokolliert und ist nützlich, um das tatsächliche Problem zu suchen.

## <a name="portal-administration-and-management"></a>Portalverwaltung und -verwaltung

### <a name="do-portals-use-any-static-content-from-cdns-content-delivery-network-that-i-need-to-whitelist"></a>Verwenden Portale statische Inhalte von CDNs (Content Delivery Network), die ich für die Whitelist benötige?

Ja. Power Apps Portale verwendet die statischen Ressourcen des Standardportals von Azure CDN, die standardmäßig JavaScript enthält und CSS Dateien für die Präsentation, die zuvor als Teil der Portal-App gerendert wurden. Sie müssen die folgende CDN-URL auf die Whitelist setzen, um Portale erfolgreich zu rendern:

    https://content.powerapps.com/resource/powerappsportal

> [!NOTE]
> Power Apps Portale, die in Microsoft Government Cloud gehostete werden, verwenden kein CDN.

### <a name="how-do-i-use-a-custom-login-provider-on-my-portal"></a>Wie wird ein benutzerdefinierter Anmeldeanbieter auf meinem Portal verwendet?

Portale unterstützen einen benutzerdefinierten Anmeldeanbieter, der Unterstützung für Standardauthentifizierungsprotokolle bietet. Wir unterstützen OpenIdConnect, SAML2 und WS-Verbundprotokolle für alle benutzerdefinierten IDP. OAuth2 wird nur für eine feste Gruppe von bekannten IDPs unterstützt. Weitere Informationen darüber, wie Sie eine IDP-Konfiguration einrichten, finden Sie unter [Konfigurieren der Portalauthentifizierung](configure/configure-portal-authentication.md).

### <a name="how-do-i-get-new-portal-releases-in-my-sandbox-portal-first-before-it-gets-applied-to-production"></a>Wie erhalte ich neue Portalversionen in meinem Sandkastenportal noch bevor sie für die Produktion angewendet werden?

Jede Portaleinführung wird in zwei Phasen ausgeführt: frühes Upgrade und allgemeine Verfügbarkeit. Während der Phase des frühen Upgrades aktualisieren wir nur Portale, die für das frühe Upgrade vorgesehen sind. Wenn Sie eine neue Portalversion in Ihrer Sandboxumgebung (Entwicklung oder Test) erhalten, können Sie das frühe Upgrade für Ihr Portal aktivieren. Informationen dazu, wie Sie das frühe Upgrade für ein Portal aktivieren, erhalten Sie unter [Aktualisieren eines Portals](https://docs.microsoft.com/dynamics365/customer-engagement/portals/upgrade-portal).

### <a name="how-do-i-use-a-custom-domain-name-for-my-portal"></a>Wie kann ein benutzerdefinierter Domänenname für das Portal verwendet werden?

Sie können Ihr Portal aktivieren, um einen benutzerdefinierten Domänennamen anstelle des Standarddomänennamens `microsoftcrmportals.com` zu verwenden. Mehr Informationen: [Verlinken Sie Ihr Portal mit einer benutzerdefinierten Domäne](admin/add-custom-domain.md)

## <a name="portal-checker"></a>Portalprüfer

### <a name="portal-does-not-load-and-displays-a-generic-error-page-server-error-in--application"></a>Das Portal lädt nicht und zeigt eine generische Fehlerseite an (Server-Fehler in der Anwendung "/"). 

Dieses Problem kann durch eine Vielzahl von Gründen verursacht werden, wie z.B. wenn ein Portal keine Verbindung zur zugrunde liegenden Common Data Service-Umgebung herstellen kann, die Common Data Service-Umgebung nicht existiert oder sich seine URL geändert hat, wenn die Anforderung an die Common Data Service-Umgebung zeitgesteuert ist, usw. Wenn Sie das Portalprüfer-Tool ausführen, wird es versuchen, den genauen Grund zu ermitteln und Sie auf die richtige Maßnahme hinweisen. 

Nachfolgend finden Sie eine Liste der häufigsten Ursachen und der entsprechenden Gegenmaßnahmen:

#### <a name="url-of-the-connected-common-data-service-environment-has-changed"></a>Die URL der verbundenen Common Data Service Umgebung hat sich geändert. 

Dies geschieht, wenn die URL der Umgebung Common Data Service von einem Benutzer geändert wird, nachdem das Portal für das Unternehmen bereitgestellt wurde. Um dieses Problem zu beheben, aktualisieren Sie die URL von Dynamics 365:

1. Öffnen Sie das [Power Apps Portale Administratorcenter](admin/admin-overview.md).
2. Wechseln Sie zu **Portalaktionen** > **Dynamics 365 URL aktualisieren**. Sobald diese Aktion erfolgreich ausgeführt wurde, wird Ihre Common Data Service Umgebungs-URL aktualisiert und das Portal beginnt zu funktionieren.

#### <a name="common-data-service-environment-connected-to-your-portal-is-in-administration-mode"></a>Die mit Ihrem Portal verbundene Common Data Service-Umgebung befindet sich im Administratormodus.

Dieses Problem tritt auf, wenn die Common Data Service-Umgebung in den Administratormodus versetzt wird, entweder beim Wechsel der Organisation vom Produktions- in den Sandboxmodus oder manuell durch einen Organisationsadministrator.

Wenn dies die Ursache ist, können Sie den Administrationsmodus deaktivieren, indem Sie die [hier](https://docs.microsoft.com/dynamics365/admin/manage-sandbox-instances#administration-mode) aufgeführten Aktionen ausführen. Sobald der Administrationsmodus deaktiviert ist, funktioniert das Portal einwandfrei.

#### <a name="authentication-connection-between-common-data-service-environment-and-portal-is-broken"></a>Die Authentifizierungsverbindung zwischen der Common Data Service-Umgebung und dem Portal ist unterbrochen

Dieses Problem tritt auf, wenn die Authentifizierungsverbindung zwischen Dynamic 365-Organisation und Portal unterbrochen ist, weil entweder die Common Data Service-Umgebung aus einem Backup wiederhergestellt wurde oder gelöscht und aus einem Backup wiederhergestellt wurde. So beheben Sie dieses Problem:

1. Öffnen Sie das [Power Apps Portale Administratorcenter](admin/admin-overview.md).
2. Wählen Sie auf der Registerkarte **Portaldetails** in der Liste **Portalstatus** die Option **Aus**.
3. Wählen Sie **Aktualisieren**.
4. Wählen Sie **Ein** aus der Liste **Portalstatus**.
5. Wählen Sie **Aktualisieren**. Das Portal wird neu gestartet und kann eine Authentifizierungsverbindung herstellen.

In bestimmten Situationen, insbesondere wenn sich die Organisations-ID nach der Wiederherstellung geändert hat (oder wenn Sie das Unternehmen neu bereitgestellt haben), funktionieren diese Maßnahmen jedoch nicht. In diesen Situationen können Sie das Portal gegen dieselbe Instanz zurücksetzen und neu bereitstellen. Informationen zum Zurücksetzen eines Portals finden Sie unter [Zurücksetzen eines Portals](admin/reset-portal.md).

#### <a name="request-to-common-data-service-environment-has-timed-out"></a>Anforderung an die Umgebung Common Data Service ist abgelaufen

Dieses Problem ist typischerweise ein vorübergehendes Problem, das auftreten kann, wenn die API-Anfragen an Ihre Common Data Service-Umgebung abgelaufen sind. Dieses Problem wird sich automatisch verringern, sobald die API-Anfragen funktionieren. Um dieses Problem zu beheben, können Sie auch versuchen, das Portal neu zu starten:

1. Öffnen Sie das [Power Apps Portale Administratorcenter](admin/admin-overview.md).
2. Gehen Sie zu **Portalaktionen** > **Neustart**.

Wenn der Neustart des Portals nicht funktioniert und dieses Problem über einen längeren Zeitraum auftritt, wenden Sie sich bitte an den Microsoft-Support.

#### <a name="website-binding-not-found"></a>Website-Bindung nicht gefunden

Dieses Problem tritt auf, wenn die Website-Bindungsdatensätze für das Portal aus der zugrunde liegenden Common Data Service-Umgebung gelöscht werden und das Portal nicht in der Lage ist, die Bindung automatisch zu erstellen. So beheben Sie dieses Problem:

1. Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2. Öffnen Sie **Portale** > **Websitebindungen**.
3. Löschen Sie alle Website-Bindungsdaten, die auf Ihr Portal verweisen. Das Feld **Sitename** hilft Ihnen, die für die Website bindenden Datensätze Ihres Portals zu identifizieren.
4. Nachdem Sie alle Datensätze für die Website-Bindung gelöscht haben, starten Sie das Portal neu.

Sobald Sie die oben genannten Schritte ausgeführt haben, wird Ihr Portal neu gestartet und stellt den Website-Bindungsdatensatz automatisch wieder her.

Es gibt jedoch Situationen, in denen das Portal nicht in der Lage ist, den Website-Bindungsdatensatz automatisch neu zu erstellen, wenn sich die GUID des in Ihrer Instanz verfügbaren Website-Datensatzes von derjenigen unterscheidet, die bei der Standardinstallation des Portale erstellt wurde. Führen Sie in dieser Situation die folgenden Schritte aus:

1. Löschen Sie alle Datensätze, die sich auf Ihr Portal beziehen.
2. Erstellen Sie manuell einen Website-Bindungsprotokoll mit folgenden Werten:
  - **Name**: Kann eine beliebige Zeichenfolge sein
  - **Website**: Wählen Sie den Website-Datensatz aus, der im Portal gerendert werden soll.
  - **Sitename**: Geben Sie den Hostnamen Ihres Portals ein, z. B. Portal-URL ohne https:// am Anfang. Wenn Ihr Portal einen benutzerdefinierten Domänennamen verwendet, dann verwenden Sie hier einen benutzerdefinierten Domänennamen.
  - Lassen Sie alle anderen Felder leer.
3. Sobald der Website-Bindungsdatensatz wiederhergestellt ist, starten Sie Ihr Portal aus dem Power Apps Portale Administrationscenter neu.

#### <a name="an-unexpected-error-has-occurred-while-trying-to-connect-to-your-common-data-service-environment"></a>Beim Versuch, sich mit Ihrer Common Data Service-Umgebung zu verbinden, ist ein unerwarteter Fehler aufgetreten

Diese Situation kann durch ein unerwartetes Problem entstehen. Um in dieser Situation Abhilfe zu schaffen, können Sie entweder versuchen, das Portal zurückzusetzen oder neu bereitzustellen. Informationen zum Zurücksetzen eines Portals finden Sie unter [Zurücksetzen eines Portals](admin/reset-portal.md).

Wenn das Zurücksetzen und Bereitstellen des Portals dieses Problem nicht löst, wenden Sie sich bitte an den Microsoft-Support.

### <a name="portal-is-not-displaying-updated-data-from-common-data-service-environment"></a>Das Portal zeigt keine aktualisierten Daten aus der Common Data Service-Umgebung an.

Alle im Portal angezeigten Daten werden aus dem Portal-Cache gerendert. Dieser Cache wird aktualisiert, wenn Daten in der Umgebung Common Data Service aktualisiert werden. Dieser Prozess ist jedoch asynchron und kann bis zu 15 Minuten dauern. Wenn die Änderungen in der Metadatenentität des Portale vorgenommen werden, z.B. Webseiten, Webdateien, Inhaltsausschnitt, Website-Einstellung usw., wird empfohlen, den Cache manuell zu löschen oder das Portal aus dem Administrationscenter von Power Apps Portale neu zu starten. Informationen zum Löschen des Cache finden Sie unter [Löschen des serverseitigen Cache für ein Portal](admin/clear-server-side-cache.md). 

Wenn Sie jedoch lange Zeit veraltete Daten in nicht-portalen Metadateneinheiten sehen, kann dies an einer Vielzahl von Problemen liegen, die nachfolgend aufgeführt sind:

#### <a name="entities-not-enabled-for-cache-invalidation"></a>Entitäten nicht für Cache-Invalidierung aktiviert

Wenn Sie veraltete Daten nur für bestimmte Entitäten und nicht für alles sehen, kann dies daran liegen, dass die Änderungsverfolgung für diese bestimmte Entität nicht aktiviert ist.

Wenn Sie das Tool Portalprüfer (Self-Service-Diagnose) ausführen, listet es den Objekttypcode aller Entitäten auf, die im Portal in Entitätenlisten oder Entitätsformularen und Webformularen referenziert werden und nicht für die Änderungsverfolgung aktiviert sind. Durchsuchen Sie Ihre Metadaten, indem Sie die unter [Durchsuchen der Metadaten für Ihre Organisation beschriebenen Schritte ausführen](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/browse-your-metadata).

Wenn bei einer dieser Entitäten ein veraltetes Datenproblem auftritt, können Sie die Änderungsverfolgung aktivieren, indem Sie das Power Apps Portals Admin Center verwenden. Benutzeroberfläche oder Dynamics 365-API. Mehr Informationen: [Änderungsverfolgung für eine Entität aktivieren](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/use-change-tracking-synchronize-data-external-systems#enable-change-tracking-for-an-entity)

#### <a name="organization-not-enabled-for-change-tracking"></a>Organisation für die Änderungsverfolgung nicht aktiviert

Abgesehen davon, dass jede Entität für die Änderungsverfolgung aktiviert wird, müssen Organisationen im Ganzen auch für die Änderungsverfolgung aktiviert werden. Eine Organisation ist für die Änderungsverfolgung aktiviert, wenn eine Portalbereitstellungsanforderung übermittelt wird. Dies kann jedoch abbrechen, wenn eine Organisation aus einer alten Datenbank wiederhergestellt oder zurückgesetzt wird. So beheben Sie dieses Problem:

1. Öffnen Sie das [Power Apps Portale Administratorcenter](admin/admin-overview.md).
2. Wählen Sie auf der Registerkarte **Portaldetails** in der Liste **Portalstatus** die Option **Aus**.
3. Wählen Sie **Aktualisieren**.
4. Wählen Sie **Ein** aus der Liste **Portalstatus**.
5. Wählen Sie **Aktualisieren**. Das Portal wird neu gestartet und kann eine Authentifizierungsverbindung herstellen.

### <a name="performance-best-practices"></a>Bewährte Methoden für die Leistung

Performance-Probleme in Portalen können durch eine Vielzahl von Konfigurationsproblemen verursacht werden. Alle Out-of-the-Box-Portalvorlagen werden auf eine Vielzahl von Lastbedingungen und Konfigurationen getestet, die die Portalleistung beeinträchtigen können, und im Folgenden finden Sie eine Liste der häufigsten Portalkonfigurationen, die zu Performance-Problemen in Ihrem Portal führen können.

Das Tool Portalprüfer (Self-Service Diagnose) weist Sie ebenfalls auf diese Probleme hin, indem es sich Ihre Portalkonfiguration ansieht.

#### <a name="web-page-tracking-enabled"></a>Webseiten-Tracking aktiviert

Das Aktivieren einer Portal-Webseite für das Seiten-Tracking kann zu Performance-Problemen in Ihrem Portal führen. Diese Funktionalität ist seit der Veröffentlichung von Dynamics 365 Portale im Januar 2018 veraltet. Mehr Informationen: [Dynamics 365 Portale: Veraltete Features](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

Das Portalprüfer-Tool listet alle Webseiten (sowohl Stamm- als auch Inhaltsseite) auf, die für die Seitenverfolgung aktiviert sind. Diese Seiten sollten durch Ausführen dieser Schritte deaktiviert werden:

1. Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2. Gehen Sie zu „Erweiterte Suche“.
3. Suchen Sie nach allen Webseiten, in denen das Feld **Aktivieren der Nachverfolgung (veraltet)** aktiviert ist (Wert wird auf Ja gesetzt).
4. Bearbeiten Sie alle Seiten in großen Mengen und setzen Sie dieses Feld auf **Nein**.

Alternativ können Sie auch zu jeder Seite gehen, die im Ergebnis des Portalprüfers aufgeführt ist, und den Wert des Feldes **Nachverfolgung aktivieren (veraltet)** auf **Nein** setzen. Es ist wichtig zu verstehen, dass, wenn Sie sich auf Dynamics 365 Portale Lösung Version 9.x befinden, dieses Feld nicht auf dem Formular angezeigt wird und Sie es möglicherweise zuerst zum Formular hinzufügen müssen. 

#### <a name="web-file-tracking-enabled"></a>Webdateiverfolgung aktiviert

Das Aktivieren einer Portal-Webdatei für die Seitenverfolgung kann zu Performance-Problemen in Ihrem Portal führen. Diese Funktionalität ist seit der Veröffentlichung von Dynamics 365 Portale im Januar 2018 veraltet. Mehr Informationen: [Dynamics 365 Portale: Veraltete Features](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

Das Portalprüfer-Tool listet alle Webdateien auf, die für die Seitenverfolgung aktiviert sind. Diese Dateien sollten durch Ausführen dieser Schritte deaktiviert werden:

1. Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2. Gehen Sie zu „Erweiterte Suche“.
3. Suchen Sie nach allen Webdateien, in denen das Feld **Verfolgung aktivieren (veraltet)** aktiviert ist (Wert wird auf Ja gesetzt).
4. Massenbearbeitung aller Datensätze und setzen Sie dieses Feld auf **Nein**.

Alternativ können Sie auch zu jeder Datei gehen, die im Ergebnis des Portalprüfers aufgelistet ist, und den Wert des Felds **Nachverfolgung aktivieren (veraltet)** auf **Nein** setzen. Es ist wichtig zu verstehen, dass, wenn Sie sich auf der Portallösung Version 9.x befinden, dieses Feld nicht auf dem Formular angezeigt wird und Sie es möglicherweise zuerst zum Formular hinzufügen müssen. 

#### <a name="login-tracking-enabled"></a>Anmeldeverfolgung aktiviert

Die Aktivierung eine Portalanmeldeverfolgung kann zu Performance-Problemen in Ihrem Portal führen. Diese Funktionalität ist seit der Veröffentlichung von Dynamics 365 Portale im Januar 2018 veraltet. Mehr Informationen: [Dynamics 365 Portale: Veraltete Features](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

Das Portalprüfer-Tool prüft, ob die Anmeldeverfolgung für Ihr Portal aktiviert ist und zeigt eine fehlgeschlagene Prüfung an, wenn sie aktiviert ist. Die Verfolgung der Anmeldung sollte deaktiviert werden, indem Sie diesen Schritten folgen:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Gehen Sie zu **Portale** > **Site-Einstellungen**.
3.  Suchen Sie nach der Site-Einstellung mit dem Namen `Authentication/LoginTrackingEnabled`.
4.  Ändern Sie den Wert dieser Website-Einstellung auf **Falsch** oder löschen Sie die Website-Einstellung.
5.  Starten Sie das Portal neu. 

#### <a name="header-output-cache-is-disabled"></a>Header Output Cache ist deaktiviert.

Das Deaktivieren des Header-Output-Cache in Ihrem Portal kann bei hoher Last zu Performance-Problemen in Ihrem Portal führen. Weitere Details zu dieser Funktionalität finden Sie unter: [Aktivieren Sie das Zwischenspeichern von Kopf- und Fußzeilenausgaben in einem Portal](configure/enable-header-footer-output-caching.md).

Das Portalprüfer-Tool prüft, ob der Header-Ausgabe-Cache in Ihrem Portal deaktiviert ist und zeigt eine fehlgeschlagene Überprüfung an, wenn er deaktiviert ist. Um es zu aktivieren:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Gehen Sie zu **Portale** > **Site-Einstellungen**.
3.  Suchen Sie nach der Site-Einstellung mit dem Namen `Header/OutputCache/Enabled`.
4.  Wenn die Site-Einstellung verfügbar ist, ändern Sie den Wert der Site-Einstellung auf **Wahr**. Wenn die Site-Einstellung nicht verfügbar ist, erstellen Sie eine neue Site-Einstellung mit diesem Namen und setzen Sie ihren Wert auf **Wahr**.
5.  Starten Sie das Portal neu. 

#### <a name="footer-output-cache-is-disabled"></a>Der Cache für die Fußzeilenausgabe ist deaktiviert.

Das Deaktivieren des Footer-Ausgabe-Cache in Ihrem Portal kann bei hoher Last zu Performance-Problemen in Ihrem Portal führen. Weitere Details zu dieser Funktionalität finden Sie unter: [Aktivieren Sie das Zwischenspeichern von Kopf- und Fußzeilenausgaben in einem Portal](configure/enable-header-footer-output-caching.md).

Das Portalprüfer-Tool prüft, ob der Cache für die Fußzeilenausgabe in Ihrem Portal deaktiviert ist und zeigt eine fehlgeschlagene Prüfung an, wenn sie deaktiviert ist. Um es zu aktivieren:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Gehen Sie zu **Portale** > **Site-Einstellungen**.
3.  Suchen Sie nach der Site-Einstellung mit dem Namen `Footer/OutputCache/Enabled`.
4.  Wenn die Site-Einstellung verfügbar ist, ändern Sie den Wert der Site-Einstellung auf **Wahr**. Wenn die Site-Einstellung nicht verfügbar ist, erstellen Sie eine neue Site-Einstellung mit diesem Namen und setzen Sie ihren Wert auf **Wahr**.
5.  Starten Sie das Portal neu. 

#### <a name="large-number-of-web-file-records"></a>Große Anzahl von Webdateidatensätzen

Die Webdateientität wird von einem Portal verwendet, um alle statischen Dateien zu speichern, die Sie in Ihrem Portal verwenden möchten. Hauptanwendungsfall dieser Entität ist es, statische Inhalte Ihrer Website wie CSS, JavaScript, Bilddateien und so weiter zu speichern. Das Vorhandensein vieler solcher Dateien kann jedoch zu Verzögerungen beim Start Ihres Portals führen.

Das Portalprüfer-Tool prüft dieses Szenario und gibt Ihnen einen Hinweis, ob Sie mehr als 500 aktive Webdateien in Ihrem Portal haben. Wenn alle diese Dateien statische Inhalte wie CSS, JavaScript, Bilddateien usw. darstellen, können Sie folgende Maßnahmen ergreifen, um dieses Problem zu beheben.

- Verwenden Sie einen externen Dateiserver wie Azure Blob Storage oder CDN, um diese Dateien zu speichern und verweisen Sie dann auf die entsprechenden Seiten entweder innerhalb der Seite oder in der darunter liegenden Vorlage.

- Wenn Sie Dateien nicht nach außen verschieben können, stellen Sie sicher, dass nicht alle Dateien zusammen mit der Startseite geladen werden. Eine Webdatei wird zusammen mit der Homepage geladen, wenn die übergeordnete Seite dieser Datei auf Home gesetzt ist. Um dieses Szenario zu vermeiden, können Sie die folgenden Schritte durchführen:

  1. Erstellen Sie eine Dummy-Webseite ohne Inhalt und eine leere Vorlage. Diese Seite wird verwendet, um einen direkten Pfad zu Ihren Webdateien zu erstellen. 
  2. Für alle Webdateien, die auf der Startseite nicht benötigt werden, ändern Sie die übergeordnete Seite in diese Dummy-Webseite. Sobald dies erledigt ist, wäre der vollständige Pfad zu Ihrer Webdatei `Portal URL/{dummy_webpage}/{web file}`.
  3. Verweisen Sie Ihre Webdatei direkt im HTML der Seitenvorlage oder der Webvorlage der Seite, auf der Sie sie verwenden möchten. Dadurch wird Ihre Datei bei Bedarf auf dieser Seite geladen. 

#### <a name="loading-static-resources-cssjs-asynchronously"></a>Asynchrones Laden von statischen Ressourcen (css/js)

Bei der Arbeit an der Portalimplementierung ist es wichtig zu verstehen, dass Sie das HTML der Seite vollständig verwalten, was bedeutet, dass die üblichen Webentwicklungspraktiken eingehalten werden sollten, um sicherzustellen, dass die Leistung Ihrer Webseite auf der Client-Seite nicht beeinträchtigt wird. 

Eine der häufigsten Ursachen für Performance-Probleme auf Webseiten ist das Laden vieler statischer Ressourcen (css/js) synchron zum Laden der Seite. Das synchrone Laden von großen Mengen an css/js-Dateien kann zu einer langen Verarbeitungszeit für Ihre Webseiten führen. 

Im Fall von Portalen, wenn Sie eine Webdatei direkt mit der Homepage verknüpfen, erstellt es eine Abhängigkeit im generierten HTML, was bedeutet, dass die Webdatei immer zusammen mit der Homepage geladen wird. Wenn es sich bei dieser Webdatei um eine css/js-Datei handelt, wird diese synchron geladen und kann die Verarbeitungszeit auf der Clientseite verlangsamen. 

Um dies zu vermeiden, können Sie die folgenden Schritte durchführen: 

1. Wenn eine Webdatei auf der Startseite nicht benötigt wird, stellen Sie sicher, dass ihre übergeordnete Seite nicht als Startseite festgelegt ist, und verwenden Sie den oben beschriebenen Mechanismus wieder, um sie bei Bedarf zu laden.
2. Wenn Sie eine JavaScript-Datei bei Bedarf auf einer beliebigen Seite laden, verwenden Sie das HTML-Attribut `<async>` oder `<defer>`, um die Datei asynchron zu laden.
3. Beim Laden einer CSS-Datei bei Bedarf können Sie das `<preload>`-HTML-Attribut (https://www.w3.org/TR/preload/) oder einen JavaScript-basierten Ansatz verwenden, da die Vorabversion noch nicht von allen Browsern unterstützt wird.

#### <a name="entity-form-lookup-configuration"></a>Entitätsformular-Suchkonfiguration 

Das Rendern einer Suche als Dropdown-Modus in Entitätsformularen oder Webformularen kann leistungsintensiv sein, wenn die Anzahl der in der Dropdown-Liste angezeigten Datensätze 200 überschreitet und häufig geändert wird. Diese Option sollte nur für statische Suchvorgänge verwendet werden, z. B. für Länder- und Statuslisten mit einer begrenzten Anzahl von Datensätzen.

Wenn diese Option für Suchvorgänge mit einer großen Anzahl von Datensätzen aktiviert ist, wird die Ladezeit der Webseite, auf der das Entitätsformular verfügbar ist, verlangsamt. Wenn diese Seite von vielen Benutzern verwendet und häufig geladen wird, kann dies die gesamte Website verlangsamen, und die Website-Ressourcen werden zum Rendern dieser Seite verwendet. Für diese Situationen sollte eine vollständige Suche verwendet werden, oder ein benutzerdefiniertes HTML-Steuerelement, das einen AJAX-Endpunkt aufruft (der mit Webvorlagen erstellt wurde), sollte für das gewünschte Erscheinungsbild erstellt werden.

#### <a name="number-of-web-roles"></a>Anzahl der Webrollen

Webrollen werden in Portalen verwendet, um die rollenbasierte Zugriffssteuerung zu ermöglichen. In der Regel ist die Anzahl der Webrollen in einem Portal begrenzt, da auch die Anzahl der verschiedenen Kombinationen von Berechtigungen begrenzt ist. Wenn die Anzahl der Webrollen in Ihrem Portal 100 überschreitet, kann dies zu Leistungsproblemen führen, die sich auf alle Seiten Ihres Portals auswirken können.

### <a name="an-active-home-site-marker-is-not-available-for-this-portal"></a>Eine aktive Startseiten-Websitemarkierung ist für dieses Portal nicht verfügbar

Dieses Problem tritt auf, wenn die Websitemarkierung **Startseite** in Ihrer Portalkonfiguration nicht verfügbar ist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Erstellen Sie eine neue Websitemarkierung mit folgenden Werten: 
  - **Name**: Startseite
  - **Webseite** : Wählen Sie die Website Ihres Portal-Hosts aus.
  - **Seite**: Wählen Sie den Webseiteneintrag aus, der als Startseite Ihres Portals festgelegt ist.

### <a name="the-home-site-marker-is-not-pointing-to-any-webpage"></a>Die Startseiten-Websitemarkierung verweist nicht auf eine Webseite.

Dieses Problem tritt auf, wenn die Site-Markierung **Startseite** verfügbar ist, jedoch nicht auf eine Webseite verweist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Startseite**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive Homepage Ihres Portals zu verweisen.

### <a name="the-home-site-marker-is-pointing-to-a-deactivated-web-page"></a>Die Startseiten-Websitemarkierung verweist auf eine deaktivierte Webseite

Dieses Problem tritt auf, wenn die Websitemarkierung **Startseite** verfügbar ist, jedoch auf eine deaktivierte Webseite verweist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Startseite**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive Homepage Ihres Portals zu verweisen.

### <a name="the-home-site-marker-is-not-pointing-to-home-page-of-the-portal"></a>Die Startseiten-Websitemarkierung verweist nicht auf die Homepage des Portals

Dieses Problem tritt auf, wenn die Websitemarkierung **Startseite** verfügbar ist, jedoch auf eine Webseite verweist, die keine Startseite des Portals ist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Startseite**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive Homepage Ihres Portals zu verweisen.

### <a name="an-active-profile-site-marker-is-not-available-for-this-portal"></a>Eine aktive Profilwebsitemarkierung ist für dieses Portal nicht verfügbar

Dieses Problem tritt auf, wenn die Websitemarkierung **Profil** in Ihrer Portalkonfiguration nicht verfügbar ist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Erstellen Sie eine neue Websitemarkierung mit folgenden Werten: 
  - **Name**: Profil
  - **Webseite** : Wählen Sie die Website Ihres Portal-Hosts aus.
  - **Seite**: Wählen Sie den Webseiteneintrag aus, der als Profilseite Ihres Portals festgelegt ist.

### <a name="the-profile-site-marker-is-not-pointing-to-any-webpage"></a>Die Websitemarkierung „Profil“ verweist nicht auf eine Webseite

Dieses Problem tritt auf, wenn die Site-Markierung **Profil** verfügbar ist, jedoch nicht auf eine Webseite verweist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Profil**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive Profilseite Ihres Portals zu verweisen.

### <a name="the-profile-site-marker-is-pointing-to-a-deactivated-web-page"></a>Die Websitemarkierung „Profil“ verweist auf eine deaktivierte Webseite

Dieses Problem tritt auf, wenn die Websitemarkierung **Profil** verfügbar ist, jedoch auf eine deaktivierte Webseite verweist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Profil**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive Profilseite Ihres Portals zu verweisen.

### <a name="an-active-page-not-found-site-marker-is-not-available-for-this-portal"></a>Eine aktive Websitemarkierung „Seite nicht gefunden“ ist für dieses Portal nicht verfügbar

Dieses Problem tritt auf, wenn die Websitemarkierung **Seite nicht gefunden** in Ihrer Portalkonfiguration nicht verfügbar ist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Erstellen Sie eine neue Websitemarkierung mit folgenden Werten: 
  - **Name**: Seite nicht gefunden
  - **Webseite** : Wählen Sie die Website Ihres Portal-Hosts aus.
  - **Seite**: Wählen Sie den Webseiteneintrag aus, der als „Seite nicht gefunden“-Seite Ihres Portals festgelegt ist.

### <a name="the-page-not-found-site-marker-is-not-pointing-to-any-webpage"></a>Die Websitemarkierung „Seite nicht gefunden“ verweist nicht auf eine Webseite

Dieses Problem tritt auf, wenn die Site-Markierung **Seite nicht gefunden** verfügbar ist, jedoch nicht auf eine Webseite verweist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Seite nicht gefunden**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive „Seite nicht gefunden“-Seite Ihres Portals zu verweisen.

### <a name="the-page-not-found-site-marker-is-pointing-to-a-deactivated-web-page"></a>Die Websitemarkierung „Seite nicht gefunden“ verweist auf eine deaktivierte Webseite

Dieses Problem tritt auf, wenn die Site-Markierung **Seite nicht gefunden** verfügbar ist, jedoch auf eine deaktivierte Webseite verweist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Seite nicht gefunden**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive „Seite nicht gefunden“-Seite Ihres Portals zu verweisen.

### <a name="an-active-access-denied-site-marker-is-not-available-for-this-portal"></a>Eine aktive Websitemarkierung „Zugriff verweigert“ ist für dieses Portal nicht verfügbar

Dieses Problem tritt auf, wenn die Websitemarkierung **Zugriff verweigert** in Ihrer Portalkonfiguration nicht verfügbar ist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Erstellen Sie eine neue Websitemarkierung mit folgenden Werten: 
  - **Name**: Zugriff verweigert
  - **Webseite** : Wählen Sie die Website Ihres Portal-Hosts aus.
  - **Seite**: Wählen Sie den Webseiteneintrag aus, der als „Zugriff verweigert“-Seite Ihres Portals festgelegt ist.

### <a name="the-access-denied-site-marker-is-not-pointing-to-any-webpage"></a>Die Websitemarkierung „Zugriff verweigert“ verweist nicht auf eine Webseite

Dieses Problem tritt auf, wenn die Site-Markierung **Zugriff verweigert** verfügbar ist, jedoch nicht auf eine Webseite verweist. So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Zugriff verweigert**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive „Zugriff verweigert“-Seite Ihres Portals zu verweisen.

### <a name="the-access-denied-site-marker-is-pointing-to-a-deactivated-web-page"></a>Die Websitemarkierung „Zugriff verweigert“ verweist auf eine deaktivierte Webseite

Dieses Problem tritt auf, wenn die Websitemarkierung **Zugriff verweigert** verfügbar ist, jedoch auf eine deaktivierte Webseite verweist (Stamm- oder Inhaltsseite können deaktiviert werden). So beheben Sie dieses Problem:

1.  Öffnen Sie die [Portalverwaltungs-App](configure/configure-portal.md).
2.  Wählen Sie im linken Bereich **Websitemarkierungen** aus.
3.  Suchen Sie die Websitemarkierung **Zugriff verweigert**.
4.  Aktualisieren Sie das Feld **Seite**, um auf eine aktive „Zugriff verweigert“-Seite Ihres Portals zu verweisen.

### <a name="profile-web-form-is-not-available-for-contact-entity"></a>Das Profil-Webformular ist für die Kontaktentität nicht verfügbar

Die Profilseite ist eine der allgemeinen Seiten, die in Ihrem Portal für alle profilbezogenen Probleme verwendet werden. Diese Seite zeigt ein Formular, mit dem Benutzer ihr Profil aktualisieren können. Das auf dieser Seite verwendete Formular stammt aus dem Hauptformular **Profilwebseite** in der Kontaktentität. Dieses Formular wird in Ihrer Common Data Service-Umgebung erstellt, in der das Portal bereitgestellt wird. Dieser Fehler wird angezeigt, wenn das Webformular **Profil** in Ihrem Portal entweder gelöscht oder deaktiviert wird. Dieses Formular ist obligatorisch und das Löschen oder Deaktivieren dieses Formulars kann dazu führen, dass die gesamte Website aufgrund eines Laufzeitfehlers im Portal beschädigt wird. Dies ist ein irreparabler Zustand und erfordert eine Neuinstallation des Portals in der Umgebung.

### <a name="published-state-is-not-available-for-this-website"></a>Der Status „Veröffentlicht“ ist für diese Website nicht verfügbar

Stellen Sie sicher, dass die Veröffentlichungsstatus-Entität **Veröffentlicht** verfügbar und aktiv ist, um das Problem zu beheben.

### <a name="published-state-is-not-visible"></a>Veröffentlichungsstatus nicht sichtbar

Um das Problem zu beheben, stellen Sie sicher, dass das Kontrollkästchen **isVisible** der Veröffentlichungsstatus-Entität **Veröffentlicht** aktiviert ist.

### <a name="list-of-entities-with-search-result-having-invalid-url"></a>Liste der Entitäten, bei denen das Suchergebnis eine ungültige URL hat

Stellen Sie sicher, dass ihre Entität über die passenden Sicherheitsberechtigungen verfügt, um das Problem zu beheben.

### <a name="list-of-entities-with-cms-security-check-failed"></a>Liste der Entitäten, bei denen die CMS-Sicherheitsüberprüfung fehlgeschlagen ist

Stellen Sie sicher, dass ihre Entität über die richtige Suchseite verfügt, um das Problem zu beheben.

### <a name="web-file-is-not-active"></a>Webdatei ist nicht aktiv

Stellen Sie sicher, dass die Webdatei den Status „Aktiv“ hat, um dieses Problem zu beheben.

### <a name="the-partial-url-of-web-file-is-misconfigured"></a>Die Teil-URL der Webdatei ist falsch konfiguriert

Um dieses Problem zu beheben, stellen Sie sicher, dass es sich bei der Teil-URL um den Dateinamen mit der Startseite als Stammseite handelt.

### <a name="web-file-doesnt-have-a-file-attachment"></a>Webdatei hat keinen Dateianhang

Um dieses Problem zu beheben, fügen Sie die entsprechende CSS-Datei zum Hinweisabschnitt der Webdatei hinzu.

### <a name="file-attachment-doesnt-have-content"></a>Dateianhang hat keinen Inhalt

Um dieses Problem zu beheben, fügen Sie die CSS-Datei mit dem gesamten Inhalt zum Hinweisabschnitt der Webdatei hinzu.

### <a name="mime-type-of-file-is-not-textcss"></a>MIME-Typ der Datei ist kein Text/CSS

Stellen Sie sicher, dass keine Plug-Ins oder Flows vorhanden sind, die den MIME-Typ der CSS-Datei(en) außer Kraft setzen, um dieses Problem zu beheben.