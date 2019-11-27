---
title: Steuern des Zugriffs auf Webseiten für ein Portal | MicrosoftDocs
description: Anweisungen, Webseitenzugriffssteuerung für ein Portal zu erstellen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5046f136d62a4a44618f66f60f72ab5166274264
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760440"
---
# <a name="control-webpage-access-for-portals"></a>Steuern des Webseitenzugriffs für Portale

Regeln für die Steuerung des Webseitenzugriffs sind Regeln, die Sie für Ihre Site erstellen, um sowohl die veröffentlichenden Aktionen, die eine Webrolle auf den Seiten Ihrer Website durchführen kann, zu steuern als auch zu kontrollieren, welche Seiten von welchen Webrollen angezeigt werden können. Die Webseiten-Zugriffsentität hat die folgenden Attribute:


|    Name     |                                                                                                                                                                  Beschreibung                                                                                                                                                                   |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Name     |                                                                                                                                                        Ein beschreibender Name für die Regel.                                                                                                                                                        |
|   Website   |                                                                                                           Die Website, für die diese Regel gilt, muss die Website der Seite ein, auf die diese Regel angewendet wird. Filtert die Webseite.                                                                                                           |
|  Webseite   |                            Die Webseite, für die diese Regel gilt. Die Regel wirkt sich nicht nur auf die Seite, sondern auch auf alle untergeordneten Seiten der Seite aus. Daher wählt dieses Attribut die Verzweigung der Website aus, für den die Regel gilt. Wenn eine Regel auf die Homepage angewendet wird, gilt sie auch für das gesamte Portal.                            |
|    Berechtigung    |                                                                                                                                    [Änderung gewähren](#grant-change) oder [Lesen einschränken](#restrict-read) unten.                                                                                                                                     |
|    Bereich    | <ul><li><strong>Gesamter Inhalt</strong>: Alle Nachfolgerinhalte sind in der Sicherheitsüberprüfung enthalten.</li><li><strong>Verknüpfte untergeordnete Webdateien ausschließen</strong>: Alle untergeordneten Webdateien, die direkt mit dieser Webseite verknüpft sind, sind von der Sicherheitsüberprüfung ausgeschlossen. Dies schließt die Nachfolgeelemente der untergeordneten Dateien nicht aus.</li></ul>Standardmäßig ist „Gesamter Inhalt“ ausgewählt. |
| Beschreibung |                                                                                                                                                     (Optional) Eine Beschreibung der Regel.                                                                                                                                                      |

Wenn Sie eine neue Zugriffssteuerungsregel erstellt haben, ordnen Sie sie einer Seite zu. Dadurch wird beides beeinfluss: die Seite, der Sie die Regel zuweisen, und alle untergeordneten Seiten – also die gesamte Verzweigung der Website.

Es gibt zwei Typen von Zugriffssteuerungsregeln: Änderung gewähren und Lesen einschränken.

## <a name="grant-change"></a>Änderung gewähren

Änderung gewähren ermöglicht es einem Benutzer in einer Webrolle, die der Regel zugewiesen ist, Inhaltsänderungen für diese Seite und alle untergeordneten Seiten dieser Seite zu veröffentlichen. Änderung gewähren hat Vorrang vor Lesen einschränken. Beispielsweise haben Sie einen Abschnitt mit Neuigkeiten auf der Site, den Benutzer in der Webrolle Neuigkeiten-Editor bearbeiten können sollen. Diese Benutzer haben möglicherweise keinen Zugriff auf die gesamte Site und können zweifellos nicht die gesamte Website bearbeiten, aber in dieser Verzweigung haben sie Veröffentlichungsberechtigungen für den gesamten Inhalt. Sie würden eine Regel für die Steuerung des Webseitenzugriffs namens „Veröffentlichung von Nachrichten für Nachrichten-Editoren gewähren“ erstellen.

Anschließen würden Sie das Recht „Änderung gewähren“ und die Webseite auf die übergeordnete Seite der gesamten Verzweigung „Neuigkeiten“ festlegen. Dann würden Sie diese Webrolle allen Kontakten zuweisen, die Neuigkeiten-Editoren sein sollen. Beachten Sie, dass ein Benutzer viele Webrollen haben kann.

Die Regel Änderung gewähren sollte in jedem Portal vorhanden sein, für das Sie die Frontside-Bearbeitung aktivieren möchten. Diese Regel gilt auf der Startseite der Website und so wird diese Regel die Standardregel für die gesamte Website. Diese Regel wird einer Webrolle zugeordnet, die die Administratorrolle für die Website darstellen soll. Benutzern, die Rechte für die Veröffentlichung von Frontside-Inhalt erhalten sollen, wird diese Rolle zugewiesen.

## <a name="restrict-read"></a>Lesen einschränken
Die Regel „Lesen einschränken” wird verwendet, um die Anzeige einer Seite (und von deren untergeordneten Seiten) und ihres Inhalts auf bestimmte Benutzer zu beschränken. Während „Änderung gewähren” eine berechtigende Regel (sie gewährt Benutzern die Möglichkeit, etwas zu tun) ist, ist die Regel „Lesen einschränken” eine restriktive Regel, da sie eine Aktion auf eine bestimmte Benutzergruppe beschränkt. Beispielsweise haben Sie einen der Abschnitt der Website, der nur von Mitarbeitern verwendet werden soll. Sie können das Lesen dieser Verzweigung auf Personen mit der Mitarbeiterwebrolle beschränken. Sie würden eine neue Regel namens „Lesen nur auf Mitarbeiter beschränken” erstellen.

Sie würden dann das Recht auf "Lesen einschränken" festlegen und die Seite auf die Seite oben in der Verzweigung festlegen, die nur von Mitarbeitern gelesen werden soll. Sie würden diese Regel dann der Webrolle "Mitarbeiter" zuordnen und dieser Rolle dann Benutzer zuweisen.

> [!Note]
> Wenn Sie **Lesen einschränken** direkt auf die Stammstartseite einer Website anwenden und **Verknüpfte untergeordnete Webdateien ausschließen** als **Umfang** auswählen, werden die Startseite und die verknüpften untergeordneten Seiten für alle Benutzer zugänglich.

### <a name="see-also"></a>Siehe auch

[Erstellen von Webrollen für Portale](create-web-roles.md)  
[Hinzufügen datensatzbasierter Sicherheit mithilfe der Entitätsberechtigungen für Portale](assign-entity-permissions.md)
