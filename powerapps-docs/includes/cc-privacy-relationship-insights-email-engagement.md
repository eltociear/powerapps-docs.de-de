Wenn Sie die E-Mail-Nachverfolgung aktivieren, ein Feature von „Eingebettete Intelligenz“, werden beim Senden einer E-Mail, die mit der Einstellung **Folgen** markiert wurde, von [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] Informationen über Interaktionen mit der E-Mail durch die Empfänger gesammelt und in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] gespeichert. Dort können KPIs zu Aktivitäten des Empfängers und Interaktionen mit „verfolgten“ E-Mails berechnet werden.  
  
 Systemadministratoren können die E-Mail-Nachverfolgung aktivieren, indem sie das Feature auf der Registerkarte **E-Mail-Nachverfolgung** in „Eingebettete Intelligenz“ bereitstellen. Anschließend können Administratoren die E-Mail-Nachverfolgung in der Organisation über den Knoten **Intelligenzkonfiguration** unter **Einstellungen** deaktivieren.  
  
 Wenn das Feature deaktiviert wurde, können von [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] gesendete E-Mails nicht mehr verfolgt werden, weder über die Benutzeroberfläche noch programmgesteuert. Darüber hinaus werden keine Empfängerinteraktionsdaten mehr zu E-Mails gesammelt, die mit der Einstellung **Folgen** markiert wurden. Alle zuvor gesammelten Daten verbleiben in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] und sind wieder verfügbar, wenn das Feature in der Organisation erneut aktiviert wird. Daten werden 90 Tage lang beibehalten, nachdem Kunden ihre Abonnements bei Microsoft beenden. [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Benutzer können die „Eingebettete Intelligenz“-Funktion „E-Mail-Nachverfolgung“ auch für einzelne Kontakte oder Leads deaktivieren, indem sie die Einstellung **E-Mail folgen** unter **Kontaktvoreinstellungen** ändern.  
  
 Die im Rahmen der E-Mail-Nachverfolgung verfügbaren [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponenten und -Dienste werden im Folgenden ausführlich dargestellt.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]**  
  
 Das Feature zur E-Mail-Nachverfolgung speichert mithilfe von [!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)] temporär E-Mail-Interaktionsblobs.