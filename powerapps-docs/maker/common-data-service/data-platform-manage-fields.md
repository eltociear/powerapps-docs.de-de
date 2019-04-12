---
title: Verwalten von benutzerdefinierten Feldern in einer Entität | Microsoft Docs
description: 'Exemplarische Vorgehensweise zum Erstellen, Lesen, Aktualisieren und Löschen benutzerdefinierter Felder in einer Entität Common Data Service.'
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="manage-custom-fields-in-an-entity"></a>Verwalten von benutzerdefinierten Feldern in einer Entität
Sie können eine oder mehrere benutzerdefinierte Felder in einer beliebigen Entität erstellen und aktualisieren. Wenn Sie ein benutzerdefiniertes Feld erstellen, geben Sie einen Satz Eigenschaften an, beispielsweise den Feldnamen, den Anzeigenamen und den Datentyp, den es enthält. Weitere Informationen finden Sie unter [Metadaten von Entitätsattributen](../../developer/common-data-service/entity-attribute-metadata.md).

> [!NOTE]
> Jede Entität besitzt Systemfelder Felder, wie Felder, die angeben, wann ein Datensatz zuletzt aktualisiert wurde und wer ihn aktualisiert hat. Außerdem haben Standardentitäten Standardfelder. Sie können keine Systemfelder oder Standardfelder ändern oder löschen. Wenn Sie ein benutzerdefiniertes Feld erstellen, sollte es Funktionen auf Grundlage dieser integrierten Felder bereitstellen.

## <a name="create-a-field"></a>Erstellen Sie ein neues Feld
1. Auf [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Fügen Sie Ihrer Entität ein neues Feld hinzu, indem Sie auf **Feld hinzufügen** klicken.

4. Geben Sie im Bereich "Neues Feld" den **Anzeigename** für Ihr Feld ein. **Name** wird automatisch aufgefüllt und als eindeutiger Name für Ihr Feld verwendet. Der **Anzeigename** wird verwendet, wenn dieses Feld Ihren Benutzern angezeigt wird, der **Name** wird in Ausdrücken und Formeln verwendet, wenn Sie Ihre App erstellen in.

    > [!NOTE]
    > Die **Anzeigename**-Felder können jederzeit aktualisiert werden, um in Ihren Apps unterschiedlich angezeigt zu werden. Das **Name**-Feld kann nicht geändert werden, nachdem die Entität gespeichert wurde, da dadurch eine vorhandenen App beschädigt werden könnte.

    > [!div class="mx-imgBorder"] 
    > ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel.png "Bereich \"Neues Feld\"")

5. Wählen Sie den **Datentyp** Ihres Felds aus. Damit wird die Methode gesteuert, mit der die Informationen gespeichert werden und wie sie in den Apps dargestellt werden. Beispielsweise wird Text bei einer Dezimalzahl oder einer URL anders gespeichert. Ausführlichere Informationen zu den Datentypen finden Sie unter [Metadaten der Entitätsattribute](../../developer/common-data-service/entity-attribute-metadata.md).

    Wenn Sie aufgefordert werden, geben Sie zusätzliche Informationen für den Datentyp an, den Sie angegeben haben. Je nach Datentyp werden verschiedene Felder angezeigt. Wenn Sie ein Feld vom Typ "Optionssatz" oder "Mehrfachauswahl-Optionssatz" erstellen, können Sie **Neuer Optionssatz** auswählen und beim Erstellen des Felds einen neuen Optionssatz erstellen. Weitere Informationen finden Sie unter [Erstellen eines Optionssatzes](custom-picklists.md).

    > [!div class="mx-imgBorder"] 
    > ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Bereich \"Neues Feld\"")


7. Aktivieren Sie unter **Erforderlich** das Kontrollkästchen, wenn Sie dieses empfohlene Feld in Ihren Apps zu einem erforderlichen Feld machen möchten. Damit wird keine harte Erzwingung über alle Verbindungen des Common Data Service bereitgestellt. Wenn Sie sicherstellen möchten, dass das Feld aufgefüllt wird, erstellen Sie eine [Geschäftsregel](data-platform-create-business-rule.md)

8. Aktivieren Sie unter **Durchsuchbar** das Kontrollkästchen, wenn dieses Feld in Ansichten, Diagrammen, Dashboards und der erweiterten Suche verfügbar sein muss. In den meisten Fällen sollte dieses Kontrollkästchen überprüft werden.

9. Klicken oder tippen Sie auf **Fertig**, um den Feldbereich zu schließen und zur Entität zurückzukehren. Sie können Schritte 3-9 für jedes zusätzliche Feld wiederholen.
   
    > [!IMPORTANT]
    > Das Feld ist noch nicht gespeichert und erstellt, bis Sie die Änderungen an der Entität speichern.

10. Klicken oder tippen Sie auf **Entität speichern**, um die Änderungen abzuschließen und im Common Data Service zu speichern.

    Sie werden benachrichtigt, wenn der Vorgang erfolgreich abgeschlossen wurde. Wenn der Vorgang nicht erfolgreich ist, gibt eine Fehlermeldung die Probleme an, die aufgetreten sind, und wie Sie sie beheben können.

## <a name="create-a-calculated-or-roll-up-field"></a>Erstellen eines berechneten Felds oder Rollupfelds
Mit berechneten Feldern können Sie manuelle Berechnungen automatisieren, die in Ihren Geschäftsprozessen verwendet werden. Beispielsweise möchte ein Vertriebsmitarbeiter möglicherweise den gewichteten Umsatzes für eine Verkaufschance kennen, die auf dem geschätzten Umsatz einer Verkaufschance multipliziert mit der Wahrscheinlichkeit basiert. Oder er möchte automatisch einen Rabatt anwenden, wenn der Auftrag größer als $500 ist. Ein berechnetes Feld kann Werte enthalten, die sich aus einfachen Berechnungen ergeben, z. B. bedingte Operationen, wie größer als oder If-Else und viele andere. Berechnete Felder können mit den folgenden Datentypen erstellt werden:

* Einzelne Textzeile
* Optionssatz
* Zwei Optionen
* Ganze Zahl
* Dezimalzahl
* Währung
* Datum und Uhrzeit

Weitere Details zu den unterstützten Ausdruckstypen und Beispielen finden Sie unter [Definieren berechneter Felder](/dynamics365/customer-engagement/customize/define-calculated-fields)

## <a name="update-or-delete-a-field"></a>Aktualisieren oder Löschen eines Felds
1. Auf [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**. Klicken oder tippen Sie dann auf eine Entität.
2. In der Liste der Felder für die Entität, die Sie ausgewählt haben, klicken oder tippen Sie auf ein Feld, und folgen Sie dann einem dieser Schritte:
   
   * Ändern Sie mindestens eine Feldeigenschaft.
   * Löschen Sie das Feld, indem Sie auf die Auslassungspunkte (...) neben dem rechten Rand das Felds klicken oder tippen und auf **Löschen** klicken oder tippen.

3. Klicken oder tippen Sie auf **Entität speichern**, um die Änderungen zu senden.
   
    > [!IMPORTANT]
    > Ihre Änderungen gehen verloren, wenn Sie sie nicht speichern, bevor Sie eine andere Seite im Browser öffnen oder den Browser beenden.

    Sie werden benachrichtigt, wenn der Vorgang erfolgreich abgeschlossen wurde. Wenn der Vorgang nicht erfolgreich ist, gibt eine Fehlermeldung die Probleme an, die aufgetreten sind, und wie Sie sie beheben können.

## <a name="best-practices-and-restrictions"></a>Bewährte Methoden und Einschränkungen
Beachten Sie beim Erstellen und Ändern von Feldern folgende Punkte:

* Sie können keine Systemfelder oder deren Werte ändern oder löschen.
* In einer Standardentität können Sie ein Standardfeld nicht ändern oder löschen, kein Feld hinzufügen, das Daten benötigt, oder eine andere Änderung vornehmen, die unter Umständen eine App beschädigen, die auf die betreffenden Entität angewiesen ist.
* In einer benutzerdefinierten Entität sollten Sie sicherstellen, dass die Änderungen, die Sie vornehmen, keine App beschädigen, die auf die betreffenden Entität angewiesen ist.
* Sie müssen jedem benutzerdefinierten Feld einen Namen geben, der in der Entität eindeutig ist, und Sie können ein Feld nicht umbenennen, nachdem Sie es erstellt haben.

## <a name="next-steps"></a>Nächste Schritte
* [Beziehungen zwischen Entitäten definierten](data-platform-entity-lookup.md)
* [Geschäftsregel formulieren](data-platform-create-business-rule.md)
* [Erstellen einer App mit Entitäten](../canvas-apps/data-platform-create-app.md)
* [Erstellen einer App von Grund auf einer Common Data Service-Datenbank](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Datenschutzbestimmungen
Mit dem allgemeinen Datenmodell vom Microsoft PowerApps sammeln und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden diese Informationen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die von Erstellern erstellt werden, helfen uns dabei, Szenarien zu verstehen, die in der Microsoft PowerApps Community üblich sind, und Lücken bei den Standardentitäten des Service festzustellen, z. B. Schemas bezüglich der Organisationen. Die Daten in den Datenbanktabellen, die mit diesen Entitäten verknüpft werden, werden von Microsoft nicht verwendet, es wird nicht darauf zugegriffen und sie werden nicht außerhalb der Region, in der die Datenbank bereitgestellt wird, repliziert. Beachten Sie jedoch, dass die benutzerdefinierte Entität und die Feldnamen möglicherweise in Regionen repliziert werden und in Übereinstimmung mit unseren Richtlinien zur Datenaufbewahrung gelöscht werden. Microsoft legt großen Wert auf Ihren Datenschutz, wie weiter unten in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

