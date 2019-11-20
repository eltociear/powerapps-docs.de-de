Ist die Einbettung von Power BI-Kacheln und ‑Dashboards aktiviert und ein Benutzer nimmt eine derartige Power BI-Einbettung vor, wird das [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]-Autorisierungstoken für Common Data Service verwendet, um sich beim Power BI-Service mit einer impliziten Bewilligung zu authentifizieren. Dies ermöglicht dem Endanwender ein nahtloses „Single Sign-on“.  
  
 Administratoren können die Einbettung von Power BI-Kacheln und ‑Dashboards jederzeit deaktivieren, um die Verwendung des [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]-Autorisierungstokens zum Authentifizieren beim Power BI-Service zu verhindern. Alle vorhandenen Kacheln oder Dashboards werden dann nicht mehr für den Endbenutzer gerendert.  
  
 Die [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]-Komponente oder der -Service, die bzw. der an bei der Einbettung von Power BI-Kacheln beteiligt ist, wird im folgenden Abschnitt ausführlicher beschrieben.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Dieser Dienst stellt das Authentifizierungstoken zur Verfügung, das zur API‑ und UI-Authentifizierung mit dem Power BI-Service ausgetauscht wird.
