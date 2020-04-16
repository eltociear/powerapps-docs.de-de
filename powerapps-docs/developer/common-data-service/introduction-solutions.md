---
title: Einführung in Lösungen | Microsoft Docs
description: Erfahren Sie, wie Lösungen verwendet werden, um Modelle zu erstellen.
services: ''
suite: powerapps
documentationcenter: na
author: shmcarth
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 01/28/2019
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ff175320897f156027cd394cf8319032c9f8a6ff
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156162"
---
# <a name="introduction-to-solutions"></a>Einführung in Lösungen

Anpasser und Entwickler benutzen *Lösungen*, um Softwareeinheiten zu erstellen, zu verpacken und zu verwalten, die die Funktionen von Common Data Service erweitern. Beispielsweise sind Dynamics 365 for Sales-, Marketing-, Customer Service-Apps von Lösungen verfasst. Lösungen werden von Anpassern und Entwicklern verteilt, sodass Organisationen Common Data Service verwenden können, um die Funktionalität für das Unternehmen, angegeben durch die Lösung, zu installieren und zu deinstallieren.

Alle Anpassungen, die Sie an Common Data Service oder einer bereits installierten Lösung vornehmen, sind Teil einer Lösung. Jede Änderung, die Sie haben, wird nachverfolgt, und alle Abhängigkeiten können berechnet werden. Wenn Sie eine verwaltete Lösung exportieren, enthält sie alle Änderungen, die für diese Lösung in einer Datei angewendet wurden, die Sie dann in eine andere Common Data Service-Umgebung importieren können.

Wenn Sie Anpassungen oder Erweiterungen zwischen verschiedenen Common Data Service-Umgebungen übertragen oder Lösungen mit AppSource verteilen möchten, müssen Sie das Lösungsframework kennen.

> [!NOTE]
> Ausführliche Informationen dazu, wie Sie effektiv Lösungen für eine erfolgreiche Implementierung Anwendungslebenszyklusverwaltung (ALM)- wird, finden Sie unter [Whitepaper: Lösungs-Lebenszyklus-Verwaltung](https://www.microsoft.com/download/details.aspx?id=57777)

## <a name="managed-and-unmanaged-solutions"></a>Verwaltete und nicht verwaltete Lösungen

Es gibt zwei Typen von Lösungen: *verwaltet* und *nicht verwaltet*.

Eine **verwaltete** Lösung ist eine abgeschlossene Lösung, die dafür vorgesehen ist, verteilt und installiert zu werden. 
- Sie können die Komponenten einer verwalteten Lösung nicht bearbeiten.
- Verwaltete Lösungen können nicht exportiert werden.
- Sie können nicht verwaltete Anpassungen Komponenten einer verwalteten Lösung hinzufügen. Wenn Sie dies tun, erstellen Sie eine Abhängigkeit zwischen den nicht verwalteten und den verwalteten Anpassungen der Lösung. Wenn eine Abhängigkeit vorhanden ist, kann die verwaltete Lösung nicht deinstalliert werden, nachdem Sie die zunächst entfernen.
- Wenn einer verwalteten Lösung gelöscht (deinstalliert) wird, werden alle Anpassungen und Erweiterungen die darin enthalten sind, entfernt.

  > [!IMPORTANT]
  > Wenn Sie eine verwaltete Lösung deinstallieren, gehen die folgenden Daten verloren: Daten, die in benutzerdefinierten Entitäten gespeichert sind, die Teil der verwalteten Lösung sind, und Daten, die in benutzerdefinierten Attributen gespeichert sind, die Teil der verwalteten Lösung in anderen Entitäten sind, die nicht Teil der verwalteten Lösung sind.

Eine **nicht verwaltete** Lösung ist eine Lösung, die sich immer noch in der Entwicklung befindet oder nicht dafür vorgesehen ist, verteilt zu werden. 
- Während eine Lösung nicht verwaltet ist, können Sie den Vorgang fortsetzen, um Komponenten hinzuzufügen und zu entfernen. 
- Sie können eine nicht verwaltete Lösung exportieren, um nicht verwaltete Anpassungen von einer Umgebung in eine andere zu übertragen.
- Wenn einer nicht verwalteten Lösung gelöscht wird, wird nur der Lösungscontainer sämtlicher Anpassungen, die in einer Anpassung enthalten sind, gelöscht. Alle nicht verwalteten Anpassungen bleiben bestehen und gehören zu der Standardlösung. 
- Wenn die nicht verwaltete Lösung vollständig ist und Sie sie verteilen möchten, exportieren und verpacken möchten, exportieren Sie sie wie eine verwaltete Lösung.

  > [!NOTE]
  > Sie können eine nicht verwaltete Lösung in dieselbe Umgebung importieren, die der Ursprungsvertrag der nicht verwalteten Lösung enthält. Wenn Sie eine verwaltete Lösung testen, wird eine separate Umgebungen benötigt, um sie zu importieren.

## <a name="solution-publishers"></a>Lösungsherausgeber

Jede Lösung ist mit einem Lösungsherausgeber verbunden. Dem Lösungsherausgeber werden Informationen bereitgestellt, wie der Herausgeber kontaktiert werden kann und wie der Anpassungspräfixwert ist. Der Standardwert ist `new`.

Wenn beliebige Schemaänderungen als Teil einer Lösung enthalten sind, wird das Lösungsherausgeberanpassungspräfix mit dem Namen der Schemaelemente verwendet. Alle benutzerdefinierten Aktionen haben auch diesen Wert, der für diese Anfragen angefügt wird. Dies ist dann von Nutzen, da dies eine einfache Erkennung erlaubt, welche Lösungen dem Schemaelement oder der benutzerdefinierten Aktion hinzugefügt werden. Es ist nicht für alle Schemaelemente und benutzerdefinierte Aktionen des Schemas erforderlich, in einer Lösung dasselbe Anpassungspräfix zu verwenden, aber es ist jedoch empfohlen.

> [!IMPORTANT]
> Bevor Sie mit dem Erstellen einer Lösung beginnen, sollten Sie einen Lösungsherausgeberdatensatz erstellen und eine neue Lösung erstellen, die mit diesen verknüpft ist. Sie müssen sicherstellen, dass der Wert einen Anpassungspräfix darstellt, der für Sie Sinn ergibt. 

Die Auswahl des Lösungsherausgebers ist wichtig, wenn Sie ein Update für Lösungen veröffentlichen wollen, die Sie versenden möchten. Ein Update kann für eine verwaltete Lösung mit demselben Herausgeber wie die ursprüngliche verwaltete Lösung angewendet werden. 

Weitere Informationen: [Verwalten von verwaltete Lösungen > Verwaltete Lösungs-Updates erstellen](/dynamics365/customer-engagement/developer/maintain-managed-solutions#create-managed-solution-updates)

## <a name="create-a-solution-publisher-and-solution"></a>Erstellen eines Lösungsherausgebers und einer Lösung 

Um einen Lösungsherausgeber und eine Lösung zu erstellen, müssen Sie zum Common Data Service-Anpassungsbereich navigieren.

Von [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)

1. Wählen Sie das Symbol *Waffel* oben links aus
2. Wählen Sie **Alle Apps**.
3. Suchen Sie nach **Common Data Service – benutzerdefinierte App**.
 Sie können auf die Ellipse (...) klicken und **App anheften** auswählen, sodass die Navigation beim nächsten Mal einfacher ist.
4. Klicken Sie auf die App **Common Data Service – benutzerdefinierte App** und wählen Sie sie aus.
5. Navigieren Sie auf **Einstellungen** > **Anpassung** > **Anpassungen**.

Von [home.dynamics.com](https://home.dynamics.com/)

1. Suchen Sie die Kachel **Common Data Service – benutzerdefiniert** und klicken Sie darauf.
2. Navigieren Sie auf **Einstellungen** > **Anpassung** > **Anpassungen**.

### <a name="create-a-solution-publisher"></a>Erstellen eines Lösungsherausgebers

1. Klicken Sie im Anpassungsbereich und wählen Sie **Herausgeber**
2. Klicken Sie auf **Neu**.
3. Im Herausgeberformular geben Sie einen **Anzeigename** ein. Ein **Namen**-Wert wird basierend auf dem Wert in Anzeigename generiert. Sie können den generierten Wert übernehmen oder einen neuen Namen eingeben.
4. Klicken Sie im Feld **Präfix** und definieren Sie den Anpassungspräfix, der für alle angepassten Schemaelementen angefügt werden sollte, die Sie hinzufügen, wenn Sie die Lösung entwickeln. Der Standardwert ist `new`. Wählen Sie einen Wert aus, der Ihre Organisation darstelle und Personen hilft zu identifizieren, welche Komponenten in Ihrem System von Ihrer Lösung stammt.
5. Ein **Optionswertpräfix**-Wert wird auf Ihrer Auswahl für Anpassungspräfix generiert. Dies ist ein Wert, der für alle möglichen Werte für Optionssatzoptionen angefügt ist, für die Sie Attribute in Ihrer Lösung hinzufügen. Dieser Wert hilft, alle Optionen zu identifizieren, die Sie für die Lösung hinzufügen.
6. Im Abschnitt des Formulars **Kontaktdetails**, können Sie möglicherweise alle Kontaktinformationen hinzufügen, die Sie für Benutzer zur Verfügung stellen möchten, um Ihre Lösung auszuwählen.
7. Klicken oder tippen Sie auf **Speichern und schließen**, wenn Sie fertig sind.

### <a name="create-a-solution"></a>Erstellen einer Lösung

1. Klicken Sie im Anpassungsbereich und wählen Sie **Lösungen**
2. Klicken Sie auf **Neu**.
3. Im Lösungsformular geben Sie einen **Anzeigename** ein. Ein **Namen**-Wert wird basierend auf dem Wert in Anzeigename generiert. Sie können den generierten Wert übernehmen oder einen neuen Namen eingeben.
4. Suchen Sie im Feld **Herausgeber** den Herausgeber, den Sie in [Erstellen eines Lösungsherausgebers](#create-a-solution-publisher) erstellt haben.
5. Wählen Sie im Feld **Version** eine entsprechende Versionen für die Lösung aus, z. B. 1.0.0.0.
6. Wenn Sie fertig sind, klicken Sie auf **Speichern**.

> [!IMPORTANT]
> Wenn Sie eine neue Lösungskomponente erstellen, die in dieser Lösung enthalten ist, können Sie dieser Lösung oder eine andere Lösung, die mit demselben Lösungsherausgeber zugeordnet wird, um ihn hinzuzufügen.
> Für Lösungskomponenten, die im Rahmen einer Lösung einem anderen Lösungsherausgeber zugeordnet werden, können sie in dieser Lösung hinzugefügt werden, aber sie hat möglicherweise inkonsistente Anpassungspräfixwerte.

## <a name="solution-layering"></a>Lösungsebenen

Es ist möglich für zwei verwalteten Lösung, dass sie so installiert werden, dass sie sich widersprechen oder dass gewisse Anpassungen, die für die Organisationen angewendet werden, eine verwaltete Lösung überschreiben. Wie funktioniert die Anwendung?

Das geht, weil Common Data Service verwaltete Lösungen in der Reihenfolge evaluiert, in der sie installiert wurden, und alle Anpassungen, die nicht in einer verwalteten Lösung sind, zuletzt ausgewertet werden.

Im folgenden Diagramm wird erläutert, wie verwaltete Lösungen und nicht verwaltete Anpassungen interagieren, um das Anwendungsverhalten zu steuern.

![Diagramm zeigt Lösungsüberlagerung](media/solution-layering.png)

In diesem Beispiel wird das Standardverhalten, das in der Systemlösung definiert ist, mit verwalteten Lösungen überschrieben oder verwalteten Lösungen angefügt. Alle nicht verwalteten Anpassungen können dann Anpassungen überschreiben oder anfügen, die dann in der Anwendung angezeigt werden

Weitere Informationen: [Einführung in Lösungen > Nicht verwaltete und verwaltete Lösungen](/dynamics365/customer-engagement/developer/introduction-solutions#managed-and-unmanaged-solutions).

## <a name="managed-properties"></a>Verwaltete Eigenschaften

Wenn Sie eine verwaltete Lösung verteilen, kann jeder Benutzer, der Ihre Lösung installiert, ihre eigenen nicht verwalteten Anpassungen darauf integrieren. Diese nciht verwalteten Anpassungen können einer Lösung hinzugefügt werden, die dann als verwaltete Lösung verteilt werden, die von Ihrer Lösung abhängen. Aber was, wenn Sie möchten, dass Benutzer manche Aufgaben nicht ausführen? Ähnlich dem Herausgeber einer verwalteten Lösung können Sie die verwalteten Eigenschaften verwenden, um bestimmte Anpassungen für die Komponenten der verwalteten Lösung zu deaktivieren.

Weitere Informationen: [Bearbeiten von verwalteten Eigenschaften](use-managed-properties.md)

## <a name="modular-solutions"></a>Modulare Lösungen

Sie können das Lösungsframework verwenden, um einen einzelnen Satz von Komponenten zu erstellen, die eine Reihe von Funktionen aufweisen. Jede verwaltete Lösung kann installiert und deinstalliert werden, um die Bereitstellung der Kunden an den ursprünglichen Zustand zurückzukehren. Jede verwaltete Lösung, die Sie erstellen, läuft auf der Systemlösung und Sie können auf die Funktionen zugreifen, die dieser Lösung zugrunde liegen.

Sie können außerdem verwaltete Lösungen erstellen, die auf anderen Lösungen ausgeführt werden, um um eine Reihe von Funktionen zu erstellen, die von unterschiedlichen Lösungen verwendet werden können. Auf diese Weise können Sie ein häufiges Modul als Lösung erstellen und verwalten, um mehrere Lösungen zu unterstützen. Aus diesem Grund müssen Kunden nur Lösungen installieren, die für sie richtig sind und Sie müssen nicht in jeder Lösung dieselben freigegebenen Funktionen mit einbeziehen. Wenn Sie ein Update zur Lösung zurückstellen müssen, das mehrere Lösungen unterstützt, müssen Sie nur das allgemeine Modul aktualisieren.

Kunden, System-Implementierungen und anderer ISV können dann Lösungen auf den Lösung aufbauen, die dann bestimmte Anpassungene rreichen, die sie benötigen.

Wenn ein Satz von Unternehmens-Funktionalitäten aus mehreren Lösungen besteht, werden die zugewiesenen Pakete bezeichnet. Sie können den *Package Deployer* verwenden, um mehrere Lösungen in einer einzelnen installierbaren Einheit zu kombinieren.

## <a name="deploy-solution-packages"></a>Bereitstellen von Lösungspaketen

Verwenden Sie den *Package Deployer*, um ein benutzerdefiniertes Installationsprogramm für ein Paket zu erstellen, das Folgendes umfassen kann: 
- Eine oder mehrere Lösungsdateien.
- Flache Dateien oder exportierte Konfigurationsdateien. 
- Benutzerdefinierter Code, der ausgeführt werden kann, bevor, während oder nachdem das Paket bereitgestellt wurde.
- inhaltsspezifische HTML für das Paket, das bei Start und Ende des Bereitstellungsprozesses angezeigt werden kann. Dies kann nützlich sein, um eine Beschreibung der Lösungen und Dateien bereitzustellen, die im Paket bereitgestellt werden.

Weitere Informationen: [Erstellen von Paketen für den Common Data Service Package Deployer](package-deployer/create-packages-package-deployer.md).

## <a name="team-development-of-solutions"></a>Teamentwicklung von Lösungen

Eine Lösungsdatei ist jedoch eine einzelne Binärdatei, die sich nicht für die Quellcodeverwaltung oder Teamentwicklung anbietet. Es gibt keine Möglichkeit, dass mehrere Entwickler die benutzerdefinierten Komponenten in der Lösung bearbeiten.

Das *SolutionPackager-Tool* löst das Problem der Quellcodeverwaltung und Teamentwicklung von Lösungsdateien. Das Tool identifiziert einzelne Komponenten in der komprimierten Lösungsdatei und extrahiert sie in einzelne Dateien. Das Tool kann eine Lösungsdatei auch neu erstellen, indem die zuvor extrahierten Dateien gepackt werden. Dadurch können mehrere Personen unabhängig voneinander an einer einzelnen Lösung arbeiten und die Änderungen an eine gemeinsame Stelle extrahieren. Da jede Komponente in der Lösungsdatei in mehrere Dateien zerlegt wurde, ist es möglich, Anpassungen zusammenzuführen, ohne vorherige Änderungen zu überschreiben. Eine zweite Verwendungsmöglichkeit des SolutionPackager-Tools ist, dass es von einem automatischen Buildprozess aufgerufen werden kann, um eine komprimierte Lösungsdatei aus zuvor extrahierten Komponentendateien zu generieren, ohne dass eine aktive Common Data Service-Instanz erforderlich ist.

Weitere Informationen: [Lösungstools für die Teamentwicklung](/dynamics365/customer-engagement/developer/solution-tools-team-development)

### <a name="see-also"></a>Siehe auch

[Common Data Service-Entwicklerübersicht](overview.md)
