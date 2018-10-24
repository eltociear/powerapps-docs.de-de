---
title: Konfigurieren der Sicherheit von Umgebungen | Microsoft-Dokumentation
description: In diesem Artikel wird das Konfigurieren der Umgebungssicherheit erläutert.
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 10/10/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 3c8bdcb855b1e15cbebeb2a51fedf8aea7684286
ms.sourcegitcommit: c4369e5f31bb08716f1af1416f3f7510a4b926d5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072517"
---
# <a name="configure-environment-security"></a>Konfigurieren der Sicherheit von Umgebungen
Common Data Service (CDS) für Apps verwendet ein rollenbasiertes Sicherheitsmodell, das den sicheren Zugriff auf die Datenbank unterstützt. In diesem Thema wird erläutert, wie die Sicherheitsartefakte erstellt werden, die Sie zum Schützen von Apps benötigen. Die Benutzerrollen steuern den Laufzeitzugriff auf Daten und sind getrennt von den Umgebungsrollen, die die Umgebungsadministratoren und Umgebungsersteller regeln. Einen Überblick über die Umgebungen finden Sie unter [Environments overview (Überblick über Umgebungen)](environments-overview.md).

## <a name="assign-security-roles-to-users"></a>Zuweisen von Sicherheitsrollen für Benutzer
Sicherheitsrollen steuern über mehrere Zugriffsebenen und Berechtigungen den Zugriff auf Daten durch den Benutzer. Mithilfe der verschiedenen Zugriffsebenen und Berechtigungen, die einer bestimmten Sicherheitsrolle zugeordnet sind, werden die Datenansicht für den Benutzer und die Interaktionen des Benutzers mit diesen Daten eingeschränkt.

Ein Umgebungsadministrator kann folgende Schritte im [PowerApps Admin Center][1] durchführen, um einem Benutzer oder einer Sicherheitsgruppe eine Umgebungsrolle zuzuweisen:

1. Wählen Sie die Umgebung aus der Tabelle mit den Umgebungen aus.

    ![](./media/environment-admin/environment-list-new.png)

2. Klicken Sie auf die Registerkarte **Sicherheit**.

3. Zeigen Sie an, ob der Benutzer bereits in der Umgebung vorhanden ist, indem Sie **Liste der Benutzer in der Umgebung anzeigen** auswählen.
    
    ![](./media/database-security/security-viewuser.png)

4. Falls kein Benutzer vorhanden ist, können Sie den Benutzer über das PowerApps Admin Center hinzufügen. Fügen Sie den Benutzer hinzu, indem Sie die E-Mail-Adresse des Benutzers in Ihrer Organisation angeben und **Benutzer hinzufügen** auswählen.

    ![](./media/database-security/security-adduser.png)

    Warten Sie einige Minuten, um zu prüfen, ob der Benutzer in der Liste der Benutzer in der Umgebung verfügbar ist.
  
5. Wählen Sie den Benutzer aus der Benutzerliste in der Umgebung aus.

    ![](./media/environment-admin/D365-Select-User.png)

6. Weisen Sie dem Benutzer die Rolle zu.

    ![](./media/environment-admin/D365-Assign-Role.png)

    > [!NOTE]
    > Derzeit können Rollen nur Benutzern zugewiesen werden. In Zukunft sollen auch Sicherheitsgruppen Rollen zugewiesen werden können.

7. Klicken Sie auf **OK**, um die Zuweisungen auf die Umgebungsrolle zu aktualisieren.

## <a name="predefined-security-roles"></a>Vordefinierte Sicherheitsrollen
Die PowerApps-Umgebung umfasst vordefinierte Sicherheitsrollen, die häufig verwendete Benutzeraufgaben mit Zugriffsebenen widerspiegeln, durch die nur auf die Unternehmensdaten zugegriffen werden kann, die mindestens erforderlich sind, um die App zu verwenden. Dabei handelt es sich um ein bewährtes Sicherheitsziel.

|Sicherheitsrolle  |*Datenbankberechtigungen  |Beschreibung |
|---------|---------|---------|
|Systemadministrator     |  Erstellen, lesen, schreiben, anpassen und Sicherheitsrollen       | Verfügt über umfassende Berechtigungen zum Anpassen oder Verwalten der Umgebung, einschließlich dem Erstellen, Verändern und Zuweisen von Sicherheitsrollen. Kann alle Daten in der Umgebung abrufen. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization).        |
|Systemanpasser     | Erstellen (selbst), Lesen (selbst), Schreiben (selbst), Löschen (selbst), Anpassen         | Verfügt über umfassende Berechtigungen zum Anpassen der Umgebung. Kann jedoch nur eigene Datensätze zu Umgebungsentitäten abrufen. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization).        |
|Umgebungsersteller     |  Keine       | Kann mithilfe von Microsoft Flow neue Ressourcen erstellen, die einer Umgebung zugewiesen sind, einschließlich Apps, Verbindungen, benutzerdefinierter APIs, Gateways und Workflows. Verfügt jedoch nicht über Berechtigungen zum Zugreifen auf Daten innerhalb einer Umgebung. Weitere Informationen finden Sie unter [Environments overview (Übersicht zu Umgebungen)](https://powerapps.microsoft.com/blog/powerapps-environments/).        |
|Common Data Service-Benutzer     |  Lesen (selbst), Erstellen (selbst), Schreiben (selbst), Löschen (selbst)       | Kann eine App innerhalb einer Umgebung ausführen und häufig verwendete Aufgaben für eigene Datensätze durchführen.        |
|Delegat     | Im Auftrag eines anderen Benutzers handeln        | Ermöglicht es, als anderer Benutzer oder mit einer anderen Identität Code auszuführen.  Wird in der Regel mit einer anderen Sicherheitsrolle verwendet, damit auf Datensätze zugegriffen werden kann. Weitere Informationen finden Sie unter [Annehmen der Identität eines anderen Benutzers](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user).        |

*Die Berechtigungen gelten global, sofern keine anderen Angaben gemacht werden.

- Mit der Umgebungserstellerrolle können nicht nur Ressourcen innerhalb einer Umgebung erstellt, sondern auch die Apps, die sie in einer Umgebung erstellt haben, an andere Benutzer in Ihrer Organisation verteilt werden. Die App kann für individuelle Benutzer freigegeben werden. Weitere Informationen finden Sie unter [Freigeben von Apps in PowerApps](../maker/canvas-apps/share-app.md).

- Benutzern, die Apps erstellen, die eine Verbindung mit der Datenbank herstellen, und die Entitäten und Sicherheitsrollen erstellen oder aktualisieren müssen, sollte neben der Rolle „Umgebungsersteller“ auch die Rolle „Systemanpasser“ zugewiesen werden, da die Rolle „Umgebungsersteller“ keine Berechtigungen für die Datenbank besitzt.

## <a name="create-or-configure-a-custom-security-role"></a>Erstellen oder Konfigurieren einer benutzerdefinierten Sicherheitsrolle
Wenn Ihre App eine benutzerdefinierte Entität verwendet, müssen ihre Berechtigungen explizit in einer Sicherheitsrolle gewährt sein, bevor Ihre App verwendet werden kann.  Sie können entweder diese Berechtigungen in einer bestehenden Sicherheitsrolle hinzufügen oder eine benutzerdefinierte Sicherheitsrolle erstellen. Es gibt eine Reihe von Mindestberechtigungen, die erforderlich sind, damit die neue Sicherheitsrolle verwendet werden kann. Erfahren Sie mehr dazu unter [Minimum privileges to run app (Mindestberechtigungen zum Ausführen von Apps)](#minimum-privileges-to-run-app).

> [!TIP]
> Wenn Sie eine benutzerdefinierte Sicherheitsrolle mit den erforderlichen Mindestberechtigungen zum Ausführen einer App erstellen möchten, lesen Sie dazu den folgenden Abschnitt: [Minimum privileges to run app (Mindestberechtigungen zum Ausführen von Apps)](#minimum-privileges-to-run-app).

Die Umgebung verwaltet möglicherweise die Einträge, die von mehreren Apps verwendet werden. Sie benötigen unter Umständen mehrere Sicherheitsrollen, um mit anderen Berechtigungen auf die Daten zugreifen zu können. Z.B.:
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

## <a name="minimum-privileges-to-run-app"></a>Mindestberechtigungen zum Ausführen von Apps
Wenn Sie eine benutzerdefinierte Sicherheitsrolle erstellen, müssen Sie eine Reihe von Mindestberechtigungen in die Sicherheitsrolle einschließen, damit ein Benutzer die App ausführen kann. Wir haben eine Lösung erstellt, die Sie importieren können, und die eine Sicherheitsrolle mit den erforderlichen Mindestberechtigungen bietet.  

Laden Sie zuerst die Lösung aus dem Download Center herunter: [CDS for Apps minimum privilege security role (CDS für die Sicherheitsrolle der Mindestberechtigung für Apps)](http://download.microsoft.com/download/6/5/5/6552A30E-05F4-45F0-AEE3-9BB01E13118A/MinprivilegeSecRole_1_0_0_0.zip).

Folgen Sie dann den Anweisungen, um die Lösung zu importieren: [Importieren, aktualisieren und exportieren von Lösungen](../maker/common-data-service/import-update-export-solutions.md).

Wenn Sie die Lösung importieren, wird diese die Rolle **min prv apps use** erstellen, welche Sie kopieren können. Erfahren Sie dazu mehr unter [Erstellen Sie eine Sicherheitsrolle durch das Kopieren von Rollen](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/create-edit-security-role#create-a-security-role-by-copy-role). Wenn das Kopieren der Rolle abgeschlossen ist, navigieren Sie zu jeder Registerkarte,Core Records (Kerndatensätze), Business Management (Unternehmensmanagement), Customization (Anpassung) und so weiter, und stellen Sie die entsprechenden Berechtigungen ein. 

> [!IMPORTANT]
> Vor dem Import in eine Produktionsumgebung sollten Sie die Lösung zunächst in einer Entwicklungsumgebung testen. 

<!--Reference links in article-->
[1]: https://admin.powerapps.com
