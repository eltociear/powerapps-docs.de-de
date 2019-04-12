---
title: Importieren oder Exportieren von Daten vom Common Data Service
description: 'Führen Sie einen Massenimporti und -export von Daten aus Excel oder CSV-Dateien in Entitäten in Common Data Service durch, indem Sie die Funktion "Daten aus Excel abrufen" verwenden'
author: sabinn-msft
ms.service: powerapps
ms.topic: conceptual
ms.component: cds
ms.date: 05/14/2018
ms.author: sabinn
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="import-or-export-data-from-common-data-service"></a>Importieren oder Exportieren von Daten vom Common Data Service

Um einen Massenimport und -export von Daten aus Microsoft Excel oder CSV-Dateien durchzuführen, verwenden Sie die Funktionen "Daten aus Excel-Datei abrufen" und "Daten exportieren" für aktualisierte Common Data Service-Umgebungen.

Es gibt zwei Möglichkeiten, um Dateien aus Excel oder aus CSV-Dateien in Entitäten zu importieren.

## <a name="option-1-import-by-creating-and-modifying-a-file-template"></a>Option 1: Import durch Erstellen und Ändern einer Dateivorlage

Jede Entität besitzt Pflichtfelder, die in der Eingabedatei vorhanden sein müssen. Wir empfehlen, dass Sie eine Vorlage erstellen. Exportieren Sie zunächst Daten aus der Entität. Verwenden Sie dieselbe Datei (mit Ihren Daten geändert), um Daten in die Entität zu importieren. Diese Vorlage spart Zeit und Aufwand. Sie müssen nicht an jedes der Pflichtfelder für jede Entität denken.

1. Bereiten Sie die Dateivorlage vor.

    a. Exportieren Sie die Entitätsdaten in die CVS-Datei. Befolgen Sie die Schritte unter **Daten nach CSV exportieren**.  
    b. Definieren Sie einen Plan, um sicherzustellen, dass die Daten eindeutig sind. Verwenden Sie entweder **Primärschlüssel** oder **Alternativschlüssel**.  
    c. Im nächsten Abschnitt finden Sie Anweisungen, sicherzustellen, dass die Daten eindeutig sind, bevor Sie sie in eine Entität importieren. 

1. Ändern Sie die Datei mit Ihren Daten.

    - Kopieren Sie Daten aus den CSV-Datei in Excel oder die Vorlage, die Sie soeben erstellt haben.

1. Importieren Sie die Datei.  
    a. Auf [powerapps.com](https://web.powerapps.com/), erweitern Sie den Abschnitt **Daten**. Wählen Sie im linken Navigationsbereich die Option **Entitäten** aus.  
    b. Wählen Sie die Entität aus, in die Sie die Daten importieren möchten.  
    c. Wählen Sie die Auslassungspunkte oder das obere Menü aus. Wählen Sie **Daten abrufen** aus: Wählen Sie **Daten aus Excel abrufen** aus.  

    > [!NOTE]
    > Wenn Sie Daten in mehrere Entitäten importieren möchten, wählen Sie im oberen Menü **Daten abrufen** aus. Wählen Sie **Daten aus Excel abrufen** aus. Dann können Sie mehrere Entitäten auswählen und **Weiter** auswählen.

    > [!div class="mx-imgBorder"] 
    > ![Beispiel des Datenimports in eine **Firma**-Entität](./media/data-platform-import-export/import-data-to-account.png)

    d. Wählen Sie im Bildschirm **Daten importieren** aus, ob Daten aus einer Excel- oder einer CSV-Datei importierten werden.  
    e. Klicken Sie auf **Hochladen**.  
    f. Wählen Ihre Datei aus. Folgen Sie den Anweisungen, um Ihre Datei hochzuladen.  

    > [!div class="mx-imgBorder"] 
    > ![Beispiel für das Hochladen einer Datei in eine **Firma**-Entität](./media/data-platform-import-export/upload-account.png)

    g. Nachdem die Datei hochgeladen wurde und der **Zuordnungsstatus** grün ist, wählen Sie **Importieren** in der oberen rechten Ecke aus. Im nächsten Abschnitt finden Sie Informationen zum Navigieren und Beheben von Zuordnungsfehlern.  

    > [!div class="mx-imgBorder"] 
    > ![Beispiel für einen erfolgreichen **Zuordnungsstatus** und eine **Importieren**-Schaltfläche](./media/data-platform-import-export/success-map-imp.png)

    h. Nachdem der Import erfolgreich beendet wurde, wird die Gesamtanzahl der Einfügungen und Updates angezeigt.  

    > [!div class="mx-imgBorder"] 
    > ![Beispiel eines erfolgreichen Imports, der die Anzahl der Einfügungen und Updates anzeigt](./media/data-platform-import-export/success-imp-insert.png)

    > [!NOTE]
    > Mithilfe der Upsert (Update oder Einfügen)-Logik, um den Datensatz zu aktualisieren, wenn er bereits vorhanden ist, oder einen neuen Datensatz zu erstellen.

## <a name="option-2-import-by-bringing-your-own-source-file"></a>Option 2: Import durch Bereitstellen der eigenen Quelldatei

Wenn Sie ein fortgeschrittener Benutzer sind und die erforderlichen Felder für eine bestimmte Entität für Common Data Service-Entitäten kennen, definieren Sie Ihre eigene Excel- oder CSV-Quelldatei. Folgen Sie den Schritten in **Die Datei importieren**.

## <a name="navigate-mapping-errors"></a>Zuordnungsfehler navigieren

Wenn Sie Zuordnungsfehler erhalten, nachdem Sie Ihre Datei hochladen, wählen Sie **Status zuordnen** aus. Führen Sie die folgenden Schritte aus, um die Feldzuordnungsfehler zu überprüfen und zu beheben.

1. Verwenden Sie das Dropdownmenü rechts unter **Anzeigen**, um die Felder **Nicht zugeordnete Felder**, **Felder mit Fehler** oder **Erforderliche Felder** zu durchzulaufen.

    > [!TIP]
    > Abhängig davon, ob Sie eine Warnmeldung oder einen Fehler erhalten, untersuchen Sie **Nicht zugeordnete Felder** oder **Felder mit Fehler** über das Dropdownmenü in **Feldzuordnungen**.

    > [!div class="mx-imgBorder"] 
    > ![Beispiel einer teilweisen Übereinstimmung aufgrund von Warnungen bei Feldzuordnungen](./media/data-platform-import-export/partial-match.png)

    > [!div class="mx-imgBorder"] 
    > ![Beispiel zum Navigieren von Feldzuordnungsproblemen](./media/data-platform-import-export/navigate-mappings.png)

    > [!div class="mx-imgBorder"] 
    > ![Beispiel zum Überprüfen und Beheben von Warnungen bei Feldzuordnungen](./media/data-platform-import-export/inspect-warnings.png)

2. Nachdem Sie alle Fehler und Warnungen behoben haben, wählen Sie **Änderungen speichern** in der oberen rechten Ecke aus. Sie wechseln zurück zum Bildschirm **Daten importieren**.
3. Wenn die Spalte **Zuordnungsstatus** in grün **Abgeschlossen** anzeigt, wählen Sie **Importieren** in der oberen rechten Ecke aus.
4. Wenn Sie die Meldung **Import erfolgreich abgeschlossen** erhalten, werden alle Einfügungen und Updates angezeigt.

## <a name="ensure-uniqueness-when-you-import-data-into-an-entity-from-excel-or-csv"></a>Stellen Sie die Eindeutigkeit sicher, wenn Sie Daten aus Excel oder CSV in eine Entität importieren

Common Data Service-Entitäten verwenden einen Primärschlüssel, um Datensätze in einer Common Data Service-Tabelle eindeutig zu identifizieren. Der Primärschlüssel für eine Common Data Service-Entität ist ein GUID (globally unique identifier). Es bietet die Standardgrundlage für Datensatzidentifikation. Datenvorgänge, wie das Importieren von Daten in Common Data Service-Entitäten, zeigen den Standardprimärschlüssel an.

Beispiel:  
Der Primärschlüssel für eine Entität **Firma** ist **accountid**.

   > [!div class="mx-imgBorder"] 
   > ![Beispielexportdatei aus einer Entität **Firma** zeigt **accountid** als Primärschlüssel](./media/data-platform-import-export/export-pk.png)

Gelegentlich funktioniert ein Primärschlüssel möglicherweise nicht, wenn Sie Daten aus einer externen Quelle integrieren. Verwenden Sie Common Data Service, um Alternativschlüssel zu definieren, die einen Datensatz anstelle des Primärschlüssels eindeutig identifizieren.

Beispiel:  
Als Entität **Firma** legen Sie möglicherweise **transactioncurrencyid** als Alternativschlüssel fest, indem Sie eine natürliche schlüsselbasierte ID verwenden. Verwenden Sie beispielsweise **US-Dollar** anstelle des GUID-Werts **88c6c893-5b45-e811-a953-000d3a33bcb9**, wie zuvor angezeigt. Sie können auch das **Währungssymbol** oder den **Währungsnamen** als Schlüssel auswählen.

   > [!div class="mx-imgBorder"] 
   > ![Beispiel zum Erstellen eines Alternativschlüssels in einer **Währung**-Entität](./media/data-platform-import-export/create-ak.png)

   > [!div class="mx-imgBorder"] 
   > ![Beispielexportdatei aus einer Entität **Firma** zeigt **Währungsname** als natürlichen Primärschlüssel](./media/data-platform-import-export/export-nk.png)

Benutzer können Primärschlüssels noch als Bezeichner verwenden, nachdem Sie Alternativschlüssel angegeben haben. Im vorangehenden Beispiel ist die erste Datei immer noch gültig, wenn GUIDS gültige Daten sind.

## <a name="export-data-to-csv"></a>Exportieren von Daten nach CSV

Sie können einen einmaligen Datenexport aus einer Standardentität oder einer benutzerdefinierten Entität ausführen. Und Sie können Daten aus mehr als einer Entität nacheinander exportieren. Wenn Sie Daten aus mehr als einer Entität exportieren, wird jede Entität in seine eigene Microsoft-CSV-Datei exportiert.

1. Auf [powerapps.com](https://web.powerapps.com/), erweitern Sie den Abschnitt **Daten**. Wählen Sie im linken Navigationsbereich die Option **Entitäten** aus.
1. Wählen Sie die Entität aus, aus der Sie die Daten exportieren möchten.
1. Wählen Sie die Auslassungspunkte oder das obere Menü aus. Klicken Sie auf **Exportieren**. Wählen Sie **Daten** aus.

    > [!div class="mx-imgBorder"] 
    > ![Beispiel des Datenexports aus einer **Firma**-Entität](./media/data-platform-import-export/export-account.png)

    > [!NOTE]
    > Wenn Sie Daten aus mehreren Entitäten exportieren, wählen Sie im oberen Menü **Exportieren** aus. Wählen Sie **Daten** aus. Sie können mehrere Entitäten auswählen.

1. Wenn der Export erfolgreich beendet wird, können Sie **Exportierte Daten herunterladen** auswählen. Dieser Download stellt einen Link zu einer herunterladbaren CSV-Datei bereit.

    > [!div class="mx-imgBorder"] 
    > ![Beispielexport, der einen erfolgreichen Export mit Link zu einer herunterladbaren Datei zeigt](./media/data-platform-import-export/export-success.png)

## <a name="unsupported-data-types"></a>Nicht unterstützte Datentypen

Die folgenden Datentypen werden derzeit nicht unterstützt.

- Zeitzone
- Optionssatz-Mehrfachauswahl
- Bild
