---
title: "Verwenden von Feldgruppen für die App-Erstellung | Microsoft-Dokumentation"
description: Verwenden Sie Feldgruppen, um die Erstellung von Apps in der gesamten Datenbank zu standardisieren.
services: powerapps
documentationcenter: na
author: aneesmsft
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/11/2017
ms.author: aneesa
ms.openlocfilehash: 023282c31ea90cd391d425faaf036603b5521d08
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="use-field-groups"></a>Feldgruppen verwenden
Feldgruppen bieten eine Möglichkeit, ein oder mehrere Felder einer Entität zu gruppieren. Feldgruppen können die Erstellung und Wartung von Apps schneller und einfacher machen. Eine Feldgruppe enthält ein oder mehrere Felder, und ein Feld kann in einer beliebigen Anzahl von Feldgruppen angezeigt werden. Ein Feld kann nur einmal in einer Feldgruppe angezeigt werden.

Feldgruppen werden auf einer Entität gespeichert und können von allen Apps, die dieselbe Entität verwenden, gemeinsam genutzt werden. Zu jedem Zeitpunkt können viele verschiedene Apps dieselbe Entität und Feldgruppen dieser Entität verwenden. Diese Zentralisierung und Freigabe von Feldgruppen hilft beim Erzwingen von Konsistenz, da eine Feldgruppe immer dieselben Felder angezeigt, egal wo sie verwendet wird. Dies erleichtert die Wartung, da eine Änderung an einer Feldgruppe automatisch an allen Stellen, die diese Feldgruppe verwenden, widergespiegelt wird. Mit Feldgruppen können Sie die Erstellung und Anpassung von Apps beschleunigen, da ein Anwendungsentwickler mit Gruppen von Feldern anstatt mit einzelnen Feldern arbeitet.

## <a name="default-field-groups"></a>Standard-Feldgruppen
Common Data Service umfasst mehrere Standard-Feldgruppen auf Entitäten. Diese Feldgruppen werden an verschiedenen Stellen verwendet, und machen die App-Erstellung und die -Anpassung schneller und einfacher.

| Standard-Feldgruppenname | Beschreibung |
| --- | --- |
| DefaultList |Wird verwendet, um eine Liste von Datensätzen in einem Tabellenformat anzuzeigen. |
| DefaultCard |Wird verwendet, um eine Liste von Datensätzen in einem Kartenformat anzuzeigen. |
| DefaultDetails |Wird verwendet, um die Details eines einzelnen Datensatzes in der Ansicht anzuzeigen und zu bearbeiten. |
| DefaultLookup |Wird verwendet, um eine Suche zum Auswählen eines Datensatzes anzuzeigen. |

## <a name="view-a-field-group"></a>Anzeigen einer Feldgruppe
1. Melden Sie sich bei [powerapps.com](https://web.powerapps.com) an.
2. Wenn Sie Zugriff auf mehr als eine Umgebung haben, stellen Sie sicher, dass Sie über die Umgebungsauswahl in der oberen Leiste die richtige Umgebung ausgewählt haben.
3. Erweitern Sie den Abschnitt **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.
4. Klicken oder tippen Sie in der Liste der Entitäten auf die Entität, für die Sie die Feldgruppe anzeigen möchten.
5. Klicken oder tippen Sie in der Kopfzeile über der Liste der Felder auf **Feldgruppen**. Sie sehen jetzt alle Feldgruppen, die derzeit für die Entität vorhanden sind.
6. Klicken oder tippen Sie in der Liste der Feldgruppen auf die Feldgruppe, für die Sie die Details anzeigen möchten.
7. In den Feldgruppendetails gibt es zwei Listen nebeneinander. Die eine hat den Titel **Entitätsfelder** und führt alle Felder für die Entität auf. Die andere hat den Titel **Felder der Feldgruppe** und listet die Felder auf, die in der Feldgruppe enthalten sind.

## <a name="modify-a-field-group"></a>Ändern einer Feldgruppe
1. Zeigen Sie die Feldgruppe an, die Sie ändern möchten.
2. Doppelklicken Sie zum Hinzufügen eines Felds auf einen Feldnamen in der **Entitätsfelder**-Liste. Sie können Felder auch per Drag & Drop aus der **Entitätsfelder**-Liste in die **Felder der Feldgruppe**-Liste verschieben.
3. Klicken Sie zum Entfernen einer Feldgruppe in der **Felder der Feldgruppe**-Liste auf das **X** neben dem Feldnamen.
4. Klicken oder tippen Sie auf die Schaltfläche **Speichern**.

*Hinweis: Das Ändern von Feldgruppen für [Standardentitäten](guided-learning/learning-common-data-service-entities.md) wird derzeit nicht unterstützt, aber Sie können Feldgruppen für Ihre benutzerdefinierten Entitäten ändern.*

## <a name="creating-a-field-group"></a>Erstellen einer Feldgruppe
Standard-Feldgruppen werden automatisch erstellt, wenn Sie eine Entität erstellen. Das Erstellen zusätzlicher Feldgruppen wird derzeit nicht unterstützt.

## <a name="delete-a-field-group"></a>Löschen einer Feldgruppe
Das Löschen einer Feldgruppe wird derzeit nicht unterstützt.

## <a name="view-and-edit-field-group-data-in-microsoft-excel"></a>Anzeigen und Bearbeiten von Feldgruppendaten in Microsoft Excel
1. Zeigen Sie die Feldgruppen für die Entität an, für die Sie die Daten untersuchen möchten.
2. Neben jeder Feldgruppe befindet sich ein Excel-Symbol. Das Excel-Symbol ist nur aktiviert, wenn die Feldgruppe über Felder verfügt.
3. Klicken Sie auf das Excel-Symbol für die Feldgruppe, die Sie in Excel öffnen möchten. Es wird eine Arbeitsmappe generiert, die die Entitätsfeldliste, das Excel-Add-In und einen Zeiger auf Ihre Umgebung enthält.
4. Öffnen Sie die generierte Arbeitsmappe, die vom Browser bereitgestellt wird.
5. Aktivieren Sie nach dem Öffnen der Arbeitsmappe die Bearbeitung. Das Excel-Add-In liest dann die Daten in die Arbeitsmappe. Weitere Informationen finden Sie unter [Open entity data in Excel (Öffnen von Entitätsdaten in Excel)](data-platform-interactive-excel.md).

## <a name="field-group-usage"></a>Verwendung von Feldgruppen
Die Standard-Feldgruppen beschleunigen die Erstellung und Anpassung von Anwendungen. Hier sind einige Stellen, an denen Sie derzeit Feldgruppen in Aktion sehen können:

* Steuerelement **Formularentität**: Das Steuerelement „Formularentität“ verwendet die Standard-Feldgruppen zum Anzeigen dynamischer Formulare, mit deren Hilfe die Erstellung von Apps beschleunigt, Konsistenz erzwungen und die Wartung vereinfacht werden kann. Weitere Informationen finden Sie unter [Verwenden des Steuerelements „Formularentität“](entity-form-control.md).
* **Nachschlagesteuerelement**: Wenn eines der Felder, die Sie auf dem Bildschirm hinzufügen, ein Verweis auf eine andere verknüpfte Entität ist, wird das Feld als Nachschlagesteuerelement (Auswahlliste) gerendert. Wenn ein Benutzer auf das Nachschlagesteuerelement klickt, um einen Datensatz aus der verknüpften Entität auszuwählen, werden die angezeigten Felder durch die **DefaultLookup**-Feldgruppe auf der verknüpften Entität bestimmt. Nur die ersten beiden Felder der **DefaultLookup**-Feldgruppe werden verwendet.
* **Erstellen einer App**: Wenn Sie sich beim Generieren einer App für die Option entscheiden, eine App aus Daten zu erstellen, werden die Bildschirme für die Entität, die Sie auswählen, automatisch erstellt. Das **Formular anzeigen**-Steuerelement auf dem **Anzeige**-Bildschirm und das **Formular bearbeiten**-Steuerelement auf dem **Bearbeiten**-Bildschirm verwenden die **DefaultDetails**-Feldgruppe, um zu bestimmen, welche Felder standardmäßig zu diesen Bildschirmen hinzugefügt werden.

