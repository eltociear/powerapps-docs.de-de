---
title: Aktualisieren der PowerApps-Befehlszeilenschnittstelle | Microsoft Docs
description: Aktualisieren der PowerApps-Befehlszeilenschnittstelle
keywords: 'PowerApps-Komponentframework-Tooling, Benutzerdefinierte Komponenten, Komponentenframework'
ms.author: nabuthuk
manager: kvivek
ms.date: 05/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47c4426c-e963-4ef6-a4b7-d56591ca8ac2
---

# <a name="updating-tooling-to-latest-version"></a>Aktualisieren der Tools auf die neueste Version

Um Ihre Microsoft PowerApps CLI auf die neueste Version 02.856.1 zu aktualisieren und von den gesamten neuen Funktionen zu profitieren, führen Sie den folgenden Befehl in der Entwicklereingabeaufforderung für VS 2017 aus.

```CLI
pac install latest
```

## <a name="what-else-do-i-need-to-know"></a>Was muss ich sonst noch wissen?

Wenn Sie bereits ein Lösungs- oder PowerApps component framework-Projekt erstellt haben, stellen Sie sicher, dass Sie diese Projekte auf die neuesten Pakete aktualisieren. Hierdurch können Sie neu hinzugefügte Funktionen bei Ihren vorhandenen Projekten nutzen. Neu erstellte Projekte enthalten diese Einstellungen bereits.

- Aktualisieren Sie das Versionstag in `pcfproj`, das sich innerhalb Ihres PowerApps component framework-Projektordners befindet:

   ```XML
   <PackageReference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="0.*"/>
   ```
- Aktualisieren Sie das Versionstag in `cdsproj`, das sich innerhalb Ihres Lösungsprojektordners befindet:

   ```XML
   <PackageReference Include="Microsoft.PowerApps.MSBuild.Solution" Version="0.*"/>
   ```

    > [!NOTE] 
    > Nachdem Sie die oben beschriebenen Änderungen vorgenommen haben, führen Sie den Befehl `msbuild /t:restore` aus, um Ihr Projekt auf die korrekte Version zu aktualisieren.


- Aktualisieren Sie das Versionstag in Ihrer `package.json`-Datei, die sich innerhalb Ihres PowerApps component framework-Projektordners befindet:

  ```JSON
  "devDependencies":{
   "pcf-scripts": "^0",
   "pcf-start": "^0"
    }
  ```
   > [!NOTE]
   > Nachdem Sie die oben genannten Änderungen vorgenommen haben, wird bei Verwendung von „npm update” in der Eingabeaufforderung Ihr Projekt immer auf die korrekte Version aktualisiert.
