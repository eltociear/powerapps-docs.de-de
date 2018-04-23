---
title: Neuerungen bei PowerApps | Microsoft-Dokumentation
description: Updates für PowerApps nach Veröffentlichungsdatum
services: powerapps
suite: powerapps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/09/2018
ms.author: sharik
ms.openlocfilehash: 92438c37b870ace2ed5b2ec086cf6c5fb1548fdc
ms.sourcegitcommit: d7ed5144f96d1ecc17084c30ed0e2ba3c6b03c26
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="whats-new-in-powerapps"></a>Neuerungen bei PowerApps
Informationen über bekannte Einschränkungen finden Sie unter [Häufige Probleme und Lösungen](common-issues-and-resolutions.md).


> [!NOTE]
> Versionen werden über mehrere Tage eingeführt. Neue oder aktualisierte Funktionen werden möglicherweise nicht sofort angezeigt.

## <a name="announcing-the-business-applications-spring-18-release-notes"></a>Ankündigung der Versionshinweise für Geschäftsanwendungen im Frühling 2018

Entdecken Sie die neuesten Updates für unsere Geschäftsanwendungen sowie einen Host für neue Funktionen zum Erstellen Ihrer eigenen Anwendungen und Erweiterungen zusätzlich zu unserer Plattform. [Laden Sie die Versionshinweise für Frühjahr 2018 als PDF herunter](https://aka.ms/businessappsreleasenotes), die für Dynamics 365, PowerApps, Microsoft Flow und Power BI gelten.

**In Kürze:** Sobald die Features ausgeliefert werden, aktualisieren wir weiterhin die PDF-Datei zu den Versionshinweisen. Diese sind dann auch auf unserer Webseite verfügbar.

## <a name="apr-9"></a>9. April
* Schneiden Sie Steuerelemente, &mdash;einschließlich der Formate, Formeln und Eigenschaften&mdash;, für Apps in einem Webbrowser mit STRG+X aus, kopieren Sie sie (STRG+C), und fügen Sie sie ein (STRG+V).

## <a name="mar-21"></a>21. März
1. Erstellen Sie [modellgesteuerte Apps](../model-driven-apps/model-driven-app-overview.md), die mit Ihrem Datenmodell und der Form Ihrer wichtigsten Geschäftsdaten und -prozesse in Common Data Service für Apps beginnt. Auf dieser Grundlage werden Formulare, Ansichten und andere Komponenten erstellt. Modellgesteuerte Apps generieren automatisch eine leistungsstarke UI, die geräteübergreifend reagiert.
2. [Erstellen Sie eine Datenbank](../../administrator/create-database.md) für die aktuelle Version von Common Data Service für Apps in einer Umgebung.
3. CDS für Apps enthält nun Folgendes:
    - **Zusätzliche Datentypen** unterstützen komplexere Definitionen für Entitäten und sorgen für eine verbesserte Benutzerfreundlichkeit. (Gilt für Canvas-Apps und modellgesteuerte Apps)
    - [Erstellen und bearbeiten Sie Entitäten](../common-data-service/data-platform-create-entity.md) direkt über die PowerApps-Website in CDS für Apps. Die **Benutzerfreundlichkeit** wurde unter anderem durch die verbesserte Leistung, eine benutzerfreundlichere Benutzeroberfläche und hilfreiche Features wie die Inline-Erstellung von Optionen verbessert. (Gilt für Canvas-Apps und modellgesteuerte Apps)
    - **Erstellen Sie serverseitige Geschäftsregeln** für das Überprüfen der Daten, die in CDS für Apps eingegeben wurden. (Gilt für Canvas-Apps und modellgesteuerte Apps)
    - **Erstellen Sie berechnete Felder und Rollupfelder** direkt über die PowerApps-Website in den Entitäten von CDS für Apps. (Gilt für Canvas-Apps und modellgesteuerte Apps)  
    - Entwickler können das **Software Development Kit** (SDK) von Common Data Service für Apps verwenden, um codebasierte Anpassungen für Common Data Service für Apps zu erstellen.
    - Erfahrene Benutzer können über eine neue **OData-Web-API** auf die in CDS für Apps gespeicherten Daten zugreifen.
    - [Importieren Sie Daten](../common-data-service/data-platform-cds-newentity-pq.md) in CDS für Apps mithilfe von **Power Query**. Verwenden Sie Power Query im Web, um Daten aus mehreren Quellen direkt in CDS für Apps zu importieren.

## <a name="mar-5"></a>5. März
1. [Anlagen](controls/control-attachments.md) in SharePoint-Listen hinzufügen (und löschen).
2. Externe [PDF](controls/control-pdf-viewer.md)-Dateien in einem Webbrowser öffnen. (Experimentelles Feature)

## <a name="feb-12"></a>12. Februar
* Der Lautstärkeregler für die Wiedergabe eingebetteter [Video-](controls/control-audio-video.md) und [Audiodaten](controls/control-audio-video.md) ist jetzt eingebettet. Zum Stummschalten der Wiedergabe müssen Benutzer jetzt den Lautstärkeregler zum Verringern der Lautstärke verwenden, statt auf eine Schaltfläche zu klicken oder zu tippen.

## <a name="feb-7"></a>7. Februar
1. Die Eigenschaften für Zoom, Helligkeit und Kontrast wurden aus den Steuerelementen [Kamera](controls/control-camera.md) und [Barcodescanner](controls/control-barcodescanner.md) entfernt.
2. Das Problem, dass der Platz für die Benutzereingabe in den Steuerelementen [Texteingabe](controls/control-text-input.md) durch die Schaltfläche „Löschen“ beschränkt wurde, wurde korrigiert. Aufgrund dieser Korrektur wird die Eigenschaft [Löschen](controls/control-text-input.md#additional-properties) eines Texteingabesteuerelements nur in den Webbrowsern Microsoft Edge (neueste Version) und Internet Explorer 11 unterstützt.
3. Es wurden Verbesserungen an der Barrierefreiheit von [Multimedia](add-images-pictures-audio-video.md)-Steuerelementen vorgenommen.

## <a name="jan-31"></a>31. Januar
1. Hinzufügen von Untertiteln für Hörgeschädigte zu [Video](controls/control-audio-video.md)-Steuerelementen.
2. Verbesserte Fehlerbehandlung in [PDF-Viewer](controls/control-pdf-viewer.md) Steuerelementen.

## <a name="jan-18"></a>18. Januar
1. PowerApps für iOS und Android unterstützt jetzt die Integration mit Microsoft Authenticator.
2. In PowerApps Studio ersetzt ein [Kombinationsfeld](controls/control-combo-box.md) das [SharePoint-Nachschlagesteuerelement](sharepoint-lookup-fields.md) in Formularen, und standardmäßig ist eine neue [Datenkarten](working-with-cards.md)-Vorlage für Einzelauswahlsuchfelder ausgewählt ist.
3. In einem [Kombinationsfeld](controls/control-combo-box.md) werden alle Einträge im erweiterten Lesemodus in einer langen Liste angezeigt.
4. Legen Sie die Größe des Datensatzgrenzwerts für den lokalen Speicher auf bis zu 2000 Datensätzen in [nicht delegierbaren Abfragen](delegation-overview.md#non-delegable-limits) fest. (Experimentelles Feature)

## <a name="jan-5"></a>5. Januar
* Verarbeiten Sie Daten direkt aus einem Power BI-Bericht oder -Dashboard, indem Sie ein [benutzerdefiniertes PowerApps-Visual (Vorschauversion)](https://powerapps.microsoft.com/blog/powerbi-powerapps-visual/) integrieren, mit dem Kontextdaten aus dem Power BI-Bericht abgerufen werden.

## <a name="dec-8"></a>8. Dezember
1. [Bedingungsvorlagen](working-with-rules.md) für Regeln leiten allgemeine Eigenschaften eines Steuerelements (wie **Text** oder **Wert**) ab.
2. Die Anzeige des [Bestätigungsdialogfeld **Aktionen werden definiert** ](working-with-rules.md)beim Definieren von Regelaktionen kann deaktiviert werden.

## <a name="nov-13"></a>13. November
1. Wählen Sie mehrere Werte für das gleiche Feld in SharePoint-Listen aus.
2. In SharePoint-Listen können [Anlagen angezeigt und heruntergeladen](controls/control-attachments.md) werden.
3. PowerApps unterstützt das [Anpassen von SharePoint-Listenformularen](customize-list-form.md).

## <a name="nov-10"></a>10. November
* Sie können in einer App [Regeln umbenennen](working-with-rules.md) und anzeigen, wenn sich ein ausgewähltes Steuerelement in der Regelbedingung befindet.
