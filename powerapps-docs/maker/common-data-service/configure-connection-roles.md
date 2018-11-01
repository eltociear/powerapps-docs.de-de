---
title: Verbindungsrollen konfigurieren | MicrosoftDocs
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-connection-roles"></a>Verbindungsrollen konfigurieren

Mit Common Data Service für Apps für können Sie **Verbindungen** zwischen Entitäten definieren, ohne eine Entitätsbeziehung zu erstellen. In Modell-angetriebenen Apps können Personen einem benannten Link zwischen Datensätzen erstellen, um eine weniger formelle Beziehung zu erstellen, die keine tatsächliche Entitätsbeziehung erstellt. Einige Beispiele sind *Freund*, *Geschwister*, *Ehegatte*, *Teilnehmer* und *Stakeholder*. Einige Verbindungen können auch reziprok sein wie *Kind* und *Eltern*, *Ehemann* und *Frau* oder *Doktor* und *Patient*.

Wenn Benutzer eine Verbindung zwischen zwei Datensätzen erstellen, können diese eine Beschreibung und eine zusätzliche Informationen wie z. B. Start- und Enddatum für Beziehungen hinzufügen. Weitere Informationen: [Verbindungen erstellen, um Beziehungen zwischen Datensätzen zu definieren und anzuzeigen](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records).

Jeder Benutzer mit Schreibzugriff zur **Verbindungsrollen**-Entität kann definieren, welche Verbindungen für Benutzer zur Verfügung stehen.

## <a name="view-connection-roles"></a>Verbindungsrollen anzeigen

Es gibt mehrere Standardverbindungsrollen, die in den CDS für Apps konfiguriert werden. Um sie anzuzeigen, wechseln Sie zu Einstellungsbereich. 

### <a name="navigate-to-the-settings-area"></a>Navigieren Sie zum Einstellungsbereich

1. Beim Anzeigen einer Modell-angetriebenen App bearbeiten Sie die URL, um alles nach `dynamics.com` zu entfernen und die Seite zu aktualisieren.
1. Navigieren Sie zu **Einstellungen** > **Geschäftlich** > **Unternehmensmanagement** und dann auf **Verbindungsrollen**.

![Verbindungsrollen in den Business Management-Einstellungen](media/navigate-settings-connection-roles.png)

In dieser Ansicht können Sie alle Verbindungsrollen sehen, die für die Umgebung verfügbar sind und Sie können Sie hier bearbeiten.

> [!NOTE]
> Wenn Sie Verbindungsrollen mit einer Lösung verteilen möchten, stellen Sie sicher, dass sie in der Lösung enthaltenen sind, die Sie verteilen möchten. Weitere Informationen: [Fügen Sie Verbindungsrollen einer Lösung hinzu](#add-connection-roles-to-a-solution)

## <a name="view-connection-roles-in-the-solution-explorer"></a>Verbindungsrollen im Lösungs-Explorer anzeigen.

Da Verbindungsrollen *Lösungsbewusst* sind, d.h. sie können einer Lösung hinzugefügt werden, können Sie auch Verbindungsrollen einer Lösung zum Verteilen hinzufügen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Die meisten Verbindungsrollen, die Sie im Bereich **Einstellungen** sehen, werden in der *internen* **Standardlösung** definiert (nicht zu verwechseln mit **Common Data Services Standardlösung**). Diese interne **Standardlösung** enthält alle Anpassungen im System. Um die **Standardlösung** anzuzeigen, wählen Sie **Alle Lösungen - intern** anzeigen.

## <a name="add-connection-roles-to-a-solution"></a>Verbindungsrollen einer Lösung hinzufügen

Im Allgemeinen wird jedoch nicht empfohlen, Komponenten in der internen **Standardlösung** zu bearbeiten. In der **Common Data Services  Standardlösung** oder einer anderen Lösung, in der Sie Arbeit erstellt haben, können Sie den Befehl **Bestehendes Hinzufügen** auswählen, um eine Standardverbindungsrolle in die Lösung zu integrieren.

![Bestehende Verbindungsrolle hinzufügen](media/add-existing-connection-role.png)

Nachdem Sie eine entsprechende Verbindungsrolle Ihrer Lösung hinzugefügt haben, können Sie sie ändern, wo sie angezeigt wird.

## <a name="create-or-edit-connection-roles"></a>Erstellen oder bearbeiten von Verbindungsrollen.

> [!IMPORTANT]
> Wenn Sie eine Lösung verteilen möchten, die neue Verbindungsrollen enthält oder Änderungen an vorhandenen Verbindungsrollen machen möchten, müssen Sie sie der Lösung hinzufügen, die Sie verteilen möchten. Neue Verbindungsrollen bearbeiten oder hinzufügen mithilfe vom Bereich **Einstellungen** fügt diese Verbindungsollen der internen **Standardlösung** hinzu und wird sie nicht in der Lösung integrieren, die Sie verteilen, es sei denn, Sie fügen das Ihrer Lösung hinzu. Weitere Informationen: [Fügen Sie Verbindungsrollen einer Lösung hinzu](#add-connection-roles-to-a-solution)

In der Liste **Verbindungsrollen** wählen Sie eine der Verbindungsrollen aus, um sie zu bearbeiten.
Es gibt drei Schritte, um eine Verbindungsrolle zu definieren, die im Formular eindeutig ausgerufen wird.

![Verbindungsrollen-Formular erstellen](media/create-connection-role-form.png)

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

Sie können neue Kategorien hinzufügen oder vorhandene ändern, indem Sie die **Kategorie** globalen Optionssatz bearbeiten. Weitere Informationen: [Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service for Apps (Auswahl)](create-edit-global-option-sets.md)

### <a name="select-record-types"></a>Datensatztyp auswählen

Wählen Sie aus, welche Datensatztypen angezeigt werden sollen - Organisation.

> [!NOTE]
> Obwohl standardmäßig **Alle** ausgewählt wird, stellen Sie sicher, dass Sie überlegen, welche Arten für die Verbindungsrolle geeignet sind, die Sie hinzufügen.

### <a name="matching-connection-roles"></a>Verbindungsrollen: Übereinstimmend

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
[Erstellen und Bearbeiten von globalen Optionssätzen für Common Data Service für Apps (Auswahl)](create-edit-global-option-sets.md)<br />
[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)


