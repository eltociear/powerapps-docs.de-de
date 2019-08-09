---
title: Problembehandlungs-Plug-Ins (Common Data Service für Apps) | Microsoft Docs
description: 'Enthält Informationen zu Fehlern, die aufgrund von Plug-Ins auftreten können und wie sie behoben werden.'
ms.custom: ''
ms.date: 04/26/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="troubleshoot-plug-ins"></a>Problembehandlungs-Plug-Ins 

Dieses Thema enthält Informationen zu Fehlern, die aufgrund von Plug-Ins auftreten können und wie sie behoben werden.

## <a name="error-there-is-no-active-transaction"></a>Fehler: Es gibt keine aktive Transaktion. 

Fehlercode: `-2147220911`<br />
Fehlermeldung: `There is no active transaction. This error is usually caused by custom plug-ins that ignore errors from service calls and continue processing.`

Es kann schwierig sein, den Fehler zu beheben, da die Ursache im Code einer anderen Person liegen kann. Um die Nachricht zu verstehen, müssen Sie bedenken, dass bei einem Fehler der Datenoperation im Synchronen Plug-In jedes Mal die Transaktion für die gesamten Operation beendet wird.

Mehr Informationen: [Skalierbares Anpassungsdesign in Common Data Service](scalable-customization-design/overview.md)

Die häufigste Ursache ist einfach, dass ein Entwickler glaubt, er könne versuchen, eine Operation auszuführen, die *möglicherweise* erfolgreich ist und er diese Operation in einem try/catch-Block umbricht und versucht, den Fehler zu schlucken, wenn die Operation fehlschlägt.

Auch wenn dies bei einer Clientanwendung funktionieren kann, bei der Ausführung eines Plug-Ins führt jeder Datenvorgangsfehler zum Rollback der gesamte Transaktion. Sie können die Fehler nicht schlucken, daher müssen Sie sicherstellen, stets <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> zurückzugeben.

## <a name="error-sql-error-execution-timeout-expired"></a>Fehler: SQL-Fehler: Ausführungs-Timeout abgelaufen

Fehlercode: `-2147204783`<br />
Fehlermeldung: `Sql error: 'Execution Timeout Expired.  The timeout period elapsed prior to completion of the operation or the server is not responding.'`

Es gibt viele Gründe für einen SQL-Timeout-Fehler.

### <a name="blocking"></a>Blockierung

Blockierung ist die häufigste Ursache für einen SQL-Timeout-Fehler, da der Vorgang auf Ressourcen wartet, die von einer anderen SQL-Transaktion gesperrt sind. Dieser Fehler entsteht, wenn das System die Integrität der Daten schützt und bei über lange Zeit ausgeführten Anforderungen, die sich auf die Leistung für Benutzer auswirken.

Blockierung kann durch andere gleichzeitige Operationen verursacht werden. Ihr Code funktioniert ggf. gut in einer isolierten Testumgebung und kann dennoch für Bedingungen anfällig sein, die nur auftreten, wenn mehrere Benutzer die Logik im Plug-In initiieren.

Beim Schreiben von Plug-Ins ist es wichtig, nachvollziehen zu können, wie skalierbare Anpassungen entwickelt werden. Mehr Informationen: [Skalierbares Anpassungsdesign in Common Data Service](scalable-customization-design/overview.md)

### <a name="cascade-operations"></a>Weitergabevorgänge

Bestimmte Aktionen, die Sie in Ihrem Plug-In vornehmen, z. B: das Zuweisen oder Löschen eines Datensatzes, kann einzelne Vorgänge in verknüpften Datensätzen initiieren. Diese Aktionen können Sperren auf den verknüpften Datensätzen anwenden, die verursachen, dass nachfolgende Datenvorgänge blockiert werden, was wiederum zu einem SQL-Timeout führen kann. 

Sie sollten die möglichen Auswirkungen dieser überlappenden Vorgänge auf Datenvorgänge in Ihrem Plug-In bedenken. Weitere Informationen: [Verhalten von Entitätsbeziehungen](../../maker/common-data-service/entity-relationship-behavior.md)

Da dieses Verhalten zwischen Umgebungen unterschiedlich konfiguriert werden kann, ist das Verhalten möglicherweise schwer reproduzierbar, außer die Umgebungen werden gleich konfiguriert.

### <a name="indexes-on-new-entities"></a>Indizes für neue Entitäten

Wenn das Plug-In Vorgänge mithilfe einer Entität oder eines Attributes ausführt, das vor Kurzem erstellt wurde, machen einige Azure SQL-Funktionen zum Verwalten von Indizes nach mehreren Tagen einen Unterschied.

## <a name="errors-due-to-user-privileges"></a>Fehler aufgrund von Benutzerrechten

In einer Clientanwendung können Sie Befehle deaktivieren, die Benutzer nicht ausführen dürfen. In einem Plug-Ins ist dies nicht vorhanden. Ihr Code enthält ggf. einige Automatisierungen, für deren Ausführung der aufrufende Benutzer keine Rechte hat ist.

Sie können registrieren, dass das Plug-In im Rahmen eines Benutzers ausgeführt wird, der die richtigen Rechte hat, indem Sie den Wert **Ausführung im Kontext des Benutzers** für den Benutzer festlegen. Oder Sie können den Vorgang ausführen, indem Sie die Identität einen anderen Benutzers annehmen. Weitere Informationen:
 - [Registrieren eines Plug-Ins](register-plug-in.md)
 - [Die Identität eines Benutzers annehmen](impersonate-a-user.md)

<!-- But if you prefer that the logic in your plug-in adapt to the privileges that the calling user has, you really need to verify the user's privileges in your code.

TODO: Add content that shows how to do this -->

## <a name="error-message-size-exceeded-when-sending-context-to-sandbox"></a>Fehler: Nachrichtengröße beim Senden von Kontext an den Sandkasten überschritten

<!-- This is the error code for an unexpected error we should be providing a specific error code. Bug 1470173 is tracking this. -->
Fehlercode: `-2147220970`<br />
Fehlermeldung: `Message size exceeded when sending context to Sandbox. Message size: ### Mb`

Dieser Fehler tritt auf, wenn eine Message-Nutzlast größer als 116,85 MB ist **UND** ein Plug-In für die Message registriert ist. Die Fehlermeldung enthält die Größe der Nutzlast, die den Fehler verursacht hat.
 
Die Beschränkung stellt sicher, dass Benutzer, die Anwendungen ausführen, sich nicht aufgrund vorhandener Ressourceneinschränkungen gegenseitig stören. Die Einschränkung bietet einen gewissen Schutz vor ungewöhnlich großen Message-Nutzlasten, die die Verfügbarkeit und Leistungsfähigkeit der Common Data Service-Plattform gefährdet.
 
116,85 MB ist groß genug, dass dieser Fall eher selten eintreten sollte. Die wahrscheinlichste Situation, in der dieser Fall eintreten könnte, ist, wenn Sie einen Datensatz mit mehreren Datensätzen abrufen, die große Binärdateien enthalten.
 
Wenn dieser Fehler auftritt, können Sie:

1.  Das Plug-In für die Message entfernen Wenn es keine Plug-Ins gibt, die für die Message registriert, wird der Vorgang ohne ein Fehler abgeschlossen.
2.  Wenn der Fehler in einem benutzerdefinierten Client auftritt, können Sie Ihren Code ändern, damit er nicht versucht, die Aufgabe in einem einzelnen Vorgang auszuführen. Schreiben Sie stattdessen Code, um die Daten in kleineren Teilen abzurufen.

## <a name="error-the-given-key-was-not-present-in-the-dictionary"></a>Fehler: Der entsprechende Schlüssel war nicht im Wörterbuch vorhanden

Common Data Service verwendet häufig Klassen, die von der abstrakten <xref:Microsoft.Xrm.Sdk.DataCollection`2>-Klasse abgeleitet wurden, die eine Sammlung von Schlüsseln und Werten darstellt. Beispiel: Mit Plug-Ins ist die Eigenschaft <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> eine <xref:Microsoft.Xrm.Sdk.ParameterCollection>, die von der <xref:Microsoft.Xrm.Sdk.DataCollection`2>-Klasse abgeleitet wurde. Diese Klassen sind im Wesentlichen Wörterbuchobjekte, bei denen Sie mithilfe des Schlüsselnamens auf einen bestimmten Wert zugreifen.

### <a name="error-codes"></a>Fehlercodes

Dieser Fehler tritt auf, wenn der Schlüsselwert im Code nicht in der Sammlung ist. Dies ist eher ein Laufzeitfehler als ein Plattformfehler. Wenn dieser Fehler innerhalb eines in Plug-Ins auftritt, hängt der Fehlercode davon ab, ob der Fehler entdeckt wurde.

Wenn der Entwickler die Ausnahme entdeckt hat und eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> zurückgegeben hat, wie unter [Behandlung von Ausnahmen in Plug-Ins](handle-exceptions.md) beschrieben, wird der folgende Fehler zurückgegeben:

Fehlercode: `-2147220891`<br />
Fehlermeldung: `ISV code aborted the operation.`

Bei diesem Fehler passiert es jedoch häufig, dass der Entwickler ihn nicht richtig entdeckt, und dann wird der folgende Fehler zurückgegeben:

Fehlercode: `-2147220956`<br />
Fehlermeldung: `An unexpected error occurred from ISV code.`

> [!NOTE]
> „ISV” steht für *Unabhängige Softwarehersteller* (Independent Software Vendor).

### <a name="causes"></a>Ursachen

Dieser Fehler tritt auf häufig zur Entwurfszeit auf und kann aufgrund eines Schreibfehlers oder durch Verwendung der falschen Groß-/Kleinschreibung auftreten. Bei Schlüsselwerten ist auf die Groß-/Kleinschreibung zu achten.

Während der Laufzeit tritt der Fehler häufig auf, weil der Entwickler davon ausgeht, dass der Wert vorhanden ist, aber dies nicht der Fall ist. Beispiel: In einem Plug-In, das für das zum Aktualisieren einer Entität registriert ist, werden nur die Werte, die geändert werden, hier auf genommen: <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Attributes> Sammlung

### <a name="prevention"></a>Vorbeugung

Um diesen Fehler zu verhindern, müssen Sie überprüfen, dass der Schlüssel auch vorhanden ist, bevor Sie versuchen, ihn zu verwenden, um auf einen Wert zuzugreifen. 

Wenn Sie beispielsweise auf ein Entitätsattribut zugreifen, können Sie die Methode <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Contains(System.String)> verwenden, um zu überprüfen, ob ein Attribut in einer Entität vorhanden ist, wie im folgenden Code dargestellt.

```csharp
// Obtain the execution context from the service provider.  
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));

// The InputParameters collection contains all the data passed in the message request.  
if (context.InputParameters.Contains("Target") &&
    context.InputParameters["Target"] is Entity)
    {
    // Obtain the target entity from the input parameters.  
    Entity entity = (Entity)context.InputParameters["Target"];

    //Check whether the name attribute exists.
    if(entity.Contains("name"))
    {
        string name = entity["name"];
    }
```

Einige Entwickler verwenden die Methode <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)> , um diesen Fehler zu vermeiden, wenn Sie auf die Entitätsattribute zugreifen. Bedenken Sie aber, dass bei dieser Methode der Standardwert des Typs zurückgegeben wird, wenn das Attribut nicht vorhanden ist. Wenn der Standardwert Null ist, funktioniert dies wie erwartet. Wenn jedoch der Standardwert nicht Null zurückgibt, beispielsweise bei `DateTime`, wird eher der Wert `1/1/0001 00:00` als Null zurückgegeben.