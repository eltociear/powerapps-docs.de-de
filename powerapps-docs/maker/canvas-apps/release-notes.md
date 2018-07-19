---
title: Neuheiten | Microsoft-Dokumentation
description: Updates für PowerApps nach Veröffentlichungsdatum
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2018
ms.author: anneta
ms.openlocfilehash: e68614f2624a0d60e09563f92bf027fdf03d77b5
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39023894"
---
# <a name="whats-new-in-powerapps"></a>Neuerungen bei PowerApps
> [!IMPORTANT]
> **Ankündigung der Anmerkungen zu dieser Version**<br>
> Sind Sie an bevorstehenden und kürzlich veröffentlichten PowerApps-Funktionen interessiert?<br>
[Lesen Sie die Anmerkungen zu dieser Version](https://docs.microsoft.com/en-us/business-applications-release-notes/april18/powerapps/overview). Sämtliche Informationen, die Sie zur Planung nutzen können, wurden detailliert zusammengefasst.

Informationen über bekannte Einschränkungen finden Sie unter [Häufige Probleme und Lösungen](common-issues-and-resolutions.md).

> [!NOTE]
> Versionen werden über mehrere Tage eingeführt. Neue oder aktualisierte Funktionen werden möglicherweise nicht sofort angezeigt.

## <a name="may-30"></a>30. Mai
1. [Rich-Text-Editor-Steuerelement](controls/control-richtexteditor.md) (experimentell): Ermöglicht es Benutzern, Text innerhalb eines WYSIWYG-Bearbeitungsbereichs zu formatieren. 

## <a name="may-21"></a>21. Mai
1. Ermöglichen Sie App-Benutzern, Daten aus Excel- oder CSV-Dateien zu importieren und zu exportieren, die lokal gespeichert sind, indem Sie die Features **Daten aus Excel abrufen** und **Daten exportieren** verwenden, die jetzt für upgegradete Umgebungen von Common Data Service (CDS) für Apps verfügbar sind. 
1. Ermöglichen Sie App-Benutzern, [Entitäten in Excel zu öffnen](../common-data-service/data-platform-excel-addin.md), um Daten, die in CDS für Apps gespeichert sind, über das Excel-Add-In für PowerApps zu erstellen, zu aktualisieren und zu löschen. 
1. [Erstellen und veröffentlichen Sie Power BI-Berichte](../common-data-service/data-platform-powerbi-connector.md), indem Sie Power BI Desktop mit der Verbindung zu CDS für Apps verwenden. 

## <a name="april-23"></a>23. April
* Laden Sie [Anlagen](controls/control-attachments.md) im Internet Explorer in benutzerdefinierten Listenformularen in SharePoint herunter.

## <a name="april-9"></a>9. April
* Schneiden Sie Steuerelemente, &mdash;einschließlich der Formate, Formeln und Eigenschaften&mdash;, für Apps in einem Webbrowser mit STRG+X aus, kopieren Sie sie (STRG+C), und fügen Sie sie ein (STRG+V).

## <a name="march-21"></a>21. März
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

## <a name="march-5"></a>5. März
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
