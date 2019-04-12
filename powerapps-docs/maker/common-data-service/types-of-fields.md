---
title: Felddatentypen im Common Data Service | MicrosoftDocs
description: 'Lernen Sie die verschiedenen Felddatentypen, die für Ihre Anwendung zur Verfügung stehen, kennen.'
keywords: ''
ms.date: 06/27/2018
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 734b4ffa-5543-4f88-8517-299589f433f7
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="types-of-fields"></a>Typen von Feldern

Die Namen der Typen hängen vom verwendeten Designer ab. [PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) verwendet eine Konvention, die die Art und Weise, wie die Daten formatiert werden, beinhaltet. Der Typ des Lösungsexplorers verwendet einen Namen, der mit einem Formatmodifikator auf den Datentyp der Datenbank ausgerichtet ist. Die folgende Tabelle enthält den entsprechenden `AttributeTypeDisplayName` API-Typ.

|Typ Portal Daten |Typ Lösungs-Explorer| API-Typ|
|--|--|--|
|**Große ganze Zahl**|**Zeitstempel**|`BigIntType`|
|**Währung**|**Währung**|`MoneyType`|
|**Kunde**|**Kunde**|`CustomerType`|
|**Datum und Uhrzeit**|**Datum und Uhrzeit**<br />*Datum- und Zeit* format|`DateTimeType`|
|**Nur Datum**|**Datum und Uhrzeit**<br />*Nur Datum*-Format|`DateTimeType`|
|**Dezimalzahl**|**Dezimalzahl**|`DecimalType`|
|**Dauer**|**Ganze Zahl**<br />*Dauer*-Format|`IntegerType`|
|**Email**|**Einzelne Textzeile**<br />*E-Mail*-Format|`StringType`|
|**Gleitkommazahl**|**Gleitkommazahl**|`DoubleType`|
|**Bild**|**Bild**|`ImageType`|
|**Sprache**|**Ganze Zahl**<br />*Sprache*-Format|`IntegerType`|
|**Suche**|**Suche**|`LookupType`|
|**Mehrfachauswahl-Optionssatz**|**MultiSelect-Optionssatz**|`MultiSelectPicklistType`|
|**Mehrzeiliger Text**|**Mehrere Textzeilen**|`MemoType`|
|**Optionssatz**|**Optionssatz**|`PicklistType`|
|**Besitzer**|**Besitzer**|`OwnerType`|
|**Telefonnummer**|**Einzelne Textzeile**<br />*Telefon*-Format|`StringType`|
|**Statusgrund**|**Statusgrund**|`StatusType`|
|**Status**|**Status**|`StateType`|
|**Textbereich**|**Einzelne Textzeile**<br />*Textbereich:*-Format|`StringType`|
|**Text**|**Einzelne Textzeile**<br />*Text*-Format|`StringType`|
|**Tickersymbol**|**Einzelne Textzeile**<br />Tickersymbol-Format|`StringType`|
|**Zeitzone**|**Ganze Zahl**<br />*Zeitzone*-Format|`IntegerType`|
|**Zwei Optionen**|**Zwei Optionen**|`BooleanType`|
|**Eindeutiger Bezeichner**|**Eindeutiger Bezeichner** oder **Primärschlüssel**|`UniqueidentifierType`|
|**URL**|**Einzelne Textzeile**<br />*URL*-Format.|`StringType`|
|**Ganze Zahl**|**Ganze Zahl**<br />*Kein*-Format|`IntegerType`|

Weitere Beschreibungen für jeden Typ, den Sie hinzufügen oder bearbeiten können, finden Sie im Thema des entsprechenden Designers:
 - [Erstellen und Bearbeiten von Feldern für Common Data Service mit PowerApps-Portal: Felddatentypen](create-edit-field-portal.md#field-data-types)
 - [Erstellen und Bearbeiten von Feldern für Common Data Service mit PowerApps-Lösungsexplorer: Felddatentypen](create-edit-field-solution-explorer.md#field-data-types)

Weitere Informationen darüber, wie Felddatentypen in der API definiert werden, finden Sie unter [Attributmetadaten](/powerapps/developer/common-data-service/entity-attribute-metadata)

## <a name="field-types-used-by-the-system"></a>Vom System verwendete Feldtypen

Einige Felder, die vom System verwendet werden, können nicht mithilfe des Designers hinzugefügt werden.

|Typ|Beschreibung|
|--|--|
|**Große ganze Zahl** oder **Zeitstempel**|Wird vom System verwendet, um eine Versionsnummer zu erfassen, um Updates für eine Entität zu verwalten.|
|**Kunde**|Ein Suchfeld, das Sie verwenden können, um einen Kunden anzugeben, der ein Konto oder ein Kontakt sein kann.<br />**Hinweis**: Dieses Attribut kann mithilfe des Lösungs-Explorer-Designers hinzugefügt werden.|
|**Besitzer**|Ein Systemsuchfeld, das auf den Benutzer oder das Team verweist, der/das einem im Besitz eines Benutzers oder Teams befindlichen Entitätsdatensatz zugeordnet ist.|
|**Statusgrund**|Ein Systemfeld mit Optionen, die weitere Details zum Statusfeld bereitstellen. Jede Option ist einer der verfügbaren Statusoptionen zugeordnet. Sie können die Optionen hinzufügen oder bearbeiten. <br /><br /> Sie können auch benutzerdefinierte Statusübergänge einschließen, um zu steuern, welche Statusoptionen bestimmten Entitäten zur Verfügung stehen. Weitere Informationen: [Festlegen von Statusgrundübergängen für benutzerdefinierte Entitäten](define-status-reason-transitions.md)|
|**Status**|Ein Systemfeld mit Optionen, die normalerweise einem aktiven und einem inaktiven Status entsprechen. Einige Systemattribute verfügen über zusätzliche Optionen, alle benutzerdefinierten Attribute haben jedoch nur die Statusoptionen **Aktiv** und **Inaktiv**.  |
|**Eindeutiger Bezeichner**|Ein Systemfeld speichert einen GUID-Wert (Globally Unique Identifier) für jeden Datensatz.|

  
## <a name="multiselect-option-set"></a>MultiSelect-Optionssatz

Sie können Formulare (Haupt-, Schnellerstellungs- und Schnellansichtsformular) und E-Mail-Vorlagen anpassen, indem Mehrfachauswahlfelder hinzugefügt werden. Beim Hinzufügen eines MultiSelect-Optionssatzfeldes können Sie mehrere Werte festlegen, die Benutzer auswählen können. Wenn Benutzer das Formular ausfüllen, können sie einen, mehrere oder alle Werte in einer Dropdownliste auswählen.

Angenommen, eine Organisation arbeitet in mehreren Bereichen oder in mehreren Ländern, dann können Sie mehrere Standorte oder Länder in das Feld „Arbeitsgebiet“ aufnehmen. Benutzer können einen oder mehrere Standorte aus der Liste verfügbarer Werte auswählen.

Der MultiSelect-Optionssatz ist nur verfügbar in den schreibgeschützten Rastern, in bearbeitbaren Rastern und Formularen. Er wird nicht unterstützt in: 
- Workflows, Aktionen, Dialoge, Roll-Ups, Diagramme und Berechnete Felder.
- Berichte, SLA und Routingregel.

Mehrfachauswahlfelder werden unterstützt in den folgenden Formulartypen:

|Formulartyp|Verfügbarkeit|
|--|--|
|**Turbo-Formular**|Ja|
|**Aktualisierungsformular**|Schreibgeschützt (Feld ist verfügbar, aber kann nicht bearbeitet werden)|
|**Altes Formular**|No|
|**Massenbearbeitungs-Formular**|No|

Sie können auch globale Optionssätze verwenden, die in der Organisation definiert werden, um Werte für die Multiselect-Optionssätze zu konfigurieren.


<a name="BKMK_UsingTheRightTypeOfNumber"></a>
  
## <a name="using-the-right-type-of-number"></a>Verwenden des richtigen Zahlentyps

Bei der Auswahl des richtigen Nummernfeldtyps sollte die Auswahl zwischen **Ganze Zahl** und **Währung** einfach sein. Die Wahl zwischen der **Fließkomma** und **Dezimalzahl** erfordert mehr Überlegungen.  
  
Dezimalstellen werden in der Datenbank genau wie angegeben gespeichert. Fließkommazahlen speichern eine sehr genaue Annäherung an den Wert. Warum eine sehr genaue Annäherung, wenn Sie stattdessen den exakten Wert haben können? Die Antwort ist, dass Sie dadurch eine unterschiedliche Systemleistung erhalten.  
  
Verwenden Sie Dezimalstellen, wenn Sie Berichte erstellen müssen, die sehr genaue Berechnungen enthalten, oder wenn Sie normalerweise Abfragen verwenden, die nach Werten suchen, die einem anderen Wert gleich oder nicht gleich sind.  
  
Verwenden Sie Fließkommazahlen, wenn Sie Daten speichern, die Brüche oder Werte repräsentieren, die Sie normalerweise mit den Operatoren "Größer als" oder "Kleiner als" hinsichtlich eines anderen Werts abrufen. In den meisten Fällen ist der Unterschied insignifikant. Sofern Sie nicht äußerst präzise Berechnungen benötigen, sollten Fließkommazahlen ausreichen.  
  
<a name="BKMK_UsingCurrencyFields"></a>
 
## <a name="using-currency-fields"></a>Verwenden von Währungsfeldern

Währungsfelder ermöglichen einer Organisation die Konfiguration mehrerer Währungen für Datensätze in der Organisation. Wenn Organisationen mehrere Währungen verwenden, möchten sie in der Regel in der Lage sein, Berechnungen, auszuführen, um Werte in ihrer Basiswährung zu ermitteln. Wenn Sie einer Entität, die keine weiteren Währungsfelder hat, ein Währungsfeld hinzufügen, werden zwei zusätzliche Felder hinzugefügt:  
  
- Ein Suchfeld mit der Bezeichnung **Währung**, das Sie auf jede für Ihre Organisation konfigurierte Basiswährung einstellen können. Sie können mehrere aktive Währungen für Ihre Organisation in **Einstellungen** > **Unternehmensmanagement** > **Währungen** konfigurieren. Dort können Sie die Währung und einen Wechselkurs in die Basiswährung angeben, die für Ihre Organisation festgelegt wurde. Wenn Sie mehrere aktive Währungen haben, können Sie dem Formular das Währungsfeld hinzufügen und Benutzern erlauben, anzugeben, welche Währung für Geldwerte in diesem Datensatz angewendet werden soll. Dadurch wird das Währungssymbol geändert, das für Währungsfelder im Formular angezeigt wird.  
  
  Benutzer können außerdem ihre persönlichen Optionen ändern, um eine Standardwährung für die von ihnen erstellten Datensätze festzulegen.
  
- Ein Dezimalfeld mit der Bezeichnung **Wechselkurs**, das den Wechselkurs für eine ausgewählte Währung für die Entität gegenüber der Basiswährung angibt. Wenn dieses Feld dem Formular hinzugefügt wird, können Benutzer den Wert anzeigen, ihn jedoch nicht bearbeiten. Der Wechselkurs wird mit der Währung gespeichert.  
  
Für jedes Währungsfeld, das Sie importieren, wird ein weiteres Währungsfeld mit dem Suffix `_Base` hinzugefügt. Dieses Feld speichert die Berechnung des Wertes des Währungsfelds, das Sie hinzugefügt haben, und der Basiswährung. Auch dieses Feld kann nicht bearbeitet werden, wenn es einem Formular hinzugefügt wird.  
  
Wenn Sie ein Währungsfeld konfigurieren, können Sie die Anzahl von Stellen auswählen. Es gibt drei Optionen, wie in der folgenden Tabelle veranschaulicht.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|Preisdezimalstellen|Dies ist eine Präzision für eine einzelne Organisation für Preise in **Einstellungen** > **Verwaltung** > **Systemeinstellungen** > **Registerkarte Allgemein**.|  
|Genauigkeit für die Angabe von Währungsbeträgen|Diese Option wendet die für die Währung in dem Datensatz definierte Präzision an.|  
|Spezifische Präzisionswerte|Diese Einstellungen ermöglichen eine bestimmte Präzision mit Werten zwischen 0 und 4 zu definieren.|  
  
<a name="BKMK_DifferentTypesOfLookups"></a> 
  
## <a name="different-types-of-lookups"></a>Verschiedene Suchtypen  

Wenn Sie ein neues Suchfeld erstellen, erstellen Sie eine neue n:1-Entitätsbeziehung zwischen der Entität, mit der Sie arbeiten, und dem für die Suche definierten **Zieldatensatztyp**. Es gibt weitere Konfigurationsoptionen für diese Beziehung, die unter [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md) beschrieben sind. Alle benutzerdefinierten Suchen erlauben jedoch nur die Referenz zu einem einzelnen Datensatz für einen Datensatztyp mit einem einzigen Ziel.  
  
Sie sollten jedoch wissen, dass sich nicht jede Suche so verhält. Es gibt, wie hier gezeigt, verschiedene Typen von Systemsuchen.  
  
|Suchtyp|Beschreibung|  
|-----------------|-----------------|  
|**Einfach**|Erlaubt eine einzelne Referenz zu einer bestimmten Entität. Alle benutzerdefinierten Suchen haben diesen Typ.|  
|**Kunde**|Erlaubt eine einzelne Referenz zu einem Konto- oder einem Kontaktdatensatz.|  
|**Besitzer**|Erlaubt eine einzelne Referenz zu einem Team- oder einem Benutzerdatensatz. Alle team- oder benutzereigenen Entitäten verfügen darüber.|  
|**PartyList**|Erlaubt mehrere Referenzen zu mehreren Entitäten. Diese Suchen finden sich in der E-Mail-Entität in den Feldern **An** und **Cc**. Sie werden auch in den Entitäten Telefon und Termin verwendet.|  
|**Betreff**|Erlaubt eine einzelne Referenz zu mehreren Entitäten. Diese Suchen finden sich in dem in Aktivitäten verwendeten relevanten Feld.|  

<a name="BKMK_ImageFields"></a>

## <a name="image-fields"></a>Bildfelder  

Verwenden Sie Bildfelder, um ein einzelnes Bild pro Datensatz in der Anwendung anzuzeigen. Jede Entität kann über ein Bildfeld verfügen. Sie können ein Bildfeld zu benutzerdefinierten Entitäten, jedoch nicht zu Standardentitäten hinzufügen. Einige Standardobjekte haben Bildfelder definiert.
  
Selbst wenn eine Entität ein Bildfeld hat, erfordert die Anzeige dieses Bildes in eine modellgesteuerten App einen weiteren Schritt. In der Entitätsdefinition sind die Feldwerte für das **Primäre Bild** entweder **[Keine]** oder **Entitätsbild**. Wählen Sie **Entitätsbild**, um das Bild in der Anwendung anzuzeigen.  
  
Wenn die Bildanzeige für eine Entität aktiviert ist, zeigen alle Datensätze, die kein Bild haben, ein Platzhalterbild an. Beispiel:

![Platzhalterbild](../common-data-service/media/lead-entity-form.PNG)
  
Benutzer können das Standardbild auswählen, um ein Bild von ihrem Computer hochzuladen. Bilder müssen kleiner als 5120 KB sein und eines der folgenden Formate haben:  
  
- JPG
- JPEG
- GIF
- TIF
- TIFF
- BMP
- PNG
  
Wenn das Bild hochgeladen wird, wird es in das .jpg-Format konvertiert, und alle heruntergeladenen Bilder verwenden auch dieses Format. Wenn ein animiertes .gif hochgeladen wird, wird nur der erste Rahmen gespeichert.  
  
Wenn ein Bild hochgeladen wird, wird es auf eine maximale Größe von 144 x 144 Pixel geändert. Benutzer sollten die Bilder neu dimensionieren oder beschneiden, bevor Sie sie hochladen, damit sie problemlos diese Größe verwenden können. Alle Bilder werden quadratisch zugeschnitten. Wenn beide Seiten eines Bilds kleiner als144 Pixel sind, wird das Bild auf ein Quadrat mit den Seitenlängen der kleineren Seite zugeschnitten.  

Weitere Informationen für Entwickler, die mit Bilddaten arbeiten:
- [Entitätsmetadaten > Entitätsbilder](/powerapps/developer/common-data-service/entity-metadata#entity-images)
- [Dynamics 365 Customer Engagement Developer Guide:Bildattribute](/dynamics365/customer-engagement/developer/image-attributes)
