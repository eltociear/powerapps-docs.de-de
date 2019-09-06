---
title: Erstellen und Entwickeln einer benutzerdefinierten Komponente | Microsoft Docs
description: Starten der Erstellung einer Komponente mit PowerApps-Komponentenframework-Tooling
keywords: 'PowerApps-Komponentframework-Tooling, Benutzerdefinierte Komponenten, Komponentenframework'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---

# <a name="create-and-build-a-custom-component"></a>Erstellen und Entwickeln einer benutzerdefinierten Komponente

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Dieses Thema enthält Informationen zum Erstellen und Bereitstellen einer benutzerdefinierten Komponente mithilfe des PowerApps component framework.

Stellen Sie sicher, dass Microsoft PowerApps CLI installiert ist

## <a name="create-a-new-component"></a>Erstellen einer neuen Komponente

Für den Anfang öffnen Sie eine neue Entwicklereingabeaufforderung für VS 2017 nach der Installation von PowerApps-CLI.

1. In der Entwicklereingabeaufforderung für VS 2017 erstellen Sie einen neuen Ordner auf Ihrer lokalen Festplatte, z. B. *C:\Benutzer\<Ihr Name>\Dokumente\Mein_PCF_Steuerelement*
2. Wechseln Sie mit dem Befehl `cd <specify your new folder path>` zum neu erstellen Ordner
3. Führen Sie den folgenden Befehl aus, um ein neues Komponentenprojekt zu erstellen, indem Sie einige Basisparameter übergeben:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Derzeit bieten wir zwei Arten von Komponenten an: **Feld** und **Dataset**.

4. Um alle erforderlichen Projektabhängigkeiten abzurufen, führen Sie den Befehl `npm install` aus.
5. Öffnen Sie Ihren Projektordner (`C:\Users\<your name>\Documents\My_PCF_Control\<component name>`) in einer Entwicklerumgebung Ihrer Wahl und beginnen Sie mit der Entwicklung Ihrer benutzerdefinierten Komponente.

## <a name="build-your-component"></a>Entwickeln Ihrer Komponente

Um Ihre Komponente zu erstellen, können Sie den Ordner in Visual Studio Code öffnen und den Befehl (Strg-Umschalt-B) verwenden. Dann wählen Sie Ihre Build-Optionen aus. Alternativ können Sie Ihre Komponente schnell mit dem `npm run build`-Befehl in Ihrem Entwicklereingabeaufforderung für VS 2017-Fenster erstellen.

> [!TIP]
> Zum Debuggen Ihrer Komponente während oder nach dem Buildvorgang siehe [Debuggen einer benutzerdefinierten Komponente](debugging-custom-controls.md).

## <a name="known-configuration-issues-and-workarounds"></a>Bekannte Konfigurationsprobleme und Behebungen

**Msbuild-Fehler MSB4036:**

1. Der Name der Aufgabe in der Projektdatei gleicht dem Namen der Aufgabenklasse.
2. Die Aufgabenklasse ist öffentlich und implementiert die Microsoft.Build.Framework.ITask-Schnittstelle.
3. Die Aufgabe ist mit \<UsingTask> korrekt in der Projektdatei in den *.tasks-Dateien im Verzeichnis <path> deklariert.

**Lösung:**

1. Öffnen Sie das Visual Studio-Installationsprogramm. 
1. Wählen Sie für VS 2017 **Ändern** aus. 
1. Klicken Sie auf „Einzelne Komponenten“.
1. Überprüfen Sie unter „Code-Tools“ die Option **NuGet-Ziele und Build-Aufgaben**.

### <a name="see-also"></a>Siehe auch

[Debuggen von benutzerdefinierten Komponenten](debugging-custom-controls.md)<br/>
[Bündeln einer benutzerdefinierten Komponente](import-custom-controls.md)<br/>
[Hinzufügen von benutzerdefinierten Komponenten zu einem Feld oder einer Entität](add-custom-controls-to-a-field-or-entity.md)<br/>
[Aktualisieren vorhandener benutzerdefinierter Komponenten](updating-existing-controls.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](overview.md)
