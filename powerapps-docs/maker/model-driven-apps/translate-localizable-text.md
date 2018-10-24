---
title: Übersetzen des lokalisierbaren Textes für modellgesteuerte Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie lokalisierbaren Text zur Unterstützung mehrerer Sprachen übersetzen können.
ms.custom: ''
ms.date: 06/03/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: e2e305313f3b86be2ea410f6668676b56aa79d95
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39682706"
---
# <a name="translate-localizable-text-for-model-driven-apps"></a>Übersetzen des lokalisierbaren Textes für modellgesteuerte Apps

Wenn Sie eine Entität oder einen Feldtext wie Feldbezeichnungen oder Dropdownlistenwerte, angepasst haben, können Sie Benutzern in Ihrer Umgebung, die nicht mit der Basissprachversion Ihrer Umgebung arbeiten, diesen angepassten Text in der bevorzugten Sprache bereitstellen. 

Der Prozess umfasst die folgenden Schritte:
1. Aktivieren der anderen Sprachen für Ihre Umgebung
2. Exportieren des lokalisierbaren Textes
3. Initiieren der Übersetzung des lokalisierbaren Textes
4. Importieren des lokalisierten Textes

## <a name="enable-other-languages-for-your-environment"></a>Aktivieren der anderen Sprachen für Ihre Umgebung

Wenn Sie die Sprachen für Ihre Umgebung noch nicht aktiviert haben, führen Sie die Schritte unter [Regions- und Sprachoptionen für Ihre Organisation](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages) durch, um sie zu aktivieren.

> [!IMPORTANT]
> Es kann einige Minuten dauern, bis jede Sprache aktiviert ist. In diesem Zeitraum können andere Benutzer der Umgebung womöglich nicht Ihre App verwenden. Sie sollten Sprachen in Zeiten aktivieren, in denen Benutzer möglichst nicht gestört werden.

> [!TIP]
> Beachten Sie bei der Aktivierung der Sprachen die LCID-Werte für die einzelnen Sprachen. Dieser Wert stellt die Sprache in den exportierten Daten für den lokalisierbaren Text dar. Sprachcodes sind vier- oder fünfstellige Gebietsschema-IDs. Gültige Gebietsschema-ID-Werte finden Sie unter [Gebietsschema-ID-Werte von Microsoft](http://go.microsoft.com/fwlink/?LinkId=122128).

## <a name="export-the-localizable-text"></a>Exportieren des lokalisierbaren Textes

Der Bereich des lokalisierbaren Textes, der exportiert wird, ist die nicht verwaltete Lösung, die den lokalisierbaren Text enthält. Dies kann nur mithilfe des Lösungs-Explorers erfolgen.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Öffnen Sie die nicht verwaltete Lösung, die den lokalisierbaren Text in der Menüleiste enthält, und wählen Sie **Übersetzungen** > **Übersetzungen exportieren** aus. 

![Exportieren von Übersetzungen](media/export-localizable-text.png)

Daraufhin sollte eine Warnung angezeigt werden, die Folgendes besagt:
> Das Exportieren angepasster Beschriftungen zur Übersetzung kann einige Minuten in Anspruch nehmen. Klicken Sie erst erneut auf den Exportlink, wenn der erste Export abgeschlossen ist. Sind Sie sicher, dass Sie den Export jetzt ausführen möchten? 

Klicken Sie auf **OK**, wenn Sie den Vorgang fortsetzen möchten.

Wenn der Export abgeschlossen ist, finden Sie eine Datei mit einem Namen wie `CrmTranslations_{0}_{1}.zip` in Ihrem Ordner „Downloads“. `{0}` steht hierbei für den eindeutigen Name der Lösung und `{1}` für die Versionsnummer der Lösung.

## <a name="get-the-localizable-text-translated"></a>Initiieren der Übersetzung des lokalisierbaren Textes

Sie können diese Datei an einen Linguistikexperten, eine Übersetzungsagentur oder eine Lokalisierungsfirma senden.

Wenn Sie Kenntnisse in der Übersetzung von Texten haben oder nur das Format sehen möchten, können Sie die exportierte ZIP-Datei extrahieren. Sie enthält zwei XML-Dateien. 
 - `[Content_Types].xml`
 - `CrmTranslations.xml`

Sie können die Datei „CrmTranslations.xml“ mit Microsoft Office Excel öffnen.

> [!TIP]
> Sofern Sie XML-Dateien standardmäßig mit Excel öffnen, ist es möglicherweise einfacher, Excel zu öffnen und dann die Datei durch Einfügen des Pfads in die extrahierte Datei „CrmTranslations.xml“ zu öffnen.

> [!IMPORTANT]
> Ändern Sie dabei auf keinen Fall das Dateiformat. Wenn Sie die Datei in einem anderen Format speichern, können Sie sie nicht wieder importieren.

Wenn Sie die Daten in Excel anzeigen, sehen Sie die Registerkarte **Lokalisierte Beschriftungen**.

![Exportierter Text für die Lokalisierung](media/localized-labels-tab-exported-languages.png)

Benutzerdefinierte Entitäten oder Felder müssen leere Zellen für den lokalisierbaren Text enthalten. Fügen Sie die lokalisierten Werte für diese Elemente hinzu.

> [!NOTE]
> Wenn Sie den Anzeigenamen oder die Beschreibung für eine Standardentität oder ein Entitätsfeld geändert haben, stellen die lokalisierten Zeichenfolgen weiterhin die Übersetzungen für den ursprünglichen Wert dar. Diese sollten entsprechend des neuen Werts lokalisiert werden.

Die Registerkarte **Anzeigezeichenfolgen** enthält Text, der für andere Benutzeroberflächenelemente wie Menübandbefehle, Fehlermeldungen und Formularbeschriftungen angezeigt wird.

### <a name="updating-localizable-text-in-the-base-language"></a>Aktualisieren von lokalisierbarem Text in der Basissprache

Wenn Sie den Anzeigenamen für eine Standardentität oder ein Entitätsfeld ändern, das in der jeweiligen Meldung enthalten ist, können Sie die Informationen auf der Registerkarte **Anzeigezeichenfolgen** für die Verwendung des benutzerdefinierten Namens aktualisieren.

> [!TIP]
> Obwohl die Benutzeroberfläche, die für die Bearbeitung von Systementitätsmeldungen verfügbar ist, viele Verweise auf Entitätsnamen enthält, enthält sie nicht alle. Mit dieser Methode finden Sie eventuell weitere Namen. Mehr erfahren Sie unter [Bearbeiten von Systementitätsmeldungen](../common-data-service/edit-system-entity-messages.md).

Wenn Sie den Anzeigenamen für die Firmenentität z.B. in *Unternehmen* ändern, durchsuchen Sie die Basissprachenspalte unter **Anzeigezeichenfolgen** für die folgenden Treffer: `account`, `accounts`, `Account` und `Accounts`. Nehmen Sie dann die entsprechenden Ersetzungen durch `company`, `companies`, `Company` bzw. `Companies` vor.

> [!IMPORTANT]
> Verwenden Sie hierfür nicht die allgemeine Funktion zum Suchen/Ersetzen in der Datei. Sie sollten darauf achten, dass sich der übereinstimmende Text tatsächlich auf die Namen bezieht, die Sie geändert haben.


## <a name="import-the-localized-text"></a>Importieren des lokalisierten Textes
Für den Import des Textes müssen die Dateien komprimiert und in das System importiert werden.

### <a name="compress-the-files"></a>Komprimieren der Dateien

Nachdem Änderungen an der Datei `CrmTranslations.xml` vorgenommen wurden, müssen Sie die Datei zusammen mit der Datei `[Content_Types].xml` im ZIP-Format komprimieren. Wählen Sie einfach *beide Dateien* aus, und klicken Sie dann mit der rechten Maustaste auf diese, um das Kontextmenü zu öffnen. Klicken Sie im Kontextmenü auf **Senden an** > **Komprimierten (gezippten) Ordner**.

### <a name="import-the-files"></a>Importieren der Dateien

Klicken Sie in der gleichen nicht verwalteten Lösung, aus der Sie zuvor die Übersetzungen exportiert haben, im Menü auf **Übersetzungen** > **Übersetzungen importieren**. 

![Importieren von Übersetzungen](media/import-translations.png)

Wählen Sie die Datei mit dem komprimierten übersetzten Text und dann **Importieren** aus.

![Importieren einer ausgewählten Datei](media/import-translated-text-dialog.png)

Nach dem Import des übersetzten Textes sollten Sie alle Anpassungen veröffentlichen, um die Änderungen in Ihren Apps anzuzeigen.

## <a name="community-tools"></a>Communitytools

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) ist ein Tool, das von der XrmToolBox-Community entwickelt wurde. Verwenden Sie Easy Translator zum Exportieren und Importieren von Übersetzungen mit Kontextinformationen. 

> [!NOTE]
> Die Communitytools werden von Microsoft nicht unterstützt.
> Wenn Sie Fragen zum Tool haben, wenden Sie sich bitte an den Herausgeber. Weitere Informationen finden Sie unter [XrmToolBox](https://www.xrmtoolbox.com).


## <a name="next-steps"></a>Nächste Schritte
[Regions- und Sprachoptionen Optionen für Ihre Organisation](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-languages)<br />
[Bearbeiten von Systementitätsmeldungen](../common-data-service/edit-system-entity-messages.md)

