---
title: "Öffnen von Entitätsdaten in Excel | Microsoft-Dokumentation"
description: "Öffnen Sie Entitätsdaten in Excel zum interaktiven Anzeigen und Bearbeiten."
services: powerapps
documentationcenter: na
author: chrisgarty
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 2a72bfa21c8d4cb7eab0a3cb2292a61d5c036696
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="open-entity-data-in-excel"></a>Öffnen von Entitätsdaten in Excel
Indem Sie Entitätsdaten in Microsoft Excel öffnen, können Sie schnell und einfach Daten mithilfe des Microsoft PowerApps-Add-Ins für Excel anzeigen und bearbeiten. Für das PowerApps-Add-In für Excel wird Microsoft Excel 2016 benötigt.

**Hinweis**: Wenn Ihr Microsoft Azure Active Directory-Mandant (Azure AD) so konfiguriert ist, dass er Active Directory-Verbunddienste (AD FS) verwendet, müssen Sie sicherstellen, dass das Update von Mai 2016 angewendet wurde, damit das Excel-Add-In Sie richtig anmelden kann.

## <a name="open-entity-data-in-excel"></a>Öffnen von Entitätsdaten in Excel
1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entities** (Entitäten). Alle Entitäten werden angezeigt.
2. Klicken Sie auf die Auslassungspunkte (...) rechts neben der Entität, die Sie interessiert.
3. Klicken Sie auf **In Excel öffnen**, und öffnen Sie dann die Arbeitsmappe, die generiert wird. Diese Arbeitsmappe enthält die Bindungsinformationen für die Entität, einen Zeiger auf Ihre Umgebung und einen Zeiger auf das PowerApps-Add-In für Excel.  
4. Klicken Sie in Excel auf **Bearbeitung aktivieren**, um das Ausführen des PowerApps-Add-Ins für Excel zu aktivieren. Das Excel-Add-In wird in einem Bereich auf der rechten Seite des Excel-Fensters ausgeführt.
5. Wenn Sie das PowerApps-Add-In für Excel zum ersten Mal ausführen, klicken Sie auf **Diesem Add-In vertrauen**, um das Ausführen des Add-Ins für Excel zuzulassen.
6. Klicken Sie, wenn Sie zur Anmeldung aufgefordert werden, auf **Sign in** (Anmelden), und melden Sie sich dann mit denselben Anmeldeinformationen an, die Sie auf [powerapps.com](https://web.powerapps.com) verwendet haben. Das Excel-Add-In verwendet einen vorherigen Anmeldekontext und meldet Sie wenn möglich automatisch an. Überprüfen Sie deshalb den Benutzernamen in der oberen rechten Ecke des Excel-Add-Ins.

Das Excel-Add-In liest die Daten für die ausgewählte Entität automatisch. Beachten Sie, dass sich in der Arbeitsmappe erst dann Daten befinden, wenn diese vom Excel-Add-In eingelesen werden.

## <a name="view-and-refresh-entity-data-in-excel"></a>Anzeigen und Aktualisieren der Entitätsdaten in Excel
Nachdem das Excel-Add-In Entitätsdaten in die Arbeitsmappe gelesen hat, können Sie die Daten jederzeit aktualisieren, indem Sie im Excel-Add-In auf **Refresh** (Aktualisieren) klicken.

## <a name="edit-entity-data-in-excel"></a>Bearbeiten von Entitätsdaten in Excel
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
Sie können mit dem Designer die Spalten anpassen, die dem Arbeitsblatt automatisch hinzugefügt werden.

1. Aktivieren Sie den Datenquellen-Designer des Excel-Add-Ins, indem Sie auf die Schaltfläche **Options** (Optionen) (das Zahnradsymbol) klicken und das Kontrollkästchen **Enable design** (Design aktivieren) aktivieren.
2. Klicken Sie im Excel-Add-In auf **Design**. Alle Datenquellen sind aufgeführt.
3. Klicken Sie neben der Datenquelle auf die Schaltfläche **Edit** (Bearbeiten) (Stiftsymbol).
4. Passen Sie die Liste im Feld **Selected fields** (Ausgewählte Felder) nach Bedarf an:
   * Klicken Sie zum Hinzufügen eines Felds aus dem Feld **Available fields** (Verfügbare Felder) zum Feld **Selected fields** (Ausgewählte Felder) auf das Feld und dann auf **Add** (Hinzufügen). Doppelklicken Sie alternativ auf das Feld.
   * Klicken Sie zum Entfernen eines Felds aus dem Feld **Selected fields** (Ausgewählte Felder) auf das Feld und dann auf **Remove** (Entfernen). Doppelklicken Sie alternativ auf das Feld.
   * Klicken Sie zum Ändern der Reihenfolge der Felder auf das Feld im Feld **Selected fields** (Ausgewählte Felder) und dann auf **Up** (Nach oben) oder **Down** (Nach unten).
5. Wenden Sie die Änderungen auf die Datenquelle an, indem Sie auf **Update** (Aktualisieren) und anschließend auf **Done** (Fertig) klicken, um den Designer zu beenden. Wenn Sie ein Feld (eine Spalte) hinzugefügt haben, klicken Sie auf **Refresh** (Aktualisieren), um einen aktualisierten Datensatz abzurufen.

## <a name="troubleshooting"></a>Problembehandlung
Es gibt ein paar Probleme, die durch einige einfache Schritte behoben werden können.

* Wenn beim Laden von Metadaten durch das Excel-Add-In eine „Forbidden“-Nachricht erscheint, verfügt das beim Excel-Add-In angemeldete Konto über keine Berechtigung für das Verwenden der Common Data Service-Zieldatenbank. Stellen Sie zum Beheben dieses Problems sicher, dass der richtige Benutzername oben rechts im Excel-Add-In angezeigt wird. Klicken Sie wenn erforderlich auf den Benutzernamen in der oberen rechten Ecke des Excel-Add-Ins, melden Sie sich ab, und melden Sie sich dann erneut an.
* Wenn während des Anmeldeprozesses eine leere Webseite geöffnet wird, benötigt das Konto AD FS, aber die Excel-Version, in der das Add-In ausgeführt wird, ist nicht aktuell genug, um das Anmeldedialogfeld zu laden. Aktualisieren Sie wenn erforderlich die Version von Excel, die Sie verwenden. Verwenden Sie dazu das [Office-Bereitstellungstool](https://technet.microsoft.com/library/mt455210.aspx), um [vom verzögerten Kanal in den aktuellen Kanal zu verschieben](https://technet.microsoft.com/library/jj219422.aspx).

Wenn ein Problem auftritt, das hier nicht beschrieben wird, können Sie sich über die [Supportseiten](https://powerapps.microsoft.com/support/) an uns wenden.

## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md)
* [Definieren von Beziehungen zwischen Entitäten](data-platform-entity-lookup.md)
* [Generate an app by using a Common Data Service database (Generieren einer App mithilfe einer Common Data Service-Datenbank)](data-platform-create-app.md)
* [Neuerstellen einer App mithilfe einer Common Data Service-Datenbank](data-platform-create-app-scratch.md)

