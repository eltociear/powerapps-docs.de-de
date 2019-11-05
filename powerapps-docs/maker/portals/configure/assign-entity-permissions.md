---
title: Hinzufügen von Daten Satz basierter Sicherheit mithilfe von Entitäts Berechtigungen für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen einer Entitäts Berechtigung und Zuweisen von Webrollen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 47730a2ba169b89534fa93221290c5598a95a8e8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553392"
---
# <a name="add-record-based-security-by-using-entity-permissions-for-portals"></a>Hinzufügen von Daten Satz basierter Sicherheit mithilfe von Entitäts Berechtigungen für Portale

Verwenden Sie zum Anwenden von Daten Satz basierter Sicherheit in Portalen auf einzelne Datensätze Entitäts Berechtigungen. Sie fügen den Webrollen Entitäts Berechtigungen hinzu, damit Sie Rollen in Ihrer Organisation definieren können, die logisch den Berechtigungen und Konzepten des Daten Satz Besitzes und des Zugriffs entsprechen, die mithilfe von Entitäts Berechtigungen eingeführt werden. Beachten Sie, dass ein bestimmter Kontakt zu einer beliebigen Anzahl von Rollen gehören kann und eine bestimmte Rolle eine beliebige Anzahl von Entitäts Berechtigungen enthalten kann. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Erstellen von Webrollen für Portale](create-web-roles.md) 

Obwohl Berechtigungen zum Ändern und Zugreifen auf URLs in einer Portal Site Zuordnung über die Inhalts Autorisierung erteilt werden, möchten Website-Manager auch Ihre benutzerdefinierten Webanwendungen schützen, die mit Entitäts Formularen und Entitäts Listen erstellt wurden. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Definieren von Entitäts Formularen](entity-forms.md) und [Definieren von Entitäts Listen](entity-lists.md)  

Um diese Features zu sichern, ermöglichen Entitäts Berechtigungen das gewähren präziser Rechte für beliebige Entitäten und die Aktivierung der Sicherheit auf Datensatzebene über Beziehungs Definitionen.

## <a name="add-entity-permissions-to-a-web-role"></a>Hinzufügen von Entitäts Berechtigungen zu einer webrolle

1.  Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2. Wechseln Sie zu **Portale** &gt; **Webrollen** , und öffnen Sie die webrolle, der Sie die Berechtigungen hinzufügen möchten. 

3. Wählen Sie **Hinzufügen** aus, um einer webrolle eine vorhandene Entitäts Berechtigung hinzuzufügen. 

4. Wählen Sie **neu** aus, um einen neuen Entitäts Daten Satz zu erstellen.

    ![Hinzufügen von Entitäts Berechtigungen zu einer webrolle](../media/add-entity-permission-web-role.png "Hinzufügen von Entitäts Berechtigungen zu einer webrolle")  

Beim Erstellen eines neuen Entitäts Berechtigungsdaten Satzes besteht der erste Schritt darin, die Entität zu bestimmen, die gesichert werden soll. Der nächste Schritt besteht im Definieren des Gültigkeits Bereichs, wie unten erläutert, und&mdash;für einen anderen Bereich als Global&mdash;die Beziehungen, die diesen Bereich definieren. Bestimmen Sie schließlich die Rechte, die der Rolle über diese Berechtigung gewährt werden. Beachten Sie, dass Rechte kumulativ sind. Wenn also ein Benutzer einer Rolle zugewiesen ist, die Lese-und Aktualisierungs Berechtigungen gewährt, verfügt der Benutzer über Lese-und Aktualisierungs Rechte für alle Datensätze, die sich zwischen den beiden Rollen überlappen.

> [!Note]
> Die Auswahl von CMS-Entitäten wie Webseiten und Webdateien ist ungültig und kann andere unbeabsichtigte Folgen haben. Das Portal bestätigt die Sicherheit von CMS-Entitäten auf der Grundlage von Inhalts Zugriffs Steuerungen, nicht von Entitäts Berechtigungen.

### <a name="global-scope"></a>Globaler Gültigkeitsbereich

Wenn einem Entitäts Berechtigungsdaten Satz mit Leseberechtigung eine Rolle mit globalem Gültigkeitsbereich gewährt wird, hat jeder Kontakt in dieser Rolle Zugriff auf alle Datensätze der definierten Entität. So können beispielsweise alle Leads, alle Konten usw. angezeigt werden. Diese Berechtigung wird automatisch von allen Entitäts Listen berücksichtigt. im Wesentlichen werden alle Datensätze entsprechend den Modell gesteuerten App-Ansichten angezeigt, die für diese Liste definiert wurden. Wenn ein Benutzer darüber hinaus versucht, über ein Entitäts Formular auf einen Datensatz zuzugreifen, auf den er keinen Zugriff hat, wird ein Berechtigungs Fehler ausgegeben.

### <a name="contact-scope"></a>Kontaktbereich

Mit dem Kontaktbereich hat ein angemeldeter Benutzer in der Rolle, für die der Berechtigungs Eintrag definiert ist, die Rechte, die durch diese Berechtigung gewährt werden, nur für Datensätze, die über eine definierte Beziehung mit dem Kontaktdaten Satz dieses Benutzers verknüpft sind.

In einer Entitäts Liste bedeutet dies, dass ein Filter zu allen Modell gesteuerten App-Ansichten hinzugefügt wird, die von dieser Liste angezeigt werden, wodurch nur Datensätze abgerufen werden, die direkt mit dem aktuellen Benutzer verknüpft sind. (Je nach Szenario kann sich diese Beziehung als Besitz-oder Verwaltungsrechte vorstellen.)

Entitäts Formulare erlauben nur die entsprechende Berechtigung zum Lesen, erstellen, schreiben usw., wenn diese Beziehung beim Laden des Datensatzes vorhanden ist. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Definieren von Entitäts Formularen und benutzerdefinierter Logik innerhalb eines Portals](entity-forms.md).  

### <a name="account-scope"></a>Kontobereich

Mit dem Kontobereich erhält ein angemeldeter Benutzer in der Rolle, für die der Berechtigungs Eintrag definiert ist, die Rechte, die durch diese Berechtigung gewährt werden, nur für Datensätze, die über eine definierte Beziehung mit dem übergeordneten Kontodaten Satz dieses Benutzers verknüpft sind.

### <a name="self-scope"></a>Self-Scope

Self-Scope ermöglicht Ihnen das Definieren der Rechte, die ein Benutzer für seinen eigenen Kontaktdaten Satz hat. Dadurch können Benutzer Entitäts Formulare oder Web Forms verwenden, um Änderungen an Ihrem eigenen Kontaktdaten Satz vorzunehmen, der mit dem Profil verknüpft ist. Beachten Sie, dass die Standardprofil Seite über ein spezielles, integriertes Formular verfügt, das es jedem Benutzer ermöglicht, ihre grundlegenden Kontaktinformationen zu ändern und Marketing Listen zu abonnieren. Wenn dieses Formular in Ihrem Portal (standardmäßig) enthalten ist, benötigen die Benutzer diese Berechtigung nicht, um es zu verwenden. Allerdings benötigen Sie diese Berechtigung, um benutzerdefinierte Entitäts Formulare oder Webformulare zu verwenden, die Ihren Benutzer Kontaktdaten Satz als Ziel haben.

### <a name="parental-scope"></a>Eltern Bereich

In diesem komplexesten Fall werden Berechtigungen für eine Entität erteilt, bei der es sich um eine Beziehung zwischen einer Entität handelt, für die bereits ein Entitäts Berechtigungsdaten Satz definiert wurde. Diese Berechtigung ist tatsächlich ein untergeordneter Datensatz der übergeordneten Entitäts Berechtigung.

Der übergeordnete Berechtigungsdaten Satz definiert eine Berechtigung und einen Bereich für eine Entität (wahrscheinlich globaler oder Kontaktbereich, obwohl das übergeordnete Element ebenfalls möglich ist). Diese Entität kann sich auf einen Kontakt (im Fall eines Kontakt Bereichs) oder global definiert beziehen. Wenn diese Berechtigung vorhanden ist, wird eine untergeordnete Berechtigung erstellt, die eine Beziehung zwischen einer anderen Entität und der in der übergeordneten Beziehung definierten Entität definiert.

Daher verfügen Benutzer in einer webrolle, die Zugriff auf Datensätze haben, die durch übergeordnete Entitäts Berechtigungen definiert sind, auch über Rechte, die durch den untergeordneten Berechtigungsdaten Satz für Datensätze definiert sind

### <a name="attributes-and-relationships"></a>Attribute und Beziehungen

In der folgenden Tabelle werden die Attribute für Entitäts Berechtigungen erläutert.

| Name                     | Beschreibung                                                                                                                                                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                     | Der beschreibende Name des Datensatzes. Dieses Feld ist erforderlich.                                                                                                                                                                                                                                                               |
| Entitäts Name              | Der logische Name der Entität, die gesichert werden soll, oder der die Kontakt Beziehung oder die übergeordnete Beziehung definiert, um eine verknüpfte Entität mit einer untergeordneten Berechtigung zu sichern. Dieses Feld ist erforderlich.                                                                                                                        |
| Bereich (obligatorisch)                   | <ul><li>**Global**: Erteilen von Berechtigungen für den Entitäts Daten Satz ohne Anforderung eines Besitzers (Contact).</li><li>**Contact**: Erteilen von Berechtigungen für den Entitäts Daten Satz, der über eine direkte Beziehung zu einem Besitzer (Kontakt) verfügt.</li><li>**Konto**: erteilen Sie Berechtigungen für den Entitäts Daten Satz, der über eine Beziehung zu einem Konto verfügt, das als Besitzer fungiert, vorausgesetzt, das Konto ist der übergeordnete Kunde des Kontakts.</li><li>**Parent**: Erteilen von Berechtigungen für den Entitäts Daten Satz durch die Kette der Beziehungen zwischen den übergeordneten Berechtigungen.</li></ul>|
| Beziehung kontaktieren     | Nur erforderlich, wenn Bereich = Kontakt. Der Schema Name der Beziehung zwischen dem Kontakt und der Entität, die im Feld Entitäts Name angegeben ist.|
| Übergeordnete Beziehung      | Nur erforderlich, wenn eine übergeordnete Entitäts Berechtigung zugewiesen wird. Der Schema Name der Beziehung zwischen der Entität, die im Feld Entitäts Name angegeben ist, und der Entität, die durch das Feld Entitäts Name auf dem zugehörigen übergeordneten Berechtigungsdaten Satz angegeben                                                                                     |
| Übergeordnete Entitäts Berechtigung | Nur erforderlich, wenn Scope = Parent.                                                                                                                                                                                                                                                            |
| Dazu                     | Berechtigung, die steuert, ob der Benutzer einen Datensatz lesen kann.                                                                                                                                                                                                                                                               |
| Schreibung                    | Berechtigung, die steuert, ob der Benutzer einen Datensatz aktualisieren kann.                                                                                                                                                                                                                                                             |
| Stelle                   | Berechtigung, die steuert, ob der Benutzer einen neuen Datensatz erstellen kann. Das Recht, einen Datensatz für einen Entitätstyp zu erstellen, gilt nicht für einen einzelnen Datensatz, sondern für eine Entitäts Klasse.                                                                                                                             |
| Lösch                   | Berechtigung, die steuert, ob der Benutzer einen Datensatz löschen kann.                                                                                                                                                                                                                                                             |
| Anfügen                   | Berechtigung, die steuert, ob der Benutzer einen anderen Datensatz an den angegebenen Datensatz anfügen kann. Das Anfügen und Anfügen an Zugriffsrechte funktioniert in Kombination. Jedes Mal, wenn ein Benutzer einen Datensatz an einen anderen anfügt, muss der Benutzer über beide Rechte verfügen. Wenn Sie z. b. einen Hinweis an einen Fall anfügen, müssen Sie über das Recht "Zugriff anfügen" für den Hinweis und das Recht "anfügen" für den Fall verfügen, dass der Vorgang funktioniert.  |
| Anfügen an                | Berechtigung, die steuert, ob der Benutzer den fraglichen Datensatz an einen anderen Datensatz anfügen kann. Das Anfügen und Anfügen an Zugriffsrechte funktioniert in Kombination. Weitere Informationen finden Sie in der Beschreibung für Append.|
| | |

## <a name="global-permissions-for-tasks-related-to-leads"></a>Globale Berechtigungen für Aufgaben im Zusammenhang mit Leads

In einem Szenario möchten wir möglicherweise eine Entitäts Liste und Entitäts Formulare verwenden, um alle Leads im Portal für alle Benutzer in einer benutzerdefinierten Lead-Manager-webrolle zu übernehmen. Im Formular für die Lead Bearbeitung, das immer dann gestartet wird, wenn eine führende Zeile in der Liste ausgewählt ist, werden in einem subraster Verwandte Aufgaben Datensätze angezeigt. Diese Datensätze sollten für alle Personen in der Lead Manager-Rolle zugänglich sein. Als ersten Schritt werden wir globale Berechtigungen für alle Benutzer in unserer Lead Manager-Rolle vergeben.

Diese Rolle verfügt über eine zugehörige Entitäts Berechtigung für die führende Entität mit einem globalen Gültigkeitsbereich.

Benutzer in dieser Rolle können auf alle Leads über Entitäts Listen oder Formulare im Portal zugreifen.

![Gewähren globaler Berechtigungen für einen Lead](../media/grant-global-permission-leads.png "Gewähren globaler Berechtigungen für einen Lead")  

Nun fügen wir der globalen Lead Berechtigung eine untergeordnete Berechtigung hinzu. Wenn der übergeordnete Berechtigungsdaten Satz geöffnet ist, wechseln Sie zum subraster untergeordnete **Entitäts Berechtigungen** , wählen Sie **neu** aus, um eine Suche nach Entitäts Berechtigungen zu öffnen, wählen Sie die Lupe aus, und wählen Sie dann **neu** aus, um einen neuen Datensatz

![Hinzufügen von Entitäts Berechtigungen zu einer webrolle](../media/add-entity-permission-web-role.png "Hinzufügen von Entitäts Berechtigungen zu einer webrolle")  

Wählen Sie die Entität als Aufgaben und den Bereich als Eltern aus. Beachten Sie, dass Sie die übergeordnete Beziehung (**Lead\_Tasks**) auswählen können. Diese Berechtigung impliziert, dass ein Kontakt, der in einer webrolle mit der übergeordneten Berechtigung enthalten ist, über eine globale Berechtigung für alle Aufgaben verfügt, die mit Leads verknüpft sind.

Beachten Sie, dass Sie für Ihre Liste diese Berechtigungen aktivieren müssen, wenn Sie Entitäts Berechtigungen für die Liste aktiviert haben und Aktionen vorliegen müssen, die es Benutzern ermöglichen, die Aktionen auszuführen, für die ihre Berechtigungen erteilt wurden. Außerdem müssen Berechtigungen für den [Entitäts Formular](entity-forms.md) Daten Satz aktiviert werden, und dieses Formular muss auf eine Seite mit einem untergeordneten Raster für die Entität, die Sie mit untergeordneten Berechtigungen aktivieren möchten, in diesem Fall Tasks. Darüber hinaus müssen Sie zum Aktivieren von Lese-oder Erstellungs Berechtigungen für Tasks diese Entitäts Formulare ebenfalls konfigurieren und die Formulare bearbeiten, um das Nachschlage Feld für die Suche zu entfernen.  

![Bearbeiten eines Webseiten Formulars](../media/edit-webpage-form.png "Bearbeiten eines Webseiten Formulars")  

Dadurch werden Berechtigungen für alle Aufgaben gewährt, die mit Leads verknüpft sind. Wenn Aufgaben in einer Entitäts Liste angezeigt werden, wird der Liste im Grunde ein Filter hinzugefügt, sodass nur Aufgaben in der Liste angezeigt werden, die mit einem Lead verknüpft sind. In unserem Beispiel werden Sie mit einem unter Raster auf einem Entitäts Formular angezeigt.

![Task Beispiel](../media/tasks-example.png "Task Beispiel")  

## <a name="contact-scoped-permissions-for-tasks"></a>Zugriffs bezogene Berechtigungen für Tasks

Ein weiteres Beispiel wäre, wenn Sie den Zugriff auf Aufgaben gestatten möchten, für die ein Kontakt mit dem übergeordneten Lead für diese Aufgabe verknüpft ist. Dieses Szenario ist beinahe identisch mit dem vorherigen Abschnitt, außer in diesem Fall hat die übergeordnete Berechtigung anstelle von Global einen Kontaktbereich. Eine Beziehung muss für die übergeordnete Beziehung zwischen der Lead-Entität und der Contact-Entität angegeben werden.

Nachdem diese Berechtigungen vorhanden sind, können Benutzer in der Lead-Manager-Rolle direkt auf Leads zugreifen, die mit Ihnen verknüpft sind, wie von der Contact-Scope-Berechtigung festgelegt, und auf Aufgaben im Zusammenhang mit denselben Leads zugreifen, die durch den untergeordneten Berechtigungsdaten Satz angegeben werden.

### <a name="see-also"></a>Siehe auch

[Erstellen von Webrollen für Portale](create-web-roles.md)  
[Steuern des Webseiten Zugriffs für Portale](webpage-access-control.md)