---
title: Lernprogramm zur Freigabe einer modellgesteuerten Anwendung mit PowerApps | Microsoft Docs
description: 'In diesem Lernprogramm erfahren Sie, wie Sie eine modellgesteuerte Anwendung freigeben können.'
documentationcenter: ''
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/21/2018
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-share-a-model-driven-app-with-powerapps"></a>Lernprogramm: Gemeinsame Nutzung einer modellgesteuerten Anwendung mit PowerApps

[!INCLUDE [powerapps](../../includes/powerapps.md)] Apps verwenden rollenbasierte Sicherheit für die gemeinsame Nutzung. Das grundlegende Konzept der rollenbasierten Sicherheit besteht darin, dass eine Sicherheitsrolle Privilegien enthält, die eine Reihe von Aktionen definieren, die innerhalb der Anwendung ausgeführt werden können. Alle App-Benutzer müssen einer oder mehreren vordefinierten oder benutzerdefinierten Rollen zugeordnet sein. Oder Rollen können auch Teams zugeordnet werden. Wenn ein Benutzer oder ein Team einer dieser Rollen zugeordnet ist, erhält die Person oder das Teammitglied die mit dieser Rolle verbundenen Berechtigungen. 

In diesem Lernprogramm führen Sie die Aufgaben für die gemeinsame Nutzung einer modellgesteuerten Anwendung aus, damit andere sie nutzen können. Informationen zu:
- Erstellen einer benutzerdefinierten Sicherheitsrolle
- Benutzer der benutzerdefinierten Sicherheitsrolle zuweisen
- Zuweisen der Sicherheitsrolle zu einer App

## <a name="prerequisites"></a>Voraussetzungen
Um eine App freizugeben müssen Sie die [!INCLUDE [powerapps](../../includes/powerapps.md)] Umgebungsadministrator- oder Systemadministratorrolle haben. 

## <a name="sign-in-to-powerapps"></a>Bei PowerApps anmelden
Melden Sie sich bei [PowerApps](https://powerapps.microsoft.com/) an. Wenn Sie noch kein [!INCLUDE [powerapps](../../includes/powerapps.md)] Konto haben, wählen Sie den Link **Kostenlos beginnen** aus.

## <a name="share-an-app"></a>Eine App freigeben 
Dieses Lernprogramm folgt der Firma Contoso, die ein Haustierpflegeunternehmen hat, das Hunde und Katzen betreut. Eine App, die eine benutzerdefinierte Entität zur Nachverfolgung des Haustierpflegegeschäfts enthält, wurde bereits erstellt und veröffentlicht. Jetzt muss die App freigegeben werden, damit die Tierpfleger sie benutzen können. Um die App freizugeben, weist ein Administrator oder App-Entwickler den Benutzern und der App eine oder mehrere Sicherheitsrollen zu. 

## <a name="create-or-configure-a-security-role"></a>Erstellen oder Konfigurieren einer Sicherheitsrolle
Die [!INCLUDE [powerapps](../../includes/powerapps.md)]-Umgebung umfasst [vordefinierte Sicherheitsrollen](#about-predefined-security-roles), die allgemeine Benutzeraufgaben mit Zugriffsebenen widerspiegeln, die so definiert sind, dass sie dem Ziel der bewährten Methoden der Sicherheit entsprechen, den Zugriff auf die für die Nutzung der Anwendung erforderliche Mindestmenge an Geschäftsdaten zu ermöglichen. Denken Sie daran, dass die Contoso Pet Grooming-App auf einer benutzerdefinierten Entität basiert. Da die Entität benutzerdefiniert ist, müssen Rechte explizit angegeben werden, bevor Benutzer darin arbeiten können. Dazu können Sie eine der folgenden Möglichkeiten wählen.
- Erweitern Sie eine vorhandene vordefinierte Sicherheitsrolle, so dass sie Rechte auf Datensätze enthält, die auf der benutzerdefinierten Entität basieren. 
- Erstellen Sie eine benutzerdefinierte Sicherheitsrolle, um die Rechte für die Benutzer der App zu verwalten. 

Da die Umgebung, in der die Pet Grooming-Datensätze verwaltet werden, auch für andere Anwendungen verwendet wird, die das Contoso-Geschäft betreibt, wird eine eigene Sicherheitsrolle für die Pet Grooming-App erstellt. Zusätzlich werden zwei verschiedene Zugriffsrechte benötigt.
- Pet Grooming-Techniker müssen andere Datensätze nur lesen, aktualisieren und anhängen können, daher hat ihre Sicherheitsrolle Lese-, Schreib- und Anfügeprivilegien. 
- Pet Grooming-Planer benötigen alle Privilegien, die Pet Grooming-Techniker haben, sowie die Möglichkeit, sie zu erstellen, anzuhängen, zu löschen und freizugeben, so dass ihre Sicherheitsrolle das Erstellen, Lesen, Schreiben, Anhängen, Löschen, Zuweisen, Anhängen und Freigeben von Privilegien beinhaltet.

Weitere Informationen zu Zugriffs- und Umfangsberechtigungen finden Sie unter [Sicherheitsrollen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

## <a name="create-a-custom-security-role"></a>Erstellen einer benutzerdefinierten Sicherheitsrolle
1. Wählen Sie auf der Seite [!INCLUDE [powerapps](../../includes/powerapps.md)] **Apps** > **…**> **Link freigeben**.
2. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Eine Sicherheitsrolle erstellen** Option **Sicherheitseinstellung** aus.
3. Wählen Sie auf der Seite **Einstellungen** die Option **Neu** aus.  

4. Im Sicherheitsrollen-Designer wählen Sie die Aktionen wie Lesen, Schreiben oder Löschen und den Umfang für die Ausführung dieser Aktion aus. Umfang legt fest, wie tief oder hoch der Benutzer innerhalb der Umgebungshierarchie eine bestimmte Aktion ausführen kann. Geben Sie im Feld **Rollenname** *Pet Grooming Technicians* ein.
5. Wählen Sie die Registerkarte **Benutzerdefinierte Entitäten**, und suchen Sie dann die Entität, die Sie verwenden möchten. Für dieses Beispiel wird die benutzerdefinierte Entität **Pet** verwendet. 
6. Wählen Sie in der Zeile **Pet** jedes der folgenden Rechte viermal aus, bis der globale Organisationsumfang ![globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde: **Lesen, Schreiben, Anhängen**
> [!div class="mx-imgBorder"] 
> ![Neue Sicherheitsrolle](media/share-model-driven-app/custom-security-role.png)
7. Da die Pet Grooming-App auch eine Beziehung zur Firmenentität hat, wählen Sie die Registerkarte **Kerndatensätze**, und wählen Sie auf der **Firma**-Zeile **Lesen** viermal, bis globaler Organisationsumfang ![Globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde. 
8. Klicken Sie auf **Speichern und schließen**. 
9. Geben Sie im Sicherheitsrollendesigner im Feld **Rollenname** *Pet Grooming Schedulers* ein. 
10. Wählen Sie die Registerkarte **Benutzerdefinierte Entitäten**, und suchen Sie dann die Entität **Pet**. 
11. Wählen Sie in der Zeile **Pet** jedes der folgenden Rechte viermal aus, bis der globale Organisationsumfang ![globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde: **Erstellen, Lesen, Schreiben, Löschen, Anhängen, Anhängen, Zuweisen, Teilen**
12. Da die Pet Grooming-App auch eine Beziehung zur Firmenentität hat und die Planer in der Lage sein müssen, Firmendatensätze zu erstellen und zu ändern, wählen Sie die Registerkarte **Kerndatensätze** aus, und wählen Sie in der Zeile **Firma** jedes der folgenden Rechte viermal aus, bis der globale Organisationsumfang ![Globaler Organisationsumfang](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde. 
    **Erstellen, Lesen, Schreiben, Löschen, Anfügen, Anfügen an, Zuweisen, Freigeben**
13. Klicken Sie auf **Speichern und schließen**.

## <a name="assign-security-roles-to-users"></a>Zuweisen von Sicherheitsrollen zu Benutzern
Sicherheitsrollen steuern den Zugriff eines Benutzers auf Daten durch einen satz von Zugriffsebenen und Berechtigungen. Die Kombination von Zugriffsebenen und Berechtigungen, die in einer bestimmten Sicherheitsrolle enthalten sind, begrenzt die Möglichkeit des Benutzers zur Anzeige von Daten und die Interaktionen des Benutzers mit den Daten.

### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>Zuweisen einer Sicherheitsrolle zu einem Pet Grooming-Techniker
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Benutzer der Sicherheitsrolle zuweisen** die Option **Sicherheitsbenutzer** aus.
2. Wählen Sie in der angezeigten Liste die Tierpfleger aus.
3. Wählen Sie **Rollen verwalten** aus.

    > [!div class="mx-imgBorder"] 
    > ![Verwalten von Rollen](media/share-model-driven-app/select-users-for-security-roles.png)

4. Wählen Sie im Dialogfeld **Benutzerrollen verwalten** die zuvor erstellte Sicherheitsrolle **Pet Grooming Technicians** aus und wählen Sie dann **OK**.

### <a name="assign-a-security-role-to-pet-grooming-schedulers"></a>Zuweisen einer Sicherheitsrolle zu einem Pet Grooming-Planer
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Benutzer der Sicherheitsrolle zuweisen** die Option **Sicherheitsbenutzer** aus.
2. Wählen Sie in der angezeigten Liste die Tierpflegeplaner aus.
3. Wählen Sie **Rollen verwalten** aus.
4. Wählen Sie im Dialogfeld **Benutzerrollen verwalten** die zuvor erstellte Sicherheitsrolle **Pet Grooming Schedulers** aus und wählen Sie dann **OK**.


## <a name="add-security-roles-to-the-app"></a>Fügen Sie Sicherheitsrollen der App hinzu
Als nächstes müssen der App eine oder mehrere Sicherheitsrollen zugewiesen werden. Benutzer haben Zugriff auf Apps basierend auf den Sicherheitsrollen, die ihnen zugewiesen sind.
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Sicherheitsrolle der App zuweisen** die Option **Meine Apps** aus.
2. Wählen Sie in der unteren rechten Ecke der App-Kachel der Contoso Pet Grooming-App **Weitere Optionen (...)**, und wählen Sie dann **Rollen verwalten**.

    ![Verwalten von Rollen für die App](media/share-model-driven-app/manage-roles.png)

4. Wählen Sie im Bereich **Rollen** aus, ob Sie den App-Zugriff allen Sicherheitsrollen oder ausgewählten Rollen gewähren möchten. Wählen Sie die Rollen **Pet Grooming Schedulers** und **Pet Grooming Technicians** aus, die Sie zuvor erstellt haben.

    > [!div class="mx-imgBorder"] 
    > ![Auswählen von Sicherheitsrollen für die App](media/share-model-driven-app/app-security-roles.png)

5. Wählen Sie **Speichern** aus.
 
## <a name="share-the-link-to-your-app"></a>Den Link zur App freigeben
1. Im Dialogfenster **Diese Anwendung freigeben**, unter **Link zu Ihrer App direkt für Benutzer freigeben** kopieren Sie die angezeigte URL.
 
2. Wählen Sie **Schließen** aus.
3. Fügen Sie die URL der Anwendung an einem Ort ein, damit Ihre Benutzer darauf zugreifen können, z. B. indem Sie sie auf einer SharePoint-Website veröffentlichen oder per E-Mail versenden.

> [!div class="mx-imgBorder"] 
> ![Link freigeben](media/share-model-driven-app/share-model-driven-URL.PNG)

Sie finden die App-URL auch auf der Registerkarte **Eigenschaften** im App-Designer. 

> [!div class="mx-imgBorder"] 
> ![App-URL kopieren](media/share-model-driven-app/app-designer-copy-web-url.png)

## <a name="about-predefined-security-roles"></a>Über vordefinierte Sicherheitsrollen
Diese vordefinierten Rollen sind in einer [!INCLUDE [powerapps](../../includes/powerapps.md)]-Umgebung verfügbar.


|Sicherheitsrolle  |*Rechte  |Beschreibung |
|---------|---------|---------|
|Umgebungserstellung     |  Keine       | Kann neue Ressourcen erstellen, die mit einer Umgebung verbunden sind, einschließlich Apps, Verbindungen, benutzerdefinierte APIs, Gateways und Flows mit Microsoft Flow. Hat jedoch keine Rechte für den Zugriff auf Daten innerhalb einer Umgebung. Weitere Informationen: [Umgebungsübersicht](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|Systemadministrator     |  Erstellen, Lesen, Schreiben, Löschen, Anpassungen, Sicherheitsrollen       | Hat volle Berechtigung zum Anpassen oder Verwalten der Umgebung, einschließlich dem Erstellen, Ändern und Zuweisen von Sicherheitsrollen. Kann alle Daten in der Umgebung anzeigen Weitere Informationen: [Erforderliche Rechte für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Systemanpasser     | Erstellen (selbst), Lesen (selbst), Schreiben (selbst), Löschen (selbst), Anpassungen         | Hat volle Rechte zum Anpassen der Umgebung. Sie können jedoch nur Datensätze für die von ihnen angelegten Umgebungsentitäten anzeigen. Weitere Informationen: [Erforderliche Rechte für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Common Data Service-Benutzer     |  Lesen, Erstellen (selbst), Schreiben (selbst), Löschen (selbst)       | Kann eine App innerhalb der Umgebung ausführen und allgemeine Aufgaben für die Datensätze, die sie besitzen, ausführen.        |
|Stellvertretung     | Vorgänge im Namen anderer Benutzer ausführen        | Ermöglicht die Ausführung von Code als anderer Benutzer oder unter anderer Identität.  Wird normalerweise mit einer anderen Sicherheitsrolle verwendet, um den Zugriff auf Datensätze zu ermöglichen. Weitere Informationen: [Annehmen der Identität eines anderen Benutzers](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*Recht hat globalen Umfang, soweit nicht anders angegeben.

## <a name="next-steps"></a>Nächste Schritte
[Ausführen einer modellgesteuerten App auf einem mobilen Gerät](../../user/run-app-client-model-driven.md)



