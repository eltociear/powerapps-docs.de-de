---
title: Hinzufügen von datensatzbasierter Sicherheit durch Verwendung von Entitätsberechtigungen für ein Portal | MicrosoftDocs
description: Anleitungen zum Hinzufügen einer Entitäts-Berechtigung und Hinzufügen von Webrollen zu dieser.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 082ed3fe584c9812482928c2c1d9a67d9690a569
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979511"
---
# <a name="add-record-based-security-by-using-entity-permissions-for-portals"></a>Hinzufügen von datensatzbasierter Sicherheit durch Verwendung von Entitätsberechtigungen für Portale

Um datensatzbasierte Sicherheit in Portalen auf einzelne Datensätze anzuwenden, verwenden Sie Entitäts-Berechtigungen. Sie fügen Entitäts-Berechtigungen zu Webrollen hinzu, um Rollen in Ihrer Organisation definieren zu können, die den Rechten und Konzepten des Datensatzbesitzes und -zugriffs, die mit Entitätsberechtigungen eingeführt werden, logisch entsprechen. Beachten Sie, dass ein bestimmter Kontakt einer beliebigen Zahl Rollen angehören und eine bestimmte Rolle eine beliebige Anzahl Entitäts-Berechtigungen enthalten kann. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Erstellen von Webrollen für Portale](create-web-roles.md) 

Obwohl Berechtigungen zum Ändern und Aufrufen von URLs in einer Portalsiteübersicht über Content-Autorisierung gewährt werden, können Website-Manager zudem ihre benutzerdefinierten Webanwendungen sichern, die mit Entitätsformularen und Entitätslisten erstellt wurden. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Definieren von Entitätsformularen](entity-forms.md) und [Definieren von Entitätslisten](entity-lists.md)  

Zum Sichern dieser Funktionen wurden Entitätsberechtigungen eingeführt, die die Gewährung granularer Rechte für beliebige Entitäten und die Aktivierung der Sicherheit auf Datensatzebene über Beziehungsdefinitionen ermöglichen.

## <a name="add-entity-permissions-to-a-web-role"></a>Hinzufügen von Entitätsberechtigungen zu Webrollen

1.  Öffnen Sie die [Portalverwaltungs-App](configure-portal.md).

2. Gehen Sie zu **Portale** &gt; **Webrollen** und öffnen die Webrolle, der Sie Berechtigungen hinzufügen möchten. 

3. Unter **verbunden**, wählen **Entitätsberechtigungen**.

4. Wählen Sie **Hinzufügen einer bestehenden Entitätsberechtigung**, um eine vorhandene Entitäts-Berechtigung einer Webrolle hinzuzufügen. 

4. Suchen Sie nach einer Entitätsberechtigung oder wählen Sie **Neue Entitätsberechtigung**, um einen neuen Entitätsberechtigungsdatensatzes zu erstellen.

    ![Hinzufügen von Entitätsberechtigungen zu Webrollen](../media/add-entity-permission-web-role.png "Hinzufügen von Entitätsberechtigungen zu Webrollen")  

Wenn Sie einen neuen Entitäts-Berechtigungsdatensatz erstellen, müssen Sie erst die Entität bestimmen, welche gesichert wird. Danach müssen Sie den Umfang definieren (siehe unten), &mdash;und im Falle eines Umfangs außerhalb von Global&mdash; müssen die Beziehungen, die diesen Umfang definieren, angegeben werden. Abschließend bestimmen Sie die Rechte, die der Rolle über diese Berechtigung gewährt werden. Beachten Sie, dass Rechte kumulativ sind. Wenn also ein Benutzer in einer Rolle ist, die Lesezugriff erteilt, und in einer anderen, die Lese- und Aktualisierungszugriff erteilt, hat der Benutzer Lese- und Aktualisierungszugriff auf alle Datensätze, die sich zwischen den beiden Rollen überschneiden.

> [!Note]
> Das Auswählen von CMS-Entitäten wie Webseite und Webdateien ist ungültig und kann andere unbeabsichtigte Konsequenzen haben. Dieses Portal bestätigt die Sicherheit für CMS-Entitäten anhand Inhalts-Zugriffssteuerungen und nicht Entitätsberechtigungen.

### <a name="global-scope"></a>Global-Umfang

Wenn ein Entitätsberechtigungs-Datensatz mit Leseberechtigung für eine Rolle gewährt wird, die einen globalen Geltungsbereich hat, hat jeder Kontakt in dieser Rolle Zugriff auf alle Datensätze in der definierten Entität. Zum Beispiel kann er alle Leads, Firmen usw. anzeigen. Diese Berechtigung wird automatisch von beliebigen Entitätslisten berücksichtigt; wobei im Wesentlichen alle Datensätze gemäß den modellgesteuerten App-Ansichten angezeigt werden, die für diese Liste definiert wurden. Wenn ein Benutzer ferner versucht, auf einen Datensatz über ein Entitätsformular zuzugreifen, auf das er keinen Zugriff hat, wird ein Berechtigungsfehler angezeigt.

### <a name="contact-scope"></a>Kontakt-Umfang

Mit dem Kontakt-Geltungsbereich werden angemeldeten Benutzern in der Rolle, für die der Berechtigungsdatensatz definiert wurde, die Rechte von dieser Berechtigung nur für Datensätze erteilt, die mit dem Kontaktdatensatz dieses Benutzers über eine definierte Beziehung verknüpft sind.

Auf einer Liste mit Entitäten bedeutet dies, dass ein Filter hinzugefügt wird für alle modellgesteuerten App-Ansichten, die durch diese Liste angezeigt werden, wobei nur die Datensätze abgerufen werden, die direkt mit dem aktuellen Benutzer verknüpft sind. (Je nach Szenario entspricht diese Beziehung dem Besitz oder den Verwaltungsrechten.)

Entitätsformulare erlauben nur die entsprechende Berechtigung zum Lesen, Erstellen, Schreiben usw., sofern diese Beziehung vorhanden ist, wenn der Datensatz geladen wird. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Entitätsformulare definieren](entity-forms.md).  

### <a name="account-scope"></a>Firmen-Umfang

Mit dem Firmen-Geltungsbereich werden angemeldeten Benutzern in der Rolle, für die der Berechtigungsdatensatz definiert wurde, die Rechte von dieser Berechtigung nur für Datensätze erteilt, die mit dem übergeordnete Firma-Datensatz dieses Benutzers über eine definierte Beziehung verknüpft sind.

### <a name="self-scope"></a>Selbst-Umfang

Der Selbst-Umfang ermöglicht Ihnen, die Rechte zu definieren, die ein Benutzer für den eigenen Kontakt (Identitäts)-Datensatz hat. Dadurch können Benutzer mithilfe von Entitätsformularen oder Webformularen Änderungen vornehmen am eigenen Kontaktdatensatz, der mit ihrem Profil verknüpft ist. Beachten Sie, dass die Profil-Standardseite über ein spezielles integriertes Formular verfügt, das es einem beliebigen Benutzer ermöglicht, die grundlegenden Kontaktinformationen zu ändern und Marketinglisten zu abonnieren oder zu kündigen. Wenn dieses Formular im Portal enthalten ist (was standardmäßig der Fall ist), benötigen Benutzer diese Berechtigung nicht zu seiner Verwendung. Sie benötigen diese Berechtigung jedoch, um benutzerdefinierte Entitätsformulare oder Webformulare zu verwenden, die auf ihren Benutzer-Kontaktdatensatz ausgerichtet sind.

### <a name="parental-scope"></a>Übergeordnet-Umfang

In diesem überaus komplexen Fall werden Berechtigungen für eine Entität erteilt, die eine Beziehung entfernt ist von einer Entität, für die bereits ein Berechtigungsdatensatz definiert wurde. Diese Berechtigung ist tatsächlich ein untergeordneter Datensatz der übergeordneten Entitätsberechtigung.

Der übergeordnete Berechtigungsdatensatz definiert eine Berechtigung und einen Umfang für eine Entität (wahrscheinlich Global- oder Kontakt-Umfang, obwohl „Übergeordnet“ auch möglich ist.) Diese Entität kann mit dem Kontakt verknüpft sein (im Fall des Kontakt-Umfangs) oder global definiert. Mit dieser eingerichteten Berechtigung wird eine untergeordnete Berechtigung erstellt, mit der eine Beziehung von einer anderen Entität zur in der übergeordneten Beziehung definierten Entität definiert wurde.

Benutzer in einer Webrolle, die Zugriff auf Datensätze haben, die von übergeordneten Entitätsberechtigungen definiert wurden, verfügen daher ebenfalls über Rechte, wie vom untergeordneten Berechtigungsdatensatz zu Datensätzen, die mit dem übergeordneten Datensatz verknüpft wurden, definiert.

### <a name="attributes-and-relationships"></a>Attribute und Beziehungen

In der folgenden Tabelle werden die Entitäts-Berechtigungsattribute erläutert.

| Name                     | Beschreibung                                                                                                                                                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                     | Der beschreibende Name des Datensatzes. In diesem Feld ist ein Eintrag erforderlich.                                                                                                                                                                                                                                                               |
| Entitätsname              | Der logische Name der Entität, die gesichert werden soll, oder die die Kontakt-Beziehung oder übergeordnete Beziehung definiert, um eine verknüpfte Entität für eine untergeordnete Berechtigung zu sichern. In diesem Feld ist ein Eintrag erforderlich.                                                                                                                        |
| Bereich (obligatorisch)                   | <ul><li>**Global**: Erteilen von Rechten für den Entitätsdatensatz ohne Anforderung für einen Besitzer (Kontakt).</li><li>**Kontakt**: Erteilen von Rechten für den Entitätsdatensatz mit direkter Beziehung zu einem Besitzer (Kontakt).</li><li>**Firma**: Erteilen von Rechten für den Entitätsdatensatz, der eine Beziehung zu einer Firma hat, die als Besitzer dient, unter der Annahme, dass die Firma übergeordneter Kunde des Kontakts ist.</li><li>**Übergeordnet**: Erteilen von Rechten für den Entitätsdatensatz über die Kette der Beziehungen seiner übergeordneten Berechtigungen.</li></ul>|
| Kontaktbeziehung     | Nur erforderlich, wenn Umfang = Kontakt. Der Schemaname der Beziehung zwischen dem Kontakt und der Entität, die vom Entitätsnamensfeld angegeben ist.|
| Übergeordnete Beziehung      | Nur erforderlich, wenn eine übergeordnete Entitätsberechtigung zugeordnet wurde. Der Schemaname der Beziehung zwischen der Entität, die vom Entitätsnamensfeld angegeben ist, und der Entität, die vom Entitätsnamensfeld für den Datensatz der übergeordnete Entitätsberechtigung angegeben ist.                                                                                     |
| Übergeordnete Entitätsberechtigung | Erforderlich, wenn Umfang= Übergeordnet.                                                                                                                                                                                                                                                            |
| Lesen                     | Recht, das steuert, ob der Benutzer einen Datensatz lesen kann.                                                                                                                                                                                                                                                               |
| Schreiben                    | Recht, das steuert, ob der Benutzer einen Datensatz aktualisieren kann.                                                                                                                                                                                                                                                             |
| Erstellen                   | Recht, das steuert, ob der Benutzer einen neuen Datensatz erstellen kann. Das Recht, einen Datensatz für einen Entitätstyp zu erstellen, bezieht sich nicht auf einen einzelnen Datensatz, sondern vielmehr auf eine Klasse von Entitäten.                                                                                                                             |
| Löschen                   | Recht, das steuert, ob der Benutzer einen Datensatz löschen kann.                                                                                                                                                                                                                                                             |
| Anfügen                   | Recht, das steuert, ob der Benutzer einen weiteren Datensatz an den angegebenen Datensatz anfügen kann. Die Zugriffsrechte "Anfügen" und "Anfügen an" funktionieren in Kombination. Jedes Mal, wenn ein Benutzer einen Datensatz an einen anderen anfügt, muss der Benutzer über beide Rechte verfügen. Wenn Sie beispielsweise eine Notiz an eine Anfrage anfügen, müssen Sie über das Anfügen-Zugriffsrecht für die Notiz verfügen sowie über das Anfügen an-Zugriffsrecht für die Anfrage, damit der Vorgang funktioniert.  |
| Anfügen an                | Recht, das steuert, ob der Benutzer den entsprechenden Datensatz an einen anderen Datensatz anfügen kann. Die Zugriffsrechte "Anfügen" und "Anfügen an" funktionieren in Kombination. Weitere Informationen finden Sie unter der Beschreibung fürs Anfügen.|
| | |

## <a name="global-permissions-for-tasks-related-to-leads"></a>Globale Berechtigungen für Aufgaben in Bezug auf Leads

In einem Szenario soll eine Liste mit Entitäten und Entitätsformulare verwendet werden, um alle Leads für das Portal für jeden in einer benutzerdefinierten "Lead-Manager"-Webrolle verfügbar zu machen. Im Lead-Bearbeitungs-Formular, das aufgerufen wird, wenn auf eine Leadzeile in der Liste geklickt wird, werden in einem Unterraster verbundene Aufgabendatensätze angezeigt. Diese Datensätze sollten für alle Mitarbeiter der Lead-Manager-Rolle verfügbar sein. Als erstes werden Global-Berechtigungen für Leads für alle Mitarbeiter der Lead Manager-Rolle erteilt.

Diese Rolle verfügt über eine Entitätsberechtigung für die Entität „Lead“ mit einem Global-Bereich.

Benutzer können in dieser Rolle auf alle Leads über Entitäts-Listen oder -Formulare im Portal zugreifen.

![Einem Lead globale Berechtigungen erteilen](../media/grant-global-permission-leads.png "Einem Lead globale Berechtigungen erteilen")  

Jetzt wird eine untergeordnete Berechtigung zur Global-Lead-Berechtigung hinzugefügt. Navigieren Sie bei geöffnetem übergeordnetem Berechtigungsdatensatz zum Unterraster **Untergeordnete Entitätsberechtigungen**, klicken Sie auf **Neu**, um eine Suche nach Entitätsberechtigungen zu öffnen, klicken Sie auf die Lupe, und klicken Sie auf **Neu**, um einen neuen Datensatz hinzuzufügen.

![Hinzufügen von Entitätsberechtigungen zu Webrollen](../media/add-entity-permission-web-role.png "Hinzufügen von Entitätsberechtigungen zu Webrollen")  

Wählen Sie die Entität als Aufgaben und den Umfang als „Übergeordnet“ aus. Beachten Sie, dass Sie die übergeordnete Beziehung (**Lead\_Tasks**) auswählen können. Diese Berechtigung bedeutet, dass ein Kontakt, der in einer Webrolle mit übergeordneter Berechtigung ist, dann für alle Aufgaben in Bezug auf Leads über die Global-Berechtigung verfügt.

Denken Sie daran: Damit Ihre Liste diese Berechtigungen berücksichtigt, müssen Sie die Entitäts-Berechtigungen in der Liste aktiviert haben UND es muss Aktionen geben, die es den Benutzern tatsächlich erlauben, die Aktionen auszuführen, für die ihre Berechtigungen gewährt wurden. Darüber hinaus müssen Berechtigungen auch im [Entitätsformular](entity-forms.md)-Datensatz aktiviert sein, und dieses Formular muss eine Seite anzeigen mit Unterraster für die Entität, die Sie mit untergeordneten Berechtigungen, in diesem Fall Aufgaben, aktivieren möchten. Darüber hinaus müssen Sie diese Entitätsformulare konfigurieren, um das Lesen und Erstellen für Aufgaben zu aktivieren, und die Formulare bearbeiten, um das Neueinstufungs-Suchfeld zu entfernen.  

![Bearbeiten eines Webseitenformulars](../media/edit-webpage-form.png "Bearbeiten eines Webseitenformulars")  

Dies gewährt dann Berechtigungen für alle Aufgaben in Bezug auf Leads. Wenn Aufgaben in einer Liste mit Entitäten angezeigt werden, wird im Wesentlichen ein Filter der Liste hinzugefügt, sodass nur Aufgaben, die mit einem Lead zusammenhängen, in der Liste angezeigt werden. In unserem Beispiel werden Sie mit einem Unterraster in ein Entitätsformular angezeigt.

![Aufgabenbeispiel](../media/tasks-example.png "Aufgabenbeispiel")  

## <a name="contact-scoped-permissions-for-tasks"></a>Kontakt-Umfang-Berechtigungen für Aufgaben

Ein anderes Beispiel: Es soll Zugriff auf Aufgaben gewährt werden, für die ein Kontakt dem übergeordneten Lead für diese Aufgabe zugeordnet wird. Dieses Szenario ist mit dem aus dem vorherigen Abschnitt fast identisch, außer dass in diesem Fall die übergeordnete Berechtigung über einen Kontakt-Umfang verfügt, statt einen Global-Umfang. Eine Beziehung muss für die übergeordnete Beziehung zwischen der Lead-Entität und der Kontakt-Entität angegeben werden.

Sobald diese Berechtigungen vorhanden sind, können Benutzer in der Lead Manager-Rolle auf Leads zugreifen, die mit ihnen direkt wie über die Kontakt-Umfangs-Berechtigung angegeben verknüpft sind, und auf Aufgaben, die mit den gleichen Leads wie durch den untergeordneten Berechtigungsdatensatz angegeben verknüpft sind.

### <a name="see-also"></a>Siehe auch

[Erstellen von Webrollen für Portale](create-web-roles.md)  
[Steuern des Webseitenzugriffs für Portale](webpage-access-control.md)