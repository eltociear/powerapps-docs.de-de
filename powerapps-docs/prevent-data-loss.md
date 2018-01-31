---
title: Richtlinien zur Verhinderung von Datenverlust (DLP) | Microsoft-Dokumentation
description: "Einführung in die Richtlinien zur Verhinderung von Datenverlust für Microsoft PowerApps."
services: 
suite: powerapps
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/28/2016
ms.author: deonhe
ms.openlocfilehash: a9f6bf12672c425a30d05a8072aafd34945eb795
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="data-loss-prevention-dlp-policies"></a>Richtlinien zur Verhinderung von Datenverlust (DLP)

Die Daten einer Organisation sind wichtig für deren Erfolg. Die Daten müssen zum Treffen von Entscheidungen zum Lesen verfügbar sein, jedoch geschützt werden, damit sie nicht für Personen freigegeben werden, die keinen Zugriff darauf haben sollten. Um diese Daten zu schützen, bietet Microsoft PowerApps (PowerApps) Ihnen die Möglichkeit, Richtlinien zu erstellen und durchzusetzen, die definieren, für welche Verbraucherdienste/Connectors bestimmte Unternehmensdaten freigegeben werden können. Diese Richtlinien, die definieren, wie Daten freigegeben werden können, werden als Richtlinien zur Verhinderung von Datenverlust (DLP) bezeichnet.  

## <a name="why-create-a-dlp-policy"></a>Warum sollten Sie eine DLP-Richtlinie erstellen?
Sie würden eine DLP-Richtlinie erstellen, um klar zu definieren, für welche Verbraucherdienste Unternehmensdaten freigegeben werden können. Beispielsweise möchte eine Organisation, die PowerApps verwendet, möglicherweise nicht, dass ihre in SharePoint gespeicherten Unternehmensdaten automatisch in Ihrem Twitter-Feed veröffentlicht werden. Um dies zu verhindern, können Sie eine DLP-Richtlinie erstellen, die SharePoint-Daten als Quelle für Tweets blockiert.

Vorteile einer DLP-Richtlinie:
* Stellt sicher, dass Daten in der gesamten Organisation auf einheitliche Weise verwaltet werden  
* Verhindert, dass wichtige Unternehmensdaten versehentlich in Diensten wie auf Webseiten von sozialen Medien veröffentlicht werden   

## <a name="managing-dlp-policies"></a>Verwalten von DLP-Richtlinien
### <a name="prerequisites"></a>Voraussetzungen
Um DLP-Richtlinien zu erstellen, zu bearbeiten oder zu löschen, werden die folgenden Elemente benötigt:

* Entweder Umgebungsadministrator- oder Mandantenadministratorberechtigungen. Weitere Informationen zu Berechtigungen finden Sie im [Umgebungsthema](environments-administration.md)

### <a name="create-a-dlp-policy"></a>Erstellen einer DLP-Richtlinie
Um eine DLP-Richtlinie zu erstellen, brauchen Sie die Berechtigungen für mindestens eine Umgebung.  

Führen Sie diese Schritt aus, um eine DLP-Richtlinie zu erstellen, die verhindert, dass Daten, die in Ihrer SharePoint-Datenbank gespeichert sind, auf Twitter veröffentlicht werden:  

1. Wählen Sie auf der Registerkarte „Datenrichtlinien“ den Link **Neue Richtlinie** aus:  
   ![Anmelden](./media/prevent-data-loss/create-policy-1.png)    
2. Geben Sie den Namen der DLP-Richtlinie als *Sichern des Datenzugriffs für Contoso* unter der Bezeichnung **Name der Datenrichtlinie** oben auf der sich öffnenden Seite ein:   
   ![Anmelden](./media/prevent-data-loss/create-policy-2.png)  
3. Wählen Sie die [Umgebung](environments-administration.md) auf der Registerkarte **Applies to** (Gilt für) aus.  
   ![Anmelden](./media/prevent-data-loss/create-policy-3.png)  
4. Wählen Sie die Registerkarte **Datengruppen** aus:  
   ![Anmelden](./media/prevent-data-loss/create-policy-4.png)  
5. Wählen Sie den Link **+ Add** (Hinzufügen) im Gruppenfeld **Business data only** (Nur Unternehmensdaten) aus:    
   ![Anmelden](./media/prevent-data-loss/create-policy-5.png)  
6. Wählen Sie auf der Seite **Dienste hinzufügen** die Dienste **SharePoint** und **Salesforce** aus:  
   ![Anmelden](./media/prevent-data-loss/create-policy-6.png)  
7. Wählen Sie die Schaltfläche **Dienste hinzufügen** aus, um die von Ihnen ausgewählten Dienste zu der Liste der Dienste hinzuzufügen, die Unternehmensdaten freigeben dürfen:    
   ![Anmelden](./media/prevent-data-loss/create-policy-7.png)  
8. Wählen Sie **Richtlinie speichern** aus:  
   ![Anmelden](./media/prevent-data-loss/create-policy-8.png)  
9. Nach einigen Augenblicken wird Ihre neue DLP-Richtlinie in der Liste der Richtlinien zur Verhinderung von Datenverlust angezeigt:  
   ![Anmelden](./media/prevent-data-loss/create-policy-9.png)  
10. **Optional:** Senden Sie an Ihr Team eine E-Mail oder eine andere Benachrichtigung mit dem Hinweis, dass nun eine neue DLP-Richtlinie verfügbar ist.

Herzlichen Glückwunsch, Sie haben nun eine DLP-Richtlinie erstellt, die es einer App ermöglicht, Daten zwischen SharePoint und Salesforce zu teilen, und die die Freigabe der Daten für andere Dienste blockiert.  

### <a name="find-a-dlp-policy"></a>Suchen einer DLP-Richtlinie
#### <a name="admins"></a>Administratoren
Administratoren können die Suchfunktion des Admin Centers verwenden, um bestimmte DLP-Richtlinien zu suchen.  

> [!NOTE]
> Administratoren sollten alle DLP-Richtlinien veröffentlichen, sodass Benutzer sich der Richtlinien bewusst sind, bevor sie PowerApps erstellen.

#### <a name="makers"></a>Ersteller
Wenn Sie keine Administratorberechtigungen haben und mehr über die DLP-Richtlinien in Ihrer Organisation erfahren möchten, wenden Sie sich an Ihren Administrator. Weitere Informationen erhalten Sie zudem im [Thema zur Umgebungserstellung](environments-overview.md)  

> [!NOTE]
> Nur Administratoren können DLP-Richtlinien bearbeiten oder löschen.  

### <a name="edit-a-dlp-policy"></a>Bearbeiten einer DLP-Richtlinie
1. Starten Sie das Admin Center, indem Sie https://admin.powerapps.com aufrufen.   
2. Wählen Sie im Admin Center, das gestartet wird, auf der linken Seite den Link **Datenrichtlinien** aus.  
   ![Anmelden](./media/prevent-data-loss/2.png)  
3. Suchen Sie die Liste der vorhandenen DLP-Richtlinien, und wählen Sie den Link „Bearbeiten“ neben der Richtlinie aus, die Sie bearbeiten möchten:  
   ![Anmelden](./media/prevent-data-loss/3.png)  
4. Nehmen Sie die gewünschten Änderungen vor. Sie können z.B. die Umgebung oder die Dienste in den Datengruppen bearbeiten.  
5. Wählen Sie **Richtlinie speichern** aus, um Ihre Änderungen zu speichern:  
   ![Anmelden](./media/prevent-data-loss/create-policy-8.png)  

Die Richtlinie wurde jetzt aktualisiert. Sie können bestätigen, dass die Änderungen an Ihrer Richtlinie vorgenommen wurden, indem Sie diese in der Liste der Richtlinien zur Verhinderung von Datenverlust suchen und ihre Eigenschaften überprüfen.   

### <a name="delete-a-dlp-policy"></a>Löschen einer DLP-Richtlinie
1. Starten Sie das Admin Center, indem Sie https://admin.powerapps.com aufrufen.    
2. Wählen Sie im Admin Center, das gestartet wird, auf der linken Seite den Link **Datenrichtlinien** aus.  
   ![Anmelden](./media/prevent-data-loss/2.png)  
3. Suchen Sie die Liste der vorhandenen DLP-Richtlinien, und wählen Sie den Link „Löschen“ neben der Richtlinie aus, die Sie löschen möchten:  
   ![Anmelden](./media/prevent-data-loss/3-delete.png)  
4. Bestätigen Sie, dass Sie die Richtlinie wirklich löschen möchten, indem Sie die Schaltfläche **Löschen** auswählen:  
   ![Anmelden](./media/prevent-data-loss/4.png)  

Die Richtlinie wurde jetzt gelöscht. Sie können bestätigen, dass die Richtlinie nicht mehr in der Liste der Richtlinien zur Verhinderung von Datenverlust aufgeführt wird, indem Sie den Link **Datenrichtlinien** auf der linken Seite auswählen und die Liste der Richtlinien überprüfen.   

### <a name="dlp-policy-permissions"></a>DLP-Richtlinienberechtigungen
Nur Mandanten- und Umgebungsadministratoren können DLP-Richtlinien erstellen und bearbeiten. Weitere Informationen zu Berechtigungen finden Sie im Thema zu [Umgebungen](environments-administration.md).  

## <a name="next-steps"></a>Nächste Schritte
* [Erfahren Sie mehr über Umgebungen](environments-administration.md)  
* [Erfahren Sie mehr über Microsoft PowerApps](getting-started.md)  
* [Erfahren Sie mehr zum Admin Center](introduction-to-the-admin-center.md)  

