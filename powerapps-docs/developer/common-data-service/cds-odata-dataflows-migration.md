---
title: Migration von Daten zwischen Common Data Service-Umgebungen mit Hilfe des OData-Konnektors für Datenflüsse
author: denisem-msft
ms.reviewer: nabuthuk
description: Migrieren Sie Daten zwischen Common Data Service-Umgebungen mit dem OData Konnektor für Datenflüsse.
ms.date: 05/05/2020
ms.service: powerapps
ms.topic: article
ms.author: demora
search.app:
- PowerApps
ms.openlocfilehash: 7cf920032665f911554d2acca434709256127c8b
ms.sourcegitcommit: 13a78a66408d39b4bc90a72613b0d303abc07b1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "3338247"
---
# <a name="migrate-data-between-common-data-service-environments-using-the-dataflows-odata-connector"></a>Migration von Daten zwischen Common Data Service-Umgebungen mit Hilfe des OData-Konnektors für Datenflüsse

Common Data Service [Web API](/powerapps/developer/common-data-service/webapi/overview) funktioniert mit jeder Technologie, die OData und OAuth unterstützt. Es stehen viele Optionen zur Verfügung, um Daten in und aus Common Data Service zu verschieben. Der OData-Konnektor ist einer der Datenflüsse, der die Migration und Synchronisierung großer Datensätze in Common Data Service unterstützen soll. 

In diesem Artikel führen wir Sie durch die Migration von Daten zwischen Common Data Service-Umgebungen mit Hilfe des OData-Konnektors für Datenflüsse. 

## <a name="prerequisites"></a>Voraussetzungen

- Berechtigung für die Sicherheitsrolle des Systemadministrators oder Systemanpassers sowohl in der Quell- als auch in der Zielumgebung.

- Power Apps, Power Automate oder Common Data Service Lizenz (pro App oder pro Benutzer).

- Zwei Common Data Service [Umgebungen mit Datenbank](/power-platform/admin/create-environment#create-an-environment-with-a-database).

## <a name="scenarios"></a>Szenarien

 - Eine einmalige umgebungs- oder mandantenübergreifende Migration ist erforderlich (z. B. Geomigration)

 - Der Entwickler muss eine App aktualisieren, die in der Produktion verwendet wird. Testdaten werden in ihrer Entwicklungsumgebung benötigt, um leicht Änderungen vornehmen zu können. 

## <a name="step-1-plan-out-the-dataflow"></a>Schritt 1: Planen Sie den Datenfluss

1. Identifizieren Sie die Quell- und Zielumgebung.

    - Die **Quellumgebung** ist die Umgebung, aus der die Daten migriert werden. 

    - Die **Zielumgebung** ist die Umgebung, in die die Daten migriert werden. 

1. Stellen Sie sicher, dass die Entitäten bereits in der Zielumgebung definiert sind. Idealerweise sollten in beiden Umgebungen die gleichen Entitäten mit der gleichen Lösung definiert sein.

1. Beim Importieren von Beziehungen sind mehrere Datenflüsse erforderlich.

    Eine (übergeordnete/unabhängige) bis viele (untergeordnete/abhängige) Entitäten erfordern separate Datenflüsse. Konfigurieren Sie den übergeordneten Datenfluss so, dass er vor allen untergeordneten Entitäten ausgeführt wird, da die Daten in den übergeordneten Entitäten zuerst geladen werden müssen, um den Feldern in den entsprechenden untergeordneten Entitäten korrekt zugeordnet zu werden.

## <a name="step-2-get-the-odata-endpoint"></a>Schritt 2: Bestimmen Sie den OData-Endpunkt 

Common Data Service bietet einen OData-Endpunkt, der keine zusätzliche Konfiguration zur Authentifizierung mit dem Datenfluss-Konnektor erfordert. Es ist ein relativ einfacher Prozess, sich mit der Quellumgebung zu verbinden. 

In diesem Artikel wird erläutert, wie ein neuer Datenfluss mit dem OData-Konnektor eingerichtet werden kann. Siehe [Datenströme erstellen](https://docs.microsoft.com/powerapps/maker/common-data-service/create-and-use-dataflows) Artikel zur Verbindung mit allen Datenquellen, die von Datenströmen unterstützt werden.

Rufen Sie aus der **Quelle** Umgebung den Endpunkt [ODaten](https://docs.microsoft.com/powerapps/developer/common-data-service/view-download-developer-resources) (alias Service-Root-URL) für diese Umgebung ab:

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie in der oberen rechten Ecke die gewünschte Quellumgebung aus.

1. Wählen Sie das Symbol Einstellungen (Zahnrad) in der oberen rechten Ecke und wählen Sie **Erweiterte Einstellungen**.

1. Wählen Sie auf der Seite **Einstellungen** den Dropdown-Pfeil neben **Einstellungen** und wählen Sie dann **Anpassungen**.

1. Wählen Sie auf der Seite **Anpassungen** das Kontrollkästchen **Entwicklerressourcen**.

1. Kopieren Sie die **Service Root-URL** auf den Notizblock.

    > [!div class="mx-imgBorder"]
    > ![Kopieren Sie die Service-Root-URL in den Entwickler-Ressourcen](./media/get-odata-endpoint-url.png)
 
## <a name="step-3-create-a-new-odata-dataflow"></a>Schritt 3: Erstellen eines neuen OData-Datenstroms

Erstellen Sie in der Umgebung **Ziel** einen neuen Datenfluss mit dem OData-Konnektor.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1. Wählen Sie oben rechts die gewünschte Zielumgebung aus der rechten oberen Ecke.

1. Erweitern Sie im linken Navigationsbereich das Menü **Daten**, und wählen Sie **Datenflüsse**.

1. Wählen Sie **Neuer Datenfluss**, um einen neuen Datenfluss zu erstellen. Geben Sie einen aussagekräftigen Namen für den Datenfluss an. Wählen Sie **Erstellen** aus.
   > [!div class="mx-imgBorder"]
   > ![Aufforderung zu einem neuen Datenfluss](./media/enter-name-for-new-dataflow.png)

1. Wählen Sie den Konnektor **OData**.

    > [!div class="mx-imgBorder"]
    > ![OData-Quelle auswählen](media/select-odata-data-source.png)

1. Geben Sie in das Dialogfeld Verbindungseinstellungen die Feldwerte ein:

    > [!div class="mx-imgBorder"]
    > ![Bestätigen, dass die Feldwerte korrekt sind](./media/enter-odata-connector-parameters.png)


    | Feld | Beschreibung |
    |--|--|
    | URL  | Geben Sie die Service-Root-URL im URL-Feld der Verbindungseinstellungen an |
    | Verbindung | Neue Verbindung erstellen. Dieser Wert wird automatisch gewählt, wenn Sie zuvor noch keine OData-Verbindung in Datenströmen hergestellt haben. |
    | Verbindungsname | Optional können Sie den Verbindungsnamen umbenennen, aber es wird automatisch ein Wert eingetragen |  |
    | On-Premise-Daten-Gateway | Keine Für Verbindungen zu diesem Cloud-Dienst ist kein firmeninterner Daten-Gateway erforderlich. |
    | Art der Authentifizierung | Organisationskonto. Wählen Sie die Schaltfläche Anmelden, um den Anmeldedialog zu öffnen, der das mit der Verbindung verbundene Konto authentifiziert. |    

    > [!IMPORTANT] 
    > Deaktivieren Sie Pop-up-Fenster und Cookie-Blocker in Ihrem Browser, um die Azure AD-Authentifizierung zu konfigurieren. Dies ist orthogonal zu der Tatsache, dass Sie den OData-Endpunkt Common Data Service oder eine andere OAuth-basierte Authentifizierungsdatenquelle verwenden. 
    
1. Wählen Sie unten rechts **Weiter**.

## <a name="step-4-select-and-transform-data-with-the-power-query"></a>Schritt 4: Auswahl und Transformation von Daten mit der Leistungsabfrage 

Verwenden Sie Power Query, um die Tabellen auszuwählen und die Daten gemäß Ihren Anforderungen zu transformieren.

Wählen Sie zunächst die Entitäten aus, die übertragen werden müssen. Sie können alle Entitäten in der Quellumgebung durchsuchen und einige der Daten in jeder Entität in einer Vorschau anzeigen.

> [!div class="mx-imgBorder"]
> ![Power Query-Navigator](./media/edit-queries-for-selected-entities.png)

1. Wählen Sie je nach Bedarf eine oder mehrere Entitäten und wählen Sie dann **Daten transformieren**.

    > [!NOTE]
    > Denken Sie beim Importieren von Beziehungen daran, dass der Datenfluss der übergeordneten Entität vor den untergeordneten Entitäten importiert werden muss. Die Daten für den untergeordneten Datenfluss erfordern, dass sich die Daten in der übergeordneten Entität befinden, damit sie korrekt zugeordnet werden können, andernfalls kann es zu einem Fehler kommen.
 
1. Im Fenster **Power Query - Abfragen bearbeiten** können Sie die Abfrage vor dem Import transformieren.

    - Wenn Sie nur Daten migrieren, sollte es nicht notwendig sein, hier irgendetwas zu ändern. 

    - Die Reduzierung der Anzahl unnötiger Spalten verbessert die Datenflussleistung bei größeren Datensätzen.

    > [!TIP]
    > Sie können zurückgehen, um weitere Tabellen in der Option **Daten abrufen** Menüband für denselben OData-Konnektor auszuwählen.

1. Wählen Sie unten rechts **Weiter**.

## <a name="step-5-configure-target-environment-settings"></a>Schritt 5: Konfigurieren der Einstellungen der Zielumgebung

In diesem Abschnitt wird beschrieben, wie die Einstellungen der Zielumgebung definiert werden.

### <a name="step-51-map-entities"></a>Schritt 5.1: Entitäten zuordnen 

Wählen Sie für jede gewählte Entität das Verhalten für den Import dieser Entität in diesen Einstellungen und wählen Sie **Weiter**.

> [!div class="mx-imgBorder"]
> ![Zuordnen von Entitäten](./media/map-entities-to-target.png)

- **In bestehende Entität laden (empfohlen)**

    - Der Datenfluss synchronisiert Daten von der Entität der Quellumgebung mit der Zielumgebung, und dasselbe Entitätenschema ist bereits in der Zielumgebung definiert.

    - Im Idealfall sollte sowohl in der Ziel- als auch in der Quellumgebung dieselbe Lösung verwendet werden, um einen nahtlosen Datentransfer zu ermöglichen. Ein weiterer Vorteil einer vordefinierten Entität ist die bessere Kontrolle darüber, in welcher Lösung die Entität definiert ist und welches Präfix verwendet wird.
    
    - Wählen Sie **Zeilen löschen, die in der Abfrageausgabe nicht mehr existieren**. Dadurch wird sichergestellt, dass die Beziehungen korrekt abgebildet werden, da die Werte für die Nachschlagen beibehalten werden.
    
    - Wenn das Schema in Quell- und Zieltabelle identisch ist, können Sie die Schaltfläche **Auto Zuordnen** wählen, um die Felder schnell zuzuordnen.
    
    - Erfordert eine Schlüsselkonfiguration in der Zielumgebung (da die Felder für den eindeutigen Bezeichner nicht geändert werden können).

- **Neue Entität laden (nicht empfohlen)**

    - Im Idealfall sollte in der Zielumgebung eine Entität aus demselben Lösungsimport wie in der Quellumgebung vordefiniert sein. Es gibt jedoch Fälle, in denen dies nicht durchführbar ist, daher gibt es diese Option zur Auswahl, wenn keine bestehende Entität zum Laden vorhanden ist. 

    - Sie erstellt eine neue benutzerdefinierte Entität in der Standardlösung der Zielumgebung.

- Es gibt die Option **Nicht laden**, aber keine Entitäten in den Datenfluss aufzunehmen, die nicht geladen werden. Sie können in diesem Menü **Zurück** wählen, um zum Power Query Menü zurückzukehren und die nicht benötigten Entitäten zu entfernen.

### <a name="step-52-refresh-settings"></a>Schritt 5.2: Einstellungen aktualisieren

Wählen Sie **Manuell aktualisieren**, da es sich um eine einmalige Migration handelt, und wählen Sie **Erstellen**. 

## <a name="step-6-run-the-dataflow"></a>Schritt 6: Führen Sie den Datenfluss aus

Das anfängliche Laden des Datenflusses beginnt, wenn Sie die Schaltfläche **Erstellen** wählen. 

> [!div class="mx-imgBorder"]
> ![Manuell aktualisieren](./media/initiate-dataflow-process.png)

Sie können einen Datenfluss manuell initiieren, indem Sie **(...)** in der Datenflussliste wählen. Stellen Sie sicher, dass abhängige Datenflüsse ausgeführt werden, nachdem die übergeordneten Flüsse abgeschlossen sind.

> [!div class="mx-imgBorder"]
> ![Manuell aktualisieren](./media/refresh-dataflow-manually.png) 

## <a name="tips"></a>Tipps

- Probieren Sie zunächst eine Entität aus, um die Schritte durchzugehen, und bauen Sie dann alle Datenflüsse auf.

- Wenn es mehr Entitäten gibt, die größere Datenmengen enthalten, sollten Sie in Erwägung ziehen, mehrere separate Datenflüsse für einzelne Entitäten zu konfigurieren.

- Bei einer zu vielen Beziehungen sind separate Datenflüsse für jede Entität erforderlich. Konfigurieren und starten Sie den Datenfluss der übergeordneten Entität (auch als eine oder unabhängige Entität bezeichnet) vor der untergeordneten Entität (auch als viele oder abhängige Entitäten bezeichnet).

- Wenn es Fehler bei der Aktualisierung des Datenflusses gibt, können Sie die Aktualisierungshistorie im Menü **(...)** in der Datenflussliste einsehen und jedes Aktualisierungsprotokoll herunterladen.

## <a name="limitations"></a>Einschränkungen

- Viele zu viele Importe von Beziehungsdaten werden nicht unterstützt.

- Übergeordnete Datenströme müssen manuell so konfiguriert werden, dass sie vor untergeordneten Datenströmen ablaufen.
