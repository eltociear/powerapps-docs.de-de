---
title: Die Funktion „Choices“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Choices“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed555f5de4abc1e29b7d2a637413c440bd882f13
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61546738"
---
# <a name="choices-function-in-powerapps"></a>Funktion „Choices“ in PowerApps
Gibt eine Tabelle mit den möglichen Werten für eine Suchspalte zurück.

## <a name="description"></a>Beschreibung
Die Funktion **Choices** gibt eine Tabelle mit den möglichen Werten für eine Suchspalte zurück.  

Verwenden Sie die Funktion **Choices**, um eine Liste mit Auswahlmöglichkeiten für den Benutzer zu erstellen. Diese Funktion wird in der Regel zusammen mit dem [**Kombinationsfeld**](../controls/control-combo-box.md)-Steuerelement in Bearbeitungsformularen verwendet.

Bei Suchvorgängen stimmt die Tabelle, die die Funktion **Choices** zurückgibt mit der Fremdtabelle überein, die dem Suchvorgang zugeordnet ist. Wenn Sie die Funktion **Choices** verwenden, ist es nicht mehr notwendig die Fremdtabelle als zusätzliche Datenquelle hinzuzufügen. Die Funktion **Choices** gibt alle Spalten der Fremdtabelle zurück.

Da die Funktion **Choices** eine Tabelle zurückgibt, können Sie die Funktionen [**Filter**](function-filter-lookup.md), [**Sort**](function-sort.md) und [**AddColumns**](function-table-shaping.md) sowie alle weiteren Funktionen verwenden, die zur Bearbeitung einer Tabelle beitragen und die Tabelle filtern, sortieren und formen. 

Derzeit kann die Funktion **Choices** nicht [delegiert](../delegation-overview.md) werden. Wenn diese Einschränkung ein Problem für Ihre App hervorruft, fügen Sie die Fremdentität als Datenquelle hinzu, und verwenden Sie diese. 

Für die Funktion **Choices** ist es nicht wie bei den Funktionen [**ShowColumns**](function-table-shaping.md) und [**Search**](function-filter-lookup.md) sowie anderen Tabellenfunktionen erforderlich, dass Spaltennamen Zeichenfolgen darstellen und in doppelten Anführungszeichen stehen. Geben Sie die Formel so an, als würden Sie direkt auf die Spalte verweisen.

Spaltenverweise müssen direkt auf die Datenquelle verweisen. Wenn beispielsweise **Accounts** die Datenquelle ist und nach **SLA** gesucht wird, lautet der Spaltenverweis **Accounts.SLA**. Der Verweis kann eine Funktion, eine Variable oder ein Steuerelement durchlaufen. Wenn aber **Accounts** an das Steuerelement **Gallery** übergeben wird, verwenden Sie die Formel **Gallery.Selected.SLA**, um auf die SLA für das ausgewählte Konto zu verweisen. Dieser Verweis hat dann ein Steuerelement durchlaufen und kann daher nicht an die Funktion **Columns** übergeben werden. Daher müssen Sie weiterhin **Accounts.SLA** verwenden.

Zu diesem Zeitpunkt können Sie Suchspalten nur mit SharePoint und Common Data Service.

## <a name="syntax"></a>Syntax
**Choices**( *Spalte-Verweis* )

* *Spalte-Verweis* – Erforderlich.  Eine Suchspalte einer Datenquelle Setzen Sie den Spaltennamen nicht in doppelte Anführungszeichen. Der Verweis muss direkt auf die Spalte der Datenquelle hergestellt werden und darf weder eine Funktion noch ein Steuerelement durchlaufen.

## <a name="examples"></a>Beispiele

#### <a name="choices-for-a-lookup"></a>Die Funktion „Choices“ für eine Suche

1. [Erstellen Sie eine Datenbank](../../../administrator/create-database.md) in Common Data Service verwendet werden, und wählen die **enthalten die Beispiel-apps und Daten** Feld.

    Es werden einige Entitäten wie z.B. **Accounts** erstellt.

    **Hinweis:** Entitätsnamen werden auf web.powerapps.com Singular- und Pluralformen in PowerApps Studio.

    ![Ausschnitt aus einer Liste der Felder aus der Entität „Account“ in Common Data Service für Apps, in dem hervorgehoben wird, dass „Primärer Kontakt“ ein Suchfeld ist](media/function-choices/entity-account.png)

    Die Entität **Accounts** weist eine Spalte für den **Primären Kontakt** auf, die eine Suchspalte für die Entität **Contacts** darstellt.  

    ![Ausschnitt aus der Liste mit den Feldern aus der Entität „Contact“ in Common Data Service](media/function-choices/entity-contact.png)

    Für jedes Konto wird entweder ein Kontakt als primärer Kontakt festgelegt oder die Spalte bleibt *leer*.

1. [Generieren Sie eine App](../data-platform-create-app.md) aus der Entität **Accounts**.

1. Scrollen Sie in der Liste mit den Anzeigen und Steuerelementen in der linken Ecke nach unten, bis **EditScreen1** angezeigt wird, und klicken Sie dann darunter auf **EditForm1**.

    ![Auf der linken Navigationsleiste unter „EditScreen1“ auf „EditForm1“ klicken](media/function-choices/select-editform.png)

1. Auf der **Eigenschaften** im rechten Bereich auf der Registerkarte **Bearbeitungsfelder**.

    ![Öffnen Sie den Bereich "Daten"](media/function-choices/open-data-pane.png)

1. In der **Felder** wählen Sie im Bereich **Feld hinzufügen**.

1. Suchen Sie nach der **Hauptkontaktperson** Feld, aktivieren Sie das Kontrollkästchen, und wählen Sie dann **hinzufügen**.

    ![Auf „Accounts“ klicken, um den Bereich „Daten“ zu öffnen](media/function-choices/field-list.png)

    Die **Hauptkontaktperson** Feld am unteren Rand des Formulars angezeigt wird. Wenn das Feld einen Fehler angezeigt wird, wählen Sie **Datenquellen** auf die **Ansicht** Registerkarte, wählen Sie die Auslassungspunkte (...) für die **Konten** -Datenquelle, und wählen Sie dann **aktualisieren** .

1. (Optional) Ziehen Sie das Feld **Primärer Kontakt** aus dem unteren Bereich der Liste in den oberen Bereich.

1. Klicken Sie auf der Karte für den **Primären Kontakt** auf das **Kombinationsfeld**-Steuerelement.

    Die **Elemente** Eigenschaft dieses Steuerelements auf eine Formel, die die Spalte identifiziert festgelegt ist, indem Sie entweder den Anzeigenamen, wie im ersten Beispiel, oder der logische Name, wie im zweiten Beispiel:

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![Eine Canvas-Anzeige mit einem Formularsteuerelement Das Kombinationsfeld-Steuerelement innerhalb der primäre Ansprechpartner Karte ausgewählt ist, und die Items-Eigenschaft, mit der Formel Optionen (Konten. "Primärkontakt") angezeigt wird](media/function-choices/accounts-primary-contact.png)

1. Klicken Sie erst auf der Registerkarte **Start** auf die Option **Neuer Bildschirm** und anschließend auf **Blank**.

1. Klicken Sie auf der Registerkarte **Einfügen** auf die Option **Datentabelle**.

1. Legen Sie die **Elemente** Eigenschaft der **Datentabelle** -Steuerelements auf diese Formel:

     **Choices( Accounts.'Primary Contact' )**

1. In der Mitte der der **Datentabelle** steuern, wählen Sie den Link, der beginnt **wählen Sie die Felder...** , und wählen Sie dann die Kontrollkästchen für das Feld oder Felder, die Sie anzeigen möchten (z. B. **Firstname** und **"LastName"**).

     ![Eine Canvas-Anzeige mit einem Datentabellensteuerelement Die Eigenschaft „Items“ ist auf die Formel „Choices( Accounts.'Primary Contact' )“ festgelegt, und in der Tabelle werden die Spalten „Vorname“ und „Nachname“ für den ersten Datensatz aus der Entität „Contacts“ angezeigt](media/function-choices/full-accounts-pc.png)