---
title: Freigeben einer Canvas-App | Microsoft-Dokumentation
description: Geben Sie Ihre Canvas-App frei, indem Sie anderen Benutzern die Berechtigung erteilen, die App auszuführen oder zu ändern.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 11/28/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 57a63ddf829e2a6c1062cad34e0f3c608d69afad
ms.sourcegitcommit: a06e3137e3cb36414f0d61825bbc687487ea6f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57804215"
---
# <a name="share-a-canvas-app-in-powerapps"></a>Freigeben einer Canvas-App in PowerApps

Nachdem Sie eine Canvas-App erstellt haben, die eine geschäftliche Anforderung behandelt, geben Sie an, welche Benutzer in Ihrer Organisation die App ausführen dürfen und welche sie ändern oder sogar erneut freigeben dürfen. Geben Sie jeden Benutzer anhand seines Namens an, oder geben Sie eine Sicherheitsgruppe in Azure Active Directory an. Wenn jeder von Ihrer App profitieren würde, geben Sie an, dass Ihre gesamte Organisation diese ausführen darf.

> [!IMPORTANT]
> Damit eine freigegebene App wie erwartet funktionieren kann, müssen Sie auch die Berechtigungen für die Datenquelle oder Quellen, auf denen die App basiert, verwalten, z.B. [Common Data Service für Apps](#common-data-service-for-apps) oder [Excel](share-app-data.md). Sie müssen möglicherweise auch [andere Ressourcen freigeben](share-app-resources.md), von denen die App abhängt, z.B. Flows, Gateways oder Verbindungen.

## <a name="prerequisites"></a>Voraussetzungen

Um eine App freizugeben, müssen Sie sie in der Cloud speichern (nicht lokal) und dann veröffentlichen.

- Geben Sie Ihrer App einen aussagekräftigen Namen und eine klare Beschreibung, damit Benutzer wissen, was die App bewirkt und sie so leicht in einer Liste finden können. Wählen Sie im Menü **Datei** in PowerApps Studio die **App-Einstellungen** aus, geben Sie einen Namen an, und tippen bzw. fügen Sie eine Beschreibung ein.

- Wenn Sie Änderungen vornehmen, müssen Sie die App speichern und erneut veröffentlichen, wenn andere Personen diese Änderungen sehen sollen.

## <a name="share-an-app"></a>Eine App freigeben

1. [Melden Sie sich bei PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und wählen Sie dann am linken Bildschirmrand **Apps** aus.

    ![Anzeigen der App-Liste](./media/share-app/file-apps.png)

1. Wählen Sie die app, die Sie freigeben, indem Sie deren Symbol auswählen möchten.

    ![Wählen Sie eine app](./media/share-app/select-app.png)

1. Wählen Sie in dem Banner **Freigabe**.

    ![Geöffneter Bildschirm „Freigeben“](./media/share-app/banner-share.png)

1. Geben Sie anhand des Namens oder Alias der Benutzer oder Sicherheitsgruppen in Azure Active Directory mit dem Sie die app freigeben möchten.

    - Die gesamte Organisation, führen Sie die app (jedoch nicht ändern oder freigeben) zulassen möchten, geben Sie **jeder** im Bedienfeld "freigeben".
    - Sie können eine app freigeben, mit einer Liste der Aliase, leicht zu merkende Namen oder eine Kombination der Argumente (z. B. **Jane Doe &lt; jane.doe@contoso.com>**) Wenn die Elemente durch Semikolons getrennt sind. Wenn mehr als eine Person hat den gleichen Namen, aber unterschiedliche Aliase, die erste Person, die gefunden werden zur Liste hinzugefügt werden. Eine QuickInfo angezeigt wird, wenn der Name oder Alias bereits über die Berechtigung verfügt, oder kann nicht aufgelöst werden. 
    
    ![Geben Sie Benutzer und mitbesitzern](./media/share-app/share-everyone.png)

    > [!NOTE]
    > Sie können keine app mit einer Verteilergruppe in Ihrer Organisation oder mit einem Benutzer oder Gruppe außerhalb Ihrer Organisation freigeben.

1. Wenn Sie zulassen möchten, die für die Sie freigeben die app zum Bearbeiten und freigeben (zusätzlich zur Ausführung), wählen Sie die **Mitbesitzer** Kontrollkästchen.

    Sie können keine gewähren **Mitbesitzer** Berechtigung einer Sicherheitsgruppe zu gruppieren, wenn Sie [erstellt die app aus in einer Projektmappe](add-app-solution.md).
    
    > [!NOTE]
    > Unabhängig von Berechtigungen können keine zwei Benutzer eine app zur gleichen Zeit bearbeiten. Wenn ein Benutzer die app zur Bearbeitung geöffnet wird, können andere Personen, führen Sie es aber nicht bearbeiten.

1. Wenn Ihre app mit Daten verbunden ist für die Benutzer Berechtigungen benötigen, geben Sie sie.

    Beispielsweise kann Ihre app mit einer Entität in CDS für Apps-Datenbank verbinden. Wenn Sie eine solche Anwendung freigeben, werden Sie von der Freigabe Bereich aufgefordert, Verwalten der Sicherheit für diese Entität.

    ![Festlegen von Berechtigungen](./media/share-app/set-permissions.png)

    Weitere Informationen zum Verwalten der Sicherheit für eine Entität finden Sie unter [verwalten Entitätsberechtigungen](share-app.md#manage-entity-permissions) weiter unten in diesem Thema.

1. Sollten Sie andere Personen leichter finden Ihre app, und wählen die **senden eine e-Mail-Einladung an neue Benutzer** Kontrollkästchen.

1. Wählen Sie am unteren Rand der Dateifreigabe-Bereich, **freigeben**.

    Jeder für die Sie die app freigegeben ausgeführt, sie in PowerApps Mobile auf einem mobilen Gerät oder in AppSource auf [Dynamics 365](https://home.dynamics.com) in einem Browser. Mitbesitzer bearbeiten und Freigeben der app in [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    Wenn Sie eine e-Mail-Einladung gesendet, kann alle Benutzer für die Sie die app freigegeben es ausführen, dazu einen Link in der Einladung.

    - Wenn ein Benutzer auf den Link auf einem mobilen Gerät auswählt, wird die app in PowerApps Mobile geöffnet.
    - Wenn ein Benutzer auf den Link auf einem Desktopcomputer auswählt, wird die app in einem Browser geöffnet.

    Mitbesitzer, die eine Einladung erhalten erhalten einen anderen Link, der die app zur Bearbeitung in PowerApps Studio geöffnet wird.

Sie können Berechtigungen für einen Benutzer oder eine Sicherheitsgruppe ändern, indem Sie ihren Namen auswählen und dann eine der folgenden Schritte aus:

- Um Mitbesitzer, führen Sie die app jedoch nicht mehr bearbeiten oder freigeben zu ermöglichen, deaktivieren Sie die **Mitbesitzer** Kontrollkästchen.
- Zum Beenden der Freigabe von der app für diesen Benutzer oder Gruppe wählen Sie das Symbol "entfernen (X)".

## <a name="security-group-considerations"></a>Überlegungen zu Sicherheitsgruppen

- Wenn Sie eine App für eine Sicherheitsgruppe, bestehende Mitglieder dieser Gruppe und jeden freigeben, der dieser Gruppe beitritt, verfügen alle über die von Ihnen angegebenen Berechtigungen für diese Gruppe. Jeder, der die Gruppe verlässt, verliert diese Berechtigung, es sei denn, die Person gehört noch zu einer anderen Gruppe, die über Zugriff verfügt, oder Sie verleihen der Person die Berechtigung als Einzelperson.
- Jedes Mitglied einer Sicherheitsgruppe besitzt dieselbe Berechtigung für eine App wie die Gruppe. Sie können allerdings für ein Mitglied oder mehrere Mitglieder dieser Gruppe tiefgreifendere Berechtigungen angeben, um diesen Personen besseren Zugriff zu gewähren. Beispielsweise Sie die Sicherheitsgruppe A die Berechtigung zum Ausführen einer app erteilen, aber Sie können auch festlegen, die zu dieser Gruppe gehört, Benutzer B **Mitbesitzer** Berechtigung. Jedes Mitglied der Sicherheitsgruppe kann die App ausführen, aber nur Benutzer B kann diese bearbeiten. Wenn Sie die Sicherheitsgruppe A geben **Mitbesitzer** und Benutzer B Berechtigung zum Ausführen der app, dieser Benutzer kann die app trotzdem bearbeiten.

## <a name="manage-entity-permissions"></a>Verwalten von Entitätsberechtigungen

### <a name="common-data-service-for-apps"></a>Common Data Service für Apps

Wenn Sie eine app basierend auf CDS für Apps erstellen, müssen Sie auch sicherstellen, dass die Benutzer, mit denen Sie die app freigeben, verfügen die entsprechenden Berechtigungen für die Entität bzw. Entitäten, die auf denen die app basiert. Insbesondere müssen die Benutzer einer Sicherheitsrolle gehören, die Aufgaben wie erstellen, lesen, schreiben und Löschen von Datensätzen mit relevanten ausführen können. In vielen Fällen sollten Sie eine oder mehrere benutzerdefinierte Sicherheitsrollen mit den genauen Berechtigungen zu erstellen, die Benutzer benötigen, um die app auszuführen. Sie können jeden Benutzer nach Bedarf dann eine Rolle zuweisen.

> [!NOTE]
> Während ich dies schreibe, können Sie Sicherheitsrollen für einzelne Benutzer jedoch nicht für Sicherheitsgruppen zuweisen.

#### <a name="prerequisite"></a>Voraussetzung

Für die nächsten beiden Verfahren müssen Sie über **Systemadministratorberechtigungen** für eine CDS for Apps-Datenbank verfügen.

#### <a name="create-a-security-role"></a>Sicherheitsrolle erstellen

1. Wählen Sie im Bereich Freigabe **Festlegen von Berechtigungen** unter **Datenberechtigungen**, und wählen Sie dann die **Sicherheitsrollen** Link.

    ![Öffnen von Sicherheitsrollen](media/share-app/security-roles.png)

1. Wählen Sie unter **Alle Rollen** **Neu** aus, tippen oder geben Sie dann einen Namen für die Rolle, die Sie erstellen, ein.

    ![Sicherheitsgruppe erstellen](media/share-app/new-role.png)

1. Wählen Sie mindestens eine Registerkarte aus, um die Entität bzw. Entitäten zu suchen, die von Ihrer App verwendet werden. Wählen Sie anschließend die Berechtigungen aus, denen Sie die Sicherheitsrolle zuweisen möchten.

    Z. B. die folgende Grafik zeigt, dass die **Core Datensätze** Registerkarte enthält die **Konten** Entität und Benutzern, denen diese Sicherheitsrolle zugewiesen wurde, zu erstellen, lesen, schreiben und Löschen von Datensätzen in dieser Entität können .

    ![Berechtigungen angeben](media/share-app/grant-access.png)

1. Klicken Sie auf **Speichern und schließen**.

#### <a name="assign-a-user-to-a-role"></a>Benutzer einer Rolle zuweisen

1. Wählen Sie im Bereich Freigabe **Festlegen von Berechtigungen** unter **Datenberechtigungen**, und wählen Sie dann die **Benutzer** Link.

    ![Verknüpfung „Benutzer“](media/share-app/open-users.png)

1. Tippen oder geben Sie in der oberen rechten Ecke den Namen des Benutzers ein, dem die Rolle zugewiesen werden soll, und klicken Sie dann auf das Suchsymbol.

    ![Nach Benutzern suchen](media/share-app/search-users.png)

1. Zeigen Sie in den Suchergebnissen auf das gewünschte Ergebnis, und aktivieren Sie dann das Kontrollkästchen, das angezeigt wird.

1. Wählen Sie oben im Banner **Rollen verwalten** aus.

1. Wählen Sie im angezeigten Dialogfeld die Kontrollkästchen für **Common Data Service-Benutzer** und die Rolle, die der Benutzer für Ihre app benötigt, und wählen Sie dann **OK.**

    ![Benutzer einer Rolle zuweisen](media/share-app/assign-users.png)

### <a name="common-data-service-previous-version"></a>Common Data Service (vorherige Version)

Wenn Sie eine app, die auf einer älteren Version von Common Data Service basiert freigeben, müssen Sie die Laufzeitberechtigung für den Dienst separat erteilen. Wenn Sie nicht über diese Berechtigung haben, finden Sie unter den umgebungsadministrator.
