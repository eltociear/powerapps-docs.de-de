---
title: Suche innerhalb des Inhalts von Dateianhängen in einem Portal | MicrosoftDocs
description: Erfahren Sie, wie Sie Ihr Portal so konfigurieren, dass es innerhalb der Inhalte von Dateianhängen in einem Portal sucht.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760442"
---
# <a name="search-within-file-attachment-content"></a>Suche im Dateianhangsinhalt

Sie können den Anhang der Notizen verwenden, um herunterladbare Dateien in Artikel der Wissensdatenbank aufzunehmen. Sie können auch Webdateien verwenden, um eine FAQ-Seite mit downloadbarem Inhalt zu erstellen.

Sie können Ihr Portal so konfigurieren, dass Portalbenutzer innerhalb des Anhangsinhalts von Wissensdatenbankartikeln suchen können. Dies erleichtert es Benutzern, die Informationen zu finden, nach denen sie suchen.

In Wissensdatenbankartikeln werden alle Notizanhänge mit dem definierten Präfix indiziert. In Webdateien werden die aktuellsten Notizenanhänge indiziert.

Um die Anhänge zu indizieren, müssen Sie die folgenden Website-Einstellungen erstellen und ihren Wert auf **True** festlegen:

|Website-Einstellung|Beschreibung|
|------------|-----------|
|Suchen/IndexNotesAttachments|Gibt an, ob der Inhalt der Notizenanhänge in Wissensdatenbankartikeln sowie in Webdateien indiziert werden soll. Standardmäßig ist dies auf **False** festgelegt.|
|KnowledgeManagement/DisplayNotes|Gibt an, ob Anhänge von Wissensdatenbankartikeln indiziert werden sollen. Standardmäßig ist dies auf **False** festgelegt.|
|||

> [!NOTE]
> Nur die Dateien, die an Wissensartikeln angefügt werden, können durchsucht werden. Die Dateien, die an Webdateien angefügt werden, sind nicht durchsuchbar.

Wenn Sie nach einem Begriff suchen, schließen die Suchergebnisse auch Anhänge mit ein. Wenn der Suchbegriff mit einem Notizenanhang übereinstimmt, wird der Link zum entsprechenden Wissensdatenbankartikel ebenfalls angegeben. Um die downloadbaren Anhänge anzuzeigen, wählen Sie **Downloads** unter **Datensatztyp** im linken Bereich aus. Um die Beschriftung **Downloads** zu ändern, bearbeiten Sie den Inhaltsausschnitt Suche/Facette/Downloads. Der Wert ist standardmäßig auf **Downloads** festgelegt.

![Anlage herunterladen](../media/search-attachment-content.png "Anlage herunterladen") 

> [!NOTE]
> - Um diese Funktionalität nutzen zu können, müssen Sie [die Relevanzsuche aktivieren](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization). Weitere Informationen [Relevanzsuche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>Portalkonfigurationen aktualisieren

Wenn Sie bereits ein Portal vor April 2018 haben und Ihr Portal auf die aktuelle Version aktualisiert haben, müssen Sie die folgenden Konfigurationen verwenden, um dieselbe Benutzererfahrung zu haben, wie bei eine neuen Portalinstallation.

**Inhaltsausschnitte**

Um die in den Suchergebnissen für Anmerkung und Webdateidownloads angezeigte Beschriftung zu ändern, erstellen Sie einen Inhaltsausschnitt „Suche/Facette/Downloads”, und legen Sie dessen Wert dann als erforderlich fest. Der Standardwert ist **Downloads**.

**Webdateien**

Der Inhalt von Dateianhängen, die Webdateien zugeordnet sind, kann jetzt indiziert werden. Sie können vorhandene Webdateien so aktualisieren, dass CSS-Dateien und Bilddateien (beispielsweise bootstrap.min.css, theme.css und homehero.jpg) von der Suche ausgeschlossen sind. 

1. Öffnen Sie die [Portalverwaltungs-App](configure-portal.md) und navigieren Sie zu **Portale** > **Webdateien**.
2. Öffnen Sie die Datei, die von der Suche ausgeschlossen werden soll.
3. Wählen Sie unter **Verschiedenes** die Option **Ja** im Feld **Von der Suche ausschließen** aus.

**Webvorlagen**

Die Webvorlage „Facettierte Suche – Ergebnisvorlage” wird überarbeitet, sodass Dateien, die Wissensdatenbankartikeln zugeordnet sind, als primäre Suchergebniselemente mit einem zugehörigen Artikellink angezeigt werden. Sie müssen die Webvorlage „Facettierte Suche – Ergebnisvorlage” auf die folgende Quelle aktualisieren.

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

**Website-Einstellungen**

Sie müssen den Wert `\_logicalname:annotation~0.9^0.25` der Website-Einstellung „Suche/Abfrage” hinzufügen. Nach dem er hinzugefügt wurde, sollte der Wert folgendermaßen sein:
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

Um die Facets zu konfigurieren, damit Anmerkungen gruppiert werden, die Wissensdatenbankartikeln und Webdateien in einem einzelnen Facet zugeordnet sind, bearbeiten Sie den Website-Einstellungsname „Suche/RecordTypeFacetsEntities” und fügen Sie `;Downloads:annotation,adx_webfile` an dessen Wert an.

Um zuzulassen, dass Wissensdatenbankartikeln zugeordnete Anhänge im Portal und in den Suchergebnissen angezeigt werden, bearbeiten Sie die Website-Einstellung **KnowledgeManagement/DisplayNotes** und legen Sie deren Wert auf **True** fest. Die Website-Einstellung **KnowledgeManagement/NotesFilter** enthält einen Präfixwert, der dem Notizentextfeld bei Notizen vorangestellt werden muss. Nur Notizen mit dem angegebenen Präfixwert werden im Portal angezeigt. Der Standardwert ist \*WEB\*, aber Sie können ihn über die Website-Einstellung ändern.

Um die Indizierung von Dateianhängen zu aktivieren, die Notizen zugeordnet sind, erstellen Sie die Website-Einstellung **Search/IndexNotesAttachments**, und legen Sie deren Wert auf **True** fest.
