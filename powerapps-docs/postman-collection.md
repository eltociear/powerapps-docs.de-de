---
title: Beschreiben eines benutzerdefinierten Connectors mit Postman | Microsoft-Dokumentation
description: Erstellen Sie eine Postman-Sammlung, um benutzerdefinierte Connectors zu registrieren
services: 
suite: powerapps
documentationcenter: 
author: archnair
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/28/2017
ms.author: archanan
ms.openlocfilehash: fd060ff873ee376b7ca886f721d360372c1d13ed
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="describe-a-custom-connector-with-postman"></a>Benutzerdefinierten Connector mit Postman beschreiben
[Postman](https://www.getpostman.com/) ist ein Tool, das Ihre API-Entwicklung schneller und einfacher machen kann. Dieses Tutorial zeigt das Erstellen einer Postman-Sammlung, die Sie dann verwenden können, um auf einfache Weise [Benutzerdefinierte Connectors](register-custom-api.md) in PowerApps zu erstellen.

## <a name="prerequisites"></a>Voraussetzungen
* Installieren Sie die [Postman-App](https://www.getpostman.com/apps)

## <a name="create-a-postman-collection"></a>Erstellen einer Postman-Sammlung
Erstellen wir gemeinsam eine Postman-Sammlung für die [Textanalyse-API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api) aus Azure Cognitive Services. Diese API bestimmt die Sprache, die Stimmung und wichtige Aussagen in den Texten, die Sie ihr übergeben.

1. Der erste Schritt beim Erstellen einer Postman-Sammlung besteht im Erstellen einer Anforderung. Beim Erstellen der Anforderung können Sie das HTTP-Verb, die Anforderungs-URL, Abfrage- oder Pfadparameter, Header und den Anforderungstext festlegen. Weitere Informationen finden Sie in der Postman-Dokumentation unter [Senden von Anforderungen ](https://www.getpostman.com/docs/requests) (Sending Requests). Legen Sie für den Endpunkt der Spracherkennungs-API die folgenden Werte fest:
   
    ![Postman-Anforderung](./media/postman-collection/request.png)
   
    Details der verwendeten Parameter und Werte:
   
   | Parameter | Wert |
   | --- | --- |
   | Verb |POST |
   | Anforderungs-URL |https://westus.api.cognitive.microsoft.com/text/analytics/v2.0/languages |
   | Params |AnzahlDerZuErkennendenSprachen |
   | Autorisierung |„Keine Authentifizierung“ |
   | Header |Ocp-Apim-Subscription-Key = <your subscription key> <br/>Content-Type = application/json |
   | Textkörper |<code>{<br/>&nbsp;&nbsp;&nbsp;"documents": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": "1",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Hello World"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}<code> |
2. Klicken Sie auf **Senden**, um die Anforderung einzuleiten und die Rückantwort zu erhalten.
3. Klicken Sie auf **Speichern**, um die Anforderung in einer Postman-Sammlung zu speichern.
   
    ![Postman-Antwort](./media/postman-collection/request-response-save.png)
4. Geben Sie im Dialogfeld **Speichern** einen **Anforderungsnamen** und eine **Anforderungsbeschreibung** ein. Diese Werte werden in Ihrem benutzerdefinierten Connector verwendet.
   
    ![Sammlung speichern in Postman](./media/postman-collection/save-request-note.png)
   
    Sie können darüber hinaus auch die Antwort auf die Anforderung speichern. Benutzerdefinierte Connectors unterstützen zurzeit nur eine einzelne Antwort pro Anforderung. Wenn Sie auf eine Anforderung mehrere Antworten erhalten, wird nur die erste verwendet.
   
    ![Antwort speichern in Postman](./media/postman-collection/save-response.png)
5. Fahren Sie mit dem Erstellen Ihrer Postman-Sammlung fort, indem Sie weitere Anforderungen und Antworten speichern.
6. Nachdem Sie das Erstellen der Postman-Sammlung für Ihre sämtlichen Anforderungen und Antworten abgeschlossen haben, exportieren Sie die Sammlung.
   
    ![Postman-Export](./media/postman-collection/export.png)
7. Wählen Sie als Exportformat **Collection v1** aus.
   
    ![Postman-Export](./media/postman-collection/export2.png)

Jetzt können Sie diese Postman-Sammlung verwenden, um einen benutzerdefinierten Connector in PowerApps zu erstellen. Weitere Informationen finden Sie unter [Registrieren und Verwenden von benutzerdefinierten Connectors in PowerApps](register-custom-api.md). 

