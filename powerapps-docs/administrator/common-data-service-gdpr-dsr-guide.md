---
title: DSR-Leitfaden zu von Kunden erstellten Daten | Microsoft-Dokumentation
description: DSR-Leitfaden zu von Kunden erstellten Daten in PowerApps
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: paulliew
ms.openlocfilehash: cff822e24f1384833caa0baa945a7d3d07a8ee9b
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-customer-data-in-common-data-service-for-apps"></a>Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps

## <a name="introduction-to-dsr-requests"></a>Einführung in DSR-Anforderungen
Im Rahmen unserer Verpflichtung, unsere Kunden im Umgang mit der DSGVO (Datenschutz-Grundverordnung) stets zu begleiten, wurden diese Informationen entwickelt, um Sie bestmöglich vorzubereiten und zu unterstützen. Diese Dokumentation beschreibt nicht nur unsere Bemühungen um eine bestmögliche Vorbereitung auf die Datenschutz-Grundverordnung, sondern soll auch Beispiele liefern, was Sie bereits heute unternehmen können, um den Bestimmungen der Datenschutz-Grundverordnung (DSGVO) mithilfe von PowerApps, Microsoft Flow und Common Data Service für Apps nachzukommen.

Die DSGVO erteilt Personen (in der Verordnung als betroffene Personen bezeichnet) das Recht, vom Arbeitgeber oder einer anderen Einrichtung oder Organisation (auch als Verantwortliche bezeichnet) erhobene personenbezogene Daten zu verwalten. Personenbezogene Daten sind in der DSGVO sehr umfassend definiert als alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person beziehen. Die DSGVO gewährt betroffenen Personen bestimmte Rechte bezüglich ihrer personenbezogenen Daten, darunter das Recht auf Erhalt einer Kopie der personenbezogenen Daten, das Recht auf Berichtigung, das Recht auf Einschränkung der Verarbeitung, das Recht auf Löschung sowie das Recht auf Erhalt der Daten in einem maschinenlesbaren Format, um sie an einen anderen Verantwortlichen übermitteln zu können. Eine betroffene Person kann bei einem Verantwortlichen mit einem formellen Antrag die Einschränkung der Verarbeitung von personenbezogenen Daten verlangen. Dieser Antrag wird auch DSR-Anforderung (Data Subject Rights, Rechte betroffener Personen) genannt.

In diesem Leitfaden wird erklärt, wie Sie als Verantwortlicher im Zuge von DSR-Anforderungen Produkte, Dienste und Verwaltungstools von Microsoft nutzen können, um personenbezogene Daten zu suchen und zu verarbeiten. Dies gilt insbesondere für die Suche nach, den Zugriff auf sowie das Ergreifen von Maßnahmen bezüglich personenbezogener Daten, die sich in Microsoft Cloud befinden. Die folgende Auflistung gibt einen Überblick über die in diesem Leitfaden beschriebenen Prozesse:

1. **Ermitteln**: Verwenden Sie Such- und Ermittlungstools, um schneller Kundendaten zu finden, die Gegenstand einer DSR-Anforderung sein könnten. Sobald Sie möglicherweise relevante Dokumente ermittelt haben, können Sie eine oder mehrere der in den folgenden Schritten beschriebenen Aktionen ausführen, um auf eine DSR-Anforderung zu reagieren. Oder Sie entscheiden, dass die Anforderung nicht den Richtlinien Ihrer Organisation bezüglich DSR-Anforderungen entspricht.

2. **Zugreifen**: Rufen Sie personenbezogene Daten aus Microsoft Cloud ab, und fertigen Sie gegebenenfalls eine Kopie an, die Sie der betroffenen Person zur Verfügung stellen können.

3. **Berichtigen**: Nehmen Sie Änderungen vor oder implementieren Sie ggf. andere angeforderte Aktionen für die personenbezogenen Daten.

4. **Einschränken**: Schränken Sie die Verarbeitung von personenbezogenen Daten ein, indem Sie entweder die Lizenzen für verschiedene Onlinedienste entfernen oder die gewünschten Dienste, wenn möglich, deaktivieren. Sie können Daten auch aus Microsoft Cloud entfernen und sie lokal oder an einem anderem Speicherort beibehalten.

5. **Löschen**: Löschen Sie personenbezogene Daten dauerhaft aus Microsoft Cloud.

6. **Exportieren**: Stellen Sie der betroffenen Person eine elektronische Kopie ihrer personenbezogenen Daten (in einem maschinenlesbaren Format) zur Verfügung.

Jeder Abschnitt dieses Leitfadens beschreibt jeweils die technischen Prozeduren, die Ihre Organisation als Verantwortlicher ergreifen kann, um auf eine DSR-Anforderung bezüglich personenbezogener Daten in Microsoft Cloud zu reagieren.

## <a name="common-data-service-customer-data"></a>Kundendaten in Common Data Service

> [!IMPORTANT]
> Gilt für Common Data Service für Apps und für Common Data Service (Vorgängerversion)

Es gibt zwei Arten von Common Data Services (CDS): CDS für Apps und die CDS-Vorgängerversion, die jeweils einen anderen Prozess für personenbezogene Daten aufweisen.

Sie können die Art der CDS-Umgebung ermitteln, indem Sie auf der [PowerApps-Website](https://web.powerapps.com) die folgenden Schritte ausführen:

1.  Wählen Sie aus der Dropdownliste „Umgebung“ die **Umgebung** aus.
2.  Navigieren Sie zu **Daten** > **Entitäten**.

    Bei Ihrer Umgebung handelt es sich um eine CDS für Apps-Umgebung, wenn folgende Entitäten angezeigt werden:

    ![Liste der PowerApps-Entitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-entities-list.png)

    Bei Ihrer Umgebung handelt es sich um eine CDS-Vorgängerversion, wenn folgende Entitäten angezeigt werden:

    ![Liste der PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-list.png)

Nachdem Sie festgestellt haben, über welche Art von CDS-Umgebung Sie verfügen, können Sie anhand der entsprechenden Abschnitte in diesem Dokument die personenbezogenen Daten ermitteln.

> [!NOTE]
> Möglicherweise verfügen Sie über einige Umgebungen in CDS für Apps und weitere in CDS (Vorgängerversion). Daher müssen Sie die nachfolgend beschriebenen Prozesse für sämtliche Umgebungen in Ihrer Organisation wiederholen.

## <a name="user-personal-data-in-common-data-service-for-apps"></a>Personenbezogene Benutzerdaten in Common Data Service für Apps

### <a name="prerequisites"></a>Voraussetzungen
Ein Benutzer muss über das Office 365 Admin Center erstellt werden. Ihm muss eine entsprechende Common Data Service-Benutzerlizenz für den Zugriff auf CDS zugewiesen werden.  Bevor der Benutzer mit der Verwendung von Common Data Service beginnen kann, ist zudem eine Sicherheitsrolle erforderlich.

Die personenbezogenen Benutzerdaten werden im Office 365 Admin Center und in der CDS-Systembenutzerentität aufbewahrt.  Bestimmte standardmäßige personenbezogene Benutzerdaten werden In Office 365 Admin Center aufbewahrt und verwaltet (z.B. Benutzername, Benutzer-ID, Telefonnummer, E-Mail-Adresse und Anschrift). Diese personenbezogenen Benutzerdaten werden in allen Umgebungen mit der CDS-Systembenutzerentität synchronisiert.  Ein Systemadministrator kann diese personenbezogenen Daten nur im Office 365 Admin Center aktualisieren. Diese Attribute werden anschließend automatisch mit CDS für Apps synchronisiert. Ein Systemadministrator kann benutzerdefinierte Attribute auch erstellen, um zusätzliche personenbezogenen Benutzerdaten in der CDS-Systembenutzerentität zu erfassen.  Diese benutzerdefinierten Attribute werden in CDS vom Systemadministrator manuell verwaltet.

Wenn ein Benutzer aus dem Office 365 Admin Center gelöscht wird, wird der Benutzerdatensatz nicht automatisch von der CDS-Systembenutzerentität entfernt, um eine Unterbrechung der Geschäftsanwendungen zu verhindern, die möglicherweise entscheidend für die Vorgänge Ihrer Organisation sind.  Ein CDS-Systemadministrator muss Maßnahmen ergreifen, um mit der Anwendung die personenbezogenen Benutzerdaten zu suchen und aus CDS zu entfernen.

Nur Benutzer mit der globalen Office 365-Administratorrolle und der Sicherheitsrolle eines CDS-Systemadministrators können die nachfolgend aufgeführten Aktionen „Ermitteln“, „Berichtigen“, „Exportieren“ und „Löschen“ durchführen.

### <a name="discover"></a>Erkunden

Systemadministratoren können mehrere CDS-Instanzen erstellen.  Diese Instanzen können zu Test-, Entwicklungs- oder Produktionszwecken verwendet werden.   Jede dieser Instanzen verfügt über eine Kopie der Systembenutzerentität mit sämtlichen benutzerdefinierten Attributen, die vom Systemadministrator hinzugefügt wurden, sowie mit den personenbezogenen Daten, die über das Office 365 Admin Center synchronisiert wurden.

Ein Systemadministrator kann eine Liste mit allen CDS-Instanzen suchen, indem er über das PowerApps Admin Center zum Dynamics 365 Administration Center navigiert.

Über das [PowerApps Admin Center](https://admin.powerapps.com/):

1.  Navigieren Sie zur Registerkarte „Umgebungen“.
2.  Wählen Sie aus der Liste der Umgebungen eine Umgebung aus.
3.  Klicken Sie auf den Link „Dynamics 365 Admin Center“.

    ![PowerApp-Umgebungsdetails](./media/common-data-service-gdpr-dsr-guide/powerapps-environment-details.png)

    Es wird eine Liste mit allen Instanzen angezeigt.

    ![PowerApps-Instanzauswahl](./media/common-data-service-gdpr-dsr-guide/powerapps-instance-picker.png)

Personenbezogene Daten von CDS-Benutzern können wie folgt gefunden werden:

|Ressourcen mit personenbezogenen Daten | Zweck | Websitezugriff | Programmatischer Zugriff
| --- | --- | --- | ---
| Entitätsdatensatz | Systembenutzerentität | [PowerApps Admin Center](https://admin.powerapps.com) | [Über die Web-API](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)
| Verlauf überprüfen | Lässt zu, dass Kunden Ressourcen ermitteln, die von Benutzern auf einer Entitätsstufe erstellt, geändert oder gelöscht wurden, oder auf die Benutzer zugegriffen haben. | [PowerApps Admin Center](https://admin.powerapps.com) | [Über die Web-API](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)

#### <a name="user"></a>User
Personenbezogene Benutzerdaten werden in Office 365 Admin Center in Azure Active Directory gespeichert.  Diese personenbezogenen Daten werden im Office 365 Admin Center verwaltet und automatisch mit allen CDS-Umgebungen synchronisiert.  Ein Systemadministrator kann diese personenbezogenen Daten nicht direkt in CDS aktualisieren, während der Benutzer aktiv ist. Sie müssen direkt im Office 365 Admin Center aktualisiert werden.  Zusätzliche personenbezogenen Daten (z.B. benutzerdefinierte Attribute) können direkt zu CDS hinzugefügt werden und müssen vom Systemadministrator manuell verwaltet werden.

Ein CDS-Systemadministrator kann den Benutzer und die personenbezogenen Daten suchen, die einem bestimmten Benutzer zugeordnet sind, indem er die folgenden Schritte ausführt:

Über das [PowerApps Admin Center](https://admin.powerapps.com/):

1.  Navigieren Sie zur Registerkarte „Umgebungen“.
2.  Wählen Sie aus der Liste der Umgebungen eine Umgebung aus.
3.  Klicken Sie auf den Link „Dynamics 365 Admin Center“.
4.  Klicken Sie auf den Namen der neuen Umgebung.
5.  Klicken Sie auf die Schaltfläche **Öffnen**.
6.  Navigieren Sie zu **Einstellungen** > **Sicherheit**.
7.  Klicken Sie auf **Benutzer**.
8.  Geben Sie den Benutzer in das Eingabefeld **Suche** ein.
9.  Klicken Sie auf die Schaltfläche **Suche**.
10. Doppelklicken Sie auf den Benutzer.

    ![PowerApps-Benutzerformular](./media/common-data-service-gdpr-dsr-guide/powerapps-user-form.png)

#### <a name="audit-history"></a>Verlauf überprüfen
Wenn die [Überwachungsnachverfolgung](https://docs.microsoft.com/dynamics365/customer-engagement/admin/audit-data-user-activity) für eine Entität in Common Data Service aktiviert ist, werden die personenbezogenen Benutzerdaten zusammen mit den Ereignissen, die der Benutzer ausgeführt hat, im Überwachungsverlauf protokolliert.

### <a name="rectify"></a>Berichtigen

Bei der Anfrage einer betroffenen Personen bezüglich einer Berichtigung der von Ihrer Organisation gespeicherten personenbezogenen Daten müssen Sie entscheiden, ob die Anforderung umgesetzt werden soll oder nicht.  Das Berichtigen von Daten kann Aktionen wie die Bearbeitung, Zensur oder Entfernung von personenbezogenen Daten aus einem Dokument oder einem anderen Element beinhalten.

Sie können mit Azure Active Directory Identitäten (personenbezogene Daten) Ihrer Benutzer in Common Data Service für Apps verwalten. Unternehmenskunden können DSR-Berichtigungsanforderungen verwalten, einschließlich eingeschränkter Bearbeitungsfeatures je nach Art des angegebenen Microsoft-Diensts.  Als verarbeitende Instanz für die Daten bietet Microsoft keine Möglichkeit, vom System generierte Protokolle zu korrigieren, da diese auf Fakten basierende Aktivitäten und einen historischen Datensatz von Ereignissen innerhalb der Microsoft-Dienste darstellen. Weitere Einzelheiten finden Sie unter [DSGVO: Datensubjektanforderungen (DSR-Anforderungen)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

Nachdem der Benutzerdatensatz aus Azure Active Directory gelöscht wurde, können Systemadministratoren die verbleibenden personenbezogenen Benutzerdaten (z.B. benutzerdefinierte Attribute, die sie hinzugefügt haben) aus allen Instanzen entfernen.  

### <a name="export"></a>Exportieren

#### <a name="system-user"></a>Systembenutzer
In der Systembenutzerentität gespeicherte personenbezogene Daten von Benutzern können über die Benutzerliste im Portal in Excel exportiert werden.

Über das [PowerApps Admin Center](https://admin.powerapps.com/):

1.  Navigieren Sie zur Registerkarte „Umgebungen“.
2.  Wählen Sie aus der Liste der Umgebungen eine Umgebung aus.
3.  Klicken Sie auf den Link „Dynamics 365 Admin Center“.
4.  Klicken Sie auf den Namen der neuen Umgebung.
5.  Klicken Sie auf die Schaltfläche „Öffnen“. Navigieren Sie zu „Einstellungen“ > „Sicherheit“.
6.  Wählen Sie die Ansicht „Aktivierte Benutzer“ aus.
7.  Klicken Sie auf die Schalfläche „In Excel exportieren“.

#### <a name="audit-history"></a>Verlauf überprüfen
Mit der Anwendung können Screenshots von dem Überwachungsverlauf erstellt und kopiert werden, indem die nachfolgend beschriebenen Schritte ausgeführt werden.
Über das [PowerApps Admin Center](https://admin.powerapps.com/):
1.  Navigieren Sie zur Registerkarte „Umgebungen“.
2.  Wählen Sie aus der Liste der Umgebungen eine Umgebung aus.
3.  Klicken Sie auf den Link „Dynamics 365 Admin Center“.
4.  Klicken Sie auf den Namen der neuen Umgebung.
5.  Klicken Sie auf die Schaltfläche „Öffnen“.
6.  Navigieren Sie zu „Einstellungen“ > „Überwachung“.

    ![PowerApps-Menü „Überwachungsverlauf“](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-menu.png)

7.  Klicken Sie auf „Zusammenfassungsansicht: Überwachung“.
8.  Suchen Sie den Überwachungsdatensatz des Benutzers.

    ![PowerApps-Menü „Verlaufsdetails“](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-details.png)

9.  Drücken Sie zum Erstellen des Screenshots die Tasten Alt + Druck.
10. Speichern Sie den Screenshot in einer Datei.
11. Sie können die Datei anschließend an Ihren DSR-Anforderer senden.

### <a name="delete"></a>Löschen

#### <a name="user"></a>User
Wenn ein Benutzer aus dem Office 365 Admin Center gelöscht wird, wird der Status des Benutzers in CDS auf „Deaktiviert“ festgelegt; die personenbezogenen Benutzerdaten werden jedoch nicht automatisch gelöscht, um eine Unterbrechung der Geschäftsanwendungen zu verhindern, die möglicherweise entscheidend für die Vorgänge Ihrer Organisation sind.
Zum Löschen der personenbezogenen Benutzerdaten aus CDS muss der Systemadministrator die personenbezogenen Daten des deaktivierten Benutzers manuell entfernen.

#### <a name="remove-user-personal-data-via-user-form"></a>Entfernen der personenbezogenen Benutzerdaten über das Benutzerformular
Wenn der Benutzerdatensatz aus Azure Active Directory gelöscht wird, wird im Benutzerformular folgende Meldung angezeigt.
Die Informationen zu diesem Benutzer werden nicht mehr von Office 365 verwaltet. Sie können diesen Datensatz aktualisieren, um auf DSR-Anforderungen zu reagieren, indem Sie sämtliche personenbezogene Daten entfernen oder ersetzen, die mit diesem Benutzer verknüpft sind.

Über das [PowerApps Admin Center](https://admin.powerapps.com/):
1.  Navigieren Sie zur Registerkarte „Umgebungen“.
2.  Wählen Sie aus der Liste der Umgebungen eine Umgebung aus.
3.  Klicken Sie auf den Link „Dynamics 365 Admin Center“.
4.  Klicken Sie auf den Namen der neuen Umgebung.
5.  Klicken Sie auf die Schaltfläche **Öffnen**.
6.  Klicken Sie auf **Einstellungen** > **Sicherheit** > **Benutzer**.
7.  Wählen Sie die Ansicht **Deaktivierte Benutzer** aus.
8.  Geben Sie unter **Nach Datensätzen suchen** einen Benutzernamen ein, und klicken Sie auf die Schaltfläche **Suche**.
9.  Doppelklicken Sie in den Suchergebnissen auf den Benutzernamen.
10. Entfernen Sie sämtliche personenbezogene Daten, und klicken Sie auf **Speichern**.

#### <a name="remove-user-personal-data-via-excel-importexport"></a>Entfernen der personenbezogenen Benutzerdaten über einen Excel-Import/-Export
1.  Klicken Sie auf **Einstellungen** > **Sicherheit** > **Benutzer**.
2.  Wählen Sie die Ansicht **Deaktivierte Benutzer** aus.
3.  Erstellen Sie eine Excel-Vorlage, die alle Spalten mit personenbezogenen Benutzerdaten enthält, die Sie aktualisieren möchten.
4.  Klicken Sie auf **Datei herunterladen**.
5.  Öffnen Sie die heruntergeladene Excel-Datei, und aktualisieren und speichern Sie die Datei.
6.  Kehren Sie zum Ansichtsfenster „Deaktivierte Benutzer“ zurück, und klicken Sie auf „Daten importieren“.
7.  Wählen Sie im Dialogfeld „Datendatei hochladen“ Ihre aktualisierte Excel-Datei aus.
8.  Nehmen Sie im Fenster „Felder zuordnen“ alle notwendigen Änderungen vor.
9.  Klicken Sie auf „Weiter“ und auf „Senden“.

Weitere Informationen zur Verwendung von Excel-Vorlagen finden Sie unter [Zusätzliche Informationen zu Excel](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/analyze-your-data-with-excel-templates).


#### <a name="remove-audit-history-via-the-audit-summary-view-form"></a>Entfernen eines Überwachungsverlaufs über das Formular „Zusammenfassungsansicht“

Über das [PowerApps Admin Center](https://admin.powerapps.com/):
1.  Navigieren Sie zur Registerkarte „Umgebungen“.
2.  Wählen Sie aus der Liste der Umgebungen eine Umgebung aus.
3.  Klicken Sie auf den Link „Dynamics 365 Admin Center“.
4.  Klicken Sie auf den Namen der neuen Umgebung.
5.  Klicken Sie auf die Schaltfläche „Öffnen“.
6.  Klicken Sie auf „Einstellungen“ > „Überwachung“.
7.  Wählen Sie „Zusammenfassungsansicht: Überwachung“ aus.
8.  Änderungsverlauf des Benutzers suchen
9.  Klicken Sie auf das Kontrollkästchen in der Zeile bzw. in den Zeilen.
10. Klicken Sie auf das Symbol „Änderungsverlauf löschen“.

## <a name="personal-data-stored-in-common-data-service-for-apps-databases"></a>In Datenbanken des Common Data Service für Apps gespeicherte personenbezogene Daten

### <a name="prerequisites"></a>Voraussetzungen
Sie können personenbezogene Daten von Einzelpersonen (z.B. Ihren eigenen Kunden) in den Inhalten Ihrer CDS-Entitäten speichern.  

Wenn eine Einzelperson eine DSR-Anforderung an Ihre Organisation sendet, muss der CDS-Systemadministrator sämtliche Entitäten suchen, in denen innerhalb Ihrer Anwendung auf diese Person verwiesen werden könnte.  Der CDS-Administrator ist verantwortlich für die Verwaltung eines Inventars der Speicherorte der personenbezogenen Daten in den verschiedenen von Ihnen verwendeten Entitäten, damit Sie auf DSR-Anforderungen von Einzelpersonen reagieren können.

Anschließend können personenbezogene Daten in einer Entität innerhalb Ihrer Inhalte mit der produktinternen Funktion exportiert, berichtigt oder gelöscht werden.  

### <a name="discover"></a>Erkunden
Wenn ein CDS-Administrator eine DSR-Anforderung von einer Einzelperson empfängt, muss der Administrator ermitteln, welche Umgebungen/CDS-Instanzen personenbezogene Daten dieser Einzelperson enthalten.  Sie sollten Richtlinien und Prozeduren für die Verwaltung eines Inventars der Umgebungen, Instanzen und Entitäten entwickeln, in dem personenbezogene Daten von Einzelpersonen gespeichert werden. Mithilfe dieses Inventars können Sie personenbezogene Daten ermitteln, die Sie innerhalb Ihrer Inhalte gespeichert haben.

Mit dem Inventar der Umgebungen, Instanzen, Entitäten und Felder, in dem personenbezogene Daten gespeichert sind, können Sie die CDS-Suchengine für die Ermittlung der personenbezogenen Daten konfigurieren.  Ein CDS-Administrator kann die Suchentitäten und Felder konfigurieren. Weitere Einzelheiten hierzu finden Sie unter [Konfigurieren der Relevanzsuche](https://go.microsoft.com/fwlink/?linkid=872506).
Anschließend kann der CDS-Administrator auf die CDS-Umgebung zugreifen und eine Suche ausführen.

1.  Klicken Sie auf das Symbol **Suche**.
2.  Wählen Sie **Relevanzsuche** aus.

    ![PowerApps-Menü „Relevanzsuche“](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3.  Geben Sie die personenbezogenen Daten der Einzelperson in das Suchfeld ein.
4.  Klicken Sie auf das Symbol „Suche“.

    ![Ergebnisse der PowerApps-Relevanzsuche](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

Personenbezogene Daten in Ihren Inhalten werden normalerweise in zentralen Entitäten gespeichert (z.B. „Konto“, „Kontakt“, „Lead“, „Verkaufschance“). Sie tragen jedoch die Verantwortung dafür, dass ein Inventar gepflegt wird, das die Speicherorte der personenbezogenen Daten von Einzelpersonen enthält.

### <a name="rectify"></a>Berichtigen
Der CDS-Systemadministrator kann die persönlichen Daten einer Einzelperson mithilfe der Liste der Ergebnisse von der Relevanzsuche aktualisieren.  Allerdings haben Sie die personenbezogenen Daten dieser Einzelperson möglicherweise auch in anderen benutzerdefinierten Entitäten gespeichert.  Der CDS-Systemadministrator trägt die Verantwortung dafür, dass ein Inventar gepflegt wird, das diese anderen benutzerdefinierten Entitäten enthält, und dass die personenbezogenen Daten der Einzelperson entsprechend aktualisiert werden.

Über die Ergebnisse der Relevanzsuche:

1.  Klicken sie auf ein Element, in dem die personenbezogenen Daten der Einzelperson gefunden wurden.
2.  Aktualisieren Sie ggf. die personenbezogenen Daten der Einzelperson.
3.  Klicken Sie auf „Speichern“.

    ![PowerApps-Kontodetails](./media/common-data-service-gdpr-dsr-guide/powerapps-account-details.png)

### <a name="export"></a>Exportieren
Es kann ein Screenshot der Daten erfasst und für Ihren DSR-Anforderer freigegeben werden, indem die nachfolgend beschriebenen Schritte ausgeführt werden.

Über das [PowerApps Admin Center](https://admin.powerapps.com/):
1.  Navigieren Sie zur Registerkarte „Umgebungen“.
2.  Wählen Sie aus der Liste der Umgebungen eine Umgebung aus.
3.  Klicken Sie auf den Link „Dynamics 365 Admin Center“.
4.  Klicken Sie auf den Namen der neuen Umgebung.
5.  Klicken Sie auf das Symbol **Suche**.
6.  Wählen Sie „Relevanzsuche“ aus.
7.  Geben Sie die personenbezogenen Daten der Einzelperson in das Suchfeld ein.
8.  Klicken Sie auf das Symbol „Suche“.
9.  Suchen Sie das Element, und doppelklicken Sie darauf.
10. Drücken Sie auf <alt> <PrtScn>, um den Screenshot zu erstellen.
11. Speichern Sie den Screenshot in einer Datei.
12. Sie können die Datei anschließend an Ihren DSR-Anforderer senden.

### <a name="delete"></a>Löschen

Der CDS-Administrator kann die personenbezogenen Daten einer Einzelperson aus den Datensätzen löschen, in denen die Daten gespeichert wurden.  Der CDS-Administrator hat folgende Möglichkeiten: (1) Er kann den Datensatz löschen, in dem die personenbezogenen Daten gespeichert wurden, oder (2) die Inhalte der personenbezogenen Daten aus dem Datensatz entfernen.  

> [!NOTE]
> Ein CDS-Administrator kann die Umgebung anpassen, um zu verhindern, dass ein Datensatz aus einer Entität gelöscht wird. Bei einer Konfiguration dieser Art müssen Sie die Inhalte der personenbezogenen Daten aus dem Datensatz löschen, statt den Datensatz selbst zu löschen.

Bei den Ergebnissen der Relevanzsuche:
1.  Klicken sie auf ein Element, in dem die personenbezogenen Daten der Einzelperson gefunden wurden.
2.  Klicken Sie im Menüband auf das Symbol „Löschen“ (Hinweis: Dieses Symbol ist deaktiviert, wenn der Datensatz nicht gelöscht werden kann).

    ![PowerApps-Konto löschen](./media/common-data-service-gdpr-dsr-guide/powerapps-account-delete.png)

## <a name="personal-data-stored-in-common-data-service-previous-version-databases"></a>In Datenbanken des Common Data Service (Vorgängerversion) gespeicherte personenbezogene Daten

### <a name="prerequisites"></a>Voraussetzungen

Sie können personenbezogene Daten von Einzelpersonen (z.B. Ihren eigenen Kunden oder Benutzern) in den Inhalten Ihrer CDS-Entitäten speichern.  

Wenn eine Einzelperson eine DSR-Anforderung an Ihre Organisation sendet, muss der CDS-Systemadministrator sämtliche Entitäten suchen, in denen innerhalb Ihrer Anwendung auf diese Person verwiesen werden könnte.  Der CDS-Administrator ist verantwortlich für die Verwaltung eines Inventars der Speicherorte der personenbezogenen Daten in den verschiedenen von Ihnen verwendeten Entitäten, damit Sie auf DSR-Anforderungen von Einzelpersonen reagieren können.

Anschließend können personenbezogene Daten in einer Entität innerhalb Ihrer Inhalte mit der produktinternen Funktion exportiert, berichtigt oder gelöscht werden.  

### <a name="discover"></a>Erkunden
Wenn ein CDS-Administrator eine DSR-Anforderung von einer Einzelperson empfängt, muss der Administrator ermitteln, welche Umgebungen/CDS-Instanzen personenbezogene Daten dieser Einzelperson enthalten.  Sie sollten Richtlinien und Prozeduren für die Verwaltung eines Inventars der Umgebungen, Instanzen und Entitäten entwickeln, in dem personenbezogene Daten von Einzelpersonen gespeichert werden. Mithilfe dieses Inventars können Sie personenbezogene Daten ermitteln, die Sie innerhalb Ihrer Inhalte gespeichert haben.

Personenbezogene Daten von Einzelpersonen können wie folgt gefunden werden:

|Ressourcen mit personenbezogenen Daten | Zweck | Websitezugriff |    Programmatischer Zugriff
| --- | --- | --- | ---
|Entitätsdatensätze | Zur Erfassung von Geschäftstransaktionen in der jeweiligen Geschäftseinheit. | PowerApps-Portal für Ersteller |    Nein

#### <a name="entity-records"></a>Entitätsdatensätze
Personenbezogene Daten von Einzelpersonen können in jeder Geschäftseinheit gespeichert werden.
Die vorliegende Version des Common Data Service umfasst ein eigenes Datenbankschema und eine Infrastruktur.  Sie verfügt über eigene Entitäten, die über die [PowerApps-Website](http://web.powerapps.com/) verwaltet werden.

So können Sie eine Liste mit Ihren Entitäten anzeigen:

1.  Auswählen der Umgebung

    ![PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2.  Navigieren Sie zur Registerkarte **Daten** > **Entitäten**.
3.  Wählen Sie die Entität aus, z.B. die Entität „Konto“.

    ![Liste mit den Details zu PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

4.  Klicken Sie auf die Entität.
5.  Klicken Sie auf die Registerkarte **Daten**. Es wird eine Liste mit Datensätzen für die Entität angezeigt.

    ![PowerApps-Legacykontodaten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

6.  Klicken Sie auf das Symbol **Daten exportieren**.
7.  Öffnen Sie das Excel-Arbeitsblatt nach Beendigung des Exports.
8.  Klicken Sie auf das Feld „Bearbeiten aktivieren“.
9.  Klicken Sie auf das Symbol „Suchen“.
10. Geben Sie die personenbezogenen Daten ein, nach denen Sie suchen möchten.
Personenbezogene Daten in Ihren Inhalten werden normalerweise in zentralen Entitäten gespeichert (z.B. „Konto“, „Kontakt“, „Lead“, „Verkaufschance“, „Worker“). Sie tragen jedoch die Verantwortung dafür, dass ein Inventar gepflegt wird, das die Speicherorte der personenbezogenen Daten von Einzelpersonen enthält.
11. **Wiederholen Sie die oben aufgeführten Schritte für jede Geschäftsentität, um die personenbezogenen Daten von Einzelpersonen zu ermitteln**; verwenden Sie hierzu die Inventarliste der Entitäten, in der die personenbezogenen Daten gespeichert sind.

### <a name="rectify"></a>Berichtigen
Bei der Anfrage einer betroffenen Personen bezüglich einer Berichtigung der von Ihrer Organisation gespeicherten personenbezogenen Daten müssen Sie entscheiden, ob die Anforderung umgesetzt werden soll oder nicht.  Das Berichtigen von Daten kann Aktionen wie die Bearbeitung, Zensur oder Entfernung von personenbezogenen Daten aus einem Dokument oder einem anderen Element beinhalten.

Sie können mit Azure Active Directory Identitäten (personenbezogene Daten) Ihrer Benutzer in Common Data Service für Apps verwalten. Unternehmenskunden können DSR-Berichtigungsanforderungen verwalten, einschließlich eingeschränkter Bearbeitungsfeatures je nach Art des angegebenen Microsoft-Diensts.  Als verarbeitende Instanz für die Daten bietet Microsoft keine Möglichkeit, vom System generierte Protokolle zu korrigieren, da diese auf Fakten basierende Aktivitäten und einen historischen Datensatz von Ereignissen innerhalb der Microsoft-Dienste darstellen.  

Weitere Einzelheiten finden Sie unter [DSGVO: Datensubjektanforderungen (DSR-Anforderungen)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

Zum Berichtigen personenbezogener, in der CDS-Umgebung enthaltener Daten können Sie die Entitätsdaten in ein Excel-Arbeitsblatt exportieren, sie aktualisieren und die aktualisierten Daten wieder in die Datenbank importieren.
Der CDS-Administrator ist dafür verantwortlich, alle Entitäten zu ermitteln, in denen die personenbezogenen Daten von Einzelpersonen gespeichert sind. Er muss die nachfolgenden Schritte für jede dieser Entitäten ausführen.

Über die [PowerApps-Website](http://web.powerapps.com/):

1.  Klicken Sie auf **Daten** > **Entitäten**.
2.  Klicken Sie auf die Entität, z.B. auf „Konto“.
3.  Klicken Sie auf die Option **Daten**.
4.  Klicken Sie auf das Symbol **Daten exportieren**.
5.  Klicken Sie auf das Symbol **In Excel öffnen** (nach Beendigung des Exports).
6.  Klicken Sie im Excel-Arbeitsblatt auf **Bearbeiten aktivieren**, und aktualisieren Sie die personenbezogenen Daten.
7.  **Speichern** Sie Ihr aktualisiertes Arbeitsblatt (verwenden Sie hierzu die Option **Speichern unter**, damit Ihnen der Speicherort der Datei bekannt ist).

    ![PowerApps-Legacykontodaten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

8.  Notwendige Aktualisierungen an den personenbezogenen Daten vornehmen
9.  Aktualisierungen speichern
10. Klicken Sie im Formular „Daten“ > „Entitäten“ > „Konto“ auf das Symbol „Daten importieren“.
11. Klicken Sie auf Feld „Suche“.
12. Wählen Sie die Datei aus, die Ihre Aktualisierungen enthält.
13. Klicken Sie auf das Feld „Öffnen“.
14. Klicken Sie auf die Schaltfläche „Importieren“.

### <a name="export"></a>Exportieren

Sie können personenbezogene Daten über jede Entität in einem Excel-Arbeitsblatt anzeigen oder bearbeiten.

Über die [PowerApps-Website](http://web.powerapps.com/):

1.  Navigieren Sie zu **Daten** > **Entitäten**.
2.  Wählen Sie die **Entität** aus, deren Daten Sie anzeigen und exportieren möchten.
3.  Klicken Sie auf die Option **Daten**.
4.  Klicken Sie auf das Symbol **Daten exportieren**. Dieser Export wird im Hintergrund ausgeführt. Sie werden benachrichtigt, sobald er beendet ist.
5. Klicken Sie auf das Symbol „In Excel öffnen“, um die exportierten Daten anzuzeigen.

### <a name="delete"></a>Löschen
Sie können personenbezogene Daten, die in Entitäten gespeichert sind, über die Funktion „Daten exportieren/importieren“ löschen.

Der CDS-Administrator ist dafür verantwortlich, alle Entitäten zu ermitteln, die personenbezogene Daten von Einzelpersonen enthalten. Für jede der Entitäten sind die folgenden Schritte wiederholt auszuführen.

Über die [PowerApps-Website](http://web.powerapps.com/):

1.  Klicken Sie auf **Daten** > **Entitäten**.
2.  Scrollen Sie in der Liste **Entität** nach unten, und suchen Sie die Entität, aus der die personenbezogenen Daten entfernt werden sollen.
3.  Klicken Sie auf die Entität.
4.  Klicken Sie auf die Option **Daten**.
5.  Klicken Sie auf das Symbol **Daten exportieren**.
6.  Klicken Sie auf das Symbol **In Excel öffnen** (nach Beendigung des Exports).
7.  **Aktivieren Sie die Bearbeitung** auf dem Excel-Arbeitsblatt.
8.  **Speichern** Sie Ihr aktualisiertes Arbeitsblatt (verwenden Sie hierzu die Option „Speichern unter“, damit Ihnen der Speicherort der Datei bekannt ist).
9.  Löschen Sie die Zeile(n) aus den Datensätzen mit den personenbezogenen Daten, die entfernt werden sollen.
10. Aktualisierungen speichern
11. Klicken Sie im Formular **Entitäten** auf das Symbol **Daten importieren**.
12. Klicken Sie auf das Feld **Suche**.
13. Wählen Sie die Datei aus, die Ihre Aktualisierungen enthält.
14. Klicken Sie auf das Feld **Öffnen**.
15. Klicken Sie auf die Schaltfläche „Importieren“.
