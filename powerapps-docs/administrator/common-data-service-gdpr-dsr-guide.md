---
title: Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service (CDS) für Apps | Microsoft-Dokumentation
description: 'Exemplarische Vorgehensweise: Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service (CDS) für Apps'
author: jamesol-msft
ms.reviewer: paulliew
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: b550d5fe7e36c36177fff017adcf9d9034c93dd4
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218048"
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-common-data-service-for-apps-customer-data"></a>Reagieren auf DSR-Anforderungen für Kundendaten in Common Data Service für Apps

## <a name="introduction-to-dsr-requests"></a>Einführung in DSR-Anforderungen
Die Datenschutz-Grundverordnung der EU erteilt Personen (in der Verordnung als *betroffene Personen* bezeichnet) das Recht, vom Arbeitgeber oder einer anderen Einrichtung oder Organisation (auch als *Verantwortliche* bezeichnet) erhobene personenbezogene Daten zu verwalten. Personenbezogene Daten sind in der DSGVO sehr umfassend definiert als alle Informationen, die sich auf eine identifizierte oder identifizierbare natürliche Person beziehen. Die DSGVO erteilt betroffenen Personen folgende Rechte bezüglich ihrer personenbezogenen Daten:

* Recht auf das Erhalten einer Kopie
* Recht auf Berichtigung
* Recht auf Einschränkung der Verarbeitung
* Recht auf Löschung
* Recht auf Datenübertragbarkeit

Eine betroffene Person kann bei einem Verantwortlichen mit einem formellen Antrag die Einschränkung der Verarbeitung von personenbezogenen Daten verlangen. Dieser Antrag wird auch DSR-Anforderung (Data Subject Rights, Rechte betroffener Personen) genannt.

In diesem Artikel wird beschrieben, welche Vorbereitungen Microsoft bezüglich der Datenschutz-Grundverordnung trifft. Darüber hinaus gibt der Artikel einen Überblick über Maßnahmen, die Sie ergreifen können, um den Bestimmungen der DSGVO mithilfe von PowerApps, Microsoft Flow und Common Data Service für Apps nachzukommen. Sie erfahren, wie Sie als Verantwortlicher mit Microsoft-Produkten, -Diensten und -Verwaltungstools im Rahmen einer DSR-Anforderung personenbezogene Daten in der Microsoft-Cloud finden, darauf zugreifen und diese behandeln können.

In diesem Artikel werden die folgenden Aktionen besprochen:

* **Ermitteln**: Verwenden Sie Such- und Ermittlungstools, um schneller Kundendaten zu finden, die Gegenstand einer DSR-Anforderung sein könnten. Sobald Sie potenziell relevante Dokumente ermittelt haben, können Sie eine oder mehrere DSR-Aktionen ausführen, um auf eine Anforderung zu reagieren. Oder Sie entscheiden, dass die Anforderung nicht den Richtlinien Ihrer Organisation bezüglich DSR-Anforderungen entspricht.

* **Zugreifen**: Rufen Sie personenbezogene Daten aus Microsoft Cloud ab, und fertigen Sie gegebenenfalls eine Kopie der Daten an, die Sie der betroffenen Person zur Verfügung stellen können.

* **Berichtigen**: Nehmen Sie Änderungen vor oder implementieren Sie ggf. andere angeforderte Aktionen für die personenbezogenen Daten.

* **Einschränken**: Schränken Sie die Verarbeitung von personenbezogenen Daten ein, indem Sie entweder die Lizenzen für verschiedene Onlinedienste entfernen oder die gewünschten Dienste, wenn möglich, deaktivieren. Sie können Daten auch aus Microsoft Cloud entfernen und sie lokal oder an einem anderem Speicherort beibehalten.

* **Löschen**: Löschen Sie personenbezogene Daten dauerhaft aus der Microsoft-Cloud.

* **Exportieren**: Stellen Sie der betroffenen Person eine elektronische Kopie ihrer personenbezogenen Daten (in einem maschinenlesbaren Format) zur Verfügung.

## <a name="cds-for-apps-customer-data"></a>CDS für Apps-Kundendaten

> [!IMPORTANT]
> Gilt für CDS für Apps und für Common Data Service (vorherige Version)

CDS für Apps und die vorherige Version von CDS unterscheiden sich bei der Interaktion mit personenbezogenen Daten.

Sie können die Art der CDS-Umgebung ermitteln, indem Sie sich bei [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) anmelden und die folgenden Schritte durchführen:

1. Wählen Sie aus der Dropdownliste **Umgebung** eine Umgebung aus.
2. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Daten** und dann auf **Entitäten**.

    Ihre Umgebung ist CDS für Apps, wenn die folgenden Entitäten aufgelistet sind:

    ![Liste der PowerApps-Entitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-entities-list.png)

    Ihre Umgebung ist die vorherige Version von CDS, wenn die folgenden Entitäten aufgelistet sind:

    ![Liste der PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-list.png)

Nachdem Sie bestimmt haben, welche CDS-Umgebung vorhanden ist, führen Sie die im folgenden Abschnitt beschriebenen Schritte durch, um personenbezogene Daten zu bestimmen.

> [!NOTE]
> Möglicherweise verfügen Sie über einige Umgebungen in CDS für Apps und weitere in der vorherigen Version von CDS. Daher müssen Sie die nachfolgend beschriebenen Prozesse für sämtliche Umgebungen in Ihrer Organisation wiederholen.

## <a name="user-personal-data-in-cds-for-apps"></a>Personenbezogenen Benutzerdaten in CDS für Apps

### <a name="prerequisites"></a>Voraussetzungen
Sie müssen Benutzer im Office 365 Admin Center erstellen und diesen eine entsprechende Benutzerlizenz und Sicherheitsrolle zuweisen, damit sie auf CDS für Apps zugreifen und dieses verwenden können.

Personenbezogene Standardbenutzerdaten (z.B. Benutzername, Benutzer-ID, Telefonnummer, E-Mail-Adresse und Anschrift) werden im Office 365 Admin Center aufbewahrt und verwaltet. Systemadministratoren können diese personenbezogenen Daten nur im Office 365 Admin Center aktualisieren. Diese Daten werden anschließend automatisch mit der Entität „User“ in CDS für Apps in allen Umgebungen synchronisiert. Systemadministratoren können benutzerdefinierte Attribute auch erstellen, um zusätzliche personenbezogenen Benutzerdaten in der CDS für Apps-Systementität „User“ zu erfassen und manuell zu warten und zu verwalten.

Wenn ein Benutzer aus dem Office 365 Admin Center gelöscht wird, wird der Benutzerdatensatz nicht automatisch von der CDS-Systementität „User“ entfernt, um eine Unterbrechung der Geschäftsanwendungen zu verhindern, die möglicherweise entscheidend für die Vorgänge Ihrer Organisation sind. Der Status des Benutzers ist in CDS für Apps auf „Deaktiviert“ festgelegt, aber die personenbezogenen Daten des Benutzers müssen von einem Systemadministrator innerhalb der App aus CDS für Apps gelöscht werden.

Nur globale Office 365-Administratoren und CDS-Systemadministratoren können die nachfolgend aufgeführten Aktionen ermitteln, berichtigen, exportieren und löschen.

### <a name="discover"></a>Erkunden
Systemadministratoren können mehrere CDS für Apps-Instanzen erstellen. Diese Instanzen können zu Test-, Entwicklungs- oder Produktionszwecken verwendet werden. Jede dieser Instanzen verfügt über eine Kopie der Systementität „User“ mit sämtlichen benutzerdefinierten Attributen, die vom Systemadministrator hinzugefügt wurden, sowie mit den personenbezogenen Daten, die über das Office 365 Admin Center synchronisiert wurden.

Ein Systemadministrator kann eine Liste mit allen CDS für Apps-Instanzen suchen, indem er über das PowerApps Admin Center zum Dynamics 365 Admin Center navigiert.

Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

3.  Klicken oder tippen Sie auf **Dynamics 365 Admin Center**.

    ![PowerApp-Umgebungsdetails](./media/common-data-service-gdpr-dsr-guide/powerapps-environment-details.png)

    Es wird eine Liste aller Instanzen angezeigt.

    ![PowerApps-Instanzauswahl](./media/common-data-service-gdpr-dsr-guide/powerapps-instance-picker.png)

Sie können personenbezogene Daten von CDS für Apps-Benutzern in den folgenden Ressourcen finden:

|Ressourcen- | Zweck | Websitezugriff | Programmatischer Zugriff
| --- | --- | --- | ---
| Entitätsdatensatz | In der Systementität „User“ werden die personenbezogenen Daten eines Benutzers gespeichert. | [PowerApps Admin Center](https://admin.powerapps.com) | Über die [Web-API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)
| Verlauf überprüfen | Lässt zu, dass Kunden Ressourcen ermitteln können, die von Benutzern auf einer Entitätsstufe erstellt, geändert oder gelöscht wurden, oder Ressourcen, auf die Benutzer zugegriffen haben. | [PowerApps Admin Center](https://admin.powerapps.com) | Über die [Web-API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)

#### <a name="user"></a>User
Personenbezogene Benutzerdaten werden in Azure Active Directory gespeichert und automatisch mit allen CDS für Apps-Umgebungen synchronisiert. Systemadministratoren können diese personenbezogenen Daten nicht direkt in CDS für Apps aktualisieren, während der Benutzer aktiv ist. Sie müssen die Daten im Office 365 Admin Center aktualisieren. Systemadministratoren können personenbezogene Daten direkt in CDS für Apps hinzufügen (z.B. benutzerdefinierte Attribute). Sie müssen diese Daten allerdings manuell verwalten.

Navigieren Sie zum [PowerApps Admin Center](https://admin.powerapps.com/), und führen Sie Folgendes durch, um einen Benutzer und dessen personenbezogene Daten zu ermitteln:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf **Öffnen**.

3. Navigieren Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**.

4. Geben Sie den Namen des Benutzers im **Suchfeld** ein, und klicken oder tippen Sie auf **Suchen**.

5. Doppelklicken oder doppeltippen Sie auf den Benutzernamen, um dessen personenbezogene Daten anzuzeigen.

    ![PowerApps-Benutzerformular](./media/common-data-service-gdpr-dsr-guide/powerapps-user-form.png)

#### <a name="audit-history"></a>Verlauf überprüfen
Wenn die [Überwachungsnachverfolgung](https://docs.microsoft.com/dynamics365/customer-engagement/admin/audit-data-user-activity) für eine Entität in CDS für Apps aktiviert ist, werden die personenbezogenen Daten sowie die vom Benutzer ausgeführten Aktionen im Überwachungsverlauf erfasst.

### <a name="rectify"></a>Berichtigen
Bei der Anfrage einer betroffenen Person bezüglich einer Berichtigung der von Ihrer Organisation gespeicherten personenbezogenen Daten müssen Sie entscheiden, ob die Anforderung umgesetzt werden soll oder nicht. Das Berichtigen von Daten kann Aktionen wie die Bearbeitung, Zensur oder Entfernung von personenbezogenen Daten aus einem Dokument oder einem anderen Element beinhalten.

Sie können Azure Active Directory zum Verwalten der Identitäten (personenbezogene Daten) Ihrer Benutzer in CDS für Apps verwenden. Unternehmenskunden können DSR-Berichtigungsanforderungen verwalten, indem sie die eingeschränkten Bearbeitungsfeatures nutzen, die im jeweiligen Microsoft-Diensts zur Verfügung stehen. Als verarbeitende Instanz für die Daten bietet Microsoft keine Möglichkeit, vom System generierte Protokolle zu berichtigen, da diese auf Fakten basierende Aktivitäten und einen historischen Datensatz von Ereignissen innerhalb der Microsoft-Dienste darstellen. Weitere Einzelheiten finden Sie unter [GDPR: Data Subject Requests (DSRs) (DSGVO: Anforderungen betroffener Personen (Data Subject Requests, DSRs))](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

Nachdem der Benutzerdatensatz aus Azure Active Directory gelöscht wurde, können Systemadministratoren die verbleibenden personenbezogenen Benutzerdaten (z.B. benutzerdefinierte Attribute) aus allen Instanzen entfernen.  

### <a name="export"></a>Exportieren

#### <a name="system-user"></a>Systembenutzer
Sie können die personenbezogenen Benutzerdaten, die in der Systementität „User“ gespeichert sind, aus der Benutzerliste im Admin Center in Excel exportieren.

Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf **Öffnen**.

3. Navigieren Sie zu **Einstellungen** > **Security** (Sicherheit), und wählen Sie dann **Enabled Users View** (Aktivierte Benutzer anzeigen).

4. Klicken Sie auf **In Excel exportieren**.

#### <a name="audit-history"></a>Verlauf überprüfen
Sie können Screenshots des Überwachungsverlaufs im Admin Center machen.

Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf **Öffnen**.

3. Navigieren Sie zu **Einstellungen** > **Auditing**, und wählen Sie **Audit Summary View** (Überwachung > Überwachungszusammenfassung anzeigen).

    ![PowerApps-Menü „Überwachungsverlauf“](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-menu.png)

4. Ermitteln Sie den Speicherort des Überwachungsdatensatzes, und drücken Sie dann ALT+DRUCK, um einen Screenshot zu machen.

    ![PowerApps-Menü „Verlaufsdetails“](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-details.png)

5. Speichern Sie den Screenshot als Datei, die Sie an den DSR-Anforderer senden können.

### <a name="delete"></a>Löschen

#### <a name="user"></a>User
Wenn ein Benutzer aus dem Office 365 Admin Center gelöscht wird, wird der Benutzerdatensatz nicht automatisch von der CDS-Systementität „User“ entfernt, um eine Unterbrechung der Geschäftsanwendungen zu verhindern, die möglicherweise entscheidend für die Vorgänge Ihrer Organisation sind. Der Status des Benutzers ist in CDS für Apps auf „Deaktiviert“ festgelegt, aber die personenbezogenen Daten des Benutzers müssen von einem Systemadministrator innerhalb der App aus CDS für Apps gelöscht werden.

#### <a name="remove-a-users-personal-data-from-the-users-summary-page"></a>Löschen der personenbezogenen Benutzerdaten von der Zusammenfassungsseite des Benutzers
Wenn der Benutzerdatensatz aus Azure Active Directory gelöscht wurde, wird auf der Zusammenfassungsseite des Benutzers folgende Meldung angezeigt:

*This user’s information is no longer managed by Office 365. You can update this record to respond to DSR requests by removing or replacing all personal data associated with this user.* (Die Informationen zu diesem Benutzer werden nicht mehr von Office 365 verwaltet.Sie können diesen Datensatz aktualisieren, um auf DSR-Anforderungen zu reagieren, indem Sie sämtliche personenbezogene Daten entfernen oder ersetzen, die mit diesem Benutzer verknüpft sind.)

Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf **Öffnen**.

3. Navigieren Sie zu **Einstellungen** > **Security** > **Users**, und wählen Sie **Disabled Users View** (Sicherheit > Benutzer > Deaktivierte Benutzer anzeigen).

4. Geben Sie den Namen des Benutzers im **Suchfeld** ein, und klicken oder tippen Sie auf **Suchen**.

9. Doppelklicken Sie in den Suchergebnissen auf den Benutzernamen.

10. Entfernen Sie auf der Zusammenfassungsseite des Benutzers alle personenbezogenen Daten, und klicken oder tippen Sie anschießend auf **Speichern**.

#### <a name="remove-a-users-personal-data-by-using-excel"></a>Entfernen der personenbezogenen Benutzerdaten mit Excel
Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf **Öffnen**.

3. Navigieren Sie zu **Einstellungen** > **Security** > **Users**, und wählen Sie **Disabled Users View** (Sicherheit > Benutzer > Deaktivierte Benutzer anzeigen).

4. Erstellen Sie eine Excel-Vorlage mit den personenbezogenen Benutzerdaten, und laden Sie diese herunter. Ausführliche Anweisungen finden Sie im Abschnitt „Eine neue Excel-Vorlage erstellen“ unter [Analysieren und Teilen von Daten mit Excel-Vorlagen](https://docs.microsoft.com/dynamics365/customer-engagement/admin/analyze-your-data-with-excel-templates#create-a-new-excel-template).

8. Öffnen Sie die heruntergeladene Excel-Vorlagendatei, entfernen Sie die personenbezogenen Benutzerdaten, und speichern Sie die Datei.

9. Kehren Sie zur Seite **Disabled Users View** (Deaktivierte Benutzer anzeigen) zurück, und klicken Sie auf **Daten importieren**.

10. Wählen sie die Excel-Vorlagendatei im Dialogfeld **Upload data file** (Datendatei hochladen) aus, und nehmen Sie die nötigen Änderungen im Fenster **Map Fields** (Felder zuordnen) vor.

12. Klicken oder tippen Sie auf **Next** (Weiter), und klicken oder tippen Sie auf **Submit** (Übermitteln).

#### <a name="remove-audit-history-from-the-audit-summary-view-page"></a>Entfernen eines Überwachungsverlaufs von der Seite „Zusammenfassungsansicht“
Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf **Öffnen**.

3. Navigieren Sie zu **Einstellungen** > **Auditing**, und wählen Sie **Audit Summary View** (Überwachung > Überwachungszusammenfassung anzeigen).

4. Machen Sie den Änderungsverlauf des Benutzers ausfindig, aktivieren oder deaktivieren Sie das jeweilige Kontrollkästchen per Klick oder Tippen neben einer bzw. mehreren Zeilen, und klicken oder tippen Sie auf **Delete Change History** (Änderungsverlauf löschen).

## <a name="personal-data-stored-in-databases-of-cds-for-apps"></a>Personenbezogene Daten, die in Datenbanken von CDS für Apps gespeichert werden

### <a name="prerequisites"></a>Voraussetzungen
Sie können personenbezogene Daten von Einzelpersonen (z.B. Ihren eigenen Kunden) in Ihren CDS für Apps-Entitäten speichern.  

CDS-Systemadministratoren sind für das Pflegen eines Inventars der Speicherorte von personenbezogenen Daten jeder Einzelperson innerhalb der verschiedenen Entitäten verantwortlich, sodass die Daten im Rahmen einer DSR-Anforderung schnell gefunden werden können.  

Anschließend können personenbezogene Daten in einer Entität mit den produktinternen Funktionalitäten exportiert, berichtigt oder gelöscht werden.  

### <a name="discover"></a>Erkunden
Wenn CDS-Systemadministratoren eine DSR-Anforderung von einer Einzelperson empfangen, müssen sie ermitteln, welche Umgebungen/CDS-Instanzen personenbezogene Daten dieser Einzelperson enthalten. Personenbezogene Daten werde normalerweise in Hauptentitäten (z.B. Account, Contact, Lead, Opportunity usw.) gespeichert. Es liegt jedoch in Ihrer Verantwortung, Richtlinien und Vorgehensweisen zum Verwalten eines Inventars der personenbezogenen Daten jeder Einzelperson zu entwickeln, sodass Sie auf DSR-Anforderungen reagieren können.

Mit einem Inventar können CDS-Systemadministratoren die Suchentitäten und -felder konfigurieren und anschließend auf die CDS für Apps-Umgebung zugreifen, um personenbezogene Daten zu ermitteln. Weitere Informationen finden Sie unter [Configure Relevance Search (Konfigurieren der Relevanzsuche)](https://go.microsoft.com/fwlink/?linkid=872506).

Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf Suchen, und klicken oder tippen Sie anschließend auf **Relevanzsuche**.

    ![PowerApps-Menü „Relevanzsuche“](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3. Geben Sie die personenbezogenen Daten der Einzelperson in das Suchfeld ein, und klicken oder tippen Sie auf **Suchen**.

    ![Ergebnisse der PowerApps-Relevanzsuche](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

### <a name="rectify"></a>Berichtigen
CDS-Systemadministratoren können die personenbezogenen Daten einer Einzelperson mithilfe der Liste der Ergebnisse von der Relevanzsuche aktualisieren. Die personenbezogenen Daten einer Einzelperson können jedoch auch in einer benutzerdefinierte Entität gespeichert sein. CDS-Systemadministratoren tragen die Verantwortung dafür, dass ein Inventar gepflegt wird, das diese anderen benutzerdefinierten Entitäten enthält, und dass die personenbezogenen Daten der Einzelperson entsprechend aktualisiert werden.

Führen Sie in den Ergebnissen der Relevanzsuche Folgendes aus:

1. Klicken oder tippen Sie auf ein Element, dass die personenbezogenen Daten einer Einzelperson enthält.

2. Aktualisieren Sie die personenbezogenen Daten einer Einzelperson, und klicken oder tippen Sie auf **Speichern**.

    ![PowerApps-Kontodetails](./media/common-data-service-gdpr-dsr-guide/powerapps-account-details.png)

### <a name="export"></a>Exportieren
Sie können einen Screenshot von den Daten machen und diesen mit dem DSR-Anforderer teilen.

Führen Sie im [PowerApps-Admin Center](https://admin.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie im Navigationsbereich auf **Umgebungen**, und wählen Sie dann eine Umgebung aus der Liste aus.

2. Klicken oder tippen Sie auf **Dynamics 365 Admin Center**, wählen Sie eine Umgebung aus der Liste aus, und klicken oder tippen Sie dann auf Suchen, und klicken oder tippen Sie anschließend auf **Relevanzsuche**.

    ![PowerApps-Menü „Relevanzsuche“](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3. Geben Sie die personenbezogenen Daten der Einzelperson in das Suchfeld ein, und klicken oder tippen Sie auf **Suchen**.

    ![Ergebnisse der PowerApps-Relevanzsuche](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

4. Doppelklicken Sie in den Suchergebnissen auf das Element.

5. Drücken Sie zum Erstellen des Screenshots die Tasten ALT+DRUCK.

6. Speichern Sie den Screenshot als Datei, die Sie an den DSR-Anforderer senden können.

### <a name="delete"></a>Löschen
CDS-Administratoren können die personenbezogenen Daten einer Einzelperson aus den Datensätzen löschen, in denen die Daten gespeichert wurden.  CDS-Systemadministratoren haben folgende Möglichkeiten: Sie können den Datensatz löschen, in dem die personenbezogenen Daten gespeichert wurden oder die Inhalte der personenbezogenen Daten aus dem Datensatz entfernen.  

> [!NOTE]
> CDS-Administratoren können die Umgebung anpassen, um zu verhindern, dass ein Datensatz aus einer Entität gelöscht wird. Bei einer Konfiguration dieser Art müssen Sie die Inhalte der personenbezogenen Daten aus dem Datensatz löschen, statt den Datensatz selbst zu löschen.

Führen Sie in den Ergebnissen der Relevanzsuche Folgendes aus:

1. Klicken oder tippen Sie auf ein Element, dass die personenbezogenen Daten einer Einzelperson enthält.

2. Klicken Sie im Menüband auf **Löschen**. (Beachten Sie, dass **Löschen** nicht ausgewählt werden kann, wenn der Datensatz nicht gelöscht werden darf.)

    ![PowerApps-Konto löschen](./media/common-data-service-gdpr-dsr-guide/powerapps-account-delete.png)

## <a name="personal-data-stored-in-databases-of-the-previous-version-of-cds"></a>Personenbezogene Daten, die in Datenbanken der vorherigen Version von Common Data Service gespeichert wurden

### <a name="prerequisites"></a>Voraussetzungen
Sie können personenbezogene Daten von Einzelpersonen (z.B. Ihren eigenen Kunden) in Ihren CDS-Entitäten speichern.  

CDS-Systemadministratoren sind für das Pflegen eines Inventars der Speicherorte von personenbezogenen Daten jeder Einzelperson innerhalb der verschiedenen Entitäten verantwortlich, sodass die Daten im Rahmen einer DSR-Anforderung schnell gefunden werden können.  

Anschließend können personenbezogene Daten in einer Entität mit den produktinternen Funktionalitäten exportiert, berichtigt oder gelöscht werden.  

### <a name="discover"></a>Erkunden
Wenn CDS-Administratoren eine DSR-Anforderung von einer Einzelperson empfangen, muss der Administrator ermitteln, welche Umgebungen/CDS-Instanzen personenbezogene Daten dieser Einzelperson enthalten. Personenbezogene Daten werde normalerweise in Hauptentitäten (z.B. Account, Contact, Lead, Opportunity usw.) gespeichert. Es liegt jedoch in Ihrer Verantwortung, Richtlinien und Vorgehensweisen zum Verwalten eines Inventars der personenbezogenen Daten jeder Einzelperson zu entwickeln, sodass Sie auf DSR-Anforderungen reagieren können.

Sie können personenbezogene Benutzerdaten der vorherigen Version von CDS in den folgenden Ressourcen finden:

|Ressourcen- | Zweck | Websitezugriff |  Programmatischer Zugriff
| --- | --- | --- | ---
|Entitätsdatensätze | Erfassung von Geschäftstransaktionen in der jeweiligen Geschäftseinheit | [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) |    Nein

#### <a name="entity-records"></a>Entitätsdatensätze
Personenbezogene Daten von Einzelpersonen können in jeder Geschäftseinheit gespeichert werden.

Die vorliegende Version von CDS umfasst ein eigenes Datenbankschema und eine Infrastruktur. Sie verfügt über ihre eigenen Entitäten, die Sie in [PowerApps](http://web.powerapps.com/) verwalten können.

So können Sie eine Liste mit Ihren Entitäten anzeigen:

1. Wählen Sie aus der Dropdownliste **Umgebung** eine Umgebung aus.

2. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Daten** und dann auf **Entitäten**.

    ![PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

3. Klicken oder tippen Sie wie unten gezeigt in der Liste der Entitäten auf eine Entität (z.B. auf die Entität „Account“).

    ![Liste mit den Details zu PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

4. Klicken oder tippen sie auf die Registerkarte **Daten**. Es wird eine Liste mit Datensätzen für die Entität angezeigt.

    ![PowerApps-Legacykontodaten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

5. Klicken oder tippen Sie auf **Daten exportieren**.

6. Klicken oder tippen Sie auf **In Excel öffnen**, sobald der Export abgeschlossen ist, und klicken oder tippen Sie anschließend auf **Bearbeiten aktivieren**.

7. Klicken oder tippen Sie auf „Suche“, geben Sie die personenbezogenen Daten der Einzelperson in das Suchfeld ein, und klicken oder tippen Sie auf **Suchen**.

8. Wiederholen Sie die oben aufgeführten Schritte für jede Geschäftsentität, um die personenbezogenen Daten von Einzelpersonen zu ermitteln. Verwenden Sie hierzu die Inventarliste.

### <a name="rectify"></a>Berichtigen
Bei der Anfrage einer betroffenen Person bezüglich einer Berichtigung der von Ihrer Organisation gespeicherten personenbezogenen Daten müssen Sie entscheiden, ob die Anforderung umgesetzt werden soll oder nicht. Das Berichtigen von Daten kann Aktionen wie die Bearbeitung, Zensur oder Entfernung von personenbezogenen Daten aus einem Dokument oder einem anderen Element beinhalten.

Sie können Azure Active Directory zum Verwalten der Identitäten (personenbezogene Daten) Ihrer Benutzer in der vorherigen Version von CDS verwenden. Unternehmenskunden können DSR-Berichtigungsanforderungen verwalten, indem sie die eingeschränkten Bearbeitungsfeatures nutzen, die im jeweiligen Microsoft-Diensts zur Verfügung stehen. Als verarbeitende Instanz für die Daten bietet Microsoft keine Möglichkeit, vom System generierte Protokolle zu berichtigen, da diese auf Fakten basierende Aktivitäten und einen historischen Datensatz von Ereignissen innerhalb der Microsoft-Dienste darstellen. Weitere Einzelheiten finden Sie unter [GDPR: Data Subject Requests (DSRs) (DSGVO: Anforderungen betroffener Personen (Data Subject Requests, DSRs))](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).

Zum Berichtigen personenbezogener, in der CDS-Umgebung enthaltener Daten können Sie die Entitätsdaten in ein Excel-Arbeitsblatt exportieren, sie aktualisieren und die aktualisierten Daten wieder in die Datenbank importieren.

Die CDS-Administratoren sind dafür verantwortlich, alle Entitäten zu ermitteln, die personenbezogene Daten von Einzelpersonen enthalten. Für jede der Entitäten sind die folgenden Schritte auszuführen.

Führen Sie in [PowerApps](http://web.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Daten** und dann auf **Entitäten**.

    ![PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. Klicken oder tippen Sie wie unten gezeigt in der Liste der Entitäten auf eine Entität (z.B. auf die Entität „Account“).

    ![Liste mit den Details zu PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. Klicken oder tippen sie auf die Registerkarte **Daten**. Es wird eine Liste mit Datensätzen für die Entität angezeigt.

    ![PowerApps-Legacykontodaten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. Klicken oder tippen Sie auf **Daten exportieren**.

5. Klicken oder tippen Sie auf **In Excel öffnen**, sobald der Export abgeschlossen ist, und klicken oder tippen Sie anschließend auf **Bearbeiten aktivieren**.

6. Klicken oder tippen Sie in der Menüleiste auf **Datei**, klicken oder tippen Sie auf **Speichern unter...**, und wählen Sie dann einen Speicherort aus, an dem die Datei gespeichert werden soll.

7. Nehmen Sie die notwendigen Aktualisierungen an den personenbezogenen Daten vor, und speichern Sie das Arbeitsblatt.

10. Kehren Sie in PowerApps zur Registerkarte **Daten** zurück, und klicken oder tippen Sie auf **Daten importieren**.

11. Klicken Sie auf **Suchen**, und wählen Sie dann die gerade aktualisierte Excel-Arbeitsmappe aus, und öffnen Sie diese.

12. klicken Sie auf **Importieren**.

### <a name="export"></a>Exportieren
Sie können personenbezogene Daten über jede Entität in ein Excel-Arbeitsblatt exportieren.

Führen Sie in [PowerApps](http://web.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Daten** und dann auf **Entitäten**.

    ![PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. Klicken oder tippen Sie wie unten gezeigt in der Liste der Entitäten auf die Entität, die Sie exportieren und anzeigen möchten (z.B. auf die Entität „Account“).

    ![Liste mit den Details zu PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. Klicken oder tippen sie auf die Registerkarte **Daten**. Es wird eine Liste mit Datensätzen für die Entität angezeigt.

    ![PowerApps-Legacykontodaten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. Klicken oder tippen Sie auf **Daten exportieren**.

    Dieser Export wird im Hintergrund ausgeführt. Sie werden benachrichtigt, sobald er beendet ist.

5. Klicken oder tippen Sie auf **In Excel öffnen**, um die exportierten Daten anzuzeigen.

### <a name="delete"></a>Löschen
Sie können personenbezogene Daten, die in Entitäten gespeichert sind, über das Feature „Daten exportieren/importieren“ löschen.

Die CDS-Administratoren sind dafür verantwortlich, alle Entitäten zu ermitteln, die personenbezogene Daten von Einzelpersonen enthalten. Für jede der Entitäten sind die folgenden Schritte auszuführen.

Führen Sie in [PowerApps](http://web.powerapps.com/) Folgendes durch:

1. Klicken oder tippen Sie zuerst im Navigationsbereich auf **Daten** und dann auf **Entitäten**.

    ![PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. Klicken oder tippen Sie wie unten gezeigt in der Liste der Entitäten auf die Entität, aus der Sie personenbezogene Daten entfernen möchten (z.B. die Entität „Account“).

    ![Liste mit den Details zu PowerApps-Legacyentitäten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. Klicken oder tippen sie auf die Registerkarte **Daten**. Es wird eine Liste mit Datensätzen für die Entität angezeigt.

    ![PowerApps-Legacykontodaten](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. Klicken oder tippen Sie auf **Daten exportieren**.

5. Klicken oder tippen Sie auf **In Excel öffnen**, sobald der Export abgeschlossen ist, und klicken oder tippen Sie anschließend auf **Bearbeiten aktivieren**.

6. Klicken oder tippen Sie in der Menüleiste auf **Datei**, klicken oder tippen Sie auf **Speichern unter...**, und wählen Sie dann einen Speicherort aus, an dem die Datei gespeichert werden soll.

7. Löschen Sie die Zeilen, die personenbezogene Daten enthalten, die Sie aus der Entität entfernen möchten, und speichern Sie anschließend das Arbeitsblatt.

10. Kehren Sie in PowerApps zur Registerkarte **Daten** zurück, und klicken oder tippen Sie auf **Daten importieren**.

11. Klicken Sie auf **Suchen**, und wählen Sie dann die gerade aktualisierte Excel-Arbeitsmappe aus, und öffnen Sie diese.

12. klicken Sie auf **Importieren**.