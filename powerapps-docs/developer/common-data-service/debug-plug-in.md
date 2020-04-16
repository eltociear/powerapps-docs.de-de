---
title: Debuggen von Plug-Ins (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit dem Plug-in-Registrierungstool Plug-Ins debuggen können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 637ed40097ff29cc74cdfc671eb4e2f6cf7edf2b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156274"
---
# <a name="debug-plug-ins"></a>Debuggen von Plug-Ins

Der Prozess des Schreibens, Registrierens und Debuggens eines Plugins ist:

1. Erstellen Sie ein .NET Framework-Klassenbibliotheksprojekt in Visual Studio
1. Fügen Sie das `Microsoft.CrmSdk.CoreAssemblies` NuGet-Paket dem Projekt hinzu
1. Implementieren Sie die <xref:Microsoft.Xrm.Sdk.IPlugin>-Schnittstelle in Klassen, die als Schritte registriert werden.
1. Fügen Sie Ihren Code der <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>-Methode hinzu, die für die Schnittstelle erforderlich ist
    1. Rufen Sie Referenzen auf Dienste ab, die Sie benötigen
    1. Fügen Sie Ihre Geschäftslogik hinzu
1. Signieren und erstellen Sie die Assembly
1. Testen des Assemblys.
    1. Registrieren des Assemblys in einer Testumgebung
    1. Fügen Sie Ihre registrierten Assembly und Schritte einer nicht verwalteten Lösung hinzu
    1. **Das Verhalten der Assemblys testen**
    1. **Überprüfen Sie, ob erwartete Ablaufverfolgungsprotokolle geschrieben werden.**
    1. **Die Assembly nach Bedarf debuggen**

Der Inhalt in diesem Thema behandelt die oben **fett gedruckten** Schritte und unterstützt die folgenden Tutorials:

- [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)
- [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)
- [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)

## <a name="test-your-assembly"></a>Testen Sie Ihre Assembly

Die einfachste Methode, Ihre Assembly zu testen, kann einfach darin bestehen, den Vorgang manuell mit der App durchzuführen. Sie sollten sich aber auch darüber im Klaren sein, dass Ereignisse, die die Ausführung von Plug-Ins bewirken, auf verschiedene Weise ausgelöst werden können, z.B. durch eine Entität, die aus einem Workflow oder aus den Webservices erstellt wurde.

Die Attributwerte oder andere Kontextinformationen zur Ausführung können je nach Ausführung der Aktion unterschiedlich sein. Wenn Sie Ihr Plug-In schreiben, stellen Sie sicher, dass Sie defensive Programmierpraktiken anwenden und nicht davon ausgehen, dass jeder Wert, den Sie erwarten, immer vorhanden sein wird.

Sie können ein Programm schreiben, das die Ausführung der Vorgänge automatisiert, die Ihr Plug-In zum Auslösen bringen und eine Reihe von möglichen Variationen beinhaltet.

Wenn Sie ein Testautomatisierungs-Framework verwenden möchten, werden Sie feststellen, dass die Community einige Tools dafür entwickelt hat. Weitere Informationen: [Testtools für serverseitige Entwicklung](testing-tools-server.md)


## <a name="use-tracing"></a>Ablaufverfolgung verwenden

Wie unter [Verwendung des Tracing-Dienstes](write-plug-in.md#use-the-tracing-service) beschrieben, können Sie Nachrichten an die [PluginTraceLog Entität](reference/entities/plugintracelog.md) im Code Ihres Plug-Ins schreiben, indem Sie die <xref:Microsoft.Xrm.Sdk.ITracingService>.<xref:Microsoft.Xrm.Sdk.ITracingService.Trace*> verwenden. Methode.

Bevor Sie diesen Service nutzen können, müssen Sie in Ihrer Common Data Service-Umgebung die Ablaufverfolgung aktivieren. Der Prozess ist in  [Ablaufverfolgungsprotokolle anzeigen](tutorial-write-plug-in.md#view-trace-logs) beschrieben.

> [!NOTE]
> Die Ablaufverfolgungsprotokollierung erfordert Organisationsspeicherplatz, insbesondere wenn viele Ablaufverfolgungen und Ausnahmen generiert werden. Sie sollten die Ablaufverfolgungsprotokollierung nur für das Debugging und die Problembehandlung aktivieren, und deaktivieren, wenn die Überprüfung abgeschlossen ist.

Während des Debuggens können Sie die Ablaufverfolgungsprotokolle für eine bestimmte Plug-In-Klasse über die Web-API in Ihrem Browser einfach abfragen. Wenn Ihre Assembly den Namen `BasicPlugin.FollowUpPlugin` hat, können Sie diese Abfrage in Ihrem Browser-Adressfeld verwenden:

`GET <your org uri>/api/data/v9.0/plugintracelogs?$select=messageblock&$filter=typename eq 'BasicPlugin.FollowUpPlugin'`

Die JSON-Ergebnisse werden wie beschrieben an Ihren Browser zurückgegeben:


```json
{
    "@odata.context": "<your org uri>/api/data/v9.0/$metadata#plugintracelogs(messageblock)",
    "value": [{
        "messageblock": "FollowupPlugin: Creating the task activity.",
        "plugintracelogid": "f0c221d1-7f84-4f89-acdb-bbf8f7ce9f6c"
    }]
}
```

> [!TIP]
> Dies funktioniert am besten, wenn Sie ein Browser-Plug-In installieren, das das zurückgegebene JSON formatiert. Oder Sie möchten Postman verwenden. Weitere Informationen: [Postman mit Web-API verwenden](/dynamics365/customer-engagement/developer/webapi/use-postman-web-api)
> 
> Sie können auch den [XrmToolbox Plugin Ablaufverfolgungsanzeige](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.PluginTraceViewer/) verwenden. Dieses Community-Tool wird von Microsoft nicht unterstützt. Wenn Sie Fragen zu diesem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung.

Ablaufverfolgungsmeldungen finden sich auch in der Protokolldatei, die heruntergeladen werden kann, wenn eine synchrone Plug-In- oder benutzerdefinierte Workflow-Assembly einen Fehler auslöst, der zu einem Fehlerdialog führt, der dem Benutzer angezeigt wird. Der Benutzer kann die Schaltfläche **Protokolldatei herunterladen** auswählen, um das Protokoll mit den Details der Ausnahme und der Ablaufverfolgungsausgabe anzuzeigen.

Bei asynchronen registrierten Plug-Ins oder benutzerdefinierten Workflow-Assemblys, die eine Ausnahme zurückgeben, werden die Ablaufverfolgungsinformationen im Bereich Details des **Systemauftrag**-Formulars in der Webanwendung angezeigt.

> [!NOTE]
> Wenn benutzerdefinierter Code in einer Datenbanktransaktion ausgeführt wird und eine Ausnahme auftritt, die ein Transaktionsrollback verursacht, werden alle Entitätsdatenänderungen durch Code rückgängig gemacht. Die `PluginTraceLog`-Entitätsdatensätze bleiben jedoch bis zum Fertigstellen des Rollbacks vorhanden.

## <a name="use-plug-in-profiler"></a>Plug-In-Profiler verwenden

Plug-in-Profiler ist eine Lösung, die Sie in Ihrer Umgebung installieren können, mit der Sie den Ausführungskontext eines Plug-Ins erfassen und dann diese Daten verwenden können, um das Ereignis während des Debuggens in Visual Studio erneut abzuspielen.

Eine Anleitung zur Installation und Verwendung des Plug-in-Profilers finden Sie im [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md). Siehe [Plug-In-Profiler installieren](tutorial-debug-plug-in.md#install-plug-in-profiler) und [Ihr Plug-In debuggen](tutorial-debug-plug-in.md#debug-your-plug-in).

### <a name="view-plug-in-profile-data"></a>Plug-In-Profildaten anzeigen

Nachdem Sie den Plug-in-Profiler installiert und einige Profile erfasst haben, können Sie den Ereigniskontext anzeigen und Daten wiedergeben, die beim Debuggen verwendet werden. Die Anzeige dieser Daten kann Ihnen helfen, die Kontextdaten der Ausführung zu verstehen, die Ihr Plug-In verwenden kann.

Sie können diese Daten mit dem Plug-in-Registrierungstool anzeigen, indem Sie den Befehl **Plug-In-Profil anzeigen** wählen. Dadurch wird der Dialog Plugin-Profil geöffnet.

![Plug-In-Profil öffnen](media/view-plug-in-profile.png)

Wählen Sie das Symbol ![Symbol herunterladen](media/prt-down-arrow-icon.png) und geben Sie im Dialog **Profil aus CRM auswählen** das zu verwendende Protokollelement an.

![Profil aus CRM auswählen](media/prt-select-profile-from-crm.png)

Und wählen Sie dann **Ansicht** im Dialogfeld **Plug-In-Profil** aus.

Dadurch wird eine geöffnete XML-Datei mit den Profilinformationen heruntergeladen. Das `Context`-Element stellt den Ausführungskontext dar, der an das Plug-In übergeben wird.

![Beispiel-Profildaten](media/prt-example-profile-data.png)

### <a name="more-information"></a>Weitere Informationen

[Testtools für serverseitige Entwicklung](testing-tools-server.md)