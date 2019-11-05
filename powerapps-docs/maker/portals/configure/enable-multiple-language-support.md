---
title: Aktivieren der Unterstützung für mehrere Sprachen MicrosoftDocs
description: Anweisungen zum Aktivieren mehrerer Sprachen für ein Portal und zum Erstellen von Inhalten in mehreren Sprachen.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f8da1ac4be7098fc712faef82f6c9566d5f10512
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552748"
---
# <a name="enable-multiple-language-portal-support"></a>Aktivieren der Unterstützung für mehrere Sprachen
Business ist nicht auf eine einzelne Region oder eine Sprache beschränkt. In einem einzelnen Portal können Inhalte in mehreren Sprachen angezeigt werden, um Kunden auf der ganzen Welt zu erreichen. Der Inhalt Ihres Portals kann in mehrere Sprachen übersetzt werden, während eine einzelne Inhalts Hierarchie beibehalten wird.

![Dropdown Menü für mehrere Sprachen](../media/multi-language-dropdown.png "Dropdown Liste für mehrere Sprachen")  

Führen Sie die folgenden Schritte aus, um mehrere Sprachen für ein Portal zu aktivieren:

1. [Aktivieren von Sprachen in einer Common Data Service Umgebung.](https://technet.microsoft.com/library/dn832148.aspx)  
2. Wechseln Sie zu **Portale** > **Website** > **Websites**.
3. Wählen Sie die Website aus, der Sie Sprachunterstützung hinzufügen möchten.
4. Wählen Sie im Abschnitt **Unterstützte Sprachen** auf der Registerkarte **Allgemein** die Option **neue Website Sprache**aus.
5. Füllen Sie das Formular aus, einschließlich der **Portal Sprache** (eine Suche nach Sprachen, die in der Organisation aktiviert sind und von Portalen unterstützt werden) und dem **Veröffentlichungs Zustand**.

   ![Neue Portal Sprache hinzufügen](../media/add-new-portal-language.png "Neue Portal Sprache hinzufügen")

   ![Festlegen der Standardsprache für Ihr Portal](../media/set-default-language-portal.png "Festlegen der Standardsprache für Ihr Portal")

> [!Note]
> Wenn Sie neue Sprachen aktivieren, nachdem das Portal bereitgestellt wurde, können Sie [die Metadatenübersetzungen importieren](../admin/import-metadata-translation.md) , um die Metadaten für die neu aktivierten Sprachen zu übersetzen.

## <a name="supported-languages"></a>Unterstützte Sprachen

In der folgenden Tabelle sind alle derzeit standardmäßig verfügbaren Sprachen aufgeführt. Diese Liste finden Sie unter **Portale** &gt; **Inhalts** &gt; **Portal Sprachen**. Der Anzeige Name einer Sprache des Portals kann geändert werden, nachdem Sie die zu ändernde Sprache auf dieser Seite ausgewählt haben. Beachten Sie, dass die Liste jetzt ostasiatische Sprachen (Japanisch, Chinesisch und Koreanisch) enthält.

| **Name**                           | **Sprach Code** | **LCID** | **Anzeige Name des Portals** |
|------------------------------------|-------------------|----------|-------------------------|
| Baskisch-Baskisch                    | EU-es             | 1069     | Euskara                 |
| Bulgarisch (Bulgarien)               | BG-BG             | 1026     | български               |
| Katalanisch-Katalanisch                  | ZS-es             | 1027     | Katala                  |
| Chinesisch (China)                    | zh-cn             | 2052     | (中国)              |
| Chinesisch (Hongkong, SAR)            | ZH-HK             | 3076     | (香港特別行政區)    |
| Chinesisch (traditionell)              | zh-tw             | 1028     | (台灣)              |
| Kroatisch (Kroatien)                 | Personalabteilung             | 1050     | Hrvatski                |
| Tschechische Republik             | CS-CZ             | 1029     | Čeština                 |
| Dänisch-Dänemark                   | da-DK             | 1030     | Danzig                   |
| Niederländisch (Niederlande)                | nl-nl             | 1043     | Nederlands              |
| Englisch                            | en-US             | 1033     | Englisch                 |
| Estnisch (Estland)                 | et-EE             | 1061     | Eesti                   |
| Finnisch (Finnland)                  | fi-fi             | 1035     | Suomi                   |
| Französisch-Frankreich                    | fr-FR             | 1036     | Französisch                |
| Galicisch (Spanien)                   | gl-es             | 1110     | Galego                  |
| Deutsch-Deutschland                   | de-de             | 1031     | Schweizer                 |
| Griechisch (Griechenland)                     | El-Gr             | 1032     | Ελληνικά                |
| Hindi-Indien                      | Hallo             | 1081     | हिंदी                   |
| Ungarisch-Ungarn                | HU-HU             | 1038     | Magyar                  |
| Indonesisch (Indonesien)             | ID-ID             | 1057     | Bahasa Indonesien        |
| Italienisch-Italien                    | IT-IT             | 1040     | Dall                |
| Japanisch (Japan)                   | ja-JP             | 1041     | die                  |
| Kasachisch (Kasachstan)                | KK-KZ             | 1087     | Қазақ.              |
| Koreanisch (Korea)                     | ko-kr             | 1042     | 한국어                  |
| Lettisch (Lettland)                   | LV-LV             | 1062     | Latviešu                |
| Litauisch (Litauen)             | lt-lt             | 1063     | lietuvi\                |
| Malaiisch (Malaysia)                   | MS-My             | 1086     | Bahasa Melayu           |
| Norwegisch (Bokmål)-Norwegen        | NB-Nein             | 1044     | Norsk Bokmål            |
| Polnisch-Polen                    | pl-pl             | 1045     | Polski                  |
| Portugiesisch (Brasilien)                | pt-br             | 1046     | Portugiesisch (Brasilien)      |
| Portugiesisch-Portugal              | pt-pt             | 2070     | Portugiesisch (Portugal)    |
| Rumänisch (Rumänien)                 | Ro-Ro             | 1048     | românwp                  |
| Russisch-Russische Föderation                   | ru-ru             | 1049     | "", "".                 |
| Serbisch (Kyrillisch): Serbien        | SR-Cyrl-CS        | 3098     | Sonstige                  |
| Serbisch (lateinisch)-Serbien           | SR-LATN-CS        | 2074     | Srpski                  |
| Slowakisch (Slowakei)                  | SK-SK             | 1051     | Slovenčina              |
| Slowenisch (Slowenien)               | SL-SI             | 1060     | Slovenščina             |
| Spanisch (herkömmliche Sortierung)-Spanien | es-es             | 3082     | Spanisch                 |
| Schwedisch-Schweden                   | SV-SE             | 1053     | Svenska                 |
| Thailändisch (Thailand)                    | th-TH             | 1054     | ไทย                     |
| Türkisch-Türkei                   | TR-TR             | 1055     | Türkçe                  |
| Ukrainisch-Ukraine                | UK-UA             | 1058     | der "-".              |
| Vietnamese-Vietnam               | vi-VN             | 1066     | Tiếng Việt              |

## <a name="create-content-in-multiple-languages"></a>Erstellen von Inhalten in mehreren Sprachen

1. Melden Sie sich bei Dynamics 365-Portalen an.
2. Wechseln Sie zu **Portale** > **Inhalts** > **Webseiten** , um eine Liste der Inhalte anzuzeigen. Für jede Webseite gibt es eine übergeordnete Version der Seite und eine untergeordnete Version der Seite für jede Sprache, die für das Portal aktiviert ist.
3. Um eine neue Lokalisierung der Seite hinzuzufügen, navigieren Sie zu einer Basis Seite, und Scrollen Sie nach unten zu **lokalisierten Inhalt**.
4. Wählen Sie auf der rechten Seite die Schaltfläche **+** aus, um eine Suche für die lokalisierte Version zu erstellen.

    ![Neuen lokalisierten Inhalt hinzufügen](../media/add-new-localized-content.png "Neuen lokalisierten Inhalt hinzufügen")  

> [!Note]
> Die Konfigurations Felder auf der Startseite einer Inhaltsseite werden nicht auf die vorhandenen Inhaltsseiten geerbt. Sie werden nur bei der Erstellung neuer Inhaltsseiten verwendet. Sie müssen die Inhaltsseiten Konfigurationen einzeln aktualisieren.

Wissens Daten Bank Artikel werden nur angezeigt, wenn Sie in die Sprache übersetzt wurden, in der der Benutzer das Portal als angezeigt festgelegt hat. In Foren und Blogs können Sie jedoch besser steuern, wie Sie in anderen Sprachen dargestellt werden. Das Angeben einer Sprache für ein Forum oder einen Blog ist optional. Wenn keine Sprache angegeben ist, wird das Forum oder der Blog in der primären Sprache der Organisation angezeigt. Wenn Sie möchten, dass das Forum oder der Blog für eine Sprache spezifisch ist, müssen Sie Sie erstellen und der Sprache zuweisen.

Weblinksets sind die Navigationslinks am oberen Rand des Portals. Indem Sie zu **Portalen** > **Inhalts** > **weblinksets** navigieren, können Sie steuern, wie dieser Inhalt übersetzt wird. Wenn eine Sprache für das Portal aktiv ist, wird eine neue Gruppe von Verknüpfungen für die neu aktivierte Sprache erstellt.

![Aktiver Weblink für neue Sprache](../media/active-weblink-new-language.png "Aktiver Weblink für neue Sprache")
