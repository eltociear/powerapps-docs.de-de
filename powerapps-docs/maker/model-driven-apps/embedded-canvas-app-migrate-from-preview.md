---
title: Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion erstellt wurden | MicrosoftDocs
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bc836669289ae6349d8e22eabe22f53c4dd6fd14
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884779"
---
# <a name="migrate-embedded-canvas-apps-on-model-driven-forms-created-using-the-public-preview-release"></a>Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion erstellt wurden
> [!IMPORTANT]
> Mit der neuesten Version sind eingebettete Canvas-Apps in modellgesteuerten Formularen allgemein verfügbar. Alle eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion erstellt wurden, sollten auf die neuen eingebetteten Canvas-Apps migriert werden, die mithilfe der neuesten Version erstellt wurden.
> Die Unterstützung von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion erstellt wurden, wird bald eingestellt. 

Um eine eingebettete Canvas-App in einem modellgesteuerten Formular zu migrieren, die mithilfe der öffentlichen Vorschauversion in der neuesten Version erstellt wurde, müssen Ersteller zuerst mithilfe der neuesten Version eine neue eingebettete Canvas-Apps erstellen. Ersteller können die Steuerelemente dann von der vorhandenen eingebetteten Canvas-App in die neue kopieren, erforderliche Datenquellen hinzufügen und fehlerhafte Verweise aktualisieren. Detaillierte Schritte werden unten aufgelistet.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
2. Öffnen Sie die eingebettete Canvas-App, die mithilfe der öffentlichen Vorschauversion für die Bearbeitung in Power Apps Studio erstellt wurde. Die Schritte zum Bearbeiten einer Canvas-App finden Sie unter: [Bearbeiten einer Canvas-App](../canvas-apps/edit-app.md).
3. Führen Sie in einer neuen Browserregisterkarte die Schritte aus, [um eine neue eingebettete Canvas-App in einem modellgestützten Formular hinzuzufügen](embedded-canvas-app-add-classic-designer.md).
4. Kopieren Sie die Steuerelemente von der eingebetteten Canvas-App, die mithilfe der öffentlichen Vorschauversion als neue eingebettete Canvas-App erstellt wurde, von den jeweiligen Bildschirmen mithilfe der unten genannten Schritte.
    1. Wählen Sie die Browserregisterkarte von Schritt 2 mit der eingebetteten Canvas-App, die mithilfe der öffentlichen Vorschauversion erstellt wurde, und öffnen Sie sie in Power Apps Studio.
    2. Wählen Sie einen Bildschirm aus, von dem die Steuerelemente kopiert werden sollen.
    3. Verwenden Sie **STRG + A**, um alle Steuerelemente auf dem Bildschirm auszuwählen.
    4. Drücken Sie **STRG + C**, um alle ausgewählten Steuerelemente zu kopieren.
    5. Wählen Sie die Browserregisterkarte von Schritt 3 mit der neuen eingebetteten Canvas-App, die mithilfe der neuesten Version erstellt wurde.
    6. Wählen Sie einen Bildschirm aus oder fügen Sie einen neuen hinzu.
    7. Verwenden Sie **STRG + V**, um die Steuerelemente auf dem ausgewählten Bildschirm einzufügen.
    8. Wiederholen Sie die Schritte, um jeden Bildschirm zu kopieren.
5. Wenn Sie mit dem Kopieren aller Bildschirme fertig sind, wählen Sie die Browserregisterkarte von Schritt 3 mit der neuen eingebetteten Canvas-App aus, die mithilfe der neuesten Version erstellt wurde.
6. Aktualisieren Sie alle Orte, von denen der Datensatz des modellgesteuerten Hostformulars aufgerufen wird. Ersetzen Sie **First(ModelDrivenFormIntegration.Data)** durch **ModelDrivenFormIntegration.Item**.
7. Fügen Sie alle fehlenden Datenquellen in die neue eingebettete Canvas-App ein.
8. Aktualisieren Sie alle fehlerhaften Verweise in der neuen eingebetteten Canvas-App. 
9. Wenn Sie fertig mit Ihren Änderungen sind, wählen Sie die Registerkarte **Datei** und dann **Speichern** aus.
10. Um Ihre Änderungen für Endbenutzer verfügbar zu machen, wählen Sie **Veröffentlichen** und dann **Diese Version veröffentlichen**.

## <a name="migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record"></a>Die Migration von eingebetteten Canvas-Apps in modellgesteuerten Formularen, bei denen eine Liste von Datensätzen verwendet wird, die mit dem aktuellen Datensatz (Hauptformular) verknüpft sind.

In der Vorschauversion mussten Ersteller, die zuvor entscheiden mussten, ob sie den aktuellen Datensatz (Hauptformular) als Datenkontext oder als eine Liste von Datensätzen weitergeben möchten, die mit dem aktuellen Datensatz (Hauptformular) verknüpft sind, um eine Canvas-App in einem modellgestützten Formular einzubetten. Sie musste dann das Canvas-App-Steuerelement entweder dem Feld- oder Unterrastersteuerelement hinzufügen.

Mit der neuesten Version wird das Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular nur im Hinblick auf das Feld vereinfacht und optimiert. Ersteller können die Liste der verknüpften Datensätze direkt in der Canvas-App mithilfe des Common Data Service-Connectors weiterhin einfach aufrufen. 

Um eine eingebettete Canvas-App in ein modellgesteuertes Formular zu migrieren, bei dem eine Liste von Datensätzen verwendet wird, die mit dem aktuellen Datensatz (Hauptformular) verknüpft sind, folgen Sie bitten den unten aufgeführten Schritten.

1. Führen Sie die Schritte im obigen Abschnitt aus, um eingebettete Canvas-Apps in ein modellgesteuertes Formular zu migrieren, die mithilfe der öffentlichen Vorschauversion als neueste Version erstellt wurden.
2. Mithilfe des Common Data Service-Connectors fügen Sie eine Datenquelle für die verknüpfte Entität der App hinzu. Um zu erfahren, wie eine Datenquelle in einer Canvas-App hinzugefügt wird, sehen Sie sich [Hinzufügen einer Datenverbindung zu einer Canvas-App in Power Apps](../canvas-apps/add-data-connection.md) an.
3. Wenn Sie die Datenquelle der verknüpften Entität für ein Steuerelement wie [Galerie](../canvas-apps/controls/control-gallery.md) oder [Datentabelle](../canvas-apps/controls/control-data-table.md) verwenden, nutzen Sie die Funktion **[Filter](../canvas-apps/functions/function-filter-lookup.md)**, um die Datensätze nach denen zu filtern, die mit dem aktuellen Datensatz (Hauptformular) verknüpft sind. Der aktuelle Datensatz (Hauptformular) ist über **ModelDrivenFormIntegration.Item** verfügbar.
    > [!NOTE]
    > Die eingebettete Canvas-App hat vom modellgesteuerten Hostformular über ModelDrivenFormIntegration.Item vollen Zugriff auf den Datensatz. Wenn Sie beispielsweise den Wert eines Felds mit dem Namen **AccountNumber** und den Anzeigenamen **Firmennummer** abrufen möchten, können Sie **ModelDrivenFormIntegration.Item.accountnumber** oder **ModelDrivenFormIntegration.Item.'Account Number'** verwenden.
4. Dank der neuesten Updates bietet Common Data Service jetzt auch Unterstützung zur Verwendung der Entitätsansichten als Filter. Weitere Informationen finden Sie in diesem Blogbeitrag: [Verbesserte Datenquellenauswahl und Common Data Service-Ansichten](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/). 

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular](embedded-canvas-app-add-classic-designer.md) <br />
[Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-edit-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements](embedded-canvas-app-properties-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md) <br />
[Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps](embedded-canvas-app-guidelines.md) <br />
