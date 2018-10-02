---
title: Erstellen eines PowerBI-Bericht | Microsoft Docs
description: Verbinden Ihrer Daten aus PowerBI Desktop mithilfe des Common Data Service for Apps-Konnektors.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-power-bi-report"></a>Power BI-Bericht anfertigen
Mit Common Data Service for Apps erhalten Sie mit Power BI Desktop direkt eine Verbindung mit Ihren Daten, um Berichte zu erstellen und mit Power BI zu veröffentlichen. Aus Power BI können Berichte in Dashboards verwendet werden, für andere Benutzer freigegeben werden und darauf über Plattformen hinweg auf Power BI-Mobile-Apps zugegriffen werden.

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>Voraussetzungen

Um mit Power BI mit Common Data Service for Apps zu verwenden, benötigen Sie Folgendes:

* Herunterladen und Installieren von Power BI Desktop. Dies ist eine kostenlose Anwendung ist, die auf Ihrem lokalen Computer ausgeführt wird. Sie können Power BI Desktop [hier](https://powerbi.microsoft.com/desktop/) herunterladen.
* Common Data Service for Apps-Umgebung mit Herstellerberechtigungen, um auf das Portal zuzugreifen und die Leseberechtigungen, um auf die Daten in Entitäten zuzugreifen.

## <a name="finding-your-common-data-service-for-apps-environment-url"></a>Suchen Sie Ihre Common Data Service for Apps-Umgebungs-URL

1. Öffnen Sie [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) und wählen Sie die Umgebung, mit der Sie eine Verbindung herstellen, und klicken Sie auf das **Einstellungszahnrad** in der oberen rechten Ecke. Klicken Sie dann auf **Erweiterte Anpassungen**

    ![CDS for App-Umgebung](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "CDS for App-Umgebung")

2. Klicken Sie auf **Ressourcen** im Entwicklerressourcenabschnitt. Dadurch wird eine neue Registerkarte geöffnet.

    ![CDS for App-Umgebung](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "CDS for App-Umgebung")

3. Kopieren Sie den Stamm die URL in die neuen Registerkarte. Dies ist die eindeutige URL für die Umgebung. Die URL hat das Format **https://yourenvironmentid.crm.dynamics.com/**. Stellen Sie sicher, dass Sie die restliche URL nicht kopieren. Halten Sie dies bereit, damit Sie es verwenden können, wenn Sie Ihren PowerBI-Bericht erstellen.

    ![CDS for App-Umgebung](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "CDS for App-Umgebung")

## <a name="connecting-to-common-data-service-for-apps-from-power-bi-desktop"></a>Verbindung mit Common Data Service for Apps von Power BI Desktop herstellen

1. Starten Sie **Power BI Desktop**. Wenn es sich um das erste Mal handelt, sehen Sie möglicherweise einen Willkommensbildschirm oder gelangen direkt zu einem leeren Canvas. Klicken Sie in beiden Fällen auf **Daten abrufen** und **Mehr**, um eine vollständige Liste der Datenquellen zu öffnen, die für Power BI Desktop verfügbar sind.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. Klicken Sie auf **Onlinedienste** und **Common Data Service for Apps (Beta)** in der Liste der Konnektoren. Klicken Sie auf **Verbinden**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. Fügen Sie Ihre **Common Data Service for Apps-Umgebungs-URL** in das Feld **Server-URL** ein und klicken Sie auf **OK**. Wenn dies das erste Mal ist, werden Sie aufgefordert, sich mithilfe derselben Anmeldeinformationen anzumelden, die Sie verwenden, um eine Verbindung mit PowerApps und Common Data Service for Apps herzustellen.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. Der Navigator zeigt Ihnen alle Entitäten, die für Ihre Umgebung zur Verfügung stehen, gruppiert in drei Ordner. Erweitern Sie den Ordner **Common Data Model**.

    * Allgemeines Datenmodell - Dies sind Standardentitäten, die häufig verwendet werden und in allen Umgebungen als Teil des allgemeinen Datenmodells verfügbar sind.
    * Benutzerdefinierte Entitäten - sind Entitäten, die Sie erstellt oder in Ihre Umgebung importiert haben.
    * System - enthält alle Entitäten in Ihrer Umgebung, einschließlich des allgemeinen Datenmodells und benutzerdefinierten Entitäten.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. Wählen Sie die Entität **Firma** aus, um eine Vorschau Ihrer Daten im rechten Bereich zu erhalten, und klicken Sie auf **Laden**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. Die Entität ist jetzt in Ihren Bericht geladen, und Sie können Berichte erstellen oder diesen Prozess wiederholen, um zusätzliche Entitäten hinzufügen.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. Klicken Sie auf das Feld **Name** im Feldbereich, um eine neue Visualisierung Ihres Berichts-Canvas hinzuzufügen. Sie können diesen Vorgang wiederholen und Visualisierungen ändern, um den Bericht zu erstellen.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>Verwenden von Optionssätzen

Optionssätze werden in Entitäten verwendet, um einem Benutzer in Apps und Flows eine Dropdownliste mit den Werten bereitzustellen. Bei Verwendung der Power BI-Konnektoren werden Optionssatzfelder als zwei Spalten dargestellt, um den eindeutigen Wert und den Anzeigenwert anzuzeigen.

Wenn Sie beispielsweise einen Optionssatz in Ihrer Entität haben, der ApprovalStatus heißt, würden zwei Felder in Power BI angezeigt werden:

* ApprovalStatus - Damit wird ein eindeutiger ganzzahliger Wert für jedes Element in Ihrem Optionssatz angezeigt. Das hilft, wenn Sie Filter anwenden, damit sie nicht betroffen sind, wenn Sie zukünftige Änderungen am Anzeigenamen vornehmen.
* ApprovalStatus_display - Damit wird der benutzerfreundliche Anzeigenamen des Elements angezeigt. Er wird am häufigsten verwendet, wenn die Option in einer Tabelle oder in einem Diagramm dargestellt wird.

    |ApproalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|Gesendet
    2|In Überprüfung
    3|Genehmigt
    4|Abgelehnt

## <a name="navigating-relationships"></a>Beziehungen navigieren

Beziehungen in Common Data Service for Apps erfordern, dass Sie in PowerBI Desktop mit einem GUID-Feld eine Beziehung zwischen den beiden Entitäten erstellen. Dies ist ein vom System generierter eindeutiger Bezeichner, der sicherstellt, dass Beziehungen für die Erstellungsdatensätze erstellt werden, wenn möglicherweise Mehrdeutigkeit oder doppelte Einträge bei anderen Felder vorhanden sind. Informationen zur Verwaltung von Beziehungen in Power BI Desktop finden Sie [hier](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships).

Mehrere Beziehungen werden möglicherweise automatisch erstellt, Sie können jedoch die Beziehungen weiterhin überprüfen und sicherstellen, dass die korrekten erstellt wurden, als Ihr Bericht erstellt wurde:

* Dieses Suchfeld in der Entität enthält die GUID des Datensatzes in der verknüpfte Entität.
* Die verknüpfte Entität verfügt über ein Feld im Format "[EntityName]id", das die GUID enthält, beispielsweise Accountid oder MyCustomEntityid
* Mit der Funktion "Beziehungen verwalten" von PowerBI Desktop erstellen Sie eine neue Beziehung zwischen Ihrem Suchfeld und dem ID-Feld in der verknüpften Entität.


## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md)
* [Beziehungen zwischen Entitäten definierten](data-platform-entity-lookup.md)


