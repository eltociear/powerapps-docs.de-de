---
title: Erstellen einer benutzerdefinierten Entität | Microsoft Docs
description: 'Erfahren Sie, wie Sie eine benutzereigene Entität in PowerApps zu erstellen.'
author: Mattp123
ms.service: powerapps
ms.component: cds
ms.topic: quickstart
ms.date: 05/01/2018
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-a-custom-entity"></a>Erstellen einer benutzerdefinierten Entität.
In PowerApps definiert eine *Entität* Informationen, die Sie in Form von Datensätzen nachverfolgen möchten, die normalerweise Eigenschaften wie Firmenname, Standort, Produkte, E-Mail und Telefon umfassen. Sie können dann diese Daten dann aufrufen, indem Sie eine App entwickeln, die auf diese Entität verweist. PowerApps bietet integrierte Standardentitäten für typische Szenarien in einer Organisation (z. B. das Nachverfolgen von Terminen), doch es gibt möglicherweise Zeiten, in denen Sie benutzerdefinierte Entitäten zum Speichern von Daten erstellen müssen, die spezifisch für Ihre Organisation sind.

In diesem Thema erfahren Sie, wie Sie eine benutzerdefinierte Entität namens "Produktbewertung" erstellen, mit der eine App erstellen können, die Bewertungen und Kommentare für Produkte anzeigt, die Ihr Unternehmen vertreibt.

## <a name="prerequisites"></a>Voraussetzungen
Um dieser Vorgehensweise zu folgen, sind die folgenden Elemente erforderlich:
* Entweder ein PowerApps-Plan 2 oder eine Microsoft Flow Plan 2-Lizenz. Alternativ können Sie sich für eine [kostenlose Testversion von PowerApps Plan 2](https://web.powerapps.com/signup?redirect=marketing&email=) registrieren.
* Entweder eine Systemadministrator- oder eine Systemanpasser-Sicherheitsrolle in Common Data Service for Apps.

## <a name="sign-in-to-powerapps"></a>Bei PowerApps anmelden
Unter [https://web.powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) bei PowerApps anmelden.

## <a name="create-an-entity"></a>Erstellen einer Entität
1. Klicken oder tippen Sie im Navigationsbereich auf **Daten**, um sie zu erweitern, und klicken oder tippen Sie dann auf **Entitäten**.

    ![Liste der Entitäten und ihrer Details](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. klicken oder tippen Sie in der Befehlsleiste auf **Neue Entität**.

    Bevor Sie eine Entität erstellen, sehen Sie sich die [Entitätsreferenz](../../developer/common-data-service/reference/about-entity-reference.md) an, um eine Beschreibung der verfügbaren Standardentitäten zu erhalten. Diese Entitäten decken typische Szenarien ab. Wenn eine dieser Entitäten Ihre Bedingungen so wie sie ist oder nach geringfügigen Änderungen erfüllt, können Sie Zeit sparen, indem Sie mit dieser Entität beginnen. 

3. Geben Sie im Bereich **Neue Entität** im Feld **Anzeigename** **Produktbewertung** ein, und geben Sie anschließend optional eine Beschreibung ein (Beschreibungen sind nützlich, wenn andere Personen diese Entität verwenden werden). Die anderen Felder im Bereich werden automatisch wie unten beschrieben befüllt. Klicken Sie auf **Weiter**, wenn Sie fertig sind.

    * **Pluralanzeigename** - Dieses Feld wird automatisch befüllt, wenn Sie einen Anzeigenamen eingeben, aber Sie können ihn nach Bedarf ändern. Der Pluralanzeigename ist der Entitätsname in der Common Data Service WebAPI und wird beim Interagieren mit dieser Entität aus PowerApps oder Flow verwendet.
    * **Name** - Dieses Feld wird auch automatisch befüllt, wenn Sie einen Anzeigenamen eingeben. Das Präfix wurde eingerichtet, als die Umgebung erstellt wurde. es stellt sicher, dass die Entitäten, die Sie erstellen, ohne Konflikte mit anderen Entitätsnamen aus und in andere Umgebungen exportiert und importiert werden können. Sie können dieses Präfix ändern, indem Sie das Präfix in Ihrem Herausgeber Standardlösung von Common Data Service aktualisieren. Damit vorhandene Apps nicht beschädigt werden, können Sie den Namen nach der Speicherung der Entität nicht mehr ändern.

       > [!NOTE]
       > Damit der Entitätsname mit [Dynamics 365 for Customer Service-Integrierte Wissenssuche](/dynamics365/customer-engagement/customer-service/set-up-knowledge-management-embedded-knowledge-search) funktioniert, darf die maximale Länge des Entitätsnamens einschließlich des Publisher-Präfixes 24 Zeichen nicht überschreiten.
     
    ![Neue Entität](./media/data-platform-cds-create-entity/newentitypanel.png "Neuer Entitätsbereich")

4. Auf der Entitätsdetailseite klicken oder tippen Sie auf das Feld **Primärer Name**, um den Bereich **Primärer Name** zu öffnen, und dann ersetzen Sie im Feld **Anzeigename** **Primärer Name** mit **Produktbewertung**. Im Feld **Name** ersetzen Sie **PrimaryName** mit **ProductReview**, und klicken oder tippen dann auf **Fertig**.
 
    Standardmäßig enthält jede Entität ein Feld für den primären Namen, der von Suchfeldern verwendet wird, wenn Beziehungen mit anderen Entitäten eingerichtet werden. Normalerweise werden im Feld primärer Name die Namen oder die primäre Beschreibung der in der Entität gespeicherten Daten gespeichert. Sie können den Namen und den Anzeigenamen des Felds Primärer Name aktualisieren , bevor Sie die Entität zum ersten Mal speichern.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/newentitydetails.png "Neue Entitätsdetails")

5. Zum Hinzufügen eines Felds zur Entität führen Sie folgende Schritte aus:
 
    a. In der Befehlsleiste klicken oder tippen Sie auf **Feld hinzufügen**, um den Bereich **Feldeigenschaften** zu öffnen.

    b. Geben Sie im Feld **Anzeigename** **Überprüfungsdatum** ein.

    c. Wählen Sie aus der **Datumstyp**-Dropdownliste **Nur Datum** aus.

    d. Klicken oder tippen Sie auf das Kontrollkästchen **Erforderlich**.
    
    e. Klicken oder tippen Sie auf **Fertig**.
     
    Weitere Informationen finden Sie unter [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md).

    > [!div class="mx-imgBorder"] 
    > ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Bereich \"Neues Feld\"")

6. Wiederholen Sie den vorherigen Schritt, um drei weitere Felder mit folgenden Konfigurationen hinzuzufügen:
    * **Anzeigename** = Produkt-Bewertung; **Datentyp** = " Ganze Zahl "; klicken oder tippen Sie auf das **Erforderlich**- Kontrollkästchen
    * **Anzeigename** = Prüfername; **Datentyp** = Text
    * **Anzeigename** = Prüferkommentar; **Datentyp** = Text

    Wenn Sie fertig sind, sollten Sie über fünf Felder verfügen, die auf der Entitätsdetailseite aufgeführt sind.

    ![Feldliste](./media/data-platform-cds-create-entity/addedfields.png "Liste der Felder")

    Beachten Sie, dass alle Entitäten schreibgeschützte Systemfelder haben. Systemfelder werden standardmäßig nicht in der Liste der Felder angezeigt, obwohl sie in die Entität vorhanden sind. Um alle Felder anzuzeigen, ändern Sie den Filter in der Befehlsleiste von **Standard** auf **Alle**. Weitere Informationen zu den Metadaten, die sich auf eine Entität beziehen, finden Sie unter [Entitätsmetadaten](../../developer/common-data-service/entity-metadata.md).

7. Klicken Sie auf **Entität speichern**, um die Entität zu speichern und geben Sie sie dann zur Verwendung in Apps frei.

    Die Produktbewertungsentität sollte in der Liste der Entitäten in der Datenbank angezeigt werden. Wenn sie nicht angezeigt wird, ändern Sie den Filter in der Befehlsleiste von **Standard** auf **Benutzerdefiniert**.

    > [!div class="mx-imgBorder"] 
    > ![Filter](./media/data-platform-cds-create-entity/filter.png "Filterauswahl")

## <a name="next-steps"></a>Nächste Schritte
In diesem Thema haben Sie erfahren, wie Sie eine benutzerdefinierte Entität namens "Produktbewertung" erstellen, mit der Sie eine App erstellen können, die Bewertungen und Kommentare für jedes Produkte anzeigt, das Ihr Unternehmen vertreibt. Anschließend erfahren Sie, wie Sie Beziehungen zwischen Entitäten (in diesem Fall die Standardproduktentität und Ihre benutzerdefinierte Produktbewertungsentität) definiert werden, sodass Sie jedes Produkt den Bewertungen und Kommentaren zuordnen können, die es erhält.

> [!div class="nextstepaction"]
> [Erstellen einer Beziehung](data-platform-entity-lookup.md)

## <a name="privacy-notice"></a>Datenschutzbestimmungen
Mit dem allgemeinen Datenmodell vom Microsoft PowerApps sammelt und speichert Microsoft benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen. Wir verwenden diese Informationen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die von App-Erstellern erstellt werden, helfen uns dabei, Szenarien zu verstehen, die in der Microsoft PowerApps Community üblich sind, und Lücken bei den Standardentitäten des Service festzustellen, z. B. Schemas bezüglich der Organisationen. Die Daten in den Datenbanktabellen, die mit diesen Entitäten verknüpft werden, werden von Microsoft nicht verwendet, es wird nicht darauf zugegriffen und sie werden nicht außerhalb der Region, in der die Datenbank bereitgestellt wird, repliziert. Beachten Sie jedoch, dass die benutzerdefinierte Entität und die Feldnamen möglicherweise in Regionen repliziert werden und in Übereinstimmung mit unseren Richtlinien zur Datenaufbewahrung gelöscht werden. Microsoft legt großen Wert auf Ihren Datenschutz, wie weiter unten in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.
