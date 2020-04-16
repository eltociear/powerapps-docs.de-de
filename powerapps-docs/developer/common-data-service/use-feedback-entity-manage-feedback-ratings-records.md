---
title: Verwenden der Feedbackentität zum Verwalten von Feedback und Bewertungen für Datensätze (Common Data Service) | Microsoft-Dokumentation
description: In diesem Thema wird die Feedbackentität behandelt, mit der Feedback und Bewertungen für Datensätze abgerufen werden.
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
ms.openlocfilehash: 3a29c5bc852796063d90a3da5bab16bd0eae1a5a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155202"
---
# <a name="use-the-feedback-entity-to-manage-feedback-and-ratings-for-records"></a>Verwenden der Feedbackentität zum Verwalten von Feedback und Bewertungen für Datensätze

Verbessern Sie Ihre Produkte und Services, indem Sie Benutzern ermöglichen, Feedback und Bewertungen für Entitätsdatensätze in Common Data Service abzugeben. Zum Beispiel können Sie Feedback und Bewertungen für die `Product`-Entität ermöglichen, um das Feedback der Benutzer zu den Produkten zu kennen, die Sie verkaufen, oder zur `Incident`-(Fall)-Entität, um die Qualität Ihres Kundensupportteams zu verstehen und zu verbessern.  
  
 Sie können das Feedback und die Bewertung für System- und benutzerdefinierte Entitäten in Common Data Service aktivieren. Feedback und Bewertung sind standardmäßig für die Entität `KnowledgeArticle` aktiviert. Verwenden Sie die neue `Feedback`-Entität, um Feedback für Entitätsdatensätze automatisch zu erstellen und zu verwalten.  
  
 Zum Aktivieren von programmgesteuertem Feedback für eine:  
  
- Systementität, benutzen Sie die <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>-Message, um die Entität zu aktualisieren, und legen Sie die <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasFeedback>-Eigenschaft auf true fest.  
  
- Benutzerdefinierte Entität, legen Sie die <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasFeedback>- Eigenschaft auf den Wert "true" fest, wenn Sie die Entität erstellen oder die vorhandene benutzerdefinierte Entität aktualisieren, um die <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasFeedback> Eigenschaft auf "true" festzulegen.  
  
  Sobald Sie eine Entität für Feedback und Bewertung aktiviert haben, können Sie sie nicht deaktivieren. Nachdem Sie eine Entität für Feedback aktiviert haben, wird eine entsprechende Beziehung zwischen der Entität und der `Feedback`-Entität hergestellt.  
  
> [!NOTE]
>  Sie können die Anpassungstools in Common Data Service benutzen, um Feedback und Bewertung für System- und benutzerdefinierte Entitäten zu aktivieren. Weitere Informationen: [Eine Entität für Feedback aktivieren](https://go.microsoft.com/fwlink/p/?LinkId=785436)  
  
 Die `Feedback`-Entität speichert die folgenden Informationen:  
  
- Feedback-Titel  
  
- Feedback-Kommentare  
  
- Feedback-Bewertung Sie können auch einen Bereich für Bewertungen definieren, indem Sie einen (numerischen) Mindest- und Maximalwert für Bewertungen angeben. Zum Beispiel eine Bewertung von 4 auf einer Skala von 1-5.  
  
- Normalisierte Bewertung für Feedback, das automatisch berechnet wird, um die angegebene Benutzerbewertung basierend auf den Minimum- und Maximalwerten auf einen Wert zwischen 0 und 1 skaliert anzuzeigen.  
  
  > [!NOTE]
  >  Mithilfe der normalisierten Bewertung können Sie angegebene Bewertungswerte für verschiedene Bewertungsbereiche (minimale oder maximale Bewertungswerte) normalisieren oder ausgleichen. Die normalisierte Bewertung wird folgendermaßen berechnet: (Bewertung – minimale Bewertung) / (maximale Bewertung – minimale Bewertung).  
  >   
  >  Außerdem wird die Bewertung für einen Datensatz als Durchschnitt aller normalisierten Bewertungen eines Datensatzes berechnet.  
  
- Feedback-Status, wie "Offen" oder "Geschlossen"  
  
- Feedback-Quelle, um die Quelle anzuzeigen, von der das Feedback eingereicht wurde. Wenn das Feedback von Common Data Service aus erstellt wurde, wird der Wert auf **Intern** festgelegt. Entwickler können je nach Anwendung, die zum Bereitstellen des Feedbacks verwendet wird, einen Wert ihrer Wahl hinzufügen.  
  
- Benutzer, die den Feedback-Datensatz erstellt oder als letztes geändert haben  
  
- Entitätsdatensatz, dem das Feedback zugeordnet ist  
  