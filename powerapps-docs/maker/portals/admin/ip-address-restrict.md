---
title: Einschränken des Zugriffs auf ein Portal mithilfe der IP-Adresse | MicrosoftDocs
description: Anweisungen zum Einschränken des Portal Zugriffs durch die IP-Adresse.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da8e6ac6d4e86a12ba196393073706c3705e4a92
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543014"
---
# <a name="restrict-portal-access-by-ip-address"></a>Einschränken des Portal Zugriffs durch IP-Adresse

Das Portal ist bei der Bereitstellung öffentlich und kann von jedem beliebigen Computer zugänglich gemacht werden. Nun können Sie den Zugriff auf Ihr Portal aus einer Liste von IP-Adressen einschränken. Beispielsweise kann es sein, dass eine Regierungsorganisation ihren Inhalt nur innerhalb Ihres Unternehmensnetzwerks übernehmen möchte. Eine kommerzielle Organisation möchte das Portal möglicherweise nur dann anzeigen, wenn es veröffentlicht wird, und nicht während der Entwicklung, um Datenverluste zu vermeiden.

Wenn eine Anforderung an das Portal von einem beliebigen Benutzer generiert wird, wird die IP-Adresse anhand der Zulassungsliste ausgewertet. Wenn die IP-Adresse nicht in der Liste enthalten ist, zeigt das Portal eine Webseite mit dem Statuscode HTTP 403 an.

Um IP-Adressen hinzuzufügen oder zu entfernen, müssen Sie eine der folgenden Rollen zuweisen:
- Office 365 (globaler Administrator) 
- Dienst Administrator. Weitere Informationen: [Verwenden der Dienst Administrator Rolle zum Verwalten Ihres](https://technet.microsoft.com/library/mt793847.aspx) Mandanten  
- System Administrator der Common Data Service Umgebung, die für das Portal ausgewählt wurde

## <a name="add-an-ip-address"></a>IP-Adresse hinzufügen

Um den Zugriff auf ein Portal über eine IP-Adresse oder einen Satz von IP-Adressen zuzulassen, können Sie die IP-Adressen der Liste hinzufügen. Dies ermöglicht den Zugriff auf das Portal nur aus der Liste der hinzugefügten IP-Adressen. Wenn Sie keine IP-Adresse hinzufügen, kann auf das Portal von allen IP-Adressen aus zugegriffen werden.

Nachdem Sie der Einschränkungs Liste eine IP-Adresse hinzugefügt haben, ist nur die angegebene IP-Adresse auf das Portal zugreifen. Wenn Sie versuchen, über eine andere IP-Adresse auf das Portal zuzugreifen, wird der Zugriff verweigert, und eine Webseite mit dem Statuscode HTTP 403 wird angezeigt. Der Inhalt dieser Webseite ist statisch und kann nicht geändert werden.

> [!div class=mx-imgBorder]
> ![HTML 403-Fehler](../media/ip-address-page-error.png "HTML 403-Fehler")  

> [!NOTE]
> Sie müssen eine öffentliche IP-Adresse angeben, auf die über das Portal zugegriffen werden kann. Der Zugriff auf die private IP-Adresse ist über das Portal nicht möglich.

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu **Einrichten der IP-Adress Einschränkung**. Eine Liste mit IP-Adressen und deren Typ wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![Einrichten der IP-Adress Einschränkung](../media/set-up-ip-address-restrict.png "Einrichten einer IP-Adresseinschränkung")

3.  Wählen Sie auf der Seite Einschränkungen für IP-Adressen einrichten die Option **Neu hinzufügen**aus.

4.  Geben Sie im Fenster IP-Adresse hinzufügen die folgenden Werte ein:

    - **Typ der IP-Adresse auswählen**: Wählen Sie aus, ob die IP-Adresse IPv4 oder IPv6 ist.

    - **IP-Adresse in CIDR-Notation angeben**: Geben Sie die IP-Adresse in CIDR-Notation an. Weitere Informationen: [Classless Inter-Domain Routing](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![IP-Adresse hinzufügen](../media/add-ip-address.png "IP-Adresse hinzufügen")    

5.  Wählen Sie **Konfigurieren**aus.

## <a name="remove-an-ip-address"></a>Entfernen einer IP-Adresse

Um den Zugriff auf ein Portal aus einer zuvor zulässigen IP-Adresse zu entfernen, können Sie die IP-Adresse aus der Liste entfernen. Wenn Sie alle IP-Adressen entfernen, kann auf das Portal von allen IP-Adressen aus zugegriffen werden.

1.  Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2.  Wechseln Sie zu **Einrichten der IP-Adress Einschränkung**. Eine Liste mit IP-Adressen und deren Typ wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![Einrichten der IP-Adress Einschränkung](../media/set-up-ip-address-restrict.png "Einrichten einer IP-Adresseinschränkung")

3.  Wählen Sie neben der zu entfernenden IP-Adresse die **Option IP-Adresse (x) entfernen** aus.

4.  Wählen Sie in der Bestätigungsmeldung **Entfernen** aus.

