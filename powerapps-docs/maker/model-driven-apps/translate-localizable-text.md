---
title: Übersetzen von lokalisierbarem Text für modellgetriebene Anwendungen | MicrosoftDocs
description: Erfahren Sie, wie Sie lokalisierbaren Text in mehrere Sprachen übersetzen lassen können.
ms.custom: ''
ms.date: 03/05/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 3d77d149-819b-45e6-8e70-1fbe54d5c153
caps.latest.revision: 19
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d0f8f154d4a2cb92a062b7ce37f9e6a0b17e9b6b
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136387"
---
# <a name="translate-localizable-text-for-model-driven-apps"></a>Übersetzen von lokalisierbarem Text für modellgesteuerte Anwendungen

Wenn Sie benutzerdefinierte Entitäten oder Feldtexte wie Feldbeschriftungen oder Dropdown-Listenwerte haben, können Sie den Benutzern in Ihrer Umgebung, die nicht mit der Ausgangssprache Ihrer Umgebungsversion arbeiten, diesen benutzerdefinierten Text in ihren bevorzugten Sprachen zur Verfügung stellen. 

Dieser Prozess umfasst die folgenden Schritte:
1. Andere Sprachen für Ihre Umgebung aktivieren
2. Exportieren des lokalisierbaren Textes
3. Den lokalisierbaren Text übersetzen lassen
4. Import des lokalisierten Textes

## <a name="enable-other-languages-for-your-environment"></a>Andere Sprachen für Ihre Umgebung aktivieren

Wenn Sie die Sprachen für Ihre Umgebung noch nicht aktiviert haben, führen Sie die unter [Aktivieren der Sprache](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages) beschriebenen Schritte aus, um sie zu aktivieren.

> [!IMPORTANT]
> Die Aktivierung jeder einzelnen Sprache kann einige Minuten dauern. Während dieser Zeit können andere Benutzer der Umgebung Ihre App möglicherweise nicht nutzen. Sie sollten Sprachen zu einem Zeitpunkt aktivieren, der für die Benutzer am wenigsten störend ist.

> [!TIP]
> Während Sie die Sprachen aktivieren, beachten Sie die für jede Sprache verwendeten LCID-Werte. Dieser Wert stellt die Sprache in den exportierten Daten für den lokalisierbaren Text dar. Sprachcodes sind vierstellige oder fünfstellige Gebietsschema-IDs. Gültige Gebietsschema-ID-Werte finden Sie unter [Gebietsschema-ID-Diagramm (LCID)](https://go.microsoft.com/fwlink/?LinkId=122128).

## <a name="export-the-localizable-text"></a>Exportieren des lokalisierbaren Textes

Der Umfang des zu exportierenden lokalisierbaren Textes ist die nicht verwaltete Lösung, die den lokalisierbaren Text enthält.

<!-- [!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)] -->

1. Wählen Sie im Power Apps-Portal die Option **Lösungen** aus.

2. Wählen Sie in der Liste **Alle Lösungen** die nicht verwaltete Lösung aus, die den gewünschten lokalisierbaren Text enthält.

3. Wählen Sie in der Menüleiste die Optionen **Übersetzungen** > **Übersetzungen exportieren** aus. 

    > [!div class="mx-imgBorder"] 
    > ![Übersetzungen exportieren](media/export-localizable-text.png "Exportieren von Übersetzungen")

    Es könnte folgende Warnung angezeigt werden:
    > Das Exportieren angepasster Beschriftungen zur Übersetzung kann einige Minuten in Anspruch nehmen. Klicken Sie nicht erneut auf den Exportlink, bevor der erste Exportvorgang abgeschlossen ist. Möchten Sie den Exportvorgang jetzt wirklich ausführen?
    
    > Klicken Sie auf **OK**, wenn Sie den Vorgang fortsetzen möchten.

Speichern Sie nach Abschluss des Exports die ZIP-Datei für die Übersetzungen. Die Datei heißt zum Beispiel `CrmTranslations_{0}_{1}.zip`, wobei `{0}` der eindeutige Name der Lösung und `{1}` die Versionsnummer der Lösung ist.

## <a name="get-the-localizable-text-translated"></a>Den lokalisierbaren Text übersetzen lassen

Sie können diese Datei an einen Sprachexperten, an eine Übersetzungsagentur oder an ein Lokalisierungsunternehmen senden.

Wenn Sie den Text selbst übersetzen können, oder wenn Sie nur das Format sehen wollen, können Sie die Zip-Datei, die Sie exportiert haben, extrahieren, und Sie werden sehen, dass sie zwei XML-Dateien enthält. 
 - `[Content_Types].xml`
 - `CrmTranslations.xml`

Sie können die CrmTranslations.xml-Datei mit Microsoft Office Excel öffnen.

> [!TIP]
> Sofern Sie normalerweise XML-Dateien mit Excel öffnen, kann es einfacher sein, zunächst Excel zu öffnen und dann die Datei durch Einfügen des Pfads der extrahierten CrmTranslations.xml-Datei zu öffnen.

> [!IMPORTANT]
> Stellen Sie sicher, dass Sie nicht das Dateiformat ändern. Wenn Sie die Datei in einem anderen Format speichern, können Sie sie nicht wieder importieren.

Wenn Sie die Daten in Excel anzeigen, sehen Sie sich die Registerkarte **Lokalisierte Beschriftungen** an.

![Exportierter Text für die Lokalisierung](media/localized-labels-tab-exported-languages.png "Exportierter Text für die Lokalisierung")

Alle benutzerdefinierten Entitäten oder Felder haben leere Zellen für den lokalisierbaren Text. Fügen Sie die lokalisierten Werte für diese Elemente hinzu.

> [!NOTE]
> Wenn Sie den Anzeigenamen oder die Beschreibung für eine Standard-Entität oder ein Entitätsfeld geändert haben, werden die lokalisierten Zeichenfolgen weiterhin die Übersetzungen für den ursprünglichen Wert wiedergeben. Diese sollten lokalisiert werden, um den neuen Wert widerzuspiegeln.

Die Registerkarte **Anzeigezeichenfolgen** enthält Text, der für andere UI-Elemente wie Menübandbefehle, Fehlermeldungen und Formularbeschriftungen angezeigt wird.

### <a name="updating-localizable-text-in-the-base-language"></a>Aktualisieren des lokalisierbaren Texts in der Ausgangssprache

Wenn Sie den Anzeigenamen für eine Standard-Entität oder ein Entitätsfeld ändern, das in einer speziellen Nachricht enthalten ist, können Sie die Informationen auf der Registerkarte **Anzeigezeichenfolgen** aktualisieren, um den benutzerdefinierten Namen zu verwenden.

> [!TIP]
> Obwohl die Benutzeroberfläche, die zum Bearbeiten von System-Entitätsnachrichten verwendet wird, viele Verweise auf Entitätsnamen enthält, enthält sie nicht alle. Mit dieser Technik können Sie mehr finden. Weitere Informationen: [Bearbeiten von Systementitätenmeldungen](../common-data-service/edit-system-entity-messages.md)

Wenn Sie beispielsweise den Anzeigenamen für die Firmenentität auf *Unternehmen* ändern, suchen Sie in der Spalte Ausgangssprache in der Spalte  **Anzeigezeichenfolgen** nach den folgenden Übereinstimmungen: `account`, `accounts`, `Account` und `Accounts` ersetzen dann entsprechend `company`, `companies`, `Company` und `Companies`.

> [!IMPORTANT]
> Führen Sie dazu kein allgemeines Suchen/Ersetzen in der Datei durch. Sie sollten darauf achten, dass sich der übereinstimmende Text tatsächlich auf die Namen bezieht, die Sie geändert haben.


## <a name="import-the-localized-text"></a>Import des lokalisierten Textes
Um den Text zu importieren, müssen die Dateien komprimiert und in das System importiert werden.

### <a name="compress-the-files"></a>Komprimieren Sie die Dateien

Nachdem Änderungen an der `CrmTranslations.xml`-Datei vorgenommen wurden, müssen Sie die Datei zusammen mit der `[Content_Types].xml`-Datei in das Zip-Format komprimieren. Wählen Sie einfach *beide Dateien* aus und klicken Sie dann mit der rechten Maustaste, um das Kontextmenü zu öffnen. Wählen Sie im Kontextmenü **Senden an** > **Komprimierter (gezippter) Ordner**.

### <a name="import-the-files"></a>Importieren Sie die Dateien

Aus derselben nicht verwalteten Lösung, aus der Sie die Übersetzungen exportiert haben, wählen Sie im Menü **Übersetzungen** > **Übersetzungen importieren**. 

<!-- ![Import translations](media/import-translations.png) -->

> [!div class="mx-imgBorder"] 
> ![Ausgewählte Datei importieren](media/import-translated-text-dialog.png "Importieren von lokalisiertem Text")

Wählen Sie die Datei, die den komprimierten übersetzten Text enthält und wählen Sie **Import**.

Nachdem der übersetzte Text importiert wurde, sollten Sie alle Anpassungen veröffentlichen, um die Änderungen in Ihrer(n) App(s) zu sehen.

## <a name="community-tools"></a>Community-Tools

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) ist ein Werkzeug, das die XrmToolBox-Community entwickelt hat. Verwenden Sie den einfachen Übersetzer, um Übersetzungen mit kontextbezogenen Informationen zu exportieren und zu importieren. 

> [!NOTE]
> Die Community-Tools werden von Microsoft nicht unterstützt.
> Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).


## <a name="next-steps"></a>Nächste Schritte
[Regions- und Sprachoptionen für Ihre Organisation](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)<br />
[Bearbeiten von Systementitätenmeldungen](../common-data-service/edit-system-entity-messages.md)
