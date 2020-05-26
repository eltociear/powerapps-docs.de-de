---
title: Globale Suche nach zusätzlichen Entitäten im Power Apps-Portal | MicrosoftDocs
description: Erfahren Sie, wie die globale Suche nach zusätzlichen Entitäten in einem Portal funktioniert.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/28/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: e1091709e096d7b7b53c5f4e02f4b84d15cd952e
ms.sourcegitcommit: 8dd68565e03a4e66db1f8937630fa4c52eb93871
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "3321287"
---
# <a name="walkthrough-configuring-additional-entitiesforglobalsearch"></a>Komplettlösung: Konfigurieren zusätzlicher Entitäten für die globale Suche  

## <a name="overview"></a>Überblick

Sie können zusätzliche Entitäten für Suchfunktionen aktivieren. Die Konfiguration der Suche nach zusätzlichen Entitäten erfordert zusätzliche Aktionen, die in diesem Artikel beschrieben werden.

Die folgenden Überlegungen gelten für die Konfiguration zusätzlicher Entitäten für die globale Suche:

- Stellen Sie sicher, dass die Einstellung [Site-Einstellung](#site-setting-for-additional-entities) für die Suche nach zusätzlichen Entitäten aktiviert ist.
- Erstellen Sie eine Ansicht mit dem Namen **Portalsuche** für jede zusätzliche Entität, nach der Sie die Suche aktivieren möchten. Weitere Informationen: [durchsuchbare Felder in der globalen Suche](search.md#fields-searchable-in-global-search)
- Stellen Sie sicher, dass eine **Entitätsberechtigung** erstellt wird, die Leseberechtigung und angemessenen Umfang für die Anzeige der Datensätze in den Suchergebnissen bietet.
- Ordnen Sie die Berechtigung der Entität den erforderlichen **Web-Rollen** zu.
- Berechtigungen für Entitäten müssen mit der **Anonyme Web-Rolle** verknüpft sein, wenn Sie die anonyme Suche nach einer Entität erlauben wollen.
- Konfigurieren Sie eine [Suchergebnisseite](#results-page-for-additional-entities) zur Anzeige der Suchergebnisse.

Die oben erläuterte explizite Konfiguration stellt sicher, dass keine Datensätze versehentlich über die globale Suche zur Verfügung gestellt werden.

### <a name="site-setting-for-additional-entities"></a>Site-Einstellung für zusätzliche Entitäten

Die Website-Einstellung **Search/EnableAdditionalEntities** ist erforderlich, wenn zusätzliche Entitäten für die Suche konfiguriert werden.

> [!IMPORTANT]
> **Search/EnableAdditionalEntities** dient explizit dazu, die Suche nach zusätzlichen Entitäten zu ermöglichen. Die Einstellung der Hauptsuchseite **Search/Enabled** muss auf **wahr** gesetzt werden, wenn die Suchfunktion verwendet wird.

Sie können auch andere verwandte Site-Einstellungen ähnlich der Suchkonfiguration für Standard-Entitäten konfigurieren. Sie können z.B. die Einstellung **Search/Filters** verwenden, um zusätzliche Entitäten zu konfigurieren und der globalen Suche eine Dropdown-Filteroption hinzuzufügen. Weitere Informationen: [Einstellung der Website](search.md#related-site-settings)

### <a name="results-page-for-additional-entities"></a>Ergebnisseite für weitere Entitäten

Die Suchergebnisseite wird über eine **Seitenmarkierung** mit der Bezeichnung ```<entitylogicalname>_SearchResultPage``` konfiguriert.

Wenn der logische Name Ihrer Entitäten beispielsweise *nwind_products* lautet, ist die Sitemarkierung ```nwind_products_SearchResultPage```. Der Wert der Website-Markierung ist die Seite, die Sie öffnen möchten, wenn das Suchergebnis ausgewählt wird. Standardmäßig wird eine Datensatz-ID im Parameter *id* Abfragezeichenfolge an die Suchergebnisseite übergeben.

Stellen Sie sicher, dass Ihre Suchergebnisseite eine Entitätsform oder eine Logik hat, die die Suchergebnisdetails anzeigt.

## <a name="walkthrough---configure-search-for-additional-entities-with-sample-database"></a>Komplettlösung - Konfigurieren der Suche nach zusätzlichen Entitäten mit Beispieldatenbank

Die folgende Komplettlösung erklärt, wie die Suche nach der Entität **Produkte bestellen** in der Beispieldatenbank **Nordwind**, verfügbar mit Common Data Service, aktiviert wird.

Weitere Informationen über Beispieldatenbanken finden Sie unter [Datenbank und Apps von Northwind Traders installieren](../../canvas-apps/northwind-install.md).

> [!TIP]
> Sie können der exemplarischen Vorgehensweise mit einer Entität Ihrer Wahl folgen, indem Sie *Wind_products* Entitätsname durch den logischen Namen Ihrer Entität ersetzen.

## <a name="step-1-add-or-update-search-site-settings"></a>Schritt 1: Hinzufügen oder Aktualisieren der Einstellungen der Such-Website

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Stellen Sie sicher, dass Sie sich in der entsprechenden Umgebung befinden, in der Ihr Portal existiert.

1. Wählen Sie **Apps** im linken Navigationsbereich und suchen Sie die **Portalmanagement** modellbasierte App.  

    ![Portalverwaltung](media/search-additional-entities/portal-management.png "Portalverwaltung")

    >[!NOTE]
    > Die Portal Management App könnte **Dynamics 365 Portale** heißen, wenn Sie sich in einer Umgebung befinden, in der Dynamics 365 Apps installiert sind.

1. Wählen Sie, um die App **Portalverwaltung** zu öffnen, und gehen Sie dann zu **Standorteinstellungen** im linken Navigationsbereich.

1. Erstellen Sie eine neue Einstellung, **Search/EnableAdditionalEntities**, und setzen Sie ihren Wert auf **true**.

    ![Site-Einstellung für EnableAdditionalEntities](media/search-additional-entities/enableadditionalentitiessearch-sitesetting.png "Website-Einstellung für EnableAdditionalEntities")

1. Erstellen oder aktualisieren Sie die Einstellung **Suche/Filter** und fügen Sie den Wert **Products:nwind_products** hinzu.

    ![Suche/Filter-Standorteinstellung](media/search-additional-entities/search-filters.png "Einstellung der Suche/Filter-Website")

## <a name="step-2-create-or-verify-the-portal-search-view"></a>Schritt 2: Erstellen oder überprüfen Sie die Ansicht Portalsuche

> [!NOTE]
> Für die folgenden Schritte muss die [Northwind Traders Lösung](../../canvas-apps/northwind-install.md) installiert werden. Wenn Sie eine andere Entität verwenden möchten, verwenden Sie die entsprechende Lösung oder verwenden Sie die Standardlösung.

1. Gehen Sie zu [Power Apps](https://make.powerapps.com), und wählen Sie **Lösungen** im linken Navigationsbereich.

1. Wählen Sie **Northwind Traders**.

    ![Lösung auswählen](media/search-additional-entities/select-solution.png "Lösung auswählen")

1. Suchen Sie nach **Produkt bestellen** Entitäten.

    ![Produkt-Einheit bestellen](media/search-additional-entities/order-product.png "Entitäten Produkt bestellen")

1. Wählen Sie die Entität **Produkt bestellen** und wählen Sie dann **Ansichten**.

    ![Ansichten](media/search-additional-entities/views.png "Ansichten")

1. Stellen Sie sicher, dass in der Liste der Ansichten **Portalsuche** angezeigt wird.

    ![Portal-Suchansicht](media/search-additional-entities/portal-search.png "Portal-Suchansicht")

    Wenn die Ansicht "Portalsuche" noch nicht vorhanden ist, wählen Sie **Ansicht hinzufügen**, geben Sie den Namen als **Portalsuche** ein und wählen Sie dann **Erstellen**.

    ![Ansicht hinzufügen](media/search-additional-entities/add-view.png "Ansicht hinzufügen")

    ![Ansicht Portalsuche hinzufügen](media/search-additional-entities/portal-search-view.png "Ansicht Portalsuche hinzufügen")

1. Stellen Sie sicher, dass der Ansicht für die Suche entsprechende Spalten hinzugefügt werden.

    ![Hinzufügen von Spalten](media/search-additional-entities/add-columns.png "Hinzufügen von Spalten")

1. Wenn Sie die Ansicht bearbeitet haben, stellen Sie sicher, dass Sie **Speichern** und dann **Veröffentlichen** wählen, bevor Sie fortfahren.

    ![Speichern und Veröffentlichen](media/search-additional-entities/save-publish.png "Ansicht speichern und veröffentlichen")

## <a name="step-3-create-entity-permissions"></a>Schritt 3: Berechtigungen für Entitäten erstellen

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie links im Navigationsbereich **Apps** aus, und öffnen Sie dann die modellgesteuerte App **Portalverwaltung**.  

1. Wählen Sie **Berechtigungen für Entitäten** im linken Navigationsbereich.

1. Wählen Sie **Neu**.

    ![Erlaubnisdatensatz für neue Entität](media/search-additional-entities/new-entity-permission.png "[Neuer Entitätsgenehmigungsdatensatz")

1. Geben Sie den Namen als **Nordwind-Produkte Alle lesen** ein und wählen Sie dann das entsprechende **Bereich** und das **Lesen** Privileg.

    In diesem Beispiel wird der Bereich **Global** der Entität **nwind_products** zur Verfügung gestellt.

    ![Umfang- und Leseberechtigungen](media/search-additional-entities/scope-read.png "Geltungsbereich und Leseberechtigungen")

1. Klicken Sie auf **Speichern und Schließen**.

1. Wählen und öffnen Sie **Nordwind-Produkte Alle lesen**.

1. Scrollen Sie nach unten zum Abschnitt **Webrollen** und wählen Sie dann **Bestehende Webrolle hinzufügen**.

    ![Bestehende Webrolle hinzufügen](media/search-additional-entities/add-existing-web-role.png "Fügen Sie eine vorhandene Webrolle hinzu")

1. Suchen Sie nach **Authentifizierte Benutzer**, und wählen Sie dann **Hinzufügen**:

    ![Authentifizierte Benutzer hinzufügen](media/search-additional-entities/add-authenticated-users.png "Hinzufügen authentifizierter Benutzer")

## <a name="step-4-add-a-webpage"></a>Schritt 4: Hinzufügen einer Webseite

1. Gehen Sie zu [Power Apps](https://make.powerapps.com), und wählen Sie **Apps** im linken Navigationsbereich.

1. Wählen Sie **Weitere Befehle** (...) für das Portal, und wählen Sie dann **Bearbeiten**, um das Portal in Power Apps Studio zu öffnen.

1. Wählen Sie **Neue Seite** aus dem Menü in der oberen linken Ecke und wählen Sie dann das Layout **Leer** für die Seite.

    ![Neue Seite](media/search-additional-entities/new-page.png "Neue Seite")

1. Geben Sie den Webseitennamen als **Produkte bestellen** ein. Diese Seite wird als Suchergebnisseite konfiguriert.

1. Wählen Sie **Komponenten** im linken Navigationsbereich und fügen Sie dann eine **Formular** Komponente zu dieser Webseite hinzu.

    ![Formularbestandteil hinzufügen](media/search-additional-entities/form-component.png "Eine Formular-Komponente hinzufügen")

1. Wählen Sie die Option **Bestehende verwenden** auf der rechten Seite Ihres Arbeitsbereichs, wählen Sie das Formular **Produkte anzeigen** für die Entität **Produkte abspulen** und setzen Sie dann **Modus** auf **Nur lesen**.

    ![Modus einstellen](media/search-additional-entities/mode.png "Stellen Sie den Modus")

## <a name="step-5-add-a-site-marker-for-the-search-results-details-page"></a>Schritt 5: Fügen Sie eine Website-Markierung für die Detailseite der Suchergebnisse hinzu

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie **Apps** im linken Navigationsbereich und wählen Sie **Portal Management** modellbasierte App.  

1. Wählen Sie **Site-Markierung** im linken Navigationsbereich.

1. Wählen Sie **Neu** und erstellen Sie dann eine neue Site-Markierung unter Verwendung der folgenden Details:

    - **Name:** **nwind_products_SearchResultPage**
    - **Seite:** **Produkte bestellen**
    
    ![Neue Standortmarkierung](media/search-additional-entities/new-site-marker.png "Neue Site-Markierung")

## <a name="step-6-rebuild-the-search-index"></a>Schritt 6: Erstellen Sie den Suchindex neu

1. Durchsuchen Sie Ihr Portal mit einem Benutzerkonto, dem die Webrolle Administrator zugewiesen wurde.

1. Hängen Sie die URL in der Adressleiste mit **/_services/about** an und wählen Sie dann **Eingabe**.

   ![_services_about Seite](media/search-additional-entities/services-about.png "_services_about page")

1. Wählen Sie [Cache löschen](https://docs.microsoft.com/powerapps/maker/portals/admin/clear-server-side-cache) aus.

1. Nachdem Sie den Cache gelöscht haben, wählen Sie [Suchindex neu aufbauen](search.md#rebuild-full-search-index).

## <a name="step-7-verify-that-global-search-works-with-the-custom-entity"></a>Schritt 7: Überprüfen Sie, ob die globale Suche mit der benutzerdefinierten Entität funktioniert

1. Navigieren Sie zum Portal mit einem Benutzer, dem *Authentifiziert* **Web-Rolle** zugewiesen wurde.

1. Gehen Sie zur Suchsymbolleiste oder zur Suchseite und suchen Sie nach einem bekannten Datensatz.

   Verwenden Sie z.B. das Suchwort **Northwind Clam Chowder**, um Ergebnisse anzuzeigen, die mit der Entität **nwind_products** verknüpft sind.

   ![Suchergebnisse](media/search-additional-entities/search-results.png "Suchergebnisse")

## <a name="next-steps"></a>Nächste Schritte

[Entfernen einer Entität aus der globalen Suche](search.md#remove-an-entity-from-global-search)

### <a name="see-also"></a>Siehe auch

[Suchbezogene Website-Einstellungen](search.md#related-site-settings)