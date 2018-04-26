---
title: Schnellstart für das Erstellen einer benutzerdefinierten Entität | Microsoft-Dokumentation
description: Schnellstart für das Erstellen einer benutzerdefinierten Entität, die auf einer anderen Entität basiert oder von Grund auf neu erstellt wird
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 2232083de556bafcc978423dafb0e98e564aaa3b
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-create-a-custom-entity"></a>Schnellstart: Erstellen einer benutzerdefinierten Entität
Sie können eine benutzerdefinierte Entität zum Speichern von Daten erstellen, die spezifisch für Ihre Organisation sind. Sie können die Daten dann anzeigen, indem Sie eine App entwickeln, die auf die Entität verweist. Nachdem Sie eine Entität erstellt haben, können Sie [eines oder mehrere ihrer Felder erstellen oder bearbeiten](data-platform-manage-fields.md) und [Beziehungen zwischen Entitäten erstellen](data-platform-entity-lookup.md).

Diese Anleitung veranschaulicht das manuelle Erstellen einer benutzerdefinierten Entität. Sie können ebenfalls Power Query verwenden, um eine Entität zu erstellen, die auf vorhandenen Daten basiert. Weitere Informationen finden Sie unter [Create new entity using Power Query (Erstellen einer neuen Entität mithilfe von Power Query)](data-platform-cds-newentity-pq.md).

> [!NOTE]
> Sehen Sie sich die [Entitätsreferenz](../../developer/common-data-service/reference/about-entity-reference.md) an, bevor Sie eine Entität erstellen. Diese Entitäten beschreiben typische Szenarios, wie z.B. Konten und Kontakte. Wenn eine dieser Entitäten Ihre Anforderungen sofort oder nach nur geringfügigen Änderungen erfüllt, können Sie Zeit sparen, indem Sie mit diesen Entität beginnen.

## <a name="create-an-entity"></a>Erstellen einer Entität
1. Erweitern Sie unter [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie in der Befehlsleiste auf **Neue Entität**.
3. Geben Sie im Feld **Anzeigename** einen Namen ein, durch den Sie die Entität zukünftig leicht erkennen. Dieser wird ebenfalls für Formulare, Diagramme und andere Objekte verwendet, die mithilfe dieser Entität erstellt werden. Sie werden feststellen, dass zwei andere Felder ebenfalls aufgefüllt wurden:

    * Pluralanzeigename: Dieser wird verwendet, wenn mit der Entität über PowerApps oder Flow interagiert wird. Zudem wird er als Name der Entität in der Common Data Service-Web-API verwendet. Der Pluralname sollte automatisch generiert werden, kann jedoch geändert werden.
    * Name: Dieser entspricht dem eindeutigen Namen der Entität, darf keine Sonderzeichen oder Leerräume enthalten und muss eindeutig sein. Der Name enthält ebenfalls ein Präfix, das beim Erstellen Ihrer Umgebung eingerichtet wurde. Dieses wird verwendet, um sicherzustellen, dass die von Ihnen erstellten Entitäten exportiert und in andere Umgebungen importiert werden können, ohne mit den Namen anderer Entitäten in Konflikt zu geraten. Dieses Präfix kann geändert werden, indem das Präfix des Herausgebers der Common Data Service-Standardprojektmappe aktualisiert wird.

    > [!NOTE]
    > Die Felder **Anzeigename** können jederzeit aktualisiert werden, damit diese in Ihren Apps unterschiedlich angezeigt werden. Das Feld **Name** kann nach dem Speichern Ihrer Entität nicht geändert werden, da dies dazu führen könnte, dass vorhandene Apps beeinträchtigt werden.

    ![Neue Entität](./media/data-platform-cds-create-entity/newentitypanel.png "Bereich „Neue Entität“")

4. Klicken Sie auf **Weiter**, um zur Seite „Entitätsdetails“ zu gelangen. Standardmäßig beginnt jede Entität mit dem Feld „Primärer Name“. Dieses Feld wird verwendet, wenn Suchvorgänge für diese Entität erstellt werden. Es sollte in der Regel dafür verwendet werden, den Namen oder die primäre Beschreibung der Daten zu speichern, die in dieser Entität gespeichert sind.

    > [!NOTE]
    > Der Name und der Anzeigename des Felds **Primärer Name** können aktualisiert werden, bevor die Entität zum ersten Mal gespeichert wird. Dies können Sie beispielsweise tun, wenn Sie das Feld „Schülername“ statt „Primärer Name“ nennen möchten.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/newentitydetails.png "Neue Entitätsdetails")

5. Optional: Fügen Sie ein Textfeld zu Ihrer Entität hinzu, indem Sie auf **Feld hinzufügen** klicken. Geben Sie im Bereich „Neues Feld“ den **Anzeigenamen** für Ihr Feld ein, und wählen Sie den Datentyp aus. Weitere Informationen finden Sie unter [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md).

    ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Bereich „Neues Feld“")


6. Klicken Sie auf **Fertig**, um dieses Feld hinzuzufügen, und wiederholen Sie Schritt 5, um weitere Felder hinzuzufügen.
7. Klicken Sie auf **Entität speichern**, um Ihre Entität zu speichern und für die Verwendung in Apps zur Verfügung zu stellen.

    Ihre Entität wird in der Liste der Entitäten in Ihrer Datenbank angezeigt. Sie können den Filter in der Befehlsleiste von „Standard“ in „Benutzerdefiniert“ ändern, um die von Ihnen erstellten Entitäten anzuzeigen.

## <a name="system-fields"></a>Systemfelder
Alle Entitäten enthalten Systemfelder. Diese Felder sind schreibgeschützt. Daher können Sie sie nicht ändern oder löschen, und ihnen keine Werte zuweisen. Standardmäßig werden Systemfelder nicht in der Liste der Felder angezeigt, obwohl diese in der Entität vorhanden sind. Sie können den Filter in der Befehlsleiste von **Standard** in **Alle** ändern, um alle Felder anzuzeigen.

Weitere Informationen zu den Metadaten einer Entität finden Sie unter [Entitätsmetadaten](../../developer/common-data-service/entity-metadata.md).

## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md)
* [Definieren von Beziehungen zwischen Entitäten](data-platform-entity-lookup.md)
* [Generate an app by using a Common Data Service database (Generieren einer App mithilfe einer Common Data Service-Datenbank)](../canvas-apps/data-platform-create-app.md)
* [Neuerstellen einer App mithilfe einer Common Data Service-Datenbank](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

