---
title: Beschränken des Zugriffs auf ein Portal über die IP-Adresse | MicrosoftDocs
description: Anleitung zum Einschränken des Portalzugriffs mit IP-Adressen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="restrict-portal-access-by-ip-address"></a>Einschränken des Portalzugriffs mit IP-Adressen

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Das Portal ist öffentlich, wenn es bereitgestellt und von jedem von jedem Computer aus zugänglich ist. Jetzt können Sie Zugriff auf das Portal von einer Liste von IP-Adressen beschränken. Beispielsweise möchte eine Regierungsorganisation den Inhalt nur im Firmennetzwerks zur Verfügung stellen. Eine Handelsorganisation will das Portal nur anzeigen, wenn es veröffentlicht ist und nicht während es scih in der Entwicklung befindet, um Datenenverluste zu vermeiden.

Wenn eine Anfrage mit dem Portal von einem beliebigen Benutzer erstellt wird, wird ihre IP-Adresse für die Zulassungsliste ausgewertet. Wenn die IP-Adresse nicht in der Liste angezeigt wird, wird das Portal einer Webseite mit einem 403-Statuscode angezeigt.

Um IP-Adressen hinzufügen oder zu entfernen, müssen Sie einer der folgenden Aufgaben zugewiesen werden:
- Globaler Office 365-Administrator 
- -Dienstadministrator. Mehr Informationen: [Verwenden Sie die Service-Administrationsrolle, um Ihren Mandanten zu verwalten](https://technet.microsoft.com/en-us/library/mt793847.aspx).  
- Systemadministrator der für das Portal ausgewählten Umgebung

## <a name="add-an-ip-address"></a>Eine IP-Adresse hinzufügen

Um den Zugriff zu einem Portal von einer IP-Adresse oder einem Satz IP-Adressen zu erlauben, können Sie die IP-Adressen der Liste hinzufügen. Dies ermöglicht das nur über die Liste der hinzugefügten IP-Adressen zugegriffen werden, das. Sofern Sie keine IP-Adresse hinzufügen, ist das Portal von allen IP-Adressen verfügbar.

Wenn Sie eine IP-Adresse einer Einschränkungsliste hinzufügen, ist das Portal nur für die angegebene IP-Adresse verfügbar. Wenn Sie versuchen, auf das Portal von allen anderen IP-Adressen zuzugreifen, wird der Zugriff und eine Webseite mit einem 403-Statuscode angezeigt. Der Inhalt der Webseite ist statisch und kann nicht geändert werden.

> [!div class=mx-imgBorder]
> ![HTML 403 Fehler](../media/ip-address-page-error.png "HTML 403 Fehler")  

> [!NOTE]
> Sie müssen einen öffentlichen IP-Adresse angeben, auf die über das Portal zugegriffen werden kann. Auf Private IP-Adresse kann nicht über das Portal zugegriffen werden.

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Gehen Sie zu **IP-Adresseinschränkung einrichten** Eine Liste von IP-Adressen und ihr Typ wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![IP-Adressen-Einschränkung einrichten](../media/set-up-ip-address-restrict.png "IP-Adressen-Einschränkung einrichten")

3.  Wählen Sie auf der Seite IP-Adressbeschränkung einrichten die Option **Neu hinzufügen**.

4.  Im Fenster "Geben Sie eine IP-Adressen ein" geben Sie die folgenden Werte ein:

    - **Wählen Sie die IP-Adresse aus**: Wählen Sie aus, ob die IP-Adresse IPv4 oder IPv6 ist.

    - **IP-Adresse in CIDR-Notation angeben**: Geben Sie die IP-Adresse CIDR-Notation an. Weitere Informationen: [Klassenlose domänenübergreifende Weiterleitung](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![Hinzufügen einer IP-Adresse](../media/add-ip-address.png "Hinzufügen einer IP-Adresse")    

5.  Wählen Sie **Konfigurieren** aus.

## <a name="remove-an-ip-address"></a>Eine IP-Adresse entfernen

Um den Zugriff in einem Portal von einer zuvor zulässigen IP-Adresse zu entfernen, können Sie die IP-Adresse aus der Liste entfernen. Wenn Sie alle IP-Adresse entfernen, ist ist das Portal von allen IP-Adressen aus verfügbar.

1.  Öffnen Sie das [Admin Center für PowerApps-Portale](admin-overview.md).

2.  Gehen Sie zu **IP-Adresseinschränkung einrichten** Eine Liste von IP-Adressen und ihr Typ wird angezeigt.

    > [!div class=mx-imgBorder]
    > ![IP-Adressen-Einschränkung einrichten](../media/set-up-ip-address-restrict.png "IP-Adressen-Einschränkung einrichten")

3.  Wählen Sie **Eine IP-Adresse entfernen (x)** neben der IP-Adresse, die entfernt werden soll.

4.  Wählen Sie in der Bestätigungsmeldung **Entfernen** aus.

