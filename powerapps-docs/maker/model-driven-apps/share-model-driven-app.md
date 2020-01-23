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
ms.date: 12/17/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bcdc8241692cd1713f4c0f4cd2f4c0d8959dffe4
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909370"
---
# <a name="share-a-model-driven-app-with-power-apps"></a>Gemeinsame Nutzung einer modellgesteuerten App mit Power Apps

[!INCLUDE [powerapps](../../includes/powerapps.md)] Apps verwenden rollenbasierte Sicherheit für die gemeinsame Nutzung. Das grundlegende Konzept der rollenbasierten Sicherheit besteht darin, dass eine Sicherheitsrolle Privilegien enthält, die eine Reihe von Aktionen definieren, die innerhalb der Anwendung ausgeführt werden können. Alle App-Benutzer müssen einer oder mehreren vordefinierten oder benutzerdefinierten Rollen zugeordnet sein. Oder Rollen können auch Teams zugeordnet werden. Wenn ein Benutzer oder ein Team einer dieser Rollen zugeordnet ist, erhält die Person oder das Teammitglied die mit dieser Rolle verbundenen Berechtigungen. 

## <a name="prerequisites"></a>Voraussetzungen
Um eine App freizugeben müssen Sie die [!INCLUDE [powerapps](../../includes/powerapps.md)] Umgebungsadministrator- oder Systemadministratorrolle haben. 

## <a name="share-your-app-for-basic-use"></a>Teilen Sie Ihre App für den grundlegenden Gebrauch
Um Berechtigungen hinzuzufügen, damit der App-Benutzer eine App in der Umgebung und allgemeine Aufgaben für die Datensätze ausführen kann, deren Besitzer sie sind, verwenden Sie die Sicherheitsrolle des **Common Data Service-Benutzers**.
1.  Auf der [Power Apps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)-Website wählen Sie **Apps**, dann neben der modellgesteuerten App, die Sie freigeben möchten, **…** und dann **Teilen**. 
    > [!IMPORTANT]
    > Die Schritte zum Freigeben einer modellgesteuerten App unterscheiden sich von einer Canvas-App. Schritte zum Freigeben einer Canvas-App finden Sie unter [Freigeben einer Canvas-App in Power Apps](../canvas-apps/share-app.md). 

2.  Unter **Benutzer der Sicherheitsrolle zuordnen** wählen Sie **Sicherheitsbenutzer** aus.
3.  Wählen Sie aus der Liste der aktivierten Benutzer die Benutzer aus, denen Sie Zugriff auf Ihre App gewähren möchten, und wählen Sie dann in der Befehlsleiste **Rollen verwalten**. 
4.  Wählen Sie im Dialogfenster **Benutzerrollen verwalten** die zuvor erstellte **Common Data Service-Benutzer**-Sicherheitsrolle aus und wählen Sie dann **OK**. 

    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/select-common-data-service-user.png "Select Common Data Service User")

5. [Fügen Sie Sicherheitsrollen der App hinzu](#add-security-roles-to-the-app)
6. [Den Link zur App freigeben](#share-the-link-to-your-app)

Benutzer mit der Common Data Service-Benutzersicherheitsrolle können jetzt auf Ihre App zugreifen. 

## <a name="share-a-model-driven-app-for-specific-use"></a>Teilen Sie eine modellgesteuerte App für eine bestimmte Verwendung
In diesem Abschnitt führen Sie die Aufgaben zum Freigeben einer modellgesteuerten App mithilfe von zwei Sicherheitsrollen aus, die sich jeweils nach den Anforderungen der App-Benutzer richten. Informationen zu:
- Erstellen einer benutzerdefinierten Sicherheitsrolle
- Benutzer der benutzerdefinierten Sicherheitsrolle zuweisen
- Zuweisen der Sicherheitsrolle zu einer App

### <a name="tutorial-overview"></a>Tutorialüberblick 
Dieser Abschnitt folgt der Firma Contoso, die ein Haustierpflegeunternehmen hat, das Hunde und Katzen betreut. Eine App, die eine benutzerdefinierte Entität zur Nachverfolgung des Haustierpflegegeschäfts enthält, wurde bereits erstellt und veröffentlicht. Jetzt muss die App freigegeben werden, damit die Tierpfleger sie benutzen können. Um die App freizugeben, weist ein Administrator oder App-Entwickler den Benutzern und der App eine oder mehrere Sicherheitsrollen zu. 

### <a name="create-or-configure-a-security-role"></a>Erstellen oder Konfigurieren einer Sicherheitsrolle
Die [!INCLUDE [powerapps](../../includes/powerapps.md)]-Umgebung umfasst [vordefinierte Sicherheitsrollen](#about-predefined-security-roles), die allgemeine Benutzeraufgaben mit Zugriffsebenen widerspiegeln, die so definiert sind, dass sie dem Ziel der bewährten Methoden der Sicherheit entsprechen, den Zugriff auf die für die Nutzung der Anwendung erforderliche Mindestmenge an Geschäftsdaten zu ermöglichen. Denken Sie daran, dass die Contoso Pet Grooming-App auf einer benutzerdefinierten Entität basiert. Da die Entität benutzerdefiniert ist, müssen Rechte explizit angegeben werden, bevor Benutzer darin arbeiten können. Dazu können Sie eine der folgenden Möglichkeiten wählen.
- Erweitern Sie eine vorhandene vordefinierte Sicherheitsrolle, so dass sie Rechte auf Datensätze enthält, die auf der benutzerdefinierten Entität basieren. 
- Erstellen Sie eine benutzerdefinierte Sicherheitsrolle, um die Rechte für die Benutzer der App zu verwalten. 

Da die Umgebung, in der die Pet Grooming-Datensätze verwaltet werden, auch für andere Anwendungen verwendet wird, die das Contoso-Geschäft betreibt, wird eine eigene Sicherheitsrolle für die Pet Grooming-App erstellt. Zusätzlich werden zwei verschiedene Zugriffsrechte benötigt.
- Pet Grooming-Techniker müssen andere Datensätze nur lesen, aktualisieren und anhängen können, daher hat ihre Sicherheitsrolle Lese-, Schreib- und Anfügeprivilegien. 
- Pet Grooming-Planer benötigen alle Privilegien, die Pet Grooming-Techniker haben, sowie die Möglichkeit, sie zu erstellen, anzuhängen, zu löschen und freizugeben, so dass ihre Sicherheitsrolle das Erstellen, Lesen, Schreiben, Anhängen, Löschen, Zuweisen, Anhängen und Freigeben von Privilegien beinhaltet.

Weitere Informationen zu Zugriffs- und Umfangsberechtigungen finden Sie unter [Sicherheitsrollen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

### <a name="create-a-custom-security-role"></a>Erstellen einer benutzerdefinierten Sicherheitsrolle
1. Auf der [!INCLUDE [powerapps](../../includes/powerapps.md)]-Website wählen Sie **Apps**, dann neben der modellgesteuerten App, die Sie freigeben möchten, **…** und dann **Teilen**.

2. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Eine Sicherheitsrolle erstellen** Option **Sicherheitseinstellung** aus.

3. Klicken Sie auf der Seite **Alle Rollen** auf **Neu**.  

4. Im Sicherheitsrollen-Designer wählen Sie die Aktionen wie Lesen, Schreiben oder Löschen und den Umfang für die Ausführung dieser Aktion aus. Umfang legt fest, wie tief oder hoch der Benutzer innerhalb der Umgebungshierarchie eine bestimmte Aktion ausführen kann. Geben Sie im Feld **Rollenname** *Pet Grooming Technicians* ein.

5. Wählen Sie die Registerkarte **Benutzerdefinierte Entitäten**, und suchen Sie dann die Entität, die Sie verwenden möchten. Für dieses Beispiel wird die benutzerdefinierte Entität **Pet** verwendet. 

6. Wählen Sie in der Zeile **Pet** jedes der folgenden Rechte viermal aus, bis der globale Organisationsumfang ![globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde: **Lesen, Schreiben, Anhängen**

   > [!div class="mx-imgBorder"] 
   > ![Neue Sicherheitsrolle](media/share-model-driven-app/custom-security-role.png)

7. Da die Pet Grooming-App auch eine Beziehung zur Firmenentität hat, wählen Sie die Registerkarte **Kerndatensätze**, und wählen Sie auf der **Firma**-Zeile **Lesen** viermal, bis globaler Organisationsumfang ![Globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde. 

8. Wählen Sie die Registerkarte **Anpassung** und wählen Sie dann in der Rechtsliste das Recht **Lesen** neben **Modellgestützte App** aus, damit der Organisationsbereich ![Globaler Organisationsbereich](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wird.

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

    > [!div class="mx-imgBorder"] 
    > ![Verwalten von Rollen](media/share-model-driven-app/select-users-for-security-roles.png)

3. Wählen Sie im Dialogfeld **Benutzerrollen verwalten** die zuvor erstellte Sicherheitsrolle **Pet Grooming Technicians** aus und wählen Sie dann **OK**.

#### <a name="assign-a-security-role-to-pet-grooming-schedulers"></a>Zuweisen einer Sicherheitsrolle zu einem Pet Grooming-Planer
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Benutzer der Sicherheitsrolle zuweisen** die Option **Sicherheitsbenutzer** aus.
2. Wählen Sie in der angezeigten Liste die Tierpflegeplaner aus.
3. Wählen Sie **Rollen verwalten** aus.
4. Wählen Sie im Dialogfeld **Benutzerrollen verwalten** die zuvor erstellte Sicherheitsrolle **Pet Grooming Schedulers** aus und wählen Sie dann **OK**.


## <a name="add-security-roles-to-the-app"></a>Fügen Sie Sicherheitsrollen der App hinzu
Der App müssen eine oder mehrere Sicherheitsrollen zugewiesen werden. Benutzer haben Zugriff auf Apps basierend auf den Sicherheitsrollen, die ihnen zugewiesen sind.
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Sicherheitsrolle der App zuweisen** die Option **Meine Apps** aus.
2. Wählen Sie in der unteren rechten Ecke der App-Kachel **Weitere Optionen (...)**, und wählen Sie dann **Rollen verwalten**.

    ![Verwalten von Rollen für die App](media/share-model-driven-app/manage-roles.png)

4. Wählen Sie im Bereich **Rollen** aus, ob Sie den App-Zugriff allen Sicherheitsrollen oder ausgewählten Rollen gewähren möchten. Wählen Sie für den grundlegenden App-Zugriff die **Common Data Service-Benutzer**-Sicherheitsrolle. Wählen Sie für einen spezifischeren Zugriff einen anderen Standard oder eine benutzerdefinierte oder eine angepasste Sicherheitsrolle aus. Wählen Sie zum Beispiel die Rollen **Pet Grooming-Planer** und **Pet Grooming-Techniker**, die Sie zuvor in diesem Abschnitt erstellt haben. 

    > [!div class="mx-imgBorder"] 
    > ![Auswählen von Sicherheitsrollen für die App](media/share-model-driven-app/app-security-roles.png)

5. Wählen Sie **Speichern** aus. 
 

    > [!IMPORTANT]
    > Benutzer, die über Berechtigungen zum **Erstellen** oder **Schreiben** in **Modellgesteuerte App** verfügen, haben Zugriff auf alle Apps in der Umgebung, auch wenn sie keiner Rolle angehören, die Zugriff auf die App hat.
    > ![Erstellen und Schreiben mit modellgesteuerten App-Berechtigungen](media/app-access-cds.png)

## <a name="share-the-link-to-your-app"></a>Den Link zur App freigeben
1. Im Dialogfenster **Diese Anwendung freigeben**, unter **Link zu Ihrer App direkt für Benutzer freigeben** kopieren Sie die angezeigte URL.
   > [!div class="mx-imgBorder"] 
   > ![Link freigeben](media/share-model-driven-app/share-model-driven-url.png)

2. Wählen Sie **Schließen** aus.
3. Fügen Sie die App-URL an einem Ort ein, damit Ihre Benutzer darauf zugreifen können, z. B. indem Sie sie auf einer SharePoint-Website veröffentlichen oder per E-Mail versenden.

Sie finden die App-URL auch auf der Registerkarte **Eigenschaften** im App-Designer. 

> [!div class="mx-imgBorder"] 
> ![App-URL kopieren](media/share-model-driven-app/app-designer-copy-web-url.png)

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



