---
title: Entitätsdaten in Excel öffnen | Microsoft Docs
description: Öffnen Sie Entitätsdaten für interaktives Anzeigen und Bearbeiten in Excel.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fa1602b59ed0fdfeec09a8bc7e5f1126249f071f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757486"
---
# <a name="open-entity-data-in-excel"></a>Entitätsdaten in Excel öffnen
Durch das Öffnen von Entitätsdaten in Microsoft Excel können Sie Daten mithilfe des Microsoft PowerApps Excel-Add-Ins schnell und problemlos anzeigen und bearbeiten. Das PowerApps Excel Add-in erfordert Microsoft Excel 2016.

![Excel-Add-In](./media/data-platform-cds-excel-addin/ExcelAddin.png "PowerApps Excel-Add-In")

## <a name="open-entity-data-in-excel"></a>Entitätsdaten in Excel öffnen
1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**. Es werden alle Entitäten angezeigt.
2. Klicken Sie auf die Auslassungspunkte (...) rechts neben der Entität, an der Sie interessiert sind.
3. Klicken Sie auf **In Excel öffnen** und öffnen Sie dann die Arbeitsmappe, die generiert wird. Diese Arbeitsmappe hat bindende Informationen für die Entität, einen Zeiger auf Ihre Umgebung und einen Zeiger auf das PowerApps Excel-Add-In.  
4. In Excel klicken Sie auf **Bearbeitung aktivieren**, um das PowerApps Excel-Add-In auszuführen. Das Excel-Add-In wird in einen Bereich auf der rechten Seite des Excel-Fensters ausgeführt.
5. Wenn Sie das PowerApps Excel-Add-In das erste Mal ausführen, klicken Sie auf **Diesem Add-In vertrauen**, um zuzulassen, dass das Excel-Add-Ins ausgeführt wird.
6. Wenn Sie aufgefordert werden, sich anzumelden, folgen Sie der Aufforderung, klicken Sie auf **Anmelden** und melden Sie sich dann an, indem Sie dieselben Anmeldeinformationen verwenden, die Sie auf [powerapps.com](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) verwenden. Das Excel-Add-In verwendet einen früheren Anmeldungskontext und meldet Sie automatisch an, wenn möglich. Deshalb sollten Sie den Benutzernamen oberen rechts im Excel-Add-In verifizieren.

Das Excel-Add-In liest die Daten für die Entität, die Sie ausgewählt haben, automatisch. Beachten Sie, dass es keine Daten in der Arbeitsmappe gibt, bis das Excel-Add-In sie einliest.

## <a name="view-and-refresh-data-in-excel"></a>Daten in Excel anzeigen und aktualisieren
Nachdem das Excel-Add-In die Entitätsdaten in die Arbeitsmappe liest, können Sie die Daten jederzeit ausführen, indem Sie im Excel-Add-In auf **Aktualisieren** klicken.

## <a name="edit-data-in-excel"></a>Daten in Excel bearbeiten
Sie können Entitätsdaten bei Bedarf ändern und anschließend wieder veröffentlichen indem Sie im Excel-Add-In auf **Veröffentlichen** klicken.

Zum Bearbeiten eines Datensatzes wählen Sie eine Zelle in der Tabelle aus, und ändern Sie dann den Zellenwert.

Um einen neuen Datensatz hinzuzufügen, führen Sie einen dieser Schritte aus:

* Klicken Sie auf eine beliebige Stelle in der Tabelle und anschließend im Excel-Add-In auf **Neu**.
* Klicken Sie in die letzte Zeile in der Tabelle, und drücken Sie dann die TAB-TASTE, bis der Cursor aus der letzten Spalte dieser Zeile verschoben und eine neue Zeile erstellt wird.
* Klicken Sie in der Zeilen direkt unterhalb der Tabelle und geben Sie Daten in eine Zelle ein. Wenn Sie den Fokus aus dieser Zelle verschieben, erweitert sich die Tabelle, um die neue Zeile einzuschließen.

Um einen neuen Datensatz zu löschen, führen Sie einen dieser Schritte aus:

* Klicken Sie mit der rechten Maustaste auf die Zeilennummer neben der Tabelle, um zu löschen, und klicken Sie dann auf **Löschen**.
* Klicken Sie in die Tabellenzeile, um zu löschen, und klicken Sie dann auf **Löschen** > **Tabellenzeilen**.

## <a name="add-or-remove-columns"></a>Hinzufügen oder Entfernen von Spalten
Sie können den Designer verwenden, um die Spalten und Entitäten anzupassen, die der Tabelle automatisch hinzugefügt werden.

1. Aktivieren Sie den Datenquellendesigner des Excel-Add-Ins, indem Sie auf die Schaltfläche **Optionen** (das Zahnradsymbol) klicken und dann das Kontrollkästchen **Entwurf aktivieren** aktivieren.
2. Klicken Sie auf **Entwurf** im Excel-Add-In. Alle Datenquellen werden aufgelistet.
3. Neben der Datenquelle klicken Sie auf die Schaltfläche **Bearbeiten** (das Stiftssymbol).
4. Passen Sie bei Bedarf die Liste im Feld **Ausgewählte Felder** an:
   * Um einem Feld vom Feld **Verfügbare Felder** dem Feld **Ausgewählte Felder** hinzuzufügen, klicken Sie auf das Feld und dann auf **Hinzufügen**. Doppelklicken Sie alternativ auf das Feld.
   * Um ein Feld aus dem Feld **Ausgewählte Felder** zu entfernen, klicken Sie auf das Feld und dann auf **Entfernen**. Doppelklicken Sie alternativ auf das Feld.
   * Um die Reihenfolge der Felder zu ändern, klicken Sie im Feld **Ausgewählte Felder** auf das Feld und dann auf **Nach oben** oder **Nach unten**.
5. Wenden Sie Ihre Änderungen auf die Datenquelle an, indem Sie auf **Aktualisieren** und dann auf **Fertig** klicken, um den Designer zu beenden. Wenn Sie ein Feld (Spalte) hinzugefügt haben, klicken Sie auf **Aktualisieren**, um einen aktualisierten Datensatz abzurufen.

> [!NOTE]
> Stellen Sie sicher, immer die ID und die erforderlichen Felder in Ihrer Arbeitsmappe einzuschließen, da Sie sonst unter Umständen Fehler beim Veröffentlichen erhalten.

> [!NOTE]
> Beim Hinzufügen von Suchfeldern stellen Sie sicher, dass Sie das ID- sowie das Anzeigefeld hinzuzufügen.

## <a name="troubleshooting"></a>Problembehandlung
Es gibt einige Probleme, die durch einige einfache Schritte behoben werden können.

* Nicht alle Entitäten unterstützen das Bearbeiten und Erstellen neuer Datensätze. Diese Entitäten können in Excel geöffnet werden, um dort Daten anzuzeigen. Die Veröffentlichung ist aber deaktiviert.
* Suchfelder müssen mithilfe des Add-Ins bearbeitet werden, um sicherzustellen, dass der korrekte Datensatz verwiesen wird. Die Felder über kopieren und einfügen zu aktualisieren, oder direkt etwas in die Felder einzugeben wird nicht unterstützt.


Falls ein Problem auftritt, das nicht hier nicht beschrieben wird, kontaktieren Sie uns über die [Supportseiten](https://powerapps.microsoft.com/support/).

## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md)
* [Beziehungen zwischen Entitäten definierten](data-platform-entity-lookup.md)
* [Generieren Sie eine App, indem Common Data Service](../canvas-apps/data-platform-create-app.md)
* [Create an app from scratch using Common Data Service](../canvas-apps/data-platform-create-app-scratch.md)

