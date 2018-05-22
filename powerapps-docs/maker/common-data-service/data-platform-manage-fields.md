---
title: Verwalten von benutzerdefinierten Feldern in einer Entität | Microsoft-Dokumentation
description: Hier finden Sie ein exemplarische Vorgehensweise zum Erstellen, Lesen, Aktualisieren und Löschen von benutzerdefinierten Feldern in einer Entität in Common Data Service (CDS) für Apps.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: a4ec386ef6a7eee02c2ac608bb6e00ed9ee39c19
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
---
# <a name="manage-custom-fields-in-an-entity"></a>Verwalten von benutzerdefinierten Feldern in einer Entität
Sie können ein oder mehrere benutzerdefinierte Felder in einer beliebigen Entität erstellen und aktualisieren. Wenn Sie ein benutzerdefiniertes Feld erstellen, geben Sie einen Satz von Eigenschaften an, z.B. den Namen des Felds, den Anzeigenamen und den Typ der Daten, die es enthält. Weitere Informationen finden Sie unter [Entity attribute metadata (Attributmetadaten von Entitäten)](../../developer/common-data-service/entity-attribute-metadata.md).

> [!NOTE]
> Jede Entität verfügt über Systemfelder, die z.B. angeben, wann und durch wen ein Eintrag zuletzt aktualisiert wurde. Darüber hinaus verfügen Standardentitäten über (Standard)Felder. Sie können keine System- oder Standardfelder ändern oder löschen. Wenn Sie ein benutzerdefiniertes Feld erstellen, sollte es zusätzliche Funktionalität zu diesen integrierten Feldern bieten.

## <a name="create-a-field"></a>Ein Feld erstellen
1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität, oder [erstellen Sie eine neue Entität](data-platform-create-entity.md).

3. Fügen Sie ein neues Feld zu Ihrer Entität hinzu, indem Sie auf **Feld hinzufügen** klicken.

4. Geben Sie im Bereich „Neues Feld“ den **Anzeigenamen** für Ihr Feld ein. **Name** wird automatisch aufgefüllt und wird als eindeutiger Name für das Feld verwendet. Der **Anzeigename** wird verwendet, wenn das Feld Ihren Benutzern angezeigt wird. Der **Name** wird während des Erstellens Ihrer App in Ausdrücken und Formularen verwendet.

    > [!NOTE]
    > Die Felder **Anzeigename** können jederzeit aktualisiert werden, damit diese in Ihren Apps unterschiedlich angezeigt werden. Das Feld **Name** kann nach dem Speichern Ihrer Entität nicht mehr geändert werden, da dies dazu führen könnte, dass vorhandene Apps beeinträchtigt werden.

    ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel.png "Bereich „Neues Feld“")

5. Wählen Sie für Ihr Feld einen **Datentyp** aus. Über den Datentyp wird gesteuert, wie Informationen gespeichert und in Apps dargestellt werden. Beispielsweise wird Text auf andere Weise gespeichert als eine Dezimalzahl oder eine URL. Weitere ausführliche Informationen zu den verfügbaren Datentypen finden Sie unter [Entity attribute metadata (Attributmetadaten von Entitäten)](../../developer/common-data-service/entity-attribute-metadata.md).

    Wenn Sie dazu aufgefordert werden, geben Sie zusätzliche Informationen für den Datentyp an, den Sie angegeben haben. Je nach Datentyp werden unterschiedliche Felder dargestellt. Wenn Sie ein Feld vom Typ „Optionssatz“ oder vom Typ „Optionssatz mit Mehrfachauswahl“ erstellen, können Sie auf **Neuer Optionssatz** klicken und mit dem Feld auch einen neuen Optionssatz erstellen. Weitere Informationen finden Sie unter [Create Option set (Erstellen eines Optionssatzes)](custom-picklists.md).

    ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Bereich „Neues Feld“")


7. Aktivieren Sie das Kontrollkästchen unter **Erforderlich**, wenn Sie dieses Feld in Ihren Apps als erforderlich markieren möchten. Dadurch machen Sie das Feld jedoch nicht für alle Verbindungen mit Common Data Service zwingend erforderlich. Wenn Sie sicherstellen müssen, dass das Feld aufgefüllt wird, erstellen Sie eine [Geschäftsregel](data-platform-create-business-rule.md).

8. Aktivieren Sie das Kontrollkästchen unter **Durchsuchbar**, wenn das Feld in Ansichten, Diagrammen, Dashboards und für die erweiterte Suche verfügbar sein soll. Dieses Kontrollkästchen sollte in den meisten Fällen aktiviert sein.

9. Klicken oder tippen Sie auf **Fertig**, um den Bereich „Feld“ zu schließen und zu der Entität zurückzukehren. Sie können die Schritte 3–9 für alle Felder wiederholen.
   
    > [!IMPORTANT]
    > Ihr Feld wird erst gespeichert und erstellt, wenn Sie die Änderungen in der Entität speichern.

10. Klicken oder tippen Sie auf **Entität speichern**, um Ihre Änderungen fertigzustellen, und speichern Sie sie in Common Data Service.

    Sie werden benachrichtigt, wenn der Vorgang erfolgreich abgeschlossen ist. Wenn der Vorgang nicht erfolgreich ist, gibt eine Fehlermeldung an, welche Probleme aufgetreten sind und wie Sie sie beheben können.

## <a name="create-a-calculated-or-roll-up-field"></a>Erstellen eines berechneten Felds oder eines Roll Up-Felds
Mithilfe von berechneten Feldern können Sie manuelle Berechnungen in Ihren Geschäftsprozessen automatisieren. Beispielsweise kann es dazu kommen, dass ein Vertriebsmitarbeiter den gewichteten Umsatz für eine Verkaufsmöglichkeit erfragt. Dann wird der für eine Verkaufsmöglichkeit geschätzte Umsatz mit der jeweiligen Wahrscheinlichkeit multipliziert. Oder der Vertriebsmitarbeiter möchte automatisch einen Rabatt gewähren, wenn die Bestellsumme über 500 USD liegt. Ein berechnetes Feld kann Werte enthalten, die mithilfe von einfachen mathematischen Vorgängen (z.B. durch „Größer als“ oder „Wenn–Sonst“-Bedingungen) berechnet werden. Berechnete Felder können über die folgenden Datentypen erstellt werden:

* Eine Textzeile
* Optionssatz
* Zwei Optionen
* Ganze Zahl
* Dezimalzahl
* Währung
* Datum und Uhrzeit

Weitere Informationen zu den unterstützten Ausdruckstypen und Beispielen finden Sie unter [Definition berechneter Felder für das Automatisieren von manuellen Berechnungen](/dynamics365/customer-engagement/customize/define-calculated-fields).

## <a name="update-or-delete-a-field"></a>Ein Feld aktualisieren oder löschen
1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**, und klicken oder tippen Sie dann auf eine Entität.
2. Klicken oder tippen Sie in der Liste der Felder für die Entität, die Sie ausgewählt haben, auf ein Feld, und führen Sie anschließend einen der folgenden Schritte aus:
   
   * Ändern Sie eine oder mehrere Eigenschaften des Felds.
   * Zum Löschen des Felds klicken oder tippen Sie auf die Auslassungspunkte (...) neben dem rechten Rand des Felds, und klicken oder tippen anschließend auf **Löschen**.

3. Klicken oder tippen Sie auf **Entität speichern**, um Ihre Änderungen zu übernehmen.
   
    > [!IMPORTANT]
    > Ihre Änderungen gehen verloren, wenn Sie sie nicht speichern, bevor Sie eine andere Seite im Browser öffnen oder den Browser schließen.

    Sie werden benachrichtigt, wenn der Vorgang erfolgreich abgeschlossen ist. Wenn der Vorgang nicht erfolgreich ist, gibt eine Fehlermeldung an, welche Probleme aufgetreten sind und wie Sie sie beheben können.

## <a name="best-practices-and-restrictions"></a>Bewährte Methoden und Einschränkungen
Beachten Sie beim Erstellen und Ändern von Feldern Folgendes:

* Sie können keine Systemfelder oder ihre Werte ändern oder löschen.
* In einer Standardentität können Sie kein Standardfeld ändern oder löschen, kein Feld hinzufügen, das Daten benötigt, und keine andere Änderung durchführen, die eine App beeinträchtigen könnte, die diese Entität verwendet.
* In einer benutzerdefinierten Entität sollten Sie sicherstellen, dass Ihre Änderungen keine App beeinträchtigen, die diese Entität verwendet.
* Geben Sie allen benutzerdefinierten Feldern eindeutige Namen innerhalb der Entität. Felder können nicht umbenannt werden, nachdem sie erstellt wurden.

## <a name="next-steps"></a>Nächste Schritte
* [Definieren von Beziehungen zwischen Entitäten](data-platform-entity-lookup.md)
* [Create a business rule (Erstellen einer Geschäftsregel)](data-platform-create-business-rule.md)
* [Erstellen einer App mithilfe von Entitäten](../canvas-apps/data-platform-create-app.md)
* [Create an app from scratch using a Common Data Service database (Erstellen einer App von Grund auf neu mithilfe einer Common Data Service-Datenbank)](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

