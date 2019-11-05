---
title: Suchen in Datei Anlagen Inhalt in einem Portal | MicrosoftDocs
description: Erfahren Sie, wie Sie das Portal für die Suche in Datei Anlagen Inhalt in einem Portal konfigurieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 52d7701ac84072c84886ea86969f28809d0e7960
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551644"
---
# <a name="search-within-file-attachment-content"></a>In Datei Anlagen Inhalt suchen

Mithilfe der Anlage "Notizen" können Sie herunterladbare Dateien in Knowledge Base-Artikeln einschließen. Sie können Webdateien auch verwenden, um eine FAQ-Seite mit herunter ladbarem Inhalt zu erstellen.

Sie können Ihr Portal so konfigurieren, dass Portalbenutzer innerhalb des Anlagen Inhalts der Knowledge Base-Artikel suchen können. Dadurch können Benutzer die gesuchten Informationen finden.

In Knowledge Base-Artikeln werden alle Notizen Anhänge mit dem definierten Präfix indiziert. In Webdateien werden die neuesten Notizen Anhänge indiziert.

Um die Anhänge zu indizieren, müssen Sie die folgenden Standorteinstellungen erstellen und deren Wert auf " **true**" festlegen:

|Standort Einstellung|Beschreibung|
|------------|-----------|
|Such-/indexnotesanlagen|Gibt an, ob der Inhalt von Notizen Anlagen in Knowledge Base-Artikeln und-Webdateien indiziert werden soll. Standardmäßig ist der Wert auf **false**festgelegt.|
|Knowledgemanagement/displaynotes|Gibt an, ob Anlagen von Knowledge Base-Artikeln indiziert werden sollen. Standardmäßig ist der Wert auf **false**festgelegt.|
|||

> [!NOTE]
> Nur die Dateien, die an Wissens Daten Bank Artikel angefügt sind, können durchsucht werden. Die Dateien, die an Webdateien angefügt sind, können nicht durchsucht werden.

Wenn Sie nach einem Begriff suchen, umfassen die Suchergebnisse auch Anhänge. Wenn der Suchbegriff mit einer Notizen Anlage übereinstimmt, wird auch der Link zum entsprechenden Knowledge Base-Artikel bereitgestellt. Um herunterladbare Anlagen anzuzeigen, wählen Sie im linken Bereich unter **Datensatz-Typ** die Option **Downloads** aus. Um die Bezeichnung " **Downloads** " zu ändern, bearbeiten Sie den Code Ausschnitt für die Suche/Facetten/Downloads. Standardmäßig ist der Wert auf **Downloads**festgelegt.

![Anhang herunterladen](../media/search-attachment-content.png "Anhang herunterladen") 

> [!NOTE]
> - Um diese Funktion verwenden zu können, müssen Sie die [relevanzsuche aktivieren](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization). Weitere Informationen: [relevanzsuche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>Aktualisieren von Portal Konfigurationen

Wenn Sie bereits über ein Portal verfügen, bevor Sie 2018 und das Portal auf die neueste Version aktualisiert haben, müssen Sie die folgenden Konfigurationen verwenden, um die gleiche Benutzer Leistung wie bei einer neuen Portal Installation zu erhalten.

**Inhalts Ausschnitte**

Um die in den Suchergebnissen angezeigte Bezeichnung für Anmerkung-und Webdatei Downloads zu ändern, erstellen Sie eine Suche/Facette/Downloads für Inhalts Ausschnitte, und legen Sie dann ihren Wert nach Bedarf fest. Der Standardwert ist **Downloads**.

**Webdateien**

Der Inhalt von Datei Anlagen, die Webdateien zugeordnet sind, kann jetzt indiziert werden. Sie können vorhandene Webdateien für CSS-Dateien und Bilddateien (z. b. Bootstrap. min. CSS, Theme. CSS und HomeHero. jpg) aktualisieren, damit Sie von der Suche ausgeschlossen werden. 

1. Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md) , und navigieren Sie zu **Portale** > **Webdateien**.
2. Öffnen Sie die Datei, die von der Suche ausgeschlossen werden soll.
3. Wählen Sie unter **Verschiedenes**die Option **Ja** im Feld **aus Suche ausschließen aus** .

**Webvorlagen**

Die Webvorlage für die facetesultsuchergebnisvorlage wird überarbeitet, um Dateien anzuzeigen, die mit Knowledge Base-Artikeln als primäre Suchergebnis Elemente verknüpft sind. Sie müssen die Webvorlage für Facetten Suchergebnis Vorlagen auf folgende Quelle aktualisieren:

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id=search-view-results type=text/x-handlebars-template>
   {{#if items}}
    <div class=page-header>
     <h3>{%endraw%}{{openTag}} stringFormat {{ resx.Search_Results_Format_String }} firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
      <em class=querytext>{{{query}}}</em>
      {{#if isResetVisible}}
       <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
      {{/if}}
     </h3>
    </div>
   <ul>
    {{#each items}}
     <li>
      <h3><a title={{title}} href={{url}}>{{#if parent}}<span class=glyphicon glyphicon-file pull-left text-muted aria-hidden=true></span>{{/if}}{{title}}</a></h3>
      <p class=fragment>{{{fragment}}}</p>
      {{#if parent}}
       <p class=small related-article>{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title={{parent.title}} href={{parent.absoluteUrl}}>{{parent.title}}</a></p>
      {{/if}}
      <ul class=note-group small list-unstyled>
       {{#if relatedNotes}}
        {{#each relatedNotes}}
         <li class=note-item>
         {{#if isImage}}
          <a target=_blank title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{else}}
          <a title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{/if}}
         <p class=fragment text-muted>{{{fragment}}}</p>
         </li>
        {{/each}}
        {{/if}}
      </ul>
     </li>
    {{/each}}
   </ul>
   {{else}}
    <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class=querytext>{{{query}}}</em>
     {{#if isResetVisible}}
      <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
     {{/if}}
    </h2>
   {{/if}}
  </script>
{%endraw%}
```

**Website Einstellungen**

Sie müssen der Such-/Abfrage-Site-Einstellung `\_logicalname:annotation~0.9^0.25` Wert hinzufügen. Nachdem der Wert hinzugefügt wurde, sollte er wie folgt lauten:
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

Wenn Sie die Facetten so konfigurieren möchten, dass Sie Anmerkungen in Zusammenhang mit Knowledge Base-Artikeln und Webdateien in einem einzelnen Facetten gruppieren, bearbeiten Sie den Namen der Website Einstellung Search/recordtypefacetsentities, und fügen Sie `;Downloads:annotation,adx_webfile` an seinen Wert an.

Um zu ermöglichen, dass mit Wissens Daten Bank Artikeln verknüpfte Anlagen im Portal und in den Suchergebnissen angezeigt werden, bearbeiten Sie die Website Einstellung **knowledgemanagement/displaynotes** , und legen Sie Ihren Wert auf **true**fest. Die Website Einstellung " **knowledgemanagement/notesfilter** " enthält einen Präfix Wert, der dem Feld "Hinweis Text" in Notes vorangestellt werden muss. im Portal werden nur Notizen mit dem angegebenen Präfix Wert angezeigt. Standardmäßig ist der Wert \*Web\*, aber Sie können ihn über die Website Einstellung ändern.

Zum Aktivieren der Indizierung von Datei Anlagen, die Notizen zugeordnet sind, erstellen Sie die **Such-/indexnotesattachments** -Website Einstellung, und legen Sie Ihren Wert auf **true**fest.
