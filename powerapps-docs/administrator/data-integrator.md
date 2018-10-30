---
title: Integrieren von Daten in Common Data Service für Apps
description: Integrieren von Daten aus mehreren Quellen in Common Data Service für Apps
author: sabinn-msft
ms.service: powerapps
ms.topic: how-to
ms.component: cds
ms.date: 10/15/2018
ms.author: sabinn
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: dfbc420dfb4945cdda635e3cbaadb1acb446753b
ms.sourcegitcommit: ebd39753e2a0b60c1d8c016e38c00dd1accf5d0c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328692"
---
# <a name="integrate-data-into-common-data-service-for-apps"></a>Integrieren von Daten in Common Data Service für Apps

<!--note from editor: the style guide says not to use "the" in front of Common Data Service for Apps, so I'm removing that.-->

Der Data Integrator (für Administratoren) ist ein Punkt-zu-Punkt-Integrationsdienst, mit dem Sie Daten in Common Data Service für Apps integrieren können. Der Dienst unterstützt die Integration von Daten aus mehreren Quellen – z.B. Dynamics 365 for Finance and Operations, Dynamics 365 for Sales, SalesForce (Vorschau), SQL (Vorschau) – in Common Data Service für Apps. Er unterstützt auch die Integration von Daten in Dynamics 365 for Finance and Operations und Dynamics 365 for Sales. Der Dienst ist seit Juli 2017 allgemein verfügbar.  

Wir haben mit Erstanbieter-Apps begonnen, z.B. mit Dynamics 365 for Finance and Operations und Dynamics 365 for Sales. Mithilfe von Power Query- oder M-basierten Connectors können wir jetzt auch weitere Quellen wie SalesForce (Vorschau) und SQL (Vorschau) unterstützen und werden diese Unterstützung in naher Zukunft auf über 20 weitere Quellen ausweiten. 

> [!div class="mx-imgBorder"]
> ![Datenquellen und Datenziele](media/data-integrator/DataIntegratorP2P-new.PNG "Datenquellen und Datenziele")

## <a name="how-can-you-use-the-data-integrator-for-your-business"></a>Wie können Sie Data Integrator für Ihr Unternehmen einsetzen?

Data Integrator (für Administratoren) unterstützt auch prozessbasierte Integrationsszenarien wie „Prospect to Cash“, die eine direkte Synchronisierung zwischen Dynamics 365 for Finance and Operations und Dynamics 365 for Sales ermöglichen. Die mit dem Datenintegrationsfeature verfügbaren Prospect to Cash-Vorlagen ermöglichen den Datenfluss für Konten, Kontakte, Produkte, Angebote, Bestellungen und Rechnungen zwischen Finance and Operations und Sales. Während die Daten zwischen Finance and Operations und Sales ausgetauscht werden, können Sie Vertriebs- und Marketingaktivitäten in Sales ausführen und die Auftragserfüllung mithilfe der Bestandsverwaltung in Finance and Operations abwickeln. 

> [!div class="mx-imgBorder"]
> ![Prospect to Cash](media/data-integrator/ProspectToCash631.png "Prospect to Cash")

Die Prospect to Cash-Integration ermöglicht Verkäufern, ihre Vertriebsprozesse mit den leistungsstarken Features von Dynamics 365 for Sales zu verarbeiten und zu überwachen, während alle Aspekte der Auftragserfüllung und Rechnungsstellung mithilfe der umfangreichen Funktionen in Finance and Operations erfolgen. Mit der Microsoft Dynamics 365-Integration von Prospect to Cash profitieren Sie von der kombinierten Leistungsstärke beider Systeme. 

Sehen Sie sich das Video an: [Integration von Prospect to Cash](https://www.youtube.com/watch?v=AVV9x5x-XCg).

Weitere Informationen zur Prospect to Cash-Integration finden Sie in der Dokumentation zur [Prospect to Cash-Lösung](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/prospect-to-cash).

Wir unterstützen auch die [Integration von Field Service](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/sales-marketing/field-service-work-order) und die [Integration von PSA (Project Service Automation)](https://docs.microsoft.com/dynamics365/unified-operations/financials/project-management/psa-integration?toc=/fin-and-ops/toc.json) in Dynamics 365 for Finance and Operations.

## <a name="data-integrator-platform"></a>Data Integrator-Plattform

Data Integrator (für Administratoren) besteht aus der Data Integrator-Plattform, sofort einsatzbereiten Vorlagen, die von unseren Anwendungsteams bereitgestellt werden (z.B. Dynamics 365 for Finance and Operations und Dynamics 365 for Sales), sowie benutzerdefinierten Vorlagen, die von unseren Kunden und Partnern erstellt werden. Wir haben eine anwendungsunabhängige Plattform erstellt, die sich für verschiedene Quellen skalieren lässt. Diese Plattform bietet verschiedene Kernfunktionen: Sie können Verbindungen (mit Integrationsendpunkten) erstellen, eine der anpassbaren Vorlagen mit vordefinierten Zuordnungen auswählen (diese können Sie weiter anpassen) und das Datenintegrationsprojekt erstellen und ausführen.  

Integrationsvorlagen dienen als Blaupause mit vordefinierten Entitäten und Feldzuordnungen, um den Datenfluss von der Quelle zum Ziel zu ermöglichen. Sie bieten auch die Möglichkeit, Daten vor dem Import zu transformieren. Häufig können die Schemas der Quell- und Ziel-Apps sehr unterschiedlich sein. In diesen Fällen kann eine Vorlage mit vordefinierten Entitäten und Feldzuordnungen als ausgezeichneter Startpunkt für ein Integrationsprojekt dienen.  

> [!div class="mx-imgBorder"]
> ![Datenintegrationsplattform](media/data-integrator/DIPlatform.PNG "Datenintegrationsplattform")

## <a name="how-to-set-up-a-data-integration-project"></a>Einrichten eines Datenintegrationsprojekts

Ein solches Projekt besteht aus drei Schritten:

1. Erstellen Sie eine Verbindung (Angeben von Anmeldeinformationen für Datenquellen).

2. Erstellen Sie eine Verbindungsgruppe (Ermitteln von Umgebungen für Verbindungen, die Sie im vorherigen Schritt erstellt haben).

3. Erstellen Sie ein Datenintegrationsprojekt mithilfe einer Vorlage (erstellen oder verwenden Sie vordefinierte Zuordnungen für eine oder mehrere Entitäten).

Sobald Sie ein Integrationsprojekt erstellt haben, können Sie das Projekt manuell ausführen sowie zukünftige Aktualisierungen nach Zeitplan einrichten. Im Rest dieses werden diese drei Schritte genauer erläutert.

### <a name="how-to-create-a-connection"></a>Erstellen einer Verbindung

Bevor Sie ein Datenintegrationsprojekt erstellen können, müssen Sie eine Verbindung für jedes System bereitstellen, mit dem Sie im Microsoft PowerApps-Portal arbeiten möchten. Stellen Sie sich diese Verbindungen als Ihre Integrationspunkte vor.

**So erstellen Sie eine Verbindung**

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com).

2. Wählen Sie unter „Daten“ die Option **Verbindungen** und dann **Neue Verbindung** aus.

3. Sie können eine Verbindung aus der Liste mit Verbindungen auswählen oder nach der gewünschten Verbindung suchen.

    > [!div class="mx-imgBorder"] 
    > ![Erstellen der Verbindung](media/data-integrator/CreateConnection780.png "Erstellen der Verbindung")

4. Wenn Sie die gewünschte Verbindung ausgewählt haben, klicken Sie auf **Erstellen**. Sie werden zur Eingabe Ihrer Anmeldeinformationen aufgefordert.

5. Nachdem Sie die Anmeldeinformationen eingegeben haben, wird die Verbindung unter Ihren Verbindungen aufgeführt.

    > [!div class="mx-imgBorder"] 
    > ![Verbindungsliste](media/data-integrator/CreateConnection1780.png "Verbindungsliste")

> [!NOTE]
> Stellen Sie sicher, dass das Konto, das Sie für die einzelnen Verbindungen angeben, über Zugriff auf Entitäten für die entsprechenden Anwendungen verfügt. Darüber hinaus kann sich das Konto für die einzelnen Verbindungen auf einem anderen Mandanten befinden. 

### <a name="how-to-create-a-connection-set"></a>Erstellen einer Verbindungsgruppe

Verbindungsgruppen sind Sammlungen mit zwei Verbindungen, den Umgebungen für die Verbindungen, Zuordnungsinformationen für die Organisation und Integrationsschlüssel, die in verschiedenen Projekten wiederverwendet werden können. Sie können mit der Verwendung einer Verbindungsgruppe für die Entwicklung beginnen und dann zu einer anderen Gruppe für die Produktion wechseln. Wichtige Informationen, die mit einer Verbindungsgruppe gespeichert werden, sind die Zuordnungen von Organisationseinheiten – z.B. Zuordnungen zwischen der juristischen Einheit (oder dem Unternehmen) „Finance and Operations“ und der Organisation bzw. den Geschäftseinheiten für Dynamics 365 for Sales. Sie können mehrere Zuordnungen der Organisation in einer Verbindungsgruppe speichern.

**So erstellen Sie eine Verbindungsgruppe**

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com).

2. Wählen Sie im linken Navigationsbereich die Registerkarte **Datenintegration** aus.

3. Wählen Sie die Registerkarte **Verbindungsgruppen** und dann **Neue Verbindungsgruppe** aus.

4. Geben Sie einen Namen für die Verbindungsgruppe ein.
  
    > [!div class="mx-imgBorder"] 
    > ![Erstellen einer Verbindungsgruppe](media/data-integrator/CreateConnectionSet1780.png "Erstellen einer Verbindungsgruppe")
  
5. Wählen Sie die zuvor erstellten Verbindungen und die geeignete Umgebung aus.

6. Wiederholen Sie die Schritte für die nächste Verbindung (stellen Sie sich diese als Quelle und Ziel vor, ohne bestimmte Reihenfolge).

7. Geben Sie die Zuordnung zwischen Organisation und Geschäftseinheit an (wenn Sie eine Integration zwischen den Systemen „Finance and Operations“ und „Sales“ durchführen).
  
    > [!NOTE]
    > Sie können mehrere Zuordnungen für jede Verbindungsgruppe angeben.
  
8. Wenn Sie alle Felder ausgefüllt haben, klicken Sie auf **Erstellen**.

9. Die neue Verbindungsgruppe wird auf der Seite mit der Liste der Verbindungsgruppen angezeigt.
    
    > [!div class="mx-imgBorder"] 
    > ![Liste der Verbindungsgruppen](media/data-integrator/CreateConnectionSet2780.png "Liste der Verbindungsgruppen")

Ihre Verbindungsgruppe ist jetzt für die Verwendung in verschiedenen Integrationsprojekten bereit.

### <a name="how-to-create-a-data-integration-project"></a>Erstellen eines Datenintegrationsprojekts

Projekte ermöglichen den Datenfluss zwischen Systemen. Ein Projekt enthält Zuordnungen für eine oder mehrere Entitäten. Zuordnungen geben an, welches Feld welchen anderen Feldern zugeordnet ist.

**So erstellen Sie ein Datenintegrationsprojekt**

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com).

2. Wählen Sie im linken Navigationsbereich die Registerkarte **Datenintegration** aus.

3. Wählen Sie auf der Registerkarte **Projekte** in der oberen rechten Ecke die Option **Neues Projekt**.

    > [!div class="mx-imgBorder"] 
    > ![Erstellen eines Projekts](media/data-integrator/CreateNewProject780.png "Erstellen eines Projekts")

4. Geben Sie einen Namen für Ihr Integrationsprojekt an.

5. Wählen Sie eine der verfügbaren Vorlagen aus (oder [erstellen Sie eine eigene Vorlage](#how-to-customize-or-create-your-own-template)). Im vorliegenden Beispiel verschieben wir die Entität „Products“ von „Finance and Operations“ nach „Sales“.

    > [!div class="mx-imgBorder"] 
    > ![Auswählen einer Vorlage zum Erstellen eines neuen Projekts](media/data-integrator/CreateNewProjectSelectTemplate780.png "Auswählen einer Vorlage zum Erstellen eines neuen Projekts")

6. Klicken Sie auf **Weiter**, und wählen Sie eine zuvor erstellte Verbindungsgruppe aus (oder [erstellen Sie eine neue Verbindungsgruppe](#how-to-create-a-connection-set)).

7. Stellen Sie sicher, dass Sie die richtige Verbindungsgruppe ausgewählt haben, indem Sie die Namen für die Verbindung und die Umgebung überprüfen.

    > [!div class="mx-imgBorder"] 
    > ![Erstellen einer neuen Verbindungsgruppe](media/data-integrator/CreateNewProjectSelectConnectionSet780.png "Erstellen einer neuen Verbindungsgruppe")

8. Klicken Sie auf **Weiter**, und wählen Sie dann die Zuordnungen zwischen juristischer Einheit und Geschäftseinheit aus.

    > [!div class="mx-imgBorder"] 
    > ![Erstellen einer neuen Zuordnung zu einer juristischen Einheit](media/data-integrator/CreateNewProjectLegalEntityMapping780.png "Erstellen einer neuen Zuordnung zu einer juristischen Einheit")

9. Lesen und akzeptieren Sie den Datenschutzhinweis auf dem nächsten Bildschirm.

10. Fahren Sie mit dem Erstellen des Projekts fort, und führen Sie das Projekt dann aus.

    > [!div class="mx-imgBorder"] 
    > ![Ausführen des Projekts](media/data-integrator/RunProject780.png "Ausführen des Projekts")

    Auf diesem Bildschirm sehen Sie verschiedene Registerkarten, **Planung** und **Ausführungshistorie**, sowie einige Schaltflächen, **Aufgabe hinzufügen**, **Entitäten aktualisieren** und **Erweiterte Abfrage**. Diese Registerkarten und Schaltflächen werden weiter unten in diesem Artikel beschrieben.

### <a name="execution-history"></a>Ausführungshistorie

Die Ausführungshistorie zeigt den Verlauf aller Projektausführungen mit Projektname, Zeitstempel der Projektausführung, Status der Ausführung sowie der Anzahl von upsert-Vorgängen und/oder Fehlern.

-   Beispiel für den Projektausführungsverlauf.

    > [!div class="mx-imgBorder"] 
    > ![Beispiel für den Projektausführungsverlauf](media/data-integrator/ExecutionHistorySuccessFailures4780.png "Beispiel für den Projektausführungsverlauf")

-   Beispiel einer erfolgreichen Ausführung mit Status „Abgeschlossen“ und der Anzahl von upsert-Vorgängen. („Update Insert“ ist eine Logik zum Aktualisieren des Datensatzes, wenn dieser bereits vorhanden ist, oder zum Einfügen eines neuen Datensatzes.)

    > [!div class="mx-imgBorder"] 
    > ![Ausführung erfolgreich](media/data-integrator/ExecutionHistorySuccess2780.png "Ausführung erfolgreich")

-   Bei Ausführungsfehlern können Sie ein Drilldown durchführen, um die Ursache zu ermitteln.

    Hier sehen Sie ein Beispiel für eine nicht erfolgreiche Ausführung mit Projektprüfungsfehlern. In diesem Fall wird der Projektprüfungsfehler durch fehlende Quellfelder in den Entitätszuordnungen verursacht.

    > [!div class="mx-imgBorder"] 
    > ![Fehler bei der Ausführungshistorie](media/data-integrator/ExecutionHistoryFailures3780.png "Fehler bei der Ausführungshistorie")

-   Wenn sich die Projektausführung im Status „FEHLER“ befindet, wird der Vorgang bei der nächsten geplanten Ausführung wiederholt.

-   Wenn sich die Projektausführung im Status „WARNUNG“ befindet, müssen Sie die Probleme in der Quelle beheben. Der Vorgang wird bei der nächsten geplanten Ausführung wiederholt.

    In beiden Fällen können Sie die Ausführung manuell wiederholen.

### <a name="how-to-set-up-a-schedule-based-refresh"></a>Einrichten einer Aktualisierung nach Zeitplan

Wir unterstützen heute zwei Arten von Ausführungen bzw. Schreibvorgängen:

-   Manuelle Schreibvorgänge (manuelles Ausführen und Aktualisieren von Projekten)

-   Schreibvorgänge nach Zeitplan (automatische Aktualisierung)

Nach dem Erstellen eines Integrationsprojekts erhalten Sie die Option, das Projekt manuell auszuführen oder Schreibvorgänge nach Zeitplan zu konfigurieren, mit denen Sie eine automatische Aktualisierung für Ihre Projekte einrichten können.

**So richten Sie Schreibvorgänge nach Zeitplan ein**

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com).

2. Sie können Projekte auf zwei verschiedene Arten planen.<br>

    Wählen Sie das Projekt aus, und klicken Sie auf die Registerkarte **Planung**, oder starten Sie das Planungstool auf der Seite mit der Projektliste, indem Sie auf die Auslassungspunkte neben dem Projektnamen klicken.

    > [!div class="mx-imgBorder"] 
    > ![Schreibvorgänge nach Zeitplan](media/data-integrator/Schedulebasedwrites780.png "Schreibvorgänge nach Zeitplan")

3. Klicken Sie auf **Wiederholen alle**, füllen Sie alle Felder aus, und klicken Sie dann auf **Zeitplan speichern**.

    > [!div class="mx-imgBorder"] 
    > ![Schreibvorgänge nach Zeitplan](media/data-integrator/Schedulebasedwrites1780.png "Schreibvorgänge nach Zeitplan")

Sie können die Häufigkeit auf einen so geringen Wert wie 1 Minute oder auf mehrere Stunden, Tage, Wochen oder Monate festlegen. Beachten Sie, dass die nächste Aktualisierung erst beginnt, wenn die Ausführung des vorherigen Projekttasks abgeschlossen ist.

Beachten Sie auch, dass Sie unter „Benachrichtigungen“ E-Mail-basierte Benachrichtigungen abonnieren können, die Sie bei Auftragsausführungen warnen, die entweder mit Warnungen abgeschlossen oder aufgrund von Fehlern gar nicht durchgeführt wurden. Sie können mehrere Empfänger – auch Gruppen – mit Kommas getrennt angeben.

> [!div class="mx-imgBorder"] 
> ![E-Mail-Benachrichtigung](media/data-integrator/EmailNotification780.png "E-Mail-Benachrichtigung")

> [!NOTE]
> - Derzeit unterstützen wir die Planung von 50 Integrationsprojekten zu einem beliebigen Zeitpunkt pro kostenpflichtigen Mandanten. Sie können jedoch weitere Projekte erstellen und sie interaktiv ausführen.
Für Testmandanten besteht eine weitere Einschränkung: Ein geplantes Projekt wird nur für die ersten 50 Ausführungen ausgeführt.
> - Wir bieten zwar Unterstützung dafür, Projekte für die Ausführung im Minutentakt zu planen, Sie sollten jedoch beachten, dass Ihre Apps hierdurch stark ausgelastet werden könnten und folglich die allgemeine Leistung beeinträchtigt werden kann. Benutzern wird ausdrücklich empfohlen, Projektausführungen unter tatsächlichen Lastbedingungen zu testen und die Leistung durch seltener ausgeführte Aktualisierungsvorgänge zu optimieren.
In Produktionsumgebungen wird empfohlen, maximal 5 Projekte pro Minute pro Mandant auszuführen.

## <a name="customizing-projects-templates-and-mappings"></a>Anpassen von Projekten, Vorlagen und Zuordnungen 

Sie können eine Vorlage verwenden, um ein Datenintegrationsprojekt zu erstellen. Eine Vorlage vereinfacht das Verschieben von Daten. Dies wiederum hilft geschäftlichen Benutzern und Administratoren dabei, die Integration von Daten aus Quellen in das Ziel zu beschleunigen, und reduziert Kosten und Aufwand insgesamt. Geschäftliche Benutzer und Administratoren können mit einer sofort einsatzfähigen Vorlage beginnen, die von Microsoft oder einem Microsoft-Partner veröffentlicht wurde, und diese an die eigenen Anforderungen anpassen, bevor sie ein Projekt erstellen. Dann speichern sie das Projekt als Vorlage und geben diese für die Organisation frei und/oder erstellen ein neues Projekt. 

Eine Vorlage stellt Ihnen die Quelle, das Ziel und die Richtung des Datenflusses bereit. Dies müssen Sie bedenken, wenn Sie Vorlagen anpassen und/oder eigene Vorlagen erstellen.  

Sie können Projekte und Vorlagen auf folgende Weise anpassen:

-   Anpassen von Feldzuordnungen

-   Anpassen einer Vorlage durch Hinzufügen einer Entität Ihrer Wahl

### <a name="how-to-customize-field-mappings"></a>Anpassen von Feldzuordnungen

**So erstellen Sie eine Verbindungsgruppe**

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com).

2. Wählen Sie das Projekt aus, in dem Sie Feldzuordnungen anpassen möchten, und klicken Sie dann auf den Pfeil zwischen den Feldern für Quelle und Ziel.

    > [!div class="mx-imgBorder"] 
    > ![Feldzuordnung](media/data-integrator/FieldMapping780.png "Feldzuordnung")

3. Damit gelangen Sie zum Bildschirm für Zuordnungen, auf dem Sie in der oberen rechten Ecke auf **Zuordnung hinzufügen** klicken können, um eine neue Zuordnung hinzuzufügen. Alternativ dazu können Sie aus der Dropdownliste die Option **Vorhandene Zuordnungen anpassen** auswählen.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen von Feldzuordnungen](media/data-integrator/FieldMappingCustomize780.png "Anpassen von Feldzuordnungen")

4. Wenn Sie die Feldzuordnungen angepasst haben, klicken Sie auf **Speichern**.

### <a name="how-to-customize-or-create-your-own-template"></a>Anpassen einer Vorlage oder Erstellen einer eigenen Vorlage 

**So erstellen Sie eine eigene Vorlage**

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com).

2. Ermitteln Sie die Quelle, das Ziel und die Flussrichtung für Ihre neue Vorlage.

3. Erstellen Sie ein Projekt, indem Sie eine vorhandene Vorlage auswählen, die der Quelle, dem Ziel und der Flussrichtung Ihrer Wahl entspricht.

<!--note from editor: Didn't we create the project in step 3? Step 4 tells us to create the project.-->

4. Nachdem Sie die geeignete Verbindung ausgewählt haben, erstellen Sie das Projekt.

5. Bevor Sie das Projekt speichern und/oder ausführen, klicken Sie in der rechten oberen Ecke auf **Aufgabe hinzufügen**.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen der Vorlage](media/data-integrator/CustomizeTemplate780.png "Anpassen der Vorlage")

    Dadurch wird das Dialogfeld **Aufgabe hinzufügen** geöffnet.

6. Geben Sie einen aussagekräftigen Namen ein, und fügen Sie die Quell- und Zielentitäten Ihrer Wahl hinzu.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen der Vorlage – Aufgabe hinzufügen](media/data-integrator/CustomizeTemplateAddtask75.png "Anpassen der Vorlage – Aufgabe hinzufügen")

7. Die Dropdownliste enthält all Ihre Quell- und Zielentitäten.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen der Vorlage – Aufgabe hinzufügen](media/data-integrator/CustomizeTemplateAddtask175.png "Anpassen der Vorlage – Aufgabe hinzufügen")

    In diesem Fall wurde eine neue Aufgabe erstellt, um die Entität „User“ aus „SalesForce“ mit der Entität „Users“ in Common Data Service für Apps zu synchronisieren.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen der Vorlage – Aufgabe hinzufügen](media/data-integrator/CustomizeTemplateAddtask275.png "Anpassen der Vorlage – Aufgabe hinzufügen")

8. Nachdem Sie die Aufgabe erstellt haben, wird diese in der Liste aufgeführt, und Sie können die ursprüngliche Aufgabe löschen.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen der Vorlage – Aufgabe hinzufügen](media/data-integrator/CustomizeTemplateAddtask3780.png "Anpassen der Vorlage – Aufgabe hinzufügen")

9. Sie haben gerade eine neue Vorlage erstellt – in diesem Fall eine Vorlage zum Abrufen von Daten der Entität „User“ aus SalesForce nach Common Data Service. Klicken Sie auf **Speichern**, um die Anpassung zu speichern.

10. Führen Sie die Schritte zum Anpassen der Feldzuordnungen für diese neue Vorlage aus. Auf der Seite **Projektseite** können Sie dieses Projekt ausführen und/oder als Vorlage speichern.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen der Vorlage – als Vorlage speichern](media/data-integrator/CustomizeTemplateSaveAsTemplate780.png "Anpassen der Vorlage – als Vorlage speichern")

11. Geben Sie einen Namen und eine Beschreibung ein, und/oder geben Sie die Vorlage für andere Personen in Ihrer Organisation frei.

    > [!div class="mx-imgBorder"] 
    > ![Anpassen der Vorlage – als Vorlage speichern](media/data-integrator/CustomizeTemplateSaveAsTemplate175.png "Anpassen der Vorlage – als Vorlage speichern")

## <a name="advanced-data-transformation-and-filtering"></a>Erweiterte Datentransformation und -filterung 

Mit der Unterstützung von Power Query stellen wir erweiterte Funktionen für die Filterung und Datentransformation von Quelldaten zur Verfügung. Power Query bietet eine benutzerfreundliche, ansprechende Benutzeroberfläche und ermöglicht es Benutzern, Daten ihren Anforderungen entsprechend zu strukturieren – ohne jeden Code. Sie können diese Oberfläche projektbasiert aktivieren. 

### <a name="how-to-enable-advanced-query-and-filtering"></a>Aktivieren erweiterter Abfrage- und Filterfunktionen

**So richten Sie die erweiterte Filterung und Datentransformation ein**

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com).

2. Wählen Sie das Projekt aus, für das Sie erweiterte Abfragen aktivieren möchten, und klicken Sie auf **Erweiterte Abfrage**.

    > [!div class="mx-imgBorder"] 
    > ![Auswählen von „Erweiterte Abfrage“](media/data-integrator/EnablePQ1780.png "Auswählen von „Erweiterte Abfrage“")

3. Es wird eine Warnung angezeigt, dass die Aktivierung erweiterter Abfragen ein unidirektionaler Vorgang ist und nicht rückgängig gemacht werden kann. Klicken Sie auf **OK**, um fortzufahren, und wählen Sie dann den Pfeil zum Zuordnen von Quelle und Ziel aus.

    > [!div class="mx-imgBorder"] 
    > ![Warnung](media/data-integrator/EnablePQ275.png "Warnung")

4. Jetzt wird die vertraute Seite für die Entitätszuordnung mit einem Link zum Starten der erweiterten Abfrage- und Filterfunktionen angezeigt.

    > [!div class="mx-imgBorder"] 
    > ![Erweiterte Abfrage- und Filterfunktionen](media/data-integrator/EnablePQ3780.png "Erweiterte Abfrage- und Filterfunktionen")

5. Klicken Sie auf den **Link**, um die Benutzeroberfläche für erweiterte Abfrage- und Filterfunktionen zu starten, auf der die Quellfelddaten in Spalten angezeigt werden (ähnlich wie bei Microsoft Excel).

    > [!div class="mx-imgBorder"] 
    > ![Erweiterte Abfrage- und Filterfunktionen](media/data-integrator/EnablePQ4780.png "Erweiterte Abfrage- und Filterfunktionen")

6. Im Menü am oberen Rand finden Sie eine Reihe von Optionen zum Transformieren von Daten, wie z.B. **Bedingte Spalte hinzufügen**, **Spalte duplizieren** und **Extrahieren**.

    > [!div class="mx-imgBorder"] 
    > ![Hinzufügen einer Spalte](media/data-integrator/EnablePQAddColumn75.png "Hinzufügen einer Spalte")

7. Sie können auch mit der rechten Maustaste auf eine beliebige Spalte klicken, um weitere Optionen anzuzeigen, z.B. **Spalten entfernen**, **Duplikate entfernen** und **Spalte teilen**.

    > [!div class="mx-imgBorder"] 
    > ![Klick mit der rechten Maustaste auf eine Spalte](media/data-integrator/EnablePQAddColumn180.png "Klick mit der rechten Maustaste auf eine Spalte")

8. Sie können auch filtern, indem Sie auf die einzelnen Spalten klicken und Filter ähnlich wie bei Excel verwenden.

    > [!div class="mx-imgBorder"] 
    > ![Aktivieren der Filterung](media/data-integrator/EnablePQFiltering80.png "Aktivieren der Filterung")

<!--note from editor: I don't see an "otherwise" in the screenshot. I see "else".-->

9. Mithilfe der bedingten Spalte können Standardwerte transformiert werden. Wählen Sie zu diesem Zweck in der Dropdownliste **Spalte hinzufügen** die Option **Bedingte Spalte hinzufügen** aus, und geben Sie für die neue Spalte einen Namen ein. Füllen Sie die Felder **Then** und **Otherwise** mit den Werten aus, die Sie als Standardwerte verwenden möchten, und verwenden Sie dabei beliebige Felder und Werte für **If** und **equal to**.

    > [!div class="mx-imgBorder"] 
    > ![Hinzufügen einer bedingten Spalte](media/data-integrator/EnablePQDefaultValueTransforms2780.png "Hinzufügen einer bedingten Spalte")

10. Beachten Sie am oberen Rand die **each**-Klausel im *fx*-Editor.

    > [!div class="mx-imgBorder"] 
    > ![fx-Editor](media/data-integrator/EnablePQDefaultValueTransforms2780.png "fx-Editor")

11. Korrigieren die **each**-Klausel im *fx*-Editor, und klicken Sie auf **OK**.

    > [!div class="mx-imgBorder"] 
    > ![Korrigieren der each-Klausel](media/data-integrator/EnablePQDefaultValueTransforms5780.png "Korrigieren der each-Klausel")

<!--note from editor: The sentence that starts with "Additionally" is confusing - not sure where the "same steps" fit in.-->

12. Jedes Mal, wenn Sie eine Änderung vornehmen, fügen Sie einen Schritt hinzu. Die angewendeten Schritte werden im Bereich auf der rechten Seite angezeigt (scrollen Sie nach unten, um den letzten Schritt zu sehen). Sie können einen Schritt rückgängig machen, falls Sie eine Änderung bearbeiten müssen. Außerdem können Sie zum erweiterten Editor wechseln, indem Sie mit der rechten Maustaste im linken Bereich oben auf **QrySourceData** klicken, um die M-Sprache anzuzeigen, die im Hintergrund ausgeführt wird.

    > [!div class="mx-imgBorder"] 
    > ![Erweiterter Editor](media/data-integrator/EnablePQDefaultValueTransforms4780.png "Erweiterter Editor")

13. Klicken Sie auf **OK**, um die Benutzeroberfläche für erweiterte Abfrage- und Filterfunktionen zu schließen. Wählen Sie dann auf der Seite mit Zuordnungsaufgaben die neu erstellte Spalte als Quelle aus, um die Zuordnung entsprechend zu erstellen.

    > [!div class="mx-imgBorder"] 
    > ![Auswählen der neuen Spalte](media/data-integrator/EnablePQDefaultValueTransforms6780.png "Auswählen der neuen Spalte")

Weitere Informationen zu Power Query finden Sie in der [Power Query-Dokumentation](https://docs.microsoft.com/power-query/).
