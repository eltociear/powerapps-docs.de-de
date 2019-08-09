---
title: Hinzufügen von Berichterstattung zur modellgesteuerten App
ms.custom: ''
ms.date: 06/24/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-reporting-to-your-model-driven-app"></a>Hinzufügen von Berichterstattung zur modellgesteuerten App

PowerApps-Apps können Berichte einschließen, die nützliche Geschäftsinformationen für den Benutzer bereitstellen. Diese Berichte basieren auf SQL Server Reporting Services und bieten die gleichen Funktionen wie für die gängigen Berichte der SQL Server Reporting Services.

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "Progress against goals standard report")

Systemberichte stehen allen Benutzern zur Verfügung. Berichte, die in Besitz einzelner Benutzer sind oder von diesen erstellt wurden, können für bestimmte Kollegen oder Teams freigegeben oder für die gesamte Organisation verfügbar gemacht werden, damit sie von allen Benutzern ausgeführt werden können. Diese Berichte verwenden FetchXML-Abfragen, die für Common Data Service und Dynamics 365 for Customer Engagement-Apps systemeigen sind, und rufen Daten ab, um den Bericht zu erstellen. Berichte, die in einer PowerApps-App erstellt werden, sind auf einer Fetch-Funktion basierende Berichte.

> [!NOTE]
> Berichtsfunktionen können nicht mit Canvas- oder modellgesteuerten Apps für Mobilgeräte, wie Tablets und Smartphones, verwendet werden. 

Berichte können auf eine der folgenden Arten erstellt werden:

- In einer modellgesteuerten App mithilfe des Berichts-Assistenten. Weitere Informationen: [Erstellen oder Bearbeiten eines Berichts mit dem Berichts-Assistenten](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
<!-- From a model-driven app using an advanced find query. To do this, you build an advanced find query and then select **Download as FetchXML**. Next, from the reports area select **New**, for **Report Type** select **Existing File**, select **Choose File** open the xml file, fill in the required fields, and save the report. More information: [Add a report](/dynamics365/customer-engagement/basics/add-existing-report) -->
- Erstellen eines benutzerdefinierten Berichts mit SQL Server Data Tools und Berichterstellungserweiterungen. Weitere Informationen: [Handbuch zu Berichterstellung und Analyse](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)


## <a name="add-reporting-to-a-unified-interface-app"></a>Hinzufügen von Berichterstattung zur App mit einheitlicher Oberfläche
Sie können auf der Fetch-Funktion basierende Berichtsfunktionen zur App hinzufügen, damit Benutzer Berichte ausführen, freigeben, erstellen und bearbeiten können. Fügen Sie hierzu die die Berichtsentität zur Siteübersicht der App hinzu. 

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und öffnen Sie eine vorhandene App zum Bearbeiten. 
2. Wählen Sie im App-Designer ![Stiftsymbol zum Bearbeiten der Siteübersicht](media/ccf-pencil-icon.png) neben **Siteübersicht** aus. 
3. Wählen Sie im Siteübersichts-Designer die Option **Hinzufügen** und anschließend **Bereich** aus. 
4. Geben Sie im Feld **Titel** einen Namen für den Bereichstitel ein, beispielsweise *Berichte*. 
5. Wählen Sie den Bereich aus, den Sie im vorherigen Schritt benannt haben, wählen Sie **Hinzufügen** und **Gruppe** aus, und geben Sie dann im Gruppenfeld **Titel** einen Namen für den Gruppentitel ein, beispielsweise *Berichte*. 
6. Wählen Sie die Gruppe aus, die Sie im vorherigen Schritt benannt haben, wählen Sie **Hinzufügen** und **Unterbereich** aus, und fügen Sie dann die folgenden Eigenschaften hinzu: 

   - **Typ**: Wählen Sie **Entität** aus.
   - **Entität**: Wählen Sie in der Liste der Entitäten **Bericht**-Entität aus.  
   - **Titel**. Geben Sie einen beschreibenden Titel ein, beispielsweise *Berichte*.

      ![Hinzufügen einer Berichtsentität zur Siteübersicht](media/report-entity-sitemap.png)

7. Wählen Sie **Speichern und schließen** aus, um zum App-Designer zurückzukehren. 


8. Wählen Sie im App-Designer **Speichern** und dann **Veröffentlichen** aus.


Nun zeigt die App einen Bereich **Berichte** an, in dem Benutzer Berichte, für die sie über die Berechtigung verfügen, anzeigen, ausführen, zuweisen, freigeben oder bearbeiten können, sowie neue Berichte mithilfe des Berichts-Assistenten erstellen können. 

> [!div class="mx-imgBorder"] 
> ![](media/report-feature-in-app.png "Berichtsanzeige")

### <a name="see-also"></a>Siehe auch
[Ausführen eines Berichts](/dynamics365/customer-engagement/basics/run-report)
