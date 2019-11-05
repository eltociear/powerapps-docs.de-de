---
title: Einrichten Power BI Integration in Ihr Portal | MicrosoftDocs
description: Erfahren Sie, wie Sie Power BI Integration in Ihr Portal einrichten.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543025"
---
# <a name="set-up-power-bi-integration"></a>Einrichten der Power BI-Integration

Power BI ist eines der besten Tools, mit denen Sie Einblicke in einfache und interaktive Visualisierungen vermitteln können. Zum Anzeigen von Dashboards und Berichten aus Power BI auf Webseiten in einem Portal müssen Sie Power BI Visualisierung über das powerapps-Portal Admin Center aktivieren. Sie können auch Dashboards und Berichte, die im neuen Arbeitsbereich von Power BI erstellt wurden, einbetten, indem Sie die Power BI Embedded Dienst Integration aktivieren.

> [!NOTE]
> - Sie müssen über eine entsprechende Power BI Lizenz verfügen.
> - Um Power BI Embedded Dienst verwenden zu können, müssen Sie über eine entsprechende Power BI Embedded Lizenz verfügen. Weitere Informationen finden Sie unter [Lizenzierung](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing).

## <a name="enable-power-bi-visualization"></a>Power BI Visualisierung aktivieren

Wenn Sie Power BI Visualisierung aktivieren, können Sie Dashboards und Berichte mithilfe des powerbi Liquid-Tags auf Webseiten in einem Portal einbetten.

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu **Einrichten Power BI Integration** , > **Power BI Visualisierung aktivieren**.

    > [!div class=mx-imgBorder]
    > ![Power BI Visualisierung aktivieren](../media/enable-power-bi-visualization.png "Power BI Visualisierung aktivieren")

3.  Wählen Sie in der Bestätigungsmeldung die Option **aktivieren** aus. Während Power BI Visualisierung aktiviert ist, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar. Wenn Power BI Visualisierung aktiviert ist, wird eine Meldung angezeigt.

Anpassungen können mithilfe des [powerbi](../liquid/portals-entity-tags.md#powerbi) Liquid-Tags Power BI Dashboards und Berichte auf Webseiten in einem Portal einbetten. Beim Einbetten des Power BI Inhalts können Anpassungen [Filter Parameter](https://docs.microsoft.com/power-bi/service-url-filters) zum Erstellen personalisierter Ansichten verwenden. Weitere Informationen: [powerbi Liquid-Tag](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Deaktivieren der Power BI Visualisierung

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu **Einrichten Power BI Integration** , > **Power BI Visualisierung deaktivieren**.

    > [!div class=mx-imgBorder]
    > ![Deaktivieren der Power BI Visualisierung](../media/disable-power-bi-visualization.png "Deaktivieren der Power BI Visualisierung")

3. Wählen Sie in der Bestätigungsmeldung die Option **Deaktivieren** aus. Während Power BI Visualisierung deaktiviert wird, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar. Wenn Power BI Visualisierung deaktiviert ist, wird eine Meldung angezeigt.

## <a name="enable-power-bi-embedded-service"></a>Aktivieren Power BI Embedded Dienstanbieter

Wenn Sie den Power BI Embedded-Dienst aktivieren, können Sie Dashboards und Berichte einbetten, die im neuen Arbeitsbereich von Power BI erstellt wurden. Die Dashboards und Berichte werden mithilfe des Liquid-Tags von powerbi auf Webseiten in einem Portal eingebettet.

**Voraussetzungen**: Vergewissern Sie sich vor dem Aktivieren des Power BI Embedded Dienstanbieter, dass Sie die Dashboards und Berichte im neuen Arbeitsbereich in Power BI erstellt haben. Stellen Sie nach dem Erstellen des Arbeitsbereichs Administrator Zugriff für den globalen Administrator bereit, sodass die Arbeitsbereiche im Admin Center der powerapps-Portale angezeigt werden. Weitere Informationen zum Erstellen neuer Arbeitsbereiche und zum Hinzufügen von Zugriff darauf finden Sie unter [Erstellen der neuen Arbeitsbereiche in Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces).

**Einschränkungen für Power BI Embedded Dienste**: Weitere Informationen zu Einschränkungen finden Sie unter [Überlegungen und Einschränkungen](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations).

> [!NOTE]
> Stellen Sie sicher, dass Power BI Visualisierung aktiviert ist, damit das powerbi Liquid-Tag funktioniert.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu **Einrichten Power BI Integration** , um **Power BI Embedded Dienst zu aktivieren** > .

    > [!div class=mx-imgBorder]
    > ![Aktivieren Power BI Embedded Dienstanbieter](../media/enable-powerbi-embedded-button.png "Aktivieren Power BI Embedded Dienstanbieter")

3. Wählen Sie im Fenster **Power BI Embedded Dienst Integration aktivieren** aus, und verschieben Sie die Power BI Arbeitsbereiche, von denen Dashboards und Berichte im Portal angezeigt werden müssen, in die Liste **ausgewählte Arbeitsbereiche** .

    > [!div class=mx-imgBorder]
    > ![Wählen Sie Power BI Arbeitsbereiche aus.](../media/enable-powerbi-embedded-window.png "Wählen Sie Power BI Arbeitsbereiche aus.")
    
    > [!NOTE]
    > Nachdem Sie der Liste **ausgewählte Arbeitsbereiche** Arbeitsbereiche hinzugefügt haben, werden die Datenbanken und Berichte nach einigen Minuten gerendert.
    

4. Wählen Sie **aktivieren**aus. Während Power BI Embedded Dienst aktiviert wird, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar. Wenn Power BI Embedded-Dienst aktiviert ist, wird eine Meldung angezeigt.

Sie müssen jetzt eine Sicherheitsgruppe erstellen und Sie Ihrem Power BI-Konto hinzufügen. Weitere Informationen finden Sie unter [Erstellen einer Sicherheitsgruppe und hinzufügen zu Power BI Konto](#create-security-group-and-add-to-power-bi-account).

### <a name="create-security-group-and-add-to-power-bi-account"></a>Sicherheitsgruppe erstellen und zu Power BI Konto hinzufügen

Nachdem Sie die Power BI Embedded Dienst Integration aktiviert haben, müssen Sie eine Sicherheitsgruppe in Azure Active Directory erstellen, ihr ein Mitglied hinzufügen und dann die Sicherheitsgruppe in Power BI über das Power BI Admin-Portal hinzufügen. Dadurch können die in neuen Power BI Arbeitsbereichen erstellten Dashboards und Berichte im Portal angezeigt werden.

> [!NOTE]
> Sie müssen sich mit dem gleichen globalen Administrator Konto anmelden, das Sie zum Aktivieren des Power BI Embedded Dienstanbieter verwendet haben.

**Schritt 1: Erstellen einer Sicherheitsgruppe**

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) mit einem globalen Administrator Konto für das Verzeichnis an.

2. Wählen Sie **Azure Active Directory**, **Gruppen**und dann **neue Gruppe**aus.

3. Geben Sie auf der Seite **Gruppe** die folgenden Informationen ein:

    - **Gruppentyp**: Sicherheit.

    - **Gruppenname**: Portal Power BI Embedded Dienst.

    - **Gruppenbeschreibung**: Diese Sicherheitsgruppe wird für die Integration des Portal-und Power BI Embedded Diensts verwendet.

    - **Mitgliedschaftentyp**: zugewiesen.

      > [!div class=mx-imgBorder]
      > ![Erstellen einer Sicherheitsgruppe für Power BI Embedded-Dienst](../media/powerbi-embed-security-group.png "Erstellen einer Sicherheitsgruppe für Power BI Embedded-Dienst")

4. Wählen Sie die Option **Erstellen**.

**Schritt 2: Hinzufügen eines Gruppenmitglieds**

**Voraussetzung**: bevor Sie der Sicherheitsgruppe ein Mitglied hinzufügen, müssen Sie über die Anwendungs-ID des Portals verfügen. Die Anwendungs-ID des Portals steht auf der Registerkarte **Details zum Portal** im [Admin Center des powerapps-Portals](admin-overview.md)zur Verfügung.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) mit einem globalen Administrator Konto für das Verzeichnis an.

2. Wählen Sie **Azure Active Directory**aus, und wählen Sie dann **Gruppen**aus.

3. Suchen Sie auf der Seite **Gruppen-alle Gruppen** nach dem **Portal Power BI Embedded Dienst** Gruppe, und wählen Sie es aus.

    > [!div class=mx-imgBorder]
    > ![Suchen und wählen Sie die Sicherheitsgruppe für Power BI Embedded-Dienst aus.](../media/search-security-group.png "Suchen und wählen Sie die Sicherheitsgruppe für Power BI Embedded-Dienst aus.")

4. Wählen Sie auf der Seite **Portal Power BI Embedded Dienst Übersicht** die Option **Mitglieder** aus dem Bereich **Verwalten** aus.

5. Wählen Sie **Mitglieder hinzufügen**aus, und geben Sie die Anwendungs-ID des Portals in das Textfeld ein.

6. Wählen Sie das Element aus dem Suchergebnis aus, und wählen Sie dann **auswählen**aus.

    > [!div class=mx-imgBorder]
    > ![Mitglied in der Sicherheitsgruppe für Power BI Embedded-Dienst hinzufügen](../media/add-member-powerbi-embed.png "Mitglied in der Sicherheitsgruppe für Power BI Embedded-Dienst hinzufügen")

**Schritt 3: Power BI Setup**

1. Melden Sie sich bei [Power BI](https://powerbi.microsoft.com) mit einem globalen Administrator Konto für das Verzeichnis an.

2. Wählen Sie oben rechts im Power BI-Dienst die Option **Einstellungen** aus, und wählen Sie dann **Verwaltungs Portal**aus.

    > [!div class=mx-imgBorder]
    > ![Wählen Sie in Power BI-Dienst Verwaltungs Portal aus.](../media/select-admin-portal.png "Wählen Sie in Power BI-Dienst Verwaltungs Portal aus.")

3. Wählen Sie Mandanten **Einstellungen**aus.

4. Wählen Sie im Abschnitt " **Entwicklereinstellungen** " die Option **Dienst Prinzipale die Verwendung Power BI APIs erlauben**aus.

5. Suchen Sie im Feld **bestimmte Sicherheitsgruppen** nach dem **Portal Power BI Embedded Dienst** Gruppe, und wählen Sie es aus.

    > [!div class=mx-imgBorder]
    > ![Hinzufügen einer Sicherheitsgruppe im Power BI Admin-Portal](../media/add-sg-powerbi.png "Hinzufügen einer Sicherheitsgruppe im Power BI Admin-Portal")

6. Wählen **Sie**übernehmen.

Anpassungen können nun mithilfe des [powerbi](../liquid/portals-entity-tags.md#powerbi) Liquid-Tags Power BI Dashboards und Berichte aus neuen Power BI Arbeitsbereichen auf Webseiten in einem Portal eingebettet werden. Um Power BI Embedded Dienst zu verwenden, muss der Authentifizierungstyp als **powerbiembedded**angegeben werden. Beim Einbetten des Power BI Inhalts können Anpassungen [Filter Parameter](https://docs.microsoft.com/power-bi/service-url-filters) zum Erstellen personalisierter Ansichten verwenden. Weitere Informationen: [powerbi Liquid-Tag](../liquid/portals-entity-tags.md#powerbi).


### <a name="manage-the-power-bi-embedded-service"></a>Verwalten des Power BI Embedded Dienstanbieter

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu **Einrichten Power BI Integration** > **Verwalten Power BI Embedded Dienstanbieter**.

    > [!div class=mx-imgBorder]
    > ![Verwalten Power BI Embedded Dienstanbieter](../media/manage-powerbi-embedded-button.png "Verwalten Power BI Embedded Dienstanbieter")

3. Entfernen oder verschieben Sie im Fenster **Power BI Embedded Dienst Integration verwalten** die Arbeitsbereiche Power BI, von denen Dashboards und Berichte im Portal angezeigt werden müssen, in die Liste **ausgewählte Arbeitsbereiche** .

    > [!div class=mx-imgBorder]
    > ![Wählen Sie Power BI Arbeitsbereiche aus.](../media/manage-powerbi-embedded-window.png "Wählen Sie Power BI Arbeitsbereiche aus.")
    
    > [!NOTE]
    > Nachdem Sie die Arbeitsbereiche aus der Liste **ausgewählte Arbeitsbereiche** entfernt haben, kann es bis zu einer Stunde dauern, bis die Änderungen angezeigt werden. Bis dahin werden die Datenbanken und Berichte ohne Probleme im Portal gerendert.

4. Wählen Sie **Speichern**.

### <a name="disable-the-power-bi-embedded-service"></a>Deaktivieren des Power BI Embedded Dienstanbieter

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu **Einrichten Power BI Integration** > **Verwalten Power BI Embedded Dienstanbieter**.

    > [!div class=mx-imgBorder]
    > ![Verwalten Power BI Embedded Dienstanbieter](../media/manage-powerbi-embedded-button.png "Verwalten Power BI Embedded Dienstanbieter")

3. Wählen Sie im Fenster **Power BI Embedded Dienst Integration verwalten** die Option **Power BI Embedded Dienst Integration deaktivieren**aus.

    > [!div class=mx-imgBorder]
    > ![Deaktivieren Power BI Embedded Dienstanbieter](../media/disable-powerbi-embedded-window.png "Deaktivieren Power BI Embedded Dienstanbieter")

4. Wählen Sie **Speichern**.

5. Klicken Sie in der Bestätigungsmeldung auf **OK** . Während Power BI Embedded Dienst deaktiviert wird, wird das Portal neu gestartet und ist für einige Minuten nicht verfügbar. Wenn Power BI Embedded-Dienst deaktiviert ist, wird eine Meldung angezeigt.

## <a name="privacy-notice"></a>Hinweis zum Datenschutz  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>Siehe auch

[powerbi Liquid-Tag](../liquid/portals-entity-tags.md#powerbi)<br> 
[Hinzufügen eines Power BI Berichts oder eines Dashboards zu einer Webseite im Portal](add-powerbi-report.md)
