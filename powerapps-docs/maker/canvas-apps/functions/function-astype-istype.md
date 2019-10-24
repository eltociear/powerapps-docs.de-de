---
title: Astype-und istype-Funktionen in Canvas-apps | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "astype" und "istype" in Canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ecb30a5a452a6ee092ccf9bc9d47f6182ef60ab
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "71993005"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>Astype-und istype-Funktionen in Canvas-apps

Überprüft einen Daten Satz Verweis auf einen bestimmten Entitätstyp (**istype**) und behandelt den Verweis als bestimmten Typ (**astype**).

## <a name="description"></a>Beschreibung

Weitere Informationen finden Sie Untergrund Legendes zu [Daten Satz verweisen und polymorphe Such](../working-with-references.md) Vorgänge.

Ein Nachschlage Feld bezieht sich in der Regel auf Datensätze in einer bestimmten Entität. Da der-Entitätstyp gut festgelegt ist, können Sie mithilfe einer einfachen Punkt Notation auf die Felder der Suche zugreifen. Beispielsweise **First (Accounts). Primärer Kontakt '. ' Full Name "** geht von der Entität **Accounts** zum **primären Kontakt** Daten Satz in der Entität **Contacts** und extrahiert das Feld **Full Name** .

Common Data Service unterstützt auch polymorphe Nachschlage Felder, die auf Datensätze aus einem Satz von Entitäten verweisen können, wie in diesen Beispielen.

| Nachschlage Feld | Kann auf |
|--------------|--------------|
| **Eigentor** | **Benutzer** oder **Teams** |
| **Kunde** | **Konten** oder **Kontakte** |
| **Auf** | **Konten**, **Kontakte**, **Wissens**Daten Bank Artikel usw. |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

In Canvas-App-Formeln können Sie Daten Satz Verweise verwenden, um mit polymorphen Lookups zu arbeiten. Da ein Daten Satz Verweis auf verschiedene Entitäten verweisen kann, wissen Sie nicht, welche Felder verfügbar sind, wenn Sie eine Formel schreiben. Die *. Die Feld* Notation ist nicht verfügbar. Diese Formeln müssen sich an die Datensätze anpassen, die von der App bei der Ausführung erkannt werden.

Die **istype** -Funktion testet, ob sich ein Daten Satz Verweis auf einen bestimmten Entitätstyp bezieht. Die-Funktion gibt einen booleschen Wert true oder false zurück.

Die **astype** -Funktion behandelt einen Daten Satz Verweis als bestimmten Entitätstyp, der manchmal *auch als Umwandlung*bezeichnet wird. Sie können das Ergebnis so verwenden, als ob es ein Datensatz der Entität wäre, und wieder verwenden *. Feld* Notation für den Zugriff auf alle Felder dieses Datensatzes. Ein Fehler tritt auf, wenn der Verweis nicht vom angegebenen Typ ist.

Verwenden Sie diese Funktionen, um zuerst den Entitätstyp eines Datensatzes zu testen und ihn dann als Datensatz dieses Typs zu behandeln, sodass die Felder verfügbar sind:

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

Diese Funktionen sind nur erforderlich, wenn Sie auf die Felder eines Daten Satz Verweises zugreifen. Beispielsweise können Sie Daten Satz Verweise in der [**Filter**](function-filter-lookup.md) -Funktion ohne **istype** oder **astype**verwenden:

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

Auf ähnliche Weise können Sie Daten Satz Verweise mit der [**Patch**](function-patch.md) -Funktion verwenden:

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

Wenn Sie [**in einem Daten**](../controls/control-gallery.md) Satz Kontext verwendet werden, z. b. in einem Katalog-oder [**Bearbeitungs Formular**](../controls/control-form-detail.md) -Steuerelement, müssen Sie möglicherweise den [globalen Operator](operators.md#disambiguation-operator) für die Mehrdeutigkeit verwenden, um auf den Entitätstyp zu verweisen. Diese Formel könnte beispielsweise für einen Katalog wirksam werden, der eine Liste von Kontakten anzeigt, bei der der **Firmen Name** eine **Kunden** Suche ist:

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

Für beide Funktionen geben Sie den Typ über den Namen der Datenquelle an, die mit der Entität verbunden ist. Damit die Formel funktioniert, müssen Sie der APP auch für alle Typen, die Sie testen oder umwandeln möchten, eine Datenquelle hinzufügen. Beispielsweise müssen Sie die Entität **Benutzer** als Datenquelle hinzufügen, wenn Sie **istype** und **astype** mit einer **Besitzer** Suche und Datensätzen aus dieser Entität verwenden möchten. Sie können nur die Datenquellen hinzufügen, die Sie tatsächlich in Ihrer APP verwenden. Sie müssen nicht alle Entitäten hinzufügen, auf die eine Suche verweisen kann.

Wenn der Daten Satz Verweis *leer*ist, gibt **istype** false zurück, und **astype** gibt *leer*zurück. Alle Felder eines *leeren* Datensatzes sind *leer*.

## <a name="syntax"></a>Syntax

**Astype**( *recordreferenzierung*, *EntityType* )

- *Recordreferenzierung* : erforderlich. Ein Daten Satz Verweis, häufig ein Nachschlage Feld, das auf einen Datensatz in einer von mehreren Entitäten verweisen kann.
- *EntityType* : erforderlich. Die spezifische Entität, für die getestet werden soll.

**Istype**( *recordreferenzierung*, *EntityType* )

- *Recordreferenzierung* : erforderlich. Ein Daten Satz Verweis, häufig ein Nachschlage Feld, das auf einen Datensatz in einer von mehreren Entitäten verweisen kann.
- *EntityType* : erforderlich. Die spezifische Entität, in die der Datensatz umgewandelt werden soll.

## <a name="example"></a>Beispiel

Informationen [zu Daten Satz verweisen und polymorphe Such](../working-with-references.md) Vorgänge enthalten ausführliche Beispiele.

1. Erstellen Sie eine leere Canvas-App für Tablets.

1. Wählen Sie auf der Registerkarte **Ansicht** die Option **Datenquellen**aus, und fügen Sie dann die Entitäten **Contacts** und **Accounts** als Datenquellen hinzu.
    > [!div class="mx-imgBorder"]
    > ![Blank App mit zwei Datenquellen: Konten und Kontakte ](media/function-astype-istype/contacts-add-datasources.png)

1. Fügen Sie ein Katalog **-Steuerelement mit einer** **leeren vertikalen** Ausrichtung ein.

    > [!div class="mx-imgBorder"]
    > ![Insert ein Katalog-Steuerelement mit einem leeren vertikalen Layout ](media/function-astype-istype/contacts-customer-gallery.png)

1. Legen Sie auf der Registerkarte **Eigenschaften** in der Nähe der rechten Seite des Bildschirms die **Items** -Eigenschaft des Katalogs auf **Contacts**fest.

    > [!div class="mx-imgBorder"]
    > ![Set Elemente im Bereich "Eigenschaften" auf Kontakte ](media/function-astype-istype/contacts-customer-datasource.png)

1. Legen Sie das Layout des Katalogs auf **Titel und Untertitel**fest.

    > [!div class="mx-imgBorder"]
    > ![Open Sie die Layoutauswahl im Eigenschaften Bereich ](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![Set Layout für Titel und Untertitel ](media/function-astype-istype/contacts-customer-flyout.png)

1. Öffnen Sie im Bereich **Daten** die Liste **Title1** , und wählen Sie dann **Vollständiger Name**aus.

    > [!div class="mx-imgBorder"]
    > ![Set Titel Wert ](media/function-astype-istype/contacts-customer-title.png)

1. Wählen Sie das **Subtitle1** Label-Steuerelement aus.

    > [!div class="mx-imgBorder"]
    > ![Set Untertitel Wert ](media/function-astype-istype/contacts-customer-subtitle.png)

1. Legen Sie die **Text** -Eigenschaft von **Subtitle1** auf diese Formel fest:

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Screen ist nun fertiggestellt und zeigt im Katalog gemischte Konten und Kontakte an ](media/function-astype-istype/contacts-customer-complete.png)

    Der Untertitel im Katalog zeigt die folgenden Werte:
    - "--", wenn der **Name des Unternehmens** *leer*ist.
    - "Konto:" und dann das Feld " **Kontoname** " aus der Entität " **Accounts** ", wenn das Feld " **Firmen Name** " auf ein Konto verweist.
    - "Contact:" und dann das Feld " **Vollständiger Name** " aus der Entität " **Kontakte** ", wenn das Feld " **Firmenname** " auf einen Kontakt verweist.

    Ihre Ergebnisse können sich von denen in diesem Thema unterscheiden, da Sie Beispiel Daten verwendet, die geändert wurden, um zusätzliche Ergebnistypen anzuzeigen.
