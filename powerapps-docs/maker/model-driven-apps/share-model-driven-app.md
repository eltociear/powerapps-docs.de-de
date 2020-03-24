---
title: Gemeinsame Nutzung einer modellgesteuerten App mit Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie eine modellgestützte App freigeben
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/04/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 42ba7e8416477890614b00f6aa89ea241287475b
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "3099925"
---
# <a name="share-a-model-driven-app-with-power-apps"></a>Gemeinsame Nutzung einer modellgesteuerten App mit Power Apps

[!INCLUDE [powerapps](../../includes/powerapps.md)] Apps verwenden rollenbasierte Sicherheit für die gemeinsame Nutzung. Das grundlegende Konzept der rollenbasierten Sicherheit besteht darin, dass eine Sicherheitsrolle Privilegien enthält, die eine Reihe von Aktionen definieren, die innerhalb der Anwendung ausgeführt werden können. Alle App-Benutzer müssen einer oder mehreren vordefinierten oder benutzerdefinierten Rollen zugeordnet sein. Oder Rollen können auch Teams zugeordnet werden. Wenn ein Benutzer oder ein Team einer dieser Rollen zugeordnet ist, erhält die Person oder das Teammitglied die mit dieser Rolle verbundenen Berechtigungen. 

## <a name="prerequisites"></a>Voraussetzungen
Stellen Sie sicher, dass Sie eine [Sicherheitsrolle](https://docs.microsoft.com/power-platform/admin/security-roles-privileges) mit gleichen oder höheren Berechtigungen haben als die Rolle, die Sie der App und anderen Benutzern zuweisen. 

## <a name="create-a-security-role-for-your-app"></a>Erstellen Sie ein Sicherheitsrolle für Ihre App
Im Allgemeinen enthalten modellgesteuerte Apps benutzerdefinierte Entitäten und andere benutzerdefinierte Konfigurationen. Es ist wichtig, zuerst [Eine Sicherheitsrolle zu erstellen](#create-a-security-role-for-your-app) mit Berechtigung alle Komponenten in Ihrer App.  
> [!NOTE]
> Dieser Schritt kann übersprungen werden, wenn vorhandene Rollen Zugriff auf die Daten in Ihrer App gewähren. 

## <a name="preview-share-a-model-driven-app"></a>Vorschau: Eine modellgesteuerte App verwenden 
Das Teilen einer modellgesteuerten App umfasst zwei Hauptschritte. Ordnen Sie der App zunächst eine oder mehrere Sicherheitsrollen zu und weisen Sie dann den Benutzern die Sicherheitsrollen zu. 
1. Besuchen Sie https://make.powerapps.com
2. Wählen Sie eine modellgesteuerte App aus und klicken Sie auf **Teilen**.
3. Wählen Sie die App aus und wählen Sie eine Sicherheitsrolle aus der Liste aus.
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-app.png "Assign a role to the app")
4. Nach einem Benutzer suchen
5. Wählen Sie den Benutzer aus der Liste aus, und wählen Sie dann eine Rolle aus.
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-user.png "Assign a role to the user")
6. Klicken Sie auf **Freigeben**.

### <a name="share-the-link-to-your-app"></a>Den Link zur App freigeben
Im Gegensatz zur Freigabe von Canvas-Apps sendet die Freigabe modellgesteuerte Apps derzeit keine E-Mail mit einem Link zur App.

So erhalten Sie den direkten Link zu einer App:
1. Bearbeiten Sie die App und klicken Sie auf die Registerkarte **Eigenschaften**
2. Kopieren Sie die **Einheitliche Oberflächen URL.**
3. Fügen Sie die App-URL an einem Ort ein, damit Ihre Benutzer darauf zugreifen können, z. B. indem Sie sie auf einer SharePoint-Website veröffentlichen oder per E-Mail versenden.


## <a name="create-or-configure-a-security-role"></a>Erstellen oder Konfigurieren einer Sicherheitsrolle
Die [!INCLUDE [powerapps](../../includes/powerapps.md)]-Umgebung umfasst [vordefinierte Sicherheitsrollen](#about-predefined-security-roles), die allgemeine Benutzeraufgaben mit Zugriffsebenen widerspiegeln, die so definiert sind, dass sie dem Ziel der bewährten Methoden der Sicherheit entsprechen, den Zugriff auf die für die Nutzung der Anwendung erforderliche Mindestmenge an Geschäftsdaten zu ermöglichen. Wenn Ihre App beispielsweise auf einer benutzerdefinierten Entität basiert, müssen die Entitätsberechtigungen explizit angegeben werden, bevor Benutzer daran arbeiten können. Dazu können Sie eine der folgenden Möglichkeiten wählen.
- Erweitern Sie eine vorhandene vordefinierte Sicherheitsrolle, so dass sie Rechte auf Datensätze enthält, die auf der benutzerdefinierten Entität basieren. 
- Erstellen Sie eine benutzerdefinierte Sicherheitsrolle, um die Rechte für die Benutzer der App zu verwalten. 

Weitere Informationen zu Zugriffs- und Umfangsberechtigungen finden Sie unter [Sicherheitsrollen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

### <a name="create-a-custom-security-role"></a>Erstellen einer benutzerdefinierten Sicherheitsrolle
1. Auf der [!INCLUDE [powerapps](../../includes/powerapps.md)]-Website wählen Sie **Apps**, dann neben der modellgesteuerten App, die Sie freigeben möchten, **…** und dann **Teilen**.

2. Wählen Sie die App aus und erweitern Sie die Liste der Sicherheitsrollen.

3. Klicken Sie auf der Seite **Alle Rollen** auf **Neu**.  

4. Im Sicherheitsrollen-Designer wählen Sie die Aktionen wie Lesen, Schreiben oder Löschen und den Umfang für die Ausführung dieser Aktion aus. Umfang legt fest, wie tief oder hoch der Benutzer innerhalb der Umgebungshierarchie eine bestimmte Aktion ausführen kann. Geben Sie im Feld **Rollenname** *Pet Grooming Technicians* ein.

5. Wählen Sie die Registerkarte **Benutzerdefinierte Entitäten**, und suchen Sie dann die Entität, die Sie verwenden möchten. Für dieses Beispiel wird die benutzerdefinierte Entität **Pet** verwendet. 

6. Wählen Sie in der Zeile **Pet** jedes der folgenden Rechte viermal aus, bis der globale Organisationsumfang ![globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde: **Lesen, Schreiben, Anhängen**

   > [!div class="mx-imgBorder"] 
   > ![Neue Sicherheitsrolle](media/share-model-driven-app/custom-security-role.png)

7. Da die Pet Grooming-App auch eine Beziehung zur Firmenentität hat, wählen Sie die Registerkarte **Kerndatensätze**, und wählen Sie auf der **Firma**-Zeile **Lesen** viermal, bis globaler Organisationsumfang ![Globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde. 

8. Wählen Sie die Registerkarte **Anpassung** und wählen Sie dann in der Rechtsliste das Recht **Lesen** neben **Modellgestützte App** aus, damit der Organisationsbereich ![Globaler Organisationsbereich](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wird.

    > [!div class="mx-imgBorder"] 
    > ![Auswählen von Sicherheitsrollen für die App](media/app-access-specific-use.png)

9. Klicken Sie auf **Speichern und schließen**. 

10. Geben Sie im Sicherheitsrollendesigner im Feld **Rollenname** *Pet Grooming Schedulers* ein. 

11. Wählen Sie die Registerkarte **Benutzerdefinierte Entitäten**, und suchen Sie dann die Entität **Pet**. 

12. Wählen Sie in der Zeile **Pet** jedes der folgenden Rechte viermal aus, bis der globale Organisationsumfang ![globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde: **Erstellen, Lesen, Schreiben, Löschen, Anhängen, Anhängen, Zuweisen, Teilen**

13. Da die Pet Grooming-App auch eine Beziehung zur Firmenentität hat und die Planer in der Lage sein müssen, Firmendatensätze zu erstellen und zu ändern, wählen Sie die Registerkarte **Kerndatensätze** aus, und wählen Sie in der Zeile **Firma** jedes der folgenden Rechte viermal aus, bis der globale Organisationsumfang ![Globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde. 
    **Erstellen, Lesen, Schreiben, Löschen, Anfügen, Anfügen an, Zuweisen, Freigeben**

14. Klicken Sie auf **Speichern und schließen**.

### <a name="assign-security-roles-to-users"></a>Zuweisen von Sicherheitsrollen zu Benutzern
Sicherheitsrollen steuern den Zugriff eines Benutzers auf Daten durch einen satz von Zugriffsebenen und Berechtigungen. Die Kombination von Zugriffsebenen und Berechtigungen, die in einer bestimmten Sicherheitsrolle enthalten sind, begrenzt die Möglichkeit des Benutzers zur Anzeige von Daten und die Interaktionen des Benutzers mit den Daten.

#### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>Zuweisen einer Sicherheitsrolle zu einem Pet Grooming-Techniker
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Benutzer der Sicherheitsrolle zuweisen** die Option **Sicherheitsbenutzer** aus.
2. Wählen Sie in der angezeigten Liste die Benutzer aus, die Hundefriseure sind, und wählen Sie dann in der Befehlsleiste **Rollen verwalten** aus.

3. Klicken Sie auf **Sicherheitsrollen verwalten.**
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/manage-roles.png "Manage roles")

4. Auf der Seite **Alle Rollen** wählen Sie **Common Data Service Benutzer** und klicken dann auf **Aktionen** und **Rolle kopieren.** 

> [!TIP]
> Sie können auch eine neue leere Rolle erstellen, anstatt eine vorhandene Rolle zu kopieren. 

6. Das Kästchen **Rollenname** stellt eine beschreibende Rolle wie *Mein benutzerdefinierter App-Zugriff* bereit.  Klicken Sie auf **OK**.

7. Im Sicherheitsrollen-Designer wählen Sie die Aktionen wie Lesen, Schreiben oder Löschen und die [Zugangsebenen](https://docs.microsoft.com/power-platform/admin/security-roles-privileges#security-roles) aus. Zugangsebenen legen fest, wie tief oder hoch der Benutzer innerhalb der Umgebungshierarchie eine bestimmte Aktion ausführen kann. 

8. Wählen Sie die Registerkarte **Benutzerdefinierte Entitäten** und suchen Sie dann die Entität, die Sie in Ihrer App verwenden möchten. 

9.  Legen Sie in der Zeile für Ihre benutzerdefinierte Entität die Zugriffsebenen für jede Berechtigung fest.  

10. Wiederholen Sie diesen Vorgang für andere in Ihrer App verwendete Entitäten. 

11. Wählen Sie die Registerkarte **Anpassung** und wählen Sie dann in der Rechtsliste das Recht **Lesen** neben **Modellgesteuerte App** aus, damit der Organisationsbereich ![Globaler Organisationsbereich](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wird.

    > [!IMPORTANT]
    > Die vom Benutzer gewährten Berechtigungen **Lesen**, **Erstellen** und **Schreiben** der **Modellgesteuerten App** haben Zugriff auf alle Apps in der Umgebung, auch wenn sie nicht Teil einer Rolle sind, die Zugriff auf die App haben.
    > ![Erstellen und Schreiben mit modellgesteuerten App-Berechtigungen](media/app-access-cds.png)

12. Klicken Sie auf **Speichern und schließen**. 


## <a name="about-predefined-security-roles"></a>Über vordefinierte Sicherheitsrollen
Diese vordefinierten Rollen sind in einer [!INCLUDE [powerapps](../../includes/powerapps.md)]-Umgebung verfügbar.


|Sicherheitsrolle  |*Rechte  |Beschreibung |
|---------|---------|---------|
|Umgebungserstellung     |  Keine       | Kann neue Ressourcen erstellen, die mit einer Umgebung verbunden sind, einschließlich Apps, Verbindungen, benutzerdefinierte APIs, Gateways und Flows mit Power Automate. Hat jedoch keine Rechte für den Zugriff auf Daten innerhalb einer Umgebung. Weitere Informationen: [Umgebungsübersicht](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|Systemadministrator     |  Erstellen, Lesen, Schreiben, Löschen, Anpassungen, Sicherheitsrollen       | Hat volle Berechtigung zum Anpassen oder Verwalten der Umgebung, einschließlich dem Erstellen, Ändern und Zuweisen von Sicherheitsrollen. Kann alle Daten in der Umgebung anzeigen Weitere Informationen: [Erforderliche Rechte für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Systemanpasser     | Erstellen (selbst), Lesen (selbst), Schreiben (selbst), Löschen (selbst), Anpassungen         | Hat volle Rechte zum Anpassen der Umgebung. Sie können jedoch nur Datensätze für die von ihnen angelegten Umgebungsentitäten anzeigen. Weitere Informationen: [Erforderliche Rechte für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Common Data Service-Benutzer     |  Lesen, Erstellen (selbst), Schreiben (selbst), Löschen (selbst)       | Kann eine App innerhalb der Umgebung ausführen und allgemeine Aufgaben für die Datensätze, die sie besitzen, ausführen.        |
|Stellvertretung     | Vorgänge im Namen anderer Benutzer ausführen        | Ermöglicht die Ausführung von Code als anderer Benutzer oder unter anderer Identität.  Wird normalerweise mit einer anderen Sicherheitsrolle verwendet, um den Zugriff auf Datensätze zu ermöglichen. Weitere Informationen: [Annehmen der Identität eines anderen Benutzers](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*Recht hat globalen Umfang, soweit nicht anders angegeben.

## <a name="use-azure-active-directory-groups-to-manage-access"></a>Zugriff auf Azure Active Directory Gruppen, um den Zugriff zu verwalten
Administratoren können ihre Organisation verwenden Azure Active Directory (Azure AD) Gruppen, um Zugriffsrechte für lizenzierte Common Data Service Benutzer zu verwalten. Beide Arten von Azure AD Gruppen - Office und Sicherheit - können zur Sicherung der Benutzerzugriffsrechte für eine App verwendet werden. Weitere Informationen: [Über Gruppenteams](/power-platform/admin/manage-teams.md#about-group-teams) 


### <a name="see-also"></a>Siehe auch
[Ausführen einer modellgesteuerten App auf einem mobilen Gerät](../../user/run-app-client-model-driven.md)

[Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)


