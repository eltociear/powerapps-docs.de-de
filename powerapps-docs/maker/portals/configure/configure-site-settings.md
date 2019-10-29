---
title: Konfigurieren von Standorteinstellungen für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von Standorteinstellungen für ein Portal und globale Einstellungen für alle Portale in Ihrer Organisation.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 339a8b221474bd9d98ed8e425f730bab1dbb1e0a
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978322"
---
# <a name="configure-site-settings-for-portals"></a>Konfigurieren von Website Einstellungen für Portale

Eine Standort Einstellung ist ein konfigurierbarer, benannter Wert, der vom Website Code verwendet wird, um das Verhalten oder den visuellen Stil des Portals zu ändern. Wenn ein Entwickler den Website Code erstellt, verweist er in der Regel auf Site Einstellungen für verschiedene Komponenten, damit Endbenutzer die Einstellungs Werte ändern können, um die Website zu ändern, ohne den Code ändern, kompilieren und die Website erneut bereitstellen zu müssen.

Die in der Installation der powerapps-Portale bereitgestellten Beispiel Portale enthalten mehrere konfigurierbare Site Einstellungen für verschiedene Stile, mit denen viele visuelle Elemente innerhalb der Site geändert werden, wie z. b. Hintergrund Stil, Textfarbe und Layoutbreite.
Sie können die folgenden Arten von Standorteinstellungen verwalten:

- **Globale Portal Einstellungen**: Diese Einstellungen gelten für alle Portale, die der Common Data Service Umgebung zugeordnet sind, in der Sie hinzugefügt werden.
- **Portal Site Einstellungen**: Diese Einstellungen gelten für bestimmte Portale (Website Datensätze), die der Common Data Service Umgebung zugeordnet sind, in der Sie hinzugefügt werden.


## <a name="manage-portal-site-settings"></a>Portal Site Einstellungen verwalten

1. Wechseln Sie zu den [Portal Einstellungen](../manage-existing-portals.md#settings) , und wählen Sie **Website Einstellungen**aus.

2. Wählen Sie **neu**aus, um eine neue Einstellung zu erstellen.

3. Wählen Sie die im Raster aufgelistete **Website Einstellung** aus, um eine vorhandene Einstellung zu bearbeiten.

4. Geben Sie Werte für die angegebenen Felder an: 

    - **Name**: eine Bezeichnung, auf die über den Website Code verwiesen wird, um die entsprechende Einstellung abzurufen. Der Name muss für die zugehörige Website eindeutig sein, da der Code, der die Einstellung abruft, den ersten Datensatz mit dem übereinstimmenden Namen erhält.
    
    - **Website**: die zugehörige Website. 
    
    - **Wert**: die Einstellung
    
    - **Beschreibung**: Zweck der Einstellung oder spezieller Anweisungen.

5. Wählen Sie **Speichern und Schließen** aus.

> [!NOTE] 
> Die Integration von Integration in Deutschland wird in der deutschen unabhängigen Cloud nicht unterstützt. Wenn Sie versuchen, die Einstellung bingmaps/Anmelde Informationen in dieser Umgebung zu erstellen, wird eine Fehlermeldung angezeigt.

## <a name="portal-site-settings"></a>Portal Website Einstellungen

|Name|Value|Beschreibung|
|----|-----|-----------|
|Authentifizierung/Registrierung/Requirements-Bestätigung|Alarm |Der boolesche Wert true aktiviert die e-Mail-Bestätigung und deaktiviert die öffnende Registrierung. Standardwert: false |
|Authentifizierung/Registrierung/Autorisierung|Alarm |Der boolesche Wert true aktiviert das Feature "Einladungscode" und deaktiviert die offene Registrierung. Standardwert: false |
|Konferenz Name|Portale-Konferenz|Der Name eines adx_conference-Datensatzes, der die Konferenz für ein bestimmtes Portal darstellt.|
|Helpdesk/caseberelementaktivierte|Fall|Ein boolescher Wert, der angibt, ob die Berechtigung des Helpdesk-falls aktiviert ist. Standardwert: false|
|Helpdesk/Ablenkung/defaultselectedproductname| |Der Name eines Produktdaten Satzes, bei dem es sich um das in der Dropdown Liste ausgewählte Standardprodukt handelt, wenn mehr als ein Produkt vorhanden ist, bei dem der producttypeer-Code 100000001 entspricht.|
|Profil/forcesignup|Alarm|Ein boolescher Wert, wenn er auf "true" festgelegt ist, zwingt den Benutzer, seine Profilinformationen zu aktualisieren, bevor ihm der Zugriff auf den Inhalt der Website gewährt wird. Standardwert: false|
|Profil/showmarketingoptionspanel|Fall|Ein boolescher Wert, der angibt, ob der Bereich, in dem die Felder aufgelistet werden, angezeigt werden soll, um die Kommunikationseinstellungen für Marketing im Profil anzugeben. Standardwert: false|
|Suchen/aktivieren|Fall|Ein boolescher Wert, der angibt, ob die Suche aktiviert ist.|
|suchen/filtern|Inhalt: adx_webpage; Ereignisse: adx_event, adx_eventschedule;<br>Blogs: adx_blog, adx_blogpost, adx_blogpostcomment;<br>Foren: adx_communityforum, adx_communityforumthread, adx_communityforumpost;<br>Ideen: adx_ideaforum, adx_idea, adx_ideacomment;<br>Probleme: adx_issueforum, adx_issue, adx_issuecomment; Helpdesk: Incident|Eine Auflistung von Filteroptionen für den logischen Such Namen. Wenn Sie hier einen Wert definieren, werden der Site weiten Suche Dropdown Filteroptionen hinzugefügt. Dieser Wert sollte in Form von Name-Wert-Paaren vorliegen, wobei Name und Wert durch einen Doppelpunkt getrennt sind, und Paare, die durch ein Semikolon voneinander getrennt sind.<br>Beispiel: "Foren: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment ".|
|Search/indexqueryname|Portal Suche|Der Name der von der Portal Suchabfrage verwendeten Systemansicht. Standard: Portal Suche|
|Suchen/Abfragen|\+ (@Query) _title:(@Query) _logicalname: adx_webpage ~ 0.9 ^ 0,2<br> -_logicalname: adx_webfile ~ 0.9 adx_partialurl:(@Query)<br> _logicalname: adx_blogpost ~ 0.9 ^ 0,1-_logicalname: adx_communityforumthread ~ 0.9|Überschreiben Sie die Abfrage für die Suche nach Websites, um zusätzliche Gewichtungen und Filter anzuwenden. @Query ist der von einem Benutzer eingegebene Abfragetext. Lucene-Abfrage Syntax Referenz: [http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](http://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|Suchen/Wort Stamm Erkennung|Englisch|Die Sprache, die vom Wort Stamm Algorithmus der Portal Suche verwendet wird. Standard: Englisch|
|Customersupport/displayalluseractivitiesontimeline|Alarm| |
|Authentication/[Protokoll]/[Anbieter]/AllowContactMappingWithEmail| |Ermöglicht die automatische Zuordnung zu einem Kontaktdaten Satz basierend auf der e-Mail. Klicken Sie [hier](https://docs.microsoft.com/en-us/dynamics365/portals/azure-ad-b2c#allow-auto-association-to-a-contact-record-based-on-email), um weitere Informationen zu erhalten.|
|||

Website Einstellungen für verschiedene Portal Features finden Sie unter:

- [Authentifizierungs Identität](set-authentication-identity.md)
- [Azure AD B2C Anbieter](azure-ad-b2c.md)
- [OAuth 2,0](configure-oauth2-settings.md)
- [Open ID Connect](configure-openid-settings.md)
- [WS-Verbund](configure-ws-federation-settings.md)
- [SAML 2,0](configure-saml2-settings.md)
- [Identitäts Anbieter zu Azure AD B2C migrieren](migrate-identity-providers.md)
- [In Datei Anlagen Inhalt suchen](https://docs.microsoft.com/dynamics365/customer-engagement/portals/search-file-attachment)
- [Verhalten und Format des Felds "Datum und Uhrzeit"](https://docs.microsoft.com/dynamics365/customer-engagement/portals/behavior-format-date-time-field)
- [Geolozierung hinzufügen](https://docs.microsoft.com/dynamics365/customer-engagement/portals/add-geolocation)
- [Felddienst integrieren](https://docs.microsoft.com/dynamics365/customer-engagement/portals/integrate-field-service)
- [Implementieren allgemeiner Datenschutzbestimmungen](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [Zwischenspeichern von Kopf-und Fußzeilen Ausgabe aktivieren](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>Verwalten der Einstellungen des globalen Portals

1. Wechseln Sie zu den [Portal Einstellungen](../manage-existing-portals.md#settings) , und wählen Sie **Website Einstellungen**aus.

2. Wechseln Sie zu **Einstellungen** &gt; **Einstellungen**.

3. Wählen Sie **neu**aus, um eine neue Einstellung zu erstellen.

4. Wählen Sie die im Raster aufgelistete **Website Einstellung** aus, um eine vorhandene Einstellung zu bearbeiten.

5. Geben Sie Werte für die angegebenen Felder an: 

    - **Name**: ein eindeutiger Name, auf den von Code verwiesen wird, um die entsprechende Einstellung abzurufen.

    - **Wert**: die Einstellung

    - **Beschreibung**: Zweck der Einstellung oder spezieller Anweisungen.

6. Wählen Sie **Speichern und Schließen** aus.

> [!NOTE] 
> Die Integration von Integration in Deutschland wird in der deutschen unabhängigen Cloud nicht unterstützt. Wenn Sie versuchen, die Einstellungen binmap/Key oder adxstudio/productivitypack/bingmap/Key in dieser Umgebung zu erstellen, wird eine Fehlermeldung angezeigt.


