---
title: Verwenden Sie die Admin App und das Dashboard in der Lösung Regional Government Emergency Response and Monitoring | Microsoft Docs
description: Enthält detaillierte Anweisungen für Admins von Regionalorganisationen zur Konfiguration von Stammdaten, zur Verwaltung von Portalbenutzern und zur Anzeige von Dashboards für wichtige Einblicke.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 7797e66766d68117cc88b151e8faa14e660ec7d4
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342109"
---
# <a name="use-the-admin-app-and-dashboard"></a>Verwenden Sie die Admin-App und das Dashboard

Dieser Artikel richtet sich an Business-Admins in regionalen medizinischen Organisationen, die die Admin Apps (modellbasierte Apps) zur Durchführung der folgenden Aktivitäten verwenden können:

-   Hinzufügen und Verwalten von Stammdaten in Entitäten, die für die Lösung erforderlich sind

-   Erstellen und verwalten Sie Portalbenutzer (Kontakte). Bei diesen Anwendern handelt es sich in der Regel um die Admins von übergeordneten medizinischen Organisationen, die ein oder mehrere Krankenhaussysteme verwalten.

- Genehmigen Sie Portal-Benutzeranfragen und lehnen Sie sie ab.

- Zeigen Sie Power BI-Dashboards in ihrem Mandant an.

## <a name="prerequisites"></a>Voraussetzungen

-   Stellen Sie sicher, dass Sie die entsprechende Sicherheitsrolle und Zugriff auf die Admin App (modellbasierte App) haben. Wenden Sie sich an Ihren IT-Admin, wenn Sie nicht auf die Admin-App zugreifen oder diese nicht verwenden können.

-   Stellen Sie sicher, dass Sie Zugang zu den Beispieldaten haben. Die Beispieldaten sind im Bereitstellungspaket unter dem Ordner **SampleData** verfügbar.

## <a name="add-and-manage-master-data"></a>Hinzufügen und Verwalten von Stammdaten

Wenn Sie sich in der App Admin (modellbasiert) anmelden, sehen Sie im linken Fensterbereich die Entitäten, in die Sie die Stammdaten eintragen müssen. Wählen Sie die Entität im linken Navigationsbereich, um die Daten anzuzeigen oder zu verwalten.

> [!div class="mx-imgBorder"] 
> ![Befüllen der Stammdaten](media/config-entities-master-data.png "Füllen Sie die Stammdaten")

-   **Hierarchiebereich**: Daten für Entitäten in diesem Bereich können entweder durch Import von Daten aus den Beispieldatendateien oder manuell hinzugefügt werden. Die Entitäten im Bereich **Hierarchie** werden in der Reihenfolge aufgelistet, in der Sie Daten auffüllen sollten. Außerdem können übergeordnete Admins (Krankenhaus-Admins) Daten unter den folgenden Entitäten für ihr Krankenhaus vom Portal aus einsehen und verwalten: **Systeme**, **Regionen**, und **Einrichtungen**.

-   **Admin-Entitäten-Bereich**: Daten im Bereich **Versorgung** Entitäten werden durch den Import von Daten aus der Beispieldatendatei hinzugefügt. Sie können Angebotsdaten später manuell hinzufügen und verwalten.

-   **Kundenbereich**: Sie verwenden **Portalbenutzer** zur [Verwaltung von Portalbenutzern](#manage-portal-users) und **Benutzeranfragen** zur [Verwaltung von Portalbenutzeranfragen](#manage-portal-user-requests).

-   **Ressourcenbereich**: Wählen Sie **Dokumentation**, um dieses Dokument anzuzeigen.

Es gibt zwei Möglichkeiten, wie Sie Stammdaten zu Entitäten in der App hinzufügen können:

-  Importieren Sie Daten unter Verwendung der Beispieldatendateien.

-  Die Daten können manuell konfiguriert und verwaltet werden.

### <a name="import-data-using-sample-files"></a>Daten mit Beispieldateien importieren

Die Beispieldatendateien sind im Bereitstellungspaket (.zip) verfügbar. Wenn Sie die .zip-Datei extrahieren, sind die Beispieldatendateien unter dem Ordner **SampleData** verfügbar.

Unter dem Ordner **SampleData** sind die Dateien so benannt, dass sie die Reihenfolge angeben, in der die Daten in Ihre Apps importiert werden sollen. Andernfalls schlägt der Datenimport fehl.

-   0_Supplies.xlsx

-   1_Counties.xlsx

-   2_Regional Organization.xlsx

-   3_Parent Organizations.xlsx

-   4_Systems.xlsx

-   5_Regions.xlsx

-   6_Facilities.xlsx

> [!NOTE]
> Wir stellen Name und FIPS-Code für alle Bezirke im Bundesstaat Washington als Beispieldaten zur Verfügung, die Sie importieren können. Sie sollten die Daten **Länder** unter Verwendung der Beispieldatendatei in Ihr System importieren, bevor Sie mit dem Import oder der Verwaltung von Daten in anderen Entitäten fortfahren.
> 
> Um Daten über Bezirke in anderen Staaten zu erhalten, besuchen Sie <https://www.census.gov/geographies/reference-files/2018/demo/popest/2018-fips.html>

#### <a name="how-to-load-data-from-data-files"></a>Wie man Daten aus Datendateien lädt

So laden Sie Beispieldaten aus der Excel-Datei in eine Entität: 

1.  Wählen Sie im linken Navigationsbereich der Admin App eine Entität aus. Wählen Sie beispielsweise **Übergeordnete Org**. 

2.  Wählen Sie **Import aus Excel** zur Auswahl der Datendatei. 

       > [!div class="mx-imgBorder"] 
       > ![Import aus Excel](media/config-import-excel.png "Importieren aus Excel")

3.  Navigieren Sie zum Ordner **SampleData** und wählen Sie die Datei **3_Parent Organizations.xlsx** und fahren Sie mit den Schritten des Assistenten fort, um die Daten zu importieren.  

4.  Nachdem die Beispieldaten importiert wurden, sehen Sie die importierten Datensätze in der Entität:

       > [!div class="mx-imgBorder"] 
       > ![Importierte Datensätze in Entität](media/config-imported-records.png "Importierte Datensätze in Entitäten")

### <a name="manually-configure-and-manage-master-data-for-your-organization"></a>Stammdaten für Ihre Organisation manuell konfigurieren und verwalten

Administratoren können die modellgesteuerte App in [Power Apps](https://make.powerapps.com) verwenden, um die Stammdaten für ihre Organisation zu erstellen und zu verwalten. Diese Daten sind erforderlich, damit die Notfalllösung funktionieren kann.

Zu Beginn müssen Sie Stammdaten in den folgenden Entitäten hinzufügen:

-   [Bedarf](#supplies-and-counties-data)

-   [Verwaltungsbezirke](#supplies-and-counties-data)

-   [Regionale Organisation](#regional-org-data)

-   [Übergeordnete Organisation](#parent-org-data)

-   [Krankenhaussysteme](#systems-data) von jeder Elternorganisation verwaltet

-   [Regionen](#regions-data)) für jedes Krankenhaussystem

-   [Einrichtungen](#facilities-data)) innerhalb jeder Region eines Krankenhaussystems

Melden Sie sich mit der von Ihrem IT-Admin bereitgestellten URL bei der Admin-App an, um Daten hinzuzufügen und zu verwalten.

#### <a name="supplies-and-counties-data"></a>Lieferungen und Daten der Counties

Verwenden Sie die Beispieldatendateien (**0_Supplies.xlsx** und **1_Counties.xlsx**) aus dem bereitgestellten Paket, um Daten für die Entitäten **Vorräte** und **Verwaltungsbezirke** zu importieren.

#### <a name="regional-org-data"></a>Regionale Org-Daten

Dies ist die regionale Netzwerkorganisation, die die Lösung bereitstellt und Daten von verschiedenen übergeordneten Organisationen verwaltet.

So erstellen Sie einen Datensatz:

1.  Wählen Sie **Regional Org** im linken Fensterbereich und wählen Sie **Neu**.

    > [!div class="mx-imgBorder"] 
    > ![Daten zu regionalen Organisationen](media/config-region-org.png "Daten zu regionalen Organisationen")

2.  Geben Sie auf der Seite **Neue regionale Organisation** den Namen der Organisation an:

    > [!div class="mx-imgBorder"] 
    > ![Neue Regionalorganisation](media/config-new-region-org.png "Neue Regionalorganisation")

3.  Wählen Sie **Speichern und schließen** Der neu erstellte Datensatz wird in der Liste **Regional Org** verfügbar sein.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte wie erforderlich und wählen Sie **Speichern und schließen**

#### <a name="parent-org-data"></a>Übergeordnete Org-Daten

Die Entität **Übergordnete Org** speichert die übergeordnete Organisation, die die von der regionalen Organisation eingerichteten Portale zur Ansicht und Verwaltung von Daten in Bezug auf die Krankenhaussysteme der übergeordneten Organisation verwenden wird.

So erstellen Sie einen Datensatz:

1.  Wählen Sie **Übergeordnetes Org** im linken Fensterbereich und wählen Sie **Neu**.

2.  Geben Sie auf der Seite **Neue übergeordnete Organisation** geeignete Werte an:

     > [!div class="mx-imgBorder"] 
     > ![Neue Mutterorganisation](media/config-new-parent-org.png "Neue übergeordnete Organisation")

    | **Feld**                |**Beschreibung** |
    |--------------------------|------------------------------------------------------|
    | Regionale Organisation    | Wählen Sie eine regionale Organisation. Diese Liste wird auf der Grundlage der **Regionalorganisation** Daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Name der übergeordneten Organisation | Geben Sie den Namen der übergeordneten Organisation an.      |
    | Beschreibung              | Geben Sie eine optionale Beschreibung ein.        |
    | Effektives Startdatum     | Geben Sie Startdatum und -zeit für diese übergeordnete Organisation ein.    |
    | Effektives Enddatum       | Geben Sie Enddatum und -zeit für diese übergeordnete Organisation ein.         |

3.  Wählen Sie **Speichern und schließen** Der neu erstellte Datensatz wird in der Liste **Übergeordnete Org** verfügbar sein.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte wie erforderlich und wählen Sie **Speichern und schließen**

#### <a name="systems-data"></a>Systemdaten

Mit der Entität **Systeme** können Sie Einträge für Krankenhaussysteme erstellen und verwalten. Auf diese Weise können Sie mehrere Krankenhaussysteme innerhalb derselben übergeordneten Organisation verwalten.

So erstellen Sie einen Datensatz:

1.  Wählen Sie **Systeme** im linken Fensterbereich und wählen Sie **Neu**.

2.  Geben Sie auf der Seite **Neues System** die entsprechenden Werte an:

    > [!div class="mx-imgBorder"] 
    > ![Systemdaten erstellen](media/config-system-data.png "Systemdaten erstellen")

    | **Feld**           | **Beschreibung**        |
    |---------------------|---------------------------------------|
    | Systemname         | Geben Sie einen Namen für das Krankenhaus ein.    |
    | Übergeordnete Organisation | Wählen Sie eine übergeordnete Organisation, mit der er assoziiert werden soll. Diese Liste wird auf der Grundlage der **Übergeordnete Org** Daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Beschreibung         | Geben Sie eine optionale Beschreibung ein.    |

3.  Wählen Sie **Speichern und schließen** Der neu erstellte Datensatz ist in der Liste **Systeme** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte wie erforderlich und wählen Sie **Speichern und schließen**

#### <a name="regions-data"></a>Regionendaten

Mit der Entität **Regionen** können Sie die geografischen Regionen für Ihre Krankenhaussysteme verwalten.

So erstellen Sie einen Datensatz:

1.  Wählen Sie **Regionen** im linken Fensterbereich und wählen Sie **Neu**.

2.  Geben Sie auf der Seite **Neue Region** die entsprechenden Werte an:

    > [!div class="mx-imgBorder"] 
    > ![Neue Region anlegen](media/config-create-region.png "Neue Region erstellen")

    | **Feld**   | **Beschreibung**                                  |
    |-------------|---------------------------|
    | System      | Wählen Sie ein Krankenhaussystem aus, mit dem diese Region verbunden ist. Diese Liste wird basierend auf den **System**daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Regionenname | Geben Sie den Regionennamen ein. Zum Beispiel Berlin.  |
    | Beschreibung | Geben Sie eine optionale Beschreibung ein. 

3.  Wählen Sie **Speichern und schließen** Der neu erstellte Datensatz ist in der Liste **Regionen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte wie erforderlich und wählen Sie **Speichern und schließen**

### <a name="facilities-data"></a>Einrichtungsdaten

Mit der Entität **Einrichtungen** können Sie die Krankenhausstandorte in jeder Region verwalten. Zum Beispiel die Einrichtungen **Potsdam** und **Oranienburg** innerhalb der Region **Berlin**.

So erstellen Sie einen Datensatz:

1.  Wählen Sie im linken Fensterbereich **Einrichtungen** und wählen Sie dann **Neu.**

2.  Geben Sie auf der Seite **Neue Einrichtung** die entsprechenden Werte an:

    > [!div class="mx-imgBorder"] 
    > ![Neue Einrichtung erstellen](media/config-new-facility.png "Neue Einrichtung erstellen")

    | **Feld**                    | **Beschreibung**            |
    |------------------------------|---------------------------------------------------|
    | Region    | Wählen Sie eine Region aus, der diese Einrichtung zugeordnet ist. Diese Liste wird basierend auf den **Regionen**daten, die Sie zuvor erstellt haben, ausgefüllt.          |
    | Name des Raums | Geben Sie den Einrichtungsnamen ein.                 |
    | DOH-Nummer    | Geben Sie die Nummer des Gesundheitsministeriums für diese Einrichtung ein.     |
    | Folgt Tropfenprotokoll     | Gibt an, ob die Einrichtung die Tröpfchen-Vorsichtsmaßnahmen für Patienten befolgt, von denen bekannt ist oder vermutet wird, dass sie mit Krankheitserregern infiziert sind, die durch Atemtröpfchen übertragen werden, wie z.B. in COVID-19-Fällen. Wählen Sie **Ja** oder **Nein**. |
    | Beschreibung    | Geben Sie eine optionale Beschreibung ein.              |
    | Effektives Startdatum         | Geben Sie Startdatum und -uhrzeit für diese Einrichtung ein.    |
    | Lizenzierte Bettenkapazität    | Geben Sie die gesamte lizenzierte Bettenkapazität an.    |
    | Akutversorgungskapazität (Luftübertragungsisolation)     | Geben Sie die Gesamtzahl der Akutpflegebetten im AIIR (Isolationsraum für luftübertragene Infektionen) ein.     |
    | ICU-Kapazität (Luftübertragungsisolation)            | Geben Sie die Gesamtzahl der Betten auf der Intensivstation in AIIR ein.       |
    | Beatmungsgeräte insgesamt       | Geben Sie die Anzahl der gesamten Beatmungsplätze in der Einrichtung ein.   |
    | Effektives Enddatum           | Geben Sie Enddatum und -uhrzeit für diese Einrichtung ein.       |
    | Bettenkapazität für plötzlichen Anstieg           | Geben Sie die Anzahl der Notfallbetten ein, über die die Einrichtung verfügen kann. Schwallbetten sind solche, die über die lizenzierte Bettenkapazität hinaus besetzt werden können, wenn Patienten aufgenommen werden müssen.                                              |
    | Akutversorgungskapazität (nicht Luftübertragungsisolation) | Geben Sie die Gesamtzahl der Akutpflegebetten in nicht AIIR (Isolationsraum für luftübertragene Infektionen) ein.|
    | ICU-Kapazität (nicht Luftübertragungsisolation)        | Geben Sie die Gesamtzahl der Betten auf der Intensivstation in Nicht-AIIR-Räumen ein.              |
    |Gesamtkapazität der Leichenhalle       | Geben Sie die Gesamtkapazität der Leichenhalle für die Einrichtung an.|
    | Einrichtungsadresse    | Geben Sie Straße, Stadt, Landkreis, Bundesland, Postleitzahl, Breitengrad und Längengrad für die Einrichtung ein.   |

3.  Wählen Sie **Speichern und schließen** Der neu erstellte Datensatz ist in der Liste **Einrichtungen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte wie erforderlich und wählen Sie **Speichern und schließen**

Sie können auch die verknüpften Daten **Zählung**, **COVID**, **Ausrüstung**, **Belegschaft** und **Lieferungen** anzeigen und verwalten, die von den übergeordneten Organisationen für eine Einrichtung eingegeben wurden, indem Sie einen Einrichtungsdatensatz öffnen und die entsprechenden Registerkarten im Datensatz verwenden.

> [!div class="mx-imgBorder"] 
> ![Öffnen eines Anlagendatensatzes](media/config-facility-record.png "Öffnen eines Einrichtungsdatensatzes")

## <a name="manage-portal-users"></a>Portal-Benutzer verwalten

Verwenden Sie die Entität **Portalbenutzer**, um Portalbenutzer hinzuzufügen und zu verwalten. Bei diesen Portalbenutzern handelt es sich um die Admins der verschiedenen übergeordneten Organisationen, die die Daten ihrer Krankenhaussysteme an regionale Organisationen melden und auch andere Admins, Mitarbeiter im Gesundheitswesen oder Berichtsbetrachter über die Portale verwalten.

### <a name="create-a-portal-user"></a>Erstellen Sie einen Portalbenutzer

1.  Melden Sie sich mit der von Ihrem IT-Admin bereitgestellten URL bei der Admin-App an.

2.  Wählen Sie im linken Fensterbereich **Portalbenutzer**. Sie sehen eine Liste der Portalbenutzer, falls diese bereits von anderen Admins in Ihrer Organisation hinzugefügt wurden. Wenn Sie einen Benutzer auswählen, werden die Details zu diesem Benutzer geöffnet.

3.  Wählen Sie **Neu**, um einen neuen Portalbenutzer zu erstellen. Geben Sie auf der Seite **Neuer Kontakt** die entsprechenden Werte an

    > [!div class="mx-imgBorder"] 
    > ![Portalbenutzer anlegen](media/config-portal-user.png "Erstellen Sie einen Portalbenutzer")

    | **Feld**           | **Beschreibung**  |
    |---------------------|-------------------|
    | Vorname          | Vorname des Benutzers.                           |
    | Nachname           | Nachname des Benutzers  |
    | Per E-Mail senden     | E-Mail des Benutzers, an den die Einladung geschickt wird.    |
    | Übergeordnete Organisation | Wählen Sie eine übergeordnete Organisation, mit der dieser Portalbenutzer assoziiert werden soll. Dadurch wird sichergestellt, dass der Benutzer nur Zugriff auf die Daten des Krankenhaus-Systems unter der ausgewählten übergeordneten Organisation hat. Wenn Sie keine übergeordnete Organisation für den Benutzer angeben, hat er/sie Zugriff auf die Daten aller übergeordneten Organsysteme unter der regionalen Organisation. |
    | Krankenhaussystem     | Wählen Sie ein Krankenhaus, mit dem dieser Portalbenutzer verbunden sein wird. |
    | Region  | Wählen Sie eine Region, mit der der Portalbenutzer assoziiert werden soll.  |
    | Raum            | Wählen Sie eine Einrichtung, mit der dieser Portalbenutzer verbunden wird. |

4.  Speichern Sie den Datensatz. Beim Speichern des Datensatzes wird der Bereich **Webrollen** verfügbar. Wählen Sie **Bestehende Web-Rolle hinzufügen**

5.  Drücken Sie auf der Seite Datensätze suchen die Eingabetaste, um die vorhandenen Web-Rollen anzuzeigen.

    > [!div class="mx-imgBorder"] 
    > ![Wählen Sie eine Rolle](media/config-select-portal-role.png "Wählen Sie eine Rolle")

6. Wählen Sie Rollen entsprechend dem Portalzugang, den Sie dem Benutzer zur Verfügung stellen müssen. Um Zugriff auf alle Funktionen im Portal zu gewähren, wählen Sie alle drei Rollen aus: **Organisation HealthCare Worker**, **Administrator der übergeordneten Organisation** und **Berichtsbetrachter**.

    Informationen über den Portalzugang, den jede dieser Rollen bietet, finden Sie im Abschnitt [Benutzer erstellen](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#create-user) im Thema Portalverwaltung.

    Um eine Rolle zu vergeben, wählen Sie die Rolle aus und wählen Sie **Hinzufügen**.

7. Speichern Sie den Portalbenutzer-Datensatz.

Je nachdem, welche Rolle(n) Sie dem Benutzer zugewiesen haben, wird er die entsprechenden Bereiche im Portal anzeigen. Weitere Informationen: [Portal für Admins und Berichtsbetrachter](portals-admin-reporting.md) und [Portal für Mitarbeiter im Gesundheitswesen](portals-user.md)

Eine E-Mail mit einem Einladungscode zur Teilnahme an Portalen wird automatisch an den neu erstellten Benutzer gesendet. Der Portalbenutzer kann die Einladung einlösen, sich anzumelden und mit der Nutzung des Portals zu beginnen. Weitere Informationen: [Mit dem Portal beginnen](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#getting-started-with-the-portal)

## <a name="manage-portal-user-requests"></a>Verwalten von Portal-Benutzeranfragen

Sie können Portal-Benutzeranfragen mit der Option **Benutzeranfragen** anzeigen, genehmigen und ablehnen.

Verwenden Sie die entsprechende Ansicht, um eine Liste der genehmigten, abgelehnten, inaktiven und ausstehenden Benutzeranfragen anzuzeigen.

> [!div class="mx-imgBorder"] 
> ![Dient zum Auswählen einer Ansicht.](media/configure-portal-request-views.png "Dient zum Auswählen einer Ansicht.")

### <a name="approve-or-decline-user-request"></a>Benutzeranfrage genehmigen oder ablehnen

Um Benutzeranfragen zu genehmigen oder abzulehnen:

1.  Melden Sie sich mit der von Ihrem IT-Admin bereitgestellten URL bei der Admin-App an.

2.  Wählen Sie im linken Fensterbereich **Benutzeranfragen** und wählen Sie dann **Ausstehende Portalbenutzeranfragen**Ansicht. Sie sehen eine Liste von Portalbenutzeranfragen, die zur Genehmigung anstehen.

3.  Doppelklicken Sie auf eine Benutzeranfrage, um sie zu öffnen.

4.  Auf dem Antragsformular für Benutzer:

    1. Wählen Sie die entsprechenden Rollen für den Benutzer im Bereich **Rollen für den Benutzer wählen**. Um eine Rolle zu gewähren oder abzulehnen, wählen Sie **Ja** bzw. **Nein** für jede Rolle.

    1. Wählen Sie aus der Liste **Anforderungsstatus**, wählen Sie **Genehmigen** oder **Ablehnen**.

    1. Wählen Sie das Speichersymbol in der unteren rechten Ecke.

        > [!div class="mx-imgBorder"] 
        > ![Genehmigung oder Ablehnung einer Benutzeranfrage](media/user-request-manage.png "Genehmigen oder Ablehnen einer Benutzeranfrage")

Auf der Grundlage der Zustimmung oder Ablehnung geschieht Folgendes:

- Wenn Sie *Genehmigen* die Zugriffsanfrage, wird der Benutzerdatensatz mit ausgewählten Rollen erstellt und der Benutzer erhält eine E-Mail mit Einladungscode. Der Benutzer kann den Einladungscode einlösen, um sich beim Portal anzumelden. Weitere Informationen: [Einladung zurücknehmen](portals-admin-reporting.md#redeem-invitation)

- Wenn Sie *Ablehnen* die Zugriffsanfrage ablehnen, wird der Benutzerdatensatz nicht erstellt, und der Benutzer erhält eine E-Mail mit der Mitteilung, dass die Anfrage abgelehnt wird.

## <a name="view-the-power-bi-dashboard"></a>Anzeigen des Power BI-Dashboards

Business-Admins in der regionalen Organisation können das Dashboard Power BI in ihrem Power BI-Mandanten anzeigen, wenn der regionale IT-Admin den Bericht als App veröffentlicht und Business-Admins Zugang gewährt hat. Weitere Informationen: [Schritt 5: Konfigurieren und Publizieren von Power BI Dashboard](deploy.md#step-5-configure-and-publish-power-bi-dashboard) 

Um das Power BI Dashboard anzuzeigen:

1. Melden Sie sich bei [Power BI](https://app.powerbi.com) an.

2. Der Arbeitsbereich, in dem die App veröffentlicht wurde, steht Ihnen für den Zugriff auf das Dashboard zur Verfügung.

3. Das Power BI-Dashboard, das Ihnen in Ihrem Power BI-Mandanten zur Verfügung steht, ist das gleiche wie das, das den Benutzern des Portals zur Verfügung steht. Der **Primärunterschied** besteht darin, dass Sie als Business Admin einer regionalen Organisation Daten für alle übergeordneten Organisationen anzeigen können, die Daten an die regionale Organisation berichten, während Benutzer, die das in das Portal eingebettete Dashboard anzeigen, nur Daten für ihre übergeordnete Organisation und die zugehörigen Krankenhaussysteme anzeigen können.

Ausführliche Informationen über das Dashboard in Power BI finden Sie unter [Einblicke gewinnen](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights) im Portalthema.

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Lösung Regional Government Emergency Response and Monitoring zu melden, besuchen Sie <https://aka.ms/rer-issues>.

- Rückmeldungen über die Lösung Regional Government Emergency Response and Monitoring finden Sie unter <https://aka.ms/rer-feedback>.

