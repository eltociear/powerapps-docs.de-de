---
title: Konfigurieren von Verbindungsrollen | Microsoft-Dokumentation
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
ms.openlocfilehash: 4faf195f1c751e3796267d52725c1cb753c4889d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688009"
---
# <a name="configure-connection-roles"></a>Konfigurieren von Verbindungsrollen

Mit Common Data Service für Apps können Sie **Verbindungen** zwischen Datensätzen von Entitäten definieren, ohne eine Entitätsbeziehung zu erstellen. In modellgesteuerten Apps können Benutzer eine benannte Verknüpfung zwischen Datensätzen erstellen, um eine weniger formale Beziehung einzurichten, die es nicht rechtfertigt, eine tatsächliche Entitätsbeziehung zu erstellen. Beispiele: *Freund*, *Geschwister*, *Ehepartner*, *Teilnehmer* und *Projektbeteiligter*. Einige Verbindungen können auch in Beziehung zueinander stehen, z.B. *Kind* und *Eltern*, *Ehemann* und *Ehefrau* oder *Arzt* und *Patient*.

Wenn Benutzer eine Verbindung zwischen zwei Datensätzen herstellen, können sie auch eine Beschreibung und zusätzliche Informationen wie Start- und Enddatum der Beziehung hinzufügen. Weitere Informationen finden Sie unter [Erstellen von Verbindungen zum Festlegen und Anzeigen von Beziehungen zwischen Datensätzen](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records).

Jeder Benutzer mit Schreibzugriff auf die Entität **Verbindungsrolle** kann festlegen, welche Verbindungen für Benutzer verfügbar sind.

## <a name="view-connection-roles"></a>Anzeigen von Verbindungsrollen

Es gibt eine Reihe von Standardverbindungsrollen, die bereits in Common Data Service für Apps konfiguriert sind. Öffnen Sie den Bereich „Einstellungen“, um sie anzuzeigen. 

### <a name="navigate-to-the-settings-area"></a>Navigieren zum Bereich „Einstellungen“

1. Bearbeiten Sie beim Anzeigen einer modellgesteuerten App die URL, um alles nach `dynamics.com` zu entfernen, und aktualisieren Sie die Seite.
1. Navigieren Sie zu **Einstellungen** > **Unternehmen** > **Unternehmensmanagement**, und wählen Sie dann **Verbindungsrollen** aus.

![Verbindungsrollen in den Einstellungen für „Unternehmensmanagement“](media/navigate-settings-connection-roles.png)

In dieser Ansicht sehen Sie die Verbindungsrollen, die für diese Umgebung verfügbar sind. Hier können Sie sie bearbeiten.

> [!NOTE]
> Wenn Sie Verbindungsrollen mit einer Lösung freigeben möchten, überprüfen Sie, ob sie in der zu verteilenden Lösung enthalten sind. Weitere Informationen finden Sie unter [Hinzufügen von Verbindungsrollen zu einer Lösung](#add-connection-roles-to-a-solution).

## <a name="view-connection-roles-in-the-solution-explorer"></a>Anzeigen von Verbindungsrollen im Projektmappen-Explorer

Da Verbindungsrollen *lösungsfähig* sind, d.h. sie können einer Lösung hinzugefügt werden, können Sie Verbindungsrollen auch einer Lösung hinzufügen, die Sie freigeben.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Die meisten Verbindungsrollen, die im Bereich **Einstellungen** angezeigt werden, werden in der *internen* **Standardlösung** (nicht zu verwechseln mit **Common Data Services-Standardlösung**) definiert. Diese interne **Standardlösung** enthält alle Anpassungen im System. Um die **Standardlösung** anzuzeigen, wählen Sie die Ansicht **Alle Lösungen – intern** aus.

## <a name="add-connection-roles-to-a-solution"></a>Hinzufügen von Verbindungsrollen zu einer Lösung

Generell ist es nicht empfehlenswert, Komponenten in der internen **Standardlösung** zu bearbeiten. In der **Common Data Services-Standardlösung** oder einer beliebigen Lösung, die Sie erstellt haben, können Sie mit dem Befehl **Vorhandenes Element hinzufügen** eine Standardverbindungsrolle in Ihre Lösung integrieren.

![Hinzufügen einer vorhandenen Verbindungsrolle](media/add-existing-connection-role.png)

Sobald Sie die Verbindungsrolle Ihrer Lösung hinzugefügt haben, können Sie sie bearbeiten, wo sie angezeigt wird.

## <a name="create-or-edit-connection-roles"></a>Erstellen oder Bearbeiten von Verbindungsrollen

> [!IMPORTANT]
> Wenn Sie eine Lösung freigeben möchten, die neue Verbindungsrollen oder Änderungen an den bestehenden Verbindungsrollen enthält, müssen Sie diese der freizugebenden Lösung hinzufügen. Wenn Sie neue Verbindungsrollen im Bereich **Einstellungen** bearbeiten oder hinzufügen, werden diese Verbindungsrollen der internen **Standardlösung** hinzugefügt und nicht in die Lösung aufgenommen, die Sie freigeben – es sei denn, Sie fügen sie zuerst Ihrer Lösung hinzu. Weitere Informationen finden Sie unter [Hinzufügen von Verbindungsrollen zu einer Lösung](#add-connection-roles-to-a-solution).

Wählen Sie in der Liste **Verbindungsrollen** eine der Verbindungsrollen zum Bearbeiten aus.
Das Definieren einer Verbindungsrolle erfolgt in drei Schritten, die im Formular klar hervorgehoben sind.

![Erstellen eines Verbindungsrollenformulars](media/create-connection-role-form.png)

### <a name="describe-the-connection-role"></a>Beschreiben der Verbindungsrolle

Legen Sie die folgenden Felder fest:

|Feld|Beschreibung|
|--|--|
|**Name**|(Erforderlich) Den Text, der die Verbindung beschreibt.|
|**Kategorie**|Eine Gruppe, die die Kategorie der Verbindung beschreibt. Weitere Informationen finden Sie unter [Werte für Verbindungsrollenkategorien](#connection-role-category-values).|
|**Description** (Beschreibung)|Eine Definition für die Rolle.|

#### <a name="connection-role-category-values"></a>Werte für Verbindungsrollenkategorien

Die **Standardwerte für Verbindungsrollenkategorien** lauten:
- Business
- Family
- Soziale
- Vertrieb
- Sonstiges
- Projektbeteiligter
- Vertriebsteam
- Dienst

Sie können neue Kategorien hinzufügen oder vorhandene ändern, indem Sie den globalen Optionssatz **Kategorie** bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Bearbeiten globaler Optionssätze für Common Data Service für Apps (Auswahllisten)](create-edit-global-option-sets.md).

### <a name="select-record-types"></a>Auswählen von Datensatztypen

Wählen Sie aus, welche Datensatztypen zum Verbinden verfügbar sind.

> [!NOTE]
> Obwohl standardmäßig **Alle** ausgewählt ist, müssen Sie berücksichtigen, welche Typen für die hinzugefügte Verbindungsrolle geeignet sind.

### <a name="matching-connection-roles"></a>Zuordnen von Verbindungsrollen

In diesem optionalen Schritt können Sie beliebige Rollen definieren, die in wechselseitiger Beziehung zueinander stehen und gemeinsam angewendet werden. Es ist zwar nicht erforderlich, doch Verbindungen sind sinnvoller, wenn sie definiert sind.

Beispielsweise lässt sich angeben, dass Glen ein *Freund* von Mary ist. Heißt das aber auch, dass Mary ein *Freund* von Glen ist? Es wäre jedenfalls wünschenswert. Wenn Glen jedoch der *Vater* von Mary ist, muss Mary nicht im Umkehrschluss der *Vater* von Glen sein. Dieser zusätzliche Schritt ist erforderlich, um eine ordnungsgemäße Wechselbeziehung herzustellen.

Wenn Benutzer eine Verbindungsrolle festlegen, der keine entsprechende Verbindungsrolle zugeordnet ist, wird die Rolle nur dann angezeigt, wenn die Verbindung in dem Datensatz aufgerufen wird, auf den sie angewendet wurde. Die Rolle ist leer, wenn sie im verknüpften Datensatz angezeigt wird, es sei denn, für sie wird eine übereinstimmende Rolle eingerichtet.

Für Rollendefinitionen wie *Freund*, *Ehepartner*, *Kollege* oder *Geschwister* wird empfohlen, der Rolle selbst die übereinstimmende Rolle zuzuweisen. Wenn eine einzelne übereinstimmende Verbindungsrolle konfiguriert ist, wird diese in beide Richtungen angewendet.

> [!IMPORTANT]
> Sie müssen eine neue Verbindungsrolle ohne diese übereinstimmende Verbindungsrolle speichern, bevor Sie die übereinstimmende Verbindungsrolle für sich selbst festlegen können.

Einige Verbindungsrollen sind bereits mit entsprechenden Verbindungsrollen konfiguriert. *Ehemaliger Mitarbeiter* wird mit *Ehemaliger Arbeitgeber* verknüpft und umgekehrt. Diese Art von Eins-zu-Eins-Zuordnung ist bei Verbindungsrollen am gängigsten.

Sie können mehrere übereinstimmende Verbindungsrollen konfigurieren, um komplexe Beziehungen zu beschreiben. Wenn Sie eine Verbindungsrolle wie *Vater* erstellen, können Sie zwei weitere Rollen wie *Tochter* und *Sohn* konfigurieren und beide als übereinstimmende Verbindungsrollen für *Vater* anwenden. Im Gegenzug sollten sowohl die Verbindungsrolle *Tochter* als auch *Sohn* *Vater* zugeordnet sein. Natürlich sollten Sie dann auch eine äquivalente Rolle *Mutter* einrichten, die ebenfalls mit *Tochter* und *Sohn* verknüpft ist.

> [!TIP]
> Bevor Sie einen komplexen Satz von Verbindungsrollen erstellen, überlegen Sie, ob auch ein einfacherer Rollensatz ausreicht. Eine Alternative für den komplexen Verbindungsrollensatz *Vater*, *Mutter*, *Sohn* und *Tochter* wäre ggf. das Verwenden der Rollen *Eltern* und *Kind*.

Wenn mehr als eine übereinstimmende Verbindungsrolle konfiguriert ist, stellen diese Verbindungsrollen die einzigen gültigen wechselseitigen Rollen dar. Die erste wird automatisch als Standardwert angewendet. Wenn der Standardwert nicht richtig ist, müssen die Benutzer die Verbindung manuell bearbeiten und zwischen den in der Konfiguration definierten gültigen Optionen wählen.

### <a name="see-also"></a>Siehe auch
<!-- This is in the basics guide. It needs to be migrated -->
[Erstellen von Verbindungen zum Festlegen und Anzeigen von Beziehungen zwischen Datensätzen](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)<br />
[Erstellen und Bearbeiten globaler Optionssätze für Common Data Service für Apps (Auswahllisten)](create-edit-global-option-sets.md)<br />
[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)


