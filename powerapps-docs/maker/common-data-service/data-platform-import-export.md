---
title: Importieren oder Exportieren von Daten aus Common Data Service für Apps
description: Verwenden der Excel-Funktionen zum Abrufen und Exportieren von Daten für die Ausführung eines Massenimports oder -exports von Daten aus Excel- oder CSV-Dateien in bzw. aus Entitäten in Common Data Service für Apps.
author: sabinn-msft
ms.service: powerapps
ms.topic: conceptual
ms.component: cds
ms.date: 05/14/2018
ms.author: sabinn
ms.openlocfilehash: 7f3e16be5bba1874759e0f9e40dc455f1e29c2bc
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697461"
---
# <a name="import-or-export-data-from-the-common-data-service-for-apps"></a>Importieren oder Exportieren von Daten aus Common Data Service für Apps

Wenn Sie Massenimporte und -exporte von Daten aus Excel- oder CSV-Dateien ausführen möchten, können Sie die Features „Get Data from Excel file“ (Daten aus Excel-Datei abrufen) und „Export Data“ (Daten exportieren) für aktualisierte Common Data Service für Apps-Umgebungen verwenden.

Es gibt zwei Möglichkeiten zum Importieren von Dateien in eine Entität aus einer Excel- oder CSV-Datei:

## <a name="option-1-import-by-creating-and-modifying-a-file-template"></a>Option 1: Importieren durch Erstellen und Anpassen einer Dateivorlage

Jede Entität weist Pflichtfelder auf, die in Ihrer Eingabedatei enthalten sein müssen. Wenn Sie Probleme vermeiden möchten, wird empfohlen, dass Sie zunächst eine Vorlage erstellen, indem Sie Daten aus einer Entität exportieren und diese (mit Ihren Daten angepasste) Datei dann verwenden, um Daten in die Entität zu importieren. Dadurch sparen Sie Zeit und Mühe, da Sie nicht für jede Entität die jeweiligen Pflichtfelder hinzufügen müssen.

1. Vorbereiten der Dateivorlage

    - Exportieren Sie zunächst die Entitätsdaten in eine CSV-Datei, indem Sie die im Abschnitt „Exportieren von Daten in CSV“ aufgeführten Schritte ausführen.
    - Definieren Sie einen Plan, um sicherzustellen, dass die Daten eindeutig sind. Verwenden Sie dafür entweder Primärschlüssel oder Alternativschlüssel.
    - Nachfolgend erhalten Sie Informationen dazu, wie Sie sicherstellen, dass die Daten eindeutig sind, bevor Sie Daten in eine Entität importieren.

1. Anpassen der Datei mit Ihren Daten

    - Kopieren Sie Daten aus Ihrer Excel- oder CSV-Datei in die Vorlage, die Sie zuvor erstellt haben.

1. Importieren der Datei
    - Erweitern Sie unter [powerapps.com](https://web.powerapps.com/) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.
    - Wählen Sie die Entität aus, in die Sie Daten importieren möchten.
    - Klicken oder tippen Sie erst im oberen Bereich auf die Auslassungspunkte oder das Menü, dann auf **Daten abrufen** und anschließend auf **Daten aus Excel abrufen**.

> [!NOTE]
> Wenn Sie die Daten in mehr als eine Entität importieren möchten, klicken oder tippen Sie im Menü im oberen Bereich auf **Daten abrufen** > **Daten aus Excel abrufen**. Sie sollten dann mehrere Entitäten auswählen und auf **Weiter** klicken oder tippen können.

![Beispiel für das Importieren von Daten in die Entität „Konto“](./media/data-platform-import-export/import-data-to-account.png)

- Dadurch gelangen Sie zur Anzeige **Daten importieren**, über die Sie auswählen können, ob Sie die Daten aus einer Excel- oder einer CSV-Datei importieren möchten.
- Klicken oder tippen Sie auf **Hochladen**.
- Wählen Sie Ihre Datei aus, und befolgen Sie die Anweisungen zum Starten des Dateiuploads.

![Beispiel für den Upload einer Datei aus der Entität „Konto“](./media/data-platform-import-export/upload-account.png)

- Nachdem die Datei hochgeladen und der Zuordnungsstatus grün angezeigt wird, klicken Sie in der oberen rechten Ecke auf **Importieren**. Wenn bei der Zuordnung Fehler entstehen, finden Sie nachfolgend weitere Informationen zum Navigieren und Beheben von Zuordnungsfehlern.

![Beispiel für einen erfolgreichen Zuordnungsstatus und eine Schaltfläche für den Import](./media/data-platform-import-export/success-map-imp.png)

- Sobald die Meldung **Der Import wurde erfolgreich abgeschlossen.** angezeigt wird, sehen Sie die Gesamtanzahl der Einfügevorgänge und Updates.

![Beispiel für einen erfolgreichen Import, einschließlich der Anzahl der Einfügevorgänge und Updates](./media/data-platform-import-export/success-imp-insert.png)

> [!NOTE]
> Wir verwenden die Upsert-Logik (Update or Insert, Aktualisieren oder Einfügen), um den Datensatz (falls bereits vorhanden) zu aktualisieren oder einen neuen Datensatz hinzuzufügen.

## <a name="option-2-import-by-bringing-your-own-source-file"></a>Option 2: Importieren mithilfe einer eigenen Quelldatei

Wenn Sie über erweiterte Kenntnisse verfügen und sich mit den Pflichtfeldern für die entsprechende Common Data Service für Apps-Entität auskennen, können Sie Ihre eigene Excel- oder CSV-Quelldatei definieren und die unter **Importieren der Datei** aufgeführten Schritte ausführen.

## <a name="navigating-mapping-errors"></a>Navigieren von Zuordnungsfehlern

Wenn ein Zuordnungsfehler auftritt, nachdem Sie Ihre Datei hochgeladen haben, klicken Sie auf **Map status** (Zuordnungsstatus), und führen Sie die folgenden Schritte aus, um Fehler bei der Feldzuordnung zu untersuchen und zu beheben.

- Verwenden Sie die Dropdownliste auf der rechten Seite unter **Anzeigen**, um sich die **Nicht zugeordneten Felder**, **Felder mit Fehlern** oder **Pflichtfelder** anzusehen.

> [!TIP]
> Je nachdem, ob Sie eine Warnung oder einen Fehler erhalten, sollten Sie über die Dropdownliste unter **Feldzuordnungen** entweder die **Nicht zugeordneten Felder** oder **Felder mit Fehlern** untersuchen.

![Beispiel für eine partielle Übereinstimmung aufgrund von Warnungen mit Feldzuordnungen](./media/data-platform-import-export/partial-match.png)

![Beispiel für Probleme bei der Navigation von Feldzuordnungen](./media/data-platform-import-export/navigate-mappings.png)

![ Beispiel zum Untersuchen und Beheben von Warnungen mit Feldzuordnungen](./media/data-platform-import-export/inspect-warnings.png)

- Sobald Sie alle Fehler und/oder Warnungen bearbeitet haben, klicken Sie in der oberen rechten Ecke auf **Änderungen speichern**. Dadurch sollten Sie zurück zur Anzeige **Daten importieren** gelangen.
- Sobald in der Spalte **Zuordnungsstatus** in grün **Abgeschlossen** angezeigt wird, klicken Sie in der oberen rechten Ecke auf **Importieren**.
- Sobald die Meldung **Der Import wurde erfolgreich abgeschlossen.** angezeigt wird, sehen Sie die Gesamtanzahl der Einfügevorgänge und Updates.

## <a name="ensuring-uniqueness-while-importing-data-into-entity-from-excel-or-csv"></a>Sicherstellen der Eindeutigkeit beim Importieren von Daten in eine Entität aus Excel- oder CSV-Dateien

Common Data Service für Apps-Entitäten verwenden einen Primärschlüssel, um Datensätze eindeutig innerhalb einer CDS-Entitätentabelle zu identifizieren. Beim Primärschlüssel für eine CDS-Entität handelt es sich um einen Globally Unique Identifier (GUID), der die Standardbasis für die Datensatzkennung darstellt. Im Rahmen von Datenvorgängen wie das Importieren von Daten in CDS-Entitäten werden die Standardprimärschlüssel sichtbar.

Beispiel: Der Primärschlüssel für die Entität „Konto“ lautet „accountid“.

![Beispielexportdatei aus der Entität „Konto“, die „accountid“ als Primärschlüssel anzeigt.](./media/data-platform-import-export/export-pk.png)

Gelegentlich kann es dazu kommen, dass ein Primärschlüssel nicht ausreicht und/oder nicht den Ansprüchen der Integration von Daten aus einer externen Quelle entspricht. In diesem Zusammenhang ermöglicht es CDS, Alternativschlüssel zu definieren, um einen Datensatz eindeutig anstelle eines Primärschlüssels zu identifizieren.

Beispiel: Für die Entität „Konto“ können Sie „transactioncurrencyid“ als Alternativschlüssel festlegen, indem Sie eine auf einem natürlichen Schlüssel basierende Identifizierung verwenden (verwenden Sie z.B. anstelle eines GUID-Werts wie oben dargestellt (*88c6c893-5b45-e811-a953-000d3a33bcb9*) „US Dollar“). Sie können auch ein Währungssymbol oder einen Währungsnamen als Schlüssel verwenden.

![Beispiel für das Erstellen eines Alternativschlüssels für die Entität „Währung“](./media/data-platform-import-export/create-ak.png)

![Beispielexportdatei aus der Entität „Konto“, die den Währungsnamen als natürlichen Schlüssel anzeigt](./media/data-platform-import-export/export-nk.png)

Der Benutzer kann weiterhin Primärschlüssel als Bezeichner verwenden, nachdem er Alternativschlüssel angegeben hat. D.h., im obenstehenden Beispiel ist die Datei gültig, wenn es sich bei den GUIDs um gültige Daten handelt.

## <a name="export-data-to-csv"></a>Exportieren von Daten in CSV

Sie können Daten einmalig von einer Standardentität oder einer benutzerdefinierten Entität exportieren, und Sie können Daten von mehr als einer Entität gleichzeitig exportieren. Wenn Sie Daten aus mehr als einer Entität exportieren, wird jede Entität in eine eigene Microsoft-CSV-Datei exportiert.

1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com/) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.
1. Wählen Sie die Entität aus, aus der Sie Daten exportieren möchten.
1. Klicken oder tippen Sie erst im oberen Bereich auf die Auslassungspunkte oder das Menü, dann auf **Exportieren** und anschließend auf **Daten**.

    ![Beispiel zum Exportieren von Daten aus der Entität „Konto“](./media/data-platform-import-export/export-account.png)

    > [!NOTE]
    > Klicken oder tippen Sie im Menü im oberen Bereich zum Exportieren von Daten aus mehreren Entitäten erst auf **Exportieren** und dann auf **Daten**. Sie sollten dann mehrere Entitäten auswählen können.

1. Sobald der Export erfolgreich abgeschlossen wurde, sollten Sie **Exportierte Daten herunterladen** können. Danach erhalten Sie einen Link zu einer herunterladbaren CSV-Datei.

    ![Beispielexport, der einen erfolgreichen Export mit einem Link zu einer herunterladbaren Datei anzeigt.](./media/data-platform-import-export/export-success.png)

## <a name="unsupported-data-types"></a>Nicht unterstützte Datentypen

Die folgenden Datentypen werden derzeit nicht unterstützt.

- Zeitzone
- Optionen mit Mehrfachauswahl
- Bild
