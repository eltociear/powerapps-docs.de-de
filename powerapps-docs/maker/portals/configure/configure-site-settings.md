---
title: Konfigurieren der Websiteeinstellungen für ein Portal | MicrosoftDocs
description: Anweisungen, Standortseinstellungen und Einstellungen für Portal- und globale Einstellungen für alle Portale im Unternehmen hinzuzufügen und zu konfigurieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 19dca44c26565bc55dcfaace48987b69dd0a195f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759554"
---
# <a name="configure-site-settings-for-portals"></a>Konfigurieren Sie Websiteeinstellungen für Portale

Eine Website-Einstellung ist ein konfigurierbarer benannter Wert, der von Websitecode verwendet wird, um das Verhalten oder die visuelle Darstellung des Portals zu ändern. Normalerweise, wenn ein Entwickler Websitecode erstellt, verweist er Website-Einstellungen für verschiedene Komponenten, damit der Endbenutzer die Einstellungswerte ändern kann, um die Website zu ändern, ohne den Code zu ändern und die Website neu zu kompilieren und bereitstellen zu müssen.

Die Beispielportale, die mit der Installation von PowerApps-Portalen verfügbar sind, enthalten mehrere konfigurierbare Website-Einstellungen für verschiedene Stile, die verwendet werden, um viele Sichtelemente innerhalb der Website zu ändern, wie Hintergrundstil, Textfarbe und Layoutbreite.
Die folgenden Typen von Websiteeinstellungen können verwaltet werden:

- **Globale Portaleinstellungen**: Diese Einstellungen gelten für alle Portale, die der Common Data Service-Umgebung zugeordnet sind, in der sie hinzugefügt werden.
- **Portalwebsite-Einstellungen**: Diese Einstellungen gelten für spezifische Portale (Websitedatensätze), die der Common Data Service-Umgebung zugeordnet sind, in der sie hinzugefügt werden.


## <a name="manage-portal-site-settings"></a>Verwalten von Portalwebsite-Einstellungen

1. Rufen Sie die [Portaleinstellungen](../manage-existing-portals.md#settings) auf und wählen Sie **Website-Einstellungen**.

2. Klicken Sie auf **Neu**, um eine neue Einstellung zu erstellen.

3. Wenn Sie eine vorhandene Einstellung bearbeiten möchten: klicken Sie auf die **Websiteeinstellung**, die im Raster aufgelistet ist.

4. Geben Sie die Werte für die bereitgestellten Felder an: 

    - **Name**: Eine durch Websitecode verwiesene Beschriftung, um die entsprechende Einstellung abzurufen. Der Name sollte für die zugehörige Website eindeutig sein, da der Code, der die Einstellung abruft, den ersten Datensatz wählt, der mit dem entsprechenden Namen gefunden wird.
    
    - **Website**: Die zugeordnete Website. 
    
    - **Wert**: Die Einstellung
    
    - **Beschreibung**: Der Zweck der Einstellung oder Spezialanweisungen.

5. Klicken Sie auf **Speichern und schließen**.

> [!NOTE] 
> Die Bing Maps-Integration wird in der deutschen Sovereign Cloud nicht unterstützt. Wenn Sie versuchen, die Einstellung für Bingmaps/Anmeldeinformationen in dieser Umgebung zu erstellen, wird eine Fehlermeldung angezeigt.

## <a name="portal-site-settings"></a>Portalseiteneinstellungen

|Name|Value|Beschreibung|
|----|-----|-----------|
|Authentication/Registration/RequiresConfirmation|FALSCH |Ein boolescher Wert von "Wahr" aktiviert die E-Mail-Bestätigung und deaktiviert die offene Registrierung. Standard: Falsch |
|Authentication/Registration/RequiresInvitation|FALSCH |Ein boolescher Wert von "Wahr" aktiviert die Einladungscodefunktion und deaktiviert die offene Registrierung. Standard: Falsch |
|conference-name|Portalkonferenz|Der Name eines adx_conference-Datensatzes, der die Konferenz für ein gegebenes Portal darstellt.|
|HelpDesk/CaseEntitlementEnabled|WAHR|Ein boolescher Wert, der angibt, ob Helpdesk-Anfrageberechtigung aktiviert ist. Standard: false|
|Helpdesk/Abweisung/DefaultSelectedProductName| |Der Name eines Produktdatensatzes, der das standardmäßig ausgewählte Produkt in der Dropdownliste ist, wird auf der Helpdesk-Fallabweisung angezeigt wird, wenn bei mehr als einem Produkt der Produkttypcode 100000001 gleicht.|
|Profil/ForceSignUp|FALSCH|Ein boolescher Wert der den Benutzer, wenn er auf "Wahr" festgelegt ist, seine Profilinformationen zu aktualisieren, bevor sie Zugriff auf die Websiteinhalte erhalten. Standard: Falsch|
|Profil/ShowMarketingOptionsPanel|WAHR|Ein boolescher Wert, der angibt, ob der Bereich angezeigt wird, in dem die Felder aufgeführt werden, in denen die Marketingkommunikationseinstellungen im Profil angegeben werden. Standard: Falsch|
|Suche/Aktivieren|WAHR|Ein boolescher Wert, der angibt, ob die Suche aktiviert ist oder nicht.|
|Suche/Filter|Content:adx_webpage;Events:adx_event,adx_eventschedule;<br>Blogs:adx_blog,adx_blogpost,adx_blogpostcomment;<br>Foren: adx_communityforum, adx_communityforumthread, adx_communityforumpost;<br>Ideas:adx_ideaforum,adx_idea,adx_ideacomment;<br>Probleme:adx_issueforum,adx_issue,adx_issuecomment;Help Desk:Vorfall|Eine Sammlung von Filteroptionen für logische Suchbegriffe. Wenn Sie hier einen Wert definieren, werden der Site-weiten Suche Dropdown-Filteroptionen hinzugefügt. Dieser Wert sollte in Form von Name/Wert-Paaren vorliegen, wobei Name und Wert durch einen Doppelpunkt und Paare durch ein Semikolon getrennt sind.<br>Zum Beispiel "Foren:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment".|
|Suchen/IndexQueryName|Portalsuche|Der Name der Systemansicht wird von der Portalsucheabfrage verwendet. Standard: Portalsuche|
|Suche/Abfrage|+(@Query) _title:(@Query) _logicalname:adx_webpage~0.9^0.2<br> -_logicalname:adx_webfile~0.9 adx_partialurl:(@Query)<br> _logicalname:adx_blogpost~0.9^0.1 -_logicalname:adx_communityforumthread~0.9|Außerkraftsetzung der Abfrage für Standortssuche, um zusätzliche Gewichtungen und Filter anzuwenden. @Query ist der Abfragetext, der von einem Benutzer eingegeben wird. Lucene-Abfragesyntaxverweis: [https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|Suchen/Wortstammerkennungen|Englisch|Die Sprache, die vom Wortstammerkennungsalgorithmus der Portalsuche verwendet wird. Standard: Englisch|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|FALSCH| |
|Authentication/[Protokoll]/[Anbieter]/AllowContactMappingWithEmail| |Zulassen der automatischen Zuordnung zu einem Kontaktdatensatz auf Grundlage der E-Mail-Adresse. Weitere Informationen erhalten Sie [hier](azure-ad-b2c.md#allow-auto-association-to-a-contact-record-based-on-email).|
|||

Für die Website-Einstellungen bezüglich verschiedener Portalfunktionen siehe:

- [Authentifizierungsidentität](set-authentication-identity.md)
- [Azure AD-B2C-Anbieter](azure-ad-b2c.md)
- [OAuth 2.0](configure-oauth2-settings.md)
- [Offener ID-Inhalt](configure-openid-settings.md)
- [WS-Verbund](configure-ws-federation-settings.md)
- [SAML 2.0](configure-saml2-settings.md)
- [Identitätsanbieter nach Azure AD B2C migrieren](migrate-identity-providers.md)
- [Suche im Dateianhangsinhalt](search-file-attachment.md)
- [Verhalten und Format des Datums- und Uhrzeitfelds](behavior-format-date-time-field.md)
- [Hinzufügen einer Geolocation](add-geolocation.md)
- [Datenschutz-Grundverordnung implementieren](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [Zwischenspeichern von Kopfzeilen- und Fußzeilenausgaben aktivieren](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>Verwalten von globalen Portaleinstellungen

1. Rufen Sie die [Portaleinstellungen](../manage-existing-portals.md#settings) auf und wählen Sie **Website-Einstellungen**.

2. Navigieren Sie zu **Einstellungen** &gt; **Einstellungen**.

3. Klicken Sie auf **Neu**, um eine neue Einstellung zu erstellen.

4. Wenn Sie eine vorhandene Einstellung bearbeiten möchten: klicken Sie auf die **Websiteeinstellung**, die im Raster aufgelistet ist.

5. Geben Sie die Werte für die bereitgestellten Felder an: 

    - **Name**: Ein durch Code verwiesener eindeutiger Name, um die entsprechende Einstellung abzurufen.

    - **Wert**: Die Einstellung

    - **Beschreibung**: Der Zweck der Einstellung oder Spezialanweisungen.

6. Klicken Sie auf **Speichern und schließen**.

> [!NOTE] 
> Die Bing Maps-Integration wird in der deutschen Sovereign Cloud nicht unterstützt. Wenn Sie versuchen, die Einstellung BinMap/Key oder Adxstudio/ProductivityPack/BingMap/Key in dieser Umgebung zu erstellen, wird eine Fehlermeldung angezeigt.


