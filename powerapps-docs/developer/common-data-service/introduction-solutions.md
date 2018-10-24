---
title: Einführung in Lösungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Lösungen zum Erstellen von modellgesteuerten Apps verwendet werden.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bcf89d9c52e1e277f65f7f02013885f30862aa56
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864977"
---
# <a name="introduction-to-solutions"></a>Einführung in Lösungen

Mithilfe von *Lösungen* verfassen, packen und pflegen Benutzer, die Anpassungen vornehmen, und Entwickler Softwareeinheiten, die Common Data Service für Apps erweitern. Die Apps Dynamics 365 for Sales, Marketing und Customer Service beispielsweise bestehen aus Lösungen. Benutzer, die Anpassungen vornehmen, und Entwickler verteilen Lösungen so, dass Organisationen Common Data Service für Apps zum Installieren und Deinstallieren von Geschäftsfunktionen verwenden können, die durch die Lösung definiert werden.

Jede Anpassung, die Sie an Common Data Service für Apps oder einer zuvor installierten Lösung vornehmen, ist Teil einer Lösung. Jede Änderung, die Sie anwenden, wird nachverfolgt, und alle Abhängigkeiten können berechnet werden. Wenn Sie eine verwaltete Lösung exportieren, enthält diese alle Änderungen, die an dieser Lösung vorgenommen wurden in einer Datei, die Sie dann in eine andere Umgebung von Common Data Service für Apps exportieren können.

Zum Transportieren von Anpassungen oder Erweiterungen zwischen verschiedenen Umgebungen von Common Data Service für Apps oder zum Verteilen von Lösungen mithilfe von AppSource, müssen Sie zunächst das Lösungsframework verstehen.

## <a name="managed-and-unmanaged-solutions"></a>Verwaltete und nicht verwaltete Lösungen

Es gibt zwei Arten von Lösungen: *verwaltete* und *nicht verwaltete*.

Eine **verwaltete** Lösung ist eine vollständige Lösung, die verteilt und installiert werden soll. 
- Sie können die Komponenten einer verwalteten Lösung nicht bearbeiten.
- Sie können verwaltete Lösungen nicht exportieren.
- Sie können nicht verwaltete Anpassungen zu den Komponenten einer verwalteten Lösung hinzufügen. Wenn Sie dies tun, erstellen Sie eine Abhängigkeit zwischen Ihren nicht verwalteten Anpassungen und der verwalteten Lösung. Wenn eine Abhängigkeit vorhanden ist, kann die verwaltete Lösung erst deinstalliert werden, wenn Sie die Abhängigkeit entfernt haben.
- Wenn eine verwaltete Lösung gelöscht (deinstalliert) wird, werden alle enthaltenen Anpassungen und Erweiterungen entfernt.

  > [!IMPORTANT]
  > Die folgenden Daten gehen beim Deinstallieren einer verwalteten Lösung verloren: Daten, die in benutzerdefinierten Entitäten gespeichert sind, die Teil der verwalteten Lösung sind, und Daten, die in benutzerdefinierten Attributen gespeichert sind, die Teil der verwalteten Lösung in anderen Entitäten sind, die nicht Teil der verwalteten Lösung sind.

Eine **nicht verwaltete** Lösung ist eine Lösung, die sich noch in der Entwicklung befindet oder nicht verteilt werden soll. 
- Solange eine Lösung nicht verwaltet ist, können Sie ihr Komponenten hinzufügen oder entfernen. 
- Sie können eine nicht verwaltete Lösung exportieren, um nicht verwaltete Anpassungen von einer Umgebung in eine andere zu transportieren.
- Wenn eine nicht verwaltete Lösung gelöscht wird, wird nur der Lösungscontainer der enthaltenen Lösungen gelöscht. Alle nicht verwalteten Anpassungen bleiben wirksam und gehören zur Standardlösung. 
- Wenn die nicht verwaltete Lösung vollständig ist, und Sie sie verteilen möchten, exportieren Sie sie als verwaltete Lösung.

  > [!NOTE]
  > Sie können eine verwaltete Lösung nicht in die gleiche Umgebung importieren, die die ursprüngliche nicht verwaltete Lösung enthält. Zum Testen einer verwalteten Lösung benötigen Sie eine separate Umgebung, in die Sie sie importieren können.

## <a name="solution-publishers"></a>Lösungsherausgeber

Jede Lösung ist mit einem Lösungsherausgeber verknüpft. Der Lösungsherausgeber stellt Informationen zum Kontaktieren des Herausgebers und einen Anpassungspräfixwert bereit. Der Standardwert ist `new`.

Wenn Schemaänderungen als Teil einer Lösung enthalten sind, wird dem Namen des Schemaelemente das Anpassungspräfix des Lösungsherausgebers vorangestellt. Zu Benutzerdefinierten Aktionen wird dieser Wert ebenfalls hinzugefügt. Das ist hilfreich, da damit eine einfache Erkennung der Lösung ermöglicht wird, die dem Schemaelement oder der benutzerdefinierten Aktion hinzugefügt wird. Es ist nicht erforderlich, dass alle Schemaelemente und benutzerdefinierten Aktionen in einer Lösung dasselbe Anpassungspräfix verwenden, aber es wird dringend empfohlen.

> [!IMPORTANT]
> Bevor Sie mit dem Erstellen einer Lösung beginnen, sollten Sie einen Datensatz für den Lösungsherausgeber und eine neue mit dem Herausgeber verknüpfte Lösung erstellen. Sie sollten sicherstellen, dass das Anpassungspräfix einen Wert darstellt, der für Sie sinnvoll ist. 

Die Auswahl Ihres Lösungsherausgebers ist wichtig, wenn Sie ein Update für eine Lösung veröffentlichen möchten, die Sie bereits geliefert haben. Ein Update kann nur auf verwaltete Lösungen mit dem gleichen Herausgeber wie die ursprüngliche verwaltete Lösung angewendet werden. 

Weitere Informationen finden Sie unter [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Pflegen von verwalteten Lösungen > Erstellen von Aktualisierungen einer verwalteten Lösung](/dynamics365/customer-engagement/developer/maintain-managed-solutions#create-managed-solution-updates)

## <a name="create-a-solution-publisher-and-solution"></a>Erstellen eines Lösungsherausgebers und einer Lösung 

Zum Erstellen eines Lösungsherausgebers und einer Lösung müssen Sie zum Anpassungsbereich von Dynamics 365 navigieren.

Auf der Website [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)

1. Klicken Sie auf das *Waffel*-Symbol in der oberen linken Ecke.
2. Klicken Sie im Dropdownmenü auf **Alle Apps**.
3. Suchen Sie nach **Dynamics 365 - custom app** (benutzerdefinierte Dynamics 365-App).
 Sie sollten auf die Auslassungspunkte (...) klicken und **Pin this app** (Diese App anheften) auswählen, damit Sie sie beim nächsten Mal leichter finden.
4. Klicken Sie auf die **Dynamics 365 - custom app** (benutzerdefinierte Dynamics 365-App), und wählen Sie die App aus.
5. Navigieren Sie zu **Einstellungen** > **Anpassung** > **Anpassungen**.

Auf der Website [home.dynamics.com](http://home.dynamics.com/)

1. Suchen Sie nach der Kachel **Dynamics 365 - custom** (Dynamics 365 – Benutzerdefiniert), und klicken Sie darauf.
2. Navigieren Sie zu **Einstellungen** > **Anpassung** > **Anpassungen**.

### <a name="create-a-solution-publisher"></a>Erstellen eines Lösungsherausgebers

1. Klicken Sie im Bereich „Anpassungen“ auf **Herausgeber**.
2. Klicken Sie auf **Neu**.
3. Geben Sie im Formular „Herausgeber“ einen **Anzeigenamen** ein. Der Wert für einen **Namen** wird basierend auf dem Anzeigenamen generiert. Sie können den generierten Wert akzeptieren oder einen neuen Wert angeben.
4. Geben Sie im Feld **Präfix** das Anpassungspräfix an, das den benutzerdefinierten Schemaelementen vorangestellt werden soll, die Sie bei der Entwicklung Ihrer Lösung hinzufügen. Der Standardwert ist `new`. Wählen Sie einen Wert aus, der Ihre Organisation darstellt und bei der Identifizierung der von Ihrer Lösung installierten Komponenten hilft.
5. Ein **Optionswertpräfix**-Wert wird basierend auf dem ausgewählten Anpassungspräfix generiert. Dieser Wert wird allen Werten für Optionen von Optionssätzen vorangestellt, die Sie den Attributen in Ihrer Lösung hinzufügen. Dieser Wert hilft beim Identifizieren von Optionen, die Sie Ihrer Lösung hinzufügen.
6. Im Abschnitt **Kontaktdetails** des Formulars können Sie Kontaktinformationen hinzufügen, die Sie für diejenigen bereitstellen möchten, die Ihre Lösung installieren.
7. Klicken Sie auf **Speichern und schließen**, wenn Sie fertig sind.

### <a name="create-a-solution"></a>Erstellen einer Lösung

1. Klicken Sie im Bereich „Anpassungen“ auf **Lösungen**.
2. Klicken Sie auf **Neu**.
3. Geben Sie im Formular „Lösung“ einen **Anzeigenamen** ein. Der Wert für einen **Namen** wird basierend auf dem Anzeigenamen generiert. Sie können den generierten Wert akzeptieren oder einen neuen Wert angeben.
4. Wählen Sie im Feld **Herausgeber** den Herausgeber aus, den Sie im Schritt [Erstellen eines Lösungsherausgebers](#create-a-solution-publisher) erstellt haben.
5. Wählen Sie im Feld **Version** eine entsprechende Version für Ihre Lösung aus, z.B. 1.0.0.0.
6. Klicken Sie auf **Speichern**, wenn Sie fertig sind.

> [!IMPORTANT]
> Verwenden Sie diese Lösung, wenn Sie eine neue Lösungskomponente erstellen, die in dieser Lösung enthalten sein soll, oder eine andere Lösung, die dem gleichen Lösungsherausgeber zugeordnet ist, um sie hinzuzufügen.
> Lösungskomponenten, die im Kontext einer Lösung erstellt wurden, die einem anderen Lösungsherausgeber zugeordnet ist, können zwar dieser Lösung hinzugefügt werden, jedoch werden für diese möglicherweise inkonsistente Werte für das Anpassungspräfix festgelegt.

## <a name="solution-layering"></a>Lösungsebenen

Es ist möglich, zwei verwaltete Lösungen zu installieren, die einander widersprechen, oder eine verwaltete Lösung durch auf die Umgebung angewendete Anpassungen zu überschreiben. Wie das funktioniert:

Das funktioniert, weil Common Data Service für Apps verwaltete Lösungen nach der Reihenfolge auswertet, in der sie installiert wurden, und weil alle Anpassungen, die sich nicht in einer verwalteten Lösung befinden, zuletzt ausgewertet werden.

Im folgenden Diagramm wird vorgestellt, wie verwaltete Lösungen und nicht verwaltete Anpassungen interagieren, um zu steuern, was zur Laufzeit in einer Anwendung enthalten ist.

![Lösungsebenen in einem Diagramm](media/solution-layering.png)

In diesem Beispiel wird das Standardverhalten, das in der Systemlösung definiert ist, von verwalteten Lösungen überschrieben oder angefügt. Alle nicht verwalteten Anpassungen können dann Anpassungen überschreiben oder anfügen, die in der Anwendung sichtbar sind.

Weitere Informationen finden Sie unter [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Einführung in Lösungen > Verwaltete und nicht verwaltete Lösungen](/dynamics365/customer-engagement/developer/introduction-solutions#managed-and-unmanaged-solutions)

## <a name="managed-properties"></a>Verwaltete Eigenschaften

Wenn Sie eine verwaltete Lösung veröffentlichen, kann jede Person, die Ihre Lösung installiert, ihre eigenen nicht verwalteten Anpassungen auf die Lösung anwenden. Diese nicht verwalteten Anpassungen können dann einer Lösung hinzugefügt werden, die als verwaltete Lösung veröffentlicht wurde und von Ihrer Lösung abhängt. Wie können Sie verhindern, dass jemand dies tut? Als Herausgeber der verwalteten Lösung können Sie verwaltete Eigenschaften verwenden, um bestimmte Anpassungen für die Komponenten Ihrer verwalteten Lösung zu deaktivieren.

Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Developer Guide: Use managed properties (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Verwenden von verwalteten Eigenschaften)](/dynamics365/customer-engagement/developer/use-managed-properties).

## <a name="modular-solutions"></a>Modulare Lösungen

Sie können das Lösungsframework verwenden, um diskrete Komponenten zu erstellen, die eine Reihe von Funktionen bereitstellen. Jede verwaltete Lösung kann installiert und deinstalliert werden, um die Bereitstellung des Kunden in den ursprünglichen Zustand zurückzuversetzen. Jede verwaltete Lösung, die Sie erstellen, wird auf der Systemlösung ausgeführt und kann auf die Funktionen der zugrunde liegenden Lösung zugreifen.

Außerdem können Sie verwaltete Lösungen erstellen, die auf anderen Lösungen ausgeführt werden, um eine Reihe von Funktionen zu erstellen, die von verschiedenen Lösungen verwendet werden können. Auf diese Weise können Sie ein allgemeines Modul als Lösung erstellen und verwalten, um mehrere Lösungen zu unterstützen. Aus diesem Grund müssen Kunden nur die Lösungen installieren, die für sie geeignet sind, und Sie müssen die gleiche freigegebene Funktion nicht in jeder Lösung einschließen. Wenn Sie ein Update für eine Lösung veröffentlichen müssen, die mehrere Lösungen unterstützt, müssen Sie nur das allgemeine Modul aktualisieren.

Kunden, Systemimplementierer und andere unabhängige Softwarehersteller können dann Lösungen auf Ihren Lösungen aufbauen, um bestimmte von ihnen benötigte Anpassungen zu erstellen.

Wenn mehrere Geschäftsfunktionen aus mehreren Lösungen bestehen, werden diese als Pakete bezeichnet. Sie können *Package Deployer* verwenden, um mehrere Lösungen in eine einzelne installierbare Einheit zusammenzufassen.

## <a name="deploy-solution-packages"></a>Bereitstellen von Lösungspaketen

Verwenden Sie *Package Deployer* zum Erstellen eines benutzerdefinierten Installers für ein Paket, das Folgendes enthalten kann: 
- Mindestens eine Lösungsdatei
- Flatfiles oder exportierte Konfigurationsdatendateien 
- Benutzerdefinierter Code, der vor, während oder nach der Bereitstellung des Pakets ausgeführt werden kann.
- HTML-Inhalt für das spezifische Paket, dass am Anfang und am Ende des Bereitstellungsprozesses angezeigt werden kann. Das kann beim Angeben einer Beschreibung der Lösungen und Dateien nützlich sein, die in dem Paket bereitgestellt werden.

Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Developer Guide: Create packages for the Dynamics 365 Package Deployer (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Erstellen von Paketen für Dynamics 365-Package Deployer)](/dynamics365/customer-engagement/developer/create-packages-package-deployer).

## <a name="team-development-of-solutions"></a>Entwicklung von Lösungen im Team

Eine Lösungsdatei ist eine einzelne Binärdatei, die sich nicht für die Quellcodeverwaltung oder Teamentwicklung eignet. Es können nicht mehrere Entwickler an den benutzerdefinierten Komponenten in der Lösung arbeiten.

Das Tool *SolutionPackager* löst das Problem bei der Quellcodeverwaltung und Teamentwicklung von Lösungsdateien. Das Tool identifiziert individuelle Komponenten in der komprimierten Lösungsdateien und extrahiert sie als einzelne Dateien. Das Tool kann eine Lösung auch wiederherstellen, indem es die zuvor extrahierten Dateien packt. Dadurch können mehrere Personen unabhängig voneinander an einer Lösung arbeiten und Änderungen in einen gemeinsamen Speicherort extrahieren. Da jede Komponente in der Lösungsdatei in mehrere Dateien aufgeteilt wird, wird das Zusammenführen von Anpassungen ohne Überschreiben der vorherigen Änderungen ermöglicht. Eine sekundäre Verwendung des SolutionPackager-Tools besteht darin, dass es in einem automatisierten Buildprozess aufgerufen werden kann, um eine komprimierte Lösungsdatei aus zuvor extrahierten Komponentendateien zu generieren, ohne dass eine Instanz von Dynamics 365 aktiv sein muss.

Weitere Informationen finden Sie unter [Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Lösungstools für die Teamentwicklung](/dynamics365/customer-engagement/developer/solution-tools-team-development).

### <a name="see-also"></a>Siehe auch

[Common Data Service for Apps Developer Overview (Übersicht für Entwickler: Common Data Service für Apps)](overview.md)
