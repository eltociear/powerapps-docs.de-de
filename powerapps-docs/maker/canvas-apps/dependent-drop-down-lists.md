---
title: Erstellen Sie eine abhängige Dropdown-Liste in einer Canvas-app | Microsoft-Dokumentation
description: Erstellen Sie eine Dropdown-Liste, die filtert, eine andere Dropdown-Liste in einer Canvas-app in PowerApps.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e00c81f25de9a764e8f6d963ff94f3c0ffe052a2
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58357251"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>Erstellen von abhängigen Dropdownlisten in einer Canvas-app

Wenn Sie abhängige (oder cascading) Dropdown-Listen erstellen, wählen Benutzer eine Option in einer Liste, um Filteroptionen in einer anderen Liste. Viele Organisationen erstellen abhängige enthält Informationen zum Ausfüllen von Formularen effizienter. Z. B. Benutzer können auswählen, ein Land oder Region, um eine Liste von Orten zu filtern, oder Benutzer können wählen Sie eine Kategorie aus, um nur die Codes in dieser Kategorie anzuzeigen.

Als bewährte Methode erstellen Sie eine Datenquelle für die Werte in der "Übergeordnet" und "Child" Listen (z. B. Länder/Regionen und Städten), die von der Datenquelle getrennt, mit denen Benutzer über die app aktualisiert. Wenn Sie diesen Ansatz verwenden, können Sie die derselben übergeordneten und untergeordneten Daten in mehr als eine app, und Sie können die Daten aktualisieren, ohne erneute Veröffentlichung der app oder apps, die sie verwenden. Erreichen Sie das gleiche Ergebnis mithilfe einer Sammlung oder eine statische Daten, aber es wird nicht empfohlen für Unternehmensszenarios.

Speichern Sie für das Szenario in diesem Thema Mitarbeiter senden Probleme, die eine **Incidents** Liste durch ein Formular. Mitarbeiter geben Sie nicht nur den Speicherort des Speichers auf dem der Fehler aufgetreten ist, sondern auch die Abteilung in diesen Speicherort. Nicht alle Speicherorte haben die gleichen Abteilungen, sodass eine **Speicherorte** Liste wird sichergestellt, dass die Mitarbeiter eine Abteilung für einen Standort angeben können, das diese Abteilung keine.

In diesem Thema wird eine SharePoint-Listen als Datenquellen verwendet, aber alle tabellarischen Datenquellen in gleicher Weise.

## <a name="create-data-sources"></a>Erstellen von Datenquellen

Ein **Speicherorte** Liste enthält die Abteilungen an jedem Standort.

| Location | Department |
|----------------|------------------|
| Eganville      | Bakery           |
| Eganville      | Deli             |
| Eganville      | Zu erzeugen          |
| Renfrew        | Bakery           |
| Renfrew        | Deli             |
| Renfrew        | Zu erzeugen          |
| Renfrew        | Apotheken         |
| Renfrew        | Blumen           |
| Pembroke       | Bakery           |
| Pembroke       | Deli             |
| Pembroke       | Zu erzeugen          |
| Pembroke       | Blumen           |

Ein **Incidents** Liste zeigt Kontaktinformationen und Informationen über jeden Vorfall. Erstellen Sie die Spalte "Date" als eine **Datum** Spalte, aber erstellen Sie die anderen Spalten als **Textzeile** Spalten, die Konfiguration vereinfachen und zu vermeiden [Delegierung](./delegation-overview.md) Warnungen im PowerApps ist.

| Vorname | Nachname | Telefonnummer     | Location | Department | Beschreibung       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | (206) 555 - 1022 | Eganville      | Zu erzeugen    | Ich hatte ein Problem mit...   | 2/12/2019 |
| Moses     | Laflamme     | (425) 555 - 1044 | Renfrew        | Blumen     | Ein Problem habe... | 2/13/2019 |

Standardmäßig gehören benutzerdefinierte SharePoint-Listen ein **Titel** Spalte an, dass Sie nicht umbenennen oder entfernen, und sie muss Daten enthalten, bevor Sie ein Element in der Liste speichern können. Die Spalte so konfigurieren, dass er nicht, dass Daten erfordert:

1. Wählen Sie das Zahnradsymbol in der Nähe der oberen rechten Ecke, und wählen Sie dann **Listeneinstellungen**.
1. Auf der **Einstellungen** Seite **Titel** in der Liste der Spalten.
1. Klicken Sie unter **diese Spalte muss Informationen enthalten**Option **keine**.

Nach dieser Änderung können Sie ignorieren die **Titel** Spalte, oder Sie können [entfernen](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8) aus der Standardansicht, wenn mindestens eine weitere Spalte angezeigt wird.

## <a name="open-the-form"></a>Öffnen Sie das Formular

1. Öffnen der **Incidents** aus, und wählen Sie dann **PowerApps** > **Anpassen von Formularen**.

    > [!div class="mx-imgBorder"]
    > ![Öffnen Sie die Liste der Vorfälle, und wählen Sie dann PowerApps > Anpassen von Formularen. ](./media/dependent-drop-down-lists/open-form.png "Öffnen Sie die Liste der Vorfälle, und wählen Sie dann PowerApps > Anpassen von Formularen.")

    Eine Browserregisterkarte mit das Standardformular in PowerApps Studio wird geöffnet.

1. (optional) In der **Felder** Bereich, zeigen Sie auf die **Titel** Feld, wählen Sie die Auslassungspunkte (...), die angezeigt wird, und wählen Sie dann **entfernen**.

    Wenn Sie geschlossen haben die **Felder** Bereich können Sie es öffnen erneut durch Auswahl **SharePointForm1** in der linken Navigationsleiste klicken und dann **Bearbeitungsfelder** auf die **Eigenschaften** Registerkarte im rechten Bereich.

1. (optional) Wiederholen Sie den vorherigen Schritt zum Entfernen der **Anlagen** Feld aus dem Formular.

    Das Formular wird mit nur die Felder, die Sie hinzugefügt haben.

    > [!div class="mx-imgBorder"]
    > ![Ohne die Felder für Titel und Anlagen bilden](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>Ersetzen Sie die Steuerelemente

1. In der **Felder** Bereich, wählen Sie den Pfeil nach unten neben **Speicherort**.

    Wenn Sie geschlossen haben die **Felder** Bereich können Sie es öffnen erneut durch Auswahl **SharePointForm1** in der linken Navigationsleiste klicken und dann **Bearbeitungsfelder** auf die **Eigenschaften** Registerkarte im rechten Bereich.

1. Öffnen der **Steuerelementtyp** aus, und wählen Sie dann **zulässige Werte**.

    > [!div class="mx-imgBorder"]
    > ![Zulässige Werte](./media/dependent-drop-down-lists/change-control.png)

    Die Eingabeelemente ändert sich in einem **Dropdown** Steuerelement.

1. Wiederholen Sie diese Schritte für die **Abteilung** Karte.

## <a name="add-the-locations-list"></a>Fügen Sie der Liste der Speicherorte

1. Wählen Sie **Ansicht** > **Datenquellen** > **Datenquelle hinzufügen**.

1. Wählen oder erstellen Sie eine SharePoint-Verbindung und geben Sie dann auf die Website, enthält die **Speicherorte** Liste.

1. Wählen Sie das Kontrollkästchen für die Liste, und wählen Sie dann **Connect**.

    > [!div class="mx-imgBorder"]
    > ![Bereich "Daten"](./media/dependent-drop-down-lists/select-list.png)

    Die Liste der Verbindungen zeigt die **Incidents** Liste, auf dem die Form basiert, und die **Speicherorte** Liste, die Standorte und Abteilungen in der Form identifiziert wird.

    > [!div class="mx-imgBorder"]
    > ![SharePoint-Datenquellen](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>Entsperren von Karten

1. Wählen Sie die **Speicherort** Karte, wählen die **erweitert** im rechten Bereich die Registerkarte, und wählen Sie dann **Unlock so ändern Sie Eigenschaften**.

1. Wiederholen Sie den vorherigen Schritt für die **Abteilung** Karte.

## <a name="rename-the-controls"></a>Benennen Sie die Steuerelemente

Wenn Sie die Steuerelemente umbenennen, können Sie sie leichter identifizieren und die Beispiele sind leichter zu verstehen. Um weiteren bewährten Methoden zu ermitteln, überprüfen Sie die [Codierung Standards und Leitlinien Whitepaper](https://aka.ms/powerappscanvasguidelines).

1. In der **Speicherort** Karte, wählen die **Dropdown** Steuerelement.

1. Benennen Sie das ausgewählte Steuerelement im oberen Bereich im rechten Bereich durch eingeben oder einfügen **DdLocation**.

    > [!div class="mx-imgBorder"]
    > ![Umbenennen eines Steuerelements](./media/dependent-drop-down-lists/rename-control.png)

1. Wiederholen Sie die vorherigen beiden Schritte in der **Abteilung** -Karte, um das Umbenennen der **Dropdown** die Steuerung an **DdDepartment**.

## <a name="configure-the-locations"></a>Konfigurieren Sie die Speicherorte

1. Legen Sie die **Elemente** Eigenschaft **Ddlocation** auf diese Formel:

    `Distinct(Locations, Location)`

1. (optional) Während Sie die Alt-Taste gedrückt halten, öffnen Sie **DdLocation**, und vergewissern Sie sich, dass die Liste mit allen drei Speicherorten enthält.

## <a name="configure-the-departments"></a>Konfigurieren Sie die Abteilungen

1. Wählen Sie **DdDepartment** , und klicken Sie auf die **Eigenschaften** im rechten Bereich auf der Registerkarte **abhängig.**

1. Klicken Sie unter **übergeordnete Steuerelement**, sicher, dass **DdLocation** angezeigt wird, in der oberen Liste und **Ergebnis** in der unteren Liste angezeigt wird.

    > [!NOTE]
    > Wenn Sie nicht auf eine Zeichenfolge, sondern auf die tatsächliche ID der Zeile der Daten entsprechen möchten, wählen Sie **ID** anstelle von **Ergebnis**.

1. Klicken Sie unter **übereinstimmende Feld**Option **Speicherorte** wählen Sie in der oberen Liste **Speicherort** in der unteren Liste, und wählen Sie dann **übernehmen**.

    > [!div class="mx-imgBorder"]
    > ![Hängt von link](./media/dependent-drop-down-lists/depends-on.png)

    Die **Elemente** Eigenschaft **DdDepartment** wird auf diese Formel festgelegt:

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    Diese Formel filtert die Elemente im **DdDepartment** basierend auf der Auswahl des Benutzers in **DdLocation**. Eine solche Konfiguration wird sichergestellt, dass die Liste "untergeordnete" Abteilungen die Daten für den Speicherort der "übergeordneten" als widerspiegelt das **Speicherorte** Liste in SharePoint gibt.

1. Auf der **Eigenschaften** Registerkarte im rechten Bereich, öffnen Sie die Liste neben **Wert**, und wählen Sie dann **Abteilung**.

    Dieser Schritt wird den Anzeigetext auf Optionen für die aus der **Abteilung** Spalte die **Speicherorte** Liste in SharePoint.

    > [!div class="mx-imgBorder"]
    > ![Wert für die Abteilung](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>Testen Sie das Formular

Während es sich bei gedrückter Alt-Taste, öffnen Sie die Liste der Speicherorte, wählen Sie eine, öffnen Sie die Liste von Abteilungen, und wählen Sie dann eine.

Die Listen der Standorte und Abteilungen spiegelt wider, die Informationen in den **Speicherorte** Liste in SharePoint.

> [!div class="mx-imgBorder"]
> ![Öffnen Sie die Liste der Standorte, ändern Sie die Auswahl von Renfrew in Pembroke und öffnen Sie dann die Liste von Abteilungen](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>Speichern Sie und öffnen Sie das Formular (optional)

1. Öffnen der **Datei** Menü, und wählen Sie dann **speichern** > **in SharePoint veröffentlichen** > **Veröffentlichen in SharePoint**.

1. Klicken Sie in der oberen linken Ecke auf den Zurück-Pfeil, und klicken Sie dann auf **Zurück zu SharePoint**.

1. Klicken Sie auf der Befehlsleiste auf **Neu**, um Ihr angepasstes Formular zu öffnen.

## <a name="faq"></a>FAQ

**Keine Daten angezeigt: die Quellen sind alle leer oder die falschen Daten.**
Bestätigen Sie, ob Sie das richtige Feld für das Steuerelement in einer der folgenden Methoden anzeigen:

- Wählen Sie eine Dropdown-Liste, und wählen Sie dann die **Wert** -Eigenschaft in der **Eigenschaften** Registerkarte im rechten Bereich.

    > [!div class="mx-imgBorder"]
    > ![Dropdown-Änderung](./media/dependent-drop-down-lists/drop-down-display-field.png)

- Wählen Sie ein Kombinationsfeld, und stellen Sie sicher, dass der primäre Text das Feld, das Sie anzeigen möchten.

    > [!div class="mx-imgBorder"]
    > ![Kombinationsfeld ändern](./media/dependent-drop-down-lists/combo-box-display-field.png)

**Meine untergeordnetes Dropdown-Liste enthält doppelte Elemente.**
Dieses Symptom ist wahrscheinlich aufgrund einer **LookUp** Spalte in SharePoint oder eine **Auswahlmöglichkeiten** -Funktion in PowerApps. Um die Duplizierung zu entfernen, umschließen einer **Distinct** Funktion, um die ordnungsgemäße zurückgegebenen Daten. Weitere Informationen finden Sie unter: [DISTINCT-Funktion](functions/function-distinct.md)

## <a name="known-limitations"></a>Bekannte Einschränkungen

Diese Konfiguration ist verfügbar auf **Dropdown** -Steuerelemente, als auch **im Kombinationsfeld** und **Listenfeld** Steuerelemente, mit denen eine Auswahl zu einem Zeitpunkt. Sie können keine der **Abhängigkeiten** die Konfiguration dieser Steuerelemente, wenn sie die Mehrfachauswahl zulässig. Dieser Ansatz wird nicht empfohlen, für die Arbeit mit Optionssätze in Common Data Service.

Die **Abhängigkeiten** Konfiguration unterstützt keine statischen Daten oder Auflistungen. Um abhängige Dropdownlisten mit diesen Quellen konfigurieren zu können, müssen bearbeiten Sie den Ausdruck direkt in der Bearbeitungsleiste. Darüber hinaus PowerApps unterstützt nicht die Verwendung von zwei Choice Felder ohne eine entsprechende Tabelle von Daten in SharePoint, und es wird keine definieren **übereinstimmende Feld** mit dieser Benutzeroberfläche.