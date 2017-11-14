Wenn Sie den Kurs bis hierhin verfolgt haben, haben Sie bereits einige Zeit auf web.powerapps.com gearbeitet. Bewusst oder unbewusst haben Sie dabei die ganze Zeit in einer *Umgebung* gearbeitet. Eine Umgebung ist einfach eine Gruppierung von Apps und anderen Ressourcen (dazu gleich mehr). Betrachten Sie die obere rechte Ecke des Bildschirms in web.powerapps.com: Dort sehen Sie ein Dropdownmenü, in dem die aktuelle Umgebung angezeigt wird.

![Umgebungsauswahl](./media/learning-manage-environments/environment-picker.png)

Wenn Sie noch nicht viel mit PowerApps gearbeitet haben, wird hier vermutlich nur die Standardumgebung angezeigt. Klicken oder tippen Sie auf das Menü, um festzustellen, ob andere Umgebungen verfügbar sind.

## <a name="why-use-environments"></a>Vorteile von Umgebungen
Eine Umgebung ist ein Container für Apps und andere Ressourcen wie Datenverbindungen und Flows aus Microsoft Flow. Sie stellt eine Möglichkeit dar, Elemente auf Grundlage Ihrer Geschäftsanforderungen zu gruppieren. Es gibt verschiedene Gründe dafür, neben der Standardumgebung weitere Umgebungen zu erstellen:

* **Trennen der App-Entwicklung nach Abteilungen**: In einem großen Unternehmen kann jede Abteilung so in einer anderen Umgebung arbeiten.
* **ALM-Unterstützung (Application Lifecycle Management)**: Sie können separate Umgebungen für Apps in der Entwicklungsphase und Apps erstellen, die bereits fertig sind und freigegeben wurden.
* **Verwalten des Zugriffs auf Daten**: Jede Umgebung kann über eine eigene Common Data Service-Datenbank und andere Datenverbindungen verfügen, die für die Umgebung spezifisch sind (d.h., sie werden nicht umgebungsübergreifend freigegeben).

Dabei müssen Sie bedenken, dass Umgebungen nur für App-Ersteller und PowerApps-Administratoren relevant sind. Wenn Sie eine App für einen Benutzer freigeben, führt dieser die App einfach nur aus, sofern er über die richtigen Berechtigungen verfügt. Er muss sich keine Gedanken darüber machen, aus welcher Umgebung sie stammt.

## <a name="create-an-environment"></a>Erstellen einer Umgebung
Bisher ging es in diesem Kurs in erster Linie um die Ersteller von Apps, Umgebungen werden allerdings von Administratoren erstellt und verwaltet. Wenn Sie kein Administrator sind, können diese Informationen trotzdem für Sie hilfreich sein, wenn Sie mit Ihrem Administrator das Einrichten von Umgebungen besprechen. Klicken oder tippen Sie im PowerApps Admin Center auf **Umgebungen** und dann auf **Neue Umgebung**. Geben Sie auf dem Bildschirm **Neue Umgebung** einen Namen für die Umgebung ein, wählen Sie eine Region aus, wählen Sie aus, ob für die Umgebung eine Common Data Service-Datenbank erstellt werden soll, und klicken oder tippen Sie auf **Umgebung erstellen**.

![Erstellen einer Umgebung](./media/learning-manage-environments/create-environment.png)

Das war es schon. Jetzt haben Sie eine neue Umgebung, in der Sie arbeiten können. Wenn Sie zurück zu web.powerapps.com navigieren, können Sie sie im Dropdownmenü mit den Umgebungen sehen.

## <a name="manage-access-to-an-environment"></a>Verwalten des Zugriffs auf eine Umgebung
Folgende Benutzer haben Zugriff auf eine Umgebung:

* **Umgebungsadministratoren**: Sie verfügen über vollständige Berechtigungen in der Umgebung.
* **Umgebungsersteller**: Sie können alle Apps anzeigen, Apps erstellen und mit dem Common Data Service arbeiten (andere Berechtigungen gelten).

Als Administrator gewähren Sie Zugriff auf eine Umgebung auf der Registerkarte **Umgebungen**. Klicken oder tippen Sie zuerst auf eine Umgebung. Wenn Sie einen Benutzer hinzufügen möchten (in diesem Beispiel ein **Umgebungsersteller**), klicken oder tippen Sie auf **Umgebungsrollen** und dann auf **Umgebungsersteller**. Hier können Sie der Rolle Benutzer oder Gruppen hinzufügen. Klicken Sie danach auf **Speichern**.

![Zugriff auf die Umgebung verwalten](./media/learning-manage-environments/environment-access.png)

Sie kennen nun die Vorteile von Umgebungen und wissen, wie Sie sie erstellen und den Zugriff darauf gewähren. Auch wenn Sie kein Administrator sind, sind diese Informationen hilfreich. Hiermit sind wir am Ende des Abschnitts zum Verwalten von Apps angelangt und bereit für den nächsten Abschnitt: das Verwalten von Daten mit Schwerpunkt auf dem Common Data Service.

