---
title: 'Export, vorbereiten und bearbeiten und importieren des Menübands (Modell-angetriebene Apps) | Microsoft Docs'
description: 'Infos zum Exportieren des Menübands, indem Sie es in eine Lösung einschließen und dann die Lösung exportieren. Sie können auswählen, alle Anpassungen zu exportieren, aber dies kann eine große Datenmenge darstellen. Wir empfehlen, dass Sie eine vorhandene nicht-verwaltete Lösung verwenden oder eine neue Lösung erstellen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="export-prepare-to-edit-and-import-the-ribbon"></a>Exportieren, Vorbereitung der Bearbeitung und Importieren des Menübands

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/export-prepare-edit-import-ribbon -->

Um das Menüband zu bearbeiten, müssen folgende Aufgaben ausgeführt werden:  
  
1.  [Exportieren des Menübands](export-prepare-edit-import-ribbon.md#BKMK_ExportTheRibbon)  
  
2.  [Vorbereitung zum Bearbeiten der XML-Datei](export-prepare-edit-import-ribbon.md#BKMK_PrepareToEditTheXML)  
  
3.  Bearbeiten des `<RibbonDiffXml>`  
  
4.  [Importieren des Menübands](export-prepare-edit-import-ribbon.md#BKMK_ImportTheRibbon)  
  
<a name="BKMK_ExportTheRibbon"></a>   
## <a name="export-the-ribbon"></a>Exportieren des Menübands  
 Exportieren Sie das Menüband, indem Sie es in eine Lösung einschließen und dann die Lösung exportieren. Sie können auswählen, alle Anpassungen zu exportieren, aber dies kann eine große Datenmenge darstellen. Wir empfehlen, dass Sie eine vorhandene nicht-verwaltete Lösung verwenden oder eine neue Lösung erstellen.  
  
#### <a name="create-a-new-solution"></a>Erstellen einer neuen Lösung  
  
1. Gehen Sie zu **Einstellungen > Anpassungen**.
1. Gehen Sie zu **Einstellungen > Lösungen**.
1. Klicken oder tippen Sie auf **Neu**.  
1. Geben Sie einen aussagefähigen **Anzeigenamen**, **Eindeutigen Namen** ein, und geben Sie einen **Herausgeber** ein, und geben Sie eine **Versionsnr.** ein.  
  
   > [!NOTE]
   >  Sie können den Standardherausgeber für die Organisation verwenden.  
  
6. Klicken Sie auf das Symbol **Speichern**.  
  
7. Wenn Sie das Menüband für bestimmte Entitäten bearbeiten möchten:  
  
   1.  Klicken Sie auf **Vorhandenes Element hinzufügen**, und klicken Sie dann auf **Entität**.  
  
   2.  Wählen Sie die Entitäten aus, die Sie in die Lösung einschließen möchten, und klicken Sie dann auf **OK**.  
  
       > [!NOTE]
       >  Für Bearbeitung von Entitätsmenübändern müssen Sie erforderliche Komponenten nicht hinzugefügt werden. Wenn Sie beabsichtigen, diese Lösung zu exportieren und sie auf ein anderes System anzuwenden, sollten Sie die erforderlichen Komponenten einschließen.  
  
8. Wenn Sie globale Menübänder bearbeiten oder eine benutzerdefinierte Gruppe allen Entitäten hinzufügen möchten, klicken Sie auf **Vorhandenes Element hinzufügen**, und klicken Sie dann auf **Anwendungsmenübänder**.  
  
9. Klicken Sie auf **Speichern und schließen**.  
  
#### <a name="use-an-existing-solution"></a>Verwenden einer vorhandenen Lösung  
  
1. Gehen Sie zu **Einstellungen > Anpassungen**.
1. Gehen Sie zu **Einstellungen > Lösungen**. 
1. Doppelklicken Sie auf eine Lösung um sie zu öffnen.  
  
5. Wenn Sie das Menüband für bestimmte Entitäten bearbeiten möchten:  
  
   1.  Klicken Sie auf **Vorhandenes Element hinzufügen**, und klicken Sie dann auf **Entität**.  
  
   2.  Wählen Sie die Entitäten aus, die Sie in die Lösung einschließen möchten, und klicken Sie dann auf **OK**.  
  
       > [!NOTE]
       >  Für Bearbeitung von Entitätsmenübändern müssen Sie erforderliche Komponenten nicht hinzugefügt werden. Wenn Sie beabsichtigen, diese Lösung zu exportieren und sie auf ein anderes System anzuwenden, sollten Sie die erforderlichen Komponenten einschließen.  
  
6. Wenn Sie globale Menübänder bearbeiten möchten, indem Sie etwa benutzerdefinierte Schaltflächen allen Entitäten hinzufügen möchten, klicken Sie auf **Vorhandenes Element hinzufügen**, und klicken Sie dann auf **Anwendungsmenübänder**.  
  
7. Klicken Sie auf **Speichern und schließen**.  
  
#### <a name="export-the-ribbon"></a>Exportieren des Menübands  
  
1. Gehen Sie zu **Einstellungen > Anpassungen**.
1. Gehen Sie zu **Einstellungen > Lösungen**.
  
4. Wählen Sie die gewünschte Lösung aus, und klicken Sie anschließend auf **Exportieren**.  
  
5. Wenn Sie kürzlich Änderungen vorgenommen haben, die noch nicht veröffentlicht wurden, klicken Sie auf **Alle Anpassungen veröffentlichen**. Klicken Sie andernfalls auf **Weiter**.  
  
6. Wenn die Option **Nicht verwaltet** ausgewählt ist, klicken Sie auf **Exportieren**.  
  
7. Klicken Sie im Dialogfeld **Dateidownload** auf **Speichern** und dann im Dialogfeld **Download abgeschlossen** auf **Ordner öffnen**.  
  
8. Klicken Sie mit der rechten Maustaste auf die komprimierte ZIP-Datei, die Sie heruntergeladen haben, und wählen Sie **Alle extrahieren...**.  
  
9. Wählen Sie einen Speicherort aus, um die Dateien zu extrahieren, und klicken Sie auf **Extrahieren**.  
  
10. Die Datei customizations.xml ist die Datei, die Sie bearbeiten.  
  
<a name="BKMK_PrepareToEditTheXML"></a>   
## <a name="prepare-to-edit-the-xml"></a>Vorbereitung zum Bearbeiten der XML-Datei  
 Für eine verbesserten Anwendungsleistung bearbeiten Sie die Datei customizations.xml mit einer Anwendung, die die Schemaüberprüfung verwenden kann, um IntelliSense-Support bereitzustellen. Weitere Informationen finden Sie unter [Bearbeiten der Anpassungsdatei mit Schemaüberprüfung](edit-customizations-xml-file-schema-validation.md).  
  
<a name="BKMK_ImportTheRibbon"></a>   
## <a name="import-the-ribbon"></a>Importieren des Menübands  
  
1. Nachdem Sie die customization.xml-Datei bearbeitet haben, klicken Sie mit der rechten Maustaste in  Visual Studio oder Visual Web Developer 2010 auf die Registerkarte customization.xml und wählen Sie **Enthaltenden Ordner öffnen**.  
  
2. Wählen Sie alle Dateien oder Ordner aus, die enthalten waren, als Sie die Lösung extrahierten. Klicken Sie mit der rechten Maustaste auf die ausgewählten Dateien, wählen Sie **Senden an**, und wählen Sie dann **Komprimierter (gezippter) Ordner**.  
  
   > [!NOTE]
   >  Dies erstellt eine komprimierte ZIP-Datei im gleichen Ordner. Der Name der Dateikann abweichen, aber er ist identisch mit einer der anderen Dateien im Ordner - außer mit einer eine ZIP-Dateinamenerweiterung.  
  
1. Gehen Sie zu **Einstellungen > Anpassungen**.
1. Gehen Sie zu **Einstellungen > Lösungen**. 
  
6. Klicken Sie auf **Importieren**.  
  
7. Klicken Sie auf **Durchsuchen** und suche Sie die komprimierte ZIP-Datei, die Sie in Schritt 2 dieser Vorgehensweise erstellten.  
  
8. Klicken Sie auf **Weiter** und anschließend auf **Importieren**.  
  
9. Nachdem derImport abgeschlossen ist, wird die Meldung angezeigt, die angibt, dass der Importvorgang erfolgreich abgeschlossen wurde. Klicken Sie auf Schließen.  
  
10. Nachdem Sie die Lösung erfolgreich importiert haben, müssen Sie Anpassungen veröffentlichen, bevor Sie die Änderungen anzeigen können. Klicken Sie der Lösungsliste auf **Alle Anpassungen veröffentlichen**.  
  
<a name="BKMK_DealWithErrorsOnImport"></a>   
### <a name="dealing-with-errors-on-import"></a>Behandeln von Fehlern beim Import  
  
1.  Wenn Sie eine Benachrichtigung erhalten, dass Fehler aufgetreten sind, durch die der Import scheiterte, klicken Sie auf **Exportprotokoll**.  
  
2.  Speichern Sie die Exportprotokolldatei. Wählen Sie die Datei aus, und klicken Sie mit der rechten Maustaste darauf. Wählen Sie **Öffnen mit**, und wählen Sie dann **Microsoft Office Excel**.  
  
3.  Wählen Sie die Tabelle **Komponenten** aus und notieren Sie die Mitteilungen in der Spalte **Fehlertext**.  
  
    > [!TIP]
    >  Der häufigste Fehlertyp ist ein Fehler beim Verweisen auf ein abhängiges Element im RibbonDiffXml. Möglicherweise vergaßen Sie, ein LocLabel einzuschließen, auf das irgendwo verwiesen wurde. Möglicherweise es gibt ein zusätzliches Leerzeichen, das am Ende eines XML-Attributs enthalten ist, das auf ein anderes Element verweist. Alle Verweise müssen genau übereinstimmen.  
  
4.  Wenn Sie den Fehler behoben haben, führen Sie die Schritte aus, um das Menüband erneut zu importieren.  
  
### <a name="see-also"></a>Siehe auch  
 [Anpassen des Menübands](customize-commands-ribbon.md)   
 [Exportieren von Menübanddefinitionen](export-ribbon-definitions.md)   
 [Verwenden von lokalisierten Bezeichnungen in Menübändern](use-localized-labels-ribbons.md)
