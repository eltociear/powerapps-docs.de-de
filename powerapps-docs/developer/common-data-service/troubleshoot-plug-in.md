---
title: Problembehandlungs-Plug-Ins (Common Data Service for Apps) | Microsoft Docs
description: 'Enthält Informationen zu Fehlern, die aufgrund von Plug-Ins auftreten können und wie sie behoben werden.'
ms.custom: ''
ms.date: 04/21/2019
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
[Skalierbarer Anpassungsentwurf in Common Data Service](scalable-customization-design/overview.md) Die häufigste Ursache ist einfach, dass ein Entwickler glaubt, er könne versuchen eine Operation auszuführen, die *möglicherweise* erfolgreich ist und er diese Operation in einem try/catch-Block umbricht und versucht, den Fehler zu schlucken, wenn die Operation fehlschlägt.

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