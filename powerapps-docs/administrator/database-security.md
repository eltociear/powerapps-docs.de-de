---
title: Konfigurieren der Sicherheit von Umgebungen | Microsoft-Dokumentation
description: In diesem Artikel wird das Konfigurieren der Umgebungssicherheit erläutert.
services: powerapps
suite: powerapps
documentationcenter: na
author: manasmams
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: 425600830a64652df7084a0222c02273a1607818
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="configure-environment-security"></a>Konfigurieren der Sicherheit von Umgebungen
Der Common Data Service verwendet ein rollenbasiertes Sicherheitsmodell, das den sicheren Zugriff auf die Datenbank unterstützt. In diesem Thema wird erläutert, wie die Sicherheitsartefakte erstellt werden, die Sie zum Schützen von Apps benötigen. Die Benutzerrollen steuern den Laufzeitzugriff auf Daten und sind getrennt von den Umgebungsrollen, die die Umgebungsadministratoren und Umgebungsersteller regeln. Einen Überblick über die Umgebungen finden Sie unter [Environments overview (Überblick über Umgebungen)](environments-overview.md).

## <a name="assign-security-roles-to-users"></a>Zuweisen von Sicherheitsrollen an Benutzer
Sicherheitsrollen steuern über mehrere Zugriffsebenen und Berechtigungen den Zugriff auf Daten durch den Benutzer. Mithilfe der verschiedenen Zugriffsebenen und Berechtigungen, die einer bestimmten Sicherheitsrolle zugeordnet sind, werden die Datenansicht für den Benutzer und die Interaktionen des Benutzers mit diesen Daten eingeschränkt.

Ein Umgebungsadministrator kann folgende Schritte im [PowerApps Admin Center][1] durchführen, um einem Benutzer oder einer Sicherheitsgruppe eine Umgebungsrolle zuzuweisen:

1. Wählen Sie die Umgebung aus der Tabelle mit den Umgebungen aus.

    ![](./media/environment-admin/environment-list-new.png)

2. Klicken Sie auf die Registerkarte **Sicherheit**.

3. Klicken Sie auf den Link, um die Umgebungsrollen in Dynamics 365 zu verwalten.

    ![](./media/environment-admin/Security-Link-D365.png)

4. Wählen Sie den Benutzer aus der Benutzerliste in der Umgebung aus.

    ![](./media/environment-admin/D365-Select-User.png)

5. Weisen Sie dem Benutzer die Rolle zu.

    ![](./media/environment-admin/D365-Assign-Role.png)

    > [!NOTE]
    > Derzeit können Rollen nur Benutzern zugewiesen werden. In Zukunft sollen auch Sicherheitsgruppen Rollen zugewiesen werden können.

6. Klicken Sie auf **OK**, um die Zuweisungen auf die Umgebungsrolle zu aktualisieren.


## <a name="predefined-security-roles"></a>Vordefinierte Sicherheitsrollen
Die PowerApps-Umgebung umfasst vordefinierte Sicherheitsrollen, die häufig verwendete Benutzeraufgaben mit Zugriffsebenen widerspiegeln, durch die nur auf die Unternehmensdaten zugegriffen werden kann, die mindestens erforderlich sind, um die App zu verwenden. Dabei handelt es sich um ein bewährtes Sicherheitsziel.

|Sicherheitsrolle  |*Datenbankberechtigungen  |Beschreibung |
|---------|---------|---------|
|Systemadministrator     |  Erstellen, lesen, schreiben, anpassen und Sicherheitsrollen       | Verfügt über umfassende Berechtigungen zum Anpassen oder Verwalten der Umgebung, einschließlich dem Erstellen, Verändern und Zuweisen von Sicherheitsrollen. Kann alle Daten in der Umgebung abrufen. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization).        |
|Systemanpasser     | Erstellen (selbst), lesen (selbst), schreiben (selbst), löschen (selbst), anpassen         | Verfügt über umfassende Berechtigungen zum Anpassen der Umgebung. Kann jedoch nur eigene Einträge zu Umgebungsentitäten abrufen. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization).        |
|Umgebungsersteller     |  Keine       | Kann mithilfe von Microsoft Flow neue Ressourcen erstellen, die einer Umgebung zugewiesen sind, einschließlich Apps, Verbindungen, benutzerdefinierter APIs, Gateways und Workflows. Verfügt jedoch nicht über Berechtigungen zum Zugreifen auf Daten innerhalb einer Umgebung. Weitere Informationen finden Sie unter [Environments overview (Übersicht zu Umgebungen)](https://powerapps.microsoft.com/blog/powerapps-environments/).        |
|Common Data Service-Benutzer     |  Lesen, erstellen (selbst), schreiben (selbst), löschen (selbst)       | Kann eine App innerhalb einer Umgebung ausführen und häufig verwendete Aufgaben für eigene Einträge durchführen.        |
|Delegat     | Im Auftrag eines anderen Benutzers handeln        | Ermöglicht es, als anderer Benutzer oder mit einer anderen Identität Code auszuführen.  Wird in der Regel mit einer anderen Sicherheitsrolle verwendet, damit auf Einträge zugegriffen werden kann. Weitere Informationen finden Sie unter [Annehmen der Identität eines anderen Benutzers](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user).        |

*Die Berechtigungen gelten global, sofern keine anderen Angaben gemacht werden.

- Mit der Umgebungserstellerrolle können nicht nur Ressourcen innerhalb einer Umgebung erstellt, sondern auch die Apps, die sie in einer Umgebung erstellt haben, an andere Benutzer in Ihrer Organisation verteilt werden. Die App kann für individuelle Benutzer freigegeben werden. Weitere Informationen finden Sie unter [Freigeben von Apps in PowerApps](../maker/canvas-apps/share-app.md).

- Benutzern, die Apps erstellen, die eine Verbindung mit der Datenbank herstellen, und die Entitäten und Sicherheitsrollen erstellen oder aktualisieren müssen, sollte ebenfalls die Rolle Systemanpasser sowie die Rolle Umgebungsersteller zugewiesen werden, da die Rolle Umgebungsersteller keine Berechtigungen auf die Datenbank hat.


## <a name="create-or-configure-a-custom-security-role"></a>Erstellen oder Konfigurieren einer benutzerdefinierten Sicherheitsrolle
Wenn Ihre App auf einer benutzerdefinierten Entität basiert, müssen Berechtigungen explizit angegeben werden, bevor Benutzer an der App arbeiten können. Dazu können Sie einen der folgenden Schritte ausführen.
- Erweitern Sie eine bereits vorhandene vordefinierte Sicherheitsrolle um Berechtigungen auf Einträge, die auf der benutzerdefinierten Entität basieren.
- Erstellen Sie eine benutzerdefinierte Sicherheitsrolle zum Verwalten von Berechtigungen für Benutzer der App.

Die Umgebung verwaltet möglicherweise die Einträge, die von mehreren Apps verwendet wird. Sie benötigen unter Umständen mehrere Sicherheitsrollen, um mit anderen Berechtigungen auf die Daten zugreifen zu können. Z.B.:
- Einige Benutzer (Typ A) müssen möglicherweise andere Einträge nur lesen, aktualisieren oder anfügen können. Daher sind die Berechtigungen ihrer Sicherheitsrolle auch nur auf diese Vorgänge beschränkt.
- Andere Benutzer benötigen möglicherweise nicht nur die gleichen Berechtigungen wie die Benutzer von Typ A, sondern auch Berechtigungen zum Erstellen, Anfügen an andere Einträge, Löschen und Freigeben. Daher werden für deren Sicherheitsrolle diese Vorgänge ebenfalls freigegeben.

Weitere Informationen zu Zugriffs- und Bereichsberechtigungen finden Sie unter [Sicherheitsrollen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

1. Wählen Sie im [PowerApps Admin Center][1] die Umgebung aus, in der Sie die Sicherheitsrolle aktualisieren möchten.

    ![](./media/environment-admin/choose-environment-updated.png)

2. Klicken Sie in der Registerkarte **Details** auf den zugehörigen Link, um die Umgebung im Dynamic 365 Admin Center zu verwalten.

3. Wählen Sie die Instanz aus, die denselben Namen wie die Umgebung hat, und klicken Sie auf „Öffnen“.

    ![](./media/database-security/glados-instance-list.png)

4. Klicken Sie im Header auf **Einstellungen** > **Sicherheit**.

    ![](./media/database-security/dyn365-settings-security.png)

5. Klicken Sie auf **Sicherheitsrollen**.

    ![](./media/database-security/dyn365-securityroles.png)

6. Klicken Sie auf **Neu**.

7. Über den Sicherheitsrollendesigner können Sie Aktionen wie „Lesen“, „Schreiben“ oder „Löschen“ auswählen sowie den Bereich der einzelnen Aktionen festlegen.

8. Klicken Sie auf die Registerkarte und suchen Sie nach Ihrer Entität, z.B. der Registerkarte **Benutzerdefinierte Entitäten**, um Berechtigungen für benutzerdefinierte Entitäten festzulegen.

9. Wählen Sie die Berechtigungen **Lesen, schreiben, anfügen** aus.

10. Klicken Sie auf **Speichern und schließen**.



<!--Reference links in article-->
[1]: https://admin.powerapps.com