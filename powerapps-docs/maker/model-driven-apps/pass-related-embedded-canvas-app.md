---
title: Eine Liste von aktuellen Datensätzen als Datenkontext mit einer eingebetteten Canvas-App übergeben | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- PowerApps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 44112fee976b12f12b43ca2bf70157266be4d8ce
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759422"
---
# <a name="pass-a-list-of-related-records-as-data-context-to-an-embedded-canvas-app"></a>Eine Liste von aktuellen Datensätzen als Datenkontext an eine eingebettete Canvas-App übergeben
> [!IMPORTANT]
> Canvas-Apps, die in modellgesteuerte Formulare eingebettet sind, sind jetzt nicht mehr in der Vorschau sondern allgemein verfügbar. Die unten aufgeführten Schritte sind veraltet und gelten nur für die öffentliche Vorschauversion von Canvas-Apps, die in modellgesteuerten Formularen eingebettet sind.
> Die aktualisierte Liste von Schritten für die aktuelle Version finden Sie unter: [Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md)

In diesem Thema wird erläutert, wie Sie eine eingebettete Canvas-App hinzufügen und eine Liste von Datensätzen, die in Bezug zum aktuellen (Hauptformular-)Datensatz stehen, als Datenkontext an die eingebettete Canvas-App übergeben.

Stellen Sie sich vor, Sie möchten eine eingebettete Canvas-App in ein Firmenhauptformular einfügen und eine Liste von Datensätzen, die in Bezug zum aktuellen Firmendatensatz stehen, an die eingebettete Canvas-App übergeben. Gehen Sie dazu wie folgt vor:

1.  Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und öffnen Sie im Formular-Editor ein Hauptformular einer Entität, wie beispielsweise der Firmenentität.
2.  Wählen Sie im Formular den Abschnitt aus, in dem die eingebettete Canvas-App angezeigt werden soll.
3.  Innerhalb des ausgewählten Abschnitts klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Steuerelement** auf **Unterraster**.
4.  Im Dialogfeld **Eigenschaften festlegen** wählen Sie die Registerkarte **Anzeigen** aus und geben dann im Eingabefeld **Name** einen Namen für das Rastersteuerelement ein.
5.  Wählen Sie im Abschnitt **Datenquelle** eine **Entität** und **Standardansicht**, die der Liste der Datensätze entspricht, die Sie als Datenkontext an die eingebettete Canvas-App übergeben möchten.
6. Wählen Sie die Registerkarte **Steuerelemente** und dann **Steuerelement hinzufügen...**.
7. Wählen Sie im Dialogfeld **Steuerelement hinzufügen** in der Liste der verfügbarer Steuerelemente **Canvas-App** und dann **Hinzufügen** aus.
8. Wählen Sie im Dialogfeld **Eigenschaften festlegen** in der Liste der Steuerelemente die Option **Canvas-App** und wählen Sie dann die Option **Web** aus.
9. Sehen Sie sich im Abschnitt unter der Steuerelementliste die Liste der entsprechenden Eigenschaften für das Canvas-App-Steuerelement an, und beachten Sie Folgendes:
     - Die Eigenschaft **Entitätsname** gibt die Entität an, die die Daten an Ihre eingebettete Canvas-App liefert. Es wird auf die vorher ausgewählte Entität festgelegt.
         -  Obwohl diese Eigenschaft veränderbar erscheint, hat die Änderung keinen Einfluss auf die eingebettete Canvas-App hat. Sie soll lediglich als Referenz für Siedienen.
     -  Die Eigenschaft **Ansichtsname** gibt die Ansicht der Entität an, die verwendet wird, um die Daten zu filtern, die Ihrer eingebetteten Canvas-App bereitgestellt werden. Es wird auf die vorher ausgewählte **Standardansicht** festgelegt.
         -  Die Daten, die an die eingebettete Canvas-App während der Laufzeit gesendet werden, werden in dieser Ansicht erkannt. Verwenden Sie in Ihrer Canvas-App nur Felder, die in der Ansicht enthalten sind, oder fügen Sie sie bei Bedarf der Ansicht hinzu. Alle Felder, die nicht in der Ansicht enthalten sind, zeigen zur Laufzeit leere Werte an.
         -  Die Filterkriterien für eine Ansicht werden zum Zeitpunkt der Erstellung nicht verwendet. Daher werden die Daten, die Sie beim Erstellen von eingebetteten Canvas-Anwendungen sehen, nicht gefiltert, es ist lediglich eine Liste der wichtigsten Datensätze, auf die Sie Zugriff haben. Zur Laufzeit werden die Filterkriterien für die Ansicht erwartungsgemäß angewendet und den Benutzern werden nur relevante Daten angezeigt.
     -  Die Eigenschaft **App ID** gibt die ID der eingebetteten Canvas-App an. Sie ist bei Erstellung der Canvas-App automatisch generiert und eingetragen.
         -  Beachten Sie, dass jede Änderung des Wertes App ID die Verknüpfung von dem modellgestützten Formular zur eingebetteten Canvas-App unterbricht.
10. Zum Erstellen oder Bearbeiten Ihrer Canvas-App wählen Sie die Schaltfläche **Anpassen** aus. Dadurch wird PowerApps Studio in einer neuen Browserregisterkarte geöffnet.
     > [!IMPORTANT]
     > Wenn das Öffnen von PowerApps Studio aufgrund eines Popupblockers des Webbrowsers blockiert ist, müssen Sie die Website make.powerapps.com aktivieren oder den Popupblocker vorübergehend deaktivieren und dann erneut **Anpassen** auswählen. 
11. Beachten Sie in PowerApps Studio, dass sich im linken Bereich ein **ModelDrivenFormIntegration**-Steuerelement befindet. Dieses Steuerelement ist dafür verantwortlich, Kontextdaten aus dem Hostmodell-basierten Formular in die eingebettete Canvas-App zu bringen. 
12. Wählen Sie das Steuerelement **Gallery1** und stellen Sie fest, dass die Eigenschaft **Elemente** auf **ModelDrivenFormIntegration.Data** gesetzt ist.
13. Wählen Sie im Eigenschaftenbereich rechts neben **Felder** **Bearbeiten** aus.
14. Ändern Sie im Datenbereich das dem **Titel1**-Steuerelement zugeordnete Feld auf **Vollständiger Name** oder ein anderes Feld, das Daten enthält.
15. Beachten Sie, dass die Galerie die Daten anzeigt, die über das **ModelDrivenFormIntegration**-Steuerelement aus dem Hostmodell-basierten Formular an sie übergeben werden. Schließen Sie den Datenbereich.
16. Wählen Sie die Registerkarte **Datei**, und wählen Sie **App-Einstellungen** aus.
17. Setzen Sie auf der Registerkarte **Erweiterte Einstellungen** im Abschnitt **Experimentfunktionen** **App eingebettete Nutzerumgebung aktivieren** auf **An**.
18. Wählen Sie **Speichern** aus. 
19. Wählen Sie die Registerkarte **Die Cloud**, geben Sie der App einen eindeutigen Namen, und wählen Sie dann **Speichern**, unten rechts. Beachten Sie Folgendes: 
    -  Wenn Sie eine App zum ersten mal speichern, wird die App automatisch veröffentlicht. 
      -  Bei späterem Speichern, müssen Sie **Veröffentlichen** und dann **Diese Version veröffentlichen** auswählen, um Ihre Änderungen zur Verfügung stellen.
20. Wählen Sie **Zurück** und dann die Browser-Registerkarte, auf der der Formular-Editor geöffnet ist. 
21. Beachten Sie, dass die Eigenschaft **App ID** des **Canvas-App**-Steuerelements nun einen automatisch ausgefüllten Wert hat. Beachten Sie Folgendes: 
     -  Der Formular-Editor verfügt über eine direkte Verbindung zu PowerApps Studio, das in einem früheren Schritt in einer anderen Browserregisterkarte geöffnet wurde.
     -  Der Formular-Editor wartete darauf, dass die App ID an ihn gesendet wurde.
     -  Die App ID wurde gesendet, als die App gespeichert wurde.
22. Wählen Sie im Dialog **Eigenschaften festlegen** die Registerkarte **Anzeige**, löschen Sie **Beschriftung im Formular anzeigen** und wählen Sie dann **OK**.
     - Wenn Sie bereits eine Canvas-App in dieses Formular eingebettet haben, wird eine Meldung angezeigt, "Nur eine Canvas-App kann in einem Formular aktiviert werden". Wenn Sie die neue Canvas-App hinzufügen, müssen Sie zuerst [die aktuelle eingebettete Canvas-App deaktivieren](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app). Anschließend [aktivieren Sie die neue eingebettete Canvas-App](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app).
23. Wählen Sie auf der Registerkarte **Start** **Speichern** und dann **Veröffentlichen** aus.

Nachdem Sie eine eingebettete Canvas-App zu Ihrem modellgestützten Formular hinzugefügt haben, teilen Sie Ihre eingebettete Canvas-App mit anderen Benutzern. Weitere Informationen: [Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md).

Wenn Benutzer eine modellgestützte App (nur Einheitliche Oberfläche) öffnen, die das von Ihnen geänderte Formular enthält, sehen sie die eingebettete Canvas-App auf dem Formular. Wenn Sie den Datensatz ändern, der auf dem Hauptformular angezeigt wird, ändert sich der Datenkontext, der an das Formular übergeben wird, und die eingebettete App wird aktualisiert, um die relevanten Daten anzuzeigen.

In diesem Thema erfahren Sie, wie Sie mit der Einbettung einer Canvas-App in einem modellgestützen Formular beginnen. Sie können die eingebettete Canvas-App weiter anpassen, um Daten aus einer Vielzahl von Datenquellen zu verbinden und einzubringen. Verwenden Sie die Funktionen Filter, Suche und LookUp und den vom Hostmodell-basierten Formular übergebenen Kontext, um bestimmte Datensätze in diesen Datenquellen zu filtern oder zu finden. Verwenden Sie den WYSIWYG-Canvas-App-Editor, um einfach die Benutzeroberfläche zu entwerfen, die Ihren Anforderungen entspricht.

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md) <br />
[Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-edit-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements](embedded-canvas-app-properties-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md) <br />
[Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps](embedded-canvas-app-guidelines.md) <br />
[Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion als die neueste Version erstellt wurden](embedded-canvas-app-migrate-from-preview.md) <br />
