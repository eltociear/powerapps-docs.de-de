In diesem Abschnitt des Kurses erstellen wir eine App aus der SharePoint-Liste „Flooring Estimates“, die Kostenvoranschläge zu Bodenbelägen enthält. Die App könnte z.B. von einem Kalkulator vor Ort beim Kunden verwendet werden, um diese Liste abzurufen und zu aktualisieren. Im Abschnitt mit den ersten Schritten haben wir Ihnen bereits gezeigt, wie Sie eine App aus der gleichen Liste generieren – warum betrachten wir sie jetzt also noch einmal? Wir beginnen diesmal nicht in PowerApps Studio, sondern zeigen, wie PowerApps in SharePoint Online integriert ist. Außerdem gehen wir ausführlicher auf den Aufbau der App ein und erläutern, wie Sie sie anpassen können. Es gibt in diesem Abschnitt daher einige neue Informationen, legen wir also gleich los!

## <a name="generate-the-app"></a>Generieren der App
Die folgende Abbildung zeigt die SharePoint-Liste „Flooring Estimates“, die grundlegende Informationen wie Name und Preis sowie ein Bild für die einzelnen Bodenbeläge enthält. Sie können erkennen, wie PowerApps und Microsoft Flow jetzt in SharePoint Online integriert sind, damit Sie aus Ihren Listen ganz einfach Apps und Flows erstellen können.

![Liste „Flooring Estimates“](./media/learning-spo-app-generate/flooring-estimates-list.png)

Klicken Sie zum Erstellen einer App auf **PowerApps** und dann auf **App erstellen**. Geben Sie im rechten Bereich einen Namen für die App ein, und klicken Sie dann auf **Erstellen**. Nachdem Sie auf **Erstellen** geklickt haben, wird die App von PowerApps generiert. PowerApps zieht eine Vielzahl von Rückschlüssen aus Ihren Daten, um eine sinnvolle App als Ausgangspunkt zu generieren.

![App aus Liste generieren](./media/learning-spo-app-generate/generate-app.png)

## <a name="view-the-app-in-powerapps-studio"></a>Anzeigen der App in PowerApps Studio
Ihre neue App mit drei Bildschirmen wird in PowerApps Studio geöffnet. Alle Apps, die aus Daten generiert wurden, weisen die gleichen Bildschirme auf:

* Der **Bildschirm zum Durchsuchen**: Hier können Sie die aus der Liste abgerufenen Daten durchsuchen, sortieren, filtern und aktualisieren und Elemente hinzufügen, indem Sie auf das Pluszeichen (+) klicken.
* Der **Detailbildschirm**: Hier werden weitere Informationen zu einem Element angezeigt, und Sie können das Element löschen oder bearbeiten.
* Der **Bildschirm zum Bearbeiten/Erstellen**: Hier können Sie vorhandene Elemente bearbeiten oder neue Elemente erstellen.

Klicken oder tippen Sie auf der linken Navigationsleiste rechts unten auf ein Symbol, um zur Miniaturansicht zu wechseln.

![Umschalten der Ansichten](./media/learning-spo-app-generate/toggle-view.png)

Klicken oder tippen Sie auf jede Miniaturansicht, um die Steuerelemente auf diesem Bildschirm anzuzeigen.

![Die generierte App](./media/learning-spo-app-generate/generate-finished-app.png)

## <a name="run-the-app-in-preview-mode"></a>Ausführen der App im Vorschaumodus
Klicken oder tippen Sie auf ![Pfeil zum Starten der App-Vorschau](./media/learning-spo-app-generate/f5-arrow-sm.png) oben rechts, um die App auszuführen. Wenn Sie durch die App navigieren, sehen Sie, dass sie alle Daten aus der Liste enthält und in der Standardversion bereits gut zu bedienen ist.

![Ausführen der App im Vorschaumodus](./media/learning-spo-app-generate/generate-run-app.png)

Als Nächstes betrachten wir die App genauer und passen sie dann an, um sie besser auf die Anforderungen zuzuschneiden.

