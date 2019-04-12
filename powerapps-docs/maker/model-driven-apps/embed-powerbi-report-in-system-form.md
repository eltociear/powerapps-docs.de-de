---
title: Einbetten eines Power BI-Berichts in ein modellgestütztes Systemformular | MicrosoftDocs
ms.custom: ''
ms.date: 03/05/2019
ms.reviewer: matp
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 1
author: prsi-msft
ms.author: prsi
manager: kvivek
tags:
  - Links to topic not migrated
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="embed-a-power-bi-report-in-a-model-driven-system-form"></a>Einbetten eines Power BI-Berichts in ein modellgestütztes Systemformular
Sie können Power BI-Berichte in modellgestützten Apps von PowerApps verwenden, um umfangreiche Berichterstellung und Analyse in Ihre Systemformulare einzubringen damit Ihre Benutzer mehr erzielen. Dadurch erhalten Sie die Möglichkeit, Daten über Systeme hinweg freizugeben und bis hin zum Kontext eines einzelnen Datensatzes anzupassen.
 
## <a name="prerequisites"></a>Voraussetzungen
Das Einbetten von Power BI-Inhalt ist eine optionale Funktion und auf allen Umgebung standardmäßig deaktiviert. Sie müssen sie aktivieren, bevor Sie Power BI-Inhalt einbetten können. Weitere Informationen: [Aktivieren von Power BI-Visualisierungen in der Organisation](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/use-power-bi?#enable--visualizations-in-the-organization).

Für diese Funktion muss eine Lösung exportiert, dann geändert werden, um den XML-Ausschnitt hinzuzufügen, und dann wieder zurück in die Umgebung importiert werden. Vergessen Sie nicht, die Änderungen nur über eine verwaltete Lösung in die Zielumgebung zu importieren. Siehe [Lösungen importieren, aktualisieren und exportieren](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions) für Anleitungen zur Installation eines Updates für eine vorhandene verwaltete Lösung.

## <a name="embed-without-contextual-filtering"></a>Einbetten ohne kontextbezogene Filterung
Sie können Ihr Power BI-Berichte und -Kacheln verwenden, indem Sie sie einfach einbetten, und Sie erhalten genau den gleichen Bericht. Hierzu werden sie nicht dem Kontext des aktuellen modellgestützten Formulars zugeführt, und daher erhalten Sie den gleichen Bericht oder die gleiche Kachel auf allen Datensätzen der Entität. Beispielsweise zeigt der folgende Bericht den geografischen Standort aller Firmen gleichzeitig an, und ist nützlich, um Zusammenfassungsinformationen anzuzeigen.

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-unfiltered.png "Embed-powerbi-report-in-system-form-unfiltered")

Sie können einen Abschnitt in Ihren Systemformularen einbetten, der Power BI-Berichte und Kacheln hostet, indem Sie folgenden Codeausschnitt innerhalb des `<sections>`-Blocks der Formular-XML hinzufügen. Anschließend importieren Sie die Lösung in die Zielumgebung. 

```xml
<section id="{d411658c-7450-e1e3-bc80-07021a04bcc2}" locklevel="0" showlabel="true" IsUserDefined="0" name="tab_4_section_1" labelwidth="115" columns="1" layout="varwidth" showbar="false">
    <labels>
        <label languagecode="1033" description="Unfiltered Power BI embedding demo"/>
    </labels>
    <rows>
        <row>
            <cell id="{7d18b61c-c588-136c-aee7-03e5e74a09a1}" showlabel="true" rowspan="20" colspan="1" auto="false">
                <labels>
                    <label languagecode="1033" description="Accounts (Parent Account)"/>
                </labels>
                <control id="unfilteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
                    <parameters>
                        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
                        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
                        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
                    </parameters>
                </control>
            </cell>
        </row>
        <row/>
    </rows>
</section>
```
> [!IMPORTANT]
> Vergewissern Sie sich, dass Sie das Steuerelement `classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}"` wie im XML-Beispiel angegeben verwenden.

 Diese Tabelle beschreibt die im vorherigen Beispiel festgelegten Eigenschaften.

|                                                 Eigenschaft                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIGroupId**                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Die Id des Power BI-Arbeitsbereichs. Der Standardarbeitsbereich des Benutzers ist immer 00000000-0000-0000-0000-000000000000. Sie können die ID eines beliebigen Arbeitsbereichs überprüfen, indem Sie sich dessen URL ansehen. Zum Beispiel: https://xyz.powerbi.com/groups/0ddbe381-256d-44bc-93de-34e47f3d9ab4/.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                               **PowerBIReportId**                                |                             Die ID des Power BI-Berichts. Ersetzen Sie diese durch den Bericht, den Sie einbetten möchten. Sie können die ID eines beliebigen Berichts überprüfen, indem Sie sich dessen URL ansehen. Zum Beispiel: https://xyz.powerbi.com/groups/me/reports/544c4162-6773-4944-900c-abfd075f6081.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                                       **TileUrl**                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Die URL des Power BI-Berichts oder der Kachel, den bzw. die Sie einbetten möchten. Stellen Sie sicher, dass Sie den richtigen Power BI-Instanznamen (ersetzen Sie msit.powerbi.com durch Ihren eigenen) und die richtige Berichts-ID (ersetzen Sie reportId=544c4162-6773-4944-900c-abfd075f6081 durch Ihre eigene) verwenden. Zum Beispiel: https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

## <a name="embed-with-contextual-filtering"></a>Einbetten mit kontextbezogener Filterung
Sie können die Power BI-Berichte und Kacheln sinnvoller machen, indem Sie die kontextbezogenen Filter auf das aktuelle Modellgesteuerte Formular anwenden, damit der Bericht bzw. die Kachel anhand der Attribute des aktuellen Datensatzes gefiltert wird. Beispielsweise zeigt der folgende Bericht den geografischen Standort einer Firma durch Filterung des Power BI-Berichts mithilfe des Firmennamens. Damit können auf einem einzelnen Bericht kontextbezogene Informationen für alle Datensätze der Entität angezeigt werden.

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-filtered.png "Embed-powerbi-report-in-system-form-filtered")

Die Filterung wird durchgeführt, indem ein `<PowerBIFilter>`-Element in den `<parameter>`-Block hinzufügt wird, wie hier dargestellt. Sie können ein beliebiges Attribut der Entität das Formulars verwenden, um den Filterausdruck zu erstellen. Weitere Informationen: [Erstellen von Filtern](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters) zur Information über die Erstellung eigener Filter.
    
```xml
<control id="filteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
    <parameters>
        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
        <PowerBIFilter>{"Filter": "[{\"$schema\":\"basic\",\"target\":{\"table\":\"My Active Accounts\",\"column\":\"Account Name\"},\"operator\":\"In\",\"values\":[$a],\"filterType\":1}]", "Alias": {"$a": "name"</PowerBIFilter>
    </parameters>
</control>
```

Beachten Sie, dass dafür dasselbe Steuerelement wie beim Einbetten des ungefilterten Berichts verwendet wird, und dass die ID der Steuerelementklasse daher unverändert bleibt. 

Diese Tabelle beschreibt alle zusätzlichen Eigenschaften, die im vorherigen Beispiel festgelegt wurden.

|                                                 Eigenschaft                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIFilter**                          |        Der Filterausdruck, der den Kontextbezug des Power BI-Berichts bietet, indem die Formularattribute als Parameter übergeben werden. Um die Lesbarkeit zu steigern, wird der Filter wie hier gezeigt erstellt.    |

    {
            "Filter": "[{
                    \"$schema\":\"basic\",
                    \"target\":{
                            \"table\":\"My Active Accounts\",
                            \"column\":\"Account Name\"
                    },
                    \"operator\":\"In\",
                    \"values\":[$a, $b],
                    \"filterType\":1
            }]",
            "Alias": {
                    "$a": "firstname",
                    "$b":"lastname"
            }
    }

Der Zielanteil des vorherigen Ausdrucks identifiziert die Tabelle und die und die Spalte, auf die der Filter angewendet wird. Der Operator identifiziert die Logik, und die Werte identifizieren die Daten, die von der modellgesteuerten PowerApps-App übergeben werden. Für eine generelle Parameterisierung werden die Werte durch Verwendung von Alias erstellt. Im letzten Ausdruck werden die Werte von **Vorname** und **Nachname** einer Firma übergeben, und einer davon wird in der Spalte **Firmenname** im Power BI-Bericht gesucht. Beachten Sie, dass **Vorname** und **Nachname** die eindeutigen Namen von Attributen der Firmenentität sind, deren Wert hier übergeben wird. 

Sie können auch komplexere Filterausdrücke erstellen, indem Sie sich Beispiele für das [Erstellen von Filtern](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters) ansehen und die entsprechenden Werte für $schema und filterType zur Verfügung stellen. Stellen Sie sicher, jedes Literal im Filterteil mit *\"* zu umgeben, damit das JSON ordnungsgemäß generiert wird.

## <a name="known-issues-and-limitations"></a>Bekannte Probleme und Einschränkungen
1. Diese Integration ist nur im Client der einheitlichen Oberfläche, auf unterstützten Webbrowsern und mobilen Geräten verfügbar.
2. Wenn Sie dieses Formular im PowerApps-Formular-Designer öffnen, wird das Steuerelement nicht auf eine sinnvolle Weise angezeigt. Dies geschieht, weil das Steuerelement nicht außerhalb des Formular-Designers angepasst wird.
3. Benutzer werden in Power BI automatisch mit ihrem PowerApps-Benutzernamen und -Kennwort authentifiziert. Wenn kein Power BI-Konto mit passenden Anmeldeinformationen vorhanden ist, wird eine Anmeldeaufforderung angezeigt, wie hier dargestellt. 

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-1.png "Embed-powerbi-report-in-system-form-auth-1")

4. Es werden keine Daten angezeigt, wenn ein falsches Konto zum Anmelden in Power BI verwendet wird. Um sich mit den richtigen Anmeldeinformationen anzumelden, melden Sie sich ab und wieder an.

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-2.png "Embed-powerbi-report-in-system-form-auth-2")

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-3.png "Embed-powerbi-report-in-system-form-auth-3")

5. Die Ansicht der Berichtsdaten, die in PowerApps angezeigt wird, ist dieselbe, wie die in Power BI, und die angezeigten Daten werden nicht durch Sicherheitsrollen und Berechtigungen von PowerApps beeinflusst. Daher werden sind die Daten im Wesentlichen identisch zu dem, was der Ersteller des Power BI-Datensatzes sehen würde. Um Einschränkungen zum Datenzugriff anzuwenden, die denen von PowerApps-Sicherheitsrollen und -Teams gleichen, verwenden Sie [Sicherheit auf Zeilenebene (RLS) bei Power BI](https://docs.microsoft.com/en-us/power-bi/service-admin-rls).
6. Wenn das Formular den Power BI-Bericht nach dem Import der Lösung und der Veröffentlichung von Anpassungen nicht anzeigt, öffnen Sie ihn im modellgesteuerten Formular-Editor und speichern Sie ihn, damit das Formular-JSON erneut erstellt wird.


### <a name="see-also"></a>Siehe auch

[Einbetten eines Power BI-Dashboards in ein persönliches modellgesteuertes PowerApps-Dashboard](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard)

[Verwenden von Power BI mit Dynamics 365 for Customer Engagement](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/use-power-bi)

[Lösungen importieren, aktualisieren und exportieren](../common-data-service/import-update-export-solutions.md)
