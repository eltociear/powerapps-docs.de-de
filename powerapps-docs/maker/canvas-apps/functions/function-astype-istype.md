---
title: AsType und IsType-Funktionen in canvas-apps | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktionen AsType und IsType in canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 999653159f838e840f7f569aa9953633a6a70065
ms.sourcegitcommit: 93096dfa1aadba77159db1e5922f3d5528eecb7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65986334"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>AsType und IsType-Funktionen in canvas-apps

Überprüft eine Datensatzreferenz für einen bestimmten Entitätstyp (**IsType**) und den Verweis als bestimmter Typ behandelt (**AsType**).

## <a name="description"></a>Beschreibung

Lesen [zu verstehen, Datensatz Verweise und polymorphen Suchvorgänge](../working-with-references.md) eine umfassendere Einführung und weitere Details.

Ein Nachschlagefeld bezieht sich in der Regel auf Datensätze in einer bestimmten Entität verwendet wird. Da der Entität vom Typ Bereich etabliert ist, können Sie die Felder der Suche mithilfe einer einfachen Punktnotation zugreifen. Z. B. **erste (Konten). " Primärer Kontakt "." Den vollständigen Namen "** führt Sie aus der **Konten** Entität, die die **Hauptkontaktperson** Datensatz in die **Kontakte** Entität und extrahiert die **vollständiger Name**  Feld.

Common Data Service unterstützt auch polymorphen Nachschlagefelder, die Datensätze aus einer Reihe von Entitäten, wie in diesen Beispielen verweisen können.

| Nachschlagefeld | Kann zu verweisen. |
|--------------|--------------|
| **Besitzer** | **Benutzer** oder **Teams** |
| **Kunde** | **Konten** oder **Kontakte** |
| **in Bezug auf** | **Konten**, **Kontakte**, **Knowledge Base-Artikel**usw. |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

In Canvas-app-Formeln können Sie mithilfe von Datensatz Verweise mit polymorphen Suchvorgänge arbeiten. Da ein Datensatzverweis auf andere Entitäten verweisen kann, wissen Sie nicht die Felder werden, wenn Sie eine Formel schreiben. Die *. Feld* Notation ist nicht verfügbar. Diese Formeln müssen Datensätze anpassen, die die app auftritt, wenn er ausgeführt wird.

Die **IsType** Funktion testet, ob ein Datensatzverweis auf einen bestimmten Entitätstyp bezieht. Die Funktion gibt einen booleschen Wert TRUE oder FALSE.

Die **AsType** Funktion behandelt einen Datensatz Verweis als einen bestimmten Typ, auch bezeichnet als *Umwandlung*. Können Sie verwenden Sie das Ergebnis, als handele es sich um einen Datensatz der Entität, und verwenden Sie in diesem Fall die *. Feld* Notation, um auf alle Felder des Datensatzes zugreifen. Ein Fehler tritt auf, wenn der Verweis des angegebenen Typs nicht.

Verwenden Sie diese Funktionen zusammen, um testen Sie zunächst den Entitätstyp eines Datensatzes, und klicken Sie dann als ein Datensatz des betreffenden Typs behandelt, sodass die Felder verfügbar sind:

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

Sie benötigen diese Funktionen nur, wenn Sie die Felder eines Datensatzes Verweises zugreifen. Sie können z. B. Datensatz verweisen, in der [ **Filter** ](function-filter-lookup.md) Funktion ohne **IsType** oder **AsType**:

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

Auf ähnliche Weise können Sie Datensätze Verweise mit der [ **Patch** ](function-patch.md) Funktion:

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

Wird in einem Datensatz, z. B. in verwendet eine [ **Katalog** ](../controls/control-gallery.md) oder [ **Bearbeitungsformular** ](../controls/control-form-detail.md) -Steuerelement, müssen Sie möglicherweise verwenden Sie die [globale Operator zur mehrdeutigkeitsvermeidung](operators.md#disambiguation-operator) auf den Entitätstyp verweisen. Beispielsweise wäre diese Formel für einen Katalog, das eine Liste von Kontakten anzeigt, in denen **Firmenname** ist eine **Kunden** Suche:

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

Für beide Funktionen geben Sie den Typ durch den Namen der Datenquelle, die mit der Entität verbunden ist. Für die Formel funktioniert müssen Sie auch eine Datenquelle für die app für alle Typen hinzufügen, die zum Testen oder umgewandelt werden sollen. Sie müssen z. B. Hinzufügen der **Benutzer** Entität als eine Datenquelle aus, wenn Sie verwenden möchten **IsType** und **AsType** mit einer **Besitzer** Such- und Datensätze von dieser Entität. Sie können nur die Datenquellen hinzufügen, die Sie tatsächlich in Ihrer app verwenden. Sie müssen nicht alle Entitäten hinzufügen, die eine Suche verweisen kann.

Wenn der Datensatzverweis ist *leere*, **IsType** gibt FALSE zurück, und **AsType** gibt *leere*. Alle Felder des eine *leere* Datensatz werden *leere*.

## <a name="syntax"></a>Syntax

**AsType**( *RecordReference*, *EntityType* )

- *RecordReference* : erforderlich. Ein Datensatzverweis, häufig ein Nachschlagefeld, die auf einen Datensatz in mehrere Entitäten verweisen kann.
- *EntityType* : erforderlich. Die bestimmte Entität für die Sie testen.

**IsType**( *RecordReference*, *EntityType* )

- *RecordReference* : erforderlich. Ein Datensatzverweis, häufig ein Nachschlagefeld, die auf einen Datensatz in mehrere Entitäten verweisen kann.
- *EntityType* : erforderlich. Die bestimmte Entität in der der Datensatz umgewandelt werden soll.

## <a name="example"></a>Beispiel

[Zu verstehen, Datensatz Verweise und polymorphen Suchvorgänge](../working-with-references.md) enthält ausführliche Beispiele.

1. Erstellen Sie eine leere Canvas-app für Tablets.

1. Auf der **Ansicht** Registerkarte **Datenquellen**, und fügen Sie dann die **Kontakte** und **Konten** Entitäten als Datenquellen.
    > [!div class="mx-imgBorder"]
    > ![Leere app mit zwei Datenquellen: Konten und Kontakte](media/function-astype-istype/contacts-add-datasources.png)

1. Fügen Sie eine **Katalog** steuern Sie mit einem **Leerzeichen vertikal** Ausrichtung.

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie ein Katalogsteuerelement mit einem leeren vertikalen layout](media/function-astype-istype/contacts-customer-gallery.png)

1. Auf der **Eigenschaften** Registerkarte in der Nähe der rechten Seite des Bildschirms, das Festlegen des Katalogs **Elemente** Eigenschaft **Kontakte**.

    > [!div class="mx-imgBorder"]
    > ![Legen Sie im Eigenschaftenbereich für Elemente auf Kontakte](media/function-astype-istype/contacts-customer-datasource.png)

1. Legen Sie das Layout des Katalogs auf **Titel und Untertitel**.

    > [!div class="mx-imgBorder"]
    > ![Öffnen Sie die Layout-Auswahl aus dem Bereich "Eigenschaften"](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![Festlegen der Layout, Titel und Untertitel](media/function-astype-istype/contacts-customer-flyout.png)

1. In der **Daten** , öffnen Sie im Bereich der **Title1** aus, und wählen Sie dann **vollständigen Namen**.

    > [!div class="mx-imgBorder"]
    > ![Titel-Wert festlegen](media/function-astype-istype/contacts-customer-title.png)

1. Wählen Sie die **Subtitle1** beschriftungs-Steuerelement.

    > [!div class="mx-imgBorder"]
    > ![Untertitel-Wert festlegen](media/function-astype-istype/contacts-customer-subtitle.png)

1. Legen Sie die **Text** Eigenschaft **Subtitle1** auf diese Formel:

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Bildschirm ist jetzt vollständig mit Konten und Kontakte und optional in dem Katalog](media/function-astype-istype/contacts-customer-complete.png)

    Der Untertitel im Katalog werden die folgenden Werte:
    - "--" Wenn die **'Company Name'** ist *leere*.
    - "Konto:" und dann die **Kontoname** aus der **Konten** Entität Wenn die **Firmenname** Feld verweist auf ein Konto.
    - "Wenden Sie sich an:" und dann die **vollständigen Namen** aus der **Kontakte** Entität Wenn die **Firmenname** Feld bezieht sich auf einen Kontakt.

    Die Ergebnisse unterscheiden sich von den in diesem Thema, da Beispieldaten, die geändert wurde verwendet, um weitere Typen von Ergebnissen anzeigen.
