---
title: Erstellen von Patches zur Vereinfachung von Lösungsupdates (Common Data Service) | Microsoft Docs
description: 'Patches helfen Ihnen, Entitäten und zugehörigen Ressourcen zu verwalten, wenn Sie eine Entität einer Lösung hinzufügen und die Lösung exportieren, werden die Entität und alle ihre verknüpften Objekte in die Lösung exportiert.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-patches-to-simplify-solution-updates"></a>Erstellen von Patches zur Vereinfachung von Lösungsupdates

Wenn Sie eine Entität einer Lösung hinzufügen und die Lösung exportieren, werden die Entität und alle ihre verknüpften Objekte in die Lösung exportiert. Diese Objekte umfassen Attribute, Formulare, Ansichten, Beziehungen und Visualisierungen und alle anderen Objekte, die zusammen mit der Entität ausgeliefert wurden. Alle Objekte zu exportieren bedeutet, dass Sie unbeabsichtigt Objekte in der Zielbereitstellung ändern können oder unbeabsichtigte Abhängigkeiten übertragen können.  
  
 Um dies zu lösen, können Sie entweder Lösungspatches erstellen und veröffentlichen, die Unterkomponenten von Entitäten enthalten, anstatt eine vollständige Entität und alle ihre Objekte zu erstellen.  Die ursprüngliche Lösung und eines oder mehrere verknüpfte Patches können zu einem späteren Zeitpunkt als Rollup (Zusammenführung) in einer aktualisierten Version bereitgestellt werden, die dann die ursprüngliche Lösung in der Common Data Service-Zielorganisation ersetzt.  
  
## <a name="patches"></a>Patches  
 Sie können entweder Patches auf verwaltete oder nicht verwaltete Lösungen anwenden und nur Änderungen an Entitäten und verknüpften Entitätsobjekten einfügen. Patches enthalten keine nicht-angepassten Systemkomponenten oder -beziehungen, von denen sie abhängen, da diese Komponenten bereits in der Organisation vorhanden sind, für die sie bereitgestellt wurden. Zu einem bestimmten Zeitpunkt in Ihrem Bereitstellungszyklus können Sie ein Rollup aller Patches in eine neue Lösungsversion durchführen, um die ursprüngliche Lösung zu ersetzen, aus der heraus die Patches erstellt wurden.  
  
 Patches werden in der Common Data Service-Datenbank als `Solution`-Entitätsdatensätze gespeichert. Ein Nicht-null-`ParentSolutionId`-Attribut gibt an, dass die Lösung ein Patch ist. Patches können durch den Organisationsdienst oder Web-APIs erstellt und verwaltet werden. Diese sind nützlich für die Entwicklung von Automatisierung, wie beispielsweise ein Produktinstallationsskript. Allerdings stellt die Common Data Service-Webanwendung verschiedene Webformulare bereit, mit denen Sie Patches interaktiv erstellen und verwalten können.  
  
- Patches können nur von einer übergeordneten Lösung aus mithilfe von <xref:Microsoft.Crm.Sdk.Messages.CloneAsPatchRequest> oder <xref href="Microsoft.Dynamics.CRM.CloneAsPatch?text=CloneAsPatch Action" /> erstellt werden.  
  
- Das dem Patch übergeordnete Objekt kann kein Patch sein.  
  
- Patches können nur eine übergeordnete Lösung haben.  
  
- Ein Patch erstellt eine Abhängigkeit (auf Lösungsebene) für seine übergeordnete Lösung.  
  
- Sie können nur ein Patch erstellen, wenn die übergeordnete Lösung vorhanden ist.  
  
- Sie können keinen Patch installieren, es sei denn ein eindeutiger Name und eine Haupt-/Nebenversionsnummer der übergeordneten Lösung wie sie von `ParentSolutionId` identifiziert wird, stimmen nicht mit denen der übergeordneten Lösung überein, die in der Zielorganisation installiert ist.  
  
- Eine Patchversion muss dieselbe Haupt- und Nebennummer haben, aber eine höhere Build- und Versionsnummer als die Versionsnummer der übergeordneten Lösung. Der Anzeigename kann unterschiedlich sein.  
  
- Wenn eine Lösung über Patches verfügt, müssen darauf folgende Patches eine numerisch höhere Versionsnummer als alle vorhandenen Patches für diese Lösung haben.  
  
- Patches unterstützen dieselben Vorgänge wie Lösungen, wie beispielsweise additive Updates, aber nicht das Entfernen. Sie können mithilfe eines Patches keine Komponenten aus einer Lösung entfernen. Zum Entfernen von Komponenten aus einer Lösung müssen Sie ein Upgrade durchführen.  
  
- Patches, die als verwaltet exportiert werden, müssen zusätzlich zu einer verwalteten übergeordneten Lösung importiert werden. Die Regel besagt, dass Patchschutz (verwaltet oder unverwaltet) der übergeordneten Ebene entsprechen muss.  
  
- Verwenden Sie keine unverwalteten Patches für Produktionszwecke.  
  
- Patches werden nur in Common Data Service-Organisationen der Version 8.0 oder höher unterstützt.  
  
  Die SolutionPackager- und PackageDeployer-Tools in dieser Version unterstützen Lösungspatches. Weitere Informationen erhalten Sie in der Onlinehilfe des Tools für alle Befehlszeilenoptionen, die mit Patches verknüpft sind.  
  
## <a name="create-a-patch"></a>Einen Patch erstellen  
 Erstellen Sie einen Patch aus einer nicht verwalteten Lösung in einer Organisation, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.CloneAsPatchRequest>-Meldung oder die <xref href="Microsoft.Dynamics.CRM.CloneAsPatch?text=CloneAsPatch Action" /> verwenden oder mithilfe der Webanwendung. Sobald Sie einen Patch erstellen, wird die ursprüngliche Version gesperrt und Sie können sie nicht mehr ändern oder exportieren, so lange es abhängige Patches gibt, die in der Organisation vorhanden sind, die die Lösung als die übergeordnete Lösung identifizieren. Patchversionsverwaltung ähnelt der Lösungsversionsverwaltung und ist im folgenden Format angegeben: *major.minor.build.release*. Sie können keine Änderungen an den vorhandenen Haupt- oder Nebenlösungsversionen vornehmen, wenn Sie einen Patch erstellen.  
  
## <a name="export-and-import-a-patch"></a>Exportieren und Importieren eines Patches  
 Sie können den Organisationsdienst oder die Web-APIs, die Webanwendung oder das Package Deployer-Tool verwenden, um einen Patch zu exportieren und zu importieren. Die Organisationsdienstmeldungs-Anforderungen sind <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> und <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest>. Die relevanten Aktionen für die Web-API sind <xref href="Microsoft.Dynamics.CRM.ImportSolution?text=ImportSolution Action" /> und <xref href="Microsoft.Dynamics.CRM.ExportSolution?text=ExportSolution Action" />.  
  
### <a name="patching-examples"></a>Beispiele fürs Patchen  
 In der folgenden Tabelle sind die Details des Beispiels eines Patchvorgangs aufgeführt. Beachten Sie, dass in diesem Beispiel die Lösung und Patches in numerischer Reihenfolge importiert werden und additiv sind, das ist in Übereinstimmung mit dem Lösungsimport im Allgemeinen.  
  
|Patchname|Beschreibung|  
|----------------|-----------------|  
|SolutionA, Version 1.0 (unverwaltet)|Enthält entityA mit 6 Feldern.|  
|SolutionA, Version 1.0.1.0 (unverwaltet)|Enthält entityA mit 6 Feldern (3 aktualisiert) und fügt entityB mit 10 Feldern hinzu.|  
|SolutionA, Version 1.0.2.0 (unverwaltet)|Enthält entityC mit 10 Feldern.|  
  
 Der Importvorgang ist wie folgt.  
  
1.  Der Entwickler oder Anpasser importiert zuerst die Basislösung (SolutionA 1.0) in die Organisation. Das Ergebnis ist entityA mit Feldern 6 in der Organisation.  
  
2.  Anschließend wird das SolutionA-Patch 1.0.1.0 importiert. Die Organisation enthält nun entityA mit 6 Feldern (3 wurden aktualisiert), sowie entityB mit 10 Feldern.  
  
3.  Zuletzt wird SolutionA-Patch 1.0.2.0 importiert. Die Organisation enthält nun entityA mit 6 Feldern (3 wurden aktualisiert), entityB mit 10 Feldern sowie entityC mit 10 Feldern.  
  
### <a name="another-patching-example"></a>Ein weiteres Beispiel für einen Patchvorgang:  
 Betrachten wir nun ein weiteres Beispiel für einen weiteren Patchvorgang. abei werden die Details in der folgenden Tabelle aufgelistet.  
  
|Patchname|Beschreibung|  
|----------------|-----------------|  
|SolutionA, Version 1.0 (unverwaltet, Basislösung)|Enthält die `Account`-Entität, bei der die Länge des Firmennummernfelds von 20 auf 30 Zeichen angepasst wird.|  
|SolutionB, Version 2.0 (nicht verwaltet, anderer Zulieferer)|Enthält die `Account`-Entität, bei der die Länge des Firmennummernfelds auf 50 Zeichen angepasst wird.|  
|SolutionA, Version 1.0.1.0 (unverwaltet, Patch)|Enthält ein Update auf die `Account`-Entität, bei der die Länge des Firmennummernfelds auf 35 Zeichen angepasst wird.|  
  
 Der Importvorgang ist wie folgt:  
  
1.  Der Entwickler oder Anpasser importiert zuerst die Basislösung (SolutionA 1.0) in die Organisation. Das Ergebnis ist eine `Account`-Entität mit einem Firmennummerenfeld von 30 Zeichen.  
  
2.  SolutionB wird importiert. Die Organisation enthält nun eine `Account`-Entität mit einem Firmennummerenfeld von 50 Zeichen.  
  
3.  SolutionA-Patch 1.0.1.0 wird importiert. Die Organisation enthält immer noch eine `Account`-Entität mit einem Firmennummerenfeld von 50 Zeichen, wie durch SolutionB angewendet.  
  
4.  SolutionB wird deinstalliert. Die Organisation enthält nun eine `Account`-Entität mit einem Firmennummerenfeld von 35 Zeichen, wir durch das SolutionA 1.0.1.0-Patch angewendet.  
  
## <a name="delete-a-patch"></a>Ein Patch löschen  
 Sie können einen Patch oder eine Basis-(übergeordnete)-Lösung löschen, indem Sie <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> verwenden oder, für die Web-API, die `HTTP DELETE`-Methode verwenden. Der Löschvorgang ist bei einer verwalteten und einer nicht verwalteten Lösung, bei der eine oder mehrere Patches in der Organisation vorhanden sind, unterschiedlich.  
  
 Für eine nicht verwaltete Lösung müssen Sie alle Patches der Basislösung zuerst löschen, in der umgekehrten Versionsreihenfolge, als in der sie erstellt wurden, bevor Sie die Basislösung deinstallieren.  
  
 Für eine verwaltete Lösung deinstallieren Sie einfach die Basislösung. Das Common Data Service-System deinstalliert automatisch die Patches in umgekehrter Versionsreihenfolge, bevor die Basislösung deinstalliert wird. Sie können auch einfach einen einzelnen Patch deinstallieren.  
  
## <a name="update-a-solution"></a>Eine Lösung aktualisieren  
 Beim Aktualisieren einer Lösung wird ein Rollup (Zusammenführung) aller Patches für diese Lösung in eine neue Version der Lösung ausgeführt. Danach wird die Lösung entsperrt und kann erneut geändert werden (nur nicht verwaltete Lösung) oder exportiert werden. Für eine verwaltete Lösung sind keine weiteren Änderungen der Lösung zulässig, außer wenn Patches aus der neu aktualisierten Lösung erstellt werden. Wenn Sie einen Rollup für Patches in eine nicht verwaltete Lösung ausführen, verwenden Sie <xref:Microsoft.Crm.Sdk.Messages.CloneAsSolutionRequest> oder die <xref href="Microsoft.Dynamics.CRM.CloneAsSolution?text=CloneAsSolution Action" />. Beim Clonen einer Lösung wird eine neue Version der nicht verwalteten Lösung erstellt. Dabei werden alle ihre Patches einbezogen, mit einer höheren *major.minor*-Versionsnummer, demselben eindeutigen Namen und einem Anzeigename.  
  
 Bei einer verwalteten Lösung wird etwas anders vorgegangen. Zuerst klonen Sie die nicht verwaltete Lösung (A), binden alle ihre Patches ein und exportieren sie dann als eine verwaltete Lösung (B). In der Zielorganisation, die die verwaltete Lösung der (A) Lösung und ihre Patches umfasst, importieren Sie die verwaltete Lösung (B) und führen dann <xref:Microsoft.Crm.Sdk.Messages.DeleteAndPromoteRequest> oder die <xref href="Microsoft.Dynamics.CRM.DeleteAndPromote?text=DeleteAndPromote Action" /> aus, um die verwaltete Lösung (A) und ihre Patches mit der aktualisierten verwalteten Lösung (B) zu ersetzen, die eine höhere Versionsnummer hat.  
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden Sie segmentierte Lösungen und Patches, um Lösungsupdates zu vereinfachen](https://technet.microsoft.com/library/mt628808.aspx)   
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Packen und Verteilen von Erweiterungen mithilfe von Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Lösungsentität](/reference/entities/solution.md)   
 [Pflegen von verwalteten Lösungen](maintain-managed-solutions.md)   
 [Veröffentlichen Sie die App für AppSource](publish-app-appsource.md)