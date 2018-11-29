---
title: Quellsteuerelement mit Lösungsdateien (Common Data Service für Apps) | Microsoft Docs
description: 'Das SolutionPackager-Tool kann für jedes beliebige Quellcodeverwaltungssystem verwendet werden. Nachdem eine Lösungs-ZIP-Datei in einen Ordner extrahiert wurde, fügen Sie einfach die Dateien zu Ihrem Quellcodeverwaltungssystem hinzu. Diese Dateien können dann auf einem anderen Computer synchronisiert werden, wo sie in eine neue identische Lösungs-ZIP-Datei gepackt werden können.'
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
# <a name="source-control-with-solution-files"></a>Quellcodeverwaltung mit Lösungsdateien

Das SolutionPackager-Tool kann für jedes beliebige Quellcodeverwaltungssystem verwendet werden. Nachdem eine Lösungs-ZIP-Datei in einen Ordner extrahiert wurde, fügen Sie einfach die Dateien zu Ihrem Quellcodeverwaltungssystem hinzu. Diese Dateien können dann auf einem anderen Computer synchronisiert werden, wo sie in eine neue identische Lösungs-ZIP-Datei gepackt werden können.  
  
 Ein wichtiger Aspekt der Verwendung extrahierter Komponentendateien bei der Quellcodeverwaltung besteht darin, dass das Hinzufügen aller Dateien zur Quellcodeverwaltung zu unnötigen Duplizierungen führen kann. Siehe [Dateireferenz von Lösungskomponenten](solution-component-file-reference-solutionpackager.md), um zu überprüfen, welche Dateien für jeden Komponententyp generiert werden und welche Dateien für die Verwendung in der Quellcodeverwaltung empfohlen werden.  
  
 Wenn weitere Anpassungen und Änderungen für die Lösung erforderlich sind, sollten Entwickler vorhandene Komponenten mit bestehenden Methoden bearbeiten oder anpassen, sie erneut exportieren, um eine ZIP-Datei zu erstellen und die komprimierte Lösungsdatei in den gleichen Ordner zu extrahieren.  
  
> [!IMPORTANT]
>  Außer in den in [Wann die Anpassungsdatei bearbeitet werden sollte](/model-driven-apps/when-edit-customization-file.md) beschriebenen Abschnitte wird das manuelle Bearbeiten extrahierter Komponentendateien und ZIP-Dateien nicht unterstützt.  
  
 Wenn das SolutionPackager-Tool die Komponentendateien extrahiert, überschreibt es nicht die vorhandenen Komponentendateien mit demselben Namen, wenn der Inhalt der Dateien identisch ist. Darüber hinaus beachtet das Tool das Schreibschutzattribut der komponentendateien und gibt eine Warnung im Konsolenfenster aus, dass einige Dateien nicht überschrieben wurden. Dadurch kann der Benutzer den minimalen Dateiensatz aus der Quellcodeverwaltung auschecken, die sich geändert haben. Der Parameter `/clobber` kann verwendet werden, um die Dateien zu überschreiben und schreibgeschützte Dateien schreiben oder löschen zu lassen. Der Parameter `/allowWrite` kann verwendet werden, um zu bewerten, welche Auswirkungen ein Extrahierungsvorgang hat, ohne dass dabei Dateien geschrieben oder gelöscht werden. Die Verwendung des Parametes `/allowWrite` mit ausführlicher Protokollierung ist effektiv.  
  
 Nach dem Abschluss des Extrahierungsvorgangs mit dem Auschecken des Minimalsatzes von Dateien aus der Quellcodeverwaltung kann der Entwickler die geänderten Dateien wieder in die Quellcodeverwaltung zurückgeben, wie bei anderen Dateitypen auch.  
  
<a name="team_dev"></a>   
## <a name="team-development"></a>Team-Entwicklung  
 Wenn mehrere Entwickler an derselben Lösungskomponente arbeiten, entsteht möglicherweise ein Konflikt, wobei Änderungen von zwei Entwicklern zu Änderungen an einer einzelnen Datei führen. Diese Gefahr wird vermindert, indem jede einzeln bearbeitbare Komponente oder Unterkomponente in eine distinkte Datei zerlegt wird. Betrachten Sie das folgende Beispiel.  
  
1. Entwickler A und Entwickler B arbeiten beide an derselben Lösung.  
  
2. Auf unabhängigen Computern erhalten beide die neuesten Quellen der Lösung vom Quellsteuerelement, Paket, und importieren eine ZIP-Datei einer nicht verwalteten Lösung in unabhängige "CDS für Apps"-Organisationen.  
  
3. Entwickler A passt die "Aktive Kontakte"-Systemansicht und das Hauptformular für die Kontaktentität an.  
  
4. Entwickler B passt die Hauptformular für die Kontoentität an und ändert die Ansicht "Kontaktsuche".  
  
5. Beide Entwickler exportieren eine nicht verwaltete Lösungs-ZIP-Datei und extrahieren sie.  
  
   1.  Entwickler A muss eine Datei für das Kontakthauptformular und eine Datei für Ansicht "Aktive Kontakte" auschecken.  
  
   2.  Entwickler B muss eine Datei für das Kontohauptformular und eine Datei für Ansicht "Kontaktsuche" auschecken.  
  
6. Beide Entwickler können, in beliebiger Reihenfolge, ihre Dateien einreichen, da sich ihre Änderungen auf verschiedene Dateien auswirken.  
  
7. Wenn beide Einreichungen abgeschlossen sind, können Sie Schritt 2 wiederholen und dann weitere Änderungen in ihren unabhängigen Organisationen vornehmen. Beide haben beide Sätze von Änderungen, ohne dass ihre Arbeit überschrieben wurde.  
  
   Dieses Beispiel funktioniert nur bei Änderungen an separaten Dateien. Es ist unvermeidlich, dass unabhängige Anpassungen Änderungen innerhalb einer einzelnen Datei erfordern. Denken Sie auf der Grundlage dieses Beispiels daran, dass Entwickler B die Ansicht "Aktive Kontakte" angepasst hat, während Entwickler A dies auch tat. Im nächsten Beispiel ist jedoch die Reihenfolge der Ereignisse wichtig. Der vollständige Prozess ist wie folgt.  
  
8. Entwickler A und Entwickler B arbeiten beide an derselben Lösung.  
  
9. Auf unabhängigen Computern erhalten beide die neuesten Quellen der Lösung von der Quellcodeverwaltung, packen und importieren eine nicht verwaltete Lösungs-ZIP-Datei in unabhängige Organisationen.  
  
10. Entwickler A passt die "Aktive Kontakte"-Systemansicht und das Hauptformular für die Kontaktentität an.  
  
11. Entwickler B passt die Hauptformular für die Kontoentität an und ändert die Ansicht "Aktive Kontakte".  
  
12. Beide Entwickler exportieren eine nicht verwaltete Lösungs- ZIP-Datei und extrahieren sie.  
  
    1.  Entwickler A muss eine Datei für das Kontakthauptformular und eine Datei für Ansicht "Aktive Kontakte" auschecken.  
  
    2.  Entwickler B muss eine Datei für das Kontohauptformular und eine Datei für Ansicht "Aktive Kontakte" auschecken.  
  
13. Entwickler A ist zuerst fertig.  
  
    1.  Bevor er seine Arbeit an die Quellcodeverwaltung übergibt, muss er die neuesten Quellen erhalten, um sicherzustellen, dass keine vorherigen Eincheckungen im Konflikt mit seinen Änderungen stehen.  
  
    2.  Es gibt keine Konflikte, deshalb kann er seine Arbeit übergeben.  
  
14. Entwickler B. ist nach Entwickler A fertig.  
  
    1.  Bevor er seine Arbeit übergibt, muss er die neuesten Quellen erhalten, um sicherzustellen, dass keine vorherigen Eincheckungen im Konflikt mit seinen Änderungen stehen.  
  
    2.  Es gibt einen Konflikt, da die Datei für "Aktive Kontakte" geändert wurde, seit er zuletzt die neuesten Quellen abgerufen hat.  
  
    3.  Entwickler B muss den Konflikt auflösen. Es ist möglich, dass die Funktionen des verwendeten Quellcodeverwaltungssystems diesen Prozess unterstützen; andernfalls bestehen die folgenden Möglichkeiten.  
  
        1.  Entwickler B kann über die Quellcodeverwaltungshistorie, falls verfügbar, sehen, dass Entwickler A die Änderung vorgenommen hat. Beide Entwickler können direkt über die Änderung sprechen. Dann muss Entwickler B lediglich seine Organisation mit der besprochenen Änderung aktualisieren. Anschließend exportiert, extrahiert und überschreibt er die fragliche Datei und reicht sie ein.  
  
        2.  Die Quellcodeverwaltung kann seine lokale Datei überschreiben. Entwickler packt B die Lösung und importiert sie in seine Organisation, dann prüft er den Status der Ansicht und nimmt entsprechende Anpassungen vor. Anschließend kann der die fragliche Datei exportieren, extrahieren und überschreiben.  
  
        3.  Wenn die vorherige Änderung als unnötig angesehen werden kann, erlaubt Entwickler B, dass seine Kopie der Datei die Version in der Quellcodeverwaltung überschreibt, und reicht sie ein.  
  
    Ob in gemeinsam genutzten oder unabhängigen Organisationen, die Team-Entwicklung von "CDS für Apps"-Lösungen erfordert, dass alle, die an einer gemeinsamen Lösung aktiv arbeiten, die Arbeit der anderen Beteiligten kennen. Das SolutionPackager-Tool beseitigt diese Notwendigkeit nicht vollständig, erlaubt aber das einfache Zusammenführen nicht im Konflikt stehender Änderungen auf Quellcodeverwaltungsebene und meldet proaktiv die Komponenten, bei denen Konflikte aufgetreten sind.  
  
    Die folgenden Abschnitte enthalten die generischen Prozesse für die effektive Verwendung des SolutionPackager-Tools in der Quellcodeverwaltung bei der Entwicklung in Teams. Diese funktionieren gleichermaüen in unabhängigen und in gemeinsam genutzten Entwicklungsorganisationen, obwohl im letzteren Fall der Export und die Extrahierung natürlich alle Änderungen beinhalten, die innerhalb der Lösung vorgenommen wurden, und nicht nur die, die der Entwickler vorgenommen hat, der den Export durchführt. Entsprechend tritt beim Import einer Lösungs-ZIP-Datei das natürliche Verhalten des Überschreibens aller Komponenten auf.  
  
<a name="create_sol"></a>   
## <a name="create-a-solution"></a>Erstellen einer Lösung  
 Die folgende Prozedur identifizeirt die typischen Schritte bei der ersten Erstellung einer Lösung.  
  
1. Erstellen Sie in einer sauberen Organisation eine Lösung auf dem „CDS für Apps”-Server, und erstellen Sie dann nach Bedarf die Komponenten, oder fügen Sie sie hinzu.  
  
2. Wenn Sie bereit sind zum Einchecken, gehen Sie wie folgt vor.  
  
   1.  Exportieren Sie die nicht verwaltete Lösung.  
  
   2.  Extrahieren Sie mithilfe des SolutionPackager-Tools die Lösung in Komponentendateien.  
  
   3.  Fügen Sie aus diesen extrahierten Komponentendateien die erforderlichen Dateien der Quellcodeverwaltung hinzu.  
  
   4.  Übergeben Sie diese Änderungen an die Quellcodeverwaltung.  
  
<a name="modify_sol"></a>   

## <a name="modify-a-solution"></a>Ändern einer Lösung  
 Die folgende Prozedur identifizeirt die typischen Schritte beim Ändern einer vorhandenen Lösung.  
  
1. Synchronisieren Sie die neuesten Lösungskomponentendateiquellen, oder rufen Sie sie ab.  
  
2. Packen Sie mit dem SolutionPackager-Tool die Komponentendateien in eine nicht verwaltete ZIP-Lösungsdatei.  
  
3. Importieren Sie die Datei der nicht verwalteten Lösung in eine Organisation.  
  
4. Passen Sie die Lösung nach Bedarf an.  
  
5. Wenn Sie bereit, die Änderungen in Quellsteuerelement sicherzustellen, die folgenden Schritte aus.  
  
   1.  Exportieren Sie die nicht verwaltete Lösung.  
  
   2.  Extrahieren Sie mithilfe des SolutionPackager-Tools die exportierte Lösung in Komponentendateien.  
  
   3.  Synchronisieren Sie die neuesten Quellen, oder rufen Sie sie aus der Quellcodeverwaltung ab.  
  
   4.  Lösen Sie eventuelle Konflikte.  
  
   5.  Übergeben Sie die Änderungen an die Quellcodeverwaltung.  
  
   Die Schritte 2 und 3 müssen ausgeführt werden, bevor weitere Anpassungen in der Entwicklungsorganisation vorgenommen werden. In Schritt 5 muss Schritt b vor Schritt c abgeschlossen werden.  
  
### <a name="see-also"></a>Siehe auch  
 [Dateireferenz von Lösungskomponenten (SolutionPackager)](solution-component-file-reference-solutionpackager.md)<br/>  
 [Verwenden des SolutionPackager-Tools, um eine Lösungsdatei zu komprimieren und zu extrahieren](compress-extract-solution-file-solutionpackager.md)