---
title: Neuerungen bei PowerApps | Microsoft-Dokumentation
description: "Updates für PowerApps nach Veröffentlichungsdatum"
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/13/2018
ms.author: sharik
ms.openlocfilehash: b8d06bb8ffbe1446f4c918e6cf1c6657c1890e65
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="whats-new-in-powerapps"></a>Neuerungen bei PowerApps
Informationen über bekannte Einschränkungen finden Sie unter [Häufige Probleme und Lösungen](common-issues-and-resolutions.md).

> [!NOTE]
> Versionen werden über mehrere Tage eingeführt. Neue oder aktualisierte Funktionen werden möglicherweise nicht sofort angezeigt.

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

## <a name="oct-30"></a>30. Oktober
1. [Anzeigen aller Regeln](working-with-rules.md) in einer App, nicht nur der Regeln für das ausgewählte Steuerelement.
2. Symbole hinzugefügt, die von App-Entwicklern am häufigsten gewünscht wurden.
3. Verbesserte Leistung der Apps auf Android- und iOS-Geräten.

## <a name="sept-20"></a>20. September
1. Nach dem ersten [Speichern einer App](save-publish-app.md) werden zusätzliche Änderungen standardmäßig automatisch alle zwei Minuten gespeichert.
2. Einfaches [Erstellen von Regeln](working-with-rules.md) für bedingte Formatierung, ohne Ausdrücke zu schreiben – legen Sie einfach die Bedingung fest, und entwerfen Sie dann direkt im PowerApps-Zeichenbereich die Ergebnisse.
3. Einfacheres Konfigurieren von Formularen, Katalogen und Datentabellen mit einem Datenbereich, der die gesamte Höhe des Bildschirms einnimmt und beim Hinzufügen eines Steuerelements eingeblendet wird.
4. Sie erhalten kontextbezogene Hinweise, die Sie beim Erstellen einer App unterstützen, egal ob Sie mit einer leeren App beginnen oder eine Vorlage, eine Datenquelle oder SharePoint verwenden.

## <a name="sept-6"></a>6. September
1. Bei von Ihnen erstellten Apps können Sie über Power BI in einem eingebetteten Dashboard die [Nutzung nachverfolgen](app-analytics.md).
2. Spalten Sie eine Textzeichenfolge mit der **[Split](functions/function-split.md)**-Funktion in einzelne Teile auf, indem Sie ein Trennzeichen angeben.
