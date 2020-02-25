---
title: Erstellen und Verwalten von Veröffentlichungsstatus in Power Apps-Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie in einem Portal Veröffentlichungsstatus erstellen und verwalten.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 6daf92aa4d821b66b8388826d69dcb8bbd99ddb4
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980523"
---
# <a name="create-and-manage-publishing-states"></a>Erstellen und Verwalten von Veröffentlichungsstatus

Im Veröffentlichungsstatus können Sie die Definition eines Inhalts-Lebenszyklus in der Portalwebsite definieren. Auf einer grundlegenden Ebene kann ein Veröffentlichungsstatus bestimmen, ob eine zugeordnete Entität auf einem Portal als angezeigt/veröffentlicht gilt. In den komplexeren Konfigurationen können Sie einen Mehrstufenprozess für Inhalt-Überprüfung und  Veröffentlichen mit Sicherheitseinschränkungen im Zusammenhang mit jeder Phase definieren.

Veröffentlichungsstatus können mit [Webseiten](web-page.md), [Internet-Dateien](web-files.md), [Web-Links](manage-web-links.md), Foren und Ankündigungen verwendet werden.

Standardmäßig werden zwei veröffentlichte Status verfügbar: Entwürfe und veröffentlicht. Entwurf gibt Inhalte an, die für Nicht-Inhaltbenutzer nicht sichtbar sein soll, während veröffentlicht Inhalte angibt, der allen Portalbenutzern sichtbar sein soll (mit anderen Sicherheitseinschränkungen) Sie können die Standardkonfiguration ändern, um Ihre individuellen Anforderungen zu erfüllen, bei Bedarf mithilfe von neuen Status hinzufügen bzw. Status- umbenennen.

## <a name="manage-publishing-states"></a>Verwalten von Veröffentlichungsstatus

Veröffentlichungsstatus können innerhalb von Portalen erstellt, bearbeitet oder gelöscht werden.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Navigieren Sie zu **Portale** > **Websites**.

3. Wählen Sie die übergeordnete Website aus, um Veröffentlichungsstatus zu verwalten.

4. Wechseln Sie zur Registerkarte **Veröffentlichungsstatus**. Die Liste der verfügbaren Veröffentlichungsstatus wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![Verwalten von Veröffentlichungsstatus](../media/publishing-states.png "Verwalten von Veröffentlichungsstatus")

5. Wenn Sie einen neuen Veröffentlichungsstatus hinzufügen möchten, wählen Sie **Neuer Veröffentlichungsstatus**.

6. Wenn Sie einen vorhandenen Veröffentlichungsstatus bearbeiten, wählen Sie den Veröffentlichungsstatusnamen aus.

7. Geben Sie im Veröffentlichungs-Statusfenster entsprechende Werte in die Felder ein.

8. Klicken Sie auf **Speichern und schließen**.


### <a name="publishing-state-attributes"></a>Veröffentlichungsstatusattribute

|Name|Beschreibung|
|-----|--------|
|Name|Der beschreibende Name des Status. In diesem Feld ist ein Eintrag erforderlich.|
|Website|Die Website, zu dem der Blog gehört. In diesem Feld ist ein Eintrag erforderlich.|
|Ist-Standard|Wenn aktiviert, gilt dieser Status als Standardstatus für die Website. Dies bestimmt den ausgewählten Standardstatus beim Erstellen neuer Entitäten durch die Portalvorderseitenbearbeitungsschnittstelle.<br>**Hinweis**: Nur ein veröffentlichter Status auf einer gegebenen Website muss als Standardstatus gekennzeichnet werden.|
|Ist sichtbar|Wenn überprüft wird die Entität, die diesem Status zugeordnet ist, als angezeigt (oder veröffentlicht), auf dem Portal betrachtet.<br>Während eine Entität, die einem nicht-sichtbaren Status zugeordnet ist, nicht angezeigt wird, ist unter Umständen eine Entität, die einem sichtbaren Status zugeordnet ist, auch nicht sichtbar aufgrund von  Sicherheitsberechtigungen, Ablaufdatum oder anderen Sichtbarkeitsregeln.<br>Benutzern mit Berechtigungen für Inhaltsverwaltung kann die Möglichkeit zur Nutzung des „Vorschaumodus” gewährt werden. Dies ermöglicht es diesen Benutzern, nicht veröffentlichten Inhalt anzuzeigen (Vorschau).|
|Anzeigereihenfolge|Ein ganzzahliger Wert, der den Auftrag angibt, auf dem der Status platziert wird, wird im Menü aufgerufen und in Dropdownlisten zum Auswählen eines Veröffentlichungstatus aufgeführt - größtenteils auf Portalvorderseitenbearbeitungsschnittstellen.|
|||

## <a name="publishing-state-transition-rules"></a>Veröffentlichungsstatus-Übergangsregeln

Veröffentlichungsstatus-Übergangsregeln ermöglichen das Anzeigen von Steuerelementen, über die  Webrollen die Berechtigung haben, ausführen, welche Content-Änderungen auf dem Portal im Hinblick auf den Veröffentlichungsstatus erfolgen.

Statusübergangsregeln regeln den Übergang von Veröffentlichungsstatus (Entwurf oder veröffentlicht). Wenn ein Benutzer versucht, den Veröffentlichungsstatus eines Elements aus einem Element zu einem anderen zu wechseln, wenn eine Regel für den Übergang vorhanden ist, dann wird der Sicherheitsanbieter sicherstellen, dass die zweite Webrolle für den angemeldeten Benutzer die entsprechende Berechtigung verfügt zum Ausführen des Vorgangs.

Wenn der angemeldete Benutzer, der die Änderungen versucht, in einer dieser Rollen ist, die eine Einführung zur Regel zuweisen, wird der Übergang erfolgreich. Wenn ein Benutzer keine Berechtigungen besitzt, eine Änderung einer Regel zu anderen vorzunehmen, dann können die Vorderseitenbearbeitungen diese Änderungen nicht vornehmen. Alternativ können Sie die Regel erstellen; denn wenn Sie Webrollen erstellen, werden diese Regeln den  Webrollen hinzugefügt. Eine Regel kann einer beliebigen Zahl von Webrollen zugeordnet werden und umgekehrt.

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Gehen Sie zu **Portale**  > **Veröffentlichungsstatus-Übergangsregeln**.

3. Klicken Sie auf **Neu**, um eine neue Regel zu erstellen.

4. Zur Bearbeitung einer vorhandenen Regel wählen Sie den Regelnamen aus.

5. Geben Sie im Veröffentlichungs-Statusübergangsfenster entsprechende Werte in die Felder ein.

6. **Speichern** wählen, sodass Sie fortfahren können, Webrollen hinzuzufügen.

    > [!div class=mx-imgBorder]
    > ![Veröffentlichungsstatus-Übergangsregel erstellen](../media/publishing-state-transition-rule.png "Veröffentlichungsstatus-Übergangsregel erstellen")

7. Wählen Sie auf der **Webrollen**-Registerkarte **Vorhandene Webrolle hinzufügen** aus. Suchen Sie im Bereich **Suchdatensätze** die entsprechenden Webrollen und fügen Sie sie hinzu.

8. Wählen Sie **Speichern** aus.

## <a name="state-based-control-rules"></a>Status-basierte Steuerregeln

[Webseitenzugriffssteuerungsregeln](webpage-access-control.md) kann mit Veröffentlichungsstatus verknüpft werden, um das erforderliche Recht zuzulassen bzw. zu verweigern, das Sie auf der Verzweigung der Website und den Veröffentlichungsstatus des Inhalts in dieser Verzweigung anzeigen oder ändern möchten. Um dies zu erzielen, weisen Sie eine Webseitenzugriffssteuerungsregel einem Veröffentlichungsstatus zu. Sobald sie einem Veröffentlichungsstatus zugeordnet ist, wird die aufgewendete Regel nur für Webseiten angewendet, wenn der Veröffentlichungsstatus aktiv ist.

Beispielsweise möchten Sie, dass eine Person in der Content-Veröffentlichungsrolle Inhalte einer Seite ändern kann,  aber nur, sofern diese Seite im Draftmodus ist.  Dadurch würde sichergestellt, dass Änderungen an der Seite nicht vorgenommen wurden, während die Seite "live" ist und einen Genehmigungsprozess ermöglicht, um die ausstehenden Änderungen vorzunehmen.

Dazu würden Sie eine Regel mit der Erteilungsänderungsberechtigung ausführen und auf den entsprechenden Link (oder die Homepage, wenn die Regel für die gesamte Website gilt) anwenden. Sie würden dann diese Regel dem Entwurfsstatus zuordnen.

> [!div class=mx-imgBorder]
> ![Statusbasierte Steuerregel erstellen](../media/state-based-control-rule.png "Statusbasierte Steuerregel erstellen")

Sie würden diese Regel mit der entsprechenden Webrolle beispielsweise Content-Veröffentlichung zuordnen. Angenommen diese Webrolle ist nicht einer erlaubenden Regel zugeordnet (z. B. eine Regel, die Regeln unabhängig vom Veröffentlichungsstatus ändert), der Benutzer in der Content-Veröffentlichungswebrolle Seiten im Entwurfsstatus ändern, kann aber keine Seiten im Veröffentlichungsstatus ändern.
