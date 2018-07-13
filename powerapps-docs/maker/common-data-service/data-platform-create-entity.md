---
title: 'Schnellstart: Erstellen einer benutzerdefinierten Entität | Microsoft-Dokumentation'
description: In diesem Schnellstartartikel erhalten Sie Informationen zum Erstellen einer benutzerdefinierten Entität in PowerApps.
author: Mattp123
ms.service: powerapps
ms.component: cds
ms.topic: quickstart
ms.date: 05/01/2018
ms.author: matp
ms.openlocfilehash: 45a341d28b4138ce03ce50d7325f9daa0f159d1a
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37897430"
---
# <a name="quickstart-create-a-custom-entity"></a>Schnellstart: Erstellen einer benutzerdefinierten Entität
Mit einer *Entität* werden in PowerApps die Informationen definiert, die Sie in Form von Datensätzen nachverfolgen möchten. Diese enthalten üblicherweise Eigenschaften wie den Firmennamen, den Standort, die Produkte, die E-Mail-Adresse und die Telefonnummer. Sie können diese Daten dann abrufen, indem Sie eine App entwickeln, die auf die Entität verweist. PowerApps stellt vorkonfigurierte Standardentitäten zur Verfügung, die für typische Szenarios in einer Organisation (beispielsweise das Nachverfolgen von Terminen) verwendet werden können. In einigen Fällen ist es aber möglicherweise erforderlich, benutzerdefinierte Entitäten zu erstellen, mit denen organisationsspezifische Daten gespeichert werden können.

In diesem Schnellstartartikel erfahren Sie, wie Sie die benutzerdefinierte Entität „Produktbewertung“ erstellen, die anschließend zur Erstellung einer App genutzt werden kann, mit der Bewertungen und Kommentare für Produkte angezeigt werden, die Ihr Unternehmen verkauft.

## <a name="prerequisites"></a>Voraussetzungen
Für diesen Schnellstart sind die folgenden Elemente erforderlich:
* Entweder eine Lizenz von PowerApps-Plan 2 oder von Microsoft Flow-Tarif 2. Sie können sich alternativ auch für eine [kostenlose Testversion von PowerApps-Plan 2](https://web.powerapps.com/signup?redirect=marketing&email=) registrieren.
* Entweder die Rolle „System Adminsitrator“ (Systemadministrator) oder „System Customizer“ (Systemanpasser) innerhalb von Common Data Service für Apps.

## <a name="sign-in-to-powerapps"></a>Anmelden bei PowerApps
Melden Sie sich bei PowerApps unter [https://web.powerapps.com](https://web.powerapps.com) an.

## <a name="create-an-entity"></a>Erstellen einer Entität
1. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Daten**, um das Element zu erweitern, und dann auf **Entitäten**.

    ![Liste der Entitäten und der zugehörigen Informationen](./media/data-platform-cds-create-entity/entitylist.png "Entity List")

2. Klicken oder tippen Sie in der Befehlsleiste auf **New entity** (Neue Entität).

    Vor dem Erstellen einer Entität sollten Sie sich die [Entitätsreferenz](../../developer/common-data-service/reference/about-entity-reference.md) ansehen, die eine Beschreibung der verfügbaren Standardentitäten enthält. Diese Entitäten können für typische Szenarios verwendet werden. Wenn eine dieser Entitäten Ihren Anforderungen entspricht oder nur geringfügige Änderungen erforderlich sind, können Sie Zeit sparen, indem Sie mit dieser Entität beginnen. 

3. Geben Sie zuerst im Bereich **New entity** (Neue Entität) im Feld **Display name** (Anzeigename) die Zeichenfolge **Produktbewertung** und anschließend optional eine Beschreibung ein. Beschreibungen sind hilfreich, wenn andere Personen diese Entität verwenden. Andere Felder im Bereich werden wie unten beschrieben automatisch aufgefüllt. Klicken Sie abschließend auf **Next** (Weiter).

   * **Plural display name** (Anzeigename im Plural): Dieses Feld wird automatisch ausgefüllt, wenn Sie einen Anzeigenamen eingeben. Sie können diese Einstellung jedoch bei Bedarf ändern. Der Anzeigename im Plural ist der Name der Entität in der Common Data Service-WebAPI und wird verwendet, wenn mit der Entität über PowerApps oder Flow interagiert wird.
   * **Name**: Dieses Feld wird auch automatisch ausgefüllt, wenn Sie einen Anzeigenamen eingeben. Das Präfix wurde beim Erstellen der Umgebung eingerichtet und stellt sicher, dass die von Ihnen erstellten Entitäten exportiert und in andere Umgebungen importiert werden können, ohne mit den Namen anderer Entitäten in Konflikt zu geraten. Sie können dieses Präfix ändern, indem Sie das Präfix des Herausgebers der Common Data Service-Standardlösung aktualisieren. Damit bei vorhandenen Apps keine Fehler auftreten, können Sie den Namen nach dem Speichern der Entität nicht mehr ändern.
     
     ![Neue Entität](./media/data-platform-cds-create-entity/newentitypanel.png "New entity panel")

4. Klicken oder tippen Sie auf der Seite mit den Entitätsdetails auf das Feld **Primary Name** (Primärer Name), um den Bereich **Primary Name** zu öffnen. Ersetzen Sie anschließend im Feld **Display name** den Wert für **Primary Name** durch **Produktbewertung**. Ersetzen Sie im Feld **Name** den Wert für **Primary Name** durch **Produktbewertung**, und klicken oder tippen Sie auf **Done** (Fertig).
 
    Standardmäßig enthält jede Entität das Feld „Primary Name“, das beim Herstellen von Beziehungen mit anderen Entitäten von Nachschlagefeldern verwendet wird. Das Feld „Primary Name“ speichert üblicherweise den Namen oder die primäre Beschreibung der Daten, die in der Entität gespeichert sind. Sie können den Namen und den Anzeigenamen des Felds „Primärer Name“ aktualisieren, bevor die Entität zum ersten Mal gespeichert wird.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/newentitydetails.png "Neue Entitätsdetails")

5. Führen Sie die folgenden Schritte aus, um der Entität ein Feld hinzuzufügen:
 
    a. Klicken oder tippen Sie in der Befehlsleiste auf **Add field** (Feld hinzufügen), um den Bereich **Field properties** (Feldeigenschaften) zu öffnen.

    b. Geben Sie im Feld **Display name** die Zeichenfolge **Datum der Bewertung** ein.

    c. Wählen Sie aus der Dropdownliste **Data type** (Datentyp) den Eintrag **Date Only** (Nur Datum) aus.

    d. Aktivieren Sie das Kontrollkästchen **Required** (Erforderlich), indem Sie darauf klicken oder tippen.
    
    e. Klicken oder tippen Sie auf **Done** (Fertig).
     
    Weitere Informationen finden Sie unter [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md).

    ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel-2.png "Bereich „Neues Feld“")

6. Wiederholen Sie den vorherigen Schritt, um drei weitere Felder mit den folgenden Konfigurationen hinzuzufügen:
   * **Display name** = Produktbewertung; **Data type** = Ganze Zahl. Klicken oder tippen Sie auf das Kontrollkästchen **Required**.
   * **Display name**  = Name des Rezensenten; **Data type** = Text.
   * **Anzeigename**  = Kommentar des Rezensenten; **Datentyp** = Text.

     Nach diesem Vorgang sollten fünf Felder auf der Seite zu den Entitätsdetails aufgeführt sein.

     ![Liste mit Feldern](./media/data-platform-cds-create-entity/addedfields.png "List of fields")

     Beachten Sie, dass alle Entitäten über schreibgeschützte Systemfelder verfügen. Standardmäßig werden Systemfelder nicht in der Felderliste angezeigt, obwohl diese in der Entität vorhanden sind. Sie können den Filter in der Befehlsleiste von **Default** (Standard) in **All** (Alle) ändern, um alle Felder anzuzeigen. Weitere Informationen zu den Metadaten einer Entität finden Sie unter [Entitätsmetadaten](../../developer/common-data-service/entity-metadata.md).

7. Klicken Sie auf **Entität speichern**, um Ihre Entität zu speichern und für die Verwendung in Apps zur Verfügung zu stellen.

    Die Entität „Produktbewertung“ sollte in der Liste der Entitäten in Ihrer Datenbank angezeigt werden. Wenn die Entität nicht angezeigt wird, müssen Sie den Filter in der Befehlsleiste von **Default** in **Custom** (Benutzerdefiniert) ändern.

    ![Filter](./media/data-platform-cds-create-entity/filter.png "Filter selection")

## <a name="next-steps"></a>Nächste Schritte
In diesem Schnellstartartikel haben Sie erfahren, wie Sie die benutzerdefinierte Entität „Produktbewertung“ erstellen, die zur Erstellung einer App genutzt werden kann, mit der Bewertungen und Kommentare für alle Produkte angezeigt werden, die von einem Unternehmen verkauft werden. Im nächsten Artikel erfahren Sie, wie Sie Beziehungen zwischen Entitäten (in diesem Fall zwischen der Standardentität „Produkt“ und Ihrer benutzerdefinierten Entität „Produktbewertung“) definieren, sodass Sie jedem Produkt die zugehörigen Bewertungen und Kommentare zuordnen können.

> [!div class="nextstepaction"]
> [Erstellen einer Beziehung](data-platform-entity-lookup.md)

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfasst und speichert Microsoft benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen. Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller erstellen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und Lücken in der Abdeckung der Standardentität des Diensts offenlegen, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.
