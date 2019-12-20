---
title: Erstellen einer benutzerdefinierten Entität | Microsoft Docs
description: Weitere Informationen zum Erstellen einer benutzerdefinierten Entität in Power Apps.
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
ms.openlocfilehash: e24249573f6c7e56ff16de6808e2423acbf3c0cf
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884186"
---
# <a name="create-a-custom-entity"></a>Benutzerdefinierte Entität erstellen
In Power Apps definiert eine *Entität* Informationen, die Sie in Form von Datensätzen nachverfolgen möchten, die normalerweise Eigenschaften wie Firmenname, Standort, Produkte, E-Mail und Telefon umfassen. Sie können dann diese Daten dann aufrufen, indem Sie eine App entwickeln, die auf diese Entität verweist. Power Apps bietet integrierte Standardentitäten für typische Szenarien in einer Organisation (z. B. das Nachverfolgen von Terminen), doch es gibt möglicherweise Zeiten, in denen Sie benutzerdefinierte Entitäten zum Speichern von Daten erstellen müssen, die spezifisch für Ihre Organisation sind.

In diesem Thema erfahren Sie, wie Sie eine benutzerdefinierte Entität namens "Produktbewertung" erstellen, mit der eine App erstellen können, die Bewertungen und Kommentare für Produkte anzeigt, die Ihr Unternehmen vertreibt.

## <a name="prerequisites"></a>Voraussetzungen
Für dieses Verfahren müssen Sie über eine Systemadministrator- oder Systemanpasser-Sicherheitsrolle in Common Data Service verfügen.

## <a name="sign-in-to-power-apps"></a>Bei Power Apps anmelden
Melden Sie sich bei Power Apps unter [https://make.powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

## <a name="create-an-entity"></a>Entität erstellen
1. Klicken oder tippen Sie im Navigationsbereich auf **Daten**, um sie zu erweitern, und klicken oder tippen Sie dann auf **Entitäten**.

    ![Liste der Entitäten und ihrer Details](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. klicken oder tippen Sie in der Befehlsleiste auf **Neue Entität**.

    Bevor Sie eine Entität erstellen, sehen Sie sich die [Entitätsreferenz](../../developer/common-data-service/reference/about-entity-reference.md) an, um eine Beschreibung der verfügbaren Standardentitäten zu erhalten. Diese Entitäten decken typische Szenarien ab. Wenn eine dieser Entitäten Ihre Bedingungen so wie sie ist oder nach geringfügigen Änderungen erfüllt, können Sie Zeit sparen, indem Sie mit dieser Entität beginnen. 

3. Führen Sie im Bereich **Neue Entität** die folgenden Schritte aus:

    a. Geben Sie im Feld **Anzeigename** **Produktbewertung** ein.

    Beachten Sie, dass die folgenden Felder automatisch aufgefüllt werden, wenn Sie einen Anzeigenamen eingeben:

    * **Pluralanzeigename** - Dieses Feld wird automatisch befüllt, wenn Sie einen Anzeigenamen eingeben, aber Sie können ihn nach Bedarf ändern. Der Pluralanzeigename ist der Entitätsname in der Common Data Service-WebAPI und wird beim Interagieren mit dieser Entität aus Power Apps oder Flow verwendet.
    * **Name** - Dieses Feld wird auch automatisch befüllt, wenn Sie einen Anzeigenamen eingeben. Das Präfix wurde eingerichtet, als die Umgebung erstellt wurde. es stellt sicher, dass die Entitäten, die Sie erstellen, ohne Konflikte mit anderen Entitätsnamen aus und in andere Umgebungen exportiert und importiert werden können. Sie können dieses Präfix ändern, indem Sie das Präfix in Ihrem Herausgeber für die Standardlösung von Common Data Service aktualisieren. Damit vorhandene Apps nicht beschädigt werden, können Sie den Namen nach der Speicherung der Entität nicht mehr ändern.

       > [!NOTE]
       > Damit der Entitätsname zusammen mit der in [Dynamics 365 for Customer Service eingebundenen Wissenssuche funktioniert](/dynamics365/customer-engagement/customer-service/set-up-knowledge-management-embedded-knowledge-search), darf der Entitätsname einschließlich Herausgeberpräfix nicht länger als 24 Zeichen sein.

    b. Ersetzen Sie im Abschnitt **Hauptfeld** im Feld **Anzeigename** **Name** durch **Produktbewertung**. 

    Standardmäßig enthält jede Entität ein **Hauptfeld**, das von Suchfeldern verwendet wird, wenn Beziehungen mit anderen Entitäten eingerichtet werden. Normalerweise werden im Hauptfeld die Namen oder die primäre Beschreibung der in der Entität gespeicherten Daten gespeichert. Sie können den Namen und den Anzeigenamen des Hauptfelds aktualisieren, bevor Sie die Entität zum ersten Mal speichern.

    Beachten Sie auch, dass das Hauptfeld auch ein eigenes Feld für **Name** enthält, das auf ähnliche Weise wie der Entitätsname funktioniert, der oben beschrieben wird. Der Name des Hauptfelds wird automatisch voraufgefüllt, wenn ein Anzeigename eingegeben wurde, verwendet dasselbe Präfix wie die Entität und kann nicht mehr geändert werden, nachdem die Entität erstellt wurde.

    c. Öffnen Sie den Abschnitt **Weitere Einstellungen**, und erweitern Sie das **Beschreibung**-Akkordeon. Sie können eine Beschreibung für die Entität eingeben, wenn Sie möchten (Beschreibungen sind nützlich, wenn andere Personen diese Entität verwenden). 
    
    d. Klicken Sie auf **Erstellen**, wenn Sie fertig sind.
     
    ![Neue Entität](./media/data-platform-cds-create-entity/newentitypanel.png "Neuer Entitätsbereich")

4. Beachten Sie, dass auf der Entitätsdetailseite die Entität noch im Hintergrund bereitgestellt wird. Nachdem die Bereitstellung abgeschlossen wurde, wird die Entität gespeichert und kann in Apps verwendet werden. Felder, Beziehungen und Schlüssel können der Entität jederzeit hinzugefügt werden (auch wenn die Bereitstellung noch ausgeführt wird), aber Ansichten, Formulare, Diagramme, Dashboards und Geschäftsregeln können nur zur Entität hinzugefügt werden, nachdem die Bereitstellung abgeschlossen ist.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/newentitydetails.png "Neue Entitätsdetails")

5. Beachten Sie unter der **Felder**-Registerkarte das **Hauptfeld**, das Sie im vorherigen Schritt benannt haben. Klicken oder tippen Sie auf das Feld **Hauptfeld**, um den Bereich **Hauptfeld** zu öffnen, falls Sie in dem Feld weitere Anpassungen vornehmen möchten. Beachten Sie, dass der **Name** nicht mehr geändert werden kann, da die Entität bereits gespeichert wurde.

5. Zum Hinzufügen eines Felds zur Entität führen Sie folgende Schritte aus:
 
    a. In der Befehlsleiste klicken oder tippen Sie auf **Feld hinzufügen**, um den Bereich **Feldeigenschaften** zu öffnen.

    b. Geben Sie im Feld **Anzeigename** **Überprüfungsdatum** ein.

    c. Wählen Sie aus der **Datumstyp**-Dropdownliste **Nur Datum** aus.

    d. Klicken oder tippen Sie auf das Kontrollkästchen **Erforderlich**.
    
    e. Klicken oder tippen Sie auf **Fertig**.
     
    Weitere Informationen finden Sie unter [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md).

    > [!div class="mx-imgBorder"] 
    > ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Neuer Feldbereich")

6. Wiederholen Sie den vorherigen Schritt, um drei weitere Felder mit folgenden Konfigurationen hinzuzufügen:
    * **Anzeigename** = Produkt-Bewertung; **Datentyp** = " Ganze Zahl "; klicken oder tippen Sie auf das **Erforderlich**- Kontrollkästchen
    * **Anzeigename** = Prüfername; **Datentyp** = Text
    * **Anzeigename** = Prüferkommentar; **Datentyp** = Text

    Wenn Sie fertig sind, sollten Sie über fünf Felder verfügen, die auf der Entitätsdetailseite aufgeführt sind.

    ![Felderliste](./media/data-platform-cds-create-entity/addedfields.png "Liste der Felder")

    Beachten Sie, dass alle Entitäten schreibgeschützte Systemfelder haben. Systemfelder werden standardmäßig nicht in der Liste der Felder angezeigt, obwohl sie in die Entität vorhanden sind. Um alle Felder anzuzeigen, ändern Sie den Filter in der Befehlsleiste von **Standard** auf **Alle**. Weitere Informationen zu den Metadaten, die sich auf eine Entität beziehen, finden Sie unter [Entitätsmetadaten](../../developer/common-data-service/entity-metadata.md).

7. Klicken Sie auf **Entität speichern**, um die letzten Änderungen Ihrer Entität zu speichern.

    Die Produktbewertungsentität sollte in der Liste der Entitäten in der Datenbank angezeigt werden. Wenn sie nicht angezeigt wird, ändern Sie den Filter in der Befehlsleiste von **Standard** auf **Benutzerdefiniert**.

    > [!div class="mx-imgBorder"] 
    > ![Filter](./media/data-platform-cds-create-entity/filter.png "Filterauswahl")

## <a name="next-steps"></a>Nächste Schritte
In diesem Thema haben Sie erfahren, wie Sie eine benutzerdefinierte Entität namens "Produktbewertung" erstellen, mit der Sie eine App erstellen können, die Bewertungen und Kommentare für jedes Produkte anzeigt, das Ihr Unternehmen vertreibt. Anschließend erfahren Sie, wie Sie Beziehungen zwischen Entitäten (in diesem Fall die Standardproduktentität und Ihre benutzerdefinierte Produktbewertungsentität) definiert werden, sodass Sie jedes Produkt den Bewertungen und Kommentaren zuordnen können, die es erhält.

> [!div class="nextstepaction"]
> [Erstellen einer Beziehung](data-platform-entity-lookup.md)

## <a name="privacy-notice"></a>Datenschutzbestimmungen
Mit dem allgemeinen Datenmodell von Microsoft Power Apps sammelt und speichert Microsoft benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen. Wir verwenden diese Informationen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die von App-Erstellern erstellt werden, helfen uns dabei, Szenarien zu verstehen, die in der Microsoft Power Apps-Community üblich sind, und Lücken bei den Standardentitäten des Service festzustellen, z. B. Schemas bezüglich der Organisationen. Die Daten in den Datenbanktabellen, die mit diesen Entitäten verknüpft werden, werden von Microsoft nicht verwendet, es wird nicht darauf zugegriffen und sie werden nicht außerhalb der Region, in der die Datenbank bereitgestellt wird, repliziert. Beachten Sie jedoch, dass die benutzerdefinierte Entität und die Feldnamen möglicherweise in Regionen repliziert werden und in Übereinstimmung mit unseren Richtlinien zur Datenaufbewahrung gelöscht werden. Microsoft legt großen Wert auf Ihren Datenschutz, wie weiter unten in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.
