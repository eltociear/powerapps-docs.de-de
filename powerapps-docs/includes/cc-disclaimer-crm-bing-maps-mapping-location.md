## <a name="mapping-functions-for-dynamics-365-plan"></a>Kartenfunktionen für Dynamics 365-Plan 
 Field Service und Project Service Automation enthalten wichtige Funktionen, die auf dem Standort basieren. Beispiel: Standort von Dienstkonten (durch die definiert wird, wo Services oder Aufgaben stattfinden) oder der geografische Start-/Endpunkt für Ressourcen (Personen, die Services oder Aufgaben ausführen).  Damit das System diese auf einer Karte anzeigen oder die Entfernung zwischen zwei Punkten berechnen kann, sind Kartendienste erforderlich (in diesem Fall Bing Maps).  
  
 Im Folgenden finden Sie den Workflow zum und vom Bing Maps-Service:  
  
|Von Dynamics 365|Bing Maps-Rückgabe|Hinweis|  
|-----------------------|-----------------------|----------|  
|Adresse (Konto oder Ressource)|Breite und Länge der Adresse (Standort)|Dies wird als Geocode einer Adresse bezeichnet.|  
|Gruppe von Standorten (Breite/Länge)|Abstand zwischen Standorten|Dies kann verwendet werden, um die optimalen Strecken für Ressourcen zu ermitteln oder die Fahrtdauer zu berechnen.|  
|Gruppe von Standorten (Breite/Länge)|Kartenansicht mit den Standorten in Form von Nadeln auf der Karte|Dies wird häufig verwendet, um die Konten und Ressourcen in einer Kartenansicht anzuzeigen.|  
  
> [!NOTE]
>  Neben den oben erwähnten Daten werden keine weiteren Daten an den Bing Maps-Service gesendet.
