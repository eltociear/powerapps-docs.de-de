---
title: "Verwalten von benutzerdefinierten Feldern in einer Entität | Microsoft-Dokumentation"
description: "Erstellen, Lesen, Aktualisieren und Löschen von benutzerdefinierten Feldern in einer Entität."
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/20/2017
ms.author: kfend
ms.openlocfilehash: f5d769459f9d10e1d0f4bab2c1cc182407865053
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="manage-custom-fields"></a>Verwalten von benutzerdefinierten Feldern
Sie können ein oder mehrere benutzerdefinierte Felder in einer beliebigen Entität erstellen und aktualisieren. Wenn Sie ein benutzerdefiniertes Feld erstellen, geben Sie einen Satz von Eigenschaften an, z.B. den Namen des Felds, den Anzeigenamen und den Typ der Daten, die es enthält. Weitere Informationen finden Sie unter [Entity field data types (Datentypen der Entitätsfelder)](https://docs.microsoft.com/common-data-service/entity-reference/field-data-types) und [Entity field properties (Eigenschaften der Entitätsfelder)](https://docs.microsoft.com/common-data-service/entity-reference/field-properties).

> [!NOTE]
> Jede Entität verfügt über [Systemfelder](data-platform-create-entity.md#system-fields-and-the-record-title-field), die z.B. angeben, wann und durch wen ein Datensatz zuletzt aktualisiert wurde. Darüber hinaus verfügen [Standardentitäten](data-platform-intro.md#standard-entities) über Standardfelder. Sie können keine System- oder Standardfelder ändern oder löschen. Wenn Sie ein benutzerdefiniertes Feld erstellen, sollte es zusätzliche Funktionalität zu diesen integrierten Feldern bieten.

## <a name="create-a-field"></a>Ein Feld erstellen

1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Common Data Service**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entities** (Entitäten). Eine Liste von Entitäten wird angezeigt. Klicken oder tippen Sie auf die Spaltenüberschrift **Typ**, um benutzerdefinierte Entitäten oben in der Liste anzuzeigen. Sie können in der Liste filtern, indem Sie mindestens ein Zeichen in der Suchleiste eingeben.

2. Klicken oder tippen Sie auf eine Entität, und klicken oder tippen Sie auf **Feld hinzufügen** am oberen Bildschirmrand.

3. Unter **Anzeigename** geben Sie die Textzeichenfolge ein, mit der Benutzer das Feld identifizieren können. Weitere Informationen finden Sie unter [Create an app (Erstellen einer App)](data-platform-create-app.md).

4. Unter **Name** geben Sie die Textzeichenfolge ein, mit der Sie auf das Feld verweisen, z.B. in einer Formel, wenn Sie eine App erstellen.
   
    > [!IMPORTANT]
    > Geben Sie einen Namen an, der eindeutig, klar und sinnvoll ist, da Sie ihn nicht mehr ändern können, nachdem Sie das Feld erstellt haben.

5. Unter **Typ** geben Sie den Datentyp an, den das Feld enthält, z.B. **Text** oder **Number**.
   
    > [!IMPORTANT]
    > Geben Sie diese Eigenschaft sorgfältig an, da Sie sie möglicherweise nicht mehr ändern können, wenn das Feld Daten enthält. Weitere Informationen zu den Datentypen, die Sie angeben können, finden Sie unter [Grundlegendes zu Entitäten](data-platform-intro.md#custom-fields).

6. Wenn Sie dazu aufgefordert werden, geben Sie zusätzliche Informationen für den Datentyp an, den Sie angegeben haben.

7. Aktivieren Sie das Kontrollkästchen bei **Eindeutig**, wenn jeder Datensatz einen eindeutigen Wert in diesem Feld haben muss.

8. Aktivieren Sie das Kontrollkästchen bei **Erforderlich**, wenn jeder Datensatz einen Wert in diesem Feld haben muss.
   
    > [!IMPORTANT]
    > Sie können nicht festlegen, dass ein benutzerdefiniertes Feld in einer Standardentität Daten enthalten muss. Diese Einschränkung verhindert, dass Sie wichtige Apps beeinträchtigen, die diese Entität verwenden.

9. Klicken oder tippen Sie auf **Speichern**, um Ihre Änderungen zu übernehmen.
   
    > [!IMPORTANT]
    > Ihre Änderungen gehen verloren, wenn Sie sie nicht speichern, bevor Sie eine andere Seite im Browser öffnen oder den Browser schließen.

Sie werden benachrichtigt, wenn der Vorgang erfolgreich abgeschlossen ist. Wenn der Vorgang nicht erfolgreich ist, gibt eine Fehlermeldung an, welche Probleme aufgetreten sind und wie Sie sie beheben können.

## <a name="update-or-delete-a-field"></a>Ein Feld aktualisieren oder löschen
1. Klicken oder tippen Sie unter [powerapps.com](https://web.powerapps.com) auf **Verwalten**, und klicken oder tippen Sie auf **Entitäten**, und klicken oder tippen Sie anschließend auf eine Entität.
2. Klicken oder tippen Sie in der Liste der Felder für die Entität, die Sie ausgewählt haben, auf ein Feld, und führen Sie anschließend einen der folgenden Schritte aus:
   
   * Ändern Sie eine oder mehrere Eigenschaften des Felds. Beachten Sie die [bewährten Methoden und Einschränkungen](data-platform-manage-fields.md#best-practices-and-restrictions).
     
       Drücken Sie Tab, um die nächste Eigenschaft auszuwählen. Um alle Änderungen an einem Feld rückgängig zu machen, klicken oder tippen Sie auf die Auslassungspunkte (...) für das Feld, und klicken oder tippen Sie anschließend auf **Rückgängig**.
   * Zum Löschen des Felds klicken oder tippen Sie auf die Auslassungspunkte (...) neben dem rechten Rand des Felds, und klicken oder tippen anschließend auf **Löschen**.
3. Klicken oder tippen Sie auf **Speichern**, um Ihre Änderungen zu übernehmen.
   
    > [!IMPORTANT]
    > Ihre Änderungen gehen verloren, wenn Sie sie nicht speichern, bevor Sie eine andere Seite im Browser öffnen oder den Browser schließen.

Sie werden benachrichtigt, wenn der Vorgang erfolgreich abgeschlossen ist. Wenn der Vorgang nicht erfolgreich ist, gibt eine Fehlermeldung an, welche Probleme aufgetreten sind und wie Sie sie beheben können.

## <a name="best-practices-and-restrictions"></a>Bewährte Methoden und Einschränkungen
Beachten Sie beim Erstellen und Ändern von Feldern Folgendes:

* Sie können keine Systemfelder oder ihre Werte ändern oder löschen.
* In einer Standardentität können Sie kein Standardfeld ändern oder löschen, kein Feld hinzufügen, das Daten benötigt, und keine andere Änderung durchführen, die eine App beeinträchtigen könnte, die diese Entität verwendet.
* In einer benutzerdefinierten Entität sollten Sie sicherstellen, dass Ihre Änderungen keine App beeinträchtigen, die diese Entität verwendet.
* Geben Sie allen benutzerdefinierten Feldern eindeutige Namen innerhalb der Entität. Felder können nicht umbenannt werden, nachdem sie erstellt wurden.
* Sie können den Datentyp jedes Felds ändern, sofern es noch keine Daten enthält. Wenn das Feld bereits Daten enthält, können Sie den Datentyp nur ändern, wenn alle vorhandenen Daten die Anforderungen des neuen Datentyp erfüllen. Sie können z.B. den Datentyp eines Felds von **Number** in **String** ändern, aber Sie können den Datentyp nicht von **String** in **Number** ändern, wenn das Feld nicht-numerische Daten enthält.
* Sie können eine App beeinträchtigen, die eine Entität verwendet, wenn Sie ein Feld in dieser Entität auf mindestens eine der folgenden Weisen ändern:
  * Sie ändern den Datentyp des Felds.
  * Sie machen Werte erforderlich, aber ein oder mehrere Datensätze enthalten in diesem Feld keinen Wert.
  * Sie machen eindeutige Werte erforderlich, aber zwei oder mehr Datensätze enthalten in diesem Feld denselben Wert.

## <a name="next-steps"></a>Nächste Schritte
* [Definieren von Beziehungen zwischen Entitäten](data-platform-entity-lookup.md)
* [Erstellen einer App mithilfe von Entitäten](data-platform-create-app.md)
* [Create an app from scratch using a Common Data Service database (Erstellen einer App von Grund auf neu mithilfe einer Common Data Service-Datenbank)](data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

