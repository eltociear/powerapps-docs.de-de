---
title: Häufig gestellte Fragen zu Aktivitäten und der Zeitachsenanzeige | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e79412c79a3b2a6d5c7f7f51c8cfcad8e4f5cc78
ms.sourcegitcommit: 826bde1eab3dd32d7bf9fa3f43ea069694845597
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290954"
---
# <a name="frequently-asked-questions-about-activities-and-the-timeline-wall"></a>Häufig gestellte Fragen zu Aktivitäten und der Zeitachsenanzeige  

## <a name="is-a-title-required-when-adding-a-new-note"></a>Sind Titel beim Hinzufügen eines neuen Hinweises erforderlich?

Nein. Beim Hinzufügen eines Hinweises zu einer Aktivität ist das Titelfeld zwar als Pflichtfeld markiert, aber es ist nicht erforderlich. Dies ist ein bekanntes Problem des alten Webclients.

## <a name="for-an-appointment-when-i-choose-the-option-to-save-as-draft-it-doesnt-show-that-the-appointment-has-been-saved-as-a-draft"></a>Wenn ich Termine mit der Option *Als Entwurf speichern* speichere, wird nicht angegeben, dass sie als Entwurf gespeichert wurden.

Wenn Sie einen Termin im alten Webclient als Entwurf speichern, wird im Titel nicht **[DRAFT]** ([ENTWURF]) angezeigt, um anzugeben, dass der Termin als Entwurf gespeichert wurde.

## <a name="can-i-add-activities-to-read-only-records"></a>Können Aktivitäten zu schreibgeschützten Datensätzen hinzugefügt werden?

Ja. Sie können Aktivitäten zu schreibgeschützten Entitäten wie Hinweisen, Telefonanrufen, Aufgaben und mehr hinzufügen. 

## <a name="are-html-tags-supported-in-notes"></a>Werden HTML-Tags in **Hinweisen** unterstützt?

Nein. Beim Erstellen einer Hinweisaktivität werden HTML-Tags unabhängig vom Datensatz oder der Entität nicht unterstützt. Wenn Sie beispielsweise <TAG> </TAG> zu einem Hinweisfeld hinzufügen, wird dies als <TAG_XXX="XX"> </TAG> dargestellt.

## <a name="how-can-i-improve-performance-on-timeline-wall"></a>Wie kann ich die Leistung der Zeitachsenanzeige verbessern?

Sie können die Leistung der Zeitachsenanzeige verbessern, indem Sie optimieren, wie viele Daten von einzelnen Entitätsdatensätzen zurückgegeben werden. 

1.  Konfigurieren Sie Entitätsformulare so, dass nur verwendete Aktivitäten angezeigt werden.  Diese Konfiguration können Sie auf der Formularebene anwenden, damit nur nützliche Aktivitäten angezeigt werden.  Wenn Sie beispielsweise keine Aufgaben für Fälle verwenden, können Sie die Zeitachsenanzeige für das Fallformular so konfigurieren, dass keine Aufgaben angezeigt werden.
2.  Reduzieren Sie die Anzahl der Standarddatensätze, die auf der Zeitachse angezeigt werden.  Gemäß der Standardkonfiguration werden 10 Datensätze zurückgegeben. Höhere Werte können zu Leistungsproblemen führen.  Es wird empfohlen, den Standardwert nicht zu überschreiten. 

## <a name="activity-wall-is-not-supported-in-print-preview"></a>Die Zeitachsenanzeige wird in der Seitenansicht nicht unterstützt.

Wenn Sie die **Seitenansicht** in Dynamics 365 öffnen, wird die **Zeitachsenanzeige** nicht in der Liste angezeigt. Zwar werden **Hinweise** angezeigt, Aufgaben und E-Mails jedoch nicht.





