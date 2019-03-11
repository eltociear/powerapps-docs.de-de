---
title: Bereitstellen der Dynamics 365-App für Outlook | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2017-04-20
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
ms.assetid: 09736e14-e744-48ca-a755-1b05bb55340e
caps.latest.revision: 39
author: jimholtz
ms.author: jimholtz
manager: brycho
ms.openlocfilehash: 98a5ec78b0edf607b954d794b3eef95403926a64
ms.sourcegitcommit: baadb67f5cc962b7c3393f9763959eae3a7649dd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57346945"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Bereitstellen der Dynamics 365-App für Outlook
Benutzer können [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] verwenden, um die Leistung von [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] zu nutzen, wenn sie [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] auf dem Desktop, im Web oder auf einem Tablet verwenden. Zeigen Sie beispielsweise Informationen über E-Mail- oder Terminempfänger an oder verknüpfen Sie eine [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]-E-Mail oder einen Termin mit einem [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]-Datensatz, wie beispielsweise einer Verkaufschance, einem Konto oder einem Fall. Weitere Informationen zu den Angeboten von [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] finden Sie im Benutzerhandbuch [Dynamics 365 App für Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] ist nicht dasselbe wie [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]. Ab dem [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] ist [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] gepaart mit [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] der bevorzugte Weg, um [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] mit [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] zu integrieren. **Beachten Sie, dass Verfolgungsaktivitäten nicht unterstützt werden, wenn [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] und [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] von demselben Benutzer gemeinsam verwendet werden.** Informationen zum [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]-Add-In finden Sie im Benutzerhandbuch von [Dynamics 365 für Outlook](http://go.microsoft.com/fwlink/p/?LinkID=524751).  
>   
>  [Delegierte Benutzer](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540) können [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] nicht zum Verfolgen von E-Mails verwenden. Wir empfehlen die Verwendung von [Verfolgung auf Ordnerebene oder von automatischer Verfolgung](https://www.microsoft.com/en-us/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx) für delegierte Benutzer.  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Vergleichen der Dynamics 365-App für Outlook mit Dynamics 365 für Outlook  
 Die folgende Tabelle vergleicht [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]-Features mit [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] (auch bekannt als [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]-Client oder -Add-In) ab dem [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)].  
  
||||  
|-|-|-|  
|**Feature**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|Nachverfolgen und als Bezug festlegen für E-Mail|Ja|Ja|  
|Nachverfolgen und als Bezug festlegen für Termine|Ja|Ja|  
|Nachverfolgen und als Bezug festlegen für Kontakte|Ja|Ja|  
|Nachverfolgen und als Bezug festlegen für Aufgaben|Nein|Ja|  
|Bezug festlegen mit einem Klick|Ja|Nein|  
|Anzeige der Empfängerzusammenfassung|Ja|Nein|  
|Anzeige der Bezugsdatensatzzusammenfassung in der E-Mail/dem Termine|Ja|Nein|  
|Funktioniert mit [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]|Ja|Nein|  
|Funktioniert mit [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] für Desktop|Ja|Ja|  
|Funktioniert mit [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] für den Mac|Ja|Nein|  
|Funktioniert mit Smartphones|Ja|Nein|  
|Direktes Öffnen und Erstellen von [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]-Datensätzen|Ja|Ja|  
|Anwenden von benutzerdefinierten Formularen und Geschäftslogik|Ja|Ja|  
|Offline arbeiten|Nein|Ja|  
|E-Mail-Vorlagen anwenden|Ja|Ja|  
|Vertriebsdokumentation anwenden|Ja|Ja|  
|Wissensartikel anwenden|Ja|Ja|  
|Möglichkeit zum Überwachen von E-Mails nach dem Senden|Ja|Nein|  
|Sortieren, Filtern, Formatieren, Gruppieren und Kategorisieren von Ansichten|Nein|Ja|  
|Erstellen von Dokumenten aus Word- und E-Mail-Dokument|Nein|Ja|  
|Synchronisierung der Steuerungsfelder|Nein|Ja|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>Anforderungen  
 Folgende Voraussetzungen müssen für die Verwendung von [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] erfüllt sein:  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] oder [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   Synchronisierung von eingehenden E-Mails über die serverseitige Synchronisierung [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][Einrichten der serverseitigen Synchronisierung von E-Mails, Terminen, Kontakten und Aufgaben](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   Erforderliche Rechte, wie unten beschrieben  
  
> [!NOTE]
>  Unterstützte Konfigurationen und Anforderungen für [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)]-Funktionen sind in der Dokumentation aufgeführt. Spezifische Konfigurationen, die nicht dokumentiert sind, gelten als nicht unterstützt.  
  
### <a name="required-privileges"></a>Erforderliche Berechtigungen  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] stellt Zugriff auf [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] über das Recht **Dynamics 365 App für Outlook verwenden** bereit. Wenn Benutzer über diese Berechtigung nicht verfügen, wird ihnen die folgende Fehlermeldung angezeigt:  
  
> „Sie wurden nicht autorisiert, diese App zu verwenden. Wenden Sie sich an den Systemadministrator, um Ihre Einstellungen zu aktualisieren.“  
  
 Benutzer müssen auch über Lese-/Schreibrechte für folgende Entitäten verfügen.  
  
 Registerkarte „Geschäftsverwaltung“:  
  
-   **Postfach**  
  
 Registerkarte „Anpassung“:  
  
-   **Entität**  
  
-   **Feld**  
  
-   **Beziehung**  
  
-   **Systemanwendungsmetadaten**  
  
-   **Systemformular**  
  
-   **Benutzeranwendungsmetadaten**  
  
-   **Ansicht**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>Festlegen der Berechtigungen für eine Sicherheitsrolle  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  Öffnen Sie **Sicherheitsrollen**.  
  
3.  Wählen Sie eine Sicherheitsrolle, und klicken Sie dann auf die Registerkarte **Geschäftsverwaltung**.  
  
4.  Überprüfen Sie im Abschnitt **Entität** die Berechtigungseinstellungen für **Postfach**. Die Sicherheitsrolle sollte die Einstellungen „Benutzer“ oder höher haben.  
  
5.  Stellen Sie im Abschnitt **Datenschutzbezogene Rechte** sicher, dass **Dynamics 365 App für Outlook verwenden** auf **Organisation** festgelegt ist. Falls nicht, klicken Sie auf **Dynamics 365 App für Outlook verwenden**.  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Unterstützte Konfigurationen mit Microsoft Exchange  
 Ab [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)], Dezember 2016 können Sie die App mit einer beliebigen Kombination von [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] oder [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] und [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] oder [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (lokal) verwenden, einschließlich Hybridkonfigurationen. Dies bedeutet, dass [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] in jede der folgenden Konfigurationen verwendet werden kann:  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (lokal)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (lokal)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  Wenn Sie [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] verwenden, müssen Sie sich per IFD authentifizieren, wie unten beschrieben.  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Unterstützte Browser für Outlook im Internet  
 Sie können [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] mit [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] in den folgenden Browsern verwenden:  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)] oder [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     Es werden die folgende Konfiguration unterstützt:  
  
    -   Geschützter Modus wird zur Sicherheitszone **Internet** aktiviert. Um den geschützten Modus zu aktivieren: in IE 10 oder 11 wählen Sie **Tools** > **Internetoptionen** > **Sicherheitsregisterkarte** > **Internet**.  
  
    -   Geschützter Modus wird für die Sicherheitszone **Lokales Internet** aktiviert. Um den geschützten Modus zu aktivieren: in IE 10 oder 11 wählen Sie **Tools** > **Internetoptionen** > **Sicherheitsregisterkarte** > **Lokales Internet**.  
  
    -   Ihre [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)]-URL ist in der Sicherheitszonenliste **Lokales Intranet**der vertrauenswürdigen Websites. In IE 10 oder 11, Gehen Sie zu **Tools** > **Internetoptionen** > **Sicherheitsregisterkarte** > **Lokales Intranet** > **Orte** > **Erweitert**.  
  
-   [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)] (aktuelle Version) für [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] (aktuelle Version) für [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)] (Version 9 oder 10) für Mac oder unter OS x  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>Unterstützte Betriebssysteme für Outlook auf Desktop-Computern  
 Sie können [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] in diesen Versionen von [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] für Desktop-Computer nutzen:  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 und [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] für Mac *.  
  
     *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] Version 15.0.847.32 oder höher ist erforderlich.  
  
### <a name="supported-mobile-devices"></a>Unterstützte mobile Geräte  
 Sie können [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] mit [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] im mobilen Browser auf allen der folgenden Smartphones und Betriebssysteme verwenden:  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)]-Geräte, auf denen iOS-Version 8, 9 oder 10 ausgeführt wird.  
  
-   [!INCLUDE[tn_android](../includes/tn-android.md)]-Smartphones, die unter [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat) oder 5.0 (Lollipop), 6 (Marshmallow) oder 7 (Nougat) ausgeführt werden.  
  
-   [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)]-Geräte, auf denen [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] oder [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)] ausgeführt wird.  
  
### <a name="supported-clients-per-feature"></a>Unterstützte Clients pro Feature  
 Die von [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] unterstützt Features sind vom Client abhängig, den Sie verwenden. In der folgenden Tabelle wird zusammengefasst, welche Features für die einzelnen Clients/Konfigurationen von [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] und [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] unterstützt werden.  
  
 ![Für jedes Dynamics 365-App für Outlook-Feature unterstützte Clients](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "Für jedes Dynamics 365-App für Outlook-Feature unterstützte Clients")  
  
 (1) [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] unterstützt [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)], [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)], [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9, [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10, [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] und [!INCLUDE[tn_chrome](../includes/tn-chrome.md)].  
  
 (2) Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] unterstützt [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)], [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)], [!INCLUDE[tn_ios](../includes/tn-ios.md)] 8 [!INCLUDE[tn_ios](../includes/tn-ios.md)] 9 [!INCLUDE[tn_ios](../includes/tn-ios.md)] 10 [!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4), [!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop, [!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow und [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat.  
  
 (3) Für die Nachverfolgung von E-Mails im Erstellmodus und Nachverfolgen von Terminen ist [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 oder [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016 notwendig.  
  
 (4) Nachverfolgung von Kontakten wird nur von [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 CU3 und [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 und höher unterstützt.  
  
 (5) Hinzufügen von E-Mail-Vorlagen, Wissensmanagementartikeln und Vertriebsdokumentation wird in Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] nicht unterstützt.  
  
 (6) Unterstützt nur auf [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 und höher.  
  
 (7) Unterstützt nur auf 16.0.6741.1000 und höher.  
  
> [!NOTE]
>  Tablets werden derzeit nicht unterstützt (CY2017).  
  
 [In diesem Blogbeitrag erhalten Sie mehr Informationen zu unterstützten Clients: Dynamics 365 App for Outlook Support Matrix (Unterstützungsmatrix für die Dynamics 365-App für Outlook)](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>Unterstützte Server  
 Die [Serveranforderungen für die Verwendung von Office-Add-Ins](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins) sind [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)], [!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)]oder [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)].  
  
### <a name="supported-languages"></a>Unterstützte Sprachen  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] unterstützt die folgenden Sprachen:  
  
||||  
|-|-|-|  
|Bulgarisch (Bulgarien) – 1026|Hindi (Indien) – 1081|Portugiesisch (Portugal) – 2070|  
|Chinesisch (China) – 2052|Ungarisch – 1038|Rumänisch – 1048|  
|Chinesisch (Taiwan) – 1028|Indonesisch – 1057|Russisch – 1049|  
|Kroatisch (Kroatien) – 1050|Italienisch – 1040|Serbisch – 2074|  
|Tschechisch (Tschechische Republik) – 1029|Japanisch – 1041|Slowakisch – 1051|  
|Dänisch – 1030|Kasachisch – 1087|Slowenisch – 1060|  
|Niederländisch – 1043|Koreanisch – 1042|Spanisch – 3082|  
|Englisch – 1033|Lettisch – 1062|Schwedisch – 1053|  
|Estnisch – 1061|Litauisch – 1063|Thailändisch – 1054|  
|Finnisch – 1035|Malaysisch – 1086|Türkisch – 1055|  
|Französisch – 1036|Norwegisch – 1044|Ukrainisch – 1058|  
|Deutsch – 1031|Polnisch – 1045|Vietnamesisch – 1066|  
|Griechisch – 1032|Portugiesisch (Brasilien) – 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Bereitstellen der Dynamics 365-App für Outlook  
 Nachdem Sie [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] eingerichtet und die erforderlichen Berechtigungen festgelegt haben, können Sie [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] auf einige oder alle Benutzer mithilfe von Push übertragen, oder Sie können es bei Bedarf von Benutzern selbst installieren lassen.  
  
> [!NOTE]
>  Wenn Sie [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)] verwenden, sehen Sie sich den folgenden Abschnitt an:  [So stellen Sie Benutzer von Dynamics 365 for Customer Engagement-Apps (lokal) bereit](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>So übertagen Sie die App mithilfe von Push an Benutzer  
  
1.  Rufen Sie **Einstellungen** >  **Dynamics 365 App für Outlook** auf.  
  
2.  Aktivieren Sie im Bildschirm **Erste Schritte mit Dynamics 365 App für Outlook** unter **Für berechtigte Benutzer hinzufügen** (Sie müssen möglicherweise auf **Einstellungen** klicken, wenn Sie diesen Bildschirm für das zweite, darauf folgende Mal öffnen) das Kontrollkästchen **Automatisch die App zu [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] hinzufügen**, wenn Sie möchten, dass Benutzer die App automatisch abrufen. Wenn ein Benutzer die erforderlichen Berechtigungen besitzt und die E-Mail durch [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] synchronisiert wurde, müssen Sie die App nur an sie übertragen. Wenn Sie die erforderlichen Berechtigungen beispielsweise einer Vertriebsmitarbeiterrolle hinzufügen und dann diese Rolle einem neuen Benutzer zuweisen, erhält dieser automatisch die App.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Um die App allen berechtigten Benutzer mithilfe von Push zu übertragen, klicken Sie auf **App allen berechtigten Benutzern hinzufügen**.  
  
    -   Um die App mithilfe von Push an bestimmte Benutzer zu übertragen, wählen Sie diese Benutzer in der Liste aus, und klicken Sie dann auf **App zu Outlook hinzufügen**.  
  
    > [!TIP]
    >  Wenn die Liste zeigt, dass ein Benutzer aussteht oder nicht hinzugefügt wurde, können Sie auf den Link **Weitere Informationen** neben dem Benutzer klicken, um weitere Informationen über den Status zu erhalten.  
  
4.  Klicken Sie abschließend auf **Speichern**.  
  
#### <a name="to-have-users-install-the-app-themselves"></a>So können Sie Benutzer veranlassen, die App selbst zu installieren  
  
1.  Klicken Sie auf die Schaltfläche **Einstellungen** ![Schaltfläche „Einstellungen“](media/mp-ua-r16-settings.png "Schaltfläche „Einstellungen“") und klicken Sie dann **Apps für Dynamics 365**.  
  
2.  Im Bildschirm **Apps für Dynamics 365** unter**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]** klicken Benutzer auf **App zu [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] hinzufügen**.  
  
> [!NOTE]
>  Benutzer können auch das Add-In deaktivieren und selbst entfernen. Weitere Informationen zu finden Sie im [Dynamics 365 für Outlook-Benutzerhandbuch](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>So stellen Sie für Benutzer von Dynamics 365 (lokal) bereit  
 Gehen Sie folgendermaßen vor, wenn Sie Dynamics 365 lokal verwenden.  
  
-   Konfigurieren Sie den Dynamics 365 Server für eine Bereitstellung mit Internetzugriff. Siehe [Konfigurieren von IFD für Microsoft Dynamics 365](https://technet.microsoft.com/library/dn609803.aspx).  
  
-   Wenn Sie sich mit Exchange lokal verbinden, müssen Sie den OAuth-Anbieter konfigurieren und Clientapps registrieren. Weitere Informationen finden Sie unter [Konfigurieren von Windows Server 2012 R2 für Dynamics 365-Anwendungen mit OAuth](https://technet.microsoft.com/library/hh699726.aspx).  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>Beheben von Installationsfehlern  
 Wenn Sie bzw. Benutzer Probleme beim Installation von [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] haben, kann es sein, dass das [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]-Postfach mit einer anderen [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)]-Organisation verknüpft ist. Ein [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]-Postfach (E-Mail-Adresse) kann Aufgaben, Termine und Kontakte nur mit einer Organisation synchronisieren, und einen Benutzer, der zu dieser Organisation gehört, kann Aufgaben, Termine und Kontakte nur mit einem [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)]-Postfach synchronisieren.  Sie können die in [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] gespeicherten Einstellungen überschreiben, wenn Sie die primäre synchronisierende Organisation ändern möchten. Weitere Informationen finden Sie in [diesem Wissensdatenbankartikel](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook).  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>Erkunden des Benutzerhandbuchs und schulen Ihrer Benutzer  
 Weitere Informationen zur Verwendung von [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] [erhalten Sie im Dynamics 365 App für Outlook-Benutzerhandbuch](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
 ![Seite aus dem Dynamics 365 App für Outlook-Benutzerhandbuch](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Seite aus dem Dynamics 365 App für Outlook-Benutzerhandbuch")  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamics 365 App für Outlook-Benutzerhandbuch](http://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [In diesem Blogbeitrag erhalten Sie mehr Informationen zu unterstützten Clients: Dynamics 365 App for Outlook Support Matrix (Unterstützungsmatrix für die Dynamics 365-App für Outlook)](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [Einrichten der serverseitigen Synchronisierung von E-Mails, Terminen, Kontakten und Aufgaben](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [Hinzufügen von Benutzern, Lizenzen und Sicherheitsrollen](http://msdn.microsoft.com/en-us/23612155-f92d-4871-a109-186419d5c19d)   
 [Hinzufügen von Interoperationsfunktionen zu Microsoft Dynamics 365 (online)](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)