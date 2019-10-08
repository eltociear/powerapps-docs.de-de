---
title: Erstellen einer abhängigen Dropdown Liste in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen Sie in powerapps eine Dropdown Liste, die eine andere Dropdown Liste in einer Canvas-App filtert.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 57abde44541a2a1e40e3a8ffc55a89e37a8c6478
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985752"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>Erstellen von abhängigen Dropdown Listen in einer Canvas-App

Wenn Sie abhängige (oder kaskadierende) Dropdown Listen erstellen, wählen Benutzer eine Option in einer Liste aus, um die Optionen in einer anderen Liste zu filtern. Viele Organisationen erstellen abhängige Listen, damit Benutzer Formulare effizienter ausfüllen können. Beispielsweise können Benutzer ein Land oder eine Region zum Filtern einer Liste von Städten auswählen, oder Benutzer können eine Kategorie auswählen, um nur die Codes in dieser Kategorie anzuzeigen.

Es wird empfohlen, eine Datenquelle für die Werte in den Listen "Parent" und "Child" (z. b. Länder/Regionen und Städte) zu erstellen, die von der Datenquelle getrennt sind, die Benutzer mithilfe der APP aktualisieren. Wenn Sie diesen Ansatz verwenden, können Sie die gleichen über-und untergeordneten Daten in mehr als einer App verwenden, und Sie können diese Daten aktualisieren, ohne die APP oder die apps erneut zu veröffentlichen, die Sie verwenden. Sie können das gleiche Ergebnis mithilfe einer Sammlung oder statischer Daten erreichen, dies wird jedoch für Unternehmens Szenarios nicht empfohlen.

Für das in diesem Thema **Vorkomm** Ende Szenario senden Mitarbeiter über ein Formular Probleme an eine Vorfall Liste. Mitarbeiter geben nicht nur den Speicherort des Speicher Orts an, an dem der Incident aufgetreten ist, sondern auch die Abteilung innerhalb des Standorts. Nicht alle Standorte verfügen über dieselben Abteilungen. Daher stellt die Liste der **Standorte** sicher, dass Mitarbeiter keine Abteilung für einen Standort angeben können, der nicht über diese Abteilung verfügt.

In diesem Thema werden Microsoft SharePoint-Listen als Datenquellen verwendet, aber alle tabellarischen Datenquellen funktionieren auf dieselbe Weise.

## <a name="create-data-sources"></a>Erstellen von Datenquellen

In der Liste der Speicher **Orte** werden die Abteilungen an jedem Standort angezeigt.

| Location | Department |
|----------------|------------------|
| Eganville      | Bäckereien           |
| Eganville      | Schalter             |
| Eganville      | Produktion          |
| Renfrew        | Bäckereien           |
| Renfrew        | Schalter             |
| Renfrew        | Produktion          |
| Renfrew        | Apotheken         |
| Renfrew        | Miger           |
| "Pembroke"       | Bäckereien           |
| "Pembroke"       | Schalter             |
| "Pembroke"       | Produktion          |
| "Pembroke"       | Miger           |

In **einer Vorfall** Liste werden Kontaktinformationen und Informationen zu den einzelnen Vorfällen angezeigt. Erstellen Sie die Datums Spalte als **Datums** Spalte, erstellen Sie aber die anderen Spalten als **einzelne Zeile mit Text** Spalten, um die Konfiguration zu vereinfachen und [Delegierungs](./delegation-overview.md) Warnungen in Microsoft PowerApps zu vermeiden.

| Vorname | Nachname | Telefonnummer     | Location | Department | Beschreibung       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | (206) 555-1022 | Eganville      | Produktion    | Ich hatte ein Problem mit...   | 2/12/2019 |
| Moses     | Laflamme     | (425) 555-1044 | Renfrew        | Miger     | Es ist ein Problem aufgetreten... | 2/13/2019 |

Standardmäßig enthalten benutzerdefinierte SharePoint-Listen eine **Titel** Spalte, die Sie nicht umbenennen oder entfernen können, und Sie muss Daten enthalten, bevor Sie ein Element in der Liste speichern können. So konfigurieren Sie die Spalte so, dass keine Daten erforderlich sind:

1. Wählen Sie in der Nähe der oberen rechten Ecke das Zahnrad Symbol aus, und wählen Sie dann **Einstellungen auflisten**aus.
1. Wählen Sie auf der Seite **Einstellungen** in der Liste der Spalten **Titel** aus.
1. Wählen Sie unter **erfordert, dass diese Spalte Informationen enthält die**Option **Nein**aus.

Nachdem Sie diese Änderung vorgenommen haben, können Sie die Spalte **Titel** ignorieren, oder Sie können Sie aus der Standardansicht [Entfernen](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8) , wenn mindestens eine andere Spalte angezeigt wird.

## <a name="open-the-form"></a>Formular öffnen

1. Öffnen Sie die Liste **Vorfälle** , und wählen Sie dann **powerapps** > **Formulare anpassen**aus.

    > [!div class="mx-imgBorder"]
    > ![Öffnen Sie die Liste Vorfälle, und wählen Sie dann powerapps > Formular anpassen aus.](./media/dependent-drop-down-lists/open-form.png "Öffnen Sie die Liste Vorfälle, und wählen Sie dann powerapps > Formular anpassen aus.")

    Eine Browser Registerkarte wird mit dem Standardformular in PowerApps Studio geöffnet.

1. optionale Zeigen Sie im Bereich **Felder** auf das Feld **Titel** , wählen Sie die Schaltfläche mit den Auslassungs Punkten (...) aus, die angezeigt wird, und wählen Sie dann **Entfernen**aus.

    Wenn Sie den **Bereich Felder** geschlossen haben, können Sie ihn erneut öffnen, indem Sie in der linken Navigationsleiste **SharePointForm1** auswählen und dann im rechten Bereich auf der Registerkarte **Eigenschaften** die Option **Felder bearbeiten** auswählen.

1. optionale Wiederholen Sie den vorherigen Schritt, um das Feld **Anlagen** aus dem Formular zu entfernen.

    Das Formular wird nur mit den hinzugefügten Feldern angezeigt.

    > [!div class="mx-imgBorder"]
    > ![formular ohne Titel und Anhänge Felder @ no__t-1

## <a name="replace-the-controls"></a>Ersetzen der Steuerelemente

1. Wählen Sie im **Bereich Felder** den Pfeil neben **Speicherort**aus.

    Wenn Sie den **Bereich Felder** geschlossen haben, können Sie ihn erneut öffnen, indem Sie in der linken Navigationsleiste **SharePointForm1** auswählen und dann im rechten Bereich auf der Registerkarte **Eigenschaften** die Option **Felder bearbeiten** auswählen.

1. Öffnen Sie die Liste **Typ des Steuer** Elements, und wählen Sie dann **zulässige Werte**aus.

    > [!div class="mx-imgBorder"]
    > ![zulässige Werte @ no__t-1

    Der Eingabe Mechanismus ändert sich in ein **Dropdown** -Steuerelement.

1. Wiederholen Sie diese Schritte für die **Abteilungs** Karte.

## <a name="add-the-locations-list"></a>Liste der Speicherorte hinzufügen

1. Wählen Sie  > **Datenquellen** **anzeigen** > **Datenquelle hinzufügen**aus.

1. Wählen Sie eine SharePoint-Verbindung aus, oder erstellen Sie eine SharePoint-Verbindung, und geben Sie **dann die Website mit der Liste**

1. Aktivieren Sie das Kontrollkästchen für diese Liste, und wählen Sie dann **verbinden**aus.

    > [!div class="mx-imgBorder"]
    > ![data Pane @ no__t-1

    In der Liste der Verbindungen wird die Liste der **Vorfälle** angezeigt, auf denen das Formular basiert, und die Liste der Speicher **Orte** , in der Standorte und Abteilungen im Formular identifiziert werden.

    > [!div class="mx-imgBorder"]
    > ![sharepoint-Datenquellen @ no__t-1

## <a name="unlock-the-cards"></a>Entsperren der Karten

1. Wählen Sie die Karte **Speicherort** aus, wählen Sie im rechten Bereich die Registerkarte **erweitert** aus, und klicken Sie dann **auf entsperren, um die Eigenschaften zu ändern**.

1. Wiederholen Sie den vorherigen Schritt für die **Abteilungs** Karte.

## <a name="rename-the-controls"></a>Umbenennen der Steuerelemente

Wenn Sie die Steuerelemente umbenennen, können Sie Sie leichter identifizieren, und die Beispiele sind einfacher zu befolgen. Weitere bewährte Methoden finden Sie im [Whitepaper Codierungs Standards und Richtlinien](https://aka.ms/powerappscanvasguidelines).

1. Wählen Sie auf der Karte **Speicherort** das **Dropdown** -Steuerelement aus.

1. Benennen Sie das ausgewählte Steuerelement im oberen Bereich des rechten Bereichs um, indem Sie **ddlocation**eingeben oder einfügen.

    > [!div class="mx-imgBorder"]
    > ![umbenennen eines Steuer Elements @ no__t-1

1. Wiederholen Sie die vorherigen beiden Schritte auf der **Abteilungs** Karte, um das **Dropdown** -Steuerelement in **dddepartment**umzubenennen.

## <a name="configure-the-locations"></a>Konfigurieren der Standorte

1. Legen Sie die **Items** -Eigenschaft von **ddlocation** auf diese Formel fest:

    `Distinct(Locations; Location)`

1. optionale Wenn Sie die Alt-Taste gedrückt halten, öffnen Sie **ddlocation**, und vergewissern Sie sich, dass die drei Standorte in der Liste angezeigt werden.

## <a name="configure-the-departments"></a>Konfigurieren der Abteilungen

1. Wählen Sie **dddepartment**aus, und wählen Sie dann auf der Registerkarte **Eigenschaften** im rechten Bereich die Option abhängig von aus **.**

1. Stellen Sie sicher, dass **ddlocation** unter über **geordnetes Steuer**Element in der oberen Liste angezeigt wird und das **Ergebnis** in der unteren Liste angezeigt wird.

    > [!NOTE]
    > Wenn Sie nicht mit einer Zeichenfolge, sondern mit der tatsächlichen ID der Daten Zeile vergleichen möchten, wählen Sie **ID** anstelle von **Ergebnis**aus.

1. Wählen Sie unter **übereinstimmendes Feld** **Standorte** in der oberen Liste aus, wählen Sie in der unteren Liste **Speicherort** aus, und klicken Sie dann auf über **nehmen.**

    > [!div class="mx-imgBorder"]
    > ![hängt von Link @ no__t-1 ab.

    Die **Items** -Eigenschaft von **dddepartment** ist auf diese Formel festgelegt:

    `Filter(Locations; Location = ddLocation.Selected.Result)`

    Diese Formel filtert die Elemente in **dddepartment** basierend darauf, was der Benutzer in **ddlocation**auswählt. Durch eine solche Konfiguration wird sichergestellt, dass die "untergeordnete" Liste der Abteilungen die Daten für den "übergeordneten" Speicherort widerspiegelt, wie die Speicher **Orte** Liste in SharePoint angibt.

1. Öffnen Sie im rechten Bereich auf der Registerkarte **Eigenschaften** die Liste neben **Wert**, und wählen Sie dann **Abteilung**aus.

    In diesem Schritt wird der Anzeige Text auf die Optionen in der Spalte **Department** der Liste **Standorte** in SharePoint festgelegt.

    > [!div class="mx-imgBorder"]
    > Wert für ![department @ no__t-1

## <a name="test-the-form"></a>Testen des Formulars

Wenn Sie die Alt-Taste gedrückt halten, öffnen Sie die Liste der Standorte, wählen Sie eine aus, öffnen Sie die Liste der Abteilungen, und wählen Sie dann eine aus.

Die Listen der Standorte und Abteilungen widerspiegeln die Informationen in **der Liste der Speicherorte in** SharePoint.

> [!div class="mx-imgBorder"]
> ![öffnen Sie die Liste der Speicherorte, ändern Sie die Auswahl von "Renfrew" in "Pembroke", und öffnen Sie dann die Liste der Abteilungen @ no__t-1.

## <a name="save-and-open-the-form-optional"></a>Speichern und Öffnen des Formulars (optional)

1. Öffnen Sie das Menü **Datei** , und wählen Sie dann **Speichern** > **Veröffentlichen in SharePoint** > **Veröffentlichen in SharePoint**aus.

1. Klicken Sie in der oberen linken Ecke auf den Zurück-Pfeil, und klicken Sie dann auf **Zurück zu SharePoint**.

1. Klicken Sie auf der Befehlsleiste auf **Neu**, um Ihr angepasstes Formular zu öffnen.

## <a name="faq"></a>HÄUFIG GESTELLTE FRAGEN

**Es können keine Daten angezeigt werden: die Quellen sind leer oder weisen falsche Daten auf.**
Überprüfen Sie auf eine der folgenden Arten, ob das richtige Feld für das Steuerelement angezeigt wird:

- Wählen Sie eine Dropdown Liste aus, und wählen Sie dann im rechten Bereich auf der Registerkarte **Eigenschaften** die Eigenschaft **Wert** aus.

    > [!div class="mx-imgBorder"]
    > Dropdown ![-Änderung @ no__t-1

- Wählen Sie ein Kombinations Feld aus, und vergewissern Sie sich, dass der primäre Text das Feld ist, das Sie anzeigen möchten.

    > [!div class="mx-imgBorder"]
    > Kombinations Feld "![-Änderung" @ no__t-1

**Die Dropdown Liste "mein untergeordnetes Element" enthält doppelte Elemente.**
Dieses Symptom ist wahrscheinlich darauf zurückzuführen, dass eine **Such** Spalte in SharePoint oder eine **Auswahl** Funktion in powerapps verwendet wird. Um die Duplizierung zu entfernen, umschließen Sie eine **eindeutige** Funktion um die ordnungsgemäß zurückgegebenen Daten. Weitere Informationen finden Sie unter: Unter [schiedliche Funktion](functions/function-distinct.md).

## <a name="known-limitations"></a>Bekannte Einschränkungen

Diese Konfiguration ist für **Dropdown** -Steuerelemente sowie für Kombinations **Feld** -und **Listenfeld** -Steuerelemente verfügbar, die jeweils eine Auswahl ermöglichen. Wenn Sie mehrere Auswahlmöglichkeiten zulassen, können **Sie die von** der Konfiguration abhängige Konfiguration nicht verwenden. Diese Vorgehensweise wird nicht zum Arbeiten mit Options Sätzen in Common Data Service empfohlen.

Die **Abhängigkeit** von der Konfiguration unterstützt keine statischen Daten oder Auflistungen. Um abhängige Dropdown Listen mit diesen Quellen zu konfigurieren, bearbeiten Sie den Ausdruck direkt in der Bearbeitungs Leiste. Außerdem unterstützt powerapps nicht die Verwendung von zwei Auswahl Feldern in SharePoint ohne übereinstimmende Datentabelle, und Sie können kein **entsprechendes Feld** in dieser Benutzeroberfläche definieren.
