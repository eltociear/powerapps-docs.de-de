---
title: Aktivieren von Mehrsprachenportalunterstützung | MicrosoftDocs
description: Anweisungen, wie Sie mehrere Sprachen für ein Portal aktivieren und Inhalte in mehreren Sprachen erstellen können.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a91ffe1c00b7dbcc40b786731e956bfdd8fc6d94
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012723"
---
# <a name="enable-multiple-language-portal-support"></a>Aktivieren von Mehrsprachenportalunterstützung
Unternehmen sind nicht auf eine Region oder eine Sprache beschränkt. Ein einzelnes Portal kann Inhalte in mehreren Sprachen anzeigen, um Kunden auf der ganzen Welt zu erreichen. Der Inhalt des Portals kann in mehreren Sprachen unter Beibehaltung einer einzelnen Inhaltshierarchie übersetzt werden.

![Mehrsprachiges Dropdown](../media/multi-language-dropdown.png "Mehrsprachige Dropdownliste")  

Um mehrere Sprachen für ein Portal zu aktivieren, folgenden Sie diesen Schritten:

1. [Aktivieren Sie Sprachen in einer Common Data Service-Umgebung.](https://technet.microsoft.com/library/dn832148.aspx)  
2. Wechseln Sie zu **Portale** > **Website** > **Websites**.
3. Wählen Sie die Website aus, der Sprachensupport hinzugefügt werden soll.
4. Im Abschnitt **Unterstützte Sprachen** auf der Registerkarte **Allgemein**, wählen Sie **Neue Website-Sprache**.
5. Füllen Sie das Formular aus, einschließlich **Portalsprache** (eine Suche von Sprachen, die in der Organisation aktiviert sind und von Portalen unterstützt werden) und **Veröffentlichungsstatus**.

   ![Fügen Sie eine neue Portalsprache hinzu](../media/add-new-portal-language.png "Fügen Sie eine neue Portalsprache hinzu")

   ![Festlegen der Standardsprache für Ihr Portal](../media/set-default-language-portal.png "Festlegen der Standardsprache für Ihr Portal")

   ![Unterstützte Sprachen](../media/supported-languages.png "Unterstützte Sprachen")

> [!Note]
> Wenn Sie neue Sprachen aktivieren, nachdem das Portal bereitgestellt wurde, können Sie [Metadatenübersetzungen importieren](../admin/import-metadata-translation.md), um die Metadaten, die für die neu aktivierten Sprachen übersetzt wurden abzurufen.

## <a name="supported-languages"></a>Unterstützte Sprachen

Auf der Tabelle unten werden alle Sprachen angezeigt, die derzeit voreingestellt verfügbar sind. Sie finden diese Liste, indem Sie zu **Portale** &gt; **Inhalte** &gt; **Portalsprachen**. Der Portalanzeigename einer Sprache kann geändert werden, nachdem die zu ändernde Sprache auf dieser Seite ausgewählt wurde. Beachten Sie, dass die Liste jetzt ostasiatische Sprachen (Japanisch, Chinesisch und Koreanisch) enthält.

| **Name**                           | **Sprachcode** | **LCID** | **Portalanzeigename** |
|------------------------------------|-------------------|----------|-------------------------|
| Baskisch – Baskisch                    | eu-ES             | 1069     | euskara                 |
| Bulgarisch – Bulgarien               | bg-BG             | 1026     | български               |
| Katalanisch – Katalanisch                  | ca-ES             | 1027     | català                  |
| Chinesisch – China                    | zh-CN             | 2052     | 中文 (中国)              |
| Chinesisch – Sonderverwaltungsregion Hongkong            | zh-HK             | 3076     | 中文 (香港特別行政區)    |
| Chinesisch – Traditionell              | zh-TW             | 1028     | 中文 (台灣)              |
| Kroatisch – Kroatien                 | hr-HR             | 1050     | hrvatski                |
| Tschechisch – Tschechische Republik             | cs-CZ             | 1029     | čeština                 |
| Dänisch – Dänemark                   | da-DK             | 1030     | dansk                   |
| Niederländisch – Niederlande                | nl-NL             | 1043     | Nederlands              |
| Englisch                            | de-DE             | 1031     | Englisch                 |
| Estnisch – Estland                 | et-EE             | 1061     | eesti                   |
| Finnisch – Finnland                  | fi-FI             | 1035     | suomi                   |
| Französisch – Frankreich                    | fr-FR             | 1036     | français                |
| Galicisch – Spanien                   | gl-ES             | 1110     | galego                  |
| Deutsch – Deutschland                   | de-DE             | 1031     | Deutsch                 |
| Griechisch – Griechenland                     | el-GR             | 1032     | Ελληνικά                |
| Hindi – Indien                      | hi-IN             | 1081     | हिंदी                   |
| Ungarisch – Ungarn                | hu-HU             | 1038     | magyar                  |
| Indonesisch – Indonesien             | id-ID             | 1057     | Bahasa Indonesia        |
| Italienisch – Italien                    | it-IT             | 1040     | italiano                |
| Japanisch – Japan                   | ja-JP             | 1041     | 日本語                  |
| Kasachisch – Kasachstan                | kk-KZ             | 1087     | қазақ тілі              |
| Koreanisch – Korea                     | ko-KR             | 1042     | 한국어                  |
| Lettisch – Lettland                   | lv-LV             | 1062     | latviešu                |
| Litauisch – Litauen             | lt-LT             | 1063     | lietuvių                |
| Malaiisch – Malaysia                   | ms-MY             | 1086     | Bahasa Melayu           |
| Norwegisch (Bokmål) – Norwegen        | nb-NO             | 1044     | norsk bokmål            |
| Polnisch – Polen                    | pl-PL             | 1045     | polski                  |
| Portugiesisch – Brasilien                | pt-BR             | 1046     | português (Brasil)      |
| Portugiesisch – Portugal              | pt-PT             | 2070     | português (Portugal)    |
| Rumänisch – Rumänien                 | ro-RO             | 1048     | română                  |
| Russisch – Russische Föderation                   | ru-RU             | 1049     | русский                 |
| Serbisch (Kyrillisch) – Serbien        | sr-Cyrl-CS        | 3098     | српски                  |
| Serbisch (Lateinisch) – Serbien           | sr-Latn-CS        | 2074     | srpski                  |
| Slowakisch – Slowakei                  | sk-SK             | 1051     | slovenčina              |
| Slowenisch – Slowenien               | sl-SI             | 1060     | slovenščina             |
| Spanisch (Traditionelle Sortierung) – Spanien | es-ES             | 3082     | español                 |
| Schwedisch – Schweden                   | sv-SE             | 1053     | svenska                 |
| Thailändisch – Thailand                    | th-TH             | 1054     | ไทย                     |
| Türkisch – Türkei                   | tr-TR             | 1055     | Türkçe                  |
| Ukrainisch – Ukraine                | uk-UA             | 1058     | українська              |
| Vietnamesisch – Vietnam               | vi-VN             | 1066     | Tiếng Việt              |

## <a name="create-content-in-multiple-languages"></a>Erstellen Sie Inhalt in mehreren Sprachen

1. Melden Sie sich bei Dynamics 365 Portale an.
2. Gehen Sie zu **Portale** > **Inhalt** > **Webseiten**, um ein Inhaltsverzeichnis anzuzeigen. Für jede Website ist eine übergeordnete Version der Seite und eine untergeordnete Version der Seite für jede Sprache vorhanden, die für das Portal aktiviert ist.
3. Wenn Sie eine neue Lokalisierung einer Seite hinzuzufügen möchten, navigieren Sie zu einer Basisseite und führen Sie einen Bildlauf zu **Lokalisierter Inhalt** durch.
4. Klicken Sie auf die Schaltfläche **+** auf der rechten Seite, um eine Suche für die die Version zu erstellen.

    ![Neuen lokalisierten Inhalt hinzufügen](../media/add-new-localized-content.png "Neuen lokalisierten Inhalt hinzufügen")  

> [!Note]
> Die Konfigurationsfelder auf der Homepage einer Inhaltsseite werden nicht auf die vorhandenen Inhaltsseiten übernommen. Sie werden nur bei der Erstellung neuer Inhaltsseiten verwendet. Sie müssen die Konfigurationen der Inhaltsseite einzeln aktualisieren.

Wissensartikel werden nur angezeigt, wenn sie in die Sprachen übersetzt wurden, die vom Benutzer für das Portals zur Anzeige festgelegt wurde. Allerdings ist bei Foren und Blogs mehr Kontrolle über die Darstellungsweise in anderen Sprachen möglich. Das Angeben einer Sprache für ein Forum oder einen Blog ist optional. Wenn eine Sprache nicht angegeben ist, wird das Forum oder der Blog in der primären Sprache der Organisation angezeigt. Wenn das Forum oder Blog für eine besondere Sprache spezifisch sein soll, müssen Sie es erstellen und eine Sprache zuweisen.

Weblinksätze sind die Navigationslinks am Anfang des Portals. Wenn Sie zu **Portale** > **Inhalt** > **Weblinksätze** navigieren, können Sie steuern, wie dieser Inhalten übersetzt wird. Wenn eine Sprache für das Portal aktiv ist, wird ein neuer Linksatz für die neu aktivierte Sprache erstellt.

![Aktiver Internet-Link für neue Sprache](../media/active-weblink-new-language.png "Aktiver Internet-Link für neue Sprache")
