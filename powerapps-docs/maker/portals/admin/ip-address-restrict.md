---
title: Beschränken des Zugangs auf ein Portal mithilfe der IP-Adresse | MicrosoftDocs
description: Anleitung zum Einschränken des Portalzugriffs mit IP-Adressen.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 0916ec5899c347012c23e87cefcf34edd282e566
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978455"
---
# <a name="restrict-portal-access-by-ip-address"></a>Einschränken des Portalzugriffs mit IP-Adressen

Das Portal ist öffentlich, wenn es bereitgestellt und von jedem von jedem Computer aus zugänglich ist. Jetzt können Sie Zugriff auf das Portal von einer Liste von IP-Adressen beschränken. Beispielsweise möchte eine Regierungsorganisation den Inhalt nur im Firmennetzwerks zur Verfügung stellen. Eine Handelsorganisation will das Portal nur anzeigen, wenn es veröffentlicht ist und nicht während es scih in der Entwicklung befindet, um Datenenverluste zu vermeiden.

Wenn eine Anfrage mit dem Portal von einem beliebigen Benutzer erstellt wird, wird ihre IP-Adresse für die Zulassungsliste ausgewertet. Wenn die IP-Adresse nicht in der Liste angezeigt wird, wird das Portal einer Webseite mit einem 403-Statuscode angezeigt.

Um IP-Adressen hinzufügen oder zu entfernen, müssen Sie einer der folgenden Aufgaben zugewiesen werden:
- Globaler Office 365-Administrator 
- -Dienstadministrator. Mehr Informationen: [Verwenden Sie die Service-Administrationsrolle, um Ihren Mandanten zu verwalten](https://technet.microsoft.com/library/mt793847.aspx).  
- Systemadministrator der Common Data Service-Umgebung, die für das Portal ausgewählt ist

## <a name="add-an-ip-address"></a>Eine IP-Adresse hinzufügen

Um den Zugriff zu einem Portal von einer IP-Adresse oder einem Satz IP-Adressen zu erlauben, können Sie die IP-Adressen der Liste hinzufügen. Dies ermöglicht das nur über die Liste der hinzugefügten IP-Adressen zugegriffen werden, das. Sofern Sie keine IP-Adresse hinzufügen, ist das Portal von allen IP-Adressen verfügbar.

Wenn Sie eine IP-Adresse einer Einschränkungsliste hinzufügen, ist das Portal nur für die angegebene IP-Adresse verfügbar. Wenn Sie versuchen, auf das Portal von allen anderen IP-Adressen zuzugreifen, wird der Zugriff und eine Webseite mit einem 403-Statuscode angezeigt. Der Inhalt der Webseite ist statisch und kann nicht geändert werden.

> [!div class=mx-imgBorder]
> ![HTML 403 Fehler](../media/ip-address-page-error.png "HTML 403 Fehler")  

> [!NOTE]
> Sie müssen einen öffentlichen IP-Adresse angeben, auf die über das Portal zugegriffen werden kann. Auf Private IP-Adresse kann nicht über das Portal zugegriffen werden.

1.  Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2.  Gehen Sie zu **IP-Adresseinschränkung einrichten** Eine Liste von IP-Adressen und ihr Typ wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![IP-Adresseinschränkung einrichten](../media/set-up-ip-address-restrict.png "IP-Adresseinschränkung einrichten")

3.  Wählen Sie auf der Seite IP-Adressbeschränkung einrichten die Option **Neu hinzufügen**.

4.  Im Fenster "Geben Sie eine IP-Adressen ein" geben Sie die folgenden Werte ein:

    - **Wählen Sie die IP-Adresse aus**: Wählen Sie aus, ob die IP-Adresse IPv4 oder IPv6 ist.

    - **IP-Adresse in CIDR-Notation angeben**: Geben Sie die IP-Adresse CIDR-Notation an. Weitere Informationen: [Klassenlose domänenübergreifende Weiterleitung](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![Eine IP-Adresse hinzufügen](../media/add-ip-address.png "Eine IP-Adresse hinzufügen")    

5.  Wählen Sie **Konfigurieren** aus.

## <a name="remove-an-ip-address"></a>Eine IP-Adresse entfernen

Um den Zugriff in einem Portal von einer zuvor zulässigen IP-Adresse zu entfernen, können Sie die IP-Adresse aus der Liste entfernen. Wenn Sie alle IP-Adresse entfernen, ist ist das Portal von allen IP-Adressen aus verfügbar.

1.  Öffnen Sie das [Admin Center für Power Apps-Portale](admin-overview.md).

2.  Gehen Sie zu **IP-Adresseinschränkung einrichten** Eine Liste von IP-Adressen und ihr Typ wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![IP-Adresseinschränkung einrichten](../media/set-up-ip-address-restrict.png "IP-Adresseinschränkung einrichten")

3.  Wählen Sie **Eine IP-Adresse entfernen (x)** neben der IP-Adresse, die entfernt werden soll.

4.  Wählen Sie in der Bestätigungsmeldung **Entfernen** aus.

