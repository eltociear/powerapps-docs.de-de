---
title: Verbindungsrollen konfigurieren | MicrosoftDocs
ms.custom: ''
ms.date: 02/11/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0827acf9d7699e6bf88374d57a6e5218e3000ef5
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040491"
---
# <a name="configure-connection-roles"></a>Verbindungsrollen konfigurieren

Mit Common Data Service können Sie **Verbindungen** zwischen Entitäten definieren, ohne eine Entitätsbeziehung zu erstellen. In Modell-angetriebenen Apps können Personen einem benannten Link zwischen Datensätzen erstellen, um eine weniger formelle Beziehung zu erstellen, die keine tatsächliche Entitätsbeziehung erstellt. Einige Beispiele sind *Freund*, *Geschwister*, *Ehegatte*, *Teilnehmer* und *Stakeholder*. Einige Verbindungen können auch reziprok sein wie *Kind* und *Eltern*, *Ehemann* und *Frau* oder *Doktor* und *Patient*.

Wenn Benutzer eine Verbindung zwischen zwei Datensätzen erstellen, können diese eine Beschreibung und eine zusätzliche Informationen wie z. B. Start- und Enddatum für Beziehungen hinzufügen. Weitere Informationen: [Verbindungen erstellen, um Beziehungen zwischen Datensätzen zu definieren und anzuzeigen](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records).

Jeder Benutzer mit Schreibzugriff zur **Verbindungsrollen**-Entität kann definieren, welche Verbindungen für Benutzer zur Verfügung stehen.

> [!IMPORTANT]
> Damit eine Entität als Datensatztyp für eine neue oder vorhandene Verbindungsrolle verfügbar ist, muss die Eigenschaft **Verbindungen aktivieren** für die Entität aktiviert sein. 

## <a name="enable-connection-roles-for-an-entity"></a>Verbindungsrollen für eine Entität aktivieren.
1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Erweitern Sie **Daten** und wählen dann **Entitäten** aus. 
3. Wählen Sie die Entität, die Sie für Verbindungsrollen aktivieren möchten, und klicken Sie anschließend in der Befehlsleiste auf **Einstellungen**. 
4. Erweitern Sie im Bereich **Einstellungen** den Bereich **Zusammenarbeit**, und wählen dann **Verbindungen aktivieren** aus.
    > [!div class="mx-imgBorder"] 
    > ![Verbindungseinstellungen aktivieren](media/enable-connections.png "Verbindungseinstellungen aktivieren")

6. **Fertig** auswählen 

## <a name="view-connection-roles"></a>Verbindungsrollen anzeigen

Es gibt mehrere Standardverbindungsrollen, die in Common Data Service konfiguriert werden.  

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wählen Sie dann im linken Fensterbereich **Lösungen**. 
2. Öffnen Sie die gewünschte nicht verwaltete Lösung. 
3. Wählen Sie in der Befehlsleiste **Existierende Lösungen** und dann **Verbindungsrolle**. 
   Die Liste der verfügbaren Verbindungsrollen wird angezeigt. 
4. Wählen Sie **Abbrechen**, um das Dialogfeld **Bestehende Verbindungsrollen hinzufügen** zu schließen, ohne der Lösung eine Verbindungsrolle hinzuzufügen.

> [!NOTE]
> - Wenn Sie Verbindungsrollen mit einer Lösung verteilen möchten, stellen Sie sicher, dass sie in der Lösung enthaltenen sind, die Sie verteilen möchten. Weitere Informationen: [Fügen Sie Verbindungsrollen einer Lösung hinzu](#add-connection-roles-to-a-solution)

### <a name="view-and-edit-connection-roles-using-the-classic-experience"></a>Anzeigen und Bearbeiten von Verbindungsrollen unter Verwendung der klassischen Erfahrung

Die meisten der Verbindungsrollen, die Sie im Bereich **Einstellungen** sehen können, sind innerhalb des Bereichs *Intern* **Standardlösung** definiert (nicht zu verwechseln mit der **Common Data Services Standardlösung**). Diese interne **Standardlösung** enthält alle Anpassungen im System. Um die **Standardlösung** anzuzeigen, wählen Sie **Alle Lösungen - intern** anzeigen. 

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und wählen Sie dann in der Befehlsleiste **Einstellungen**![Einstellungen](media/powerapps-gear.png) und dann **Erweiterte Einstellungen**.
2. Navigieren Sie zu **Einstellungen** > **Geschäftlich** > **Unternehmensmanagement** und dann auf **Verbindungsrollen**.

   > [!div class="mx-imgBorder"] 
   > ![Verbindungsrollen in den Business Management-Einstellungen](media/navigate-settings-connection-roles.png "Verbindungsrollen in den Business Management-Einstellungen")

In dieser Ansicht können Sie alle Verbindungsrollen sehen, die für die Umgebung verfügbar sind und Sie können Sie hier bearbeiten.

## <a name="add-connection-roles-to-a-solution"></a>Verbindungsrollen einer Lösung hinzufügen
Da Verbindungsrollen *Lösungsbewusst* sind, d.h. sie können einer Lösung hinzugefügt werden, können Sie auch Verbindungsrollen einer Lösung zum Verteilen hinzufügen.

Im Allgemeinen wird jedoch nicht empfohlen, Komponenten in der internen **Standardlösung** zu bearbeiten. Innerhalb der Lösung, die Sie für die Arbeit in der Lösung erstellt haben, können Sie den Befehl **Bestehende hinzufügen** im Bereich **Lösungen** verwenden, um jede der aktiven Verbindungsrollen in Ihre Lösung zu bringen.

> [!div class="mx-imgBorder"] 
> ![Bestehende Verbindungsrolle hinzufügen](media/add-existing-connection-role.png)

Nachdem Sie eine entsprechende Verbindungsrolle Ihrer Lösung hinzugefügt haben, können Sie sie ändern, wo sie angezeigt wird.

> [!NOTE]
> Der Status der Verbindungsrolle wird beim Export aus einer Lösung nicht in die Verbindungsrolle übernommen. Wenn die Lösung in eine Zielumgebung importiert wird, wird der Status daher standardmäßig auf aktiv gesetzt. 


## <a name="create-a-connection-role"></a>Erstellen einer Verbindungsrolle

> [!IMPORTANT]
> Wenn Sie eine Lösung verteilen möchten, die neue Verbindungsrollen enthält oder Änderungen an vorhandenen Verbindungsrollen machen möchten, müssen Sie sie der Lösung hinzufügen, die Sie verteilen möchten. Neue Verbindungsrollen bearbeiten oder hinzufügen mithilfe vom Bereich **Einstellungen** fügt diese Verbindungsollen der internen **Standardlösung** hinzu und wird sie nicht in der Lösung integrieren, die Sie verteilen, es sei denn, Sie fügen das Ihrer Lösung hinzu. Weitere Informationen: [Fügen Sie Verbindungsrollen einer Lösung hinzu](#add-connection-roles-to-a-solution)

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und wählen Sie dann im linken Fensterbereich **Lösungen**. 
2. Öffnen Sie die gewünschte nicht verwaltete Lösung und wählen Sie dann in der Befehlsleiste **Neu** > **Andere** > **Verbindungsrolle**. 
3. Füllen Sie die drei Schritte auf dem Formular aus, um [Beschreiben Sie die Verbindungsrolle](#describe-the-connection-role).

   > [!div class="mx-imgBorder"] 
   > ![Verbindungsrollen-Formular erstellen](media/create-connection-role-form.png)

### <a name="describe-the-connection-role"></a>Beschreiben der Verbindungsrolle

Legen Sie die folgenden Felder fest:

|Feld|Beschreibung|
|--|--|
|**Name**|(Erforderlich) Der Text, der die Verbindung beschreibt.|
|**Kategorie**|Eine Gruppe, welche die Kategorie der Verbindung beschreibt. Weitere Informationen: [Verbindungsrollen-Kategoriewerte](#connection-role-category-values)|
|**Beschreibung**|Geben Sie einen Namen für die Rolle ein.|

#### <a name="connection-role-category-values"></a>Verbindungsrolle Kategoriewerte

Die standardmäßige **Verbindungsrollen-Kategorie**-Werte lauten:
- Geschäftlich
- Familie
- Soziale Medien
- Sales
- Andere
- Projektbeteiligter
- VERTRIEBSTEAM
- Service

Sie können neue Kategorien hinzufügen oder vorhandene ändern, indem Sie die **Kategorie** globalen Optionssatz bearbeiten. Weitere Informationen: [Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service (Auswahllisten)](create-edit-global-option-sets.md)

#### <a name="select-record-types"></a>Datensatztyp auswählen

Wählen Sie aus, welche Datensatztypen angezeigt werden sollen - Organisation.

> [!NOTE]
> Obwohl standardmäßig **Alle** ausgewählt wird, stellen Sie sicher, dass Sie überlegen, welche Arten für die Verbindungsrolle geeignet sind, die Sie hinzufügen.

#### <a name="matching-connection-roles"></a>Verbindungsrollen: Übereinstimmend

In diesem optionalen Schritt können Sie alle Rollen definieren, die in einer Weise gegenseitig angewendet werden. Es ist kein Pflichtfeld, aber Verbindungen sind sinnvoller, wenn diese definiert werden.

So können Benutzer festlegen, dass Glen ein *Freund* von Mary ist, aber bedeutet dies auch, dass Mary ein *Freund* von Glen ist? Wir hoffen es. Aber, wenn Glen der *Vater* von Mary ist, bedeutet dies nicht, dass Mary der *Vater* von Glen ist. Das Einrichten der richtigen Reziprozität erfordert diesen zusätzlichen Schritt.

Wenn Benutzer eine Verbindungsrolle einstellen, die die Kriterien einer übereinstimmenden Verbindungsrolle hat, wird die Rolle nur angezeigt, wenn Sie die Verbindung des Datensatzes anzeigt, dass die Verbindung auf das angewendet wurde. Wenn vom eingefügten Datensatz angezeigt wird, ist die Rolle leer, es sei denn, eine entsprechende Rolle ist festgelegt.

Für die Rolle wie *Freund*, *Ehepartner*, *Kollege*, *Geschwister* ist es besser, die entsprechenden Rolle selber zuzuweisen. Wenn eine einzelne übereinstimmenden Verbindungsrolle konfiguriert ist, wird die aufgewendete einzelne übereinstimmenden Verbindungsrolle in beiden Anweisungen angewendet.

> [!IMPORTANT]
> Sie müssen eine neue Verbindungsrolle ohne die übereinstimmenden Verbindungsrolle speichern, bevor Sie die übereinstimmenden Verbindungsrolle auf sich einstellen können.

Sie werden feststellen, dass einige Verbindungsrollen bereits konfiguriert mit entsprechenden Verbindungsrollen konfiguriert werden. *Ehemaliger Mitarbeiter* wird mit *Ehemaliger Arbeitgeber* und umgehkehrt abgeglichen. Diese Art von eins-zu-eins übereinstimmenden Verbindungsrollen ist in der Regel am sinnvollsten.

Sie können mehrere Verbindungsrollen konfigurieren, um komplexe Beziehungen zu beschreiben. Wenn Sie eine Verbindungsrolle wie *Vater* erstellen, können Sie zwei weitere Rollen konfigurieren wie *Tochter* und *Sohn* und beide als entsprechende Verbindungsrollen *Vater* zuweisen. Sowohl *Tochter* wie *Sohn* sind Verbindungsrollen, die dem *Vater* zugeordnet werden sollten. Selbstverständlich sollten Sie eine äquivalente Rolle für *Mutter* einrichten, die auf ähnliche Weise mit *Tochter* und *Sohn* abgeglichen wird.

> [!TIP]
> Bevor Sie komplexere Verbindungsrollen festlegen, sollten Sie überlegen, ob ein einfacherer Rollensatz auch genügt. Beispielsweise statt komplexe Verbindungsrollen wie *Vater*, *Mutter*, *Sohn* und *Tochter* fetzulegen, prüfen Sie ob, einfach *Eltern* und *Kind* für Sie auch funktionieren.

Wird mehr als einer übereinstimmende Verbindungsrolle konfiguriert, stellen diese Verbindungsrollen nur die gültigen gegenseitigen Rollen dar. Die erste wird automatisch als Standardwert angewendet. Wenn der Standardwert nicht zutrifft, muss der Benutzer die erforderliche Verbindung manuell bearbeiten und zwischen gültigen Optionen wählen in der Konfiguration.

### <a name="see-also"></a>Siehe auch
<!-- This is in the basics guide. It needs to be migrated -->
[Erstellen von Verbindungen zum Festlegen von Beziehungen zwischen Datensätzen](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)<br />
[Erstellen und Bearbeiten globaler Optionssätze für Common Data Service (Auswahllisten)](create-edit-global-option-sets.md)<br />
[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)


