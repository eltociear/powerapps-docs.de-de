---
title: Anzeigen von Portal-Fehlerprotokollen und speichern in Azure BLOB Storage | MicrosoftDocs
description: Erfahren Sie, wie Sie Portal Fehlerprotokolle anzeigen und in Ihrem Azure BLOB Storage-Konto speichern.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0b8482108be50c07c229d2c283391d96624e6884
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977264"
---
# <a name="view-portal-error-logs"></a>Anzeigen von Fehlerprotokollen für ein Portal

Als Portaladministrator oder Entwickler können Sie powerapps-Portale verwenden, um eine Website für Ihre Kunden zu erstellen. Eine häufige Aufgabe für einen Entwickler besteht darin, Probleme während der Entwicklung des Portals zu debuggen. Zur Unterstützung des Debuggens können Sie auf detaillierte Fehlerprotokolle zugreifen, wenn Sie Probleme in Ihrem Portal haben. Es gibt mehrere Möglichkeiten, Fehlerprotokolle für ihre Portale zu erhalten.

## <a name="custom-error"></a>Benutzerdefinierter Fehler

Wenn eine serverseitige Ausnahme in Ihrem Portal auftritt, wird standardmäßig eine angepasste Fehlerseite mit einer benutzerfreundlichen Fehlermeldung angezeigt. Informationen zum Konfigurieren der Fehlermeldung finden Sie unter [Anzeigen einer benutzerdefinierten Fehlermeldung](#display-a-custom-error-message).

Es ist jedoch besser, die ausführliche Fehlerseite ASP.net zu Debuggingzwecken auch als gelber Screen of Death (Ysod) bekannt anzuzeigen. Auf der Seite mit den detaillierten Fehlern können Sie den vollständigen Stapel von Server Fehlern erhalten.

> [!div class=mx-imgBorder]
> ![Gelber Bildschirm mit](../media/ysod.png "dem gelben Bildschirm des Todes")

Um Ysod zu aktivieren, müssen Sie [benutzerdefinierte Fehler](#disable-custom-error) in Ihrem Portal deaktivieren.

> [!NOTE]
> Es empfiehlt sich, benutzerdefinierte Fehler nur zu deaktivieren, wenn Sie sich in der Entwicklungsphase befinden, und benutzerdefinierte Fehler nach dem Live Vorgang zu aktivieren.

Weitere Informationen zu benutzerdefiniertem Fehler: [Anzeigen einer benutzerdefinierten Fehlerseite](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>Benutzerdefinierten Fehler deaktivieren

Sie können benutzerdefinierte Fehler in Portalen deaktivieren, um die ausführliche Ausnahme Meldung anzuzeigen, wenn eine serverseitige Ausnahme in Ihrem Portal auftritt.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu den **Portal Aktionen** , > **benutzerdefinierte Fehler zu deaktivieren**.

   > [!div class=mx-imgBorder]
   > ![Benutzerdefinierten]Fehler beim(../media/disable-custom-errors.png "Deaktivieren des benutzerdefinierten") Fehlers deaktivieren

3. Wählen Sie in der Bestätigungsmeldung die Option **Deaktivieren** aus. Während benutzerdefinierte Fehler deaktiviert werden, wird das Portal neu gestartet und ist nicht verfügbar. Eine Meldung wird angezeigt, wenn benutzerdefinierte Fehler deaktiviert werden.

### <a name="enable-custom-error"></a>Benutzerdefinierten Fehler aktivieren

Sie können benutzerdefinierte Fehler in Portalen aktivieren, um anstelle von Ysod eine professionell aussehende Seite anzuzeigen. Diese Seite enthält sinnvolle Informationen, wenn in der Anwendung eine Ausnahme auftritt.

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu den **Portal Aktionen** , > **benutzerdefinierte Fehler zu aktivieren**.

   > [!div class=mx-imgBorder]
   > ![Benutzerdefinierten Fehler]beim(../media/enable-custom-errors.png "Aktivieren des benutzerdefinierten") Fehlers aktivieren

3. Wählen Sie in der Bestätigungsmeldung die Option **aktivieren** aus. Wenn benutzerdefinierte Fehler aktiviert sind, wird das Portal neu gestartet und ist nicht verfügbar. Eine Meldung wird angezeigt, wenn benutzerdefinierte Fehler aktiviert sind.

> [!NOTE]
> - Wenn Sie die Instanz ändern, mit der das Portal verbunden ist, wird die Einstellung benutzerdefinierte Fehler auf Aktiviert festgelegt. Wenn erforderlich, müssen Sie die benutzerdefinierten Fehler erneut deaktivieren.
> - Sie dürfen benutzerdefinierte Fehler nicht aktivieren oder deaktivieren, wenn die Instanz, mit der das Portal verbunden ist, geändert wird. Andernfalls wird eine Fehlermeldung angezeigt.

### <a name="display-a-custom-error-message"></a>Anzeigen einer benutzerdefinierten Fehlermeldung

Sie können Ihr Portal so konfigurieren, dass ein benutzerdefinierter Fehler anstelle eines generischen Fehlers angezeigt wird.

Um einen benutzerdefinierten Fehler zu definieren, verwenden Sie den Inhalts Ausschnitt `Portal Generic Error`. Der Inhalt, der in diesem Ausschnitt definiert ist, wird auf der Fehlerseite angezeigt. Dieser Inhalts Ausschnitt ist standardmäßig nicht verfügbar und muss erstellt werden. Der **Inhaltstyp** für den Inhalt kann **Text** oder **HTML**sein. Informationen zum Erstellen oder Bearbeiten des Inhalts Ausschnitts finden Sie unter [Anpassen von Inhalten mithilfe von Inhalts Ausschnitten](https://docs.microsoft.com/dynamics365/customer-engagement/portals/customize-content-snippets).

> [!NOTE]
> Wenn Liquid-Code im Inhalts Ausschnitt geschrieben wird, wird er übersprungen und nicht gerendert.

Wenn Sie benutzerdefinierte Fehler aktivieren, wird die Meldung in der folgenden Struktur auf der Fehlerseite angezeigt:

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

Im folgenden finden Sie ein Beispiel für eine benutzerdefinierte Fehlermeldung, bei der ein Inhalts Ausschnitt des Typs HTML verwendet wird:

Dies ist ein benutzerdefinierter Fehler. Bitte melden Sie ein Support Ticket mit Screenshot des Fehlers, indem Sie hier klicken.

> [!div class=mx-imgBorder]
> Benutzerdefinierte(../media/custom-error-message.png "Fehler") Meldung für ![benutzerdefinierte Fehlermeldung]

> [!NOTE]
> Wenn das Portal einen Inhalts Ausschnitt nicht abrufen kann, weil keine Verbindung mit Common Data Service hergestellt werden kann oder wenn der Code Ausschnitt in Common Data Service nicht verfügbar ist, wird eine Fehlermeldung angezeigt.

## <a name="access-portal-error-logs"></a>Zugriffs Portal-Fehlerprotokolle

Nachdem Sie das Portal entwickelt und veröffentlicht haben, müssen Sie weiterhin in der Lage sein, auf Portal Protokolle zuzugreifen, um von ihren Kunden gemeldete Probleme zu debuggen. Für den Zugriff auf die Protokolle können Sie das Portal so konfigurieren, dass alle Anwendungsfehler an ein Azure BLOB Storage-Konto gesendet werden, das Sie besitzen. Durch den Zugriff auf Portal-Fehlerprotokolle können Sie effizient auf Kunden Abfragen reagieren, da Sie Details zum Problem haben. Um Portal Fehlerprotokolle in Azure BLOB Storage zu erhalten, müssen Sie die Diagnoseprotokollierung über das powerapps-Portal Admin Center aktivieren.

> [!NOTE]
> Wenn Sie die Common Data Service Instanz ändern, mit der Ihr Portal verbunden ist, ist die Diagnoseprotokollierung deaktiviert. Sie müssen die Diagnoseprotokollierung erneut aktivieren.

### <a name="enable-diagnostic-logging"></a>Aktivieren der Diagnoseprotokollierung

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu den **Portal Aktionen** > aktivieren Sie die **Diagnoseprotokollierung**.

   > [!div class=mx-imgBorder]
   > ![Aktivieren der Diagnoseprotokollierung](../media/enable-diagnostic-logging.png "Aktivieren der Diagnoseprotokollierung")

3. Geben Sie im Fenster **Diagnoseprotokollierung aktivieren** die folgenden Werte ein:

   - **Verbindungs Zeichenfolge Azure BLOB Storage Dienstanbieter**: URL des Azure BLOB Storage Dienstanbieter zum Speichern der Portal Fehlerprotokolle. Die maximale Länge der URL beträgt 2048 Zeichen. Wenn die URL länger als 2048 Zeichen ist, wird eine Fehlermeldung angezeigt. Weitere Informationen zur Verbindungs Zeichenfolge: [Konfigurieren von Azure Storage Verbindungs](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string) Zeichenfolgen
   - **Wählen Sie Beibehaltungs Dauer**: Dauer für die Beibehaltung der Portal Fehlerprotokolle im BLOB-Speicher aus. Die Fehlerprotokolle werden nach der ausgewählten Dauer gelöscht. Sie können einen der folgenden Werte auswählen:
     - 1 Tag
     - 7 Tage
     - 30 Tage
     - 60 Tage
     - 90 Tage
     - 180 Tage
     - Immer

   Standardmäßig beträgt die Beibehaltungs Dauer 30 Tage.
  
   > [!div class=mx-imgBorder]
   > ![Diagnose Protokollierungs Fenster]aktivieren Fenster zum(../media/enable-diagnostic-logging-window.png "Aktivieren der Diagnoseprotokollierung")

4. Klicken Sie auf **Konfigurieren**.

Nachdem die Diagnoseprotokollierung konfiguriert wurde, wird ein neuer BlobContainer für die **telemetrieprotokolle** in Ihrem Azure Storage-Konto erstellt, und die Protokolle werden in die BLOB-Dateien geschrieben, die im Container gespeichert sind. Der folgende Screenshot zeigt den BlobContainer für **telemetrieprotokolle** in Azure Storage-Explorer:

> [!div class=mx-imgBorder]
> ![Azure-Blog Speicherkonto](../media/azure-blob-storage.png "Azure-blobspeicherkonto")

Wenn die Diagnoseprotokollierung erfolgreich aktiviert wurde, wird die folgende Aktion verfügbar:
- **Aktualisieren der Konfiguration der Diagnoseprotokollierung**: Hiermit können Sie die Konfiguration der Diagnoseprotokollierung für das Portal aktualisieren oder entfernen.
- **Deaktivieren der Diagnoseprotokollierung**: Hiermit können Sie die Konfiguration der Diagnoseprotokollierung für das Portal deaktivieren.
 
### <a name="update-diagnostic-logging"></a>Aktualisieren der Diagnoseprotokollierung

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu den **Portal Aktionen** > aktualisieren Sie die **Diagnose Protokollierungs Konfiguration**.

   > [!div class=mx-imgBorder]
   > Aktualisieren der Konfiguration der Diagnose ![Protokollierung](../media/update-diagnostic-logging.png "Aktualisieren der Konfiguration der Diagnose")

3. Geben Sie im Konfigurationsfenster für die Diagnoseprotokollierung aktualisieren die folgenden Werte ein:
   - **Möchten Sie die Verbindungs Zeichenfolge des Azure BLOB Storage Dienstanbieter aktualisieren?** : Hiermit können Sie angeben, ob die Verbindungs Zeichenfolge des Azure BLOB Storage Dienstanbieter aktualisiert werden soll. Standardmäßig ist diese Option ausgewählt.
   - **Verbindungs Zeichenfolge Azure BLOB Storage Dienstanbieter**: URL des Azure BLOB Storage Dienstanbieter zum Speichern der Portal Fehlerprotokolle. Die maximale Länge der URL kann 2048 Zeichen umfassen. Wenn die URL länger als 2048 Zeichen ist, wird eine Fehlermeldung angezeigt. Dieses Feld wird nur angezeigt, wenn das Kontrollkästchen möchten **Sie die Verbindungs Zeichenfolge des Azure BLOB Storage Dienstanbieter aktualisieren?** aktiviert ist. Weitere Informationen zur Verbindungs Zeichenfolge: [Konfigurieren von Azure Storage Verbindungs](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string) Zeichenfolgen
   - **Wählen Sie Beibehaltungs Dauer**: Dauer für die Beibehaltung der Portal Fehlerprotokolle im BLOB-Speicher aus. Die Fehlerprotokolle werden nach der ausgewählten Dauer gelöscht. Sie können einen der folgenden Werte auswählen:
     - 1 Tag
     - 7 Tage
     - 30 Tage
     - 60 Tage
     - 90 Tage
     - 180 Tage
     - Immer

   Standardmäßig beträgt die Beibehaltungs Dauer 30 Tage.

   > [!div class=mx-imgBorder]
   > ![Konfigurationsfenster zum Aktualisieren der Diagnoseprotokollierung](../media/update-diagnostic-logging-window.png "Update Konfigurationsfenster für Diagnoseprotokollierung")

4. Klicken Sie auf **Aktualisieren**.

### <a name="disable-diagnostic-logging"></a>Deaktivieren der Diagnoseprotokollierung

1. Öffnen Sie das [powerapps-Portal Admin Center](admin-overview.md).

2. Wechseln Sie zu den **Portal Aktionen** > deaktivieren Sie die **Diagnoseprotokollierung**.

   > [!div class=mx-imgBorder]
   > ![Deaktivieren der Diagnoseprotokollierung](../media/disable-diagnostic-logging.png "Deaktivieren der Diagnoseprotokollierung")

3. Klicken Sie in der Bestätigungsmeldung auf **Deaktivieren** .

## <a name="display-plugin-error"></a>Anzeige des Plug-ins

Ein anderes Szenario, das häufig bei der Entwicklung eines Portals auftritt, ist ein Fehler, der von benutzerdefinierten Plug-ins und Geschäftslogik generiert wird, die in ihrer Common Data Service Umgebung geschrieben Auf diese Fehler kann im Allgemeinen durch [Deaktivieren von benutzerdefinierten Fehlern](#disable-custom-error) oder [Aktivieren der Diagnoseprotokollierung](#enable-diagnostic-logging)zugegriffen werden. In einigen Fällen ist es jedoch schneller, diese Fehler direkt im Portal anzuzeigen, um das Problem schneller zu diagnostizieren. Zu diesem Zweck können Sie das Portal so konfigurieren, dass benutzerdefinierte Plug-in-Fehler von Common Data Service auf dem Portal Bildschirm angezeigt werden.

Erstellen Sie zum Anzeigen von benutzerdefinierten Plug-in-Fehlern die Website Einstellung `Site/EnableCustomPluginError` und legen Sie Ihren Wert auf true fest. Die benutzerdefinierten Plug-in-Fehler werden auf dem Bildschirm anstelle eines generischen Fehlers angezeigt. Der Fehler zeigt nur den Nachrichten Teil des Plug-in-Fehlers und nicht die komplette Stapel Überwachung an.

Es folgen die Bildschirme, in denen benutzerdefinierte Plug-in-Fehler auftreten 
- Entitäts Liste 
    - Abrufen von Datensätzen 
- Entitäts Formular 
    - Abrufen 
    - Erstellen/aktualisieren usw. 
- Web Forms 
    - Abrufen 
    - Erstellen/aktualisieren usw.

Wenn die Standort Einstellung nicht vorhanden ist, wird Sie standardmäßig als falsch behandelt, und Plug-in-Fehler werden nicht angezeigt.
