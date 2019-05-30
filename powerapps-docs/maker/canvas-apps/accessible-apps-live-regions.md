---
title: Ankündigen zu können dynamische Änderungen mit live-Regionen in canvas-apps | Microsoft-Dokumentation
description: Wie Sie dynamische Bereiche zu verwenden, um der Sprachausgabe über dynamische Änderungen in der Canvas-apps zu benachrichtigen.
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a886b1c585f4fc07efc29bc1166ce4aca5586b5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61549948"
---
# <a name="announce-dynamic-changes-with-live-regions-for-canvas-apps"></a>Ankündigen von dynamischen Änderungen mit live-Regionen für Canvas-apps

Dynamische Änderungen stellen Herausforderungen bis hin zu den Sehvermögen. Benutzern, die eine app über eine Sprachausgabe Zugriff sind sich der Fokus auf einen Teil der app. Wenn eine Änderung an anderer Stelle auftritt, nicht die Benutzer darauf aufmerksam machen.

Sie können dieses Problem beheben, durch das Hinzufügen von live-Regionen, die Sprachausgabe nachverfolgen. Wenn der Inhalt in einen dynamischen Bereichs geändert wird, wird eine Bildschirmsprachausgabe, die diese Änderung ankündigen.

Der zugrunde liegende Mechanismus für dynamische Bereiche sind [Aria-live-Regionen](https://www.w3.org/TR/wai-aria-1.1/#dfn-live-region), sodass dieselben Richtlinien werden angewendet.

## <a name="example-uses-of-live-regions"></a>Für die Verwendung von live-Regionen

Sie können dynamische Bereiche verwenden, um Benutzer zu benachrichtigen, wenn Ereignisse, wie diese auftreten:

* Ein Überprüfungsfehler angezeigt, in einem Formular.
* Eine Aktion, die durch eine Schaltfläche ausgelöst wird, ist erfolgreich. Beispielsweise ein Benutzer eine Schaltfläche zum Hinzufügen eines Elements zu einer Sammlung auswählen, und ein dynamischen Bereichs könnten die Meldung, die "Wurde hinzugefügt" wird angezeigt.
* Der Benutzer ausgewählt, eine andere Registerkarte.
* Ein Zeitgeber im Hintergrund aktualisiert ein Newsfeed.

## <a name="create-and-configure-a-live-region"></a>Erstellen und Konfigurieren eines dynamischen Bereichs

Sie können konfigurieren, nur eine **[Bezeichnung](controls/control-text-box.md)** Steuerelement als eines dynamischen Bereichs. Die **Live** Eigenschaft bestimmt, welcher Typ des dynamischen Bereichs.

* **Off**: Keines dynamischen Bereichs. Die Sprachausgabe keine Änderungen.
* **Polite**: Die Sprachausgabe Änderungen nach Abschluss sprechen. Verwenden Sie diesen Wert für nicht kritische Benachrichtigungen, die keine unmittelbare Aufmerksamkeit erfordern.
* **Assertive**: Sprachausgaben unterbrechen selbst, um die Änderungen sofort bekanntgeben zu können. Verwenden Sie diese für wichtige Benachrichtigungen, die sofortige Aufmerksamkeit erfordern.

Wenn das Textinhalt eines dynamischen Bereichs geändert wird, wird den gesamte Textinhalt, nicht nur der geänderte Teil die Sprachausgabe. Wenn der Wert des der **[Text](controls/properties-core.md)** -Eigenschaftensatz auf eine leere Zeichenfolge **""** , der Sprachausgabe nicht vorgelesen nichts.

Um eine Nachricht wiederholen, löschen Sie Textinhalt durch Festlegen des Werts, der die **[Text](controls/properties-core.md)** Eigenschaft eine leere Zeichenfolge **""** und legen Sie den Wert an die Nachricht erneut.

## <a name="best-practices"></a>Bewährte Methoden

* Legen Sie immer **[Visible](controls/properties-core.md)** auf "true". Einige Bildschirmsprachausgaben erkennen nicht dynamische Bereiche, die aus- und wieder eingeblendet.
* Vermeiden Sie die Änderung des Werts der  **[Live](controls/properties-accessibility.md)** . Einige Bildschirm, die Leser erkennen nicht, wird eine nicht-live-Region live und umgekehrt.
* Positionieren des dynamischen Bereichs in einer logischen Position in der app an, auch wenn es nicht angezeigt wird. Sicherstellen Sie, dass dessen Inhalt im Kontext mit den Elementen sinnvolle davor und danach. Benutzer können zugreifen ein dynamischen Bereichs jederzeit über die normalen Navigation mit Sprachausgabe, nicht nur, wenn Änderungen auftreten.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie [zeigen Inhalt nur für Sprachausgaben](accessible-apps-content-visibility.md) ob des dynamischen Bereichs sehbehinderte Benutzer ausgeblendet werden soll.