---
title: Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher | MicrosoftDocs
description: Informationen zum Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher
ms.custom: ''
ms.date: 12/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 313e33760a2bc3daf0ac645a8b99d3be22455675
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2019
ms.locfileid: "2895150"
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher

Sie können Dataflows konfigurieren, um ihre Daten im Azure Data Lake Storage Gen2-Konto Ihrer Organisation zu speichern. In diesem Artikel werden die wesentlichen Schritte für diesen Vorgang beschrieben und er enthält Anweisungen und bewährte Methoden. 

> [!IMPORTANT]
> Die Funktion Datenfluss mit analytischen Entitäten verwendet den Dienst In Data Lake exportieren, der möglicherweise ein unterschiedliches Maß an Compliance, Datenschutz, Sicherheit und Datenstandortverpflichtungen bietet. Weitere Informationen über den Service **In Data Lake exportieren** finden Sie im [Blog-Artikel](https://go.microsoft.com/fwlink/?linkid=2109088).

Es gibt einige Vorteile beim Konfigurieren von Dataflows zum Speichern der zugehörigen Definitionen und Datendateien in Ihrem Data Lake, u. a. folgende:
- Azure Data Lake Storage Gen2 bietet einen enorm skalierbaren Speicherraum für Daten.
- Dataflow-Daten und -definitionsdateien können durch Entwickler Ihrer IT-Abteilung genutzt werden, um Azure-Daten und KI-Dienste (Künstliche Intelligenz) wie in den GitHub-Beispielen der Azure-Datendienste veranschaulicht zu nutzen.
- Damit können Entwickler in Ihrer Organisation mithilfe von Entwicklerressourcen für Dataflows und Azure Dataflow-Daten in interne Anwendungen und branchenspezifische Lösungen integrieren.

## <a name="requirements"></a>Anforderungen
Sie benötigen Folgendes, um Azure Data Lake Storage Gen2 für Dataflows zu verwenden:
- Eine Power Apps-Umgebung. Sie können mit jedem Power Apps-Plan Dataflows mit Azure Data Lake Storage Gen2 als Ziel erstellen. Sie müssen in Umgebungen als Entwickler autorisiert werden. 
- Ein Azure-Abonnement. Sie benötigen ein Azure-Abonnement, um Azure Data Lake Storage Gen2 zu verwenden.
- Eine Ressourcengruppe. Sie können eine bereits vorhandene Ressourcengruppe nutzen oder eine neue erstellen.
- Ein Azure Storage-Konto. Bei dem Speicherkonto muss die Funktion "Data Lake Storage Gen2" aktiviert sein.

> [!TIP]
> Wenn Sie kein Azure-Abonnement haben, [erstellen Sie ein kostenloses Testkonto](https://azure.microsoft.com/free/), bevor Sie starten.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-platform-dataflows"></a>Bereiten Sie Azure Data Lake Storage Gen2 für Power Platform-Dataflows vor
Bevor Sie Ihre Umgebung mit einem Azure Data Lake Storage-Gen2-Konto konfigurieren, müssen Sie ein Speicherkonto erstellen und konfigurieren. Hier sind die Anforderungen für Power Platform-Dataflows:
1.  Das Speicherkonto muss im selben Azure Active Directory-Mandanten wie Ihr Power Apps-Mandant erstellt werden.
2.  Es wird empfohlen, das Speicherkonto in derselben Region wie die Power Apps-Umgebung zu erstellen, in der es verwendet werden soll. Um zu bestimmen, wo Ihre Power Apps-Umgebung ist, wenden Sie sich an den Umgebungsadministrator.
3.  Bei dem Speicherkonto muss die Funktion für den hierarchischen Namespace aktiviert sein.
4.  Dir muss eine Besitzerrolle im Speicherkonto zugewiesen werden.

In den folgenden Abschnitten werden Sie durch die erforderlichen Schritte für die Konfiguration Ihres Azure Data Lake Storage Gen2-Kontos geführt.

## <a name="create-the-storage-account"></a>Erstellen des Speicherkontos
Folgen Sie den Schritten unter [Erstellen eines Azure Data Lake Storage Gen2-Speicherkontos](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).
1.  Stellen Sie sicher, dass Sie dieselbe Region wie für Ihren -Mandanten auswählen und Ihren Speicher als SpeicherV2 (universell v2) festlegen.
2.  Stellen Sie sicher, dass Sie die Funktion für den hierarchischen Namespace aktivieren. 
3.  Wir empfehlen, die Replikationseinstellung auf "Georedundanter Speicher (RA-GRS) mit Leseberechtigung" festzulegen.

## <a name="connect-your-azure-data-lake-storage-gen2-to-power-apps"></a>Verbinden von Azure Data Lake Storage Gen2 mit Power Apps
Sobald Sie Ihr Azure Data Lake Storage Gen2-Konto im Azure-Portal eingerichtet haben, können Sie es mit einem bestimmten Dataflow oder einer Power Apps-Umgebung verbinden. Durch die Verbindung eines Lakes mit einer Umgebung können andere Entwickler und Administratoren in der Umgebung Dataflows erstellen, bei denen ihre Daten auch im Lake Ihrer Organisation gespeichert werden. 

Führen Sie diese Schritte aus, um Ihr Azure Data Lake Storage Gen2-Konto mit dem Dataflow zu verbinden:
1.  Melden Sie sich in [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und überprüfen Sie, in welcher Umgebung Sie sich befinden. Der Umgebungs-Schnellzugriff befindet sich auf der rechten Seite der Kopfzeile. 
2. Wählen Sie im linken Navigationsbereich den Abwärtspfeil neben **Daten** aus.

   ![Registerkarte für Power Apps-Entwicklerportaldaten](media/powerapps-portal-data.png)

3. Wählen Sie in der daraufhin angezeigten Liste die Option **Dataflows** und dann in der Befehlsleiste die Option **Neuer Dataflow** aus.

   ![Erstellen eines neuen Dataflows](media/new-dataflow.png) 

4. Wählen Sie die gewünschten analytischen Entitäten aus. Diese Entitäten geben an, welchen Daten Sie im Azure Data Lake Store Gen2-Konto Ihrer Organisation speichern möchten. 

   ![Auswählen analytischer Entitäten](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>Auswählen des Speicherkontos zur Nutzung für den Dataflow-Speicher
Wenn ein Speicherkonto noch nicht mit der Umgebung verknüpft wurde, erscheint ein Dialogfeld **Link zum Data Lake**. Sie müssen sich anmelden und den Data Lake suchen, den Sie im vorherigen Schritt bereits erstellt haben. In diesem Beispiel wird kein Data Lake mit der Umgebung verknüpft. Daher erscheint eine Aufforderung, in der Sie gebeten werden, einen hinzuzufügen. 


1. Speicherkonto auswählen

    Der Bildschirm **Speicherkonto wählen** wird angezeigt
    
    ![Speicherkonto auswählen](media/select-storage-account.png)
    
2. Wählen Sie **Abonnement-ID** aus dem Speicherkonto aus.
3. Wählen Sie **Ressourcengruppenname**, in dem das Speicherkonto erstellt wurde, aus.
4. Geben Sie den **Namen des Speicherkontos** ein.
5. Wählen Sie **Speichern** aus.

Nachdem diese Schritte erfolgreich abgeschlossen sind, ist Ihr Azure Data Lake Storage Gen2-Konto mit Power Platform Dataflows verbunden, und Sie können fortfahren, einen Dataflow zu erstellen.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen
Einige Überlegungen und Einschränkungen sind zu bendenken, wenn Sie mit Ihrem Dataflow-Speicher arbeiten:
- Die Verknüpfung zum Azure Data Lake Store Gen2-Konto für Dataflow-Speicher wird in der Standardumgebung nicht unterstützt.
- Sobald ein Datenflow-Speicherort für einen Dataflow konfiguriert ist, kann sie nicht mehr geändert werden.
- Standardmäßig kann jedes Mitglied der Umgebung auf Dataflow-Daten mithilfe des Power Platform Dataflow-Konnektors zugreifen. Nur die Besitzer eines Dataflows können jedoch auf dessen Dateien in Azure Data Lake Storage Gen2 direkt zugreifen. Um weitere Benutzer zu berechtigen, direkt auf die Dataflow-Daten im Lake zuzugreifen, müssen Sie sie auf den **CDM-Ordner** des Dataflows im Data Lake oder im Data Lake selbst autorisieren.
- Wenn ein Dataflow gelöscht, wird sein **CDM-Ordner** im Lake ebenfalls gelöscht. 

> [!IMPORTANT]
> Sie sollten Dateien, die von Dataflows im Lake Ihrer Organisation erstellt werden, nicht ändern oder keine Dateien zum **CDM-Ordner** eines Dataflows hinzufügen. Das Ändern von Dateien kann Dataflows schädigen oder deren Verhalten ändern und wird nicht unterstützt. Power Platform Nur Dataflows können Lesezugriff auf die Dateien verleihen, die sie im Lake erstellen. Wenn Sie andere Personen oder Services auf das Dateisystem berechtigen, das von Power Platform Dataflows verwendet wird, verleihen Sie ihnen nur Lesezugriff zu Dateien oder Ordnern in dem Dateisystem.

## <a name="privacy-notice"></a>Datenschutzbestimmungen
Durch Aktivieren der Erstellung von Dataflows mit analytischen Entitäten in Ihrer Organisation über **In Data Lake exportieren** werden Details zum Azure Data Lake Storage-Konto, wie z. B. der Name des Speicherkontos, an den Service In Data Lake exportieren gesendet und dort gespeichert, der sich derzeit außerhalb der PowerApps Compliance-Grenze befindet und möglicherweise weniger oder andere Datenschutz- und Sicherheitsmaßnahmen hat als jene in PowerApps. Beachten Sie, dass Sie die Data Lake-Zuordnung jederzeit entfernen können, um diese Funktion nicht mehr zu nutzen. Ihre Azure Data Lake Storage-Kontodaten werden entfernt aus **Exportieren zu Data Lake** Service.
Weitere Informationen zum Exportieren in Data Lake finden Sie in [diesem Beitrag.](https://go.microsoft.com/fwlink/?linkid=2109088)


## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
*Was muss ich tun, wenn ich zuvor Dataflows im Azure Data Lake Storage Gen2 meiner Organisation erstellt habe und deren Speicherort ändern möchte?*

   Sie können den Speicherort eines Dataflows nicht ändern, nachdem er erstellt wurde.

*Wann kann ich den Dataflow-Speicherort einer Umgebung ändern?*

   Das Ändern des Dataflow-Speicherorts der Umgebung wird derzeit nicht unterstützt. 

## <a name="next-steps"></a>Nächste Schritte
Dieser Artikel hat Anleitungen geliefert, wie man ein Azure Data Lake Storage Gen2-Konto für einen Dataflow-Speicher verbindet. 

Weitere Informationen zu Dataflows, das Common Data Model und Azure Data Lake Storage Gen2 sind in diesen Artikeln zu finden:
- [Self-Service Datenaufbereitung mit Dataflows](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Erstellen und Verwenden von Dataflows in Power Apps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Verbinden Sie Azure Data Lake Storage Gen2 für die Dataflowspeicherung](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Daten zu einer Entität hinzufügen in Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

Weitere Informationen über Azure Storage finden Sie in diesem Artikel:
- [Azure Storage Sicherheitshandbuch](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

Weitere Informationen über das Common Data Model sind in diesen Artikeln zu finden:
- [Common Data Model – Übersicht](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model-Ordner](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM-Modell-Dateidefinition](https://go.microsoft.com/fwlink/?linkid=2045521)

Sie können Fragen in der [Power Apps Community](https://go.microsoft.com/fwlink/?linkid=2099971) stellen.
