---
title: Steuern des Webseiten Zugriffs für ein Portal | MicrosoftDocs
description: Anweisungen zum Erstellen von Webseiten-Zugriffs Steuerungs Regeln für ein Portal.
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551069"
---
# <a name="control-webpage-access-for-portals"></a>Steuern des Webseiten Zugriffs für Portale

Zugriffs Steuerungs Regeln für Webseiten sind Regeln, die Sie für Ihre Website erstellen, um sowohl die Veröffentlichungs Aktionen zu steuern, die eine webrolle auf den Seiten Ihrer Website ausführen kann, als auch zu steuern, welche Seiten von welchen Webrollen angezeigt werden. Die Entität "Webseiten Zugriff" weist die folgenden Attribute auf:


|    Name     |                                                                                                                                                                  Beschreibung                                                                                                                                                                   |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Name     |                                                                                                                                                        Ein beschreibender Name für die Regel.                                                                                                                                                        |
|   Website   |                                                                                                           Die Website, für die diese Regel gilt. muss mit der Website der Seite, auf die diese Regel angewendet wird, abgestimmt werden. Filtert die Webseite.                                                                                                           |
|  Webseite   |                            Die Webseite, für die diese Regel gilt. Die Regel wirkt sich nicht nur auf die Seite, sondern auf alle untergeordneten Seiten der Seite aus. Daher wählt dieses Attribut die Verzweigung der Website aus, auf die die Regel angewendet werden soll. Wenn eine Regel auf die Startseite angewendet wird, gilt sie für das gesamte Portal.                            |
|    Right    |                                                                                                                                    [Ändern](#grant-change) oder [beschränken Sie den Lesevorgang weiter](#restrict-read) unten.                                                                                                                                     |
|    Umfang    | <ul><li><strong>Alle Inhalte</strong>: alle Nachfolger Inhalte sind in der Sicherheitsüberprüfung enthalten.</li><li><strong>Direkte untergeordnete Webdateien ausschließen</strong>: alle untergeordneten Webdateien, die direkt mit dieser Webseite verknüpft sind, sind von der Sicherheitsüberprüfung ausgeschlossen. Dies schließt keine untergeordneten Elemente aus.</li></ul>Standardmäßig ist der gesamte Inhalt ausgewählt. |
| Beschreibung |                                                                                                                                                     Optionale Eine Beschreibung der Regel.                                                                                                                                                      |

Nachdem Sie eine neue Zugriffs Steuerungs Regel erstellt haben, ordnen Sie Sie einer Seite zu. Dadurch wirkt sich dies auf die Seite aus, der Sie die Regel zuweisen, und alle untergeordneten Seiten&mdash;mit anderen Worten: der gesamte Branch der Website.

Es gibt zwei Arten von Zugriffs Steuerungs Regeln: Gewährung von Änderungen und Einschränken der Lesevorgänge.

## <a name="grant-change"></a>Änderung erteilen

Durch die Gewährung von Änderungen kann ein Benutzer in einer webrolle, die der Regel zugeordnet ist, Inhalts Änderungen für diese Seite und alle untergeordneten Seiten dieser Seite veröffentlichen. Die Änderungs Änderung hat Vorrang vor dem Einschränken der Lesevorgänge. Angenommen, Sie haben einen News-Abschnitt der Website, der von Benutzern in der webrolle "News Editor" bearbeitet werden soll. Diese Benutzer haben möglicherweise keinen Zugriff auf die gesamte Website, und die gesamte Website kann nicht bearbeitet werden. in diesem Branch verfügen Sie jedoch über eine vollständige Inhalts Veröffentlichungs Autorität. Erstellen Sie eine Webseiten-Zugriffs Steuerungs Regel namens "News Publishing Publishing to News Editoren".

Als nächstes legen Sie die Berechtigung zum Gewähren von Änderungen und der Webseite auf der übergeordneten Seite der gesamten Nachrichtenverzweigung Ihrer Site fest. Anschließend weisen Sie diese webrolle allen Kontakten zu, die Sie als News-Editoren festlegen möchten. Beachten Sie, dass ein Benutzer viele Webrollen haben kann.

Eine Regel zum Erteilen von Änderungen sollte immer in jedem Portal vorhanden sein, für das Sie die Front-seitige Bearbeitung aktivieren möchten. Diese Regel gilt für die Startseite der Website, sodass Sie die Standardregel für den gesamten Standort ist. Diese Regel wird mit einer webrolle verknüpft, die die Administrator Rolle für die Site darstellen soll. Benutzer, denen Rechte zum Veröffentlichen von Inhalten gewährt werden sollen, werden dieser Rolle zugewiesen.

## <a name="restrict-read"></a>Lesezugriff einschränken
Mithilfe der Regel zum Einschränken von Lese Vorschauen werden die Anzeige einer Seite (und der zugehörigen untergeordneten Seiten) und deren Inhalt auf bestimmte Benutzer beschränkt. Während die Grant-Änderung eine einschränkende Regel ist (Sie gewährt die Möglichkeit, für Ihre Benutzer etwas zu tun), ist das Einschränken von Lese vorhalten eine einschränkende Regel, da eine Aktion auf eine begrenzte Anzahl von Benutzern beschränkt wird. Angenommen, Sie haben einen Abschnitt der Website, der nur von Mitarbeitern verwendet werden soll. Sie können das Lesen dieser Verzweigung auf Personen in der Mitarbeiter-webrolle beschränken. Erstellen Sie eine neue Regel mit dem Namen "Lesezugriff auf Mitarbeiter beschränken".

Anschließend würden Sie das Recht festlegen, das Lesen und die Seite auf die Seite am oberen Rand der Verzweigung einzuschränken, die nur von Mitarbeitern gelesen werden soll. Ordnen Sie dann diese Regel der Employee-webrolle zu, und weisen Sie dieser Rolle dann Benutzer zu.

> [!Note]
> Wenn Sie das Recht **Lesen** auf die Stamm Seite der Startseite einer Website anwenden und die Option direkte untergeordnete **Webdateien** als **Bereich**ausschließen auswählen, sind die direkten untergeordneten Webdateien der Startseite für alle Benutzer zugänglich.

### <a name="see-also"></a>Siehe auch

[Erstellen von Webrollen für Portale](create-web-roles.md)  
[Hinzufügen von Daten Satz basierter Sicherheit mithilfe von Entitäts Berechtigungen für Portale](assign-entity-permissions.md)
