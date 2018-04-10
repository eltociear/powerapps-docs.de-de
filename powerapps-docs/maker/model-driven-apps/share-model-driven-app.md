---
title: 'Tutorial: Freigeben einer modellgesteuerten App mit PowerApps | Microsoft-Dokumentation'
description: In diesem Tutorial erfahren Sie, wie Sie eine modellgesteuerte App freigeben.
services: ''
suite: powerapps
documentationcenter: ''
author: Mattp123
manager: brycho
editor: ''
tags: ''
ms.service: powerapps
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: 7917211c343e1375641ba2813810cb6723151f53
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-share-a-model-driven-app-with-powerapps"></a>Tutorial: Freigeben einer modellgesteuerten App mit PowerApps

[!INCLUDE [powerapps](../../includes/powerapps.md)]-Apps verwenden zum Freigeben rollenbasierte Sicherheit. Die rollenbasierte Sicherheit baut auf folgendem Grundprinzip auf: Die Sicherheitsrolle enthält Berechtigungen, die bestimmte Aktionen in der App zulassen oder verweigern. Allen App-Benutzern muss mindestens eine vordefinierte oder benutzerdefinierte Rolle zugewiesen werden. Alternativ können Rollen auch Teams zugewiesen werden. Wenn einem Benutzer oder einem Team eine dieser Rollen zugewiesen wird, werden diesen die Berechtigungen zugewiesen, die der Rolle zugeordnet sind. 

In diesem Tutorial führen Sie die entsprechenden Schritte zum Freigeben einer modellgesteuerten App durch, damit sie auch von anderen verwendet werden kann. In diesem Tutorial lernen Sie Folgendes:
- wie Sie eine benutzerdefinierte Sicherheitsrolle erstellen
- wie Sie Benutzern diese benutzerdefinierte Sicherheitsrolle zuweisen
- wie Sie die Sicherheitsrolle einer App zuweisen

> [!IMPORTANT]
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

## <a name="prerequisites"></a>Voraussetzungen
Zum Freigeben der App müssen Sie über die [!INCLUDE [powerapps](../../includes/powerapps.md)]-Rollen „Umgebungsadministrator“ oder „Systemadministrator“ verfügen. 

## <a name="sign-in-to-powerapps"></a>Anmelden bei PowerApps
Melden Sie sich bei [PowerApps](https://powerapps.microsoft.com/) an. Wenn Sie noch nicht über ein [!INCLUDE [powerapps](../../includes/powerapps.md)]-Konto verfügen, klicken Sie auf **Steigen Sie kostenlos ein**.

## <a name="share-an-app"></a>Freigeben einer App 
In diesem Tutorial wird das Beispielunternehmen Contoso verwendet, das Haustierpflegedienstleistungen für Hunde und Katzen anbietet. Eine App, die eine benutzerdefinierte Entität zum Status des Haustierpflegegeschäfts enthält, wurde bereits erstellt und veröffentlicht. Jetzt muss die App freigegeben werden, damit sie von den Angestellten des Haustierpflegesalons verwendet werden kann. Zum Freigeben der App weist ein Administrator oder ein App-Ersteller Benutzern oder der App mindestens eine Sicherheitsrolle zu. 

## <a name="create-or-configure-a-security-role"></a>Erstellen oder Konfigurieren einer Sicherheitsrolle
Die [!INCLUDE [powerapps](../../includes/powerapps.md)]-Umgebung umfasst [vordefinierte Sicherheitsrollen](#about-predefined-security-roles), die häufig verwendete Benutzeraufgaben mit Zugriffsebenen widerspiegeln, durch die nur auf die Unternehmensdaten zugegriffen werden kann, die mindestens erforderlich sind, um die App zu verwenden. Dabei handelt es sich um ein bewährtes Sicherheitsziel. Denken Sie daran, dass die Contoso-Tierpflege-App auf einer benutzerdefinierten Entität basiert. Da die Entität benutzerdefiniert ist, müssen Berechtigungen explizit angegeben werden, bevor Benutzer an der App arbeiten können. Dazu können Sie einen der folgenden Schritte ausführen.
- Erweitern Sie eine bereits vorhandene vordefinierte Sicherheitsrolle um Berechtigungen für Datensätze, die auf der benutzerdefinierten Entität basieren. 
- Erstellen Sie eine benutzerdefinierte Sicherheitsrolle zum Verwalten von Berechtigungen für Benutzer der App. 

Da die Umgebung, die die Haustierpflegedatensätze enthält, auch für andere Contoso-Apps verwendet wird, wird eine benutzerdefinierte Sicherheitsrolle exklusiv für die Haustierpflege-App erstellt. Außerdem sind zwei weitere Berechtigungssätze erforderlich.
- Haustierfriseure müssen möglicherweise andere Datensätze nur lesen, schreiben oder anfügen. Daher sind die Berechtigungen ihrer Sicherheitsrolle auch nur auf diese Vorgänge beschränkt. 
- Haustierpflegemanager benötigen möglicherweise nicht nur die gleichen Berechtigungen wie Haustierfriseure, sondern auch Berechtigungen zum Erstellen, Schreiben, Lesen, Anfügen, Löschen und Freigeben. Daher werden diese Vorgänge ebenfalls für ihre Sicherheitsrolle freigegeben.

Weitere Informationen zu Zugriffs- und Bereichsberechtigungen finden Sie unter [Sicherheitsrollen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles).

## <a name="create-a-custom-security-role"></a>Erstellen einer benutzerdefinierten Sicherheitsrolle
1. Klicken Sie auf der [!INCLUDE [powerapps](../../includes/powerapps.md)]-Website auf **Model-driven** > **Apps** > **...**> **Share link** (Modellgesteuert > Apps > ... > Link teilen).
2. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Create a security role** (Sicherheitsrolle erstellen) **Security Setting** (Sicherheitseinstellung) aus.
3. Klicken Sie auf der Seite **Einstellungen** auf **Neu**.  

4. Über den Sicherheitsrollendesigner können Sie Aktionen wie „Lesen“, „Schreiben“ oder „Löschen“ auswählen sowie den Bereich der einzelnen Aktionen festlegen. Der Geltungsbereich gibt an, auf welcher Ebene in der Umgebungshierarchie der Benutzer bestimmte Aktionen durchführen kann. Geben Sie im Feld **Role Name** (Rollenname) *Haustierfriseur* ein.
5. Klicken Sie auf die Registerkarte **Custom Entities** (Benutzerdefinierte Entitäten), und entscheiden Sie sich für eine geeignete benutzerdefinierte Entität. Für dieses Beispiel wird die benutzerdefinierte Entität **Pet** (Haustier) verwendet. 
6. Wählen Sie in der Zeile **Pet** (Haustier) jede der Berechtigungen viermal aus, bis der Geltungsbereich „Global“ ![Globaler Geltungsbereich](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt ist: **Lesen, Schreiben, Anfügen**
![Neue Sicherheitsrolle](media/share-model-driven-app/custom-security-role.png)
7. Da die Haustierpflege-App auch mit der Konto-Entität in Verbindung steht, klicken Sie auf die Registerkarte **Core Records** (Kerndatensätze), und wählen Sie in der Zeile **Account** (Konto) **Read** (Lesen) viermal aus, bis der Geltungsbereich „Global“ ![Globaler Geltungsbereich](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt ist. 
8. Klicken Sie auf **Speichern und schließen**. 
9. Geben Sie im Sicherheitsrollen-Designer im Feld **Role Name** (Rollenname) *Haustierpflegemanager* ein. 
10. Klicken Sie auf die Registerkarte **Custom Entities** (Benutzerdefinierte Entitäten), und entscheiden Sie sich für die **Haustier**-Entität. 
11. Wählen Sie in der Zeile **Pet** (Haustier) jede der Berechtigungen viermal aus, bis der Geltungsbereich „Global“ ![Globaler Geltungsbereich](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt ist: **Erstellen, Lesen, Schreiben, Anfügen, Anfügen an, Zuweisen, Freigeben**
12. Da die Haustierpflege-App auch mit der Konto-Entität in Verbindung steht, und da Manager Kontodatensätze erstellen und anpassen müssen, klicken Sie auf die Registerkarte **Core Records** (Kerndatensätze), und wählen Sie in der Zeile **Account** (Konto) jede der folgenden Berechtigungen viermal aus, bis der Geltungsbereich „Global“ ![Globaler Geltungsbereich](media/share-model-driven-app/organizational-scope-privilege.png) ausgewählt wurde. 
    **Erstellen, Lesen, Schreiben, Löschen, Anfügen, Anfügen an, Zuweisen, Freigabe**
13. Klicken Sie auf **Speichern und schließen**.

## <a name="assign-security-roles-to-users"></a>Zuweisen von Sicherheitsrollen für Benutzer
Sicherheitsrollen steuern über mehrere Zugriffsebenen und Berechtigungen den Zugriff auf Daten durch den Benutzer. Mithilfe der verschiedenen Zugriffsebenen und Berechtigungen, die einer bestimmten Sicherheitsrolle zugeordnet sind, werden die Datenansicht für den Benutzer und die Interaktionen des Benutzers mit diesen Daten eingeschränkt.

### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>Zuweisen einer Sicherheitsrolle für Haustierfriseure
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Assign users to the security role** (Benutzern eine Sicherheitsrolle zuweisen) **Security Users** (Sicherheitsbenutzer) aus.
2. Wählen Sie aus der angezeigten Liste die Haustierfriseure aus.
3. Klicken Sie auf **Rollen verwalten**.

    ![Rollen verwalten](media/share-model-driven-app/select-users-for-security-roles.png)

4. Wählen Sie im Dialogfeld **Manage User Roles** (Benutzerrollen verwalten) die Sicherheitsrolle **Haustierfriseure** aus, die Sie weiter oben erstellt haben, und klicken Sie auf **OK**.

### <a name="assign-a-security-role-to-pet-grooming-schedulers"></a>Zuweisen einer Sicherheitsrolle für Haustierpflegemanager
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Assign users to a security role** (Benutzern eine Sicherheitsrolle zuweisen) **Security Users** (Sicherheitsbenutzer) aus.
2. Wählen Sie aus der angezeigten Liste die Haustierpflegemanager aus.
3. Klicken Sie auf **Rollen verwalten**.
4. Wählen Sie im Dialogfeld **Benutzerrollen verwalten** die Sicherheitsrolle **Haustierpflegemanager** aus, die Sie weiter oben erstellt haben, und klicken Sie auf **OK**.


## <a name="add-security-roles-to-the-app"></a>Hinzufügen von Sicherheitsrollen für die App
Als Nächstes muss der App mindestens eine Sicherheitsrolle zugewiesen werden. Benutzer erhalten abhängig von den ihnen zugewiesenen Sicherheitsrollen Zugriff auf Apps.
1. Wählen Sie im Dialogfeld **Diese App freigeben** unter **Add the security role to your app** (Ihrer App die Sicherheitsrolle hinzufügen) **Meine Apps** aus.
2. Klicken Sie in der unteren rechten Ecke der App-Kachel der Contoso-Haustierpflege-App auf **Weitere Optionen (...)** und dann auf **Rollen verwalten**.

    ![Rollen für die App verwalten](media/share-model-driven-app/manage-roles.png)

4. Im Bereich **Rollen** können Sie festlegen, ob Sie den App-Zugriff allen oder nur ausgewählten Sicherheitsrollen gewähren. Wählen Sie die Rollen **Haustierpflegemanager** und **Haustierfriseur** aus, die Sie weiter oben erstellt haben.

    ![Sicherheitsrollen für die App auswählen](media/share-model-driven-app/app-security-roles.png)

5. Wählen Sie **Speichern**.
 
## <a name="share-the-link-to-your-app"></a>Teilen des Links Ihrer App
1. Kopieren Sie im Dialogfeld **Diese App freigeben** unter **Share the link to your app directly with users** (Link zur App direkt mit Benutzern teilen) die angezeigte URL.
 
2. Klicken Sie auf **Schließen**.
3. Fügen Sie die URL an einem Ort ein, auf den Ihre Benutzer zugreifen können, z.B. auf einer SharePoint-Website oder in einer E-Mail.

![Link teilen](media/share-model-driven-app/share-model-driven-URL.PNG)

Die App-URL finden Sie auch auf der Registerkarte **Eigenschaften** im App-Designer. 
    
![Kopieren der App-URL](media/share-model-driven-app/app-designer-copy-web-url.png)

## <a name="about-predefined-security-roles"></a>Vordefinierte Sicherheitsrollen
Diese vordefinierten Sicherheitsrollen sind in einer [!INCLUDE [powerapps](../../includes/powerapps.md)]-Umgebung verfügbar.


|Sicherheitsrolle  |Berechtigungen*  |Beschreibung |
|---------|---------|---------|
|Umgebungsersteller     |  Keine       | Kann mithilfe von Microsoft Flow neue Ressourcen erstellen, die einer Umgebung zugewiesen sind, einschließlich Apps, Verbindungen, benutzerdefinierter APIs, Gateways und Workflows. Verfügt jedoch nicht über Berechtigungen zum Zugreifen auf Daten innerhalb einer Umgebung. Weitere Informationen finden Sie in der [Übersicht zu Umgebungen](https://powerapps.microsoft.com/blog/powerapps-environments/).        |
|Systemadministrator     |  Erstellen, Lesen, Schreiben, Anpassen, Sicherheitsrollen       | Verfügt über umfassende Berechtigungen zum Anpassen oder Verwalten der Umgebung, einschließlich Erstellen, Verändern und Zuweisen von Sicherheitsrollen. Kann alle Daten in der Umgebung abrufen. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization).        |
|Systemanpasser     | Erstellen (selbst), Lesen (selbst), Schreiben (selbst), Löschen (selbst), Anpassen         | Verfügt über umfassende Berechtigungen zum Anpassen der Umgebung. Kann jedoch nur eigene Datensätze zu Umgebungsentitäten abrufen. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen für Anpassungen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization).        |
|Common Data Service-Benutzer     |  Lesen, Erstellen (selbst), Schreiben (selbst), Löschen (selbst)       | Kann eine App innerhalb einer Umgebung ausführen und häufig verwendete Aufgaben für eigene Datensätze durchführen.        |
|Delegat     | Im Auftrag eines anderen Benutzers handeln        | Ermöglicht es, als anderer Benutzer oder mit gewechselter Identität Code auszuführen.  Wird in der Regel mit einer anderen Sicherheitsrolle verwendet, damit auf Datensätze zugegriffen werden kann. Weitere Informationen finden Sie unter [Annehmen der Identität eines anderen Benutzers](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user).        |

*Die Berechtigungen gelten global, sofern keine anderen Angaben gemacht werden.

## <a name="next-steps"></a>Nächste Schritte
[Schnellstart: Ausführen einer modellgesteuerten App auf einem mobilen Gerät](run-app-client-model-driven.md)



