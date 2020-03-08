---
title: Upgrade für die Verwendung von System eigenem Common Data Service-Connector | Microsoft-Dokumentation
description: ''
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e77bf1304ac7d1083348dce18d7d78189dfef306
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845374"
---
# <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service und die verbesserte Datenquelle

## <a name="overview"></a>Übersicht

Wenn Sie vor dem 2019. November eine Canvas-App mit einem Common Data Service-Connector erstellt haben, haben Sie möglicherweise keinen Vorteil von der aktuellen Version des Common Data Service. 

Die Option **Datenquellen-und Common Data Service Ansichten verbessern** bietet folgende Vorteile:

1. Beträchtliche Geschwindigkeit bei der Geschwindigkeit.
2. Höhere Zuverlässigkeit.
3. Zugriff auf Common Data Service **Ansichten** und **Datei-und Bild Feld Attribute**.

Die Option **Datenquellen Umgebung verbessern und Common Data Service Sichten** wird im Abschnitt Erweiterte Einstellungen angezeigt:

![Verbessern der Datenquellen Darstellung und Common Data Service Ansichten](media/use-native-cds-connector/improved-data-source-setting.png)

Die **relationalen Daten, Optionssätze und anderen neuen Features für Common Data Service** werden jetzt im Abschnitt veraltete Features angezeigt.

## <a name="how-do-i-upgrade"></a>Gewusst wie Upgrade?

Führen Sie ein Upgrade Ihrer APP durch, indem Sie die Einstellungen der Features überprüfen und anschließend die folgenden Anweisungen befolgen:

### <a name="improve-data-source-experience-and-common-data-service-views-is-on"></a>*Verbessern Sie die Datenquellen Leistung, und Common Data Service Ansichten* ist in:

Entweder haben Sie Ihre Canvas-App bereits für die Verwendung dieses Features konvertiert, oder Sie haben eine APP mit der Standardeinstellung *on* für dieses Feature gestartet. Es sind keine weiteren Aktionen erforderlich. 

Möglicherweise möchten Sie auch die **explizite Spaltenauswahl** aktivieren:

![Explizite Spaltenauswahl](media/use-native-cds-connector/explicit-column-selection.png)

> [!NOTE]
> **Verbessern der Datenquellen Darstellung und Common Data Service Sichten** werden in [powerapps für Windows](https://www.microsoft.com/p/power-apps/9nblggh5z8f3)nicht unterstützt. Sie müssen *Diese Funktion deaktivieren* , wenn Sie powerapps für Windows verwenden.

### <a name="relational-data-option-sets-and-other-new-features-for-common-data-service-is-off"></a>*Relationale Daten, Optionssätze und andere neue Features für Common Data Service* sind deaktiviert:

Überprüfen Sie den Abschnitt mit den *veralteten Features* unter *Erweiterte Einstellungen*.  Wenn diese Einstellung auf *Off*festgelegt ist, fahren Sie mit den folgenden Anweisungen als ersten Schritt der Konvertierung fort. 

> [!IMPORTANT]
> Wenn Sie keine **relationalen Daten, Optionssätze und anderen neuen Features für Common Data Service** in den *erweiterten Einstellungen*sehen oder bereits aktiviert sind, *über*springen Sie die folgenden Schritte, und fahren Sie mit dem [nächsten Abschnitt](#improve-data-source-experience-and-common-data-service-views-is-off)fort.

- **Schritt 1**: Aktivieren Sie die Funktion " **anzeigen Amen verwenden** " **auf**:
    
    1. Aktivieren Sie die Funktion *zum Verwenden von* **anzeigen Amen** .
    1. Warten Sie, bis der Integritäts Monitor die Analyse Ihrer APP abgeschlossen hat.
    1. Speichern, schließen und öffnen Sie Ihre APP erneut.
    1. Beheben Sie alle Formel Fehler.
    1. Speichern, schließen und öffnen Sie Ihre APP erneut.
    
    *Mögliche Fehler und Vorschläge*:
    
    Es ist möglich, dass einige der neu gezeigten anzeigen Amen mit den anzeigen Amen anderer Entitäten, Felder oder Steuerelemente in Konflikt stehen können. Beispielsweise können Sie über ein-Steuerelement und ein-Feld mit demselben Namen verfügen. Sie können den Namen des Steuer Elements mit einem eindeutigen Wert ändern, um ihn zu korrigieren.
    
    Bei einem Konflikt zwischen Feld und Entitäts Anzeige Name wird möglicherweise eine Formel angezeigt, die eine Entität erwartet, jedoch in einen lokal Bereichs bezogenen Feldnamen aufgelöst wird.

    Verwenden Sie die eckige Klammer mit einem **@** Symbol, um einen globalen Bereich anzugeben, sodass er in die Entität aufgelöst wird. Beispiel: **[@entityName]** .
    
    
- **Schritt 2**: **Aktivieren von relationalen Daten, Options Sätzen und anderen neuen Features für Common Data Service** und **Verwenden von GUID-Datentypen anstelle von** Zeichen folgen Funktionen **in**:
    
    1. **Aktivieren Sie relationale Daten, Optionssätze und andere neue Features für Common Data Service-** Funktion *auf*.
    1. Aktivieren Sie *die Funktion* **GUID-Datentypen anstelle von** Zeichen folgen verwenden.
    1. Warten Sie, bis der Integritäts Monitor die Analyse Ihrer APP abgeschlossen hat.
    1. Beheben Sie alle Formel Fehler.
    1. Speichern, schließen und öffnen Sie Ihre APP erneut.  
    
    *Mögliche Fehler und Vorschläge*:
    
    Wenn Sie ein Optionsfeld oder einen hart codierten GUID-Textwert verwenden, sind in dieser Phase möglicherweise Fehler aufgetreten.  <br><br> 
    
    - *Options Satz Werte*: Wenn Sie ein Options Satz Feld mit einem Text Bezeichner für den Options Satz Wert verwenden, verwenden Sie stattdessen die Punkt Notation, um auf den Options Satz Wert zu verweisen. Ändern Sie beispielsweise `Patch(Accounts, OptionSet1 = “12345”)` in `Patch(Accounts, OptionSet.Item1)`, wobei `Item1` dem `12345` Wert entspricht. <br>
    Weitere Informationen finden Sie im Abschnitt [ausführliche Beispiele](#detailed-examples) .
    - *GUIDs*: Wenn Sie eine statische GUID-Zeichenfolge wie z. b. `015e45e1044e49f388115be07f2ee116`verwenden, konvertieren Sie Sie in eine Funktion, die ein GUID-Objekt zurückgibt. beispielsweise `GUID(“015e45e1044e49f388115be07f2ee116”)`. 
    - *Lookups*: Wenn Sie Suchfunktionen zum Abrufen von Such Werten der ersten Ebene verwenden, z. b. `Lookup(Contacts, ‘contactID’ = ThisItem.ContactID”)`, sollten Sie die Verwendung von `ThisItem.PrimaryContacts` in Erwägung nehmen (wobei primarycontacts der Name der Entität ist).

### <a name="improve-data-source-experience-and-common-data-service-views-is-off"></a>*Verbessern der Datenquellen Leistung und Common Data Service Ansichten* sind deaktiviert:

Verwenden Sie die folgende Anweisung, um die Funktion zum verbessern *von*Funktionen für **Datenquellen und Common Data Service Ansichten** zu aktivieren:

1. Entfernen Sie die vorhandenen Common Data Service Datenquellen Verbindungen. 
1. Aktivieren *Sie das Feature* **verbessern der Datenquellen Funktionen und Common Data Service Ansichten** .
1. Fügen Sie die Common Data Service Verbindung mithilfe der neuen Datenquellen Auswahl hinzu.
1. Speichern Sie die Anwendung.

> [!NOTE]
> Wenn Ihre Anwendung sehr groß ist, kann das Hinzufügen von Datenquellen Verbindungen einige Zeit in Anspruch nehmen. Schließen Sie die Anwendung während dieses Vorgangs nicht.

## <a name="converting-canvas-apps-with-the-dynamics-365-connector"></a>Umrechnen von Canvas-apps mit dem Dynamics 365-Connector

Zum Konvertieren Ihrer APP, die den Dynamics 365-Connector verwendet, müssen Sie die Verbindungen entfernen und den Datenquellen hinzufügen. Führen Sie die folgenden Schritte aus, um Ihre Verbindungen mit ihren Datenquellen zu konvertieren.

1. Stellen Sie sicher, dass die Funktion **Datenquellen-und Common Data Service Ansichten verbessern** *aktiviert ist*.
2. Entfernen Sie die vorhandenen Dynamics 365-Datenquellen Verbindungen.
3. Fügen Sie die Verbindungen mit den Datenquellen der Common Data Service mithilfe der neuen Datenquellen Auswahl hinzu. 

    > [!NOTE] 
    > Wenn Sie Verbindungen mit anderen Umgebungen (mit Ausnahme von Current) haben, wählen Sie die Kategorie *Entität* und dann die Option *Weitere* (...) aus, um die Umgebung zu ändern. Sie können dann eine Entität aus einer anderen Umgebung auswählen, die Sie der Anwendung hinzufügen möchten. Mandanten übergreifende Verbindungen funktionieren nicht mit dem verbesserten nativen Connector. Sie müssen die Datenintegration für den Mandanten übergreifenden Zugriff auf Daten verwenden.
4.  Speichern Sie die Anwendung.

*Mögliche Fehler und Vorschläge*:

Bei der Konvertierung können Fehler auftreten, wenn Sie keine anzeigen Amen verwenden, wenn Sie GUID-Zeichen folgen verwenden oder wenn Sie ein Optionsfeld Feld verwenden.

- Wenn der Name des Steuer Elements Konflikte verursacht, ändern Sie den Namen des Steuer Elements in einen anderen und einen eindeutigen Namen. 
- Bei Konflikten mit dem anzeigen Amen von Feldern und Entitäten wird möglicherweise eine Formel angezeigt, die eine Entität erwartet, aber in einen stärker lokal Bereichs bezogenen Feldnamen aufgelöst wird. Verwenden Sie die eckige Klammer mit einem *@* Symbol, um einen globalen Bereich anzugeben, sodass er in die Entität aufgelöst wird. Beispiel: **[@entityName]** .
- *Options Satz Werte*: Wenn Sie ein Options Satz Feld mit einem Text Bezeichner für den Options Satz Wert verwenden, verwenden Sie stattdessen die Punkt Notation, um auf den Options Satz Wert zu verweisen. Ändern Sie beispielsweise `Patch(Accounts, OptionSet1 = “12345”)` in `Patch(Accounts, OptionSet.Item1)`, wobei `Item1` dem `12345` Wert entspricht. <br>
Weitere Informationen finden Sie im Abschnitt [ausführliche Beispiele](#detailed-examples) .
- *GUIDs*: Wenn Sie eine statische GUID-Zeichenfolge wie z. b. `015e45e1044e49f388115be07f2ee116`verwenden, konvertieren Sie Sie in eine Funktion, die ein GUID-Objekt zurückgibt. beispielsweise `GUID(“015e45e1044e49f388115be07f2ee116”)`. 
- *Lookups*: Wenn Sie Suchfunktionen zum Abrufen von Such Werten der ersten Ebene verwenden, z. b. `Lookup(Contacts, ‘contactID’ = ThisItem.ContactID”)`, sollten Sie die Verwendung von `ThisItem.PrimaryContacts` in Erwägung nehmen (wobei primarycontacts der Name der Entität ist).
- Weitere polymorphe Verweise finden Sie unten im Abschnitt ausführliche Beispiele. 

## <a name="detailed-examples"></a>Ausführliche Beispiele

Die Umstellung Ihrer APP für die Verwendung der neuen **Optionssätze** und der **beiden Optionen** Datentypen mit unterstützenden Steuerelementen kann eine Herausforderung darstellen, während Sie ein Upgrade einer APP ausführen, um die neue Funktion für *verbesserte Datenquellen Funktionen und Common Data Service Ansichten*

### <a name="option-sets"></a>Optionssätze

Separate `_myfield` und `_myfield_label` Felder wurden für eine zuvor festgelegte Option verwendet. Nun gibt es ein einzelnes `myfield`, das sowohl für Gebiets Schema unabhängige Vergleiche als auch zum Abrufen der Gebiets Schema spezifischen Bezeichnung verwendet werden kann.

#### <a name="removing-and-adding-option-set-data-cards"></a>Entfernen und Hinzufügen von Options Satz-Datenkarten

Es wird empfohlen, vorhandene Datenkarten zu entfernen und Sie wieder hinzuzufügen, damit Sie mit dem Options Satz funktionieren. Wenn Sie z. b. mit der-Konto Entität arbeiten und die Kategorieoption festgelegt ist, werden Sie feststellen, dass die *Datin* -Eigenschaft der Datenkarte auf `_accountcategorycode_label`festgelegt wurde. In der Feldliste können Sie sehen, dass die Datenkarte den Typ " *String*" aufweist:

![OptionSET mit altem Stilnamen](./media/use-native-cds-connector/OptionSet-with-old-style-name.png)

Mit der neuen *verbesserten Funktion für Datenquellen Funktionen und Common Data Service Ansichten* wird `_accountcategorycode_label`nicht mehr angezeigt. Sie wird durch `accountcategorycode`ersetzt. Ihre Karte ist nun als **Benutzer** definiert gekennzeichnet, und es werden Fehler angezeigt. Entfernen Sie die alte Datenkarte, und fügen Sie die *Option* zurück. Die neue Datenkarte ist *options Satz* fähig.

![OptionSET mit altem Stilnamen](./media/use-native-cds-connector/OptionSet-with-new-style-name.png)

#### <a name="editing-the-option-set-filter-expressions-to-use-new-syntax"></a>Bearbeiten der Option festlegen von Filter Ausdrücken, um die neue Syntax zu verwenden

Wenn Sie zuvor einen Options Satz Wert in einem Filter Ausdruck verwenden möchten, müssen Sie das *Wertfeld* verwenden. Beispiel:

```powerapps-dot
Filter(Account,'Category Value' = "1")
```

Sie müssen diese Formel bearbeiten. Der Options Satz-textidentifer wird nicht mehr für den Wert verwendet. Dieser Ausdruck sollte aktualisiert werden, um Folgendes zu sehen:

```powerapps-dot
Filter(Account, Category= ‘Category (Accounts)’.’Preferred Customer’)
```

"Category (Accounts)" ist der Name der Enumeration, der im Feld "Category" der Entität "Accounts" verwendet wird. Dies ist ein lokaler Options Satz.  Weitere Informationen zu lokalen und globalen Options Sätzen finden Sie hier: [globale Optionssätze.](https://docs.microsoft.com/powerapps/maker/common-data-service/create-edit-global-option-sets)

#### <a name="editing-option-set-patch-statements-to-use-new-syntax"></a>Bearbeitungs Option festlegen von Patch-Anweisungen für die Verwendung der neuen Syntax

Im folgenden finden Sie ein Beispiel für eine frühere patchanweisung für options Satz:

```powerapps-dot
Patch( Accounts, First(Accounts), { ‘Category Value’: 1 } ) )
```

Sie müssen Ihre-Anweisungen aktualisieren, damit Sie dem folgenden Formular folgen:

```powerapps-dot
Patch( Accounts, First(Accounts), { Category: ‘Category (Accounts)’.’Preferred Customer’ } )
```

#### <a name="option-set-disambiguation"></a>Options Satz-Eindeutigkeit

Wenn der Anzeige Name eines Options Satz **Felds** und der Name des Options Satzes identisch sind, müssen Sie die Formel eindeutig machen. Um das Code Beispiel für die Konten Kategorie weiterhin verwenden zu können, impliziert der **@** , dass der Options Satz verwendet wird, nicht das-Feld.

```powerapps-dot
Filter(Accounts, 'Category Code' = [@’Category Code’].'Preferred Customer')
```

### <a name="two-options"></a>Zwei Optionen

#### <a name="removing-and-adding-two-option-set-data-cards"></a>Entfernen und Hinzufügen von zwei Options Satz-Datenkarten

Entfernen Sie vorhandene Datenkarten, und fügen Sie Sie wieder hinzu, damit Sie mit den beiden Optionen festgelegt werden. Die Datentypen wurden früher als einfacher boolescher Wert erkannt, z. b. true/on und false/off ohne Bezeichnungen:

![Zwei Options Satz-Alter Stil](./media/use-native-cds-connector/TwoOptionSet-Old.png)

Mit der neuen *verbesserten Funktion für Datenquellen Funktionen und Common Data Service Ansichten* wird die Karte nun als **Benutzer** definiert gekennzeichnet, und es werden Fehler angezeigt.  Entfernen Sie die alte Datenkarte, und fügen Sie die Option zurück. Nachdem Sie hinzugefügt haben, wird standardmäßig ein Bearbeitungs Steuerelement mit zwei Optionen angezeigt.

![Twooptionset-New](./media/use-native-cds-connector/TwoOptionSet-New.png)

Wenn Sie den Schalter für das boolesche Feld bevorzugen, können Sie die Datenkarte entsperren und das Steuerelement in der Datenkarte durch ein Umschalten ersetzen.  Sie müssen diese Eigenschaften auch beim Umschalten festlegen.

```powerapps-dot
Toggle1.Default = ThisItem.’Do not allow Bulk Emails’
Toggle1.TrueText = ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’
Toggle1.FalseText = ‘Do not allow Bulk Emails (Accounts)’.Allow
DataCard.Value = If( Toggle1.Value,
    ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’,
    ‘Do not allow Bulk Emails (Accounts)’.Allow )
```

![Schalter mit zwei Optionen umschalten](./media/use-native-cds-connector/TwoOption-Toggle.png)

#### <a name="refining-two-option-patch-statements"></a>Verfeinern von zwei Option Patch-Anweisungen

Die Verwendung der [Patch](./functions/function-patch.md) -Funktion mit zwei Optionen sollte "as is" funktionieren. Sie unterstützt die direkte Verwendung von true und false, ähnlich wie boolescher Wert. Der einzige Unterschied besteht darin, dass Sie, wenn Sie den Wert in einem Label-Steuerelement früher eingefügt haben, das "true" und "false" anzeigt, nun die beiden Options Bezeichnungen anzeigen.

### <a name="polymorphic-lookups"></a>Polymorphe Suchvorgänge

Die folgenden Richtlinien unterstützen Sie bei der Aktualisierung Ihrer Anwendung, wenn auf [polymorphe](working-with-references.md) Felder verwiesen wird. Polymorphe Lookups unterstützen aus demselben Feldverweise auf einen eingeschränkten Satz von mehreren Entitäten.  Ähnlich wie bei verweisen in anderen Sprachen ist ein Daten Satz Verweis ein Zeiger auf einen bestimmten Datensatz in einer bestimmten Entität. Ein Daten Satz Verweis enthält die Entitäts Informationen, die es ermöglichen, auf einen Datensatz in mehreren verschiedenen anderen Entitäten zu verweisen. Dies unterscheidet sich von einer normalen Suche, die nur auf Datensätze in einer Entität verweisen kann.  

#### <a name="access-set-and-filter-on-the-owner-field-of-a-record"></a>Zugreifen auf das Feld "Besitzer" eines Datensatzes, festlegen und Filtern

Beispielsweise kann das Feld "Owner" in einer Entität auf einen Datensatz in der Entität "Users" oder der Entität "Teams" verweisen. Das gleiche Nachschlage Feld in verschiedenen Datensätzen kann auf Datensätze in unterschiedlichen Entitäten verweisen.
 
![Polymorphe Besitzer (Feld)](./media/use-native-cds-connector/Polymorphic1.png)
 
##### <a name="polymorphic-with-filter-and-patch"></a>Polymorph mit Filter und Patch

Daten Satz Verweise können genauso wie ein vollständiger Datensatz verwendet werden:

```powerapps-dot
Filter( Accounts, Owner = First( Teams ) )
Patch( Accounts, First( Accounts ), { Owner: First( Users ) })
```

##### <a name="polymorphic-with-a-gallery-displaying-owner-name"></a>Polymorph mit einem Katalog, der den Besitzer Namen anzeigt

Da ein Verweis auf verschiedene Entitäten verweisen kann, müssen Sie spezifisch sein. **ThisItem.Owner.Name**kann nicht verwendet werden, da das Namensfeld in der **Team** Entität **Team Name**ist, und das Feld Name in der **Benutzer** Entität **Vollständiger Name**ist. Power apps weiß nicht, auf welche Art von Suche Sie verweisen, bis Sie die app ausführen.

So beheben Sie dieses Problem: 

1. Fügen Sie die Datenquellen für die Entitäts Typen hinzu, die der Besitzer aufweisen könnte. im aktuellen Beispiel Benutzer und Teams).
2. Verwenden Sie zusätzliche Funktionen, um ihre Absicht klar zu machen.

Es gibt zwei neue Funktionen, die Sie verwenden können:

- Istype – überprüft, ob ein Daten Satz Verweis von einem bestimmten Entitätstyp ist.
- Astype – wandelt einen Daten Satz Verweis auf einen bestimmten Entitätstyp um.

Mit diesen Funktionen können Sie eine Formel schreiben, die den Namen des Besitzers, der aus zwei unterschiedlichen benannten Feldern stammt, basierend auf dem Entitätstyp des Besitzers anzeigt:

```powerapps-dot
If( IsType( ThisItem.Owner,  [@Teams]), 
    AsType( ThisItem.Owner, [@Teams]).'Team Name', 
    AsType( ThisItem.Owner, [@Users]).'Full Name' )
```

![Katalog mit AS-Typ](./media/use-native-cds-connector/Polymorphic-And-AsType-in-Gallery.png)

Der globale disambiguations-Operator für `[@Teams]` und `[@Users]` wird verwendet, um sicherzustellen, dass Sie auf den globalen Entitätstyp verweisen. Obwohl es in diesem Fall nicht notwendig ist, ist es empfehlenswert, immer zu löschen. 1: n-Beziehungen verursachen häufig einen Konflikt im Daten Satz Bereich des Katalogs, und diese Vorgehensweise vermeidet diese Verwirrung.
 
#### <a name="access-and-set-the-company-name-field-a-customer-data-type-of-the-contacts-entity"></a>Zugreifen auf und Festlegen des Felds "Firmen Name" (ein Kunden Datentyp) der Entität "Kontakte"

Das Feld "Kundensuche" ist eine weitere polymorphe Suche, die dem Besitzer ähnelt. Pro Entität kann nur ein Besitzer Feld vorhanden sein. Eine Entität kann jedoch NULL, ein oder mehrere Kunden Suchfelder enthalten. Die Entität "Contacts" enthält das Feld "Firmen Name", bei dem es sich um ein Kunden Suchfeld handelt. Weitere Informationen finden Sie [unter Anzeigen der Felder eines Kunden](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#show-the-fields-of-a-customer) .
 
#### <a name="access-and-set-the-regarding-field-of-activity-entities-such-as-faxes-phone-calls-email-messages"></a>Greifen Sie auf das Feld "betrifft" der Aktivitäts Entitäten zu, z. b. Faxe

Polymorphe suchen sind nicht auf Konten und Kontakte beschränkt. Die Liste der Entitäten ist mit benutzerdefinierten Entitäten erweiterbar. Die Faxe-Entität hat z. b. ein polymorph in Bezug auf das Nachschlage Feld, das auf Konten, Kontakte und andere Entitäten verweisen kann. Wenn Sie einen Katalog mit der Datenquelle auf Faxe festgelegt haben, können Sie die folgende Formel verwenden, um den Namen anzuzeigen, der dem Feld bezüglich des Nachschlage Vorgangs zugeordnet ist. 
 
 ```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    "" )
```

![Katalog mit bezüglich](./media/use-native-cds-connector/Polymorphic-With-Regarding.png)
 
Weitere Details finden Sie in den Nachschlage [Feldern](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-lookup-fields) und [in Bezug auf Beziehungen](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-relationships) .

#### <a name="access-the-list-of-all-activities-for-a-record"></a>Zugreifen auf die Liste aller Aktivitäten für einen Datensatz

In Common Data Service werden Entitäten wie Faxe, Tasks, e-Mails, Notizen, Telefonanrufe, Buchstaben und Chats als [Aktivitäten](https://docs.microsoft.com/powerapps/developer/common-data-service/activity-entities)bezeichnet. Sie können auch eigene [benutzerdefinierte Aktivitäts Entitäten](https://docs.microsoft.com/powerapps/developer/common-data-service/custom-activities)erstellen.

Sie können Aktivitäten eines bestimmten Typs (z. b. Faxe oder Steuern) oder alle Aktivitäten anzeigen, die einer Entität zugeordnet sind, z. b. das Konto. Fügen Sie die Entität Aktivitäten und andere einzelne Entitäten hinzu, deren Daten in der Canvas-App angezeigt werden sollen.

Jedes Mal, wenn Sie einen Datensatz hinzufügen (z. b. die Tasks-Entität), wird ein Datensatz in der Aktivitäts Entität mit den Feldern erstellt, die für alle Aktivitäts Entitäten gemeinsam sind. Weitere Informationen finden Sie unter [Aktivitäts Entität](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#activity-entity) .

Das folgende Beispiel zeigt, dass bei der Auswahl eines Kontos alle diesem Konto zugeordneten Aktivitäten angezeigt werden:
 
![Polymorphe Aktivitäten](./media/use-native-cds-connector/Polymorphic-Activities.png) 
 
Die Datensätze werden aus der Aktivitäts Entität angezeigt. Sie können jedoch weiterhin die [istype](./functions/function-astype-istype.md) -Funktion verwenden, um zu ermitteln, welche Art von Aktivität Sie sind. Bevor Sie istype mit einem Entitätstyp verwenden, müssen Sie die erforderliche Datenquelle hinzufügen.
 
Mit dieser Formel können Sie den Daten Satz Typen in einem Label-Steuerelement innerhalb des Katalogs anzeigen:

 ```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown")
```

 ![Polymorph-istype](./media/use-native-cds-connector/Polymorphic-IsType.png)

#### <a name="access-the-list-of-notes-for-a-record"></a>Zugreifen auf die Liste der Notizen für einen Datensatz

Beim Erstellen einer Entität können Sie Anlagen aktivieren. Wenn Sie das Kontrollkästchen zum Aktivieren von Anlagen aktivieren, erstellen Sie eine Beziehungs Beziehung mit der Notizen-Entität, wie in dieser Abbildung für die Accounts-Entität gezeigt:

![Notes-Field](./media/use-native-cds-connector/Notes-Field.png)

##### <a name="filtering"></a>Filtern

Basierend auf dem Feld "betrifft" können Sie nicht lesen oder filtern. Die 1: n-Beziehung der umgekehrten Hinweise ist jedoch verfügbar. Um alle Anmerkungen aufzulisten, die einer Konto Entität zugeordnet sind, können Sie die folgende Formel verwenden:

```powerapps-dot
First( Accounts ).Notes
```

##### <a name="patch"></a>Patch

Sie können das Feld Notizen für eine Entität nicht mithilfe von Patch festlegen. Zum Hinzufügen eines Datensatzes zur Notizen-Tabelle einer Entität können Sie die Funktion "in Beziehung" verwenden. Erstellen Sie zuerst den Hinweis, wie in diesem Beispiel:

```powerapps-dot
Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note", isdocument:'Is Document (Notes)'.No } ) )
```

## <a name="next-steps"></a>Nächste Schritte

- [Referenz zu Formeln](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [Referenz zu Steuerelementen](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties)

### <a name="see-also"></a>Siehe auch

[Was ist Common Data Service?](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)
