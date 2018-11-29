---
title: String (RESX)-Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: 'Infos zur Verwendung von String-Webressourcen, um lokalisierte Zeichenfolgen zur Verwendung bereitzustellen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="resx-web-resources"></a>RESX Webressourcen

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/resx-web-resources -->

Verwenden Sie diese Webressourcen, um lokalisierte Zeichenfolgen in der Benutzeroberfläche des Datenmigrations-Managers zu verwalten, die Sie definieren, oder verweisen Sie mit Fehlermeldungen angezeigt. 

# <a name="using-resx-web-resources"></a>Verwenden von RESX-Webressourcen

RESX-Webressourcen enthalten die lokalisierten Zeichenfolgenwerte und Schlüssel für eine einzeln Sprache, definiert im Format RESX XML. RESX ist ein häufig verwendetes Format, um lokalisierte Ressourcen für Windows-Anwendungen zu definieren, d. h. für diesen Dateityp stehen gängige Tools zur Verfügung, und Lokalisierungsanbieter sind mit der Arbeit damit vertraut. Wenn die Datei als Webressource in CRM veröffentlicht wird, wird sie in ein JSON-Format umgewandelt, das zur Anwendung nach Bedarf heruntergeladen wird.

Wenn Sie RESX-Webressourcen erstellen, müssen Sie den Sprachenwert explizit festlegen sowie den Gebietsschemabezeichner (LCID) für die entsprechende Sprache im Namen der Webressource einschließen. Beispielsweise `new_/strings/MyAppResources.1033.resx` würde Ressourcen für englische Sprache enthalten. Siehe [Microsoft-Gebietsschema-ID-Werte](https://msdn.microsoft.com/library/ms912047(WinEmbedded.10).aspx) für eine Liste der LCID-Werte.

Um den lokalisierten Wert zu extrahieren, verwenden Sie die [Xrm.Utility.getResourceString](clientapi/reference/Xrm-Utility/getResourceString.md)-Funktion. Diese Funktion akzeptiert zwei Parameter: `WebResourceName` und `keyValue`. 

Beispielsweise `Xrm.Utility.getResourceString("new_/strings/MyAppResources","hello")` gibt den lokalisierten Zeichenfolgenwert für den Ressourcenschlüssel hallo innerhalb der Webressource `new_/strings/MyAppResources.1033.resx` zurück, wenn die bevorzugte Sprache des Benutzers Englisch ist. Beachten Sie, dass die Funktion sich nicht auf eine bestimmte Sprache oder vollständigen Namen der RESX-Webressource bezieht. Die Funktionalität ist von der RESX-Webressource abhängig, die mit der aufrufenden JavaScript-Webressource als Abhängigkeit verknüpft ist. Weitere Informationen: [Webressourcenabhängigkeiten](web-resource-dependencies.md).

Der entsprechende Zeichenfolgenwert ist festgelegt durch die Spracheinstellung und die deaktivierten Sprachen einzelner Benutzer, die in der Organisation verfügbar sind. Wenn eine isolierte Zeichenfolge nicht gefunden wird, die Spracheinstellung des Benutzers entspricht, wird automatisch die lokalisierte Zeichenfolge auf die Ausgangssprache für die Organisation zurückgesetzt. Wenn keine entsprechende Zeichenfolge für die Organisationsausgangssprache gefunden wird, wird ein NULL-Wert zurückgegeben.

### <a name="see-also"></a>Siehe auch
[Webressourcen](web-resources.md)<br />
[Erstellen von barrierefreien Webressourcen](create-accessible-web-resources.md)<br />
[Webressourcen und IFrame-Inhalte für die Verwendung mit dem Dynamics 365 für mobile Client erstellen](/dynamics365/customer-engagement/developer/create-web-resources-iframe-mobile)<br />
[Abhängigkeiten von Webressourcen](web-resource-dependencies.md)<br />
[Webressourcen der Webseite (HTML)](webpage-html-web-resources.md)<br />
[Silverlight (XAP)-Webressourcen](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)<br />
[Webressourcen für Skripts (JScript)](script-jscript-web-resources.md)<br />
[Bild- (JPG, PNG, GIF, ICO)-Webressourcen](image-web-resources.md)<br />
[XSL-Webressourcen (Stylesheet)](stylesheet-xsl-web-resources.md)<br />
[Webressourcen von Daten (XML)](data-xml-web-resources.md)<br />
[CSS Webressourcen](css-web-resources.md)<br />
[WebResource-Entitätsmeldungen und Methoden](/dynamics365/customer-engagement/developer/webresource-entity-messages-methods)<br />
[Beispiel: Mehrere Werte über den Datenparameter an eine Webressource übergeben](sample-pass-multiple-values-web-resource-through-data-parameter.md)<br />
[Beispiel: Importieren von Dateien als Webressourcen](sample-import-files-web-resources.md)<br />