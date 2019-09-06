---
title: getSelectedResults (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getselectedresults-client-api-reference"></a>getSelectedResults (Client-API-Referenz)


Verwenden Sie diese Methode, um das aktuell ausgewählte Ergebnis des Suchsteuerelements abzurufen. Das aktuell ausgewählte Ergebnis stellt außerdem das Ergebnis dar, das aktuell geöffnet ist. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
var kbSearchResult = kbSearchControl.getSelectedResults();
```

## <a name="return-value"></a>Rückgabewert 

**KBSearchResult**. Das aktuell ausgewählte Ergebnis.

## <a name="kbsearchresult-properties"></a>KBSearchResult-Eigenschaften

| **Eigenschaft**        | **Typ** | **Beschreibung**  |
|---------------------|----------|------------------|
| **answer**          | String   | Das HTML-Markup, das den Inhalt des Artikels enthält. Diesen Inhalt können Sie an eine benutzerdefinierte Aktion übergeben, die ihn einer E-Mail beifügen könnte, die an den Kunden gesendet werden soll. |
| **articleId**       | String   | Die Artikel-ID, die als Alternativschlüssel verwendet wird. Sie können ihn verwenden, um zu überprüfen, ob dieser Artikel in Common Data Service bereits vorhanden ist.|
| **articleUid**      | String   | Die eindeutige Artikel-ID. Dieser Wert wird als Alternativschlüssel verwendet. Die ID ist erforderlich, um einen neuen Wissensdatenbank-Datensatz beim Zuordnen eines Artikels zu erstellen, falls noch nicht vorhanden. |
| **attachmentCount** | Nummer   | Anzahl der Anlagen im Artikel. |
| **createdOn**       | Date     | Das Datum, an dem der Artikel erstellt wurde. Dieser Wert entspricht der Zeitzone und dem Format des aktuellen Benutzers. Sie möchten ggf. das Alter des Artikels in der Geschäftslogik verwenden. |
| **expiredDate**     | Date     | Das Datum des Artikels ist abgelaufen bzw. wird ablaufen. Sie können dieses Datum mit den aktuellen Daten vergleichen, um zu bestimmen, ob der Artikel schon abgelaufen ist. Der Wert verwendet die Zeitzone und das Format des aktuellen Benutzers.|
| **folderHref**      | String   | Der Link zum Ordnerpfad des Artikels.|
| **href**            | String   | Der direkte Link zum Artikel.|
| **isAssociated**    | Boolean  | Gibt an, ob der Artikel mit dem übergeordneten Datensatz verknüpft ist. Sie können diesen Wert überprüfen, bevor Sie den Artikel dem aktuellen Datensatz mithilfe von Formularskripts oder in einem anderen Prozess, der von Formularskripts initiiert wird, zuordnen. |
| **lastModifiedOn**  | Date     | Datum, an dem der Artikel zuletzt geändert wurde. Dieser Wert entspricht der Zeitzone und dem Format des aktuellen Benutzers. |
| **publicUrl**       | String   | URL des Support-Portals für den Artikel. Wenn die Portal-URL-Option deaktiviert ist, ist dies leer. Verwenden Sie eine benutzerdefinierte Aktion, um dies in einem Link im Inhalt einer E-Mail beizufügen, die an einen Kunden gesendet werden soll. |
| **published**       | Boolean  | Gibt an, ob sich der Artikel im Veröffentlicht-Status befindet. **True**, wenn veröffentlicht, andernfalls **False**. Überprüfen Sie, ob der Artikel veröffentlicht wird, bevor Sie Informationen dazu an einen Kunden senden. |
| **question**        | String   | Der Titel des Artikels. Wenn Sie in einem Geschäftsprozess auf den Artikel verweisen werden, können Sie darauf über den Namen mithilfe dieses Werts verweisen.  |
| **rating**          | Nummer   | Die Bewertung des Artikels.  |
| **searchBlurb**     | String   | Ein kurzer Ausschnitt des Artikelinhalts, der die Bereiche mit den Suchabfrage-Treffern enthält. Verwenden Sie dies, um den Benutzern in der Suchliste eine Kurzübersicht über den Artikel zu geben und ihnen zu helfen, zu entscheiden, ob dies der Artikel ist, den sie suchen. |
| **serviceDeskUri**  | String   | Link zum Artikel. Nutzen Sie diesen Link, um den Artikel zu öffnen.   |
| **timesViewed**     | Nummer   | Die Anzahl der Male, die ein Artikel im Portal von Kunden angesehen wurde.  |