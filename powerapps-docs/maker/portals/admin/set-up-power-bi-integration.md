---
title: Einrichten der Power BI-Integration mit Ihrem Portal | MicrosoftDocs
description: Informationen zum Einrichten der Power BI-Integration mit dem Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6a471dba2f91ca869ad9ba9da46f6e02cb2a643d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756738"
---
# <a name="set-up-power-bi-integration"></a>Power BI-Integration einrichten

Power BI ist eines der besten Tools zur Vermittlung von Erkenntnissen mit einfacher und interaktiver Visualisierung. Um Dashboards und Berichte von Power BI auf Webseiten in einem Portal anzeigen zu können, müssen Sie die Power BI-Visualisierung über das PowerApps-Portal-Administratorcenter aktivieren. Sie können auch Dashboards und Berichte einbetten, die im neuen Arbeitsbereich von Power BI erstellt werden, indem Sie die Power BI Embedded-Dienstintegration aktivieren.

> [!NOTE]
> - Sie müssen über eine entsprechende Power BI-Lizenz verfügen.
> - Um den Power BI Embedded-Dienst nutzen zu können, müssen Sie über eine entsprechende Power BI Embedded-Lizenz verfügen. Weitere Informationen finden Sie unter [Lizenzierung](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing).

## <a name="enable-power-bi-visualization"></a>Power BI-Visualisierung aktivieren

Wenn Sie die Power BI-Visualisierung aktivieren, können Sie Dashboards und Berichte auf Webseiten in ein Portal einbetten, indem Sie das Powerbi-Liquid-Tag verwenden.

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Wechseln Sie zu **Einrichten der Power BI Integration** > **Aktivieren der Power BI-Visualisierung**.

    > [!div class=mx-imgBorder]
    > ![Power BI-Visualisierung aktivieren](../media/enable-power-bi-visualization.png "Power BI-Visualisierung aktivieren")

3.  Wählen Sie in der Bestätigungsmeldung **Aktivieren** aus. Während die Power BI-Visualisierung aktiviert wird, startet das Portal neu und ist für einige Minuten nicht verfügbar. Eine Meldung wird angezeigt, wenn die Power BI-Visualisierung aktiviert ist.

Systemanpasser können das Liquid-Tag [powerbi](../liquid/portals-entity-tags.md#powerbi) verwenden, um Power BI-Dashboards und -Berichte auf Webseiten in einem Portal einzubetten. Beim Einbetten des Power BI-Inhalts können Systemanpasser mit [Filterparametern](https://docs.microsoft.com/power-bi/service-url-filters) personalisierte Ansichten erstellen. Weitere Informationen: [Liquid-Tag powerbi](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Power BI-Visualisierung deaktivieren

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Wechseln Sie zu **Einrichten der Power BI Integration** > **Deaktivieren der Power BI-Visualisierung**.

    > [!div class=mx-imgBorder]
    > ![Power BI-Visualisierung deaktivieren](../media/disable-power-bi-visualization.png "Power BI-Visualisierung deaktivieren")

3. Wählen Sie in der Bestätigungsmeldung **Deaktivieren** aus. Während die Power BI-Visualisierung deaktiviert wird, startet das Portal neu und ist für einige Minuten nicht verfügbar. Eine Meldung wird angezeigt, wenn die Power BI-Visualisierung deaktiviert ist.

## <a name="enable-power-bi-embedded-service"></a>Power BI Embedded-Dienst aktivieren

Mit dem Power BI Embedded-Dienst können Sie auch Dashboards und Berichte einbetten, die im neuen Arbeitsbereich von Power BI erstellt werden. Die Dashboards und Berichte werden auf Webseiten in einem Portal eingebettet, indem der Liquid-Tag powerbi verwendet wird.

**Voraussetzungen**: Bevor Sie den Power BI Embedded-Dienst aktivieren, stellen Sie sicher, dass Sie Ihre Dashboards und Berichte im neuen Arbeitsbereich in Power BI erstellt haben. Nachdem Sie den Arbeitsbereich erstellt haben, geben Sie dem globalen Administrator einen Administratorzugang, damit die Arbeitsbereiche im PowerApps-Portal-Administratorcenter angezeigt werden. Weitere Informationen zum Erstellen neuer Arbeitsbereiche und zum Gewähren von Zugriffen für diese finden Sie unter [Erstellen neuer Arbeitsbereiche in Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces).

**Power BI Embedded-Dienstbeschränkungen**: Weitere Informationen zu Beschränkungen finden Sie unter [Überlegungen und Beschränkungen](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations).

> [!NOTE]
> Stellen Sie sicher, dass die Power BI-Visualisierung aktiviert ist, damit das Liquid-Tag powerbi funktioniert.

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Einrichten der Power BI-Integration** > **Aktivieren des Power BI Embedded-Dienstes**.

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded-Dienst aktivieren](../media/enable-powerbi-embedded-button.png "Power BI Embedded-Dienst aktivieren")

3. Wählen Sie im Fenster **Integration des Power BI Embedded-Diensts aktivieren** die Power BI-Arbeitsbereiche aus, für die Dashboards und Berichte in Ihrem Portal angezeigt werden müssen, und verschieben Sie sie in die Liste **Ausgewählte Arbeitsbereiche**.

    > [!div class=mx-imgBorder]
    > ![Power BI-Arbeitsbereiche auswählen](../media/enable-powerbi-embedded-window.png "Power BI-Arbeitsbereiche auswählen")
    
    > [!NOTE]
    > Nachdem Sie Arbeitsbereiche der Liste **Ausgewählte Arbeitsbereiche** hinzugefügt haben, werden die Datenbanken und Berichte nach einigen Minuten wiedergegeben.
    

4. Wählen Sie **Aktivieren** aus. Während der Power BI Embedded-Dienst aktiviert wird, startet das Portal neu und ist für einige Minuten nicht verfügbar. Eine Meldung wird angezeigt, wenn der Power BI Embedded-Dienst aktiviert ist.

Sie müssen jetzt eine Sicherheitsgruppe erstellen und sie zu Ihrem Power BI-Konto hinzufügen. Weitere Informationen finden Sie unter [Erstellen von Sicherheitsgruppen und sie dem Power BI-Konto hinzufügen](#create-security-group-and-add-to-power-bi-account).

### <a name="create-security-group-and-add-to-power-bi-account"></a>Erstellen von Sicherheitsgruppen und sie dem Power BI-Konto hinzufügen

Nachdem Sie die Integration des Power BI Embedded-Diensts aktiviert haben, müssen Sie eine Sicherheitsgruppe in Azure Active Directory erstellen, dieser ein Mitglied hinzufügen und dann die Sicherheitsgruppe in Power BI über das Power BI-Administratorportal hinzufügen. Somit können Dashboards und Berichte, die in neuen Power BI-Arbeitsbereichen erstellt werden, im Portal angezeigt werden.

> [!NOTE]
> Sie müssen sich mit demselben globalen Administratorkonto anmelden, mit dem Sie den Dienst Power BI Embedded aktiviert haben.

**Schritt 1: Erstellen einer Sicherheitsgruppe**

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) unter Verwendung eines globalen Administratorkontos für das Verzeichnis an.

2. Wählen Sie **Azure Active Directory**, **Gruppen** und dann **Neue Gruppe** aus.

3. Geben Sie auf der Seite **Gruppe** die folgenden Informationen ein:

    - **Gruppentyp**: Sicherheit.

    - **Gruppenname**: Power BI Embedded-Dienst des Portals.

    - **Gruppenbeschreibung**: Diese Sicherheitsgruppe wird für das Portal und die Integration des Power BI Embedded-Diensts verwendet.

    - **Mitgliedschaftstyp**: Zugewiesen.

      > [!div class=mx-imgBorder]
      > ![Erstellen einer Sicherheitsgruppe für den Power BI Embedded-Dienst](../media/powerbi-embed-security-group.png "Erstellen einer Sicherheitsgruppe für den Power BI Embedded-Dienst")

4. Wählen Sie **Erstellen** aus.

**Schritt 2: Hinzufügen eines Gruppenmitglieds**

**Voraussetzung**: Bevor Sie ein Mitglied der Sicherheitsgruppe hinzufügen, müssen Sie die Anwendungs-ID des Portals bei sich haben. Die Anwendungs-ID des Portale finden Sie auf der Registerkarte **Portaldetails** in [PowerApps Portale Administrations-Center](admin-overview.md).

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) unter Verwendung eines globalen Administratorkontos für das Verzeichnis an.

2. Wählen Sie **Azure Active Directory** und dann **Gruppen** aus.

3. Suchen Sie auf der Seite **Gruppen – Alle Gruppen** nach der Gruppe **Power BI Embedded-Dienst des Portals**, und wählen Sie sie aus.

    > [!div class=mx-imgBorder]
    > ![Suchen und Auswählen der Sicherheitsgruppe für den Power BI Embedded-Dienst](../media/search-security-group.png "Suchen und Auswählen der Sicherheitsgruppe für den Power BI Embedded-Dienst")

4. Wählen Sie auf der Seite **Übersicht über den Power BI Embedded-Dienst des Portals** die Option **Mitglieder** im Bereich **Verwalten** aus.

5. Wählen Sie **Mitglieder hinzufügen** aus und geben Sie die Anwendungs-ID des Portals in das Textfeld ein.

6. Wählen Sie Mitglieder aus dem Suchergebnis und dann **Auswählen** aus.

    > [!div class=mx-imgBorder]
    > ![Hinzufügen von Mitgliedern in der Sicherheitsgruppe für den Power BI Embedded-Dienst](../media/add-member-powerbi-embed.png "Hinzufügen von Mitgliedern in der Sicherheitsgruppe für den Power BI Embedded-Dienst")

**Schritt 3: Power BI-Einrichtung**

1. Melden Sie sich in [Power BI](https://powerbi.microsoft.com) unter Verwendung eines globalen Administratorkontos für das Verzeichnis an.

2. Wählen Sie oben rechts im Power BI-Dienst die Option **Einstellungen** und dann **Verwaltungsportal** aus.

    > [!div class=mx-imgBorder]
    > ![Auswählen des Admin-Portals im Power BI-Dienst](../media/select-admin-portal.png "Auswählen des Admin-Portals im Power BI-Dienst")

3. Wählen Sie **Mandanteneinstellungen** aus.

4. Wählen Sie im Abschnitt **Entwicklereinstellungen** die Option **Erlauben, dass Dienstprinzipale Power BI-APIs verwenden** aus.

5. Suchen Sie im Feld **Spezifische Sicherheitsgruppen** nach der Gruppe **Power BI Embedded-Dienst des Portals**, und wählen Sie sie aus.

    > [!div class=mx-imgBorder]
    > ![Hinzufügen einer Sicherheitsgruppe im Power BI-Admin-Portal](../media/add-sg-powerbi.png "Hinzufügen einer Sicherheitsgruppe im Power BI-Admin-Portal")

6. Wählen Sie **Übernehmen** aus.

Systemanpasser können jetzt das Liquid-Tag [powerbi](../liquid/portals-entity-tags.md#powerbi) verwenden, um Power BI-Dashboards und -Berichte von neuen Power BI-Arbeitsbereichen auf Webseiten in einem Portal einzubetten. Um den Power BI Embedded-Dienst zu verwenden, muss der Authentifizierungstyp als **powerbiembedded** festgelegt worden sein. Beim Einbetten des Power BI-Inhalts können Systemanpasser mit [Filterparametern](https://docs.microsoft.com/power-bi/service-url-filters) personalisierte Ansichten erstellen. Weitere Informationen: [Liquid-Tag powerbi](../liquid/portals-entity-tags.md#powerbi).


### <a name="manage-the-power-bi-embedded-service"></a>Power BI Embedded-Dienst verwalten

1. Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2. Wechseln Sie zu **Einrichten der Power BI-Integration** > **Verwalten des Power BI Embedded-Dienstes**.

    > [!div class=mx-imgBorder]
    > ![Verwalten des Power BI Embedded-Dienstes](../media/manage-powerbi-embedded-button.png "Power BI Embedded-Service verwalten")

3. Entfernen Sie im Fenster **Integration des Power BI Embedded-Diensts verwalten** die Power BI-Arbeitsbereiche, für die Dashboards und Berichte in Ihrem Portal angezeigt werden müssen, oder verschieben Sie sie in die Liste **Ausgewählte Arbeitsbereiche**.

    > [!div class=mx-imgBorder]
    > ![Power BI-Arbeitsbereiche auswählen](../media/manage-powerbi-embedded-window.png "Power BI-Arbeitsbereiche auswählen")
    
    > [!NOTE]
    > Nach dem Entfernen der Arbeitsbereiche aus der Liste **Ausgewählte Arbeitsbereiche** kann es bis zu 1 Stunde dauern, bis die Änderungen berücksichtigt werden. Bis dahin werden die Datenbanken und Berichte im Portal ohne Probleme wiedergegeben.

4. Wählen Sie **Speichern** aus.

### <a name="disable-the-power-bi-embedded-service"></a>Power BI Embedded-Dienst deaktivieren

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Wechseln Sie zu **Einrichten der Power BI-Integration** > **Verwalten des Power BI Embedded-Dienstes**.

    > [!div class=mx-imgBorder]
    > ![Verwalten des Power BI Embedded-Dienstes](../media/manage-powerbi-embedded-button.png "Power BI Embedded-Service verwalten")

3. Wählen Sie im Fenster **Integration des Power BI Embedded-Diensts verwalten** die Option **Integration des Power BI Embedded-Diensts deaktivieren** aus.

    > [!div class=mx-imgBorder]
    > ![Deaktivieren des Power BI Embedded-Dienstes](../media/disable-powerbi-embedded-window.png "Deaktivieren des Power BI Embedded-Dienstes")

4. Wählen Sie **Speichern** aus.

5. Wählen Sie **OK** in der Bestätigungs-Message aus. Während der Power BI Embedded-Dienst deaktiviert wird, startet das Portal neu und ist für einige Minuten nicht verfügbar. Eine Meldung wird angezeigt, wenn der Power BI Embedded-Dienst deaktiviert ist.

## <a name="privacy-notice"></a>Datenschutzbestimmungen  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>Siehe auch

[Liquid-Tag powerbi](../liquid/portals-entity-tags.md#powerbi)<br> 
[Hinzufügen eines Power BI-Berichts oder -Dashboards zu einer Webseite im Portal](add-powerbi-report.md)
