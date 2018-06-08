---
title: Öffnen von Entitätsdaten in Excel | Microsoft-Dokumentation
description: Öffnen Sie Entitätsdaten in Excel zum interaktiven Anzeigen und Bearbeiten.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: 8dbf6088104270d9251b70eec9adf0642de2f879
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445879"
---
# <a name="open-entity-data-in-excel"></a>Öffnen von Entitätsdaten in Excel
Indem Sie Entitätsdaten in Microsoft Excel öffnen, können Sie schnell und einfach Daten mithilfe des Microsoft PowerApps-Add-Ins für Excel anzeigen und bearbeiten. Für das PowerApps-Add-In für Excel wird Microsoft Excel 2016 benötigt.

![Excel-Add-In](./media/data-platform-cds-excel-addin/ExcelAddin.png "PowerApps-Add-In für Excel")

## <a name="open-entity-data-in-excel"></a>Öffnen von Entitätsdaten in Excel
1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**. Alle Entitäten werden angezeigt.
2. Klicken Sie auf die Auslassungspunkte (...) rechts neben der Entität, die Sie interessiert.
3. Klicken Sie auf **In Excel öffnen**, und öffnen Sie dann die Arbeitsmappe, die generiert wird. Diese Arbeitsmappe enthält die Bindungsinformationen für die Entität, einen Zeiger auf Ihre Umgebung und einen Zeiger auf das PowerApps-Add-In für Excel.  
4. Klicken Sie in Excel auf **Bearbeitung aktivieren**, um das Ausführen des PowerApps-Add-Ins für Excel zu aktivieren. Das Excel-Add-In wird in einem Bereich auf der rechten Seite des Excel-Fensters ausgeführt.
5. Wenn Sie das PowerApps-Add-In für Excel zum ersten Mal ausführen, klicken Sie auf **Diesem Add-In vertrauen**, um das Ausführen des Add-Ins für Excel zuzulassen.
6. Klicken Sie, wenn Sie zur Anmeldung aufgefordert werden, auf **Sign in** (Anmelden), und melden Sie sich dann mit denselben Anmeldeinformationen an, die Sie auf [powerapps.com](https://web.powerapps.com) verwendet haben. Das Excel-Add-In verwendet einen vorherigen Anmeldekontext und meldet Sie wenn möglich automatisch an. Überprüfen Sie deshalb den Benutzernamen in der oberen rechten Ecke des Excel-Add-Ins.

Das Excel-Add-In liest die Daten für die ausgewählte Entität automatisch. Beachten Sie, dass sich in der Arbeitsmappe erst dann Daten befinden, wenn diese vom Excel-Add-In eingelesen werden.

## <a name="view-and-refresh-data-in-excel"></a>Anzeigen und Aktualisieren von Daten in Excel
Nachdem das Excel-Add-In Entitätsdaten in die Arbeitsmappe gelesen hat, können Sie die Daten jederzeit aktualisieren, indem Sie im Excel-Add-In auf **Refresh** (Aktualisieren) klicken.

## <a name="edit-data-in-excel"></a>Bearbeiten von Daten in Excel
Sie können Entitätsdaten nach Bedarf ändern und dann zurückpublizieren, indem Sie im Excel-Add-In auf **Publish** (Veröffentlichen) klicken.

Wählen Sie zum Bearbeiten eines Datensatzes eine Zelle im Arbeitsblatt aus, und ändern Sie den Zellenwert.

Führen Sie zum Hinzufügen eines neuen Datensatzes einen der folgenden Schritte aus:

* Klicken Sie auf eine beliebige Stelle im Arbeitsblatt und dann im Excel-Add-In auf **New** (Neu).
* Klicken Sie in die letzte Zeile des Arbeitsblatts, und drücken Sie dann die TAB-TASTE, bis sich der Cursor aus der letzten Spalte der Zeile bewegt und eine neue Zeile erstellt wird.
* Klicken Sie in die Zeile direkt unter dem Arbeitsblatt, und beginnen Sie mit der Eingabe von Daten in eine Zelle. Wenn Sie den Fokus aus dieser Zelle bewegen, wird das Arbeitsblatt um die neue Zeile erweitert.

Führen Sie zum Löschen eines Datensatzes einen der folgenden Schritte aus:

* Klicken Sie mit der rechten Maustaste auf die Zeilennummer neben der zu löschenden Arbeitsblattzeile, und klicken Sie dann auf **Löschen**.
* Klicken Sie mit der rechten Maustaste in die zu löschende Arbeitsblattzeile, und klicken Sie dann auf **Löschen** > **Tabellenzeilen**.

## <a name="add-or-remove-columns"></a>Hinzufügen oder Entfernen von Spalten
Sie können mit dem Designer die Spalten und Entitäten anpassen, die dem Arbeitsblatt automatisch hinzugefügt werden.

1. Aktivieren Sie den Datenquellen-Designer des Excel-Add-Ins, indem Sie auf die Schaltfläche **Options** (Optionen) (das Zahnradsymbol) klicken und das Kontrollkästchen **Enable design** (Design aktivieren) aktivieren.
2. Klicken Sie im Excel-Add-In auf **Design**. Alle Datenquellen sind aufgeführt.
3. Klicken Sie neben der Datenquelle auf die Schaltfläche **Edit** (Bearbeiten) (Stiftsymbol).
4. Passen Sie die Liste im Feld **Selected fields** (Ausgewählte Felder) nach Bedarf an:
   * Klicken Sie zum Hinzufügen eines Felds aus dem Feld **Available fields** (Verfügbare Felder) zum Feld **Selected fields** (Ausgewählte Felder) auf das Feld und dann auf **Add** (Hinzufügen). Doppelklicken Sie alternativ auf das Feld.
   * Klicken Sie zum Entfernen eines Felds aus dem Feld **Selected fields** (Ausgewählte Felder) auf das Feld und dann auf **Remove** (Entfernen). Doppelklicken Sie alternativ auf das Feld.
   * Klicken Sie zum Ändern der Reihenfolge der Felder auf das Feld im Feld **Selected fields** (Ausgewählte Felder) und dann auf **Up** (Nach oben) oder **Down** (Nach unten).
5. Wenden Sie die Änderungen auf die Datenquelle an, indem Sie auf **Update** (Aktualisieren) und anschließend auf **Done** (Fertig) klicken, um den Designer zu beenden. Wenn Sie ein Feld (eine Spalte) hinzugefügt haben, klicken Sie auf **Refresh** (Aktualisieren), um einen aktualisierten Datensatz abzurufen.

> [!NOTE]
> Stellen Sie sicher, dass Sie immer die ID und erforderliche Felder in Ihre Arbeitsmappe einfügen, ansonsten treten bei der Veröffentlichung möglicherweise Fehler auf.

> [!NOTE]
> Wenn Sie Nachschlagefelder hinzufügen, müssen Sie sicherstellen, dass Sie jeweils die ID- und die Anzeigefelder hinzufügen.

## <a name="troubleshooting"></a>Problembehandlung
Es gibt ein paar Probleme, die durch einige einfache Schritte behoben werden können.

* Nicht alle Entitäten unterstützen das Bearbeiten und die Erstellung neuer Datensätze. Diese Entitäten öffnen Excel und ermöglichen Ihnen, Daten anzuzeigen, das Veröffentlichen wird jedoch deaktiviert.
* Nachschlagefelder müssen über das Add-In bearbeitet werden, damit garantiert auf den richtigen Datensatz verwiesen wird. Das Aktualisieren dieser Felder durch Kopieren und Einfügen und durch Direkteingabe in das Feld wird nicht unterstützt.


Wenn ein Problem auftritt, das hier nicht beschrieben wird, können Sie sich über die [Supportseiten](https://powerapps.microsoft.com/support/) an uns wenden.

## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md)
* [Definieren von Beziehungen zwischen Entitäten](data-platform-entity-lookup.md)
* [Schnellstart: Generieren einer App von Common Data Service für Apps aus in PowerApps](../canvas-apps/data-platform-create-app.md)
* [Create an app from scratch using Common Data Service for Apps (Erstellen einer App von Grund auf mit Common Data Service für Apps)](../canvas-apps/data-platform-create-app-scratch.md)

