---
title: Testen der Webhook-Registrierung mit der Anforderungsprotokollierungs-Website (Common Data Service) | Microsoft-Dokumentation
description: Um die kontextbezogenen Daten zu verstehen, die mit einem Webhook übergeben werden, ist die Verwendung einer Anforderungsprotokoll-Website nützlich, um die Daten zu untersuchen. In diesem Thema wird beschrieben, wie Sie dies durchführen.
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
ms.openlocfilehash: a92de35959665dd99eae405c10f2b38d6fd0c15a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155254"
---
# <a name="test-webhook-registration-with-request-logging-site"></a>Webhook-Registrierung mit Anforderungsprotokollierungs-Website testen 

Ehe Sie einen Service erstellen oder konfigurieren, um Webhooks zu konsumieren, sollten Sie testen, welche Daten der Service empfängt, sodass Sie wissen, welche Art von Daten Sie verarbeiten müssen. Zu diesem Zweck können Sie eine oder mehrere Anforderungsanmelde-Websites nutzen. Zum Zwecke dieses Beispiels führen wir [Webhook-Tester](https://webhook.site) aus, um ein Ziel für die Webhook-Anforderungen zu erstellen. Verwenden Sie die folgenden Schritte:

1. Wechseln Sie zu [https://webhook.site](https://webhook.site). In der oberen rechten Ecke grüne wird die Schaltfläche **Kopieren** angezeigt.
    ![Kopierschaltfläche des Webhook-Testers](media/webhook-tester-copy-button.png)
1. Verwenden Sie die Schaltfläche **Kopieren**, um die URL zu kopieren. Lassen Sie diese Seite geöffnet.
1. Verwenden Sie das Plug-In-Registrierungstool, um einen neuen Webhook zu registrieren, wie in [Registrieren eines Webhooks](register-web-hook.md) beschrieben. 
    1. Verwenden Sie die in Schritt 2 kopierte URL als die **Endpunkt-URL**. 
    1. Legen Sie einen Namen und alle gewünschten Authentifizierungseigenschaften fest. Webhook-Tester wertet diese Werte nicht so aus, wie dies ein tatsächliche Website, die Daten verarbeitet, tut. Sie können aber sehen, wie sie übergeben werden.
1. Verwenden Sie das Plug-In-Registrierungstool, um einen Schritt mit dem Webhook zu registrieren, den Sie in Schritt 4 erstellt haben, wie in [Registrieren eines Schritts für einen Webhook](register-web-hook.md#register-a-step-for-a-webhook) beschrieben. 
    1. Stellen Sie sicher, dass Sie ein Ereignis verwenden, das Sie auf einfache Weise ausführen können, indem Daten in der Common Data Service-Anwendung verarbeitet werden, beispielsweise Aktualisieren einer Kontaktentität.
1. Verwenden Sie die Common Data Service-App, um den Vorgang auszuführen, um das Ereignis auszulösen.
1. Nachdem Sie das Ereignis ausgelöst haben, kehren Sie zur Webhook-Tester-Seite aus Schritt 2 zurück. Sie sollten sehen, dass die Seite aktualisiert wurde, um die Daten anzuzeigen, die an die Anforderung übergeben wurden:

    ![Ein Beispiel für eine Anforderung, die auf der Webhook-Tester-Website protokolliert ist](media/webhook-tester-example.png)

    > [!TIP]
    > Verwenden Sie die Option **JSON formatieren**, damit das JSON, das an den Text der Anforderung zurückgegeben wird, besser lesbar ist.

## <a name="next-steps"></a>Nächste Schritte

[Verwenden Sie Webhooks zum Erstellen externer Handler für Serverereignisse](use-webhooks.md)

### <a name="see-also"></a>Siehe auch
[Registrieren eines Webhooks](register-web-hook.md)