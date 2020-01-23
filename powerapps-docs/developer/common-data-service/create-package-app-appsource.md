---
title: 'Schritt 3: Erstellen eines AppSource-Pakets für die App (Common Data Service) | Microsoft Docs'
description: Lernen Sie, wie Sie eine AppSource-Paket (ZIP-Datei) erstellen, um die Lösungs- und Demodatendateien zusammen mit anderen erforderlichen Dateien zu integrieren.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 43accbf1e1acf8c32e76c5e0c0dab4975cd847a0
ms.sourcegitcommit: f70be39855e4931312fe0035525586a15ed4487b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2019
ms.locfileid: "2922349"
---
# <a name="step-3-create-an-appsource-package-for-your-app"></a>Schritt 3: Erstellen eines AppSource-Pakets für die App

Sie müssen ein AppSource-Paket (ZIP-Datei) erstellen, um die Lösungs- und Demodatendateien zusammen mit anderen erforderlichen Dateien zu integrieren. Ein AppSource-Paket besteht aus den folgenden Dateien:

|Datei|Beschreibung|
|--|--|
|Paketdatei|Eine Paketdatei wird vom Package Deployer Tool verwendet, um Ihre Lösungen und Demokonfigurationsdaten in mehreren Sprachen bereitzustellen.|
|[Content_Types].xml|Datei, die MIME-Typinformationen zur Dateityperweiterungen im AppSource-Paket bereitstellt. Diese sind normalerweise .dll, .xml, .exe, und .config Dateitypen, aber Sie können fast jeden Dateityp hinzufügen, der von Windows unterstützt wird.|
|Symboldatei|Eine Bilddatei für das Appsource Paketsymbol; Größe sollte Pixel 32x32 sein. Gültige Bildformate sind PNG und JPG.|
|HTML-Datei|Datei, die die Lizenzbedingungen enthält.|
|input.xml|Dateien, der die Anlagen in Ihrem AppSource-Paket beschreibt.|


## <a name="create-a-package-file"></a>Erstellen Sie eine Paketdatei

Ein Paket können Sie in mehrere Dateien bündeln und bereitstellen, die gleichzeitig mit der App verknüpft sind. 

1. Erstellt ein Dynamics 365 Paket , um die Lösungs- und Konfigurationsdatendateien zu integrieren, die Sie erstellt haben in [Schritt 2: Erstellen einer verwalteten Lösung für Ihre App](create-solution-app-appsource.md) Ein benutzerdefinierter Code, der ausgeführt werden kann, bevor, während oder nachdem das Paket auf der Common Data Service-Instanz bereitgestellt wird. Ausführliche Informationen zum Erstellen einer Paketdatei finden Sie unter [Erstellen von Paketen für Dynamics 365 Package Deployer](/dynamics365/customer-engagement/developer/create-packages-package-deployer).

    Nachdem Sie ein Paket erstellt haben, besteht das Paket aus folgenden Ereignisse:

    - **\<PackageName> Ordner**Dieser Ordner enthält alle Lösungen, Konfigurationsdateien, Textdateien und Inhalte für Ihr Paket. Geben Sie beispielsweise **PkgFolder** ein.  
  
    - **\<PackageName>.dll**: Die Assembly enthält den benutzerdefinierten Code für das Paket. Beispiel: **SamplePackage.dll**.

2. Dann erstellen Sie eine **[Content_Types].xml**-Datei, die MIME-Typ-Informationen zu Dateityperweiterungen bereitstellt, die in Ihrem Paket enthalten sind. Dies ist getrennt von jener, die wieder im AppSource-Paket enthalten ist. Hier erhalten Sie Beispielinhalte einer Content_Types.xml Datei mit den aufgelisteten Dateitypen:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="https://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="xml" ContentType="application/octet-stream" />
      <Default Extension="xaml" ContentType="application/octet-stream" />
      <Default Extension="dll" ContentType="application/octet-stream" />
      <Default Extension="zip" ContentType="application/octet-stream" />
      <Default Extension="jpg" ContentType="application/octet-stream" />
      <Default Extension="gif" ContentType="application/octet-stream" />
      <Default Extension="png" ContentType="application/octet-stream" />
      <Default Extension="htm" ContentType="application/octet-stream" />
      <Default Extension="html" ContentType="application/octet-stream" />
      <Default Extension="db" ContentType="application/octet-stream" />
      <Default Extension="css" ContentType="application/octet-stream" />
    </Types>
    ```

3. Komprimieren (ZIP) Sie die folgenden Dateien in einer Datei mit dem Namen *package.zip*:
   - Paketordner (ISVs Sie PkgFolder)
   - Paket DLL (SamplePackage.dll)
   - [Content_Types].xml

     Damit diese Dateien komprimiert werden können, navigieren Sie zum Ordner, in dem die Dateien vorhanden sind, wählen sie alle, machen Sie einen Klick mit der rechten Maustaste und wählen Sie **Senden an** > **Komprimierter (gezippter) Ordner**.

     ![Zippen Sie die Dateien in einem Paket](media/appsource-zip-package.png) 

4. Benennen Sie die ZIP-Datei in **package.zip** um.

## <a name="create-content_typesxml"></a>[Content_Types].xml erstellen

Sie können die **[Content_Types].xml** wieder verwenden, die Sie im vorherigen Abschnitt mit Schritt 2 erstellt haben.

## <a name="create-an-icon-for-your-appsource-package"></a>Erstellen eines Symbols für das AppSource-Paket

Erstellen Sie eine Symboldatei der Größe 32x32 zur Anzeige zusammen mit dem bevorzugten Lösungsnamen und -Beschreibung im Dynamics 365 Admin Center-Portal. Gültige Dateiformate sind PNG und JPG.

## <a name="create-an-html-file-for-license-terms"></a>Erstellen Sie eine HTML-Datei für Lizenzbedingungen

Erstellen Sie eine HTML-Datei, die die Lizenzbedingungen enthält. Sie können eine HTML-Datei pro Sprache haben, um die Lizenzbedingungen in der vom Benutzer ausgewählten Sprache anzeigen, falls die App mehrere Sprachen unterstützt.

## <a name="create-inputxml-file"></a>Erstellen Sie eine input.xml-Datei

Erstellen einer *input.xml* Datei, die Informationen über das Paket und die Inhalte des Pakets bereitstellt. Hier sind die Inhalte eines Dateibeispiels **input.xml**; jedes Element wird weiter unten in der Tabelle veranschaulicht.

```xml
<?xml version="1.0" encoding="utf-8"?>
<PvsPackageData>
  <ProviderName>Microsoft</ProviderName>
  <PackageFile>package.zip</PackageFile>
  <SolutionAnchorName>SampleSolution.zip</SolutionAnchorName>
  <StartDate>12/01/2017</StartDate>
  <EndDate>01/01/2021</EndDate>
  <SupportedCountries>US,CA</SupportedCountries>
  <LearnMoreLink>https://www.microsoft.com</LearnMoreLink>
  <Locales>
    <PackageLocale Code="1033" IsDefault="true">
      <Logo>logo32x32.png</Logo>
      <Terms>
        <PackageTerm File="TermsOfUse.html" />
      </Terms>
    </PackageLocale>
  </Locales>
</PvsPackageData>
```


Hier finden Sie eine Beschreibung der Elemente in der Datei **input.xml**.

|Element|Beschreibung|
|--|--|
|ProviderName|Name des Lösungsanbieters. Wenn Sie ein Team als Microsoft werden, geben Sie **Microsoft** an.|
|PackageFile|Name des Pakets (.zip-Datei) für das Package Deployer Tool. Dies sollte die Paketassembly, den Paketordner mit Ihren App-Anlagen und die Content_Types.xml-Datei enthalten. Die package.zip-Datei wird unter dem Abschnitt [Erstellen einer Paketdatei](#create-a-package-file) erstellt.|
|SolutionAnchorName|Name der Lösungs ZIP Datei im Paket, die für den Anzeigenamen und die Beschreibung der Lösungsanlagen verwendet wird.|
|StartDate|Datum, an dem die App für AppSource verfügbar ist. Das Datumsformat ist TT/MM/JJJJ.|
|Enddatum|Datum, an dem die App für AppSource nicht mehr verfügbar ist. Das Datumsformat ist TT/MM/JJJJ.|
|SupportedCountries|Dies ist eine durch Trennzeichen getrennte Liste mit Ländern oder Regionen, in denen die App verfügbar sein soll. Zurzeit werden folgende Länder unterstützt: AE,AL,AM,AO,AR,AT,AU,AZ,BA,BB,BD,BE,BG,BH,BM,BN,BO,BR,BY,CA,CH,CI,CL,CM,CO,CR,CV,CW,CY,CZ,DE,DK,DO,DZ,EC,EE,EG,ES,FI,FR,GB,GE,GH,GR,GT,HK,HN,HR,HU,ID,IE,IL,IN,IQ,IS,IT,JM,JO,JP,KE,KG,KN,KR,KW,KY,KZ,LB,LK,LT,LU,LV,LY,MA,MC,MD,ME,MK,MN,MO,MT,MU,MX,MY,NG,NI,NL,NO,NZ,OM,PA,PE,PH,PK,PL,PR,PS,PT,PY,QA,RO,RS,RU,RW,SA,SE,SG,SI,SK,SN,SV,TH,TM,TN,TR,TT,TW,UA,US,UY,UZ,VE,VI,VN,ZA,ZW|
|LearnMoreLink|URL zur Seite mit ausführlichen Informationen für dieses Paket.|
|Gebietsschema|Eine Instanz dieses Knotens für jede Sprache, die Sie in der bevorzugten Lösung der Benutzeroberfläche sichern möchten. Dieser Knoten enthält die folgenden untergeordneten Elemente:<br/>- **PackageLocale.Code**: Die LCID der Sprache für den Knoten. Beispiel: US-Englisch ist 1033<br/>- **PackageLocale.IsDefault**: Gibt die Standardsprache an. Diese wird als Ausweichsprache genutzt, wenn die Sprache, die vom Kunden ausgewählt wurde, nicht verfügbar ist.<br/>- **Logo**: Wählen Sie ein Logo für Ihre App. Größe des Bilds muss 32x32 sein. Gültige Bildformate sind PNG und JPG.<br/>- **Bedingungen**: Name der HTML-Datei, die Lizenzbedingungen für alle Sprachen enthält.|

## <a name="add-the-items-to-an-appsource-package"></a>Einem AppSource-Paket die Elemente hinzufügen

Letzter Schritt besteht darin, alle Komponenten hinzufügen, die Sie zuvor nach einer komprimierten Datei (ZIP) einzeln erstellen, die Ihr App-Quellpaket sein wird.

1. Navigieren Sie zum Ordner, der die Paketdatei, [Content_Types].xml, das Symbol und die Lizenzbedingungsdatei (HTML) enthält, wählen Sie alle Datenbanken aus, klicken Sie mit der rechten Maustaste und wählen Sie dann den Ordner **Senden an** > **ZIP-komprimierten Ordner** aus.

    ![AppSource-Paket](media/appsource-package.png)

    > [!IMPORTANT]
    > Sie müssen der Inhaltsstruktur für Ihr Paket genau folgen, wie hier beschrieben. Sonst erzeugt das Paket während der Zertifizierung Fehler. Einige allgemeine Probleme, die zu Zertifizierungsfehler führen, beibehalte falsche Namen oder eine geschachtelte Dateistruktur.

2. Benennen Sie die Datei gemäß der App um. Es ist empfehlenswert, den Kontonamen und App-Namen einzuschließen. Beispiel: **Microsoft_SamplePackage.zip**.
 

> [!div class="nextstepaction"]
> [Schritt 4: Speichern Sie das AppSource-Paket auf Azure Storage](store-appsource-package-azure-storage.md) 
