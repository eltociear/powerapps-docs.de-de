---
title: Implementieren der Datenschutz-Grundverordnung in Power Apps-Portalen | MicrosoftDocs
description: Erfahren Sie, wie Sie die Datenschutz-Grundverordnung in Power Apps-Portalen implementieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 80a60ae7b1dd8810ee3509dfe9fcd108dffceb5d
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980039"
---
# <a name="implementing-general-data-protection-regulations-in-your-power-apps-portals"></a>Datenschutz-Grundverordnung in Ihren Power Apps-Portalen implementieren

Die Datenschutz-Grundverordnung (DSGVO) ist ein Gesetz der Europäischen Union (EU), durch das Daten für alle Einzelpersonen in der EU geschützt werden. Mit der DSGVO können Personen die Verwendung ihrer persönlichen Daten in Common Data Service steuern.

Als Administrator können Sie Ihr Portal so konfigurieren, dass es die DSGVO-Standards erfüllt. Beispielsweise bedürfen Minderjährige der elterlichen Zustimmung, um das Portal zu verwenden. Sie können auch Geschäftsbedingungen für Personen festlegen, die Ihr Portal verwenden. Benutzer müssen den Geschäftsbedingungen zustimmen, um das Portal zu verwenden.

Die DSGVO erlaubt es Ihnen, die Zustimmung der Portalbenutzer zur Verwendung Ihrer persönlichen Daten einzuholen, minderjährige Benutzer zu identifizieren und eine elterliche Zustimmung für Minderjährige einzuholen.

## <a name="audit-logging"></a>Überwachungsprotokollierung

Das Feld **Letzte erfolgreichen Anmeldung** im Portalkontaktdatensatz zeigt an, wann ein Portalbenutzer sich zuletzt angemeldet hat. Dieses Datum wird durch eine Überwachung des Kontaktdatensatzes erfasst, und diese Informationen werden im standardmäßigen Überwachungsstream verfügbar gemacht. Dies ermöglicht es dem Administrator, inaktive Communitymitglieder anzuzeigen und ihre Datensätze zu löschen.

> [!NOTE]
> Die Anmelde-Nachverfolgungsfunktion ist eingestellt. Es wird empfohlen, eine Analytiktechnologie wie Azure Application Insights zu nutzen, um diese Art von Informationen zu erfassen. Wenn Sie die Liste von veralteten Funktionen anzeigen wollen, klicken Sie [hier](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/).

## <a name="identifying-minor-portal-users-and-obtaining-parental-consent"></a>Ermitteln minderjähriger Portalbenutzer und Einholung der elterlichen Zustimmung

Vorschriften zum Identifizieren von Minderjährigen sind je nach Land/Region verschieden. Da ein Minderjähriger auf das Portal nur mit elterlicher Zustimmung zugreifen kann, können Sie das Portal so konfigurieren, dass es Minderjährige mithilfe dieser Felder im Portal-Kontaktdatensatz identifiziert:
- **Ist minderjährig**: Gibt an, dass der Kontakt in der entsprechenden Rechtsprechung als minderjährig gilt. Standardmäßig ist **Nein** ausgewählt.
- **Ist minderjährig mit elterlicher Zustimmung**: Gibt an, dass der Kontakt in der entsprechenden Rechtsprechung als minderjährig gilt und die Zustimmung der Eltern vorliegt. Standardmäßig ist **Nein** ausgewählt.

    ![Ermitteln minderjähriger Portalbenutzer und Einholung der elterlichen Zustimmung](../media/identify-minor-in-portal.png "Ermitteln minderjähriger Portalbenutzer und Einholung der elterlichen Zustimmung")

Mithilfe der folgenden Website-Einstellungen wird die Verwendung des Portals durch Minderjährige und Minderjährige ohne elterliche Zustimmung gesteuert:

| Name  | Beschreibung   |
|-----------------------|------------------------------------------|
| Authentication/Registration/DenyMinors  | Verweigert die Verwendung des Portals durch Minderjährige. Standardmäßig ist dies auf "false" gesetzt.                          |
| Authentication/Registration/DenyMinorsWithoutParentalConsent | Verweigert die Verwendung des Portals durch Minderjährige ohne elterliche Zustimmung. Standardmäßig ist dies auf "false" gesetzt. |
|||

Wenn ein Portalbenutzer als Minderjähriger ermittelt wird und das Portal so konfiguriert ist, dass Minderjährige gesperrt werden, wird eine entsprechende Meldung angezeigt, und der Inhalt wird nicht angezeigt.

![Nachricht zu Altersanforderungen](../media/gdpr-age-req.png "Nachricht zu Altersanforderungen")

Wenn ein Portalbenutzer als Minderjähriger ohne elterliche Zustimmung ermittelt wird und das Portal so konfiguriert ist, dass Minderjährige ohne elterliche Zustimmung gesperrt werden, wird eine entsprechende Meldung angezeigt, und der Inhalt wird nicht angezeigt.

![Nachricht zur Zustimmung der Eltern](../media/gdpr-parental-consent.png "Nachricht zur Zustimmung der Eltern")

Durch die folgenden Inhaltsausschnitte werden Meldungen gesteuert, die angezeigt werden, wenn das Portal durch Minderjährige und durch Minderjährige ohne elterliche Zustimmung verwendet wird. Sie können die Meldung gemäß Ihren Anforderungen ändern.

| Name                                                        | Typ | Value                                                                    |
|-------------------------------------------------------------|------|--------------------------------------------------------------------------|
| Account/Signin/MinorNotAllowedHeading                       | Text | Altersanforderungen                                                         |
| Account/Signin/MinorNotAllowedCopy                          | HTML | Die Verwendung dieses Portals ist für Minderjährige ungeeignet und wird nicht gestattet. |
| Account/Signin/MinorWithoutParentalConsentNotAllowedHeading | Text | Zustimmung der Eltern                                                         |
| Account/Signin/MinorWithoutParentalConsentNotAllowedCopy    | HTML | Für die Verwendung dieses Portal durch Minderjährigen ist die Zustimmung der Eltern erforderlich.              |
|||

Wenn sich jemand mithilfe eines externen Anbieters registriert und das Portal so konfiguriert ist, dass es Minderjährige oder Minderjährige ohne elterliche Zustimmung sperrt, wird der Kontaktdatensatz nicht erstellt, und der Benutzer wird nicht authentifiziert.

## <a name="agreeing-to-terms-and-conditions"></a>Den Geschäftsbedingungen zustimmen

Gemäß der DSGVO müssen Portalbenutzer den Geschäftsbedingungen zustimmen, um Marketing, Profilerstellung oder Zugriff auf private Informationen zuzulassen. Als Administrator können Sie Ihre eigenen Geschäftsbedingungen veröffentlichen, um die Zustimmung des Portalbenutzers zu erhalten, bevor er/sie für die Website authentifiziert wird.

![Portalnutzungsbedingungen](../media/gdpr-terms-agreement.png "Portalnutzungsbedingungen")

Mit den folgenden Inhaltsausschnitten wird die Anzeige von Geschäftsbedingungen auf dem Bildschirm gesteuert. Sie können den Text gemäß Ihren Anforderungen ändern.

| Name                                           | Typ | Value                                 |
|------------------------------------------------|------|---------------------------------------|
| Account/Signin/TermsAndConditionsHeading       | Text | Bestimmungen                  |
| Account/Signin/TermsAndConditionsCopy          | HTML |                                       |
| Account/Signin/TermsAndConditionsAgreementText | Text | Ich stimme diesen Geschäftsbedingungen zu |
| Account/Signin/TermsAndConditionsButtonText    | Text | Fortfahren                              |
|||

Der Inhaltsausschnitt `Account/Signin/TermsAndConditionsCopy` ist standardmäßig leer. Ein Portaladministrator muss die Geschäftsbedingungen in diesen Inhaltsausschnitt eingeben.

Die folgenden Website-Einstellungen steuern das Veröffentlichungsdatum der Bedingungen und ob die Bedingungen im Portal angezeigt werden sollen:

| Name  | Beschreibung |
|------------|---------------|
| Authentication/Registration/TermsPublicationDate  | Ein Datums-/Uhrzeitwert im GMT-Format, um das Wirksamkeitsdatum der aktuell veröffentlichten Geschäftsbedingungen darzustellen. Wenn die Bedingungszustimmung aktiviert ist, werden Portalbenutzer, die den Bedingungen nach diesem Datum nicht zugestimmt haben, dazu aufgefordert, ihnen zuzustimmen, wenn sie sich das nächste Mal anmelden. Wenn das Datum nicht angegeben wird und die Bedingungszustimmung aktiviert ist, werden die Bedingungen jedes Mal angezeigt, wenn sich Portalbenutzer anmelden. <br> **Hinweis**: Wenn Sie möchten, dass ein Portalbenutzer jedes Mal, wenn er sich anmeldet, den Geschäftsbedingungen zustimmt, dann geben Sie für diese Website-Einstellung keinen Wert an.|
| Authentication/Registration/TermsAgreementEnabled | Ein Wert „wahr” oder „falsch”. Bei Festlegung auf wahr, zeigt das Portal die Geschäftsbedingungen der Website an. Benutzer müssen den Geschäftsbedingungen zustimmen, bevor sie als authentifiziert gelten und die Website verwenden können. Standardmäßig ist dies auf "false" gesetzt.        |
|||

Das folgende Feld wird im Portal-Kontaktdatensatz hinzugefügt, um das Datum und die Uhrzeit eines Portalbenutzers zu speichern, zu denen er den Geschäftsbedingungen zugestimmt hat:
- **Portal-Bedingungszustimmungsdatum**: Gibt Datum und Uhrzeit an, zu der die Person den Geschäftsbedingungen des Portals zugestimmt hat.

    ![Vereinbarungsdatum zu Portalnutzungsbedingungen](../media/portal-terms-agreement.png "Vereinbarungsdatum zu Portalnutzungsbedingungen")

### <a name="see-also"></a>Siehe auch

[Identitätsanbieter nach Azure AD B2C migrieren](migrate-identity-providers.md)
