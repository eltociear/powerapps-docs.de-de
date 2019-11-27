---
title: Hinzufügen von Berichtsfeatures zur modellgesteuerten App
ms.custom: ''
ms.date: 08/16/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: aba6196680d674b8ee42096e340a105b19ac8d07
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752341"
---
# <a name="add-reporting-features-to-your-model-driven-app"></a>Hinzufügen von Berichtsfeatures zur modellgesteuerten App

PowerApps-Apps können Berichte umfassen, die nützliche Geschäftsinformationen für den Benutzer bereitstellen. Diese Berichte basieren auf SQL Server Reporting Services und bieten die gleichen Funktionen wie für die gängigen Berichte der SQL Server Reporting Services.

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "Progress against goals standard report")

Systemberichte stehen allen Benutzern zur Verfügung. Berichte, die in Besitz einzelner Benutzer sind oder von diesen erstellt wurden, können für bestimmte Kollegen oder Teams freigegeben oder für die gesamte Organisation verfügbar gemacht werden, damit sie von allen Benutzern ausgeführt werden können. Diese Berichte verwenden FetchXML-Abfragen (systeminterne XML-Abfragen in Common Data Service), um Berichtsdaten abzurufen und den Bericht zu erstellen. Berichte, die in einer PowerApps-App erstellt werden, sind auf einer Fetch-Funktion basierende Berichte.

> [!NOTE]
> Berichtsfunktionen können nicht mit Canvas- oder modellgesteuerten Apps für Mobilgeräte, wie Tablets und Smartphones, verwendet werden. 

<!-- Reports can be built in either of the following ways.

- From a model-driven app using the report wizard. More information: [Create or edit a report using the Report Wizard](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
- Create custom reports using SQL Server Data Tools and Report Authoring Extensions. More information: [Reporting and Analytics Guide](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)  -->


## <a name="add-reporting-to-a-unified-interface-app"></a>Hinzufügen von Berichterstattung zur App mit einheitlicher Oberfläche
Sie können auf der Fetch-Funktion basierende Berichtsfunktionen zur App hinzufügen, damit Benutzer Berichte ausführen, freigeben, erstellen und bearbeiten können. Fügen Sie hierzu die die Berichtsentität zur Siteübersicht der App hinzu. 

1. Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an, und öffnen Sie eine vorhandene App zum Bearbeiten. 
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
> ![](media/report-feature-in-app.png "Report view")

## <a name="options-for-creating-new-reports"></a>Optionen zum Erstellen neuer Berichte
Sie können auf zwei Arten einen neuen Bericht erstellen:
- Verwenden Sie den Berichts-Assistenten. Öffnen Sie eine modellgesteuerte App, die für die Berichterstellung aktiviert wurde, und führen Sie den Berichts-Assistenten aus, um einen neuen Bericht zu erstellen. Mit dem Berichts-Assistenten können Berichte mit Tabellen und Diagrammen erstellt werden, auch Drillthroughberichte und Berichte mit den n wichtigsten Kunden, Verkaufschancen usw. Weitere Informationen: [Erstellen eines Berichts mit dem Berichts-Assistenten](../../user/create-report-with-wizard.md) 
- Verwenden Sie die Berichterstellungserweiterung. Sie können neue Fetch-basierte Reporting Services-Berichte mit Visual Studio, SQL Server Data Tools und de Berichterstellungserweiterung schreiben oder vorhandene anpassen. Weitere Informationen: [Erstellen eines neuen Berichts mithilfe von SQL Server Data Tools](/dynamics365/customer-engagement/analytics/create-a-new-report-using-sql-server-data-tools)

## <a name="report-visibility"></a>Berichtssichtbarkeit
Standardentitätsberichte wie die Kontenübersicht für die Kontenentität stehen für alle App-Benutzer zur Verfügung. Benutzer, die Berichte besitzen, können sie für bestimmte Kollegen oder Teams freigeben. Systemadministratoren und -anpasser können Berichte organisationsweit sichtbar machen, damit sie von allen Benutzern verwendet werden können. Weitere Informationen zur Freigabe eines Berichts finden Sie unter [Freigeben eines Berichts für andere Benutzer und Teams](../../user/work-with-reports.md#share-a-report-with-other-users-or-teams). 

## <a name="reports-in-solutions"></a>Berichte in Lösungen
Bei den Berichten handelt es sich um lösungsfähige Berichte. Wird einer Lösung ein Bericht als Komponente hinzugefügt, wird sie zu einer einzelnen Softwareeinheit, durch die der Funktionsumfang und die Benutzeroberfläche von PowerApps erweitert werden. Nur Berichte, die für die Organisation sichtbar sind, können zu Lösungen hinzugefügt werden.

Um zu ermitteln, ob ein Bericht von der Organisation angezeigt werden kann, öffnen Sie in der Berichtsliste eine modellgesteuerte App, wählen Sie einen Bericht aus, und wählen Sie dann **Bearbeiten**. Überprüfen Sie auf der Registerkarte **Verwaltung**, ob **Sichtbar für** auf **Organisation** festgelegt ist. 

> [!div class="mx-imgBorder"] 
> ![](media/report-scope.png "Organization level report visibility")

Momentaufnahmen von Berichten können nicht als Teil einer Lösung hinzugefügt, importiert oder exportiert werden. In modellgesteuerten Apps gelten Berichte, Unterberichte, die Berichtskategorie, der Berichtsanzeigebereich sowie der berichtsbezogene Datensatztyp als Komponenten eines Berichtssatzes. Wenn Sie ein Lösungsupdate in einem Modus ohne Überschreibung importieren, werden alle Updates der Lösung für einen Bericht ignoriert, sofern eine Komponente des Berichtssatzes angepasst wurde.

## <a name="related-topics"></a>Verwandte Themen
[Arbeiten mit Berichten](/powerapps/user/work-with-reports)<br/>
[Erstellen eines Berichts mit dem Berichts-Assistenten](/powerapps/user/create-report-with-wizard)<br/>
[Hinzufügen eines Berichts von außerhalb von PowerApps](/powerapps/user/add-existing-report)<br/>
[Bearbeiten des Standardfilters eines Berichts](/powerapps/user/edit-report-filter)<br/>
[Problembehandlungsberichte](/powerapps/user/troubleshoot-reports)
