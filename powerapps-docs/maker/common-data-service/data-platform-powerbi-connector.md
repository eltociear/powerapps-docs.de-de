---
title: Erstellen eines Power BI-Berichts | Microsoft-Dokumentation
description: Verbinden Ihrer Daten aus Power BI Desktop mithilfe des Connectors von Common Data Service für Apps
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: 5fffcbcd8f58ae05f3fe5b3b4f871cf39d003321
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218186"
---
# <a name="create-a-power-bi-report"></a>Einen Power BI-Bericht erstellen
Mit Common Data Service für Apps können Sie eine direkte Verbindung zu Ihren Daten von Power BI Desktop herstellen, um Berichte zu erstellen und in Power BI zu veröffentlichen. In Power BI können Berichte in Dashboards verwendet und für andere Benutzer freigegeben werden. Außerdem kann plattformübergreifend von Power BI-Apps für Mobilgeräte aus darauf zugegriffen werden.

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen Folgendes, um Power BI mit Common Data Service für Apps zu verwenden:

* Laden Sie die kostenlose Anwendung Power BI Desktop auf Ihren lokalen Computer herunter, und installieren Sie diese. Sie können Power BI Desktop [hier](https://powerbi.microsoft.com/desktop/) herunterladen.
* Die Umgebung von Common Data Service für Apps mit Erstellerberechtigungen, um auf das Portal zuzugreifen und Leseberechtigungen, um auf die Daten in den Entitäten zuzugreifen.

## <a name="finding-your-common-data-service-for-apps-environment-url"></a>Suchen der Umgebungs-URL von Common Data Service für Apps

1. Öffnen Sie [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), und wählen Sie die Umgebung aus, mit der Sie eine Verbindung herstellen möchten, und klicken Sie auf das Zahnradsymbol für **Einstellungen** in der oberen rechten Ecke. Klicken Sie dann auf **Erweiterte Anpassungen**.

    ![Umgebung von CDS für Apps](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "CDS for Apps Environment")

2. Klicken Sie im Abschnitt „Entwicklerressourcen“ auf **Ressourcen**, um eine neue Registerkarte zu öffnen.

    ![Umgebung von CDS für Apps](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "CDS for Apps Environment")

3. Kopieren Sie den Stamm der URL in die neue Registerkarte. Dies ist die eindeutige URL für Ihre Umgebung. Die URL weist das Format **https://yourenvironmentid.crm.dynamics.com/** auf. Achten Sie darauf, den Rest der URL nicht zu kopieren. Speichern Sie diese, sodass Sie sie verwenden können, wenn Sie einen Power BI-Bericht erstellen.

    ![Umgebung von CDS für Apps](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "CDS for Apps Environment")

## <a name="connecting-to-common-data-service-for-apps-from-power-bi-desktop"></a>Herstellen einer Verbindung zu Common Data Service für Apps über Power BI Desktop

1. Starten Sie **Power BI Desktop**. Beim ersten Start wird ein Willkommensbildschirm oder ein leerer Zeichenbereich angezeigt. Klicken Sie in beiden Fällen auf **Daten abrufen** und dann auf **Mehr**, um die vollständige Liste der Datenquellen zu öffnen, die für Power BI Desktop verfügbar sind.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. Klicken Sie in der Liste der Connectors auf **Onlinedienste** und **Common Data Service für Apps (Beta)**. Klicken Sie auf **Verbinden**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. Fügen Sie die **Umgebung-URL von Common Data Service für Apps** in das Feld **Server-URL** ein, und klicken Sie auf **OK**. Bei der ersten Verwendung werden Sie dazu aufgefordert, sich mit den gleichen Anmeldeinformationen anzumelden, die Sie verwenden, um eine Verbindung mit PowerApps oder Common Data Service für Apps herzustellen.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. Der Navigator zeigt alle Entitäten, die für Ihre Umgebung verfügbar sind, in drei Ordner gruppiert an. Erweitern Sie den Ordner **Common Data Model**.

   * Common Data Service: Dabei handelt es sich um Standardentitäten, die häufig verwendet werden und in allen Umgebungen als Teil von Common Data Model verfügbar sind.
   * Benutzerdefinierte Entitäten: Entitäten, die Sie erstellt oder in Ihre Umgebung importiert haben.
   * System: Enthält alle Entitäten in Ihrer Umgebung, einschließlich Common Data Service und der benutzerdefinierten Entitäten.

     ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. Wählen Sie die Entität **Account** (Konto) aus, um eine Vorschau Ihrer Daten im rechten Bereich anzuzeigen, und klicken Sie auf **Laden**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. Die Entität wird nun in Ihren Bericht geladen, und Sie können mit der Erstellung von berichten beginnen oder diesen Vorgang wiederholen, um weitere Entitäten hinzuzufügen.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. Klicken Sie im Bereich „Felder“ auf das Feld **Name**, um eine neue Visualisierung zum Zeichenbereich Ihres Berichts hinzuzufügen. Sie können diesen Vorgang nun wiederholen und Visualisierungen ändern, um Ihren Bericht zu erstellen.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>Verwenden von Optionssätzen

Optionssätze werden in Entitäten verwendet, um dem Benutzer in Apps und Flows eine Dropdownliste Werte bereitzustellen. Wenn Sie den Optionssatz „Power BI-Connector“ verwenden, werden Felder als zwei Spalten dargestellt, um den eindeutigen Wert und den Anzeigewert anzuzeigen.

Wenn Sie beispielsweise eine Option für Ihre Entität namens „ApprovalStatus“ festgelegt haben, werden in Power BI zwei Felder angezeigt.

* ApprovalStatus: Dadurch wird ein eindeutiger ganzzahliger Wert für jedes Element in Ihrem Optionssatz angezeigt. Dies ist nützlich, wenn Filter angewendet werden, damit diese nicht beeinträchtigt werden, wenn Sie in Zukunft Änderungen am Anzeigenamen vornehmen.
* ApprovalStatus_display: Dadurch wird der Anzeigename des Elements angezeigt. Dies wird am häufigsten verwendet, wenn Sie die Option in einer Tabelle oder in einem Diagramm darstellen.

    |ApproalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|Gesendet
    2|Wird überprüft
    3|Approved (Genehmigt)
    4|Abgelehnt

## <a name="navigating-relationships"></a>Navigieren in Beziehungen

Für Beziehungen in Common Data Service für Apps ist es erforderlich, dass Sie in Power BI-Desktop mithilfe eines GUID-Felds eine Beziehung zwischen zwei Entitäten erstellen. Dabei handelt es sich um einen vom System generierten eindeutigen Bezeichner, der sicherstellt, dass Beziehungen für die Datensätze erstellt werden, bei denen Mehrdeutigkeiten oder Duplizierungen mit anderen Feldern vorhanden sein können. [Hier](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships) finden Sie weitere Informationen zum Verwalten von Beziehungen in Power BI Desktop.

Einige Beziehungen werden automatisch erstellt. Sie können diese beim Erstellen Ihres Berichts jedoch überprüfen und sicherstellen, dass die richtigen Beziehungen erstellt wurden:

* Das Nachschlagefeld der Entität enthält die GUID des Datensatzes in der verknüpften Entität.
* Die verknüpfte Entität enthält ein Feld mit dem Format „[EntityName]id“, das die GUID, z.B. „Accountid“ oder „MyCustomEntityid“ enthält.
* Wenn Sie das Feature „Beziehungen verwalten“ von Power BI Desktop verwenden, sollten Sie eine neue Beziehung zwischen dem Nachschlagefeld und dem ID-Feld der verknüpften Entität erstellen.


## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Feldern in einer Entität](data-platform-manage-fields.md)
* [Definieren von Beziehungen zwischen Entitäten](data-platform-entity-lookup.md)


