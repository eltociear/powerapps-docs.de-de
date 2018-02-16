---
title: Konfigurieren von Datenbanksicherheit | Microsoft-Dokumentation
description: "Dieses Thema erläutert das Konfigurieren von Datenbanksicherheit."
services: powerapps
documentationcenter: na
author: maertenm
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/08/2017
ms.author: kfend
ms.openlocfilehash: ea4fc21eb98ddb4861739559062f01190fb14819
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="configure-database-security"></a>Datenbanksicherheit konfigurieren
Der Common Data Service verwendet ein rollenbasiertes Sicherheitsmodell, das den sicheren Zugriff auf die Datenbank unterstützt. In diesem Thema wird erläutert, wie die Sicherheitsartefakte erstellt werden, die Sie zum Schützen von Apps benötigen. Die Benutzerrollen steuern den Laufzeitzugriff auf Daten und sind getrennt von den Umgebungsrollen, die die Umgebungsadministratoren und Umgebungsersteller regeln. Einen Überblick über die Umgebungen finden Sie unter [Environments overview (Überblick über Umgebungen)](environments-overview.md).

Es ist wichtig zu verstehen, welche Zugriffsebene für diese Entitäten für Benutzer der App erforderlich ist. Der Common Data Service unterstützt Berechtigungen zum Erstellen, Lesen, Aktualisieren und Löschen (Create, Read, Update, Delete, CRUD) für Entitäten.

* **Erstellen**: Ein Benutzer kann neue Einträge in der Entität erstellen.
* **Lesen**: Ein Benutzer kann vorhandene Einträge in der Entität anzeigen und durchsuchen.
* **Aktualisieren**: Ein Benutzer kann einen vorhandenen Eintrag in der Entität aktualisieren oder bearbeiten.
* **Löschen**: Ein Benutzer kann einen vorhandenen Eintrag in der Entität löschen oder entfernen.

Die zwei am häufigsten verwendeten Berechtigungsstufen sind der schreibgeschützte Zugriff und der Vollzugriff. Der Common Data Service beinhaltet Berechtigungssätze auf diesen zwei Berechtigungsstufen für alle seine Entitäten. Ansichtsberechtigungssätze bieten Lesezugriff auf eine Entität. Wartungsberechtigungssätze bieten Vollzugriff auf eine Entität.

Das Sicherheitsmodell ermöglicht die Zuweisung beliebiger Kombinationen dieser Berechtigungen zu Benutzerrollen. Rollen kombinieren die verschiedenen Berechtigungen, die im Rahmen der ihnen hinzugefügten Berechtigungssätze erteilt werden. Daher können die Mitglieder einer Rolle auf alle Daten zugreifen, auf die ihnen die in der jeweiligen Rolle enthaltenen Berechtigungssätze Zugriff gewähren. Weitere Informationen zum Sicherheitsmodell von Common Data Service finden Sie unter [Security model (Sicherheitsmodell)](https://docs.microsoft.com/common-data-service/entity-reference/security-model).

## <a name="identify-the-entities"></a>Identifizieren der Entitäten
Um die richtigen Zugriffssteuerungen für eine App zu konfigurieren, müssen Sie wissen, welche Entitäten die App verwendet. Führen Sie die folgenden Schritte aus, um eine Liste der von einer App verwendeten Entitäten anzuzeigen.

1. Öffnen Sie die App in Microsoft PowerApps Studio.
2. Klicken oder tippen Sie auf der Registerkarte **Inhalt** auf **Datenquellen**. Die Liste der Datenquellen wird im rechten Bereich angezeigt.

## <a name="configure-security"></a>Konfigurieren der Sicherheit
Wenn Sie eine neue Entität erstellen, müssen Sie auch einen neuen Berechtigungssatz erstellen oder einen vorhandenen Berechtigungssatz bearbeiten, um Zugriff auf die Daten der betreffenden Entität bereitzustellen. Wenn Sie eine App erstellen, wird empfohlen, dass Sie auch einen Berechtigungssatz für den Zugriff auf alle Entitäten erstellen, die zum Ausführen der App erforderlich sind. Die Sicherheit wird im Admin Center verwaltet.

1. Öffnen Sie das [Admin Center](https://admin.powerapps.com).
2. Klicken oder tippen Sie auf die Umgebung, die Ihre Datenbank enthält.
3. Klicken oder tippen Sie auf **Sicherheit**. Anschließend können Sie die Registerkarten **Berechtigungssätze** und **Benutzerrollen** verwenden, um die Sicherheit für Ihre Datenbank zu konfigurieren.

## <a name="create-a-permission-set"></a>Erstellen eines Berechtigungssatzes
Um den Zugriff auf eine neue App zu ermöglichen, müssen Sie zunächst einen neuen Berechtigungssatz erstellen.

1. Klicken oder tippen Sie auf **Berechtigungssätze**.
2. Klicken oder tippen Sie auf **Neuer Berechtigungssatz**, um einen Berechtigungssatz zu erstellen.
3. Geben Sie einen Namen und eine Beschreibung für den Berechtigungssatz ein, und klicken oder tippen Sie anschließend auf **Erstellen**. Der neue Berechtigungssatz wird in der Liste der Berechtigungssätze angezeigt.
4. Klicken oder tippen Sie auf den soeben erstellten Berechtigungssatz.
5. Klicken oder tippen Sie auf die Registerkarte **Entitäten**. Die Registerkarte **Entitäten** enthält eine Liste aller Entitäten in Ihrer Datenbank. Aktivieren Sie für jede Entität, die in Ihrer App verwendet wird, das Kontrollkästchen zum Zulassen der Berechtigung.
6. Klicken oder tippen Sie auf **Speichern**.

## <a name="create-a-policy-technical-preview"></a>Erstellen einer Richtlinie (Technical Preview)
Um den Zugriff auf die in einer Entität enthaltenen Datensätze zu aktivieren oder einzuschränken, müssen Sie zuerst eine Richtlinie erstellen.

1. Klicken oder tippen Sie auf **Richtlinien**.
2. Klicken oder tippen Sie auf **Neue Richtlinie**.
3. Geben Sie einen Namen und eine Beschreibung für die Richtlinie ein.
4. Wählen Sie den Typ der zu erstellenden Richtlinie aus. Wenn Sie eine Auswahllisten-Richtlinie erstellen, geben Sie die zu verwendende Auswahlliste ein.
5. Wählen Sie den zu verwendenden Operator aus.
6. Wählen Sie den Prüfwert für die Richtlinie aus.
7. Klicken oder tippen Sie auf **Erstellen**.

## <a name="assign-a-policy-technical-preview"></a>Zuweisen einer Richtlinie (Technical Preview)
Um eine Richtlinie anzuwenden, müssen Sie sie einer Datenentität in einem Berechtigungssatz zuweisen.

1. Klicken oder tippen Sie auf **Berechtigungssätze**.
2. Klicken oder tippen Sie auf den Berechtigungssatz, unter dem Sie eine Richtlinie zuweisen möchten.
3. Klicken oder tippen Sie auf die Schaltfläche **Bearbeiten** für die Entität, der Sie eine Richtlinie zuweisen möchten.
4. Klappen Sie den Abschnitt **Richtlinienzuweisung** auf.
5. Wählen Sie die Datenoperationen aus, auf die eine Richtlinie angewendet werden soll (**Erstellen**, **Lesen**, **Aktualisieren** oder **Löschen**).
6. Wählen Sie das Entitätsfeld aus, auf dem die Richtlinie basieren soll.
7. Wählen Sie die zuzuweisende Richtlinie aus.
8. Klicken oder tippen Sie auf **Zuweisen**.
9. Klicken oder tippen Sie auf **Speichern**.

## <a name="create-and-assign-a-role"></a>Erstellen und Zuweisen einer Rolle
Wenn die richtigen Berechtigungen in einem Berechtigungssatz enthalten sind, können Sie eine Rolle erstellen, die Benutzern zugewiesen werden kann.

1. Klicken oder tippen Sie auf **Benutzerrollen**.
2. Klicken oder tippen Sie auf **Neue Rolle**.
3. Geben Sie einen Namen und eine Beschreibung für die Rolle ein, und klicken oder tippen Sie dann auf **Erstellen**. Die neue Rolle wird in der **Benutzer**-Rollenliste angezeigt.
4. Klicken oder tippen Sie auf die soeben erstellte Rolle.
5. Klicken oder tippen Sie auf die Registerkarte **Berechtigungssätze**.
6. Geben Sie den Namen des Berechtigungssatzes ein, den Sie zuvor erstellt hatten. Klicken oder tippen Sie in der Dropdownliste, die während der Eingabe angezeigt wird, auf den Berechtigungssatz, um ihn der Rolle hinzuzufügen. Wiederholen Sie diesen Schritt für jeden weiteren Berechtigungssatz, den Sie in die Rolle aufnehmen möchten.
7. Klicken oder tippen Sie auf die Registerkarte **Benutzer** für die Rolle.
8. Geben Sie die Namen oder E-Mail-Adressen der Benutzer oder Gruppen ein, die der Rolle hinzugefügt werden sollen. Klicken oder tippen Sie in der Dropdownliste, die während der Eingabe angezeigt wird, auf den Benutzer. Benutzer und Gruppen, denen die Rolle zugewiesen werden soll, werden zur Liste hinzugefügt.
9. Klicken oder tippen Sie auf **Speichern**.

Die Benutzer oder Gruppen in dieser Rolle können nun auf die Daten zugreifen, auf die ihnen einer der dieser Rolle zugeordneten Berechtigungssätze den Zugriff erteilt. Um die Daten in Ihrer Datenbank zu verwenden, muss ein Benutzer über eine Sicherheitsrolle und über Zugriff auf eine PowerApp-App verfügen, die die Daten verwendet.

## <a name="edit-permission-sets-and-roles"></a>Bearbeiten von Berechtigungssätzen und Rollen
Um Rollen und Berechtigungssätze nach der Erstellung zu bearbeiten, klicken Sie auf die Schaltfläche **Bearbeiten**.

Um eine Rolle oder einen Berechtigungssatz zu löschen, verwenden Sie die Schaltfläche **Löschen**.

## <a name="out-of-box-security-roles"></a>Sofort verfügbare Sicherheitsrollen
Zwei Sicherheitsrollen stehen sofort zur Verfügung:

* **Datenbankbesitzer**: Die Rolle „Datenbankbesitzer“ ist für Benutzer in einer administrativen Funktion gedacht. Der Ersteller der Umgebung wird dieser Rolle automatisch zugewiesen. Benutzer in dieser Rolle besitzen immer Vollzugriff auf alle Entitäten in der Datenbank. Sie haben sogar Vollzugriff auf neu hinzugefügte Entitäten. Benutzer in dieser Rolle können außerdem Schemas in der Datenbank erstellen und bearbeiten. Sie müssen dieser Rolle keine Berechtigungssätze hinzufügen. Sie müssen ihr lediglich Benutzer zuweisen.
* **Organisationsbenutzer**: Die Rolle „Organisationsbenutzer“ ist die Standardrolle, die allen Benutzern zugewiesen wird. Der Zweck dieser Rolle besteht darin, allen Benutzern den Zugriff auf die Entitäten zu ermöglichen, die öffentliche Daten enthalten. Wenn eine App im eingeschränkten Modus freigegeben wird, sollten die von der App verwendeten Entitäten in dieser Rolle enthalten sein. Sie müssen diese Rolle nicht zuweisen, da sie bereits jedem in Ihrer Organisation zugewiesen ist. Sie müssen nur die Berechtigungssätze hinzufügen, die Sie Ihrer gesamten Organisation geben möchten.

